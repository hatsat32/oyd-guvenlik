# Şifreli E-posta Hizmetleri

[Edward Snowden'in](https://en.wikipedia.org/wiki/Edward_Snowden) kamuya açıkladığı gerçeklerden sonra şifreli e-posta hizmetleri fazlasıyla tartışılmış ve konuşulmuştur. Özellikle [Lavabit'in](https://en.wikipedia.org/wiki/Lavabit) muhtemelen [FBI](https://www.fbi.gov/) baskısı sebebi ile kapatılmasından sonra benzer şifreli e-posta hizmetlerine ilişkin merak ve tartışma daha da arttı. Şifreli e-posta hizmetlerini bir ihtiyaç olarak görüldüğünden günümüzde giderek daha fazla şifreli e-posta'yı bir web arayüzü üzerinden hizmet olarak sunan şirketlerin sayısı artmaktadır. Her güvenlik aracı gibi bu hizmetlerin de bir kullanım alanı ve sınırları bulunmaktadır.

## Şifreli e-posta hizmeti nedir?

Öncelikle "şifreli" veya "güvenli" e-postanın ne olmadığından söz etmek gerekir. Herhangi bir yazışmanın "mahrem" veya "güvenli" sayılabilmesi için şifrelemenin [uçtan uca(end-to-end)](https://en.wikipedia.org/wiki/End-to-end_encryption) olması gereklidir. Bu koşulun gerçekten oluşmasının tek imkanı tarafların şifreleme anahtarlarını kendi cihazlarında üretmeleri ve sadece kendi ellerinde bulundurmalarıdır. Aracı olarak hizmet sunan şifreli e-posta hizmet sağlayıcısının şifreleme işlemine müdahil olduğu her durumda **güvenin** bir kısmı hizmet sağlayıcıya aktarılmış olur.

Kabaca şifreli e-posta hizmetleri uygulama bakımından ikiye ayrılabilir; taraflar arasındaki iletişimin uçtan uca şifrelenebildiği cins ile sadece gelen e-postaların gelen kutusunda kullanıcıya ait bir anahtar ile şifreli saklandığı cins olarak.

## Şifreli Gelen Kutusu

Pek çok mahremiyet yanlısı e-posta sağlayıcısı, arayüzleri aracılığı ile gelen e-postaların şifrelenerek gelen kutusuna kaydedilmesine imkan vermektedir. Söz konusu şifreleme genellikle kendi sunucularında kullanıcı adına üretilen bir GPG anahtarı ile yapmaktadırlar. Bu yöntemin iki adet faydası bulunmaktadır;

* Bir sebepten e-postalar veya e-posta hesabı kaybedilirse, e-postaların şifreli oluşlarından dolayı içeriklreinin ifşa olmaları mümkün olmayacaktır.

* E-posta hizmet sağlayıcısı bir devlet tarafından kullanıcıları hakkında bilgi vermeye zorlanırsa şirket şifrelenmiş veriden ve tutuyor ise üstveriden başka teslim edebileceği bir şey olmayacaktır.

Üç de iyi değerlendirilmesi gereken zararı bulunmaktadır;

* Doğal olarak gelen e-postalar vardıklarında sunucu tarafından okunabildiklerinden ne hizmet sağlayıcısının ne de kendisinden bilgi talep eden devletlerin söz konusu e-postaların kaydedilip şifrelenmeden önce okumasına engel olan bir durum yoktur.

* E-postalarınız şifreli saklanacağından, cihazlarınızda yerel olarak GPG kurulu ve hizmet sağlayıcınızın ürettiği gizli anahtar elinizde değil ise postalarınızı okumak için size sunulan webmail arayüzüne mahkum kalırsınız.

* Kullanılan anahtarı kendiniz sağlamıyor ve hizmet sağlayıcınızın ürettiği anahtarı kullanıyorsanız bu anahtarın güvenliği konusunda da güveni hizmet sağlayıcınıza vermiş olursunuz.

Tüm anlatılanlar bir yana bu şekilde yapılan şifrelemeden __belirtilen kapsam dışında__ **güvenlik** veya **mahremiyet** beklememek yerinde olacaktır.

Söz konusu imkanı sağlayan pek çok e-posta sağlayıcısı olmakla birlikte aşağıda sayılanlar günümüzde en çok tanınanları sayılabilir:

[Mailbox](https://mailbox.org)
[Posteo](htpps://posteo.de)
[Fastmail](htpps://fastmail.com)


## Uçtan Uca Şifreli E-posta

Uçtan uca şifreli e-posta hizmeti veren şirketler her kullanıcısı için üyelik sırasında bir anahtar oluşturmakta ve bu anahtar aracılığı ile çoğunlukla sadece kendi üyeleri arasındaki yazışmaları şifreleyebilmektedir. Hizmet sağlayıcının dışındaki e-posta kullanıcılarına bir parola ile şifrelenmiş e-posta atabilmek mümkün olsa da bu standart olarak sağlanmamakta ve olağan kullanım için kimi zaman zahmetli olmaktadır. Bu hizmetler ile;

* Aynı hizmet sağlayıcıyı kullanan yazışmalar veya parola ile şifrelenerek diğer e-posta kullanıcılarına yapılan yazışmalar hizmet sağlayıcı tarafından da okunamadığı iddia edilmektedir.

* Devletlerden gelen taleplere şirketlerin sağlayabileceği sadece üstveri, anahtarın şifreli hali ve şifreli yazışmalar olmaktadır.

Her ne kadar anahtarın üretimi ve hizmetin kullanımı için gereken yazılımlar "özgür" ve tarayıcıda yerel olarak çalışsa da her giriş yaptığınızda tarayıcınıza yüklenen javascript kodunun doğruluğunu denetleme imkanının olmayışı ve her halukarda şifreli de olsa gizli anahtarınızın şirketin sunucusuna yüklenmesi ile [bruteforce](https://en.wikipedia.org/wiki/Brute-force_attack) saldırılara imkan vermesi tatsız sonuçlardır. Sayılan sebepler ile belirli bir güvenin hizmet sağlayana aktarıldığı ve bu **güvenin haksız çıkması** ihtimalinin değerlendirilmesi önemlidir.

Uçtan uca şifreli e-posta hizmeti veren en tanınmış iki isim [Tutanota](https://tutanota.com) ve [Protonmail](https://protonmail.com) idir. Benzer hizmetler vermelerine rağmen bu amaçla kullandıkları teknolojiler ve yaklaşımlar bir hayli farklıdır.

### Tutanota vs Protonmail


#### Ücretsiz Üyelik

Protonmail de Tutanota da giriş seviyesi temel güvenlik özelliklerinin sunulduğu bedava hesaplar vermekte. Bu bakımdan şayet ihtiyaçlarınız sınırlı ve bütçeniz dar ise iki hizmet sağlayıcıdan da bedava hizmet almanız mümkün.


#### Anonim Üyelik ve Ödeme

Teoride her iki şirket de anonim üyelik veriyor ve cryptoparalar ile ödeme kabul ediyor fakat Protonmail pratik olarak anonim üyeliği daha zor kılıyor. Muhtemelen boşuna açılan bedava hesapları azaltmak adına bir çaba olsa da güvenlik ihtiyacının bir parçası olabilecek anonimliği bozan bu çabanın iyi olmadığı kesin.


#### Fiyat

Protonmail'in gün itibari ile en ucuz ücretli üyeliği 4 Avro/aylık olmakla ayda 1 Avro'ya hizmet veren Tutanotaya göre 4 kat daha pahalı durumda. Protonmail bunu nükleer sığınaklarının maliyetine ve İsviçre'de bulunmalarına bağlamakta. Tutanota ise Almanya'da çeşitli veri merkezlerinde sunuuclarını çalıştırmakta. Fiyatlandırma konusundaki inandırıcılık kullanıcıya kalmış durumda.


#### Platform Yaygınlığı

Her iki hizmet de GNU/Linux dahil olmak üzere tüm platformlarda istemci bulunduruyor. Lakin Protonmail SMTP protokolü ile yerel e-posta istemcilerinin kullanılabilmesi için bir köprü yazılımı da geliştirmiş ve bunu ücret ödeyen kullanıcılarına sunuyor durumda. Böylece isteyenler Thunderbird gibi kendi e-posta istemcileri ile Protonmail'i kullanabilmekte. Tutanota ise sadece webmail ve kendi istemcileri ile kullanıma imkan veriyor.


#### Yazılım Özgürlüğü

Protonmail ile Tutanota'nın en büyük ayrılıklarından biri burada ortaya çıkıyor. Protonmail yazılım özgürlüğü konusunda verdiği sözleri zamanında tutamamakta. Şu anda sadece webmail ve köprü yazılımı özgür olmakla, diğer tüm platformlar için olan yazılımları mülk konumunda bulunuyor. Tutanota ise tam tersine tüm yazılımlarını özgür geliştirmekte ve Android istemcisi [F-droid'den](https://f-droid.org) bile indirilebiliyor. [Hatta Tutanota özgür yazılıma özgür yazılım diyen nadir şirketlerden biri](https://tutanota.com/blog/posts/desktop-clients/)


#### Şifreleme Teknolojileri

Protonmail ile Tutanota arasındaki en önemli farklardan bir tanesi kullandıkları şifreleme teknolojilerinden gelmekte. Protonmail uzun zamandır e-posta şifreleme için kullanılan GnuPG yazılımı üzerine kurulu bir sistem. Tutanota ise simetrik şifreleme algoritması olan AES128 ile asimetrik RSA2048 algoritmasının bir birleşimini kullanmakta. Algoritmaların geçmişi ve güvenliği bakımından gözle görülecek bir fark bulunmamakla birlikte, bu durum hizmetin özgürlüğü açısından çok önemli pratik bir fark ortaya koymakta. Keza Protonmail diğer GPG istemcileri ile şifreli iletişim kurabilirken Tutanota bu imkandan yararlanamamakta.


#### Hizmet Özgürlüğü

Muhtemelen Tutanota ve Protonmail arasındaki en önemli fark hizmetlerinin özgürlüğü. Tutanota şifreleme imkanını doğal olarak sadece kendi kullanıcıları arasında sağlayabilmekte ve federatif e-posta sisteminde ayrı bir [walled garden](https://www.fsf.org/blogs/community/iphone) olarak bulunmakta. Dışarıdan bir kullanıcının şifreli olarak Tutanota kullanıcısına e-posta atması şu an itibari ile mümkün değil fakat [GPG uyumluluğu üzerine çalışacaklarına dair bir açıklamaları bulunmakta.](https://www.reddit.com/r/tutanota/comments/9blzp4/support_for_pgpgpg/)

Protonmail ise GPG ile çalışmakta ve yakın zamanda kendi kullanıcılarının GPG anahtarlarının indirilebileceği [anahtar sunucularını](hkps://api.protonmail.ch) devreye almış durumdalar. Hala Android ve IOS istemcilerinden hizmet sağlayıcılar arası şifreleme konusunda sorun çekilse de webmail üzerinden yapılan yazışmalarda gelen e-posta GPG ile şifreli veya imzalı ise Protonmail doğrudan anahtarı indirip cevapları şifreli olarak gönderebiliyor. Bu bakımdan Protonmail dışı kişilerle şifreli yazışmak gün itibari ile mümkün ve görece kolay.

Aynı zamanda SMTP ve POP3 gibi federatif e-posta protokolleri iki hizmet tarafından da doğrudan desteklenmemekte. Sadece Protonmail [kendi köprü yazılımları](https://protonmail.com/bridge/) ile buna imkan vermekte.

# Sonuç

Şifreli e-postayı bir hizmet olarak almak tercih sayılabilir. Kendi e-posta sunucunuzu işletmek ve GPG kullanmak hiç bugün olduğu kadar kolay olmamıştı. Hali ile şifreli yazışmak, bunu güvenli şekilde yapmak ve anahtarınızı kendi elinizde tutmanın güvenini hissetmek için hala en iyi seçenek GPG'yi kendi yerel cihazınızda tercih ettiğiniz güvenilir bir e-posta hizmet sağlayıcı ile kullanmaktır.

[GPG anahtarı oluşturmak ve kullanmak için rehberimizden yararlanabilirsiniz.](../yazisma_guvenligi/openpgp.md)
