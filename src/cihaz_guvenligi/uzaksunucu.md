# Uzak Sunucuda Dosya Şifreleme

**Bulut yoktur, başkasının bilgisayarı vardır.**

Bugün bulut olarak adlandırılan ama aslında kimi şirketlerin veri merkezlerinde bulundurdukları bilgisayarların depolama imkanları olan saklama hizmetleri temel bir mahremiyet ve güvenlik sorunu oluşturmakta.

Başkasının bilgisayarına verilerinizi gönderdiğinizde, [taşıma sırasında](ag_guvenligi/letsencrypt.md) şifreli olsalar da depolandıkları sabit sürücüde şifresiz şekilde kaydedilecektir. Bu bilgisayarın sahibi olan ile bu sistemlere yeterli yetki ile erişen herkesin de verilerinize dilerseler ulaşabilecekleri anlamına gelir.

Gerçek insanların bunu yaptıklarına dair bir verimiz olsa da mahremiyet zararlısı şirketlerin otomatize sistemler aracılığı ile tüm verilerinizi işlediği bilinen bir gerçek. Google yüklediğiniz dosyalar için sizden [kullanım hakkı](https://www.theverge.com/2012/4/25/2973849/google-drive-terms-privacy-data-skydrive-dropbox-icloud) almakta, dosyalarınızı bilinen dosyalarların [özgüt değerleri ile kıyaslayarak](https://torrentfreak.com/google-drive-uses-hash-matching-detect-pirated-content/) sansür uygulamakta.

Bu duruma en kolay çare başkalarının bilgisayarın kullanmamak olabilir. Bunun için evinizde veya güvendiğiniz bir yerde kendi sunucunuz üzerinde [Nextcloud]( çalıştırabilirsiniz. Lakin kimi kişiler için bu zahmetli, pahalı veya duruma göre imkansız olabilmekte. Bu durumda [şifreleme](cihaz_guvenligi/cihaz_sifreleme.md) yine yardımımıza yetişmekte.

Şayet gönderdiğiniz her veri, dosya sadece taşıma sırasında değil size ait bir anahtar ile şifrelenmiş olursa gönderdiğiniz sunucu tarafında bunların okunması neredeyse imkansız olur. Bu hala verinin silinmesi, şifresinin kırılmaya çalışılması veya [rubber hose](https://en.wikipedia.org/wiki/Rubber-hose_cryptanalysis) saldırılara engel olmayacak olsa da faydalı bir araç olarak gerektiği yerde değerlendirilebilir.

## Planlama



[Bu bölüme katkı verebilirsiniz](https://git.oyd.org.tr)
