# Yazışma Güvenliği

__Yazışma Güvenliği__ mesajlarınızın amaçlanan alıcısına gönderilirken sizin cihazınızda şifrelendiğinden ve sadece alısının okuyabileceğinden emin olmaktır. Her ne kadar [ağ güvenliği](../network_security/README.md) ve [cihaz güvenliği](../device_security/README.md) önemli olsalar da, mesaj şifrelemek çoğu durumda gereklidir:

* __Gizlilik__: Mesajları şifrelemek, mesajın sadece amaçlanan taraflarca okunabileceğinden emin olmanın tek yoludur.
* __Doğrulama__: Mesaj şifrelemek, mesajlaştığınız kişinin kimliğinden emin olmanın tek yoludur.

Mesaj şifrelemek kimi zaman zorlu olabilir:

* __Bir cihaz sahibi olmalısınız__: Mesaj şifrelemenin fikri, mesajlarınızın şifrelenmesi için bir başka üçüncü kişiye güvenmemenizdir. Bu sebeple tüm şifreleme sizin ciahzınızda gerçekleştiğinden bir cihaz sahibi olmanız gereklidir.
* __Meşakatli öğrenme süreci__: Şifreleme yazılımlarını doğru kullanmak için hatrı sayılır bir öğrenme sürecini; açık anahtar, özel anahtar, anahtarlıklar gibi kavramlar için geçirmeniz gerekir.
* __Sınırlı kullanıcı sayısı__: Mesaj şifreleme kullanmak, sadece size aynı yazılımı kullanan kişilerle güvenli iletişim kurabilmeniz anlamına gelir.

Barizdir ki bu tedbirler cihazınızın güvenliği delindiyse bir işe yaramayacaktır.

## Mesaj Şifreleme Hakkında

Bu sayfalarda anılan "mesaj şifreleme" teknik olarak "açık-anahtar kriptografidir" ve şu şekilde çalışmaktadır:

* __Özel anahtar__: Herkes kendi özel anahtarına sahiptir. İsimden anlaşılabileceği gibi, bu anahtar gizli tutulmalıdır. Bu anahtarı size şifrelenen mesajları okumak için kullanırsınız.

* __Açık anahtar__: Herkes bir açık anahtara da sahiptir. Bu anahtar genellikle her yere yayınlanır. Şayet bir kimse size şifreli mesaj göndermek istiyorsa sizin açık anahtarınızı kullanarak mesajını şifreler. Sadece açık anahtarın çifti olan özel anahtara sahip olan kişi mesajı deşifre edebilir.

__Mesaj şifrelemeyi öğrenmek için öneriler__

Her ne kadar en yüksek korumayı sağlasa da, açık anahtar şifreleme kullanmak bir maceradır. Yolculuğunuzu daha az korkutucu kılmak için aşağıdakileri aklınızda tutmanızı öneririz:

* __Kendinizi adamaya hazır olun__: Açık anahtar şifrelemesini kullanmak bir çok yeni yetenek ve jargonu öğrenmeye hevesli olmayı gerektirir. Açık anahtar kullanımının genel kabulüne daha çokça vakit olduğundan bu emeği harcamak fayfasız gibi görünebilir fakat kritik kütleye ulaşmak için bizim gibi erkenden bu işe girenlerin olması gereklidir.

* __Şifreli arkadaşlar edinin__: çoğu iletişiminiz şifreli olmasa bile kendinize açık anahtar şifreleme anternmanı yapabilecğeiniz bir arkadaş bulup kendisi ile güvenli iletişim kurun.

* __Hevesli insanlara takılın__: açık anahtar şifrelemesi kullanan insanlar genellikle bu konuda reklam yapmaya ve diğer insanlara yardım etmeye çok heveslidiler. Sorularınızı cevaplayacak ve size destek olacak böyle birini bulun.

__Şifreli Mesajlaşmanın Sınırları__

Her ne kadar şifreleme ile e-postanızın içeriğini saklayabiliyor olsanız da şifreleme kime veya kimden e-posta aldığınızı *saklamaz* Bu açık anahtar şifrelemesi ile bile pek çok kişisel bilginin güvende olmadığı anlamına gelir.

Neden? Bir kimsenin gönderdiğinzi e-postanın içeriği hakkında hiçbir şey bilmediğini düşünün fakat kiminle e-postalaştığınızı, ne sıklıkla bunu yaptığınızı ve başlıkları biledildiklerini hayal edin. Bu bilgi bağlantılarınız, alışkanlıklarınız, tanıdıklarınız ile ilgi ve etkinlikleriniz hakkında çokça şey söyleyecektir.

İlişkilerinizi gizli tutabilmenin tek yolu buna saygı gösterecek servis sağlayıcılar aracılığı ile iletişim kurmaktır. [[Radikal servis sağlayıcılar litemize->radical-servers]] bu tip hizmet sağlayıcıları incelemek adına göz atabilirsiniz.

## Mesaj Şifreleme Kullanın

* [Şifreli E-Posta](openpgp.md)
* [Kayıt Dışı Mesajlaşma](otr.md)