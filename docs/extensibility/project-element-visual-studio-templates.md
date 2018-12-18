---
title: Proje öğesi (Visual Studio şablonları) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 464f6498ccf06f5087c0fa6b12a456082a36c2bd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639145"
---
# <a name="project-element-visual-studio-templates"></a>Proje öğesi (Visual Studio şablonları)
Projeye eklemek için dizinleri ve dosyaları belirtir.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Proje >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`File`|Gerekli öznitelik.<br /><br /> Şablon proje dosyasının adını belirtir *.zip* dosya.|  
|`ReplaceParameters`|İsteğe bağlı öznitelik.<br /><br /> Proje dosyası bir proje şablondan oluşturulduğunda değiştirilmelidir parametre değerleri içerip içermediğini belirten bir Boole değeri. Varsayılan değer `false`.|  
|`TargetFileName`|İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda, proje dosyasının adını belirtir.|  
|`IgnoreProjectParameter`|İsteğe bağlı öznitelik.<br /><br /> Geçerli çözüme projeyi eklenmesi gerekip gerekmediğini belirtir. Varsa özel parametresinin değeri "$*myCustomParameter*$" var. parametre değiştirme dosyasında proje oluşturulur, ancak şu anda açık çözümün bir parçası eklenmedi.|  
  
### <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Klasör](../extensibility/folder-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeye eklemek için bir klasörü belirtir.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Bir projeye eklemek için dosyayı belirtir.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Project` bir isteğe bağlı bir alt öğesidir `TemplateContent`.  
  
 `Project` Öğesi için belirtin bir proje kullanılan ve bu nedenle, yalnızca geçerli proje şablonları.  
  
 `Project` öğeleri olabilir [klasör](../extensibility/folder-element-visual-studio-project-templates.md) alt öğeleri veya [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) alt öğeleri, ancak değil her ikisinin bir karışımıyla `Folder` ve `ProjectItem` alt öğeleri.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanıcı tarafından girilen adına dayalı proje dosya adına otomatik olarak yeniden adlandırır **yeni proje** iletişim kutusu. Kullanım `TargetFileName` şablonla oluşturulan proje dosyaları için bir alternatif dosya adı sağlamak istiyorsanız özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir proje şablonu için meta verileri gösterir. bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] uygulama.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [ProjectItem öğesi (Visual Studio Proje şablonları)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder öğesi (Visual Studio Proje şablonları)](../extensibility/folder-element-visual-studio-project-templates.md)