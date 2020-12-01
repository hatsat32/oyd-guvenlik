# Yetkilendirme Güvenliği

Login veya yetkilendirme GNU/Linux dahil olmak üzere neredeyse her bilgisayar sisteminin temel güvenlik tedbirlerinden biridir. Ekran kilidi olarak yaygın şekilde kullanıcıların karşısına çıkan yetkilendirme sistemleri, bilgisayara kimlerin hangi yetki ile erişeceğine ve erişime olan kişilerin belirlenmesinde kullanılır.

En temel yetkilendirme kullanımı kullanıcı adı ve parola şekilindedir. Her kullanıcı bir kullanıcı adı ile tanımlanır ve bu kullanıcıya giriş yapabilmesi için bir parola verilir. Söz konusu parola kullanıcılar tarafından sır olarak saklanır ve sisteme girişte kendilerine sorulur. Bu bakımdan yetkilendirme sisteminin güvenliği [parolanın güvenliği](https://guvenlik.oyd.org.tr/beseri_guvenlik/parolalar.html) ve kullanıcıların sır tutabilmesine bağlıdır.

Yetkilendirme sistemlerine sunulabilecek diğer girdiler; tek kullanımlık kodlar (OTP), biyometrik veriler (parmakizi vb.) ve kriptografik araçlar (akıllı kartlar, Yubikey) olarak çeşitlendirilebilir. Bu girdiler tek başına yetkilendirme için yeterli görülebileceği gibi ikinci faktör olarak parola ile birlikte sistem güvenliğini arttırmak için de kullanılabilir. Bu sayede bir kullanıcının sistemde yetkilendirilmesi bilgiği bir şey ile sahip olduğu bir şeye gereksinim duyacağından yetkilendirme için bir saldırganın edinmesi gereken kaynak arttırılmış olur.

## İkinci faktör

İkinci faktör olarak tercih edeceğiniz sistem tamamen kullanım ve güvenlik ihtiyaçlarınıza bağlıdır. Kimi sistemler var olan donanımlarınızı (akıllı telefon, parmak) kullanabilirken kimileri kriptografik bir aracı gerektirmektedir. Bu anlamda hem fiziki hem de kullanım bakımından bir miktar külfet getirmekle hangi yöntemin daha faydalı olacağı kullanım koşuluna bağlıdır.

Akıllı cihazlardan google-authenticator ile yapılaca OTP yetkilendirmesi hali hazırda sahip olunan bir cihazı kullanmakla en düşük maliyeti ortaya çıkaracak ve sürekli yanınızda taşıdığınız bir cihazı unutma ihtimalini doğurmayacaktır. Lakin her bilgisayarınıza giriş yapmak istediğinizde telefonunuza da erişmeniz ve kodu ekrana girmeniz gerekeceğinden yorucu bir duruma dönüşebilir sık kullanılan bilgisayarlarda. 

Parmak izi kullanan sistemler kullanım kolaylığı sunsa da söz konusu sistemler arasında en az güvenli olandır. Hem parmak izi hataya açık bir sistem olarak haklı olarak erişmeniz gereken bir sisteme erişememenize sebep olabilir hem de bir saldırganın en kolay aşabileceği ikinci faktör konumundadır. Filmlerdeki gibi parmağınızdan olmakla görece basit [yöntemlerle parmak izi sistemlerinin aşılması](https://www.forbes.com/sites/daveywinder/2019/11/02/smartphone-security-alert-as-hackers-claim-any-fingerprint-lock-broken-in-20-minutes/) mümkündür.

Kriptografik araçlar ise her iki sistemin bir birleşimini sunmaktadır. Bu cihazlar hem taklit edilip aşılması zor hem de pratik olarak kullanması çok kolaydır. Lakin [Yubikey](https://yubico.com] gibi cihazlar hem pahalı hem de kolay elde edilebilen araçlar değildir. Bu araçların kurulumları da bir miktar karmaşık olsa da muhtemelen fiziki güvenliğiniz için en iyi seçenek olmaktadırlar. Tek eksik yön bu cihazları sürekli taşımanız gerektiğinden bunu yapmanın pratik bir yolunu da hayatınıza ekleme zorunluluğudur.

Yetkilendirme güvenliği için ikinci faktör olarak kullanılabilecek sistemlere ilişkin rehberlerimize aşağıdaki bağlantılardan erişebilirsiniz:

[Google-Authenticator ile yetkilendirme](cihaz_guvenligi/ga_pam.md)

[Yubikey ile yetkilendirme](cihaz_guvenligi/yubikey_pam.md)

[Parmak izi ile yetkilendirme](cihaz_guvenligi/parmak_pam.md)
