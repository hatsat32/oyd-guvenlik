# OTR (Off-The-Record Messaging)

## OTR’ye Giriş

[Off-the-Record Mesajlaşma (OTR)](https://en.wikipedia.org/wiki/Off-the-Record_Messaging) mesajlaşmanın baştan sona(end-to-end) şifrelenmesini sağlar. Pek çok özelliği vardır:

* __Şifreleme__ Bütün şifreleme cihazınızda gerçekleşir. Sohbet güvenli olmayan ağlar ve hizmet sağlayıcılar üzerinden yapılsa bile başkaları tarafından okunması engellenir.
* __Doğrulama__ Konuştuğunuz kişilerin iddia ettikleri kişiler olup olmadığını doğrulayabilirsiniz.
* __Perfect forward secrecy (mutlak gizlilik)__ Eğer özel anahtarlarınızın kontrolünü kaybederseniz önceki herhangi bir sohbetiniz ifşa olmaz. 
* __İnkar Edilebilirlik__ Gönderdiğiniz mesajlar sizin tarafınızdan gönderildiğine ilişkin üçüncü kişilerce anlaşılabilecek bir emare taşımaz. Herhangi biri sohbetin bitimi ertesinde mesajları sizden gelmiş gibi gösterebilir. Bununla birlikte, sohbet sırasında sizin iletişimde olduğunuz kişi gördüğü mesajların doğrulanmış ve değiştirilmemiş olduğundan emindir.

## OTR'yi Yükleme

### GNU/Linux

#### Alt+F2’ye basın ve çalıştırın:
`gnome-terminal`
#### Yeni terminal penceresine aşağıdaki satırı kopyalayın ve Enter’a basın:
`sudo apt-get install pidgin-otr`
#### Pidgin’i çalıştırmak için Alt+F2’ye basın ve yazın:
`pidgin`

### Android

[F-droid](https://f-droid.org/) veya bir başka kaynaktan [Conversations Legacy](https://conversations.im/) indirin. Conversations Legacy'nin Pix-art gibi başka forkları da olmasına rağmen özellikle onları tercih etmenizi gerektirecek bir sebep olmadıkça Conversations en iyi tercih olacaktır.

### Windows

<https://pidgin.im/download> adresini ziyaret edin.

### Mac

Pidgin Mac’te çalıştırılabilir fakat onun yerine Adium kullanmak çok daha kolay. Adium Pidgin’in Mac OS uyumlu hali. [Adium](https://adium.im)'u indir.

## Hesabınıza giriş yapın veya yeni hesap oluşturun

Şayet bir sunucuda XMPP hesabınız var ise kullanıcı adı ve parolasını girerek bağlantı sağlayabilirsiniz. Şayet bir XMPP hesabınız yok ise bu aşamada kayıt imkanı veren bir sunucuda hesap açabilirsiniz. Tek yapmanız gereken kendinize bir

Aşağıdaki sunucuları tercihinizde değerlendirebilirsiniz;

[Calyx Institute](https://www.calyxinstitute.org/) - Çok geniş XMPP kullanıcı kitlesine hizmet veren bir Dernek. Sayısal haklar alanında çalışmalar sürdüren derneğin XMPP sunucusu anonim kayıt kabul ediyor.
Kayıt için (kullanıcı adı)@jabber.calyxinstitute.org alan adı kullanılabilir.

[Conversations](https://conversations.im/#xmpp) - Conversations yazılımının kendi sunucusu. Şayet özgür yazılıma destek olunmak istiyorsanız ücretli bu hizmeti tercih edebilirsiniz. İlk altı ay ücretsiz kullanım imkanı vermekte.

[Riseup](https://www.riseup.net) - Riseup teknoloji kolektifinin ücretsiz hizmetlerinden biri de XMPP. Doğrudan kayıt imkanı vermediği için bir Riseup hesabı sahibi olmanızı gerektiriyor.


## OTR kurulumu

Şimdi hem Pidgin ve OTR kurulu olduğuna göre

* Ana pencereden Tools > Plugins’i seçin

* Off-The-Record Messaging eklentisini etkinleştirin ve Configure’a basın

* Listeden XMPP hesabınızı seçin ve Generate’e basın

* __ÖNEMLİ NOT!__: "Default OTR Settings" altında hem *Require private messaging* hem de *Don’t log OTR conversations* seçeneklerini işaretleyin. Bu seçenekler yalnızca şifrelenmiş sohbetler yapmanızı ve sohbetlerin kaydının tutulmadığını temin eder. Fakat aklınızda olsun ki konuştuğunuz kişinin sohbetin kaydını tutma ihtimali her zaman vardır. Karşınızdaki kişiye sohbetinizin kaydını tutup tutmadığını sormak iyi bir fikisr.

## Rehbere Arkadaş Ekleme

* Arkadaş eklemek için, ana Pidgin penceresinden Buddies > Add Buddy’i seçin.

* Kendi hesabınızı seçtiğinizden ve doldururken arkadaşınızın kullanıcı adını doğru yazdığınızdan emin olun. Arkadaşlarınızı kategorize etmek üzere grup oluşturma seçeneğiniz bulunmakta.

* Add’e tıklayın.

* Arkadaşlarınız eklendiğinde sohbet etmeye uygun bir şekilde ana Pidgin penceresinde görünecekler. Sohbeti başlatmak için listeden arkadaşınızın kullanıcı adına çift tıklayabilirsiniz.

## Arkadaşları Doğrulama

Start private conversation’a tıklayın ve gizli sohbetiniz için birbinizi doğrulamak adına talimatları izleyin. Birini doğrulamanın en kolay yolu kişiye sadece onun cevaplayabileceği bir soru sorduğunuz Soru Cevap yöntemidir. Bu, konuştuğunuz kişinin konuştuğunuzu sandığınız kişi olduğunu onaylama adına önemli bir güvenlik adımıdır. Kabul edilebilir sorulara örnekler:

> S: Dün gece Hilmi’lerde seninle ne hakkında konuştuk? (küçük harf, iki kelime)
>
> C: kaynak makinesi

Yukarıdaki konuşmada bahsedilen anda yalnızca iki kişinin bulunması sorulan soruyu güvenli kılıyor.

> S: Yatak odamın duvarındaki afişi kim tasarladı? (küçük harf, üç kelime)
>
> C: arı kovanı kolektifi

Bu da yatak odanıza aldığınız kişilere güvendiğinizi farzeden güvenli bir soru.

"Saçımın rengi ne?" veya "Köpeğimin adı ne?" gibi sorular güvenli sayılmaz çünkü herhangi biri bu soruların cevaplarını kolaylıkla tahmin edebilir.
