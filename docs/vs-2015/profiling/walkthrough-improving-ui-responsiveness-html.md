---
title: 'İzlenecek yol: Kullanıcı Arabirimi yanıt hızı (HTML) geliştirme | Microsoft Docs'
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
- performance tools, JavaScript [Store apps]
- performance, JavaScript [Store apps]
- performance, HTML [Store apps]
- performance tools, HTML [Store apps]
ms.assetid: 7e5a2524-dbf5-4a40-b5d6-2d1ed7fff3de
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cf1b080a0e803beda6682265dc383dc43a33d0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791156"
---
# <a name="walkthrough-improving-ui-responsiveness-html"></a>İzlenecek yol: Kullanıcı Arabirimi yanıt hızı (HTML) geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, tanımlamak ve kullanarak bir performans sorunu düzeltme sürecinde müşteri adayları [HTML kullanıcı Arabirimi yanıtlama hızı Profil Oluşturucusu](../profiling/html-ui-responsiveness.md). Profil Oluşturucu, JavaScript kullanarak Visual Studio için Windows evrensel ve Windows Store uygulamalarında kullanılabilir. Bu senaryoda, DOM öğeleri çok sık güncelleştiren bir performans testi uygulaması oluşturma ve tanımlamak ve bu sorunu çözmek için Profiler'ı kullanın.  
  
### <a name="creating-and-running-the-performance-test-app"></a>Uygulama oluşturma ve çalıştırma performans testi  
  
1.  Visual Studio'da yeni bir Windows Evrensel JavaScript projesi oluşturun. (Seçmek **dosya / yeni / Project**. Seçin **JavaScript** sol bölmede ve ardından **Windows**, **Windows 10**, ardından da **Evrensel**, veya  **Windows Phone**.  
  
2.  > [!IMPORTANT]
    >  Bu konu başlığında gösterilen Tanılama sonuçları için bir Windows 8 uygulaması gösterilmektedir.  
  
3.  Orta bölmede gibi boş proje şablonlarından birini seçin **boş uygulama**.  
  
4.  İçinde **adı** gibi bir ad belirtin, kutusunda `JS_Perf_Tester`ve ardından **Tamam**.  
  
5.  İçinde **Çözüm Gezgini**default.html açın ve arasına aşağıdaki kodu yapıştırın \<gövdesi > etiketleri:  
  
    ```html  
    <div class="wrapper">  
        <button id="content">Waiting for values</button>  
    </div>  
    ```  
  
6.  Default.css açın ve aşağıdaki CSS kodunu ekleyin:  
  
    ```css  
    #content {  
        margin-left: 100px;  
        margin-top: 100px;  
    }  
    ```  
  
7.  Default.js açın ve tüm kodu şu kodla değiştirin:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var content;  
        var wrapper;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
  
                    content = document.getElementById("content");  
                    wrapper = document.querySelector(".wrapper");  
  
                    content.addEventListener("click", handler);  
  
                } else {  
                }  
  
                args.setPromise(WinJS.UI.processAll());  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var idx = 0;  
        var count = 0;  
        var max = 5000;  
        var text = ["what", "is", "the", "Matrix?"];  
        var color = ["red", "crimson", "maroon", "purple"];  
  
        function increment() {  
  
            setTimeout(function () {  
  
                idx++;  
                count++;  
  
                if (idx > 3) { idx = 0; }  
                if (count < max) { increment(); }  
  
            }, 1000);  
        }  
  
        function setValues() {  
  
            content = document.getElementById("content");  
            content.removeNode(true);  
  
            var newNode = document.createElement("button");  
            newNode.id = "content";  
            newNode.textContent = text[idx];  
            //newNode.textContent = getData();  
            newNode.style.backgroundColor = color[idx];  
            //newNode.style.animationName = "move";  
            //count++;  
  
            wrapper.appendChild(newNode);  
  
        }  
  
        function update() {  
  
            setTimeout(function () {  
  
                setValues();  
                if (count < max) { update(); }  
            });  
        }  
  
        function handler(args) {  
  
            content.textContent = "eenie";  
            increment();  
            update();  
        }  
  
    })();  
  
    ```  
  
8.  Hata ayıklamayı başlatmak için F5 tuşuna basın. Doğrulayın **değerleri için bekleyen** düğmesi sayfada görüntülenir.  
  
9. Seçin **değerleri için bekleyen** ve düğme metni ve renk yaklaşık saniyede bir kez güncelleştirmesini doğrulayın. Bu tasarım gereğidir.  
  
10. Visual Studio'ya dönün (Alt + Sekme) geçin ve sonra hata ayıklamayı durdurmak için Shift + F5'i seçin.  
  
     Uygulamanın çalıştığını doğruladıktan sonra profil oluşturucuyu kullanarak performansı inceleyebilirsiniz.  
  
### <a name="analyzing-performance-data"></a>Performans verilerini çözümleme  
  
1. Üzerinde **hata ayıklama** araç penceresindeki **hata ayıklamayı Başlat** listesinde, Windows Phone Öykünücüleri birini seçin veya **simülatör**.  
  
2. Üzerinde **hata ayıklama** menüsünde seçin **performans ve tanılama**.  
  
3. İçinde **kullanılabilir Araçları**, seçin **HTML UI yanıtlama hızı**ve ardından **Başlat**.  
  
    Bu öğreticide, profil oluşturucu için başlangıç projesi iliştirmekte. Yüklü bir uygulama için profil oluşturucu ekleme gibi diğer seçenekleri hakkında daha fazla bilgi için bkz. [HTML UI yanıtlama hızı](../profiling/html-ui-responsiveness.md).  
  
    Profil Oluşturucu başlattığınızda, Vsetwcollector.exe'yi çalıştırmak için izninizi isteyen bir kullanıcı hesabı denetimi görebilirsiniz. Seçin **Evet**.  
  
4. Çalışan uygulamada seçin **değerleri için bekleyen** ve yaklaşık 10 saniye bekleyin. Düğme metni ve renk yaklaşık saniyede bir kez güncelleştirmesini doğrulayın.  
  
5. Çalışan uygulamayı, Visual Studio (Alt + Sekme) geçin.  
  
6. Seçin **koleksiyonu Durdur**.  
  
    Profil Oluşturucu, Visual Studio'da yeni bir sekmede bilgileri görüntüler. CPU kullanımı ve görsel üretilen iş (FPS) veri bakın, bazı eğilimleri kolayca belirleyebilirsiniz:  
  
   - CPU kullanımı artırır önemli ölçüde yaklaşık 3 saniye sonra (ne zaman bastığınız **değerleri için bekleyen** düğme) ve bu noktadan itibaren olaylar (betik, stil ve işleme olayları tutarlı karışık) Temizle desenini gösterir.  
  
   - Görsel üretilen iş değil etkilenen ve adresindeki 60 FPS kalır (diğer bir deyişle, bırakılan çerçeve yok).  
  
     CPU kullanım grafiği, yüksek etkinlik bu dönemde uygulamanın ne yaptığını bulmak için tipik bir bölümünü bakalım.  
  
7. CPU kullanım grafiği ortasında bir iki ikinci bölümü seçin (ya da'a tıklayın ve Sürükle veya sekme ve ok tuşlarını kullanın). Aşağıdaki çizimde, bir seçim yaptıktan sonra CPU kullanım grafiği gösterir. Paylaşılmayan seçimi alandır.  
  
    ![CPU kullanım grafiği](../profiling/media/js-htmlviz-app-cpu.png "JS_HTMLViz_App_CPU")  
  
8. Seçin **yakınlaştırmak**.  
  
    Seçilen süre içinde daha fazla ayrıntı göstermek için grafiğin değişiklikler. Aşağıdaki çizim, yakınlaştırma sonra CPU kullanım grafiği gösterir. (Belirli verileri farklılık gösterebilir, ancak genel düzen görünür olacaktır.)  
  
    ![Görünüm uzaklaştırılacağını](../profiling/media/js-htmlviz-app-zoom.png "JS_HTMLViz_App_Zoom")  
  
    Zaman Çizelgesi ayrıntılarını alt bölmede, seçilen süre için ayrıntıları örneği gösterilmektedir.  
  
    ![Zaman Çizelgesi ayrıntıları](../profiling/media/js-htmlviz-app-details.png "JS_HTMLViz_App_Details")  
  
    CPU kullanım grafiği görünür eğilimler olayları zaman çizelgesi ayrıntıları onaylayın: çok kısa süreler boyunca gerçekleşen olayların vardır. Zaman Çizelgesi Ayrıntıları görünümü, bu olayların olduğunu gösterir. `Timer`, `Layout`, ve `Paint` olayları.  
  
9. Bağlam menüsünü kullanın (veya sağ tıklayın) birini `Timer` alt bölmede, olayları ve **olaya filtre**. Aşağıda ayrıntıları örneği biri için gösterilmektedir `Timer` uygulamasını test etme olayları.  
  
     ![Süreölçer olayı](../profiling/media/js-htmlviz-app-timer.png "JS_HTMLViz_App_Timer")  
  
     Veriler bilgiler çeşitli öğrendiğiniz kayıtlar. Örneğin:  
  
    -   Her `Timer` olay, bir komut dosyası olay olarak tanımlamak için renk kodlu bir çağrı içerir `document.createElement`stil hesaplama ve çağrı çizgidir `style.backgroundColor` ve `appendChild()`.  
  
    -   Seçili kısa süre içinde (yaklaşık iki saniye), çok sayıda vardır `Timer`, `Layout`, ve `Paint` gerçekleşen olayları. `Timer` Olaylar meydana uygulamayı çalıştırıp seçin sonra görünüşte açıktır saniye başına tek bir güncelleştirme çok daha sık **değerleri için bekleyen** düğmesi.  
  
10. Araştırmak için anonim işlev bağlantısını için aşağıdakilerden birini seçin. `Timer` alt sol bölmesinde olayları. Aşağıdaki işlev içinde default.js açar:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        });  
    }  
    ```  
  
     Bu özyinelemeli işlev çağıran bir döngü ayarlar `setValues()` düğmeyi kullanıcı arabiriminde güncelleştiren işlevi. Profil oluşturucuyu farklı Zamanlayıcı olayları inceleyerek, en olduğunu fark veya Zamanlayıcı olayların tümünü neden bu koddan, büyük olasılıkla sorun burada kaynaklanan görünecek şekilde, çok sık çalışıyor.  
  
### <a name="fixing-the-performance-issue"></a>Performans sorunu düzeltme  
  
1.  Değiştirin `update()` işlevi aşağıdaki kod ile:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        }, 1000 );  
    }  
    ```  
  
     Kodun düzeltilmiş bu sürümü, varsayılan gecikme değerini kullanımını kaynaklanan kod, önceki sürümünden atlandı 1000 milisaniyeden kısa gecikme içerir. Profil Oluşturucu verileri, varsayılan değer sıfır milisaniye neden olduğunu görünür `setValues()` işlevi çok sık çalıştırmak.  
  
2.  HTML kullanıcı Arabirimi yanıtlama hızı profil oluşturucuyu yeniden çalıştırın ve CPU kullanım grafiği denetleyin. Aşırı olayları kalkar ve CPU kullanımı, sıfıra yakın için bıraktı bulabilirsiniz. Düzeltildi!  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)



