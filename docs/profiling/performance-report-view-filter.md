---
title: Performans Rapor Görünümü Filtresi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 17fc42eab94d98ceb636e53e3ed6efd39a08f920
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254276"
---
# <a name="performance-report-view-filter"></a>Performans Raporu Görünüm Filtresi
**Profil Oluşturucusu Rapor Görünümü Filtresi** penceredir en üstünde bulunan **performans raporu** penceresi. Göremiyorsanız, tıklatın **Göster filtre** düğmesi.  
  
 Sonuçlarınızı daraltmak için her filtre yan tümcesi değiştirebilirsiniz. Aşağıdaki sütunlar filtresi Oluşturucu'da kullanılabilir.  
  
|Filtre öğesi|Açıklama|  
|-----------------|-----------------|  
|Ve/veya|Seçin **ve** bir sonuç eşleşiyorsa bu yan tümce sonraki yan tümcesi hem de girintili için olmalıdır. Seçin **veya** bir sonuç eşleşiyorsa bu yan tümcesi veya sonraki yan tümcesi girintili olabilir.|  
|Alan|Alanın filtre yan tümcesi geçerli rapor dosyasında kullanılabilir veri alanları listesinden kullanmak için seçin.|  
|İşleç|Alan ve değer arasında istediğiniz ilişkiyi belirten işleci seçin.<br /><br /> = Eşittir<br /><br /> <> Eşit değildir<br /><br /> < Küçüktür<br /><br /> > Büyüktür<br /><br /> < = küçüktür veya eşittir<br /><br /> > = büyüktür veya eşittir|  
|Değer|Aranacak bir değer girin veya seçin. Bazı alanları alan için kullanılabilir değerleri listeler.|  
  
 Filtre en iyi sonuçlar verir düşündüğünüz kadar filtre yan tümcesi ekleyebilirsiniz. Tıklatın **yürütme filtre** veri dosyasına filtre uygulamak için.  
  
 Gelen **işaretleri** rapor görünümü, verileri iki işaretleri arasında toplanan veriler için rapor görünümlerini sınırlandırmak için filtre yan tümcesi oluşturabilir. Başlangıç ve bitiş verileri, sonra sağ tıklatın ve seçin raporu istediğiniz işaretleri seçin **işaretleri üzerinde filtre Ekle** veya **zaman damgaları üzerinde filtre Ekle**. Her iki süzgeçleri aynı aralığa geçerli veri dosyasındaki verilerin sınırlar; **İşaretleri üzerinde filtre Ekle** diğer .vsp dosyalara uygulanabilir.  
  
 Filtre kaydetmek için tıklatın **verme filtresi** üzerinde **performans raporu** araç için bir konum ve dosya adı belirtin. *vspf* dosya. Daha önce kaydedilen bir filtreyi yüklemek için tıklayın **alma filtresi** ve kaydedilmiş filtre dosyasını bulun. Filtre dosyalar, veri dosyalarını bağımsız profil oluşturma araçları yüklü olan bilgisayarlarda filtre uygulamak için de kullanılabilir. Daha fazla bilgi için bkz: [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans araçları verilerini çözümleme](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)