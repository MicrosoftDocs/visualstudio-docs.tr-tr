---
title: ProjectSubType öğesi (Visual Studio şablonları) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d1ca080ea61fbaaba7992fd8f4f1f4fbeac843d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824342"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType öğesi (Visual Studio şablonları)
Şablon içinde belirtilen değerle bir alt kategorisi olarak sınıflandırır `ProjectType` öğesi.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ProjectSubType> SubType </ProjectSubType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve nasıl görüntülendiğini tanımlar **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|  
  
## <a name="text-value"></a>Metin değeri  
 Bir metin değeri gereklidir.  
  
 Bu değer, şablon kategorisidir belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectSubType` bir isteğe bağlı bir alt öğesidir `TemplateData`.  
  
 `ProjectSubType` Öğesi bir alt kategoriye sağlar [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) öğesi. Bu değer içerebilir:  
  
- `SmartDevice-NETCFv1`: Belirtir, şablon hedefleri [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] sürüm 1.0.  
  
- `SmartDevice-NETCFv2`: Belirtir, şablon hedefleri [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] sürüm 2.0.  
  
  Bir şablon içeriyorsa, bir `ProjectType` öğe değerini `Web`, `ProjectSubType` öğe şablonunun programlama dilini belirtir. Bu öğe, aşağıdaki değerlere sahip olabilir:  
  
- `CSharp`: Belirtir şablon oluşturur, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Web proje veya öğe.  
  
- `VisualBasic`: Belirtir şablon oluşturur, bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Web proje veya öğe.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir proje şablonu için meta verileri gösterir. bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] cihazı hedefleyen uygulama [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] sürüm 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [ProjectType öğesi (Visual Studio şablonları)](../extensibility/projecttype-element-visual-studio-templates.md)