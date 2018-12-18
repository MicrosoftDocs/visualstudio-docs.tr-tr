---
title: DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama | Microsoft Docs
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
- CSS styles [Windows Store apps], debugging
- CSS rules [Windows Store apps], debugging
- CSS debugging [Windows Store apps]
- debugging, CSS rules [Windows Store apps]
- HTML debugging [Windows Store apps]
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f5a2c8ef6792403628430cb9881b24e6e279f02
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750144"
---
# <a name="debug-css-styles-using-dom-explorer"></a>DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Windows Store uygulamaları, Windows Phone Store uygulamaları ve Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan uygulamaları hata ayıklama işlemi yaparken, görüntüleyebilir ve seçili DOM öğeleri ve bunların alt öğeleri CSS kurallarını değiştirin.  
  
 **Stilleri** ve **hesaplanan** DOM Gezgini sekmeleri seçili öğe için geçerli olan CSS kurallarını gösterir. Kurallar, CSS öncelik kurallarına göre kendi belirlilik sırasında görüntülenir. Bir sekmedeki bir seçici veya stilin en başında yer alan kurallar (en belirgin kurallar) seçili öğeye en son uygulanacak olanlardır ve bir seçici veya stilin en altında yer alan kurallarsa ilk uygulanacak olan kurallardır. Kural uygulandığında, daha önce uygulanan kuralları geçersiz kılar.  
  
 **Stilleri**, **hesaplanan**, ve **değişiklikleri** sekmelerinde stil bilgilerinin farklı görünümleri.  
  
-   Kullanım **stilleri** görüntülemek için sekmesinde kuralları gibi CSS Seçici adına göre düzenlenmiş `html, body`. Bu sekmeyi, belirli stilleri etkinleştirmek veya devre dışı bırakmak, değerleri el ile düzenlemek ve bu değişikliklerin sonuçlarını hemen görmek için de kullanabilirsiniz.  
  
-   Kullanım **hesaplanan** stilin hesaplanan değerlerini görüntülemek için sekmesinde. Örneğin, 1em için bir boyut ayarlarsanız, Internet Explorer tarafından hesaplanan değer 16px olabilir. Bu sekmedeki stiller, düzenlenir stil adına göre gibi `height`. Bu sekmeyi, belirli stilleri etkinleştirmek veya devre dışı bırakmak, değerleri el ile düzenlemek ve bu değişikliklerin sonuçlarını hemen görmek için de kullanabilirsiniz.  
  
    > [!NOTE]
    >  Bilgi sağlanan Visual Studio 2013 Update 2 ' **izleme** ile sekmesindeki birleştirildiği **hesaplanan** sekmesinde ve **izleme** sekmesi kaldırılmıştır.  
  
-   Kullanım **değişiklikleri** tanımlamak ve hata ayıklama oturumu sırasında değiştirdiğiniz CSS stillerini izlemek için sekmesinde (yalnızca Windows Store ve Windows Phone Store uygulamaları).  
  
> [!TIP]
>  Stillerde yaptığınız değişiklikler **stilleri** ve **hesaplanan** sekmeleri kalıcı değildir. Hata ayıklamayı durdurduğunuzda kaybolurlar. Kaynak kodu değiştirmek ve hata ayıklayıcıyı durdurup yeniden olmadan sayfaları yeniden yüklemek için kullanarak uygulamanızı yenileyin ![Yenile Windows uygulama düğmesine](../debugger/media/js-refresh.png "JS_Refresh") düğmesine (**Yenile Windows uygulaması** ) üzerinde **hata ayıklama** araç çubuğu (yalnızca Windows Store ve Windows Phone Store uygulamaları). Daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="example-of-fixing-a-css-rule"></a>CSS kuralı düzeltme örneği  
 Bu örnekte, CSS kurallarının nasıl inceleneceği ve stil sorunlarında nasıl hata ayıklanacağı gösterilmiştir. Bu örnekte, varsayalım grup başlıklarını görüntülemek için kullanılan bir yazı tipi rengini değiştirmek istediğiniz [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] bölünmüş uygulama şablonunda.  
  
> [!NOTE]
>  Bu örnek, bir Windows Store uygulaması gösterir, ancak gösterilen tüm DOM Gezgini özellikleri Windows Phone Store App ve Apache Cordova için Visual Studio araçları kullanarak oluşturulan bir uygulama değişiklikleri sekmesinde dışında de geçerlidir.  
  
#### <a name="to-view-and-change-css-rules"></a>CSS kurallarını görüntülemek ve değiştirmek için  
  
1.  Visual Studio'da oluşturma bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] bölünmüş uygulama proje şablonunda JavaScript ve HTML kullanarak uygulama.  
  
2.  İçinde **Çözüm Gezgini**, items.CSS'yi açın. (İtems.css'yi sayfalar klasöründe bulabilirsiniz.)  
  
3.  Aşağıdaki CSS kodunu değiştirin:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
    }  
    ```  
  
     şununla değiştirin:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
        color: #ff6a00;  
    }  
    ```  
  
     Böylece, listedeki her madde için #ff6a00 (orange) rengini belirten bir stil eklenir. CSS Seçici `.itemspage .itemslist .item`, Canlı DOM'da iç içe geçmiş öğe olarak görüntülenen öğelerin DIV items.html içinde sınıf adları kümesini gösterir `item` DIV öğesi liste öğelerini belirtir.  
  
4.  Seçin **simülatör** aşağı açılan listesinde **hata ayıklama** araç çubuğu (**yerel makine** varsayılan değerdir).  
  
     ![Select hata ayıklama hedef liste](../debugger/media/js-select-target.png "JS_Select_Target")  
  
5.  Uygulamanızı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
     Uygulama yüklemesi tamamlandığında, arama liste öğelerinin başlıkları gibi yüklenirken **grup başlığı: 1**. Renk değişmez ve dolayısıyla turuncu renk uygulama girişimi işe yaramamıştır. Neyin yanlış gittiğini bulalım ve DOM Gezgini'ndeki CSS sekmelerini kullanarak düzeltelim.  
  
    > [!TIP]
    >  Uygulama Simulator'da göründükten sonra, CSS stillerinde yaptığınız seçimlerin ve değişikliklerin sonuçlarını hemen görebilmek için Simulator'ı hemen Visual Studio penceresinin yanına konumlandırın.  
  
6.  Visual Studio'ya geçip tıklatın **öğe seçin** DOM Gezgini (veya Ctrl + B tuşuna basın). Böylece seçim modu değişir ve öğeyi tıklatarak seçebilirsiniz ve uygulama da önplana gelir. Tek tıklatmadan sonra mod geri döner. İşte **öğe seçin** düğmesi. ![DOM Gezgini'nde öğe düğmesini seçme](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
    > [!TIP]
    >  HTML öğelerini doğrudan DOM Gezgini'nde de seçebilirsiniz. Öğeleri seçme hakkında daha fazla bilgi için bkz. [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7.  Simulator'da, listedeki ilk öğeyi başlığının üzerine geldiğinizde **grup başlığı: 1**, giriş sayfasının sol bölmesinde. Başlık aşağıda gösterildiği gibi vurgulanır:  
  
     ![Öğe seçin düğmesini kullanarak](../debugger/media/js-css-select-element.png "JS_CSS_Select_Element")  
  
    > [!NOTE]
    >  Windows Phone öykünücüsü gelerek vurgulama öğeleri yalnızca kısmen destekler.  
  
8.  Seviyelendirilmiş başlığını tıklatın. DOM Gezgini ilgili HTML öğesini otomatik olarak seçer ve bu da aşağıdaki gibidir.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     DOM Gezgini'nde H4 öğesini seçtiğinizde, artık DOM Gezgini sekmeleri H4 öğesiyle ilişkilendirilmiş kuralları gösterir. **Hesaplanan** sekmesi gösterilmiştir Burada, `color` özelliği açık:  
  
     ![DOM Gezgini'nde izleme stiller sekmesi](../debugger/media/js-css-styles.png "JS_CSS_Styles")  
  
     Bu görünüm, ilişkili kurallar hakkında yararlı bilgiler sağlayan `color` stil, aşağıdaki gibi:  
  
    -   Biz değiştiren değiştirdiğimiz CSS Seçici `.itemspage .itemslist .item`, (üstü çizili metin olarak görünür) son stil hesaplamasında kullanılmadığını. Başka birkaç örneği `color` stili de kullanılmaz.  
  
        > [!TIP]
        >  Uzun seçici adları söz konusu olduğunda, araç ipucunda tam ad görüntülenir.  
  
    -   Son hesaplanan CSS değeri `rgba(255, 255, 255, 0.87)`, özel olarak şu CSS Seçici için ayarlanır: `.itemspage .itemslist .item .item-overlay .item-title`, items.CSS'de tanımlıdır ayrıca tanımlanan.  
  
        > [!TIP]
        >  Başlık renginin nerede ayarlandığını öğrendiğimize göre, nerede değiştirebileceğimizi de biliyoruz demektir. Ancak, kalan adımlarda gösterildiği gibi, uygulamayı yenilemeden değişiklikleri DOM Gezgini'nde test edebiliriz.  
  
9. İlk oluşum için onay kutusunu temizleyin `color` stilinin, `.itemspage .itemslist .item .item-overlay .item-title` Seçici. Şimdi Simulator'da, öğenin rengini istediğimiz ve biz, CSS Seçici değiştiren tüm değişiklik turuncu, başlıklar görmeniz `.itemspage .itemslist .item`, artık geçersiz kılınmadığı (diğer bir deyişle, artık uygulanan üstü çizili metin vardır). İşte **hesaplanan** biz onay kutusunu temizledikten sonra sekmesi.  
  
     ![CSS stil güncelleştirdikten sonra hesaplanan sekmesini](../debugger/media/js-css-styles-fixed.png "JS_CSS_Styles_Fixed")  
  
10. Seçin **değişiklikleri** sekmesi.  
  
     Kullanım **değişiklikleri** tanımlamak ve hata ayıklama oturumu sırasında yaptığınız stil değişikliklerini izlemek için sekmesinde. Aşağıdaki çizimde gösterildiği `.itemspage .itemslist .item .item-overlay .item-title` seçicide **değişiklikleri** sekmesinde, artık geçersiz kılınır.  
  
     ![DOM Gezgini değişiklikleri sekmesinde](../debugger/media/js-css-styles-changes.png "JS_CSS_Styles_Changes")  
  
11. El ile CSS stil değerlerini düzenleyin ve kullanarak sonuçları hemen görebilirsiniz **stilleri** sekmesi.  
  
12. Seçin **stilleri** sekmesi.  
  
13. Açık `.itemspage .itemslist .item .item-overlay .item-title` stil seçicisini.  
  
14. İlk örneğini seçin `color` stil ve özellik değerini çift tıklatarak `rgb(255, 255, 255, 0.87)`.  
  
15. Bu değeri değiştirmek için klavyeyi kullanın. Değiştirin `rgb(255, 255, 0, 0.87)`, ve ardından Enter tuşuna basın. Simulator'da tüm öğe başlıklarının rengi sarı olarak değişir.  
  
16. Kaynak CSS dosyası için değişiklik yapmak için tıklatın **items.CSS'yi** bağlantısını **stilleri** sekmesi. Bu değeri değiştirebileceğiniz items.css açılır `color` , uygulama kodunuz stili. Durdurup hata ayıklayıcıyı yeniden başlatmadan uygulamayı yenilemek için şuna tıklayın ![Yenile Windows uygulama düğmesine](../debugger/media/js-refresh.png "JS_Refresh") (**Yenile Windows uygulama**) düğmesine **Hata ayıklama** araç çubuğu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)   
 [DOM Gezgini'ni kullanarak Düzen hatalarını ayıklama](../debugger/debug-layout-using-dom-explorer.md)   
 [DOM olayı dinleyicilerini görüntüleme](../debugger/view-dom-event-listeners.md)   
 [Ürün desteği ve erişilebilirlik](http://go.microsoft.com/fwlink/?LinkId=253502)



