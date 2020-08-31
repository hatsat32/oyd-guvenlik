# Mobil Cihazlar

### Hangi taşınabilir cihaz benim için uygun?

Cihazınızı içinde bulunduğunuz duruma göre seçmelisiniz:

* **Yüksek Risk**: Bir devletin veya uzman ajanlık şirketlerinin hedefi olacağınızdan şüpheleniyorsanız.
* **Orta Risk**: Hali hazırda hedef olmadığınız halde bir saldırganın cihazlarınıza fiziksel erişim sağlaması durumunda kolay lokma olmayı tercih etmiyorsanız.
* **Düşük Risk**: Taşınabilir cihazlarınızı hassas veriler için kullanmıyorsanız.

#### Yüksek risk

Eğer riskiniz yüksek ise, **cep telefonunuzu hassas hiç bir şey için kullanmayın**. Bunun sebebi, tüm telefonların sizi kablosuz telefon ağına (hücresel ağ) bağlayan, "[baseband modem][]" olarak adlandırılan bir donanım içermesidir. Bu modemler özel mülktür ve uzaktan kötüye kullanılabilecek pek çok güvenlik açığı içermektedir. Bir kere aşıldıktan sonra, [baseband modem] iletişiminizi takip etmek ve kişisel verilerinizi elde etmek için kullanılabilir.

[Replicant][] tamamen özgür bir Android dağıtımı olarak sadece belirli cihazlar üzerinde çalışmaktadır. Çalıştığı cihazların temel özelliği [baseband modem]'i işlemciden izole etmenin bir imkanı olmasıdır. [Replicant] aynı zamanda, cihaz  üzerindeki, Wi-Fi, Bluetooth, GPS gibi donanımları özgür sürücüleri bulunmadığı için çalıştırmaz. Şayet mobil cihaz kullanmanız gerekiyorsa ve bu cihaz ile önemli veriler işleyecekseniz [Replicant] kurulu bir telefon iyi bir tercih olabilir.

Cep telefonlarına alternatif olarak Wi-Fi desteği olan ama hücresel ağa bağlanmayan bir tablet satın alabilirsiniz. Bu tip cihazlar baseband modem içermemektedir ve uzaktan saldırılara karşı çok daha dayanıklıdır. Sadece Wi-Fi içeren bir cihaz ile hala hücresel ağa, ayrı bir taşınabilir hotspot cihazı ile bağlanabilirsiniz.

NOT: Uçak modu yeterli değildir. Cihazınıza bağlı olarak, uçak modunda bile baseband modem hala çalışıyor ve cihazınızı saldırılara açık tutuyor olabilir.

Tavsiye edilen sadece Wi-Fi destekleyen cihazlar:

_Güncellenecektir (1 Ağustos 2020)_

#### Orta risk

Taşınabilir cihazınızda; devletler, şirketler veya meraklı insanlar tarafından elde edilmesini istemediğiniz hassas veriler mi var? Elbette var, herkesin var! Bu durumda, biri cihazınızı bulduğunda veya çaldığında onların işini olabildiğince zorlaştırmak istemeniz çok doğal.

Şayet hiç uğraşmayacağım diyorsanız, kendinizi Apple şirketinin sinsi yumuşak kollarına bırakıp modern bir iPhone alabilirsiniz. Pek çok gerçek olayda bu cihazlara örgütlü devletler dışında kolaylıkla erişilemediği görüldü. Lakin Apple şirketinin Çin ile yaşadığı aşk, yakın zamanda özgür olmayan yazılımında bulunan açıklar ve İsrailli bir şirketin 1000 ABD dolarına her iPhone'un kilidini kırabildiği iddiası ile yaşamanız gereklidir.

Tavsiyemiz uygun bir cihaz alarak üzerinde [GrapheneOS][] veya [LineageOS][] Android dağıtımları çalıştırmanız ve Google, Facebook gibi casusluk şirketlerinin yazılımları da dahil özgür olmayan yazılımlar **çalıştırmamanızdır**. [GrapheneOS] ve [LineageOS] piyasadan alabileceğiniz pek çok cihaza kolaylıkla kurulabilen ve mahremiyetinize önem veren toplulukların geliştirdiği işletim sistemleridir.

Tavsiye edilen cihazlar:

* **[LineageOS için][lineageos devices]**;
	* [LG G3](https://wiki.lineageos.org/devices/d855) Türkiye'de kolaylıkla bulunabilen, temizi için biraz araştırma gerektiren ama zamanına göre çok iyi donanıma sahip bir cihazdır. LineageOS kurulumu rootlama gereğinden dolayı biraz baş ağrıtabilir ama fiyat/performansta çok başarılıdır. Ancak LG G3 cihazlar, kronik olarak anakart arızası yaşayabilmektedir. Bu durumu göz önünde bulundurmanızı tavsiye ederiz.
	* [Sony Xperia Z](https://wiki.lineageos.org/devices/yuga) Görece eski bir donanım olan Z Türkiye'de bolca ve ucuza bulunabiliyor. LineageOS kurulumu da çok kolaydır. Lakin donanım yaşını gösterdiği için cihazınızı sonuna kadar kullanıyorsanız sizi tatmin etmeyebilir.
	* [Xiaomi Redmi Note 7](https://wiki.lineageos.org/devices/lavender) Çok daha modern bir donanım olarak Redmi Note 7 performans isteyen kullanıcılar için iyi bir tercih olabilir. USB-C desteklediği için de geleceğe dönük rahat etmenizi sağlar. Ancak NFC desteği **bulunmamaktadır**.

* **[GrapheneOS için][grapheneos devices]**;
	* Google [Pixel serisi](https://grapheneos.org/#device-support) cihazların tamamına GraphenOS kurulabilmekte fakat Pixel 4 sürümü henüz tamamlanmadı. Graphene uzun dönemli destek için, şimdilik Pixel 3 serisi cihazları önermektedir. GrapheneOS, Pixel 4 için tamamlandığında bu önerinin Pixel 4 olarak değişmesi muhtemel.

#### Düşük risk

Telefonunuzu kilitsiz bir şekilde öylece ortalıkta mı bırakıyorsunuz? O zaman ya başınıza gelecekleri hak ediyorsunuz ya da gerçekten taşınabilir cihazlarınızda hiçbir şey olmadığını düşünüyorsunuz. Ne yazık ki modern taşınabilir cihazlar İnternet'e bağlı oldukları ve kullanıldıkları sürece siz fark etmeseniz de ziyadesiyle fazla veri üretir ve bunları kaydederler. Bu verilerden belki haberiniz yoktur ama pekala bilgili bir kişi -ki bu bilgisayarla ilgili her sorunuzda aradığınız arkadaşınız bile olabilir- bu bilgilere ulaşmanın bir yolunu bilebilir.

Bu sebeple riskinizin düşük olduğuna eminseniz ve yanıldığınız için pişman olmayacaksanız, pekala herhangi bir telefon alıp ekran kilidi bile kullanmadan hayatınızı sürdürebilirsiniz.

## Genel tavsiyeler

### Cihazlarınızı yanınızdan ayırmayın

Cihazlarınızı fiziksel olarak yanınızda tutmak her zaman iyi bir fikirdir. Aksi takdirde bir saldırganın cihazınıza girmek, verilerinizi ele geçirmek ve gelecekteki etkinliklerinizi izlemek amacı ile kötücül yazılım yüklemesine fırsat doğabilir.

Cihazlarınızın zafiyeti tavsiye edilen donanımları kullanıp kullanmadığınıza, [şifrelemenin](cihaz_sifreleme.md) etkinleştirilip etkinleştirilmediğine ve cihazınızı bir parola veya PIN ile koruyup korumadığınıza bağlıdır.

**Bir saldırganın cihazınıza girebilme olasılığı:**

| Cihazınız | Yetkin saldırgan | Eğitimli saldırgan | Olağan saldırgan |
| ---: | --- | --- | --- |
| Tavsiye edilen cihaz + Şifrelenmiş + Kilitli | DÜŞÜK | ÇOK DÜŞÜK | HİÇ |
| Tavsiye edilen cihaz + Kilitli | ORTA | DÜŞÜK | ÇOK DÜŞÜK |
| Normal cihaz + Şifreli + Kilitli | YÜKSEK | ORTA | DÜŞÜK |
| Normal cihaz + Kilitli | ÇOK YÜKSEK | YÜKSEK | ORTA |
| Kilitsiz | KESİN | KESİN | KESİN |

Saldırgan tipleri:

* **Yetkin saldırganlar** Kilitli telefonlara girmekte uzmanlaşmış büyük devletleri ve uluslararası şirketleri kapsar.
* **Eğitimli saldırganlar** Yerel kolluk kuvvetlerini ve telefon kıran adli tıp şirketlerini kapsar.
* **Olağan saldırganlar** Özel donanım sahibi olmayan yetenekli teknoloji meraklılarını kapsar.

Eğer cihazınızdan uzak kalacaksanız ve cihazınıza girilme ihtimali var ise verilerinizi yedeklemeli, fabrika ayarlarına dönüş yapmalısınız (veya yeni bir cihaz almayı düşünebilirsiniz).

### Ekran kilidinde PIN veya parola kullanın - biyometrik kullanmayın

Bilgisayarlarımızın aksine mobil cihazlarımız neredeyse sürekli açık kalırlar. Bu sebeple tüm diskiniz şifreli bile olsa açık bulunan cihazınıza her isteyen erişebiliyorsa muhtemelen pek de güvende sayılmazsınız. Ekran kilidinizi 4-6 haneli bir PIN olarak belirleyip kabaca 3 ayda bir [Zarola](https://zarola.oyd.org.tr) yöntemi ile değiştirin veya bir parola belirleyip daha uzun aralıklarla değiştirin.

Parmak izi, yüz tanıma gibi biyometrik yetkilendirme sistemleri doğaları gereği güvensizdir. Her ne kadar şirketler bunların aşılamaz olduklarını iddia etseler de çoğu zaman bu tip sistemlere karşı etkili saldırılar yapılmıştır ve en başarılısı [ebeveyninin parmağına uyuduğu sırada telefonunu dokundurup binlerce dolarlık oyun satın alan çocuğun zekasını aşamaz.](https://www.usatoday.com/story/news/nation/2016/12/28/girl-uses-sleeping-moms-thumbprint-pokemon/95907370/) Bu sebeple biyometrik giriş yöntemleri kullanacaksanız bunları ikinci aşama olarak değerlendirip hem PIN/parola hem biyometrik kullanın. Şayet biyometrik verileriniz bir şekilde bir gün çalınırsa yeni bir parmak veya yüz alamayacağınızı unutmayın.

**Yüksek risk taşıdığınızı düşünüyorsanız, cihazınızı size açtıracak kişinin Avrupa İşkencenin Önlenmesi Komitesi'nin kararlarını umursamayacağını asla unutmayın.**

### Ekranınızı saklayın

En büyük ihlaller en küçük tedbirsizliklerden yaşanabilir. Muhtemelen yüksek bütçeli kırma girişimleri yakınlarımızın telefonlarımızı kurcalamasından daha az olası. Bu sebeple ekran parolanızı veya PIN'inizi girerken ve genel olarak cihazınızı kullanırken telefonunuzun ekranını omzunuzun üstünden bakacak kişilerden sakının. Buna kanıksadığınız güvenlik kameraları da dahildir. Paranoyakça gelebilir ama cihazınızı koruyan en önemli veriyi bu şekilde ortalığa saçmanız muhtemelen her şeyi riske atmanızla eşdeğerdir.

### Kapkaça karşı tedbir alın

Her türlü tedbiri almış olabilirsiniz ama bir an vardır ki cihazınız olabildiğince korunaksızdır. Telefonunuzu kullandığınız an! Bu noktada hem cihazınız açık hem de ekran kilidi yok. Pratik olarak o anda telefonu elinde bulunduran herkes neredeyse her işlemi cihazınız ile yapabilir, [bu bir şaka değil](https://www.bbc.com/news/uk-38183819). Haliyle telefonunuzun elinizden kapılması durumunda tedbir almak için [Privatelock](https://f-droid.org/en/packages/com.wesaphzt.privatelock/) kullanabilirsiniz.

### Bildirimlerin kilit ekranında görülmesine izin vermeyin

Bankanızdan gelen 2FA kodları, sevdiklerinizden gelen yazışmalar, en güncel dedikodular ve hepsi açıkça cihazınızın kilit ekranında görünüyorsa mahremiyetiniz ile birlikte güvenliğiniz de olduğu gibi çöpe gidebilir. Ayarlarınızdan kilit ekranında görülecekleri sınırlayın.

### Bilmediğiniz cihazlara bağlamayın

Bu öneri hem tanınmadık Wi-Fi ağlarını hem de artık her yerde bulunan USB şarj çıkışlarını kapsar. Cihazınızı bu bilinmeyen ortamlara maruz bırakmak sizi riske sokabilir. Ya kendi şarj cihazınızı kullanın ya da bu tip çıkışları kullanmak zorundaysanız [USB kondom](https://en.wikipedia.org/wiki/Juice_jacking#Mitigation) kullanın. Ayrıca yeni Android sürümlerinde "Şarj için USB" diye bir seçenek de vardır.

### Kablosuz aygıtlarınızı kullanmıyorsanız kapatın

Wi-Fi ve Bluetooth gibi teknolojiler kablosuz olarak sizinle ilgili pek çok veriyi ortalığa saçabilirler. Bunun yanı sıra takip edilmeniz için de elverişli bir araç olarak kullanılabilirler. Bu sebeple kullanmadığınız her zaman bu donanımları kapatın.

### Signal kullanın

**Signal** özgür bir anlık yazışma yazılımı olarak telefonunuzla gelen normal yazışmaya güvenli bir alternatif oluşturmaktadır. WhatsApp veya Telegram gibi çalışsa da çok daha güvenlidir.

Neden Signal kullanmalısınız?

* GSM hizmet sağlayıcınız size gönderilen her mesajın bir kopyasını tutmaktadır. Signal ile GSM hizmet sağlayıcınız ne mesajlarınıza ne de iletişimde bulunduğunuz insanlara ulaşabilir.
* Bir saldırgan için telefon numaranızı ele geçirmek görece kolaydır. Konuştuğunuz kişinin başına bu geldiğinde Signal, kişinin "güvenlik numarası'nın" değiştiğine dair bir uyarı verir. Bu aynı zamanda biri yeni telefon edindiğinde de gerçekleşir. Güvenlik numarasını doğrulamak aranızdaki yazışmaların kimse tarafından okunmadığını garanti eder.
* Signal aynı zamanda güvenli ses iletişimi için de kullanılabilir. GSM hizmet sağlayıcınız kimi aradığınızı, kimin sizi aradığı ve aramaların uzunluğuna ilişkin kayıt tutar. Signal ile yaptığınız aramalarda GSM servis sağlayızınız bu bilgilere ulaşamaz. Cihazınız güvenli olduğu sürece aramalarınızın içeriği ve uzunluğu gizli kalacaktır.
* WhatsApp, Telegram veya Wire gibi diğer "güvenli" olarak pazarlanan yazışma programları Signal ile kıyaslanınca çokça soruna sahiptir.

Daha fazla bilgi için, [Security Planner / Signal](https://securityplanner.org/#/tool/signal)'e bakın.

### Silence kullanın

**[Silence](https://silence.im/)**, Android için geliştirilmiş bir SMS (kısa mesaj servisi) yazılımıdır. Silence'ı kurduktan sonra telefonunuzun standart SMS programı olarak atarsınız ve tüm SMS'leriniz Silence'e gelir. Normal koşullarda her SMS programı gibi SMS'leriniz gelir ve gider ama Silence kullanan kişilerle anahtar değişimi yaptıktan sonra tamamen uçtan uca şifreli SMS yazışması yapabilirsiniz.

### Fotoğraf çekerken güvenlik

Telefonunuzun kamerası, çektiğiniz her fotoğrafa yüksek olasılıkla hassas çokça veriyi eklemektedir. İnternet'te paylaştığınız bir gönderinin nasıl kullanılacağını bilemeyeceğinizden, fotoğrafların taşıdığı kişisel veriyi paylaşmadan önce silmek iyi bir fikirdir.

Fotoğraflarınızda "geotagging" sorununu engellemek için, kamera ayarlarınızı açın ve konum bilgisini kaydetme ayarlarını kapatın.

Geotagging kapalı iken bile kamera yazılımınız cihazınızın modelini ve diğer potansiyel olarak hassas veriyi fotoğraflara kaydedecektir. Bu durumdan kurtulmanın en iyi yolu ayrı bir yazılımla EXIF verisini fotoğraf dosyalarından silmektir. Bu yazılımlar aynı zamanda konum bilgisini de çektiğiniz geçmiş fotoğraflardan silmek için de kullanılabilir.

Daha fazla bilgi için: [Fotoğraflardan EXIF üstverisini silmenin 3 yolu](https://www.makeuseof.com/tag/3-ways-to-remove-exif-metadata-from-photos-and-why-you-might-want-to/).

[replicant]:https://replicant.us
[lineageos]:https://lineageos.org
[grapheneos]:https://grapheneos.org
[lineageos devices]:https://wiki.lineageos.org/devices/
[grapheneos devices]:https://grapheneos.org/faq#device-support
[baseband modem]:https://en.wikipedia.org/wiki/Baseband_processor
