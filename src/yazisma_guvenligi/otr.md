# Kayıt Dışı Mesajlaşma

## OTR’ye Giriş

[Off-the-Record Mesajlaşma (OTR)](https://en.wikipedia.org/wiki/Off-the-Record_Messaging) mesajlaşmanın baştan sona(end-to-end) şifrelenmesini sağlar. Pek çok özelliği vardır:

* __Şifreleme__ Bütün şifreleme cihazınızda gerçekleşir. Sohbet güvenli olmayan ağlar ve hizmet sağlayıcılar üzerinden yapılsa bile başkaları tarafından okunması engellenir.
* __Doğrulama__ Konuştuğunuz kişilerin iddia ettikleri kişiler olup olmadığını doğrulayabilirsiniz.
* __Perfect forward secrecy (mutlak gizlilik)__ Eğer özel anahtarlarınızın kontrolünü kaybederseniz önceki herhangi bir sohbetiniz ifşa olmaz. 
* __İnkar Edilebilirlik__ Gönderdiğiniz mesajlar sizin tarafınızdan gönderildiğine ilişkin üçüncü kişilerce anlaşılabilecek bir emare taşımaz. Herhangi biri sohbetin bitimi ertesinde mesajları sizden gelmiş gibi gösterebilir. Bununla birlikte, sohbet sırasında sizin iletişimde olduğunuz kişi gördüğü mesajların doğrulanmış ve değiştirilmemiş olduğundan emindir.

## OTR'yi Yükleme

Bu rehberde biz OTR'yi Pidgin ile kullanıyor olacağız. Pidgin, OTR’nin en gelişmiş tatbiki olmakla birlikte GNU Linux, Windows ve Mac üzerinde çalıştırılabilmekte.

### Gnu/Linux

#### Alt+F2’ye basın ve çalıştırın:
`gnome-terminal`
#### Yeni terminal penceresine aşağıdaki satırı kopyalayın ve Enter’a basın:
`sudo apt-get install pidgin-otr`
#### Pidgin’i çalıştırmak için Alt+F2’ye basın ve yazın:
`pidgin`

### Windows

<https://pidgin.im/download> adresini ziyaret edin.

### Mac

Pidgin Mac’te çalıştırılabilir fakat onun yerine Adium kullanmak çok daha kolay. Adium Pidgin’in Mac OS uyumlu hali. [Adium](https://adium.im)'u indir.

## Pidgin’e Hesap Ekleme

Pidgin’e riseup.net hesabı ekleme talimatları için [pidgin tutorial](https://riseup.net/en/chat/clients/pidgin) kullanabilirsiniz.

## OTR kurulumu

Şimdi hem Pidgin ve OTR kurulu olduğuna göre

* Ana pencereden Tools > Plugins’i seçin

* Off-The-Record Messaging eklentisini etkinleştirin ve Configure’a basın

* Listeden riseup.net hesabınızı seçin ve Generate’e basın

* __ÖNEMLİ NOT!__: "Default OTR Settings" altında hem *Require private messaging* hem de *Don’t log OTR conversations* seçeneklerini işaretleyin. Bu seçenekler yalnızca şifrelenmiş sohbetler yapmanızı ve sohbetlerin kaydının tutulmadığını temin eder. Fakat aklınızda olsun ki konuştuğunuz kişinin sohbetin kaydını tutma ihtimali her zaman vardır. Karşınızdaki kişiye sohbetinizin kaydını tutup tutmadığını sormak iyi bir fikir.

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
