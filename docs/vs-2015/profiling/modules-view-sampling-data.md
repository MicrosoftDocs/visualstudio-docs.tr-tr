---
title: Modüller görünümü - örnekleme verileri | Microsoft Docs
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
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a885ca96ce58be7448f5b9b814457b38e08a1233
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742494"
---
# <a name="modules-view---sampling-data"></a>Modüller Görünümü - Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme profil oluşturma verileri örneklenen modüller tarafından gruplandırılmış veri görüntüler performans verileri modülleri görünümü. Her bir hiyerarşik ağaç kökünde modülüdür. Örneklenen modülündeki işlevlerin modülü düğümünün altında listelenir.  
  
> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 İşlevi çalıştırıldığında zaman örnekleri toplandı (diğer bir deyişle, işlev çağrı yığınının en üstünde olduğu), yürütülmekte yönerge adresi ve kaynak satırları işlevi düğümünün altında listelenir. Satırı veya yönerge yürüttüğünde veri kaynak satırı veya bir yönerge işaretçisini toplandığından, dahil ve hariç olan değerler her zaman satır verileri hem de yönerge veri için aynıdır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Modül, işlev, satır numarası veya yönerge işaretçisi adresi adı.|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|İşlevi, çizgi veya yönerge işaretçisini içeren modül adı.|  
|**Modül yolu**|Modül, işlev, satır veya yönerge işaretçisini içeren modül yolu.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Kapsamlı örnekler**|-Bir işlev için bu işlev veya bu işlev tarafından çağrılan bir işlev Yürütülüyor; örnek sayısı diğer bir deyişle, çağrı sayısı, bu işlevi içeren örnek yığın.<br />-Bir modül için modülünden hangi en az bir işlevdeki örneklerin sayısı yürütülüyor.<br />-Bir satır veya yönergesi, örnek sayısı için bu satırı veya yönerge yürütürken.|  
|**Kapsamlı örnek yüzdesi**|-Bir işlev veya modül için profil çalıştıran tüm örneklerin yüzdesi bu işlev veya modül, kapsamlı örnekler yoktu.<br />-Bir satır veya yönerge için profil oluşturma tüm örneklerin yüzdesi çalıştırın, bu satırı veya yönerge Yürütülüyor içinde.|  
|**Dışlamalı örnekler**|Bir işlev-çağrı sayısı bu işlev doğrudan yürütülmüş örnekleri yığın; diğer bir deyişle, bu işlev çağrı yığınının en üstünde olan örnek sayısı.<br />-Bir modül için modülündeki işlevlerin dışlamalı örnekler toplamı.<br />-Bir satır veya yönergesi, örnek sayısı için bu satırı veya yönerge yürütürken.|  
|**Dışlamalı örnek yüzdesi**|-Bir işlev veya modül için profil çalıştıran tüm örneklerin yüzdesi bu işlev veya modül dışlamalı örnekleri yoktu.<br />-Bir satır veya yönerge için profil oluşturma tüm örneklerin yüzdesi çalıştırın, bu satırı veya yönerge Yürütülüyor içinde.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modüller görünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modüller görünümü - izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)



