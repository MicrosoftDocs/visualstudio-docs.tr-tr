---
title: Kod Kapsamı Sorunlarını Giderme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2651a84ae3c621237f34ff1667da6ecbacf0923a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055108"
---
# <a name="troubleshoot-code-coverage"></a>Kod kapsamı sorunlarını giderme

Visual Studio'da kod kapsamı analiz aracı yerel ve Yönetilen derlemeler için verileri toplar (*.dll* veya *.exe* dosyaları). Ancak, bazı durumlarda, **kod kapsamı sonuçlarını** penceresi benzeri bir hata görüntüler "boş üretilen sonuçlar:..." Neden boş sonuçlar alabilirsiniz birkaç nedeni vardır. Bu makale, bu sorunların giderilmesine yardımcı olur.

## <a name="what-you-should-see"></a>Görmeniz gereken

Seçerseniz bir **kod kapsamı analizi** komutunu **Test** menüsünde, yapı ve testler sonra bir listesini görmelisiniz sonuçlanıyor **kod kapsamı** pencere. Ayrıntıları görmek için öğeleri genişletmeniz gerekebilir.

![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png)

Daha fazla bilgi için [ne kadar kodun test edildiğini belirlemek için kod kapsamı kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Sonuçları ya da eski sonuçları görmek için olası nedenler

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Visual Studio'nun doğru sürümüne sahip misiniz?
 Visual Studio Enterprise ihtiyacınız vardır.

### <a name="no-tests-were-executed"></a>Hiçbir sınama yürütülemedi

Analiz&mdash;çıktı penceresini onaylayın. İçinde **çıktıyı Göster** aşağı açılan listesinde **testleri**. Herhangi bir uyarı veya hatanın günlüğe kaydedilip kaydedilmediğine bakın.

Açıklama&mdash;Testler çalışırken kod kapsamı analizi yapılır. Testler çalıştırıldığında sadece belleğe yüklenen derlemeleri içerir. Testlerin hiçbiri yürütülür için kod kapsamı raporunda hiçbir şey yoktur.

Çözüm&mdash;Test Gezgini'nde seçin **tümünü Çalıştır** testlerin başarıyla sonuçlandığını doğrulamak için. Kullanmadan önce tüm hataları düzeltin **kod kapsamı analizi**.

### <a name="youre-looking-at-a-previous-result"></a>Bir önceki sonucu arıyorsunuz

Değiştirme ve testlerinizi yeniden çalıştırın, bir önceki kod kapsamı sonucu eski çalıştırmadan renklendirme kodu ile birlikte görünür olabilir.

1.  Kod Kapsamı Çözümlemeyi Çalıştırın.

2.  En son sonuç kümesini seçtiğinizden emin olun **kod kapsamı sonuçlarını** penceresi.

### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (simge) dosyaları kullanılamaz

Analiz&mdash;derleme hedef klasörü açın (genellikle *bin\debug*) ve her derleme için doğrulayın bir *.pdb* aynı dizinde dosya *.dll*veya *.exe* dosya.

Açıklama&mdash;kod kapsamı motorunun her derleme, ilişkili olmasını gerektirir *.pdb* testi çalıştırması sırasında erişilebilir dosya. Yoksa hiçbir *.pdb* belirli bir derleme, derleme için dosya analiz edilmiyor.

*.Pdb* dosyası oluşturuldu, birlikte aynı derleme *.dll* veya *.exe* dosyaları.

Çözüm&mdash;yapı ayarlarınızı oluşturduğundan emin olun *.pdb* dosya. Varsa *.pdb* proje oluşturulduğunda, dosyaları güncel değil, daha sonra proje özelliklerini açın, seçin **derleme** sayfasında **Gelişmiş**ve incelemek**Hata ayıklama bilgisi**.

Varsa *.pdb* ve *.dll* veya *.exe* dosyalar farklı yerlerde kopyalama *.pdb* aynı dizine dosya. Kod kapsamı motorunun aramak için yapılandırmak da mümkündür *.pdb* dosyalarını başka bir konumda. Daha fazla bilgi için [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Bir izleme eklenmiş ya da optimize edilmiş ikili kullanma

Analiz&mdash;ikili iyileştirme profil destekli iyileştirme gibi gelişmiş herhangi bir biçimde gerçekleştirdi, veya bir profil aracıyla araç gibi izleme eklenmiş belirlemek *vsinstr.exe* veya  *VSPerfMon.exe*.

Açıklama&mdash;bir derleme zaten izleme eklenmiş veya başka bir profil aracıyla araç, derleme kod kapsamı analizinden atlanmıştır. Kod kapsamı analizi bu tür derlemeler üzerinde gerçekleştirilemez.

Çözüm&mdash;en iyi duruma getirme ve yeni yapı kullan kapatabilirsiniz.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod yönetilen (.NET) veya yerel (C++) kodu değilse

Analiz&mdash;bazı testlerin çalıştığından üzerinde doğrulama yönetilen veya C++ kodu.

Açıklama&mdash;Visual Studio'daki kod kapsamı analizi yalnızca yönetilen ve yerel (C++) kodlar kullanılabilir. Üçüncü taraf araçları ile çalışıyorsanız, bazılarını veya tümünü kodu farklı bir platformda çalışabilir.

Çözüm&mdash;hiçbiri kullanılamaz.

### <a name="assembly-has-been-installed-by-ngen"></a>NGen tarafından yüklenen derleme

Analiz&mdash;derlemeyi yerel görüntü önbelleğinden yüklenmedi doğrulayın.

Açıklama&mdash;Performans nedeniyle değil yerel görüntü derlemeleri analiz. Daha fazla bilgi için [Ngen.exe (yerel Görüntü Oluşturucu)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Çözüm&mdash;derlemenin MSIL sürümünü kullanın. Bu, NGen ile işlem yok.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Hatalı sözdizimi ile özelleştirilmiş .runsettings dosyası

Analiz&mdash;özel kullanıyorsanız *.runsettings* dosyası sözdizimi hatası içerebilir. Kod kapsamı çalışmıyor ve kod kapsamı penceresi test çalıştırması veya sonunda eski sonuçları açmaz.

Açıklama&mdash;özel bir birim testlerinizin çalıştırabileceğiniz *.runsettings* kod kapsam seçeneklerini yapılandırmak için bir dosya. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

Çözüm&mdash;hatalarının olası iki tür vardır:

-   **XML hatası**

     Açık *.runsettings* dosyasını Visual Studio XML düzenleyicisinde. Hata göstergelerine bakın.

-   **Normal ifade hatası**

     Dosyadaki her dize bir düzenli ifadedir. Her biri için belirli bir görünüm ve hatalar için gözden geçirin:

    -   Eşleşmeyen parantezler (...) ya da atlatılamayan parantezler \\(...) \\). Arama dizisinde parantezleri eşleştirmek istiyorsanız, atlatmak gerekir. Örneğin, bir işlevi kullanımı eşleştirmek için şunu yazın: `.*MyFunction\(double\)`

    -   İfadenin başına yıldız veya artı koyun. Herhangi bir dizenin karakterlerini eşleştirmek için noktadan sonra yıldız kullanın: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Yanlış istisnalarla özelleştirilmiş .runsettings dosyası

Analiz&mdash;özel kullanıyorsanız *.runsettings* dosya, derlemenizi içerdiğinden emin olun.

Açıklama&mdash;özel bir birim testlerinizin çalıştırabileceğiniz *.runsettings* kod kapsam seçeneklerini yapılandırmak için bir dosya. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

Çözüm&mdash;Tümünü Kaldır `Include` düğümlerden *.runsettings* dosya ve Tümünü Kaldır `Exclude` düğümleri. Bu problemi çözdüyse, bunları aşamalar halinde yerleştirin.

DataCollectors düğümünün Kod Kapsamını belirttiğinden emin olun. Bu örnek ile karşılaştırın [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Bazı kodlar her zaman kapsandığı gibi gösterilmez

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>İzlemeden önce yerel DLL'lerdeki kodun başlatılması

Analiz&mdash;statik olarak bağlı yerel kodda, başlatma işlevinin bir parçası olarak **DllMain** ve onu çağıran kod bazen gösterilen kodu çalıştırıldı olsa bile kapsanmamış olarak.

Açıklama&mdash;kod kapsamı aracı uygulama başlamadan hemen önce İzleme'yi bir derlemeye eklenmesiyle çalışır. Herhangi bir derleme başlatma kodu önceden yüklenen **DllMain** derleme yüklenir ve uygulama çalışmadan önce yürütür. Statik olarak yüklenen derlemeler için genellikle uygulandığı kapsanmayan için bu kodu görüntülenir.

Çözüm&mdash;yok.

## <a name="see-also"></a>Ayrıca bkz.

- [Ne kadar kodun test edildiğini belirlemek için kod kapsamını kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)