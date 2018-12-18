---
title: İletiler görünümünü | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31baccc88b25979dfc92fed6217bec3b0ef16a55
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477085"
---
# <a name="messages-view"></a>İletiler Görünümü
Her penceresinde bir ilişkili ileti akışı vardır. Bu ileti akışı iletilerin görüntüleme penceresi görüntüler. Bir pencere tanıtıcının, ileti kodu ve iletinizi gösterilir. Bir iş parçacığı veya işlem de iletiler görünümünü oluşturabilirsiniz. Bu, bir özel işlem veya pencere Başlatma iletilerinin yakalamak için özellikle yararlıdır iş parçacığı tarafından sahip olunan tüm windows gönderilen iletileri görüntülemenize olanak sağlar.  
  
 Tipik bir iletilerin görüntüleme penceresi, aşağıda yer almaktadır. Bir pencere tanıtıcının ilk sütun içerir ve ikinci sütunda ileti kodu içeren unutmayın (açıklandığı [iletisi kodlarını](../debugger/message-codes.md)). Kodu çözülmüş ileti parametreler ve dönüş değerleri sağda olduğu.  
  
 ![Spy&#43; &#43; iletiler görünümünü](../debugger/media/spy--_messagesview.png "Spy ++ _MessagesView")  
Spy ++ iletiler görünümü  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>İletiler Görünümü penceresi, işlem veya iş parçacığı açmak için  
  
1.  Odağı taşımak bir [Windows görünümü](../debugger/windows-view.md), [işlemler görünümü](../debugger/processes-view.md), veya [iş parçacıkları görünümü](../debugger/threads-view.md) penceresi.  
  
2.  İletileri incelemek istediğiniz öğe için düğümü bulun ve seçin.  
  
3.  Gelen **Spy** menüsünde seçin **günlük iletilerini**.  
  
     [İleti seçenekleri iletişim kutusu](../debugger/message-options-dialog-box.md) açar.  
  
4.  Görüntülemek istediğiniz ileti seçeneklerini seçin.  
  
5.  Tuşuna **Tamam** günlük iletilerini başlamak için.  
  
     Bir iletilerin görüntüleme penceresi açar ve bir **iletileri** menü Spy ++ araç çubuğuna eklenir. Seçilen seçeneklere bağlı olarak, iletileri etkin iletileri görünüm penceresine akış başlayın.  
  
6.  Yeterli iletileri varsa, seçin **Günlüğü Durdur** gelen **iletileri** menüsü.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İletiler görünümünü denetleme](../debugger/how-to-control-messages-view.md)  
 İletiler görünümü yönetmek açıklanmaktadır.  
  
 [Bul penceresinden iletiler görünümünü açma](../debugger/how-to-open-messages-view-from-find-window.md)  
 İletiler görünümü pencere Bul iletişim kutusunu açmak açıklanmaktadır.  
  
 [İletiler görünümünde ileti arama](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Belirli bir ileti iletiler görünümünde bulmak açıklanmaktadır.  
  
 [Başlatma ve ileti günlüğü görüntülemeyi durdurma](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 İleti günlüğe kaydetme durdurmak ve başlatmak açıklanmaktadır.  
  
 [İleti kodları](../debugger/message-codes.md)  
 İletiler görünümü içinde listelenen iletileri kodlarını tanımlar.  
  
 [İleti özelliklerini görüntüleme](../debugger/how-to-display-message-properties.md)  
 Bir ileti hakkında daha fazla bilgi görüntülemek nasıl.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Spy++ Görünümleri](../debugger/spy-increment-views.md)  
 Windows, iletileri, işlemleri ve iş parçacıklarının Spy ++ ağaç görünümler açıklanmaktadır.  
  
 [Spy++ kullanma](../debugger/using-spy-increment.md)  
 Spy ++ araç tanıtır ve nasıl kullanılacağını açıklar.  
  
 [İleti Seçenekleri iletişim kutusu](../debugger/message-options-dialog-box.md)  
 Hangi iletileri etkin iletiler görünümünde listelenir seçmek için kullanılır.  
  
 [İleti arama iletişim kutusu](../debugger/message-search-dialog-box.md)  
 Düğüm iletiler görünümünde belirli bir ileti bulmak için kullanılır.  
  
 [İleti Özellikleri iletişim kutusu](../debugger/message-properties-dialog-box.md)  
 İleti görünümünde seçilen bir ileti özelliklerini görüntülemek için kullanılır.  
  
 [Spy++ Başvurusu](../debugger/spy-increment-reference.md)  
 Her Spy ++ menü ve iletişim kutusunu tanımlayan bölümleri içerir.