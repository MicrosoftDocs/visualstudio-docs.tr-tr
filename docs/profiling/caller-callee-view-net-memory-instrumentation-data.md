---
title: Caller-Callee görünümü-NET bellek Izleme verileri | Microsoft Docs
description: Seçilen bir işlev için ayırma ve zamanlama verilerini ve bunun üst ve alt işlevlerini gösteren .NET bellek profili oluşturma verilerinin arayan/çağrılan görünümünü gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3fa4928f9da81b2141eec76e54bce7887f50a074
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148084"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Arayan/Aranan görünümü-.NET bellek izleme verileri
İzleme yöntemi kullanılarak toplanan .NET bellek profili oluşturma verilerinin arayan/çağrılan görünümü seçili bir işlev için ayırma ve zamanlama verilerini ve seçilen işlevin üst ve alt işlevlerini görüntüler. Arayan/çağrılan görünümü üç kılavuz içerir.

 **Geçerli işlev** ortadaki kılavuzda görüntülenir ve seçili işlevle ilgili bellek profili oluşturma bilgilerini gösterir. Değerler, işleve tüm örneklenmiş çağrıları içerir.

 **Geçerli işlevi çağıran işlevler** üst kılavuzda görüntülenir ve çağıran (üst) işlevden çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerinin miktarını gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin aranan (alt) işlevlerine yönelik bellek profili oluşturma verilerini gösterir.

 Bu satırı geçerli işlev haline getirmek için bir arayan veya çağrılan işlev satırına çift tıklayın.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**İşlev adı**|İşlevin adı.|
|**İşlev adresi**|İşlevin adresi.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI.|
|**İşlem adı**|İşleme atanan ad.|
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlevin izleme nedeniyle zaman yükü. Araştırma ek yükü tüm özel zamanlarda çıkarıldı.|
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev için zaman yükü ve alt öğesi izleme nedeniyle alt işlevleri. Araştırma ek yükü tüm kapsamlı bir şekilde çıkarıldı.|
|**Tür**|İşlevin bağlamı:<br /><br /> **0** -geçerli işlev<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök Işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="net-memory-allocation-values"></a>.NET bellek ayırma değerleri

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı ayırmalar**|-Geçerli işlev için, işlev gövdesinde kod yürütürken oluşturulan nesne sayısı (yani, işlev çağrı yığınının en üstünde olduğunda). Numara, bu işlev tarafından çağrılan işlevlerde oluşturulmuş nesneleri içermez.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin özel ayırmaların sayısı.<br />-Bir çağrılan işlev için, bu işlevin geçerli işlev tarafından çağrılan örnekleri tarafından oluşturulan nesne sayısı. Bu sayı, çağrılan işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içermez.|
|**Dışlamalı ayırmalar%**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Kapsamlı ayırmalar**|-Geçerli işlev için, profil oluşturma çalıştırmasında işlev tarafından ayrılan nesne sayısı. Bu sayı, işlev tarafından çağrılan çağrılan işlevlerde oluşturulan nesneleri içerir.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin dahil olduğu ayırmaların sayısı.<br />-Bir çağrılan işlev için, geçerli işlevden çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan nesne sayısı. Bu sayı, bu çağrılan işlev tarafından çağrılan işlevlerin yaptığı ayırmaları içerir.|
|**Kapsamlı ayırmalar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Dışlamalı baytlar**|-Geçerli işlev için, profil oluşturma çalıştırmasında işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, işlev tarafından çağrılan çağrılan işlevlerde ayrılan belleği içermez.<br />-Çağıran işlevi için, bu çağıran işlev tarafından yapılan çağrılardan oluşturulan geçerli işlevin özel bayt sayısı.<br />-Bir çağrılan işlev için, bu işlevin, geçerli işlevden çağrılar tarafından oluşturulan örnekleri tarafından ayrılan bayt sayısı. Bu sayı, çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan baytları içermez.|
|**Dışlamalı bayt yüzdesi**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|
|**Kapsamlı baytlar**|-Geçerli işlev için, bellekteki, profil oluşturma çalıştırmasında ayrılan bayt sayısı. Bu sayı, işlev tarafından çağrılan çağrılan işlevlerde ayrılan belleği içerir.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin örneklerinin dahil edilen bayt sayısı.<br />-Bir çağrılan işlev için, bu işlevin, geçerli işlevden çağrılar tarafından oluşturulan örnekleri tarafından ayrılan bayt sayısı. Bu sayı, bu çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan baytları içerir.|
|**Dahil edilen baytlar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler
 Geçen kapsamlı değerler, bir işlevin çağrı yığınında olduğu süreyi belirtir. Süre, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen kapsamlı süre**|-Geçerli işlev için, işlevde harcanan zaman. Değer, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin geçen kapsamlı zaman miktarı.<br />-Bir çağrılan işlev için, bu işlevde harcanan zaman, geçerli işlevden çağrılar tarafından oluşturulmuştur. Değer, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.|
|**Geçen kapsamlı süre yüzdesi**|Bu bağlamda bu işlevin geçen iç zamanında harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama geçen kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının ortalama geçen kapsamlı süresi.|
|**Geçen maksimum kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının geçen maksimum kapsamlı süresi.|
|**Geçen minimum kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının geçen en düşük kapsamlı süre.|

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler
 Geçen dışlamalı değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Bu süre; bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıların süresini içerir, ancak alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen dışlamalı süre**|-Geçerli işlev için, işlevin gövdesinin yürütülmesi için harcanan zaman. Değer, alt işlevlerde harcanan süreyi dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları içerir.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin geçen dışlamalı süresinin miktarı.<br />-Bir çağrılan işlev için, bu işlevde harcanan zaman, geçerli işlevden çağrılar tarafından oluşturulmuştur. Değer, çağrılan işlevin alt işlevlerinde harcanan süreyi dışlar, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları içerir.|
|**Geçen dışlamalı süre yüzdesi**|Bu bağlamda bu işlevin toplam geçen dışlamalı süre içinde harcanan toplam çalışma zamanında geçen dışlamalı sürenin yüzdesi.|
|**Geçen ortalama dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının geçen ortalama dışlamalı süre.|
|**Geçen maksimum dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının geçen en büyük dışlamalı süresi.|
|**Geçen en düşük dışlamalı süre**|Bu bağlamda bu işleve yapılan çağrının en az geçen dışlamalı süresi.|

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler
 Uygulama kapsamlı değerleri bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez, ancak alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama kapsamlı süresi**|-Geçerli işlev için, işlevinde harcanan zaman ve alt işlevleri. Değer, işletim sistemine yapılan çağrılarında, bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan süreyi dışlar.<br />-Çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin uygulama kapsamlı süresi miktarı.<br />-Bir çağrılan işlev için, bu işlevde harcanan zaman ve geçerli işlevden çağrılar tarafından oluşturulan alt işlevleri. Değer, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez.|
|**Uygulama kapsamlı süresi%**|Bu bağlamda bu işlevin toplam uygulama kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama kapsamlı süresi.|
|**En fazla uygulama kapsamlı süresi**|Bu bağlamda bu işleve yapılan çağrının en büyük uygulama kapsamlı süresi.|
|**En az uygulama kapsamlı süre**|Bu bağlamda bu işleve yapılan çağrının en düşük uygulama kapsamlı süresi.|

## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri
 Uygulama dışlamalı değerleri, alt işlevlerde harcanan zamanı hariç olmak üzere işlevinde harcanan süreyi belirtir. Belirtilen zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi de dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı uygulama süresi**|-Geçerli işlev için, işlevin gövdesinin yürütülmesi için harcanan zaman. Değer, alt işlevlerde harcanan zamanı içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları dahil eder.<br />-Bir çağıran işlevi için, bu çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin uygulama dışlamalı zaman miktarı.<br />-Bir çağrılan işlev için, bu işlevde harcanan zaman, geçerli işlevden çağrılar tarafından oluşturulmuştur. Değer, çağrılan işlevin alt işlevlerinde harcanan zamanı içermez ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrı dahil eder.|
|**Uygulama dışlamalı süresi%**|Bu bağlamda bu işlevin toplam uygulama dışlamalı saatinde harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Ortalama uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.|
|**Maksimum uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.|
|**En az uygulama dışlamalı süresi**|Bu bağlamda bu işleve yapılan çağrının en düşük uygulama dışlamalı süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Aranan görünümü-.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/çağrılan görünümü-izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)
- [Çağıran/çağrılan görünümü-örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
