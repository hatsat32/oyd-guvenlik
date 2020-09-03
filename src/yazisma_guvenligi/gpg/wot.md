# GPG Anahtarları ile Güven Ağı Oluşturmak

Güven ağı en basit anlamı ile bir kimlik yönetimi şeklidir. Günlük hayatımızda kimin kim olduğunu söyleyenin bir çeşit otorite olması durumunun aksine güven ağında her kişi kimliğinin ve topluluğun güveninin kaynağıdır.

Basitçe güven ağı, tanıdıklarınızın tanıdıklarına güvenmenizdir. Aynı şekilde sizi tanıyan insanlara güvenenler de sizin söylediğiniz kişi olduğunuza güvenir.

## GPG neden güven ağına ihtiyaç duyar

GnuPG sadece bir şifreleme aracı değil aynı zamanda bir kimlik aracıdır. Bu kriptografik imza yöntemi ile anahtarın sahibinin bir bilginin kendisine ait olduğunu kanıtlaması gibi kendisinin söylediği kişi olduğunu da kanıtlamasını sağlar. Bu neden ile GPG inkar edilebilir şifreleme sunmaz ve bu neden ile çoğu GPG kullanıcı anahtarlarında gerçek adlarını ve e-posta adreslerini bulundurur. Çünkü amaç kişinin kendini kanıtlamasıdır.

Pek çok devlet ve şirket kaynaklı kimlik yönetim sisteminin aksine GPG merkezi bir otoriteye dayanmaz. Bu neden ile herhangi bir kişi istediği isimle veya bilgiyle [bir anahtar oluşturabilir](gpg-anahtar-uretimi.md) ve bunu hiç bir sorunun sorulmadığı anahtar sunucularına yükleyebilir. Bu sebepten [tanınmış kişilerin ismine pek çok sahte anahtar bulunmakta](https://keyserver.ubuntu.com/pks/lookup?search=richard+stallman&fingerprint=on&op=index), [gerçek insanların anahtarlarında da belki binlerce sahte imza](https://keyserver.ubuntu.com/pks/lookup?search=0xF2AD85AC1E42B367&fingerprint=on&op=index) bulunmakta. Bu vahşi batı düzenine çözüm olarak kısmen daha [merkezi sistemler](keys.openpgp.org) ve [başkaca güven kaynakları ile desteklenmiş çözümler](wkd.md) önerilmekte ise de güven ağı hala bireyin en güçlü olduğu, en özgürlükçü sistemdir.

## Güven ağı nasıl kurulur

Bir GPG anaharı sahibi iseniz çevrenizde tanıdığınız GPG kullanıcılarının anahtarlarını imzalayarak kendi güven ağınızı oluşturabilirsiniz. Bunun için [Kleopatranın grafik arayüzünden](gui_gpg.md) veya doğrudan [uçbirim aracılığı ile](ucbirim_gpg.md) imzalama işlemlerini yapabilirsiniz.

Bir anaharı imzalamak için sırası ile aşağıdaki işlemleri yapmanız gereklidir.

1. İmzalanacak umumi anahtarı bulup indirmek
2. Anahtarı imzalamak
3. Anahtarın sahibine imzalı anahtarı dışa akarıp göndermek veya bir anahtar sunucusuna yüklemek.

İmzalama işlemini yaptıktan sonra şayet imzaladığınız anahtarın güven değerine bakarsanız en yüksek değerde olduğunu göreceksiniz.

`gpg --gpg --list-keys [anahtar ID veya e-posta]`


```
pub   rsa4096 2013-07-20 [SC]
      67819B343B2AB70DED9320872C6464AF2A8E4C02
uid           [  full  ] Richard Stallman <rms@gnu.org>
sig!3        2C6464AF2A8E4C02 2013-07-20  Richard Stallman <rms@gnu.org>
sig!3        170AF0E2954295DF 2017-06-21  Ian Andrew Kelling <ian@iankelling.org>
sig!         42272957268B3FCA 2020-03-18  Alper Atmaca <alper@oyd.org.tr>
sub   rsa4096 2013-07-20 [E]
sig!         2C6464AF2A8E4C02 2013-07-20  Richard Stallman <rms@gnu.org>

gpg: 4 good signatures
gpg: 202 signatures not checked due to missing keys
```
Bu noktadan sonra sizi tanıyan ve anahtarınıza güvenen kişiler imzaladığınız anahtarın da belirtilen kişiye ait olduğuna güvenecekler. Elbette tek imza tam anlamı ile yeterli olmamakta ve GPG belirli bir güvenilir imza isteyecektir. Bu bakımdan bir güven ağı ne kadar sık dokunduysa o derecede güvenilir olacaktır.

Kendi güven ağınızı oluşturduktan sonra yapmanız gereken tek şey bu ağı tüm dünyadaki güven ağına bağlamaktır. Bunun için grubunuzdan bir kişinin güvenilen, anahtarında çokça geçerli tanınmış insanların imzası olan bir kişiye ulaşması ve anahtarını imzalatması gereklidir. Bu olduğunda sizin küçük güven ağınız tüm **dünyadaki GPG güven ağının** bir parçası olur.

## Güven ağının temelleri

Şayet herkes koşulsuz şartsız herkesin anahtarını imzalıyor olsaydı bir "güven" ilişkisinden söz etmemiz mümkün olmazdı. Bu bakımdan bir kişinin anahtarını imzalamak size güvenen herkesin güvenine karşı bir **sorumluluk** taşıdığından bu eylemi dikkatli bir şekilde gerçekleştirmeniz gerekmektedir.

Neredeyse 30 yıldır hayatta olan güven ağı dünyada kabul edilmiş kimi kurallara göre işler. Bu kurallara bağlı olarak güven ağınızı oluşturmak hem sizin hem de **tüm GPG kullanıcıları için çok ama çok önemlidir.**

1. Yüzyüze tanışmadığınız kimsenin anahtarını imzalamayın
2. Tanıştığınız kişilerin söyledikleri kişiler olduğunu mümkün ise birden fazla fotoğraflı resmi kimlik ile doğrulayın
3. Anahtar parmakizlerinin tamamını kontrol edin ve anahtardaki bilgilerin kimliklerindeki bilgiler ile eşleştiğinden emin olun.

Yukarıdaki kurallar **olmazsa olmaz** detaylar olmakla birlikte hem kendi anahtarınızdaki gereksiz imzaları azaltmak hem de boş yere imza atmamak için aşağıdaki kuralları da kendi rızanıza göre getirebilirsiniz. Bu özellikle anahtarınıza olan güven büyük ise daha da önem kazanır.

* İmzalayacağınız anahtarda bulunan e-postaların gerçekten o kişi tarafından kullanıldığını doğrulamak yerinde olabilir. Her ne kadar o kişi dediği kişi olsa da e-postaların gerçek sahibi olmayabilir. Bunu gerçekleştirmenin en kolay yolu kişiden o anahtar ile imzalı bir e-posta talep etmektir.

* Kişi GPG anahtarına hala sahip mi? Pek çok insan bir GPG anahtarı oluşturup ya anahtar dosyasını ya da parolasını kaybederek erişimlerini yitiriyorlar. Bu hayalet anahtarlar sonsuza kadar anahtar sunucularında kaldığından siz de boş yere imza atmış ve ihtimalen güvensiz bir anahtara güven oluşturmuş oluyorsunuz Bu bakımdan yine imzalı bir e-posta bu durumun da kanıtı olabilir.

* Kişi söz konusu anahtara ne kadar süredir sahip olduğu bilgisi kişinin ciddi bir GPG kullanıcısı olup olmadığının da belirtisi olabilir. Şayet anahtarını yeni oluşturmuş ve bir deney olarak bulunduran bir kişiye güven teslim etmek anahtarı kaybetmesi durumunda yukarıdaki durumu yaratabileceğinden belki bir süre anahtara sahip olması üzerine anahtarını imzalamanız yerinde olabilir.

* Kişinin anahtarını ait olduğu alanlarda ilan etmesi anahtarına olan hakimiyetinin de göstergesi olabilir. Pek çok kişi anahtarının parmak izini ait oldukları sosyal medya kanallarında görünür kılmaktadır. Bu durumun imzalama yapılmadan incelenmesi güven ilişkisini pekiştirebilir.

* Kişi anahtar imzalamanın ve güven ağına dahil olmanın sorumluluklarının farkında olmalıdır. Bu bakımdan imzalanacak anahtarın sahibi ile kısa bir GPG muhabbeti kişinin sizin ona vereceğiniz güveni koruyup koruyamayacağına dair çok şey söyleyebilir.

* Anahtarın genişliği 2048 bit'ten fazla değil ise çok geçmeden eskiyecek ve güvenli kabul edilmeyecek bir anahtar söz konusudur. Şayet bu anahtarı kullanan kişinin özellikle daha düşük boyutta bir anahtar kullanmak için özel bir gerekçesi yok ise anahtarı imzalamayı bir kere daha düşünebilirsiniz.

## Yalnız mısınız

Pek çok yeni GPG kullanıcısı için bu bir gerçeklik olabilir. Keza GPG kullanıcısı sayısı fazla olmamakla birlikte bu kişileri tanımak da genellikle bilişim ve özgür yazılım camialarından olmayan insanlar için zor olabilmektedir. Bu durumun sizi yıldırmasına izin vermemelisiniz. Öncelikle bir GPG anahtarı sahibi olmak kendi başına çok kullanışlı ve genel bilişim güvenliğinize çok fazla katkı sunacak bir ayrıcalıktır. İkincisi tüm dünyada sizi sıcak karşılayacak ve güven ağlarına dahil edecek topluluklar bulunmaktadır.

Türkiye'de bu toplulukların başında, bu rehberin de yaratıcısı olan [Özgür Yazılım Derneği](https://oyd.org.tr) ve [Hackerspace İstanbul](https://hackerspace.ist) gelmekte ve Türkiye'deki uluslararası bağlantıya sahip en önemli güven ağının da merkezinde bulunmaktadır. İki topluluk da belirli aralıklarla İstanbul'da ve mümkün olursa başka illerde uluslararası bir etkinlik olan [Cryptoparty](https:www.cryptoparty.in) düzenlemektedir. Cryptoparty'ler katılımcıların birbirlerine yardım ederek güvenli iletişim araçlarını kullanmayı kolaylaştırmak ve GPG anahtarlarını imzalayarak yerel güven ağları oluşturmak üzere gerçekleştirilir. Türkiye'de gerçekleştirilen etkinlikleri [Cryptoparty İstanbul](https://cryptoparty.istanbul) adresinden veya Özgür Yazılım Derneği'nin iletişim kanallarından takip edebilirsiniz.

## Ek okuma listesi

* [GnuPG güven ağı makalesi](https://www.gnupg.org/gph/en/manual/x547.html)
* [GnuPG güven ağı wikisi](https://wiki.gnupg.org/WebOfTrust)
* [Güven ağı wikipedia](https://en.wikipedia.org/wiki/Web_of_trust)
* [Güven ağının algoritmasına ilişkin bir açıklama](https://security.stackexchange.com/questions/73267/gpg-web-of-trust-level)
