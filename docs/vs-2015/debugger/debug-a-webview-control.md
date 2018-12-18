---
title: Bir WebView denetiminde hata ayıklama | Microsoft Docs
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
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f8a4dcc64903b97e3b469fb962777e3b90f84ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729077"
---
# <a name="debug-a-webview-control"></a>WebView denetiminde hata ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Denetlemek ve hatalarını ayıklamak için `WebView` bir Windows çalışma zamanı uygulama denetimleri, uygulamanız başlatıldığında komut dosyası hata ayıklayıcı iliştirmek için Visual Studio yapılandırabilirsiniz. Visual Studio 2013 güncelleştirme 2 ile başlayarak, ile etkileşim kurmak için iki yolumuz olur `WebView` hata ayıklayıcıyı kullanma denetler:  
  
-   Açık [DOM Gezgini](../debugger/quickstart-debug-html-and-css.md) için bir `WebView` örneğini ve DOM öğeleri inceleyin, CSS stil sorunlarını araştırmak ve dinamik olarak işlenen değişiklikleri stilleri için test.  
  
-   Web sayfası seçin veya `iFrame` görüntülenen `WebView` örneği bir hedef olarak [JavaScript Konsolu](../debugger/javascript-console-commands.md) penceresinde ve ardından Konsolu komutları kullanarak bir Web sayfası ile etkileşim kurun. Konsolu, geçerli komut dosyası yürütme bağlamı erişim sağlar.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Hata ayıklayıcının (C#, Visual Basic, C++)  
  
1.  Visual Studio'da ekleme bir `WebView` uygulamanızı Windows çalışma zamanı denetimi.  
  
2.  Çözüm Gezgini'nde seçerek proje özelliklerini açın. **özellikleri** proje için kısayol menüsünden.  
  
3.  Seçin **hata ayıklama**. İçinde **uygulama işlemi** listesinde **betik**.  
  
     ![Komut dosyası hata ayıklayıcının](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (İsteğe bağlı) Visual Studio Express olmayan sürümleri, seçerek just-in-time (JIT) hata ayıklama devre dışı **Araçları**, **seçenekleri**, **hata ayıklama**, **Just-ın-Time**, ve JIT devre dışı bırakmak için betik hata ayıklama.  
  
    > [!NOTE]
    >  JIT hata ayıklama devre dışı bırakarak, iletişim kutuları için bazı sayfalarında meydana gelen işlenmeyen özel durumları gizleyebilirsiniz. Visual Studio Express JIT hata ayıklama her zaman devre dışı bırakıldı.  
  
5.  Hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>İnceleyin ve bir WebView denetiminde hata ayıklama için DOM Gezgini'ni kullanın  
  
1.  (C#, Visual Basic, C++) Komut dosyası hata ayıklayıcı uygulamanıza ekleyin. Yönergeler için ilk bölümüne bakın.  
  
2.  Henüz yapmadıysanız, ekleme bir `WebView` denetlemek için uygulamanızı ve hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
3.  İçeren dizine gidin `Webview` denetim.  
  
4.  DOM Gezgini penceresini `WebView` denetimi seçerek **hata ayıklama**, **Windows**, **DOM Gezgini**, URL'sini seçin `WebView` , incelemek istediğiniz.  
  
     ![DOM Gezgini'ni açıp](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     DOM Gezgini ile ilişkili `WebView` Visual Studio'da yeni bir sekme olarak görünür.  
  
5.  Görüntüleme ve açıklandığı gibi canlı DOM öğeleri ve CSS stilleri değiştirme [DOM Gezgini'ni kullanarak hata ayıklama CSS stillerinde](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>JavaScript Konsolu penceresi inceleyin ve bir WebView denetiminde hata ayıklama için kullanın  
  
1.  (C#, Visual Basic, C++) Komut dosyası hata ayıklayıcı uygulamanıza ekleyin. Yönergeler için ilk bölümüne bakın.  
  
2.  Henüz yapmadıysanız, ekleme bir `WebView` denetlemek için uygulamanızı ve hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
3.  JavaScript Konsolu penceresi açın `WebView` denetimi seçerek **hata ayıklama**, **Windows**, **JavaScript Konsolu**.  
  
     JavaScript Konsolu penceresi görüntülenir.  
  
4.  İçeren dizine gidin `Webview` denetim.  
  
5.  Konsol penceresinde Web sayfası seçin veya bir `iFrame` tarafından görüntülenen `WebView` denetim **hedef** listesi.  
  
     ![Hedef seçimi JavaScript konsol penceresinde](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Konsolunu kullanarak, tek bir etkileşim kurabilir `WebView`, `iFrame`, paylaşmak sözleşme veya aynı anda çalışan web. Her öğesi, web platformu ana bilgisayarı (WWAHost.exe) ayrı bir örneğini gerektirir. Bir kerede bir ana bilgisayar ile etkileşim kurabilir.  
  
6.  Görüntüleme ve uygulamanızda değişkenleri değiştirin ya da açıklandığı gibi konsol komutlarını kullanın [hızlı başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md) ve [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)



