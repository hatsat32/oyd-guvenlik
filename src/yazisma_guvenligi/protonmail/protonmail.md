# Protonmail ile GPG Kullanımı

## Protonmail Nedir?

[Protonmail](https://protonmail.com) şifreli bir e-posta hizmetidir. Güvenlik rehberinin detaylıca incelediği şifreli e-posta hizmet sağlayıcıları arasında Protonmail'i ayıran özellik GPG şifrelemenin hizmetin temelinde olmasıdır. Bu Protonmail kullanıcılarının Protonmail dışındak diğer e-posta adreslerine GPG şifreli e-posta atabilmelerini ve diğer e-posta adreslerinden GPG şifreli e-posta alıp tarayıcıdan okuyabilmelerine imkan veriyor. Bu bakımdan Protonmail kullanıcıları uçtan uca şifrelemeye sadece Protonmail kullanıcıları arasında değil tüm GPG kullanıcıları arasında sahip oluyorlar.

Protonmail kullanmak elde edebileceğiniz en güvenli GPG kurulumu değildir. Protonmail'e her girdiğinizde tarayıcınıza gelen javascript kodunu doğrulamanız mümkün değildir. Protonmail'in istemcileri de ne yazık ki hala özgür değil. Bunun tek istisnası smtp ile Protonmail hesabınıza bağlanmanızı sağlayan [köprü(bridge)](https://protonmail.com/bridge) yazılımı. Her ne kadar Protonmail size yukarıdaki gerekçeler ile en iyi sonucu vermeyecek de olsa, pek çok Protonmail kullanıcısı ile çokça tehdit modeline yeterli güvenli yazışma yapmak ve gerekirse diğer GPG kullanıcıları ile yazışmanız çok kolay. Karar size kalmış.

## Protonmail'e GPG ile E-posta Atmak

GPG şifrelemesi yapmak için ilk gereken şey yazışacağınız Protonmail adresine ait anahtarı elde etmek. Bunun için;

* Yazıştığınız kişiden anahtarını e-posta ekine koymasını isteyebilirsiniz. Bu durumda gelen anahtarı import edip hiç sorun çekmeden kullanmaya başlayabilirsiniz.

* E-posta şifreli ise arkanıza yaslanıp şifreli cevap verebilirsiniz. Keza Enigmail otomatik olarak şifreli gelen e-postanın anahtarını bulacaktır.

* Protonmail anahtar sunucusundan ilgili anahtarı çekebilirsiniz.

### Protonmail Anahtar Sunucusundan Anahtar Çekmek

Anahtar sunucuları GPG kullanımının temel araçlarından biri. Bir firhist olan bu sunuculardan Protonmail'de sadece kendi anahtarlarını içerecek şekilde bir tane bulunduruyor. Protonmail'in sunucusu diğer sunucularla eşitlenmediğinden sadece bu sunucuya tam Protonmail adresi ile istek atarak cevap almanız mümkün.

Uçbirimde:

`gpg --search --keyserver hkps://api.protonmail.ch [aradığınız adres]`

şeklinde arama yapabilirsiniz. Adresi doğru girdi iseniz bir tane anahtar size önerilecektir. 1'e basıp ilgili anahtarı indirebilirsiniz.

Şayet Thunderbird/Enigmail ikilisini kullanacaksanız birden fazla imkanınız bulunuyor. Bunlardan ilki, özellikle Protonmail adresleri ile sıkça yazışacaksanız, Protonmail anahtarsunucusunu Enigmail'in ayarlarından anahtar sunucuları listesine eklemektir. Bunu yapmanın güzel tarafı Enigmail şayet anahtarını bilmediği bir Protonmail adresi görür ise bunun anahtarını otomatik olarak indirip şifreleme seçeneğini açacaktır.

![alt-text](enigmail_ayarlar.png "Enigmail ayarlarına Protonail sunucunu eklemek")

Şayet e-posta yazma ekranında hızlıca bunu yapmaya karar verirseniz, Enigmail sekmesinden anahtar yönetimi (key management) kısmına tıklayıp anahtar sunucusu (keyserver) kısmına Protonmail'in sunucu adresini girip doğrudan arama yapma seçeneğini seçebilirsiniz.

![alt-text](enigmail_yonetim.png "Enigmail anahtar yönetimi")

Şayet e-postanızı göndermeden önce şifreleme seçeneğini açarsanız, Enigmail anahtarı olmayan Protonmail adresinin anahtarını göstermenizi sizden isteyecektir. Bu noktada eksik anahtarları indir (download missing keys) seçeneğini tıklayıp anahtar yönetimi sayfasından bir üstteki adımı takip ederek işleminizi bitirebilirsiniz.

![alt-text](enigmail_gonderim.png "Enigmail eksik anahtar paneli")

Tebrikler, bir Protonmail kullanıcısına tek seçeneklerinin Protonmail olmadığını göstermiş oldunuz. Protonmail'e atacağınız e-postaların ekine açık anahtarınızı eklemeniz veya e-postayı şifreli atmanız durumunda Protonmail sadece **web** istemcisinden otomatik olarak şifreli yanıt atacaktır. Android ve OS istemcilerde sorun çıktığı görülmüştür. Hali ile yazıştığınız kişiyi bu konuda bilgilendirmeniz önerilir. Sizin açık anahtarınızı Protonmail hesaplarında sizin adınıza eklemeleri gereklidir sorunsuz bir iletişim için.

## Protonmail'den Diğer Adreslere GPG Şifreli E-posta Atmak

Protonmail'den GPG kullanan bir başka adrese şifreli e-posta atmak için öncelikli olarak ilgili e-postanın açık anahtarını yazışmak istediğiniz kişinin adına rehberinize eklemeniz gerekli.

Şayet GPG kullanan kişi size ilk mesajı şifreli veya imzalı attıysa "Bu ileti, henüz güvenilmeyen bir genel anahtar tarafından imzalanmıştır." ibaresi çıkacak ve yanında güven anahtarı düğmesi olacaktır. Bu özetle kişinin anahtarını kendi anahtarınızla imzalamanız ve otomatik olarak kişinin açık anahtarının adına eklenmesi ile gelecek yazışmaları otomatik olarak GPG şifreli yapacaktır.

Şayet gelen e-posta şifreli veya imzalı değilse ya da siz ilk şifreli e-postayı atacaksanız öncelikle rehberinizden şifreleme yapmak istediğiniz kişinin paneline gelin ve küçük dişli şekliyle ifade edilen gelişmiş ayarları açın.

![alt-text](proton_kisi.png)

Daha sonra açılan ayarlardan anahtar yükle seçeneğini seçerek ilgili kişinin anahtar dosyasını yükleyin ve şifrele düğmesini aktif hale getirin.

![alt-txt](proton_kisi_ayar.png)

Bundan sonra kişiye atacağınız e-postalar kişinin GPG anahtarı ile şifrelenecektir.
