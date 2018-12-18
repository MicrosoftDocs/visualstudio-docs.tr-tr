---
title: Modüller görünümü - .NET bellek örnekleme verileri | Microsoft Docs
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
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b9a02e5579eb5dc82f2e1f21a10444c329a317f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765532"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modüller Görünümü - .NET Bellek Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme metodu kullanılarak toplanan .NET bellek ayırma verisini modülleri görünümünü bellek verileri profil oluşturma çalıştırmasını içinde yürütülen modülleri göre gruplandırır. Her bir hiyerarşik ağaç kökünde modülüdür. Modülündeki işlevlerin modülü düğümünün altında listelenir.  
  
 Bellek ayırma deyimleri kaynak dosya satır numaralarını işlevi düğümünün altında listelenir ve ayırmayı yönergeleri adresleri satırı düğümünün altında listelenir. Dahil ve hariç olan değerler her zaman satır verileri ve yönerge verileri için aynıdır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Modül, işlev, satır numarası veya yönerge adresi adı.|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|Modülün yolu.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Kapsamlı ayırmalar**|-Bir işlev için işlevi tarafından oluşturulan nesnelerin toplam sayısı. Bu işlev tarafından çağrılan işlevler oluşturulan nesneleri içerir.<br />-Bir modül için en az bir işlev modülünden ayrılan profil oluşturma yürütmesine nesneleri sayısı yürütülüyor. Modül işlevleri tarafından çağrılan işlevler oluşturulan nesneleri içerir.<br />-Bir satır veya yönergesi, çizgi veya yönergesi tarafından ayrılan nesnelerin toplam sayısı için.|  
|**Kapsamlı ayırma yüzdesi**|, Profil oluşturma çalışmasında ayrılan tüm nesneleri yüzdesi olan modülün, işlev, satır veya yönerge kapsamlı ayırmalar.|  
|**Dışlamalı ayırmalar**|-Geçerli işlev, işlev işlev gövdesinin kod yürütülürken, oluşturulan nesne sayısı için (diğer bir deyişle, ne işlev çağrı yığınının en üstünde zaman). Sayı, bu işlev tarafından çağrılan işlevler oluşturulan nesneleri içermez.<br />-Bir modül için modülündeki işlevlerin dışlamalı ayırmalar toplamı.<br />-Bir satır veya yönergesi, bu satırı veya yönergesi tarafından oluşturulmuş nesneleri toplam sayısı için.|  
|**Dışlamalı ayırma yüzdesi**|, Profil oluşturma çalışmasında ayrılan tüm nesneleri yüzdesi olan modülün, işlev, satır veya yönerge dışlamalı ayırmalar.|  
|**Kapsamlı bayt**|-Bir işlev için işlev tarafından ayrılan bayt sayısı. Bu işlev tarafından çağrılan işlevler ayrılan bayt sayısını içerir.<br />-Bir modül için en az bir işlev modülünden ayrılan bir profil oluşturma çalışmasında yer ayrılan bayt sayısı yürütülüyor. Modül işlevleri tarafından çağrılan tüm işlevleri oluşturulan nesneleri içerir.<br />-Bir satır veya yönergesi, çizgi veya yönergesi tarafından oluşturulan nesnelerin toplam sayısı için.|  
|**Kapsamlı bayt yüzdesi**|Kapsamlı bayt modülü, işlev, satır veya yönerge olan, profil oluşturma çalışmasında ayrılan tüm baytların yüzdesi.|  
|**Dışlamalı bayt**|-Bir işlev için işlev tarafından ayrılan bayt sayısı. Bu işlev tarafından çağrılan işlevlerdeki ayrılan bayt sayısı içermez.<br />-Bir modül için modülündeki işlevleri tarafından ayrılan özel baytları toplamı.<br />-Bir satır veya yönergesi, bu satırı veya yönergesi tarafından ayrılan nesnelerin toplam sayısı için.|  
|**Dışlamalı bayt yüzdesi**|Dışlamalı bayt modülü, işlev, satır veya yönerge olan, profil oluşturma çalışmasında ayrılan tüm baytların yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Modüller görünümü - izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller görünümü](../profiling/modules-view-sampling-data.md)   
 [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)



