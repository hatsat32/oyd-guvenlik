# GrapheneOS Kurulumu

<!-- toc -->

GrapheneOS güvenlik odaklı bir Android projesi. Proje Google Pixel cihazların donanımsal özellikleri ile birlikte güvenlik özelliklerinin varsayılan olarak geldiği bir dağıtım sağlamakta.

GrapheneOS'in kurulumu proje tarafından hazırlanan rehber ve betik sayesinde fazlasıyla kolay. Bu rehber [Grapheneos'in web sitesindeki](https://grapheneos.org/install) kurulum rehberinden çeviridir. Keza proje kısıtlı sayıda cihazda çalıştığından kurulum fazlasıyla belgelenmiş ve iyileştirilmiş durumda. Kimi değişiklikler ise kolaylık ve anlaşılırlık amacı ile eklenmiştir rehbere.

## Kurulum

Bu rehber GrapheneOS'in resmen desteklenen cihazlarına ilişkindir. Hem projenin hem de özel kurulumlar için kullanılabilir.

## Gereksinimler

En az 2GB boş hafızaya sahip olmalısınız.

Windows 10, macOS Catalina, Arch Linux, Debian buster ve Ubuntu 20.04 LTS GraphenOS'in kurulumu için desteklenen işletim sistemleridir. Bu işletim sistemlerinden birinin güncel haline kuruluma devam etmeden önce sahip olmalısınız. Eski sürümler ve diğer GNU/Linux dağıtımları genellikle çalışmakla birlikte bir sorunla karşılaşmanız durumunda desteklenen işletim sistemlerinden birini denemeniz önerilir. 

Desteklenen cihazlardan birine sahip olmanız gerekli. Cihazınızın kilidinin açılıp GrapheneOS kurulabilmesini garanti etmek için operatörlerin sattığı cihazlardan uzak durmanız önerilir. Operatörler tarafından satılan cihazlar aynı işletim sistemi ve firmware'i içermekle birlikte cihazda operatöre özel ayarların açılabilmesi için bir ID ile birlikte gelmekte. Bu ayarlar bootloader'in kilidinin açılmasını engellemekte. Operatörler bunu devreden çıkarabilecek olsalar da destek ekibinin bunu bilmeme ihtimali yüksek ve olsa bile bunu yapmayabilirler. Operatörlerden bağımsız bir cihaz edinerek bu tehlikeden ve potansiyel dertlerden uzak kalabilirsiniz. Eğer operatör cihazının kilidini açabilirseniz bu GrapheneOS için bir sorun teşkil etmeyecektir.

Cihazın standart işletim sistemini güncellemek ve buradaki önergeleri takip etmeden önce en güncel firmware'i çalıştırdığından emin olmakta fayda var. Bu şekilde olası sorunlara, eksik özelliklere ve eski sürümlerdeki diğer değişikliklerle karşılaşmanın önüne geçilebilir. Dilerseniz cihazınızı online olarak güncelleyebilir veya Pixel cihazlara has tam güncelleme paketini yükleyebilirsiniz.

Bu rehber komut satırı araçları kullanmakta. Windows'ta eski komut satırı yerine PowerShell kullanılmakta.

### Fastboot kurulumu

Fastboot'un güncel bir kopyasını edinmeniz ve işletim sisteminizde PATH çevresel değişkenine ekli olmalıdır. `fastboot --version` komutunu çalıştırarak hangi sürüme sahip olduğunuzu görebilirsiniz. Sürümünüz en az **29.0.6.** olmalıdır. Dağıtımınızın paket yöneticisini kurulum için kullanabilirsiniz lakin pek çok paket deposu fastboot'un geliştirici sürümünü bulundurmakta, standart versiyon platform-tools (adb, fastboot, etc) kendilerine göre düzenleyip güncel tutmamakta.

Dağıtım paketlerinin listesi:


* __Arch Linux:__ `android-tools` fastboot ve diğer gerekli araçları getirmekte ve adb gibi başka araçların kurulmasına ihtiyaç duymamakta. adroid-udev fastboot ve adb'nin yerel oturumda root yetkisi olmadan çalışabilmesini sağlayacak udev kuralları içermekte.
* __Debian:__ Gelen paketler hem çalışmamakta hem de eski sürümlerden oluşmakta, kurulumda kullanmayın (üstteki paragrafa bakın)
* __Ubuntu:__ Gelen paketler hem çalışmamakta hem de eski sürümlerden oluşmakta, kurulumda kullanmayın (üstteki paragrafa bakın)

### platform-tools haricen kurulumu

Eğer işletim sisteminiz fastboot'un uygun bir sürümünü içermiyor ve repolarında bulundurmuyor ise platform-tools'un harici bir sürümünü Google'dan kurmayı değerlendirebilirsiniz. Eğer Android SDK kurulumunuz var ise veya geliştirme ile uğraşacaksanız platform-tools' paketlerini Android SDK paket yöneticisi ile kurabilir ve güncel tutabilirsiniz. Android SDK, haricen veya Android Studio aracılığı ile elde edilebilir.

Platform-tools'u indirmek doğrulamak ve çıkartmak için GNU/Linux işletim sisteminde:

`curl -O https://dl.google.com/android/repository/platform-tools_r30.0.4-linux.zip`

`echo '5be24ed897c7e061ba800bfa7b9ebb4b0f8958cc062f4b2202701e02f2725891  platform-tools_r30.0.4-linux.zip' | sha256sum -c`

**Not:** Yukarıda belirtilen sha256 değeri zaman içinde güncellenen paketler nedeni ile değişmiş olabilir. Bu değerin kolaylıkla bulunabildiği tek yer [GrapheneOS kurulum sayfası](https://grapheneos.org/install) olduğundan kurulumdan önce değişikliklere göz atmakta fayda var.

`unzip platform-tools_r30.0.4-linux.zip`

Daha sonra aracı işletim sisteminizin PATH yoluna eklemek ve her seferinde doğrudan yolunu göstermeden çalıştırmak için GNU/Linux'da aşağıdaki komutu kullanabilirsiniz:

`export PATH="$PWD/platform-tools:$PATH"`

Tercih ederseniz indirdiğiniz paketin dizinine gidip fastboot binary dosyasının bulunduğu dizinde uçbirimde başına `./` koyarak fastboot'u çalıştırmanız mümkün.

Kurulumun ardından `fastboot --version` komutunun çıktısı:

```
fastboot version 30.0.4-6686687
Installed as /home/username/downloads/platform-tools/fastboot
```

Bu açık olan uçbirime ait geçici bir PATH kaydı olmakla birlikte eğer yeni bir uç birim açarsanız tekrar yukarıdaki şekilde kaydedilmesi gerekir. Kurulum betiğini çalıştırmadan önce fastboot komutunun kullandığınız uçbirimde çalıştığından emin olun.

### Signify'ın kurulması

HTTPS'nin sunabildiğinin güvencenin ötesinde indirilen işletim sisteminin doğrulanabilmesi için signify aracını kullanabilirsiniz. Eğer signify paketini güvendiğiniz bir paket yöneticisinden elde edemiyorsanız signify kullanmanın çok da bir anlamı bulunmamakta. GrapheneOS sürümleri kendi sunucumuzda bulundurulmakta ve üçüncü taraflarca sunulan mirror'ları kullanmamaktayız. Kötücül bir signify kurulumu tüm işletim sisteminizi ve GrapheneOS imajınızı da geleneksel işletim sistemlerindeki tehdit yönetimi eksikliğinden dolayı tehlikeye atabilir. Bu durumda signify kullanmak hiç kullanmamaktan daha kötü olabilir. Sunucularımızın kötücül davranması rastgele birinin GitHub hesabının veya GitHub'ın kendisinin kötücül olmasından daha düşük bir ihtimal. Her halukarda bu rehbere kurulum için güvenmektesiniz ki yayınlanan sürümlerle bu web sitesi aynı sunucu üzerinde bulunmakta.

**Not:** Yukarıdaki not hali ile GrapheneOS'in sitesi için geçerli durumda. Şu anda üçüncü bir tarafın rehberini okumakta olduğunuzdan şüphe duyduğunuz durumlarda yukarıdaki tehdit modeline bağlı olarak [GrapheneOS web sitesini](https://grapheneos.org) referans almanız önerilir.

Dağıtımlarda bulunan Signify paket listesi:

    Arch Linux: signify
    Debian: signify-openbsd
    Ubuntu:signify-openbsd

### OEM kilidinin kaldırılma ayarı

OEM kilidinin kaldırılması için işletim sistemi içinden izin verilmesi gerekli.

Geliştirici ayarlarını Ayarlar menüsünden -> About phone (telefon hakkında) sekmesi altında bulunan "build number" bölümüne geliştirici modunun aktive edildiğine dair mesaj gelinceye kadar tıklayarak açabilirsiniz.

Daha sonra Settings(ayarlar) -> System(sistem) -> Advenced(gelişmiş) -> Developer Options(geliştirici seçenekleri) yolunu takip edip "Enable OEM unlocking"(OEM kilidini kaldır) sçeeneğini seçebilirsiniz. Bu Google Play hizmetleri ile gelen cihazlarda hırsızlığa karşı fabrika ayarlarına geri döndürme koruması kapsamında internet bağlantısı gerektirecektir.

### Bootloader'in kilidini kaldırmak

Öncelikle cihazın bootloader ekranına girmeniz gerekli. Bunu cihazı kapatıp ardından ses kısma düğmesini ile güç düğmesine aynı anda basıp tutarak gerçekleştirebilirsiniz.

Bootloader kilidini işletim sistemi ve firmware yüklemek için kaldırın:

`fastboot flashing unlock`

**Not:** Bu komutu telefonu bağladığınız bilgisayar üzerinden fastboot'un çalıştığı uçbirimden çalıştırmanız gerekiyor.

Komutun telefon üzerinden onaylanması gerekli. Onayın ardından cihazdan tüm verinin silinecektir.

### Fabrika imajının indirilmesi

Kurulum işlemini tamamlayabilmek için cihazınıza uygun GrapheneOS fabrika imajına ihtiyacınız olacak.

Dilerseniz dosyaları web tarayıcınız ile doğrudan indirebilir veya curl benzeri bir komut kullanabilirsiniz. Genellikle komut satırı kullanmak hali hazırda kurulumun kalanında kullanacak olduğunuzu düşünürsek daha kolaydır. Curl ile işlemi gerçekleştirmek için talimatlar aşağıda bulunmakta.

Fabrika imajları doğrulamak için gerekli olan umumi anahtarın (factory.pub) indirmek için:

`curl -O https://releases.grapheneos.org/factory.pub`

factory.pub'un içeriği şu şekildedir:

```
untrusted comment: GrapheneOS factory images public key
RWQZW9NItOuQYJ86EooQBxScfclrWiieJtAO9GpnfEjKbCO/3FriLGX3
```
Umumi anahtar aynı zamanda Twitter'deki resmi @GrapheneOS hesabında, /u/GrapheneOS Reddit hesabında ve GitHub'da bulunabilir. Kullanımda olan anahtar bir yenisi ile değiştirildiğinde eskisi ile imzalanmakta.

Fabrika imajlarını indirme sayfasından indirmek için; örneğin Pixel 3 XL için 2020.05.05.02 (crosshatch) sürümünü indirmek için:

```
curl -O https://releases.grapheneos.org/crosshatch-factory-2020.05.05.02.zip
curl -O https://releases.grapheneos.org/crosshatch-factory-2020.05.05.02.zip.sig
```

Signify yazılımını güvenli şekilde edinebildiyseniz imzaları aşağıdaki komut ile doğrulayabilirsiniz:

`signify -Cqp factory.pub -x crosshatch-factory-2020.05.05.02.zip.sig && echo verified`

**Not:** Her ne kadar komut signify olarak komutu çağırmış olsa da komutun Debian ve Ubuntu'da `signify-openbsd` olduğunu hatırlatmak gerkeli.

Bu komut eğer doğrulama başarılı ise "verified" çıktısı verecektir. Eğer bir şey yanlış giderse hata alacaksınız.

### Fabrika imajının flashlanması

İlk kurulum fabrika imajının flashlanması ile gerçekleştirilmekte. Bu var olan işletim sistemini kaldırıp tüm yükli veriyi yok edecektir.

Kurulum işlemine başlamak için cihazda bootloader ekranına gidin.

Ardından fabrika imajlarını çıkartın.

GNU/Linux'da:

**Not:** Bu işlemi fabrika imajını indirdiğiniz dizinde yapmanız gerekli.

`unzip crosshatch-factory-2020.05.05.02.zip`

Çıkarttığınız dizine gidin:

`cd crosshatch-factory-2020.05.05.02`

İmajı dizindeki `flash-all` betiği ile kurun:

`./flash-all.sh`

Flash işleminin bitmesini bekleyin ve ardından cihazı kullanmadan önce bootloader'i tekrar kilitleyin keza kilitleme işlemi cihazdaki tüm verileri yok edecektir.

### Bootloader'i kilitlemek

Bootloader'in kilitlenmesi boot aşamasındaki doğrulama için önemlidir. Bu aynı zamanda fastboot'un başka flashlamalar veya veri silmek için kullanılmasının da önüne geçer. Doğrulanmış boot cihaz işletim sistemine yapılan herhangi bir müdahaleyi (vbmeta, boot/dtbo, product, system, vendor) engelleyecektir ve değiştirilmiş/bozulmuş herhangi bir verinin okunmasına mani olacaktır. Eğer değişiklikler fark edilirse hata koruması veriyi orjinal haline getirmeye çalışır ve düzeltme sonrasında doğrulama gerçekleştirilebilir ki bu kötücül olmayan bozulmalara karşı son derece etkilidir.

Bootloader ekranında kilitleme için:

`fastboot flashing lock`

Komutun telefon üzerinden onaylanması gerekli. Onayın ardından cihazdan tüm verinin silinecektir.

### Oem kilidinin kapatılması

OEm kilidinin kaldırılması için gereken ayar cihaz açıldıktan sonra tekrar geliştirici seçeneklerinden kapatılabilir.

### Kurulumun doğrulanması

Auditor ve kullanımı ile ilgili bilgiyi [GraphenOS'in rehberinden edinebilirsiniz](https://attestation.app/tutorial)

[Mobil cihazlara ilişkin genel tedbirler](mobil_cihaz_tavsiyeler.md)
