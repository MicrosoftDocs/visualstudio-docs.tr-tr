---
title: İşlevler görünümü - .NET bellek izleme verileri | Microsoft Docs
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
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bacc61ec9c254ce662854a08fe6a508977a72e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730182"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>İşlevler Görünümü - .NET Bellek İzleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşlevler görünümü izleme metodunu kullanarak toplanan .NET bellek ayırma profil oluşturma verilerinin profil oluşturma çalışması süresince bellek ayrılan işlevler listelenir. Bir işlevi satır ayırma ve zamanlama verilerini işlevi sayısı ve boyutu raporlar.  
  
## <a name="general"></a>Genel  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev adresi**|İşlevin adresi.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Çağrı sayısı**|Bu işleve yapılan çağrılar toplam sayısı.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|İşlevi içeren modül yolu.|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Zaman dışlamalı araştırma ek yükü**|Zaman ek yükü izleme nedeniyle bu işlev. Tüm özel sürelerinden çıkarıldığında araştırma ek yükü.|  
|**Zaman kapsamlı araştırma ek yükü**|Bu işlevde ve alt işlevleri nedeniyle izleme için ek yükü süre. Tüm kapsamlı sürelerinden çıkarıldığında araştırma ek yükü.|  
  
## <a name="net-memory-values"></a>.NET bellek değerleri  
 Bir işlev dahil .NET bellek değerlerini (ayırmalar) sayısı ve boyutu (bayt), işlev ve alt işlevleri tarafından oluşturulan nesnelerin gösterir.  
  
 Özel bellek değerleri sayısı ve boyutu, işlevi ve onun alt işlevleri tarafından oluşturulan nesnelerin gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı ayırmalar**|Bu işlevdeki ve bu işlev tarafından çağrılan işlevler oluşturulan nesnelerin toplam sayısı.|  
|**Kapsamlı ayırma yüzdesi**|Yüzdesi, profil oluşturma çalışmasında ayrılan tüm nesneler, bu işlevin kapsamlı ayırmalar yoktu.|  
|**Dışlamalı ayırmalar**|İşlev işlev gövdesinde kod yürütülürken oluşturulan nesneleri toplam sayısı. Bu sayı, bu işlev tarafından çağrılan işlevler oluşturulan nesneleri içermez.|  
|**Dışlamalı ayırma yüzdesi**|, Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin dışlamalı ayırmalar yoktu.|  
|**Kapsamlı bayt**|Bu işlevdeki ve bu işlev tarafından çağrılan işlevler ayrılan belleğin bayt sayısı.|  
|**Kapsamlı bayt yüzdesi**|Bu işlevin kapsamlı bayt olan, profil oluşturma çalışmasında ayrılan tüm bellek bayt yüzdesi.|  
|**Dışlamalı bayt**|Bu işlev tarafından ayrılan, ancak tarafından not işlevleri bellek bayt sayısı, bu işlev tarafından çağrılmış.|  
|**Dışlamalı bayt yüzdesi**|Bu işlevin dışlamalı bayt olan, profil oluşturma çalışmasında ayrılan tüm bellek bayt yüzdesi.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerleri  
 Geçen kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Saati, harcanan süre alt işlevleri ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen kapsamlı süre**|Bu işleve yapılan tüm çağrıların toplam kapsamlı süre.|  
|**Geçen kapsamlı süre yüzdesi**|Bu işlevin geçen kapsamlı süre harcandığını profil oluşturma çalışması toplam geçen kapsamlı süre yüzdesi.|  
|**Geçen ortalama kapsamlı süre**|Bu işlev çağrısına ortalama kapsamlı süre.|  
|**Geçen maksimum kapsamlı süre**|Maksimum kapsamlı süre bu işlev çağrısına geçti.|  
|**Geçen minimum kapsamlı süre**|Minimum kapsamlı süre bu işlev çağrısına geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerleri  
 Geçen dışlamalı değerleri bir işlev doğrudan çağrı yığınının en üstünde çağırılma yürütüldüğü zaman gösterir. Bağlam geçişleri ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında zaman zaman içerir, ancak alt işlevlerde harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dışlamalı süre**|Toplam bu işleve yapılan tüm çağrılar dışlamalı süre.|  
|**Geçen dışlamalı süre yüzdesi**|Toplam geçen dışlamalı süre bu işlevin içinde harcandığını profil oluşturma çalışması toplam geçen dışlamalı süre yüzdesi.|  
|**Geçen ortalama dışlamalı süre**|Ortalama dışlamalı süre bu işlev çağrısına geçti.|  
|**Geçen maksimum dışlamalı süre**|Maksimum dışlamalı süre bu işlev çağrısına geçti.|  
|**Geçen minimum dışlamalı süre**|Minimum dışlamalı süre bu işlev çağrısına geçti.|  
  
## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerlerini  
 Uygulama kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Süresi, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez, ancak alt işlevlerde harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı uygulama süresi**|Bu işleve yapılan tüm çağrılar toplam uygulama kapsamlı zamanı.|  
|**Kapsamlı uygulama süresi yüzdesi**|Bu işlevin toplam uygulama kapsamlı süre içinde harcandığını profil oluşturma çalışması toplam geçen kapsamlı süre yüzdesi.|  
|**Ortalama kapsamlı uygulama süresi**|Bu işlev için bir çağrı, ortalama uygulama kapsamlı süre.|  
|**Maksimum kapsamlı uygulama süresi**|Bu işlev çağrısı en fazla uygulama kapsamlı zamanı.|  
|**Minimum kapsamlı uygulama süresi**|Bu işlev çağrısına en düşük uygulama kapsamlı süre.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Bir işlev doğrudan çağrı yığınının en üstünde çağırılma yürütüldüğü zaman dışlamalı uygulama değerlerini belirtin. Ya da alt işlevlerde harcanan süreyi içermez süresi, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı uygulama süresi**|Bu işleve yapılan tüm çağrıların toplam uygulama dışlamalı süre.|  
|**Dışlamalı uygulama süresi yüzdesi**|Bu işlevin toplam uygulama dışlamalı süre içinde harcandığını profil oluşturma çalışması toplam geçen dışlamalı süre yüzdesi.|  
|**Ortalama dışlamalı uygulama süresi**|Bu işlev için bir çağrı, ortalama uygulama dışlamalı süre.|  
|**Maksimum dışlamalı uygulama süresi**|Bu işlev çağrısı en fazla uygulama özel zamanı.|  
|**Minimum dışlamalı uygulama süresi**|Bu işlev çağrısına en düşük uygulama dışlamalı süre.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [İşlevler görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [İşlevler görünümü](../profiling/functions-view-instrumentation-data.md)   
 [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)



