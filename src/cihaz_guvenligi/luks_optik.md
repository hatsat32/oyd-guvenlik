# Optik Diskleri Şifrelemek

Optik diskler genellikle 8cm çapında lazer ile üzerine veri kaydedilen kayıt ortamlarıdır. Dünya tarihinde ilk yaygın kullanımı olan [LaserDisk](https://duckduckgo.com/l/?kh=-1&uddg=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FLaserDisc) teknolojisinin [format savaşlarını](https://en.wikipedia.org/wiki/Format_war) kaybetmesinin ardından [Compact Disk veya kısa adı ile CD](https://en.wikipedia.org/wiki/Compact_Disc) dünyadaki optik disk kullanımının gerçekten yaygınlaşmasına öncülük etmiştir. CD teknolojisini [Digital Versatile Disk veya DVD](https://en.wikipedia.org/wiki/DVD) izlemiş ve görsel sanat eserlerinin dağıtımında yaygınlık kazanmıştır.

Optik diskler üretildikleri tarihte bilgisayar kullanıcıları için sihirli sayılabilecek araçlardı. [Yaygın olarak "disket" olarak bilinen Floppy Disk](https://en.wikipedia.org/wiki/Floppy_disk) ile kıyaslanınca, bir CD-ROM neredeyse **500** kat kapasiteye sahiptir. Aynı zamanda optik disklerin 2000'lerin başlarında kullanıma giren flash belleklere nazaran çok daha ucuz olması uzun bir süre optik kayıt ortamlarının veri taşımanın ilk tercihi olmasına sebep olmuştur.

Bugün kimileri tarafından [optik disklerin öldüğü](https://www.lifewire.com/death-of-the-computer-optical-drive-832403) iddia edilmekte ve genel olarak tüketiciye sunulan cihazlarda yer ve hafiflik endişeleri ile optik disk sürücüleri gözden çıkarılmakta ise de optik diskler günümüzde görece özel koşullarda tartışmasız avanajlar sunmaktadır. Bu özelliklerin kimileri sayısal güvenlik amacı ile eşsiz sayılabilir. Bu sebepten optik diskleri gözden çıkarmadan önce güvenlik adına kullanımlarının ve genel veri güvenliğinin optik diskler üzerinde nasıl sağlanabileceğinin gözönüne alınması gereklidir.

## Optik disklerin güvenlik kullanımları

Optik diskler çoğu kayıt ortamı gibi fiziki ve sayısal kimi özellikler içermektedir. Bu özellikler günümüzün elektriksel kayıt sistemlerinden farklılıklar göstermekle özel durumlarda tercih edilebilir olmaktadır.

* Optik diskler hafif ve incedir.

* Optik diskler elektronik bir aksam içermediğinden çevresel ve mekanik etkilere dayanıklıdır.

* Elektronik veya metal aksam içermediğinden x-ray veya manyetik dedektör gibi araçlarda daha az görünürlerdir.

* Optik diskler gözden çıkarılabilecek kadar ucuzdur.

* Optik diskler tekrar yazılabilir versiyonları hariç bir kere yazıldıktan sonra değiştirilemezler.

Yukarıda sayılan özelliklerden taşınan verinin güvenlik gereksinimlerine veya taşımanın gerektirdiği güvenlik koşullarına göre faydalanılabilir.

### Optik disklerin saklama kullanımı

Optik disklerin mekanik parçalar içermemesi ve dış etmenlere olan dayanıklılığı çeşitli verilerin güvenli şekilde saklanması için değerli bir özellik oluşturmakta. Her ne kadar büyük kapasiteler sunmasa da önemli verilerin yedeklerinin oluşturulması ve bu yedeklerin güvenli konumlarda saklanmasına imkan sağlamaktadır. Bu bakımdan aşağıdaki örnek koşullarda optik diskler tecih konusu olabilir:

* Kriptografik anahtar ve araçların yedeklerinin saklanması

* Offline tutulması gereken hassas verilerin yedeklenmesi ve saklanması

### Optik disklern taşıma kullanımı

Optik disklerin en değerli kullanımlarından biri veri taşıma ihtiyacında ortaya çıkmaktadır. Optik disklerin ucuz olmaları ve ince yapıları sebebi ile gözden çıkarılabilir şekilde çeşitli aracılar veya riskli alanlardan taşınması mümkün olmaktadır.

* Posta yolu ile anonim şekilde gönderilmeleri

* Sınır güvenliği gibi riskli alanlardan fark ettirilmeden geçirilebilmeleri

* El koyulması durumunda ekonomik bir endişeye yol açmaması

## Optik disklerin teknik faydaları

Veri güvenliğinin operasyonel koşullarında bir verinin optik disk üzerinde tutulması veya işlenmesinin olası faydaları bulunmaktadır.

* Optik diskler çok hızlı şekilde imha edilebilirler.

* Optik diskler bir kere yazıldıktan sonra değiştirilemedikleri için üzerindeki verilerin bütünlüğünü korurlar.

* Optik diskler kolayca depolanabilir ve fazla yer kaplamazlar. Hareketli parça içermediklerinden mekanik olarak görece dayanıklı sayılırlar.

## Şifreli optik disk oluşturmak

Bir optik diskteki verileri şifrelemenin pek çok yolu bulunmakta. [GPG kullanarak tüm dosyaları şifreleyip](yazisma_guvenligi/gpg/gui_gpg.md) diske yazmak mümkün olduğu gibi [uzak sunucudaki dosyaların şifrelendiği](cihaz_guvenligi/uzaksunucu.md) şekilde şifrelenne dizini olduğu gibi diske yazdımak mümkün.

Bu rehber Luks ile bir optik diskin şifrelenmesini anlatacaktır. Bu yöntemin yukarıdaki seçeneklere göre birkaç faydası bulunmakta.

* Tüm GNU/Linux sistemler Luks aygıtları otomatik olarak açabilmekte ve dosya sistemini gösterebilmekte. Bu sebepten diskin kullanımı çok kolaylaşmakta.

* Crypfs ve GPG gibi ayrı bir yazılımın kullanımına gerek kalmadan deşifre işlemi yapılabilmekte.

* Dosya dizinleri ve boyutları gibi üstverilerin ifşası engellenebilmekte.

Bu rehberi takip edebilmek için bir herhangi bir GNU/Linux dağıtımını kullanmanız, root erişimine ve bir disk yazıcıya sahip olmanız gerekmekte. Rehber DVD kapasitesini esas almakla birlikte boyutları dilediğiniz şekilde değiştirmeniz mümkündür.

### Boş bir dosya yaratın

İçine verilerin yazılacağı boş bir dosyaya ihtiyaç duyulmakta. Bunu basitçe `/dev/zero` ile sıfır yazarak yaratabilecek olsak da şifreli verinin diskteki boşluk alanlardan ayırt edilememesi için aşağıdaki şekilde rastgele verilerden bir dosya oluşturun.

`dd if=/dev/urandom of=disk.img bs=1M count=4400`

Count değerini kullandığınız medyanın boyutuna göre ayarlayabilirsiniz. Yukarıdaki komut 4.4Gb boyutunda disk.img adlı bir dosya oluşturacaktır.

### Luks dosyasını oluşturup dosyalarınızı ekleyin

Aşağıdaki komut sırası ile Luks imajını oluşturup dosyalarınızı yedekleyebilirsiniz. Dosyalarınızın konumunu <yedeklenecek dizin yolu> ile belirtlen yere koymayı ihmal etmeyin.

`sudo losetup /dev/loop1 disk.img && cryptsetup luksFormat /dev/loop1 && cryptsetup luksOpen /dev/loop1 yedekdisk && genisoimage -R -J -joliet-long -graft-points -V backup -o /dev/mapper/yedekdisk <yedeklenecek dizinin yolu>`

Yukarıdaki çeşitli komutlar sıra ile çalışacak ve size sıra ile kullanmak istediğiniz parolayı iki kere soracak ve ardından gösterdiğiniz dizindeki dosyaları oluşturulan dosyaya şifreli olarak aktaracaktır.

### Luks dosyasını kapatın

Dosyanın oluşturulması tamamlandıktan sonra aşağıdaki komut ile bilgisayarınızda bağlı bulunan aygıtları kaldırarak imaj dosyasının işleminin tamamlayın.

`sudo cryptsetup luksClose /dev/mapper/yedekdisk && losetup -d /dev/loop1`

### disk.img dosyasını yazın

Tercihiniz olan bir yazdırma yazılımı ile disk.img dosyasını diskinize yazabilirsiniz. Yazma işleminin bitmesinin ardından diskinizi cihazınıza taktığınızda şayet otomatik başlatma ayarlı ise diskinizin parolası sorulacak ve doğru girmeniz durumunda dosya yöneticinizde disk içeriğini şifresiz olarak görebileceksiniz.
