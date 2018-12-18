---
title: EventSource olaylarını işaretleyici olarak Görselleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e6c28682bb6b93a2a72aaa353a2af68a9450cb9
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058597"
---
# <a name="visualize-eventsource-events-as-markers"></a>EventSource olaylarını işaretleyici olarak Görselleştirme
Eşzamanlılık görselleştiricisi EventSource olaylarını işaretleyici olarak görüntüleyebilir ve işaretlerinin görüntülenme biçimini kontrol edebilirsiniz. EventSource işaretçileri görüntülemek için GUID ETW sağlayıcısını kullanarak kayıt [Gelişmiş ayarları](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusu. Eşzamanlılık görselleştiricisi EventSource olaylarını olarak göstermek için varsayılan kuralları sahip [bayrak işaretleyicileri](../profiling/flag-markers.md), [aralık işaretçileri](../profiling/span-markers.md), ve [ileti işaretçileri](../profiling/message-markers.md). EventSource olaylarını olaylara özel alanlar ekleyerek görüntülenme biçimini özelleştirebilirsiniz. İşaretçileri hakkında daha fazla bilgi için bkz: [eşzamanlılık görselleştiricisi işaretleyicileri](../profiling/concurrency-visualizer-markers.md). EventSource olaylarını hakkında daha fazla bilgi için bkz: <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>EventSource olayların varsayılan Görselleştirme  
 Varsayılan olarak, eşzamanlılık görselleştiricisi EventSource olaylarını göstermek için aşağıdaki kuralları kullanır.  
  
### <a name="marker-type"></a>İşaret türü  
  
1.  Olayları [Opcode](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win: başlangıç veya win: Durdur kabul edilir başına veya sonuna bir aralık sırasıyla.  İç içe geçmiş veya yayılma çakışan görüntülenemiyor. Bir iş parçacığı üzerinde başlayan ve başka birinde son olay çiftleri görüntülenemiyor.  
  
2.  Sürece, işlem kodu win: Başlangıç ne win: Durdur bir olay işaret bayrak olarak kabul edilir kendi [düzeyi](/windows/desktop/WES/defining-severity-levels) (EVENT_RECORD alanı. EVENT_HEADER. EVENT_DESCRIPTOR) olan win: ayrıntılı ya da daha yüksek.  
  
3.  Diğer durumlarda, olay iletisi olarak kabul edilir.  
  
### <a name="importance"></a>Önem derecesi  
 Aşağıdaki tabloda, olay düzeyi işaret önem nasıl eşlendiğini tanımlar.  
  
|ETW düzey|Eşzamanlılık görselleştiricisi önem|  
|---------------|---------------------------------------|  
|Win: LogAlways|Normal|  
|Win: kritik|Kritik|  
|Win: hata|Kritik|  
|Win: uyarı|Yüksek|  
|Win: bilgi|Normal|  
|Win: ayrıntılı|Düşük|  
|Win büyüktür: ayrıntılı|Düşük|  
  
### <a name="series-name"></a>Seri adı  
 Olayın görev adı için seri adı kullanılır. Seri adı hiçbir görev olayı için tanımlanmışsa boştur.  
  
### <a name="category"></a>Kategori  
 Düzeyi win ise: kritik veya win: hata sonra kategori uyarı (-1). Aksi takdirde, kategori (0) varsayılandır.  
  
### <a name="text"></a>Metin  
 Printf türü biçimlendirilmiş metin iletisi olay için tanımlanan değilse işaret açıklaması görüntülenir. Aksi takdirde, olayın adı ve her yükü alanının değeri açıklamasıdır.  
  
## <a name="customize-visualization-of-eventsource-events"></a>EventSource olaylarını görselleştirme özelleştirme  
 EventSource olaylarını olaya uygun alanlar ekleyerek aşağıdaki bölümlerde açıklandığı gibi görüntülenme biçimini özelleştirebilirsiniz.  
  
### <a name="marker-type"></a>İşaret türü  
 Kullanım `cvType` alan, olay temsil etmek için kullanılan işaret türünü denetlemek için bir bayt. CvType için kullanılabilir değerleri şunlardır:  
  
|cvType değeri|Sonuçta elde edilen işaret türü|  
|------------------|---------------------------|  
|0|İleti|  
|1.|Aralık başlangıcı|  
|2|Aralık sonu|  
|3|Bayrağı|  
|Diğer tüm değerler|İleti|  
  
### <a name="importance"></a>Önem derecesi  
 Kullanabileceğiniz `cvImportance` alan, bir EventSource olay önem ayarını denetlemek için bir bayt. Ancak, alt düzey kullanarak bir olay görüntülenen önemini kontrol öneririz.  
  
|cvImportance değeri|Eşzamanlılık görselleştiricisi önem|  
|------------------------|---------------------------------------|  
|0|Normal|  
|1.|Kritik|  
|2|Yüksek|  
|3|Yüksek|  
|4|Normal|  
|5|Düşük|  
|Diğer tüm değerler|Düşük|  
  
### <a name="series-name"></a>Seri adı  
 Kullanım `cvSeries` olay alanı, eşzamanlılık görselleştiricisi EventSource olaya verir seri adı denetlemek için bir dize.  
  
### <a name="category"></a>Kategori  
 Kullanım `cvCategory` alan, eşzamanlılık görselleştiricisi EventSource olaya verir kategori denetlemek için bir bayt.  
  
### <a name="text"></a>Metin  
 Kullanım `cvTextW` alan, eşzamanlılık görselleştiricisi EventSource olaya içeren açıklama denetlemek için bir dize.  
  
### <a name="spanid"></a>SpanID  
 Olayları çiftlerini eşleşecek şekilde, int cvSpanId alanını kullanın. Değer bir aralık temsil Başlat/Durdur olayların her çifti için benzersiz olmalıdır. Genellikle eşzamanlı kodu için bu eşitleme temelleri gibi kullanımını <xref:System.Threading.Interlocked.Exchange%2A> (CvSpanID için kullanılan değer) anahtarının doğru olduğundan emin olmak için.  
  
> [!NOTE]
>  Bunları kısmen aynı iş parçacığı üzerinde üst üste veya bunları bir iş parçacığında başlatmaya izin vermek yayılma, iç içe SpanID kullanılmasına izin verin ve başka bir uç desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eşzamanlılık görselleştiricisi işaretleyicileri](../profiling/concurrency-visualizer-markers.md)