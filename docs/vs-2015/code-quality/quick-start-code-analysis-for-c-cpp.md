---
title: 'Hızlı Başlangıç: C / C++ için Kod Analizi | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 56f14abab372a6a6e533675b070d420a4dfc7a5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758190"
---
# <a name="quick-start-code-analysis-for-cc"></a>Hızlı Başlangıç: C/C++ İçin Kod Çözümleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi düzenli olarak C veya C++ kodu çalıştırarak uygulamanızı kalitesini artırabilir. Bu yaygın sorunlar, iyi bir programlama uygulama ya da test sürecinde bulmak zor olan hataları ihlalleri bulmanıza yardımcı olabilir. Geçerli olan, ancak yine de siz veya kodunuzu kullanan diğer kişilerin sorunlarına neden olabilir, belirli bir kod desenleri için Kod Analizi arar çünkü kod çözümleme uyarıları derleyici hataları ve Uyarıları farklılık gösterir.  
  
## <a name="in-this-topic"></a>Bu konuda  
  
-   [Bir proje için kural kümelerini yapılandırma](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Kod analizini Çalıştır](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analiz ve kod çözümleme uyarıları çözün](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Kod Analizi uyarılarını gizleme](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [İş öğeleri için kod çözümleme uyarıları oluşturma](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Arama ve Kod Analizi sonuçlarını filtreleme](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a> Bir proje için kural kümelerini yapılandırma  
  
1.  İçinde **Çözüm Gezgini**, proje adı için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2.  Aşağıdaki adımlar isteğe bağlıdır:  
  
    1.  İçinde **yapılandırma** ve **Platform** listeleri, derleme yapılandırması ve hedef platformu seçin.  
  
    2.  Varsayılan olarak, Kod Analizi uyarıları otomatik olarak dış araçları tarafından oluşturulan kodu raporlamaz. Üretilen koddan gelen uyarıları görüntülemek için temizleyin **üretilen koddan gelen sonuçları Gizle** onay kutusu.  
  
        > [!NOTE]
        >  Bu seçenek hataları ve Uyarıları formları ve şablonlar görüntülendiğinde kod çözümleme hataları ve Uyarıları üretilen koddan gelen engellemez. Hem görüntüleyebilir ve bir form veya şablon için kaynak kodunu korumak.  
  
3.  Seçili yapılandırma kullanarak proje oluşturulan her zaman, Kod Analizi çalıştırmak için seçin **C/c++ derlemede kod çözümlemeyi etkinleştir** onay kutusu. Ayrıca kod analizini el ile açıp çalıştırabilirsiniz **Çözümle** menüsüne ve ardından **kod çözümlemeyi Çalıştır** *ProjectName*.  
  
4.  İçinde **bu kural kümesini Çalıştır** listesinde, aşağıdakilerden birini yapın:  
  
    -   Kullanmak istediğiniz bir kural kümesi seçin.  
  
    -   Seçin  **\<Gözat … >** var olan bir özel kural kümesini belirlemek için listesinde değil.  
  
    -   Bir özel kural kümesi tanımlar.  
  
         Daha fazla bilgi için [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Standart C/C++ kural kümeleri  
 Visual Studio iki standart yerel kod için kural kümesi içerir:  
  
|Kural kümesi|Açıklama|  
|--------------|-----------------|  
|Önerilen Microsoft yerel Minimum kurallar|Bu kural kümesi, olası güvenlik açıkları ve Uygulama Kilitlenmesi gibi yerel, kodunuzda en kritik sorunlara odaklanır. Doğal projeleriniz için oluşturduğunuz herhangi bir özel kural kümesi bu kural kümesini içermelidir.|  
|Microsoft yerel önerilen kurallar|Bu kural kümesi, çok çeşitli sorunları kapsar. Bu yerel en az önerilen kurallar Microsoft tüm kurallar içerir.|  
  
##  <a name="BKMK_Run"></a> Kod analizini Çalıştır  
 Proje özellik sayfaları, Kod Analizi sayfasında projenizi her çalıştırma için Kod Analizi yapılandırabilirsiniz. Kod analizini el ile çalıştırabilirsiniz.  
  
 Bir çözüm üzerinde kod analizi çalıştırmak için:  
  
- Üzerinde **derleme** menüsünde seçin **çözüm üzerinde kod analizini Çalıştır**.  
  
  Bir proje üzerinde kod analizi çalıştırmak için:  
  
- Çözüm Gezgini'nde proje adını seçin.  
  
- Üzerinde **derleme** menüsünde seçin **kod çözümlemeyi Çalıştır** *proje adı*.  
  
  Proje veya çözüm derlenir ve Kod Analizi çalıştırır. Sonuçları Kod Analizi penceresinde görünür.  
  
##  <a name="BKMK_Analyze"></a> Analiz ve kod çözümleme uyarıları çözün  
 Belirli bir uyarıyı çözümlemek için Kod Analizi penceresi içinde uyarı başlığı seçin. Sorun hakkında ek bilgileri görüntülemek için uyarı genişletir. Mümkün olduğunda, kod analizi, uyarıya yol açan analiz mantığı ve satır numaralarını görüntüler. Sorun için olası çözümleri dahil olmak üzere uyarı hakkında ayrıntılı bilgi için Yardım konusuna ileti MSND Kitaplığı'nda görüntülenecek Uyarı Kimliği'ni seçin.  
  
 Bir uyarı genişlettiğinizde, Visual Studio Kod Düzenleyicisi'nde uyarıya yol açan kod satırının vurgulanır.  
  
 Sorun anladıktan sonra kodunuzu çözebilirsiniz. Ardından uyarı artık Kod Analizi penceresi açılır ve düzeltmenizi henüz yeni uyarılar ortaya emin olmak için kod analizini yeniden çalıştırın.  
  
> [!TIP]
>  Kod analizinden kaynaklanan Kod Analizi penceresi yeniden çalıştırabilirsiniz. Seçin **Çözümle** düğmesine tıklayın ve analiz kapsamını seçin. Seçilen proje veya çözümün tamamını üzerinde analiz yeniden çalıştırabilirsiniz.  
  
##  <a name="BKMK_Suppress"></a> Kod Analizi uyarılarını gizleme  
 Kod Analizi uyarısı düzeltmemeyi ne zaman karar verebilirsiniz zamanlar vardır. Uyarı çözümleme sorunu kodunuzun tüm gerçek uygulamasında ortaya çıkacağını olasılık ile ilgili çok fazla değiştirilemeyen gerektirir karar verebilirsiniz. Veya uyarıda kullanılan analiz belirli bir içerik için uygun olduğunu düşündüğünüz. Artık Kod Analizi penceresinde görünecekleri bireysel uyarıları gösterilmemesini sağlayabilirsiniz.  
  
 Bir uyarıyı bastırmak için:  
  
1. Ayrıntılı bilgi görüntülenmiyorsa genişletmek için uyarı başlığı seçin.  
  
2. Seçin **eylemleri** Uyarı alt kısmındaki bağlantı.  
  
3. Seçin **ileti Gizle** seçip **içinde kaynak**.  
  
   Bir ileti gizleme ekler `#pragma warning (disable:` *WarningId* `)` , kod satırının için uyarı bastırır.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> İş öğeleri için kod çözümleme uyarıları oluşturma  
 Visual Studio içinden hatalardan oturum iş öğesi izleme özelliğini kullanabilirsiniz. Bu özelliği kullanmak için Team Foundation Server'ın bir örneğine bağlanmak gerekir.  
  
 **Bir veya daha fazla C/C++ kod uyarıları için bir iş öğesi oluşturmak için**  
  
1.  Kod Analizi penceresi genişletin ve Uyarıları seçin  
  
2.  Uyarılar için kısayol menüsünde **iş öğesi oluştur**, iş öğesi türünü seçin.  
  
3.  Visual Studio seçili uyarılar için tek bir iş öğesi oluşturur ve iş öğesini IDE'nin belge penceresinde görüntüler.  
  
4.  Ek bilgileri ekleyin ve ardından **çalışma öğesini Kaydet**.  
  
##  <a name="BKMK_Search"></a> Arama ve Kod Analizi sonuçlarını filtreleme  
 Uzun listesi uyarı iletilerini arayabilir ve çoklu proje çözümlerinde uyarıları filtreleyebilirsiniz.  
  
1.  **Başlık veya Uyarı Kimliği Filtresi uyarılarını için**: anahtar sözcüğü girin **filtre** metin kutusu.  
  
2.  **Proje tarafından Filtresi uyarılarını için**: çok projeli bir çözüm, listenin en üstünde bir veya daha fazla projelerinde seçin Kod Analizi penceresinin sağ. Tüm uyarıları görüntülemek için çözüm adı seçin.  
  
3.  **Filtre Uyarıları önem derecesine göre için**: varsayılan olarak, Kod Analizi ileti önem derecesi atanan **uyarı**. Bir veya daha fazla ileti olarak önemi atamak için **hata** özel bir kuralda ayarlayın. Seçin ya da **uyarı** veya **hata** ilgili önem atanmış olan iletileri görüntülemek için. Seçin **tüm** tüm iletileri görüntülemek için.



