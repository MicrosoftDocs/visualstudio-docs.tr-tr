---
title: Kod ölçüm verileri ile çalışma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ca9d384b8c7b6d49e44826c65a156d715baa0786
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775894"
---
# <a name="working-with-code-metrics-data"></a>Kod Ölçüm Verileri ile çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Kod ölçümleri sonuçları** penceresi kod ölçümleri analiz tarafından oluşturulan verileri görüntüler. Kod ölçüm verileri değerleri hakkında daha fazla bilgi için bkz: [kod ölçüm değerleri](../code-quality/code-metrics-values.md).  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Kod ölçümleri sonuçları penceresi](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Kod ölçümleri sonuçları görüntüleme](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Kod ölçümleri sonuçlarını filtreleme](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Ekleme, kaldırma ve veri sütunlarını yeniden düzenleme](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Pano veya Excel veri kopyalama](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Kod ölçüm sonuçlarına göre iş öğesi oluşturma](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Kod ölçümleri sonuçları penceresi  
 **Kod ölçümleri sonuçları** penceresinin hesaplanan sonuçlar görüntülenecek sütunlar ve üstündeki araç vardır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Hiyerarşi**|**Hiyerarşi** sütun Genişlet veya daralt, istediğiniz ayrıntı düzeyini görmek için kod hiyerarşi ağaç görünümünü içerir. Kalan sütunlardan hesaplanan sonuçları gösterilmektedir. İstediğiniz sonuç sütunları düzenlemek ya da gizleme.|  
|**Bakım**|**Bakım** sütun, sayısal bir sonuç yanı sıra bir simge içerir. Yeşil bir simge bakım görece yüksek derecede gösterir. Sarı bir simge, bir devamlılık orta derecede gösterir. Düşük bakım ve olası bir sorun nokta kırmızı bir simge belirtir. Bu renk göstergeleri AvoidUnmaintainableCode FxCop kural tarafından kullanılan önem derecesi kategorilerine karşılık gelir. Bu kural, 10, 20'den daha yüksek bir dizindir dizini 10 ve 20 ve ne bir hata veya uyarı arasında ise bir uyarı daha düşük bakım dizini ise hata tetikler. Bakım dizini olan üç ölçüm bir Birleştirici: döngüzel karmaşıklığına, kod ve hesaplama karmaşıklığı satır. Değerleri birimleri ifade değil.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a> Kod ölçümleri sonuçları görüntüleme  
 Kod ölçümleri sonuçları oluşturma, kod ölçümleri sonuçları penceresi otomatik olarak görüntülenir. Ayrıca, herhangi bir zamanda penceresinde görüntüleyebilirsiniz.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Kod ölçümleri sonuçları penceresini görüntülemek için  
  
-   Üzerinde **Çözümle** menüsünde tıklatın **Windows** ve ardından **kod ölçümleri sonuçları**.  
  
     \- veya -  
  
-   Üzerinde **görünümü** menüsünde **diğer Windows** ve ardından **kod ölçümleri sonuçları**.  
  
     Sonuç içerdiğinde bile, kod ölçümleri sonuçları penceresi görüntülenir.  
  
#### <a name="to-view-code-metrics-details"></a>Kod ölçümleri görüntülemek için ayrıntıları  
  
-   Kod ölçümleri sonuçları oluşturulduysa ağacında genişletin **hiyerarşi** sütun.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a> Kod ölçümleri sonuçlarını filtreleme  
 Görüntülenen sonuçlarını filtreleyebilirsiniz **kod ölçümleri sonuçları** üstündeki araç çubuğunu kullanarak pencere. Örneğin, bir bakım dizini 65 aşağıda olan sonuçları görmek isteyebilirsiniz.  
  
 **Filtre** açılan kutusu sonuçları sütun adlarını içerir. Bir filtre tanımlandığında, listenin bir girinti birlikte eklenir. Liste, tanımlanan son on filtreler içerebilir.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Kod ölçümleri sonuçları filtrelemek için  
  
1.  Gelen **filtre** listesinde, sütun adı seçin.  
  
2.  İçinde **Min**, görüntülenecek en düşük değerini yazın.  
  
3.  İçinde **Max**, görüntülenecek maksimum değeri yazın.  
  
4.  Tıklayın **Filtre Uygula** düğmesi.  
  
5.  Sonuç ayrıntıları görmek için hiyerarşi ağacı genişletin.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Ekleme, kaldırma ve veri sütunlarını yeniden düzenleme  
 Ekleyebilir ve sütunları Kaldır sonuçları **kod ölçümleri sonuçları** penceresi. Ayrıca, istediğiniz sırayla görünecekleri sonuçları sütunları yeniden düzenleyebilirsiniz.  
  
#### <a name="to-remove-a-column"></a>Bir sütunu kaldırmak için  
  
1.  Tıklayın **sütunları Ekle/Kaldır** düğmesi.  
  
     \- veya -  
  
     Herhangi bir sütunun başlığına sağ tıklayın ve ardından **sütunları Ekle/Kaldır**.  
  
2.  İçinde **sütunları Ekle/Kaldır** iletişim kutusu, onay kutusunu temizleyerek sütunu kaldırın ve ardından istediğiniz **Tamam**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Önceden kaldırılan bir sütun eklemek için  
  
1.  Tıklayın **sütunları Ekle/Kaldır** düğmesi.  
  
     \- veya -  
  
     Herhangi bir sütunun başlığına sağ tıklayın ve ardından **sütunları Ekle/Kaldır**.  
  
2.  İçinde **sütunları Ekle/Kaldır** iletişim kutusunda, eklemek ve ardından istediğiniz sütun için onay kutusunu seçin **Tamam**.  
  
#### <a name="to-rearrange-columns"></a>Sütunları yeniden sıralamak için  
  
1.  Tıklayın **sütunları Ekle/Kaldır** düğmesi.  
  
     \- veya -  
  
     Herhangi bir sütunun başlığına sağ tıklayın ve ardından **sütunları Ekle/Kaldır**.  
  
2.  İçinde **sütunları Ekle/Kaldır** iletişim kutusunda, taşıyabilir ve ardından yukarı veya aşağı oka tıklayın istediğiniz sütunu seçin.  
  
3.  Sütun, istediğiniz yerde konumlandırıldığında tıklayın **Tamam**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Pano veya Excel veri kopyalama  
 Seçin ve seçili bir satır kod ölçümleri verileri, adı ve her veri sütununun değeri için bir satır içeren bir metin dizesi olarak panoya kopyalayın. Ayrıca **listeyi Microsoft Excel'de Aç** tüm kod ölçümleri sonuçları bir Excel elektronik tablosuna dışarı aktarmak için  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Kod ölçüm sonuçlarına göre iş öğesi oluşturma  
 Oluşturabileceğiniz bir [!INCLUDE[esprfound](../includes/esprfound-md.md)] temel alan iş öğesi sonuçlanıyor **kod ölçüm sonuçlarını** penceresi. İş öğesi oluşturulduğunda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otomatik olarak bir başlık girer **başlık** alan ve kod ölçümleri verileri altında **geçmişi** sekmesi.  
  
 İş öğeleri oluşturma hakkında daha fazla bilgi için bkz. [iş öğesi oluşturma &#91;yeniden yönlendirilen&#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Bir sonuca bağlı bir iş öğesi oluşturmak için  
  
1.  Bir sonuca sağ tıklayın.  
  
2.  İşaret **iş öğesi oluştur**ve ardından oluşturmak istediğiniz iş öğesinin türüne tıklayın (**hata**, **görev**, vb.).  
  
3.  Tüm gerekli alanları doldurarak iş öğesi formu tamamlayın.  
  
4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** iş öğesini kaydetmek için.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Bir sonuca bağlı bir hata oluşturmak için  
  
1.  Seçmek için sonuca tıklayın.  
  
2.  Tıklayın **iş öğesi oluşturma** düğmesi.  
  
3.  Tüm gerekli alanları doldurarak iş öğesi formu tamamlayın.  
  
4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** iş öğesini kaydetmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ölçüm karmaşıklığı ve yönetilen kod bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Nasıl yapılır: Kod Ölçümleri Verileri Üretme](../code-quality/how-to-generate-code-metrics-data.md)



