---
title: ProjectType öğesi (Visual Studio şablonları) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14726d5338830eb4044d22778d886241cfd0cd83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921138"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType öğesi (Visual Studio şablonları)
Belirtilen grubun altında görünmesi proje şablonu kategorilere ayırır **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.  
  
> [!WARNING]
>  Proje şablonları, c++, Visual Studio 2012'den itibaren desteklenir. C++'da Visual Studio 2010 ve önceki sürümleri için desteklenmez.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt öğeleri  
 Yok.  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırır ve nasıl görüntülendiğini tanımlar **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|  
  
## <a name="text-value"></a>Metin değeri  
 Bir metin değeri gereklidir.  
  
 Bu değer, türde bir proje şablonu oluşturur ve aşağıdaki değerlerden birini içermelidir belirtir:  
  
- `CSharp`: Belirtir şablon oluşturur, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proje veya öğe.  
  
- `VisualBasic`: Belirtir şablon oluşturur, bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] proje veya öğe.  
  
- `Web`: Belirtir şablon bir Web proje veya öğe oluşturur. Varsa `ProjectType` öğesi içerir, bu değer, dil proje veya öğe içinde tanımlanan [ProjectSubType öğesi (Visual Studio şablonları)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectType` gerekli alt öğesi olan `TemplateData`.  
  
 Değerini `ProjectType` öğeyi belirten bir şablon içinde bulunduğu **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu. Örneğin, bir şablonu ile bir `ProjectType` değerini `CSharp` altında görünür **Visual C#** düğümünde **yeni proje** iletişim kutusu.  
  
 Kullanarak şablon alt belirtilebilir [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi.  
  
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
 [ProjectSubType öğesi (Visual Studio şablonları)](../extensibility/projectsubtype-element-visual-studio-templates.md)