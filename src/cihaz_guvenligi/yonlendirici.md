# Yönlendirici Güvenliği

<!-- toc -->

Evinizin köşesinde unuttuğunuz, telefon kablosuna bağlı ve sadece İnternet bağlantınız kesildiğinde hatırladığınız küçük siyah kutular güvenliğiniz için önemli bir rol üstlenmektedirler. Bu cihazlar sizi internet servis sağlayıcınıza, cihazlarınızı da bir yerel ağ altında birbirine bağlar.

Modem ile yönlendirici teknik olarak farklı şeylerdir. [Modem (modulator demodulator kelimelerinin birleşimi)](https://en.wikipedia.org/wiki/Modem) iki nokta arasında bağlantı kurularak veri aktarılmasını sağlayan bir cihazdır. Bir zamanların çevirmeli bağlantı için kullanılan 56k modemleri gibi [ADSL](https://en.wikipedia.org/wiki/Asymmetric_digital_subscriber_line) ve [VDSL](https://en.wikipedia.org/wiki/VDSL) teknolojileri de sizi internet servis sağlayıcınıza bağlar. Dünya'da kullanımı artık yok olmakta olsa da Türkiye hala fiberoptik altyapı eksikliği altında bu teknolojileri yaygın olarak kullanmaya devam etmektedir.

[Yönlendirici (router)](https://en.wikipedia.org/wiki/Router_(computing)) bir ağı alt ağlara bölmeye yarayan ve aralarındaki trafiği düzenleyen bir donanımdır. Özel olarak tasarlanmış minik bir bilgisayar olmakla birlikte cihazlarınıza kablosuz bağlantı sağlamak ve denetlemekle görevlidir.

Modem olarak satılan cihazlar aslında bir modem ve yönlendiricinin birleşiminden oluşur. Bu bakımdan modeminizin arkasına bir yönlendirici daha eklemenize engel olan bir şey olmadığı gibi modemi ayrı bir donanım olarak alıp bir yönlendiriciye bağlamanız da mümkündür.

Yönlendiricilerin İnternet bağlantınızda ve yerel ağınıza (cihazlarınızın birbirini görebildiği iç ağınız) hakim olması onları güvenliğinizin önemli bir parçası haline getirmekte. Yönlendiricinizin kontrolünde olan bir kişi aşağıdaki saldırılarla sınırlı olmamakla pek çok saldırıyı gerçekleştirebilir:

* Yerel ağınıza bağlı olan cihazları takip edebilir kaydedebilir.

* İnternet bağlantınızın gittiği yerleri ve şifresiz iletişimleri takip edebilir.

* Sizi güvenliğinizi tehdit edecek şekilde sahte sitelere yönlendirebilir.

* Ağınızdaki diğer cihazlara ulaşıp onların güvenliğini aşabilir.

* Ağınızda bulunan depolama aygıtlarına erişebilir ve dosyalarınızı çalabilir.

Bu tehditler ve bunun gerçekleşme ihtimali düşük olasılıklar içermez. Dünya'da pek çok kere yönlendiriciler yüzünden risk altına girmiş kullanıcılar oldu. Bunun sebepleri arasında; [yönlendirici üreticisinin kötü güvenlik uygulamaları](https://arstechnica.com/information-technology/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/), internet servis sağlayıcılarının dağıttığı yönlendiricilere güvensiz ve onaysız uzaktan erişim portları açması, güncellenmeyen veya güncellemesi artık olmayan cihazlardaki güvenlik açıkları sayılabilir. 

Bu kadar önemli bir cihazın görece önemsiz görüntüsü nedeni ile ihmal ile karşılanması görece doğal karşılanabilir fakat çok basit tedbir ve değişikliklerle söz konusu cihazların güvenliği sağlanabilir.

## Yönlendirici ve modem arayüz parolanızı değiştirin

Ağınızda bulunan her cihaz yönlendiricinizin ayarlarının yapıldığı arayüze bir web tarayıcısı aracılığı ile erişebilir. Bu durumda cihazınızın ayarlarının değiştirilmesi gibi istenmeyen sonuçlar ortaya çıkabilir. Pek çok yönlendirici standart "admin/admin" gibi parolalarla geldiklerinden bu ayarın kullanımın ilk anında değiştirilmesi gereklidir.

Yönlendiricilerde farklı olabilmekle birlikte çoğu yönlendirici `192.168.1.1` adresinden erişilebilir. Cihazınızdaki web tarayıcısına adresi girdiğinizde karşınıza giriş sayfası çıkacaktır. Buradan cihazınıza ait standart parola ile giriş yaptıktan sonra ayarlar içinden bu parolayı değiştirebilirsiniz.

## Wifi parolalarınızı güvenli kılın

Wifi güvenliği neredeyse her köşede verilen bir tavsiye fakat pek çok insan için pratik gereklilikler altında ihmale uğramakta. Wifi ev ağınızı radyo dalgaları ile belki de yüzlerce metre uzaklara ulaştırmakta ve hiç göremediğiniz biri tarafından erişilebilmesine imkan verebilmekte.

Belki pek çok insan wifi güvenliğinin gerekliliğinin farkında ama misafirlerine güvenli bir parolayı aktarmanın zorluğuna katlanmamak için cep telefonu numaralarından "12345678" gibi bariz girdileri parola olarak kullanmakta. 

Bu neden ile wifi parolalarınızı [zarola](https://zarola.oyd.org.tr) veya rastgele 16-24 karakter uzunluğunda bir değer ile değiştirmeniz tavsiye edilir. Zarola ezberlemesi kolay olacağından misafirlerinizin veya ağa yeni eklemek istediğiniz cihazların kolaylıkla dahil edilmesine imkan verirken rastgele parola ise sıklıkla parola değiştirmenize imkan sağlayacaktır.

Kablosuz ağınızın kullandığı şifreleme algoritmasının da günümüz gerekliliklerine uygun olduğunu denetleyin. WEP artık güvenli sayılmayan ve aşılması çok kolay bir güvenlik tedbiri olarak kesinlikle tavsiye edilmemektedir. Bunun yerine modern WPA2 şifrelemeyi kullanmanız güvenli bir wifi ağı için gereklidir.

Ağınıza güvendiğiniz misafirler olsa bile bilinmeyen cihazları eklemeniz önerilmez. Bu bakımdan kimi yönlendiriciler yalıtılmış ve sadece İnternet bağlantısı sağlayan "misafir" ağları oluşturabilir. Cihazınız bu imkanı sağlıyor ise kullanmanız kesinlikle tavsiye edilir. Şayet parolanızı misafirlerinizle kolaylıkla paylaşmak isterseniz [karekod](https://qifi.org/) yardımı ile cihazların kolayca tarayıp bağlantı sağlayabileceği karekodlar oluşturabilirsiniz.

## Mümkün ise wifi kullanmayın

Wifi çok rahat bir kullanım sağlasa bile her halukarda cihazınızı erişiminiz olmayan dış dünyaya açarak bir saldırı imkanı doğurur. Tüm yazılımlar ve donanımlar gibi bilinmeyen güvenlik açıklarının var olduğu bir dünyada bu kimi zaman kabul edilemeyecek bir risk taşıyabilir.

Kablolu bağlantılar hem daha istikrarlı bağlantı sağlar hem de ağınız ile ilgili bilgilerin dışarıya radyo dalgaları ile sızmasını engeller. Bu neden ile şayet wifi ağına ihtiyacınız özellikle yok ise cihazlarınızı kablo ile bağlayıp wifi ağınızı tamamen kapatmanız faydalı olabilir. Bu aynı zamanda Google gibi mahremiyet düşmanı şirketlerin ağınızın konumunu kullanıp kaydetmesine de engel olacaktır.

## Cihazlarınıza fiziki erişimi sınırlandırın

Tüm güvenliği kritik cihazlarınız gibi yönlendiricinizin de ortalık yerde durması uygun bir durum sayılmaz. Bu bakımdan cihazınızı gözden uzak mümkünse erişimi kolay olmayan bir alanda saklamanız önerilir. Bu cihazınıza doğrudan erişimi engelleyerek çeşitli müdahaleleri görece zor kılacağından güvenliğinize katkı sunacaktır.

## Cihazınızı güncelleyin

Pek çok yönlendirici satın alındıkları tarihten itibaren üreticisi tarafından belirli süreler ile güncellemeler ile desteklenmektedir. Ne yazık ki görece ucuz ve önemsenmeyen ürünler olmakla hem üreticiler tarafından gerekli güvenlik güncellemeleri bir süre yapılmamakta ve kullanıcılar da gerekli güncellemeleri zamanında uygulamamakta. Bu tip açıklardan dolayı pek çok güvenlik açığı kablosuz bağlantı veya uzak erişim ile kullanıcılarının güvenliğini tehdit edebilmektedir.

Cihazınızın yönetim paneline girerek güncelleme seçeneklerine bakabilir veya üreticinin web sayfasından elinizdeki modelin sunulan en güncel yazılımına bakabilirsiniz. Şayet üreticiniz artık cihazınıza destek vermiyor ise özgür bir yazılım ile cihazınızı güncelleyebilir veya yeni bir modele geçerek destek alabilirsiniz.

## Cihazınızı özgürleştirin

Her ne kadar yukarıdaki tavsiyeler genel olarak tüm yönlendiriciler için geçerli olsalar da üreticilerin pek de özen göstermedikleri ürünler olmakla son kullanıcı yönlendiricileri pek çok mülk yazılım içermekte ve potansiyel olarak incelenememiş güvenlik açıkları içerme ihtimali taşımakta. Bu duruma en iyi çözüm ise yazılım özgürlüğünden geçmekte. LibreCMC ve OpenWRT sayılması gereken en önemli projeler olmakla belirli donanımları güncel özgür sistemlerle güncelleyerek güvenliğinizi hatrısayılır miktarda arttırabilir ve cihazlarınızın kabiliyetini de geliştirebilirsiniz.

* [Özgür yönlendirici rehberi](/cihaz_guvenligi/librecmc_openwrt.md)




