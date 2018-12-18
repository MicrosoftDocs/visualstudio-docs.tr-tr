---
title: 'İzlenecek yol: Bellek sızıntısını (JavaScript) bulma | Microsoft Docs'
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
- memory leaks, JavaScript example
ms.assetid: f595412f-776b-49a2-8433-ea0062c6904d
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2b84adac23547f42cca6113c5f5a7090f224e8c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744944"
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>İzlenecek yol: Bellek sızıntısını bulma (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Bu izlenecek yol, tanımlamak ve JavaScript bellek Çözümleyicisi'ni kullanarak bir basit bir bellek sorunu düzeltme sürecinde yol gösterir. JavaScript bellek Çözümleyicisi, JavaScript kullanarak Windows için oluşturulan Visual Studio için Windows Store uygulamalarında kullanılabilir. Bu senaryoda, hatalı oluşturulmuş aynı hızda öğelerin disposing yerine bellekte DOM öğeleri korunur bir uygulama oluşturun.  
  
 Bu uygulamada bir bellek sızıntısı nedenini özgü olsa da, burada gösterilen adımları bellek sızıntısına yol açan nesneleri yalıtmaya genellikle daha etkilidir bir iş akışı gösterilmektedir.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>JavaScript bellek Çözümleyicisi test uygulamasını çalıştırma  
  
1.  Visual Studio'da **dosya**, **yeni**, **proje**.  
  
2.  Seçin **JavaScript** sol bölmede ve ardından **Windows**, **Windows 8**, ardından da **Evrensel** veya  **Windows Phone uygulamaları**.  
  
    > [!IMPORTANT]
    >  Bu konu başlığında gösterilen bellek kullanım sonuçları, bir Windows 8 uygulaması karşı test edilmez.  
  
3.  Seçin **boş uygulama** Orta bölmede, proje şablonu.  
  
4.  İçinde **adı** gibi bir ad belirtin, kutusunda `JS_Mem_Tester`ve ardından **Tamam**.  
  
5.  İçinde **Çözüm Gezgini**default.html açın ve arasına aşağıdaki kodu yapıştırın \<gövdesi > etiketleri:  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    >  Windows 8.1 Evrensel uygulama şablonunu kullanıyorsanız, hem de HTML ve CSS kodu güncelleştirmeniz gerekiyor. Windows ve. WindowsPhone projeleri.  
  
6.  Default.css açın ve aşağıdaki CSS kodunu ekleyin:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7.  Default.js açın ve tüm kodu şu kodla değiştirin:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var wrapper;  
        var elem;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
                } else {  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                elem = document.getElementById("item");  
                wrapper = document.querySelector(".wrapper");  
                var btn = document.querySelector(".memleak");  
                btn.addEventListener("click", btnHandler);  
                run();  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        function run() {  
            initialize();  
            load();  
        }  
  
        function initialize() {  
  
            if (wrapper != null) {  
                elem.removeNode(true);  
            }  
        }  
  
        function load() {  
  
            var newDiv = document.createElement("div");  
  
            newDiv.style.zIndex = "-1";  
            newDiv.id = "item";  
  
            wrapper.appendChild(newDiv);  
        }  
  
        function btnHandler(args) {  
            run();  
        }  
  
    })();  
    ```  
  
8.  Hata ayıklamayı başlatmak için F5 tuşuna basın. Doğrulayın **bellek sızıntısı** düğmesi sayfada görüntülenir.  
  
9. Visual Studio'ya dönün (Alt + Sekme) geçin ve sonra hata ayıklamayı durdurmak için Shift + F5'i seçin.  
  
     Uygulamanın çalıştığını doğruladıktan sonra bellek kullanımı inceleyebilirsiniz.  
  
### <a name="analyzing-the-memory-usage"></a>Bellek kullanımını analiz etme  
  
1. Üzerinde **hata ayıklama** araç, **hata ayıklamayı Başlat** listesinde, güncelleştirilmiş proje için hata ayıklama hedefi seçin: Windows Phone Öykünücüleri birini veya **simülatör**.  
  
   > [!TIP]
   >  Bir Windows Store uygulaması için de seçebilirsiniz **yerel makine** veya **uzak makine** bu listede. Ancak, bir öykünücü veya benzetici kullanmanın avantajı yanındaki Visual Studio yerleştirin ve çalıştırılan uygulama ve JavaScript bellek Çözümleyicisi arasında kolayca geçiş ' dir. Daha fazla bilgi için bkz. [Visual Studio'dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md) ve [uzak bir makinede çalıştırma Windows Store apps](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2. Üzerinde **hata ayıklama** menüsünde seçin **performans Profiler...** .  
  
3. İçinde **kullanılabilir Araçları**, seçin **JavaScript belleği**ve ardından **Başlat**.  
  
    Bu öğreticide, bellek Çözümleyicisi başlangıç projesine iliştirmekte. Bellek Çözümleyicisi yüklü bir uygulama ekleme gibi diğer seçenekleri hakkında daha fazla bilgi için bkz. [JavaScript belleği](../profiling/javascript-memory.md).  
  
    Bellek Çözümleyicisi'ni başlattığınızda, Vsetwcollector.exe'yi çalıştırmak için izninizi isteyen bir kullanıcı hesabı denetimi görebilirsiniz. Seçin **Evet**.  
  
4. Seçin **bellek sızıntısı** düğmesini dört kez art arda.  
  
    Düğme, olay işleme kodunu bir bellek sızıntısı neden olabilecek default.js yoksa iş seçtiğinizde. Bu tanılama amacıyla kullanacaksınız.  
  
   > [!TIP]
   >  Bir bellek sızıntısı için test etmek istediğiniz senaryoyu yinelenen öbek için uygulama başlatma sırasında veya bir sayfa yüklenirken eklenen nesneleri gibi sizi ilgilendirmeyen bilgilerini filtrelemek kolaylaştırır.  
  
5. Çalışan uygulamayı, Visual Studio (Alt + Sekme) geçin.  
  
    JavaScript bellek Çözümleyicisi, Visual Studio'da yeni bir sekmede bilgileri görüntüler.  
  
    Bu Özet görünümü gösterir işlem bellek kullanımı zamanla bellek grafiği. Görünüm, ayrıca gibi komutlar sağlar **yığın. anlık görüntü Al**. Anlık görüntü, belirli bir zamandaki bellek kullanımı hakkında ayrıntılı bilgiler sağlar. Daha fazla bilgi için bkz. [JavaScript belleği](../profiling/javascript-memory.md).  
  
6. Seçin **yığın. anlık görüntü Al**.  
  
7. Uygulamasına geçin ve seçin **bellek sızıntısı**.  
  
8. Seçin ve Visual Studio'ya **yığın. anlık görüntü Al** yeniden.  
  
    Bu örnekte temel anlık görüntü (#1) ve anlık görüntü #2 gösterilmiştir.  
  
    ![Temel anlık görüntü ve anlık görüntü 2](../profiling/media/js-mem-app-snapshot2.png "JS_Mem_App_Snapshot2")  
  
   > [!NOTE]
   >  Windows Phone öykünücüsü, anlık görüntünün alındığı zaman uygulama görüntüsü göstermez.  
  
9. Uygulamasına geçin ve seçin **bellek sızıntısı** düğmesini tekrar.  
  
10. Seçin ve Visual Studio'ya **yığın. anlık görüntü Al** üçüncü kez.  
  
    > [!TIP]
    >  Bu iş akışında üçüncü bir anlık görüntüsünü alarak temel anlık görüntüden ikinci anlık bellek sızıntılarını ile ilişkili olmayan değişiklikleri filtre uygulayabilirsiniz. Örneğin, üstbilgiler ve altbilgiler bazı değişiklikler, bellek kullanımı oluşturur, ancak bellek sızıntılarını ilişkisiz bir sayfasında güncelleştirme gibi beklenen değişiklikler olabilir.  
  
     Bu örnekte, anlık görüntü #2 ve anlık görüntü #3 gösterilmiştir.  
  
     ![Anlık görüntü 2 ve 3 anlık görüntü](../profiling/media/js-mem-app-snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. Visual Studio'da **Durdur** profil oluşturmayı durdurmak için.  
  
12. Visual Studio'da anlık görüntüleri karşılaştırın. Anlık görüntü #2 aşağıda gösterilmiştir:  
  
    - (Kırmızı yukarı ok sol tarafından gösterilen) yığın boyutu birkaç KB anlık görüntü # 1'e kıyasla arttı.  
  
      > [!IMPORTANT]
      >  Tam bellek kullanım değerlerini yığın boyutu için hata ayıklama hedefi üzerinde bağlıdır.  
  
    - (Yukarı ok sağda kırmızı tarafından gösterilen) yığındaki nesnelerin sayısı, anlık görüntü #1 kıyasla arttı. Bir nesne (+ 1) eklendi ve hiçbir nesne kaldırıldı (-0).  
  
      Anlık görüntü #3 aşağıda gösterilmiştir:  
  
    - Yığın boyutu, anlık görüntü # 2'ye kıyasla birkaç yüz bayt olarak yeniden arttı.  
  
    - Yığındaki nesnelerin sayısı, tekrar anlık görüntü # 2'ye kıyasla arttı. Bir nesne (+ 1) eklendi ve hiçbir nesne kaldırıldı (-0).  
  
13. Anlık görüntü # 3'te, bağlantı metnini sağdaki + 1 değerini gösteren seçin / - 0 yanında kırmızı yukarı ok.  
  
     ![Farklı bir yığın nesnelerin görünümünü bağlantı](../profiling/media/js-mem-app-link.png "JS_Mem_App_Link")  
  
     Bu adlı yığındaki nesnelerin fark görünümünü açar **anlık görüntü #3 - anlık görüntü #2**, varsayılan olarak gösteren türler görünümü. Varsayılan olarak, anlık görüntü #2 ve 3 anlık görüntü arasındaki yığına eklenen nesnelerin bir listesini görürsünüz.  
  
14. İçinde **kapsam** seçin, filtre **kalan nesneler anlık görüntü # 2'den**.  
  
15. Üst nesne ağacının HTMLDivElement nesne, burada gösterildiği gibi açın.  
  
     ![Fark görünümü nesne sayısı yığında](../profiling/media/js-mem-app-typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Bu görünüm aşağıdaki gibi bir bellek sızıntısı hakkında yararlı bilgiler gösterir:  
  
    - Bu görünüm Kimliğine sahip bir DIV öğesine gösterir `item`, ve nesnesinin tutulan boyut birkaç yüz bayt (tam değeri değişir).  
  
    - Bu nesne anlık görüntü # 2 arta kalan bir nesne ve olası bellek sızıntısı temsil eder.  
  
      Uygulamayı biraz bilgi bu noktada yardımcı olur: seçme **bellek sızıntısı** düğmesi bir DIV öğesine kaldırmak ve kod sağ çalışıyor gibi görünüyor bir öğe ekleyin (diğer bir deyişle, bellek sızıntıları). Sonraki bölümde bunu düzeltelim açıklanmaktadır.  
  
    > [!TIP]
    >  Bazı durumlarda, bir nesne olarak bulma `Global` nesne, nesneyi tanımlamak yardımcı olabilir. Bunu yapmak için tanımlayıcısı için kısayol menüsünü açın ve ardından **kök görünümünde göster**.  
  
##  <a name="FixingMemory"></a> Bellek sorunu düzeltme  
  
1. Profil Oluşturucu tarafından ortaya verileri kullanarak "Item" Kimliğine sahip DOM öğeleri kaldırmak için sorumlu kodu inceleyin. İçinde oluşan `initialize()` işlevi.  
  
   ```javascript  
   function initialize() {  
  
       if (wrapper != null) {  
           elem.removeNode(true);  
       }  
   }  
   ```  
  
    `elem.removeNode(true)` belki de düzgün çalışmıyor. Kod DOM öğesi nasıl önbelleğe alma inceleyin ve bir sorun bulunamadı; önbelleğe alınan öğeye başvuru güncelleştirilmiyor.  
  
2. İçinde default.js, yük işlevi çağırmadan önce yalnızca aşağıdaki kod satırını ekleyin `appendChild`:  
  
   ```javascript  
   elem = newDiv;  
   ```  
  
    Öğe seçtiğinizde doğru kaldırılır, böylece bu kod önbelleğe alınan öğeye başvuru güncelleştirmeleri **bellek sızıntısı** düğmesi. Tüm kod yükleme işlevi için artık şöyle görünür:  
  
   ```javascript  
   function load() {  
  
       wrapper = document.querySelector(".wrapper");  
  
       var newDiv = document.createElement("div");  
  
       newDiv.style.zIndex = "-1";  
       newDiv.id = "item";  
       elem = newDiv;  
  
       wrapper.appendChild(newDiv);  
   }  
   ```  
  
3. Üzerinde **hata ayıklama** menüsünde seçin **performans ve tanılama**.  
  
4. İçinde **kullanılabilir Araçları**, seçin **JavaScript belleği**ve ardından **Başlat**.  
  
5. Üç anlık görüntülerini almak için önce yordamın aynısını izleyin. Adımlar burada özetlenmektedir:  
  
   1. Uygulamada, seçin **bellek sızıntısı** düğmesini dört kez art arda.  
  
   2. Seçin ve Visual Studio'ya **yığın. anlık görüntü Al** temel anlık görüntü için.  
  
   3. Uygulamada, seçin **bellek sızıntısı** düğmesi.  
  
   4. Seçin ve Visual Studio'ya **yığın. anlık görüntü Al** ikinci bir anlık görüntü.  
  
   5. Uygulamada, seçin **bellek sızıntısı** düğmesi.  
  
   6. Seçin ve Visual Studio'ya **yığın. anlık görüntü Al** üçüncü anlık görüntü.  
  
      Anlık görüntü #3 yığın boyutu olarak gösterdiğini **artış yok** anlık görüntü #2 ve nesne sayısı + 1 / -1, nesneleri bir gösteren eklenmiş olan ve bir nesne kaldırıldı. İstenen davranışı budur.  
  
      Anlık görüntü #2 ve anlık görüntü #3 aşağıda gösterilmiştir.  
  
      ![Anlık görüntüleri gösteren sabit bir bellek sızıntısı](../profiling/media/js-mem-app-fixed-snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JavaScript Belleği](../profiling/javascript-memory.md)



