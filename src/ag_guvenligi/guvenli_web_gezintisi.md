# Güvenli Web Gezintisi

<!-- toc -->

## Web tarayıcınızı seçin

Her gün, muhtemelen en sık kullandığınız yazılım web tarayıcınızdır. Bu sebepten dolayı, web tarayıcınızın güvenli ve özgür olması çok kritiktir. Mozilla Firefox kullanın!

[Firefox'u buraya tıklayarak indirebilirsiniz.](https://getfirefox.com)

## Firefox'ta ayarlarınızı yapın

### Üçüncü taraf çerezleri devre dışı bırakın

Üçüncü parti çerezler, siz İnternet'te gezinirken davranışlarınızı izlemek için reklam ağları tarafından kullanılan tanımlayıcılardır.

1. Sandviç menüden Tercihler'e girin. Gizlilik ayarlarını yapmak için Gizlilik ve Güvenlik'e tıklayın. Gelişmiş izleme koruması başlığı altındaki Üçüncü sırada olan "Özel" seçeneğini seçin.

2.En yüksek düzeyde güvenlik için sırasıyla Çerezler, Takip amaçlı içerikler, Kripto madencileri, Parmak izi toplayıcılar seçeneklerinin hepsini işaretleyerek engellenmelerini sağlayın.

3. Çerezler'in yanındaki menüden "Tüm üçüncü taraf çerezleri"ni seçin. Hemen altındaki menüden "Tüm pencerelerde" seçeneğini seçin.

![alt-text](guvenli_web_gezintisi/firefox.png)

4. Aşağı inince göreceğiniz "Web sitelerine Do Not Track (İzlemeyin) sinyali gönder" ibaresinin altında "Her zaman" seçeneğini tıklayın.

![alt-text](guvenli_web_gezintisi/firefox1.png)

5. Çerezler ve site verilerinin altında "Firefox kapatıldığında çerezleri ve site verilerini sil" seçeneğini işaretleyin.

6. Gezinme geçmişinizin temizlendiğinden emin olmak için; Geçmiş ayarlarının olduğu yerdeki menüden "Firefox geçmiş için özel ayarlar kullansın" seçeneğini işaretleyin. Altındaki kutucuklardan "Firefox kapatılınca geçmişi temizle"yi tıklayın.

![alt-text](guvenli_web_gezintisi/firefox2.png)

7. İzinler başlığının altında "Açılır pencereleri engelle" ve "Siteler eklenti yüklemeye çalıştığında beni uyar" seçeneklerini seçin.

![alt-text](guvenli_web_gezintisi/firefox3.png)

8. Firefox veri toplama ve kullanma izinleri başlığının altındaki hiçbir kutucuğu işaretlememenizi öneririz.

9. Aldatıcı içerik ve tehlikeli yazılım koruması başlığının altındaki kutucukların hepsini işaretleyin.

10. Sertifikalar başlığının altında "Her seferinde bana sor" ve "Sertifikaların geçerliliğini doğrulamak için OCSP otomatik yanıt sunucularını sorgula" seçeneklerini işaretleyin.

![alt-text](guvenli_web_gezintisi/firefox4.png)

### Varsayılan arama motorunuzu değiştirin

Yine tercihlerden "Arama" kısmına gelin. Varsayılan arama motoru olarak [duckduckgo.com](https://duckduckgo.com)'u seçin. Riseup arama motoru olarak DuckDuckGo'yu öneriyor. [Masaüstü](https://duck.co/help/desktop/adding-duckduckgo-to-your-browser) veya [mobil](https://duck.co/help/mobile) tarayıcılar için kurulum talimatlarını inceleyin.

## Tarayıcı eklentileri

Eklentiler aksi belirtilmedikçe Firefox ve Chrome (mülk yazılım!) ile uyumludur.

### Başlıca eklentiler

Aşağıdaki eklentiler, herkesin sürekli olarak kullanmasını önerdiğimiz başlıca eklentilerdir. Stabil ve açık kaynak olan bu eklentiler, web sitelerinin bozulmasına çok nadir sebep olurlar.


|||
|---|---|
|![uBlock Origin](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/icon38%402x.png)|[uBlock Origin](https://github.com/gorhill/uBlock) ([Chrome](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm), [Firefox](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)) reklam ve takipçi ağların çoğunu engeller. Adblock Plus veya Disconnect'e benzerdir ama daha iyi ve daha hızlı çalışır.|
|![HTTPS Everywhere](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/HTTPS_Everywhere_icon.svg/60px-HTTPS_Everywhere_icon.svg.png)|[HTTPS Everywhere](https://www.eff.org/https-everywhere), destekleyen web sitelerinde otomatik olarak güvenli TLS bağlantılarına geçiş yapar. Gezinti içeriğinizin gözetilmesine karşı korunmanıza yardımcı olur. Hangi siteleri ziyaret ettiğinizi gizlemez (ayriyeten [Tor](tor.md) veya VPN kullanmıyorsanız).|
|![Privacy Badger](https://upload.wikimedia.org/wikipedia/commons/thumb/1/13/PrivacyBadgerLogo.svg/125px-PrivacyBadgerLogo.svg.png)|[Privacy Badger](https://www.eff.org/privacybadger) sizi izleme eğiliminde olan takipçileri dinamik olarak tespit eder ve engeller. Privacy Badger reklam engelleyici olmadığı için uBlock alternatifi değildir, ancak uBlock'un varsayılan modda sahip olmadığı güvenlik özelliklerine sahiptir.|

Kullanım notları;

- IP adres sızıntıları; Tüm tarayıcılar sesli ve görüntülü konferanslar sırasında gerçek IP adresinizi sızdırır. Eğer VPN veya Tor ile birlikte sesli veya görüntülü konuşma gerçekleştiriyorsanız, uBlock ayarlarında WebRTC IP sızıntılarını engelleyen ayarı aktif etmelisiniz.
- uBlock gelişmiş mod; Eğer uBlock'u [gelişmiş modda](https://github.com/gorhill/uBlock/wiki/Advanced-user-features) kullanıyorsanız, ayriyeten Privacy Badger kullanmanız gerek yoktur.

### Gelişmiş Eklentiler

Bu eklentiler kullanımları zor olduğundan veya web sitelerinde bozulmalara yol açabileceğinden için ileri düzey kullanıcılar içindir.

Bu eklentiler web tarayıcılarının çalışma şekillerinden kaynaklanan temel mahremiyet kusurlarının üzerinden gelmeye çalışır. Ancak, pek çok web sitesi basit işlevler için bu kusurlardan faydalanır, bu yüzden bu kusurları gidermek zaman zaman web sitelerinin çalışmamasına sebep olabilir.

Bahsedilen kusurların bazıları şunlardır;

* __HTTP Referrer:__ Bir linke tıkladığınızda, tarayıcınız bulunduğunuz sitenin konumunu yeni siteye gönderir. Hassas ve kişiyi tanımlayan bilgiler site URLinde bulunabileceğinden, HTTP Referer kapatılmalıdır. Bunu sadece bir eklenti kullanarak gerçekleştirebilirsiniz.
* __HTTP User-Agent:__ Tarayıcınız ziyaret ettiğiniz her web sitesine, tarayıcınıza özel bir "User-Agent" bilgisi gönderir. Bu bilgi çevrimiçi etkinliğinizi belirlemek için diğer veriler ile birlikte kullanılabilecek pek çok benzersiz veri içerir. Tor Tarayıcı'da kullanılanlar gibi daha genel bir değer kullanmak daha iyidir.
* __HTML5 Canvas:__ Pek çok site tarayıcınızın benzersiz bir parmakizini almak ve sizi izlemek için HTML5 Canvas kullanmaya başladı. Şu anda bu özelliği devre dışı bırakmak için bir yol olmasa da, bazı eklentiler ile önüne geçilebilir.
* __JavaScript:__ JavaScript günümüzde pek çok web sitesi için temel bir bağımlılıktır, ama zaman zaman devre dışı bırakmak isteyebilirsiniz. JavaScript aktifken, web sitelerinin tarayıcı parmakizinizi oluşturması ve sizi izlemesi çok daha kolaydır. Ayrıca tarayıcı güvenlik kusurlarının pek çoğu JavaScript kaynaklıdır.

Firefox için:

* [µMatrix](https://addons.mozilla.org/en-US/firefox/addon/umatrix/) seçici olarak JavaScript'i, eklentileri veya diğer kaynakları engellemenize ve üçüncü-taraf kaynakları kontrol etmenizi sağlar. Bunun yanında mahremiyetinizi korumak için user-agent maskeleme, referer engelleme gibi ek özellikler sunar. NoScript ve RequestPolicy yerine kullanılabilir.
* [Canvas Blocker](https://addons.mozilla.org/en-US/firefox/addon/canvasblocker/) HTML5 canvas desteğini belirli siteler için devre dışı bırakmanızı sağlar.

Chrome için:

* [µMatrix](https://chrome.google.com/webstore/detail/%C2%B5matrix/ogfcmafjalglgifnmanfmnieipoejdcf) seçici olarak JavaScript'i, eklentileri veya diğer kaynakları engellemenize ve üçüncü-taraf kaynakları kontrol etmenizi sağlar. Bunun yanında mahremiyetinizi korumak için user-agent maskeleme, referer engelleme gibi ek özellikler sunar. NoScript ve RequestPolicy yerine kullanılabilir.
* [CanvasFingerPrintBlock](https://chrome.google.com/webstore/detail/canvasfingerprintblock/ipmjngkmngdcdpmgmiebdmfbkcecdndc) HTML5 canvas desteğini belirli siteler için devre dışı bırakmanızı sağlar (eklenti kaynak kodu kapalıdır).

### Zararlı veya önerilmeyen eklentiler

Popüler olmalarına rağmen, bu eklentileri kullanmaktan kaçınmanızı öneriyoruz.

* [Adblock Plus](https://adblockplus.org/) reklam ve takipçileri engellemek için en iyi eklentilerden biriydi. Ancak, şu an reklamverenlerin kendi filtrelerini atlamaları için bir rüşvet programı yürütüyorlar. Ayrıca, uBlock kullandığı teknoloji açısından daha iyidir.
* [Disconnect](https://disconnect.me/disconnect) uBlock gibi çalışır ve kaynağı açıktır. uBlock kullanıyorsanız, uBlock'ta olmayan bazı görselleştirmeler sunmasına rağmen Disconnect gereksizdir.
* [Ghostery](https://www.ghostery.com) uBlock gibi çalışır, ancak varsayılan olarak pek çok takipçiye izin verir ve kaynak kodu özel mülktür.

## Firefox'un Ayarlarını Güçlendirmek

Firefox ne yazık ki tam anlamı ile kullanıcı güvenliğini ve mahremiyetini koruyacak ayarlarla gelmemekte. [Mozilla Vakfı](https://foundation.mozilla.org/en/) genellikle kullanıcıların kolaylık beklentileri ile en yüksek güvenlik ve mahremiyet standartları arasında  bir ortayol arama çabasında bulunmakta. Bu ortayol çabasını kendi güvenliğiniz lehine çevirmek için Firefox'un kimi gizli ayarlarını düzeltmeniz gerekli. Bunun için sırası ile aşağıdaki işlemleri uygulayabilirsiniz:

Öncelikle Firefox'u çalıştırıp adres çubuğuna aşağıdaki satırı yazıp giriş yapın:

`about:config`

Sizi satırlar dolusu bir tablo ve bir arama çubuğu karşılayacak. Aşağıdaki ayarlardan düzenlemek istediklerinizi arama çubuğuna yazıp belirtilen değişikliği yapabilisiniz.


[WebRTC](https://en.wikipedia.org/wiki/WebRTC) günümüzde Jitsi gibi pek çok tarayıcı üzerinden çalışan yazılımın kullandığı bir teknoloji. Lakin aynı zamanda tasarım itibari ile tarayıcınızın cihazınıza ait gerçek IP adresini sızdırmasına da sebep olmakta. Bu sebeple özellikle VPN ve TOR kullandığınız bir kurulumda WebRTC'nin devre dışı bırakılması önem arzediyor. Kimi web yazılımlarını bu sebepten dolayı çalışmayabilir.

`media.peerconnection.enabled`

Bu satıra çift tıklayarak `false` yazmasını sağlayın

[Fingerprint veya parmakizi](https://en.wikipedia.org/wiki/Device_fingerprint#Browser_fingerprint) tarayıcıların cihaza özel yapılandırmalardan kullanıcıları takip etmeye yarayan bir yöntem. Firefox bunu varsayılan olarak engellemek üzerine ayarlı. Lakin yine de kontrol etmek isteyebilirsini.

`privacy.resistfingerprinting` "true" olmalıdır.

Firefox'un doldurduğunuz formların içeriklerini hatırlayıp kaydetmesini mahremiyetiniz için tercih etmeyebilirsiniz. Keza bu bilgiler cihazınızda duracağından sizin için bir risk oluşturabilir. Bu özelliği kapatmak için aşağıdaki ayarı değiştirebilirsiniz.

`browser.formfill.enable` "false" olmalıdır.

Web'de gezindiğiniz sayfaların cihazınızın konumuna erişmesi sizin için bir mahremiyet riski olabilir. Firefox'un bu talepleri kendiliğinden berteraf etmesi için aşağıdaki ayarı değiştirebilirsiniz.

`geo.enabled` "false" olmalıdır.

Telemetri tarayıcınızın kimi eylemlerini bildirmesine sebep olabilir. Bu girdiğiniz sitelerin sizin hakkınızda bilgi edinmesine ve sizi takip etmelerini sağlayabilir. Bu telemetrileri kapatmanız tavsiye edilir. Aşağıdaki satırları bulup "false" olarak işaretleyebilirsiniz.

```
toolkit.telemetry.archive.enabled
toolkit.telemetry.bhrping.enabled
toolkit.telemetry.firstshutdownping.enabled
toolkit.telemetry.newprofileping.enabled
toolkit.telemetry.unified
toolkit.telemetry.updateping.enabled
toolkit.telemetry.shutdownpingsender.enabled
toolkit.telemetry.shutdownpingsender.enabledFirstSession
toolkit.telemetry.pioneer-new-studies-available
```
Firefox tarama deneyiminizi iyileştirmek için çeşitli içerikleri siz açıkça talep etmeseniz de yüklemeye çalışabilir veya tarama geçmişinizi girdiğiniz sitelere iletebilir. Bu hareketlerinizi ifşa ettiğinden mahremiyetiniz için bir sakınca oluşturabilir. Bu ayarları değiştirerek Firefox'un sadece talep ettiğiniz içeriklere erişmesini sağlayabilirsiniz.

`network.dns.disableprefetch` "true" olmalıdır.

`network.prefetch-next` "false" olmalıdır.

`dom.webnotifications.enabled` "false olmalıdır.

`network.http.sendRefererHeader` "0" olmalıdır.

`security.ssl.disable_session_identifiers` arama çubuğuna yazdıktan sonra "bolean" seçeneğini seçip + simgesine tıklayın ve değerin "true" olduğunu kontrol edin.

İnternetin ve Web'in temel şifreleme teknolojisi olan [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security) pek çok geçmişten kalan ve artık güvenli sayılmayan bağlantı standardını hala yaşatmaktadır. Eski sistemlerin desteklenmesi için süren bu uygulama sizin için bir güvenlik riski teşkil edebilir. Bu ayarları değiştirdiğinizde pek çok büyük şirketin ve kimi devlet kurumlarının sitelerinin çalışmaması sonucu ile karşılaşabilirsiniz. Güvenli bağlantı kurmayan bu sitelere erişmek için bu ayarları geçici olarak kaldırmanız gerekebilir.

`security.ssl3.rsa_des_ede3_sha` "false" olmalıdır.

`security.ssl.require_safe_negotiation` "true olmalıdır.

`security.tls.version.min` "3" değerinde olmalıdır.

`security.tls.enable_0rtt_data` "false" olmalıdır. Bu değer ile her şifreli bağlantı ile yeni bir anahtar oluşturulur.

[WebGL](https://en.wikipedia.org/wiki/WebGL) Web yazılımlarının cihazınızın grafik işlemcisine erişebilmesini sağlayan bir teknoloji. Bu çeşitli güvenlik sorunlarını da birlikte getirdiğinden bu ayarı kapatmanız güvenliğinizi arttırabilir.

`webgl.disabled` "true" olmalıdır.

Tarayıcınızın bilgisayarınızın batarya durumunu ziyaret ettiğiniz web sitelerine iletmesinin bir anlamı var mı gerçekten?

` dom.battery.enabled` "false" olmalıdır.
