## Shadowsocks nedir?

[Shadowsocks](https://en.wikipedia.org/wiki/Shadowsocks), socks5 protokolünü temel alan bir proxy uygulamasıdır. 2012’de [Çin Halk Cumhuriyeti’nin ünlü güvenlik duvarını](https://en.wikipedia.org/wiki/Great_Firewall) aşabilmek için [Python dilinde](https://www.python.org/) geliştirilmiştir. İlerleyen zamanlarda farklı dil ve platformlarda sunucu ve istemcileri de yazılmıştır. En popülerleri; shadowsocks-rust, shadowsocks-libev ve go-shadowsocks2 yazılımlarıdır. GNU/Linux, BSD türevleri ile MacOS ve Windows işletim sistemleri için Qt5 grafik arayüz içeren [shadowsocks-qt5](https://github.com/shadowsocks/shadowsocks-qt5/releases) adında bir istemcisi vardır. Ayrıca Android, iOS ve Windows için özel yazılmış istemcileri de bulunmaktadır. Orjinal python sunucu/istemcisi PIP paket yöneticisi ile kurulabilmektedir. 

Shadowsocks, akan veriyi şifrelemek için [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) ve [ChaCha](https://www.cryptopp.com/wiki/ChaCha20) algoritmalarını kullanmaktadır. Ayrıca bu algoritmaların üzerine [AEAD(Authenticated Encryption with Associated Data)](https://en.wikipedia.org/wiki/Authenticated_encryption) yani "İlişkili Verilerle Kimlik Doğrulamalı Şifreleme" yapmaktadır. Bu sayede veri hem şifreli hem de doğrulanmış şekilde iletilmektedir. 

Shadowsocks’u diğer proxy yöntemlerinden ayrıştıran bir nokta da TCP’nin yanında UDP trafiğini de taşıyabilmesidir. Ek olarak bir eklenti sistemi de bulunmaktadır ve [v2ray](https://github.com/v2ray/v2ray-core) bu eklentilerden en popüleridir. v2ray'ın kullanım amacı akan verinin şeklini gizlemektir. Bu eklenti sayesinde akan trafik HTTP, HTTPS veya QUIC protokolleri gibi bir ağda doğal olarak beklenen trafiği taklit edebilir.


## Basit bir sunucu istemci kurulumu


### Sunucu tarafında

Tercihinize bağlı olarak sunucunuzda bir shadowsocks yazılımını seçip çalıştırmanız gerekmektedir. Bu rehber shadowsocks-rust kurulumunu takip edecektir fakat json ayar dosyası neredeys tüm istemciler için benzer olacaktır.

[github/shadowsocks-rust](https://github.com/shadowsocks/shadowsocks-rust/releases/) adresinden en güncel yayınlanmış sürümü seçip detaylarına göz gezdirin. Bu rehberin yazıldığı tarihteki en güncel sürüm v1.8.12'dir. Platformunuza göre yayınlanan bir kurulum dosyasını seçmeniz gerekmekte. Rehber GNU/Linux üzerinden ilerleyeceği için Gnu/Linux dağıtımları için derlenmiş olan dosya kullanılacaktır. 

Karşınıza iki seçenek çıkacaktır: Glibc ve MUSL. Tercihimiz Glibc olacak lakin bir **GNU/Linux değil Busybox/Linux dağıtımı** kullanıyorsanız **MUSL** için derlenmiş halini seçmeniz gerekecektir.

"shadowsocks-v1.8.12.x86_64-unknown-linux-gnu.tar.xz" dosyasını indirdikten sonra sunucuda dosyayı açıp içindeki dört çalıştırılabilir dosyayı, komut dizinlerinden birine koyun. /usr/local/sbin/ dizinini tercih edilebilir çünkü bu dizinin amacı root yetkisi ile çalıştırılacak ama paket yöneticisi vasıtasıyla kurulmamış uygulamaları barındırmaktır.

Daha sonrasında /etc/ dizini altında shadowsocks-config.json adında bir dosya oluşturup içine aşağıdakileri yazın;

```json
{
"server":"<sunucunuzun ip adresi>",
"server_port": 8388,
"password":"<güvenli bir parola>",
"timeout":300,
"method":"aes-256-gcm"
}
```

- *server* kalemi shadowsocks’un dinleyeceği, sunucunuzun IP adresini seçmenizi sağlar. Tek ağ kontrolcüsü olan cihazlarda tek bir IP olacağından işiniz kolay olacaktır. Eğer birden fazla ağ kontrolcünüz varsa hangisinde çalışmasını istediğinize siz karar vermelisiniz, yahut 0.0.0.0 yazarak bütün ip adreslerinizi dinlemesini sağlayabilirsiniz.

- _server_port_ kalemi yazılımın kullanacağı IP adreslerinde dinlemesini istediğiniz portu belirttiğiniz yerdir, standart 8388 kullanılır. Örnek sunucumuzda önceki bölümde bahsedilen v2ray pluginini kullanıldığından 443 HTTPS portunu kullanılmakta. Böylece trafik HTTPS portuna akmak ile veri HTTPS trafiği gibi gözükmekte, dolayısıyla [DPI (derin paket incelemesi)](https://en.wikipedia.org/wiki/Deep_packet_inspection) yapan güvenlik duvarları tarafından shadowsocks takip edilememektedir.

- _password_ parolanızı belirttiğiniz yer, basit bir şekilde çalıştığından ötürü güvenli bir parola kullanmanız şart. Bunun için [Zarola](https://zarola.oyd.org.tr) kullanmanızı hararetle öneririz.

- _timeout_ bağlantı zaman aşımının belirlendiği ayar kalemi, 300 saniye makul bir süre.

- _method_ şifreleme algoritmanız bu bölümde belirlenir, tercihimiz aes-256-gcm. Bu algoritma [256 bitlik bir anahtar kullanarak simetrik](https://en.wikipedia.org/wiki/Symmetric-key_algorithm) blok şifreleme yapan bir algoritma. Genel ihtiyaçlara yetecek kadar hızlı ve şu an desteklenen en güçlü algoritma.

Bu dosyayı kaydettikten sonra servis yöneticinize bir servis yazmanız gerekmekte. Bu kısım tercihinize kalmış, lakin örnek sunucumuz systemd kullandığından systemd için basit bir servisi aşağıdaki gibi yazabilirsiniz:

```
[Unit]
After=network.target
[Service]
Type=simple
User=nobody
Group=nobody
ExecStart=/usr/local/sbin/ssserver -c /etc/shadowsocks-config.json
[Install]
WantedBy=multi-user.target
```

Daha sonrasında bu servisi aktif hale getirip başlangıçta çalışacak şekilde ayarlanması gerekiyor. Ardından shadowsocks sunucunuz hizmet vermeye hazır olacak.

[systemd'de bu servisin aktif hale getirilmesini anlatarak katkıda bulunabilirsiniz](https:/git.oyd.org.tr)


### İstemci Tarafında

Teknik olarak sunucu tarafındaki ayarların aynısı istemci için de geçerli fakat ayar dosyasınun şu şekilde değiştirilmesi gerekli:

```json
{
"server":"<sunucunuzun ip adresi>",
"server_port": 8388,
"local_address":"<istemcinizin ip adresi>",
"local_port": 1080,
"password":"<güvenli bir parola>",
"timeout":300,
"method":"aes-256-gcm"
}
```

- _local_address_ kalemi istemciniz üzerinde, sslocal'ın (shadowsocks istemcinizin) dinleyecegi, programlarinizi yönlendireceginiz yerel adresin seçildiği yer.

- _local_port_ kalemi, istemci olarak kullandığınız bilgisayarda, localhost’ta hangi port üzerinden socks5 yayını yapacağınının seçildiği yer. Bazı istemciler bu ayarı kullanmamakta (android istemcisi, android’in kendi VPN altyapısını kullandığından yerel bir socks5 bağlantısı yerine tüm trafiği yönetebilmekte) lakin shadowsocks-rust istemcisi ve diğer bir çok istemci bu ayarı kullanıyor.

Son olarak da systemd servis dosyamı şu şekilde düzenleyin:

```
[Unit]
After=network.target
[Service]
Type=simple
User=nobody
Group=nobody
ExecStart=/usr/local/sbin/sslocal -c /etc/shadowsocks-config.json
[Install]
WantedBy=multi-user.target
```

Ve hepsi bu kadar! Artık socks5 destekleyen yazılımlarınızı shadowsocks proxy’si üzerinden internete, farklı bir noktadan çıkartabilirsiniz. Örnek olarak Firefox, Thunderbird ve Telegram uygulamaları üzerinde bu proxy’i kullanabilirsiniz. 

Eğer bütün trafiğinizi shadowsocks üzerinden yönlendirmek isterseniz iptables ve redsocks uygulamaları ile bunu sağlayabilirsiniz.

[iptables ve redsocks ile yönlendirme yapılmasını anlatarak bu rehbere katkı verebilirsiniz.](https://git.oyd.org.tr)

Android temelli cihazlar üzerinde de shadowsocks kullanılabilir. Android VPN ayarlarından "Sürekli VPN modu" etkinleştirilerek bağlantının sürekliliği sağlanabilir.Bu sayede cihazdan geçen bütün trafik sunucunuz üzerinden internete çıkar, güvenli olmayan ağlarda iletişiminiz takip edilemez ve bütün trafik tek bir IP adresine doğru gözükür.

Shadowsocks belki Çin Halk Cumhuriyeti devleti tarafından erişimi engellenmeye çalışılan, önlem geliştirilen ve kısıtlanan bir yazılım olabilir ancak aktif geliştirici kitlesi, eklentileri ve genel basitliği ile sadece Çin vatandaşları tarafından değil aynı zamanda diğer bütün dünya vatandaşları tarafından da tercih edilesi bir noktaya gelmiştir.

Güncelliğini farklı dil ve platformlarda koruyan ciddi bir geliştirici kitlesi bulunmakta ve aktif kullanıcı sayısı ile güçlü bir proxy yazılımı olan Shadowsocks kitlesel gözetime karşı etkili bir araçtır.
