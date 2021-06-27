# Güvenli Dosya Silme

Taşınabilir bellekler başta olmak üzere verilerin şifresiz kaydedildiği veri kayıt ortamlarından bu dosyaların silinmesi işlemi pek çok zaman geri döndürülebilir bir işlem olabilmekte. Silinmesi gereken bir dosyanın silindiğinin sanılması ve bu dosyanın daha sonra istenmeyen bir koşulda geri getirilmesi bir güvenlik tehlikesi olarak ele alınması gereken bir durum. Özellikle cihazlar arasında veri aktarımı için sıklıkla kullanılan taşınabilir bellekler çoğunlukla iki şifreli cihaz arasında şifresiz şekilde bu verileri taşıdıklarından hedef olmaya çok daha açıklar. Özellikle taşınabilir doğaları ve göz ardı edilen güvenlik sorunları sebebi ile taşınabilir bellekler ve üzerine yazılan şifresiz verilerin güvenli şekilde silinmesi güvenlik gereklilikleri bakımından önem taşımakta.

## Depolama araçları ve bilgisayarlar

Bilgisayarlar veri depoladıkları sabit sürücü, SSD ve USB bellekler gibi aygıtlar üzerinde bir dosya sistemine ihtiyaç duyarlar. Bu dosya sistemi üzerinde hangi dosyanın nerede bulunduğu kayıtlıdır. İşletim sistemine bir dosyanın silinmesi talebi geldiğinde sistem kaynaklarından tasarruf etmek adına işletim sistemi dosyayı oluşturan kayıtları fiilen silmez sadece o bölümün ileride kullanılmak üzere uygun olduğunu belirten bir kayıt düşer. İşletim sistemi artık o dosyayı olması gereken yerde göstermemesine rağmen dosya kayıt ortamında hala bulunmaya devam ettiği üzere özel yazılımlar aracılığı ile kurtarılabilir. Bunu engellemenin yolu tüm bellek alanının şifrelenmesi, dosyaların şifreli olarak belleklere yazılması veya şifresiz yazılan dosyaların güvenli şekilde silinmesinden geçer.

**Yine de unutulmamalıdır ki aşağıda anlatılan tüm teknikler bir kayıt ortamından verinin gerçekten silindiğini garanti edemez sadece zorlaştırabilir. Dosya sistemleri çeşitli bozulma korumaları içermekle imha çabasını boşa çıkarabilir. Önemli durumlarda tüm belleğin silinmesi ve son noktada fiziki imha tek kesin çözüm olarak görülmelidir.**

Bir kayıt ortamındaki belirli bir dosyayı güvenli silmek için çokça araç bulunmakta. Bunların pek çoğu uçbirimden kullanılmakla birlikte neredeyse her GNU/Linux dağıtımı ile gelmekte. Grafik arayüz kullanımı için ise kurulum yapılması gerekli. Bir dosyanın silinmesi özellikle kesin kabul edilmemelidir. Bu dosyanın kolay yöntemlerle geri kazanılmasını kolaylaştıracak olsa da dosya sistemlerinin yedekleri ve SSD'lerin verileri yönetim biçiminden dolayı bu verilerin uygun tekniklerle geri kazanılması mümkün olabilir.

### Nautilus-Wipe eklentisi ile dosya silme

Nautilus GNOME masa üstü ortamının varsayılan dosya yöneticisidir. En sık karşılaşılacak dosya yöneticisi olması ile birlikte çeşitli eklentiler ile kolay kullanım imkanı da sağlamaktadır. Wipe eklentisi sağ tık menüsünden bir dosyanın veya dizinin güvenli silinmesi için kolay erişilebilir bir seçenek oluşturur. Bu eklentiyi kurmak için Nautilus'un kurulu olması şartı ile aşağıdaki komutları kullanabilirsiniz:

Debian tabanlı dağıtımlar için: `sudo apt-get install nautilus-wipe`

RPM tabanlı dağıtımlar için : `sudo yum install nautilus-wipe`

Kurulum tamamlandıktan sonra Nautilus'un sağ tık menüsünde `wipe` ve `wipe available disk space` seçenekleri ortaya çıkacaktır.

![alt-text](dosya_silme/wipe_menu.png)

* Wipe ile belirli bir dosyanın bulunduğu sektör silinebilir.
* Wipe available disk space ile o depolama alanındaki boş bölge silinebilir.

### SRM ile dosya silme

Secure remove (SRM) ile uçbirimden çeşitli güvenlik seviyelerinde dosya silme işlemi yapılabilir. Bu paketi kurmak için aşağıdaki komutları kullanabilirsiniz:

Debian tabanlı dağıtımlar için: `sudo apt-get install srm`

RPM tabanlı dağıtımlar için : `sudo yum install srm`

Kurulumun ardından uçbirimden `srm` komutu ile silme işlemi yapmanız mümkün. Silme işleminin çeşitli güvenlik seviyeleri ve hızları bulunmakta. Bunun için amacınıza uygun aşağıdaki parametrelerden yararlanabilirsiniz.

* `-f` parametresi hızlı ama güvensiz bir silme sağlayacaktır
* `-l` parametresi -f parametresine göre daha yavaş ama görece güvenli silme sağlayacaktır
* `-r` bir dizin ve altındaki tüm dizin ve dosyaları silecektir
* `-z` son yazma işlemini diskte iz bırakmamak için rastgele veri yerine sıfır yazarak tamamlar

Bir dosyayı silmek için `srm [parametre] [dosya yolu]` şeklinde kullanabilirsiniz.

### DD ile dosya silme

Disk Destroyer (dd) neredeyse her GNU/Linux dağıtımı ile gelen genel amaçlı bir yazılım. Bu yazılım aracılığı ile herhangi bir kurulum yapmadan bir depolama alanını veya bir dosyayı imha edebilirsiniz. Hatırlatmakta fayda var ki adı **disk yokedici** olan bir yazılımı çok dikkatli kullanmalısınız. Aşağıdaki komut ile dd aracılığı ile belirli bir dosyayı silebilirsiniz.

`dd if=/dev/urandom of=[dosya dizini] bs=4096 bs=1`

Dosyanın büyüklüğüne ve yazma hızlarına bağlı olarak bu işlem uzun sürebilir. dd varsayılan olarak bir ilerleme çıktısı vermemekte. Şayet `Status=progress` parametresini verirseniz işlemin gidişatına ilişkin bir miktar bilgiyi sunacaktır.
