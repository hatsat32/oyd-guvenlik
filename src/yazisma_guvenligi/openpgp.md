# Şifreli E-Posta


## E-posta nedir?

Günümüzde e-posta kullanmayan neredeyse kimsenin kalmadığı düşünüldüğünde bu soru anlamsız gelebilir lakin e-postanın güvenliğinden bahsedilmeden önce güvenli kılınmaya çalışılan şeyin tanınması gereklidir.

E-posta İnternet'in ilk yazışma sistemidir. Bugünlerde sayısız yeni iletişim sistemi, yazılımı geliştirilmiş olsa da e-posta hala önemini korumaktadır. E-postayı bu bakımdan değerli kılan özelliklerin başında sistemin [federatif](https://en.wikipedia.org/wiki/Federation_%28information_technology%29) olması ve kullanıcıların bir web tarayıcısından başka bir araca ihtiyaç duymaması gerelebilir.

E-posta federatif olmasının bir özelliği olarak kullanılan hizmet sağlayıcı/sunucu ve yazışılan diğer kişilerin kullandığı sistemler gibi pek çok üçüncü kişiye güven gerektirmektedir. Bu durum sistemi güvenli kılmayı da görece zorlaştırmaktadır. [TLS](https://tr.wikipedia.org/wiki/Transport_Layer_Security) tüm İnternet ile birlikte e-posta güvenliğini de arttırmıştır. Lakin TLS'in yaygınlaşmasından önce [Edward Snowden](https://en.wikipedia.org/wiki/Edward_Snowden) kamu ile paylaştığı bilgiler ışığında ABD'nin **tüm dünyanın** e-posta iletişimini takip edip analiz ettiği ortaya çıkmıştır.

TLS ile genel olarak e-posta sunucunuz ile aranızdaki iletişim şifreli olsa da posta kutunuzda duran e-postalar hala okunabilir durumdadır. Gözetim kapitalizmi bu e-postalarınızı okuyarak size bir şeyler satmaya çalışabilir veya kanuni olsun olmasın devletler e-postalarınıza sunucuları ele geçirerek erişebilir. Bu durumu engellemenin gerçekten tek yolu e-postalarınızı şifrelemektir!


## E-posta nasıl şifrelenir?

GnuPG e-posta şifrelemenin en yaygın ve güvenilir aracıdır. GNU Privacy Guard veya kısaca GPG olarak bilinen yazılım bugün sadece e-postalarınızı şifrelemenin dışında pek çok kriptografik işlem için kullanılabilecek çok amaçlı bir yazılımdır.

"Pretty Good Privacy" ismi ile Phil Zimmerman tarafından 80'lerde ABD'de yazılan PGP, ülkedeki gelmesi beklenen şifreleme yasaklarına karşı geliştirilip dünya ile paylaşılmıştır. ABD ve RSA şirketinin açtığı dava üzerine yazılımın kaynak kodu, anayasal korumadan faydalanmak adına kitap olarak basılıp yayınlanmıştır. Zimmerman'ın PGP'yi satması ile bugün özgür bir yazılım olarak GnuPG ismi ile hayatına devam etmektedir.

GnuPG ile e-postalarınızı ve eklerini şifreleyebilir, size ulaşan e-postanın değiştirilmediğini bilebilir veya gönderen kişinin kimliğini doğrulayabilirsiniz. GnuPG, merkezi bir otoriteye dayanmadan insanların arasında bir güven ilişkisi kurulmasına imkan verir. Bu bakımdan GPG günümüzdeki [en özgürleştirici](https://oyd.org.tr/en/articles/defense-of-gpg/) şifreleme yazılımıdır.

GnuPG anahtar üretimi için [rehberimize danışabilirsiniz](gpg/gpg-anahtar-uretimi.md).


## Webmail kullanarak e-posta şifrelenebilir mi?

Açıkçası, şifreli e-posta göndermenin en iyi yolu [Thunderbird](https://www.thunderbird.net/en-US/) gibi bir istemci ile [Enigmail](https://www.enigmail.net) benzeri bir eklenti kullanmaktır. Böylece şifreleme işlemi tamamen bilgisayarınızda güvenli şekilde gerçekleşir. Bu yöntemin kurulumu için [GnuPG ile e-posta şifreleme](/gpg/eposta-sifreleme.md) rehberimize bakabilirsiniz.

Şayet kullandığınız e-posta hizmeti istemci üzerinden bağlanmanıza imkan vermiyor veya başka bir sebepten istemci kullanmak istemiyorsanız bir tarayıcı eklentisi ile e-postalarınız şifrelemeniz mümkün. [Mailvelope](https://www.mailvelope.com/en/) veya [FireGnuPG](http://tr.getfiregpg.org/s/home) gibi eklentiler tarayıcınızda şifreleme işlemini gerçekleştirebilir.

Şifreli e-posta imkanını webmail olarak sunan hizmet sağlayıcılar da bulunmaktadır. Söz konusu şirketlerin sayısı günümüzde giderek artmakta olsa da farklı teknolojilerle farklı çözümler sunan bir tanesini seçmek için [şifreli e-posta hizmetleri](sifreli-eposta-hizmetleri.md) rehberimize başvurabilirsiniz.


## Şifrelenmiş e-posta neyi korumaz?

E-posta gibi asimetrik bir iletişim yöntemini şifrelemeye çalışmanın bazı eksiklikleri ve dikkat edilmesi gereken noktaları vardır.

* GnuPG, kullandığınız yönteme göre e-postalarınızın başlığını **şifrelemeyebilir**. Çoğunlukla e-postanın başlığı e-postanızın içeriği hakkında çok şey söyleyebileceği için bu hususa dikkat edilmelidir. Başlıkları şifrelemek de posta kutusunda e-posta aramayı çok zor kılmaktadır. Bu bakımdan tercihin bilinçli yapılması önemlidir.

* GnuPG ile şifrelemiş olsanız dahi e-postalarınızın iletilebilmesi için bir takım bilgilerin açık olarak aktarılması gereklidir. Bunu üzerine adres ve isim yazmadığınız bir postanın iletilememesi ile kıyaslayabilirsiniz. Bu durumdan dolayı kullandığınız sunucuyu veya ağ iletişiminizi gözleyebilen biri kimlerle ilişki içinde olduğunuzu [üstveri](https://en.wikipedia.org/wiki/Metadata) (metadata) aracılığıyla öğrenebilir.

* GnuPG anahtarları uzun vadeli ve sizinle ilişkilendirilmiş anahtarlar kullanır. Bu bakımdan imzalanmış bir e-postanın kimden geldiğini inkar etmek mümkün olmadığı gibi kullanılan anahtarların bir şekilde ortaya çıkması durumunda, eski iletişimler de okunabilir hale gelecektir. Şifreli e-postaları ileride bir zaman açabilme ümidi ile saklayan bir kurum (bkz. NSA) bir gün anahtarınızın ifşa olması durumunda e-postalarınızı geriye dönük olarak okuyabilir. Bu elbette e-postaları şifrelememek için bir bahane değildir ama bazı durumlarda dikkate alınması gereken bir risktir.


## Peki anahtarların aitliğini kim doğrular?

Bu sorunun cevabı basittir; herkes ve hiç kimse!

Bir GnuPG anahtarına olan güven tamamen o anahtarı kullanan kişinin o kişi olduğunu bilmenize dayanır. Bu o kişiyi gerçekten tanımanız, güvenli bir kanal veya yüz yüze anahtarın parmak izini doğrulamanızı gerektirebileceği gibi kriptografik olarak kullanılan anahtarı imzalayan kişilerden birini ve anahtarını tanımanız da olabilir.

Güven ağı (web of trust) GnuPG'nin güven ilişkisinin temelidir. GnuPG kullanıcıları tanıdıkları ve güvendikleri kişilerin anahtarlarını imzalarlar. Bu imzalar bir süre sonra tanıdıkların tanıdıkları şekilde bir ağa dönüşür ve iki kişi birbirini tanımasa dahi bir seviyeye kadar birbirlerinin anahtarına güven duyabilirler.

Bu sistem elbette mükemmel değildir. Bugün anahtar sunucuları, özellikle tanınan kişilerin, sahte anahtarları ile doludur. Bu sahte anahtarlarda pek çok sahte imza bulmak da mümkündür. Bu sebeple [WKS](https://www.gnupg.org/documentation/manuals/gnupg/gpg_002dwks_002dserver.html) gibi sistemler görece güvenli ve kolay anahtar dağıtımı yöntemleri geliştirilmektedir. Lakin hiç bir sistem sorunsuz değildir ve anahtar güvenliğine sağduyu ile yaklaşılmalıdır.


## Şifreli e-posta hakkında tavsiyeler nelerdir?

* Gizli anahtarlarınızı şifreli bir ortamda çevrimdışı olarak saklayın. Bu anahtarınızın, cihazınız çalınır, kaybolur veya el koyulursa ele geçmesini engeller. Bunun için [kağıt bir yedek](gpg/paperbackup.md) almayı düşünebilirsiniz.
* **ASLA** ama asla gizli anahtarınızı kimse ile paylaşmayın, umumi bir cihaza kaydetmeyin ve uzak sunucuya yüklemeyin.
* **[ZAROLA KULLANIN!](https://zarola.oyd.org.tr)**. Çünkü anahtarınızın güvenliği anahtar parolanızın güvenliğine bağlıdır.
* Çevrenizde bir CryptoParty yapın ve bu sayede arkadaşlarınıza da GnuPG kullanmayı öğretip anahtarlarınızı imzalayarak kendi güven ağınızı oluşturun. [Özgür Yazılım Derneği](https://oyd.org.tr) ve [Hackerspace Istanbul](https://hackerspace.ist) düzenli aralıklarla [CryptoParty](https://cryptoparty.online)'ler düzenlemektedir.
* İçeriğinin gizliliğinden bağımsız olarak şifreli e-postalar gönderin. Bu gerçekten hem sizin hem tüm toplum için önemlidir. Şayet sadece gerektiğinde şifreleme yaparsanız analiz edilmesi gereken iletişim miktarı hatrı sayılır miktarda azalacaktır ve bir örüntü ortaya çıkacaktır. Havadan sudan bile şifreli yazışın!
