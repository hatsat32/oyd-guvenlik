## GPG ile Komut Satırında işlemler

<!-- toc -->

GPG temel olarak komut satırında çalışan bir yazılımdır. Bu bakımdan grafik arayüzler tarafından sunulmayan pek çok faydalı özelliği uçbirim aracılığı ile kullanmak ve kimi zaman grafik arayüzlerin sunduğu işlevleri daha kolay yerine getirmek mümkündür. Pek çok kullanıcı için uçbirim korkutucu olabilmektedir. Lakin her Gnu/Linux cihazda bir uçbirim ve GPG kurulu olduğu düşünüldüğünde GPG'nin evrensel kullanımı uçbirimde toplanmaktadır.

GPG'nin man sayfası çok kalabalıktır. Bu rehberde son kullanıcıya lazım olabilecek temel ve orta seviyedeki işlevler ipuçları ile birlikte sunulacaktır. Şayet GPG ile ilgili daha çok şey öğrenmek istenirse aşağıdaki komut ile man sayfasının okunması veya pratik olarak yardım sayfasının çağrılması mümkündür.

`man gpg` ve `gpg --help`

## Şifreleme ve İmzalama

[Uçbirim aracılığı ile e-posta](../ucbirim_eposta.md) şifreleme, imzalama ve deşifre rehberine bu başlıktaki detaylar için başvurulabilir.

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

Şayet imzayı metin olarak aktarmayı düşünüyorsanız `--armor` parameteresini ekleyerek base64 kodlama ile aynı işlemi gerçekleştirebilirsiniz.

`gpg --detached-sign --armor [dosya dizini]`

## İmza denetleme

GPG ile imzalanmış bir metni doğrulamak için aşağıdaki komutu kullanıp mesajı yapıştırdıktan sonra `ctrl + D` komutu ile işlemi tamamlayabilirsiniz.

`gpg --verify`

Şayet bir dosyaya ait .sig uzantlı imzayı denetleyecekseniz ve dosya ile imza dosyasının adı aynı ise aşağıdaki komutu kullanabilirsiniz.

`gpg --verify [imza dosyası.sig]`

## Umumi anahtarları listeleme

GPG kullanımı iletişime geçeceğiniz kişilerin umumi anahtarlarını da bulundurmanızı gerektirmekte. Bu anahtarlar bir fihrist gibi cihazınızda tutulmaktadır. Bunları listelemek için aşağıdaki komutu kullanabilirsiniz.

`gpg --list-keys`

Anahtarlığınızdaki belirli bir anahtarı arıyor iseniz aşağıdaki şekilde arama yapabilirsiniz.

`gpg --list-keys [anahtar ID veya e-posta]`

## Özel anahtarları listeleme

Şayet size ait özel anahtarlarınızı listelemek isterseniz aşağıdaki komutu kullanabilirsiniz.

`gpg --list-secret-keys`

## İmzaları listeleme

Şayet bir anahtara atılmış olan imzaları görüntülemek isterseniz aşağıdaki komutu kullanabilirsiniz.

`gpg --list-sigs [anahtar ID veya e-posta]`

## Anahtar imzalarını kontrol etme

Bir anahtardaki imzaları görüntülemek yerine bu imzalar arasında [WOT](/yazisma_guvenligi/wot.md) ile güven ağı doğrulaması yapmak isterseniz aşağıdaki komut ile anahtarlığınızdaki umumi anahtarlarla atılı imzalar arasında bir bağlantı olup olmadığını denetleyebilirsiniz.

`gpg --check-signatures [anahtar ID veya e-posta]`

## Umumi anahtar dışa çıkartma

Kendi anahtarınıza veya bir başka kişiye ait umumi anahtarı bir amaçla kullanmak veya bir yere göndermek için dosyaya kaydetmek isterseniz aşağıdaki komutu kullanabilirsiniz. Şayet bu anahtarın basılabilir olmasını isterseniz `--armor` parametresini verebilirsiniz. Bu durumda çıktı ASCII karakterlerle yazdırılacaktır.

`gpg --export [anahtar ID veya e-posta] > [anahtar dosya yolu]`

## Sunucuda anahtar arama

Pek çok GPG anahtarı anahtar sunucularında aleni olarak tutulur. Bu anahtar rehberlerinde belirli bir anahtarı, ismi veya e-postayı aramak mümkündür. Bu aranan anahtarın iddia edilen kişi veya e-postaya ait olduğunu göstermese de anahtar keşfini kolaylaştırmaktadır. Anahtarı doğrulamak için [güven ağından faydalanmak](/yazisma_guvenligi/wot.md) veya harici kaynaklardan bu anahtarı doğrulamak gereklidir. Bir anahtar sunucunda anahtar aramak için aşağıdaki komutu kullanabilirsiniz.

`gpg --search [anahtar ID veya e-posta]`

Bu GPG yapılandırmanızda belirli olan anahtar sunucusunu kullanacaktır. Kimi zaman [Protonmail anahtar sunucusunda arama yapmak gibi](/yazisma_guvenligi/protonmail.md) belirli bir sunucuda arama yapmak isteyebilirsiniz. Bu durumda `--keyserver` parametresi ile sunucu adresi belirtmeniz gereklidir.

`gpg --search --keyserver [sunucu adresi] [anahtar ID veya e-posta]`

## Sunucuya anahtar gönderme

Bir umumi anahtarı imzaladıktan veya bir değişiklik yaptıktan sonra anahtar sunucusuna göndermek için aşağıdaki komutu kullanabilirsiniz. Anahtar aramasında olduğu gibi belirli bir sunucuya göndermek için `--keyserver` parametresini anahtar sunucusunun adresi ile takip ederek işlem yapabilirsiniz.

`gpg --send-key [anahtar ID veya e-posta]`

## Anahtarları güncelleme

Anahtarlığınızdaki tüm anahtarları, imza değişiklikleri veya iptaller gibi durumlar açısından güncellemek isterseniz aşağıdaki komutu kullanabilirsiniz. Belirli bir anahtar sunucusunu kullanmak için `--keyserver` parametresini kullanabilirsiniz.

`gpg --refresh-keys`

Belirli bir anahtarı güncellemek için aynı komutu bir anahtar belirteci ile çalıştırabilirsiniz.

`gpg --refresh-keys [anahtar ID veya e-posta]`

## Anahtar içe aktarma

Dosya olarak edindiğiniz bir anahtarı anahtarlığınıza eklemek için aşağıdaki komutu kullanabilirsiniz.

`gpg --import < [anahtar dosya yolu]`

ASCII armor şeklinde kopyaladığınız anahtarları bir dosyaya yazmadan doğrudan GPG anahtarlığınıza ekleyebilirsiniz. bunun için basitçe `gpg --import` komutunu çalıştırın `CTRL + ALT + V` ile anahtar metnini yapıştırıp ardından `CTRL + ALT + D` kombinasyonuna iki kere basarak içe aktarma işlemini tamamlayın.

## Anahtar düzenleme

GPG anahtarları üretildikten sonra üzerlerinde çeşitli değişiklikler yapılabilmekte. Bunlar arasında iptal tarihi uzatmaları, imzalamalar, parola değişimleri gibi işlemler bulunmakta. Aşağıdaki komut ile herhangi bir anahtar üzerinde değişiklik yapmak için gerekli menüyü açabilirsiniz.

`gpg --edit-key [anahtar ID veya e-posta]`

Bu komutu çalıştırmanız ardından o anahtara ilişkin anahtara ilişkin bilgiler ve e-posta adresleri çıkacaktır.

```
gpg (GnuPG) 2.2.19; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Secret key is available.

sec  rsa4096/42272957268B3FCA
     created: 2016-10-26  expires: 2021-10-29  usage: C   
     card-no: 0006 08567377
     trust: ultimate      validity: ultimate
ssb  rsa4096/6619345C6DF49077
     created: 2016-10-26  expires: 2021-10-29  usage: E   
     card-no: 0006 10145476
ssb  rsa4096/471A839AB4DD8E6D
     created: 2016-10-26  expires: 2021-10-29  usage: S   
     card-no: 0006 10145476
ssb  rsa4096/B3FFE58F10352423
     created: 2016-10-26  expires: 2021-10-29  usage: A   
     card-no: 0006 10145476
[ultimate] (1). Alper Atmaca <info@alperatmaca.com.tr>
[ultimate] (2)  Alper Atmaca <alperatmaca@riseup.net>
[ultimate] (3)  Alper Atmaca <alperatmaca@gmail.com>
[ultimate] (4)  Alper Atmaca <alper@oyd.org.tr>
[ultimate] (5)  Alper Atmaca (alperatmaca@gmail.com) <alperatmaca@gmail.com>
```

Şayet açılan kabuktan `help` komutunu yazmanız ile kullanabileceğiniz seçenekler listelenecektir.

```
gpg> help
quit        quit this menu
save        save and quit
help        show this help
fpr         show key fingerprint
grip        show the keygrip
list        list key and user IDs
uid         select user ID N
key         select subkey N
check       check signatures
sign        sign selected user IDs [* see below for related commands]
lsign       sign selected user IDs locally
tsign       sign selected user IDs with a trust signature
nrsign      sign selected user IDs with a non-revocable signature
adduid      add a user ID
addphoto    add a photo ID
deluid      delete selected user IDs
addkey      add a subkey
addcardkey  add a key to a smartcard
keytocard   move a key to a smartcard
bkuptocard  move a backup key to a smartcard
delkey      delete selected subkeys
addrevoker  add a revocation key
delsig      delete signatures from the selected user IDs
expire      change the expiration date for the key or selected subkeys
primary     flag the selected user ID as primary
pref        list preferences (expert)
showpref    list preferences (verbose)
setpref     set preference list for the selected user IDs
keyserver   set the preferred keyserver URL for the selected user IDs
notation    set a notation for the selected user IDs
passwd      change the passphrase
trust       change the ownertrust
revsig      revoke signatures on the selected user IDs
revuid      revoke selected user IDs
revkey      revoke key or selected subkeys
enable      enable key
disable     disable key
showphoto   show selected photo IDs
clean       compact unusable user IDs and remove unusable signatures from key
minimize    compact unusable user IDs and remove all signatures from key

* The 'sign' command may be prefixed with an 'l' for local signatures (lsign),
  a 't' for trust signatures (tsign), an 'nr' for non-revocable signatures
  (nrsign), or any combination thereof (ltsign, tnrsign, etc.).
```
Bir anahtar üzerinde işlem yapmak için `key [anahtar numarası]` şeklinde seçim yapabilirsiniz. Benzer şekilde bir e-postaya bağlı kullanıcı kimliği seçmek için de `uid [UID numarası]` komutunu kullanabilirsiniz. Bunu yapmanız üzerine ilgili öğenin yanında `*` işareti çıkacaktır.

`[ultimate] (1)* Alper Atmaca <info@alperatmaca.com.tr>`

```
ssb* rsa4096/6619345C6DF49077
     created: 2016-10-26  expires: 2021-10-29  usage: E 
```

Seçili öğeler üzerinde menüde çıkan işlemleri dilediğiniz gibi gerçekleştirebilirsiniz. Değişiklikleri kaydetmek için `save` komutunu kullanarak işlemi sonlandırabilir veya `quit` komutu ile değişiklikleri kaydetmeden çıkabilirsiniz.

## Anahtar imzalama

Tanıdığınız ve güvendiğiniz bir kişinin anahtarının o kişiye ait olduğunu kanıtlamak için kişinin anahtarını kendi anahtarınız ile imzalayabilirsiniz. Bunu yaptığınızda kişiyi kendi [güven ağınıza](/yazisma_guvenligi/gpg/wot.md) dahil edersiniz. Bu güveni fiilen tanıştığınız ve gerçek kimliğini bildiğiniz kişilere vermeniz kendi güven ağınızdaki diğer kişiler açısından çok önemlidir. Sizin güvendiğiniz kişiye diğer kişiler de otomatik olarak güvenecektir.

Bir kişinin anahtarını imzalamak için aşağıdaki komutu çalıştırıp karşınıza gelen mesajları takip edebilirsiniz.

`gpg --sign-key [anahtar ID veya e-posta]
