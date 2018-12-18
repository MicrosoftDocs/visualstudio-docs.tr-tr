---
title: Kod kapsamı sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: f7df2f4c83a61c62a7774bea475d54c3deea4c47
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306058"
---
# <a name="troubleshooting-code-coverage"></a>Kod Kapsamı Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'daki kod kapsamı analiz aracı yerel ve yönetilen (.ddl veya .exe dosyaları) derlemeler için verileri toplar. Ancak bazı durumlarda Kod Kapsamı Sonuçlar penceresi "Boş üretilen sonuçlar: ..." benzeri bir hata gösterir. Bunun olmasının çeşitli sebepleri vardır. Bu konu bu sorunların giderilmesine yardımcı olmak amacıyla hazırlanmıştır.  
  
## <a name="what-you-should-see"></a>Görmeniz gereken  
 Seçerseniz bir **kod kapsamı analizi** Test menüsünden komut ve derleme ve testler sonra kod kapsamı penceresinde sonuç listesini görmelisiniz. Ayrıntıları görmek için öğeleri genişletmeniz gerekebilir.  
  
 ![Kod kapsamı sonuçlarını renklendirme ile](../test/media/codecoverage1.png "CodeCoverage1")  
  
 Daha fazla bilgi için [kullanarak kod kapsamı için belirlemek ne kadar kodun test](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Sonuçları ya da eski sonuçları görmek için olası nedenler  
  
### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Visual Studio'nun doğru sürümüne sahip misiniz?  
 Visual Studio Enterprise ihtiyacınız vardır.  
  
### <a name="no-tests-were-executed"></a>Hiçbir sınama yürütülemedi  
 Çözümleme  
 Çıktı penceresini onaylayın. İçinde **çıktıyı Göster** aşağı açılan listesinde **testleri**. Herhangi bir uyarı veya hatanın günlüğe kaydedilip kaydedilmediğine bakın.  
  
 Açıklama  
 Kod kapsamı analizleri testler çalışırken tamamlanır. Testler çalıştırıldığında sadece belleğe yüklenen derlemeleri içerir. Testlerin hiçbiri çalıştırılmazsa kod kapsamı raporunda hiçbir şey olmaz.  
  
 Çözüm  
 Test Gezgini'nde seçin **tümünü Çalıştır** testlerin başarıyla sonuçlandığını doğrulamak için. Kullanmadan önce tüm hataları düzeltin **kod kapsamı analizi**.  
  
### <a name="youre-looking-at-a-previous-result"></a>Bir önceki sonucu arıyorsunuz  
 Testleri değiştirdiğinizde ve yeniden çalıştırdığınızda bir önceki kod kapsamı sonucu eski çalıştırmadan kod renklendirme dahil görünebilir.  
  
1.  Kod Kapsamı Çözümlemeyi Çalıştırın.  
  
2.  En son sonuç kümesini Kod Kapsamı sonuçları penceresinde seçtiğinizden emin olun.  
  
### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (simge) dosyaları kullanılamaz  
 Çözümleme  
 Derleme hedef klasörünü (genellikle bin\debug) açın ve her derleme için .pdb dosyasının .dll veya .exe dosyası ile aynı dizinde olduğunu doğrulayın.  
  
 Açıklama  
 Kod kapsamı motorunun test sırasında her derleme için ilişkili .pdb dosyasının erişilebilir olmasına ihtiyacı vardır. Belirli bir derleme için .pdb dosyası yoksa, o dosya analiz edilmez.  
  
 .pdb dosyası .dll veya .exe dosyasıyla birlikte aynı derleme sırasında oluşturulmalıdır.  
  
 Çözüm  
 Yapım ayarlarının .pdb dosyasını oluşturduğundan emin olun. Proje oluşturulduğunda .pdb dosyaları güncelleştirilmez, açıp proje özellikleri seçin **derleme** sayfasında **Gelişmiş** ve incelemek **hata ayıklama bilgisi**.  
  
 .pdb ve .dll veya .exe dosyaları farklı yerlerdeyse, .pdb dosyasını aynı dizine kopyalayın. Kod kapsamı motorunu .pdb dosyalarını başka bir konumda aramak için yapılandırmak mümkündür. Daha fazla bilgi için [kod kapsamı çözümlemeyi özelleştirme](../test/customizing-code-coverage-analysis.md).  
  
### <a name="using-an-instrumented-or-optimized-binary"></a>Araçlı ya da optimize edilmiş ikili kullanma  
 Çözümleme  
 İkilinin Profil Destekli İyileştirme gibi gelişmiş bir iyileştirmeden geçmiş olduğu veya csinstr.exe veya vsperfmon.exe gibi profil aracı tarafından oluşturulduğunu belirleyin.  
  
 Açıklama  
 Bir derleme zaten başka bir profil aracıyla araç haline getirilmiş veya iyileştirilmişse, derleme kod kapsamı analizinden atlanmıştır.  
  
 Kod kapsamı analizi bu tür derlemelerde gerçekleştirilmez.  
  
 Çözüm  
 İyileştirmeyi kapatın ve yeni bir yapım kullanın.  
  
### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod yönetilen (.NET) veya yerel (C++) kodu değilse  
 Çözümleme  
 Yönetilen veya C++ kodunda bazı testlerin çalıştığından emin olun.  
  
 Açıklama  
 Visual Studio'daki kod kapsama analizi sadece yönetilen ve yerel (C++) kodlar için kullanılabilir. Üçüncü parti araçlar kullanıyorsanız, kodunuzun bazı veya tamamı farklı bir platformda çalışabilir.  
  
 Çözüm  
 Hiçbiri kullanılamaz.  
  
### <a name="assembly-has-been-installed-by-ngen"></a>NGen tarafından yüklenen derleme  
 Çözümleme  
 Derlemenin yerel bir görüntü önbelleğinden yüklenmediğinden emin olun.  
  
 Açıklama  
 Performansla ilgili nedenlerden dolayı yerel görüntü derlemeleri analiz edilmez. Daha fazla bilgi için [Ngen.exe (yerel Görüntü Oluşturucu)](http://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).  
  
 Çözüm  
 Derlemenin MSIL sürümünü kullanın. NGen ile işlemeyin.  
  
### <a name="custom-runsettings-file-with-bad-syntax"></a>Hatalı sözdizimi ile özelleştirilmiş .runsettings dosyası  
 Çözümleme  
 Özelleştirilmiş bir .runsettings dosyası kullanıyorsanız, sözdizimi hatası içerebilir.  
  
 Kod kapsamı içindeki sonuçlardır. Kod kapsamı penceresi test sonunda açılmaz ya da eski sonuçları gösterir.  
  
 Açıklama  
 Birim testlerini kod kapsam seçeneklerini yapılandırmak için özelleştirilmiş .runsettings dosyasıyla çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için [kod kapsamı çözümlemeyi özelleştirme](../test/customizing-code-coverage-analysis.md).  
  
 Çözüm  
 Olası iki hata türü şunlardır:  
  
-   **XML hatası**  
  
     .runsettings dosyasını Visual Studio XML düzenleyicisinde açın. Hata göstergelerine bakın.  
  
-   **Normal ifade hatası**  
  
     Dosyadaki her dize bir düzenli ifadedir. Her birini hatalar için gözden geçirin ve bu belirtilen için bakın:  
  
    -   Eşleşmeyen parantezler (...) ya da atlatılamayan parantezler \\(...) \\). Arama dizisinde parantezleri eşleştirmek istiyorsanız, atlatmak gerekir. Örneğin, bir işlevi kullanımı eşleştirmek için şunu yazın: `.*MyFunction\(double\)`  
  
    -   İfadenin başına yıldız veya artı koyun. Herhangi bir dizenin karakterlerini eşleştirmek için noktadan sonra yıldız kullanın: `.*`  
  
### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Yanlış istisnalarla özelleştirilmiş .runsettings dosyası  
 Çözümleme  
 Özelleştirilmiş bir .runsettings dosyası kullanıyorsanız, derlemenizi içerdiğinden emin olun.  
  
 Açıklama  
 Birim testlerini kod kapsam seçeneklerini yapılandırmak için özelleştirilmiş .runsettings dosyasıyla çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için [kod kapsamı çözümlemeyi özelleştirme](../test/customizing-code-coverage-analysis.md).  
  
 Çözüm  
 Tümünü Kaldır `Include` .runsettings dosyasını kaldırın ve sonra tüm düğümlerden `Exclude` düğümleri. Bu problemi çözdüyse, bunları aşamalar halinde yerleştirin.  
  
 DataCollectors düğümünün Kod Kapsamını belirttiğinden emin olun. Bu örnek ile karşılaştırın [kod kapsamı çözümlemeyi özelleştirme](../test/customizing-code-coverage-analysis.md).  
  
## <a name="some-code-is-always-shown-as-not-covered"></a>Bazı kodlar her zaman kapsandığı gibi gösterilmez  
  
### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>İzlemeden önce yerel DLL'lerdeki kodun başlatılması  
 Çözümleme  
 Statik olarak bağlı yerel kodda, başlatma işlevinin bir parçası olarak **DllMain** ve onu çağıran kod bazen gösterilen kodu çalıştırıldı olsa bile kapsanmamış olarak.  
  
 Açıklama  
 Kod kapsamı aracı uygulama başlamadan önce izlemenin derlemeye eklenmesiyle çalışır. İçindeki bu süreden önce yüklenen herhangi bir derleme, başlatma kodunu **DllMain** derleme yüklenir ve uygulama çalışmadan önce yürütür. Kod kapsanmayacak gibi görünür.  
  
 Genellikle, bu statik olarak yüklenen derlemeler için geçerlidir.  
  
 Çözüm  
 Yok.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ne Kadar Kodun Test Edildiğini Belirlemek için Kod Kapsamını Kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)



