# Nasıl katkıda bulunabilirim?

ÖYD Güvenlik Rehberi'ne katkıda bulunmaya git.oyd.org.tr üzerinde bir hesap oluşturarak başlayabilirsiniz. Bunun haricinde sisteminizde git'in kurulu olması ve yerel testleri yapabilmek için mdbook yazılımını kurabilir olmanız gerekmektedir.

Deponun "[Konular](https://git.oyd.org.tr/oyd/guvenlik/issues)" (Issues) sayfasını inceleyerek, projenin şu anda ihtiyaç duyduğu değişiklikleri görebilirsiniz. Bu sayfadaki konularda farklı etiketler mevcuttur. Katkı verebileceğinizi düşündüğünüz bir sorunu üstlenerek başlayabilirsiniz. Bunun için ilgili konunun sayfasına bir yorum bırakabilirsiniz.

## Depoyu çatallamak

Öncelikle, oyd/guvenlik altında bulunan depoyu kendi kullanıcınıza çatallamanız (forklamanız) gerekmektedir. Bu işlem için sayfanın sağ üstünde bulunan "Çatalla" butonuna basın. Depo sizin kullanıcınıza çatallanacaktır. Bu noktadan itibaren yapacağınız tüm değişiklikleri kendi çatalınızda yapacaksınız.

## Depoyu klonlamak

Şimdi, çatalladığınız depoyu yerelinize (bilgisayarınıza) klonlayın. Bunun için uygun bir dizinde aşağıdaki komutu çalıştırabilirsiniz:

```
git clone git@git.oyd.org.tr:kullanici_adiniz/guvenlik
```

Depo yerelinize klonlandı.

## Ana depodaki değişiklikleri çekme

Mevcut halde, oyd/guvenlik'te yer alan ana depoyu değil de kendi deponuzu klonladığınız için, `git pull` çalıştırdığınızda doğal olarak kendi çatalınızdan değişiklikleri talep etmiş olacaksınız. Bunun için `upstream` isminde yeni bir uzak sunucu (remote) eklememiz gerekiyor. Aşağıdaki komutu çalıştırarak bu depoyu ekleyebilirsiniz.

```
git remote add upstream https://git.oyd.org.tr/oyd/guvenlik.git
```

Upstream'in eklenip eklenmediğini `git remote -v` komutu ile kontrol edebilirsiniz. 

## mdBook kurulumu

ÖYD Güvenlik Rehberi, mdBook altyapısını kullanmaktadır. Bunun için mdBook yazılımının bilgisayarınızda kurulu olması gerekmektedir. mdBook'u kurmak için aşağıdaki komutları sırasıyla çalıştırın:

```
wget -O mdbook.tar.gz https://github.com/rust-lang/mdBook/releases/download/v0.4.1/mdbook-v0.4.1-x86_64-unknown-linux-gnu.tar.gz
tar -xvf mdbook.tar.gz
sudo mv mdbook /usr/local/bin/ 
```

Bu noktadan itibaren, `mdbook` komutunu çalıştırdığınızda mdBook çalışacaktır.

## Değişikliklerin yerelde test edilmesi

Değişikliklerinizi yaparken, yaptığınız değişiklikleri canlı olarak test etmenizde yarar vardır. Bunun için proje dizinindeyken:

```
mdbook serve
```

Yukarıdaki komutu çalıştırdığınızda, `localhost:3000` üzerinden proje servis edilecektir. Yaptığınız her değişiklikte proje tekrardan build olacağı için, değişikliklerinizi canlı olarak takip edebilirsiniz. 

## Değişikliklerin gönderilmesi

Öncelikle yereldeki dosyalarımızı işlememiz (commit) ve kendi çatalımıza ittirmemiz (push) gerekmektedir. Bunun için aşağıdaki komutları kullanabilirsiniz:

```
git add *
git commit -m "Buraya bir mesaj girin"
git push origin master
```

Lütfen anlaşılır commit mesajları girin. `add` komutunda `*` yerine değiştirdiğiniz dosyaları da yazabilirsiniz. `*` karakteri, değiştirdiğiniz tüm dosyaları commit'inize alacaktır.

_Not: GnuPG kullanıyorsanız, `-S` parametresiyle commit'lerinizi imzalayabilirsiniz._

## Değişiklik isteği açmak (pull request)

Yaptığınız değişiklikleri kendi çatalınıza ittirdikten sonra, git.oyd.org.tr üzerinde kendi çatalınıza gidin ve "Değişiklik İstekleri"ne gidin. Buradan "Yeni değişiklik isteği" butonuna basın. Değişiklik isteğiniz oyd:master ile sizin çatalınız arasında olmalıdır.

Anlamlı bir mesaj yazdıktan sonra, değişiklik isteğinizi açın. Eğer bir sorunu kapatıyorsanız, ilgili sorunun numarasını başına `#` işareti koyarak belirtmeyi unutmayın.

Değişiklik isteğiniz depo bekçileri tarafından incelenerek kısa bir sürede karara bağlanacaktır.

## Önemli uyarılar

1. **YERELDE TEST ETMEDİĞİNİZ HİÇBİR ŞEYİ DEĞİŞİKLİK İSTEĞİ OLARAK AÇMAYIN.**
2. Ana depoya yeni commit'ler atıldıkça, kendi yerelinizde `git pull upstream` yapmayı unutmayın.
3. Sorun ve değişiklik isteği mesajlarınızı açık bir dille yazmaya özen gösterin.
4. Projelerin birkaç gönüllü insan tarafından yürütüldüğünü, açtığınız konulara ve değişiklik isteklerine hemen cevap verilemeyeceğini unutmayın.
5. Tek bir değişiklik isteğinde 40 tane dosya değiştirmeyin, çok fazla değişiklik yapacaksanız bunları ayrı ayrı değişiklik isteklerine bölün.

----

Katkılarınız için teşekkür ederiz.
