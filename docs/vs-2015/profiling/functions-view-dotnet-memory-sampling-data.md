---
title: İşlevler görünümü - .NET bellek örnekleme verileri | Microsoft Docs
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
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfdfbab17538648b816c094409f9396cc5f638b8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788322"
---
# <a name="functions-view---net-memory-sampling-data"></a>İşlevler Görünümü - .NET Bellek Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET bellek ayırma profil oluşturma örnekleme yöntemiyle toplanan veriyi işlevler görünümünü ayırmaların sayısı ve boyutu raporlar ve profil oluşturma çalışması süresince bellek ayrılan işlevler listelenir.  
  
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
|**Kapsamlı ayırmalar**|Bu işlevde ve alt işlevleri ayrılmış nesneleri toplam sayısı.|  
|**Kapsamlı ayırma yüzdesi**|Yüzdesi, profil oluşturma çalışmasında ayrılan tüm nesneler, bu işlevin kapsamlı ayırmalar yoktu.|  
|**Dışlamalı ayırmalar**|İşlev çağrı yığınının başında doğrudan yürütülürken, oluşturulan nesne sayısı. Bu sayı, alt işlevlerde oluşturulan nesneleri içermez.|  
|**Dışlamalı ayırma yüzdesi**|Yüzdesi, profil oluşturma çalışmasında ayrılan tüm nesneler, bu işlevin dışlamalı ayırmalar yoktu.|  
|**Kapsamlı bayt**|Bu işlevde ve alt işlevleri tarafından ayrılan bellek bayt sayısı.|  
|**Kapsamlı bayt yüzdesi**|Bu işlevin kapsamlı bayt olan, profil oluşturma çalışmasında ayrılan tüm bellek bayt yüzdesi.|  
|**Dışlamalı bayt**|Bu işlev tarafından ancak alt işlevleri tarafından ayrılan bellek bayt sayısı.|  
|**Dışlamalı bayt yüzdesi**|Bu işlevin dışlamalı bayt olan, profil oluşturma çalışmasında ayrılan tüm bellek bayt yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlevler görünümü - izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [İşlevler görünümü](../profiling/functions-view-sampling-data.md)   
 [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)



