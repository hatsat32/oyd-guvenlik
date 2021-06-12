# Güvenli Bellek Bölümü Silmek

Bir depolama aygıtını ve üzerindeki verileri yok etmenin fiziken imhadan sonra en kesin yolu bellek bölümünün tamamının silinmesidir. Bu işlemin yapılması aygıtın ömründen bir miktar götürdüğü için çok sıklıkla tekrar edilmemesi ve gerekli görülen güvenlik beklentisinden fazlasının uygulanmaması tavsiye edilir. Bu bakımdan veriyi yok etmek için çeşitli işlemler farklı seviyelerde uygulanabilir.

* **Tüm bellek üzerine sıfır yazmak:** Hızlıca cihaz üzerindeki verinin kolay yöntemlerle kurtarılmasını engelleyecek hızlı bir yöntemdir. Lakin özellikle SSD'lerin içindeki işlemci cihazın ömrünü korumak için sıfır yazma işlemini yapmayıp sadece bunu dosya sistemine işaretleyebilmektedir. Bu durumda ileri tekniklerle SSD'ler üzerindeki çipler okunarak veriler olduğu gibi geri kazanılabilmektedir. Aynı zamanda klasik HDD'ler mikroskop altında incelenerek sıfır yazımından önceki veri de tek geçiş yapılması durumunda okunabilmektedir. Bu neden ile sıfır yazma işlemi sadece güvenlik beklentisinin düşük olduğu durumlarda kullanılmalıdır.

* **Tüm bellek üzerine rastgele veri yazma:** Rastgele veri yazmak hem fiziki metodlarla yok edilen verinin geri kazanılmasını oldukça zorlaştırmaktadır hemde SSD'lerdeki işlemcinin yazılan veriyi ayrım yapmadan işlemesini gerekli kılmaktadır.

* **Yazma tekrarı:** Bellek üzerine yapılan yazma işlemi ne kadar tekrar edilirse yazılımsal ve fiziki incelemeler ile silinmek istenen verinin geri getirilmesi ihtimali o kadar düşmektedir. Bu durum özellikle sabit sürücüler için önemli olmakla birlikte kimi kaynaklarda bu sayının 35 geçişe kadar çıkmaktadır.

## Gnome Disk Utility ile bölüm silme

Gnome Disk Utility pek çok GNU/Linux dağıtımında gelen kullanımı kolay bir disk yöneticisi. Bu araç ile kolaylıkla harici bellekler ve diğer depolama aygıtları üzerine sıfır yazarak silme işlemi yapabilirsiniz. Bunun için Disks'i çalıştırıp silmek istediğiniz bellek aygıtını seçtikten sonra sağ üst köşedeki menüden `Format Disk` seçeneğini seçin.

![alt-text](cihaz_guvenligi/dosya_silme/gdu1.png)

Karşınıza çıkacak arayüzden `Overwrite existing data with zeroes (slow)` seçeneğini seçerek `Format` düğmesine basın ve ardından onaylayın.

![alt-text](cihaz_guvenligi/dosya_silme/gdu2.png)

![alt-text](cihaz_guvenligi/dosya_silme/gdu3.png)

## DD ile bölüm silme

Disk Destroyer (dd) genel amaçlı bir disk aracı olarak belleklerin üzerindeki verilerin silinmesi için oldukça elverişli bir araç. Bunun için öncelikle silmek istediğiniz aygıtın doğru yolunu bulmanız gerekli. Bunun için `lsblk` komutunu çalıştırıp çıktısını inceleyebilirsiniz.

```
loop12                   7:12   0  32,1M  1 loop  /snap/snapd/12057
loop13                   7:13   0  65,1M  1 loop  /snap/gtk-common-themes/1515
loop14                   7:14   0  32,1M  1 loop  /snap/snapd/11841
sda                      8:0    0 223,6G  0 disk  
├─sda1                   8:1    0   512M  0 part  /boot/efi
├─sda2                   8:2    0     1K  0 part  
├─sda5                   8:5    0   731M  0 part  /boot
└─sda6                   8:6    0 222,4G  0 part  
  └─sda6_crypt         253:0    0 222,3G  0 crypt 
    ├─vgxubuntu-root   253:1    0 221,4G  0 lvm   /
    └─vgxubuntu-swap_1 253:2    0   976M  0 lvm   [SWAP]
sdb                      8:16   1   7,5G  0 disk  
```
Yukarıdakine benzer bir çıktı alacaksınız. Taktığınız belleği kapasitesinden veya son takılan aygıt olarak görebilirsiniz. Yukarıdaki örnekte 7,5G olarak görülen `sdb` aygıtı cihaza takılı USB belleği ifade etmekte.

Bu aygıtı sıfır yazarak silmek için dd ile aşağıdaki komutu çalıştırabilirsiniz.

`sudo dd if=/dev/zero of=/dev/[aygıt adı] bs=4096 status=progress`

Rastgele veri ile bu yazma işlemini yapmak için:

`sudo dd if=/dev/urandom of=/dev/[aygıt adı] bs=4096 status=progress`

## Wipe ile bölüm silme

Şayet dd'den daha kolay bir araç kullanmak isterseniz dosya silmek için kullanılan `wipe` bölümlerin silinmesi için de kullanılabilmekte. Wipe'ı kurmak için aşağıdaki komutları kullanabilirsiniz:

Debian tabanlı dağıtımlar için: `sudo apt-get install wipe`

RPM tabanlı dağıtımlar için : `sudo yum install wipe`

Kurulumun ardından basitçe `wipte [aygıt adı]` şeklinde belleği silme işlemini başlatabilirsiniz. Bunun uzun bir süre alacağını öngörerek yapmanız önerilir.
