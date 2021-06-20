## Shadowsocks nedir?

[Shadowsocks](https://en.wikipedia.org/wiki/Shadowsocks), socks5 protokolünü temel alan bir proxy uygulamasıdır. 2012’de [Çin Halk Cumhuriyeti’nin ünlü güvenlik duvarını](https://en.wikipedia.org/wiki/Great_Firewall) aşabilmek için [Python dilinde](https://www.python.org/) geliştirilmiştir. İlerleyen zamanlarda farklı dil ve platformlarda sunucu ve istemcileri de yazılmıştır. En popülerleri; shadowsocks-rust, shadowsocks-libev ve go-shadowsocks2 yazılımlarıdır. GNU/Linux, BSD türevleri ile MacOS ve Windows işletim sistemleri için Qt5 grafik arayüz içeren [shadowsocks-qt5](https://github.com/shadowsocks/shadowsocks-qt5/releases) adında bir istemcisi vardır. Ayrıca Android, iOS ve Windows için özel yazılmış istemcileri de bulunmaktadır. Orjinal python sunucu/istemcisi PIP paket yöneticisi ile kurulabilmektedir. 

Shadowsocks, akan veriyi şifrelemek için [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) ve [ChaCha](https://www.cryptopp.com/wiki/ChaCha20) veya [GCM](https://en.wikipedia.org/wiki/Galois/Counter_Mode) algoritmalarını kullanmaktadır. Ayrıca bu algoritmaların üzerine [AEAD(Authenticated Encryption with Associated Data)](https://en.wikipedia.org/wiki/Authenticated_encryption) yani "İlişkili Verilerle Kimlik Doğrulamalı Şifreleme" yapmaktadır. Bu sayede veri hem şifreli hem de doğrulanmış şekilde iletilmektedir. 

Shadowsocks’u diğer proxy yöntemlerinden ayrıştıran bir nokta da TCP’nin yanında UDP trafiğini de taşıyabilmesidir. Ek olarak bir eklenti sistemi de bulunmaktadır ve [v2ray](https://github.com/v2ray/v2ray-core) bu eklentilerden en popüleridir. v2ray'ın kullanım amacı akan verinin şeklini gizlemektir. Bu eklenti sayesinde akan trafik HTTP, HTTPS veya QUIC protokolleri gibi bir ağda doğal olarak beklenen trafiği taklit edebilir.

<!-- toc -->

## Temel shadowsocks kurulumu


### Sunucu kurulumu

Tercihinize bağlı olarak sunucunuzda bir shadowsocks yazılımını seçip çalıştırmanız gerekmektedir. Bu rehber shadowsocks-rust kurulumunu takip edecektir fakat json ayar dosyası neredeyse tüm istemciler için benzer olacaktır.

[github/shadowsocks/shadowsocks-rust](https://github.com/shadowsocks/shadowsocks-rust/releases/) adresinden en güncel yayınlanmış sürümü seçip detaylarına göz gezdirin. Bu rehberin yazıldığı tarihteki en güncel sürüm v1.11.0'dır. Platformunuza göre yayınlanan bir kurulum dosyasını seçmeniz gerekmektedir. Rehber GNU/Linux üzerinden ilerleyeceği için Gnu/Linux dağıtımları için derlenmiş olan dosya kullanılacaktır.

Karşınıza iki seçenek çıkacaktır: Glibc ve MUSL. Tercihimiz Glibc olacak lakin bir **GNU/Linux değil Busybox/Linux dağıtımı** kullanıyorsanız **MUSL** için derlenmiş halini seçmeniz gerekecektir.

"shadowsocks-v1.11.0.x86_64-unknown-linux-gnu.tar.xz" dosyasını indirdikten sonra sunucuda dosyayı açıp içindeki dört çalıştırılabilir dosyayı, komut dizinlerinden birine koyun. /usr/local/sbin/ dizinini tercih edilebilir çünkü bu dizinin amacı root yetkisi ile çalıştırılacak, paket yöneticisi vasıtasıyla kurulmamış uygulamaları barındırmaktır.

*shadowsocks*ı debian, archlinux ve fedora depolarından, sırasıyla; `apt install shadowsocks`, `pacman -S shadowsocks` ve `dnf install python3-shadowsocks` komutlarıyla da sisteminize kurabilirsiniz.

Daha sonrasında /etc/ dizini altında shadowsocks-config.json adında bir dosya oluşturup içine aşağıdakileri yazın;

```json
{
"server":"<sunucu ip adresi>",
"server_port":443,
"password":"<güvenli bir parola>",
"method":"aes-256-gcm",
"timeout":300
}
```

- *server* kalemi shadowsocks’un dinleyeceği, sunucunuzun IP adresini seçmenizi sağlar. Tek ağ kontrolcüsü olan cihazlarda tek bir IP olacağından işiniz kolay olacaktır. Eğer birden fazla ağ kontrolcünüz varsa hangisinde çalışmasını istediğinize siz karar vermelisiniz, yahut 0.0.0.0 yazarak bütün ip adreslerinizi dinlemesini sağlayabilirsiniz.

- *server_port* kalemi yazılımın kullanacağı IP adreslerinde dinlemesini istediğiniz portu belirttiğiniz yerdir, standart 8388 kullanılır. Örnek sunucumuzda önceki bölümde bahsedilen v2ray pluginini kullanıldığından 443 HTTPS portunu kullanılmakta. Böylece trafik HTTPS portuna akmak ile veri HTTPS trafiği gibi gözükmekte, dolayısıyla [DPI (derin paket incelemesi)](https://en.wikipedia.org/wiki/Deep_packet_inspection) yapan güvenlik duvarları tarafından shadowsocks tespit edilememektedir.

- *password* parolanızı belirttiğiniz yer, basit bir şekilde çalıştığından ötürü güvenli bir parola kullanmanız şart. Bunun için [Zarola](https://zarola.oyd.org.tr) kullanmanızı hararetle öneririz. Parolanızı aklınızda tutmayacaksanız `openssl rand -base64 32` komutu ile de oluşturabilirsiniz.

- *timeout* bağlantı zaman aşımının belirlendiği ayar kalemi, 300 saniye makul bir süre.

- *method* şifreleme algoritmanız bu bölümde belirlenir, tercihimiz aes-256-gcm. Bu algoritma [256 bitlik bir anahtar kullanarak simetrik](https://en.wikipedia.org/wiki/Symmetric-key_algorithm) blok şifreleme yapan bir algoritma. Genel ihtiyaçlara yetecek kadar hızlı ve şu an desteklenen en güçlü algoritma.

Bu dosyayı kaydettikten sonra servis yöneticinize bir servis yazmanız gerekmekte. Örneğin, kullanımı yaygın olan _systemd_ için, aşağıdaki satırları `/usr/lib/systemd/system/shadowsocks.service` adında bir dosyaya kaydederek bu servisi oluşturabilirsiniz:

```
[Unit]
After=network.target
[Service]
Type=simple
ExecStart=/usr/local/sbin/ssserver -c /etc/shadowsocks-config.json
[Install]
WantedBy=multi-user.target
```

`shadowsocks.service` dosyasını oluşturduktan sonra kullanabileceğiniz aşağıdaki beş satır, shadowsocks sunucunuz için, systemd'ye sırasıyla _başlat_/_durdur_/_yenidenBaşlat_/_etkinleştir_/_devreDışıBırak_ komutlarını verir:
```shell
systemctl start shadowsocks.service
systemctl stop shadowsocks.service
systemctl restart shadowsocks.service
systemctl enable shadowsocks.service
systemctl disable shadowsocks.service
```
Bir servisi *etkinleştirmek* sistem başladığında servisin de otomatik olarak başlamasını sağlar. Bu ayarı kapatmak için de servisi *devreDışıBırak*ırız.

- Bu işlemlerin ardından temel shadowsocks sunucusu hazır. *Sunucuya v2ray eklentisi de dahil etmek isterseniz sunucu üzerinde çalışmaya devam edebilirsiniz;*
______
#### v2ray eklentisi

Klavuz yazılırken güncel sürümü v1.3.1 olan v2ray eklentisini [github/shadowsocks/v2ray-plugin](https://github.com/shadowsocks/v2ray-plugin/releases) adresinden indirebilirsiniz. İndirdiğiniz arşivden tek bir çalıştırılabilir dosya çıkmaktadır. Bu dosyayı da öncekilerin yanına bırakabilirsiniz; `sudo tar --directory /usr/local/sbin/ -xf v2ray-plugin-linux-amd64-v1.3.1.tar.gz`. Ardından sunucu ip adresi ile https bağlantısı için setifikayı ve onu imzalayan anahtarı oluşturuyoruz.

```shell
sudo mkdir /etc/shadowsocks
sudo openssl req -x509 -newkey ED25519 -keyout "/etc/shadowsocks/key.pem" -out "/etc/shadowsocks/cert.pem" -days 365 --nods -subj "/CN=$ip
```

İstemci ayar dosyasını şu satırları da içerecek şekilde değiştiriyoruz;

```json
{
"dns":"quad9",
"no_delay":true,
"plugin":"/usr/local/sbin/v2ray-plugin_linux_amd64",
"plugin_opts":"server;cert=/etc/shadowsocks/cert.pem;key=/etc/shadowsocks/key.pem;fast-open=true;loglevel=none"
}
```
Ek yapılandırmadaki "*dns*", "*no_delay*" ve "*fast-open*" isteğe bağlı; fast-open, çalışabilmesi için `sysctl` ile sistem üzerinde etkinleştirilmeli.
______

### İstemci Kurulumu

Teknik olarak sunucu tarafındaki ayarların aynısı istemci için de geçerli, iki ek satırla beraber istemci ayar dosyasını şu şekilde oluşturuyoruz:

```json
{
"server":"<sunucu ip adresi>",
"server_port":443,
"password":"<güvenli bir parola>",
"method":"aes-256-gcm",
"timeout":300,
"local_address":"<istemci ip adresi>",
"local_port": 1080
}
```

- *local_address* kalemi istemciniz üzerinde, sslocal'ın (shadowsocks istemcinizin) dinleyeceği, programlarınızı yönlendireceğiniz yerel adresin seçildiği yer. "127.0.x.x" kullanılabilir.

- *local_port* kalemi, istemci olarak kullandığınız bilgisayarda, seçilen yerel ip adresinde socks5 için dinlenecek portun seçildiği yer. Bazı istemciler bu ayarı kullanmamakta (android istemcisi, android’in kendi VPN altyapısını kullandığından yerel bir socks5 bağlantısı yerine tüm trafiği yönetebilmekte) lakin shadowsocks-rust istemcisi ve diğer bir çok istemci bu ayarı kullanıyor.

Son olarak da systemd servis dosyasını \(`/lib/systemd/system/shadowsocks-client.service`) şu sekilde düzenleyebilir ve isterseniz `nobody` kullanıcısı yerine `useradd --no-create-home --system shadowsocks` ile servisi çalıştırmak için bir sistem kullanıcısı oluşturabilirsiniz:

```
[Unit]
After=network.target
[Service]
Type=simple
ExecStart=/usr/local/sbin/sslocal -c /etc/shadowsocks-config.json
User=nobody
Group=nogroup
[Install]
WantedBy=multi-user.target
```
`systemctl [start|stop|restart|enable|disable] shadowsocks-client.service`
Komutlarını istemci tarafında da kullanabilirsiniz.

- *v2ray eklentisi de dahil etmek isterseniz*;
______
#### v2ray eklentisi

Sunucuda oluşturduğumuz `cert.pem` dosyasını istemcide `/etc/shadowsocks/` dizinine, `v2ray-plugin_linux_amd64` dosyasını da `/usr/local/sbin` dizinine kopyaladıktan sonra, istemci ayar dosyasını aşağıdaki satırları da içerecek şekilde düzenliyoruz;

```json
{
"dns":"quad9",
"no_delay":true,
"plugin":"/usr/local/sbin/v2ray-plugin_linux_amd64",
"plugin_opts":"cert=/etc/shadowsocks/cert.pem;fast-open=true;loglevel=none",
"protocol":"socks",
"ipv6_first":true
}
```
______
Ve hepsi bu kadar! Artık socks5 destekleyen yazılımlarınızı shadowsocks proxy’si üzerinden internete, farklı bir noktadan çıkartabilirsiniz. Örnek olarak Firefox, Thunderbird ve Telegram uygulamalarının ağ ayarlarında bu proxy’nin yerel ip ve port bilgilerini girerek kullanabilirsiniz.

Eğer bütün trafiğinizi shadowsocks üzerinden yönlendirmek isterseniz iptables ve [redsocks(http)](http://darkk.net.ru/redsocks) uygulamaları ile bunu sağlayabilirsiniz.

[iptables ve redsocks ile yönlendirme yapılmasını anlatarak bu rehbere katkı verebilirsiniz.](https://git.oyd.org.tr/oyd/guvenlik)

Android temelli cihazlar üzerinde de shadowsocks kullanılabilir. Android VPN ayarlarından "Sürekli VPN modu" etkinleştirilerek bağlantının sürekliliği sağlanabilir.Bu sayede cihazdan geçen bütün trafik sunucunuz üzerinden internete çıkar, güvenli olmayan ağlarda iletişiminiz takip edilemez ve bütün trafik tek bir IP adresine doğru gözükür.

Shadowsocks belki Çin Halk Cumhuriyeti devleti tarafından erişimi engellenmeye çalışılan, önlem geliştirilen ve kısıtlanan bir yazılım olabilir ancak aktif geliştirici kitlesi, eklentileri ve genel basitliği ile sadece Çin vatandaşları tarafından değil aynı zamanda diğer bütün dünya vatandaşları tarafından da tercih edilesi bir noktaya gelmiştir.

Güncelliğini farklı dil ve platformlarda koruyan ciddi bir geliştirici kitlesi bulunmakta ve aktif kullanıcı sayısı ile güçlü bir proxy yazılımı olan Shadowsocks kitlesel gözetime karşı etkili bir araçtır.
______
- Kaynaklar
  - <https://shadowsocks.org>
  - <https://github.com/shadowsocks/shadowsocks-rust/wiki>
  - <https://github.com/shadowsocks/v2ray-plugin>
  - <https://gitlab.com/0000matteo0000/shadowsocks-config.git>
  - <http://darkk.net.ru/redsocks>
