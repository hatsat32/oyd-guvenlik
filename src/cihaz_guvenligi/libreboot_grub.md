# Libreboot ve GPG ile boot güvenliği

Libreboot GPG ile birlikte bilgisayarınızı daha güvenlli hale getirebilir. Bunun için öncelikle bir bilgisayarın nasıl çalıştığını ve açılmak için içinden geçtiği süreçlerin anlaşılması gereklidir.

Bir bilgisayar hayatına elektrik ile başladığında şunlar sıra ile gerçekleşir;

..
Anakarttaki bir hafızadan Libreboot(nedir?) RAM'e yüklenir ve çalışmaya başlar.
Libreboot bir bootloader olan GRUB'ı yükler
GRUB /boot sektöründe bulunan ayar dosyasına bağlı olarak Linux'u yani çekirdeği yükler
Çekirdek donanımları devreye alarak işletim sistemini yükler.
Bilgisayarınız açılır.

Bu sürecin güvenliği her aşamanın bir sonraki aşamanın istenilen şekilde ve bilinen kaynaktan yüklenmesinin sağlanması ile mümkündür.

...

Libreboot kendi dahilinde GRUB çalıştırır. Bu bakımdan Libreboot kurulu bir cihazda kullanılabilecek biri depolama aygıtında, biri bios çipinde olmak üzere iki GRUB bulunur. Libreboot çalışma aşamasında bios çipinde bulunan GRUB ile sistemde bulunan GRUB'ı yükler.

GPG ile Libreboot'un GRUB'ın kurulumunu ve yüklenecek çekirdeklerin değiştirilmediğini doğrulaması için ayarlarda bir miktar değişiklik yapmak gerekli.


## Bir GPG anahtarı edinin

Grub kriptografik olarak çekirdek ve ayar dosyalarını denetlemek için GPG kullanmakta ve kullanılacak anahtarı sizin üretmeniz gerekmekte. Şayet halihazırda bir GPG anahtarınız yok ise sadece bu amaçla veya genel olarak kullanılmak üzere bir GPG anahtarı üretebilirsiniz. Bunun için [GPG rehberinden](/yazisma_guvenligi/gpg/gpg-anahtar-uretimi.md) yararlanabilirsiniz.

Bu noktada ihtiyaç ve beklentilerinize göre değerlendirmeniz gereken bir husus bulunmakta. Şayet kişisel GPG anahtarınızı sürekli olarak kullanacaksanız bu anahtarın bir noktada açığa çıkması veya kaybedilmesi tehlikesini de göze alıyor olacaksınız. Aynı zamanda anahtarınız cihazlarınızda ve belki başka cihazlarda tarafınızdan kullanılabileceği üzere bir noktada arzunuza aykırı olarak ayar dosyası veya çekirdek imzalamakta kullanılabilir siz bunu fark etmeden.

Şayet boot güvenliğiniz için bu risk fazla ise sadece Libreboot ile kullanılmak üzere bir anahtar oluşturup bunu güvenli şekilde saklayabilirsiniz ve sadece gerektiğinde kullanabilirsiniz. Elbette bu durum az kullanılan anahtarı kaybetmeniz, parolasını unutmanız tehlikesini de göz önüne almanız gerekli. Hiç değilse elinizin altında olmayışının can sıkıcılığına da göğüs germeniz gerekebilir.

Kullanmak konusunda karar verdiğiniz bir GPG anahtarınız olduktan sonra sonraki aşamaya geçebilrsiniz.


## Gerekli yazılımları indirin

Libreboot imajında değişiklikler yapabilmek ve bu değişiklikleri bios çipine yükleyebilmek için gerkeli yazılımları indirmelisiniz. [Libreboot'un arşisinden](https://www.mirrorservice.org/sites/libreboot.org/release/stable/20160907/) gerekli dosyaları indirebilir imzasını GPG ile doğrulayabilirsiniz. İhtiyacınız olan cbfstool ve flashrom (dizinde flash adında) yazılımları indirdiğiniz arşivin dizininde bulunacak.

Flashrom yazılımını dağıtımınızın reposunda da bulabilirsiniz.

Debian Dağıtımlarda:

`sudo apt-get update`

`sudo apt-get install flashrom`

Yum yönetici kullanan dağıtımlarda (Fedora, Centos)

`sudo yum install flashrom`


## Değiştirilecek Libreboot imajını elde edin.

Bu noktada iki seçeneğiniz bulunuyor. Şayet cihazınızda halihazırda Libreboot yüklü ise cihazınızın ROM'undan doğrudan imajı alabilir ve üzerinde değişiklik yapabilirsiniz.

* Bunun için aşağıdaki komutu çalıştırabilirsiniz;

`sudo flashrom -p internal -r ~/libreboot.rom`

ROM imajı **libreboot.rom** olarak belirttiğiniz dizine kaydolacaktır.

* Şayet ROM imajını indirip değişikliklerinizi yapmak isterseniz;

[Libreboot imajını indirin](https://www.mirrorservice.org/sites/libreboot.org/release/stable/20160907/rom/grub/)

Çip boyutunu öğrenmek için `flashrom -p internal` komutunu kullandığınızda size aşağıdaki gibi bir sonuç döndürecektir.

> Found Macronix flash chip "MX25L6406E/MX25L6408E" (8192 kB, SPI) \
> mapped at physical address 0x00000000ff800000.

Yukarıdaki örnekte çip boyutu 8mb görünmektedir.

Dilediğiniz arşiv yöneticisi ile cihazınıza uygun olan imajı çıkarabilirsiniz.


## ROM imajından grubtest.cfg dosyasını çıkarın.

ROM imajında yapılacak değişiklikler için cbfstool yazılımı kullanılmakta. Bunun için çıkardığınız libreboot.rom dosyasını cbfstool'un bulunduğu dizine ekleyin.

Terminalde cbfstool dizininde iken `./cbfstool libreboot.rom print` komutu ile ROM imajında bulunan dosyaları listeleyebilirsiniz. İmaj içinde grub.cfg ve grubtest.cfg adlı iki grub ayar dosyası görülecektir. grub.cfg Libreboot'un temel kullandığı yapılandırma dosyası olmakla öncelikle denemek amacı ile grubtest.cfg dosyası ile deneme yapmak önemlidir. Böylece yapılandırmadan memnun olduktan sonra grub.cfg dosyası ile test dosyasını değiştirip cihazınızı güvenli şekilde hazır hale getirebilirsiniz.

cbfstool dizininde libreboot.rom'un bulunduğundan emin olup aşağıdaki komutu çalıştırarak grubtest.cfg dosyasını çıkarabilirsiniz.

`./cbfstool libreboot.rom extract -n grubtest.cfg -f grubtest.cfg`


## GRUB Güvenliği için Parola belirleyin.

Bir saldırganın GPG doğrulamasını aşmak için yapması gereken tek şey boot aşamasında GRUB'a doğrulama yapmamasını söylemek. Bu bakımdan Libreboot içinde çalışan GRUB'ın ayar değişiklikleri için parola talep etmesi güvenliğin anlamlı olabilmesi için şart.

Bunun için [Zarola](zarola.oyd.org.tr) yöntemini kullanmanızı hararetle tavsiye ederiz. Keza bilgisayarınızın güvenliğinin ilk adımı bu parolanın güvenliğine bağlı.

Bunun için bir terminalde `grub-mkpasswd-pbkdf2` komutunu çalıştırıp parolanızı girin. Çıktı şuna benzeyecektir;

`grub.pbkdf2.sha512.10000.HEXDIGITS.MOREHEXDIGITS`

grubtest.cfg dosyasını seçtiğiniz düzenleyici ile terminalden aldığınız parola özüt değerini aşağıdaki şekilde girin.

```
gfxpayload=keep
terminaloutput --append gfxterm

set superusers="root"
password_pbkdf2 root grub.pbkdf2.sha512.10000.HEXDIGITS.MOREHEXDIGITS


#Default to first option, automatically boot after 1 seccond
```

Her açılışta GRUB'a parola girmemek için standart yükleme seçeneğini paroladan ari kılmak yerinde olacaktır. GRUB GPG ile kontrolleri yapacağı için bu güvenlik açısından bir sorun teşkil etmeyecektir. Bunun için `--unrestricted` parametresini aşağıdaki gibi ekleyin.

`menuentry 'Load Operating System (incl. fully encrypted disks)  [o]' --hotkey='o' --unrestricted {`

Harddiskte bulunan GRUB'ın GPG güvenliğini geçememesi için alağıdaki gibi unset superusers satırının başına "#" koyarak devredışı bırakılması gerekiyor.

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

GRUB'ın kontrolleri yapacağı size ait GPG anahtarının açık anahtarının uygun formatta kaydetmeniz gerekli. Bunun için aşağıdaki komutu çalıştırın. boot.key sizin açık anahtarınız olarak dizine kaydedilecektir.

`gpg --export > boot.key`


## GRUB'ın imza kontrolünü açın

Libreboot GRUB'ın GPG anahtarınız ile imza kontrol etmesi için aşağıdaki parametreyi grubtest.cfg yapılandırma dosyasına menü girdilerinden üste koyun.

```
trust (cbfsdisk)/boot.key
set check_signatures=enforce
```

## Çekirdek ve yapılandırma dosyalarını imzalayın

Libreboot'un kontrol etmesi gereken dosyalara anahtarınız ile imza atmanız gerekmektedir. İmzalanacak dosyalar aşağıdaki gibidir;

```
/boot/initramd veya initramfs
/boot/vmlinuz.*
/boot/grub/grub.cfg
```

Libreboot'a eklenecek;

`grubtest.cfg`

Dosyaları imzalamak için aşağıdaki komutu listedeki dosyalar için tek tek çalıştırın.

`gpg -u [anahtar ID veya e-postanız] --detach-sign [imzalanacak dosya]`

Her işlem sonrasında imzalanan dosyanın adı ile bir .sig dosyası oluşacaktır. Boot dizini altındaki dosyaları imzalamak için root yetkisine ihtiyacınız var. GPG'yi root yetkisi ile çalıştırdığınızda anahtarınız root kullanıcısında olmadığından anahtar bulunamadığına dair hata alabilirsiniz. Bunun için en kolay yol anahtarınısı root kullanıcısına da import edip işlemlerinizi bu şekilde yapmanız olabilir. **bu kötü bir yöntem başka çıkarı yok mu**?

her .sig dosyasını ilgili dosyanın yanına ekledikten sonra ROM'un hazırlanmasına ve yüklenmesine geçilebilir.


## Libreboot ROM'una grubtest.cfg'nin yazılması

Aşağıdaki dosyaları cbftool dizininin altına alın:

```
boot.key
grubtest.cfg
grubtest.cfg.sig
```

Daha sonra ROM içindeki eski dosyaların silinmesi gerekiyor. Bunun için aşağıdaki komutu sırası ile çalıştırın.

`./cbfstool libreboot.rom remove -n boot.key`

`./cbfstool libreboot.rom remove -n grubtest.cfg`

`./cbfstool libreboot.rom remove -n grubtest.cfg.sig`

Ardından yeni dosyalarımızı Libreboot.rom'un içine eklenmesi gerekiyor.

`./cbfstool libreboot.rom add -n boot.key -f boot.key -t raw`

`./cbfstool libreboot.rom add -n grubtest.cfg -f grubtest.cfg -t raw`

`./cbfstool libreboot.rom add -n grubtest.cfg.sig -f grubtest.cfg.sig -t raw`

Artık libreboot.rom dosyanız bios çipinize yazılmaya hazır.


## ROM'a libreboot.rom imajının yazılması

libreboot.rom dosyasını "flash" dosyasının bulunduğu dizine alın ve ardından aşağıdaki komutu çalıştırarak çipe imajı yazın.

`sudo ./flash update libreboot.rom`

Şayet doğru ROM imajını seçtiğinizden emin olmanıza rağmen uyumsuzluk hatası alıyorsanız yazım işlemini zorla yapabilirsiniz. **kullandığınız ROM imajının doğrul olduğundan emin olun**

`sudo ./flash forceupdate libreboot.rom`


## Bilgisayarınızı yeniden başlatın ve denemenizi yapın

ROM yazıldıktan sonra bilgisayarınızı yeniden başlatıp yaptığınız değişikliklerin çalışıp çalışmadığını deneyebilirsiniz. Ekranınız açılır açılmaz birkaç kere boşluk tuşuna basıp gelen GRUB ekranında ` Load test configuration (grubtest.cfg) inside of CBFS` seçeneğini seçin. Gelen ekrandan bilgisayarınızı başlattığınızda sorunsuz şekilde çalışıyorsa her şey yolunda demektir.

Herhangi bir şey yanlış ise ve cihazınız açılmaz ise. Bilgisayarınızı kapatıp yeniden açtığınızda olağan yapılandırmanız ile açılacaktır.

Eğer imza sisteminin çalışıp çalışmadığını denemek isterseni. Kasıtlı olarak imzalı dosyaların imzalarını kaldırıp grubtest.cfg ile bilgisayarınızı başlatırsanız hata almanız gerekir. Bu şekilde yapılandırmanızın doğru ve imza denetlediğini görebilirsiniz.


## Yapılandırmanızı kalıcı hale getirin.

Şayet grubtest.cfg yapılandırmasından memnun kaldıysanız. grubtest.cfg dosyasını grub.cfg olarak adandırıp 7. adımdan itibaren işlemleri tekrarlayın. Bundan sonra bilgisayarınız libreboot ve GRUB'ın GPG denetimi altında açılacaktır.

**Çekirdek veya GRUB yapılandırmalarınıza güncelleme geldiği durumlarda imzaları yenilemeyi ihmal etmeyin**


## İmzalama işlemini otomatik kılın.

Güncellemeler size pek belli etmeden gerçekleşebilir kurulumunuza bağlı olarak. Bu durumlarda güncellenen çekirdek ve grub yapılandırma dosyası libreboot'un bir sonraki açılışta cihazınızı çalıştırmayı reddetmesi ile sonuçlanabilir. Bu durumda libreboot'u imza kontrolü olmadan çalıştırabilirsiniz parolasını girerek lakin gereksiz paniğe yol açmamak adına işletim sisteminizin çekirdeğinizi her güncellediği esnada imzalarını da yenilemesini sağlayabilirsiniz. Bunun için aşağıdakiler gereklidir;

* Çalışan sisteminizde imzalama için kullandığınız GPG anahtarınızın bir kopyasının root kullanıcısında bulunması

* Küçük bir betiği ilgili dizine koymanız

[Grub2-signing-extention](https://github.com/Bandie/grub2-signing-extension/blob/master/sbin/grub-update-kernel-signature) betiğini indirebilir veya aşağıdaki şeklinden kopyalayabilirsiniz.

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

**Dizindeki betikler isimlerine göre sıra ile çağrıldıklarından betiğinizin alfabeye göre sonda yer alması gerekiyor.**

`/etc/kernelpostinst.d/`

Ardından çalıştırılabilir yapın:

`sudo chmod +x zz-update-signatures`

Bu aşamanın ardından her çekirdek güncellemesinde ilgili betik çalışarak imzaların varlığını kontrol edecek, imza yok ise /boot dizinindeki her dosyayı imzalayacak ve ardından grub yapılandırmasını imzalayacaktır. Bu aşamada cihazınız sizden GPG anahtarınızın parolasını isteyecektir.


## Ek Okumalar

https://libreboot.org/docs/gnulinux/grub_hardening.html

https://github.com/Bandie/grub2-signing-extension

https://www.crowdstrike.com/blog/enhancing-secure-boot-chain-on-fedora-29/

https://www.gnu.org/software/grub/manual/grub/html_node/Using-digital-signatures.html

