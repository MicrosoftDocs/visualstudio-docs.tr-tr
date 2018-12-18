---
title: Visual Studio şablon bildirim Şeması Başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38581d7c7dd788fef481676283fdc96c8abc96ba
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586319"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio şablon bildirim Şeması Başvurusu
Visual Studio şablon bildirim biçimi bu şema açıklar (*.vstman*) oluşturulan dosyalar için Visual Studio Proje veya öğe şablonları. Şema ayrıca konumu ve şablon ilgili diğer bilgileri açıklar.  
  
 : Olduğundan ayrı bir öğe ve proje şablonu dizinleri, bildirim hiçbir öğe ve proje şablonlarının bir karışımını olmalıdır.  
  
> [!IMPORTANT]
>  Bu bildirimi, Visual Studio 2017'den itibaren kullanılabilir.  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest öğesi  
 Bildirimin kök öğesi.  
  
### <a name="attributes"></a>Öznitelikler  
  
-   **Sürüm**: şablon bildirimi sürümünü temsil eden bir dize. Gerekli.  
  
-   **Yerel ayar**: yerel ya da yerel ayarlara şablon bildirim temsil eden bir dize. Yerel ayar değeri tüm şablonları için geçerlidir. Her yerel ayar için ayrı bir bildirim kullanmanız gerekir. İsteğe bağlı.  
  
### <a name="child-elements"></a>Alt öğeleri  
  
-   **VSTemplateContainer** isteğe bağlı.  
  
-   **VSTemplateDir** isteğe bağlı.  
  
### <a name="parent-element"></a>Üst öğe  
 Yok.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Kapsayıcı şablon bildirimi öğeleri. Bir bildirim tanımladığı her şablon için bir şablon kapsayıcısı var.  
  
### <a name="attributes"></a>Öznitelikler  
 **VSTemplateType**: şablon türünü belirten bir dize değeri (`"Project"`, `"Item"`, veya `"ProjectGroup"`). Gerekli  
  
### <a name="child-elements"></a>Alt öğeleri  
  
-   **RelativePathOnDisk**: disk üzerinde şablon dosyasının göreli yol. Bu konumu gösterilen şablonu ağacında şablonu yerleşimini de tanımlar. **yeni proje** veya **yeni öğe** iletişim. Bir dizin ve tek tek dosyaları dağıtılan şablonlar için şablon dosyaları içeren dizine bu yolu gösterir. Şablonları olarak dağıtılan için bir *.zip* dosya, bu yolu olmalıdır yolu *.zip* dosya.  
  
-   ** VSTemplateHeader: A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) açıklayan üstbilgi öğesi.  
  
### <a name="parent-element"></a>Üst öğe  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Şablon bulunduğu dizin açıklar. Birden çok bildirim içerebilir **VSTemplateDir** girişlerinin yerelleştirilmiş adını ve şablon kategorisi ağacında görünümlerini denetlemek için sıralama dizinler için sıralama belirtin.  
  
 Kendi tasarımı nedeniyle **VSTemplateDir** girişleri, yalnızca yerel olmayan belirtilen bildirimleri içinde görünmelidir.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt öğeleri  
  
-   **RelativePath**: şablon yolu. Yüzden ilk tüm bildirimler için yol başına yalnızca bir giriş olabilir.  
  
-   **LocalizedName**: A **NameDescriptionIcon** yerelleştirilmiş adı belirten öğe. İsteğe bağlı.  
  
-   **SortOrder**: sıralama düzenini belirten bir dize. İsteğe bağlı.  
  
-   **ParentFolderOverrideName**: geçersiz kılınan üst klasörün adı. İsteğe bağlı. Bu öğeyi bir **adı** özniteliği, adını belirten bir dize değeridir.  
  
### <a name="parent-element"></a>Üst öğe  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Yerelleştirilmiş şablonları için büyük olasılıkla bir açıklama ve adını belirtir. Bkz: **LocalizedName** yukarıda.  
  
### <a name="attributes"></a>Öznitelikler  
  
-   **Paket**: Paket belirten bir dize değeri. İsteğe bağlı.  
  
-   **Kimliği**: kimliğini belirten bir dize değeri İsteğe bağlı.  
  
### <a name="child-elements"></a>Alt öğeleri  
 Yok.  
  
### <a name="parent-element"></a>Üst öğe  
 **LocalizedName**  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki kod, bir proje şablonu örneğidir *.vstman* dosya.  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Aşağıdaki kod, bir öğe şablonunu örneğidir *.vstman* dosya.  
  
```xml  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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