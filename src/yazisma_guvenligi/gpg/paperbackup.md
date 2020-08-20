# Paperbackup ile Kağıda Anahtar Yedeği Basmak

[GnuPG](../gpg-anahtar-uretimi.md) ve [SSH](https://en.wikipedia.org/wiki/Secure_Shell) gibi araçlar ile kullandığımız asimetrik [RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem)) anahtarları bilişim sistemlerine erişimde çok önemli bir yer kaplamaktadır. Bu bakımdan kullanıcıların bu anahtarlar ile şifreledikleri veya erişim imkanına sahip oldukları cihazlara bağımlılıkları oranında anahtarların da değeri artmaktadır. Bir anahtarın kaybı, şifrelenmiş verilere erişimi neredeyse imkansız hale getirdiği gibi erişim imkanı kaybedilen uzak sunucuların yarattığı sorunlar da tatsız olabilmektedir. Bu bakımdan anahtarların yedeklerinin alınması ve güvende tutulması çok önemlidir. Bu bakımdan pek az düşünülse de **kağıt** bu amaç için çok ideal bir ortamdır.

## Kağıdın avantajları

* __Uzun ömürlülük__: Kağıt, taş dışında bugüne kadar veri taşımayı başarmış en eski ortamlardan bir tanesidir. [Antik Mısır papirüsleri](https://en.wikipedia.org/wiki/History_of_writing#Writing_materials)'nin tarihi M.Ö 3000 yılına kadar gitmektedir. İlginç bir şekilde papirüs, kitap gibi bir yığın halinde bulundurulduğunda yangına karşı da bir hayli dayanıklıdır. Bu sayede kitaplar, yangına uğramış pek çok yapıdan kısmi zararlarla kurtarılabilmiştir. Günümüzde suya dayanıklı kağıtlar ve baskı teknolojilerinin geliştirilmesi ile birlikte, asitsiz kağıtların üzerine tonerle yapılmış bir baskıyı ömür bakımından yenebilecek pek az kayıt imkanı bulunmaktadır.

* __Maliyet__: Kağıt, MB başına en ucuz kayıt medyası olmasa da şifreleme anahtarları gibi küçük verileri kaydetmek için çok ekonomik bir tercihtir. Bir yazıcı ve 5-20 sayfa arası kağıt ile bir GnuPG anahtarı rahatlıkla yedeklenebilmektedir. Baskı maliyetinin 0,05 TL civarında olduğunu varsayarsak, 1 liranın altında bir maliyetle yedekler almak mümkündür. Aynı zamanda evinize giren bir hırsız hard diskinize veya hard diskinizin takılı olduğu makineye göz dikebilir, fakat kimsenin bir deste kağıdı alma arzusu taşıyacağı düşünülmez.

* __Saklama kolaylığı__: Kağıt yedekleri saklamak için çok özel şartlara ihtiyacınız yoktur. Sabit sürücü ve benzeri dijital kayıt ortamlarını nem, sıcaklık, sarsıntı gibi öğelerden korumak zorunda olduğunuz gibi, kimi zaman en iyi koşullarda saklanmalarına rağmen [bozulmaları mümkündür](https://www.backblaze.com/blog/hard-drive-failure-rates-q1-2017/). Buna karşın, bir poşete konmuş kağıtlar siz onları unutsanız dahi olduğu yerde sağlam kalmaya devam edecek ve gerekirse gözünüzle okunmanıza da imkan verecektir.

## Kağıdın dezavantajları

* __Oluşturma__: Dijital verilerin kağıt yedeklerini oluşturmak görece zor bir işlemdir. Dijital veriyi başka bir dijital ortama aktarmak günümüzde çocuk oyuncağı kıvamındadır, fakat kağıt gibi analog bir sisteme bunu güvenle ve emin bir şekilde aktarmak can sıkıcı olabilmektedir. Aynı zamanda dijital verilerin bastırılabilir şekilde kodlanmasının (encode) ve büyük boyutlu verilerin bastırılmasının çok fazla zaman ve kaynak harcaması bu durumu zorlaştırmaktadır.

* __Kurtarma__: Eğer yedekten kurtarma yapılamıyorsa, yapılan şeye yedek demek pek mümkün değildir. Kağıdın bu konudaki avantajı, aynı zamanda bir dezavantajdır. Bastırdığınız kağıt üzerindeki dijital veriyi tekrar bilgisayara geçirmek için karekodlar, datamatrix veya [OCR](https://en.wikipedia.org/wiki/Optical_character_recognition) gibi teknikleri kullanmanız gerekmektedir. Bunun için bir tarayıcı vasıtasıyla kağıdı taramanız gerekecektir. En son çare olarak veriyi tek tek elle girme imkanınız da bulunmaktadır, fakat bu gerçekten son çare olacak kadar zahmetli bir süreçtir.

## Paperbackup

[Paperbackup](https://github.com/intra2net/paperbackup), ASCII olarak kodlanmış dijital verilerin kağıt yedeklerinin kolayca çıkartılmasını sağlayan bir yazılımdır. Python ile geliştirilmiştir.

Her Python kodu gibi `paperbackup` da bir takım bağımlılıklara sahiptir. Aşağıdaki komutu çalıştırarak gereken bağımlılıkları sisteminize indirip kurabilirsiniz.

RPM kullanan dağıtımlar için (Red Hat, Fedora, CentOS vb.):  
`sudo yum install PyX enscript qrencode hashlib zbar`  
APT kullanan dağıtımlar için (Debian, Ubuntu, Mint vb.):  
`sudo apt-get update && sudo apt-get install python3-pyx enscript python3-qrencode hashlib python3-zbar`

### Anahtar veya veri yedeğini oluşturma

Öncelikle yedeğini alacağımız verinin ASCII olmasına veya dosya normalde binary ise base64 ile kodlanmış (encode) haline ihtiyacımız var.

GnuPG anahtarınızın yedeklemeye uygun halini çıkartmak için şu komutu çalıştırabilirsiniz:

`gpg --export-secret-key --armour [anahtar ID] > anahtar_sec.asc`

Alınan çıktı, bir metin editörüyle açıldığında şu şekilde görünmelidir:

```
-----BEGIN RSA PRIVATE KEY-----

MVp4OTNhQXNrSXNibzB2K1F0bEU3SzJ5MVhVSDdXc2F1eVZ5L0JidjREcjAKNU1xMzVMTnl0TDZp
ZDdpeXhKVlNoR3B5R0xCNU0zSkZ3Tk40SndrODM4a1hQSkQreW55SWdwS2ttRGdYNFNNQgpqSmxZ
MVc2TDk0NGc5MFRBRUJGUXZHMFdnQ1JzWXJtWjRuUHAvcmhLdzBGSUxzdzZSeXlBN0RpazQ2R0ND
a0VvClduYS9WZTcxejhsL1Fkako0bzdDNUhlb2pUWU4vaHROL2ZFejJKQSsyOGNoM05KcXZGUEtB
R2UzZmROdC9DTW4KSm5wR1lEWm1YMi8vWG4rdGlOMnpwWTZnc255Wm45RGcwVzVlK2k4WWRmdS9K
NjJnKzQvUlRtaVNTcmNuVjgzWgp0ZGlhdDJrWGhwbi8xS1pJRCtMWXZwNFE2cmJvVnBmMFhhTHJI
cEFRYnFFdndrVW5rVkc1K2c4T2prZzZTYlduCld1ZzUvaWh3a0RJWEZtOVhsRlpuby83RTY1V2Yr
aFVYZmJ0TkxwbHpJMlV4TS9remxWQUNQRXQ1UWpYVldhK0gKOWRSRzY0MXFHNERzaW9Oci8wQkIr
RHZFSTZaS1JIdTNnbzlpbmlkLzU0WUNPSldIVTUyRnl0YVdKdUw0QkpiOQpWcUd1V3NjYTZXejEw
UStXaDhvNkt1V0JCc2VPSnNxMEhiWVdsRHdEeTZVdm9LM1RKaE8wYzFQcmlvWFk3N0dpCjd5UXZs
WWtEb1hqVGFxbXRUbHBWaG13OG9DdG5teDZCeVdldEhhcmV4WXNIM21oTnc2OHZkNU9NV0V2ak1m
REEKeVNuUFdvbEV5WFVWR3FwdXkrS25XNnpjYlo4UStxTUxqOVdLZ0UrWTJtUy9jNHhrOHlmZzRx
Sk9rM1ZnWXl2cApDa3NOK2hrVnVQMnV5Nis2bGVmMmVUNHV1RjhJcmQxbnAycU1lOVpUSmY0Zndp
QUhtbjczcFZsbnpaL2RYSFpuCkVHNEl5NG15ZjByZUFTVTk3U0NZbW9sbWl6WTJjVDhhaFFOVWU4
VXk1cGlGcjRWb01OVktzVWl1REJaMVlDUEkKcXI5cGk3eWN0ZlRscUxWRitscHpZRE5ZRjZtK0JH
Vkx3aGQ2SmVyMWJKcllIbjJmc0FqblFqeDNNdFM3MXFMSApBUT09Cj1IUTlJCi0tLS0tRU5EIFBH

-----END RSA PRIVATE KEY-----
```

Eğer yedeğini almak istediğiniz veri başka bir şey ise, aşağıdaki komut aracılığıyla base64 ile kodlayarak yedeklemeye hazır hale getirebilirsiniz. Yedekleyeceğiniz veriden yaklaşık %25 daha büyük bir sonuç elde edeceğinizi unutmayın.

`base64 -w 65 [yedeklenecek verinin yolu] > [kaydedilecek dosyanın yolu]`

Yedeklenecek anahtarı veya veriyi hazır ettikten sonra, `paperbackup`ı kurun.

### Kağıt yedeği hazırlama

Öncelikle [Paperbackup git deposuna](https://github.com/intra2net/paperbackup) gidin ve sağdaki yeşil renkli "İndir" düğmesini kullanarak `paperbackup`ı indirin. Ayrıca aşağıdaki komut ile git deposunu bilgisayarınıza klonlayabilirsiniz.

`git clone https://github.com/intra2net/paperbackup`

İndirdiğiniz dosyayı bir yere çıkartın ve aşağıdaki komut ile `paperbackup`ın olduğu dizine gidin.

`cd [paperbackup dizini]`

Daha sonra kağıt yedeğinizi PDF formatında hazırlamak için aşağıdaki komutu kullanabilirsiniz.

`python3 paperbackup.py [yedek dosyasının dizini]`

Betik işini yaptıktan sonra, çalıştırdığınız dizinde şu şekilde bir PDF dosyası sizi karşılayacak.

![alt-text](paperbackup/paperbackup1.png "Karekodlar")
![alt-text](paperbackup/paperbackup2.png "ASCII Yedek")

### Yedeği bastırma

Yedeğinizi bastırmak konusunda karar size kalmış durumda. Temel olarak dikkat etmeniz gereken unsurlardan biri eğer güvenlik gerektiren bir yedeği şifresiz olarak yedeklediyseniz baskı aracınıza ve ona ulaşmak için kullandığınız bağlantıya (ör. Yerel ağ yazıcısı) güvenip güvenmediğiniz sorusudur. Bu bakımdan en güvenilir yöntem PDF dosyasını bir USB belleğe alarak doğrudan yazıcıdan bastırmak veya bilgisayarınıza yazıcıyı USB ile bağlamaktır.

Kağıt ve yazdırma yöntemi size kalmış. Her türlü baskı beklentilerinizi fazlasıyla karşılayacak kadar uzun ömürlü olacaktır. Lakin asitsiz kağıda toner baskı en iyi sonucu size sağlayacaktır hem baskı kalitesi hem de ömür bakımından.

Yedeklernizi bastırdıktan sonra katlamayın ve bir zarf içinde veya daha iyisi su geçirmez bir poşet içinde saklamayı ihmal etmeyin. Yedeğinizi **tarihlerseniz** ileride bu bilgi işinize yarayabilir veya başka ileri tarihli yedekler almanız durumunda karışmasını engelleyebilir.

### Kurtarma

Öncelikle kağıt yedeğinizi mümkün olan en yüksek çözünürlükte tarayın. Taramanızın sonucu olan PDF dosyasını `paperbackup` dizinine taşıdıktan sonra aşağıdaki komut ile kurtarabilirsiniz.

`./paperrestore.sh [kurtarılacak PDF dizini] > kurtarma`

Paperbackup ona verdiğiniz isimle dosyayı bulunduğu dizine kaydedecektir.

### Okuma listesi ve benzer projeler

* <https://github.com/tuxlifan/paperbackup>
* <http://ollydbg.de/Paperbak/>
* <https://github.com/Rupan/paperbak/>
* <https://git.teknik.io/scuti/paperback-cli>
* <https://github.com/colorsafe/colorsafe>
* <http://ronja.twibright.com/optar/>
* <http://www.jabberwocky.com/software/paperkey/>
* <https://github.com/4bitfocus/asc-key-to-qr-code>
