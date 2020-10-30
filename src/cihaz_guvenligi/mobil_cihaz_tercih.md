### Hangi mobil cihaz benim için uygun?

Cihazınızı içinde bulunduğunuz duruma göre seçmelisiniz:

* **Yüksek Risk**: Bir devletin veya uzman ajanlık şirketlerinin hedefi olacağınızdan şüpheleniyorsanız.
* **Orta Risk**: Hali hazırda hedef olmadığınız halde bir saldırganın cihazlarınıza fiziksel erişim sağlaması durumunda kolay lokma olmayı tercih etmiyorsanız.
* **Düşük Risk**: Taşınabilir cihazlarınızı hassas veriler için kullanmıyorsanız.

#### Yüksek risk

Eğer riskiniz yüksek ise, **cep telefonunuzu hassas hiç bir şey için kullanmayın**. Bunun sebebi, tüm telefonların sizi kablosuz telefon ağına (hücresel ağ) bağlayan, "[baseband modem][]" olarak adlandırılan bir donanım içermesidir. Bu modemler özel mülktür ve uzaktan kötüye kullanılabilecek pek çok güvenlik açığı içermektedir. Bir kere aşıldıktan sonra, [baseband modem] iletişiminizi takip etmek ve kişisel verilerinizi elde etmek için kullanılabilir.

[Replicant][] tamamen özgür bir Android dağıtımı olarak sadece belirli cihazlar üzerinde çalışmaktadır. Çalıştığı cihazların temel özelliği [baseband modem]'i işlemciden izole etmenin bir imkanı olmasıdır. [Replicant] aynı zamanda, cihaz  üzerindeki, Wi-Fi, Bluetooth, GPS gibi donanımları özgür sürücüleri bulunmadığı için çalıştırmaz. Şayet mobil cihaz kullanmanız gerekiyorsa ve bu cihaz ile önemli veriler işleyecekseniz [Replicant] kurulu bir telefon iyi bir tercih olabilir.

Cep telefonlarına alternatif olarak Wi-Fi desteği olan ama hücresel ağa bağlanmayan bir tablet satın alabilirsiniz. Bu tip cihazlar baseband modem içermemektedir ve uzaktan saldırılara karşı çok daha dayanıklıdır. Sadece Wi-Fi içeren bir cihaz ile hala hücresel ağa, ayrı bir taşınabilir hotspot cihazı ile bağlanabilirsiniz.

NOT: Uçak modu yeterli değildir. Cihazınıza bağlı olarak, uçak modunda bile baseband modem hala çalışıyor ve cihazınızı saldırılara açık tutuyor olabilir.

Tavsiye edilen sadece Wi-Fi destekleyen cihazlar:

_Güncellenecektir (1 Ağustos 2020)_

#### Orta risk

Taşınabilir cihazınızda; devletler, şirketler veya meraklı insanlar tarafından elde edilmesini istemediğiniz hassas veriler mi var? Elbette var, herkesin var! Bu durumda, biri cihazınızı bulduğunda veya çaldığında onların işini olabildiğince zorlaştırmak istemeniz çok doğal.

Şayet hiç uğraşmayacağım diyorsanız, kendinizi Apple şirketinin sinsi yumuşak kollarına bırakıp modern bir iPhone alabilirsiniz. Pek çok gerçek olayda bu cihazlara örgütlü devletler dışında kolaylıkla erişilemediği görüldü. Lakin Apple şirketinin Çin ile yaşadığı aşk, yakın zamanda özgür olmayan yazılımında bulunan açıklar ve İsrailli bir şirketin 1000 ABD dolarına her iPhone'un kilidini kırabildiği iddiası ile yaşamanız gereklidir.

Tavsiyemiz uygun bir cihaz alarak üzerinde [GrapheneOS][] veya [LineageOS][] Android dağıtımları çalıştırmanız ve Google, Facebook gibi casusluk şirketlerinin yazılımları da dahil özgür olmayan yazılımlar **çalıştırmamanızdır**. [GrapheneOS] ve [LineageOS] piyasadan alabileceğiniz pek çok cihaza kolaylıkla kurulabilen ve mahremiyetinize önem veren toplulukların geliştirdiği işletim sistemleridir.

Tavsiye edilen cihazlar:

* **[LineageOS için][lineageos devices]**;
	* [LG G3](https://wiki.lineageos.org/devices/d855) Türkiye'de kolaylıkla bulunabilen, temizi için biraz araştırma gerektiren ama zamanına göre çok iyi donanıma sahip bir cihazdır. LineageOS kurulumu rootlama gereğinden dolayı biraz baş ağrıtabilir ama fiyat/performansta çok başarılıdır. Ancak LG G3 cihazlar, kronik olarak anakart arızası yaşayabilmektedir. Bu durumu göz önünde bulundurmanızı tavsiye ederiz.
	* [Sony Xperia Z](https://wiki.lineageos.org/devices/yuga) Görece eski bir donanım olan Z Türkiye'de bolca ve ucuza bulunabiliyor. LineageOS kurulumu da çok kolaydır. Lakin donanım yaşını gösterdiği için cihazınızı sonuna kadar kullanıyorsanız sizi tatmin etmeyebilir.
	* [Xiaomi Redmi Note 7](https://wiki.lineageos.org/devices/lavender) Çok daha modern bir donanım olarak Redmi Note 7 performans isteyen kullanıcılar için iyi bir tercih olabilir. USB-C desteklediği için de geleceğe dönük rahat etmenizi sağlar. Ancak NFC desteği **bulunmamaktadır**.

* **[GrapheneOS için][grapheneos devices]**;
	* Google [Pixel serisi](https://grapheneos.org/#device-support) cihazların tamamına GraphenOS kurulabilmekte fakat Pixel 4 sürümü henüz tamamlanmadı. Graphene uzun dönemli destek için, şimdilik Pixel 3 serisi cihazları önermektedir. GrapheneOS, Pixel 4 için tamamlandığında bu önerinin Pixel 4 olarak değişmesi muhtemel.

#### Düşük risk

Telefonunuzu kilitsiz bir şekilde öylece ortalıkta mı bırakıyorsunuz? O zaman ya başınıza gelecekleri hak ediyorsunuz ya da gerçekten taşınabilir cihazlarınızda hiçbir şey olmadığını düşünüyorsunuz. Ne yazık ki modern taşınabilir cihazlar İnternet'e bağlı oldukları ve kullanıldıkları sürece siz fark etmeseniz de ziyadesiyle fazla veri üretir ve bunları kaydederler. Bu verilerden belki haberiniz yoktur ama pekala bilgili bir kişi -ki bu bilgisayarla ilgili her sorunuzda aradığınız arkadaşınız bile olabilir- bu bilgilere ulaşmanın bir yolunu bilebilir.

Bu sebeple riskinizin düşük olduğuna eminseniz ve yanıldığınız için pişman olmayacaksanız, pekala herhangi bir telefon alıp ekran kilidi bile kullanmadan hayatınızı sürdürebilirsiniz.
