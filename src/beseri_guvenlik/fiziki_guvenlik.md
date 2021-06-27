# Fiziki Güvenlik

<!-- toc -->

Bir cihazın güvenliği sadece yazılımsal değil aynı zamanda donanımsal koşullara da bağlıdır. Teknik olarak cihazınıza uzaktan gelebilecek tehlikelere karşı tedbir alsanız bile cihazınıza fiziki erişimi olan bir saldırganın, çok daha etkili ve görünmez saldırılarına maruz kalmanız işten bile değildir. Bu tip saldırılara karşı alınabilecek tedbirler yine fiziki olmaktadır.

Fiziki erişimi ile gerçekleştirilebilecek saldırılar, basit bir web araması ile elde öğrenilebileceklerden ulus devlet seviyesinde kaynakları gerektiren yöntemlere uzanmaktadır. Bu bakımdan fiziki erişim ile yapılabilecek saldırılar sadece filmlerde görülebilecek cinsten zorlukta değildir.

Fiziki saldırılara karşı alınabilecek tedbirler hem teknik hem de beşeri olmaktadır. Basit davranış değişiklikleri ile cihazlarınızın fiziki güvenliğini çok daha iyi hale getirebilir, teknik tedbirlerle cihazlarınızı çok daha zorlu hedefler kılabilirsiniz.

## Cihazlarınızı yanınızdan ayırmayın

Cihazlarınıza kimsenin dokunmadığından emin olmanın en ucuz ve en kesin yolu cihazlarınızdan gözünüzü ayırmamaktır. Her ne kadar basit bir tavsiye gibi görünse de cihazlarımızı terk ettiğimiz zamanlar değerlendirildiğinde pek çok kişinin dikkat etmesi gerektiği ortaya çıkacaktır.

Elbette tüm cihazlarınızı **sürekli** üzerinizde taşımak tehdit modelinize bağlı olarak anlamlı olabileceği gibi gereksiz bir yük de yaratabilir. Bu bakımdan iki koşulun değerlendirilmesinin önemi ortaya çıkmaktadır.

* Cihazlarınızı bıraktığınız/kullandığınız ortamın fiziki güvenliği

* Cihazlarınızın müdahaleye dayanıklılığı

Bu iki koşulu size tehlike oluşturabilecek saldırıların imkanları ile kıyaslayarak anlamlı bir modelleme yapmanız mümkündür. Şayet cihazınızı pek de tanımadığınız insanlarla birlikte çalıştığınız işyerinizde bırakıyorsanız cihazlarınız için pek çok yönden endişe edebilirsiniz. Söz konusu alan kamera ile izleniyor ve görüntüleri tutan kişilere güvenebilirseniz riskiniz azalabilir. Evinizde bıraktığınız bilgisayarınız görece daha güvende olacaktır. Şayet evinizi veya bilgisayarınızı koruyacak bir alarm sisteminiz varsa daha az risk içinde sayılırsınız.

İçinde bulunduğunuz durumun maddi koşulları ile cihazlarınızı terk ettiğiniz alanların koşullarının bir kıyaslamasının her an yapılması gerekli. Bu konu hakkında **Evil Maid** kavramı altındaki yaklaşımları inceleyebilirsiniz.

## Cihazlarınızı gözetim altında tutun

Şayet cihazlarınızı taşıyamıyor veya taşımak istemiyorsanız, cihazlarınızı sürekli gözetim altında bulundurmayı değerlendirebilirsiniz. Bu cihazlarınıza yapılacak bir müdahaleyi engellemeyecek olsa da saldırganı caydırabilir, sizden habersiz müdahale edemeyecek olduğundan dolayı saldırının anlamını yitirmesine neden olabilir veya durumun farkında olmayan bir saldırganı kayıt altına alabilir. Her halükarda kayıt sisteminizin de güvenliğini düşünmeniz ve gözetim sisteminizin sizi olası durumlarda uyaracağından ve kayıtlara kolayca müdahale edilemeyeceğinden emin olmanız gerekir. Şayet hiç bakmadığınız veya baktığınızda silinmiş bir kamera kaydı bir girişimi kaydetse bile çok işinize yaramayacaktır.

Bu amaçla tasarlanmış ilginç projelerden biri olarak [Guardian Project](https://guardianproject.info/) tarafından geliştirilen [Haven](https://github.com/guardianproject/haven/releases) dikkate değerdir. Bir android telefonu güvenli bir gözetim aracına çevirmeye yarayan Haven, cihazın sensörleri ve kamerası ile izlediği alandaki değişiklikleri kaydedip kullanıcısına Signal ve TOR üzerinden haber verebilmekte.

## Cihazlarınızı girişimlere dayanıklı hale getirin

Cihazlarınızı fiziki müdahalelere karşı dayanıklı hale getirmek hem donanımsal/yazılımsal tedbirleri hem de cihazınıza yapılan müdahaleleri ortaya çıkaracak fiziki tedbirleri kapsamaktadır.

### Yazılımsal/Donanımsal tedbirler

Cihazınızın /boot sektörünü ve tüm açılış aşamalarını kriptografik araçlarla kontrol altına alarak bir saldırganın bu süreci bozmasını engelleyebilirsiniz. Bu pek çok basit ve gelişmiş saldırıyı durdurma potansiyeline sahip bir tedbir olmakla kimi zaman özel donanım ve emek gerektirmektedir. 

* [Boot sektörünü şifrelemek](../cihaz_guvenligi/sifreli_boot.md)

* [Libreboot ve GPG ile boot güvenliği](../cihaz_guvenligi/libreboot_grub.md)

* [Boot sektörünü USB bellek üzerinde taşımak](../cihaz_guvenligi/usb_grub.md)

* [Cihaz Şifreleme](../cihaz_guvenligi/cihaz_sifreleme.md)

* [Yubikey ile GPG anahtarı Güvenliği]()

### Fiziki güvenlik tedbirleri

Cihazınıza fiziki girişimde bulunmak genellikle bir biçimde cihazınızın açılmasını gerektirebilir. Bu cihazın donanımlarına bir ekleme yapmak veya ram ve sabit sürücü gibi donanımların çıkarılarak/değiştirilerek müdahale edilmesi olabileceği gibi kabaca kilidi açık cihazınızın elinizden kapılması da olabilir. Bir saldırganın yapacağı değişikliklerin ifşa olacağını fark etmesi hem caydırıcı hem de genel olarak güven verici bir önlemdir.

* [Simli Oje ve Entropi ile Fiziki Güvenlik](oje.md)

* [Haven ile ortam izlemesi](haven.md)

* [Private Lock ile Kapkaç Tedbiri](private_lock.md)










