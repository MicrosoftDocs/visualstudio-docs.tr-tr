---
title: Kodlanmış UI testleri farklı Web tarayıcıları ile kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: gewarren
manager: douge
ms.openlocfilehash: e9e540e35bdfd68d8c371c2bad0ace3fc4b420e0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893240"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Kodlanmış UI Testleriyle Farklı Web Tarayıcıları Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI testleri, web uygulamaları için Internet Explorer'ı kullanarak testlerinizi kaydederek sınamayı otomatikleştirebilirsiniz. Bu web uygulamaları için Internet Explorer veya başka tarayıcı türleri kullanarak testinizi özelleştirebilir ve geri oynatabilirsiniz.  
  
 **Gereksinimler**  
  
- Visual Studio Enterprise  
  
- İşletim sistemleri:  
  
  -   Microsoft Windows 7  
  
  -   Microsoft Windows 8  
  
  -   Microsoft Windows Server 2008 R2 SP1  
  
- Web tarayıcı sürümleri:  
  
  -   Windows Internet Explorer 9  
  
  -   Windows Internet Explorer 10  
  
  -   Mozilla Firefox ve Google Chrome'un desteklenen sürümleri için Git [burada](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)  
  
- Yükleme [kodlanmış UI çapraz tarayıcı test etmek için Selenium bileşenlerini](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
  **Ne tüm web tarayıcıları destekleniyor mu?**  
  
- [Özellikleri denetlemek için özel kod ekleme](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) properties, search ve playback waiters gibi.  
  
- Açılır pencereler ve iletişim kutuları  
  
- [Dönüş türü olmadan temel JavaScript yürütme](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
- Arama (akıllı eşleşme kullanarak) esneklik ve [performans geliştirmeleri](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Birden çok web tarayıcı türleri arasında kodlanmış UI testleri neden kullanmalıyım?  
 Çeşitli web tarayıcı türleri kullanarak, web uygulamanızı test ederek, farklı tarayıcılar çalıştıran kullanıcıların kullanıcı arabirimi deneyimi daha iyi benzetirsiniz. Örneğin, uygulamanız diğer web tarayıcıları ile uyumlu olmayan Internet Explorer denetim veya kod içerebilir. Diğer tarayıcılar arasında kodlanmış UI testleri çalıştırarak, müşterilerinizi etkilemeden önce herhangi bir sorunu keşfedebilir ve düzeltebilirsiniz.  
  
## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Kodlanmış UI testleri desteklenen web tarayıcısı kullanarak web uygulamaları üzerinde nasıl kaydederim ve kayıttan yürütürüm?  
 **Kayıt:** Internet Explorer'ı kullanarak web uygulama testinizi kaydetmek için kodlanmış UI Test Oluşturucusu'nu kullanmanız gerekir. İsteğe bağlı olarak, doğrulama ve kodlanmış UI testleri için normalde yaptığınız gibi önceden tanımlanmış bir özellik kümesi kullanarak sınanmış denetimler için özel kod ekleyebilirsiniz. Daha fazla bilgi için [kullanım UI Otomasyon için Test kodunuzu](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  Google Chrome veya Mozilla Firefox tarayıcısı kullanarak kodlanmış UI testleri kaydedemezsiniz.  
  
 **Internet Explorer ile kayıttan yürütme:** hiçbir tarayıcı açıkça belirtilmediğinde testler varsayılan olarak Internet Explorer'da çalışır. Açıkça ayarlayarak kullanılacak tarayıcı durum **BrowserWindow.CurrentBrowser** özelliğini test kodunuzda. Internet Explorer için bu özelliği ayarlanmalıdır **IE** veya **Internet Explorer**.  
  
 **Geri Internet Explorer web tarayıcılarıyla çalma:** Internet Explorer web tarayıcılarında çalmak için BrowserWindow.CurrentBrowser özelliğini test kodunuzda ya da değiştirin **Firefox** veya **Chrome** .  
  
 Testleri IE olmayan web tarayıcılarında çalmak için yüklemelisiniz **kodlanmış UI çapraz tarayıcı test etmek için Selenium bileşenlerini**.  
  
#### <a name="installing-selenium-components"></a>Selenium bileşenlerini yükleme  
  
1. Üzerinde **Araçları** menüsünde seçin **Uzantılar ve güncelleştirmeler**.  
  
2. Uzantı ve güncelleştirmeler iletişim kutusunda arama `Selenium components for Cross Browser Testing`.  
  
3. Uzantısını vurgulayın ve seçin **indirme**.  
  
   > [!TIP]
   >  Kodlanmış UI çapraz tarayıcı test etmek için Selenium bileşenlerini indirebilirsiniz [burada](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
   Daha fazla bilgi oluşturma ve kullanarak kodlanmış UI testleri için bkz. [kodlanmış UI testleri](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
### <a name="enable-debugging"></a>Hata ayıklamayı etkinleştir  
 Web uygulamanızda hata ayıklamayı etkinleştirmek için aşağıdaki yapılandırma seçeneklerini tamamlamanız gerekir:  
  
1.  Yalnızca Kendi Kodumu Etkinleştir:  
  
    1.  Üzerinde **Araçları** menüsünde seçin **seçenekleri** seçip **hata ayıklama**.  
  
    2.  Seçin **yalnızca kendi kodumu etkinleştir**.  
  
2.  CLR özel durumları devre dışı bırakın:  
  
    1.  Üzerinde **hata ayıklama** menüsünde seçin **özel durumları**.  
  
    2.  İçin **ortak dil çalışma zamanı özel durumları**, onay kutusunu temizleyin **kullanıcı-işlenmemiş**.  
  
##  <a name="generate"></a> *Kodlanmış UI testi BrowserWindow.CurrentBrowser değiştirme seçeneği görmüyorum.*  
 Bir sürümünü kullanıyor olabilecek [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] çeşitli web tarayıcıları kullanarak kodlanmış UI testleri desteklemiyor. Bu tür kodlanmış UI testleri kullanmak için Visual Studio Enterprise'ı kullanmanız gerekir.  
  
 *Başka neleri bilmeliyim?*  
 **Notlar**  
  
- ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") Apple Safari web tarayıcısı desteklenmiyor.  
  
- ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") web tarayıcısını başlatma eylemini, kodlanmış UI testi parçası olmalıdır.  
  
   Internet Explorer kullanmadığınız sürece açık bir web tarayıcısına sahip ve adımlar üzerinde çalıştırmak istiyorsanız, kayıttan yürütme başarısız olur. Bu nedenle, web tarayıcınızı başlatması kodlanmış UI testleriniz bir parçası olarak dahil en iyi uygulamadır.  
  
- ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") belirli otomatikleştirme tarayıcı tabanlı UI eylemlerini gibi en üst düzeye çıkarmak, en aza indirmek ve geri yükleme desteklenmiyor.  
  
  **İpuçları**  
  
- ![İpucu](../test/media/tip.png "İpucu") çıktı kodlanmış UI günlüklerinde ekran görüntüleri içerecek şekilde yapılandırabilirsiniz. Bunu yapmak için bazı yapılandırma ayarlarını QTAgent32.exe.config dosyasında ayarlamanız gerekir. Varsayılan olarak, bu dosya aşağıdaki konuma yüklenir:  
  
   **C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE**  
  
   Aşağıdaki değerleri ayarlayın:  
  
  - `EqtTraceLevel` içinde `system.diagnostics` bölümü.  
  
  - `<add name="EqtTraceLevel" value="4" />`  
  
     3 veya daha yüksek bir değere ayarlayarak ekran görüntüleri her eylem için alınır. Değeri 1 veya 2'ye ayarlandığında, ekran görüntüleri yalnızca hata eylemleri alır.  
  
    Daha fazla bilgi için [çözümleme kodlanmış UI testleri kullanarak kodlanmış UI Test günlüklerini](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
### <a name="videos"></a>Videolar  
 [IE ve kayıttan çalma üzerinde her yerde kaydedin](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [Çapraz tarayıcı testleri kodlanmış UI Test Oluşturucusu ile yazar](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)  
  
 [Çapraz tarayıcı testleri UI eşlemesi düz el kodlama kullanarak Yazar](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)  
  
 [Çapraz tarayıcı sırayla birden çok tarayıcı üzerinde testler](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)  
  
 [Tarayıcı test hatalarını giderme](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)  
  
### <a name="guidance"></a>Kılavuz  
 [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Bölüm 5 – Visual Studio 2012 ile sürekli teslimat testi: Sistem testlerini otomatikleştirme](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>SSS  
 [Kodlanmış UI testleri SSS - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodlanmış UI testleri SSS -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio UI Otomasyon (kodlanmış UI içerir) test etme](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Kodlanmış UI Test Günlüklerini Kullanarak Kodlanmış UI Testlerini Çözümleme](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)



