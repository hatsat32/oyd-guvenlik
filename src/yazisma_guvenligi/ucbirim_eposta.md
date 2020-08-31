# Uçbirim ile E-posta Şifrelemek

Şayet oldschool yöntemi benimsemek isterseniz e-posta şifrelemek adına, bu işlemi terminalden yapmaktan daha iyi bir yol bulamazsınız! GPG ilk ortaya çıktığında kullanımı terminalden bir mesajı şifrelemek göndermek üzere e-posta istemcisine yapıştırmak ve tekrar aynı yoldan deşifre etmekten geçiyordu. Günümüzde [Thunderbirg/Enigmail](thunderbird_enigmail.md) gibi yazışmayı çok kolaylaştıran arayüzler geliştirilmiş olsa da terminalden bu işlemi gerçekleştirebilmek hala temel düzeyde faydalı olabilmektedir.

## E-postanızı yazın

Öncelikle e-postanızı daha rahat ettiğiniz bir yerde yazmak isteyebilirsiniz. Bunun için tercihiniz olan bir metin editörünü seçebilir veya bir kelime istemci de kullanabilirsiniz. GPG sadece salt metin olarak çalışacağından formatlama detaylarının mesajınıza aktarılmayacağını hatırlatmalıyız.

## Bir uçbirim açın

Kullandığınız Gnu/Linux dağıtımında bulunan bir uçbirim penceresini, GPG anahtarınızın sahibi olan kullanıcı olarak açın. Bunun için grafik arayüzden faydalanabilir veya aşağıdaki tuş kombinasyonunu kullanabilirsiniz.

`ctrl + alt + t`

## GPG ile mesajınızı şifreleyin ve imzalayın

Aşağıdaki komut ile GPG'yi mesaj şifreleme aşamasına geçirin.

`gpg --encrypt --armour` veya `gpg -ea`

Tercihen mesajınızı imzalamayı da seçebilirsiniz. Bu hem alıcınızın mesajın sizden geldiği konusunda emin olmasını sağlar hem de mesajın bütünlüğünü garanti eder.

`gpg --encrypt --sign --armour` veya `gpg -esa`

Mesajınızı sadece imzalayarak sizden geldiğini de kanıtlamak isteyebilirsiniz. Bu imkan GPG anahtarı olmayan birinin dahi mesajın size ait olduğunu doğrulamasına imkan sağlar.

`gpg --clear-sign`

Şayet sisteminizde varsayılan olan bir anahtar var ise GPG imzalama için kendiliğinden bu anahtarı kullanacaktır. Şayet sisteminizde olan başka bir anahtarı kullanmak isterseniz aşağıdaki ek komut ile anahtarınızı belirtin.

`gpg --clear-sign -u (anahtar ID veya e-posta)`

Dilediğiniz komutu çalıştırdığınızda aşağıdaki şekilde GPG sizden alıcının e-posta adresini veya kullanılacak anahtarın ID'sini isteyecektir.

```
gpg: using "xxxxxxxxxxxxxxxx" as default secret key for signing
You did not specify a user ID. (you may use "-r")

Current recipients:

Enter the user ID.  End with an empty line: 

```
Alıcınızın kullandığı anahtarda belirttiği e-posta adresini girip "enter" tuşuna basın ve başka bir alıcı yok ise tekrar gelen ekrande bir adres girmeden "enter" tuşlayın.

Terminal sizi yanıp sönen imleci ile karşılayacaktır. Buraya mesajınızı yazın veya kopyalayın. Her şeyin yerinde göründüğünü düşündüğünüzde aşağıdaki tuş kombinasyonu ile işlemi tamamlayın.

`ctrl + D`

GPG size mesajınızın şifreli çıktısını verecektir.

```
-----BEGIN PGP MESSAGE-----

hQIMA2YZNFxt9JB3AQ/7BW72H19P3yYliDyn5DOjxrTaQ0DZGLI3iRMXIb11JWEC
rCRvN8pokKeSa/8jcWFodWmsbj1hz5apFQho54HUuTRu3Q91QNgKOEXphiHGeEG8
Io1EYV/xzeH0v/NzJsQprqeEcr1hdbN3IfDkVV6jE2XZckZ6plOFM+Ubxe2UhXiE
EFx8x6p6mO8tNESy/TBGlIk/6hhrXISMqSz1JKdsbiyUTYGzmcM0lz7UzidMtjhJ
npb8b0nRSfBNufavqFRNhqedkYc9+dDvILs8VH2KVSPJjtSrUOPuKgcBWcLDMFl7
y94MaZwh3aIPOlEyVId8iCLO1XyzYRN8MWyyvsK7Z5O+Fs8sfmGTSBiKfzKP+7aU
Ine1cUjPXvh3DDHm9qPbSRGr/nr5W+Pt5TvEzNs2hiS4LuM9kQW2+FZYCMJgJXaE
DeRyx8RrPUJG8LnazZ4yFVNfQq8CBxcR+xjKDbtPtgiI9u2Cvoo/H1rQzOS+1/nQ
kq4xmdjrYTHLr0VXWWU+Zjy/qXNHYAvkwKXNwqJ58W+eQBQwc2GeYW79fo+cc2DV
7zv078sbodikV1uda7jQvHuDnSUa8nJPpoSjTWb+Fv/YAesQjgJlDjsqm/K3ElUq
UvcJOSf31P2PytfUxH8saI/sRe0ciX2PFSvhLBKygLtxzBOOkzFqh6UO9JzVv1rS
6QFIjHJTZebjytaMF/iGJnL99F7kaLUzdBJh7zpkT3Blj3Bldk2zo7lZOoJxHTGI
kfIJRWYPkP1qStTqu6EKr8NaJkbtM2SZ7uZgqXIxX+ncX4bLXsTj63y3jytVO/Q8
yiMJva+8nK6mwu1dqN8zsPHwaaggH16JXlBwcwtdB9mze7OAmRfwirMWwnHtsc8S
zuRUHPdlXbjRuPzBJA8tChl4LvSdqivjlGq7XK+hcfmjmevc7DnaJznSR++Q52O/
E16lKbQCmf/9c1l19f2HuNWHscxppLaeGqM7+5EFgj13riN08wKiMODBtJyH/vbP
nt3XamHevon7H0rsXse/0TY8BomEaaVlpn85MgGNVA0Zb3UxaZm++bWwBW/Kvpu3
1LWPWZx4WmJwT+EA4nSF2HwxUWyy6FeQf2z+mfyEnbhxueFnig6f5hfm6OvIR4PJ
5LwHDXgcKCzvNUGFLLFf5ZR/6lLJZ7wFvlNvqdvNNTrkhqU5/qw5uJuA1F5jUYf7
Rl5WGSLBJN0FWryW30SuFlNcQgU0xxyKwPSnrPRg3mPMumQ1LaOPO8SCzogklQM6
jdktewFEJb5A4LR+Fh/MpwP5AiPwpl+CAMe3jZSiOhJzBjun/UJS2M8s1hIVTzSd
gLa/ewTVc6jkyGDmUpQMOQTumm7IIyX0HBhZBYtDBxq9lPStrCpNkgmPIblHLwtX
95krDh2WORbuYxlzlE8/R6KfhqCxPMMn4+eS401zeSv3Z/u+3ImHXZTAz/qf+rcl
vn7ufVp6IyzMHmQ742l1tpaX3PRq0V+AprSbupodAACzf+zrkJqiC08O6Bz7cX0c
WtrjYbxxnjdYPsuV3HGS380HSrdlp8LhMAHDpha5gT7Ge7FHdCk=
=ezWd
-----END PGP MESSAGE-----

```

Bu noktadan sonra soz konusu çıktıyı alıp dilerseniz e-posta ile dilerseniz mektup ile mesajın şifrelendiği kişiye gönderebilirsiniz.

**BONUS:** Şayet mesajınızı metin olarak yazdıysanız **pro** şekilde aşağıdaki komutla da doğrudan şifreleyebilirsiniz:

`cat [metin yolu] | gpg -esa`

Şayet mesajınızı Libreoffice ile yazdıysanız daha ilginç şekilde aşağıdaki komut ile doğrudan mesajınızı metin olarak şifreleyebilirsiniz:

`soffice --cat [belge yolu] | gpg -esa`

## Mesajınızı deşifre edin

Yukarıdaki gibi bir mesajın alıcısı iseniz Terminalden bu mesajı deşifre etmeniz çok kolay. Tek yapmanız gereken aşağıdaki komutu girip ardından mesajı yapıştırmak.

`gpg --decrypt` veya `gpg -d`

Mesajı yapıştırdıktan sonra `ctrl + D` ile işlemi sonlandırabilirsiniz. GPG size parolanızı soracak ve ardından mesajınızı gösterecektir.

```
gpg: encrypted with 4096-bit RSA key, ID 6619345C6DF49077, created 2016-10-26
      "Alper Atmaca <xxxxxxxxxxxxxxxxxxxx>"
entropi ne süpergpg: Signature made Pzt 24 Ağu 2020 22:41:49 +03
gpg:                using RSA key 8F2E9434DDFF4613F6829D8B471A839AB4DD8E6D
gpg: Good signature from "Alper Atmaca <xxxxxxxxxxxxxxxx>" [ultimate]
gpg:                 aka "Alper Atmaca <xxxxx@riseup.net>" [ultimate]
gpg:                 aka "Alper Atmaca <xxxxxx@gmail.com>" [ultimate]
gpg:                 aka "Alper Atmaca <xxxxx@oyd.org.tr>" [ultimate]
gpg:                 aka "Alper Atmaca (alperatmaca@gmail.com) <alperatmaca@gmail.com>" [ultimate]

```
