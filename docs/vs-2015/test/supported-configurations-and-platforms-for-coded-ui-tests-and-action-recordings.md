---
title: Desteklenen yapılandırmalar ve platformlar için kodlanmış UI testlerini ve Eylem kayıtlarını | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests
ms.assetid: 544742b5-4ec1-4d51-b941-72b2f6ff17bc
caps.latest.revision: 108
ms.author: gewarren
manager: douge
ms.openlocfilehash: 23c1c84180df7fd185ce29d265f89c6b905ff794
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198776"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Desteklenen yapılandırmalar ve platformlar için kodlanmış UI testleri için Visual Studio Enterprise aşağıdaki tabloda listelenmiştir. Bu yapılandırmalar kullanılarak oluşturulan eylem kayıtları için de geçerlidir. [!INCLUDE[MTRlong](../includes/mtrlong-md.md)].  
  
> [!NOTE]
>  Kodlanmış kullanıcı arabirimi test işlemi, test altındaki uygulama ile aynı ayrıcalıklara sahip olmalıdır.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
## <a name="supported-configurations"></a>Desteklenen Yapılandırmalar  
  
|Yapılandırma|Desteklenir|  
|-------------------|---------------|  
|İşletim Sistemleri|[!INCLUDE[win7](../includes/win7-md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]<br /><br /> [!INCLUDE[win8](../includes/win8-md.md)]<br /><br /> Windows 10|  
|32 bit / 64 bit Desteği|32 bit çalıştıran 32 bit Windows [!INCLUDE[TCMext](../includes/tcmext-md.md)] 32-bit uygulamaları test edebilir.<br /><br /> 32 bit çalıştıran 64 bit Windows [!INCLUDE[TCMext](../includes/tcmext-md.md)] , UI Eşitlemesi olan 32 bit WOW Uygulamalarını test edebilir.<br /><br /> 32 bit çalıştıran 64 bit Windows [!INCLUDE[TCMext](../includes/tcmext-md.md)] 64 bit Windows Forms ve WPF uygulamaları, UI Eşitlemesi olmayan test edebilirsiniz.|  
|Mimari|x86 ve x64 **Not:** Internet Explorer çalışması dışında 64 bit modunda desteklenmez [!INCLUDE[win8](../includes/win8-md.md)] veya sonraki sürümler.|  
|.NET|.NET 2.0, 3.0, 3.5, 4 ve 4.5. **Not:** [!INCLUDE[TCMext](../includes/tcmext-md.md)] ve Visual Studio her ikisinin çalışması .NET 4. Ancak, listelenen .NET sürümleri kullanılarak geliştirilen uygulamalar desteklenir.|  
  
> [!NOTE]
>  *UI Eşitlemesi* kayıttan yürütme her denetimin ileti kuyrukta doğrulanan burada bir özelliktir. Bir denetim kendisine gönderilen olaya yanıt vermiyorsa, olay yeniden gönderilir.  
  
## <a name="platform-support"></a>Platform Desteği  
  
|Platform|Destek Düzeyi|  
|--------------|----------------------|  
|Windows Phone uygulamaları|Yalnızca WinRT XAML uygulamaları desteklenen telefonla.|  
|Windows Mağazası Uygulamaları|Yalnızca XAML tabanlı Mağaza uygulamaları desteklenir.|  
|Evrensel Windows Uygulamaları|Yalnızca XAML tabanlı Evrensel Windows uygulamaları telefon ve Masaüstü desteklenir.|  
|Kenar|Visual Studio 2015 güncelleştirme 2 ve daha sonra kullanarak [Coded UI Cross Browser Testing uzantısı](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)|  
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **önemli:** Internet Explorer 10 yalnızca masaüstünde desteklenir. <br /><br /> Internet Explorer 11 **önemli:** Internet Explorer 11 yalnızca masaüstünde desteklenir.|Tam olarak desteklendi.<br /><br /> -   **Internet Explorer 9 ve Internet Explorer 10 HTML5 desteği:** kodlanmış UI testleri HTML5 denetimlerinin doğrulama kaydı ve kayıttan yürütme destekler: ses, Video, ProgressBar ve kaydırıcı. Daha fazla bilgi için [kodlanmış UI testlerinde HTML5 denetimleri kullanma](../test/using-html5-controls-in-coded-ui-tests.md). **Uyarı:** kodlanmış oluşturursanız, Internet Explorer 10 kullanıcı Arabirimi testleri, çalıştırılamıyor Internet Explorer 9 veya Internet Explorer 8 kullanarak. Bunun nedeni Internet Explorer 10'un Ses, Video, İlerleme Çubuğu ve Kaydırma gibi HTML5 denetimlerini içermesidir. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.<br />-   **Internet Explorer 10 yazım denetimi desteği:** Internet Explorer 10 yazım, tüm metin kutuları için özellikleri içerir. Bu, önerilen düzeltmeler listesinden seçim yapmanızı sağlar. Kodlanmış UI Testi, alternatif yazım önerisi seçmek gibi kullanıcı eylemlerini yoksayar. Yalnızca metin kutusuna yazılan son metin kaydedilir.<br />     Yazım denetimini kullanan kodlanmış kullanıcı arabirimi testi için şu eylemler kaydedilir: Sözlüğe Ekle, Kopyala, Tümünü Seç, Sözlüğe Ekle ve Yoksay.<br />-   **Windows 8 altında çalışan 64-bit Internet Explorer desteği:** daha önce Internet Explorer'ın 64-bit sürümleri kayıt ve kayıttan yürütme için desteklenen değil. İle [!INCLUDE[win8](../includes/win8-md.md)] ve [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], kodlanmış UI testleri, Internet Explorer'ın 64-bit sürümleri için etkinleştirilmiştir. **Uyarı:** 64-bit Internet Explorer desteği yalnızca çalıştırılıyorsa uygulanır [!INCLUDE[win8](../includes/win8-md.md)] veya üzeri.<br />-   **Internet Explorer 9 iliştirilmiş siteler desteği:** Internet Explorer 9'da, iliştirilmiş siteler tanıtıldı. İliştirilmiş Sitelerle, sevdiğiniz sitelere önce Internet Explorer'ı açmak zorunda kalmadan doğrudan Windows görev çubuğundan ulaşabilirsiniz. Kodlanmış UI testleri iliştirilmiş sitelerde amaç duyarlı eylemler oluşturabilir. Sabitlenmiş siteler hakkında daha fazla bilgi için bkz. [iliştirilmiş siteler](http://go.microsoft.com/fwlink/?LinkId=220037).<br />-   **Internet Explorer 9 anlamsal etiketler desteği:** Internet Explorer 9, aşağıdaki anlamsal etiketleri sunmuştur: bölüm, nav, makale, aside, hgroup, üstbilgi, altbilgi, şekil, figcaption ve mark. Kodlanmış UI testleri kaydedilirken bu anlamsal etiketlerin tamamını yoksayar. Kodlanmış UI Test Oluşturucusu kullanarak bu etiketlere onaylama ekleyebilirsiniz. Bu öğelerin herhangi birine gidip özelliklerini görüntülemek için kodlandırılmış UI Test Oluşturucusu'nda gezinti aramayı kullanabilirsiniz.<br />-   **Sorunsuz işleme beyaz boşluk karakterlerin Internet Explorer sürümleri arasında:** Internet Explorer 8, Internet Explorer 9 ve Internet Explorer 10 arasında beyaz boşluk karakterleri işleme farklılıkları vardır. Kodlanmış UI Testi bu farklılıkları sorunsuz bir şekilde işler. Dolayısıyla, örneğin, Internet Explorer 8'de oluşturulmuş bir kodlanmış UI testinin kayıttan oynatılması Internet Explorer 9 ve Internet Explorer 10'da başarıyla yapılabilir.<br />-   **Bildirim alanında, Internet Explorer olan artık kümesiyle kaydedilir "Continue on Error" özniteliği ayarlayın:** Internet Explorer'ın bildirim alanı'ndaki tüm işlemler şimdi "Continue on Error" öznitelik kümesiyle kaydedilir. Kayıttan yürütme sırasında bildirim çubuğu görünmüyorsa, eylemleri yoksayılır ve kodlanmış UI testi sonraki eylem ile devam eder.|  
|Windows Forms ve WPF üçüncü taraf denetimleri|Tam olarak desteklendi.<br /><br /> Windows Formlar ve WPF uygulamalarında üçüncü taraf denetimleri etkinleştirmek için başvurular ve kod eklemeniz gerekir. Daha fazla bilgi için [etkinleştirme kodlanmış UI Testing of Your Controls](../test/enable-coded-ui-testing-of-your-controls.md).|  
|Internet Explorer 6<br /><br /> Internet Explorer 7|Desteklenmez.|  
|Chrome<br /><br /> Firefox|Eylem adımlarını kaydetme desteklenmiyor. Kodlanmış UI Testleri Chrome ve Firefox tarayıcılarda Visual Studio 2012 Update 4 veya sonraki sürümüyle kayıttan yürütülebilir. Git [burada](http://msdn.microsoft.com/library/jj835758.aspx) daha fazla ayrıntı için.|  
|Opera<br /><br /> Safari|Desteklenmez.|  
|Silverlight|Desteklenmez.<br /><br /> Visual Studo 2013 için ancak indirebileceğiniz [Microsoft Visual Studio 2013 kodlanmış UI Test eklentisi için Silverlight](https://go.microsoft.com/fwlink/?LinkId=691026) Visual Studio Galerisi.|  
|Flash/Java|Desteklenmez.|  
|Windows Forms 2.0 ve ileri sürümü|Tam olarak desteklendi. **Not:** NetFx denetimleri tam olarak desteklenir, ancak tüm üçüncü taraf denetimleri desteklenmez.|  
|WPF 3.5 ve ileri sürümü|Tam olarak desteklendi.<br /><br /> **Not** NetFx denetimleri tam olarak desteklenir, ancak tüm üçüncü taraf denetimleri desteklenmez.|  
|Windows Win32|Bazı bilinen sorunlar ile çalışabilir, ancak resmi olarak desteklenmez.|  
|MFC|Kısmen desteklenir. Şu [Microsoft Web sitesi](http://go.microsoft.com/fwlink/?LinkId=206511) hangi özelliklerin desteklendiğine dair Ayrıntılar için.|  
|SharePoint|Tam olarak desteklendi.|  
|Office İstemci Uygulamaları|Desteklenmez.|  
|Dynamics CRM web istemcisi|Tam olarak desteklendi.|  
|Dynamics (Ax) 2012 işlemcisi|Eylem kaydı ve kayıttan yürütme kısmen desteklenir. Şu [Microsoft Web sitesi](http://go.microsoft.com/fwlink/?LinkId=232677) Ayrıntılar için.|  
|SAP|Desteklenmez.|  
|Citrix/Terminal Hizmetleri|Terminal sunucusu üzerinde işlemleri kaydetmeye önerilmemektedir. Kaydedici, aynı anda birden fazla çalışan desteklemiyor.|  
|PowerBuilder|Kısmen desteklenir.<br /><br /> Desteğin kapsamı, PowerBuilder denetimleri için erişilebilirliğin etkin olduğu kadardır.|  
  
 Diğer platformları destekleyecek uzantılar oluşturma konusunda daha fazla bilgi için bkz: [etkinleştirme kodlanmış UI Testing of Your Controls](../test/enable-coded-ui-testing-of-your-controls.md) ve [genişletme kodlanmış UI testleri ve Eylem kayıtlarını Microsoft Excel'i desteklemek için](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Mevcut eylem kaydından bir kodlanmış UI testi oluşturma](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)



