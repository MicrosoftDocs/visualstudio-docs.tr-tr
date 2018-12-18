---
title: Özet görünümü | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdacfcba18d465685053cdea4581a5806c25db9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757323"
---
# <a name="summary-view"></a>Özet Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özet görünümü profil oluşturma yürütmesine en pahalı performans işlevleri veya nesneler hakkındaki bilgileri görüntüler. Bu görünümde bir zaman çizelgesi grafiği sağlar ve profil oluşturma yöntemine performans ölçümleri temelinde en pahalı işlevleri veya nesneleri iki veya daha fazla listesini alan. Bu görünümdeki veriler kullanılan profil oluşturma yöntemine bağlıdır (örnekleme, izleme veya eşzamanlılık) ve .NET bellek ayırma olup toplanmadı.  
  
 Eşzamanlılık verileri Özet görünümünü dışındaki tüm Özet görünümleri için profil oluşturma gerçekleşen zaman içinde oluşturulan uygulamanın işlemci (CPU) kullanımı Özet görünümünde zaman çizelgesi grafiği gösterir.  
  
-   Grafikte zaman kesimini belirtirseniz, o kesimi için verileri yeniden Çözümle veya belirtilen segmente zaman çizelgesi görünen yakınlaştırma. Daha fazla bilgi için [nasıl yapılır: Özet zaman çizelgesinden rapor görünümlerini filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
-   İşlev için işlev Ayrıntıları görünümünde açmak için bir Özet görünümü listesindeki bir işlev tıklayabilirsiniz. Ayrıca, diğer görünüm seçenekleri işlevi de sağ tıklayabilirsiniz.  
  
-   Özet görünümü listelerinde görüntülenen öğe sayısını değiştirmek için açın **Araçları** menüsünde **seçenekleri**ve ardından **performans araçları**. Altında **genel ayarlar**, değişiklik **Özet görünümündeki fonksiyonların sayısı** ayarı.  
  
## <a name="notifications-links"></a>Bildirimleri bağlantıları  
 Bildirim listesinde rapor için görüntüleme seçeneklerini ayarlamak için bağlantıları tıklatabilirsiniz. Zaman Çizelgesi grafiği sağa listesidir.  
  
|||  
|-|-|  
|**Kullanıcı olmayan kod Göster**<br /><br /> **Yalnızca benim kodumu Göster**|Yerel kod veya izleme metodunu kullanarak toplanan veriyi profil oluşturma için kullanılabilir değil. Yalnızca kullanıcı kodunun verilerini görüntüleme arasında geçiş yapar (**sadece benim kodumu Göster**) ve sistem kod dahil olmak üzere tüm koddan verileri görüntüleme (**Göster kullanıcı olmayan kod**). Varsayılan olarak, veriler, kullanıcı kodu sınırlıdır. Bu ayarı değiştirmek için bkz [nasıl yapılır: görüntü yalnızca benim kodum için filtre profil oluşturma araçları rapor görünümlerini](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Rehberi görüntüle**|Performans kural uyarılar görüntüler **hata listesi** penceresi. Daha fazla bilgi için [verileri çözümlemek için performans kurallarını kullanma](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## <a name="report"></a>Rapor  
 Farklı görünümlerini açmak için ve karşılaştırmak, Kaydet veya raporu filtrelemek için rapor listesi bağlantılar tıklayabilirsiniz. Zaman Çizelgesi grafiği sağa listesidir.  
  
|||  
|-|-|  
|**Kırpılmış çağrı ağacını Göster**|Çağrı ağacı Görünümü'nde en pahalı yürütme yollarını görüntüler. Daha fazla bilgi için [çağrı ağacı görünümü](../profiling/call-tree-view.md).|  
|**Etkin satırları göster**|Araçlar yöntemini kullanarak toplanan veriyi profil oluşturma için kullanılamaz. Satırlar görünümünde en pahalı kaynak kodu satırlarını görüntüler. Daha fazla bilgi için [satırlar görünümü](../profiling/lines-view.md).|  
|**Raporları Karşılaştır**|Görüntüler **seçin analiz dosyaları karşılaştırma** geçerli dosyayı karşılaştırmak için başka bir profil oluşturma veri dosyasını belirtebileceğiniz iletişim kutusu. Daha fazla bilgi için [performans veri dosyalarını karşılaştırma](../profiling/comparing-performance-data-files.md).|  
|**Rapor verilerini dışarı aktar**|Görüntüler **dışarı aktarma raporu** virgülle ayrılmış değer (.csv) veya .xml dosyaları olarak kaydetmek için bir veya daha fazla rapor görünümlerini belirtebileceğiniz iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: profil oluşturma araçları raporları dışarı aktarma](http://msdn.microsoft.com/en-us/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Analiz edilen Raporu Kaydet**|Geçerli profil oluşturma veri dosyasını arabirimdeki daha hızlı açılır .vsps dosyası olarak kaydeder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Daha fazla bilgi için [nasıl yapılır: Analiz profil oluşturma veri dosyaları Kaydet](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Rapor verilerini Filtrele**|Verileri rapor görünümünde sınırlandırmak için ölçüt belirleyebileceğiniz profil oluşturma rapor filtresi bölmesi görüntülenir. Daha fazla bilgi için [performans raporu Görünüm Filtresi](../profiling/performance-report-view-filter.md)|  
|**Tam ekrana geç**|Rapor görünümü için tam ekran moduna geçiş yapar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özet görünümü](../profiling/summary-view-sampling-data.md)   
 [Özet görünümü](../profiling/summary-view-instrumentation-data.md)   
 [Özet Görünümü](../profiling/summary-view-dotnet-memory-data.md)



