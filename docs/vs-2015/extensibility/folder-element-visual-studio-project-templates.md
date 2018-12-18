---
title: Folder öğesi (Visual Studio Proje şablonları) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81d2856bb7c261219fd69ec1e12db85cfb41d7e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787672"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder Öğesi (Visual Studio Proje Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projeye eklenecek klasörü belirtir.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Proje >  
 \<Klasör >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli öznitelik.<br /><br /> Proje klasörünün adı.|  
|`TargetFolderName`|İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda klasörü vermek adını belirtir. Bu parametre değiştirme kullanarak bir klasör adı için yararlı bir özniteliktir veya uluslararası bir dize içeren bir klasör adlandırma .zip dosyasındaki doğrudan kullanılamaz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Folder`|Projeye eklemek için bir klasörü belirtir. `Folder` alt öğeleri içerebilir `Folder` öğeleri.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Projeye eklemek için bir dosyasını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|İsteğe bağlı alt öğesi [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 `Folder` İsteğe bağlı bir alt öğesi olan `Project`.  
  
 Bir şablonda klasörlere proje öğeleri düzenlemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz:  
  
-   Klasörleri şablon .zip dosyasına ekleyin ve bunları .vstemplate içindeki proje dosyasında yolunu belirterek ekleyin `ProjectItem` öğelerle Hayır `Folder` öğeleri. Önerilen yöntem budur. Örneğin:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Klasörleri şablon .zip dosyasına ekleyin ve bunları projenin .vstemplate dosyasında ekleyebilirsiniz `Folder` öğeleri. Örneğin:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Klasörleri şablon .zip dosyasında içermez, ancak klasörleri ekleme `TargetFileName` özniteliği `ProjectItem` öğesi. Örneğin:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Örnek  
 Meta veriler için bir proje şablonu için aşağıdaki örnekte bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows uygulaması.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [ProjectItem Öğesi (Visual Studio Öğe Şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)

