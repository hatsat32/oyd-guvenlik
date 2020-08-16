# Boot Güvenliği

Bilgisayarınız düğmesine basmanızdan işletim sisteminin sizi kullanılabilir şekilde karşılayacağı ana kadar sırası ile pek çok yazılım çalıştırarak açılır. Bu süreç bilgisayarınızın donanımların yüklenmesinden işletim sisteminizin açılış ayarlarına kadar pek çok süreci yöneten farklı yazılımlarca yönetilir. sürecin başından sonuna kadar istediğiniz gibi güvenli gitmesi fiziki ve yazılımsal kimi güvence ve varsayımlara bağlıdır.


## Boot güvenliğini neden önemsemelisiniz?

Cihazınızın boot sürecini ele geçirmiş bir saldırgan işletim sistemi seviyesinde farkına bile varılamayacak saldırılar gerçekleştirebilir. Özellikle tedbir alınmamış bilgisayarlarda bahsedilen saldırıların gerçekleştirilmesi ciddi bilgi birikimi de gerektirmemektedir. Bu tip saldırıları önlemek için çeşitli tedbirler alabilirsiniz.

Bilgisayarınızında ilk çalışan yazılım anakartınızda küçük bir ROM çipinde bulunan boot yazılımıdır. [BIOS](https://en.wikipedia.org/wiki/BIOS) Türkiye'de bilgisayar tarihinden bilinen bir yazılımdır. BIOS'un yerini çağdaş bilgisayarlda artık [UEFI-Unified Extensible Firmware Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) almıştır. UEFI Microsoft'un da içinde bulunduğu bir konsorsiyum tarafından düzenlenmekle neredeyse satılan ana akım tüm bilgisayarların boot yazılımıdır.


## Boot nasıl gerçekleşir?
