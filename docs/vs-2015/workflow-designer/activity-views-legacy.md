---
title: Etkinlik görünümleri (eski) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e5fb8368228118b210865b1a351d12b1b5da4b27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229324"
---
# <a name="activity-views-legacy"></a>Etkinlik Görünümleri (Eski)
Tarafından sağlanan etkinliklerinin birçok [!INCLUDE[wf](../includes/wf-md.md)], hangi iş akışları öğesinden oluşur, çeşitli tasarım görünümlerini eski içinde kullanılabilir olan [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Bir etkinlik Tasarımcısı'ndan sürüklediğinizde **araç kutusu** tasarım yüzeyine ve bundan sonra etkinliği seçtiğinizde kullanın ya da farklı tasarım görünümler arasında geçiş yapabilirsiniz **iş akışı**menü veya sağ tıklayarak seçili etkinlik. Seçili etkinlik adı üzerinde işaretçiyi getirdiğinizde, ayrıca, farklı görünümler arasında geçiş yapmak için kullanabileceğiniz bir sekme açılır kümesi görünür.  
  
 Her etkinlik, en az bir görünüme sahiptir; Bu bir etkinlik Tasarımcısı'ndan sürüklediğinizde gösterilen varsayılan görünümü şu şekildedir **araç kutusu** tasarım yüzeyine. Bu etkinlik varsayılan görünüm olarak kullanılabilir **[etkinlik türü] görüntülemek** seçeneği menüleri ve sekmelerinde, örneğin, **görünümü paralel**. Ek görünümler etkinliklerin çoğunu sahip ve farklı görünümleri farklı olabilir. Örneğin, [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) etkinliğinde maaş görünümü ve [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) etkinliğinde bir olay görünümü. Çoğu Windows Workflow Foundation ile gelen etkinliklerinin **görünümü iptal işleyicisi** ve **görünümü hataları** Tasarım görünümüne görünümleri [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) ve [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) ilişkili.  
  
 Aşağıdaki tabloda, ad ve açıklama her görünümün listeler.  
  
|Menü/sekmesi seçeneği|Açıklama|  
|----------------------|-----------------|  
|**Görünüm [etkinlik türü]**|Seçili etkinlik varsayılan grafik gösterimi görüntülemek için bu menü veya sekme seçeneği belirleyin.|  
|**Görünüm iptal işleyicisi**|Bu menü veya sekmesinde görünüm için görünüm seçeneği [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) seçilen etkinlikle ilişkilendirilmiş.|  
|**Hata işleyicisini görüntüle**|Bu menü veya sekmesinde görünüm için görünüm seçeneği [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) seçilen etkinlikle ilişkilendirilmiş.|  
|**Dengeleme İşleyicisini Görüntüle**|Bu menü veya sekmesinde görünüm için görünüm seçeneği [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) seçili ile ilişkili [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Olay işleyicisini görüntüle**|Bu menü veya sekmesinde görünüm için görünüm seçeneği [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) seçili ile ilişkili [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Benzer görünümleri hakkında daha fazla bilgi için bkz: [sıralı iş akışı görünümleri (eski)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md)   
 [Sıralı İş Akışı Görünümleri (Eski)](../workflow-designer/sequential-workflow-views-legacy.md)