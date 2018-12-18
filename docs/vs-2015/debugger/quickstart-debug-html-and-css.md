---
title: 'Hızlı Başlangıç: HTML ve CSS hatalarını ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [Windows Store apps]
- DOM Explorer [Windows Store apps]
ms.assetid: 6d156cff-36c6-425a-acf8-e1f02d4f7869
caps.latest.revision: 104
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 710bafe2383d95358ba06a287a300d9aea7baf66
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729985"
---
# <a name="quickstart-debug-html-and-css"></a>Hızlı Başlangıç: HTML ve CSS hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Visual Studio, JavaScript uygulamaları için Internet Explorer ve Visual Studio geliştiricilerinin aşina olan özellikleri içeren kapsamlı bir hata ayıklama deneyimi sağlar. Bu özellikler için desteklenen [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], Windows Phone Store uygulamaları ve Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan uygulamalar için  
  
 DOM İnceleme araçları tarafından sağlanan etkileşimli hata ayıklama modelini kullanarak görüntüleyebilir ve İşlenmiş HTML ve CSS kodunu değiştirin. Tüm hata ayıklayıcıyı durdurup yeniden olmadan bunu yapabilirsiniz.  
  
 Bu konuda:  
  
- [Dinamik DOM'u inceleniyor](#InspectingDOM)  
  
- [Öğeleri seçme](#SelectingElements)  
  
  DOM Gezgini kullanma hakkında ek bilgi için aşağıdaki konulara bakın:  
  
- [DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)  
  
- [DOM Gezgini'ni kullanarak düzen hatalarını ayıklama](../debugger/debug-layout-using-dom-explorer.md)  
  
- [DOM olayı dinleyicilerini görüntüleme](../debugger/view-dom-event-listeners.md)  
  
- [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)  
  
- [WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)  
  
  Diğer JavaScript kullanarak JavaScript Konsolu penceresi ve kesme noktaları, ayarlama gibi özellikler, hata ayıklama hakkında bilgi için bkz. [hızlı başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md) ve [uygulamaları Visual Studio'da hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InspectingDOM"></a> Dinamik DOM'u inceleniyor  
 DOM Gezgini işlenen sayfanın bir görünümü gösterir ve değerleri değiştirebilir ve sonuçları hemen görmek için DOM Gezgini'ni kullanabilirsiniz. Bu, hata ayıklayıcıyı durdurup yeniden olmadan değişiklikleri test etmek sağlar. Bu yöntemi kullanarak sayfa ile etkileşim kurduğunuzda, kaynak kodu, projenizdeki değişmez istenen kod düzeltmeleri bulduğunuzda, kaynak kodunuzda değişiklikler yaparsınız.  
  
> [!TIP]
>  Durdurup kaynak kodunuzda değişiklikler yaptığınızda hata ayıklayıcı önlemek için uygulamanızı kullanarak yenileyebilirsiniz **Yenile Windows uygulama** düğme hata ayıklama araç çubuğu (veya, F4 tuşuna basarak). Daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 DOM Gezgini kullanabilirsiniz:  
  
- DOM öğesi alt ağacı gidin ve İşlenmiş HTML, CSS ve JavaScript kodu inceleyin.  
  
- Öznitelikler ve CSS stilleri işlenen öğeler için dinamik olarak düzenleme ve sonuçları hemen görün.  
  
- CSS stilleri sayfa öğeleri için nasıl uygulanmış incelemenize ve henüz uygulanmamış kuralları izleme.  
  
  Hata ayıklama uygulamaları, genellikle DOM Gezgini'nde öğeleri seçmeniz gerekir. Bir öğe seçtiğinizde, DOM Gezgini sağ tarafındaki sekmeler otomatik olarak görünen değerlerin DOM Gezgini'nde seçilen öğenin yansıtacak şekilde güncelleştirin. Sekmeleri şunlardır: **stilleri**, **hesaplanan**, **Düzen**. Windows Store apps de destek **olayları** ve **değişiklikleri** sekmeler. Öğeleri seçme hakkında daha fazla bilgi için bkz. [öğeleri seçme](#SelectingElements).  
  
> [!TIP]
>  DOM Gezgini penceresi kapatılırsa seçin **hata ayıklama**>**Windows** > **DOM Gezgini** yeniden açın. Pencere, yalnızca bir betik hata ayıklama oturumu sırasında görünür.  
  
 Aşağıdaki yordamda, etkileşimli bir uygulama, DOM Gezgini'ni kullanarak hata ayıklama işleminde gideceğiz. Kullanan bir uygulama oluşturacağız bir `FlipView` denetlemek ve sonra hata ayıklama. Uygulama çeşitli hatalar içeriyor.  
  
> [!WARNING]
>  Aşağıdaki örnek bir Windows Store uygulaması uygulamadır. Cordova için aynı özellikleri desteklenir, ancak uygulama farklı olacaktır.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Dinamik DOM'u inceleyerek hata ayıklamak için  
  
1. Seçerek Visual Studio'da yeni bir çözüm oluşturma **dosya** > **yeni proje**.  
  
2. Seçin **JavaScript** > **Store**, seçin ya da **Windows uygulamaları** veya **Windows Phone uygulamaları**, seçin **Boş uygulama**.  
  
3. Proje için bir ad yazın `FlipViewApp`ve **Tamam** uygulamayı oluşturmak için.  
  
4. Default.html gövde öğesi içinde bu kodu ekleyin:  
  
   ```html  
   <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
            style="display:none">  
       <div class="fixedItem" >  
           <img src="#" data-win-bind="src: flipImg" />  
       </div>  
   </div>  
   <div id="fView" style="width:100px;height:100px"  
       data-win-control="WinJS.UI.FlipView" data-win-options="{  
       itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
   </div>  
   ```  
  
5. Default.css açın ve aşağıdaki CSS ekleyin:  
  
   ```css  
   #fView {  
       background-color:#0094ff;  
       height: 100%;  
       width: 100%;  
       margin: 25%;  
   }  
   ```  
  
6. Default.js dosyasında kodu şu kodla değiştirin:  
  
   ```javascript  
   (function () {  
       "use strict";  
  
       var app = WinJS.Application;  
       var activation = Windows.ApplicationModel.Activation;  
  
       var myData = [];  
       for (var x = 0; x < 4; x++) {  
           myData[x] = { flipImg: "/images/logo.png" }  
       };  
  
       var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
       app.onactivated = function (args) {  
           if (args.detail.kind === activation.ActivationKind.launch) {  
               if (args.detail.previousExecutionState !==  
               activation.ApplicationExecutionState.terminated) {  
                   // TODO: . . .  
               } else {  
                   // TODO: . . .  
               }  
               args.setPromise(WinJS.UI.processAll());  
  
               updateImages();  
           }  
       };  
  
       function updateImages() {  
  
           pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
           pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
           pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
       };  
  
       app.oncheckpoint = function (args) {  
       };  
  
       app.start();  
  
       var publicMembers = {  
           items: pages  
       };  
  
       WinJS.Namespace.define("Data", publicMembers);  
  
   })();  
   ```  
  
    Bu uygulamayı (Simülatörde benzer görünür) Phone öykünücüsü çalıştırıyoruz, görmek istediğimiz aşağıda gösterilmiştir. Ancak uygulama bu duruma getirmek için size bir dizi hataları düzelttikten gerekecektir.  
  
    ![Beklenen sonuçları gösteren FlipView uygulama](../debugger/media/js-dom-appfixed.png "JS_DOM_AppFixed")  
  
7. Seçin ya da **simülatör** veya **öykünücüsü 8.1 WVGA 4 inç 512MB** listesinde yanındaki açılan listeden **hata ayıklamayı Başlat** düğmesini **hataayıklama**araç çubuğu:  
  
    ![Select hata ayıklama hedef liste](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Seçin **hata ayıklama** > **hata ayıklamayı Başlat**, veya uygulamanızı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
    Bu uygulama simülatör telefonda veya Phone öykünücüsünde çalışır, ancak stil birkaç hataların olmadığı için çoğunlukla boş bir ekran görürsünüz. İlk `FlipView` görüntü Orta ekranın yanında küçük bir kare görünür.  
  
9. Uygulama Simulator'da çalıştırıyorsanız, seçin **değiştirme çözümleme** 1280 x 800 ekran çözünürlüğü yapılandırmak için simülatör sağındaki araç çubuğu komutuna. Bu, aşağıdaki adımlarda gösterilen değerler Simülatörde gördüğünüz eşleştiğini garanti eder.  
  
10. Seçin ve Visual Studio'ya **DOM Gezgini** sekmesi.  
  
    > [!TIP]
    >  Çalıştırılan uygulama ve Visual Studio arasında geçiş yapmak için Alt + sekme veya F12 tuşuna basabilirsiniz.  
  
11. DIV öğesi Kimliğine sahip bölüm için DOM Gezgini penceresinde seçin `"fView"`. Görüntülemek ve doğru DIV öğesinin seçmek için ok tuşlarını kullanın. (Bir öğenin alt öğelerini görüntülemek için sağ ok tuşu sağlar.)  
  
     ![DOM Gezgini](../debugger/media/js-dom-explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    >  Yazarak JavaScript konsol penceresinin sol alt köşesinde DIV öğesinin seçebilirsiniz `select(fView)` adresindeki >> giriş istemi ve sonra Enter tuşuna basın.  
  
     DOM Gezgini penceresinin sağ tarafındaki sekmeler otomatik olarak görünen değerlerin geçerli öğenin DOM Gezgini'nde yansıtacak şekilde güncelleştirin.  
  
12. Seçin **hesaplanan** sekmesinde.  
  
     Bu sekme, seçili DOM öğesinin her bir özellik için hesaplanan ya da son değeri gösterir.  
  
13. Yükseklik CSS kuralı açın. Bir satır içi stil kümesine yükseklik değeri ayarlamak için % 100 ile tutarsız görünen 100px fark `#fView` CSS Seçici. Üstü çizili metin için `#fView` Seçici satır içi stil bu stil öncelik aldığını gösterir.  
  
     Aşağıdaki çizimde gösterildiği **hesaplanan** sekmesi.  
  
     ![DOM Gezgini hesaplanan sekmesini](../debugger/media/js-dom-explorer-computed.png "JS_DOM_Explorer_Computed")  
  
14. Satır içi stil genişliği ve yüksekliği için ana DOM Gezgini penceresinde çift `fView` DIV öğesi. Şimdi burada değerleri düzenleyebilirsiniz. Bu senaryoda, tamamen kaldırmak istiyoruz.  
  
15. Seçin `width: 100px;height: 100px;`Delete tuşuna basın ve ardından Enter tuşuna basın. Enter tuşuna bastıktan sonra hata ayıklama oturumunuzu durdurdu henüz olsa da yeni değerlerini hemen simülatörü veya Phone öykünücüsü yansıtılır.  
  
    > [!IMPORTANT]
    >  DOM Gezgini penceresi özniteliklerinde güncelleştirebilirsiniz gibi görünen değerleri de güncelleştirebilirsiniz **stilleri**, **hesaplanan**, ve **Düzen** sekmeler. Daha fazla bilgi için bkz. [DOM Gezgini'ni kullanarak hata ayıklama CSS stillerinde](../debugger/debug-css-styles-using-dom-explorer.md) ve [DOM Gezgini'ni kullanarak hata ayıklama Düzen](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Simülatör veya Phone öykünücüsü'nü seçerek ya da Alt + Tab tuşlarını kullanarak uygulamaya geçin.  
  
     Artık `FlipView` denetimi görünür simülatör telefonda veya Phone öykünücüsünde'nın ekran boyutundan büyük. Bu, istenen sonucu değildir. Araştırmak için Visual Studio'ya geçiş yapın.  
  
17. DOM Gezgini'nde seçin **hesaplanan** yeniden sekme ve yüksekliği kuralı açın. FView öğe hala CSS'den beklendiği gibi % 100 değerini gösterir, ancak bu uygulama için istediğimiz değil olan simülatör ekran yüksekliği (örneğin, 800 piksel veya 667.67px) için hesaplanan değeri eşittir. Araştırmak için yükseklik ve genişlik kaldırabilirsiniz `fView` DIV öğesi.  
  
18. İçinde **stilleri** sekmesinde, yükseklik ve genişlik özelliklerini işaretini kaldırın `#fView` CSS Seçici.  
  
     **Hesaplanan** sekmesi artık 400 piksel ölçülerinden küçük yüksekliğini gösterir. Bu değer, UI-platform CSS dosyası olan dark.css içinde belirtilen .win flipview Seçici'den gelen bilgileri gösterir.  
  
19. Uygulamaya geri geçiş yapın.  
  
     Şeyler iyileştirdik. Ancak, yine de düzeltmek için bir daha fazla sorun olduğunu: kenar boşluklarını çok büyük görünür.  
  
20. Araştırmak için Visual Studio'ya ve seçin **Düzen** öğenin kutu modelinin aramak için sekmesinde.  
  
     İçinde **Düzen** sekmesinde, aşağıdaki değerleri görürsünüz:  
  
    - Simülatör için: 320px (kaydırma) ve 320px (kenar boşluğu).  
  
    - Phone öykünücüsü: 100px (kaydırma) ve 100px (kenar boşluğu).  
  
      Aşağıdaki çizimde gösterildiği nasıl **Düzen** sekmesi, Phone öykünücüsü (100px uzaklığı ve kenar boşluğu) kullanıyorsanız, arar.  
  
      ![DOM Gezgini Düzen sekmesini](../debugger/media/js-dom-explorer-layout.png "JS_DOM_Explorer_Layout")  
  
      Doğru görünüyor. **Hesaplanan** sekmesi de aynı kenar boşluğu değerleri gösterir.  
  
21. Seçin **stilleri** bulun ve sekme `#fView` CSS Seçici. % 25'için bir değer, burada gördüğünüz **kenar boşluğu** özelliği.  
  
22. % 25'i seçin ve için 25px değiştirin ve Enter tuşuna basın.  
  
23. Ayrıca **stilleri** sekmesinde .win flipview Seçici için height kuralı seçin ve 400 piksel ölçülerinden küçük 500px için değiştirin ve Enter tuşuna basın.  
  
24. Uygulamaya geri geçiş yapmak ve öğelerin yerleşimini doğru görüntülendiğini görürsünüz. Düzeltmeleri kaynağına ve hata ayıklayıcıyı durdurup yeniden olmadan uygulamayı yenilemek için aşağıdaki yordama bakın.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Uygulamanızı hata ayıklama sırasında yenilemek için  
  
1.  Uygulamayı hala devam ederken, Visual Studio'ya geçiş yapın.  
  
2.  Default.HTML açın ve yüksekliğini ve genişliğini değiştirerek kaynak kodunuzu değiştirmeniz `"fView"` % 100 DIV öğesi.  
  
3.  Seçin **Yenile Windows uygulama** hata ayıklama araç çubuğundan düğme (veya F4 tuşuna basın). Düğme şöyle görünür: ![Yenile Windows uygulama düğmesine](../debugger/media/js-refresh.png "JS_Refresh").  
  
     Uygulama sayfaları yeniden ve ön plana simülatörü veya Phone öykünücüsünde döndürür.  
  
     Yenileme özelliği hakkında daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
##  <a name="SelectingElements"></a> Öğeleri seçme  
 Bir uygulamanın hataları ayıklanırken üç yolla DOM öğeleri seçebilirsiniz:  
  
- Öğelerini doğrudan DOM Gezgini penceresinde (veya ok tuşlarını kullanarak) tıklayarak.  
  
- Kullanarak **öğe seçin** düğmesine (Ctrl + B).  
  
- Kullanarak `select` biri olan komut, [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md).  
  
  Öğeleri seçin ve bir öğe üzerinde fare işaretçisini DOM Gezgini penceresi kullandığınızda, karşılık gelen öğe çalışan uygulamada vurgulanır. Öğesindeki DOM Gezgini'nde seçmek için tıklatın veya vurgulayın ve öğeleri seçmek için ok tuşlarını kullanabilirsiniz. Kullanarak öğeleri DOM Gezgini'nde de seçebilirsiniz **Select öğesi** düğmesi. Aşağıdaki çizimde gösterildiği **öğe seçin** düğmesi.  
  
  ![DOM Gezgini'nde öğe düğmesini seçme](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
  Tıkladığınızda **Select öğesi** (veya Ctrl + B tuşlarına basın) çalışan uygulamada tıklayarak DOM Gezgini'nde öğeyi seçebilir böylece bu seçim modu değişir. Modu tek tıklatmadan sonra geri normal seçim moduyla değiştirir. Tıkladığınızda **Select öğesi**, uygulama ön plana gelir ve imleci değişikliklerini yeni seçim modunu gösterecek. Anahatları belirlenmiş öğe'e tıkladığınızda DOM Gezgini ön plana seçili belirtilen öğeyi döndürür.  
  
  Seçtiğiniz önce **öğe seçin**, çalışmakta olan uygulamayla öğelerinde getirerek vurgulamak belirtebilirsiniz **web sayfasında öne çıkan özellikleri görüntülemek** düğmesi. Aşağıdaki çizim, bu düğmeyi gösterir. Öne çıkan özellikleri varsayılan olarak görüntülenir.  
  
  ![Web Sayfa Görüntüle düğmesini vurgular](../debugger/media/js-dom-display-highlights-button.png "JS_DOM_Display_Highlights_Button")  
  
  Öğeleri vurgulama seçtiğinizde, Simülatörde üzerine öğeler vurgulanmıştır. Görünür kutu modeli vurgulanan öğelerle eşleme için renk **Düzen** DOM Gezgini sekmesi.  
  
> [!NOTE]
>  Üzerine gelerek öğeleri vurgulama, Windows Phone öykünücüsü'nde kısmen desteklenir.  
  
 Kullanarak öğeleri seçmek nasıl gösteren bir örnek için **Select öğesi** düğmesi, bkz: [DOM Gezgini'ni kullanarak hata ayıklama CSS stillerinde](../debugger/debug-css-styles-using-dom-explorer.md).  
  
##  <a name="BrowserSupport"></a> Tarayıcı ve Platform desteği  
 JavaScript ve DOM Gezgini JavaScript Konsolu penceresi için Visual Studio Araçları, aşağıdaki platformlarda desteklenir:  
  
- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] JavaScript ve HTML kullanarak Windows Phone Store uygulamaları  
  
- Internet Explorer 11'in üzerinde çalışan [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Üzerinde çalışan Internet Explorer 10 [!INCLUDE[win8](../includes/win8-md.md)]  
  
  Git [burada](http://go.microsoft.com/fwlink/?LinkID=232448) indirmek için [!INCLUDE[win8](../includes/win8-md.md)] ve Visual Studio.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da uygulamalarının hatalarını ayıklama](../debugger/debug-store-apps-in-visual-studio.md)   
 [DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)   
 [DOM Gezgini'ni kullanarak Düzen hatalarını ayıklama](../debugger/debug-layout-using-dom-explorer.md)   
 [DOM olayı dinleyicilerini görüntüleme](../debugger/view-dom-event-listeners.md)   
 [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Bir WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)   
 [Klavye kısayolları](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md)   
 [HTML, CSS ve JavaScript örnek kod hatalarını ayıklama](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Ürün desteği ve erişilebilirlik](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)



