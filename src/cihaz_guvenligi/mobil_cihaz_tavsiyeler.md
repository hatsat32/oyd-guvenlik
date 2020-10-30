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
