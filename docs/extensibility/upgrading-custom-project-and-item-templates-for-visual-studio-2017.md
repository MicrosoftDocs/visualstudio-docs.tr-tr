---
title: Özel proje ve öğe şablonları için Visual Studio 2017 yükseltme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af60281e7211e7b16e86200c02aef791d26da274
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143484"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Özel proje ve öğe şablonları için Visual Studio 2017 yükseltme

Visual Studio Visual Studio 2017'dan başlayarak, bir .vsix veya bir .msi, Visual Studio'nun önceki sürümleri için farklı bir şekilde yüklendi proje ve öğe şablonları bulur. Özel proje öğesi şablonları kullanıp uzantıları sahipseniz, uzantılarınızın güncelleştirmeniz gerekir. Bu konuda yapmanız gerekir açıklanmaktadır.

Bu değişiklik, yalnızca Visual Studio 2017 etkiler. Visual Studio'nun önceki sürümleri etkilemez.

VSIX uzantısı bir parçası olarak bir öğe veya proje şablonu oluşturmak istiyorsanız, bkz: [oluşturma özel Proje ve öğe şablonlarını](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Tarama şablonu

Visual Studio'nun önceki sürümlerinde **devenv/Setup** veya **devenv /installvstemplates** proje ve öğe şablonları bulmak için yerel diskte tarama. Visual Studio 2017 içinde başlayarak, tarama için kullanıcı düzeyinde konum gerçekleştirilir. Varsayılan kullanıcı düzeyinde konumu **%USERPROFILE%\Documents\\< Visual Studio sürümü\>\Templates\\**. Bu konum tarafından oluşturulan şablonlar için kullanılan **proje** > **şablonları dışarı aktar...**  , komut **otomatik olarak şablon Visual Studio'ya içeri** seçeneği Sihirbazı'nda.

Diğer (kullanıcı olmayan) konumları için konum ve diğer özellikleri şablonun belirten bir manifest(.vstman) dosyası içermelidir. .Vstman dosya şablonları için kullanılan .vstemplate dosyasıyla birlikte oluşturulur. Uzantınızı bir .vsix kullanarak yüklerseniz, bu Visual Studio 2017 uzantı derleyerek gerçekleştirebilirsiniz. Ancak bir .msi kullanırsanız, değişiklikler el ile yapmanız gerekir. Bu değişiklikleri yapmak için yapmanız gerekenler bir listesi için bkz: **yükseltmeleri yüklü uzantıları için bir. MSI** bu konuda daha sonra.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>VSIX uzantısı proje veya öğe şablonları ile güncelleştirme  

1.  Çözüm Visual Studio 2017 açın. Yükseltme kodu istenir. **Tamam**'ı tıklatın.  
  
2.  Yükseltme işlemi tamamlandıktan sonra yükleme hedef sürümü değiştirmeniz gerekebilir. VSIX proje source.extension.vsixmanifest dosyasını açın ve seçin **yükleme hedefleri** sekmesi. Varsa **sürüm aralığı** alandır **[14.0]**, tıklatın **Düzenle** ve Visual Studio 2017 içerecek şekilde değiştirin. Örneğin, ayarlayabilirsiniz **[14.0,15.0]** Visual Studio 2015 ya da Visual Studio 2017 veya için uzantıyı yüklemek için **[15.0]** yalnızca Visual Studio 2017 yüklemek için.  
  
3.  Kodu yeniden derleyin.  
  
4.  Visual Studio’yu kapatın.  
  
5.  VSIX yükleyin.  
  
6.  Aşağıdakileri yaparak güncelleştirme test edebilirsiniz:  
  
    1.  Değişiklik tarama dosyasını aşağıdaki kayıt defteri anahtarı tarafından etkinleştirilir:  
  
         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Anahtarı ekledikten sonra çalıştırmak **devenv /installvstemplates**.  
  
    3.  Visual Studio'yu yeniden açın. Beklenen konumda şablonunuzu bulmanız gerekir.  
  
    > [!NOTE]
    >  Visual Studio genişletilebilirliğini proje şablonu kayıt defteri anahtarı mevcut olduğunda için kullanılabilir değil. Kayıt defteri anahtarını silin (ve yeniden **devenv /installvstemplates**) bunları kullanmak için.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Proje ve öğe şablonları dağıtmak için diğer öneriler  
  
-   Daraltılmış şablon dosyalarını kullanmaktan kaçının. Şablon dosyaları kaynakları ve içeriği almak için sıkıştırılmamış olmasına gerek daraltılmış, böylece kullanıcılar kullanmak costlier. Bunun yerine, şablonu başlatma hızlandırmak için kendi dizin altında tek tek dosya olarak proje ve öğe şablonları dağıtmanız gerekir. VSIX uzantıları için SDK derleme görevleri otomatik olarak herhangi bir daraltılmış şablonu VSIX dosyası oluşturulurken sıkıştırmasını.  
  
-   Şablon bulma sırasında gereksiz kaynak derleme yüklerini önlemek için paket/kaynak kimliği girişlerinde şablon adı, açıklama, simge veya Önizleme kullanmaktan kaçının. Bunun yerine, yerelleştirilmiş bildirimleri yerelleştirilmiş adlar veya özellikleri kullanan her yerel ayar için bir şablon girişi oluşturmak için kullanabilirsiniz.  
  
-   Şablon dosyası öğeleri olarak ekliyorsanız, bildirim üretme, beklenen sonuçları vermeyebilir. Bu durumda, el ile oluşturulan bildirim VSIX proje eklemeniz gerekir.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Dosya değişiklikleri proje ve öğe şablonları  
Yeni dosyalar doğru oluşturabilmesi için Visual Studio 2015 ve Visual Studio 2017 şablon dosyalarını sürümleri arasındaki farkı noktalarının gösteriyoruz.  
  
 Visual Studio 2015 tarafından oluşturulan varsayılan proje .vstemplate dosyası şöyledir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ProjectTemplate1</Name>  
    <Description>ProjectTemplate1</Description>  
    <Icon>ProjectTemplate1.ico</Icon>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <SortOrder>1000</SortOrder>  
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
    <CreateNewFolder>true</CreateNewFolder>  
    <DefaultName>ProjectTemplate1</DefaultName>  
    <ProvideDefaultName>true</ProvideDefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">  
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>  
    </Project>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Öğesinden yeniden VSIX projesi ile sonuçlandı (bunu VSIX proje bildirim dizininde bulabilirsiniz) .vstman dosya şöyledir:  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ProjectTemplate1</Name>  
        <Description>ProjectTemplate1</Description>  
        <Icon>ProjectTemplate1.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>ProjectTemplate1</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Tarafından sağlanan bilgileri [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) öğesi aynı kalır.  **\<VSTemplateContainer >** öğesi ilişkili şablonu için .vstemplate dosyasına işaret eder.  
  
 Visual Studio 2015 tarafından oluşturulan varsayılan öğesi .vstemplate dosyasını şöyledir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ItemTemplate1</Name>  
    <Description>ItemTemplate1</Description>  
    <Icon>ItemTemplate1.ico</Icon>  
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    <DefaultName>Class.cs</DefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <References>  
      <Reference>  
        <Assembly>System</Assembly>  
      </Reference>  
    </References>  
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Öğesinden yeniden VSIX projesi ile sonuçlandı (bunu VSIX proje bildirim dizininde bulabilirsiniz) .vstman dosya şöyledir:  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Tarafından sağlanan bilgileri  **\<TemplateData >** öğesi aynı kalır.  **\<VSTemplateContainer >** öğesi ilişkili şablonu için .vstemplate dosyasına işaret eder  
  
 .Vstman dosyasının farklı öğeler hakkında daha fazla bilgi için bkz: [Visual Studio şablon bildirim şema başvurusu](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Yükseltmeleri uzantıları için yüklenmiş bir. MSI

MSI tabanlı uzantılar şablonları ortak şablon konumlara aşağıdaki gibi dağıtın:

- **\<Visual Studio yükleme dizini > \Common7\IDE\\< ProjectTemplates/öğe şablonları >**

- **\<Visual Studio yükleme dizini > \Common7\IDE\Extensions\\< UzantıAdı\>\\< proje/öğe şablonları >**

Uzantınızı MSI tabanlı bir dağıtım gerçekleştirirse, şablon bildirim el ile oluşturmak ve uzantı kurulumunda bulunduğundan emin olun gerekir. Yukarıda listelenen .vstman örnekler karşılaştırın ve [Visual Studio şablon bildirim şema başvurusu](../extensibility/visual-studio-template-manifest-schema-reference.md).

Proje ve öğe şablonları için ayrı bildirimlerini oluşturmanız gerekir ve kök şablon dizinine belirtildiği yukarıdaki işaret etmelidir. Uzantı ve yerel ayar başına bir bildirim oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

[Şablon bulma sorunlarını giderme](troubleshooting-template-discovery.md)  
[Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)