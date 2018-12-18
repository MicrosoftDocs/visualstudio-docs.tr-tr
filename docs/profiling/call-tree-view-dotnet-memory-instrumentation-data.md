---
title: .NET bellek izleme verileri çağrı ağacı görünümü - | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05286c10758c19f1e3f5a5692f814a096763544
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263604"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Çağrı ağacı görünümü - .NET bellek izleme verileri
Çağrı ağacı görünümü izleme metodunu kullanarak toplanan .NET bellek ayırma profil oluşturma veri profili uygulamada geçiş işlevi yürütme yollarını görüntüler. Ağaç kökü uygulamanın veya bileşenin içine giriş noktasıdır. Her işlevi düğümü adlı, tüm işlevlere ve .NET bellek ve zamanlama verileri işlevi için listeler.  
  
 Çağrı ağacı görünümü çağrısı ağacında üst işlevi tarafından çağrılan işlev örnekleri için değerler. Yüzde değerleri, toplam sayısı veya boyutu çalıştırmak profil ayırmalarının işlevi örneği değerini karşılaştırarak hesaplanır.  
  
## <a name="highlight-the-execution-hot-path"></a>Yürütme etkin yolunu Vurgula  
 Çağrı ağacı görünümü genişletin ve işlem veya en büyük oluşturulan işlevi ya da çoğu bellek nesneleri yürütme yolu vurgulayın. En etkin yol görüntülemek için işlem veya işlevi sağ tıklayın ve ardından **genişletin etkin yolunuzda**.  
  
## <a name="set-the-call-tree-root-node"></a>Çağrı ağacı kök düğümü ayarlayın  
 Profil oluşturma Çalıştır her işlem, bir kök düğümü olarak görüntülenir. Çağrı ağacı görünümü başlangıç düğümü başlangıç düğümü olarak ayarlamak istediğiniz düğümünü sağ tıklayarak ve ardından seçerek ayarlayabilirsiniz **ayarlamak kök**.  
  
 Kök düğüm kümesi olduğunda, Seçili düğümün alt ağacı dışında görünümünden diğer tüm girişleri kaldırın. Kök düğüm görüntülemekte olduğunuz düğüme geri sıfırlayabilirsiniz; Çağrı ağacı Görünümü penceresinde sağ tıklayın ve **sıfırlama kök**.  
  
## <a name="general"></a>Genel  
  
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
|**İşlem adı**|İşleme atanan adı.|  
|**Zaman özel araştırma ek yükü**|Bu işlev süredir yükü, araçları tarafından kaynaklanır. Araştırma yükünü tüm özel sürelerinden çıkarılır.|  
|**Zaman dahil araştırması ek yükü**|Bu işlev ve onun alt işlevleri için ek yükü süresi, araçları tarafından kaynaklanır. Araştırma yükü tüm kapsayıcı sürelerinden çıkarılır.|  
|**Türü**|İşlev Bağlam:<br /><br /> -   **0** -geçerli işlevi<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlevi<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kök işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
  
## <a name="net-memory-values"></a>.NET bellek değerleri  
 Bir işlevin dahil .NET bellek değerleri sayısını (ayırmaları) ve boyutunu (bayt) işlev ve işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri gösterir.  
  
 Özel bellek değerleri sayısını ve boyutunu değil işlev tarafından adı veriliyordu işlevleri ve işlev gövdesi kodda tarafından oluşturulan nesneleri gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsayıcı ayırmaları**|Bu işlev çağrısı ağacında üst işlevi tarafından adı veriliyordu örnekler tarafından ayrılan nesnelerin sayısı. Bu sayı, alt işlevleri tarafından yapılan ayırmaları içerir.|  
|**Kapsayıcı ayırmaları %**|Profil çalıştırdığınızda oluşturulan tüm nesneler yüzdesi çağrısı ağacında üst işlevi tarafından çağrılan işlevi örnekleri dahil ayırmaları yoktu.|  
|**Özel ayırmaları**|Bu işlev çağrısı ağacında üst işlevi tarafından adı veriliyordu örnekler tarafından ayrılan nesnelerin sayısı. Bu sayı, alt işlevleri tarafından yapılan ayırmaları içermez.|  
|**Özel ayırmaları %**|Profil çalıştırdığınızda oluşturulan tüm nesneler yüzdesi çağrısı ağacında üst işlevi tarafından çağrılan işlevi örneklerinin özel ayırmaları yoktu.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen dahil değerleri  
 Çağrı yığınındaki bir işlevi olan süresi geçen dahil değerleri gösterir. Zaman harcanan zamanın işlev tarafından çağrılan işlevler ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarını içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dahil süre**|Çağrı ağacı üst işlevinde tarafından çağrıldığında toplam bu işleve yapılan tüm çağrıların dahil süre geçti.|  
|**Geçen dahil süre %**|Çağrı ağacı üst işlevinde tarafından çağrıldığında toplam geçen dahil zaman bu işlevin harcandığını profil çalışma toplam geçen dahil zamanı yüzdesi.|  
|**Ortalama dahil geçen zaman**|Çağrı ağacı üst işlevinde tarafından çağrıldığında ortalama bu işlev çağrısının dahil zaman geçti.|  
|**Max geçen dahil süre**|Çağrı ağacı üst işlevinde tarafından çağrıldığında en fazla bu işlev çağrısının dahil zaman geçti.|  
|**Min (bunlar dahil) geçen zaman**|Çağrı ağacı üst işlevinde tarafından çağrıldığında en düşük bu işlev çağrısının dahil zaman geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen özel değerler  
 Bir işlev, doğrudan çağrı yığını üstünde yürütme süresi geçen özel değerleri gösterir. Zaman zaman bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarını içerir. Ancak, zaman harcanan zamanın işlevin adı veriliyordu işlevlerinde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen özel süre**|Çağrı ağacı üst işlevinde tarafından çağrıldığında toplam bu işleve yapılan tüm çağrıların özel zaman geçti.|  
|**Özel geçen süre %**|Çağrı ağacı üst işlevinde tarafından çağrıldığında toplam geçen özel zaman bu işlevin harcandığını profil çalışma toplam geçen özel zaman yüzdesi.|  
|**Ortalama özel geçen zaman**|Çağrı ağacı üst işlevinde tarafından çağrıldığında ortalama bu işlev çağrısının özel zaman geçti.|  
|**Max geçen özel süre**|En üst işlev çağrısı ağacında tarafından çağrıldığında bu işlev çağrısının özel süre.|  
|**Min özel geçen zaman**|En üst işlev çağrısı ağacında tarafından çağrıldığında bu işlev çağrısının özel süre.|  
  
## <a name="application-inclusive-values"></a>Uygulama (bunlar dahil) değerleri  
 Uygulama dahil değerler çağrı yığınındaki bir işlevi olan süreyi belirtir. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez. Zaman harcanan zamanın işlevin adı veriliyordu alt işlevlerinde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama dahil süresi**|Bu işlev çağrısı ağacında üst işlevi çağrıldığında tüm çağrıları toplam uygulama dahil saati.|  
|**Uygulama dahil süresi %**|Çağrı ağacı üst işlevinde tarafından çağrıldığında, bu işlevin toplam uygulama dahil süresi içinde harcandığını profil çalışma toplam geçen dahil zamanı yüzdesi.|  
|**Ortalama uygulama dahil süresi**|Ortalama uygulama dahil zamanı üst işlev çağrısı ağacında tarafından çağrıldığında bu işlevi çağrısı.|  
|**En fazla uygulama dahil süresi**|En fazla uygulama dahil zamanı üst işlev çağrısı ağacında tarafından çağrıldığında bu işlevi çağrısı.|  
|**Min uygulama dahil süresi**|Minimum uygulama dahil zamanı üst işlev çağrısı ağacında tarafından çağrıldığında bu işlevi çağrısı.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerler işlevin adı veriliyordu alt işlevlerinde harcanan zamanın hariç işlevindeki harcanan süreyi belirtir. Zamanı da bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları dışlar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama özel süresi**|Bu işlev çağrısı ağacında üst işlevi çağrıldığında tüm çağrıları toplam uygulama özel saati.|  
|**Uygulama özel süresi %**|Çağrı ağacı üst işlevinde tarafından çağrıldığında, bu işlev toplam uygulama özel zamanında harcandığını profil çalışma toplam geçen özel zamanı yüzdesi.|  
|**Ortalama uygulama özel süresi**|Ortalama uygulama özel zamanı üst işlev çağrısı ağacında tarafından çağrıldığında bu işlevi çağrısı.|  
|**En fazla uygulama özel süresi**|En fazla uygulama özel zamanı üst işlev çağrısı ağacında tarafından çağrıldığında bu işlevi çağrısı.|  
|**Min uygulama özel süresi**|Minimum uygulama özel zamanı üst işlev çağrısı ağacında tarafından çağrıldığında bu işlevi çağrısı.|