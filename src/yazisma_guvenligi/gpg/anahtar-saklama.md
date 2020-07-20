# Anahtar yönetimi

**Anahtar yönetimi** GPG'nin en tehlikeli ve önemli parçasıdır. Öyle ki; GPG'nin tüm gücü şifreleme imkanını tamamen sizin elinize vermesidir. Elbette büyük güç büyük sorumlulukla gelmekte ve bu sorumluluk da kendi anahtarınızı kendinizin yönetmesi olmakta. Anahtarı kaybetmenizin bedeli şifrelediğiniz verileri sonsuza kadar kaybetmeniz olacağı gibi anahtarınızın kaybı tüm kimliğinizin ile birlikte anahtardan dolayı size duyulan güveninde yok olmasına sebep olacaktır.

Doğru bir anahtar yönetiminin birkaç unsuru bulunmakta:

* __Yedekleme__ GPG ile tüm şifreleme cihazınızda gerçekleştiğinden ve sorumluluğu da size ait olduğundan, anahtarınızı bir aksilik durumunda geri verecek bir otorite(!) bulunmaz. Gizli anaharınızın yedeğini uygun şekilde almanız gereklidir.
* __Saklama__ GPG anahtarınızı yedeklediğiniz kayıt medyasının ve konumunun doğru ve ihtiyaçlarınıza uygun olarak seçilmiş olması gereklidir. Her kayıt medyasının bir tür saklama sorunu içerdiğini ve bu yedekleri kime teslim ettiğiniz veya nereye koyduğunuz gelecek için önemlidir.
* __Planlama__ GPG anahtarınızın başına gelebilecekleri düşünerek buna uygun planlama yapmanız gerekir. Aksi halde tedbirin sınırı olmayacağından gereğinden fazla çaba harcamanız mümkündür.

## Planlama

Planlamanızı sağduyu ile yapın. Her tedbir planlaması gibi bir risk yönetimi yapmanız yerinde olacaktır. Bunun için kendinize aşağıdaki soruları sorun ve cevaplarına göre uygun tedbirleri alın.

1. Anahtarımı kaybetmeme sebep olacak tehlikeler neler?
Dizüstünüzü kaybetmeniz, sabit sürücünüzün bozulması, telefonunuzu kaybetmeniz, evinizi su basması vs..

2. Anahtarımı kaybetmeme sebep olacak tehlikelerin gerçekleşme ihtimalleri nedir?
Sıklıkla seyyahat ediyorsanız ve anahtarınızın tek kopyası dizüstünüzde ise mesela yüksek
Bir afete uğrama ihtimaliniz ise düşük

3. Anahtarımı kaybedersem ne kadar üzülürüm?
Tüm e-postalarınızı, dosyalarınızı anahtarınız ile şifreliyorsanız kesinlikle günlerce ağlarsınız.
Ara sıra gpg ile yazışıyor, anahtarınızı imzalatmıyor ve önemli görmüyorsanız yenisini üretip geçebilirsiniz.

4. Ne kadar zaman ve kaynak ayırabilirim?
7 kıtada 3 farklı konumda titanyuma kazınmış yedekler alabiliyorsanız ne güzel...
Bir saatiniz var ise bu işe zaman ayırabilecek hızlıca elinizdekileri kullanabilirsiniz.

## Yedekleme

Yedeklemek anlam bakımından elinizdeki bir verinin kötü bir ihtimale karşı bir kopyasının alınmasını ve saklanmasını ifade eder. GPG anahtarınızı kullanabilmek için muhtemelen bir cihazda tutuyor olacaksınız. İki veya daha cihazınızda bu anahtarın olması kötü de olsa bir nevi yedekleme sayılabilir.

Şayet vaktiniz yoksa veya anahtarınız o kadar önemli değil ise basitçe anahtarınızı dilediğiniz bir kayıt medyasına kopyasını alıp evinizin bir köşesine kaldırabiliriniz. Bu her halukarda offline bir yedeğinizin bildiğiniz bir yerde durmasının rahatlığını size verir.

Anahtarınıza önem veriyorsanız veya kaybetmenizin ciddiyeti her türlü önlemi almanızı gerektirecek düzeydeyse en az iki kopyanın mümkünse farklı kayıt ortamlarında (dvd vd usb bellek gibi) aynı tehlike modelini içermeyen farklı konumlarda (eviniz ve şehir dışındaki arkadaşınız gibi) bulundurulması gerekliliklerinizi karşılayabilir.

### Anahtarınızın yedeğini almak

### GNU/Linux

* Şayet uçbirim (terminal) aşinalığınız varsa açacağınız bir uçbirim ekranında aşağıdaki komutu çalıştırın

`gpg --export-secret-key --armour [anahtar id veya e-posta adresi] >  [anahtarın kaydedileceği dizin]`

kurulumunuza bağlı olarak size anahtarınızın parolasını soracaktır. Parolasını girmeniz üzerine anahtarınızın yedeğini verdiğiniz dizine kaydedecektir. Emin olmak için dosyanın içeriğini açıp bakmanızı ve "-----BEGIN SECRET KEY-----" ile başlayan satırları gözle bir kontrol etmeniz önerilir.

* Şayet Kleopatra gibi GUI arayüz kullanıyor iseniz, arayüzde Export veya backup gibi ifade edilen seçeneği arayıp talimatları takip edin. Anahtarınızın yedeğini bir dosya olarak kaydettikten sonra dosyayı dilediğiniz gibi yedekleyebilirsiniz. Şayet arayüz size `armour` veya `base64` gibi bir ifade ile seçenek sunuyor ise seçmenizi öneririz. Böylece yedeğinizi gerekirse kağıda basabilirsiniz.

### Android

Android'de GPG istemcisi [OpenKeychain](https://www.openkeychain.org/) kullanılmakta.

* Ana ekranda size ait gizli anahtarlarınız ile tüm diğer açık anahtarlarınız listeleinir.

* Gizli anahtarınızın üstüne tıklayıp sağ üst köşeden menüyü açıp backup/yedekle seçeneğine tıklayın.

* OpenKeychain yedek alacağınız anahtarınızı ayrıca AES256 ile şifreleyecektir. Bu sebeple size dörtlü şekilde ayrılmış dokuz numara verecektir. Bu numaraları aralarındaki - işaretleri de dahil şekilde bir kağıda yazın ve güvenli bir yerde tutun.

* Bu noktadan sonra yedeğinizi share/paylaş seçeneği ile ağ üzerinden veya telefonunuzun dahili hafızasına kaydedip offline olarak bilgisayarınıza aktarabilirsiniz. Biz açıkça dertli olmayacaksa offline seçeneği tavsiye ederiz.

* __ÖNEMLİ NOT!__: OpenKeychain ile aldığınız yedek dosyası ayrıca AES256 ile size verilen parola ile şifrelidir. Şayet bu şifreyi çözmeden dosyayı yedeklemeye karar verirseniz verilen parolayı da **MUTLAKA** güvenli şekilde saklamak zorundasınız. Bunun yerine bilgisayarınızda GPG ile şifreyi çözebilir ve elde ettiğiniz anahtarı bu şekilde OpenKeychain'in verdiği parolaya ihtiyaç duymadan da saklayabilirsiniz.

## Saklama

Anahtarınızı çok çeşitli şekillerde saklamanız mümkündür;

* __Kayıt medyası__: Yedeğinizi; sabit sürücü, usb bellek, flash kart, cd-rw, dvd-r/+r, kağıt çıktısı gibi ortamlarda saklamanız mümkündür. Anahtar dosyası en fazla 4kb civarında olduğundan yer sıkıntısı çekmeyeceksiniz.

* __Saklama yeri__: Yedeğinizi saklayacağınız yeri iyi seçmeniz gereklidir. Şayet evinizin soyulmasından endişeleniyorsanız ve bilgisayarınız ile birlikte yedeklerinizi aldığınız pahalı görünümlü sabit sürücünüz de elinizden giderse yedeğinizin size bir faydası olmayacaktır. Bu sebeple konum olarak yedeğinizin yerini ihtiyaçlarınıza göre seçmenizi öneririz.

* __Saklama koşulları__: Yedeğinizi kaydettiğiniz medyanın saklama koşullarına uymanız şiddetle önerilir. CD medyalar zamanla [disk rot](https://en.wikipedia.org/wiki/Disc_rot) riski içerir. Bu yüzden optik disklerde DVD+R veya Blurday kullanmanız ve kutusunda dikine nemsiz ortamda saklamanız önerilir.

Sabit diskler, usb bellek ve flash kartlar zamanla veri bozulmasına uğrayabilir. Sabit diskler bu bakımdan hareketli parçaları sebebi ile çok daha risk altındadır. Bu ortamları kullanırken dikkatli olunması ve iyi bir değerlendirme yapılması önerilir.

Kağıt bu açıdan akıllara son gelen seçenek olsa da insanlık tarihinin en dayanıklı kayıt ortamı olarak hala tartışmasız bulunmaktadır. Bu sebeple anahtarınızın bir yedeğinin kağıda basılmış olarak bir yerde saklanması fiyat/kafa rahatlığında tartışmasızdır. Anahtarınızın --armour yani base64 encode halini bir kağıda dümdüz basıp bir kenara kaldırabileceğiniz gibi geri dönüşümü karekodlar aracılığı ile kolaylaştırmak için [paperbackup](https://github.com/intra2net/paperbackup) gibi bir araçtan da faydalanabilirsiniz. [Kağıt yedek rehberimiz size bu konuda yardımcı olabilir.](paperbackup/paperbackup.md) Yedeklerinizi katlamadan su geçirmez bir şekilde paketleyip ışık görmeyen bir yerde saklamanız önerilir.

## Kıyamet!

Şayet kıyamet koparsa diye GPG'nin **iptal sertifikası** isminde bir seçeneği bulunmakta. Bu araç ile gpg size kısa bir çıktı vermekte ve anahtarınızı geri dönmeyecek şekilde kaybetmeniz durumunda anahtar sunucularına bu anahtarı göndermeniz ile anahtarınız kullanılmaz duruma gelmektedir. Şayet anahtarınızı *güven* oluşturmak için kullanıyorsanız küçük bir adım olarak bunu yapmanız önerilir.

İptal sertifikasını oluşturmak için GNU/Linux'ta uçbirim aracılığı ile şu komutu kullanabilirsiniz.

* `gpg --generate-revocation [anahtar kimliği veya e-posta adresi] > [sertifikanın kaydedileceği dizin]

* GPG'ye ciddiyetinizi belirttikten sonra iptal için bir gerekçe girip dilerseniz yazılı bir gerekçe ekleyip sertifikayı üretim için onaylayın.

* Anahtara ait parolanızı girdiğinizde iptal sertifikanız kaydedilmiş olacaktır. Bu dosyayı sayısal olarak veya bir kağıda bastırıp güvenli bir yerde saklayın.

* Şayet iptal sertifikasını kullanmanız gerekirse iptal sertifikasını anahtar gibi import/içe aktar seçeneği ile GPG'ye girip `gpg --send-keys [iptal sertifikasının dizini]` komutunu kullanarak sunuculardaki anahtaırnızı iptal edebilirsiniz.

## Önerimiz

Şayet durum değerlendirmesi yapmak istemiyorsanız aşağıdaki tavsiyemizi değerlendirip çokça tehlikeye karşı kolayca güvende kalabilirsiniz.

* Anahtarınızın yedeğini alın.

* Anahtarınızı bir 2 adet DVD-R'ye(DVD'yi anahtar dosyanızın kopyaları ile tamamen doldurabilirseniz muhteşem olur) bir adet SD Karta kopyalayın ve 3 kopya paperbackup ile kağıda basın.

* Her kağıt yedeğin yanına bir tane sayısal yedeği ekleyip katlamadan kilitli poşet içinde 3 örnek hazırlayın.

* Bir örneği kendiniz evinizde, bir örneğini güvendiğiniz bir arkadaşınızda bir örneğini de şehir dışında güvenli bir yerde saklayın. Bu bilgiyi kimse ile paylaşmayın, yedekleri posta/kargo ile göndermeyin.
