---
title: Kaydetme ve dışarı aktarma performans araçları verilerini | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9b96ae54c91e80fe34c817f710cb400e61f9876
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768500"
---
# <a name="saving-and-exporting-performance-tools-data"></a>Verileri kaydetme ve dışarı aktarma performans araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, kaydedin ve performans veri dosyalarını dışarı aktarma açıklanmaktadır.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Nasıl yapılır: performans veri dosyalarını analiz edilmiş raporu dosyaları olarak kaydedin  
 Filtrelenmiş veya filtrelenmemiş görünümlerini profil oluşturma veri (.vsp) dosyalarını analiz edilmiş raporu (.vsps) dosyası olarak kaydedebilirsiniz. Bir analiz edilmiş raporu dosya rapor görünümü penceresindeki görüntülenebilir ve özgün .vsp dosyasından daha önemli ölçüde daha küçük. Ancak, verileri .vsps dosyası için bir filtre uygulayamazsınız. Tümleşik geliştirme ortamında (IDE) dosyayı açmaya gerek kalmadan performans Gezgini'nden bir analiz edilmiş raporu dosyası oluşturabilir veya açın ve .vsp dosyasının filtreleyebilir ve ardından sonuçları kaydedin.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Performans Gezgini'nden bir analiz edilen performans raporu kaydetmek için  
  
1.  Altında **raporları**, analiz edin ve ardından istediğiniz profil oluşturma veri dosyasını sağ tıklatın **Kaydet analiz**.  
  
2.  İçinde **analiz verilerini Kaydet** iletişim kutusunda, dizini belirtin ve ardından dosya adını yazın.  
  
3.  Tıklayın **kaydedin.**  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Rapor Görünümü penceresinden bir performans analiz raporu kaydetmek için  
  
1.  Profil oluşturma veri (.vsp) dosyasının rapor görünümü penceresi açın.  
  
2.  (İsteğe bağlı) Verilere filtre uygulayın. Daha fazla bilgi için [performans raporu Görünüm Filtresi](../profiling/performance-report-view-filter.md).  
  
3.  Tıklayın **Kaydet analiz** rapor görünümü penceresi araç çubuğu üzerinde.  
  
4.  İçinde **analiz verilerini Kaydet** iletişim kutusunda, dizini belirtin ve ardından dosya adını yazın.  
  
5.  Tıklayın **kaydedin.**  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Nasıl yapılır: dışarı aktarma profil oluşturma araçları raporları bir. XML veya. CSV dosyası  
 Bir veya daha fazla rapor görünümlerini .vsp dosyasının veya .vsps profil oluşturma veri dosyası ya da bir virgülle ayrılmış olarak veya bir XML dosyasını dışarı aktarabilirsiniz. Rapor Görünümü penceresi verileri dışarı veya rapor görünümlerini tüm veri dosyasından dışarı aktarabilirsiniz önce filtreleyebilirsiniz **performans Gezgini** penceresi.  
  
> [!NOTE]
>  Ayrıca, kopyalayın ve rapor görünümü penceresi seçili satırları sekmeyle ayrılmış değerler olarak yapıştırın.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Performans Gezgini penceresinden performans raporları dışarı aktarmak için  
  
1.  İçinde **performans Gezgini**, raporu seçin ve ardından sağ tıklayıp **dışarı**.  
  
     **Dışarı aktarma raporu** iletişim kutusu görüntülenir.  
  
2.  Dışarı aktarmak istediğiniz rapor görünümleri seçin.  
  
3.  Altında **önek raporu ile**, eklemek için rapor adı öneki belirtin.  
  
4.  Altında **dışarı aktarılan rapor konumu**, dizini belirtin.  
  
5.  Altında **dışarı aktarılan raporun biçimi**, (virgülle ayrılmış) (*.csv) seçin ya da XML verisi (\*.xml).  
  
6.  Tıklayın **dışarı**.  
  
     Her rapor görünümü adlı ayrı bir dosyaya kaydedilir \<önek > _\<rapor görünümü adı >.\< CSV&#124;xml >  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Rapor Görünümü penceresinden performans raporları dışarı aktarmak için  
  
1.  .Vsp dosyasının rapor görünümü penceresi açın.  
  
2.  (İsteğe bağlı) Verilere filtre uygulayın. Daha fazla bilgi için [performans raporu Görünüm Filtresi](../profiling/performance-report-view-filter.md).  
  
3.  Tıklayın **dışarı aktarma raporu** rapor görünümü penceresi araç çubuğu üzerinde.  
  
4.  Dışarı aktarmak istediğiniz rapor görünümleri seçin.  
  
5.  Altında **önek raporu ile**, eklemek için rapor adı öneki belirtin.  
  
6.  Altında **dışarı aktarılan rapor konumu**, dizini belirtin.  
  
7.  Altında **dışarı aktarılan raporun biçimi**, (virgülle ayrılmış) (*.csv) seçin ya da XML verisi (\*.xml).  
  
8.  Tıklayın **dışarı**.  
  
     Her rapor görünümü adlı ayrı bir dosyaya kaydedilir \<önek > _\<rapor görünümü adı >.\< CSV&#124;xml >  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)   
 [Veri Araçları performansını analiz etme](../profiling/analyzing-performance-tools-data.md)   
 [Performans veri dosyalarını karşılaştırma](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



