---
title: Çağrı ağacı görünümü - .NET bellek izleme verileri | Microsoft Docs
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
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed87363751c18794d9cf4c00e156d75760e0bf8d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782511"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Çağrı Ağacı Görünümü - .NET Bellek İzleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çağrı ağacı görünümü izleme metodunu kullanarak toplanan .NET bellek ayırma profil oluşturma verilerinin geçiş işlev yürütme yolları profili oluşturulan uygulamada görüntüler. Ağacının kökü, uygulamanın veya bileşenin içine giriş noktasıdır. Her işlev düğümü adlı, tüm işlevlere ve .NET bellek ve işlev için zamanlama verileri listeler.  
  
 Çağrı ağacı görünümü çağrı ağacında üst işlev tarafından çağrılan işlev örnekleri için değerler. Yüzde değerleri, toplam sayısı veya boyutu ayırma profil oluşturma, işlev örneği değerine karşılaştırılmasıyla hesaplanır.  
  
## <a name="highlighting-the-execution-hot-path"></a>Yürütme etkin yol vurgulamasını  
 Çağrı ağacı görünümü genişletebilir ve işlem ya da en büyük oluşturulan işlev veya çoğu bellek nesneleri yürütme yolunu vurgulayın. En etkin yol görüntülemek için işlem ya da işlev sağ tıklayın ve ardından **etkin yolu Genişlet**.  
  
## <a name="setting-the-call-tree-root-node"></a>Çağrı ağacı kök düğümü ayarlama  
 Profil oluşturma çalıştırmasını her işlem, bir kök düğümü olarak görüntülenir. Çağrı ağacı görünümü başlangıç düğümü başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayıp ardından seçerek ayarlayabilirsiniz **kümesi kök**.  
  
 Kök düğümü ayarladığınızda, Seçili düğümün alt ağacı dışında görünümünden diğer tüm girişleri kaldırın. Görüntülemekte olduğunuz düğüme geri kök düğümü sıfırlayabilirsiniz; Çağrı ağacı Görünümü penceresine sağ tıklayıp **sıfırlama kök**.  
  
## <a name="general"></a>Genel  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev adresi**|İşlevin adresi.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Çağrı sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|İşlevi içeren modül yolu.|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşleme atanan ad.|  
|**Zaman dışlamalı araştırma ek yükü**|Zaman ek yükü bu işlev, ölçümlü izlemeyle neden olur. Tüm özel sürelerinden çıkarıldığında araştırma ek yükü.|  
|**Zaman kapsamlı araştırma ek yükü**|İzleme tarafından neden olduğu zaman ek yükü Bu işlevde ve alt işlevleri. Tüm kapsamlı sürelerinden çıkarıldığında araştırma ek yükü.|  
|**Türü**|İşlevin bağlamı:<br /><br /> -   **0** -geçerli işlevi<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kök işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
  
## <a name="net-memory-values"></a>.NET bellek değerleri  
 Bir işlev dahil .NET bellek değerlerini (ayırmalar) sayısı ve boyutu (bayt) işlevi ve işlev tarafından çağrılan işlevler tarafından oluşturulmuş nesneleri gösterir.  
  
 Özel bellek değerleri sayısı ve boyutu değil işlev tarafından çağrılan işlevler ve işlev gövdesindeki kod tarafından oluşturulan nesneleri gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı ayırmalar**|Çağrı ağacında üst işlev tarafından çağrılan örnekleri bu işlev tarafından ayrılan nesnelerin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|  
|**Kapsamlı ayırma yüzdesi**|Yüzde, profil oluşturma çalışmasında oluşturulan tüm nesnelerin çağrı ağacında üst işlev tarafından çağrılan işlev örneklerinin kapsamlı ayırmalar yoktu.|  
|**Dışlamalı ayırmalar**|Çağrı ağacında üst işlev tarafından çağrılan örnekleri bu işlev tarafından ayrılan nesnelerin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içermez.|  
|**Dışlamalı ayırma yüzdesi**|Yüzde, profil oluşturma çalışmasında oluşturulan tüm nesnelerin çağrı ağacında üst işlev tarafından çağrılan işlev örneklerinin dışlamalı ayırmalar yoktu.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerleri  
 Geçen kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Saati, harcanan süre işlev tarafından çağrılan işlevler ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen kapsamlı süre**|Toplam çağrı ağacında üst işlevi tarafından çağrıldığında, bu işleve yapılan tüm çağrılar dahil süre.|  
|**Geçen kapsamlı süre yüzdesi**|Profil oluşturma çalıştırmasını çağrı ağacında üst işlevi tarafından çağrıldığında, toplam geçen kapsamlı süre bu işlevin içinde harcanan toplam geçen kapsamlı süre yüzdesi.|  
|**Geçen ortalama kapsamlı süre**|Çağrı ağacında üst işlevi tarafından çağrıldığında ortalama kapsamlı süre bu işlev çağrısına geçti.|  
|**Geçen maksimum kapsamlı süre**|En fazla çağrı ağacında üst işlevi tarafından çağrıldığında bu işlev çağrısına kapsamlı süre.|  
|**Geçen minimum kapsamlı süre**|Çağrı ağacında üst işlevi tarafından çağrıldığında minimum kapsamlı süre bu işlev çağrısına geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerleri  
 Geçen dışlamalı değerleri bir işlev doğrudan çağrı yığınının en üstünde çağırılma yürütüldüğü zaman gösterir. Zaman zaman bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içerir. Ancak, zaman işlev tarafından çağrılan işlevlerdeki harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dışlamalı süre**|Toplam çağrı ağacında üst işlevi tarafından çağrıldığında bu işleve yapılan tüm çağrıların dışlamalı süre.|  
|**Geçen dışlamalı süre yüzdesi**|Profil oluşturma çalıştırmasını çağrı ağacında üst işlevi tarafından çağrıldığında, toplam geçen dışlamalı süre bu işlevin içinde harcanan toplam geçen dışlamalı süre yüzdesi.|  
|**Geçen ortalama dışlamalı süre**|Çağrı ağacında üst işlevi tarafından çağrıldığında ortalama dışlamalı süre bu işlev çağrısına geçti.|  
|**Geçen maksimum dışlamalı süre**|Çağrı ağacında üst işlevi tarafından çağrıldığında maksimum dışlamalı süre bu işlev çağrısına geçti.|  
|**Geçen minimum dışlamalı süre**|Çağrı ağacında üst işlevi tarafından çağrıldığında minimum dışlamalı süre bu işlev çağrısına geçti.|  
  
## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerlerini  
 Uygulama kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Zaman bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez. Saat, işlev tarafından çağrılan işlevlerdeki alt harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı uygulama süresi**|Bu işlev çağrısı ağacında üst işlevi tarafından çağrıldığında yapılan tüm çağrıların toplam uygulama kapsamlı süre.|  
|**Kapsamlı uygulama süresi yüzdesi**|Profil oluşturma çalıştırmasını çağrı ağacında üst işlevi tarafından çağrıldığında, toplam kapsamlı uygulama süresi, bu işlevin içinde harcanan toplam geçen kapsamlı süre yüzdesi.|  
|**Ortalama kapsamlı uygulama süresi**|Çağrı ağacında üst işlevi tarafından çağrıldığında, bu işlev için bir çağrı, ortalama uygulama kapsamlı süre.|  
|**Maksimum kapsamlı uygulama süresi**|Çağrı ağacında üst işlevi tarafından çağrıldığında, bu işlev çağrısı en fazla uygulama kapsamlı zamanı.|  
|**Minimum kapsamlı uygulama süresi**|En düşük uygulama kapsamlı süre, çağrı ağacında üst işlevi tarafından çağrıldığında, bu işlev çağrısı.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerlerini, işlev tarafından çağrılan işlevlerdeki alt için harcanan süre hariç işlevde harcanan zamanı gösterir. Zamanı, aynı zamanda bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları dışlar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı uygulama süresi**|Bu işlev çağrısı ağacında üst işlevi tarafından çağrıldığında yapılan tüm çağrıların toplam uygulama dışlamalı süre.|  
|**Dışlamalı uygulama süresi yüzdesi**|Profil oluşturma çalıştırmasını çağrı ağacında üst işlevi tarafından çağrıldığında, bu işlevin toplam uygulama dışlamalı süre içinde harcanan toplam geçen dışlamalı süre yüzdesi.|  
|**Ortalama dışlamalı uygulama süresi**|Ortalama uygulama dışlamalı süre, çağrı ağacında üst işlevi tarafından çağrıldığında, bu işlev çağrısı.|  
|**Maksimum dışlamalı uygulama süresi**|En fazla uygulama dışlamalı süre, çağrı ağacında üst işlevi tarafından çağrıldığında, bu işlev çağrısı.|  
|**Minimum dışlamalı uygulama süresi**|En düşük uygulama dışlamalı süre, çağrı ağacında üst işlevi tarafından çağrıldığında, bu işlev çağrısı.|



