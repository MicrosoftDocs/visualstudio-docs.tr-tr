---
title: Çağrı ağacı görünümü - izleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b42cce6c9134a668d5096150d986e950ed8a8e7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262237"
---
# <a name="call-tree-view---instrumentation-data"></a>Çağrı ağacı görünümü - izleme verileri
Bir işlev çağrısı ağacında değerlerini çağrısı ağacında üst işlevi tarafından çağrılan işlev örnekleri için zaman belirtin. Yüzde değerleri, toplam geçen dahil süre işlevi örneklerine profil çalıştırmada tüm işlevlerin değerini karşılaştırılmasıyla hesaplanır.  
  
## <a name="general"></a>Genel  
 Genel sütunları görünümü satırı işlevinde tanımlayın.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev adresi**|İşlev adresi.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Çağrı sayısı**|Bu işleve yapılan çağrı toplam sayısı.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İşleme atanan adı.|  
|**Zaman özel araştırma ek yükü**|Bu işlev süredir yükü, araçları tarafından neden oldu. Araştırma yükünü tüm özel sürelerinden çıkarılır.|  
|**Zaman dahil araştırması ek yükü**|Bu işlev ve onun alt işlevleri için ek yükü süresi, araçları tarafından neden oldu. Araştırma yükü tüm kapsayıcı sürelerinden çıkarılır.|  
|**düzeyi**|Çağrı ağacı işlevinde derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen dahil değerleri  
 Geçen dahil değerleri çağrısı ağacında üst işlevi tarafından çağrılan işlev örneklerine çağrı yığınını zamanını gösterir. Zaman harcanan zamanın işlevin adı veriliyordu alt işlevleri ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarını içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dahil süre**|Toplam bu işlevi bu bağlamda yapılan tüm çağrıların dahil süre geçti.|  
|**Geçen dahil süre %**|Çalıştıran profil oluşturma toplam geçen dahil süre yüzdesi bu işlevi bu bağlamda toplam geçen dahil süre geçen süre.|  
|**Ortalama dahil geçen zaman**|Ortalama bu işlevi bu bağlamda çağrısı dahil süre.|  
|**Max geçen dahil süre**|En fazla bu işlevi bu bağlamda çağrısı dahil süre.|  
|**Min (bunlar dahil) geçen zaman**|En düşük bu işlevi bu bağlamda çağrısı dahil süre.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen özel değerler  
 Geçen özel değerler üst işlev çağrısı ağacında tarafından çağrılan işlev örneklerine işlev gövdesine kodu yürütülmekte süre gösterir; diğer bir deyişle, ne zaman işlevi çağrı yığını üstünde oluştu. Zaman zaman bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarını içerir. Ancak, zaman harcanan zamanın işlevin adı veriliyordu alt işlevlerinde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen özel süre**|Toplam bu işlevi bu bağlamda yapılan tüm çağrıların özel zaman geçti.|  
|**Özel geçen süre %**|Çalıştıran profil oluşturma toplam geçen özel süre yüzdesi bu işlevi bu bağlamda toplam geçen özel zaman harcandığını.|  
|**Ortalama özel geçen zaman**|Ortalama bu işlevi bu bağlamda çağrısı özel süre.|  
|**Max geçen özel süre**|En fazla bu işlevi bu bağlamda çağrısı özel süre.|  
|**Min özel geçen zaman**|En düşük bu işlevi bu bağlamda çağrısı özel süre.|  
  
## <a name="application-inclusive-values"></a>Uygulama (bunlar dahil) değerleri  
 Uygulama dahil değerler çağrı yığınındaki çağrısı ağacında üst işlevi tarafından adlı bir işlev örnekleri olan süreyi belirtir. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez, ancak zaman harcanan zamanın işlevin adı veriliyordu alt işlevleri dahil.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama dahil süresi**|Toplam uygulama dahil süresi Bu işlevi bu bağlamda yapılan tüm çağrıların.|  
|**Uygulama dahil süresi %**|Çalıştıran profil oluşturma toplam geçen dahil süre yüzdesi bu işlevi bu bağlamda toplam uygulama dahil süresi geçen süre.|  
|**Ortalama uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı ortalama uygulama dahil saati.|  
|**En fazla uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı en fazla uygulama dahil saati.|  
|**Min uygulama dahil süresi**|Bu işlevi bu bağlamda çağrısı minimum uygulama dahil saati.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerler üst işlev çağrısı ağacında tarafından çağrılan işlev örneklerine doğrudan kod işlev gövdesine yürütülmekte, süre gösterir; diğer bir deyişle, ne zaman işlevi çağrı yığını üstünde oluştu. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez. Bu ayrıca harcanan zamanın işlevin adı veriliyordu alt işlevlerinde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama özel süresi**|Toplam uygulama özel süresi Bu işlevi bu bağlamda yapılan tüm çağrıların.|  
|**Uygulama özel süresi %**|Çalıştıran profil oluşturma toplam geçen özel süre yüzdesi bu işlevi bu bağlamda toplam uygulama özel süresini harcandığını.|  
|**Ortalama uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı ortalama uygulama özel saati.|  
|**En fazla uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı en fazla uygulama özel saati.|  
|**Min uygulama özel süresi**|Bu işlevi bu bağlamda çağrısı minimum uygulama özel saati.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Çağrı ağacı görünümü](../profiling/call-tree-view-sampling-data.md)   
 [Çağrı ağacı görünümü - izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Çağrı ağacı görünümü - örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)