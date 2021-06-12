# Tails

Tails özünde anonimlik ve güvenlik sağlamak üzere geliştirilmiş bir GNU/Linux dağıtımıdır. Kullanıcılarına yabancı bilgisayarlarda güvenli bir iletişim ve çalışma ortamı sunduğu gibi kendi bilgisayarlarında da mümkün olan en az izi bırakarak iletişim kurmalarını sağlar. Tails'i diğer dağıtımlardan özel kılan [canlı](https://en.wikipedia.org/wiki/Live_USB) bir sistem olarak tamamen kullanılan usb bellek veya optik disk gibi bir medya üzerinden yüklenip bilgisayarın RAM'inde çalışmasıdır. Bu bakımdan Tails kullanılan bilgisayarın depolama aygıtlarına istenmedikçe bir veri kaydetmez ve bilgisayarın kapatılması üzerine yapılan işlemler RAM'den silinerek yok edilir. Bu sebepten Tails'in kısaltmasındaki "a" amnesic yani unutkan anlamına gelmektedir. Tails kullanıcılarına en az iz bırakarak bilgisayar kullanmalarına imkan sağlar.

Tails bu amacını gerçekleştirmek için çeşitli araçları bir araya getirip bunların en güvenli kullanımlarını temel alır. Bu araçlardan en önemlisi [TOR](/ag_guvenligi/tor.md). Tails'de tüm internet bağlantısı TOR üzerinden geçer. Bu şekilde kullanıcının anonimliği önceliklendirilmiş olur. Tails aynı zamanda kullanıldığı USB bellek üzerindeki boş alanda güvenli veri depolama yapılmasına da [Luks](https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup) ile imkan sağlar. Bu şekilde Tails ile birlikte üzerinde sürekli çalışılması gereken verilerin güvenli taşınması ve işlenmesi mümkündür. Bu rehberde anlatılan pek çok güvenlik ve mahremiyet aracı da Tails ile birlikte kurulu gelmekte.

Tails kullanabilmek için üç şeye ihtiyacınız bulunmakta:

* Tails imajı ve doğrulamak için gereken GPG imzası
* 8GB ve daha yüksek kapasiteli hızlı bir USB bellek veya bir DVD
* Yazma işlemini yapabileceğiniz güvendiğiniz bir bilgisayar

## Tails Kurulumu

Tails'i kurmak için [Tails kendi sitesinde](https://tails.boum.org) yaygın olarak kullanılan tüm işletim sistemleri ile kurulum için adım adım rehber bulundurmakta. Bunun için [kurulum sayfasından](https://tails.boum.org/install/index.en.html) yardım alabilirsiniz. Farklı indirme yöntemleri ile doğrulama biçimleri detaylı olarak anlatılmış durumda.

Bu rehber GNU/Linux dağıtım kullanarak GPG ile imza doğrulaması yapmayı anlatmaktadır. Bunun temel sebeplerinden biri Tails kullanmak için herkesin farklı bir sebebi olmakla birlikte güvenlik temel gerekçe olduğu durumda eldeki en güvenli ve en az aracıya güven gerektiren yöntemin takip edilmesindeki faydadır. Tails'in indirme ve web sitesindeki doğrulama sistemi hem indirilen imajın bütünlüğü hem de doğrulama için gereken GPG anahtarının gerçekliği için [HTTPS/TLS](https://tr.wikipedia.org/wiki/Transport_Layer_Security) sistemine güvenmekte. [Güvenli web gezintisi](/ag_guvenligi/guvenli_web_gezintisi.md) bu sisteme dayanmakta ise de her halde TLS genelde devletlerle yakın ilişkileri olan sertifika otoritelerine ve onların ticari zaaflarına bağlıdır. Bu bakımdan Tails'i güvendiğiniz bir kişinin kurulumundan elde edemiyor ve sıfırdan başlıyoranız bunun için en güvenli yöntem Bittorent ile imajı indirmek ve GPG ile doğrulamaktır.

### Tails imajını edinin

Bunu yapabilmek için öncelikle [Tails'in web sayfasına](https://tails.boum.org) ulaşabilmeniz gerekli. Bu sayfaya erişim pek çok ağ ve ülke dahilinde engelli olabilir. Bunu bir [VPN](/ag_guvenligi/vpn.md) veya [TOR](/ag_guvenligi/tor.md) ile aşmanız mümkün olduğu gibi Tails'in sitesinin aynalarından da fayda edebilirsiniz. Bunlar arasında [TOR Projesine](https://archive.torproject.org/amnesia.boum.org/tails/) ve [Linux çekirdek arşivine](https://mirrors.edge.kernel.org/tails/) ait olanlar sayılabilir.

Tails imajını elde etmenin en hızlı ve güvenilir yolu BitTorent aracılığı ile indirmektir. BitTorent pek çok insanın bilgisayarındaki eş imajlardan aktarım yapacağı için indireceğiniz imajın doğruluğunu sağlamanın emin yollarından biridir. Bunun için Tails'in sitesinden `Get Tails` başlığına girip işletim sisteminizi seçerek veya yükleyeceğiniz medya tipini seçerek indirme sayfasına ulaşabilirsiniz. Buradan BitTorent seçeneğini seçerek [Transmission](https://transmissionbt.com/download/) veya [qBittorent](https://www.qbittorrent.org/download.php) gibi özgür torrent istemcilerinden biri ile indirmeyi tamamlayabilirsiniz.

![alt-text](/tails/bittorent.png)

İndirme işleminin sonunda iki adet dosya elde edeceksiniz. Bunlardan ilki `tails-amd64-xxxx.img` şeklinde gelen Tails imajı ile aynı isimde olup sonu `.sig` ile biten GPG imzası. Bu imajı doğrulamak için her iki dosyaya da ihtiyaç bulunmakta.

### Tails GPG anahtarını elde edin

Doğrulama işlemini yapabilmek için öncelikle Tails'ın dağıtım anahtarına ihtiyacınız olacak. Bu anahtarı doğru şekilde elde etmek sürecin en zor kısmını oluşturmakta. Keza imza veya imza anahtarının kötücül bir niyetle değiştirilmiş kopyasını edinmeniz kuracağınız Tails için gereken güven koşullarını ciddi şekilde bozacaktır. Tails'in kendi sistemleri ele geçirilmiş olup size bozuk anahtar veya imaj sunabileceği gibi internet bağlantınızı sağlayan aracılar da buna neden olabilir. Hali ile doğru anahtara sahip olmak tüm bu saldırılara karşı tek kesin güvence konumunda sayılmakta.

Tails'e ait GPG imza anahtarını en güvenli şekilde elde etmek için aşağıdaki yollara sahipsiniz.

* [GPG güven ağına](/yazisma_guvenligi/wot.md) aşina iseniz Tails anahtarındaki imzalar arasından tanıdığınız biri var mı denetleyebilirsiniz.

* Güvendiğiniz ve aranızdaki ilişki olası saldırganlarınıza bariz olmayan birinin Tails kurulumundan hem doğrulama yapabilir hem Tails GPG anahtarını edinebilirsiniz.

Tails anahtarını Özgür Yazılım Derneğinin güven ağı çevresinden doğrulayabilirsiniz. ÖYD GPG kullanıcılarından biri ile tanışıp anahtarlarını imzaladıysanız Tails anahtarına güven ağı ile ulaşabilirsiniz. Bunun için aralıklarla düzenlenen [CryptoParty İstanbul](https://oyd.org.tr/projeler/) etkinliklerinden birine katılabilirsiniz.

### Tails imajını doğrulayın.

Bu işlemi kullandığınız GNU/Linux dağıtımının uçbiriminden kolaylıkla yapabilirsiniz. Şayet bir grafik arayüz tercih ediyorsanız da Kleopatra aracılığı ile aynı işlemi yapmanız mümkün. [GnuPG komut satırı rehberi](/yazisma_guvenligi/gpg/ucbirim_gpg.md) ve [GnuPG grafik arayüz kullanım rehberi](/yazisma_guvenligi/gpg/gui_gpg.md) bu konuda danışabileceğiniz kaynaklardır.

Uçbirimde doğrulama işlemini yapmak için indirilen Tails imajı ve imzasının bulunduğu dizinde bir uçbirim açarak aşağıdaki komutu yazabilirsiniz.

`gpg --verify [tails imaj imzasının yolu]`

Şayet anahtarı güven ağı ile doğrulayabiliyorsanız aşağıdaki şekilde anahtara tam güveni işaret edecek şekilde `[full]` ibaresi ile imzanın doğrulandığı görülecektir. Tails imzanın tarihinin en güncel sürümün yayınlandığı tarihten en az 5 gün erken olmasına dikkat edilmesini istemekte.

```
gpg: assuming signed data in 'tails-amd64-4.19.img'
gpg: Signature made Pzt 31 May 2021 13:31:59 +03
gpg:                using EDDSA key CD4D4351AFA6933F574A9AFB90B2B4BD7AED235F
gpg: Good signature from "Tails developers (offline long-term identity key) <tails@boum.org>" [full]
gpg:                 aka "Tails developers <tails@boum.org>" [full]
```

### Tails imajını yazdırın

#### Optik disk

GNU/Linux dağıtımlarda bir disk imajını optik diske yazdırmak için pek çok kullanışlı yazılım bulunmakta. Brassero bunun için iyi bir tercih sayılır.

Brassero'yu kurmak için aşağıdaki komutları kullanabilirsiniz:

Debian tabanlı dağıtımlarda: `sudo apt-get install brassero`

RPM tabanlı dağıtımlarda: `sudo yum install brassero`

İndirdiğiniz .ISO imajını yazmak için Brassero'yu açtıktan sonra menünün en altındaki `Burn image` seçeneğini seçerek ilerleyin.

![alt-text](/cihaz_guvenligi/tails/brassero.png)

Açılacak pencereden .ISO imajını ve optik sürücünüzü seçerek yazdırma işlemini başlatın.

![alt-text](/cihaz_guvenligi/tails/brassero_yaz.png)

#### USB bellek

USB bellekler hem modern bilgisayarların pek çoğunda artık gelmeyen optik okuyucu eksikliğinden hem de Tails ile birlikte güvenli depolama ve kimi ayarların kalıcı olarak saklanmasına imkan verdiğinden tercih edilir durumda. Tails kullanacağınız USB bellek üzerinden çalışacağı için USB 3.0 ve hızlı bir model tercih etmeniz yerinde olur. Aynı zamanda bunun için yeni bir bellek alacaksanız bunu adınıza internetten sipariş etmek veya yaşadığınız alanların yakınlarında bir yerden gidip almamanızı öneririz. Ulaşabileceğiniz çevredeki elektronik dükkanlarından birine rastgele karar verip raftan rastgele bir cihazı alıp nakten ödeme yapmanız en güvenli seçeneğiniz olacaktır.

Tails imajını yazmak için hem uçbirimden hem de bir Gnome aracı olan Gnome Disk Utility kullanabilirsiniz. Pek çok dağıtımda bu yazılım gelmekle birlikte eksik olması durumunda dağıtımınızın uygulama arayüzünden veya aşağıdaki komutla kurabilirsiniz:

Debian tabanlı dağıtımlarda: `sudo apt-get install gnome-disk-utility`

RPM tabanlı dağıtımlarda: `sudo yum install gnome-disk-utility`

![alt-text](/cihaz_guvenligi/luks_usb/gd_anaekran.png)

Gnome Disk Utility'nin listelediği depolama aygıtlarından cihazınıza Tails yazmak için taktığınız USB belleği bulmanız gerekli. Bunu kapasitesinden veya isminden anlamanız mümkün veya USB belleğinizi taktığınızda listede beliren cihaz olmasından da ayırt edebilirsiniz.

![alt-text](/cihaz_guvenligi/tails/gnome_disks_drive.png)

USB belleğinizi seçtikten sonra pencerenin sağ üst köşesindeki menüden `Restore Disk Image` seçeneğini seçip karşınıza çıkan pencereden indirdiğiniz Tails imaj dosyasını gösterip `Start Restoring` seçeneği ile işleme başlayabilirsiniz.

**SEÇTİĞİNİZ BELLEK ÜZERİNDEKİ TÜM VERİ KAYBOLACAKTIR**

![alt-text](/cihaz_guvenligi/tails/gnome_disks_menu.png)

## Tails'i çalıştırın

Tails'i kullanabilmek için USB belleğinizi kullanacağınız bilgisayara takıp bilgisayarı baştan başlatmalısınız. Çoğu bilgisayar USB girişlerine takılmış aygıtları otomatik olarak başlatmayacaktır. Bu sebepten Tails çalıştıracağınız bilgisayarı başlatırken üreticisine göre değişmekte olan bir tuşa basmanız gerekir. Kimi zaman bilgisayarlar açılış ekranlarında kısa bir süre ile `boot menüsü` girişi yapabilmeniz için basılması gereken tuşu gösterir. Aksi halde F12-F9, ESC ve DEL tuşları çoğu zaman işe yarar. Eski bir numara olarak bu düğmelerin hepsine hızlı şekilde tek tek basmak çoğu zaman ilk seferde sizi uğraşdırmadan sonuca götürebilir.

Şayet boot menüsünü açmak konusundaki cambazlıkta başarılı olduysanız karşınıza cihazınıza bağlı olan boot edilebilir cihazların bir listesi çıkacaktır. Bu listeden Tails Kurduğunuz USB belleği varsa ismi ile seçebilirsiniz yoksa `removable devices` veya `USB devices` benzeri harici bir aygıtı ifade eden menüyü seçerek Tails'i başlatabilirsiniz. Şayet bu işe yaramaz ise USB belleği tam olarak taktığınızdan emin olun ve başka bir USB girişini daha deneyin. Kimi bilgisayarlar boot edecekleri USB girişlerde ayrım yapabilmektedir. Şayet başarılı şekilde doğru USB aygıtı seçebilirseniz Tails bootloader'i olan Grub sizi siyah ekranı ile karşılayacaktır.

![alt-text](/cihaz_guvenligi/tails/grub.png)

Şayet bu aşamaya gelmekte sorun yaşıyorsanız aşağıdakileri sıra ile denemeniz önerilir:

* İndirdiğiniz Tails imajını doğruladığınızdan emin olun.
* Aynı USB belleğe tekrar kurulum yaparak işlemden emin olun.
* Aksi halde başka bir USB bellek ile tekrar deneyin.
* Bilgisayarınızla ilgili bir sıkıntı olması ihtimaline karşı başka bir bilgisayarda Tails'i çalıştırmayı deneyin.

Buna rağmen bilgisayar donanımlarının farklılıklarından dolayı kimi zaman hata almanız muhtemel olduğundan Tails'in sitesini ziyaret ederek karşılaştığınız hataya çözüm bulabilirsiniz.

## Tails kullanımı

Tails'i çalıştırmanızın ardından kullanılan bilgisayarın hızına bağlı olarak birkaç dakika içinde karşılama ekranı görüntülenecektir. Bu ekrandan çeşitli tercihlerin değiştirilmesi ve sistem başlatılmadan önce belirlenmesi gereken bazı özelliklerin açılması mümkün. Bu tercihler kullanım amacınıza göre önem gösterebilir. Aşağıdaki ayarları bu bölümde belirleyebilirsiniz.

* Tails'in dili
* Klavye dili
* Kullanılacak formatlar
* Ayarlandıysa kalıcı depolama alanının oturuma yüklenmesi
* Root kullanıcısı ve parolası
* 


















