## GPG ile Komut Satırında işlemler

GPG temel olarak komut satırında çalışan bir yazılımdır. Bu bakımdan grafik arayüzler tarafından sunulmayan pek çok faydalı özelliği uçbirim aracılığı ile kullanmak ve kimi zaman grafik arayüzlerin sunduğu işlevleri daha kolay yerine getirmek mümkündür. Pek çok kullanıcı için uçbirim korkutucu olabilmektedir. Lakin her Gnu/Linux cihazda bir uçbirim ve GPG kurulu olduğu düşünüldüğünde GPG'nin evrensel kullanımı uçbirimde toplanmaktadır.

GPG'nin man sayfası çok kalabalıktır. Bu rehberde son kullanıcıya lazım olabilecek temel ve orta seviyedeki işlevler ipuçları ile birlikte sunulacaktır. Şayet GPG ile ilgili daha çok şey öğrenmek istenirse aşağıdaki komut ile man sayfasının okunması veya pratik olarak yardım sayfasının çağrılması mümkündür.

`man gpg` ve `gpg --help`

## Şifreleme ve İmzalama

[Uçbirim aracılığı ile e-posta](yazilim_guvenligi/ucbirim_eposta.md) şifreleme, imzalama ve deşifre rehberine bu başlıktaki detaylar için başvurulabilir.

## Simetrik şifreleme

GPG sadece RSA ve ECC gibi asimetrik şifreleme algoritmalarını değil aynı zamanda AES gibi simetrik şifreleme imkanlarını da sunmaktadır. Bu şifreleme yönteminde bir parola hem şifreleme hem deşifre için kullanıldığından özel bir anahtar yönetimine ihtiyaç duyulmaz ve kimi zaman kullanımı tercih edilebilir.

Bir mesajı veya dosyayı simetrik olarak şifrelemek için aşağıdaki komutları kullanabilirsiniz:

`gpg --symmetric --armor` veya `gpg -ca`

Bir dosyayı şifrelemek isterseniz aşağıdaki komutu girebilirsiniz. GPG şifrelenmiş dosyayı .asc uzantısı ile aynı yere kaydedecektir:

`gpg --symmetric --armor [dosya dizini]`

Şifrelediğiniz veriyi aynı zamanda bir anahtarınız var ise imzalayarak sizden geldiğine ve bütünlüğüne kanıt oluşturabilirsiniz.

`gpg --symmetric --sign --armor` veya `gpg -csa`

## İmzalama

GPG birden fazla şekilde imzalama yapabilmektedir. Her imzalama tipi iletim ve gereken karakter bakımından farklılık arz ettiğinden kullanıcının beklentisine göre tercih yapması mümkündür.

### Clear-sign

Clear-sign veya açık imza imzalanan içeriğin okunabilmesine imkan sağlamaktadır. Bu sayede mesajınız gözle okunabilirken dileyen biri altında bulunan imza bloğu ile birlikte mesajınızın doğruluğunu denetleyebilmektedir. Bu şekilde bir mesaja imza atmak isterseniz aşağıdaki komutu girip mesajınızı yazın ve `ctrl + D` komutu ile sonlandırın.

`gpg --clear-sign`

### Embeded-sign

Embeded veya gömülü imza, mesaj ve imza bloğunun tek bir base64 bloğunda kodlanması ile ortaya çıkar. Bu mesaj şifreli olmamakla birlikte okunabilmesi için yine de çözülmesi gereklidir. Bu şekilde bir imza elde etmek için aşağıdaki komutu girip mesajınızı yazın ve `ctrl + D` komutu ile sonlandırın.

`gpg --sign --armor`

### Detached-sign

Detached veya ayrık imza, imzalanan veri ile imza bloğunun ayrı dosyalar olması anlamına gelmektedir. Çoğunlukla dijital verilerin doğruluğunu göstermek için kullanır. Dosyanın yanında aynı isimde .sig uzantılı imza dosyası da gelir. Bu tip bir imza oluşturmak için aşağıdaki komutu kullanabilirsiniz. GPG imza dosyasını imzalanan dosyanın yanına .sig uzantısı ile ekleyecektir.

`gpg --detached-sign [dosya dizini]`

Şayet imzayı metin olarak aktarmayı düşünüyorsanız `--armor` paramteresini ekleyerek base64 kodlama ile aynı işlemi gerçekleştirebilirsiniz.

`gpg --detached-sign --armor [dosya dizini]`

## İmza denetleme

GPG ile imzalanmış bir metni doğrulamak için aşağıdaki komutu kullanıp mesajı yapıştırdıktan sonra `ctrl + D` komutu ile işlemi tamamlayabilirsiniz.

`gpg --verify`

Şayet bir dosyaya ait .sig uzantlı imzayı denetleyecekseniz ve dosya ile imza dosyasının adı aynı ise aşağıdaki komutu kullanabilirsiniz.

`gpg --verify [imza dosyası.sig]`

## Umumi anahtarları listeleme

GPG kullanımı iletişime geçeceğiniz kişilerin umumi anahtarlarını da bulundurmanızı gerektirmekte. Bu anahtarlar bir firhist gibi cihazınızda tutulmaktadır. Bunları listelemek için aşağıdaki komutu kullanabilirsiniz.

`gpg --list-keys`

Anahtarlığınızdaki belirli bir anahtarı arıyor iseniz aşağıdaki şekilde arama yapabilirsiniz.

`gpg --list-keys [anahtar ID veya e-posta]`

## Özel anahtarları listeleme

Şayet size ait özel anahtarlarınızı listelemek isterseniz aşağıdaki komutu kullanabilirsiniz.

`gpg --list-secret-keys`

## İmzaları listeleme

## Anahtar imzalarını kontrol etme

## Umumi anahtar dışa çıkartma

## Sunucuda anahtar arama

## Sunucuya anahtar gönderme

## Anahtarları güncelleme

## Anahtar içe aktarma

## Anahtar düzenleme

## Anahtar imzalama
