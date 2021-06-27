# Google-Authenticator ile Login Güvenliği

Google-authenticator(GA) GNU/Linux cihazlarda login ekranlarında parola ile birlikte [ikinci faktör olarak (2FA)](../beseri_guvenlik/2fa.md) akıllı cihazlardan alınacak bir kodu sunarak giriş yapılmasına imkan veren bir yazılım. GA kullanarak cihazlarınıza erişimi daha kontrollü ve güvenli hale getirmek mümkün.

## Kurulum

Öncelikle bilgisayarınıza google-authenticator ve PAM modülünü kurmanız gerekiyor. Bunun için aşağıdaki komutları çalıştırın.

Debian sistemlerde: `sudo apt-get install google-authenticator libpam-google-authenticator`

RPM tabanlı sistemlerde: `sudo yum install google-authenticator libpam-google-authenticator`

Kurulumun tamamlanmasının ardından GA'nın ayarlarını yaparak cihazınızda bir anahtar oluşturmak bunu kullandığınız mobil cihazdaki bir OTP yazılımına aktarmak için aşağıdaki komutu uçbirimde çalıştırın.

`google-authenticator`

Komutu çalıştırmanızın ardından `Do you want authentication tokens to be time-based (y/n)` sorusuna evet anlamında `y` cevabını verip devam edin.

Uçbirimde aşağıdaki şekilde bir karekod ve bir terslik durumunda kullanılmak üzere 5 adet tek kullanımlık kod çıkacaktır.

![alt-text](ga/qrcode.png)

Çıkan karekodu tercihiniz olan bir OTP yazılımı ile mobil cihazınıza eklemelisiniz. Bunun için özgür [andOTP yazılımı önerilir ve kullanım rehberine başvurabilirsiniz.](../beseri_guvenlik/andotp.md) Aynı zamanda acil durum kodlarını da elle veya yazıcı ile yazdırarak güvenli bir yerde taşımanız bir aksilik durumunda cihazınıza erişmeniz için hararetle önerilir. Bunun için en iyi yol bastırdığınız kodları kesip koyu renkli bir bant ile kaparak cüzdan gibi sürekli taşıdığınız bir yerde bulundurmanız olacaktır. Böylece gerektiğinde kodları kullanmanız mümkün olacağı gibi istenmeyen şekilde el geçirilmesinin de önüne geçebilirsiniz. Şayet tehdit modelniz bu durumun aksine hareket etmenizi gerektiriyor ise cihazınıza daha zor olacak ise de GA erişimi olmadan da ulaşmanız mümkündür.

Karekodu taradıktan sonra gelecek tüm sorulara evet diyerek kurulumu tamamlayın. Çıkan sorular sırası ile bir kodun tekrar kullanılması, zaman sapmalarına karşı koruma ve sürekli giriş denemelerine karşı tedbir sunacaktır.

```
Do you want me to update your "/home/xxxx/.google_authenticator" file? (y/n) y

Do you want to disallow multiple uses of the same authentication
token? This restricts you to one login about every 30s, but it increases
your chances to notice or even prevent man-in-the-middle attacks (y/n) y

By default, a new token is generated every 30 seconds by the mobile app.
In order to compensate for possible time-skew between the client and the server,
we allow an extra token before and after the current time. This allows for a
time skew of up to 30 seconds between authentication server and client. If you
experience problems with poor time synchronization, you can increase the window
from its default size of 3 permitted codes (one previous code, the current
code, the next code) to 17 permitted codes (the 8 previous codes, the current
code, and the 8 next codes). This will permit for a time skew of up to 4 minutes
between client and server.
Do you want to do so? (y/n) y

If the computer that you are logging into isn't hardened against brute-force
login attempts, you can enable rate-limiting for the authentication module.
By default, this limits attackers to no more than 3 login attempts every 30s.
Do you want to enable rate-limiting? (y/n) y
```
Bu işlemin ardından ev dizinizin altında `.google_authenticator` dizininde kullanılacak anahtarınız oluşturulmuş olacak ve işletim sisteminizin PAM ayarlarına giriş yapmaya hazır olacaksınız.

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

`auth required pam_google_authenticator.so`

** Şayet bu aşamada bir sorun var ve ekran kilidinizi devreye alırsanız cihazınıza tekrar giremeyebilirsiniz!! **

Bu noktadan sonra cihazınızdaki tüm yetkilendirme gereken işlemlerde sizden GA kodu istenecektir. Her şeyin yolunda olduğundan emin olmak ve bir sorun varsa zahmetsizde düzeltmek için ** yukarıdaki tavsiyeye bağlı olarak açık tuttuğunuz sudo yetkili uçbirimden ** başka bir uç birim açarak aşağıdaki komutu girin.

`sudo echo test`

sudo yetkilendirmesi için sizden parola ve ardından GA kodu sorulması gerekli. Şayet bu gerçekleşmedi veya `test` yazısı başarılı şekilde yazılmadı ise ayarlarınızda bir terslik var demek olacağından geri dönüp adımlarda bir hata yapıp yapmadığınızı kontrol etmelisiniz. Şayet bir sorunla karşılaşırsanız sudo yetkili uçbirimden `/etc/pam.d/common-auth` dosyasında yaptığınız değişiklikleri geri alıp kaydederek cihazınızın erişiminiz dışına kitlenmesini engelleyebilirsiniz.

Şayet test'i başarılı şekilde geçti iseniz artık google-authenticator ile birlikte cihazınızı biraz daha güvenli şekilde kullanmaya başlayabilirsiniz.

## Diğer kullanıcılar

Eğer cihazda birden fazla kullanıcı var ve sadece bir kullanıcı GA kullanacak ise `/etc/pam.d/common-auth` yapılandırmasındaki değişikliği aşağıdaki ile değiştirerek sadece google-authenticator kurulumu yapmış kullanıcıların OTP kullanmasını sağlayabilirsiniz.

** Bu durum root kullanıcısının 2FA dışında kalmasına sebep olacağından gerekmedikçe önerilmez. **

`auth required pam_google_authenticator.so nullok`

Şayet root kullanıcısının da girişini GA ile kullanmak isterseniz yukarıdaki adımları root kullanıcı ile tekrar etmeniz gereklidir.
