# Libreboot ve GnuPG ile boot güvenliği

Libreboot, GnuPG ile birlikte bilgisayarınızı daha güvenli hale getirebilir. Bunun için öncelikle bir bilgisayarın nasıl çalıştığını ve açılmak için içinden geçtiği süreçlerin anlaşılması gereklidir.

Bir bilgisayar hayatına elektrik ile başladığında sırasıyla aşağıdaki adımlar gerçekleşir:

1. Libreboot, anakarttaki bir hafızadan RAM'e yüklenir ve çalışmaya başlar.
2. Libreboot, bir önyükleyici (bootloader) olan GRUB'ı yükler.
3. GRUB `/boot` dizininde bulunan ayar dosyasına bağlı olarak Linux'u yani çekirdeği yükler.
4. Çekirdek donanımları devreye alarak işletim sistemini yükler.
5. Bilgisayarınız açılır.

Bu sürecin güvenliği, her aşamanın kendinden sonraki aşamayı istenilen şekilde ve bilinen kaynaktan yüklenmesinin sağlanması ile mümkündür.

Libreboot, kendi dahilinde GRUB'ı çalıştırır. Bu bakımdan Libreboot kurulu bir cihazda kullanılabilecek biri depolama aygıtında, biri BIOS çipinde olmak üzere iki GRUB bulunur. Libreboot çalışma aşamasında BIOS çipinde bulunan GRUB'ı kullanarak sistemde bulunan GRUB'ı yükler.

GnuPG ile Libreboot'un GRUB'ın kurulumunu ve yüklenecek çekirdeklerin değiştirilmediğini doğrulaması için ayarlarda bir miktar değişiklik yapmak gerekmektedir.

## Bir GnuPG anahtarı oluşturun

GRUB, kriptografik olarak çekirdek ve ayar dosyalarını denetlemek için GnuPG kullanmaktadır. Şifreleme esnasında kullanılacak anahtarın kullanıcı tarafından üretilmesi gerekmektedir. Eğer halihazırda bir GnuPG anahtarınız yoksa, sadece bu amaçla kullanmak için veya genel olarak kullanılmak üzere bir GnuPG anahtarı üretebilirsiniz. Bunun için [GnuPG anahtar üretimi](/yazisma_guvenligi/gpg/gpg-anahtar-uretimi.md) rehberinden yararlanabilirsiniz.

Bu noktada, ihtiyaç ve beklentilerinize göre değerlendirmeniz gereken bir husus vardır. Eğer kişisel GnuPG anahtarınızı sürekli olarak kullanacaksanız, bu anahtarın bir noktada açığa çıkması veya kaybedilmesi tehlikesini de göze almanız gerekecektir. Aynı zamanda bu durum, siz farkında olmadan anahtarınız kullanılarak çekirdeklerin veya ayar dosyalarının sizin anahtarınızla imzalanabileceği anlamına da gelmektedir. Bu sebepten dolayı anahtarınızı bir [zarola](https://zarola.oyd.org.tr) ile korumanızı ve [kağıt bir yedeğini almanızı](../yazisma_guvenligi/gpg/paperbackup.md) şiddetle tavsiye ederiz.

GnuPG anahtarınızı oluşturduktan sonra sonraki aşamaya geçebilirsiniz.

## Gerekli yazılımları indirin

Libreboot imajında değişiklikler yapabilmek ve bu değişiklikleri BIOS çipine yükleyebilmek için bazı yazılımlara ihtiyaç vardır. [Libreboot'un arşivinden](https://www.mirrorservice.org/sites/libreboot.org/release/stable/20160907/) gerekli dosyaları indirebilir, indirilen dosyaların imzalarını GnuPG ile doğrulayabilirsiniz. İhtiyacınız olan `cbfstool` ve `flashrom` (dizinde flash adında) yazılımları indirdiğiniz arşivin dizininde bulunmaktadır.

Flashrom yazılımını dağıtımınızın paket depolarından da indirebilirsiniz.

APT paket yöneticisi kullanan dağıtımlarda (Debian, Mint, Ubuntu vb.):

`sudo apt-get update`

`sudo apt-get install flashrom`

Yum paket yöneticisi kullanan dağıtımlarda (Fedora, CentOS vb.):

`sudo yum install flashrom`

## Değiştirilecek Libreboot imajını elde edin

Bu noktada iki seçenek bulunmaktadır. Şayet cihazınızda halihazırda Libreboot yüklüyse, cihazınızın ROM'undan doğrudan imajı çekebilir ve üzerinde değişiklik yapabilirsiniz.

* Bunun için aşağıdaki komutu çalıştırabilirsiniz;

`sudo flashrom -p internal -r libreboot.rom`

ROM imajı **libreboot.rom** olarak bulunduğunuz dizine kaydolacaktır.

* Eğer ROM imajını indirip değişikliklerinizi yapmak isterseniz, Libreboot imajını [buradan](https://www.mirrorservice.org/sites/libreboot.org/release/stable/20160907/rom/grub/) indirebilirsiniz.

Çipin boyutunu öğrenmek için, `flashrom -p internal` komutunu çalıştırın. Aşağıdaki gibi bir çıktı elde etmeniz gerekmektedir:

> Found Macronix flash chip "MX25L6406E/MX25L6408E" (8192 kB, SPI) \
> mapped at physical address 0x00000000ff800000.

Yukarıdaki örnekte, çip boyutu 8 MB olarak görünmektedir.

Dilediğiniz arşiv yöneticisi ile cihazınıza uygun olan imajı çıkarabilirsiniz.

## ROM imajından grubtest.cfg dosyasını çıkarın

ROM imajında yapılacak değişiklikler için `cbfstool` yazılımını kullanabilirsiniz. Bunun için çıkardığınız `libreboot.rom` dosyasını `cbfstool`'un bulunduğu dizine koyun.

Uçbirimde `cbfstool` dizininde iken `./cbfstool libreboot.rom print` komutu ile ROM imajında bulunan dosyaları listeleyebilirsiniz. İmaj içinde `grub.cfg` ve `grubtest.cfg` adlı iki GRUB ayar dosyası görülecektir. `grub.cfg`, Libreboot'un temel kullandığı yapılandırma dosyasıdır. Öncelikle  `grubtest.cfg` dosyasını düzenleyerek bir deneme yapılandırması oluşturun. Böylece, yapılandırmadan memnun olduktan sonra `grub.cfg` dosyası ile test dosyasını değiştirip cihazınızı güvenli şekilde hazır hale getirebilirsiniz.

`cbfstool` dizininde `libreboot.rom`'un bulunduğundan emin olup, aşağıdaki komutu çalıştırarak `grubtest.cfg` dosyasını çıkarabilirsiniz.

`./cbfstool libreboot.rom extract -n grubtest.cfg -f grubtest.cfg`

## GRUB güvenliği için parola belirleyin

Bir saldırganın GnuPG doğrulamasını aşmak için yapması gereken tek şey, boot aşamasında GRUB'a doğrulama yapmamasını söylemektir. Bu bakımdan, Libreboot içinde çalışan GRUB'ın ayar değişiklikleri için parola talep etmesi güvenliğin anlamlı olabilmesi için şarttır.

Bunun için [Zarola](https://zarola.oyd.org.tr) yöntemini kullanmanızı şiddetle tavsiye ederiz. Çünkü bilgisayarınızın güvenliğinin ilk adımı bu parolanın güvenliğine bağlıdır.

Bunun için bir uçbirim açıp, `grub-mkpasswd-pbkdf2` komutunu çalıştırıp parolanızı girebilirsiniz. Çıktı şuna benzeyecektir:

```
grub.pbkdf2.sha512.10000.B08007ADC512E1BB058D62132F94A6EBF96E27511538F1F9ED59B3DE0556FA70A63F617C56D532C499D2E42AABF6B9F8F5EDAC604DC88567268A2D63DF0325F3.A9392DB618EE22AC423CB490B9809B08FB003FBA63B04F310DCD776335282B5D57134671248C711D9D60A7E9A220821B6701EB038F1368D87B66FC632B73801B
```

Seçtiğiniz metin editörü ile `grubtest.cfg` dosyasına, bir önceki adımda aldığınız parola özüt (hash) değerini aşağıdaki şekilde girin.

```
gfxpayload=keep
terminaloutput --append gfxterm

set superusers="root"
password_pbkdf2 root grub.pbkdf2.sha512.10000.B08007ADC512E1BB058D62132F94A6EBF96E27511538F1F9ED59B3DE0556FA70A63F617C56D532C499D2E42AABF6B9F8F5EDAC604DC88567268A2D63DF0325F3.A9392DB618EE22AC423CB490B9809B08FB003FBA63B04F310DCD776335282B5D57134671248C711D9D60A7E9A220821B6701EB038F1368D87B66FC632B73801B

#Default to first option, automatically boot after 1 seccond
```

Her açılışta GRUB'a parola girmemek için, standart yükleme seçeneğini parola gerektirmeyen bir şekilde ayarlamak yerinde olacaktır. GRUB, GnuPG ile kontrolleri yapacağı için bu işlem güvenlik açısından bir sorun teşkil etmeyecektir. Bunun için `--unrestricted` parametresini aşağıdaki gibi ekleyin.

`menuentry 'Load Operating System (incl. fully encrypted disks)  [o]' --hotkey='o' --unrestricted {`

Sabit diskinizde bulunan GRUB'ın GnuPG güvenliğini geçememesi için aşağıdaki gibi `unset superusers` satırının başına `#` koyarak devre dışı bırakılması gerekmektedir.

```
function try_user_config {
   set root="${1}"
   for dir in boot grub grub2 boot/grub boot/grub2; do
      for name in '' autoboot_ libreboot_ coreboot_; do
         if [ -f /"${dir}"/"${name}"grub.cfg ]; then
            #unset superusers
            configfile /"${dir}"/"${name}"grub.cfg
         fi
      done
   done
}
```

## Açık anahtarınızı hazırlayın

GRUB'ın kontrolleri yapacağı GnuPG anahtarınızın açık anahtarını (public key) uygun formatta kaydetmeniz gerekmektedir. Bunun için aşağıdaki komutu çalıştırın. Açık anahtarınız, `boot.key` ismiyle bulunduğunuz dizine kaydedilecektir. (_Birden fazla GnuPG anahtarınız varsa, `--export` parametresinden sonra anahtar ID'nizi ya da e-posta adresinizi girmeniz gerekmektedir._)

`gpg --export > boot.key`

## GRUB'ın imza kontrolünü açın

Libreboot GRUB'ın imzaları GnuPG anahtarınızla kontrol etmesi için aşağıdaki parametreyi `grubtest.cfg` yapılandırma dosyasında menü girdilerinden üste ekleyin.

```
trust (cbfsdisk)/boot.key
set check_signatures=enforce
```

## Çekirdek ve yapılandırma dosyalarını imzalayın

Libreboot'un kontrol etmesi gereken dosyalara kendi anahtarınızla imza atmanız gerekmektedir. İmzalanacak dosyalar aşağıdaki gibidir;

```
/boot/initramd veya initramfs
/boot/vmlinuz.*
/boot/grub/grub.cfg
```

Libreboot'a eklenecek;

`grubtest.cfg`

Dosyaları imzalamak için aşağıdaki komutu listedeki dosyalar için tek tek çalıştırın.

`gpg -u [anahtar ID veya e-postanız] --detach-sign [imzalanacak dosya]`

Her işlem sonrasında imzalanan dosyanın adı ile bir .sig dosyası oluşacaktır. Boot dizini altındaki dosyaları imzalamak için root yetkisine ihtiyacınız vardır. GnuPG'yi root yetkisi ile çalıştırdığınızda, anahtarınız root kullanıcısının anahtarlığında olmadığından ilgili anahtarın bulunamadığına dair bir hata alabilirsiniz. Bunun için çalıştırdığınız GnuPG komutlarına `--homedir /home/kullaniciadi/.gnupg` parametresini ekleyerek GnuPG'nin anahtarınızın bulunduğu dizinde çalışmasını sağlayabilirsiniz.

Her bir .sig dosyasını ilgili dosyanın yanına ekledikten sonra ROM'un hazırlanmasına ve yüklenmesine geçebilirsiniz.

## Libreboot ROM'una grubtest.cfg'nin yazılması

Aşağıdaki dosyaları `cbfstool` dizininin altına alın:

```
boot.key
grubtest.cfg
grubtest.cfg.sig
```

Daha sonra ROM'un içindeki eski dosyaların silinmesi gerekmektedir. Bunun için aşağıdaki komutları sırasıyla çalıştırın:

`./cbfstool libreboot.rom remove -n boot.key`

`./cbfstool libreboot.rom remove -n grubtest.cfg`

`./cbfstool libreboot.rom remove -n grubtest.cfg.sig`

Ardından yeni dosyalarımızın `libreboot.rom`'un içine eklenmesi gerekmektedir. Bunun için:

`./cbfstool libreboot.rom add -n boot.key -f boot.key -t raw`

`./cbfstool libreboot.rom add -n grubtest.cfg -f grubtest.cfg -t raw`

`./cbfstool libreboot.rom add -n grubtest.cfg.sig -f grubtest.cfg.sig -t raw`

Artık `libreboot.rom` dosyanız BIOS çipinize yazılmaya hazır.

## ROM'a libreboot.rom imajının yazılması

`libreboot.rom` dosyasını "flash" dosyasının bulunduğu dizine alın ve ardından aşağıdaki komutu çalıştırarak çipe imajı yazın.

`sudo ./flash update libreboot.rom`

Eğer doğru ROM imajını seçtiğinizden emin olmanıza rağmen uyumsuzluk hatası alıyorsanız yazım işlemini zorla yapabilirsiniz.  
**KESİNLİKLE GARANTİSİ YOKTUR, BİLGİSAYARINIZI KULLANILAMAZ HALE GETİREBİLİRSİNİZ.**

`sudo ./flash forceupdate libreboot.rom`

## Bilgisayarınızı yeniden başlatın ve denemenizi yapın

ROM yazıldıktan sonra, bilgisayarınızı yeniden başlatıp yaptığınız değişikliklerin çalışıp çalışmadığını deneyebilirsiniz. Ekranınız açılır açılmaz birkaç kere boşluk tuşuna basıp, gelen GRUB ekranında `Load test configuration (grubtest.cfg) inside of CBFS` seçeneğini seçin. Gelen ekrandan bilgisayarınızı başlattığınızda sorunsuz şekilde çalışıyorsa her şey yolunda demektir.

Herhangi bir şey yanlışsa ve cihazınız açılmazsa, bilgisayarınızı kapatıp yeniden açtığınızda olağan yapılandırmanız ile açılacaktır, panik yapmayın.

Eğer imza sisteminin çalışıp çalışmadığını denemek isterseniz, kasıtlı olarak imzalı dosyalarını silip `grubtest.cfg` ile bilgisayarınızı başlatmaya çalışırsanız hata almanız lazımdır. Bu şekilde yapılandırmanızın doğru olduğunu ve imzaları denetlediğini görebilirsiniz.

## Yapılandırmanızı kalıcı hale getirin

Eğer `grubtest.cfg` yapılandırmasından memnun kaldıysanız, `grubtest.cfg` dosyasını `grub.cfg` olarak adlandırıp 7. adımdan itibaren işlemleri tekrarladığınızda, bilgisayarınız Libreboot ve GRUB'ın GnuPG denetimi altında açılacaktır.

**Çekirdek veya GRUB yapılandırmalarınıza güncelleme geldiği durumlarda imzaları yenilemeyi ihmal etmeyin, aksi takdirde bilgisayarınız açılmaz.**

## İmzalama işlemini otomatikleştirmek

Güncellemeler, kurulumunuza bağlı olarak kendiliğinden ve sessizce gerçekleşebilmektedir. Bu durum, güncellenen çekirdek ve GRUB yapılandırma dosyası imzalanmayacağı için, Libreboot'un bir sonraki açılışta cihazınızı çalıştırmayı reddetmesi ile sonuçlanabilir. Bu durumda Libreboot'u, parolasını girerek, imza kontrolü olmadan çalıştırabilirsiniz. Ancak gereksiz paniğe yol açmamak adına, işletim sisteminizin çekirdeğinizi her güncellediğinde imzalarını da yenilemesini sağlayabilirsiniz. Bunun için küçük bir betiğe ihtiyacınız vardır. Bu betiğin olduğu gibi çalışabilmesi için özel anahtarınızı (private key) root kullanıcısının anahtarlığına koyabilir (`gpg --import ile`) ya da betiğin içerisinde `gpg` ile başlayan tüm komutların sonuna `--homedir /home/kullaniciadiniz/.gnupg` parametresini ekleyebilirsiniz.

[grub2-signing-extension](https://github.com/Bandie/grub2-signing-extension/blob/master/sbin/grub-update-kernel-signature) betiğini bağlantıdan indirebilir veya aşağıdan kopyalayabilirsiniz.

```
#!/bin/bash
#grub2-update-kernel-signature
#Renews the signature in /boot/.
#Author: Bandie
#Licence: GNU-GPLv3

function sign(){
  for f in `find /boot -maxdepth 1 -type f`
  do
    if gpg --detach-sign $f
    then
      echo $f signed.
    else
      return 1
    fi
  done
  if gpg --detach-sign "/boot/grub/grub.cfg"
  then
    echo /boot/grub/grub.cfg signed.
  else
    return 1
  fi
  return 0
}


rm /boot/*.sig
rm /boot/grub/grub.cfg.sig

if ! sign
then
  sign
fi
```

Betiği aşağıdaki dizine **zz-update-signatures** adıyla kaydedin:

**Dizindeki betikler isimlerine göre sırayla çağrıldıklarından betiğinizin alfabetik olarak sonda yer alması gerekiyor.**

`/etc/kernelpostinst.d/`

Ardından dosyaya çalıştırma izni verin:

`sudo chmod +x zz-update-signatures`

Bu aşamanın ardından, her çekirdek güncellemesinde ilgili betik çalışarak imzaların varlığını kontrol edecek, imza yoksa `/boot` dizinindeki her dosyayı imzalayacak ve ardından GRUB yapılandırmasını imzalayacaktır. Bu aşamada cihazınız sizden GnuPG anahtarınızın parolasını isteyecektir.

## Ek Okumalar

<https://libreboot.org/docs/gnulinux/grub_hardening.html>

<https://github.com/Bandie/grub2-signing-extension>

<https://www.crowdstrike.com/blog/enhancing-secure-boot-chain-on-fedora-29/>

<https://www.gnu.org/software/grub/manual/grub/html_node/Using-digital-signatures.html>
