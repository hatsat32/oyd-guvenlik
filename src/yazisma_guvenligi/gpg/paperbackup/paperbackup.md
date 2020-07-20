# Paperbackup ile Kağıda Anahtar Yedeği Basmak

[Gnupg](../gpg-anahtar-uretimi.md) ve [SSH](https://en.wikipedia.org/wiki/Secure_Shell) gibi asimetrik [RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem)) anahtarları bilişim sistemlerine erişimde çok önemli bir yer kaplamaktadır. Bu bakımdan kullanıcıların bu anahtarlar ile şifreledikleri veya erişim imkanına sahip olduklara cihazlara bağımlılıkları oranında anahtarların da değeri artmaktadır. Bir anahtarın kaybı şifrelenmiş verilere erişimi neredeyse imkansız hale getirdiği gibi erişim imkanı kaybedilen uzak sunucuların yarattığı sorunlar da tatsız olabilmektedir. Bu bakımdan anahtarların sayısal yedeklerinin alınması ve güvende tutulması çok önemli. Bu bakımdan pek az düşünülse de **Kağıt** bu amaçla çok ideal bir ortam olabilmekte.

## Kağıdın avantajları

* __Uzun ömürlülük__:Kağıt taş dışında bugüne kadar veri taşımayı başarmış en eski ortamlardan bir tanesi. [Antik Mısır papirusları](https://en.wikipedia.org/wiki/History_of_writing#Writing_materials) milattan önce 3000 yılına kadar gitmekte. İlginç şekilde kitap gibi bir yığın halinde bulundurulduğunda yangına karşı da bir hayli dayanıklıdır. Bu bakımdan yangına uğramış pek çok yapıdan kitaplar kısmi zararlarla kurtarılabilmiştir. Günümüzde suya dayanıklı kağıt ve baskı teknolojilerinin geliştirilmesi ile birlikte, asitsiz kağıt üstüne tonerle yapılmış bir baskıyı ömür bakımından yenebilecek pek az kayıt imkanı bulunmaktadır.

* __Maliyet__:Kağıt Mb başına en ucuz kayıt medyası olmasa da şifreleme anahtarları gibi küçük verileri kaydetmek için çok ekonomik bir tercih. Bir yazıcı ve 5-20 sayfa arası kağıt ile bir Gnupg anahtarı rahatlıkla yedeklenebilmekte. Baskı maliyetinin 5 krş civarında olduğunu varsayarsak 1 liranın altında yedekler almak mümkün. Aynı zamanda baskıyı yapan makineyi de satın almanız gerekmemekte. Aynı zamanda evinize giren bir hırsız harddiskinize göz dikebilir fakat kimsenin bir deste kağıdı alma arzusu taşıyacağı düşünülmez.

* __Saklama Kolaylığı__:Kağıt yedekleri saklamak için çok özel şartlara ihtiyacınız yok. Sabit sürücü ve benzeri sayısal kayıt ortamlarını nem, sıcaklık, sarsıntı gibi öğelerden korumak zorunda olduğunuz gibi kimi zamanlarda en iyi koşullarda saklanmalarına rağmen [bozulmaları mümkün olabilmekte.](https://www.backblaze.com/blog/hard-drive-failure-rates-q1-2017/) Buna karşı bir poşete konmuş kağıt siz onu unutsanız dahi olduğu yerde sağlam kalmaya devam edecek ve gerekirse gözünüz ile okunmanıza da imkan verecektir.

## Kağıdın dezavantajları

* __Oluşturma__:Sayısal verilerin kağıt yedeklerini oluşturmak görece zor bir işlem. Sayısal veriyi bir sayısal ortama aktarmak günümüzde çocuk oyuncağı kıvamında fakat kağıt gibi anolog bir sisteme bunu güvenle ve emin şekilde aktarmak can sıkıcı olabilmekte. Aynı zamanda sayısal verilerin bastırılabilir şekilde encode edilmesi ve büyük boyutlu verilerin baskısının çok zaman ve kaynak harcaması bu durumu daha kolay kılmamakta.

* __Kurtarma__:Yedekten kurtarma yapılamıyorsa yapılan şeye yedek demek pek mümkün olmaz. Kağıdın bu konudaki avantajı aynı zamanda bir dezavantaj da taşımakta. Bastırdığınız kağıt üzerindeki sayısal veriyi tekrar bilgisayara geçirmek için karekodlar, datamatrix veya [OCR](https://en.wikipedia.org/wiki/Optical_character_recognition) gibi teknikleri kullanmanız gerekli. Bu amaçla tarayıcı ile kağıdı taramalı ve hatasız şekilde veriyi geri alabilmelisiniz. Tabii en son çare olarak veriyi tek tek elle girme imkanınız da bulunmakta fakat bu gerçekten son çare olacak kadar zahmetli bir süreç.

## Paperbackup

[Paperbackup](https://github.com/intra2net/paperbackup) küçük bir python kodu aracılığı ile ASCII sayısal verilerin kolayca kağıt yedeklerinin çıkarılmasını sağlayan bir program.

Her python kodu gibi paperbackup da bir takıp bağımlılıklar içeriyor. İlk çalıştırdığınızda mutlaka bir bağımlılığın elinizde olmaması garanti gibi. Bu sebeple aşağıdaki komutu çalıştırarak muhtemel bağımlılıkları sisteminize indirip kurabilirsiniz.

RPM tabanlı sistemler için:
`sudo yum install PyX enscript qrencode hashlib zbar`
Debian için:
`sudo apt-get update && sudo apt-get install PyX enscript qrencode hashlib zbar`

### Anahtar veya veri yedeğini oluşturma

Öncelikle yedeğini alacağımız verinin ASCII veya base64 encode edilmiş haline ihtiyacımız var.

Gnupg anahtarımızın yedeğini şu şekilde alırsak ortaya çıkan anahtar dosyası yedeklenmeye uygun olacaktır.

`gpg --export-secret-key --armour [anahtar ID] > anahtar_sec.asc`

alınan çıktı bir metin editörü ile incelenirse şu şekilde görünmesi gerekli.

-----BEGIN PRIVATE KEY-----

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

-----END PRIVATE KEY-----

Eğer yedeğini almak istediğiniz veri başka bir şey ise aşağıdaki komut aracılığı ile base64 enode ederek yedeklemeye hazır edebilirsiniz. Unutmayın ki yedekleyeceğiniz veriden %25 daha büyük bir sonuç elde edeceksiniz ve her sayfaya 10 Kb veri için 15 sayfa elde edeceksiniz.

`base64 -w 65 [yedeklenecek verinin dizini] > [kaydedilecek dizin]`

Bununla birlikte yedeklenecek verinizi veya anahtarınızı hazır etmiş bulunmaktasınız.

### Kağıt yedeği hazırlama

Öncelikle [Paperbackup git deposundan](https://github.com/intra2net/paperbackup) sağdaki yeşil indir düğmesi ile gerekli dosyaları indirin veya aşağıdaki komut ile git deposunu kopyalayın.

`git clone https://github.com/intra2net/paperbackup`

Programı indirdiğiniz dizine gidin.

`cd [paperbackup dizini]`

Daha sonra kağıt yedeğinizin PDF dosyasını hazırlamak için aşağıdaki komutu kullanabilirsiniz.

`python3 paperbackup.py [yedek dosyasının dizini]`

Betik işini yaptıktan sonra çalıştırdığınız dizinde şu şekilde bir PDF dosyası sizi karşılayacak.

![alt-text](paperbackup1.png "Karekodlar")
![alt-text](paperbackup2.png "ASCII Yedek")

### Yedeği bastırma

Yedeğinizi bastırmak konusunda karar size kalmış durumda. Temel olarak dikkat etmeniz gereken unsurlardan biri eğer güvenlik gerektiren bir yedeği şifresiz olarak yedeklediyseniz baskı aracınıza ve ona ulaşmak için kullandığınız bağlandıya (ör. Yerel ağ yazıcısı) güvenip güvenmediğiniz sorusudur. Bu bakımdan en güvenilir yöntem PDF dosyasını bir USB belleğe alarak doğrudan yazıcıdan bastırmak veya bilgisayarınıza yazıcıyı USB ile bağlamaktır.

Kağıt ve yazdırma yöntemi size kalmış. Her türlü baskı beklentilerinizi fazlasıyla karşılayacak kadar uzun ömürlü olacaktır. Lakin asitsiz kağıda toner baskı en iyi sonucu size sağlayacaktır hem baskı kalitesi hem de ömür bakımından.

Yedeklernizi bastırdıktan sonra katlamayın ve bir zarf içinde veya daha iyisi su geçirmez bir poşet içinde saklamayı ihmal etmeyin. Yedeğinizi **tarihlerseniz** ileride bu bilgi işinize yarayabilir veya başka ileri tarihli yedekler almanız durumunda karışmasını engelleyebilir.

### Kurtarma

Öncelikle kağıt yedeğinizin mümkün olan en yüksek çözünürlükte tarayın. Taramanızın sonucu olan PDF dosyasını paperbackup dizinine taşıyın ve aşağıdaki komut ile geri kurtarabilirsiniz.

`./paperrestore.sh [kurtarılacak PDF dizini] > kurtarma`

Paperbackup ona verdiğiniz isimle dosyayı bulunduğu dizine kaydedecektir.

### Okuma listesi ve benzer projeler

* [https://github.com/tuxlifan/paperbackup]()
* [http://ollydbg.de/Paperbak/]()
* [https://github.com/Rupan/paperbak/]()
* [https://git.teknik.io/scuti/paperback-cli]()
* [https://github.com/colorsafe/colorsafe]()
* [http://ronja.twibright.com/optar/]()
* [http://www.jabberwocky.com/software/paperkey/]()
* [https://github.com/4bitfocus/asc-key-to-qr-code]()
