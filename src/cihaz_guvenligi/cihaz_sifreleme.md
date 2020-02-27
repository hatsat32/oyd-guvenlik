# Cihaz Şifreleme

## Neden cihazlarınızı şifrelemesiniz

Cihazlarınızı şifrelemekle, cihazınızın depolama alanındaki; işletim sisteminizi, kurduğunuz yazılımları ve kişiel verilerinizi içeren bölümleri cihazınız kapalı iken parolasını bilmeyenlere karşı erişilmez kılarsınız.

Cihazınız şifreli değil iken çalınması kaybolması durumunda cihazınızı bulan herhangi biri kolaylıkla dosyalarınızı okuyabilir, hesaplarınıza erişebilir ve kimliğinizi çalabilir. Daha kötüsü, bir saldırgan kötücül yazılımları cihazınıza yükleyerek tüm kullanımınıza uzaktan erişebilir.

## Cihazlar nasıl şifrelenir

Tam disk şifreleme (full disk encryption) bazı mobil cihazlarda olağan olarak gelmekte olsa da dizüstü ile masaüstü bilgisayarlarda ve çoğu cep telefonunda elle ayarlanmalıdır. 

Bilgisayar Kurulumları:

* **GNU/Linux**: Neredeyse her GNU/Linux dağıtımı kurulumu sırasında diskinizi şifrelemeyi mümkün kılar. Bu amaçla iki yöntem sözkonusudur:
  * "Tam Disk" Şifreleme: GNU/Linux dağıtımlarda [LUKS](https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup) artık standart olarak desteklenmektedir. Bu yöntem cihazınızın ana depolama alanındaki işletim sistemi dahil her şeyi şifreler. Cihazınız açılırken size ayrı ve deşifre amacıyla bir parola sorulur.
  * "Ev Dizini" Şifreleme: Bu yaklaşımda ise işletim sistemi **şifrelenmez** Kişisel verileriniz korunacaktır fakat bir saldırganın cihazınıza eriştiğinde işletim sisteminize etki edecek bir değişiklik yapmasını engellemeyecektir.

* **Windows**: [Security Planner / Windows Şifrelemesi](https://securityplanner.org/#/tool/windows-encryption)
  * Önemli: Standart olarak Microsoft şifreleme anahtarlarınızı uzak sunucularda yedeklemektedir. Bu Microsoft'un ve işbirliği yaptığı her devletin cihazınızı kolaylıkla deşifre edebilmesi demektir. Eğer bir devletin cihazınızın içeriğine erişmesinden endişeli iseniz bu "özelliği" devredışı bırakmalısınız ve [yeni anahtarlar üretmelisiniz](https://theintercept.com/2015/12/28/recently-bought-a-windows-computer-microsoft-probably-has-your-encryption-key/).

* **macOS**: [Security Planner / Mac Şifreleme](https://securityplanner.org/#/tool/mac-encryption)


Cep Telefonu Kurulumları:

* **iOS**: [Security Planner / Apple iOS Şifreleme](https://securityplanner.org/#/tool/apple-ios-encryption)
* **Android**: [Security Planner / Android Cihaz Şifreleme](https://securityplanner.org/#/tool/android-device-encryption)

## Cihaz şifrelemenin zorlukları

**Sınırları:** Cihaz şifreleme her derde deva değildir! Eğer [parolalarınız](../human_security/passwords.md) yeterince güçlü değil ise bir bilgisayar rahatlıkla parolanızı tahmin edebilir ve cihazınıza erişilebilir. Ayrıca cihaz şifreleme virüslere ve kötücül yazılımlara karşı hiç bir koruma sağlamaz. Eğer verileriniz bir bulut hizmetine yedeklendiyse ve bu hizmeti sağlayan sunucular açığa çıkar veya devletle işbirliği yaparsalarsa cihaz şifrelemesi verilerinizi korumayacaktır (kullanılan hizmet özellikle uçtan uca şifreleme desteklemiyorsa).

**Yetkilendirme etkinleştirilmelidir** Cihaz şifrelemesi, yetkilendirme zorunlu değilse etkili değildir. Örneğin dizüstünü bilgisayarınıza giriş yapmanız veya cep telefonunuzun ekran kilidini bir PIN ile korumanız gibi...

**Veri kurtarmayı imkansız kılar** Tam disk şifreleme, iyi bir parola ve PIN yönetimi sürdürülmüyorsa verilerinize erişiminizi kaybetme riskinizi arttırır. Unutulan bir parola veya PIN, disk şifreleme anahtarının bulunduğu sektörde yaşanan bir arıza verilerinizi sizin veya bir başkasının kurtaramayacağının garantisidir. Verilerinizin düzenli yedeklerini alarak veri kaybı riskini azaltmalısınız. Yedeklerinizi de fiziki güvneliğini sağlayamıyorsanız şifrelemeniz önerilir.

**Cihaz kapalı veya kilitli olmalıdır** Cihaz şifrelemesi sadece bilgisayarınız kapalı iken tam güvenlik sağlar. Bir kere parolanız ile giriş yaptıktan sonra bilgisayarınız, verilerinizin deşifre edilmesi için gerekli anahtarı hafızasına almış olmakla ekran kilidi etkin olsa bile çalışır durumda olduğundan (veya uyurken) bir kişinin verilerinize erişme riskini taşır. Bu tip bir saldırı fazlasıyla teknik yetkinlik gerektirmekte ve bu risk bilgisayarınızı açık tutmanıza veya giriş yapmanıza engel olmamalı. Fakat cihazınızın sizden uzak kalabileceği tehlikeli durumlarda bilgisayarınızı kapalı tutmak en iyisidir. Eğer bu tip bir saldırının kurbanı olmaktan endişeli iseniz en iyisi cihazınızı fiziksel olarak her zaman yanınızda bulundurmalısınız.

## Ek okuma listesi

* [Security In-a-box / Güvenli Dosya Depolama](https://securityinabox.org/en/guide/secure-file-storage/)
* [Security Planner / Windows Şireleme](https://securityplanner.org/#/tool/windows-encryption)
* [Security Planner / Mac Şifreleme](https://securityplanner.org/#/tool/mac-encryption)
* [Security Planner / Apple iOS Şifreleme](https://securityplanner.org/#/tool/apple-ios-encryption)
* [Security Planner / Android Cihaz Şifreleme](https://securityplanner.org/#/tool/android-device-encryption)
* [Security Self-defense / iPhone'nunuzu nasıl Şifrelersiniz](https://ssd.eff.org/en/module/how-encrypt-your-iphone)
