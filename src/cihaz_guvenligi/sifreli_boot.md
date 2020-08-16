# /boot sektörünü şifrelemek

Boot sektöründe bulunan çekirdek ve grub yapılandırma dosyalarınından doğabilecek tehlikeleri /boot sektörünü şifreleyerek yüksek oranda bertaraf edebilirsiniz.

GNU/Linux dağıtımlarının kurulum aşamasında sunduğu tam disk şifreleme /boot sektörünü **şifrelemez**. Bu tercihin pratik sebepleri bulunmakla birlikte bir gün tercihen bu yapılandırmanın seçilebilmesi dağıtımlar yönünden gereklidir.

## Boot sektörünü şifrelemek ne sağlar?

* Boot sektörünün şifrelenmesi bilgisayarınıza kapalı iken erişen fiziken erişen bir kişinin kötücül bir çekirdek veya grub yapılandırmasını sürücünüze yazarak bilgisayarınızın güvenliğini elinizden almasına yüksek oranda engel olur. 

## Boot sektörünün şifrelenmesi

**UYARI: Bu rehberde yapacağınız işlemler işletim sisteminizin çalışmamasına sebebiyet verebilir. Yedek almadan bu rehberde anlatılanları uygulamamanız hararetle önerilir**

Bu rehber anlatımında [Cryptsetup-team](https://cryptsetup-team.pages.debian.net/cryptsetup/encrypted-boot.html) rehberini esas almış ve testi Fedora 31 dağıtımında yapmıştır.

Öncelikle bilgisayarınızın kurulum aşamasında LUKS şifreleme ile kurulduğu varsayımı ile aşağıdaki komut ile sürücünüzün düzenine bakın.

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

Boot sektörünü şifrelemek için ilgili sektör silip tekrar yapılandırılacağı için öncelikle /boot altında olan dosyaların bir kopyasının alınması gerekmektedir. Sisteminizde bu rehber dahilinde yapacağınız pek çok işlem root yetkisi gerektrmektedir. Başlamak için;

/boot dizinini salt-okunur olarak mount edin.

`mount -oremount,ro /boot`

/boot dizinin yazılacağı boş bir tar dosyası oluşturun.

`install -m0600 /dev/null /tmp/boot.tar`

/boot dizinini oluşturduğunuz tar dosyasına kaydedin.

`tar -C /boot --acls --xattrs --one-file-system -cf /tmp/boot.tar .`

/boot dizinini unmount edin.

`umount /boot`

Eğer /boot/efi gibi alt noktalar var ise cihazınızda onları da unmount edin.

`umount /boot/efi`

Şayet `umount` komutu inat ederse `-l` parametresi ile çalıştırın.

/boot sektörünün olacağı cihazı LUKS1 ile şifreleyin.

```
cryptsetup luksFormat --type luks1 /dev/sda1

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











