# Yetkilendirme Güvenliği

Login veya yetkilendirme GNU/Linux dahil olmak üzere neredeyse her bilgisayar sisteminin temel güvenlik tedbirlerinden biridir. Ekran kilidi olarak yaygın şekilde kullanıcıların karşısına çıkan yetkilendirme sistemleri, bilgisayara kimlerin hangi yetki ile erişeceğine ve erişime olan kişilerin belirlenmesinde kullanılır.

En temel yetkilendirme kullanımı kullanıcı adı ve parola şekilindedir. Her kullanıcı bir kullanıcı adı ile tanımlanır ve bu kullanıcıya giriş yapabilmesi için bir parola verilir. Söz konusu parola kullanıcılar tarafından sır olarak saklanır ve sisteme girişte kendilerine sorulur. Bu bakımdan yetkilendirme sisteminin güvenliği [parolanın güvenliği](https://guvenlik.oyd.org.tr/beseri_guvenlik/parolalar.html) ve kullanıcıların sır tutabilmesine bağlıdır.

Yetkilendirme sistemlerine sunulabilecek diğer girdiler; tek kullanımlık kodlar (OTP), biyometrik veriler (parmakizi vb.) ve kriptografik araçlar (akıllı kartlar, Yubikey) olarak çeşitlendirilebilir. Bu girdiler tek başına yetkilendirme için yeterli görülebileceği gibi ikinci faktör olarak parola ile birlikte sistem güvenliğini arttırmak için de kullanılabilir. Bu sayede bir kullanıcının sistemde yetkilendirilmesi bilgiği bir şey ile sahip olduğu bir şeye gereksinim duyacağından yetkilendirme için bir saldırganın edinmesi gereken kaynak arttırılmış olur.

## İkinci faktör

İkinci faktör olarak tercih edeceğiniz sistem tamamen kullanım ve güvenlik ihtiyaçlarınıza bağlıdır. Kimi sistemler var olan donanımlarınızı (akıllı telefon, parmak) kullanabilirken 

[Google-Authenticator ile yetkilendirme](cihaz_guvenligi/ga_pam.md)

[Yubikey ile yetkilendirme](cihaz_guvenligi/yubikey_pam.md)

[Parmakizi ile yetkilendirme](cihaz_guvenligi/parmak_pam.md)

[Bu bölüme katkı verebilirsiniz](https://git.oyd.org.tr/oyd/guvenlik)
