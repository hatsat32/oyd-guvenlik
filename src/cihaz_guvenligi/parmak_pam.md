# parmakizi ile Login Güvenliği

parmakizi yetkilendirme için yaygınca kullanılan bir girdi. Biyometrik verilerin yetkilendirme kullanımı hem kişilerden görece ayrılmaz bir öğeyi kullanarak kişilerin fiziki varlığını garanti etmekte hem de neredeyse kişiye her bireye özel bir veriyi kullanarak güvenlik sağlamakta. Biyometrik verilerin kanuni kullanım sınırları bir yana bırakıldığında sayılan özellikleri diğer ikinci faktör araçlarından kullanımını özellikle arzulanır kılmakta.

Lakin parmakizi seçenekler arasındaki en güvenli tercih sayılmaz. Bu bakımdan:

* parmakizi değiştirilemez. Hali ile bu verinin güvenliğini sağlamak özellikle önem kazanır.

* parmakizi insanların her yere bıraktığı bir şey olmakla görece kolaylıkla elde edilebilir bir bilgidir.

* parmakizi tarama sistemleri aldatılmaya açıktır. Her ne kadar gelişmiş donanımlar bunu zorlaştırsa da imkansız kılmamaktadır.

* parmakizi taramaları kişiyi tanımlamakta hata yapabilir. Özellikle yaralanmalar gibi fiziki değişiklikler taramayı imkansız kılabilir.

Bu sebeplerden ötürü parmakizi üçüncü faktör olarak veya kişilerin fiziki varlığını kanıtlamak için zayıf bir kanıt olarak kullanılabilir. Her halde sadece parola ile korunan bir sisteme parmakizi eklenmesi bir miktar güvenlik sağlayacaktır. Özellikle dahili parmakizi tarayıcısı olan cihazlarda bunu yapmanın maliyeti neredeyse sıfır olduğundan değerlendirilebilir bir seçenek olarak ortaya çıkabilir.

## Kurulum

Öncelikle bilgisayarınıza  `fprintd` paketini kurmanız gerekli. Bunun için aşağıdaki komutları çalıştırın.

Debian sistemlerde: `sudo apt-get install fprintd`

RPM tabanlı sistemlerde: `sudo yum install fprintd`

Kurulumun ardından fprintd ve dahili PAM modülü bilgisayarınıza kurulmuş olacak. parmakizi taramasına başlamak için aşağıdaki komutu girin.

`fprintd-enroll -f [ Parmak adı ]`

fprintd'ye hangi parmağınızı taradığınızı belirtmeniz gerekli. Bu sayede size tarama sırasında hangi parmağınızı sorduğunu bilebilirsiniz. Tavsiye olarak her iki elinizde ikişer parmağı tanıtmanız aksi bir durumda kullanımınızı etkilememek için yeterli olacaktır. `-f` paramtersi ardından parmak adını aşağıdaki şekilde girebilirsiniz.

left-thumb		: Sol baş parmak
left-index-finger	: Sol işaret parmağı
left-middle-finger	: Sol orta parmak
left-ring-finger	: Sol yüzük parmağı
left-little-finger	: Sol serçe parmak
right-thumb		: Sağ başparmak
right-index-finger	: Sağ işaret parmağı
right-middle-finger	: Sağ orta parmak
right-ring-finger	: Sağ yüzük parmağı
right-little-finger	: Sağ serçe parmak

Sol serçe parmağınızı tanıtmak için örnek olarak:

`fprintd-enroll -f left-little-finger`

Sizden parmağınızı 4 kere tarayıcıdan geçirmeniz istenecek ve başarılı olması halinde ekleme işlemi tamamlanacaktır.

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

[PAM](https://en.wikipedia.org/wiki/Linux_PAM) GNU/Linux cihazlarda kullanıcı yetkilendirmesinden sorumlu olan yazılımdır. `/etc/pam.d` dizini altında bulunan ayar dosyaları ile PAM davranışları şekillendirilebilir. Bu rehber PAM detaylarına girmek üzere yazılmadığından bir sistemdeki olası en güvenli kullanımı önerecektir. Fakat GA ve PAM ayarlarını ihtiyacınıza göre istediğiz gibi şekillendirebilirsiniz. Buna parola olmadan sadece GA kodu ile cihazınıza giriş yapmaktan, su/sudo gibi özel login tiplerine sınırlama getirmek şeklinde çeşitlendirmek mümkün.

Cihazınızdaki tüm PAM kontrolündeki login işlemlerine GA kodunu uygulamak için aşağıdaki dosyayı tercih ettiğiniz bir metin editörü ile açın. Aşağıdaki komutta `nano` editörü kullanılmıştır.

** Birazdan açacağınız sudo yetkisi vereceğiniz uçbirimi kapatmayın!!! **

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

Dosyanın sonuna aşağıdaki satırı ekleyin ve `ctrl + x` komutu ile kaydedip çıkın.

`auth    required   pam_fprintd.so`

** Şayet bu aşamada bir sorun var ve ekran kilidinizi devreye alırsanız cihazınıza tekrar giremeyebilirsiniz!! **

Bu noktadan sonra cihazınızdaki tüm yetkilendirme gereken işlemlerde sizden parmakiziniz istenecektir. Her şeyin yolunda olduğundan emin olmak ve bir sorun varsa zahmetsizde düzeltmek için ** yukarıdaki tavsiyeye bağlı olarak açık tuttuğunuz sudo yetkili uçbirimden ** başka bir uç birim açarak aşağıdaki komutu girin.

`sudo echo test`

sudo yetkilendirmesi için sizden parola ve ardından parmakizi sorulması gerekli. Şayet bu gerçekleşmedi veya `test` yazısı başarılı şekilde yazılmadı ise ayarlarınızda bir terslik var demek olacağından geri dönüp adımlarda bir hata yapıp yapmadığınızı kontrol etmelisiniz. Şayet bir sorunla karşılaşırsanız sudo yetkili uçbirimden `/etc/pam.d/common-auth` dosyasında yaptığınız değişiklikleri geri alıp kaydederek cihazınızın erişiminiz dışına kitlenmesini engelleyebilirsiniz.

Şayet test'i başarılı şekilde geçti iseniz artık parmakiziniz ile birlikte cihazınızı biraz daha güvenli şekilde kullanmaya başlayabilirsiniz.

## Diğer kullanıcılar

Eğer cihazda birden fazla kullanıcı var ve sadece bir kullanıcı parmakizi kullanacak ise `/etc/pam.d/common-auth` yapılandırmasındaki değişikliği aşağıdaki ile değiştirerek sadece parmakizi kurulumu yapmış kullanıcıların ikinci faktöre ihtiyaç duymasını sağlayabilirsiniz.

** Bu durum root kullanıcısının 2FA dışında kalmasına sebep olacağından gerekmedikçe önerilmez. **

`auth required pam_google_authenticator.so nullok`

Şayet root kullanıcısının da girişini parmakizi ile kullanmak isterseniz yukarıdaki adımları root kullanıcı ile tekrar etmeniz gereklidir.
