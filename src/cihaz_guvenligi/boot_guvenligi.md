# Boot Güvenliği

Bilgisayarınız düğmesine basmanızdan işletim sisteminin sizi kullanılabilir şekilde karşılayacağı ana kadar sırası ile pek çok yazılım çalıştırarak açılır. Bu süreç bilgisayarınızın donanımların yüklenmesinden işletim sisteminizin açılış ayarlarına kadar pek çok süreci yöneten farklı yazılımlarca yönetilir. sürecin başından sonuna kadar istediğiniz gibi güvenli gitmesi fiziki ve yazılımsal kimi güvence ve varsayımlara bağlıdır.


## Boot güvenliğini neden önemsemelisiniz?

Cihazınızın boot sürecini ele geçirmiş bir saldırgan işletim sistemi seviyesinde farkına bile varılamayacak saldırılar gerçekleştirebilir. Özellikle tedbir alınmamış bilgisayarlarda bahsedilen saldırıların gerçekleştirilmesi ciddi bilgi birikimi de gerektirmemektedir. Bu tip saldırıları önlemek için çeşitli tedbirler alabilirsiniz.

Bilgisayarınızında ilk çalışan yazılım anakartınızda küçük bir ROM çipinde bulunan boot yazılımıdır. [BIOS](https://en.wikipedia.org/wiki/BIOS) Türkiye'de bilgisayar tarihinden bilinen bir yazılımdır. BIOS'un yerini çağdaş bilgisayarlda artık [UEFI-Unified Extensible Firmware Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) almıştır. UEFI Microsoft'un da içinde bulunduğu bir konsorsiyum tarafından düzenlenmekle neredeyse satılan ana akım tüm bilgisayarların boot yazılımıdır.


## Boot nasıl gerçekleşir?

Bilgisayarınızı açtığınız andan itibaren, sisteminizde yüklü olan çeşitli yazılımlar, çalışarak işletim sisteminiz yükleninceye kadar sırası ile çalışarak birbirlerini yüklerler. Bu zincirleme işlem işletim sisteminiz ile bilgisayarın donanımları arasındaki uyumu sağlar.

Bilgisayarınızda ilk çalışan yazılım, cihazın anakartında özel bir çip üzerinde çalışan UEFI veya BIOS yazılımıdır. Bu yazılım sistemdeki cihazları kullanılabilir hale getirmek, cihazınızda boot imkanı tanıyan bir cihaz bulup bunun çalışmasını sağlamak ile görevlidir. Modern bilgisayarlda en sık görülecek yazılım [UEFI (Unified Extensible Firmware Interface)](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) idir. 

UEFI aynı zamanda [Secureboot](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot_2) adında bir güvenlik sistemi de içermektedir. Secureboot günümüzdeki uygulaması ile bir [DRM](https://oyd.org.tr/yazilar/drm/) yani kullanıcıların özgürlüklerini sınırlayan bir sistemdir. Secureboot, Microsoft'a ait bir anahtar içerir ve bu anahtar ile imzalanmamış hiç bir kodun çalışmasına izin vermez. Bu sebeple pek çok GNU/Linux dağıtımı modern cihazlarda çalışabilmek için ya Secureboot'un kapatılmasını ya da Microsoft tarafından imzalanmış shim adında bir yazılımın sisteme dahil edilmesini gerektirmektedir. Secureboot'a kullanıcılar kendi anahtarlarını ekleyip kendi imzaladıkları kodların çalışmasını sağlayabilseler de bu çok zorlu bir süreç olmakla birlikte UEFI ve Secureboot'un özgür olmayan yazılımlar olduğu gerçeğini değiştirmemektedir.

Özgür [Libreboot](https://libreboot.org) desteklendiği cihazlarda bios yazılımının tamamen yerine geçerek olabilecek en özgür bilgisayar sistemine imkan sağlamaktadır. Libreboot doğrudan GRUB kullandığından, GRUB tarafından desteklenen şifreleme ve imzalama imkanlarını doğal olarak desteklemektedir. Bu sayede hem güvenli hemde özgür bir sistem oluşturmak mümkündür.

Sisteminizdeki UEFI veya Libreboot bir önyükleyici çalıştıracaktır. GNU/Linux dağıtımlar için bu GRUB'dır. GRUB sürücünüzdeki /boot sektöründe Linux çekirdeği ile birlikte bulunur ve çekirdeğin yüklenmesinden sorumludur. Çekirdek sisteminizde donanımlarla işletim sisteminizin arasındaki iletişimden sorumlu olmakla güvenliğiniz için önemli bir konumdadır.

Çekirdeğin yüklenmesinin ardından işletim sisteminiz yüklenir ve bilgisayarınız sizin tarafınızdan kullanılabilir hale gelir.


## Boot zincirindeki güvenlik tehlikeleri

* Şayet secureboot'un açık olmadığı standart bir kurulumunuz var ise bir saldırganın çekirdeğinizi kötücül bir versiyon ile değiştirip parolalarınızı ele geçirmesi veya daha ileri saldırılar gerçekleştirmesi mümkündür.

* Bilgisayarınıza fiziki erişimi olan biri /boot sektörünüzdeki çekirdek ve GRUB yapılandırmanızı herhangi bir özel tekniğe ihtiyaç duymadan kolaylıkla değiştirebilir ve güvenliğinize zarar verebilir.

* Secureboot nihayetinde Microsoft gibi tarihi kullanıcı dostu olmayan olaylarla dolu olan bir şirkete ve 99 ABD doları karşılığında imzaladığı kodların güvenliğine dayanmaktadır. Bu bakımdan bir saldırganın özel bir tedbir almadıysanız. parasını verip secureboot'un güvenliğini geçmesi mümkündür.

* Özgürlük her zaman güvenlik ile eş anlamlı değildir. UEFI ve secureboot kullanmıyor ve libreboot yüklü bir cihaz kullanıyor olsanız da güvenliğiniz için gerekli adımları atmadığınız sürece benzer riskleri siz de taşıyor olacaksınız.


## Boot güvenliğine giriş yapın

* [Libreboot ve GPG ile Boot Güvenliği](libreboot_grub.md)

* [UEFI ile /boot Sektörü Şifreleme](sifreli_boot.md)