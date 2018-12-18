---
title: Modüller görünümü - .NET bellek izleme verileri | Microsoft Docs
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
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85024296eff4fb4d26b3a588217a1e6fe5221d3e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755398"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Modüller Görünümü - .NET Bellek İzleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET bellek ayırma verisini izleme metodunu kullanarak toplanan modülleri görünümünü, profil oluşturma çalıştırmasını içinde yürütülen modüller tarafından bellek ve zamanlama verileri gruplandırır. Modülün işlevleri için profil oluşturma verilerini modülü düğümünün altında listelenir.  
  
## <a name="general"></a>Genel  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|İşlev veya modül adı.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Çağrı sayısı**|Bu işlev veya modül yapılan çağrıları toplam sayısı.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|İşlevi içeren modül yolu.|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|Hangi modülün veya işlevin yürütülmekte olan işlemin adı.|  
|**Zaman dışlamalı araştırma ek yükü**|Bu işlev veya modül nedeniyle izleme için ek yükü süre.|  
|**Zaman kapsamlı araştırma ek yükü**|Zaman ek yükü bu işlev veya modül ve izleme nedeniyle alt işlevleri.|  
  
## <a name="net-memory-values"></a>.NET bellek değerleri  
 Bir işlev dahil .NET bellek değerlerini (ayırmalar) sayısı ve boyutu (bayt), işlev ve alt işlevleri tarafından oluşturulan nesnelerin gösterir.  
  
 Özel bellek değerleri sayısı ve boyutu, işlevi ve onun alt işlevleri tarafından oluşturulan nesnelerin gösterir.  
  
 Dahil ve hariç bellek bir modülün özel bellek değerlerini modülündeki işlevlerin ve kapsamlı toplamını değerlerdir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı ayırmalar**|-Bir işlev için işlevi tarafından oluşturulan nesnelerin toplam sayısı. Bu işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içerir.<br />-Modülünden gelen en az bir işlevi yürütürken bir modül için çalıştıran bir profil nesne sayısını ayrılan. Bu sayı ayrılan nesneler modülü işlevleri çağrılarından tarafından oluşturulan işlevleri içerir.|  
|**Kapsamlı ayırma yüzdesi**|, Profil oluşturma çalışmasında ayrılan tüm nesneleri yüzdesi olan modülün veya işlevin kapsamlı ayırmalar.|  
|**Dışlamalı ayırmalar**|-Bir işlev, işlev işlev gövdesinde kod yürütülürken, oluşturulan nesne sayısı için (diğer bir deyişle, ne işlev çağrı yığınının en üstünde zaman). Bu sayı, işlev tarafından çağrılan işlevler oluşturulan nesneleri içermez.<br />-Bir modül için modülündeki işlevlerin dışlamalı ayırmalar toplamı.|  
|**Dışlamalı ayırma yüzdesi**|, Profil oluşturma çalışmasında ayrılan tüm nesneleri yüzdesi olan modülün veya işlevin dışlamalı ayırmalar.|  
|**Dışlamalı bayt**|-(Diğer bir deyişle, işlev çağrı yığınının en üstünde olduğunda) bir işlev için işlev, işlev kod yürütülürken, ayrılan belleğin bayt sayısı gövde. Bu sayı ayrılan bayt işlev tarafından çağrılan işlevler içermez.<br />-Bir modül için modülündeki işlevleri tarafından ayrılan özel baytları toplamı.|  
|**Dışlamalı bayt yüzdesi**|Dışlamalı bayt modülü, işlev, satır veya yönerge olan, profil oluşturma çalışmasında ayrılan tüm baytların yüzdesi.|  
|**Kapsamlı bayt**|-Bir işlev için işlev tarafından ayrılan bayt sayısı. Bu sayı ayrılan bayt işlev tarafından çağrılan işlevler içerir.<br />-Modülünden gelen en az bir işlevi yürütürken bir modül için bir, profil oluşturma çalışmasında ayrılan bayt sayısı ayrılan. Bu sayı modül işlevleri tarafından çağrılan tüm işlevleri oluşturulan nesneleri içerir.|  
|**Kapsamlı bayt yüzdesi**|Modülün veya işlevin kapsamlı bayt olan, profil oluşturma çalışmasında ayrılan tüm baytların yüzdesi.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerleri  
 Geçen kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Saati, harcanan süre alt işlevleri ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen kapsamlı süre**|-Bir işlev için işlevde harcanan süre. Alt işlevleri ve işletim sistemi, bağlam anahtarları ve giriş/çıkış işlemleri gibi çağrılarında harcanan süreyi içerir.<br />-Bir modül için modülünde en az bir işlev çağrı yığınındaki olduğu süre.|  
|**Geçen kapsamlı süre yüzdesi**|Toplam geçen kapsamlı süre Bu modülün veya işlevin içinde profil oluşturma, toplam geçen kapsamlı süre yüzdesi harcandığını.|  
|**Geçen ortalama kapsamlı süre**|-Bir işlev için ortalama kapsamlı süre bu işlev çağrısına geçti.<br />-Bir modül için ortalama kapsamlı süre modülündeki işlevleri yapılan tüm çağrıların geçti.|  
|**Geçen maksimum kapsamlı süre**|-Bir işlev için maksimum kapsamlı süre bu işlev çağrısına geçti.<br />-Bir modül için en fazla modülündeki işlevleri yapılan tüm çağrıların kapsamlı süre geçti.|  
|**Geçen minimum kapsamlı süre**|-Bir işlev için en az Bu modülün veya işlevin çağrısına kapsamlı süre geçti.<br />-Bir modül için minimum kapsamlı süre modülündeki işlevleri yapılan tüm çağrıların geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerleri  
 Geçen dışlamalı değerleri bir işlev doğrudan çağrı yığınının en üstünde çağırılma yürütüldüğü zaman gösterir. Saati bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi yapılan çağrıda zaman içerir, ancak alt işlevlerde harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dışlamalı süre**|-Bir işlev için modülün veya işlevin harcanan süre. Bu bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içerir, ancak alt işlevlerde harcanan zamanı dışlar.<br />-Bir modül için modülündeki işlevlerin özel süreleri toplamı geçti.|  
|**Geçen dışlamalı süre yüzdesi**|Toplam geçen dışlamalı süre Bu modülün veya işlevin içinde profil oluşturma, toplam geçen dışlamalı süre yüzdesi harcandığını.|  
|**Geçen ortalama dışlamalı süre**|-Bir işlev için ortalama dışlamalı süre bu işlev çağrısına geçti.<br />-Bir modül için ortalama dışlamalı süre modülündeki işlevleri yapılan tüm çağrıların geçti.|  
|**Geçen maksimum dışlamalı süre**|-Bir işlev için maksimum dışlamalı süre bu işlev çağrısına geçti.<br />-Bir modül için maksimum dışlamalı süre modülündeki işlevleri yapılan tüm çağrıların geçti.|  
|**Geçen minimum dışlamalı süre**|-Bir işlev için minimum dışlamalı süre Bu modülün veya işlevin çağrısına geçti.<br />-Bir modül için minimum dışlamalı süre modülündeki işlevleri yapılan tüm çağrıların geçti.|  
  
## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerlerini  
 Uygulama kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Süresi, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez, ancak alt işlevlerde harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı uygulama süresi**|-Bir işlev için işlev çağrılarında harcanan süre. Bu alt işlevlerde geçen ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları dışlar süreyi içerir.<br />-Bir modül için işletim sistemi çağrılarında harcanan süre hariç çağrı yığını, en az bir işlev modülü süreyi açıktı.|  
|**Kapsamlı uygulama süresi yüzdesi**|Kapsamlı uygulama süresi Bu modülün veya işlevin içinde harcandığını profil oluşturma çalışması toplam geçen kapsamlı süre yüzdesi.|  
|**Ortalama kapsamlı uygulama süresi**|-Bir işlev için bu işlev için bir çağrı, ortalama uygulama kapsamlı süre.<br />-Bir modül için modülündeki işlevleri yapılan tüm çağrıların ortalama uygulama kapsamlı süre.|  
|**Maksimum kapsamlı uygulama süresi**|-Bir işlev için bu işlevi çağrısı, en fazla uygulama kapsamlı süre.<br />-Bir modül için modülündeki işlevleri yapılan tüm çağrıların en fazla uygulama kapsamlı süre.|  
|**Minimum kapsamlı uygulama süresi**|-Bir işlev için yapılan çağrının Bu modülün veya işlevin en düşük uygulama kapsamlı süre.<br />-Bir modül için modülündeki işlevleri yapılan tüm çağrıların en düşük uygulama kapsamlı süre.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerleri modüldeki veya alt işlevlerde harcanan zaman hariç işlev için harcanan zamanı gösterir. Belirtilen zaman ayrıca bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları dışlar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı uygulama süresi**|-Bir işlev için bu işleve yapılan çağrıların toplam uygulama dışlamalı süre.<br />-Bir modül için modülündeki işlevleri yapılan tüm çağrıların toplam uygulama dışlamalı süre.|  
|**Dışlamalı uygulama süresi yüzdesi**|Dışlamalı uygulama süresi Bu modülün veya işlevin içinde harcandığını profil oluşturma çalışması toplam geçen dışlamalı süre yüzdesi.|  
|**Ortalama dışlamalı uygulama süresi**|-Bir işlev için bu işlev için bir çağrı, ortalama uygulama dışlamalı süre.<br />-Bir modül için modülündeki işlevleri yapılan tüm çağrıların ortalama uygulama dışlamalı süre.|  
|**Maksimum dışlamalı uygulama süresi**|-Bir işlev için bu işlevi çağrısı, en fazla uygulama dışlamalı süre.<br />-Bir modül için modülündeki işlevleri yapılan tüm çağrıların en fazla uygulama dışlamalı süre.|  
|**Minimum dışlamalı uygulama süresi**|-Bir işlev için yapılan çağrının Bu modülün veya işlevin en düşük uygulama dışlamalı süre.<br />-Bir modül için modülündeki işlevleri yapılan tüm çağrıların en düşük uygulama dışlamalı süre.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modüller görünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modüller görünümü](../profiling/modules-view-instrumentation-data.md)   
 [Modüller Görünümü](../profiling/modules-view-sampling-data.md)



