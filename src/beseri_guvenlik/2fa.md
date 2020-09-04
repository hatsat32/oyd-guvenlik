# Çift Aşamalı Doğrulama

## Çift aşamalı doğrulama kullanın

Çift aşamalı doğrulama veya kısa adı ile 2FA (Two Factor Authentication) bir sisteme veya hesaba erişim için iki farklı girdinin gerekmesi demektir. Genellikle girdilerin kaynaklarının veya elde edilme şekillerinin farklı olması istenir. Sadece parola ile giriş yapılan sistemlerde "parola" bilinen bir şey olarak bir aşamayı ifade eder. Bunun yanında bir başka "şey" daha gerekmesi durumunda ikinci aşama elde edilmiş olur.

Bugün bankacılık işlemleri yapan neredeyse herkes 2FA'nın en yaygın metoduna aşinadır. Bankacılık sistemine giriş yaptığınızda banka sizden parolanızı girmenizi istediği gibi bir de atılan SMS'teki kodu girmenizi ister. Bu durumda parolanız **bildiğiniz** bir şey olarak ilk aşamayı, SMS'in gönderildiği SIM kart da **sahip olduğunuz** ikinci aşamayı oluşturur. Bu bakımdan bir kişinin hesabınıza erişmek için hem parolanızı öğrenmesi hem de SIM kartınız ile birlikte onun parolasını da bilmesi gereklidir.

## 2FA neden önemlidir?

2FA basit bir çaba ile bir sistemi çok daha güvenli kılar. Bir saldırgan birden fazla fiziki koşulda bulunan ve elde etmesi görece daha zor olan iki ayrı sırrı elde etmesi gerekir. 2FA kodları çoğunlukla zamana bağlı olduğu için bu sırrın öğrenilmesi de ileride kullanılabileceği anlamına gelmeyecektir. Bu sebeple mümkün olunan her hesap ve sistemde bir şekilde 2FA kullanılması tavsiye edilir. Görece en güvensizi SMS yolu ile olsa da, akıllı cihazınızda çalışacak bir yazılım veya özellikle bu iş için geliştirilmiş bir donanım 2FA olarak kullanılabilir.

## 2FA nasıl kullanılır?

2FA kullanımı hesaplarınızın hizmet sağlayıcısına bağlıdır.

* **SMS aracılığıyla**: Pek çok hizmet size SMS ile bu imkanı sunacaktır. SMS uygulaması kolay bir yol olduğundan tercih edilmektedir. Fakat GSM şebekesi doğası gereği güvensiz olduğundan size gönderilen kodun çalınması veya SIM kartınızın çeşitli şekillerde kopyalanması sizi riske atabilir. Aynı zamanda kişisel veriniz ve günümüzde kimliğinizin bir parçası olan cep telefonu numaranızı vermek anonimliğinizi bozacağı gibi güvenliğinizi tehlikeye de atabilir.

* **Yazılım aracılığıyla**: Akıllı cihazlarınıza kurabileceğiniz bir yazılım aracılığıyla 2FA kullanmanız mümkün olabilir. Bu imkan her zaman SMS'e tercih edilmelidir. Cihazınız zamana bağlı olarak çoğunlukla 60 saniye geçerli kodları yerel olarak üretecek ve size gösterecektir. Bunu yapmak için ilgili yazılımı çalıştırmanız ve hesap yöneticisinin size gösterdiği adımları takip edip ilgili karekodu okutmanız yeterlidir.

	* [FreeOTP+](https://github.com/helloworld1/FreeOTPPlus) ve [andOTP](https://github.com/andOTP/andOTP), Android cihazlarınızda 2FA kodları üretmek için kullanabileceğiniz özgür yazılımlardır.

* **Donanımsal anahtarlar ile**: Özellikle çift aşamalı yetkilendirme için tasarlanmış cihazlar güvenlik için en iyi çözümdür. Lakin donanımların pahalı olması sebebi ile pek az hizmet bu yöntemi tercih etmektedir. Bu amaçla kendi cihazınızı alıp yazılım yerine bu cihazlar ile kod üretimi yapabilirsiniz.

	* [Yubikey](https://www.yubico.com): Sadece bir 2FA cihazı olmaktan çok daha fazlasını yapabilen en yaygın kullanılan çift aşamalı yetkilendirme cihazıdır. Birden fazla protokolü desteklemekle tavsiye edilebilecek ilk üründür.
	* [RSA Tokens](https://community.rsa.com/community/products/securid/hardware-tokens): Bulabilir ve kullanabilirseniz RSA donanımlarını kod tabanlı 2FA uygulamalarında kullanabilirsiniz.

## 2FA kullanırken nelere dikkat edilmeli?

2FA başkalarının hesabınıza girmesini etkili şekilde engellediği gibi sizin de hesabınıza erişmenizi aynı şekilde engelleyebilir. Bu sebeple 2FA kodlarınızın gönderildiği SIM kartınızı veya kodların üretildiği cihazınızı korumalısınız. Hayat sürprizlerle dolu olduğundan genellikle SMS harici her 2FA uygulaması size çoğunlukla 10 tane yedek kod verir. Bu yedek kodları bastırarak güvenilir bir yerde saklamanız hatta bir iki tanesini cüzdanınızda taşımanız şiddetle önerilir. Bu şekilde ikinci aşamanızı kaybetmeniz durumunuzda hesaplarınızdan mahrum kalmazsınız.

## Ek okuma listesi

* [Olağan Paranoya / Çift Aşamalı Kimlik Doğrulama İle Hesabınızın Güvenliğini Arttırın](https://www.olaganparanoya.com/cift-asamali-kimlik-dogrulama/)
