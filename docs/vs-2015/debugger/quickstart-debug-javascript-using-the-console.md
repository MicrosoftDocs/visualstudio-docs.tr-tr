---
title: 'Hızlı Başlangıç: Konsolu kullanarak JavaScript hata ayıklama | Microsoft Docs'
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
- VS.WebClient.JavaScriptConsole
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript Console
- JavaScript debugging
- debugging, JavaScript
ms.assetid: ea7adb71-52b6-4a5a-9346-98ca94b06bd7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61f36594b4158c95621ec240fd7a883accd259a8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802609"
---
# <a name="quickstart-debug-javascript-using-the-console"></a>Hızlı Başlangıç: Konsolu kullanarak JavaScript hata ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 JavaScript Konsolu penceresi, etkileşim ve JavaScript kullanılarak oluşturulan Store uygulamalarında hata ayıklamak için kullanabilirsiniz. Bu özellikler için desteklenen [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları, Windows Phone Store uygulamaları ve Apache Cordova için Visual Studio Araçları kullanılarak oluşturulmuş uygulamalar. Konsolu komut başvurusu için bkz. [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md).  
  
 JavaScript Konsolu penceresi sağlar:  
  
- Nesneleri, değer ve iletileri uygulamanızdan konsol penceresine Gönder.  
  
- Görüntüleyebilir ve çalışan uygulamada yerel ve genel değişkenlerin değerlerini değiştirebilirsiniz.  
  
- Görünüm nesnesi görselleştiriciler.  
  
- Geçerli betik bağlamı içinde yürütülen bir JavaScript kodu çalıştırın.  
  
- JavaScript hataları ve belge nesne modeli (DOM) ve Windows çalışma zamanı özel durumlarının yanı sıra özel durumları görüntüleyin.  
  
- Ekranı temizleme gibi diğer görevleri gerçekleştirin. Bkz: [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md) komutların tam listesi için.  
  
  Bu konuda:  
  
- [JavaScript Konsolu penceresi kullanarak hata ayıklama](#InteractiveConsole)  
  
- [Etkileşimli hata ayıklama ve kesme modu](#InteractiveDebuggingBreakMode)  
  
- [Tek satır modu ve JavaScript Konsolu penceresi çok satırlı modu](#SinglelineMultilineMode)  
  
- [Betik yürütme bağlamını değiştirme](#Switching)  
  
> [!TIP]
>  JavaScript Konsolu penceresi kapatılırsa seçin **hata ayıklama**>**Windows** > **JavaScript Konsolu** yeniden açın. Betik hata ayıklama oturumu yalnızca sırasında penceresi görünür.  
  
 JavaScript Konsolu penceresi kullanarak, hata ayıklayıcıyı durdurup yeniden olmadan uygulamanız ile etkileşebilirsiniz. Daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md). Diğer JavaScript DOM Gezgini'ni kullanarak ve kesme noktaları, ayarlama gibi özellikler, hata ayıklama hakkında bilgi için bkz. [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) ve [uygulamaları Visual Studio'da hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InteractiveConsole"></a> JavaScript Konsolu penceresi kullanarak hata ayıklama  
 Aşağıdaki adımlar oluşturur bir `FlipView` uygulama ve etkileşimli bir şekilde kodlama hatası JavaScript hata ayıklama işlemini göstermektedir.  
  
> [!CAUTION]
>  Burada örnek uygulaması Windows Store uygulamasıdır. Bununla birlikte, burada açıklanan konsol özellikleri, Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan uygulamalar için de geçerlidir.  
  
#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>FlipView uygulamanın JavaScript kodunda hata ayıklamak için  
  
1.  Seçerek Visual Studio'da yeni bir çözüm oluşturma **dosya** > **yeni proje**.  
  
2.  Seçin **JavaScript** > **Store uygulamaları**, seçin ya da **Windows uygulamaları** veya **Windows Phone uygulamaları**, seçin **Boş uygulama**.  
  
3.  Proje için bir ad yazın `FlipViewApp`ve **Tamam** uygulamayı oluşturmak için.  
  
4.  Default.html gövde öğesi içinde mevcut HTML kodu şu kodla değiştirin:  
  
    ```html  
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
             style="display:none">  
        <div class="fixedItem" >  
            <img src="#" data-win-bind="src: flipImg" />  
        </div>  
    </div>  
    <div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{  
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
    </div>  
    ```  
  
5.  Default.css açın ve eklemek için CSS `#fView` Seçici:  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 500px;  
        margin: 25px;  
    }  
    ```  
  
6.  Default.js açın ve aşağıdaki JavaScript kodunu ile kodu değiştirin:  
  
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
  
            pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
            pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
            pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
  
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
  
7.  Hata ayıklama hedefi zaten seçili değilse, seçin **simülatör** veya Windows Phone için **öykünücüsü 8.1 WVGA 4 inç 512MB** listesinde yanındaki açılan listeden **cihaz** düğmesini **hata ayıklama** araç çubuğu:  
  
     ![Select hata ayıklama hedef liste](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8.  Hata ayıklayıcıyı başlatmak için F5 tuşuna basın.  
  
     Uygulama çalışır ancak görüntüleri eksik. JavaScript Konsolu penceresi APPHOST hataları görüntüleri eksik olduğunu gösterir.  
  
9. İle `FlipView` simülatörü veya türü Phone öykünücüsü çalışan uygulama `Data.items` giriş penceresi istemi konsolunda (yanındaki ">>" simgesi) ve Enter tuşuna basın.  
  
     Görselleştirici için `items` nesne konsol penceresinde görünür. Gösterir `items` nesne örneği ve betik bağlamda kullanılabilir. Konsol penceresinde, bir nesnenin özellik değerlerini görüntülemek (veya ok tuşlarını kullanmak için) düğümleri arasında tıklayabilirsiniz. Aşağı uygulamasına tıklarsanız `items._data` nesne, bu resimde gördüğünüz gibi görüntü başvuruları beklendiği gibi yanlış olduğunu göreceksiniz. Varsayılan görüntülerini (logo.png), nesnenin hala mevcut ve beklenen görüntülerle interspersed eksik görüntüleri vardır.  
  
     ![JavaScript Konsolu penceresi](../debugger/media/js-console-window.png "JS_Console_Window")  
  
     Ayrıca çok daha fazla öğe olduğunu unutmayın. `items._data` beklediğiniz daha nesne.  
  
10. İsteminde `Data.items.push` ve Enter tuşuna basın. Görselleştirici için konsol penceresinde gösterir `push` uygulanan işlevi, bir [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] proje dosyası. Bu uygulamada kullanıyoruz `push` doğru öğeleri eklenecek. Biraz araştırma IntelliSense kullanarak, biz size kullanması gereken, öğrenmek `setAt` varsayılan görüntüleri değiştirilecek.  
  
11. Hata ayıklama oturumunu durdurmadan etkileşimli olarak bu sorunu gidermek için default.js açıp bu koddan seçin `updateImages` işlevi:  
  
    ```javascript  
    pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
     Bu kodu kopyalayıp giriş JavaScript Konsolu komut isteminden yapıştırın.  
  
    > [!TIP]
    >  Çok satırlı kod yapıştırdığınızda JavaScript Konsolu'nu istemi giriş, giriş Konsolu komut isteminde, otomatik olarak çok satırlı moda geçer. Çok satırlı modunu açıp kapatmak için Ctrl + Alt + M tuşlarına basabilirsiniz. Çok satırlı modunda bir komut çalıştırmak için Ctrl + Enter tuşlarına basın veya pencerenin sağ alt köşesindeki ok simgesini seçin. Daha fazla bilgi için bkz. [tek satır modu ve çok satırlı modu JavaScript konsol penceresinde](#SinglelineMultilineMode).  
  
12. Düzeltme `push` işlevi çağırır isteminde değiştirerek `pages.push` ile `Data.items.setAt`. Düzeltilen kod gibi görünmelidir:  
  
    ```javascript  
    Data.items.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    Data.items.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    Data.items.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
    > [!TIP]
    >  Kullanmak istiyorsanız `pages` yerine nesne `Data.items`, tutmak için kodunuzda bir kesme noktasını ayarlamanız gerekir `pages` kapsam nesnesi.  
  
13. Betiği çalıştırmak için yeşil ok simgesini seçin.  
  
14. Tek satırlı moda giriş Konsolu komut isteminde, ve ardından Ctrl + Alt + M tuşlarına basın **Temizle giriş** (giriş isteminden kodu silmek için red "X").  
  
15. Tür `Data.items.length = 3` istemi ve Enter tuşuna basın. Bu verilerden fazlalık öğeleri kaldırır.  
  
16. Simülatör telefonda veya Phone öykünücüsünde tekrar kontrol edin ve doğru görüntüleri doğru olduğunu göreceksiniz `FlipView` sayfaları.  
  
17. DOM Gezgini'nde, güncelleştirilmiş DIV öğesinin görebilirsiniz ve beklenen IMG öğeleri bulmak için alt ağacı içinde gezinebilirsiniz.  
  
18. Seçim yaparak hata ayıklamayı durdurmak **hata ayıklama** > **hata ayıklamayı Durdur** veya göre Shift + F5 tuşuna basarak ve kaynak kodu düzeltin.  
  
     Örnek kodu içeren tam default.html sayfa düzeltildi için bkz: [hata ayıklama HTML, CSS ve JavaScript örnek kodu](../debugger/debug-html-css-and-javascript-sample-code.md).  
  
##  <a name="InteractiveDebuggingBreakMode"></a> Etkileşimli hata ayıklama ve kesme modu  
 Kesme noktaları ve JavaScript hata ayıklama araçları gibi JavaScript Konsolu penceresi kullanırken, kodda ilerleyebilmeniz kullanabilirsiniz. Hata ayıklayıcıda çalışan bir programın bir kesme noktası karşılaştığında, hata ayıklayıcı programın yürütülmesini geçici olarak askıya alır. Yürütme askıya alındığında, programınız kesme modu için çalışma modundan geçer. Yürütme herhangi bir zamanda sürdürebilirsiniz.  
  
 Bir program kesme modundayken, JavaScript Konsolu penceresi betikleri ve geçerli betik yürütme bağlamında geçerli olmayan komutları çalıştırmak için kullanabilirsiniz. Bu yordamda, sabit sürümünü kullanacağınız `FlipView` Kesme moduna kullanımını göstermek için daha önce oluşturduğunuz uygulama.  
  
#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Bir kesme noktası ayarlayın ve uygulama hatalarını ayıklamak için  
  
1.  Default.html dosyasındaki `FlipView` , daha önce oluşturulan, kısayol menüsünü açın, uygulama `updateImages()` işlevi ve ardından **kesme noktası** > **kesme noktası Ekle**.  
  
2.  Seçin **yerel makine** veya **öykünücüsü 8.1 WVGA 4 inç 512MB** yanındaki açılan liste **hata ayıklamayı Başlat** düğmesini **hata ayıklama** araç çubuğu.  
  
3.  Seçin **hata ayıklama** > **hata ayıklamayı Başlat**, veya F5 tuşuna basın.  
  
     Yürütme ulaştığında uygulama Kesme moduna girer `updateImages()` işlevi ve program yürütme geçerli satırı sarı renkle vurgulanır.  
  
     ![Kesme modu ile JavaScript Konsolu'nu kullanarak](../debugger/media/js-breakmode.png "JS_BreakMode")  
  
     Hemen geçerli hata ayıklama oturumunu sona erdirmeden program durumunu etkileyen değişkenlerin değerlerini değiştirebilirsiniz.  
  
4.  Tür `updateImages` istemine yazıp Enter tuşuna basın. Görselleştirici işlevi için konsol penceresinde görünür.  
  
5.  İşlev uygulaması göstermek için konsol penceresinde işlevi seçin.  
  
     Aşağıdaki çizimde, bu noktada konsol penceresinde gösterir.  
  
     ![JavaScript Konsolu penceresi Görselleştirici gösteren](../debugger/media/js-console-function-visualizer.png "JS_Console_Function_Visualizer")  
  
6.  Tek satırlık bir işlev, giriş sorusu çıktı penceresinden kopyalayın ve 3 dizin değeri değiştirin:  
  
    ```javascript  
    pages.setAt(3, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
7.  Kod satırının çalıştırmak için Enter tuşuna basın.  
  
     Satır satır kodda adım adım istiyorsanız F11 tuşuna basın veya program yürütme devam etmek için F5 tuşuna basın.  
  
8.  Program yürütme devam etmek için F5 tuşuna basın. `FlipView` Uygulama görünür ve artık tüm dört sayfalar varsayılan olmayan görüntülerden birini gösterir.  
  
     Visual Studio'ya geçmek için F12 ya da Alt + Tab tuşuna basın.  
  
##  <a name="SinglelineMultilineMode"></a> Tek satır modu ve JavaScript Konsolu penceresi çok satırlı modu  
 JavaScript Konsolu penceresi için giriş istemi tek satır modu hem de çok satırlı modunu destekler. Bu konuda etkileşimli hata ayıklama yordamda her iki modu kullanarak bir örnek sağlar. Modlar arasında geçiş yapmak için Ctrl + Alt + M tuşlarına basabilirsiniz.  
  
 Tek satır modu giriş geçmişi sağlar. Yukarı Ok ve aşağı ok tuşlarını kullanarak giriş geçmişinde gidebilirsiniz. Komut dosyalarını çalıştırdığınızda giriş istemi tek satır modu temizler. Tek satırlı modunda bir komut çalıştırmak için Enter tuşuna basın.  
  
 Komut dosyalarını çalıştırdığınızda, çok satırlı modunu giriş istemi temizlemez. Çok satırlı modunu tek satır modu arasında geçiş yaptığınızda tuşlarına basarak giriş satırının temizleyebilirsiniz **Temizle giriş** (kırmızı "X"). Çok satırlı modunda bir komut çalıştırmak için Ctrl + Enter tuşlarına basın veya pencerenin sağ alt köşesindeki ok simgesini seçin.  
  
##  <a name="Switching"></a> Betik yürütme bağlamını değiştirme  
 JavaScript Konsolu penceresi bir kerede web platformu ana bilgisayarı (WWAHost.exe) tek bir örneğini temsil eder, tek bir yürütme bağlamı ile etkileşim sağlar. Bazı senaryolarda, uygulamanız başka bir örnek kullandığınızda, konağının başlatılabilir bir `iframe`, bir paylaşım sözleşmesi, bir web çalışanı veya `WebView` denetimi. Ana bilgisayar başka bir örneğini çalıştırıyorsa, yürütme bağlamındaki seçerek uygulama çalıştırılırken farklı yürütme bağlamı seçebilirsiniz **hedef** listesi.  
  
 Aşağıdaki çizimde, hedef liste JavaScript konsol penceresinde gösterir.  
  
 ![Hedef seçimi JavaScript konsol penceresinde](../debugger/media/js-console-target.png "JS_Console_Target")  
  
 Yürütme bağlamı kullanarak da geçebilirsiniz `cd` komutu, ancak bir yürütme bağlamı adını bilmeniz gerekir ve kullandığınız başvuru kapsamda olmalıdır. **Hedef** listesi diğer yürütme bağlamları daha iyi erişim sağlar.  
  
##  <a name="BrowserSupport"></a> Tarayıcı ve Platform desteği  
 JavaScript Konsolu penceresi, aşağıdaki platformlarda desteklenir:  
  
-   [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] JavaScript ve HTML kullanarak Windows Phone Store uygulamaları  
  
-   Internet Explorer 11'in üzerinde çalışan [!INCLUDE[win81](../includes/win81-md.md)]  
  
-   Üzerinde çalışan Internet Explorer 10 [!INCLUDE[win8](../includes/win8-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da uygulamalarının hatalarını ayıklama](../debugger/debug-store-apps-in-visual-studio.md)   
 [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md)   
 [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Klavye kısayolları](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [HTML, CSS ve JavaScript örnek kod hatalarını ayıklama](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Hızlı Başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)   
 [Bir WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)   
 [Ürün desteği ve erişilebilirlik](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)



