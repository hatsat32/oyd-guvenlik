# Şifreli E-Posta

## E-posta nedir?

Bu soru anlamsız gelse de güvenli kılınmadan önce bir sistemin ne olduğu az da olsa anlaşılmalıdır. E-posta İnternet'in ilk mesajlaşma yöntemidir. Bu bakımdan üzerine onlarca alternatif geliştirilmiş olsa da hala baskın iletişim aracı olarak hayatımızdaki yerini sürdürmektedir.

E-posta aynı zamanda tasarımı gereği bir çok aracıya güvenmenizi gerektiren, güvenli kılması zor bir sistemdir. TLS kullanımın yaygınlaştığı görece yakın bir zamana kadar gönderilen her e-posta tüm içeriği ile birlikte aktarım sırasında, ulaştığı sunucuda ve iletildiği diğer her kanalda okunabilir durumdaydı. [Edward Snowden](https://en.wikipedia.org/wiki/Edward_Snowden) tarafından ortaya çıkarılan sırların ışığıda Amerika Birleşik Devletlerinin istihbarat örgütlerinin **TÜM DÜNYANIN** e-postalarını kaydettiği ve analiz ettiği ortaya çıkmıştır.

TLS ile genel olarak e-posta sunucunuz ile aranızdaki iletişim ve çoğunlukla da gönderdiğiniz e-postanın alıcısının kullandığı sunucu arasındaki iletişim şifreli olsa da sunucularda duran e-postalar hala okunabilir durumdadır. Gözetim kapitalizminin bir unsuru olarak şayet bir şey yapılabiliyor ise muhtemelen yapılıyordur ve gerçek şu ki e-postalarınız okunuyor, size bunun üzerinden reklam satılıyor!

## E-posta Nasıl Şifrelenir

GnuPG'ye hoşgeldiniz. Bugün bildiğimiz ismiyle GNU Privacy Guard sadece e-posta şifrelemek için değil neredeyse bilgisayarınızda yapabileceğiniz her kriptografik işlem için kullanılabilecek çok amaçlı bir yazılımdır.

Pretty Good Privacy ismi ile Philiph Zimmerman tarafından 80'lerde ABD'de yazılan PGP ülkedeki gelmesi beklenen şifreleme yasaklarına karşı geliştirilip dünya ile paylaşılmıştır. ABD ve RSA şirketinin davası üzerine yazılımın kaynak kodu anayasal korumadan faydalanmak adına kitap olarak basılıp yayınlanmış ve Zimmarman'ın PGP'yi satması ile bugün özgür bir yazılım olarak GnuPG ismi ile hayatına devam etmektedir.

GPG ile e-postalarınızı ve eklerini şifreleyebilir, size ulaşan e-postanın değiştirilmediğini bilebilir veya gönderen kişinin kimliğini doğrulayabilirsiniz. GPG merkezi bir otoriteye dayanmadan insanların arasında bir güven ilişkisi kurulmasına imkan verir.

<<<<<<< HEAD
<!-- gpg bağlantısı verilecek -->
=======
[GPG kurulumu için rehberimize danışabilirsiniz](gpg/gpg-anahtar-uretimi.md)
>>>>>>> 070ae67b96cbd01b5ce2afb1706c6cd9924119fd

## Webmail Kullanarak e-posta şifrelenebilir mi?

Açıkçası, şifreli e-posta göndermenin en iyi yolu [Thunderbird](https://www.thunderbird.net/en-US/) gibi bir istemci ile [Enigmail](https://www.enigmail.net) benzeri bir eklenti kullanmaktır.

<<<<<<< HEAD
## Şifrelenmiş e-posta neyi korumaz?
=======
[Mailvelope](https://www.mailvelope.com/en/) eklentisi tarayıcınıza kurabileceğiniz ve girdiğiniz webmail üzerinden GPG şifreli yazışma yapmanıza imkan sağlayan bir tarayıcı eklentisi. Kurulumu biraz daha karmaşık olacak olsa da web üzerinden e-postalarınızı yönetme ihtiyacınız varsa değerlendirilebilir bir seçenek.

Kimi e-posta sağlayıcılar kendi yazılımları aracılığı ile GPG destekli şifreli e-posta hizmeti sunmakta. Bunun için [şifreli e-posta hizmetleri](sifreli-eposta-hizmetleri.md) rehberimize danışabilirsiniz.

## Şifrelenmiş E-posta Neyi Korumaz
>>>>>>> 070ae67b96cbd01b5ce2afb1706c6cd9924119fd

Her şifreleme yöntemi gibi e-posta gibi asimetrik bir iletişim yöntemini şifrelemenin de bazı eksiklikleri ve dikkat edilmesi gereken noktaları vardır.

	Kullandığınız yönteme göre GPG e-postalarınızın başlığını şifrelemeyebilir. Çoğunlukla e-postanın başlığı e-postanızın içeriği hakkında çokça şey söyleyebileceği için bu hususa dikkat edilmelidir. Başlıkları şifrelemek daha sonra posta kutusunda e-posta aramayı çok zor kılacağı gibi e-posta şifrelememek de mesajların içeriğini ifşa etmek anlamına gelebilir. Bu bakımdan tercihin bilinçli yapılması önemlidir.

	GPG ile şifrelemiş olsanız dahi e-postalarınızın iletilebilmesi için bir takım bilgilerin açık olarak aktarılması gerekecektir. Bunu üzerine adres ve isim yazmadığınız bir postanın iletilemeyeceği ile kıyaslayabilirsiniz. Bu durumdan dolayı sunucuları veya iletişimi gözleyebilen biri kimlerle ilişki içinde olduğunuzu [üstveri](üstveri bağlantısı ver) aracılığı öğrenebilir.

	GPG uzun vadeli, kişilerin kimliği ile sıkı sıkıya bağlı anahtarlar kullanır. Bu bakımdan imzalanmış bir e-postanın kimden geldiğini inkar etmek mümkün olmadığı gibi kullanılan anahtarların bir şekilde ortaya çıkması durumunda, eski iletişimler de okunabilir hale gelecektir. Şifreli e-postaları bir zaman açabilme ümidi ile saklayan bir kurum (bkz. NSA) bir gün e-postalarınızı okuyabilir. Bu elbette e-postaları şifrelememek için bir bahane değil ama bazı durumlarda dikkate alınması gereken bir risktir.

## Peki anahtarların aitliğini kim doğrular?

Bu sorunun basit cevabı; herkes ve kimsedir.

Bir GnuPG anahtarına olan güven tamamen o anahtarı kullanan kişinin o anahtarı kullandığını bilmenize dayanır. Bu o kişiyi gerçekten tanımanız ve güvenli bir kanal veya yüz yüze anahtarın parmak izini doğrulamanız anlamına gelebileceği gibi, kriptografik olarak kullanılan anahtarı imzalayan kişilerden birini ve anahtarını tanımanız da olabilir. 

Güven ağı GPG'nin temel güven ilişkisinin temelidir. GPG kullanıcıları tanıdıkları ve güvendikleri kişilerin anahtarlarını imzalarlar. Bu imzalar bir süre sonra tanıdıkların tanıdıkları şekilde bir ağa dönüşür ve iki kişi birbirini tanımasa dahi bir seviyeye kadar tanımadığı ama tanıdığının tanıdığı bir kişinin anahtarına güvenebilir.

## Şifreli e-posta hakkında tavsiyeler nelerdir?

* Gizli anahtlarınızı şifreli bir ortamda çevrimdışı olarak saklayın. Bu anahtarınızın, cihazınız çalınır, kaybolur veya el koyulursa ele geçmesini engeller.
* **ASLA** ama asla gizli anahtarınızı kimse ile paylaşmayın, umumi bir cihaza kaydetmeyin ve uzak sunucuya yüklemeyin.
* *[ZAROLA KULLANIN!](zarola.oyd.org.tr)* çünkü anahtarınızın güvenliği bu parolanızın güvenliğine bağlıdır.
* Çevrenizde bir CryptoParty yapın ki arkadaşlarınıza da GnuPG kullanmayı öğretip anahtarlarınızı imzalayarak kendi güven ağınızı oluşturun.
* İçeriğinden bağımsız olarak şifreli e-postalar gönderin. Bu gerçekten hem sizin hem tüm toplum için önemlidir. Şayet sadece gerektiğinde şifreleme yaparsanız analiz edilmesi gereken iletişim miktarı hatrısayılır miktarda azılacaktır ve bir örüntü ortaya çıkacaktır. Havadan sudan bile şifreli yazışın!
