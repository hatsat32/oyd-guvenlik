# Yazışma Güvenliği

__Yazışma Güvenliği__Mesajların iletildiği hat üzerinde sunucu dahil kimsenin okuyamamasıdır. Bunun için gönderilecek mesajların cihazları terk etmeden şifrelenmesi gereklidir. [ağ güvenliği](../ag_guvenligi/) ve [cihaz güvenliği](../cihaz_guvenligi/) mesajların mahremiyetini ve güvenliğini bir noktaya kadar sağlasa da uçtan uca şifreleme aşağıdaki özellikleri iletişiminizin güvenliğine ekler:

* __Gizlilik__: Mesajların şifrelenmesi, sadece gönderilmek istenen kişinin bu mesajları okuyabileceğinin garantisidir.
* __Doğrulama__: Mesajların şifrelenmesi ve imzalanması yazışılan kişinin kimliğinden emin olmanın tek yoludur.

Şifreli yazışma yapmak bir miktar emek gerektirmektedir:

* __Bir cihaz sahibi olmalısınız__: Mesaj şifrelemenin temeli, mesajlarınızın şifrelenmesi için bir başka kişiye güvenmemekte yatar. Bu sebeple tüm şifreleme işlemi sizin cihazınızda gerçekleştiğinden, bu işlemi yapmaya yeterli bir cihaz sahibi olmanız gereklidir.
* __Meşakatli öğrenme süreci__: Şifreleme yazılımlarını doğru kullanabilmek için bir miktar deneyim gereklidir. Açık anahtar, özel anahtar, imzalama gibi kavramlara farkındalık sahibi olmanız süreci güvenli yürütebilmeniz için elzemdir.
* __Sınırlı kullanıcı sayısı__: Ne yazık ki herkes şifreli yazışabileceğiniz kişiler bugünlerde görece yaz. Yazılımlardaki gelişme ve güvenlik endişeleri ile bu sayı giderek artsa bile çevrenizdeki insanlara konu hakkında bilgi verip yardım etmeniz gerekebilir.

Mesajlarınızın güvenliğinin cihazınızın güvenliğinden geçtiğini de unutmamalısınız. Dünyanın en ileri şifreleme teknolojileri şifrelemenin yapıldığı cihaz kadar güvenli olabilir. Bu sebepten [cihaz güvenliği](/cihaz_guvenigi/README.md) konusunda dikkat etmelisiniz.


## Mesaj şifreleme hakkında

Bugün iletişim için kullanılan en yaygın şifreleme yöntemi [açık anahtar şifrelemesi veya asimetrik şifrelemedir.](https://en.wikipedia.org/wiki/Public-key_cryptography)

* __Özel anahtar__: Şifreli iletişime taraf olacak herkes bir özel anahtar sahibidir. Bu anahtar isminden de anlaşılacağı üzere gizli kalmalıdır keza şifrelenmiş mesajların açılması ancak bu anahtarla mümkündür. Bu anahtar aynı zamanda kişilerin kimliklerini ve mesajlarının doğruluğunu kanıtlamak için yapacakları imzalama işlemini de sağlar.

* __Açık anahtar__: Her özel anahtar bir açık anahtar içerir. Açık anahtar bir mesajın sadece şifrelenmesini sağlar fakat şifreyi çözemez. Açık anahtar ile şifrelenen bir veri ancak özel anahtar ile açılabilir. Bu tek yönlü ilişki sayesinde açık anahtar ile herkes özel anahtarın sahibine başkaca bir bilgiye gerek olmadan şifreleme yapabilir. Açık anahtar bu sebepten anahtar sunucularında, e-posta eklerinde yayınlanır.

Asimetrik şifreleme pek çok sistemde kullanılmakla en yaygın ve bilinen uygulaması [GnuPG](openpgp.md) ile şifreli e-posta yazışmasıdır. GPG kendini kanıtlamış çok amaçlı bir yazılım olarak pek çok amaçla şifreleme yapmak için kullanılabilir.

GnuPG gibi yazılımlar kullanıcıların anahtarlarını yönetmesini gerektirse bile günümüzde pek çok yazılım bu gerekliliği ortadan kaldırmakta. Özellikle [anlık yazışma](anlik_yazisma.md) yazılımları kullanıcılarına basit arayüzler aracılığı ile görece kolay şifreleme imkanları sunmaktadır. Arkaplanda çalışan kriptografi açık/özel anahtar ikilisine dayalı olsa da kullanıcıların bu anahtarlarla hiçbir ilgileri olmamaktadır. Bu durum kimi taraflarca güvenli yazışmayı kolaylaştırdığı için övülmekte kimileri tarafından ise kullanıcıları bilgiden yalıtarak özel sistemlere mahkum ettiği iddia edilmektedir.


### Şifreli yazışmaya giriş yapmak için öneriler

Şifreleme teknolojileri çağdaş yaşamın en güvenli iletişim imkanlarını sağlayacak olsa da kimi zaman zorluklar ve anlaşılmazlıklar da getirebilmektedir. Şayet güvenliğinizi şifreleme teknolojileri ile sağlamaya hazırlanıyorsanız aşağıdaki önerilerimizi aklınızda tutmanızı dileriz:

* __Kendinizi adamaya hazır olun__: Şifreleme teknolojileri, pek çok insan için hiç duyulmamış terimler ve becerileri de yanında getirmektedir. Şayet kullanıcısına kolaylık(!) sunan bir yazılım kullanmıyorsanız bu jargon ve becerileri de elde etmeniz gerekecektir. Hali ile okumaya ve öğrenmeye zaman ve emek ayırmaya hazır olmalısınız. Aynı zamanda edindiğiniz deneyimi çevrenizle paylaşıp başkaca insanların güvenlik süreçlerini kolaylaştırabilirsiniz.

* __Şifreli arkadaşlar edinin__: Komik gelse de çoğu zaman şifreli iletişim yapmanın en zor tarafı konuşacak birini bulmaktır. Günümüzde şifreli iletişim teknolojileri yaygınlık kazansa da hala [özür olmayan yazılımlar](https://oyd.org.tr/yazilar/ozgur-yazilim/) kullananlar çoğunlukta. Bu sebepten çevrenize yardım ederek sizinle ve başkaları ile güvenli yazışmalarını sağlamak zorunda kalabilirsiniz.

* __Hevesli insanlara takılın__: Şifreleme ve güvenli iletişim konusunda zaman ve emek harcamış insanlar genel olarak deneyimlerini paylaşmak konusunda heveslidir. Şayet aklınıza takılan sorular var ise veya insanlara yardım etme isteği taşıyorsanız çevrenizde bu konuda çalışma yapmakta olan topluluk veya insanlarla temasa geçin. Size zevkle yardımcı olacaklardır.


### Şifreli mesajlaşmanın sınırları

Şifreleme her ne kadar e-postalarınızın, mesajlarınızın içeriğini saklayabiliyor olsa da [üstveri](https://en.wikipedia.org/wiki/Metadata) **bu korumanın kapsamına girmez.** Üstveri kimin kiminle yazıştığını, ne zaman yazıştığını ağ üzerindeki diğer kişilere açık edebilir. Bunu mektubunuzun üstüne adres yazmak zorunda olmanızla kıyaslayabilirsiniz. Bu sebepten şifrelemenin her soruna çözüm olmadığına dikkat etmelisiniz.

Kimin kiminle yazıştığının bilinmesinin neden önemli olduğunu merak edebilirsiniz. İnsanlar ve ilişkileri hakkında bilgi toplamak için her zaman mesajların içeriğine ulaşılması gerekmeyebilir. Bu bakımdan sadece kimin kiminle, ne sıklıkla yazıştığı hakkında toplanan veri herkesin sosyal çevresini ve kişilerin birbirine olan önemini ortaya koyacaktır. Buradan hareketleriniz, sosyal yaşantınızdaki değişiklikler gibi çokça önemli bilgi mesajlarınızın içeriği okunmadan dahi elde edilebilir. ABD istihbarat teşkilatının eski bir başkanı, insanları üstveriye bağlı olarak öldürdüklerine dair bir açıklama bile yapmıştır.

Bu bakımdan ilişkilerinizi gizli tutabilmek önemlidir. Bunun için size ve iletişiminizin mahremiyetine saygı gösteren hizmet sağlayıcılardan hizmet alabilir veya temel iletişim imkanlarınızı sağlayacak sunucuları kendiniz işletebilirsiniz. Rehberimizde konuya ilişkin pek çok yardımcı kaynak bulabilirsiniz.


## Yazışma güvenliğine giriş yapın

* [Şifreli E-Posta](openpgp.md)
* [OTR](otr.md)
* [OMEMO](omemo.md)
* [Signal](signal.md)
