# Yubikey ile Login Güvenliği

<!-- toc -->

[Yubikey](https://yubico.com) çok işlevli kriptografik bir güvenlik aracı. Yubikeyler [GPG](../yazisma_guvenligi/gpg/gpg.md) anahtarı olarak kullanılabildiği gibi U2F ve TOTP gibi ikinci faktör yetkilendirme araçları olarak da kullanılabilmekte. Bu özellikleri sayesinde bilgisayarlarda yetkilendirme aşamasında ikinci faktör olarak kullanılması mümkün olmakta. Bu kullanıcıların bildikleri bir şey (parola/pin) ve sahip oldukları bir şey (Yubikey) ile sistemlere giriş yapabilmelerine imkan vermekte.

## Kurulum

Öncelikle Yubikey'in challange-response imkanından yararlanarak login olabilmek için aşağıdaki gerekli paketleri kurmanız gerekmekte.

Debian tabanlı sistemler için:

```
sudo apt-add-repository ppa:yubico/stable
sudo apt update
sudo apt install yubikey-manager
```

RPM tabanlı sistemler için: `sudo yum install libpam-yubico yubikey-manager`

### Yubikey'in ayarlanması

Öncelikle Yubikey'inizin bilgisayarınızda görüldüğünden emin olmak için aşağıdaki komutu bir uçbirimde çalıştırıp Yubikey versiyonunuzu gördüğünüzden emin olun.

`ykinfo -v`

Şayet Yubikey dahilinde bir challange-response slotu altında anahtarınız bulunuyorsa bu bölümü geçebilirsiniz. Aksi takdirde Yubikey'inizin iki OTP bölümünden birinde bir sefere mahsus olarak kurulum yaparak gerekli anahtarların oluşturulmasını sağlamanız gerekiyor. Bunun için Yubikey'i bilgisayarınıza takarak bir uçbirimde aşağıdaki komutu çalıştırın.

`ykpersonalize -2 -ochal-resp -ochal-hmac -ohmac-lt64 -oserial-api-visible`

Uçbirimden aşağıdaki gibi bir cevap dönecektir. Üretilen anahtar listelenecek ve 2 bölüme bu anahtarı atayıp atamak istemediğiniz sorulacaktır. Soruya evet anlamında `y` diyerek devam edin.

```
Firmware version 4.x.x Touch level 263 Program sequence 3

Configuration data to be written to key configuration 2:

fixed: m:
uid: n/a
key: h:69b16d50e08c34f12fecc148ae0eabf284c59484
acc_code: h:000000000000
OATH IMF: h:0
ticket_flags: CHAL_RESP
config_flags: CHAL_HMAC|HMAC_LT64
extended_flags: SERIAL_API_VISIBLE

Commit? (y/n) [n]: 
```

Şayet Yubikey'inizi bilgisayara takılı bırakıyoranız, yetkilendirmenin sizden habersiz sistem tarafından gerçekleştirilmesini engellemek için Yubikey'e dokunma gerekliliği getirebilirsiniz. Bunun için aşağıdaki komutu kullanabilirsiniz.

`ykpersonalize -2 -ochal-resp -ochal-hmac -ohmac-lt64 -ochal-btn-trig -oserial-api-visible`

Bu noktadan sonra artık Yubikey'iniz challange-response bölümüne sahip ve kullanıma hazır. Şayet denemek isterseniz aşağıdaki komutu girerek bir uçbirimde rastgele cevabı görebilirsiniz.

`ykman otp calculate 2 1111111111111111`

### PAM ayarları

PAM yapılandırmasını ayarlamadan önce gerekli Yubikey anahtarının bilgisayarınızda ev dizini altına eklenmesi gerekiyor. Bunun için aşağıdaki komutu çalıştırın.

`ykpamcfg -2 -v`

Uçbirim Yubikey'e istek göndererek dönüşünü bekleyecektir. Şayet dokunma ayarını açtıysanız Yubikey'e dokunmanız gerekebilir bu noktada. Uçbirimden aşağıdaki gibi bir sonuç alacaksınız.

```
debug: ../util.c:222 (check_firmware_version): YubiKey Firmware version: 4.4.2

Sending 63 bytes HMAC challenge to slot 2
Sending 63 bytes HMAC challenge to slot 2
Stored initial challenge and expected response in '/home/xxx/.yubico/challenge-1234567'.
```

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

`auth required pam_yubico.so mode=challenge-response`

** Şayet bu aşamada bir sorun var ve ekran kilidinizi devreye alırsanız cihazınıza tekrar giremeyebilirsiniz!! **

Bu noktadan sonra cihazınızdaki tüm yetkilendirme gereken işlemlerde sizden Yubikey'i takmanız istenecektir. Her şeyin yolunda olduğundan emin olmak ve bir sorun varsa zahmetsizde düzeltmek için ** yukarıdaki tavsiyeye bağlı olarak açık tuttuğunuz sudo yetkili uçbirimden ** başka bir uç birim açarak aşağıdaki komutu girin.

`sudo echo test`

sudo yetkilendirmesi için Yubikey'iniz takılı iken sizden parola sorulması ve uçbirimin `test` yazdırması gerekli. Şayet bu gerçekleşmedi ise ayarlarınızda bir terslik var demek olacağından geri dönüp adımlarda bir hata yapıp yapmadığınızı kontrol etmelisiniz. Şayet bir sorunla karşılaşırsanız sudo yetkili uçbirimden `/etc/pam.d/common-auth` dosyasında yaptığınız değişiklikleri geri alıp kaydederek cihazınızın erişiminiz dışına kitlenmesini engelleyebilirsiniz.

Şayet test'i başarılı şekilde geçti iseniz artık Yubikey ile birlikte cihazınızı biraz daha güvenli şekilde kullanmaya başlayabilirsiniz.

### Diğer kullanıcılar

Eğer cihazda birden fazla kullanıcı var ve sadece bir kullanıcı Yubikey kullanacak ise `/etc/pam.d/common-auth` yapılandırmasındaki değişikliği aşağıdaki ile değiştirerek sadece google-authenticator kurulumu yapmış kullanıcıların OTP kullanmasını sağlayabilirsiniz.

** Bu durum root kullanıcısının 2FA dışında kalmasına sebep olacağından gerekmedikçe önerilmez. **

`auth required pam_yubico.so mode=challenge-response nullok`

Şayet root kullanıcısının da girişini Yubikey ile gerçekleştirmek isterseniz yukarıdaki adımları root kullanıcı ile tekrar etmeniz gereklidir.
