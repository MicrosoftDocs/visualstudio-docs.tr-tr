---
title: 'Nasıl yapılır: Koleksiyon metotları seçme | Microsoft Docs'
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
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ca8018b572671f349c058e314b26f7897e421b9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727622"
---
# <a name="how-to-choose-collection-methods"></a>Nasıl yapılır: Koleksiyon Metotları Seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profil Araçları performans verilerini toplama üç yöntemi destekler: örnekleme, izleme ve eşzamanlılık. .NET bellek ayırma ve yaşam süresi verilerini toplamak için örnekleme veya Araçlar yöntemi de kullanabilirsiniz.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Performans oturumu kullanabilirsiniz **yöntemi** uygulamanız için en uygun koleksiyon yöntemi belirtmek için özellik. Performans Sihirbazı, performans Gezgini ya da bir performans oturumunun özellik sayfaları koleksiyonunu yöntemi ayarlayabilirsiniz. Komut satırı araçlarını kullanıyorsanız bkz [komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md) daha fazla bilgi için.  
  
## <a name="performance-wizard"></a>Performans Sihirbazı  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Performans Sihirbazı'nı kullanarak toplama yöntemi seçme  
  
-   Sihirbazın ilk sayfasında, aşağıdaki seçeneklerden birini seçin:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**CPU örnekleme**|İlk çözümleme ve CPU kullanımı sorunlarını analiz etmek için yararlı olan uygulama istatistikleri toplar.|  
|**İzleme**|Odaklı analiz için ve giriş/çıkış performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verilerini toplar.|  
|**.NET bellek ayırma**|Toplar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bellek ayırma verilerinin örnekleme profili oluşturma yöntemi kullanarak.|  
|**Eşzamanlılık**|Sayısal kaynak Çekişme verisi toplar.|  
  
## <a name="performance-explorer"></a>Performans Gezgini  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>Performans Gezgini'ni kullanarak koleksiyon yöntemi seçme  
  
1.  Üzerinde **performans Gezgini** araç yanındaki oka tıklayın **yöntemi** aşağı açılan listesi.  
  
2.  Tercih ettiğiniz bir koleksiyon Metoda tıklayın.  
  
## <a name="performance-session-property-pages"></a>Performans oturumu özellik sayfaları  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Performans oturumu özellikleri kullanarak örnekleme veya Araçlar yöntemini seçmek için  
  
1.  İçinde **performans Gezgini**, performans oturumu seçin.  
  
     Bir performans oturumu dosyası adı bir .psess uzantısına sahiptir.  
  
2.  Performans oturumu sağ tıklayın ve ardından **özellikleri**.  
  
3.  İçinde **özellik sayfaları**, tıklayın **genel**.  
  
4.  Tercih ettiğiniz bir koleksiyon Metoda tıklayın.  
  
    -   Örnekleme verileri toplanırken kullanılabilen diğer seçenekler hakkında daha fazla bilgi için bkz: [tarafından örnekleme kullanarak performans istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    -   Örnekleme verileri toplanırken kullanılabilen diğer seçenekler hakkında daha fazla bilgi için bkz: [tarafından ölçümlü izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Performans oturumu Özellikleri'ni kullanarak .NET bellek verileri toplama seçmek için  
  
1.  İçinde **performans Gezgini**, performans oturumu seçin.  
  
     Bir performans oturumu dosyası adı bir .psess uzantısına sahiptir.  
  
2.  Performans oturumu sağ tıklayın ve ardından **özellikleri**.  
  
3.  İçinde **özellik sayfaları**, tıklayın **genel**.  
  
4.  Tıklayın **örnekleme** veya **izleme**.  
  
5.  Tıklayın **toplamak .NET nesnesi ayırma bilgilerini** boyutuna ve sayısına toplanacak [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nesne ayırma.  
  
6.  (İsteğe bağlı) Tıklayın **ayrıca .NET nesnesi ömür bilgilerini toplayın** içinde nesne belleği yeniden çöp toplama kuşakları hakkında veri toplamak için.  
  
     .NET bellek verileri toplanırken kullanılabilen diğer seçenekler hakkında daha fazla bilgi için bkz: [toplama .NET bellek ayırma ve yaşam süresi verisi](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Performans oturumu Özellikleri'ni kullanarak eşzamanlılık verileri toplama seçmek için  
  
1.  İçinde **performans Gezgini**performans oturumu sağ tıklayın ve ardından **özellikleri**.  
  
2.  İçinde **özellik sayfaları**, tıklayın **genel**.  
  
3.  Tıklayın **eşzamanlılık**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)   
 [Performans Oturumu Özellikleri](../profiling/performance-session-properties.md)



