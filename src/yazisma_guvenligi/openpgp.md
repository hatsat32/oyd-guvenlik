# Şifreli E-Posta

## E-posta nedir?

Bu soru anlamsız gelse de güvenli kılınmadan önce bir sistemin ne olduğu az da olsa anlaşılmalıdır. E-posta İnternet'in ilk mesajlaşma yöntemidir. Bu bakımdan üzerine onlarca alternatif geliştirilmiş olsa da hala baskın iletişim aracı olarak hayatımızdaki yerini sürdürmektedir.

E-posta aynı zamanda tasarımı gereği bir çok aracıya güvenmenizi gerektiren, güvenli kılması zor bir sistemdir. TLS[^1] kullanımının yaygınlaştığı görece yakın bir zamana kadar gönderilen her e-posta tüm içeriği ile birlikte aktarım sırasında, ulaştığı sunucuda ve iletildiği diğer her kanalda okunabilir durumdaydı. [Edward Snowden](https://en.wikipedia.org/wiki/Edward_Snowden) tarafından ortaya çıkarılan sırların ışığıda Amerika Birleşik Devletlerinin istihbarat örgütlerinin **TÜM DÜNYANIN** e-postalarını kaydettiği ve analiz ettiği ortaya çıkmıştır.

TLS ile genel olarak e-posta sunucunuz ile aranızdaki iletişim ve çoğunlukla da gönderdiğiniz e-postanın alıcısının kullandığı sunucu arasındaki iletişim şifreli olsa da sunucularda duran e-postalar hala okunabilir durumdadır. Gözetim kapitalizminin bir unsuru olarak şayet bir şey yapılabiliyor ise muhtemelen yapılıyordur ve gerçek şu ki e-postalarınız okunuyor, size bunun üzerinden reklam satılıyor!

## E-posta nasıl şifrelenir?

GnuPG'ye hoşgeldiniz. Bugün bildiğimiz ismiyle "GNU Privacy Guard", sadece e-posta şifrelemek için değil neredeyse bilgisayarınızda yapabileceğiniz her kriptografik işlem için kullanılabilecek çok amaçlı bir yazılımdır.

"Pretty Good Privacy" ismi ile Phil Zimmerman tarafından 80'lerde ABD'de yazılan PGP, ülkedeki gelmesi beklenen şifreleme yasaklarına karşı geliştirilip dünya ile paylaşılmıştır. ABD ve RSA şirketinin davası üzerine yazılımın kaynak kodu, anayasal korumadan faydalanmak adına kitap olarak basılıp yayınlanmış ve Zimmerman'ın PGP'yi satması ile bugün özgür bir yazılım olarak GnuPG ismi ile hayatına devam etmektedir.

GnuPG ile e-postalarınızı ve eklerini şifreleyebilir, size ulaşan e-postanın değiştirilmediğini bilebilir veya gönderen kişinin kimliğini doğrulayabilirsiniz. GnuPG, merkezi bir otoriteye dayanmadan insanların arasında bir güven ilişkisi kurulmasına imkan verir.

GnuPG kurulumu için [rehberimize danışabilirsiniz](gpg/gpg-anahtar-uretimi.md).

## Webmail kullanarak e-posta şifrelenebilir mi?

Açıkçası, şifreli e-posta göndermenin en iyi yolu [Thunderbird](https://www.thunderbird.net/en-US/) gibi bir istemci ile [Enigmail](https://www.enigmail.net) benzeri bir eklenti kullanmaktır. Ancak [Mailvelope](https://www.mailvelope.com/en/) veya [FireGnuPG](http://tr.getfiregpg.org/s/home) gibi eklentiler ile bu mümkündür.

## Şifrelenmiş e-posta neyi korumaz?

Her şifreleme yöntemi gibi, e-posta gibi asimetrik bir iletişim yöntemini şifrelemeye çalışmanın da bazı eksiklikleri ve dikkat edilmesi gereken noktaları vardır.

* GnuPG, kullandığınız yönteme göre e-postalarınızın başlığını **şifrelemeyebilir**. Çoğunlukla e-postanın başlığı e-postanızın içeriği hakkında çok şey söyleyebileceği için bu hususa dikkat edilmelidir. Başlıkları şifrelemek daha sonra posta kutusunda e-posta aramayı çok zor kılacağı gibi e-postaları şifrelememek de mesajların içeriğini ifşa etmek anlamına gelebilir. Bu bakımdan tercihin bilinçli yapılması önemlidir.

* GnuPG ile şifrelemiş olsanız dahi e-postalarınızın iletilebilmesi için bir takım bilgilerin açık olarak aktarılması gerekecektir. Bunu üzerine adres ve isim yazmadığınız bir postanın iletilememesi ile kıyaslayabilirsiniz. Bu durumdan dolayı sunucuları veya iletişimi gözleyebilen biri kimlerle ilişki içinde olduğunuzu [üstveri](https://en.wikipedia.org/wiki/Metadata) (metadata) aracılığıyla öğrenebilir.

* GnuPG uzun vadeli, kişilerin kimliği ile sıkı sıkıya bağlı anahtarlar kullanır. Bu bakımdan imzalanmış bir e-postanın kimden geldiğini inkar etmek mümkün olmadığı gibi kullanılan anahtarların bir şekilde ortaya çıkması durumunda, eski iletişimler de okunabilir hale gelecektir. Şifreli e-postaları bir zaman açabilme ümidi ile saklayan bir kurum (bkz. NSA) bir gün e-postalarınızı okuyabilir. Bu elbette e-postaları şifrelememek için bir bahane değildir ama bazı durumlarda dikkate alınması gereken bir risktir.

## Peki anahtarların aitliğini kim doğrular?

Bu sorunun basit cevabı, herkes ve hiç kimsedir.

Bir GnuPG anahtarına olan güven tamamen o anahtarı kullanan kişinin o anahtarı kullandığını bilmenize dayanır. Bu o kişiyi gerçekten tanımanız ve güvenli bir kanal veya yüz yüze anahtarın parmak izini doğrulamanız anlamına gelebileceği gibi, kriptografik olarak kullanılan anahtarı imzalayan kişilerden birini ve anahtarını tanımanız da olabilir.

Güven ağı GnuPG'nin temel güven ilişkisinin temelidir. GnuPG kullanıcıları tanıdıkları ve güvendikleri kişilerin anahtarlarını imzalarlar. Bu imzalar bir süre sonra tanıdıkların tanıdıkları şekilde bir ağa dönüşür ve iki kişi birbirini tanımasa dahi bir seviyeye kadar tanımadığı ama tanıdığının tanıdığı bir kişinin anahtarına güvenebilir.

## Şifreli e-posta hakkında tavsiyeler nelerdir?

* Gizli anahtarlarınızı şifreli bir ortamda çevrimdışı olarak saklayın. Bu anahtarınızın, cihazınız çalınır, kaybolur veya el koyulursa ele geçmesini engeller. Bunun için [kağıt bir yedek](yazisma_guvenligi/gpg/paperbackup/paperbackup.md) almayı düşünebilirsiniz.
* **ASLA** ama asla gizli anahtarınızı kimse ile paylaşmayın, umumi bir cihaza kaydetmeyin ve uzak sunucuya yüklemeyin.
* **[ZAROLA KULLANIN!](https://zarola.oyd.org.tr)**. Çünkü anahtarınızın güvenliği anahtar parolanızın güvenliğine bağlıdır.
* Çevrenizde bir CryptoParty yapın ve bu sayede arkadaşlarınıza da GnuPG kullanmayı öğretip anahtarlarınızı imzalayarak kendi güven ağınızı oluşturun. [Özgür Yazılım Derneği](https://oyd.org.tr) ve [Hackerspace Istanbul](https://hackerspace.ist) düzenli aralıklarla [CryptoParty](https://cryptoparty.online)'ler düzenlemektedir.
* İçeriğinin gizliliğinden bağımsız olarak şifreli e-postalar gönderin. Bu gerçekten hem sizin hem tüm toplum için önemlidir. Şayet sadece gerektiğinde şifreleme yaparsanız analiz edilmesi gereken iletişim miktarı hatrı sayılır miktarda azalacaktır ve bir örüntü ortaya çıkacaktır. Havadan sudan bile şifreli yazışın!
---
[^1]: Transport Layer Security <https://tr.wikipedia.org/wiki/Transport_Layer_Security>
