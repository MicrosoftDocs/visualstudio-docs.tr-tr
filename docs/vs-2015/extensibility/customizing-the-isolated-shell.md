---
title: Yalıtılmış Kabuğu özelleştirme | Microsoft Docs
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
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097186ba43202c537bf8acbe0b47893151055c19
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733781"
---
# <a name="customizing-the-isolated-shell"></a>Yalıtılmış Kabuğu özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio kullanıcı arabirimini farklı yönlerini değiştirme ve özel uygulamanıza dahil olan özellikler ve komutları kısıtlayarak, Visual Studio yalıtılmış Kabuğu uygulamanızı özelleştirebilirsiniz.  
  
## <a name="using-the-applicationpkgdef-file"></a>Application.pkgdef dosyası kullanma  
 Yalıtılmış Kabuk şablonu çözümü içeren bir *SolutionName*. Aşağıdaki özellikleri değiştirmenize olanak tanıyan Application.pkgdef dosyası:  
  
##### <a name="the-application-title"></a>Uygulama Başlığı  
 "AppName" satırın değerini değiştirerek uygulama başlık çubuğunda görüntülenen addır uygulama başlığı özelleştirebilirsiniz *SolutionName*. Application.pkgdef dosyası. Daha fazla ayrıntı için [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Şu anda yüklü olan projenin görüntülenecek uygulama başlığı istemiyorsanız "ShowHierarchyRootInTitle" satırın değerini değiştirmek *SolutionName*. DWORD: 00000001 dosyasından Application.pkgdef DWORD: 00000000 için.  
  
##### <a name="the-application-icon"></a>Uygulama simgesi  
 Uygulama adı uygulama başlık çubuğunda görüntülenen simge uygulama simgesine özelleştirebilirsiniz. Farklı bir simgeye simgesi dizinine kopyalayın. İçinde **Çözüm Gezgini**, kaynak dosyaları klasöre simgesi ekleyin. Ardından VSShellStub.rc dosyasını açın ve IDI_STUBPROGRAM yeni simgesine adıyla değiştirin. Daha fazla ayrıntı için [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Komut satırı logosu  
 Uygulama "CommandLineLogo" satırın değerini değiştirerek komut satırından başlatıldığında görüntülenen metni komut satırı logosu, özelleştirebileceğiniz *SolutionName*. Application.pkgdef dosyası. Daha fazla ayrıntı için [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Kullanıcı dosyaları alt klasör adı  
 Uygulamanız için kullanıcı dosyaları "UserFilesSubFolderName" satırın değerini değiştirerek tutar klasörün adını değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Yeni Proje iletişim kutusunda çözüm Ağaç düğümünün başlığı  
 Yeni Proje iletişim kutusunda çözüm düğümüne başlığı "NewProjDlgSlnTreeNodeTitle" satırın değerini değiştirerek özelleştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Yüklü Şablonlar üst bilgisinde yeni proje iletişim kutusu  
 Yüklü Şablonlar üst bilgisinde yeni proje iletişim kutusu "NewProjDlgInstalledTemplatesHdr" satırın değerini değiştirerek değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Çeşitli dosyalar varsayılan olarak gizle gerekip gerekmediğini  
 Çeşitli dosyalar varsayılan olarak "HideMiscellaneousFilesByDefault" satırın değerini değiştirerek Gizle gerekip gerekmediğini belirtin *SolutionName*. Application.pkgdef dosyası. Çeşitli dosyalar gizlemek için değer ayarlama `dword:00000001`ve dosyaları göstermek için değeri ayarlayın `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Çıkış penceresi devre dışı gerekip gerekmediğini  
 "DisableOutputWindow" satırın değerini değiştirerek, uygulamanızın çıkış penceresinde devre dışı gerekip gerekmediğini belirtin *SolutionName*. Application.pkgdef dosyası. Çıkış penceresi devre dışı bırakmak için değer ayarlama `dword:00000001`ve çıktı penceresini görüntülemek için değeri ayarlayın `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Ana penceredeki bırakılan dosyaları izin verilip verilmeyeceğini  
 "AllowsDroppedFilesOnMainWindow" satırın değerini değiştirerek uygulamanızdaki ana penceredeki bırakılan dosyaları izin verilip verilmeyeceğini belirtebilirsiniz *SolutionName*. Application.pkgdef dosyası. Bırakılan dosyaları izin vermek için değeri ayarlayın `dword:00000001`ve bırakılan dosyaları izin vermeyecek şekilde değeri ayarlayın `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Varsayılan arama sayfası  
 Web tarayıcısı penceresi açıldığında, "DefaultSearchPage" satırın değerini değiştirerek, görüntülenen sayfadır web tarayıcı sayfası özelleştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="the-default-home-page"></a>Varsayılan giriş sayfası  
 Giriş sayfasında "DefaultHomePage" satırın değerini değiştirerek özelleştirebilirsiniz *SolutionName*. Application.pkgdef dosyası. Daha fazla ayrıntı için [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Çözüm kavramı Gizle gerekip gerekmediğini  
 "HideSolutionConcept" satırın değerini değiştirerek uygulamanızdaki çözüm Gizle gerekip gerekmediğini belirtin *SolutionName*. Application.pkgdef dosyası. Çözüm gizlemek için değer ayarlama `dword:00000001`ve çözüm göstermek için değeri ayarlayın `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Varsayılan hata ayıklama altyapısı  
 Hata ayıklama altyapısı uygulamanızın kullandığı "DefaultDebugEngine" satırın değerini değiştirerek değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyasına, hata ayıklama altyapısı GUİD'si.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Kullanıcı seçenekleri dosyası dosya uzantısı  
 Uygulamanız için kullanıcı dosyaları "UserOptsFileExt" satırın değerini değiştirerek tutar klasörün adını değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="the-solution-file-extension"></a>Çözüm dosya uzantısı  
 "SolutionFileExt" satırın değerini değiştirerek, çözüm dosyaları için kullanılan uzantısı değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="the-default-user-files-folder-root"></a>Varsayılan kullanıcı dosyaları klasörünü kök  
 Uygulamanız için kullanıcı dosyaları kök klasörü adı "UserFilesSubFolderName" satırın değerini değiştirerek değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="the-solution-file-creator-identifier"></a>Çözüm dosyası oluşturan tanımlayıcısı  
 "SolutionFileCreatorIdentifier" satırın değerini değiştirerek, çözüm dosyaları için kullanılan tanımlayıcı değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="the-default-projects-location"></a>Varsayılan proje konumu  
 Varsayılan proje konumu adını "DefaultProjectsLocation" satırın değerini değiştirerek değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="the-application-localization-package"></a>Uygulama yerelleştirme paketi  
 "AppLocalizationPackage" satırın değerini değiştirerek, uygulamanız için kullanılan yerelleştirme paketi değiştirebilirsiniz *SolutionName*. Application.pkgdef dosyası.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Hiyerarşi kök başlığında gösterilip gösterilmeyeceğini  
 "ShowHierarchyRootInTitle" satırın değerini değiştirerek uygulamanızdaki başlık çubuğundaki hiyerarşi kök gösterilip gösterilmeyeceğini belirtin *SolutionName*. Application.pkgdef dosyası. Hiyerarşi kök göstermek için değer ayarlama `dword:00000001`ve hiyerarşi kök gizlemek için değeri ayarlayın `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Başlangıç sayfasını belirtme  
 Özel uygulamanız için bir başlangıç sayfasını belirtmek için *SolutionName*. Application.pkgdef dosya ayarlanmış "DisableStartPage" değeri `dword:00000000`, altında `[$RootKey$\StartPage\Default]` URI ait .xaml dosyası konumunu ayarlayın:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct dosyasında *SolutionName*UI proje, açıklama "No_ShellPkg_startPageCommand" giriş satırı:  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Ait .xaml dosyası ve ihtiyacınız kadar tüm grafik dosyaları eklemelisiniz *SolutionName* proje. Bu dosyalar için gerçekten kopyalanmalıdır *SolutionName* proje dizini, diğer bazı dizinden eklenmedi.  
  
 Tüm dosyalar üzerinde ayarlayın **öğesi türü** özelliğini **yalıtılmış Kabuk Dosya** kopyalanacağı dosyaların sırayla *$RootFolder$* dizin. (Ayarlanacak **öğesi türü** özelliği, dosyaya sağ tıklayın ve seçin **özellikleri**. Bu özellik altında bulunan **yapılandırma özellikleri**, **genel**.)  
  
 Başlangıç sayfalarını özelleştirme hakkında daha fazla bilgi için bkz. [başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Yalıtılmış Kabuğu diğer öğelerini kullanma  
 Diğer dosyalar ve uygulamanızı daha fazla özelleştirmek için yalıtılmış Kabuk çözüm şablonunda yer projeleri kullanabilirsiniz.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Visual Studio paketleri etkinleştir/devre dışı bırak  
 *SolutionName*.pkgundef dosyası, bazı paketlerden hariç tutarak, belirli türde bir Visual Studio işlevselliği devre dışı bırakmak olanak sağlar. Örneğin, aşağıdaki satırı:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Çeşitli dosyalar projeleri görüntülenen proje şablonları kümesini kaldırır. **yeni proje** iletişim. Daha fazla ayrıntı için [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Menü komutlarını etkinleştir/devre dışı bırak  
 *SolutionName*UI.vsct dosyası derleme dışı bırakılan listesini yalıtılmış kabuğu için kullanılabilir tüm menü komutlarını içerir. Belirli bir komut devre dışı bırakmak için karşılık gelen satırı açıklamadan çıkarın. Örneğin, pencere/bölünmüş açıklama devre dışı bırakmak için açıklama durumundan çıkarın `<Define name="No_SplitCommand"/>` satır. Daha fazla ayrıntı için [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Karşılama ekranında kullanılan bit eşlem  
 Uygulama başlatıldığında "SplashScreenBitmap" satırın değerini değiştirerek, görüntülenen pencere Karşılama ekranında kullanılan bit eşlem özelleştirebilirsiniz *SolutionName*. Application.pkgdef dosyası. Daha fazla ayrıntı için [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Yardım/penceresi hakkında  
 Yalıtılmış Kabuk şablonda Yardım'ı özelleştirmek için kullanabileceğiniz ayrı bir proje yok/hakkında kutusu uygulamanız için. Daha fazla ayrıntı için [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).

