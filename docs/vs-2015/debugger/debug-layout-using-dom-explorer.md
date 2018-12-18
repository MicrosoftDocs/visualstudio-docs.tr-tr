---
title: DOM Gezgini'ni kullanarak Düzen hatalarını ayıklama | Microsoft Docs
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
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba06e6a8ba95887c0cc6b6acfd14cef10ff03798
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787766"
---
# <a name="debug-layout-using-dom-explorer"></a>DOM Gezgini'ni kullanarak düzen hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 **Düzen** DOM Gezgini gösterir sekmesinde [CSS kutu modeli](http://go.microsoft.com/fwlink/?LinkID=238778) seçili öğe için bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulaması, Windows Phone Store uygulaması veya Apache Cordova için Visual Studio araçları kullanarak oluşturulan bir uygulama. Bu kutu modeli görsel bir temsilini tanımlamak ve öğelerin görünümünü etkileyen Düzen ilgili değerleri değiştirmek için kullanabilirsiniz.  
  
> [!TIP]
>  Yaptığınız değişiklikler **Düzen** sekmesini kalıcı değildir. Kaynak kodunuzu kalıcı değişiklikler yapın ve ardından kullanarak uygulamanızı yenileyin **Yenile Windows uygulama** hata ayıklama araç çubuğu düğmesini (yalnızca Windows Store ve Windows Phone Store uygulamaları). Bu şekilde, hata ayıklayıcı yeniden başlatmayı önleyebilirsiniz.  
  
 Kutusu modelinde gösterilmeyen düzen özelliklerini değiştirmek için DOM Gezgini'ni kullanmak için bkz: [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) ve [DOM Gezgini'ni kullanarak hata ayıklama CSS stillerinde](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="example-of-fixing-a-layout-issue"></a>Bir düzen sorunu düzeltme örneği  
 Bu örnekte, bir liste öğesinin Hub/Pivot şablonu, bulunan kutu modeli değerleri yorumlar gösterilmektedir **Düzen** sekmesini ve sonra bir düzen sorununu düzeltmek için özellik değerlerini değiştirin.  
  
#### <a name="to-fix-the-layout-issue"></a>Düzen sorunu düzeltmek için  
  
1.  Visual Studio'da Hub/Pivot proje şablonu kullanan yeni bir Store uygulaması oluşturun.  
  
2.  Paylaşılan pages\hub klasöründe hub.css açın.  
  
3.  Aşağıdaki CSS kodunu değiştirin:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     Bu CSS kod ile:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4.  AppName.WindowsPhone veya appName.Windows projesi ya da Çözüm Gezgini'nde seçin ve ardından **başlangıç projesi olarak ayarla** proje için kısayol menüsünden.  
  
5.  Başlangıç projeniz bağlı olarak seçin **öykünücüsü 8.1 WVGA 4 inç 512 MB** veya **simülatör** hata ayıklama araç çubuğundaki aşağı açılan listesinde (**yerel makine** varsayılandır değer).  
  
     ![Hata ayıklama hedef seçme](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6.  Uygulamanızı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
7.  4. bölüm, kaydırma veya flicking açın.  
  
    > [!TIP]
    >  Seçimleri ve CSS stillerinde yaptığınız değişikliklerin sonuçlarını hemen görmek için Visual Studio penceresinde yanındaki Phone öykünücü veya benzetici sağ konumu.  
  
     4. Bölüm yüklediğinde, daha düşük görüntüleri doğru görünmüyor görebilirsiniz. Her öğe görüntü Kes (sol yarısına eksik olan) yarıya görünür.  
  
8.  Seçin ve Visual Studio'ya **öğe seçin** DOM Gezgini (veya Ctrl + B tuşuna basın). Böylece seçim modu değişir ve öğeyi tıklatarak seçebilirsiniz ve uygulama da önplana gelir. Tek tıklatmadan sonra mod geri döner.  
  
    > [!TIP]
    >  HTML öğelerini doğrudan DOM Gezgini'nde seçmek için ok tuşlarını ya da diğer yöntemleri kullanabilirsiniz. Öğeleri seçme hakkında daha fazla bilgi için bkz. [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. Phone öykünücü veya benzetici, gri sağ yarısında yarıya inmiştir görüntülerden birini seçin. Vurgulama seçilen öğe, Windows Phone öykünücüsü'nde burada gösterildiği gibi görünür:  
  
     ![DOM öğesini seçerek](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    >  Bunlardan birini önce kutusu DOM öğeleri vurgulama göstermek için öğelerin üzerine geldiğinizde Simülatörünü destekler. Windows Phone öykünücüsü bu desteklemez.  
  
     DOM öğesini seçtiğinizde, DOM Gezgini ilgili IMG öğesi Visual Studio'da otomatik olarak seçer. DOM Gezgini'nde seçilen öğenin şöyle görünür:  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. Tıklayın **Düzen** sekmesi. Bu sekme, Windows Phone öykünücüsü'nde burada gösterildiği gibi seçili öğenin kutu modelinin gösterir.  
  
     ![DOM Gezgini Düzen sekmesinde](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Bu görünüm öğeyle ilgili bazı yararlı bilgiler sağlar:  
  
    -   Renkleri vurgulama Simülatörde öğelerin üzerine gelindiğinde görüntülenen kutusu için karşılık gelir. Mavi rengi temsil \<img > öğesi boyutları. Tan rengi kenar boşluğu değerleri temsil eder.  
  
    -   (Siyah görüntüleri sol tarafında) belirti eşleştiği için hangi ipuçları sorunun nedenini sol kenar boşluğu (sol kenar boşluğu) ayarlanır.  
  
    -   0 piksel (örneğin, kenarlık ve dolguyla) değerlerini göster kutuları karşılık gelen CSS özelliklerini büyük olasılıkla ayarlandığını önerir.  
  
11. Sol kenar boşluğu kural nasıl uygulandığını görmek için **hesaplanan** sekmesinde ve sol kenar boşluğu kuralı altına bakın. Bu kural 5em değeriyle ayarlanmış, ancak hesaplanan değer 66.66px ya da 146.66px, hedef cihazınıza bağlı olduğunu görebilirsiniz.  
  
    > [!TIP]
    >  **Hesaplanan** sekme gösterir sol kenar boşluğu kural kümesi `..hubpage .hub. section4 .sub-image-row img` CSS Seçici, hub.css içinde bulunamadı. Bu Tanıtım uygulamada düzeltme yapmak gerek duyduğunuz olmasıdır.  
  
     Ayrıca **Düzen** Düzen değerleri değişiklikleri test etmek için sekmesinde.  
  
12. İçinde **Düzen** sekmesini, ya da **66.66** veya **146.66**, içinde göründüğü **kenar boşluğu** kutusunun sol tarafında kutusu.  
  
13. Tür `0` ve Enter tuşuna basın. (Ayrıca yukarı ok ve aşağı ok tuşlarını değeri değiştirmek için kullanabilirsiniz.)  
  
14. Diğer seçin \<img > öğelerini DOM Gezgini ve bunların sol kenar boşluğu değerleri 0 olarak değiştirin.  
  
15. Phone öykünücü veya simülatör geçin. 4. Bölüm görüntülerin güncelleştirilmiş sol kenar boşluğu değerleri uygulandı. Bu değerleri de güncellenir **hesaplanan** sekmesi altında sol kenar boşluğu kuralı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)   
 [DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)   
 [DOM olayı dinleyicilerini görüntüleme](../debugger/view-dom-event-listeners.md)



