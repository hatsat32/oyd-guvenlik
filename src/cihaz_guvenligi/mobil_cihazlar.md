# Mobil Cihazlar

## Hangi taşınabilir cihaz benim için uygun?

Cihazınızı içinde bulunduğunuz duruma göre seçmelisiniz:

* **Yüksek Risk**: Bir devletin veya uzman ajanlık şirketlerinin hedefi olacağınızdan şüpheleniyorsanız.
* **Orta Risk**: An itibari ile hedef değilsiniz fakat bir saldırganın cihazlarınıza fiziksel erişim sağlaması durumunda kolay hedef olmayı tercih etmiyorsunuz.
* **Düşük Risk**: Taşınabilir cihazlarınızı hassas veriler için kullanmıyorsunuz.

### Yüksek risk

Eğer riskiniz yüksek ise, **cep telefonunuzu hassas hiç bir şey için kullanmayın**. Bunun sebebi, tüm telefonların "baseband modemi" olarak adlandırılan, sizi kablosuz telefon ağına ("hücresel ağ") bağlayan bir donanım içermesidir. Bu modemler özel mülk ve tonla uzaktan kötüye kullanılabilecek güvenlik açığı içermektedir. Bir kere aşıldıktan sonra, baseband modem iletişiminizi takip etmek ve kişisel verilerinizi elde etmek için kullanılabilir.

[Replicant](https://www.replicant.us/) tamamen özgür bir android dağıtımı olarak sadece belirli cihazlar üzerinde çalışmaktadır. Çalıştığı cihazların temel özelliği baseband modemi işlemciden izole etmenin bir imkanı olmasıdır. Şayet mobil cihaz kullanmanız gerekiyor ve bu cihaz ile önemli veriler işleyecek iseniz Replicant kurulu bir telefon iyi bir tercih olabilir. Özgür olmayan sürücülerden dolayı wi-fi ve bluetooth gibi donanımların çalışmayacağını düşünerek hareket etmeniz önerilir.

Cep telefonlarına alternatif olarak Wi-Fi desteği olan ama hücresel ağa bağlanmayan bir tablet satın alabilirsiniz. Bu tip cihazlar basband modem içermemekte ve uzaktan saldırılara çok daha dayanıklıdır. Sadece Wi-Fi içeren bir cihaz ile hala hücresel ağa, ayrı bir taşınabilir hotspot cihazı ile bağlanabilirsiniz.

NOT: Uçak modu yeterli değildir. Cihazınıza bağlı olarak, uçak modunda bile baseband modemi hala çalışıyor ve cihazınızı saldırılara açık tutuyor olabilir.

Tavsiye edilen sadece Wi-Fi destekleyen cihazlar:

* [Samsung Note 2](https://redmine.replicant.us/projects/replicant/wiki/GalaxyNote2N7100) veya [Samsung Galaxy S 3 (I9300)](https://redmine.replicant.us/projects/replicant/wiki/GalaxyS3I9300)
* [Pixel C](https://en.wikipedia.org/wiki/Pixel_C) veya [Pixelbook](https://en.wikipedia.org/wiki/Google_Pixelbook).
* [iPad](https://en.wikipedia.org/wiki/IPad), fakat sadece **hücresel ağ desteklemeyen** modeller.

### Orta risk

Taşınabilir cihazınızda; devletlerin, şirketlerin veya meraklı insanlar tarafından elde edilmesini istemediğiniz hassas veriler mi var? Elbette var, herkesin var!

Bu durumda biri cihazınızı bulduğunda veya çaldığında onların işini olabildiğince zorlaştırmak istemeniz çok doğal.

Şayet hiç uğraşmayacağım diyorsanız kendinizi Apple şirketinin sinsice yumuşak kollarına bırakıp modern bir Iphone alabilirsiniz. Pek çok gerçek olayda bu cihazlara örgütlü devletler dışında kolaylıkla erişilemediği görüldü. Lakin Apple şirketinin Çin ile yaşadığı aşk, yakın zamanda özgür olmayan yazılımında bulunan açıklar ve İsrail'li bir şirketin 1000 ABD dolarına her Iphone'un kilidini kırabildiği iddiası ile yaşamanız gereklidir.

Tavsiyemiz uygun bir cihaz alarak üzerinde GrapheneOS veya LineageOS android dağıtımları çalıştırmanız ve Google, Facebook gibi hiç bir casus şirketin yazılımları dahil özgür olmayan yazılımlar çalıştırmamanızdır. GrapheneOS ve LineageOS piyasadan alabileceğiniz pek çok cihaza kolaylıkla kurulabilen ve mahremiyetinize önem veren toplulukların geliştirdiği işletim sistemleridir.

Tavsiye edilen cihazlar:

* **LinegaOS için**;
	* [LG G3](https://wiki.lineageos.org/devices/d855) Türkiye'de kolaylıkla bulunabilen, temizi için biraz araştırma gerektiren ama zamanına göre çok iyi donanıma sahip bir cihazdır. LineageOS kurulumu rootlama gereğinden dolayı biraz baş ağrıtabilir ama fiyat/performansta çok başarılıdır.
	* [Sony Xperia Z](https://wiki.lineageos.org/devices/yuga) Görece eski bir donanım olan Z Türkiye'de bolca ve ucuza bulunabiliyor. LineageOS kurulumu da çok kolay. Lakin donanım yaşını göstermekte ve cihazınızı sonuna kadar kullanıyorsanız sizi tatmin etmeyebilir.
	* [Xiaomi Redmi 4(X)](https://wiki.lineageos.org/devices/santoni) Daha modern bir donanım olarak Redmi 4 performans isteyen kullanıcılar için iyi bir tercih olabilir.

* **GrapheneOS için**;
	* [Pixel](https://grapheneos.org/#device-support) Google Pixel cihazların tamamına GraphenOS kurulabilmekte fakat uzun dönemli destek için Graphene 3 serisi cihazları önermekte.

### Düşük risk

Telefonunuzu kilitsiz öylece ortalıkta mı bırakıyorsunuz? O zaman ya başınıza gelecekleri hak ediyorsunuz ya da gerçekten taşınabilir cihazlarınızda hiç bir şey olmadığını düşünüyorsunuz. Ne yazık ki modern taşınabilir cihazlar İnternet'e bağlı oldukları ve kullanıldıkları sürece siz fark etmeseniz de çokça veri üretir ve kaydederler. Bu verilerden belki haberiniz yoktur ama pekala bilgili bir kişi -ki bu her bilgisayar sorunuzda aradığınız arkadaşınız bile olabilir- bu bilgilere ulaşmanın bir yolunu bilebilir.

Bu sebeple riskinizin düşük olduğuna eminseniz ve yanıldığınız için pişman olmayacaksanız pekala herhangi bir telefon alıp sadece ekran kilidi kullanarak hayatınızı sürdürebilirsiniz.

# Genel tavsiyeler

## Cihazlarınızı yanınızdan ayırmayın

Cihazlarınızı fiziksel olarak yanınızda tutmak her zaman iyi bir fikirdir. Aksi takdirde bir saldırganın cihazınıza girmek, verilerinizi ele geçirmek ve gelecekteki etkinliklerinizi izlemek amacı ile kötücül yazılım yüklemesine fırsat doğabilir.

Cihazlarınızın zafiyeti tavsiye edilen donanımları kullanıp kullanmadığınıza, [şifrelemenin](cihaz-şifreleme.md) etkinleştirilip etkinleştirilmediğine ve cihazınızı bir parola veya PIN ile koruyup korumadığınıza bağlıdır

**Bir saldırganın cihazınıza girebilme olasılığı:**

<table class="table">
<tr>
  <th>Cihazınız</th>
  <th>Yetkin saldırgan</th>
  <th>Eğitimli saldırganr</th>
  <th>Olağan saldırgan</th>
</tr>
<tr>
  <td>Tavsiye edilen cihaz + Şifrelenmiş + Kilitli</td>
  <td>DÜŞÜK</td>
  <td>ÇOK DÜŞÜK</td>
  <td>HİÇ</td>
</tr>
<tr>
  <td>Tavsiye edilen cihaz + Kilitli</td>
  <td>ORTA</td>
  <td>DÜŞÜK</td>
  <td>ÇOK DÜŞÜK</td>
</tr>
<tr>
  <td>Normal cihaz + Şifreli + Kilitli</td>
  <td>YÜKSEK</td>
  <td>ORTA</td>
  <td>DÜŞÜK</td>
</tr>
<tr>
  <td>Normal cihaz + Kilitli</td>
  <td>ÇOK YÜKSEK</td>
  <td>YÜKSEK</td>
  <td>ORTA</td>
</tr>
<tr>
  <td>Kilitsiz</td>
  <td>KESİN</td>
  <td>KESİN</td>
  <td>KESİN</td>
</tr>
</table>

Saldırgan tipleri:

* **Yetkin saldırgalar** Kilitli telefonlara girmekte uzmanlaşmış büyük devletleri ve uluslararası şirketleri kapsar.
* **Eğitimli saldırganlar** Yerel kolluk kuvvetlerini ve telefon kıran adli tıp şirketlerini kapsar.
* **Olağan saldırganlar** Özel donanım sahibi olmayan yetenekli teknoloji meraklılarını kapsar.

Eğer cihazınızdan uzak kalacaksanız ve cihazınıza girilme ihtimali var ise verilerinizi yedeklemeli, fabrika ayarlarına dönüş yapmalısınız(veya yeni bir cihaz almayı düşünebilirsiniz).

## Ekran kilidinde pin veya parola kullanın / Biyometrik kullanmayın

Bilgisayarlarımızın aksine mobil cihazlarımız neredeyse sürekli açık kalırlar. Bu sebeple tüm diskiniz şifreli bile olsa açık bulunan cihazınıza her isteyen erişebiliyorsa muhtemelen pek de güvende sayılmazsınız. Ekran kilidinizi 4/6 haneli bir pin olarak belirleyip kabaca 3 ayda bir [zarola](https://zarola.oyd.org.tr) yöntemi ile değiştirin veya bir parola belirleyip daha uzun aralıklarla değiştirin.

Parmak izi, yüz tanıma gibi biyometrik yetkilendirme sistemleri doğaları gereği güvensizdir. Her ne kadar şirketler bunların aşılamaz olduklarını iddia etseler de çoğu zaman bu tip sistemlere karşı etkili saldırılar yapılmıştır ve en başarılısı [ebeveyninin parmağına uyuduğu sırada telefonunu dokundurup binlerce dolarlık oyun satın alan çocuğun zekasını aşamaz.](https://www.usatoday.com/story/news/nation/2016/12/28/girl-uses-sleeping-moms-thumbprint-pokemon/95907370/) Bu sebeple biyometrik giriş yöntemleri kullanacaksanız bunları ikinci aşama olarak değerlendirip hem pin/parola hem biyometrik kullanın. Şayet biyometrik verileriniz bir şekilde bir gün çalınırsa yeni bir parmak veya yüz alamayacağınızı unutmayın.

## Ekranınızı saklayın

En büyük ihlaller en küçük tedbirsizliklerden yaşanabilir. Muhtemelen yüksek bütçeli kırma girişimleri yakınlarımızın telefonlarımızı kurcalamasından daha az olası. Bu sebeple ekran parolanızı veya pininizi girerken ve genel olarak cihazınızı kullanırken telefonunuzun ekranını omzunuzun üstünden bakacaklardan sakının. Buna kanıksadığınız güvenlik kameraları da dahildir. Paranoyakça gelebilir ama cihazınızı koruyan en önemli veriyi bu şekilde ortalığa saçmanız muhtemelen her şeyi riske atmanızla eşdeğerdir.

## Kapkaç'a tedbir alın

Her türlü tedbiri almış olabilirsiniz ama bir an var ki cihazınız olabildiğince korunaksız. Telefonunuzu kullandığınız an! Bu noktada hem cihazınız açık hem de ekran kilidi yok. Pratik olarak o anda telefonu elinde bulunduran herkes neredeyse her işlemi cihazınız ile yapabilir. [Bu bir şaka değil](https://www.bbc.com/news/uk-38183819). Hali ile telefonunuzun elinizden kapılması durumunda tedbir almak için [Privatelock](https://f-droid.org/en/packages/com.wesaphzt.privatelock/) kullanabilirsiniz.

## Bildirimlerin kilit ekranında görülmesine izin vermeyin

Bankanızdan gelen 2FA kodları, sevdiklerinizden gelen yazışmalar, en güncel dedikodular ve hepsi açıkça cihazınızın kilit ekranında görünüyorsa mahremiyetiniz ile birlikte güvenliğiniz de olduğu gibi çöpe gidebilir. Ayarlarınızdan kilit ekranında görülecekleri sınırlayın.

## Bilmediğiniz cihazlara bağlamayın

Bu öneri hem tanınmadık wi-fi ağlarını hem de artık her yerde bulunan usb şarj çıkışlarını kapsar. Cihazınızı bu bilinmeyen ortamlara maruz bırakmak sizi riske sokabilir. Ya kendi şarj cihazınızı kullanın ya da zorundaysanız bu tip çıkışları kullanmaya [usb kontom](https://en.wikipedia.org/wiki/Juice_jacking#Mitigation) kullanın.

## Kablosuz aygıtlarınızı kullanmıyorsanız kapatın

Wi-fi ve bluetooth gibi teknolojiler kablosuz olarak sizinle ilgili pek çok veriyi ortalığa saçabilirler. Bunun yanı sıra takip edilmeniz için de elverişli bir araç olarak kullanılabilirler. Bu sebeple kullanmadığınız her zaman bu donanımları kapatın.

## Signal kullanın

**Signal** özgür bir anlık yazışma yazılımı olarak telefonunuzla gelen normal yazışmaya güvenli bir alternatif oluşturmaktadır. WhatsApp veya Telegram gibi çalışsa da çok daha güvenlidir.

Neden signal kullanmalısınız?

* GSM hizmet sağlayıcınız size gönderilen her mesajın bir kopyasını tutmaktadır. Signal ile GSM hizmet sağlayıcınız ne mesajlarınıza ne de iletişimde bulunduğunuz insanlara ulaşabilir.
* Bir saldırgan için telefon numaranızı ele geçirmek görece kolaydır. Konuştuğunuz kişinin başına bu geldiğinde Signal, kişinin "güvenlik numarası'nın" değiştiğine dair bir uyarı verir. Bu aynı zamanda biri yeni telefon edindiğinde de gerçekleşir. Güvenlik numarasını doğrulamak aranızdaki yazışmaların kimse tarafından okunmadığını garanti eder.
* Signal aynı zamanda güvenli ses iletişimi için de kullanılabilir. GSM hizmet sağlayıcınız kimi aradığınızı, kimin sizi aradığı ve aramaların uzunluğuna ilişkin kayıt tutar. Signal ile yaptığınız aramalarda GSM servis sağlayızınız bu bilgilere ulaşamaz. Cihazınız güvenli olduğu sürece aramalarınızın içeriği ve uzunluğu gizli kalacaktır.
* WhatsApp, Telegram veya Wire gibi diğer "güvenli" olarak pazarlanan yazışma programları Signal ile kıyaslanınca çokça soruna sahiptir.

Daha fazla bilgi için, [Security Planner / Signal](https://securityplanner.org/#/tool/signal)'e bakın.

## Silence kullanın

**[Silence](https://silence.im/)** android için geliştirilmiş bir SMS (kısa mesaj servisi) yazılımıdır. Silence'i kurduktan sonra telefonunuzun standart sms programı olarak atarsınız ve tüm SMS'leriniz Silence'e gelir. Normal koşullarda her SMS programı gibi sms'leriniz gelir ve gider ama Silence kullanan kişilerle anahtar değişimi yaptıktan sonra tamamen uçtan uca şifreli sms yazışması yapabilirsiniz.

## Güvenli fotoğraf çekin

Telefonunuzun kamerası, çektiğiniz her fotoğrafa yüksek olasılıkla hassas çokça veriyi eklemekte. İnternette paylaştığınız bir gönderinin nasıl kullanılacağını bilemeyeceğinizden, fotoğrafların taşıdığı kişisel veriyi paylaşmadan önce silmek iyi bir fikirdir.

Fotoğraflarınızda "geotagging" sorununu engellemek için, kamera ayarlarınızı açın ve konum bilgisini kaydetme ayarlarını kapatın.

Geotagging kapalı iken bile kamera yazılımınız cihazınızın modelini ve diğer potansiyel olarak hassas veriyi fotoğraflara kaydedecektir. Bu durumdan kurtulmanın en iyi yolu ayrı bir yazılımla EXIF1 verisini fotoğraf dosyalarından silmektir. Bu yazılımlar aynı zamanda konum bilgisini de çektiğiniz geçmiş fotoğraflardan silmek için de kullanılabilir.

Daha fazla bilgi için: [Fotoğraflardan EXIF üstverisini silmenin 3 yolu](https://www.makeuseof.com/tag/3-ways-to-remove-exif-metadata-from-photos-and-why-you-might-want-to/).
