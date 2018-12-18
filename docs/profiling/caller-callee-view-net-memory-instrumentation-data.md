---
title: Arayan Aranan görünümü - NET bellek izleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6005bfcd4c69220c26929a8ad57f0e37923f388c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265507"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Arayan/Aranan görünümü - .NET bellek izleme verileri
Arayan/Aranan görünümü .NET bellek izleme metodunu kullanarak toplanan verileri profil ayırma ve seçili işlev ve seçilen bu işlev üst ve alt işlevlerini için zamanlama verilerini görüntüler. Arayan/Aranan görünümü üç kılavuzları içerir.  
  
 **Geçerli işlevi** Orta kılavuzunda görüntülenir ve bellek profili oluşturma seçili işlevi hakkında bilgi gösterir. Tüm örneklenen işlev çağrıları değerlerini içerir.  
  
 **Geçerli işlevini çağırdı işlevleri** üst kılavuzunda görüntülenir ve arayan (üst) işlevi gelen çağrıları tarafından üretildi. Seçili (geçerli) işlevinin değeri miktarını gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzunda görüntülenir ve alt işlevi geçerli bir işlev tarafından çağrıldığında profil oluşturma verilerini seçili işlevi ' Aranan (alt) işlevleri için bellek miktarını gösterir.  
  
 Geçerli işlev satır yapmak için bir çağıran veya Aranan işlevi satırı çift tıklatın.  
  
## <a name="general"></a>Genel  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev adresi**|İşlev adresi.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Çağrı sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**İşlem kimliği**|Çalıştırma profili oluşturma, işlem kimliği.|  
|**İşlem adı**|İşleme atanan adı.|  
|**Zaman özel araştırma ek yükü**|Araçları nedeniyle bu işlev için ek süre. Araştırma yükünü tüm özel sürelerinden çıkarılır.|  
|**Zaman dahil araştırması ek yükü**|Bu işlev ve araçları nedeniyle alt işlevleri için ek yükü süresi. Araştırma yükü tüm kapsayıcı sürelerinden çıkarılır.|  
|**Türü**|İşlev Bağlam:<br /><br /> **0** -geçerli işlevi<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlevi<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kök işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
  
## <a name="net-memory-allocation-values"></a>.NET bellek ayırma değerleri  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Özel ayırmaları**|-Geçerli işlev, işlev kodunu işlev gövdesine yürütülmekte olan yükleyen oluşturulan nesne sayısı için (diğer bir deyişle, ne zaman işlevi çağrı yığını üstünde olduğu). Sayı, bu işlev tarafından adı veriliyordu işlevlerinde oluşturulan nesneleri içermez.<br />-Çağıran işlev için geçerli işlevi bu çağıran işlev gelen çağrıları tarafından oluşturulan özel ayrılmasını sayısı.<br />-Çağrılan işlev için geçerli işlev tarafından çağrılan bu işlev örnekleri tarafından oluşturulan nesne sayısı. Bu sayı, çağrılan işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içermez.|  
|**Özel ayırmaları %**|Profil çalıştırdığınızda oluşturulan tüm nesneler yüzdesi bu işlevin özel ayırmaları yoktu.|  
|**Kapsayıcı ayırmaları**|-Geçerli işlev için profil oluşturma işlevi tarafından ayrılan nesne sayısını çalıştırın. İşlevin adı veriliyordu Aranan işlevlerinde oluşturulan nesneleri içerir.<br />-Çağıran işlev için geçerli işlevi bu çağıran işlev gelen çağrıları tarafından oluşturulan dahil ayrılmasını sayısı.<br />-Çağrılan işlev için geçerli işlevi gelen çağrıları tarafından oluşturulan bu işlev örnekleri tarafından ayrılan nesne sayısı. Bu çağrılan işlev tarafından çağrılan işlevler tarafından yapılan ayırmaları sayısını içerir.|  
|**Kapsayıcı ayırmaları %**|Profil çalıştırdığınızda oluşturulan tüm nesneler yüzdesi bu işlevin kapsayıcı ayırmaları yoktu.|  
|**Özel bayt sayısı**|-Geçerli işlev için profil oluşturma işlevi tarafından ayrılan belleğin bayt sayısını çalıştırın. Sayı ayrılmış bellek işlev tarafından çağrılan Aranan işlevleri içermez.<br />-Çağıran işlevi için oluşturulmuş geçerli işlevinin özel bayt sayısı tarafından bu çağıran işlevi çağırır.<br />-Çağrılan işlev için geçerli işlevi gelen çağrıları tarafından oluşturulan bu işlev örnekleri tarafından ayrılan bayt sayısı. Çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan bayt sayısı dahil değildir.|  
|**Özel bayt %**|Profil çalışmasını ayrılan tüm bayt bellek yüzdesi bu işlevin özel ayırmaları yoktu.|  
|**Kapsayıcı bayt**|-Geçerli işlev için profil oluşturma işlevi tarafından ayrılan belleği bayt sayısı çalıştırın. İşlevin adı veriliyordu Aranan işlevlerinde ayrılmış bellek sayısını içerir.<br />-Çağıran işlev için bu çağıran işlev gelen çağrıları tarafından oluşturulmuş geçerli işlevi örneklerini dahil bayt sayısı.<br />-Çağrılan işlev için geçerli işlevi gelen çağrıları tarafından oluşturulan bu işlev örnekleri tarafından ayrılan bayt sayısı. Bu çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan bayt sayısını içerir.|  
|**Kapsayıcı bayt %**|Profil çalışmasını ayrılan tüm bayt bellek yüzdesi bu işlevin kapsayıcı ayırmaları yoktu.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen dahil değerleri  
 Çağrı yığınındaki bir işlevi olan süresi geçen dahil değerleri gösterir. Zaman harcanan zamanın alt işlevleri ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarını içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dahil süre**|-Geçerli işlevi için işlevinde harcanan süre. Değer alt işlevleri ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içerir.<br />-Çağıran işlevi için bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevinin geçen dahil süre miktarı.<br />-Aranan işlevi için bu harcanan zamanın geçerli işlevinden tarafından üretildi işlevi çağırır. Değer alt işlevleri ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içerir.|  
|**Geçen dahil süre %**|Bu işlevi bu bağlamda geçen dahil süre harcandığını profil Çalıştır toplam geçen dahil zamanı yüzdesi.|  
|**Ortalama dahil geçen zaman**|Ortalama bu işlevi bu bağlamda çağrısı dahil süre.|  
|**Max geçen dahil süre**|En fazla bu işlevi bu bağlamda çağrısı dahil süre.|  
|**Min (bunlar dahil) geçen zaman**|En düşük bu işlevi bu bağlamda çağrısı dahil süre.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen özel değerler  
 Bir işlev, doğrudan çağrı yığını üstünde yürütme süresi geçen özel değerleri gösterir. Zaman zaman bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içerir ancak harcanan zamanın alt işlevlerde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen özel süre**|-Geçerli işlevi için işlevinin gövdesini yürütme harcanan süre. Değer alt işlevlerde geçen süre, ancak İçerik Geçişi ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içeren zamanı dışlar.<br />-Çağıran işlev için bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevinin özel geçen süre.<br />-Aranan işlevi için bu harcanan zamanın geçerli işlevinden tarafından üretildi işlevi çağırır. Değer, aranan işlevi alt işlevlerde geçen süre, ancak İçerik Geçişi ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içeren zamanı dışlar.|  
|**Özel geçen süre %**|Çalıştıran profil oluşturma toplam geçen özel süre yüzdesi bu işlevi bu bağlamda toplam geçen özel zaman harcandığını.|  
|**Ortalama özel geçen zaman**|Ortalama bu işlevi bu bağlamda çağrısı özel süre.|  
|**Max geçen özel süre**|En fazla bu işlevi bu bağlamda çağrısı özel süre.|  
|**Min özel geçen zaman**|En düşük bu işlevi bu bağlamda çağrısı özel süre.|  
  
## <a name="application-inclusive-values"></a>Uygulama (bunlar dahil) değerleri  
 Uygulama dahil değerler çağrı yığınındaki bir işlevi olan süreyi belirtir. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez ancak alt işlevlerde harcanan zamanın içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama dahil süresi**|-Geçerli işlevi için işlevi ve onun alt işlevlerde geçen süre. Değer bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın dışlar.<br />-Çağıran işlevi için bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevinin uygulama dahil süre miktarı.<br />-Çağrılan işlev için geçerli işlevi gelen çağrıları tarafından üretildi. Bu işlev ve onun alt işlevlerde harcanan zamanın. Değer, bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez.|  
|**Uygulama dahil süresi %**|Çalıştıran profil oluşturma toplam geçen dahil süre yüzdesi bu işlevi bu bağlamda toplam uygulama dahil süresi geçen süre.|  
|**Ortalama uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı ortalama uygulama dahil saati.|  
|**En fazla uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı en fazla uygulama dahil saati.|  
|**Min uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı minimum uygulama dahil saati.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerler alt işlevlerde geçen zaman hariç işlevindeki harcanan süreyi belirtir. Belirtilen zaman da bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi için harcanan incalls olduğu zamanı dışlar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama özel süresi**|-Geçerli işlevi için işlevinin gövdesini yürütme harcanan süre. Değer alt işlevlerde harcanan zamanın içermez ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içermez.<br />-Çağıran işlev için bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevinin uygulama özel süre miktarı.<br />-Aranan işlevi için bu harcanan zamanın geçerli işlevinden tarafından üretildi işlevi çağırır. Değer Aranan işlevi alt işlevlerde harcanan zamanın içermez ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içermez.|  
|**Uygulama özel süresi %**|Çalıştıran profil oluşturma toplam geçen özel süre yüzdesi bu işlevi bu bağlamda toplam uygulama özel süresini harcandığını.|  
|**Ortalama uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı ortalama uygulama özel saati.|  
|**En fazla uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı en fazla uygulama özel saati.|  
|**Min uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı minimum uygulama özel saati.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Arayan/Aranan görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/Aranan görünümü - izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)   
 [Arayan/Aranan görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)