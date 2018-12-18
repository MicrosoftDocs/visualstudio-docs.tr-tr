---
title: Bir Web Görünümü denetimi (UWP) hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4576cfa5724869aba86842c5debb4df685559879
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465466"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Bir UWP uygulaması WebView denetiminde hata ayıklama
  
 İncelemek ve hata ayıklama için `WebView` Windows çalışma zamanı uygulama denetimlerinde, uygulamanızı başlattığınızda komut dosyası hata ayıklayıcısı eklemek için Visual Studio yapılandırabilirsiniz. İle etkileşim kurmak için iki yolu vardır `WebView` hata ayıklayıcıyı kullanma denetler:  
  
-   Açık [DOM Gezgini](../debugger/quickstart-debug-html-and-css.md) için bir `WebView` örneği, DOM öğeleri inceleyin, CSS stili sorunları araştırmak ve stilleri dinamik olarak işlenen değişiklikler test.  
  
-   Web sayfası seçin veya `iFrame` görüntülenen `WebView` örneği bir hedef olarak [JavaScript Konsolu](../debugger/javascript-console-commands.md) penceresinde ve ardından Konsolu komutları kullanarak Web sayfası ile etkileşime. Konsol geçerli komut dosyası yürütme bağlamı erişim sağlar.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Hata ayıklayıcısını (C#, Visual Basic, C++)  
  
1.  Visual Studio'da eklemek bir `WebView` ve Windows çalışma zamanı uygulamanızın denetim.  
  
2.  Çözüm Gezgini'nde seçerek proje özelliklerini açın **özellikleri** projesinin kısayol menüsünden.  
  
3.  Seçin **hata ayıklama**. İçinde **uygulama işlemi** listesinde, seçin **betik**.  
  
     ![Komut dosyası hata ayıklayıcısını](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (İsteğe bağlı) Visual Studio Express olmayan sürümleri için tam zamanında (JIT) seçerek hata ayıklama devre dışı **Araçlar > Seçenekler > hata ayıklama > hemen zaman**, ve hata ayıklama için komut dosyası JIT devre dışı bırakma.  
  
    > [!NOTE]
    >  JIT hata ayıklama devre dışı bırakarak, bazı sayfalarında meydana gelen işlenmeyen özel durumlar için iletişim kutularını gizleyebilirsiniz. Visual Studio Express JIT hata ayıklamayı her zaman devre dışı bırakılır.  
  
5.  Hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>İnceleyin ve bir Web Görünümü denetimi hata ayıklama için DOM Gezgini'ni kullanın  
  
1.  (C#, Visual Basic, C++) Komut dosyası hata ayıklayıcısı uygulamanıza ekleyin. Yönergeler için ilk bölümüne bakın.  
  
2.  Henüz yapmadıysanız, ekleme bir `WebView` denetim uygulamanıza ve hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
3.  Sayfayı içeren gidin `Webview` control(s).  
  
4.  DOM Gezgini penceresi açmak `WebView` seçerek denetim **hata ayıklama**, **Windows**, **DOM Gezgini**ve ardından URL'sini `WebView` , incelemek istediğiniz.  
  
     ![DOM Gezgini'ni açıp](../debugger/media/js_dom_webview.png "JS_DOM_WebView")  
  
     DOM Gezgini'nde ilişkili `WebView` Visual Studio'da yeni bir sekme olarak görünür.  
  
5.  Görüntüleme ve açıklandığı gibi dinamik DOM öğeleri ve CSS stilleri değiştirme [DOM Gezgini'ni kullanarak hata ayıklama CSS stilleri](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>JavaScript Konsolu penceresi inceleyin ve bir Web Görünümü denetimi hata ayıklamak için kullanın  
  
1.  (C#, Visual Basic, C++) Komut dosyası hata ayıklayıcısı uygulamanıza ekleyin. Yönergeler için ilk bölümüne bakın.  
  
2.  Henüz yapmadıysanız, ekleme bir `WebView` denetim uygulamanıza ve hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
3.  JavaScript konsolu penceresini `WebView` seçerek denetim **hata ayıklama**, **Windows**, **JavaScript Konsolu**.  
  
     JavaScript Konsolu penceresi görüntülenir.  
  
4.  Sayfayı içeren gidin `Webview` control(s).  
  
5.  Konsol penceresinde, Web sayfası seçin veya bir `iFrame` tarafından görüntülenen `WebView` denetim **hedef** listesi.  
  
     ![Hedef seçimi JavaScript konsol penceresinde](../debugger/media/js_console_target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Konsolunu kullanarak, tek bir etkileşim kurabilen `WebView`, `iFrame`paylaşmak sözleşme veya aynı anda çalışan web. Her öğe ayrı bir web platformu ana bilgisayar (WWAHost.exe) örneği gerektirir. Aynı anda bir ana bilgisayar ile etkileşim kurabilirsiniz.  
  
6.  Görüntüleyin ve uygulamanızda değişkenleri değiştirin veya açıklandığı gibi konsol komutlarını kullanmak [hızlı başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md) ve [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç: HTML ve CSS hata ayıklama](../debugger/quickstart-debug-html-and-css.md)