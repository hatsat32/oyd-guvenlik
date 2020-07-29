## Shadowsocks nedir?

Shadowsocks socks5 protokolünü temel alan bir proxy uygulamasıdır. 2012’de Çin Halk Cumhuriyeti’nin ünlü güvenlik duvarını aşabilmek için Python dilinde geliştirilmiştir. İlerleyen zamanlarda farklı dil ve platformlarda da sunucu ve istemcileri yazılmıştır, en popülerleri shadowsocks-rust, shadowsocks-libev ve go-shadowsocks2 yazılımlarıdır. Linux, BSD türevleri, MacOS, ve Windows işletim sistemleri için Qt5 temelli bir istemcisi vardır (shadowsocks-qt5), ayrıca Android, iOS ve Windows için özel yazılmış istemcileri de bulunmaktadır. Hâlâ orjinal python sunucu/istemcisi pip paket yöneticisi ile kurulabilmektedir. Akan veriyi şifrelemek için AES ve ChaCha algoritmalarını kullanmaktadır, ayrıca bu algoritmaların üzerine AEAD yani İlişkili Verilerle Kimlik Doğrulamalı Şifreleme yapmaktadır. Bu sayede veri hem şifreli hem de kimliği doğrulanmış şekilde taşınmaktadır. Shadowsocks’u diğer proxy yöntemlerinden ayrıştıran bir nokta da TCP’nin yanında UDP trafiğini de taşıyabilmesidir. Ek olarak standart bir eklenti sistemi de bulunmaktadır ve v2ray en popüler eklentilerden biridir, kullanım amacı akan verinin şeklini gizlemektir, bu plugin sayesinde akan trafik HTTP, HTTPS veya QUIC protokollerini taklit edebilir.

## Basit bir sunucu istemci kurulumu

### Sunucu tarafında

Tercihinize bağlı bir sunucu yazılımı seçip çalıştırabilmeniz gerekmektedir. Ben shadowsocks-rust sunucusunu kullanmayı tercih edeceğim ama ayar json dosyası neredeyse bütün istemciler için aynı olacaktır.

[github/shadowsocks-rust](https://github.com/shadowsocks/shadowsocks-rust/releases/) adresinden en güncel yayınlanmış sürümü seçip detaylarına bakıyorum. Bu belge yazılırkenki en güncel sürüm v1.8.12 olarak yayınlanmıştı. Platformunuza göre yayınlanan bir dosyayı seçmeniz gerekmekte, ben Gnu/Linux dağıtımları için derlenmiş olan halini indireceğim. Önümde iki seçenek var, Glibc ve MUSL. Ben Glibc için derlenmiş pakedi seçeceğim, eğer bir Gnu/Linux değil Busybox/Linux dağıtımı kullanıyorsanız MUSL için derlenmiş halini seçmeniz gerekecektir.

shadowsocks-v1.8.12.x86_64-unknown-linux-gnu.tar.xz dosyasını indirdikten sonra evimdeki sunucumda açıyorum ve içindeki dört çalıştırılabilir dosyayı, komut dizinlerimden birine koyuyorum. Ben /usr/local/sbin/ dizinini tercih ediyorum çünkü bu dizinin amacı root yetkisi ile çalıştırılacak ama paket yöneticisi vasıtasıyla kurulmamış uygulamaları barındırmaktır.

Daha sonrasında /etc/ dizini altında shadowsocks-config.json adında bir dosya oluşturup içine şunları yazıyorum.

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

- _server_port_ kalemi yazılımın kullanacağı IP adreslerinde dinlemesini istediğiniz portu belirttiğiniz yerdir, standart 8388 kullanılır. Ben kendi sunucumda daha önce bahsettiğim v2ray pluginini kullandığımdan 443 HTTPS portunu kullanmaktayım. Böylece trafik HTTPS portuna akmakta, veri HTTPS trafiği gibi gözükmekte, dolayısıyla DPI (derin paket incelemesi) yapan güvenlik duvarları tarafından shadowsocks takip edilememektedir.

- _password_ parolanızı belirttiğiniz yer, basit bir şekilde çalıştığından ötürü güvenli bir parola kullanmanız şart.

- _timeout_ bağlantı zaman aşımını belirttiğiniz ayar kalemi, 300 saniye makul bir süre.

- _method_ şifreleme algoritmanızı seçtiğiniz yer, ben aes-256-gcm kullanıyorum, bu algoritma 256bitlik bir anahtar kullanarak simetrik blok şifreleme yapan bir algoritma ve ihtiyacımı karşılayacak kadar hızlı ve şu an desteklenen en güçlü algoritma.

Bu dosyayı kaydettikten sonra servis yöneticinize bir servis yazmanız gerekmekte. Bu kısmı sizin tercihinize bırakıyorum, lakin ben systemd kullandığımdan basit bir servis yazdım.

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

Daha sonrasında bu servisi aktif hale getirip başlangıçta çalışacak şekilde ayarladım. Ve sunucum çalışır durumda.

### İstemci Tarafında

Aslında sunucu tarafındaki ayarların aynısını yaptım, neredeyse her şey aynı, lakin ayar dosyamı şu şekilde değiştirdim.

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

- _local_address_ kalemi istemciniz üzerinde, sslocal'ın (shadowsocks istemcinizin) dinleyecegi, programlarinizi yönlendireceginiz yerel adresi seçtiginiz yer.
- _local_port_ kalemi, istemci olarak kullandığınız bilgisayarda, localhost’ta hangi port üzerinden socks5 yayını yapacağını seçtiğimiz yer. Bazı istemciler bu ayarı kullanmamakta (android istemcisi mesela android’in kendi VPN altyapısını kullandığından yerel bir socks5 bağlantısı yerine tüm trafiği yönetebilmekte) lakin shadowsocks-rust istemcisi ve diğer bir çok istemci bu ayarı kullanıyor.

Son olarak da systemd servis dosyamı şu şekilde güncelledim.

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

Ve bu kadar! Artık socks5 destekleyen yazılımlarınızı shadowsocks proxy’si üzerinden internete, farklı bir noktadan çıkartabilirsiniz. Ben kendi bilgisayarımda Firefox, Thunderbird ve Telegram uygulamaları üzerinde bu proxy’i kullanmaktayım. Eğer bütün trafiğinizi shadowsocks üzerinden yönlendirmek istiyorsanız iptables ve redsocks uygulamaları ile bunu sağlayabilirsiniz. Android temelli telefonum üzerinde de shadowsocks kullanmaktayım ve sürekli VPN modu aktif şekilde ayarladım, bu sayede telefonumdan geçen bütün trafik kendi sunucum üzerinden internete çıkmakta, tanımadığım ağlara bağlandığımda iletişimim takip edilememekte ve bütün trafiğim tek bir IP adresine doğru gidiyor gözükmekte.

Shadowsocks belki Çin Halk Cumhuriyeti devleti tarafından erişimi engellenmeye çalışılan, önlem geliştirilen ve kısıtlanan bir yazılım ve protokol olabilir, ancak aktif geliştirici kitlesi, eklentileri ve genel basitliği ile sadece Çin vatandaşları tarafından değil aynı zamanda diğer bütün dünya vatandaşları tarafından da tercih edilesi bir noktaya gelmiştir. Güncelliğini farklı dil ve platformlarda koruyan ciddi bir geliştirici kitlesi ve aktif kullanıcı kitlesi ile güçlü bir proxy yazılımı olan Shadowsocks umarım sizin de ilginizi çekmiştir.
