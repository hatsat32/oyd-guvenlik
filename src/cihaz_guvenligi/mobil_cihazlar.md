# Mobil Cihazlar

<!-- toc -->

Taşınabilir cihazlar günlük hayatın vazgeçilmez parçaları haline gelmiş durumdalar. Artık bilgisayar denilince dizüstü bilgisaylar akla gelmekte, her telefon kullanıcısı bir şekilde "akıllı" mobil cihazlar kullanmakta. Bu gelişme insanların sürekli bağlı kalmasını ve tüm toplumsal örgütlenmenin bu bağlılığa dayanmasına sebep olmakta ve bu cihazlarla ürettilen bilgi giderek artmakta.

Söz konusu mobil cihazlar olunca çalınma, kaybolma ve bir şekilde istenmeyen ellere düşme ihtimali taşınabilirliklerinden dolayı çok olası olmakta. Bu durum cihazların bilinçli veya bilinçsiz olarak içerdikleri çok miktardaki kişisel ve değerli bilgi ile birleştiğinde konuya ilişkin güvenlik tedbirlerinin de özellikle değerlendirilmesi gerekmekte.

## Özgürlük sorunu

Günümüzdeki tüm genel son kullanıcı ürünleri gibi mobil cihazlar da özgürlük düşüncesi ile imal edilmemektedirler. Özgür olmayan sistemlerin üreticilerine hizmet ettiği gerçeği kullanıcıların güvenliğini de belirsizlik içine itmektedir.

* Donanım özgürlüğü: Modern bilişim aygıtlarının donanı seviyesindeki özgürlüğü neredeyse yok denecek düzeydedir. [Tamir etme](https://oyd.org.tr/yazilar/donanim-ozgurlugu/)imkanlarının kısıtlanmasından, [DRM](https://oyd.org.tr/yazilar/drm/) uygulamalarına kadar pek çok yansıma gözlemlenebilir. Bu durumu değiştirmek üzere [projeler](https://www.pine64.org/pinephone/) var olsa da çip üreticileri gibi alternatifi zor bulunan kritik parçaların ayakbağı özgür donanımların elde edilmesine hala engel olmaktadır.

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

### Sürekli bağlantı ihtiyacı ve GSM destekli cihazlar

Şayet durumun değerlendirmeniz sonucunda modern cep telefonu kullanımı alışkanlıklarını sürdürmek zorundaysanız Baseband modemi taşıyan bir cihazı alıp kullanmak zorunda kalacaksınız. Bu teorik olarak özgür olmayan ve kürsel bir ağ ile sürekli bağlantı kuran bir işlemciyi cihazınızın üzerinde yetki sahibi olabileceği riskini de taşımak anlamına gelmekte. Genel kanı, özellikle hedef alınmayacaksanız veya hedef gözetmeyen toplu bir gözetim/saldırının nesnesi olma ihtimaliniz düşük ise bu tehlikeyi taşımanın makul olduğu yönündedir.

Bu noktada yapacağınız cihaz tercihi baseband modemden doğan endişelerinizi azaltabilir. [Baseband izolasyonu](https://www.replicant.us/freedom-privacy-security-issues.php) cihazların ana işlemcisi ile baseband modeminin birbirinden ayrı olmasını ifade etmektedir. Bu şekilde tasarlanmış cihazlarda işletim sisteminin ve işlediği bilgilerin modem tarafından görülmesi mümkün olmadığı gibi modem sisteme doğrudan müdahale edememekte. Bu anlamda işletim sistemi modemi kapatmak istediğinde (uçak modu) modemin gerçekten kapandığına inanmak mümkün olabilmekte.

Hangi telefonların bu imkanı sunduğunu öğrenmek ise başlı başına bir sorun olabilmekte. [Replicant projesinin](https://www.replicant.us/) tercih ettiği cihazlar özellikle baseband izolasyonu imkanı sağlamakta. [GrapheneOS](https://grapheneos.org) projesi de sanallaştırma aracılığı ile cihaz işlemcisi ile basband arasında bağlantıları kontrol edebilmekte. [Pinephone](https://www.pine64.org) da [wifi ve modem donanımlarını işlemciden ayrı tutmakta.](https://www.pine64.org/2020/01/24/setting-the-record-straight-pinephone-misconceptions/) Benzer şekilde [Librem5](https://puri.sm/products/librem-5/) cihazlar da baseband modem'i sistemde ayrı çalıştırmakta.

Sayılan cihazların ya modern kullanım için eski ya da Türkiye'de bulunması zor cihazlar olması gerçeği söz konusu tavsiyeyi bir noktada boşa çıkarmakta. Bir cihazın izolasyon konusundaki kapasitesini öğrenmek çoğu zamandan pek de kolay bulunmayan tasarım detaylarını incelemeyi gerektirdiğinden yeni cihazların keşfi kolay olmamakta.

Şayet sayılan projelere dahil bir cihazı kullanma imkanınız var ise GSM şebekesini kullanırken en azından cihazınızı kontrol altında tumanız mümkün olabilir.

### Wifi

Günümüzdeki internet üzerinden iletişim hizmet ve sistemlerinin gelişmişliği altında artık sesli ve yazılı iletişimin sadece internet bağlantısı ile sağlanması çok kolaylaşmış durumda. [Signal](yazisma_guvenligi/signal.md) veya [Jitsi](https://meet.jit.si) gibi araçların sağladığı imkanlar ile artık GSM ses bağlantısına ihtiyaç eskisi kadar yok. Bu neden ile bir kişi internet bağlantısını sağlayabildiği her yerden iletişim kurması mümkün.

Buna e-posta gibi diğer iletişim ihtiyaçlarının da çoğunlukla İnternet üzerine taşındığı gözönüne alındığında bir kişinin GSM şebekesinin sağladığı klasik ses ve yazılı (SMS) bağlantı imkanlarına ihtiyacının az olması muhtemel. Özellikle [VOIP](https://en.wikipedia.org/wiki/VoIP) benzeri klasik telefon hizmetini İnternet üzerinden sağlayan servislerle telefon ihtiyacının da karşılanabilmesi mümkün.

Özellikle büyük şehirlerde pek çok yerde wifi bağlantısının bulunabildiği durumlarda GSM modemi içermeyen veya izolasyonu yeterli olan bir cihazı sadece wifi üzerinden kullanmak fikri değerlendirilebilir.

### Harici wifi modem

Modern cihazlardaki GSM modem izolasyonunun sıkıntısı ve wifi bulunmayan alanlarda bağlantı ihtiyacı için bugünlerde yaygın şekilde kullanılan wifi hotspot olarak da bilinen 4G modemlerin kullanılan mobil cihaz ile eş olarak kullanılması bir seçenek. Bu kurulum hem kişilere iyi derecede bir baseband izolasyonu sağlarken hem de kişilerin sürekli bağlantı ihtiyaçlarını karşılayabilir. Lakin GSM sistemlerinin mahremiyet yönünden getirdiği sorunlar ve bu durumun yansıması olabilecek güvenlik endişelerini ortadan kaldırmamakta.


[Hangi Mobil Cihaz](mobil_cihaz_tercih.md)

[Mobil Cihaz Genel Tavsiyeler](mobil_cihaz_tavsiyeler.md)
