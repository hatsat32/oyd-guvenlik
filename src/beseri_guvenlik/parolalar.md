# Parolalar

<!-- toc -->

## Parola yöneticisi kullanın<a name="parola-yoneticisi"></a>

Parola yöneticisi kullanmak, kişisel güvenliğinizi arttırmak için yapabileceğiniz en önemli değişikliktir.

Bilgisayarların işlem güçlerinin giderek arttığı ve sızıntılar dolayısı ile çokça kişinin parolaları İnternet'e saçıldığı için insanların kafalarından uydurduğu parolalar artık yetersiz kalmaktadır. Güvenli parolalar artık **xoo|Z'eetohth3Zoaph^** gibi göründüğünden insanların hatırlaması mümkün değildir.

Bir parola yöneticisi, size hem güçlü hem de eşsiz parolalar kullanma imkanı sağlar. Parola yöneticisi ile her hesabınız için benzersiz parolalar atar ve tüm hesaplarınızın parolalarına erişmenizi sağlayacak sadece bir adet parola hatırlarsınız. Özetle siz bir tane güvenli parola hatırlarsınız, parola yöneticisi sizin için yüzlerce!

İyi bir parola yöneticisinde dikkat edilmesi gereken üç önemli özelliği vardır:

* **Yerel Uygulama**: Parolalarınızı, bir ana parola ile şifreleyerek saklayan özel bir uygulamadır. Bu oldukça güvenilir bir seçenek olmakla birlikte birden fazla cihaz arasında eşitlemeyi güçleştirecektir.
* **Bulut Hizmetleri**: Genellikle ücretli olmakla parolalarınızı cihazlarınızdan bağımsız olarak saklayan bir hizmeti ifade eder. Bulut hizmetleri aracılığı ile parolalarınıza her yerden ulaşmanın kolaylığı olmakla birlikte dezavantajı daha az güvenliğe sahip olmasıdır. 
* **Tarayıcı Eklentileri**: Hem yerel uygulama hem de bulut hizmeti olarak sunulan parola yöneticileri çoğunlukla, parolalarınıza kolaylıkla erişebilmeniz için bir tarayıcı eklentisine sahiptirler. Bu eklentiler rahatlık sağlar fakat daha az güvenlidirler.
* **Özgür Yazılım**: Kullanacağınız parola yöneticisi muhakkak özgür bir yazılım olmalıdır. Nasıl çalıştığını bilemediğiniz bir yazılıma parolalarınızı teslim etmek güvenli değildir.

Hangi aracı seçtiğinize bakmaksızın gerçekten önemli olan bir parola yöneticisi kullanmanızdır. Lütfen aşağıdaki önerileri aklınızda tutun:

* **Ana Parola**: Bir parola yöneticisi kullanırken, ana parolanızı kaybetmemeniz hayati önem taşır. Ana parolayı unutma ihtimaline karşı bir yere bu parolayı not edebilirsiniz. Ama güçlü ve unutulması zor bir ana parola üretmek için **[Zarola](https://zarola.oyd.org.tr)** kullanmanızı öneriyoruz. Bilgisayarlar için zor ama hatırlamanız için kolay bir parola tüm sayısal hayatınızın dayanacağı bir parolayı unutmamak için en garanti yoldur.
* **Yedekler**: Parola yöneticinizin verilerini düzenli olarak yedeklemeniz de bir o kadar önemlidir. Bulut hizmeti yedekleme işini sizin için yaparken yerel yedeklerinizi düzenli olarak almanız yararınıza olacaktır. Yerel uygulamalar için veri dosyasının yedeğini almak yeterlidir. Ara sıra parola yöneticinizin parolaları sakladığı küçük dosyayı bir USB belleğe koyup kenara kaldırmak sizi çokça baş ağrısından kurtarabilir.

Yaygın özgür parola yöneticileri;

*  [KeePassXC](https://keepassxc.org/): (yerel uygulama) Kullanım kolaylığı açısından tavsiye edilen yerel parola yöneticisidir. Neredeyse her bilgisayarda çalışabilmektedir ve Nextcloud ile eşitlenebilir.
* [Pass](pass.md): GnuPG ve Git ile çalışan bir parola yöneticisidir. Eğer GnuPG'ye ve Git'e biraz hakimseniz, kesinlikle `pass` kullanmanız tavsiye edilir. Pass, parolalarınızı GnuPG anahtarınızla şifreler ve uzak bir Git sunucusuyla eşitleyebilir. Android istemcisi ve Firefox eklentisi mevcuttur.
* [Bitwarden](https://bitwarden.com/): Tamamen uzak sunucuda çalışan ve pek çok platform için istemcileri bulunan bir parola yöneticisidir.

## Güçlü Parolalar Kullanın<a name="guclu-parola"></a>

Güçlü parolalar rastgele üretilirler. Bir parolanın gücünü, uzunluğu ve rastgeleliği belirler. Cihazınız ve parola yöneticisi ana parolası haricindeki tüm parolalarınız bir parola yöneticisi tarafından rastgele üretilmelidir. Parolalarınız en az 12 karakter olmalıdır. Ancak 26 karakterden uzun parola kullanmanıza gerek yoktur. İyi bir parola geleceğe yönelik iyi bir yatırımdır.

İnsanlar, bilgisayarların aksine güvenli parolalar yaratmakta bir hayli başarısızdır. Bırakın bilgisayar bu işi sizin için yapsın.

Hatırlamanız gereken parolalar üretmek için pek çok yol bulunmaktadır. Eğer parola yöneticisi kullanıyorsanız bırakın uygulama sizin için üretsin. Ancak kendiniz hatırlaması kolay güçlü parolalar oluşturmak istiyorsanız biz [Zarola](https://zarola.oyd.org.tr) kullanmanızı öneriyoruz.

[Zarola](https://zarola.oyd.org.tr), kolayca hatırlanabilir ve yüksek derecede güvenli parolalar oluşturabilmenizi sağlayan bir yöntemdir. İnsanlar rastgele şeyler üretemeyeceklerinden rastgelelik kaynağı olarak zar veya bozuk para kullanılır. 7776 Tane kelime içinden seçilen 7 adet ile parola oluşturulur ve hikayeleştirilerek ezberlenir. Bazen komik hikayeler bile çıkar!

Konuya ilişkin Security Self-defense'in "[Güçlü Parolalar Üretmek](https://ssd.eff.org/en/module/creating-strong-passwords)" rehberine bakabilirsiniz.

Her hesabın güvenli ve eşsiz bir parola ile korunması önemlidir, çünkü bir hesaba erişim bazen diğer hesap ve sistemlere erişim hakkı doğurabilir. Bu durum, özellikle hesaplarınızı sıfırlama imkanı olan her **e-posta hesabı** için geçerlidir (genellikle "parolamı unuttum" bağlantıları ile).

## Eşsiz parolalar kullanın<a name="essiz-parola"></a>

Eşsiz parolalar kullanmak üçüncü parti hizmetleri kullanırken alınan riskleri en aza indirir. Şayet bir parolayı birden fazla hesap için kullanırsanız, bir hesaptan sızan kullanıcı adı ve parolalar ile diğer hesaplarınıza sızılabilir. Farklı servisler için farklı parolalar kullanmak hesaplarınızı birbirinden izole ederek riski azaltacaktır. Bir parola yöneticisi kullanmak bunu yapmayı oldukça kolaylaştırır.

## Parolalarınızı gizli tutun<a name="gizli-parola"></a>

Parolalarınızı her kim sorarsa sorsun asla kimseye vermeyin (Evet, teknik destek vermek için soran IT personeline de vermeyin.). Neredeyse her hesap ve sistem parola sıfırlamasına olanak tanımaktadır. Herhangi bir IT uzmanı, size parolanızı sormadan bakım amaçlı parolanızı sıfırlayabilmektedir. Bu tip sistemler aynı zamanda erişimleri takip altında tutar, sizi sıfırlama hakkında bilgilendirir ve her yönetici erişiminden sonra parolanızı değiştirmeniz istenir. Bunun için sadece söz konusu sistemlere erişiminizin olması yeterlidir.

## Kurumsal ve kişisel parolalarınızı ayırın<a name="kurumsal-kisisel-parola"></a>

Burada kurumsal paroladan kasıt, kurumunuzun sistemlerine ve dijital kimliklerine erişim sağlayan herhangi bir paroladır. Bunlar gerçekten önemli bilgiler olduklarından, kişilerin kendi kişisel hesaplarına girmek için kullandıkları parolalardan farklı olmalı ve ayrı olarak saklanmalıdır. Kurumsal parolanızı, parola yöneticisinde ayrı bir giriş veya farklı bir parola dosyası kullanarak, ya da tamamen farklı bir parola yöneticisi seçerek saklayabilirsiniz.

## Ek okuma listesi<a name="ek-okuma"></a>

* [Security Planner / Password Managers](https://securityplanner.org/#/tool/password-manager)
* [Security In-a-box / Passwords](https://securityinabox.org/en/guide/passwords/)
* [Security Self-defense / Animated Overview: Using Password Managers to Stay Safe Online](https://ssd.eff.org/en/module/animated-overview-using-password-managers-stay-safe-online)
* [Security Self-defense / How to: Use KeepPassXC](https://ssd.eff.org/en/module/how-use-keepassxc)
* [Security Self-defense / Creating Strong Passwords](https://ssd.eff.org/en/module/creating-strong-passwords)
* [Security Education Companion / Passwords](https://sec.eff.org/topics/passwords)
* [Security Education Companion / Password Managers](https://sec.eff.org/topics/password-managers)
