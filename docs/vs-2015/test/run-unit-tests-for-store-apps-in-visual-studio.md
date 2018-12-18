---
title: Store uygulamaları için birim testleri çalıştırma
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 14
author: alexhomer1
ms.author: gewarren
manager: robinr
ms.openlocfilehash: 9496a41d3eadd91112579b54250a6022bd6484e5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050927"
---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Visual Studio'da Store uygulamaları için birim testleri çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, Microsoft Visual Studio ile Test Gezgini'ni kullanarak birim testlerini çalıştırmak açıklar

> [!NOTE]
>  Bu bölümdeki konular, Visual Studio Express Windows 8 için işlevselliğini açıklar. Visual Studio Community, Enterprise ve Professional birim testi için ek özellikler sağlar.
>
> - Bir eklenti bağdaştırıcısı Microsoft Test Gezgini için oluşturduğu tüm üçüncü taraf veya açık kaynak birim testi çerçevesini kullanın. Ayrıca, analiz ve testleriniz için kod kapsamı bilgileri görüntüleyebilirsiniz.
>   -   Her derlemeden sonra testlerinizi çalıştırın. Microsoft Fakes, testlerinizi, sistem ve üçüncü taraf işlevselliği için test kodu değiştirerek kendi kodlarına odaklanmasını yönetilen kod için bir yalıtım çerçevesi de kullanabilirsiniz.
>
>   Daha fazla bilgi için [Birim Test kodunuzu](../test/unit-test-your-code.md) MSDN Kitaplığı'nda.

##  <a name="BKMK_In_this_topic"></a> Bu konudaki
 [Birim test çerçeveler ve test projeleri](#BKMK_Unit_test_frameworks_and_test_projects)

 [Testleri Test Gezgini'nde çalıştırma](#BKMK_Running_tests_in_Test_Explorer)

- [Testleri çalıştırma](#BKMK_Running_tests)

  [Test sonuçlarını görüntüleme](#BKMK_Viewing_test_results)

- [Test ayrıntılarını görüntüleme](#BKMK_Viewing_test_details)

- [Test yönteminin kaynak kodunu görüntüleme](#BKMK_Viewing_the_source_code_of_a_test_method)

  [Test listesini düzenleme](#BKMK_Organizing_the_test_list)

- [Testlerinizin gruplandırılması](#BKMK_Grouping_tests)

- [Aramayı ve filtrelemeyi test listesi](#BKMK_Searching_and_filtering_the_test_list)

  [Hata ayıklama birim testleri](#BKMK_Debugging_unit_tests)

##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Birim test çerçeveler ve test projeleri
 Visual Studio Express for Windows Store Apps yönetilen ve yerel C++ kod için Microsoft birim testi çerçevelerini içerir. Test Gezgini, bir çözümde birden çok test projesini ve üretim kodu projelerin bir parçası olan test sınıflarından testleri çalıştırabilirsiniz. Visual C# ve Visual Basic birim testi çerçeveleri veya test projeleri Visual C++ herhangi bir birleşimi olabilir. Test altındaki kod .NET Framework için yazıldığında, test projesi hedef kodun dili ne olursa olsun herhangi bir .NET Framework dilde yazılabilir. Yerel C/C++ kod projeleri, bir C++ birim test çerçevesi kullanılarak test edilmelidir.

##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Testleri Test Gezgini'nde çalıştırma
 Test projesi oluşturduğunuzda, testler Test Gezgini'nde görünür. Test Gezgini görünür değilse seçin **Test** Visual Studio menüsünde **Windows**ve ardından **Test Gezgini**.

 ![Birim Test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Çalıştırma, yazma ve testlerinizi yeniden çalıştırın, Test Gezgini sonuçları varsayılan gruplarında görüntüler **başarısız testler**, **başarılı testler**, **Atlanan testler** ve  **Testleri Çalıştır**. Test Gezgini'nin testlerinizi gruplandırma şeklini değiştirebilirsiniz.

 Bulma, düzenleme ve Test Gezgini araç çubuğundan testleri çalıştırmak, işin çoğunu gerçekleştirebilirsiniz.

 ![Test Gezgini araç çubuğundan testleri](../test/media/ute-toolbar.png "UTE_ToolBar")

###  <a name="BKMK_Running_tests"></a> Testleri çalıştırma
 Tüm testler, Çözümdeki tüm testleri bir grup veya seçtiğiniz test kümesini çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Bir çözümdeki tüm testleri çalıştırmak için tercih **tümünü Çalıştır**.

- Varsayılan bir grupta tüm testleri çalıştırmak için tercih **Çalıştır...**  ve sonra menüde grubu seçin.

- Seçilmiş test için kısayol menüsünü açın ve ardından çalıştırmak istediğiniz testleri tek tek seçin **seçili Testleri Çalıştır**.

  Testler çalışırken Test Gezgini penceresinin en üstündeki geçer/başarısız çubuğunda animasyon görünür. Tüm testler başarılı ya da herhangi bir test başarısız olursa kırmızıya döner test çalışması kılavuzumuzun geçer/başarısız çubuğu yeşile döner.

##  <a name="BKMK_Viewing_test_results"></a> Test sonuçlarını görüntüleme
 Test Gezgini çalıştırma, yazma ve testlerinizi yeniden çalıştırın gibi sonuçları gruplarında görüntüler. **başarısız testler**, **başarılı testler**, **Atlanan testler** ve **çalıştırma Testleri**. Test Gezgini görüntüler altındaki ayrıntılar bölmesi test özeti çalıştırın.

###  <a name="BKMK_Viewing_test_details"></a> Test ayrıntılarını görüntüleme
 Tek bir testin ayrıntılarını görüntülemek için testi seçin.

 Test ayrıntıları bölmesinde aşağıdaki bilgileri görüntüler:

- Kaynak dosya adı ve test yönteminin satır sayısı.

- Testin durumu.

- Test yöntemini çalıştırmak için geçen geçen süre.

  Test başarısız olursa, Ayrıntılar bölmesinde de görüntüler:

- Test için birim test çerçevesi tarafından döndürülen ileti.

- Yığın izleme zaman test başarısız oldu.

###  <a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Test yönteminin kaynak kodunu görüntüleme
 Visual Studio düzenleyicisinde bir test yöntemi için kaynak kodunu görüntülemek için testi seçin ve ardından **testi Aç** kısayol menüsünde (klavye: F12).

##  <a name="BKMK_Organizing_the_test_list"></a> Test listesini düzenleme

###  <a name="BKMK_Grouping_tests"></a> Testlerinizin gruplandırılması
 Varsayılan olarak, Test Gezgini'nin testlerinizi alt düğümleri olarak görüntüler **başarısız testler**, **başarılı testler**, **Atlanan testler** ve **çalıştırılmamış testler**.

|||
|-|-|
|![Test Gezgini Grup düğmesi](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Bunları yürütme süresini tarafından testlerinizi gruplamak için açık **Group By** listesindeki **süresi**. Seçin **Test sonucu** özgün gruplandırma için geçiş yapmak için.|

###  <a name="BKMK_Searching_and_filtering_the_test_list"></a> Aramayı ve filtrelemeyi test listesi
 Çok sayıda test varsa, belirtilen dizeyle listeyi filtrelemek için Test Gezgini arama kutusuna yazabilirsiniz. Arama dizesini girin önce Filtre listeden seçerek dizeleri belirli türlerdeki filtrenizle kısıtlayabilirsiniz.

 ![Arama filtre kategorisi](../test/media/ute-searchfilter.png "UTE_SearchFilter")

##  <a name="BKMK_Debugging_unit_tests"></a> Hata ayıklama birim testleri
 Test Gezgini, testleriniz için hata ayıklama oturumu başlatmak için kullanabilirsiniz. Kodunuzu Visual Studio hata ayıklayıcısı ile sorunsuz bir şekilde Adımlama, İleri ve geri birim testleri ve test altındaki projeye arasında sürer. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hatalarını ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde kesme noktası ayarlayın.

   > [!NOTE]
   >  Test yöntemleri herhangi bir sırada çalışabileceğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktalarını ayarlayın.

2. Test Gezgini'nde test yöntemlerini seçin ve ardından **seçilen Testlerde Hata Ayıkla** kısayol menüsünde.

   Hata ayıklayıcısı hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](../debugger/debugging-in-visual-studio.md).
