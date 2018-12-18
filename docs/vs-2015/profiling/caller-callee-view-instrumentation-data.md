---
title: Arayan-Aranan görünümü - izleme verileri | Microsoft Docs
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
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bbba1d9e169f82c7c43907bae87894de1dbcb9f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775790"
---
# <a name="callercallee-view---instrumentation-data"></a>Arayan/Aranan görünümü - izleme verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arayan/Aranan görünümü seçili işlev ve üst ve alt işlevleri hakkında profil bilgileri çağrı ağacında görüntüler. Arayan/Aranan görünümü üç Kılavuzlar içerir.  
  
 **Geçerli işlev** Orta Kılavuz ve bunun görüntülenen profil oluşturma seçili işlev hakkında bilgi gösterir. İşlev çağrıları tüm değerleri içerir.  
  
 **Geçerli işlevi çağırmış işlevler** üst kılavuz ve bunun görüntülenen profil oluşturma seçili işlev çağıran (üst) işlevleri hakkında bilgi gösterir. Değerleri bu çağıran işlev çağrılarının tarafından oluşturulmuş geçerli işlev değerini miktarını gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuz ve bunun görüntülenen profil oluşturma seçili işlev (alt) çağrılan işlevlerin örnekleri hakkında bilgi gösterir. Değerleri yalnızca geçerli işlev tarafından çağrıldığında alt işlevde harcanan zamanı gösterir.  
  
## <a name="general"></a>Genel  
 Genel sütunları bir görünüm satır işlevi tanımlar.  
  
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
|**İşlem adı**|İşlemin adı.|  
|**Zaman dışlamalı araştırma ek yükü**|Zaman ek yükü bu işlev, ölçümlü izlemeyle neden oldu. Tüm özel sürelerinden çıkarıldığında araştırma ek yükü.|  
|**Zaman kapsamlı araştırma ek yükü**|Zaman ek yükü Bu işlevde ve alt işlevleri, ölçümlü izlemeyle neden oldu. Tüm kapsamlı sürelerinden çıkarıldığında araştırma ek yükü.|  
|**Türü**|İşlevin bağlamı:<br /><br /> **0** -geçerli işlevi<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kök işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerleri  
 Geçen kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Zaman alt işlevlerde harcanan zaman ve işletim sistemi, bağlam anahtarları ve giriş/çıkış işlemleri gibi çağrılarında harcanan süreyi içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen kapsamlı süre**|-Geçerli işlev için işlevde harcanan süre. Değer, alt işlevleri ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları harcanan süreyi içerir.<br />-Çağıran işlev için bu çağıran işleve çağrılar tarafından oluşturulmuş geçerli işlevin geçen kapsamlı süre miktarı.<br />-Çağrılan işlev için bu işlev çağrıları geçerli işlevden tarafından oluşturulan örneklerinde için harcanan süre. Değeri, çağrılan alt işlevlerini ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan zaman içerir.|  
|**Geçen kapsamlı süre yüzdesi**|Geçen kapsamlı süre bu işlevi bu bağlamda harcandığını profil oluşturma çalışması toplam geçen kapsamlı süre yüzdesi.|  
|**Geçen ortalama kapsamlı süre**|Ortalama kapsamlı süre bu bağlamda bu işlev çağrısına geçti.|  
|**Geçen maksimum kapsamlı süre**|Maksimum kapsamlı süre bu bağlamda bu işlev çağrısına geçti.|  
|**Geçen minimum kapsamlı süre**|Minimum kapsamlı süre bu bağlamda bu işlev çağrısına geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerleri  
 Geçen dışlamalı değerleri bir işlev doğrudan çağrı yığınının en üstünde çağırılma yürütüldüğü zaman gösterir. Bağlam geçişleri ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan zaman zaman içerir, ancak alt işlevlerde harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dışlamalı süre**|-Geçerli işlev için işlevin doğrudan yürütme harcanan zamanı. Değer, alt işlevleri ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları harcanan süreyi içerir.<br />-Çağıran işlev için bu çağıran işleve çağrılar tarafından oluşturulmuş geçerli işlevin geçen dışlamalı süre miktarı.<br />-Çağrılan işlev için bu işlev çağrıları geçerli işlevden tarafından oluşturulan örneklerinde için harcanan süre. Değeri, çağrılan işlevin alt işlevlerde harcanan zaman içermez, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içerir.|  
|**Geçen dışlamalı süre yüzdesi**|Çalıştıran profil oluşturma toplam geçen dışlamalı süre yüzdesi bu işlevi bu bağlamda toplam geçen dışlamalı süre geçen süre.|  
|**Geçen ortalama dışlamalı süre**|Ortalama dışlamalı süre bu bağlamda bu işlev çağrısına geçti.|  
|**Geçen maksimum dışlamalı süre**|Maksimum dışlamalı süre bu bağlamda bu işlev çağrısına geçti.|  
|**Geçen minimum dışlamalı süre**|Minimum dışlamalı süre bu bağlamda bu işlev çağrısına geçti.|  
  
## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerlerini  
 Uygulama kapsamlı değerleri, çağrı yığınındaki bir işlevi olduğu zamanı gösterir. Süresi, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez, ancak alt işlevlerde harcanan süreyi içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsamlı uygulama süresi**|-Geçerli işlev için işlev ve alt işlevleri harcanan süre. Değeri, işletim sistemi, bağlam anahtarları ve giriş/çıkış işlemleri gibi çağrılarında harcanan süreyi içermez.<br />-Çağıran işlev için kapsamlı uygulama süresi Bu çağıran işleve çağrılar tarafından oluşturulmuş geçerli işlevin miktarı.<br />-Çağrılan işlev için bu işlev çağrıları geçerli işlevden tarafından oluşturulan örneklerinde için harcanan süre. Değer alt işlevleri çağrılan işlevin harcanan süreyi içerir, ancak bu harcanan zaman bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında içermez.|  
|**Kapsamlı uygulama süresi yüzdesi**|Çalıştıran profil oluşturma toplam geçen kapsamlı süre yüzdesi bu işlevi bu bağlamda kapsamlı toplam uygulama süresi geçen süre.|  
|**Ortalama kapsamlı uygulama süresi**|Bu işlevi bu bağlamda bir çağrı, ortalama uygulama kapsamlı süre.|  
|**Maksimum kapsamlı uygulama süresi**|Bu bağlamda bu işlev çağrısı en fazla uygulama kapsamlı zamanı.|  
|**Minimum kapsamlı uygulama süresi**|En düşük uygulama kapsamlı süre bu işlevi bu bağlamda bir çağırma.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerlerini işlevde harcanan zamanı gösterir. Bu alt işlevlerde geçen süre ve aynı zamanda bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları hariç süre dahil değildir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı uygulama süresi**|-Geçerli işlev için işlevin doğrudan yürütme harcanan zamanı. Değer alt işlevlerde harcanan süreyi içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içermez.<br />-Çağıran işlev için bu çağıran işleve çağrılar tarafından oluşturulmuş geçerli işlevin dışlamalı uygulama süresi miktarı.<br />-Çağrılan işlev için bu işlev çağrıları geçerli işlevden tarafından oluşturulan örneklerinde için harcanan süre. Değeri, çağrılan işlevin alt işlevlerde harcanan süreyi içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrıları içermez.|  
|**Dışlamalı uygulama süresi yüzdesi**|Çalıştıran profil oluşturma toplam geçen dışlamalı süre yüzdesi bu bağlamda bu işlevin toplam uygulama dışlamalı süre geçen süre.|  
|**Ortalama dışlamalı uygulama süresi**|Bu işlevi bu bağlamda bir çağrı, ortalama uygulama dışlamalı süre.|  
|**Maksimum dışlamalı uygulama süresi**|Bu bağlamda bu işlev çağrısı en fazla uygulama özel zamanı.|  
|**Minimum dışlamalı uygulama süresi**|En düşük uygulama dışlamalı süre, bu bağlamda bu işlev çağrısı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Arayan / Aranan görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)   
 [Arayan/Aranan görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/Aranan görünümü - .NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)



