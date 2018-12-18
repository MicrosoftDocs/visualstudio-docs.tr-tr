---
title: İşlevler görünümü - izleme verileri | Microsoft Docs
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
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c19175af6af583120c9fd648328ecf90deaeb3a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786814"
---
# <a name="functions-view---instrumentation-data"></a>İşlevler Görünümü - İzleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşlevleri rapor görünümü işlev adı tarafından profil oluşturma verilerini listeler.  
  
## <a name="general"></a>Genel  
 Genel sütunları bir görünüm satır işlevi tanımlar.  
  
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
|**Zaman dışlamalı araştırma ek yükü**|Zaman ek yükü bu işlev, ölçümlü izlemeyle neden olur. Bu ek yükü işlev tarafından çağrılan işlevlerdeki içermez. Tüm özel sürelerinden çıkarıldığında araştırma ek yükü.|  
|**Zaman kapsamlı araştırma ek yükü**|İzleme tarafından neden olduğu zaman ek yükü Bu işlevde ve alt işlevleri. Ek yükü işlev tarafından çağrılan işlevler dahil edin. Tüm kapsamlı sürelerinden çıkarıldığında araştırma ek yükü.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerleri  
 Geçen kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Zaman harcanan zaman bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan zaman ve işlev tarafından çağrılan işlevler içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen kapsamlı süre**|Bu işleve yapılan tüm çağrıların toplam kapsamlı süre.|  
|**Geçen kapsamlı süre yüzdesi**|Bu işlevin geçen kapsamlı süre harcandığını profil oluşturma çalışması toplam geçen kapsamlı süre yüzdesi.|  
|**Geçen ortalama kapsamlı süre**|Bu işlev çağrısına ortalama kapsamlı süre.|  
|**Geçen maksimum kapsamlı süre**|Maksimum kapsamlı süre bu işlev çağrısına geçti.|  
|**Geçen minimum kapsamlı süre**|Minimum kapsamlı süre bu işlev çağrısına geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerleri  
 Geçen dışlamalı değerler olduğunda işlev çağrı yığınının en üstünde bir işlev kodu işlev gövdesinde diğer bir deyişle, yürütülmekte olan, zamanı gösterir. Zaman bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içerir, ancak, harcanan süre işlev tarafından çağrılan işlevlerdeki içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dışlamalı süre**|Toplam bu işleve yapılan tüm çağrılar dışlamalı süre.|  
|**Geçen dışlamalı süre yüzdesi**|Toplam geçen dışlamalı süre bu işlevin içinde harcandığını profil oluşturma çalışması toplam geçen dışlamalı süre yüzdesi.|  
|**Geçen ortalama dışlamalı süre**|Ortalama dışlamalı süre bu işlev çağrısına geçti.|  
|**Geçen maksimum dışlamalı süre**|Maksimum dışlamalı süre bu işlev çağrısına geçti.|  
|**Geçen minimum dışlamalı süre**|Minimum dışlamalı süre bu işlev çağrısına geçti.|  
  
## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerlerini  
 Uygulama kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Süresi, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez, ancak harcanan süre işlev tarafından çağrılan işlevler dahil edin.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı uygulama süresi**|Bu işleve yapılan tüm çağrılar toplam uygulama kapsamlı zamanı.|  
|**Kapsamlı uygulama süresi yüzdesi**|Bu işlevin toplam uygulama kapsamlı süre içinde harcandığını profil oluşturma çalışması toplam geçen kapsamlı süre yüzdesi.|  
|**Ortalama kapsamlı uygulama süresi**|Bu işlev için bir çağrı, ortalama uygulama kapsamlı süre.|  
|**Maksimum kapsamlı uygulama süresi**|Bu işlev çağrısı en fazla uygulama kapsamlı zamanı.|  
|**Minimum kapsamlı uygulama süresi**|Bu işlev çağrısına en düşük uygulama kapsamlı süre.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Bir işlev doğrudan çağrı yığınının en üstünde çağırılma yürütüldüğü zaman dışlamalı uygulama değerlerini belirtin. Süresi, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez ve bu harcanan süre işlev tarafından çağrılan işlevlerdeki içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı uygulama süresi**|Bu işleve yapılan tüm çağrıların toplam uygulama dışlamalı süre.|  
|**Dışlamalı uygulama süresi yüzdesi**|Bu işlevin toplam uygulama dışlamalı süre içinde harcandığını profil oluşturma çalışması toplam geçen dışlamalı süre yüzdesi.|  
|**Ortalama dışlamalı uygulama süresi**|Bu işlev için bir çağrı, ortalama uygulama dışlamalı süre.|  
|**Maksimum dışlamalı uygulama süresi**|Bu işlev çağrısı en fazla uygulama özel zamanı.|  
|**Minimum dışlamalı uygulama süresi**|Bu işlev çağrısına en düşük uygulama dışlamalı süre.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [İşlevler görünümü](../profiling/functions-view-sampling-data.md)   
 [İşlevler görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [İşlevler Görünümü - İzleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)



