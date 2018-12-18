---
title: Performans raporuna genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 455c05ae0d8645040d3f9eac68d20f57138df5cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830775"
---
# <a name="performance-report-overview"></a>Performans raporuna genel bakış
Bir performans oturumu profil oluşturma verilerini görüntüleyebilirsiniz **performans raporu** penceresi Visual Studio Team System geliştirme sürümü tümleşik geliştirme ortamının (IDE). Profil oluşturma verilerinin .vsp .vsps dosyalarında kaydedilir. Rapor görünümü windows görüntüleme ve uygulama performans sorunlarını analiz etmenize olanak sağlar.  
  
> [!CAUTION]
>  Bir profil oluşturma veri dosyasını, bilgisayar adı gibi hassas bilgileri, işletim sistemi, dosya yolları, bellek bilgileri ve diğer bilgisayar kurulum bilgilerini sürümünü içerir. Verilerin hem de kendi yerel dağıtım üzerinde kesin denetim korumanız gerekir. *vsp* biçimi ve için dışarı aktarılmasından sonra bir. *CSV* veya. *XML* dosya.  
>   
>  Olay izleme verileri performans oturumu bir parçası olarak toplanır, ek bilgiler olay izleme günlüğü görünebilir (. *etl*) dosyası. Bu bilgiler, etki alanı ve kullanıcı adınızı içerir; Bu nedenle, günlük dosyasının dağıtım üzerinde kesin denetim korumanız gerekir.  
  
## <a name="performance-report-window"></a>Performans Rapor penceresi  
 Performans raporu görüntüleyin, yönetin ve performans verilerini filtrelemek için kullanılan bir araç penceresidir ve özelleştirilebilir sorgu denetimi içerir.  
  
 Ana Performans Raporu penceresi araç çubuğunda, her görünüm erişebilirsiniz. Yanındaki oka tıklayın **Geçerli Görünüm** listesi görüntüleyin ve mevcut olan tek bir görünüm seçin.  
  
 Performans Raporu penceresi, aşağıdaki veri görünümleri sağlar:  
  
### <a name="summary-view"></a>Özet Görünümü  
 Varsayılan olarak, profil oluşturma verisi Özet görünümünde görüntülenir. Bu görünüm, performans sorunlarını araştırmasını bir başlangıç noktasıdır. Özet görünümünde her satırında, işlev veya modül adı sağ tıklayarak ayrıntılı görünümlerine taşıyabilirsiniz. Daha fazla bilgi için [özeti görünümünü](../profiling/summary-view.md).  
  
### <a name="callercallee-view"></a>Arayan/Aranan görünümü  
 Arayan/Aranan görünümü tek bir işlevi için çağrı ağacı görüntüler. Görünüm, üç bölüme ayrılır:  
  
- Hedef işlevi ortasında görünümü görüntülenir.  
  
- ' % S'işlevi (arayanlar) olarak adlandırılan işlevler hedef işlevi görüntülenir.  
  
- (Çağrılanlar) hedef işlev tarafından çağrılmış işlevler hedefin altında görüntülenir.  
  
  Çağrılan listesi veya çağrılan listenin herhangi bir işlevde çift tıklayarak farklı bir işlev seçebilirsiniz. Daha fazla bilgi için [arayan/Aranan görünümü](../profiling/caller-callee-view.md).  
  
### <a name="call-tree-view"></a>Çağrı Ağacı Görünümü  
 Çağrı ağacı görünümü, profili oluşturulan uygulamada geçiş işlev yürütme yollarını görüntüler. Ağacının kökü, uygulamanın veya bileşenin içine giriş noktasıdır. Her işlev düğüm, tüm bu işlev çağrıları ile ilgili performans verilerini ve onu çağıran işlevlerini listeler.  
  
 Çağrı ağacı görünümü ayrıca genişletin ve en çok zaman harcanan veya sık örneklenen bir işlev yürütme yolunu vurgulayın. En etkin yol görüntülemek için işlev sağ tıklayın ve ardından **etkin yolu Genişlet**. Daha fazla bilgi için [çağrı ağacı görünümü](../profiling/call-tree-view.md).  
  
### <a name="process-view"></a>İşlem Görünümü  
 İşlem görünümü, her bir işlem ve profili oluşturulmuş bir iş parçacığı için performans verilerini görüntüler. Daha fazla bilgi için [işlem görünümü](../profiling/process-view.md).  
  
### <a name="modules-view"></a>Modüller Görünümü  
 Modüller görünümü proje modülleri listeler ve her bir modül için profil oluşturma verilerini gösterir. Genişlet veya Daralt işlevi profil oluşturma verilerini görüntülemek için modül adı. Örnekleme kullanarak verileri toplandığında, profil oluşturma verilerini kaynak kodu satır, yönerge işaretçisini de kullanılabilir. Daha fazla bilgi için [modüller görünümü](../profiling/modules-view.md).  
  
### <a name="functions-view"></a>İşlevler Görünümü  
 İşlevler görünümü, profil oluşturma sırasında çağrılan işlevleri listeler. Daha fazla bilgi için [işlevler görünümü](../profiling/functions-view.md).  
  
### <a name="line-view"></a>Satır görünümü  
 Satırlar görünümü, örnekleme profil oluşturma sırasında yürütülen belirli kaynak kod satırlarına görüntülemenize olanak tanır. Daha fazla bilgi için [satırlar görünümü](../profiling/lines-view.md).  
  
### <a name="instruction-pointer-ip-view"></a>Yönerge işaretçisi (IP) görünümü  
 Yönerge işaretçisi görünümü, örnekleme profil oluşturma sırasında yürütülen belirli yönergeleri görüntülemenize olanak tanır. Daha fazla bilgi için [yönerge işaretçileri (IP) görünümü](../profiling/instruction-pointers-ips-view.md).  
  
### <a name="allocation-view"></a>Ayırma görünümü  
 Ayırma görünümü kullanılabilir olmadığını **toplamak .NET nesne ayırma** bağlı seçili **genel** sayfasının **performans oturumu** Özellikleri iletişim kutusu. Bkz: [performans oturumuna genel bakış](../profiling/performance-session-overview.md). Ayırma görünümü, uygulama veya bileşen tarafından ayrılan .NET nesneleri listeler. Çağrı ağacı, bir nesne satır genişletildiğinde görüntülenir. Çağrı ağacı içinde nesne oluşturma sonuçlanan yürütme yolları gösterir. Her işlev çağrısı ağacında dahil ve hariç ayırmaların sayısı ilgili bilgiler de gösterilir. Ayırma görünümü ayrıca genişletin ve nesnelerin en büyük sayı ayrılan bir işlev yürütme yolunu vurgulayın. En etkin yol görüntülemek için işlev sağ tıklayın ve ardından **etkin yolu Genişlet**. Daha fazla bilgi için [toplamak .NET bellek ayırma ve yaşam süresi verilerini](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) ve [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md).  
  
### <a name="objects-lifetime-view"></a>Nesne ömrü görünümü  
 Nesne ömrü görünümü kullanılabilir olmadığını **toplamak .NET nesnesi ayırma bilgilerini** ve **ayrıca .NET nesnesi ömür bilgilerini toplayın** bağlı seçili **genel**sayfasında **performans oturumu** Özellikleri iletişim kutusu.  
  
 Nesne ömrü görünümü, her türdeki örneklerin toplam sayısı ve her çöp toplama kuşağında nesne sayısını görüntüler. Daha fazla bilgi için [nesne ömrü görünümü](../profiling/object-lifetime-view.md).  
  
## <a name="customizable-filter-control"></a>Özelleştirilebilir filtre denetimi  
 Özelleştirilebilir filtre denetimi şu seçeneklere sahiptir:  
  
-   **Filtre alma** -özel önceden kaydedilmiş bir sorgu alır.  
  
-   **Filtre dışarı** -özel sorgu belirtilen konuma kaydeder.  
  
-   **Sorguyu** -sorgu özel sorgu denetimde görüntülenen gibi çalışır.  
  
-   **Sorguyu Durdur** -çalışmakta olan bir sorgu yürütülmesini durdurur. Sorgu çalışıyorsa bu düğmesi kullanılamaz.  
  
-   **Sorgu Göster** -gösterir/Özel sorgu denetimi gizler.  
  
-   **Analyzed Kaydet** -raporu geçerli Analizine birlikte bir .vsps dosyası olarak kaydeder.  
  
-   **Dışarı aktarma** -geçerli raporda kaydeder. CVS olarak biçimlendirilmiş veya. XML biçimli dosya için farklı görünümlerini kaydetme seçeneği ile.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)   
 [Performans raporu görünümleri](../profiling/performance-report-views.md)