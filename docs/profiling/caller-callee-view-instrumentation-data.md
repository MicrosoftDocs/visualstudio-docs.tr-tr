---
title: Arayan Aranan görünümü - izleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8a24d19fabc3cb82dbb4004ec71b6fa00bc470c
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34336119"
---
# <a name="callercallee-view---instrumentation-data"></a>Arayan/Aranan görünümü - izleme verileri
Arayan/Aranan görünümü çağrısı ağacında seçilen işlevi ve üst ve alt işlevleri profil bilgilerini görüntüler. Arayan/Aranan görünümü üç kılavuzları içerir.  
  
 **Geçerli işlevi** Orta Kılavuz ve bunun görüntülenen profil seçili işlevi hakkında bilgi gösterir. İşlev tüm çağrıları değerlerini içerir.  
  
 **Geçerli işlevini çağırdı işlevleri** üst kılavuz ve bunun görüntülenen profil seçili işlevi çağıran (üst) işlevleri hakkında bilgi gösterir. Değerleri bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevi değerini miktarını gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuz ve bunun görüntülenen profil seçili işlevinin Aranan (alt) işlevleri örnekleri hakkında bilgi gösterir. Değerleri geçerli işlevi tarafından çağrıldığında, alt işlevinde harcanan zamanı gösterir.  
  
## <a name="general"></a>Genel  
 Genel sütunları görünümü satırı işlevinde tanımlayın.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev adresi**|İşlev adresi.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Çağrı sayısı**|Bu işleve yapılan çağrılar toplam sayısı.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Zaman özel araştırma ek yükü**|Bu işlev süredir yükü, araçları tarafından neden oldu. Araştırma yükünü tüm özel sürelerinden çıkarılır.|  
|**Zaman dahil araştırması ek yükü**|Bu işlev ve onun alt işlevleri için ek yükü süresi, araçları tarafından neden oldu. Araştırma yükü tüm kapsayıcı sürelerinden çıkarılır.|  
|**Türü**|İşlev Bağlam:<br /><br /> **0** -geçerli işlevi<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlevi<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kök işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen dahil değerleri  
 Çağrı yığınındaki bir işlevi olan süresi geçen dahil değerleri gösterir. Zaman alt işlevlerde geçen süre ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dahil süre**|-Geçerli işlevi için işlevinde harcanan süre. Değer alt işlevleri ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içerir.<br />-Çağıran işlevi için bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevinin geçen dahil süre miktarı.<br />-Çağrılan işlev için geçerli işlevi gelen çağrıları tarafından oluşturulan bu işlev örneklerinde harcanan süre. Değer, Aranan alt işlevlerini ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içerir.|  
|**Geçen dahil süre %**|Bu işlevi bu bağlamda geçen dahil süre harcandığını profil Çalıştır toplam geçen dahil zamanı yüzdesi.|  
|**Ortalama dahil geçen zaman**|Ortalama bu işlevi bu bağlamda çağrısı dahil süre.|  
|**Max geçen dahil süre**|En fazla bu işlevi bu bağlamda çağrısı dahil süre.|  
|**Min (bunlar dahil) geçen zaman**|En düşük bu işlevi bu bağlamda çağrısı dahil süre.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen özel değerler  
 Bir işlev, doğrudan çağrı yığını üstünde yürütme süresi geçen özel değerleri gösterir. İçerik Geçişi ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın zaman içerir ancak harcanan zamanın alt işlevlerde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen özel süre**|-Geçerli işlevi için işlevin doğrudan yürütmede harcanan süre. Değer alt işlevleri ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içerir.<br />-Çağıran işlev için bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevinin özel geçen süre.<br />-Çağrılan işlev için geçerli işlevi gelen çağrıları tarafından oluşturulan bu işlev örneklerinde harcanan süre. Aranan işlevi alt işlevlerde harcanan zamanı değeri dışlar, ancak bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarını içerir.|  
|**Özel geçen süre %**|Çalıştıran profil oluşturma toplam geçen özel süre yüzdesi bu işlevi bu bağlamda toplam geçen özel zaman harcandığını.|  
|**Ortalama özel geçen zaman**|Ortalama bu işlevi bu bağlamda çağrısı özel süre.|  
|**Max geçen özel süre**|En fazla bu işlevi bu bağlamda çağrısı özel süre.|  
|**Min özel geçen zaman**|En düşük bu işlevi bu bağlamda çağrısı özel süre.|  
  
## <a name="application-inclusive-values"></a>Uygulama (bunlar dahil) değerleri  
 Uygulama dahil değerler çağrı yığınındaki bir işlevi olan süreyi belirtir. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez ancak alt işlevlerde harcanan zamanın içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama dahil süresi**|-Geçerli işlevi için işlevi ve onun alt işlevlerde geçen süre. Değer bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın dışlar.<br />-Çağıran işlevi için bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevinin uygulama dahil süre miktarı.<br />-Çağrılan işlev için geçerli işlevi gelen çağrıları tarafından oluşturulan bu işlev örneklerinde harcanan süre. Değer harcanan zamanın Aranan işlevi alt işlevlerde içerir, ancak bu harcanan zamanın bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında içermez.|  
|**Uygulama dahil süresi %**|Çalıştıran profil oluşturma toplam geçen dahil süre yüzdesi bu işlevi bu bağlamda toplam uygulama dahil süresi geçen süre.|  
|**Ortalama uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı ortalama uygulama dahil saati.|  
|**En fazla uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı en fazla uygulama dahil saati.|  
|**Min uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı minimum uygulama dahil saati.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerler işlevinde harcanan süreyi belirtir. Bu alt işlevlerde geçen süre ve ayrıca bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları dışlar zamanı dışlar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama özel süresi**|-Geçerli işlevi için işlevin doğrudan yürütmede harcanan süre. Değer alt işlevlerde harcanan zamanın içermez ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içermez.<br />-Çağıran işlev için bu çağıran işlev gelen çağrıları tarafından üretildi. geçerli işlevinin uygulama özel süre miktarı.<br />-Çağrılan işlev için geçerli işlevi gelen çağrıları tarafından oluşturulan bu işlev örneklerinde harcanan süre. Değer Aranan işlevi alt işlevlerde harcanan zamanın içermez ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içermez.|  
|**Uygulama özel süresi %**|Çalıştıran profil oluşturma toplam geçen özel süre yüzdesi bu işlevi bu bağlamda toplam uygulama özel süresini harcandığını.|  
|**Ortalama uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı ortalama uygulama özel saati.|  
|**En fazla uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı en fazla uygulama özel saati.|  
|**Min uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı minimum uygulama özel saati.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Arayan/Aranan görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)   
 [Arayan/Aranan görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/Aranan görünümü - .NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)