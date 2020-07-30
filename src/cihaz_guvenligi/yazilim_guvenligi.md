# Yazılım Güvenliği

## Yazılımlarınızı güncel tutun

Bir saldırgan yazılımlarınızdaki bir zayıflığı kullanarak cihazlarınızın güvenliğini tehlikeye atabilir. Bu risk çoğu zaman sadece yazılımlarınızı güncel tutarak önleyebileceğiniz bir durumdur. Yazılım geliştiricileri çoğunlukla bu açıkları saldırganlar durumu keşfetmeden önce düzelterek güncellemeler aracılığı ile yamarlar. 

Özellikle işletim sisteminizi güncel tutmak önemlidir çünkü işletim sisteminiz cihazınızdaki her işleme ayrıcalıklı ulaşım yetkisi vardır.

Otomatik Güncellemer Nasıl Açılır?

* **GNU/Linux**: Çoğu dağıtımda otomatik güncelleştirmeler zaten açık gelir ve kritik güncelleştirmeler konusunda uyarılırsınız. Elle güncelleme yapmak isterseniz kullandığınız dağıtımın grafik arayüzünden faydalanabilir veya;
	* Debian tabanlı dağıtımlar için: Terminalden **sudo apt-get update & sudo apt-get upgrade -y** komutunu kullanarak güncelleme yapabilirsiniz.
	* RPM tabanlı dağıtımlar için: Terminalden **sudo yum update -y** komutunu kullanarak güncelleme yapabilirsiniz.
* **macOS**: **Apple** menüsüne tıklayın, **Sistem tercihleri** > **App Store** > **Güncellemeleri otomatik olarak denetle**
* **Windows**: **Başlat** çubuğuna tıklayın, daha sonra **Ayarlar** > **Güncelleme ve güvenlik** > **Windows Güncellemeleri** > **İleri seçenekler**i tıkladıktan sonra **Güncellemeler nasıl indirilsinin** altındaki **Otomatik (önerilen)**'i seçin.

Uyarılar:

* Bazı güncellemerin işe yaraması için güncellemeden sonra cihazınızı yeniden başlatmanız gerekebilir. Bu yüzden güncellemelerden sonra cihazınızın yeniden başlatılmasına izin vermeniz gerekir.
* Eğer özel yazılım gereksinimleriniz varsa otomatik güncellemeler yazılımlarınızın çalışmasında aksamalara sebep olabilir. Örneğin bazı işletim sistemi güncellemeleri mevcut yazılımla uyuşmayabilir.
* Yazılımınızı güncel tutmak, kullanıcıyı kandırarak yapılan kötü amaçlı yazılım ve oltalama saldırılarından korumaz.

## Uygulama mağazasını kullanın

Mümkün olduğunca yazılımlarınızı işletim sisteminize ait uygulama mağazasından indirmelisiniz;

* **Güvenilirlik**: Uygulama mağazasındaki uygulamalar geliştiricileri tarafından imzalanır ve mağaza tarafından doğrulanır. Bu doğrulama çoğu zaman sığ bir inceleme olduğu için mutlak olarak güven duyulmamalıdır ama hiç yoktan iyidir.
* **Güncellemeler**: Uygulama mağazası uygulamalarınızı güncel tutmanıza yardım eder.
* **Side Loading Saldırılarını Önler**: Uygulama mağazası dışından uygulama indirmeye "Side Loading" denir. Side loading şuanda Android'de varsayılan olarak engelli, iOS'te ise imkansız ancak GNU/Linux'ta, macOS seçime bağlı durumda. Windows sistemler ise çoğunlukla side loading'e dayanmakta. Side loading kullanarak indirdiğiniz ve doğrulamadığınız her yazılım nihayetinde sisteminizi kötücül yazılımlara karşı tehlikeye atar. Bu neden ile sistemlerinize kurduğunuz yazılımları güvenilir kaynaklardan ve uygulama mağzalarından yüklemeniz önerilir.

Not: Resmi Android uygulama mağazası Google Play'i taklitçi uygulamalardan kaçınmak için dikkatli kullanmalısınız. En iyisi sadece özgür yazılımların sunulduğu [F-Droid](https://f-droid.org) uygulama mağzasını kullanmanızdır.

## Şüpheliyse indirmeyin

Mobil uygulamalar, tarayıcı eklentileri ve ücretsiz programların artması ile birçok güvenlik problemi de ortaya çıktı. Bu sebep ile güvendiğiniz kuruluşların (örneğin daha önce kullanmış olduğunuz) yazılım geliştiricileri tarafından geliştirilmeyen yazılımlardan mümkün ise kaçının.

Görünürde iyi niyetli olan veya faydalı görünen yazılımlar (antivirüs tarayıcıları gibi) aslında arkaplandaki kötü hareketlerini gizliyor olabilir. Çoğu tarayıcıda ve mobil cihazda bir uygulama kurulum sırasında cihazda ulaşabileceği bilgiler ve donanımlar hakkında çeşitli izinler ister. Bu izinlerin uygulamanın beklenen amacı kapsamında kaldığına kabaca göz atmak gereklidir.Örneğin bir fener uygulaması cihazınızın rehberine erişmek veya telefon aramaları yapabilmek isterse bu yazılımı kullanmamalısınız. Aramalarınıza, kişilerinize, kameranıza, mikrofonunuza, konum servislerinize veya tüm saklama alanınıza verdiğiniz erişim izinleri hakkında çok dikkatli olunmalıdır.

İndirdikten sonra verdiğiniz izinlere bakmak, cihaza ve koşula göre farklılık gösterebilir. Firefox tarayıcısında, ayarlar altında mahremiyet ve güvenlik sekmesinde verilen izinleri görebilirsiniz. Chrome ve Chromium'da, chrome://extensions/'a gidin ve her eklenti için izinlere tıklayın. iOS cihazlarında, ayarların altında tüm izinlerin listesi vardır. Her iznin altında da o izinleri kullanan uygulamalar yer alır. Android cihazlarında Ayarlar > Uygulama yöneticisinde uygulama listesini görüntüleyebilirsiniz. Her uygulamanın altında uygulamanın kullandığı izinleri gösteren bir liste vardır.

Genel bir alışkanlık olarak cihazlarınızda gereksiz veya çok seyrek kullandığınız yazılımları kullanmamak gerekir. Şayet bir yazılımın sunduğu hizmeti Web'den alabiliyorsanız, yazılımını cihazınıza kurmak yerine tarayıcınız aracılığı ile web üzerinden hizmet almayı seçebilirsiniz. Genel olarak da bir yazılım hem özgür değil hem de ücret istemeden çok şey vaad ediyorsa işin içinde bir bit yeniği var mı bakılmalıdır.

Maalesef dizüstü ve masaüstü bilgisayarlarındaki çoğu işletim sisteminin bir izin yönetimi yok ve yazılımlar kurulum sırasında sistem kaynaklarına erişim için izin istemiyor. Bu yüzden bilgisayarlarınıza indirdiğiniz yazılımlarda çok daha dikkatli olmanız gerekiyor.

## Korsan yazılım kullanmayın / Mümkünse mülk yazılım kullanmayın

Korsan yazılım indirmek bilgisayarınıza virüs veya kötü amaçlı yazılım bulaştırmak için harika bir yoldur. Pek çok mülk yazılım da kaynak koduna erişemediğiniz için şüpheli ve bazen amacı gereği zaten güvenlik tehlikesidir.

Eğer cihazlarınızda yapmanız gereken bir işlem varsa ve bunun için uygun bir yazılım arıyorsanız öncelikle özgür veya açık kaynak yazılımları değerlendirmeniz önerilir.

## Özgür yazılım kullanın

Özgür veya açık kaynak uygulamalar, genellikle kullanılan özel mülk yazılımlara harika alternatiflerdir. GNU/linux, windows, MacOs ve Android için kolaylıkla elde edilebilir.

* **[Gimp](https://www.gimp.org/)**: Taramalı grafik ve fotoğraf düzenleme programı (Adobe Photoshop'a alternatif)
* **[Inkscape](https://inkscape.org/en/)**: Vektör çizme programı (Adobe Illustrator'a alternatif)
* **[LibreOffice](https://www.libreoffice.org/)**: Ofis verimlilik takımı (Microsoft Office'e alternatif)
* **[Scribus](https://www.scribus.net)**: Masaüstü yayıncılık uygulaması (Adobe Indesign'a alternatif)
* **[F-Droid](https://f-droid.org)**: Android işletim sistemlerinde özgür yazılımların bulunabileceği benzersiz bir uygulama deposu.

## Ayrıca bakınız

* [Güvenlik planlayıcısı / Windows bilgisayarınızı güncelleyin](https://securityplanner.org/#/tool/update-your-windows-computer)
* [Güvenlik planlayıcısı / Mac'inizi güncel tutun](https://securityplanner.org/#/tool/keep-your-mac-updated)
* [Güvenlik planlayıcısı / Güvenli uygulamalar kullanın](https://securityplanner.org/#/tool/use-safe-apps)
