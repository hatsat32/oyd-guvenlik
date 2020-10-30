# Mobil Cihazlar

Taşınabilir cihazlar günlük hayatın vazgeçilmez parçaları haline gelmiş durumdalar. Artık bilgisayar denilince dizüstü bilgisaylar akla gelmekte, her telefon kullanıcısı bir şekilde "akıllı" mobil cihazlar kullanmakta. Bu gelişme insanların sürekli bağlı kalmasını ve tüm toplumsal örgütlenmenin bu bağlılığa dayanmasına sebep olmakta ve bu cihazlarla ürettilen bilgi giderek artmakta.

Söz konusu mobil cihazlar olunca çalınma, kaybolma ve bir şekilde istenmeyen ellere düşme ihtimali taşınabilirliklerinden dolayı çok olası olmakta. Bu durum cihazların bilinçli veya bilinçsiz olarak içerdikleri çok miktardaki kişisel ve değerli bilgi ile birleştiğinde konuya ilişkin güvenlik tedbirlerinin de özellikle değerlendirilmesi gerekmekte.

## Özgürlük sorunu

Günümüzdeki tüm genel son kullanıcı ürünleri gibi mobil cihazlar da özgürlük düşüncesi ile imal edilmemektedirler. Özgür olmayan sistemlerin üreticilerine hizmet ettiği gerçeği kullanıcıların güvenliğini de belirsizlik içine itmektedir.

<<<<<<< HEAD
* Donanım özgürlüğü: Modern bilişim aygıtlarının donanı seviyesindeki özgürlüğü neredeyse yok denecek düzeydedir. [Tamir etme](https://oyd.org.tr/yazilar/donanim-ozgurlugu/)imkanlarının kısıtlanmasından, [DRM](https://oyd.org.tr/yazilar/drm/) uygulamalarına kadar pek çok yansıma gözlemlenebilir. Bu durumu değiştirmek üzere [projeler](https://www.pine64.org/pinephone/) var olsa da çip üreticileri gibi alternatifi zor bulunan kritik parçaların ayakbağı özgür donanımların elde edilmesine hala engel olmaktadır.
=======
Eğer riskiniz yüksek ise, **cep telefonunuzu hassas hiçbir şey için kullanmayın**. Bunun sebebi, tüm telefonların sizi kablosuz telefon ağına (hücresel ağ) bağlayan, "[baseband modem][]" olarak adlandırılan bir donanım içermesidir. Bu modemler özel mülktür ve uzaktan kötüye kullanılabilecek pek çok güvenlik açığı içermektedir. Bir kere aşıldıktan sonra, [baseband modem] iletişiminizi takip etmek ve kişisel verilerinizi elde etmek için kullanılabilir.
>>>>>>> 6807e00a2b0f975f38fc8d9fb647201fc4670ac2

* Yazılım özgürlüğü: Günümüzdeki yazılım özgürlüğü mücadelesinin çizgisinde mobil cihazların da yazılımsal özgürlüğü hala ilerleme aşamasında. Bilgisayarlar gibi firmware seviyesinden işletim sistemi ile kullanıcı yazılımlarına kadar pek çok yazılım üreticilerden geldiği hali ile özgür olmamakta. İşletim sistemi ve yazılımlar görece özgürleştirilebilse de hala firmware seviyesi mülk olarak kullanılmak zorunda. Bu bilinmezlikle birlikte bir güvenlik riskini de orta çıkarmakta.

* GSM mahremiyeti: Baseband modem, GSM şebekesine bağlantı kuran donanım olarak mobil cihazlarda donanım ve yazılım özgürlüğünün en büyük düşmanı konumunda. Baseband çoğu cihazda ana işlemci ile doğrudan bağlantı halinde, RAM'i ortak kullanmakta ve dilediği veriye ulaşıp işlem yapabilmekte. Bu cihazın yazılımının eski ve özgür olmaması bir risk oluşturmakta ve bu durumun [kötüye kullanıldığı bilinmekte.](https://money.cnn.com/2014/06/06/technology/security/nsa-turn-on-phone/index.html) GSM'in güvenli olduğu varsayılsa bile sistemin tasarımı gereği hizmet sağlayıcı ve uzantısı olarak devletler tüm kullanıcıların anlık olarak nerede olduğunu ve kullanım bilgilerini elde edebilmekte. Bu mahremiyet sorunu duruma göre bir güvenlik sorununa da dönüşebilmekte.

## Risk değerlendirmesi

Mobil cihazların günümüz kullanıcıları için hem mahremiyet hem de güvenlik açısından pek çok istenmeyecek özelliği bulunmaktadır. Bu özelliklerin kimi doğal olarak var olmakta kimileri ise kasıtlı olarak kişileri ve bilgilerini kontrol etmek amacı ile kötüye kullanılmaktadır.

Bugün genel bir tavsiye olarak güvenlik ihtiyacının yüksek olduğu durumlarda ve tehlike doğurabilecek bilgilerin işlenmesinde mobil cihazların kullanılması önerilmez. Hem donanımsal bilinmezlik hem de gerekli güvenlik ihtiyacının karşılanmasının mobil cihazın avantajlarını çok yüksek oranda ortadan kaldırmasından dolayı kritik kullanımlarda uygun donanımların seçilmesi yerinde olur.

Şayet kullanım ihtiyacı mobil bir donanımı gerektiriyor ve bu gereklilik öngörülen riskleri aşacak durumda ise değerlendirmenin yapılarak gerekli tedbirlerin alınması ile riskin en aza indirilmesi mümkündür.

1. Taşınabilir bir cihaza ihtiyaç var mı?
2. Anlık bağlantı (GSM) gerekli mi?
3. Cihazın korunmasına ne kadar kaynak ayrılabilir?
4. Gerektiğinde cihazı elden çıkarma maliyetine katlanılabilir mi?
5. Kullanım mülk yazılımları gerektiriyor mu?

Yukarıdaki soruların cevaplarına göre en uygun cihaz ve kullanım tasarımının yapılması mümkündür. Tercihlerinize göre farklı cihaz ve kurulumlar yapabilirsiniz. Kullanım koşullarınızı belirledikten sonra cihaz seçimine geçebilirsiniz.

## Kullanım senaryoları

Aşağıda çeşitli kullanım senaryoları belirlenmiştir. Buna göre uygun kullanım önerileri de bulunmaktadır.

1. Sürekli bağlantı
2. wifi - wifi
3. Harici wifi modem
4. şifreleme

### Sürekli bağlantı ihtiyacı ve GSM destekli cihazlar

Şayet durumun değerlendirmeniz sonucunda modern cep telefonu kullanımı alışkanlıklarını sürdürmek zorundaysanız Baseband modemi taşıyan bir cihazı alıp kullanmak zorunda kalacaksınız. Bu teorik olarak özgür olmayan ve kürsel bir ağ ile sürekli bağlantı kuran bir işlemciyi cihazınızın üzerinde yetki sahibi olabileceği riskini de taşımak anlamına gelmekte. Genel kanı, özellikle hedef alınmayacaksanız veya hedef gözetmeyen toplu bir gözetim/saldırının nesnesi olma ihtimaliniz düşük ise bu tehlikeyi taşımanın makul olduğu yönündedir.

Bu noktada yapacağınız cihaz tercihi baseband modemden doğan endişelerinizi azaltabilir. [Baseband izolasyonu](https://www.replicant.us/freedom-privacy-security-issues.php) cihazların ana işlemcisi ile baseband modeminin birbirinden ayrı olmasını ifade etmektedir. Bu şekilde tasarlanmış cihazlarda işletim sisteminin ve işlediği bilgilerin modem tarafından görülmesi mümkün olmadığı gibi modem sisteme doğrudan müdahale edememekte. Bu anlamda işletim sistemi modemi kapatmak istediğinde (uçak modu) modemin gerçekten kapandığına inanmak mümkün olabilmekte.

Hangi telefonların bu imkanı sunduğunu öğrenmek ise başlı başına bir sorun olabilmekte. [Replicant projesinin](https://www.replicant.us/) tercih ettiği cihazlar özellikle baseband izolasyonu imkanı sağlamakta. [GrapheneOS](https://grapheneos.org) projesi de sanallaştırma aracılığı ile cihaz işlemcisi ile basband arasında bağlantıları kontrol edebilmekte. [Pinephone](https://www.pine64.org) da [wifi ve modem donanımlarını işlemciden ayrı tutmakta.](https://www.pine64.org/2020/01/24/setting-the-record-straight-pinephone-misconceptions/) Benzer şekilde [Librem5](https://puri.sm/products/librem-5/) cihazlar da baseband modem'i sistemde ayrı çalıştırmakta.

Sayılan cihazların ya modern kullanım için eski ya da Türkiye'de bulunması zor cihazlar olması gerçeği söz konusu tavsiyeyi bir noktada boşa çıkarmakta. Bir cihazın izolasyon konusundaki kapasitesini öğrenmek çoğu zamandan pek de kolay bulunmayan tasarım detaylarını incelemeyi gerektirdiğinden yeni cihazların keşfi kolay olmamakta.

Şayet sayılan projelere dahil bir cihazı kullanma imkanınız var ise GSM şebekesini kullanırken en azından cihazınızı kontrol altında tumanız mümkün olabilir.

## Wifi

Günümüzdeki internet üzerinden iletişim hizmet ve sistemlerinin gelişmişliği altında artık sesli ve yazılı iletişimin sadece internet bağlantısı ile sağlanması çok kolaylaşmış durumda. [Signal](yazisma_guvenligi/signal.md) veya [Jitsi](https://meet.jit.si) gibi araçların sağladığı imkanlar ile artık GSM ses bağlantısına ihtiyaç eskisi kadar yok. Bu neden ile bir kişi internet bağlantısını sağlayabildiği her yerden iletişim kurması mümkündür.



[Hangi Mobil Cihaz](cihaz_guvenligi/mobil_cihaz_tercih.md)










<<<<<<< HEAD
=======
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

Fotoğraflarınızda "konum etiketi(geotagging)" sorununu engellemek için, kamera ayarlarınızı açın ve konum bilgisini kaydetme ayarlarını kapatın.

Konum etiketi kapalı iken bile kamera yazılımınız cihazınızın modelini ve diğer potansiyel olarak hassas veriyi fotoğraflara kaydedecektir. Bu durumdan kurtulmanın en iyi yolu ayrı bir yazılımla EXIF verisini fotoğraf dosyalarından silmektir. Bu yazılımlar aynı zamanda konum bilgisini de çektiğiniz geçmiş fotoğraflardan silmek için de kullanılabilir.

Daha fazla bilgi için: [Fotoğraflardan EXIF üstverisini silmenin 3 yolu](https://www.makeuseof.com/tag/3-ways-to-remove-exif-metadata-from-photos-and-why-you-might-want-to/).

[replicant]:https://replicant.us
[lineageos]:https://lineageos.org
[grapheneos]:https://grapheneos.org
[lineageos devices]:https://wiki.lineageos.org/devices/
[grapheneos devices]:https://grapheneos.org/faq#device-support
[baseband modem]:https://en.wikipedia.org/wiki/Baseband_processor
>>>>>>> 6807e00a2b0f975f38fc8d9fb647201fc4670ac2
