# Mobil Cihazlar

Taşınabilir cihazlar günlük hayatın vazgeçilmez parçaları haline gelmiş durumdalar. Artık bilgisayar denilince dizüstü bilgisaylar akla gelmekte, her telefon kullanıcısı bir şekilde "akıllı" mobil cihazlar kullanmakta. Bu gelişme insanların sürekli bağlı kalmasını ve tüm toplumsal örgütlenmenin bu bağlılığa dayanmasına sebep olmakta ve bu cihazlarla ürettilen bilgi giderek artmakta.

Söz konusu mobil cihazlar olunca çalınma, kaybolma ve bir şekilde istenmeyen ellere düşme ihtimali taşınabilirliklerinden dolayı çok olası olmakta. Bu durum cihazların bilinçli veya bilinçsiz olarak içerdikleri çok miktardaki kişisel ve değerli bilgi ile birleştiğinde konuya ilişkin güvenlik tedbirlerinin de özellikle değerlendirilmesi gerekmekte.

## Özgürlük sorunu

Günümüzdeki tüm genel son kullanıcı ürünleri gibi mobil cihazlar da özgürlük düşüncesi ile imal edilmemektedirler. Özgür olmayan sistemlerin üreticilerine hizmet ettiği gerçeği kullanıcıların güvenliğini de belirsizlik içine itmektedir.

* Donanım özgürlüğü: Modern bilişim aygıtlarının donanı seviyesindeki özgürlüğü neredeyse yok denecek düzeydedir. [Tamir etme](https://oyd.org.tr/yazilar/donanim-ozgurlugu/)imkanlarının kısıtlanmasından, [DRM](https://oyd.org.tr/yazilar/drm/) uygulamalarına kadar pek çok yansıma gözlemlenebilir. Bu durumu değiştirmek üzere [projeler](https://www.pine64.org/pinephone/) var olsa da çip üreticileri gibi alternatifi zor bulunan kritik parçaların ayakbağı özgür donanımların elde edilmesine hala engel olmaktadır.

* Yazılım özgürlüğü: Günümüzdeki yazılım özgürlüğü mücadelesinin çizgisinde mobil cihazların da yazılımsal özgürlüğü hala ilerleme aşamasında. Bilgisayarlar gibi firmware seviyesinden işletim sistemi ile kullanıcı yazılımlarına kadar pek çok yazılım üreticilerden geldiği hali ile özgür olmamakta. İşletim sistemi ve yazılımlar görece özgürleştirilebilse de hala firmware seviyesi mülk olarak kullanılmak zorunda. Bu bilinmezlikle birlikte bir güvenlik riskini de orta çıkarmakta.

* GSM mahremiyeti: Baseband modem GSM şebekesine bağlantı kuran donanım olarak mobil cihazlarda donanım ve yazılım özgürlüğünün en büyük düşmanı konumunda. Baseband çoğu cihazda ana işlemci ile doğrudan bağlantı halinde, RAM'i ortak kullanmakta ve dilediği veriye ulaşıp işlem yapabilmekte. Bu cihazın yazılımının eski ve özgür olmaması bir risk oluşturmakta ve bu durumun [kötüye kullanıldığı bilinmekte.](https://money.cnn.com/2014/06/06/technology/security/nsa-turn-on-phone/index.html) GSM'in güvenli olduğu varsayılsa bile sistemin tasarımı gereği hizmet sağlayıcı ve uzantısı olarak devletler tüm kullanıcıların anlık olarak nerede olduğunu ve kullanım bilgilerini elde edebilmekte. Bu mahremiyet sorunu duruma göre bir güvenlik sorununa da dönüşebilmekte.

## Risk değerlendirmesi

Mobil cihazların günümüz kullanıcıları için hem mahremiyet hem de güvenlik açısından pek çok istenmeyecek özelliği bulunmaktadır. Bu özelliklerin kimi doğal olarak var olmakta kimileri ise kasıtlı olarak kişileri ve bilgilerini ticarileştirme amacı ile kötüye kullanılmaktadır.

Bugün genel bir tavsiye olarak güvenlik ihtiyacının yüksek olduğu durumlarda ve tehlike doğurabilecek bilgilerin işlenmesinde mobil cihazların kullanılması önerilmez. Hem donanımsal bilinmezlik hem de gerekli güvenlik ihtiyacının karşılanmasının mobil cihazın avantajlarını ortadan çok yüksek oranda kaldırmasından dolayı önemli durumlarda uygun donanımların seçilmesi yerinde olur.

Şayet kullanım ihtiyacı mobil bir donanımı gerektiriyor ve bu gereklilik öngörülen riskleri aşacak durumda ise değerlendirmenin yapılarak gerekli tedbirlerin alınması ile riskin en aza indirilmesi mümkündür.

1. Taşınabilir bir cihaza ihtiyaç var mı?
2. Anlık bağlantı (GSM) gerekli mi?
3. Cihazın korunmasına ne kadar kaynak ayrılabilir?
4. Gerektiğinde cihazı elden çıkarma maliyetine katlanılabilir mi?
5. Kullanım mülk yazılımları gerektiriyor mu?

Yukarıdaki soruların cevaplarına göre en uygun cihaz ve kullanım tasarımının yapılması mümkündür. Tercihlerinize göre farklı cihaz ve kurulumlar yapabilirsiniz. Kullanım koşullarınızı belirledikten sonra cihaz seçimine geçebilirsiniz.

## Kullanım senaryoları

Aşağıda çeşitli kullanım senaryoları belirlenmiştir. Buna göre uygun kullanım önerileri de bulunmaktadır.

1. Mutlaka bağlı olmalıyım
2. wifi wifi
3. Harici wifi modem
4. şifreleme

### GSM modemli cihaz kullanımı

Şayet durumun değerlendirmeniz sonucunda modern cep telefonu kullanımı alışkanlıklarını sürdürmek zorundaysanız Baseband modemi taşıyan bir cihazı alıp kullanmanız gerekli. Bu teorik olarak özgür olmayan ve kürsel bir ağ ile sürekli bağlantı kurma imkanına sahip bir işlemciyi cihazınızın üzerinde yetki sahibi olabileceği riskini de taşımak anlamına gelmekte. Genel kanı, özellikle hedef alınmayacaksanız veya hedef gözetmeyen toplu bir gözetim/saldırının nesnesi olma ihtimaliniz düşük ise bu tehlikeyi taşımanın makul kabul edildiği yönündedir.

Bu noktada cihaz tercihiniz söz konusu riskinizi azaltabilir. [Baseband izolasyonu](https://www.replicant.us/freedom-privacy-security-issues.php) cihazların ana işlemcisi ile baseband modeminin birbirinden ayrı olmasını ifade etmektedir. Bu şekilde tasarlanmış cihazlarda işletim sisteminin ve işlediği bilgilerin modem tarafından görülmesi mümkün olmadığı gibi modem sisteme doğrudan müdahale edememekte. Bu anlamda işletim sistemi modemi kapatmak istediğinde (uçak modu) modemin gerçekten kapandığına inanmak mümkün olabilmekte.




[Hangi Mobil Cihaz](cihaz_guvenligi/mobil_cihaz_tercih.md)










