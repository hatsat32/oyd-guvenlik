# Mobil Cihazlar

## Hangi taşınabilir cihaz benim için uygun?

İdeal taşınabilir cihaz durumunuza bağlıdır:

* **Yüksek Risk**: Bir devletin veya uzman ajanlık şirketlerinin hedefi olacağınızdan şüpheleniyorsanız.
* **Orta Risk**: Etkin olarak hedeflenmiyorsunuz fakat bir saldırganın cihazlarınıza fiziksel erişim sağlaması durumunda kolay hedef olmayı tercih etmiyorsunuz.
* **Düşük Risk**: Taşınabilir cihazlarınızı hassas veriler için kullanmıyorsunuz.

### Yüksek Risk

Eğer yüksek risk taşıyorsanız, **cep telefonunuzu hassas hiç bir şey için kullanmayın**. Bunun sebebi, tüm telefonların "baseband modemi" olarak adlandırılan, sizi kablosuz telefon ağına ("hücresel ağ") bağlayan bir şey içermesidir. Bu modemler özel mükt ve tonla uzaktan kötüye kullanılabilecek güvenlik açığı içermektedir. Bir kere aşıldıktan sonra, baseband modemi iletişiminizi takip etmek ve kişisel verilerinizi elde etmek için kullanılabilir.

Cep telefonlarına alternatif olarak Wi-Fi desteği olan ama hücresel ağa bağlanmayan bir tablet satın alabilirsiniz. Bu tip cihazlar basband modemi içermemekte ve uzaktan saldırılara çok daha dayanıklıdır. Sadece Wi-Fi içeren bir cihaz ile hala hücresel ağa, ayrı bir taşınabilir hotspot cihazı ile bağlanabilirsiniz.

NOT: Uçak modu yeterli değildir. Cihazınıza bağlı olarak, uçak modunda bile baseband modemi hala çalışıyor ve cihazınızı saldırılara açık tutuyor olabilir.

Tavsiye edilen sadece Wi-Fi destekleyen cihazlar:

* [Pixel C](https://en.wikipedia.org/wiki/Pixel_C) veya [Pixelbook](https://en.wikipedia.org/wiki/Google_Pixelbook).
* [iPad](https://en.wikipedia.org/wiki/IPad), fakat sadece **hücresel ağ desteklemeyen** modeller.

### Orta Risk

Taşınabilir cihazınızda; suçlular, devletler veya meraklı insanlar tarafından elde edilmesini istemediğiniz hassas veriler mi var? Elbette var, herkesin var!

Bu durumda biri cihazınızı bulduğunda veya çaldığında onların işini olabildiğince zorlaştırmak istersiniz.

En iyi seçenekleriniz, ne yazık ki, Google veya Apple tarafından üretilen bir cihaz almak. Bu cihazlar diğer üreticilere göre çok daha donanımsal güvenlik içermekte ve daha sık güncellemekte. Fakat bu cihazlar bile yetkin saldırganlar tarafından veya cihaz kilidi etkin değilse genellikle kırılabilmekte.

Tavsiye edilen cihazlar:

* [Pixel](https://en.wikipedia.org/wiki/Google_Pixel)
* [iPhone or iPad](https://en.wikipedia.org/wiki/IPhone) (iPhone 4S veya sonrası cihaz şifrelemeden yararlanmak için gerekli)

### Düşük Risk

Telefonunuzu kilitsiz öylece ortalıkta mı bırakıyorsunuz? Tebrikler, taşınabilir donanımların çok da güvenli olmadığını kabul etmeye başladınız demektir.

Fakat bu sayfadaki taşınabilir cihaz güvenliğini takip etmenin sizin ve iletişim kurduğunuz insanlar için çokça faydası olacaktır.

## Cihazlarınızı yanınızdan ayırmayın

Cihazlarınızı fiziksel olarak yanınızda tutmak her zaman iyi bir fikirdir. Aksi takdirde bir saldırganın cihazınıza girmek, verilerinizi ele geçirmek ve gelecekteki etkinliklerinizi izlemek amacı ile kötücül yazılım yülemesine çokça fırsat doğacaktır.

Cihazınızın zafiyeti tavsiye edilen donanımları kullanıp kullanmadığınıza, [cihaz şifrelemenin => cihaz-şifreleme]] etkinleştirilip etkinleştirilmediğine ve cihazınızı bir parola veya PIN ile koruyup korumadığınıza bağlıdır.

**Bir saldırganın cihazınıza girebilme olasılığı:**

<table class="table">
<tr>
  <th>Cihazınız</th>
  <th>Yetkin saldırgan</th>
  <th>Eğitimli saldırganr</th>
  <th>Olağan saldırgan</th>
</tr>
<tr>
  <td>Tavsiye edilen cihaz + Şifrelenmiş + Kilitli</td>
  <td>DÜŞÜK</td>
  <td>ÇOK DÜŞÜK</td>
  <td>HİÇ</td>
</tr>
<tr>
  <td>Tavsiye edilen cihaz + Kilitli</td>
  <td>MEDIUM</td>
  <td>LOW</td>
  <td>VERY LOW</td>
</tr>
<tr>
  <td>Normal cihaz + Şifreli + Kilitli</td>
  <td>YÜKSEK</td>
  <td>ORTA</td>
  <td>DÜŞÜK</td>
</tr>
<tr>
  <td>Normal cihaz + Kilitli</td>
  <td>ÇOK YÜKSEK</td>
  <td>YÜKSEK</td>
  <td>ORTA</td>
</tr>
<tr>
  <td>Kilitsiz</td>
  <td>KESİN</td>
  <td>KESİN</td>
  <td>KESİN</td>
</tr>
</table>

Saldırgan tipleri:

* **Yetkin saldırgalarn** Kilitli telefonlara girmekte uzmanlaşmış büyük devletleri ve uluslar arası şirketleri kapsar.
* **Eğitimli saldırganlar** Yerel kolluk kuvvetlerini ve telefon kıran adli tıp şirketlerini kapsar.
* **Olağan saldırganlar** Özel donanım sahibi olmayan yetenekli teknoloji meraklılarını kapsar.

Eğer cihazınızdan uzak kalacak ve cihazınıza girilme ihtimali var ise, verilerinizi yedeklemeli tam fabrika ayarlarına dönüş yapmalısınız(veya yeni bir cihaz almayı düşünebilirsiniz).

## Signal Kullanın

**Signal** özgür bir anlık yazışma yazılımı olarak telefonunuzla gelen normal yazışmaya güvenli bir alternatif oluşturmaktadır. WhatsApp veya Telegram gibi çalışsa da çok daha iyi bir güvenlik sağlar.

Neden signal kullanmalısınız?

* GSM hizmet sağlayıcınız size gönderilen her mesajın bir kopyasını tutmaktadır. Signal ile GSM hizmet sağlayıcınız ne mesajlarınıza ne de iletişimde bulunduğunuz insanlara ulaşabilir.
* Bir saldırgan için telefon numaranızı ele geçirmek görece kolaydır. Signal ile bir kişinin "güvenlik numarası'nın" değiştiğine dair bir uyarı alırsınız. Bu aynı zamanda biri yeni telefon edindiğinde de gerçekleşir.
* Signal aynız amanda güvenli sesli iletişim için de kullanılabilir. GSM hizmet sağlayıcınız kimi aradığınız, kimin sizi aradığı ve aramaların uzunluğuna ilişkin kayıt tutar. Signal ile GSM servis sağlayızınız bu bilgilere ulaşamaz. Cihazınız güvenli olduğu sürece aramalarınızın içerğiği ve uzunluğu gizli kalacaktır.
* WhatsApp, Telegram veya Wire gibi diğer "güvenli" yazışma programları Signal ile kıyaslanınca çokça soruna sahiptir.

Daha fazla bilgi için, [Security Planner / Signal](https://securityplanner.org/#/tool/signal)'e bakın.

## Cihazımı bul'u Etkinleştirin

"Cihazımı bul" seçeneğini etkinleştirmeyi değerlendirin. Bu çalınan veya kaybolan bir cihazınızı uzaktan yerini tespit etmek, kilitlemek veya kişisel verilerinizi silmek imkanı verir.

Daha fazla bilgi için:

* [Security Planner / Cihazımı Bul (Android)](https://securityplanner.org/#/tool/find-my-device).
  * NOT: Bu özellik bir Google hesabını cihazınıza bağlamanızı gerektirir. Ayrıca "Cihazımı Bul" seçenğini etkinleştirirseniz Google konum bilginize dair daha fazla bilgiyi elde edecektir.
* [Security Planner /  IPhıne'umu Bul (iOS)](https://securityplanner.org/#/tool/find-my-iphone).

## Güvenli Fotoğraf Çekin

Telefonunuzun kamerası, çektiğiniz her fotoğrafa yüksek olasılıkla hassas çokça veriyi eklemekte. İnternette paylaştığınız bir gönderinin nasıl kullanılacağını bilemeyeceğinizden, fotoğrafların taşıdığı kişisel veriyi paylaşmadan önce silmek iyi bir fikirdir.

Fotoğraflarınızda "geotagging" sorununu engellemek için, kamera ayarlarınızı açın ve konum bilgisini kaydetme ayarlarını kapatın.

Geotagging kapalı iken bile kamera yazılımınız cihazınızın modelini ve diğer potansiyel olarak hassas veriyi fotoğraflara kaydedecektir. Bu durumdan kurtulmanın en iyi yolu ayrı bir yazılımla "EXIF1 verisini fotoğraf dosyalarından silmektir. Bu yazılımlar aynı zamanda konum bilgisini de çektiğiniz geçmiş fotoğraflardan silmek için de kullanılabilir.

Daha fazla bilgi için: [Fotoğraflardan EXIF üstverisini silmenin 3 yolu](https://www.makeuseof.com/tag/3-ways-to-remove-exif-metadata-from-photos-and-why-you-might-want-to/).

## Diğer Öneriler

* Cihazınızın kilidini açmak için bir parola veya en azından bir PIN kullanın. Parmak izi veya yüz tanıma gibi biyometrik verileri ekran kilidi için kullanmayın. Bu özellikler güvenli değildir.
* Telefonunuzu bildirimlerin detaylarını kilit ekranında göstermeyecek şekilde ayarlayın.
* Telefonunuzun bulut ile hangi verileri eşitlediğini bilin. Örneğin bir fotoğrafı telefonunuzdan silmiş olsanız bile Dropbox veya iCloud gibi bir hizmete çoktan yedeklenmiş olabilir.
