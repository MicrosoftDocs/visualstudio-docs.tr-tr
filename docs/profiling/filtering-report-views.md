---
title: Rapor görünümlerini filtreleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf8e172f6693b4efcff1cfff3eb8c79178bb9f90
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919175"
---
# <a name="filter-report-views"></a>Rapor görünümlerini filtreleme
Profil oluşturma performans raporu görünümlerde görüntülenmesi ve rapor dosyasına dışarı profil oluşturma verileri sınırlamak için veri dosyaları için filtre uygulayabilirsiniz. Bir rapor için zaman damgası değerlerini arasındaki verileri sınırlayabilir ve belirli işlem ve iş parçacıkları için verileri sınırlayabilirsiniz. Filtreler bir dosyaya kaydedin ve kaydedilmiş filtre içeri aktararak Bu filtre üzerinde farklı bir profil oluşturma veri dosyasını oluşturun.  
  
 Bir rapor için zaman diliminin Özet görünümü grafik zaman çizelgesini kullanarak da sınırlayabilirsiniz. Bkz: [nasıl yapılır: Özet zaman çizelgesinden rapor görünümlerini filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Sistem ve üçüncü taraf kodu bir raporundan dışlamak için bkz: [nasıl yapılır: Filtre profil oluşturma Araçlar rapor görünümleri için sadece benim kodumu görüntüle](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-profiler-report-filter"></a>Bir profil oluşturucu rapor filtresi oluşturmak için  
  
1.  Performans Raporu Görünüm Filtresi penceresi görüntülenmiyorsa, tıklayın **Göster filtre** performans rapor görünümü araç.  
  
     Performans Raporu Görünüm filtresi bir tablodur. Tablodaki her satır bir filtre yan tümcesi temsil eder. Bir filtre için istediğiniz sayıda yan tümce ekleyebilirsiniz.  
  
2.  Filtre eklemek istediğiniz her yan tümce için bir satır aşağıdaki alanlarda değerleri girin veya seçin.  
  
    |Alan|Açıklama|  
    |-----------|-----------------|  
    |**Ve/veya**|Seçin **ve** eşleşiyorsa bir sonuç bu yan tümce hem de sonraki yan tümcesi her ikisi de true olmalıdır. Seçin **veya** eşleşiyorsa bir sonucu veya bu yan tümce hem de sonraki yan tümcesi True olabilir.|  
    |**Alan**|Filtre yan tümcesi veri alanlarının görüntülenen listeden kullanmak için rapor alanı seçin.|  
    |**İşleci**|Alan ve değer arasında yan tümcesinde istediğiniz ilişkiyi belirtir bir işleç seçin.<br /><br /> = Eşittir<br /><br /> <> Eşit değildir<br /><br /> < Küçüktür<br /><br /> > Büyüktür<br /><br /> < = küçüktür veya eşittir<br /><br /> > = büyüktür veya eşittir|  
    |**Değer**|Aranacak bir değer girin veya seçin. Bazı alanları, alan için kullanılabilen değerleri listeler.|  
  
  
#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Bir profil oluşturucu rapor filtresi işaretleri rapor görünümünde oluşturmak için  
  
1. Seçin **işaretleri** gelen **Geçerli Görünüm** performans raporu Görünüm araç çubuğundaki listesi.  
  
    İşaretler profil oluşturucu rapor görüntülenir.  
  
2. ETW ve örnekleme bile, raporun başlangıç noktası olarak kullanmak istediğiniz seçin.  
  
3. Tuşuna basın ve CTRL basılı tutun ve raporun bitiş noktası olarak kullanmak istediğiniz bir etkinliğe tıklayın.  
  
4. Sağ tıklayın ve sonra aşağıdaki seçeneklerden birine tıklayın:  
  
   - **Filtre işaretlerini Ekle** işareti sütunu Filtre alanını kullanan filtre yan tümcesi oluşturur.  
  
   - **Üzerinde zaman damgalarına Filtre Ekle** içindeki zaman damgası milisaniye sütun filtresi alan olarak kullanan bir filtre yan tümcesi oluşturur.  
  
     İki seçenek, aynı başlangıç ve bitiş noktalarını geçerli veri dosyası filtreleyin. İki seçenekten birini diğer raporlarda kullanmak için filtreyi dışarı aktarırsanız daha iyi olabilir.  
  
#### <a name="to-load-an-existing-filter-from-a-file"></a>Bir dosyadan varolan bir filtreyi yüklemek için  
  
1.  Performans rapor görünümü araç çubuğunda **içeri aktarma filtre**.  
  
     **Yük filtre** iletişim kutusu görüntülenir.  
  
2.  Filtre (.vspf) dosyası yüklemek için konum ve dosya adını belirtin.  
  
#### <a name="to-execute-a-filter"></a>Bir filtre yürütmek için  
  
-   Performans rapor görünümü araç çubuğunda **yürütme filtre**.  
  
#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Yürütülmesi çok uzun sürecek bir filtre durdurmak için  
  
-   Performans rapor görünümü araç çubuğunda **Durdur filtre**.  
  
#### <a name="to-remove-a-filter-on-a-report-view"></a>Rapor görünümünde filtreyi kaldırmak için  
  
1.  Performans Raporu Görünüm filtresi yan tümcelerinde satırlarını silin.  
  
2.  Performans rapor görünümü araç çubuğunda **yürütme filtre**.  
  
#### <a name="to-save-a-filter-to-a-file"></a>Bir filtre bir dosyaya kaydetmek için  
  
1.  Performans rapor görünümü araç çubuğunda **dışarı aktarma filtre**.  
  
     **Kaydet filtre** iletişim kutusu görüntülenir.  
  
2.  Filtre (.vspf) dosyası kaydetmek için konum ve dosya adını belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans Araçları Rapor Görünümlerini Özelleştirme](../profiling/customizing-performance-tools-report-views.md)