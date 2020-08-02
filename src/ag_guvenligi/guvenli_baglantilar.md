# DEPRECATED: Güvenli Bağlantılar

## Güvenli bağlantılar nelerdir?

Riseup servislerini kullanırken şifreleme kullanıyor olmalısınız. Güvenli bağlantıları kullanmazsanız internet trafiğiniz şifrelenmemiş olur. Bu, e-postanızı gözlemek hatta daha kötüsü giriş bilgilerinizi elde etmek veya bizim sunucularımızı taklit etmek isteyen herhangi biri tarafından erişilebilir olması anlamına gelir. Riseup'a güvenli bir bağlantı kurmak gözetlemecilere ve taklitçilere karşı makul bir koruma sağlar.

## Güvenli bağlantı nasıl kullanılır?

Posta istemcinizi güvenli bağlantı ile kullanmak için yapmanız gereken bir takım kurulum ayarları bulunmakta. Endişelenmeyin, birlikte yapacağız.

Eğer Thunderbird kullanıyorsanız, ayarlarınızı kontrol etmek üzere aşağıdaki adımları atlayarak [thunderbird bölümü](#thunderbird)'ne gidebilirsiniz. Eğer farklı bir posta istemcisi kullanıyorsanız lütfen [genel ayarlar bölümü](#genel-ayarlar)'nü okuyun. Eğer posta istemcisinin ne olduğuyla ilgili hiçbir fikriniz yoksa, bir sonraki bölümü okuyun ve size öğretelim.

## Posta istemcisi nedir?

Posta istemcisi nedir? Posta istemcisi e-posta oluşturmak ve e-postalarınızı okumak için özelleşmiş programa denir. Bu program Thunderbird, Apple Mail, Outlook, Eudora vb. olabilir. E-postalarınızı okumak ve yazmak için kullandığınız hangisi ise o sizin e-posta istemcinizdir.

## Genel Ayarlar

Normal koşullarda, posta istemciniz için gerekli kurulum ayarlarını araştırmanız ve programın bütün bağlantılarda(POP veya IMAP ile SMTP için) SSL veya TLS kullanmaya ayarlı olduğundan ve ayrıca doğru portu kullanıyor olduğunuzdan emin olun. Eğer bunların ne anlama geldiğini bilmiyorsanız endişelenmeyin, biz buradayız.

Bunu yapmak için belirli prosedür her posta istemcisi için epey farklı ve hatta bazen aynı yazılımın farklı sürümleri için bile çok farklı olabiliyor.

Genellikle biz posta istemcileri için destek sunmuyoruz. Gelgelelim, [posta istemcilerinini kurma ile ilgili biraz bilgi](https://riseup.net/en/email/clients) sahibiyiz. Eğer istemciniz listedeyse oradaki bilgi gerekli değişiklikleri yapmanıza yardımcı olacaktır.

Eğer Mozilla'nın Thunderbird'ünü kullanmıyorsanız, istemcinizi onunla değiştirmeyi düşünmeniz için ısrar ediyoruz. Thunderbird makul derecede güvenli, kullanımı kolay bir özgür yazılım projesi. Denemekten zarar gelmez! [Thunderbird kurulumu için talimatlarımız](https://riseup.net/en/email/clients/thunderbird) are really good, its what we know best and can support you much easier if you use it.

Eğer Thunderbird'e geçmek istemiyorsanız, bu değişikliklerin nasıl yapılacağına aşina değilseniz ve bizim yardım sayfalayarımız faydalı olmadıysa, gerekli kurulum değişikliklerini yapmak üzere kendi çevrenizden bu tip işlerden anlayan birini aramanız veya kullandığınız yazılımın topluluğuna başvurmanız gerekmekte.


## Thunderbird

Thunderbird'de gerekli değişiklikleri yapmak üzere aşağıdaki adımları izleyin:

İlk olarak Thunderbird'ün hangi sürümünü kullandığınızı anlamak için "Help" menüsünden "About Thunderbird"e tıklayın

Kullandığınız sürümün numarasını öğrendiğinizde aşağıdaki aşamalardan sizin sürümünüzle eşleşeni izleyin. Eğer kullandığınız Thunderbird'ün sürümü 2.x veya daha eskiyse sürümü yükseltmeniz gerekmekte. Maalesef bunun nasıl yapıldığını burada anlatamayacağız ancak "Thunderbird'ün sürümünü yükseltme" diyerek çevrimiçi arama yaptığınızda gerekli bilgiyi bulabilirsiniz.

### Thunderbird 3.x ve daha yeni sürümler

Thunderbird sürüm 3.x'de güvenli bağlantıları etkinleştirmek üzere gerekli değişiklikleri yapmak için lütfen aşağıdaki adımları izleyin:

* "Edit" menüsünden "Account Settings"i seçin
* Hesap ayarları iletişim kutusu açıldıktan sonra riseup hesabınız için "Server Settings"i seçin
* Kutunun ortasında "Security Settings" yazan bir başlık göreceksiniz
* Başığın altında "Connection Security" ile etiketlenmiş bir açılan menü bulunmakta
* Açılan menü SSL/TLS'i ayarlamak için kurulu olmalı
* İletişim kutusunun sağ üst köşesinde "Port" yazan bir ayar bulunmakta
* Bu ayar otomatik olarak yapılmış olmalı ama emin olmak için kontrol et
  * Eğer IMAP kullanıyorsan Port numarası 993 olmalı
  * POP kullanıyorsan port numarası 995 olmalı
* Eğer IMAP veya POP kullanıyorsan "Server Settings" iletişim kutusunun en üst satırında "Server Type" satırı bulunur.
* Bir sonraki aşamada sol panelde "Outgoing Server (SMTP)" başlığına tıklayın
* Bir kere sağ panelde bulunan riseup SMTP sunucusuna tıklayın
* Uzak sağ köşedeki iletişim kutusunda "Edit" seçeneğine tıklayın
* "Connection Security" seçeneğini SSL/TLS'e ayarlayın
* "Port" ayarının 465'e ayarlı olduğundan emin olun
* "Ok" tıklayın
* Bir daha "Ok" tıklayın
* Herhangi bir noktada "Authentication Method" ayarını değiştirmemelisiniz - ayar her zaman "Normal Password" olmalı
* Heyo! Bu işi de atlattınız!!!

## iOS

Eğer bunun gibi bir apple cihazınız var ise nasıl güvenli şekilde ayarlarınızı değiştirebileceğinizle ilgili [talimatlarımızı](https://riseup.net/en/email/clients/ios-mail) inceleyebilirsiniz.

## SSS

S: Eğer webmail kullanırsam, güvenli olur mu?

C: Web'i kullandığınızda, bağlantınızı bilgisayarınızdan İnternetteki çeşitli sunucular aracılığı ile ziyaret etmeye çalıştığınız sayfanın web sunucusuna yaparsınız. Bu bağlantıyı "HTTP" diye anılan bir şey ile yaparsınız. Bu bağlantıda gönderdiğiniz veriler açıktan gider ve güvenli değildir. Saldırganlar, web sitesi hesaplarınıza ve ziyaretiniz sırasında gönderdiğiniz veya aldığınız tüm bilgilere ulaşabilirler. Ama umut bitmez! "HTTP"'nin bir "HTTPS" (sonundaki 'S' güvenli anlamında) adında güvenli bir versiyonu vardır. HTTPS saldırılara dayanabilecek şekilde güvenli bağlantılar kurmak üzere tasarlanmıştır.

Daha fazla güvenlik için ziyaret etmek istediğiniz web sayfasının ziyaret etmeye niyetlendiğiniz web sayfası olduğunu doğrulayabilirsiniz. HTTPS kullanırken, ziyaret ettiğiniz sunucunun doğru sunucu olduğunu göstermeye yarayacak bir sertifika size ulaşır. Sitenin ziyaret etmek istediğiniz site olduğunu doğrulamak için [[size sunulan sertifikayı doğrulamalısınız->/certificates]].

Sertifikalar ile ilgili farkında olmanız gereken bazı hususlar vardır (Güvenli bağlantıların sınırları hakkında aşağıdakileri inceleyin).

Adres çubuğunda adresin başına bakın. Eğer <code>https://</code> (‘s’e dikkat) ile başlıyor ise güvenli bir bağlantınız var demektir. Şayet sadece <code>http://</code> (‘s’ Yok) var ise güvenli bir bağlantı kurulmamıştır. Adres çubuğunda adresteki "http"yi "https"ye 's' ekleyerek çevirerip git derseniz sayfayı güvenli olarak tekrar yükleyebilirsiniz.

Üçücü ve daha az güvenilir bir yol olarak küçük asmakilit simgesine bakmaktır. Simge ya adres çubuğunda ya da pencerenin alt köşesinde (kullanılan tarayıcıya göre konum değişebilir) görünecektir. Simge kilitli görünmelidir. Eğer asmakilit yoksa veya kilitli görünmüyorsa güvenli bir bağlantı kullanmıyorsunuz demektir. Farenizi simgenin üstüne getirerek daha fazla bilgi alabilir veya tıklayarak (bazen sağ tık) güvenli bağlantı için kullanılan sertifika hakkında detaylı bilgileri ortaya çıkaracaktır.

S: POP/IMAP & SMTP Nedir?

C: POP ve IMAP yazılımlar tarafından e-posta sunucusundan e-postaların okunması için kullanılan yaygın protokollerdir. Genellikle bu protokollerden aynı anda sadece birini kullanırsınız. SMTP bir başka e-posta aktarım protokolüdür fakat bu bilgisayarınızdan e-posta sunucusuna e-posta göndermek için kullanılır.

S: Eğer e-posta istemcimi kendim ayarlıyorsam hangi portları kullanmalıyım?

C: TLS kullanan POP bağlantıları için 995 numaralı portu kullanın.
   TLS kullanan IMAP bağlantıları için 993 numaralı portu kullanın.
   TLS kullanan SMTP bağlantıları için 465 numaralı portu kullanın.

S: Ya güvenli e-posta kullanımı ile ilgili daha fazla sorum varsa?

C: Eğer detaylıca [riseup yardım sayfalarını](https://support.riseup.net) incelediyseniz ve hala sorularınız var ise sizi [riseup yardım talebi](https://support.riseup.net/en/topics/new) aracılığı ile sormaya davet ederiz. Kullanıcılarımıza iletişimlerini nasıl daha güvenli kıldığımızı ve tüm İnternet kullanıcılarının mahremiyetini nasıl arttırdığımızı anlatmaktan memnuniyet duyarız.

## Güvenli bağlantıların sınırları

Artık güvenli bağlantılar kullandığınıza göre her şey tamamen güvenli değil mi? Ne yazık ki hayır! Güvenli bağlantılar sadece verinin iletimini güvenli kılar, verinin mahremiyetini sağlamaz. Örneğin; güvenli bağlantılar aracılığı ile e-posta gönderdiğinizde, e-postanız sunucularımızdan şifreli olarak gönderilir fakat İnternette e-postazın hedefine ulaşmadan önce atlayacağı çokça başka basamak vardır. Bu basamaklar nadiren şifrelidir ve bu bir kimseye hem İnternette iletimi sırasında hem sunucuda beklerken hem de alıcının bilgisayarında e-postalarınıza erişmek için sayısız fırsat verir. Güvenli bağlantılar kullanmak gerçeklikte sadece kullanıcı adı ve parolalarınızın korunmasına yarar.

E-posta iletişiminizi daha güvenli kılmak için başka neler yapabilirsiniz? Eğer e-postalarınızı uçtan uca güvenli kılmak istiyorsanız [GnuPG gibi güçlü şifreleme araçlarını](../yazisma_guvenligi/openpgp.md) kullanmaya başlamanız ve insanların sizinle bu araçlarla iletişim kurmasını sağlamalısınız. [Thunderbird için Enigmail](../yazisma_guvenligi/openpgp.md#webmail-kullanarak-e-posta-şifrelenebilir-mi) isminde, güçlü şifreleme imkanlarını kolaylıkla kullanımını sağlayan bir eklenti vardır.

Web'de güvenlik HTTPS'nin etrafında gönmektedir ve bu belirli bir sertifikanın sunucu için "geçerli" sayılıp sayılmayacağının web tarayıcısı tarafından belirlenmesini gerektirir. Bu şu anda tarayınız tarafından dağıtılan "güvenilir" sertifika otoriteleri listesi aracılığı ile olur. Bu baya tırt bir şey çünkü sizi bir kullanıcı olarak bir çeşit merkezi otoriteye bağlantı güvenliğinizi onaylaması için güvenmenizi gerektirir. Neden bir takım kendini yetkilendirmiş otoriteye güvenli bağlantılarınızda pay vermek isteyesiniz? Neden bunun tırt olduğuna ilişkin daha fazla bilgi isterseniz [sosyal yapılarımızı şekillendiren teknik mimari](https://lair.fifthhorseman.net/~dkg/tls-centralization/) hakkındaki makaleyi okumalı ve bu merkezileşmiş hiyerarşinin neden çok sorunlu olduğuna şahit olmalısınız.
