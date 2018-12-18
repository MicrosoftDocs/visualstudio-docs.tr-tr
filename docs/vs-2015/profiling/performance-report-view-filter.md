---
title: Performans Raporu Görünüm Filtresi | Microsoft Docs
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
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26ab5282ece99700b035c45abe4f3a7c6ffee82a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754292"
---
# <a name="performance-report-view-filter"></a>Performans Raporu Görünüm Filtresi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler Rapor Görünümü Filtresi penceresi performans raporu penceresinin en üstünde bulunur. Göremiyorsanız, tıklayın **Göster filtre** düğmesi.  
  
 Her filtre yan tümcesi, sonuçlarınızı daraltmak için değiştirebilirsiniz. Aşağıdaki sütunlar, filtre Oluşturucusu'nda kullanılabilir.  
  
|Filtre öğesi|Açıklama|  
|-----------------|-----------------|  
|Ve/veya|Seçin **ve** eşleşiyorsa bir sonuç bu yan tümce hem de sonraki yan tümcesi her ikisi de true olmalıdır. Seçin **veya** eşleşiyorsa bir sonucu veya bu yan tümce hem de sonraki yan tümcesi True olabilir.|  
|Alan|Filtre yan tümcesi geçerli rapor dosyada kullanılabilir olan veri alanları listesinden kullanılacak bir alan seçin.|  
|İşleç|Alan ve değer arasında istediğiniz ilişkiyi belirtir işleci seçin.<br /><br /> = Eşittir<br /><br /> <> Eşit değildir<br /><br /> < Küçüktür<br /><br /> > Büyüktür<br /><br /> < = küçüktür veya eşittir<br /><br /> > = büyüktür veya eşittir|  
|Değer|Aranacak bir değer girin veya seçin. Bazı alanları, alan için kullanılabilen değerleri listeler.|  
  
 Filtre en iyi sonuçlar verecek düşündüğünüz kadar filtre yan tümce ekleyebilirsiniz. Tıklayın **yürütme filtre** veri dosyasına filtre uygulamak için.  
  
 Gelen **işaretleri** rapor görünümü, verileri iki işaretler arasında toplanan veriler için rapor görünümlerini sınırlandırmak için filtre yan tümcesi üretebilir. Başlangıç ve bitiş veri, sonra sağ tıklayıp ya da rapor için istediğiniz işaretleri seçin **işaretleri filtreye Ekle** veya **zaman damgalarına Filtre Ekle**. Her iki filtreleri aynı aralığa geçerli veri dosyasındaki verileri sınırlamak; **İşaretleri filtreye Ekle** diğer .vsp dosyalarına uygulanabilir.  
  
 Filtre kaydetmek için tıklatın **dışarı aktarma filtre** performans raporu araç ve .vspf dosyası için bir konum ve dosya adı belirtin. Daha önce kaydedilen bir filtreyi yüklemek için tıklayın **içeri aktarma filtre** ve kaydedilmiş filtre dosyasını bulun. Filtre dosyaları, veri dosyalarını bağımsız profil oluşturma araçları yüklü olan bilgisayarlarda filtrelemek için de kullanılabilir. Daha fazla bilgi için [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Araçları performansını analiz etme](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



