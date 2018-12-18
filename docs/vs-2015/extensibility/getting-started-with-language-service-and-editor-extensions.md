---
title: Dil hizmeti ve düzenleyici uzantılarıyla çalışmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09056d184256e2d62387af08c61186c6ff57c02
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735205"
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Dil Hizmeti ve Düzenleyici Uzantılarıyla Çalışmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programlama diliniz veya herhangi bir içerik türü için anahat oluşturma, ayraç eşleştirme, IntelliSense ve ampuller gibi dil hizmeti özellikleri eklemek için düzenleyici Uzantıları'nı kullanabilirsiniz. Ayrıca, Visual Studio Düzenleyicisi, Örneğin Renklendirme, kenar boşlukları, kenarlıklar ve diğer görsel öğelere metin davranışını ve görünümünü özelleştirebilirsiniz. Ayrıca, kendi içerik türünü tanımlayın ve görünümünü ve davranışını içeriğinizi göründüğü metin görünümlerinin belirtin.  
  
 Düzenleyici uzantıları yazmaya başlamak için Visual Studio SDK'ın bir parçası olarak yüklenen Düzenleyici proje şablonlarını kullanın. Visual Studio SDK VSPackage'ları kullanarak ya da Yönetilen Genişletilebilirlik Çerçevesi (MEF) kullanarak Visual Studio uzantıları, geliştirme kolaylaştıran Araçlar indirilebilir bir kümesidir.  
  
> [!NOTE]
>  Visual Studio SDK'sı hakkında daha fazla bilgi için bkz. [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Kendi Düzenleyici uzantıları yazmadan önce aşağıdaki kavramları ve teknolojileri hakkında bilgi öneririz.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) ve düzenleyici uzantılarıyla  
 Windows Presentation Foundation (WPF) kullanarak Visual Studio Düzenleyicisi kullanıcı arabirimi (UI) uygulanır. WPF, zengin bir görsel deneyimi ve iş mantığından kod visual yönlerini ayıran tutarlı bir programlama modeli sağlar. Düzenleyici uzantıları oluşturduğunuzda, birçok WPF öğeleri ve özellikleri kullanabilirsiniz. Daha fazla bilgi için [Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) ve düzenleyici uzantılarıyla  
 Visual Studio Düzenleyicisi, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşenleri ve uzantıları yönetmek için kullanır. MEF, ayrıca geliştiricilerin daha fazla uzantıları Visual Studio gibi bir ana bilgisayar uygulaması için kolayca oluşturmanıza olanak tanır. Bu çerçeve, MEF sözleşmesi göre bir uzantı tanımlayın ve MEF Bileşeni parçası olarak dışarı aktarın. Ana bilgisayar uygulaması bileşen parçalarına bunları bulma, bunları kaydetme ve doğru bağlamına uygulanan sağlamaktan yönetir.  
  
> [!NOTE]
>  MEF Düzenleyicisi'nde hakkında daha fazla bilgi için bkz: [düzenleyicide Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio Düzenleyici uzantı noktaları ve uzantıları  
 Düzenleyici uzantı noktaları, özelleştirme ve genişletme MEF Bileşeni bölümleri şunlardır. Bazı durumlarda bir arabirim uygulama ve doğru meta verilerle birlikte dışarı uzantı noktası genişletin. Diğer durumlarda, yalnızca bir uzantı bildirme ve belirli bir tür olarak verme.  
  
 Düzenleyici uzantıları temel tür bazıları şunlardır:  
  
- Kenar boşlukları ve kaydırma çubukları  
  
- Etiketler  
  
- Kenarlıklar  
  
- Seçenekler  
  
- IntelliSense  
  
  Düzenleyici uzantı noktaları hakkında daha fazla bilgi için bkz: [dil hizmeti ve düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Düzenleyici uzantıları dağıtma  
 Visual Studio'da çözüme çözümü source.extension.vsixmanifest adlı bir meta veri dosyası ekleyerek ve ardından ikili dosyaları ve bildirimi bir kopyasını bilinen bir klasörde Visual Studio'ya ekleme Düzenleyici uzantılarını dağıtın. Bildirim dosyası, uzantıyı (örneğin, adı, yazar, sürüm ve içerik türünü) hakkındaki temel gerçekleri tanımlar. VSIX bildirim dosyası ve uzantılarını dağıtma hakkında daha fazla bilgi için bkz. [sevkiyat Visual Studio uzantıları](../extensibility/shipping-visual-studio-extensions.md).  
  
 Uzantı bir bilgisayara yüklediğinizde, ikili dosyaları ve bildirim Visual Studio için bilinen bir klasörün bir alt klasör içerir.  
  
> [!WARNING]
>  Visual Studio'daki Düzenleyici genişletilebilirlik şablonlardan birini kullanırsanız, bildirimleri ve dağıtım konumuyla ilgili ayrıntıları endişelenmeniz gerekmez. Şablonları kaydolun ve bir uzantısını dağıtmak için gereken her şeyi içerir.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Deneysel örneğinde çalışan uzantıları  
 Aşağıdaki Deneysel klasöründe (Windows Vista ve Windows 7) dağıtarak bir uzantı geliştirirken çalışma sürümünüz, Visual Studio'nun verenlerden:  
  
 *% LOCALAPPDATA %* \VisualStudio\10.0Exp\Extensions\\*şirket*\\*Extensionıd*  
  
 Burada *% LOCALAPPDATA %* oturum açan kullanıcı adı *şirket* uzantısına sahip bir şirket adı ve *Extensionıd* uzantı kimliğidir.  
  
 Uzantı Deneysel bir konuma dağıttığınızda, hata ayıklama modunda çalıştırır. Visual Studio ikinci bir örneğini başlatılır ve adlı **Microsoft Visual Studio - Deneysel örnek**.  
  
## <a name="managing-extensions"></a>Uzantıları yönetme  
 Visual Studio uzantılarını listelenir **Uzantılar ve güncelleştirmeler** (üzerinde **Araçları** menü). Bir uzantıyı deneysel örneğinde test ediyorsanız, listelenen **Uzantılar ve güncelleştirmeler** deneysel örneğinde geliştirme örneğinde listelenmez, ancak.  
  
 Daha fazla bilgi için [bulma ve Visual Studio uzantılarını kullanarak](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Düzenleyici uzantıları oluşturmak için şablonları kullanma  
 Düzenleyici şablonları sınıflandırıcılar, kenarlıklar ve kenar boşlukları özelleştirme MEF uzantıları oluşturmak için kullanabilirsiniz. Hem C# ve Visual Basic projeleri için şablonlar vardır. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 VSIX proje şablonu, uzantıları oluşturmak için de kullanabilirsiniz. Bu şablonu herhangi bir türden uzantısı dağıtıp source.extension.vsixmanifest dosyasının, gerekli derleme başvurularını ve dağıtmanıza olanak tanıyan bir derleme görevleri içeren bir proje dosyası için gereken öğeleri sağlar. uzantı. Daha fazla bilgi için [VSIX proje şablonu](../extensibility/vsix-project-template.md).  
  
 Visual Studio Paket uzantısından MEF Bileşenleri Düzenleyicisi de oluşturabilirsiniz. Ayrıntılar için aşağıdaki izlenecek yollara bakın:  
  
-   [İzlenecek Yol: Düzenleyici Uzantısı ile Kabuk Komutu Kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [İzlenecek Yol: Düzenleyici Uzantısı ile Kısayol Tuşu Kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)

