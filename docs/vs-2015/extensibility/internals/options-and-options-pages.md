---
title: Seçenekler ve Seçenekler sayfaları | Microsoft Docs
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
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 005aeceb328a24c8c90994b6b274dbddc6b874f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783285"
---
# <a name="options-and-options-pages"></a>Seçenekler ve Seçenekler Sayfaları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tıklayarak **seçenekleri** üzerinde **Araçları** menüsü açılır **seçenekleri** iletişim kutusu. Bu iletişim kutusundaki seçenekleri topluca seçenekler sayfaları adlandırılır. Gezinti bölmesindeki ağaç denetimi seçenekleri kategorileri içerir ve her kategori Seçenekleri sayfası vardır. Bir sayfa seçtiğinizde, buna ilişkin seçenekler sağ bölmede görünür. Bu sayfalar VSPackage durumunu belirleyen seçenekleri değerlerini değiştirmenize olanak sağlar.  
  
## <a name="support-for-options-pages"></a>Seçenekler sayfaları için destek  
 <xref:Microsoft.VisualStudio.Shell.Package> Sınıfı seçenekler sayfaları ve seçenekleri kategoriler oluşturmak için destek sağlar. <xref:Microsoft.VisualStudio.Shell.DialogPage> Sınıfı bir seçenekler sayfası uygular.  
  
 Varsayılan uygulaması <xref:Microsoft.VisualStudio.Shell.DialogPage> özelliklerinin genel kılavuz kullanıcıya genel özelliklerini sunar. Sayfasında, kendi kullanıcı arabirimini (UI) sahip bir özel seçenekler sayfası oluşturmak için çeşitli yöntemler geçersiz kılarak bu davranışı özelleştirebilirsiniz. Daha fazla bilgi için [seçenekler sayfası oluşturma](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Sınıfının Implements <xref:Microsoft.VisualStudio.Shell.IProfileManager>, Seçenekler sayfaları için ve ayrıca kullanıcı ayarlarını kalıcı sağlar. Varsayılan uygulamaları <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> ve <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> yöntemleri kalıcı bir kayıt defteri kullanıcı bölümünü özellik değişiklikleri özelliği için ve bir dizeden dönüştürülebilir ise.  
  
## <a name="options-page-registry-path"></a>Seçenekler sayfası kayıt defteri yolu  
 Varsayılan olarak, bir seçenekler sayfası tarafından yönetilen özelliklerin kayıt defteri yolu birleştirerek belirlenir <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word DialogPage ve Seçenekler sayfası sınıfı türü adı. Örneğin, bir seçenekler sayfası sınıfı şu şekilde tanımlanabilir.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Varsa <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, eğer özellik ad ve değer çiftlerini HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ anahtarlarını olduğu Company.OptionsPage.OptionsPageGeneral.  
  
 Seçenekler sayfası, kayıt defteri yolu birleştirerek belirlenir <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, word ve ToolsOptionsPages seçenekleri sayfasında kategori ve adı. Örneğin, özel seçenekler sayfası kategori seçeneği Sayfalarım, varsa ve <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> seçenekleri sayfasında HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ kayıt defteri anahtarı varsa, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp olduğu VisualStudio\8.0Exp\ToolsOptionsPages\My seçeneği Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Araçlar/Seçenekler sayfası öznitelikleri ve düzeni  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Öznitelik kategorileri Gezinti ağacında özel seçenekler sayfası gruplandırmayı belirler **seçenekleri** iletişim kutusu. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Özniteliği bir seçenekler sayfası arabirimi sağlayan VSPackage ile ilişkilendirir. Aşağıdaki kod parçasını göz önünde bulundurun:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Bu iki seçenekler sayfaları, OptionsPageGeneral ve OptionsPageCustom MyPackage sağladığını bildirir. İçinde **seçenekleri** hem seçenekler sayfaları iletişim kutusu görünür **seçeneği Sayfalarım** kategori olarak **genel** ve **özel**sırasıyla.  
  
## <a name="option-attributes-and-layout"></a>Seçenek öznitelikleri ve düzeni  
 Sayfa sağlayan kullanıcı arabirimi (UI) özel seçenekler sayfası seçeneklerinde görünümünü belirler. Düzen, etiketleme ve genel seçenekler sayfası seçeneklerinin açıklaması aşağıdaki özniteliklere göre belirlenir:  
  
- <xref:System.ComponentModel.CategoryAttribute> seçeneği kategorisini belirler.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> seçenek görünen adını belirler.  
  
- <xref:System.ComponentModel.DescriptionAttribute> seçenek tanımı belirler.  
  
  > [!NOTE]
  >  Eşdeğer öznitelikleri, SRCategory LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanın ve tanımlanan [yönetilen proje örnek](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Aşağıdaki kod parçasını göz önünde bulundurun:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  Seçenekler sayfasında OptionInteger seçeneği görüntülenir **tamsayı seçeneği** içinde **My seçenekleri** kategorisi. Seçeneğini belirlediyseniz, açıklama **benim tamsayı seçeneğini**, Açıklama kutusuna görünür.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Başka bir VSPackage erişen seçenekler sayfaları  
 Barındırdığı ve yönettiği bir seçenekler sayfası bir VSPackage Otomasyon modelini kullanarak, başka bir VSPackage'ı programlı olarak erişilebilir. Örneğin, aşağıdaki kodda bir VSPackage'ı bir seçenek sayfasını barındıran olarak kaydedilir.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Aşağıdaki kod parçası, MyOptionPage OptionInteger değerini alır:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Zaman <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> öznitelik kayıtları bir seçenekler sayfası, sayfayı AutomationProperties anahtar ise altında kayıtlı `SupportsAutomation` özniteliğin bağımsız değişkeni `true`. Otomasyon ilişkili VSPackage'ı ve Otomasyon bulmak için bu kayıt defteri girdisi inceler, ardından barındırılan seçenekler sayfası, bu durumda, kılavuz sayfam özelliğine erişir.  
  
 Otomasyon özelliği, kayıt defteri yolu birleştirerek belirlenir <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, word, AutomationProperties ve seçenekleri sayfasında kategori ve adı. Örneğin, Seçenekler sayfasında My kategorisi kategori, kılavuz sayfam adı varsa ve <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp ve Otomasyon özelliği HKEY_LOCAL_MACHINE\SOFTWARE\ kayıt defteri anahtarı var Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My kılavuz sayfası.  
  
> [!NOTE]
>  Kurallı ad, My Category.My kılavuz sayfası, bu anahtarın adı alt değeridir.

