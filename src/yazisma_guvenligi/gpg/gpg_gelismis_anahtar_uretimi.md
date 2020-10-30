# İleri Anahtar Üretimi

GPG, RSA algoritmasına dayalı asimetrik şifreleme kullanmaktadır. RSA anahtar çiftinin uzun dönem kullanılması ve hali ile saklanması gereklidir. Bu bakımdan hem üretimi hem de saklanması bakımından dikkat gösterilmesi gereklidir. Özellikle şifreleme ihtiyacınız mahremiyet beklentisini aşıp güvenlik gerektiren durumlara yönelik ise anahtar üretimi gibi kritik bir aşamayı olabilecek en az etmen ve şüphe ile yürütmek gerekmektedir.

## Güvenli ortam

Anahtarın üretimi sırasında kullanılan bilgisayar çok önemli bir girdinin kaynağıdır. Entropi, yani cihazınızda anahtar üretimi sırasında kullanılacak rastgeleliğin kalitesi bilgisayarınız ve işletim sisteminize bağlıdır. Aynı zamanda bilgisayarınızda kötücül bir yazılımın çalışmaması veya bilmediğiniz bir açığın söz konusu olması durumunu da göz önünde bulundurmanız faydalı olabilir. Sonuç olarak tehdit modeliniz bu tip sorunları kapsamıyor olsa bile bir kere üretip belki hayatınız boyunca kullanacağınız bir anahtarı çok kolay tedbirler altında üretmenin bir zararı da yoktur.

Şayet bu amaçla rastgele bir konumdan nakit ödeme ile bir bilgisayar alıp tüm ağ araçlarını söküp asla İnternet'e bağlamamayı gerektirecek bir tehdit modeliniz yok ise yapabileceğiniz en kolay ve etkili yöntem bir USB bellek üzerinden [Tails](https://tails.boum.org) başlatarak anahtarınızı bu işletim sistemi üzerinde üretmeniz olacaktır.

[Tails rehberinin yazılmasına katkı verebilirsiniz](https://git.oyd.org.tr/oyd/guvenlik/issues/46)

Bir diğer seçenek ise anahtarınızı bir güvenlik donanımı olan [Gnupg akıllı kart](https://www.floss-shop.de/en/security-privacy/smartcards/13/openpgp-smart-card-v3.3?number=654010) veya [Yubikey](https://www.yubico.com/products/) üzerinde üretmektir. Bu yöntemin faydası güvenlik donanımından başka bilgisayarın hiçbir sistemi anahtarla temas etmemiş olacaktır. Tüm kriptografik işlemler bu cihaz üzerinde güvenli olarak gerçekleşeceğinden birden fazla cihazda güvenli şekilde anahtarınızı kullanmak da kolaylaşmaktadır. Akıllı kart üzerinde anahtar oluşturmanın kötü tarafı ise yedekleme imkanınızın olmamasıdır. Şayet kartınızı kaybeder veya bir sebepten bozarsanız anahtarınız sonsuza kadar şifrelediğiniz verilerle birlikte kaybolacaktır. Akıllı kart kullanmak ama yedek de almak istiyorsanız anahtarınızı bilgisayarda üretip ardından akıllı karta yüklemeniz de mümkündür.

[Akıllı kart ve Yubikey rehberi yazarak bu rehbere katkı verebilirsiniz](https://git.oyd.org.tr/oyd/guvenlik/issues/59)

## Anahtarı Planlamak

### Anahtar işlevleri

Bir GPG anahtarı 4 temel işlev taşıyabilir. Bunlar; sertifika, şifreleme, imzalama, yetkilendirmedir.

* Sertifika: Başka anahtarları imzalamak için gereken işlevdir.
* Şifreleme: Anahtar ile şifreleme yapmak için gereken işlevdir.
* İmzalama : Mesaj veya dosyaların bütünlüğünü ve aitliğini kanıtlamak için gereken imzanın atılabilmesi için gereken işlevdir.
* Yetkilendirme: SSH ve benzeri sistemlerde kimlik kanıtlayarak yetkilendirme almak için gereken işlevdir.

GPG anahtarları bir tane ana anahtar ve çeşitli sayıdaki alt anahtardan oluşur. Sertifika yetkisi ana anahtara ait olmakla birlikte şifreleme, imzalama ve yetkilendirme yetkileri ana anahtara veya alt anahtarlara verilebilmektedir.

### Sertifika yetkisinin önemi

Anahtar sayısı ve yetkilerini değerlendirirken sertifika yetkisi önemlidir. GPG bir şifreleme yazılımı olduğu kadar kimlik yönetimi de sağlamaktadır. Sertifika yetkisi GPG kullanıcısının diğer kullanıcıların anahtarlarını imzalayarak [güven ağı](https://en.wikipedia.org/wiki/Web_of_trust) oluşturulmasını sağlamakta ve alt anahtarlara duyulan güveni de getirmektedir. Bu bakımdan alt anahtarların ifşa olması gibi olumsuz bir durumda ana anahtarın korunabilmiş olması yeni alt anahtarların eski güven ağı kaybedilmeden tekrar oluşturulmasına imkan sağlamaktadır.

Günlük kullanımda sertifika yetkisi özellikle gerekli değildir. Keza alt anahtarlara ait olan şifreleme imzalama ve yetkilendirme işlevleri GPG'nin günlük kullanımı için yeterlidir. Ancak bir başka GPG anahtarının imzalanması, yeni bir alt anahtar oluşturulması veya tarihi geçen bir anahtarın yenilenmesi gibi sıklıkla gerekmeyen durumlarda ana anahtar gerekli olmaktadır. Bu bakımdan ana anahtarı güvenle saklanacağı bir ortama alıp, çalınma ve ifşa olma tehlikesi taşıyan cihazlarda sadece alt anahtarları bulundurarak belirli bir güvenlik elde etmek mümkündür. Bu uygulamanın kötü tarafı ise tüm anahtarlarınızın bir akıllı karta alamayacak olmanız ve her sertifika işlemi için anahtarınızı güvenli alandan çıkarmanın zahmetine katlanmaktır.

### Anahtar boyutu

Anahtarınızın boyutu doğrudan sağlayacağı güvenlik ile ilişkilidir. GPG'nin kullandığı RSA algoritmasında 1024 ile 4096 bit arasında bir anahtar seçmeniz mümkündür. Bugün Türkiye'de kanuna bağlı olarak kullanılan e-imza sertifikaları RSA2048 bit idir. RSA1024 ise artık güvenli kabul edilmemektedir. Anahtarınızın büyüklüğü geleceğe dönük olarak güvenli sayılacağı ömrü de uzatacağından en büyük anahtar genişliğini seçmeniz kesinlikle tavsiye edilir. Anahtar boyutuna ilişkin temel endişe kriptografik işlemlerin işlemci gücü bakımından giderek zorlaşmasıdır. Günümüzde en kötü akıllı mobil cihazın bile işlemci gücü 4096 bit anahtar boyutları ile makul sürelerde işlem yapma imkanı sağladığından bu endişe güncelliğini temel kullanımlar açısından görece yitirmiş durumdadır.

### Anahtar algoritması

GPG'nin güncel versiyonu olan 2.0.19 artık tarihi olarak kullanılan RSA algoritmasının yanında [Elliptic-curve cryptography (ECC)](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography) de desteklemeye başlamıştır. ECC, RSA ile karşılaştırılabilir güvenlik seviyeleri için daha kısa anahtarlar oluşturulmasına imkan sağlamaktadır. [Kuantum bilgisayarlar](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography#Quantum_computing_attacks) ve [arkakapı](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography#Backdoors) endişeleri taşımakla birlikte pratik ve daha kolay yönetilebilir anahtarlara ihtiyaç duyulması durumunda en yüksek anahtar genişliğinde tercih edilmesi düşünülebilir.

### Anahtar yapısı

Şayet GPG'den standart bir anahtar üretmesi istenir ise aşağıdaki gibi bir anahtar oluşturacaktır.

├─Ana anahtar (sertifika ve imzalama)
└─Alt anahtar (şifreleme)

Bu anahtar ana anahtar ile imzalama işlemini yapacağından neredeyse her işlemde ana anahtarın da sistemde bulunması ve kullanılabiliyor olması gereklidir. GPG'nn böyle bir tercihte bulunmasının iki nedeni vardır. Öncelikle sertifika ve imza işlemleri temelde benzerdir ve ikisi de güven ilişkisi yaratır. Bu bakımdan iki benzer işlemi tek anahtarın görmesi anlamlıdır. İkinci olarak temel işlemleri yapmak için gereken en az anahtar miktarı bu şekilde elde edildiği için anahtar boyutu da küçük olmaktadır.

Fakat tehdit modelinize bağlı olarak daha güvenlik işlevi gösterebilecek bir düzen oluşturmak mümkündür. Sertifika yetkisinin anahtara sağladığı güven ilişkisini günlük kullanımdan yalıtarak alt anahtarların; vadesini, güvenini ve döngüsünü güvenli şekilde yönetmek mümkündür. Şöyle ki;

* Şifreleme anahtarınız çalınan dizüstü bilgisayarınız ile birlikte açığa çıkarsa geçmişe dönük olarak tüm iletişim ve şifreli dosyalarınızın açılması mümkündür.

* İmza anahtarınız benzer bir talihi paylaşırsa bir saldırgan bu anahtarı kullanarak sizi taklit edebilir; kullandığınız amaca bağlı olarak size ait görünen metin, dosya ve kod yaratabilir.

* yetkilendirme anahtarınızın ortaya çıkması bu anahtara bağlı olarak giriş yaptığınız tüm sistemlerin ele geçirilmesi anlamına gelebilir.

Bu neden ile GPG'nin kalıcı anahtar modelini biraz kullanım pürüzü yaratacak da olsa elle [geçici(ephemeral)](https://cryptography.fandom.com/wiki/Ephemeral_key) anahtar modeline çevirebilirsiniz. Bu yöntem bir bakııma [OTR](../otr.md) ve [OMEMO](../omemo.md) sistemlerinde kullanılan yönteme benzemekle fark olarak her mesajda değil sizin belirleyeceğiniz daha uzun aralıklarda değişim yapmanızı gerektirir.

Basitçe ifade etmek gerekirse;

1. Ana anahtara sadece sertifika yetkisi verilir.
2. 3 alt anahtara şifreleme, imzalama, yetkilendirme işlevleri verilir.
3. Ana anahtara 3 yıl gibi uzun bir vade süresi verilir.
4. Alt anahtarlara 3 ay gibi görece kısa bir vade süresi verilir.
5. Ana anahtar anahtarlardan ayrılır ve offline olarak güvenli saklanır.
6. Alt anahtarlar cihazlara aktarılır ve kullanılır. Gerekli görüldükçe veya belirlenen süreler ile değiştirilir. Değişim ana anahtarla yapılır ve imzalanarak güven ağına dahil edilir.

Bu çabaya katlanmak her kullanıcının kendi durumuna göre karar vermesi gereken bir tercih. Keza sizin güvenlik ihtiyaçlarınız için bu durum aşırı olabilir ve sürekli GPG ile uğraşmak canınızı sıkabilir. Geçmişe dönük olarak şifreli verilerinizi sürekli olarak yeniden şifrelemek veya yokoluşa terk etmek sorun yaratabilir. Sizinle iletişime geçen kişiler sürekli olarak anahtarınızın yeni versiyonunu edinmekten sıkılabilir.

Bu süreci işletebilmek için ne yazık ki anahtarınızı baştan buna uygun olarak üretmeniz gerekmektedir. Anahtarlara verilen işlevler daha sonra değiştirilememektedir. Bu rehberde yukarıdaki amacı gösterebilecek bir anahtarın üretim ve kullanım süreci işlenecektir.

## Güvenli Anahtar Üretimi

Anahtar üretimi için güvenli ortamınızı elde ettikten sonra bir uçbirim açarak anahtar üretim sürecine başlayabilirsiniz.

GPG'nin uzman modunu çağırarak anahtar üretim sürecine başlayın.

`gpg --full-gen-key --expert`

Karşınıza aşağıdaki seçenekler çıkacaktır.

```
gpg (GnuPG) 2.2.19; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Lütfen istediğiniz anahtarı seçiniz:
   (1) RSA ve RSA (varsayılan)
   (2) DSA ve Elgamal
   (3) DSA (yalnız imzalamak için)
   (4) RSA (sadece imzalamak için)
   (7) DSA (yeteneklerini belirtin)
   (8) RSA (yeteneklerini belirtin)
   (9) ECC and ECC
  (10) ECC (sign only)
  (11) ECC (set your own capabilities)
  (13) Existing key
  (14) Existing key from card
Seçiminiz? 


```
Bu noktada RSA veya ECC algoritmaları arasındaki kararı vermiş olmanız gereklidir. Rehber RSA algoritmasını geçmişi ve kuantum endişeleri nedeni ile tercih edecektir. 8 tuşuna basıp "enter" ile devam edin.

```
bir RSA anahtarı için olası eylemler: İmzalama Onayla Şifrele Kimlik kanıtla 
Şimdilik mümkün eylemler: İmzalama Onayla Şifrele 

   (1) İmzalama yeteneğini açar/kapar
   (2) Şifreleme yeteneğini açar/kapar
   (3) Kimlik kanıtlama yeteneğini açar/kapar
   (0) Bitti

Seçiminiz? 

```

Bu aşamada ana anahtarınızı ürettiğiniz için amacımıza bağlı olarak sadece Onaylama (sertifika) yetkisinin *mümkün eylemler* arasında kalmasının sağlanması gerekli. Bunun için sırası ile 1-enter-2-enter tuşlayarak imzalama ve şifreleme yetkisini anahtardan ayırabilirsiniz. Bu aşamadan sonra aşağıdaki noktaya vardığınızda 0 tuşlayıp "enter" ile işlemi tamamlayabilirsiniz.

```
bir RSA anahtarı için olası eylemler: İmzalama Onayla Şifrele Kimlik kanıtla 
Şimdilik mümkün eylemler: Onayla 

   (1) İmzalama yeteneğini açar/kapar
   (2) Şifreleme yeteneğini açar/kapar
   (3) Kimlik kanıtlama yeteneğini açar/kapar
   (0) Bitti

Seçiminiz? 
```

GPG sizden anahtar boyutunuzu girmenizi isteyecektir. En yüksek güvenliği sağlayan anahtar genişliği olan 4096 sayısını girerek "enter" tuşlayın.

```
RSA anahtarları 1024 bit ile 4096 bit arasında olmalı.
İstediğiniz anahtar uzunluğu nedir? (3072) 4096
```

Bu aşamadan sonra anahtarınızın geçerlilik süresini belirlemeniz istenecektir. Bu süre tercihi size kalmış olmakla birlikte ana anahtarınızın geçerliliğini yıl düzeyinde yapmanız kolaylık sağlayacaktır. Süreyi belirlemek için istediğiniz miktarı ardından birimi belirten harf ile girip "enter" tuşlayın.

```
İstenen anahtar uzunluğu: 4096 bit
Lütfen anahtarın ne kadar süreyle geçerli olacağını belirtin.
         0 = anahtar süresiz geçerli
      <n>  = anahtar n gün geçerli
      <n>w = anahtar n hafta geçerli
      <n>m = anahtar n ay geçerli
      <n>y = anahtar n yıl geçerli
Anahtar ne kadar geçerli olacak? (0) 3y
```

GPG'nin süreyi doğrulamak için sorduğu soruya evet anlamında "y" veya "e" tuşlayarak devam edebilirsiniz.

```
Anahtarın geçerliliği Cum 25 Ağu 2023 09:45:04 +03 de bitecek.
Bu doğru mu? (e/H ya da y/N) y
```

Bu aşamadan sonra GPG size adınız ve e-posta adresinizi soracaktır. Doğal olarak burada doğru cevap vermek zorunda değilsiniz. Bir rumuz ve geçersiz bir e-posta adresi kullanabilirsiniz. Lakin bu durumda anahtarınız ile sosyal çevrenizde bir güven anahtarı oluşturmanızı zorlaştıracağı gibi size e-posta şifrelemek isteyen insanlara da bir külfet getirecektir. Kararı kullanım amacınıza göre belirleyebilirsiniz.

```
GnuPG anahtarınızı betimlemek için bir kullanıcı kimliği oluşturmaya ihtiyaç duyuyor.

Adınız ve Soyadınız: Claude Shannon
E-posta adresiniz: entropyrulez@bell.com
Önbilgi:
```

Karşınıza çıkacak doğrulamayı denetledikten sonra tamam anlamında "t" tuşlayarak devam edebilirsiniz.

```
Seçtiğiniz KULLANICI-KİMLİĞİ:
    "Claude Shannon <entropyrulez@bell.com>"

(A)dı ve Soyadı, (Y)orum, (E)posta alanlarını değiştir ya da (T)amam/Çı(k)? 
````

GPG size parolanızı soracaktır. Burada bir [**Zarola**](https://zarola.oyd.org.tr) kullanmanız hararetle tavsiye edilir. Anahtarınızın güvenliği bu parolaya doğrudan bağlı olduğundan bu parolanın unutmayacağınız şekilde olması ve yeterince entropi içermesini sağlamanın en kolay yolu Zarola yönteminden geçmektedir.

Bu aşamadan sonra cihazınız anakartınızın köşelerinde kalmış entropi için çırpınıp size anahtarınızı üretecektir. Bu süreç `/dev/random` aygıtınızda kalan entropi miktarı ve yenilenme hızına bağlı olarak yavaş olabilir. Bilgisayarınız ile bir şeyler yaparak bu süreci hızlandırabilirsiniz. Anahtarınız hazır olduğunda GPG sizi aşağıdaki çıktı ile karşılayacaktır.

```
(A)dı ve Soyadı, (Y)orum, (E)posta alanlarını değiştir ya da (T)amam/Çı(k)? t
Bir miktar rasgele bayt üretilmesi gerekiyor. İlk üretim sırasında biraz
hareket (klavyeyi kullanmak, fareyi hareket ettirmek, disklerden yararlanmak)
iyi olacaktır; bu yeterli rasgele bayt kazanmak için rasgele sayı
üretecine yardımcı olur.
gpg: anahtar 6CD5E60735205895 son derece güvenli olarak imlendi.
gpg: revocation certificate stored as '/home/alper/.gnupg/openpgp-revocs.d/A09D0D53E6BEEF6A971F64036CD5E60735205895.rev'
genel ve gizli anahtar üretildi ve imzalandı.

pub   rsa4096 2020-08-25 [C] [son kullanma tarihi: 2023-08-25]
      A09D0D53E6BEEF6A971F64036CD5E60735205895
uid                      Claude Shannon <entropyrulez@bell.com>
```

Şayet `gpg --list-secret-keys` komutunu çağırırsanız yeni anahtarınızı ve detaylarını görecek olmalısınız.

```
sec   rsa4096 2020-08-25 [C] [son kullanma tarihi: 2023-08-25]
      A09D0D53E6BEEF6A971F64036CD5E60735205895
uid           [   son  derece   ] Claude Shannon <entropyrulez@bell.com>
```

Artık alt anahtarların üretimine geçmek ve kullanılabilir bir anahtar oluşturmaya başlamak mümkündür. Aşağıdaki komut ile anahtarınızı düzenlemeye başlayabilirsiniz.

`gpg --edit-key --expert [key ID veya e-posta]`

Komut sizi aşağıdaki gibi bir çıktı ile karşılayacak ve promt'ta bekleyecektir.

```
gpg (GnuPG) 2.2.19; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Gizli anahtar mevcut.

sec  rsa4096/6CD5E60735205895
     oluşturuldu: 2020-08-25  son kullanma tarihi: 2023-08-25  kullanımı: C   
     güvencesi: son derece    geçerliliği: son derece
[   son  derece   ] (1). Claude Shannon <entropyrulez@bell.com>

gpg> 
```

`help` yazarak bu aşamada yapabileceğiniz işlemler hakkında bilgi alabilirsiniz.

```
gpg> help
quit        bu menüden çık
save        kaydet ve çık
help        bunu gösterir
fpr         parmakizini gösterir
grip        show the keygrip
list        anahtarı ve kullanıcı kimliğini gösterir
uid         N kullanıcı kimliğini seçer
key         N yardımcı anahtarını
check       imzaları sınar
sign        seçilen kullanıcı kimliği imzalar [* ilgili komutlar için aşağıya bakın]
lsign       kullanıcı kimlikleri yerel olarak imzalar
tsign       seçili kullanıcı kimlikleri bir güvence imzasıyla imzalar
nrsign      seçili kullanıcı kimlikleri yürürlükten kaldırılamayan bir imzayla imzalar
adduid      bir kullanıcı kimliği ekler
addphoto    bir foto kimliği ekler
deluid      seçili kullanıcı kimlikleri siler
addkey      bir yardımcı anahtar ekler
addcardkey  bir akıllı karta bir anahtar ekler
keytocard   bir akıllı karttan bir anahtarı taşır
bkuptocard  bir akıllı karttan bir yedekleme anahtarını taşır
delkey      seçili yardımcı anahtarları siler
addrevoker  bir yürürlükten kaldırma anahtarı ekler
delsig      seçili kullanıcı kimliklerden imzaları siler
expire      anahtar için ya da seçili yardımcı anahtarlar için zamanaşımı tarihini değiştirir
primary     seçili kullanıcı kimliğini asıl olarak imler
pref        tercihleri listeler (uzman)
showpref    tercihleri listeler (ayrıntılı)
setpref     Seçili kullanıcı kimlikler için tercih listesini belirler
keyserver   seçili kullanıcı kimlikler için tercih edilen anahtar sunucu adresini belirler
notation    seçili kullanıcı kimlikleri için bir simgelem belirler
passwd      anahtar parolasını değiştirir
trust       sahibiningüvencesini değiştirir
revsig      Seçili tüm kullanıcı kimliklerdeki imzaları yürürlükten kaldırır
revuid      Seçili tüm kullanıcı kimlikleri yürürlükten kaldırır
revkey      anahtarı ya da seçili yardımcı anahtarları yürürlükten kaldırır
enable      anahtarı kullanıma sokar
disable     anahtarı iptal eder
showphoto   seçili foto kimlikleri gösterir
clean       kullanışsız kullanıcı kimlikleri sıkıştırır ve kullanışsız imzaları anahtardan kaldırır
minimize    kullanışsız kullanıcı kimlikleri sıkıştırır ve tüm imzaları anahtardan kaldırır

* The 'sign' command may be prefixed with an 'l' for local signatures (lsign),
  a 't' for trust signatures (tsign), an 'nr' for non-revocable signatures
  (nrsign), or any combination thereof (ltsign, tnrsign, etc.).
```

`addkey` komutu ile anahtara alt anahtarlar eklemeye başlayabilirsiniz. Alt anahtar ekleme süreci ana anahtarın üretimi ile tamamen aynıdır. Yukarıdaki adımları tekrar ederek son noktada bir ana anahtar ve 3 belirli işlevi taşıyan alt anahtar üretmiş olmanız gereklidir.

```
sec  rsa4096/6CD5E60735205895
     oluşturuldu: 2020-08-25  son kullanma tarihi: 2023-08-25  kullanımı: C   
     güvencesi: son derece    geçerliliği: son derece
ssb  rsa4096/9D0FFCD0DE126F3D
     oluşturuldu: 2020-08-25  son kullanma tarihi: 2021-08-25  kullanımı: E   
ssb  rsa4096/3F7DB977B818DDB4
     oluşturuldu: 2020-08-25  son kullanma tarihi: 2021-08-25  kullanımı: S   
ssb  rsa4096/841A8F682342D15B
     oluşturuldu: 2020-08-25  son kullanma tarihi: 2021-08-25  kullanımı: A   
[   son  derece   ] (1). Claude Shannon <entropyrulez@bell.com>
```

Yukarıdaki gibi veya arzu ettiğiniz sonucu elde ettikten sonra `save` komutu ile değişiklikleri kaydedip çıkabilirsiniz. Artık anahtarınızın aşağıdaki gibi görünüyor olması gereklidir.

```
sec   rsa4096 2020-08-25 [C] [son kullanma tarihi: 2023-08-25]
      A09D0D53E6BEEF6A971F64036CD5E60735205895
uid           [   son  derece   ] Claude Shannon <entropyrulez@bell.com>
ssb   rsa4096 2020-08-25 [E] [son kullanma tarihi: 2021-08-25]
ssb   rsa4096 2020-08-25 [S] [son kullanma tarihi: 2021-08-25]
ssb   rsa4096 2020-08-25 [A] [son kullanma tarihi: 2021-08-25]
```

**ÇOK ÖNEMLİ NOT:** Bu noktada anahtarınızın yedeğini güvenli şekilde almanız **hayati** öneme sahiptir. Bunun için rehberdeki [Anahtar Yönetimi](anahtar-saklama.md) ve [Paperbackup ile kağıt yedek](paperbackup.md) rehberlerinden yardım alabilirsiniz.

## Ana anahtarın ayrılması

Ana anahtarı alt anahtarlardan ayırmanın GPG'de belirgin bir yolu bulunmamakta. Bu amacı gerçekleştirmek için biraz dolambaçlı bir yol kullanmak gerekiyor.

**ÖNEMLİ NOT:** Bu bölümde anahtar üzerinde geri döndürülemez işlemler yapılacağından ve işlemlerin bir kısmı yedekten anahtar almayı gerekli kıldığından tüm anahtarınızın yedeğini aldığınızdan emin olun.

Öncelikle anahtarınızın alt anahtarlarını dışarı çıkartmanız gerekmekte. Bu aşamada anahtarın UID'sini belirtmeniz gerekmekte keza e-posta ile bu işlem gerçekleşmiyor.

`gpg --armor --export-secret-subkeys [anahtar ID] > [kayıtdizini]`

Bu işlemin ardından anahtarınızı silin.

`gpg --delete-secret-keys [anahtar ID veya e-posta]`

GPG israrla bu anahtarı silmek isteyip istemediğinizi sorgulayacaktır. Endişesi konusunda haklı olmakla birlikte kararlılığınızı gösterip tüm sorularına olumlu cevap verin.

```
gpg (GnuPG) 2.2.19; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


sec  rsa4096/6CD5E60735205895 2020-08-25 Claude Shannon <entropyrulez@bell.com>

Bu anahtar, anahtar zincirinden silinsin mi? (e/H ya da y/N) y
Bu bir gizli anahtar! - gerçekten silinecek mi? (e/H veya y/N) y
```

Bu aşamadan sonra anahtarlığınızda sadece "pub" ile işaretli umumi anahtarınız kalmış olacaktır.

```
pub   rsa4096 2020-08-25 [C] [son kullanma tarihi: 2023-08-25]
      A09D0D53E6BEEF6A971F64036CD5E60735205895
uid           [   son  derece   ] Claude Shannon <entropyrulez@bell.com>
sub   rsa4096 2020-08-25 [E] [son kullanma tarihi: 2021-08-25]
sub   rsa4096 2020-08-25 [S] [son kullanma tarihi: 2021-08-25]
sub   rsa4096 2020-08-25 [A] [son kullanma tarihi: 2021-08-25]
```

Artık yedeğini aldığınız alt anahtarları geri yükleyerek ana anahtarınızı içermeyen kullanım anahtarınızı tamamlayabilirsiniz.

`gpg --import [yedek dizini]`

GPG parolanızı soracak ve doğru girmeniz ardından alt anahtarları ekleyecektir.

```
gpg: anahtar 6CD5E60735205895: "Claude Shannon <entropyrulez@bell.com>" değişmedi
gpg: To migrate 'secring.gpg', with each smartcard, run: gpg --card-status
gpg: anahtar 6CD5E60735205895: gizli anahtar alındı
gpg: İşlenmiş toplam miktar: 1
gpg:              değişmedi: 1
gpg:       gizli anahtarlar okundu: 1
gpg:   gizli anahtarlar indirildi: 1
```

`gpg --list-secret-keys` ile gizli anahtarlarınızı listelerseniz aşağıdaki gibi ana anahtarınızın sec# şekline işaretli olduğundan eksik olduğunu görebilirsiniz.

```

sec#  rsa4096 2020-08-25 [C] [son kullanma tarihi: 2023-08-25]
      A09D0D53E6BEEF6A971F64036CD5E60735205895
uid           [   son  derece   ] Claude Shannon <entropyrulez@bell.com>
ssb   rsa4096 2020-08-25 [E] [son kullanma tarihi: 2021-08-25]
ssb   rsa4096 2020-08-25 [S] [son kullanma tarihi: 2021-08-25]
ssb   rsa4096 2020-08-25 [A] [son kullanma tarihi: 2021-08-25]

```

Artık cihazlarınızda kullanacağınız sıyrılmış alt anahtarlarınızı dışarı çıkarıp aktarabilirsiniz.

`gpg --export-secret-keys --armor [anahtar ID veye e-posta]`

## Anahtarları akıllı karta aktarmak

Ürettiğiniz anahtarlarınızı daha güvenli kullanmak isterseniz bir Gnupg akıllı karta veya Yubikey gibi bir donanıma aktarabilirsiniz. Bu konuda yardıma ihtiyaç duyarsanız rehberlerimize danışabilirsiniz.

[Yubikey rehberi yazarak katkıda bulunabilirsiniz](https://git.oyd.org.tr/oyd/guvenlik/issues/59)

[GnuPG akıllı kart rehberi yazarak katkıda bulunabilirsiniz]

## Kaynaklar

- [Getting Started with GNU Privacy Guard ](https://spin.atomicobject.com/2013/09/25/gpg-gnu-privacy-guard/)

- [GPG Tutorial](https://futureboy.us/pgp.html#GettingStarted)

- [EFF GPG Guide](https://ssd.eff.org/en/module/how-use-pgp-linux)
