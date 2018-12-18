---
title: .NET bellek ayırma görünümü | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7a473a7c6758fe58c82f8894822d3a250165a43
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933683"
---
# <a name="net-memory-allocations-view"></a>.NET Bellek Ayırma Görünümü
Ayırma görünümü, profil oluşturma çalışması süresince oluşturulan türlerini listeler. Her türde ayırmalar şeklinde sonuçlanan işlevi yürütme yollarını görüntüler bir çağrı ağacı kök düğümü türüdür.  
  
 Profil oluşturma çalıştırmasını içinde oluşturulan türünden nesnelerin toplam sayısı ve bu tür nesneler için ayrılmış baytların toplam sayısı, türü bir satırdaki verileri görüntüler. Dahil ve hariç olan değerler türü için her zaman aynı olur.  
  
- Kapsamlı işleve ve çağrı ağacında üst işlev tarafından çağrılan alt işlevleri örneklerinde oluşturulan nesneler için değerler.  
  
- Bunlar üst işlev tarafından çağrılmış olduğunda doğrudan işlevi tarafından oluşturulan nesneler için özel değerler şunlardır. Alt işlevlerde oluşturulan nesneler dahil edilmez.  
  
  Verileri bir işlev için oluşturulan nesne sayısını ve üst tür nesneler için ayrılan bayt sayısını görüntüler.  
  
## <a name="highlight-the-execution-hot-path"></a>Yürütme etkin yolu vurgulayın  
 Çoğu nesne üst türü oluşturulan çağrı ağacını yürütme yolunu bulabilirsiniz.  
  
-   En etkin yol görüntülemek için tür veya işlev sağ tıklayın ve ardından **etkin yolu Genişlet**.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Ayrılmış türün veya işlevin adı.|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|Tür veya işlev içeren modül adı.|  
|**Modül yolu**|Tür veya işlev içeren modül yolu.|  
|**Kaynak dosyası**|Tür veya işlev tanımını içeren kaynak dosya.|  
|**İşlevin satır numarası**|Bu tür tanımı veya kaynak dosyada işlev satır sayısı.|  
|**düzeyi**|Veri türü veya bir işlev için olup olmadığını gösterir.|  
|**Kapsamlı ayırmalar**|-Bir işlev için işlevi tarafından oluşturulan üst öğe türündeki nesnelerin toplam sayısı. Bu sayı, alt işlevlerde oluşturulan nesneleri içerir.<br />-Bir tür için oluşturulan bu türdeki örneklerin toplam sayısı.|  
|**Kapsamlı ayırma yüzdesi**|-Bir işlev için olan işleve göre üst türü kapsamlı ayırma profil oluşturma çalıştırmasını içinde oluşturulan tüm nesnelerin yüzdesi.<br />-Bir tür için, profil oluşturma çalışmasında oluşturulan nesnelerin toplam sayısının yüzdesi türün örneklerinin yoktu.|  
|**Dışlamalı ayırmalar**|-Bir işlev için işlev çağrı yığınının başında doğrudan yürütülürken, oluşturulan nesne sayısı. Bu sayı, alt işlevlerde oluşturulan nesnelerin içermez.<br />-Bir tür için oluşturulan bu türdeki örneklerin toplam sayısı.|  
|**Dışlamalı ayırma yüzdesi**|-Bir işlev için olan işleve göre üst türü dışlamalı ayırma profil oluşturma çalıştırmasını içinde oluşturulan tüm nesnelerin yüzdesi.<br />-Bir tür için, profil oluşturma çalışmasında oluşturulan nesnelerin toplam sayısının yüzdesi türün örneklerinin yoktu.|  
|**Kapsamlı bayt**|-Bir işlev için üst türü nesneler için işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, alt işlevleri tarafından ayrılan bellek içerir.<br />-Bir tür için türü örnekleri için profil oluşturma çalışmasında ayrılan toplam bayt sayısı.|  
|**Kapsamlı bayt yüzdesi**|-Bir işlev için kapsamlı ayırma işleviyle üst türü, profil oluşturma çalışmasında ayrılan tüm bellek yüzdesini oluştu.<br />-Bir tür için, profil oluşturma çalışmasında ayrılan tüm bellek yüzdesi için ayrılmış örnekleri türü.|  
|**Dışlamalı bayt**|-Bir işlev için üst türü nesneler için işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, alt işlevleri tarafından ayrılan bellek içermez.<br />-Bir tür için profil oluşturma ayrılan bayt sayısı türü örnekleri için çalıştırın.|  
|**Dışlamalı bayt yüzdesi**|-Bir işlev için işleve göre üst türü dışlamalı ayırmalar, profil oluşturma çalışmasında ayrılan tüm bellek yüzdesini oluştu.<br />-Bir tür için, profil oluşturma çalışmasında ayrılan tüm bellek yüzdesi için ayrılmış örnekleri türü.|