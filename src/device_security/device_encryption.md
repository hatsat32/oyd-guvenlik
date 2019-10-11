# Cihaz Şifreleme

## Neden Cihaz Şifrelemesi Kullanmalı?

Cihaz şifrelemesi ile cihazınızın depolama alanı --işletim sisteminizi, kurduğunuz yazılımları ve kişisel verilerinizi içeren kısım--cihazınız kapalı iken erişilmesini engelleyecek şekilde karıştırılmış olmasını sağlar.

Cihaz şifrelemesi devrede değilken eğer biri cihazınızı çalar, kayıp cihazınızı bulur veya başka şekilde donanımınıza erişim elde ederseler kolaylıkla dosyalarınızı okuyabilir, hesaplarınıza erişebilir ve kimliğinizi çalabilir. Daha kötüsü, bir saldırgan kötücül yazılımları cihazınıza yükleyerek tüm kullanımınıza uzaktan erişebilir.

## Cihaz Şifrelemesi Nasıl Etkinleştirilir

Tam disk şifreleme bazı mobil cihazlarda olağan olarak gelmekte olsa da dizüstü ile masaüstü bilgisayarlarda ve çoğu cep telefonunda elle ayarlanmalıdır. 

Bilgisayar Kurulumları:

* **Windows**: [Security Planner / Windows Şifrelemesi](https://securityplanner.org/#/tool/windows-encryption)
  * Önemli: Standart olarak Microsot şifreleme anahtarlarınızı uzak sunucularda yedeklemektedir. Bu Microsoft'un ve işbirliği yaptığı her devletin cihazınızı kolaylıkla deşifre edebilmesi demektir. Eğer bir ulus devletin cihazınızın içeriğine erişmesinden endişeli iseniz bu "özelliği" devredışı bırakmalısınız ve [yeni anahtarlar üretmelisiniz](https://theintercept.com/2015/12/28/recently-bought-a-windows-computer-microsoft-probably-has-your-encryption-key/).

* **macOS**: [Security Planner / Mac Şifreleme](https://securityplanner.org/#/tool/mac-encryption)
* **Linux**: Neredeyse her Gnu/Linux dağıtımı kurulumu sırasında cihaz şifrelemeyi etkin kılmanıza imkan verir. Bunun iki cinsi vardır:
  * "Tam Disk" Şifreleme: Bu yaklaşım cihazınızın ana depolama alanındaki işletim sistemi dahil herşeyi şifreler. Cihazınız açılırken ayrı bir parola sorulur.
  * "Ev Dizini" Şifreleme: BU yaklaşımda ise işletim sistemi **şifrelenmez** Kişisel verileriniz korunacaktır fakat bir saldırganın cihazınıza erişip kötücül yazılım kurmasını zorlaştırmayacaktır.

Cep Telefonu Kurulumları:

* **iOS**: [Security Planner / Apple iOS Şifreleme](https://securityplanner.org/#/tool/apple-ios-encryption)
* **Android**: [Security Planner / Android Cihaz Şifreleme](https://securityplanner.org/#/tool/android-device-encryption)

## Cihaz Şifrelemenin Zorlukları

**Sınırları** Cihaz şifreleme her derde deva değildir! Eğer [parolalarınız](../human_security/passwords.md) yeterince güçlü değil ise bir bilgisayar rahatlıkla parolanızı tahmin edebilir ve cihazınıza erişebilir. Ayrıca cihaz şifreleme virüslere ve kötücül yazılımlara karşı hiç bir koruma sağlamaz. Eğer verileriniz bir bulut hizmetine yedeklendiyse ve bu hizmeti sağlayan sunucular açığa çıkar veya devletle işbirliği yaparsalarsa cihaz şifrelemesi verilerinizi korumayacaktır (kullanılan hizmet özellikle kullanıcı tarafından şifreleme desteklemiyorsa).

**Yetkilendirme Etkinleştirilmelidir** Cihaz şifrelemesi, yetkilendirme zorunlu değilse etkili değildir. Örneğin dizüstünü bilgisayarınıza giriş yapmanız veya cep telefonunuzun ekran kilidini bir PIN ile korumanız gibi...

**Veri Kurtarmayı İmkansız Kılar** Tam disk şifreleme, iyi parola ve PIN yönetimi sürdürülmüyorsa verilerinize erişiminizi kaybetme riskinizi arttırır. Unutulan bir parola veya PIN, disk şifreleme anahtarının tutulduğu sektörde yaşanan bir arıza verilerinizi sizin veya bir başkasının kurtaramayacağının garantisidir. Verilerinizin düzenli yedeklerini alarak veri kaybı riskini azaltmalısınız.

**Cihaz kapalı veya kilitli olmalıdır** Cihaz şifrelemesi sadece bilgisayarınız kapalı veya açık ama parola girişi gerektirirken koruma sağlar. Bir kere parolanız ile giriş yaptıktan sonra bilgisayarınız, verilerinizin deşifre edilmesi için gerekli gizli anahtarı hafızasına almış olmakla ekran kilidi etkin olsa bile çalışır durumda olduğundan(veya uyurken) bir kişinin verilerinize erişme riskini taşır. Öyle bile olsa bu tip bir saldırı fazlasıyla teknik yetkinlik gerektirmekte ve bu risk bilgisayarınızı çalışırken açık tutmanıza veya giriş yapmanıza engel olmamalı. Fakat cihazınızın sizden uzak kalabileceği tehlikeli durumlarda bilgisayarınızı kapalı tutmak en iyisidir. Eğer bu tip bir saldırının kurbanı olmaktan endişeli iseniz en iyisi cihazınızı fiziksel olarak her zaman yanınızda tutmalısınız.

## Ek Okuma Listesi

* [Security In-a-box / Güvenli Dosya Depolama](https://securityinabox.org/en/guide/secure-file-storage/)
* [Security Planner / Windows Şireleme](https://securityplanner.org/#/tool/windows-encryption)
* [Security Planner / Mac Şifreleme](https://securityplanner.org/#/tool/mac-encryption)
* [Security Planner / Apple iOS Şifreleme](https://securityplanner.org/#/tool/apple-ios-encryption)
* [Security Planner / Android Cihaz Şifreleme](https://securityplanner.org/#/tool/android-device-encryption)
* [Security Self-defense / İphone'nunuzu nasıl Şifrelersiniz](https://ssd.eff.org/en/module/how-encrypt-your-iphone)
