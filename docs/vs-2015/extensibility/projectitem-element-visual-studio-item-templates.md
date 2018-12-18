---
title: ProjectItem öğesi (Visual Studio öğe şablonları) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44fe6613288cac93034dd32a3203f1bb73004f83
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747948"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem Öğesi (Visual Studio Öğe Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğe şablonunda içeren bir dosyayı belirtir.  
  
> [!NOTE]
>  `ProjectItem` Öğesi şablonu için bir proje veya bir öğe olmasına bağlı olarak farklı öznitelikleri kabul eder. Bu konu başlığı altında açıklanır `ProjectItem` öğesi için öğesi. Bir açıklaması için `ProjectItem` görmek için proje şablonları, öğe [ProjectItem öğesi (Visual Studio Proje şablonları)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectItem >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`SubType`|İsteğe bağlı öznitelik.<br /><br /> Çok dosyalı öğe şablonunda alt öğenin türünü belirtir. Bu değer Düzenleyicisi belirlemek için kullanılır, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] öğesini açmak için kullanır.|  
|`CustomTool`|İsteğe bağlı öznitelik.<br /><br /> Proje dosyasında CustomTool öğe için ayarlar.|  
|`ItemType`|İsteğe bağlı öznitelik.<br /><br /> Öğe için Itemtype proje dosyasında ayarlar.|  
|`ReplaceParameters`|İsteğe bağlı öznitelik.<br /><br /> Öğe bir proje şablondan oluşturulduğunda değiştirilmelidir parametre değerleri içerip içermediğini belirten bir Boole değeri. Varsayılan değer `false`.|  
|`TargetFileName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan oluşturulan öğenin adını belirtir. Bu öznitelik, bir öğe adı oluşturmak için parametre değiştirme kullanmak için kullanışlıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonu içeriğini belirtir.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 A `string` şablon .zip dosyasında dosyanın adını temsil eden.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectItem` İsteğe bağlı bir alt öğesi olan `TemplateContent`.  
  
 `TargetFileName` Özniteliği, parametrelerle dosyaları yeniden adlandırmak için kullanılabilir. Örneğin, dosya `MyFile.vb` istediğiniz dosyanın adı, kullanıcı tarafından sağlanan dosya adı temel şablon .zip dosyası, ancak kök dizininde mevcut **Yeni Öğe Ekle** iletişim kutusunda, aşağıdaki XML kullanmanız gerekir:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Bu şablonu kullanarak bir öğe oluşturulduğunda dosya adı girilen kullanıcı adı hesaplanır **Yeni Öğe Ekle** iletişim kutusu. Bu, çok dosyalı öğe şablonları oluştururken kullanışlıdır. Daha fazla bilgi için [nasıl yapılır: çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md) ve [şablon parametreleri](../ide/template-parameters.md).  
  
## <a name="example"></a>Örnek  
 Standart öğesi şablonu için meta veriler aşağıdaki örnekte bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] sınıfı.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Nasıl yapılır: çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)   
 [Şablon Parametreleri](../ide/template-parameters.md)

