---
title: Proje ve yapılandırma özellikleri için destek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 783c73cc73da188ec1be626cf54db93ca62af465
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865108"
---
# <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
**Özellikleri** penceresinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE) proje ve yapılandırma özelliklerini görüntüleyebilirsiniz. Kullanıcı, uygulamanın özelliklerini ayarlayabilirsiniz böylece, kendi proje türü için özellik sayfası sağlayabilirsiniz.  
  
 İçinde bir proje düğümü seçerek **Çözüm Gezgini** tıklayıp **özellikleri** üzerinde **proje** menüsünde, yapılandırma içeren bir iletişim kutusunu açabilirsiniz özellikleri. İçinde [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]ve proje sekmeli sayfa bu iletişim kutusu açılır, bu dillerden türetilmiş türleri [genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md). Daha fazla bilgi için [derleme içinde değil: izlenecek yol: Proje oluşturma ve yapılandırma özellikleri (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Projeleri (MPFProj) için yönetilen paket çerçevesini oluşturmak ve yeni proje sistemi yönetmek için yardımcı sınıflar sağlar. Kaynak kod ve derleme yönergelerini bulabilirsiniz [projeler - Visual Studio 2013 için MPF](https://github.com/tunnelvisionlabs/MPFProj10).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Yapılandırma özellikleri ve proje kalıcılığı  
 Yapılandırma özellikleri, örneğin proje türüyle ilişkili dosya adı uzantısı, .csproj, .vbproj ve .myproj sahip bir proje dosyasında kalır. Dil projeleri genellikle proje dosyası oluşturmak için bir şablon dosyası kullanın. Ancak, gerçekte proje türleri ve şablonları ilişkilendirmek için çeşitli yollar vardır. Daha fazla bilgi için [şablon dizin açıklaması (. Vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Yapılandırma özellikleri, şablon dosyasına öğeleri ekleyerek oluşturulur. Bu özellikler, ardından bu şablonu kullanan proje türü kullanılarak oluşturulan projeler için kullanılabilir. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projeler ve ikisi de MPFProj [derleme içinde değil: MSBuild'e genel bakış](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) şablon dosyaları için şema. Bu dosyalar her yapılandırma için bir PropertyGroup bölüm içerir. Proje Özellikleri bölümünde bir yapılandırma bağımsız değişken boş bir dize olarak ayarlanmış olan ilk PropertyGroup genellikle kalıcıdır.  
  
 Aşağıdaki kod, temel bir MSBuild proje dosyası başlangıcını gösterir.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 Bu proje dosyasında `<Name>` ve `<SchemaVersion>` proje özellikleri ve `<Optimize>` bir yapılandırma özelliğidir.  
  
 Proje dosyası proje ve yapılandırma özelliklerini kalıcı hale getirmek için projenin sorumluluğundadır.  
  
> [!NOTE]
>  Bir proje kalıcılığı, varsayılan değerleri farklı kalıcı tek özellik değerleri ile en iyi duruma getirebilirsiniz.  
  
## <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek  
 `Microsoft.VisualStudio.Package.SettingsPage` Yapılandırma özellik sayfaları sınıfı uygular. Varsayılan uygulaması `SettingsPage` genel özellik kılavuzunda kullanıcıya ortak özellikler sunar. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Yöntemini seçerse öğelerinden türetilen sınıfları `SettingsPage` proje özellik kılavuzları için. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Yöntemini seçerse öğelerinden türetilen sınıfları `SettingsPage` yapılandırma özellik kılavuzları için. Proje türünüzü uygun özellik sayfaları seçmek için bu yöntemleri geçersiz kılmalıdır.  
  
 `SettingsPage` Sınıfı ve `Microsoft.VisualStudio.Package.ProjectNode` sınıfı, yapılandırma özellikleri kalıcı hale getirmek için bu yöntemleri sunar:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` ve `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` Proje özelliklerinin kalıcı.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` ve `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` yapılandırma özellikleri kalıcı.  
  
  > [!NOTE]
  >  Uygulamaları `Microsoft.VisualStudio.Package.SettingsPage` ve `Microsoft.VisualStudio.Package.ProjectNode` sınıfları kullanın `Microsoft.Build.BuildEngine` almak ve proje dosyasından proje ve yapılandırma özelliklerini ayarlamak için yöntemleri (MSBuild).  
  
  Türetilen sınıf `SettingsPage` uygulamalıdır `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` ve `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` proje dosyasının proje veya yapılandırma özelliklerini kalıcı hale getirmek için.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute ve kayıt defteri yolu  
 Türetilen sınıflar `SettingsPage` Vspackage'lar arasında paylaşılacak şekilde tasarlanmıştır. Türetilen bir sınıf oluşturmak bir VSPackage için mümkün kılmak için `SettingsPage`, ekleme bir `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` türetilen bir sınıf için `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Öznitelik eklendiği VSPackage önemli değildir. Ne zaman bir VSPackage kayıtlı ile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], oluşturulabilecek herhangi bir nesnenin sınıfı kimliği (CLSID) kayıtlı şekilde bir çağrı <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> oluşturabilirsiniz.  
  
 Kayıt defteri yolu için oluşturulan bir nesnenin birleştirerek belirlenir <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word ve CLSID nesne türü guid'si. Varsa `MyProjectPropertyPage` sınıfına sahip {3c693da2-5bca-49b3-bd95-ffe0a39dd723} guid'sini ve UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp olup, ardından kayıt defteri yolunu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio olacaktır \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Proje ve yapılandırma özellik öznitelikleri ve düzeni  
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, Ve <xref:System.ComponentModel.DescriptionAttribute> öznitelikler düzeni, etiketleme ve açıklama genel özellik sayfası, proje ve yapılandırma özelliklerini belirler. Bu öznitelikler kategorisi belirlemek için sırasıyla görünen adı ve açıklaması seçeneği.  
  
> [!NOTE]
>  Eşdeğer öznitelikleri, SRCategory LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanın ve tanımlanan [projeler - Visual Studio 2013 için MPF](https://github.com/tunnelvisionlabs/MPFProj10).  
  
 Aşağıdaki kod parçasını göz önünde bulundurun:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp` Yapılandırma özellik görünür Yapılandırma özelliği sayfasında **My Yapılandırma özelliği** kategorisinde **My kategori**. Seçeneğini belirlediyseniz, açıklama **Alanım açıklaması**, açıklama panelinde görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ekleme ve kaldırma özellik sayfaları](../../extensibility/adding-and-removing-property-pages.md)   
 [Projeleri](../../extensibility/internals/projects.md)   
 [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
