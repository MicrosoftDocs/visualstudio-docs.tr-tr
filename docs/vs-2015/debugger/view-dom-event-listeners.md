---
title: DOM olayı dinleyicilerini görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1e0cf0abc35c87de3c7caa3ed00e57cb07cf987
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727376"
---
# <a name="view-dom-event-listeners"></a>DOM olayı dinleyicilerini görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 **Olayları** DOM Gezgini sekmesinde bir DOM öğesiyle ilişkili olayları gösterir. Her bir üst düğüm **olayları** sekmesinde, etkin aboneler bir olayını temsil eder. Üst düğüm belirli bir olay için kayıtlı olay dinleyicileri temsil eden alt düğümleri içerir. Olay dinleyicilerini görüntülemenin yanı sıra JavaScript kodunda olay dinleyicisi konumuna gitmek için bu sekmeyi kullanabilirsiniz. Bu konu başlığı altındaki bilgiler, HTML ve JavaScript kullanarak Store uygulamaları için geçerlidir.  
  
 Listede **olayları** sekmesini dinamiktir. Uygulama çalışırken, bir olay dinleyicisi eklerseniz, yeni olay dinleyicisi Burada görünecek. Ekleme ve kaldırma olay dinleyicileri hakkında daha fazla bilgi için bkz. [olay dinleyicileri ile sorunları çözmek için ipuçları](#Tips) bu konuda.  
  
> [!NOTE]
>  DOM öğeleri gibi olmayan kod öğeleri için olay dinleyicileri `xhr`, üzerinde görünmez **olayları** sekmesi.  
  
## <a name="view-event-listeners-for-dom-elements"></a>DOM öğeleri için Görünüm olay dinleyicileri  
 Bu örnek, bir Windows Phone Store uygulaması gösterir. Burada açıklanan DOM Gezgini özellikleri Windows Store uygulamaları için de desteklenir.  
  
#### <a name="to-view-event-listeners"></a>Olay dinleyicilerini görüntülemek için  
  
1.  Visual Studio'da Windows Phone Pivot uygulaması proje şablonunu kullanan bir JavaScript uygulaması oluşturun.  
  
2.  Şablonu Visual Studio'da Aç **öykünücüsü 8.1 WVGA 4 inç 512MB** hata ayıklayıcı hata ayıklama araç çubuğundaki aşağı açılan listesinde:  
  
     ![Hata ayıklama hedef seçme](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
3.  Uygulamayı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
4.  Çalışan uygulamada Git **3. bölüm** pivot öğesi.  
  
5.  Visual Studio (Alt + sekme veya F12) geçin.  
  
6.  DOM Gezgini'nde `Find` sağ üst köşedeki.  
  
7.  `ListView`yazın ve ardından Enter tuşuna basın.  
  
8.  Gerekirse, seçin **sonraki** düğmesi bulunacak `DIV` temsil eden öğe `ListView` denetimi (Bu öğeyi bir `data-win-control` değerini `WinJS.UI.ListView`).  
  
     `DIV` Öğesi DOM Gezgini'nde artık seçilmelidir.  
  
9. Seçin **olayları** DOM Gezgini sağ tarafındaki bölmede sekme.  
  
     Artık etkin aboneler için sahip olayları görebilirsiniz `DIV` burada gösterildiği şekilde öğesi.  
  
     ![DOM Gezgini olaylar sekmesinde](../debugger/media/js-dom-events.png "JS_DOM_Events")  
  
10. Bu olayları için olay dinleyicileri bulmak için ilişkili JavaScript dosya bağlantılarını seçin.  
  
11. Olay dinleyicileri DOM hiyerarşideki üst öğeler için hızlı bir şekilde tanımlamak için bir üst öğenin DOM Gezgini alt kısmındaki hiyerarşi listeden seçim yapın.  
  
     ![DOM hiyerarşideki üst öğeleri seçme](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")  
  
     **Olayları** olay dinleyicileri hiyerarşi listesinde seçtiğiniz herhangi bir öğe için sekmesinde gösterilir.  
  
###  <a name="Tips"></a> Olay dinleyicileri ile sorunları çözmek için ipuçları  
 Bazı uygulama senaryolarında olay dinleyicileri açıkça kullanarak kaldırılmalıdır [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Kullanım **olayları** DOM Gezgini'nde kod çalıştırılırken, olay dinleyicileri DOM öğeleri kaldırılmış olup olmadığını sınamak için sekmesinde. Bu tür sorunları gidermenize yardımcı olacak bazı ipuçları şunlardır:  
  
-   Tek sayfa gezinti modelini kullanan uygulamalar için Visual Studio uygulanan [proje şablonları](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx), bir sayfanın parçası olan DOM öğeleri gibi nesneler için kayıtlı olay dinleyicileri kaldırmak genellikle gerekli değildir. Bu senaryoda, DOM öğesi ve onun ilişkili olay dinleyicileri aynı ömrü vardır ve atık olarak toplanmış olabilir.  
  
-   DOM öğesi ya da nesne ömrü ilişkili olay dinleyicisinden farklı ise, çağrılacak olabilir `removeEventListener` yöntemi. Örneğin, kullanırsanız `window.onresize` olay, olay işleme burada sayfadan ayrılmak giderseniz, olay dinleyicisi Kaldır gerekebilir.  
  
-   Varsa `removeEventListener` belirtilen dinleyiciyi kaldırmak başarısız olursa farklı bir nesne örneğinde adlı. Kullanabileceğiniz [bind yöntemi (işlev)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md) dinleyici eklediğinizde, bu sorunu çözmek için yöntemi.  
  
-   Kullanarak eklenmiş bir olay dinleyiciyi kaldırmak için [bind yöntemi (işlev)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md) veya dinleyiciyi eklediğinizde, anonim bir işlevi kullanarak işlev örneği depolar. Güvenli bir şekilde bu düzenin kullanılacağı yöntemlerinden biri aşağıda verilmiştir:  
  
    ```javascript  
    // You could use the following code within the constructor function of an object, or  
    // in the ready function of a PageControl object (Store app).  
    this.storedHandler = this._handlerFunc.bind(this);  
    elem.addEventListener('mouseup', this.storedHandler);  
  
    // In this example, add the following code in the PageControl object's unload function.  
    elem.removeEventListener('mouseup', this.storedHandler);  
  
    ```  
  
     Bağımlı işlev bir başvuru depolamak yerine aşağıdaki kodu kullanın, olay dinleyicisi açıkça kaldırmak mümkün olmayacaktır:  
  
    ```javascript  
    // Avoid this pattern. No reference to the bound function is available.  
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));  
    ```  
  
-   Olay dinleyicisi kullanarak kaldıramazsınız `removeEventListener` kullanarak eklediyseniz `obj.on<eventname>` gibi öznitelik `window.onresize = handlerFunc`.  
  
-   JavaScript bellek Çözümleyicisi kullanın [JavaScript belleği](../profiling/javascript-memory.md) uygulamanızda. Açıkça kaldırılmalıdır olay dinleyicileri bir bellek sızıntısı olarak görünebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)   
 [DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)   
 [DOM Gezgini'ni kullanarak düzen hatalarını ayıklama](../debugger/debug-layout-using-dom-explorer.md)



