---
title: Arayan-Aranan görünümü - .NET bellek izleme verileri | Microsoft Docs
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
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf809747bff2146c6a45afd49768dbda69ae7d91
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782291"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Arayan/Aranan görünümü - .NET bellek izleme verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arayan/Aranan görünümü profil oluşturma Araçlar yöntemini kullanarak toplanan veriyi .NET bellek ayırma ve zamanlama verileri için seçilen işlevin seçili işleve ve üst ve alt görüntüler. Arayan/Aranan görünümü üç Kılavuzlar içerir.  
  
 **Geçerli işlev** Orta kılavuzda görüntülenir ve bellek profili oluşturma seçili işlev hakkında bilgi gösterir. İşlev çağrıları tüm örneklenen değerlerini içerir.  
  
 **Geçerli işlevi çağırmış işlevler** üst kılavuz görüntülenir ve çağıran (üst) işlevi'öğesinden gelen çağrılar tarafından oluşturulmuş seçili (geçerli) işlevinin değeri miktarını gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuz görüntülenir ve bellek alt işlevi geçerli işlev tarafından çağrıldığında çağrılan (alt) işlevlerini seçili işlev için profil oluşturma gösterilmektedir.  
  
 Geçerli işlev satır yapmak için bir çağıran ya da çağrılan işlev satır çift tıklayın.  
  
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
|**İşlem kimliği**|Profil oluşturma işlemi kimliği.|  
|**İşlem adı**|İşleme atanan ad.|  
|**Zaman dışlamalı araştırma ek yükü**|Zaman ek yükü izleme nedeniyle bu işlev. Tüm özel sürelerinden çıkarıldığında araştırma ek yükü.|  
|**Zaman kapsamlı araştırma ek yükü**|Bu işlevde ve alt işlevleri nedeniyle izleme için ek yükü süre. Tüm kapsamlı sürelerinden çıkarıldığında araştırma ek yükü.|  
|**Türü**|İşlevin bağlamı:<br /><br /> **0** -geçerli işlevi<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kök işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
  
## <a name="net-memory-allocation-values"></a>.NET bellek ayırma değerleri  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı ayırmalar**|-Geçerli işlev, işlev işlev gövdesinde kod yürütülürken, oluşturulan nesne sayısı için (diğer bir deyişle, ne işlev çağrı yığınının en üstünde zaman). Sayı, bu işlev tarafından çağrılan işlevler oluşturulan nesneleri içermez.<br />-Çağıran işlev için geçerli işlevi çağıran işlevden bu çağrılar tarafından oluşturulan özel ayırmaların sayısı.<br />-Çağrılan işlev için bu işlev geçerli işlev tarafından çağrılan örnekleri tarafından oluşturulan nesne sayısı. Bu sayı çağrılan işlev tarafından çağrılan işlevler tarafından oluşturulmuş nesneleri içermez.|  
|**Dışlamalı ayırma yüzdesi**|, Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin dışlamalı ayırmalar yoktu.|  
|**Kapsamlı ayırmalar**|-Geçerli işlev için profil oluşturma işlevi tarafından ayrılan nesnelerin sayısını çalıştırın. İşlev tarafından çağrılan çağrılan işlevler oluşturulan nesneleri içerir.<br />-Çağıran işlev için bu çağıran işleve çağrılar tarafından oluşturulan kapsamlı ayırmalar geçerli işlevin sayısı.<br />-İçin çağrılan işlev, geçerli işlevden örnekleri tarafından oluşturulan bu işlev tarafından ayrılan nesnelerin sayısını çağırır. Bu çağrılan işlev tarafından çağrılan işlevler tarafından yapılan ayırmaları içerir.|  
|**Kapsamlı ayırma yüzdesi**|, Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin kapsamlı ayırmalar yoktu.|  
|**Dışlamalı bayt**|-Geçerli işlev için profil oluşturma çalışması işlev tarafından ayrılan bellek bayt sayısı. Sayı, ayrılmış bellek işlev tarafından çağrılmış çağrılan işlevlerdeki içermez.<br />-Çağıran işlevin için bu çağıran işlev tarafından oluşturulmuş geçerli işlevin özel bayt sayısı çağırır.<br />-Çağrılan işlev için çağrılarından geçerli işlev tarafından oluşturulan bu işlev örnekleri tarafından ayrılan bayt sayısı. Çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan bayt sayısı dahil değildir.|  
|**Dışlamalı bayt yüzdesi**|, Profil oluşturma çalışmasında ayrılan tüm bellek bayt yüzdesi, bu işlevin dışlamalı ayırmalar yoktu.|  
|**Kapsamlı bayt**|-Geçerli işlev için profil oluşturma çalışması işlev tarafından ayrılan bellek bayt sayısı. Sayı, işlev tarafından çağrılmış çağrılan işlevlerdeki ayrılmış bellek içerir.<br />-Çağıran işlev için bu çağıran işleve çağrılar tarafından oluşturulan geçerli işlevin örneklerinin kapsamlı bayt sayısı.<br />-Çağrılan işlev için çağrılarından geçerli işlev tarafından oluşturulan bu işlev örnekleri tarafından ayrılan bayt sayısı. Bu çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan bayt sayısını içerir.|  
|**Kapsamlı bayt yüzdesi**|, Profil oluşturma çalışmasında ayrılan tüm bellek bayt yüzdesi, bu işlevin kapsamlı ayırmalar yoktu.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerleri  
 Geçen kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Saati, harcanan süre alt işlevleri ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen kapsamlı süre**|-Geçerli işlev için işlevde harcanan süre. Değer, alt işlevleri ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları harcanan süreyi içerir.<br />-Çağıran işlev için bu çağıran işleve çağrılar tarafından oluşturulmuş geçerli işlevin geçen kapsamlı süre miktarı.<br />-Çağrılan işlev için bu harcanan süreyi geçerli işlevden tarafından oluşturulan işlevi çağırır. Değer, alt işlevleri ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları harcanan süreyi içerir.|  
|**Geçen kapsamlı süre yüzdesi**|Geçen kapsamlı süre bu işlevi bu bağlamda harcandığını profil oluşturma çalışması toplam geçen kapsamlı süre yüzdesi.|  
|**Geçen ortalama kapsamlı süre**|Ortalama kapsamlı süre bu bağlamda bu işlev çağrısına geçti.|  
|**Geçen maksimum kapsamlı süre**|Maksimum kapsamlı süre bu bağlamda bu işlev çağrısına geçti.|  
|**Geçen minimum kapsamlı süre**|Minimum kapsamlı süre bu bağlamda bu işlev çağrısına geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerleri  
 Geçen dışlamalı değerleri bir işlev doğrudan çağrı yığınının en üstünde çağırılma yürütüldüğü zaman gösterir. Bağlam geçişleri ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında zaman zaman içerir, ancak alt işlevlerde harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dışlamalı süre**|-Geçerli işlev için işlev gövdesi yürütme harcanan süre. Değeri, alt işlevlerde geçen süre, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içeren süreyi içermez.<br />-Çağıran işlev için bu çağıran işleve çağrılar tarafından oluşturulmuş geçerli işlevin geçen dışlamalı süre miktarı.<br />-Çağrılan işlev için bu harcanan süreyi geçerli işlevden tarafından oluşturulan işlevi çağırır. Değeri, çağrılan işlevin alt işlevlerde geçen süre, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içeren zaman içermez.|  
|**Geçen dışlamalı süre yüzdesi**|Çalıştıran profil oluşturma toplam geçen dışlamalı süre yüzdesi bu işlevi bu bağlamda toplam geçen dışlamalı süre geçen süre.|  
|**Geçen ortalama dışlamalı süre**|Ortalama dışlamalı süre bu bağlamda bu işlev çağrısına geçti.|  
|**Geçen maksimum dışlamalı süre**|Maksimum dışlamalı süre bu bağlamda bu işlev çağrısına geçti.|  
|**Geçen minimum dışlamalı süre**|Minimum dışlamalı süre bu bağlamda bu işlev çağrısına geçti.|  
  
## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerlerini  
 Uygulama kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Süresi, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez, ancak alt işlevlerde harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı uygulama süresi**|-Geçerli işlev için işlev ve alt işlevleri harcanan süre. Değeri, işletim sistemi, bağlam anahtarları ve giriş/çıkış işlemleri gibi çağrılarında harcanan süreyi içermez.<br />-Çağıran işlev için kapsamlı uygulama süresi Bu çağıran işleve çağrılar tarafından oluşturulmuş geçerli işlevin miktarı.<br />-Çağrılan işlev için bu işlevdeki ve alt işlevleri tarafından oluşturulan için harcanan süre geçerli işlevden çağırır. Değer bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez.|  
|**Kapsamlı uygulama süresi yüzdesi**|Çalıştıran profil oluşturma toplam geçen kapsamlı süre yüzdesi bu işlevi bu bağlamda kapsamlı toplam uygulama süresi geçen süre.|  
|**Ortalama kapsamlı uygulama süresi**|Bu işlevi bu bağlamda bir çağrı, ortalama uygulama kapsamlı süre.|  
|**Maksimum kapsamlı uygulama süresi**|Bu bağlamda bu işlev çağrısı en fazla uygulama kapsamlı zamanı.|  
|**Minimum kapsamlı uygulama süresi**|En düşük uygulama kapsamlı süre bu işlevi bu bağlamda bir çağırma.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerleri alt işlevlerde harcanan zaman hariç işlevde harcanan zamanı gösterir. Belirtilen zaman da bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sisteminde geçen incalls olduğu süre dahil değildir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı uygulama süresi**|-Geçerli işlev için işlev gövdesi yürütme harcanan süre. Değer alt işlevlerde harcanan süreyi içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içermez.<br />-Çağıran işlev için bu çağıran işleve çağrılar tarafından oluşturulmuş geçerli işlevin dışlamalı uygulama süresi miktarı.<br />-Çağrılan işlev için bu harcanan süreyi geçerli işlevden tarafından oluşturulan işlevi çağırır. Değeri, çağrılan işlevin alt işlevlerde harcanan süreyi içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içermez.|  
|**Dışlamalı uygulama süresi yüzdesi**|Çalıştıran profil oluşturma toplam geçen dışlamalı süre yüzdesi bu bağlamda bu işlevin toplam uygulama dışlamalı süre geçen süre.|  
|**Ortalama dışlamalı uygulama süresi**|Bu işlevi bu bağlamda bir çağrı, ortalama uygulama dışlamalı süre.|  
|**Maksimum dışlamalı uygulama süresi**|Bu bağlamda bu işlev çağrısı en fazla uygulama özel zamanı.|  
|**Minimum dışlamalı uygulama süresi**|En düşük uygulama dışlamalı süre, bu bağlamda bu işlev çağrısı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Arayan/Aranan görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/Aranan görünümü - izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)   
 [Arayan / Aranan görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)



