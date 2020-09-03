---
title: DOM Gezginini kullanarak CSS stillerinde hata ayıkla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 676a4ef2570873998f3ebc890e06d6d5ccae4cf2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852432"
---
# <a name="debug-css-styles-using-dom-explorer"></a>DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan Windows Mağazası uygulamaları, Windows Phone mağaza uygulamaları ve uygulamaları hata ayıkladığınızda, seçilen DOM öğeleri ve bunların alt öğeleri için CSS kurallarını görüntüleyebilir ve değiştirebilirsiniz.  
  
 DOM Gezgini 'ndeki **Stiller** ve **hesaplanan** sekmeler seçili BIR öğe için uygulanan CSS kurallarını gösterir. Kurallar, CSS öncelik kurallarına göre kendi belirlilik sırasında görüntülenir. Bir sekmedeki bir seçici veya stilin en başında yer alan kurallar (en belirgin kurallar) seçili öğeye en son uygulanacak olanlardır ve bir seçici veya stilin en altında yer alan kurallarsa ilk uygulanacak olan kurallardır. Kural uygulandığında, daha önce uygulanan kuralları geçersiz kılar.  
  
 **Stiller**, **hesaplanan**ve **değişiklikler** sekmeleri stil bilgisinin farklı görünümlerini sağlar.  
  
- CSS seçici adına göre düzenlenen kuralları görüntülemek için **Stiller** sekmesini kullanın (örneğin,) `html, body` . Bu sekmeyi, belirli stilleri etkinleştirmek veya devre dışı bırakmak, değerleri el ile düzenlemek ve bu değişikliklerin sonuçlarını hemen görmek için de kullanabilirsiniz.  
  
- Bir stilin hesaplanan değerlerini görüntülemek için **hesaplanan** sekmesini kullanın. Örneğin, 1em için bir boyut ayarlarsanız, Internet Explorer tarafından hesaplanan değer 16px olabilir. Bu sekmedeki stiller, gibi stil adına göre düzenlenmiştir `height` . Bu sekmeyi, belirli stilleri etkinleştirmek veya devre dışı bırakmak, değerleri el ile düzenlemek ve bu değişikliklerin sonuçlarını hemen görmek için de kullanabilirsiniz.  
  
    > [!NOTE]
    > Visual Studio 2013 güncelleştirme 2 ' de, **izleme** sekmesinde belirtilen bilgiler, **hesaplanan** sekmeyle birleştirildi ve **izleme** sekmesi kaldırılmıştır.  
  
- Bir hata ayıklama oturumu sırasında değiştirdiğiniz CSS stillerini tanımlamak ve izlemek için **değişiklikler** sekmesini (yalnızca Windows mağazası ve Windows Phone Store uygulamaları) kullanın.  
  
> [!TIP]
> **Stillerde** ve **hesaplanan** sekmelerdeki stillerde yaptığınız değişiklikler kalıcı değildir. Hata ayıklamayı durdurduğunuzda kaybolurlar. Hata ayıklayıcıyı durdurup yeniden başlatmadan kaynak kodunu değiştirmek ve sayfaları yeniden yüklemek için, **hata ayıklama** araç çubuğundaki ![Windows uygulamasını Yenile düğme](../debugger/media/js-refresh.png "JS_Refresh") **düğmesini (Windows**Mağazası ve Windows Phone Store uygulamaları) kullanarak uygulamanızı yenileyin. Daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="example-of-fixing-a-css-rule"></a>CSS kuralı düzeltme örneği  
 Bu örnekte, CSS kurallarının nasıl inceleneceği ve stil sorunlarında nasıl hata ayıklanacağı gösterilmiştir. Bu örnekte, bölünmüş uygulama şablonunda grup başlıklarını göstermek için kullanılan bir yazı tipinin rengini değiştirmek istediğinizi varsayalım [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .  
  
> [!NOTE]
> Bu örnekte bir Windows Mağazası uygulaması gösterilmektedir, ancak gösterilen tüm DOM Gezgini özellikleri bir Windows Phone Mağazası uygulaması için de geçerlidir ve değişiklikler sekmesi dışında, Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan bir uygulama.  
  
#### <a name="to-view-and-change-css-rules"></a>CSS kurallarını görüntülemek ve değiştirmek için  
  
1. Visual Studio 'da, [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] bölünmüş uygulama proje şablonunda JavaScript ve HTML kullanarak bir uygulama oluşturun.  
  
2. **Çözüm Gezgini**, Items. css ' yi açın. (İtems.css'yi sayfalar klasöründe bulabilirsiniz.)  
  
3. Aşağıdaki CSS kodunu değiştirin:  
  
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
  
     Böylece, listedeki her madde için #ff6a00 (orange) rengini belirten bir stil eklenir. CSS Seçicisi, `.itemspage .itemslist .item` Canlı DOM 'da iç içe geçmiş öğeler olarak görünen items.html IÇINDEKI DIV öğeleri için bir sınıf adları kümesini gösterir. `item`DIV öğesi liste öğelerini belirtir.  
  
4. **Hata ayıklama** araç çubuğundaki aşağı açılan listeden **simülatör** ' ı seçin (**yerel makine** varsayılan değerdir).  
  
     ![Hata ayıklama hedef listesini seçin](../debugger/media/js-select-target.png "JS_Select_Target")  
  
5. Uygulamanızı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
     Uygulamanın yüklenmesi bittiğinde, **grup başlığı: 1**gibi liste öğelerinin başlıklarına bakın. Renk değişmez ve dolayısıyla turuncu renk uygulama girişimi işe yaramamıştır. Neyin yanlış gittiğini bulalım ve DOM Gezgini'ndeki CSS sekmelerini kullanarak düzeltelim.  
  
    > [!TIP]
    > Uygulama Simulator'da göründükten sonra, CSS stillerinde yaptığınız seçimlerin ve değişikliklerin sonuçlarını hemen görebilmek için Simulator'ı hemen Visual Studio penceresinin yanına konumlandırın.  
  
6. Visual Studio 'ya geçin ve DOM Gezgini 'nde **öğe seç** ' e tıklayın (veya CTRL + B tuşlarına basın). Böylece seçim modu değişir ve öğeyi tıklatarak seçebilirsiniz ve uygulama da önplana gelir. Tek tıklatmadan sonra mod geri döner. **Öğe seç** düğmesi aşağıda verilmiştir. ![DOM Gezgini 'nde öğe seç düğmesi](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
    > [!TIP]
    > HTML öğelerini doğrudan DOM Gezgini'nde de seçebilirsiniz. Öğe seçme hakkında daha fazla bilgi için bkz. [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7. Simülatör 'da, giriş sayfasının sol panelinde, listedeki ilk öğenin başlığının üzerine gelin, **grup başlığı: 1**. Başlık aşağıda gösterildiği gibi vurgulanır:  
  
     ![Öğe Seç düğmesini kullanma](../debugger/media/js-css-select-element.png "JS_CSS_Select_Element")  
  
    > [!NOTE]
    > Windows Phone öykünücüsü, öğeleri vurgulayarak yalnızca kısmen destekler.  
  
8. Seviyelendirilmiş başlığını tıklatın. DOM Gezgini ilgili HTML öğesini otomatik olarak seçer ve bu da aşağıdaki gibidir.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     DOM Gezgini'nde H4 öğesini seçtiğinizde, artık DOM Gezgini sekmeleri H4 öğesiyle ilişkilendirilmiş kuralları gösterir. **Hesaplanan** sekme burada, `color` özelliği açık şekilde gösterilir:  
  
     ![DOM Gezgini 'nde izleme stilleri sekmesi](../debugger/media/js-css-styles.png "JS_CSS_Styles")  
  
     Bu görünüm, stille ilişkili kurallar hakkında aşağıdakiler gibi yararlı bilgiler sağlar `color` :  
  
    - Items. css ' de değiştirildiğimiz CSS Seçicisi, `.itemspage .itemslist .item` son stil hesaplamasında kullanılmıyor (üstü çizili metinde görünür). Stilin bazı diğer örnekleri `color` de kullanılmıyor.  
  
        > [!TIP]
        > Uzun seçici adları söz konusu olduğunda, araç ipucunda tam ad görüntülenir.  
  
    - Son hesaplanan CSS değeri, `rgba(255, 255, 255, 0.87)` AŞAĞıDAKI CSS Seçicisi için özel olarak ayarlanmıştır: `.itemspage .itemslist .item .item-overlay .item-title` Items. css dosyasında da tanımlanır.  
  
        > [!TIP]
        > Başlık renginin nerede ayarlandığını öğrendiğimize göre, nerede değiştirebileceğimizi de biliyoruz demektir. Ancak, kalan adımlarda gösterildiği gibi, uygulamayı yenilemeden değişiklikleri DOM Gezgini'nde test edebiliriz.  
  
9. `color`Stilin, seçiciyle ilgili olan ilk oluşum için onay kutusunu temizleyin `.itemspage .itemslist .item .item-overlay .item-title` . Şimdi, benzeticide, tüm öğe başlıklarının renginin, amaçladığınız şekilde ve CSS 'de değiştirildiğimiz seçicinin `.itemspage .itemslist .item` artık geçersiz kılınmadığını görürsünüz (diğer bir deyişle, artık üzeri çizili metin uygulanmaz). Bu onay kutusunu temizledikten sonra **hesaplanan** sekme aşağıda verilmiştir.  
  
     ![CSS stili güncelleştirildikten sonra hesaplanan sekme](../debugger/media/js-css-styles-fixed.png "JS_CSS_Styles_Fixed")  
  
10. **Değişiklikler** sekmesini seçin.  
  
     Bir hata ayıklama oturumu sırasında yaptığınız stil değişikliklerini tanımlamak ve izlemek için **değişiklikler** sekmesini kullanın. Aşağıdaki çizimde `.itemspage .itemslist .item .item-overlay .item-title` **değişiklikler** sekmesindeki seçici gösterilmektedir, bu artık geçersiz kılınır.  
  
     ![DOM Gezgini 'nin değişiklikler sekmesi](../debugger/media/js-css-styles-changes.png "JS_CSS_Styles_Changes")  
  
11. Ayrıca CSS stil değerlerini el ile düzenleyebilir ve **Stiller** sekmesini kullanarak anında sonuca bakabilirsiniz.  
  
12. **Stiller** sekmesini seçin.  
  
13. `.itemspage .itemslist .item .item-overlay .item-title`Stil seçiciyi açın.  
  
14. Stilin ilk oluşumunu seçin `color` ve ardından özellik değerine çift tıklayın `rgb(255, 255, 255, 0.87)` .  
  
15. Bu değeri değiştirmek için klavyeyi kullanın. Olarak değiştirin `rgb(255, 255, 0, 0.87)` ve ardından ENTER tuşuna basın. Simulator'da tüm öğe başlıklarının rengi sarı olarak değişir.  
  
16. Kaynak CSS dosyasında değişiklik yapmak için **Stiller** sekmesinde **Items. css** bağlantısına tıklayın. Bu, uygulama kodunuzda stilin değerini değiştirebileceğiniz Items. css ' yi açar `color` . Hata ayıklayıcıyı durdurup yeniden başlatmadan uygulamayı yenilemek için, **hata ayıklama** araç çubuğundaki ![Windows uygulamasını Yenile düğmesine](../debugger/media/js-refresh.png "JS_Refresh") (**Windows uygulamasını Yenile**) tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md)   
 [DOM Gezginini kullanarak hata ayıklama düzeni](../debugger/debug-layout-using-dom-explorer.md)   
 [DOM olay dinleyicilerini görüntüle](../debugger/view-dom-event-listeners.md)   
 [Ürün desteği ve erişilebilirlik](https://msdn.microsoft.com/library/tzbxw1af(VS.110).aspx)
