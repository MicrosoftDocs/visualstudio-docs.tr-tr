---
title: Spy ++ araç çubuğu | Microsoft Docs
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
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05dc7dd74af20c76a3b673d5960cd88331ad7d51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763336"
---
# <a name="spy-toolbar"></a>Spy++ Araç Çubuğu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spy ++'ta menü çubuğunun altında araç çubuğu görünür. Görüntülemek veya araç çubuğunda gizlemek için **görünümü** menüsünü tıklatın **araç**.  
  
 Aşağıdaki denetimler araç çubuğunda kullanılabilir.  
  
## <a name="uielement-list"></a>UIElement Listesi  
  
|Düğme|Efekt|  
|------------|------------|  
|![Spy&#43; &#43; Windows düğme](../debugger/media/icon-spy-windows.gif "Icon_Spy ++ _Windows")|Bir ağaç görünümü denetimleri ve windows sisteminde görüntüler. Daha fazla bilgi için [Windows görünümü](../debugger/windows-view.md).|  
|![Spy&#43; &#43; işler düğmesi](../debugger/media/icon-spy-processes.gif "Icon_Spy ++ _Processes")|Sistemde işlemleri ağaç görünümünü gösterir. Daha fazla bilgi için [işlemler görünümü](../debugger/processes-view.md).|  
|![Spy&#43; &#43; iş parçacıkları düğmesi](../debugger/media/icon-spy-threads.gif "Icon_Spy ++ _Threads")|Sistemde iş parçacıklarının ağaç görünümünü gösterir. Daha fazla bilgi için [iş parçacıkları görünümü](../debugger/threads-view.md).|  
|![Spy&#43; &#43; iletileri düğmesi](../debugger/media/icon-spy-messages.gif "Icon_Spy ++ içi _iletiler")|Pencere iletilerini görüntülemek için bir pencere oluşturur ve açar **ileti seçenekleri** iletişim kutusunu pencere iletileri görüntülenecek ve diğer seçenekleri de seçmeniz seçebilirsiniz. Daha fazla bilgi için [iletiler görünümünü](../debugger/messages-view.md).|  
|![Spy&#43; &#43; Başlat düğmesi günlük](../debugger/media/icon-spy-startlog.gif "Icon_Spy ++ _StartLog")|İleti günlüğe kaydetmeyi başlatır ve ileti akışı görüntüler. Bu denetim yalnızca olduğu bir **iletileri** etkin pencereyi bir penceredir. Daha fazla bilgi için [nasıl yapılır: ileti günlüğü görüntülemeyi başlatıp](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; Durdur günlüğü düğmesi](../debugger/media/icon-spy-stoplog.gif "Icon_Spy ++ _StopLog")|Günlüğe kaydetme ve ileti akışı görüntülenmesini durdurur iletisi gönderir. Bu denetim yalnızca olduğu bir **iletileri** etkin pencereyi bir penceredir. Daha fazla bilgi için [nasıl yapılır: ileti günlüğü görüntülemeyi başlatıp](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; oturum Seçenekler düğmesi](../debugger/media/icon-spy-logoptions.gif "Icon_Spy ++ _LogOptions")|Görüntüler [ileti seçenekleri](../debugger/message-options-dialog-box.md) iletişim kutusu. Windows seçin ve türleri görüntüleme için ileti bu iletişim kutusunu kullanın. Bu denetim yalnızca olduğu bir **iletileri** etkin pencereyi bir penceredir.|  
|![Spy&#43; &#43; Temizle günlüğü düğmesi](../debugger/media/spy-clearlog.gif "Spy ++ _ClearLog")|Etkin içeriğini temizler **iletileri** penceresi. Bu denetim yalnızca olduğu bir **iletileri** etkin pencereyi bir penceredir.|  
|![Spy&#43; &#43; Bul penceresi düğmesine](../debugger/media/icon-spy-findwindow.gif "Icon_Spy ++ _FindWindow")|Açılır [Bul penceresi](../debugger/find-window-dialog-box.md) iletişim kutusunda, pencere arama ölçütü ayarlayın ve özellikleri ve iletileri görüntülemek olanak sağlar. Daha fazla bilgi için [nasıl yapılır: Bulucu Aracı kullanma](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43; &#43; Bul penceresi düğmesine ilk](../debugger/media/icon-spy-window.gif "Icon_Spy ++ _Window")|Geçerli görünümde eşleşen pencere, işlem, iş parçacığı veya iletinin arar.|  
|![Spy&#43; &#43; Bul penceresi İleri düğmesine](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy ++ _NextWindow")|Geçerli görünümde eşleşen bir sonraki pencereye, işlem, iş parçacığı veya iletinin arar. Yalnızca benzersiz olmayan geçerli arama sonucu olduğunda bu denetimi (ve ilgili menü komutunu) kullanılabilir. Örneğin, bir pencere tutucu penceresi ağacında arama ölçütü olarak kullandığınızda, bu işleyici pencere ağacında yalnızca bir pencere olmadığından benzersiz sonuçları ürettiği; Bu örnekte, **Sonrakini Bul** kullanılabilir değil.|  
|![Spy&#43; &#43; Bul önceki pencereyi düğmesi](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy ++ _PrevWindow")|Geçerli görünümde eşleşen bir önceki pencereye, işlem, iş parçacığı veya iletinin arar. Yalnızca benzersiz olmayan geçerli arama sonucu olduğunda bu denetimi (ve ilgili menü komutunu) kullanılabilir. Örneğin, bir pencere tutucu penceresi ağacında arama ölçütü olarak kullandığınızda, bu işleyici pencere ağacında yalnızca bir pencere olmadığından benzersiz sonuçları ürettiği; Bu örnekte, **Öncekini Bul** kullanılabilir değil.|  
|![Spy&#43; &#43; özellik Gezgini penceresi](../debugger/media/icon-spy-propexp.gif "Icon_Spy ++ _PropExp")|Windows görünümünde seçilen penceresi özelliklerini görüntüler.|  
|![Spy&#43; &#43; yenile düğmesi](../debugger/media/icon-spy-refresh.gif "Icon_Spy ++ _Refresh")|Sistem görünümleri yeniler.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Spy ++ kullanma](../debugger/using-spy-increment.md)   
 [Spy ++ görünümleri](../debugger/spy-increment-views.md)   
 [Spy++ Başvurusu](../debugger/spy-increment-reference.md)



