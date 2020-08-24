# /boot sektörünü şifrelemek

Boot sektöründe bulunan çekirdek ve grub yapılandırma dosyalarınından doğabilecek tehlikeleri /boot sektörünü şifreleyerek yüksek oranda bertaraf edebilirsiniz.

GNU/Linux dağıtımlarının kurulum aşamasında sunduğu tam disk şifreleme /boot sektörünü **şifrelemez**. Bu tercihin pratik sebepleri bulunmakla birlikte bir gün tercihen bu yapılandırmanın seçilebilmesi dağıtımlar yönünden gereklidir.

## Boot sektörünü şifrelemek ne sağlar?

Boot sektörünün şifrelenmesi bilgisayarınıza kapalı iken erişen fiziken erişen bir kişinin kötücül bir çekirdek veya grub yapılandırmasını sürücünüze yazarak bilgisayarınızın güvenliğini elinizden almasına yüksek oranda engel olur. 

## Boot sektörünün şifrelenmesi

**UYARI: Bu rehberde yapacağınız işlemler işletim sisteminizin çalışmamasına sebebiyet verebilir. Yedek almadan bu rehberde anlatılanları uygulamamanız hararetle önerilir**

Bu rehber anlatımında [Cryptsetup-team](https://cryptsetup-team.pages.debian.net/cryptsetup/encrypted-boot.html) rehberini esas almış ve kimi noktalarda değişiklikler getirmiştir. Test Fedora 31 dağıtımı ile UEFI kullanan Dell XPS 13 cihaz üzerinde yapmıştır.

Öncelikle bilgisayarınızın kurulum aşamasında LUKS şifreleme ile kurulduğu varsayımı ile aşağıdaki komut aracılığıyla sürücünüzün düzenine bakın.

```
root@debian:~# lsblk -o NAME,FSTYPE,MOUNTPOINT /dev/sda
NAME                    FSTYPE      MOUNTPOINT
sda
├─sda1                  ext2        /boot
├─sda2
└─sda5                  crypto_LUKS
  └─sda5_crypt          LVM2_member
    ├─debian--vg-root   ext4        /
    └─debian--vg-swap_1 swap        [SWAP]
```
Yukarıda bulunan /boot olarak işaretli olan "sda1" kurulumumuzun konusu olan donanımı ifade etmektedir. Bu değer sizin cihazınızda farklı olabilir. **Doğru cihazı seçtiğinizden emin olun.** Bu rehberde hep sda1 olarak kullanılacaktır.

Boot sektörünü şifrelemek için ilgili sektör silip tekrar yapılandırılacağı için öncelikle /boot altında olan dosyaların bir kopyasının alınması gerekmektedir. Sisteminizde bu rehber dahilinde yapacağınız pek çok işlem root yetkisi gerektirmektedir. Başlamak için;

/boot dizinini salt-okunur olarak bağlayın edin.

`mount -oremount,ro /boot`

/boot dizinin yazılacağı boş bir tar dosyası oluşturun.

`install -m0600 /dev/null /tmp/boot.tar`

/boot dizinini oluşturduğunuz tar dosyasına kaydedin.

`tar -C /boot --acls --xattrs --one-file-system -cf /tmp/boot.tar .`

/boot dizinini çıkarın.

`umount /boot`

Eğer /boot/efi gibi alt noktalar var ise cihazınızda onları da çıkarın.

`umount /boot/efi`

Şayet `umount` komutu inat ederse `-l` parametresi ile çalıştırın.

/boot sektörünün olacağı cihazı LUKS1 ile şifreleyin.

**ÖNEMLİ NOT: Şayet cihazınızın /root sektörü de şifreli ise aşağıda belirleyeceğiniz parolanın farklı olması durumunda bilgisayarınızın her açılışında 3 kere parola girmeniz gerekeceğini hatırlatmak isteriz. Bu durumu önlemenin çeşitli yolları olsa da güvenlik endişeniz yüksek ise 3 kere parola girmeye katlanmanız veya aynı parolayı hem /boot hem /root sektörleri için belirlemenizi öneririz. Şayet aynı parolayı kullanırsanız işletim sisteminiz otomatik otomatik olarak 1 parola girişini atlayacaktır.**


`cryptsetup luksFormat --type luks1 /dev/sda1`


```
WARNING!
========
This will overwrite data on /dev/sda1 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter passphrase for /dev/sda1:
Verify passphrase:
```
Gerekli değeri crypttab'a girip ilgili bölümü açın.

`uuid="$(blkid -o value -s UUID /dev/sda1)"`

`echo "boot_crypt UUID=$uuid none luks" | tee -a /etc/crypttab`

`cryptsetup luksOpen /dev/nvme0n1p2 boot_crypt`


```
Starting crypto disk...boot_crypt (starting)...
Please unlock disk boot_crypt:  ********
boot_crypt (started)...done.

```

Oluşturulan cihaz üzerinde bir dosya sistemi kurulması gerekli. Bunun için `/boot` dizininin UUID değerinin bilinmesi gerekli. Aşağıdaki komutu girerek gerekli değeri öğrenin.

`grep /boot /etc/fstab`

Komut ertesinde aşağıdaki gibi bir cevap dönecektir.

```
# /boot was on /dev/sda1 during installation
UUID=c104749f-a0fa-406c-9e9a-3fc01f8e2f78 /boot           ext2    defaults        0       2
```

`UUID=` sonrasında gelen tireler ile ayrılmış değeri bir sonraki komutta dosya sistemi oluşturmak için kullanılacaktır. Aşağıdaki komut ile dosya sistemini oluşturun.

**ÖNEMLİ NOT: UUID değeri her cihazda farklı olacağından yukarıdaki komut sonrası gelen değeri kullandığınızdan emin olmalısınız.**

`mkfs.ext4 -m0 -U c104749f-a0fa-406c-9e9a-3fc01f8e2f78 /dev/mapper/boot_crypt`

Komutu çalıştırdıktan sonra uçbirim aşağıdaki dönüşü size verecektir.

```
mke2fs 1.44.5 (15-Dec-2018)
Creating filesystem with 246784 1k blocks and 61752 inodes
Filesystem UUID: c104749f-a0fa-406c-9e9a-3fc01f8e2f78
[…]
```

Şifrelenen ve dosya sistemi oluşturulan /boot sektörünün daha önce yedeklenen içeriğinin geri yüklenmesi gerekli. Bunun için öncelikle /boot sektörünü bağlamak için aşağıdaki komutları çalıştırın.

`mount -v /boot`

Eğer EFI bölümünüz var ise bilgisayarınızda onu da ayrıca bağlamanız gereklidir.

`mount -v /boot/efi`

Ardından yedeklenen tar dosyasını /boot dizinine açın.

`tar -C /boot --acls --xattrs -xf /tmp/boot.tar`

Boot sektörü şifrelenip, gerekli dosyalar eklendikten sonra GRUB2 yapılandırmasının şifreli /boot sektörü için tekrar ayarlanması gerekli. Bunun için aşağıdaki komutları sırası ile çalıştırın.

`echo "GRUB_ENABLE_CRYPTODISK=y" >>/etc/default/grub`

**Kullandığınız GNU/Linux dağıtımı grub yapılandırma dosyasını farklı isimdeki dizinlerin altına eklemiş olabilir. Aşağıdaki komutta verilen dizinin cihazınızdaki doğru konum ile değiştirildiğinden emin olun.**

`grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg`

## Önemli notlar

* Bilgisayarınızın ilk açılışında GRUB /boot sektörüne erişebilmek için size parolanızı soracaktır. Siyah ekranda gelen tatsız bir giriş ekranı sizi korkutmasın. Parolanızı girerken ekranda * gibi simgeler çıkmayacağından parolayı doğru girmek konusunda dikkatli olun. Aynı zamanda GRUB /boot sektörünü deşifre edebilmek için işlemcilerin yerleşik AES motorunu veya işlemcinin tüm çekirdeklerini kullanamadığından işlemin tamamlanması bir dakikadan fazla alabilir. Şayet parolayı doğru girer iseniz cihazınızın yüklenmesine devam edilir, yanlış girerseniz UEFI ekranına dönülür.

* /boot sektörü için belirlediğiniz parola şayet /root sektörünüz ile aynı ise bilgisayarınız sizden aynı parolayı iki kere isteyecektir: bir kere açılışta GRUB tarafından bir kere de işletim sisteminizin yüklenmesi için. Şayet farklı parolalar belirledi iseniz 3 kere parola sorulacaktır.

* GRUB standart olarak ABD (US) klavye kullanır. Bu sebeple açılışta parolanızı girer iken Türkçe veya başka dilde özel harfler ve özel karakterler girmeniz gerekiyor ise bunların US klavyede nasıl girildiğini öğrenmeniz gereklidir.
