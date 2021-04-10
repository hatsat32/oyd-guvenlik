# Parmak izi ile Login Güvenliği

Parmak izi, yetkilendirme için en yaygın kullanılan girdilerden biridir. Biyometrik verilerin yetkilendirme için kullanımı hem kişilerden görece ayrılmaz bir öğeyi kullanarak kişilerin fiziki varlığını garanti etmekte hem de neredeyse her bireye özel bir veriyi kullanarak kişiye güvenlik sağlamaktadır. Biyometrik verilerin kanuni kullanım sınırları bir yana bırakıldığında, bu özellikler diğer ikinci faktör araçlarına göre parmak izi kullanımını özellikle ön plana çıkartmaktadır.

Ancak parmak izi seçenekler arasındaki en güvenli tercih sayılmaz. Bu bakımdan:

* Parmak izi değiştirilemez. Haliyle bu verinin güvenliğini sağlamak özellikle önem kazanır.
* Parmak izi insanların her yere bıraktığı bir şey olması hasebiyle görece kolaylıkla elde edilebilir bir bilgidir.
* Parmak izi tarama sistemleri aldatılmaya açıktır. Her ne kadar gelişmiş donanımlar bunu zorlaştırsa da imkansız kılmamaktadır.
* Parmak izi taramaları kişiyi tanımlamakta hata yapabilir. Özellikle yaralanmalar gibi fiziki değişiklikler taramayı imkansız kılabilir.

Bu sebeplerden ötürü parmak izini üçüncü faktör olarak veya sadece kişilerin fiziki varlığını kanıtlamak için zayıf bir kanıt olarak kullanmakta yarar vardır. Halihazırda sadece parola ile korunan bir sisteme parmak izi doğrulaması eklenmesi bir miktar daha güvenlik sağlayacaktır. Özellikle dahili parmak izi tarayıcısı olan cihazlarda bunu yapmanın maliyeti neredeyse sıfır olduğundan değerlendirilebilir bir seçenek olarak ortaya çıkabilir.

**EĞER TEHDİT MODELİNİZDE ALIKONULMA İHTİMALİ VARSA NE OLURSA OLSUN PARMAK İZİ DOĞRULAMASI KULLANMAYIN.** 

## Kurulum

Öncelikle bilgisayarınıza  `fprintd` paketini kurmanız gerekiyor. Bunun için aşağıdaki komutları sırayla çalıştırabilirsiniz:

Debian tabanlı (Ubuntu, Mint vb.) sistemlerde: `sudo apt-get install fprintd`

Red Hat tabanlı (Fedora vb.) sistemlerde: `sudo yum install fprintd`

Kurulumun ardından fprintd ve dahili PAM modülü bilgisayarınıza kurulmuş olacak. Parmak izi taramasına başlamak için aşağıdaki komutu girin.

`fprintd-enroll -f [ Parmak adı ]`

fprintd'ye hangi parmağınızı taradığınızı belirtmeniz gerekmektedir. Bu sayede, size tarama sırasında hangi parmağınızı sorduğunu bilebilirsiniz. Tavsiyemiz, olası bir aksilik durumunda kullanımınızı etkilememek için her iki elinizde bulunan ikişer parmağı tanıtmanız yönünde olacaktır. Geçerli parmak isimleri şunlardır:

|Komut|Parmak adı|
|-----|----------|
|left-thumb	|Sol baş parmak|
|left-index-finger|Sol işaret parmağı|
|left-middle-finger|Sol orta parmak|
|left-ring-finger|Sol yüzük parmağı|
|left-little-finger|Sol serçe parmak|
|right-thumb	|Sağ başparmak|
|right-index-finger|Sağ işaret parmağı|
|right-middle-finger|Sağ orta parmak|
|right-ring-finger|Sağ yüzük parmağı|
|right-little-finger|Sağ serçe parmak|

Sol serçe parmağınızı tanıtmak için örnek komut:

`fprintd-enroll -f left-little-finger`

Daha sonra parmağınızı 4 kere tarayıcıdan geçirmeniz istenecek ve başarılı olması halinde ekleme işlemi tamamlanacaktır.

```
Using device /net/reactivated/Fprint/Device/0
Enrolling left-little-finger finger.
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-completed
```

İşlemin başarısını test etmek için aşağıdaki komutu çalıştırıp parmağınızı okutabilirsiniz.

`fprintd-verify -f left-little-finger`

Kayıtlı parmak izleriniz listelenecek ve belirttiğiniz parmağı okutmanız üzerine onay alacaksınız.

```
Using device /net/reactivated/Fprint/Device/0
Listing enrolled fingers:
 - #0: left-little-finger
Verify result: verify-match (done)
```
## PAM ayarları

[PAM](https://en.wikipedia.org/wiki/Linux_PAM), GNU/Linux sistemlerde kullanıcı yetkilendirmesinden sorumlu olan yazılımdır. `/etc/pam.d` dizini altında bulunan yapılandırma dosyaları ile PAM davranışları şekillendirilebilir. Bu rehber PAM detaylarına girmek üzere yazılmadığından dolayı bir sistemdeki olası en güvenli kullanımı önerecektir. Arzu ederseniz, PAM ayarlarını ihtiyacınıza göre istediğiz gibi şekillendirebilirsiniz. 

Cihazınızın PAM kontrolündeki tüm login işlemlerine parmak izi doğrulamasını eklemek için aşağıdaki dosyayı tercih ettiğiniz bir metin editörü ile açın. Aşağıdaki komutta `nano` editörü kullanılmıştır.

**Birazdan açacağınız sudo yetkisi vereceğiniz uçbirimi kapatmayın!!!**

`sudo nano /etc/pam.d/common-auth`

Karşınıza aşağıdakine benzer bir metin çıkacaktır.

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
#auth    optional                        pam_exec.so /home/alper/wrongpasspic.sh
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional                        pam_cap.so
# end of pam-auth-update config
```

Dosyanın sonuna aşağıdaki satırı ekleyin ve `Ctrl + X` kısayolu ile dosyayı kaydedip çıkın.

`auth    required   pam_fprintd.so`

**Şayet bu aşamada bir sorun varsa ve ekran kilidinizi devreye alırsanız cihazınıza tekrar giremeyebilirsiniz!!**

Bu noktadan sonra cihazınızdaki tüm yetkilendirme gereken işlemlerde sizden parmak iziniz istenecektir. Her şeyin yolunda olduğundan emin olmak ve bir sorun varsa zahmetsizce düzeltmek için **yukarıdaki tavsiyeye bağlı olarak açık tuttuğunuz sudo yetkili uçbirimden** başka bir uçbirim açarak aşağıdaki komutu girin.

`sudo ls ~`

Sudo yetkilendirmesi için sizden parola ve ardından parmak izi istenmesi gerekir. Şayet bu gerçekleşmediyse veya ev dizininin altındaki dosyalar başarılı bir şekilde listelenmediyse geri dönüp adımlarda bir hata yapıp yapmadığınızı kontrol edin. Şayet bir sorunla karşılaşırsanız sudo yetkili uçbirimden `/etc/pam.d/common-auth` dosyasında yaptığınız değişiklikleri geri alıp kaydederek cihazınızın kilitlenmesini engelleyebilirsiniz.

Şayet testi başarılı şekilde geçtiyseniz artık parmak iziniz ile birlikte cihazınızı biraz daha güvenli şekilde kullanmaya başlayabilirsiniz.

## Diğer kullanıcılar

Eğer cihazda birden fazla kullanıcı varsa ve sadece bir kullanıcı parmak izi kullanacaksa `/etc/pam.d/common-auth` yapılandırmasındaki değişikliği aşağıdakiyle değiştirerek sadece parmak izi kurulumu yapmış kullanıcıların ikinci faktöre ihtiyaç duymasını sağlayabilirsiniz.

**Bu durum root kullanıcısının 2FA dışında kalmasına sebep olacağından gerekmedikçe önerilmez.**

`auth required pam_fprintd.so nullok`

Şayet root kullanıcısının da girişini parmak iziyle yapmak isterseniz yukarıdaki adımları root kullanıcısıyla tekrar etmeniz gereklidir.
