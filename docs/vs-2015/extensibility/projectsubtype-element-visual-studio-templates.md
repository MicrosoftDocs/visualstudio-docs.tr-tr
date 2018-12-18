---
title: ProjectSubType öğesi (Visual Studio şablonları) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bfc64d4f5a1de6223178321eecb3050478ed9960
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807770"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablon içinde belirtilen değerle bir alt kategorisi olarak sınıflandırır `ProjectType` öğesi.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve nasıl görüntülendiğini tanımlar **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Bu değer, şablon kategorisidir belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectSubType` bir isteğe bağlı bir alt öğesidir `TemplateData`.  
  
 `ProjectSubType` Öğesi bir alt kategoriye sağlar [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) öğesi. Bu değer içerebilir:  
  
- `SmartDevice-NETCFv1`: Belirtir, şablon hedefleri [!INCLUDE[Compact](../includes/compact-md.md)] sürüm 1.0.  
  
- `SmartDevice-NETCFv2`: Belirten tempalate hedefleri [!INCLUDE[Compact](../includes/compact-md.md)] sürüm 2.0.  
  
  Bir şablon içeriyorsa, bir `ProjectType` öğe değerini `Web`, `ProjectSubType` öğe şablonunun programlama dilini belirtir. Bu öğe, aşağıdaki değerlere sahip olabilir:  
  
- `CSharp`: Belirtir şablon oluşturur, bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] Web proje veya öğe.  
  
- `VisualBasic`: Belirtir şablon oluşturur, bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Web proje veya öğe.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir proje şablonu için meta verileri gösterir. bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] cihazı hedefleyen uygulama [!INCLUDE[Compact](../includes/compact-md.md)] sürüm 2.0.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [ProjectType Öğesi (Visual Studio Şablonları)](../extensibility/projecttype-element-visual-studio-templates.md)

