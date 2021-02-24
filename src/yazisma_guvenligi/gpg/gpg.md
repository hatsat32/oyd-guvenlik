# GnuPG veya GPG Nedir?

GPG özgür bir kriptografik araçtır. GPG ile [asimetrik](https://en.wikipedia.org/wiki/Public-key_cryptography) ve [simetrik](https://en.wikipedia.org/wiki/Symmetric-key_algorithm) araçları kullanarak şifreleme, imzalama, kimlik doğrulama ve güven ağı oluşturmak gibi işlemlerin yapılması mümkündür.

Günümüzde GPG GNU/Linux işletim sistemlerinin paket dağıtımlarının güvenliğini sağlamaktan, e-posta şifrelemeye ve [yakın zamanın en önemli bilgilerinin](https://en.wikipedia.org/wiki/Edward_Snowden) ortaya çıkmasında kullanılmaktadır.

## PGP'nin tarihi

Bugün özgür yazılımlar arasında bulunan ve çoğunlukla GPG olarak adlandırılan yazılım hayatına Phil Zimmermann'ın yazdığı Pretty Good Privacy (PGP) adıyla başladı. PGP muhtemelen özgür yazılım ve özgür bilgi alanındaki en ilham verici hikayelerden birine sahip.

PGP hayatında 1991'de ilk sürümünün o zamanların yaygın İnternet iletişim platformu olan [Usenet'lere](https://en.wikipedia.org/wiki/Usenet) yüklenmesi ile başladı. Özellikle sonradan sorun olacak ABD yasaları 40 bit genişliğinin üzerindeki anahtarlarla çalışan yazılımların ithalatını yasaklamakta olduğundan Zimmermann'ın isteği üzerine çeşitli arkadaşları aracılığı ile kim zaman ankesörlü telefonlar ve [akustik eşleyiciler](https://en.wikipedia.org/wiki/Acoustic_coupler) aracılığı ile dağıtımı sağlanmıştır.

Yazılım özgür olmamakla birlikte Zimmerman ticari olmayan kullanımları için bir ücret talep etmemiş ve PGP'nin kaynak kodunu da yazılımla birlikte dağıtmıştır. Yazılımın dağıtılması beklendiği üzere ABD hükümetinin dikkatini çekmiş ve Zimmermann ABD askeri ihracat yasasına muhalefetten dava edilmiştir. Aynı zamanda PGP'nin kullandığı [RSA](https://en.wikipedia.org/wiki/RSA) algoritmasının lisans haklarına sahip şirket de konuya dahil olmuştur.

Zimmermann'ın PGP'nin yayılması ve insanlarca özgürce kullanılabilmesi için ortaya attığı fikir ise takdire değerdir. Her ne kadar kriptografik aracın ihracatı kanunun engeline takılıyor olsa da ABD anayasasının fikir özgürlüğü hükmü kişilerin yayınladıkları kitapları mutlak suretle korumaktadır. Bu kapsamda Zimmermann [OCR](https://en.wikipedia.org/wiki/Optical_character_recognition) uyumlu bir yazı tipi ile birlikte [PGP'nin tüm kaynak kodunu](https://html.duckduckgo.com/html?q=PGP%20Source%20Code%20and%20Internals.) MIT yayınevinden yayınlamıştır. Bu sayede kitap anayasal koruma altında dağıtılmış ve dileyenler kitabın cildini ayırarak tarama yardımı ile PGP'ye erişme imkanı sağlamıştır.

PGP'nin Zimmermann tarafından şirketleştirilmesi üzerine [Özgür Yazılım Vakfı](https://fsf.org) öncülüğünde [GnuPG](https://en.wikipedia.org/wiki/GNU_Privacy_Guard#History) adı ile özgür bir yazılım olarak OpenPGP standardına uygun şekilde geliştirilmeye başlanmıştır.

## GPG kullanmak

GPG genel olarak kullanılması zor görülen bir yazılımdır. Bu görüş yazılımın neredeyse 30 yıllık geçmişinde teknik çevrelerce kullanılmasından gelmekte ise de son yıllarda özellikle mahremiyet endişesinin yükselişte olduğu günümüzde son kullanıcı için fazlasıyla kullanışlı yazılımlar geliştirilmiştir. Bu bakımdan artık GPG sadece siyah beyaz uçbirimde çalışan bir yazılım olmaktan çıkmış ve her seviyeden bilgisayar kullanıcısının kolaylıkla kullanabileceği bir hal almıştır.

Elbette GPG kullanıcılarını küçük çocuklar gibi gören ve onların iyiliğini(!) onların adına ve çoğu zaman onlara rağmen düşünen diğer güvenlik vadeden yazılımlar gibi değildir. GPG kullanıcıların kendilerine ve çevrelerine olan güvenine dayanır. [Bu bakımdan GPG gücü ve hali ile sorumluluğu koşulsuz şartsız kullanıcılara verir.](https://oyd.org.tr/en/articles/defense-of-gpg/)

Bu rehber ile GPG kullanımını herkes için kolaylaştırmak ve anlaşılabilir kılmak amaçlanmıştır. Bunu yaparken GPG'nin kullanıcıya aktardığı güç korunmaya çalışılmıştır. Bu bakımdan kullanıcının güvenlik ve sorumluklarını sınırlandıran uygulamalara yer verilmemiştir. 

Her seviyeden kullanıcı için kullanım tavsiye ve rehberlerimize göz atabilirsiniz:

* [Kolay GPG anahtar üretimi](gpg-anahtar-uretimi.md)

* [Gelişmiş GPG anahtar üretimi](gpg_gelismis_anahtar_uretimi.md)

* [GPG anahtarını güvenle saklamak](anahtar-saklama.md)

* [GPG anahtarının kağıt yedeğini almak](paperbackup.md)

* [GPG ile uçbirimde işlemler](ucbirim_gpg.md)

* [GPG ile grafik arayüzde işlemler](gui_gpg.md)

* [GPG ile e-posta şifreleme](yazisma_guvenligi/openpgp.md)
