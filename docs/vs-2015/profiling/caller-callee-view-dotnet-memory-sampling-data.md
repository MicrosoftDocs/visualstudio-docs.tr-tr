---
title: Arayan-Aranan görünümü - .NET bellek örnekleme verileri | Microsoft Docs
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
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edeccd8318de36a09a9191a30274ff342cb7a41d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816794"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Arayan/Aranan görünümü - .NET bellek örnekleme verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arayan/Aranan görünümü seçili işlev ve üst ve alt işlevleri için profil oluşturma verilerini .NET bellek görüntüler. Arayan/Aranan görünümü üç Kılavuzlar içerir.  
  
 **Geçerli işlev** Orta kılavuzda görüntülenir ve bellek profili oluşturma seçili işlev hakkında bilgi gösterir. İşlev çağrıları tüm örneklenen değerlerini içerir.  
  
 **Geçerli işlevi çağırmış işlevler** üst kılavuz görüntülenir ve çağıran (üst) işlevi'öğesinden gelen çağrılar tarafından oluşturulmuş seçili (geçerli) işlevinin değeri miktarını gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuz görüntülenir ve bellek alt işlevi geçerli işlev tarafından çağrıldığında çağrılan (alt) işlevlerini seçili işlev için profil oluşturma gösterilmektedir.  
  
 Geçerli işlev satır yapmak için bir çağıran ya da çağrılan işlev satır çift tıklayın.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|İşlevi içeren modül yolu.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
|**İşlev adı**|İşlev tam adı.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**İşlev adresi**|İşlevin adresi.|  
|**Türü**|İşlevin bağlamı:<br /><br /> **0** -geçerli işlevi<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**düzeyi**|İşlev çağrısı ağacında derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kapsamlı ayırmalar**|-Geçerli işlev için profil oluşturma işlevi tarafından ayrılan nesnelerin sayısını çalıştırın. Bu sayı, çağrılan işlevlerde oluşturulan nesneleri içerir.<br />-Çağıran işlev için bu işleve çağrılar tarafından oluşturulan kapsamlı ayırmalar geçerli işlevin sayısı.<br />-Çağrılan işlev için geçerli işlev tarafından çağrılan örnekleri bu işlev tarafından ayrılan nesne sayısı. Çağrılan işlev tarafından çağrılan işlevler tarafından yapılan ayırmaları içerir.|  
|**Kapsamlı ayırma yüzdesi**|, Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin kapsamlı ayırmalar yoktu.|  
|**Dışlamalı ayırmalar**|-Geçerli işlev, işlev işlev gövdesinin kod yürütülürken, oluşturulan nesne sayısı için (diğer bir deyişle, ne işlev çağrı yığınının en üstünde zaman). Sayı, işlev tarafından çağrılan işlevler oluşturulan nesneleri içermez.<br />-Çağıran işlev için geçerli işlevin bu işlevin çağrılarından tarafından oluşturulan özel ayırmaların sayısı.<br />-Çağrılan işlev için geçerli işlev tarafından çağrılan örneklerini bu işlev tarafından oluşturulan nesne sayısı. Sayı çağrılan işlev tarafından çağrılan işlevler tarafından oluşturulmuş nesneleri içermez.|  
|**Dışlamalı ayırma yüzdesi**|, Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin kapsamlı ayırmalar yoktu.|  
|**Kapsamlı bayt**|-Geçerli işlev için profil oluşturma çalışması işlev tarafından ayrılan bellek bayt sayısı. Sayı ayrılan bellek bu işlev tarafından çağrılan işlevler içerir.<br />-Çağıran işlevin için oluşturulmuş geçerli işlevin kapsamlı bayt sayısı tarafından çağıran işlevi çağırır.<br />-Çağrılan işlev için çağrılarından geçerli işlev tarafından oluşturulan bu işlev örnekleri tarafından ayrılan bayt sayısı. Çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan bayt sayısını içerir.|  
|**Kapsamlı bayt yüzdesi**|, Profil oluşturma çalışmasında ayrılan tüm bellek bayt yüzdesi, bu işlevin kapsamlı ayırmalar yoktu.|  
|**Dışlamalı bayt**|-Geçerli işlev için profil oluşturma çalışması işlev tarafından ayrılan bellek bayt sayısı. Geçerli işlev tarafından çağrılan işlevler tarafından ayrılan bellek bu sayının içermez.<br />-Çağıran işlev için geçerli işlevi çağıran işleve çağrılar tarafından oluşturulan özel bayt sayısı.<br />-Çağrılan işlev için çağrılarından geçerli işlev tarafından oluşturulan işlev örnekleri tarafından ayrılan bayt sayısı. Çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan bayt sayısı dahil değildir.|  
|**Dışlamalı bayt yüzdesi**|, Profil oluşturma çalışmasında ayrılan tüm bellek bayt yüzdesi, bu işlevin dışlamalı ayırmalar yoktu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Arayan/Aranan görünümü - .NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Arayan / Aranan görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)   
 [Arayan/Aranan görünümü - izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)



