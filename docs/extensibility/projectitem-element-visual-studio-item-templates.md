---
title: ProjectItem öğesi (Visual Studio öğe şablonları) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae7b54e6311a58d93c5cc11cfc073c4032df32dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855995"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem öğesi (Visual Studio öğe şablonları)
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
| Öznitelik | Açıklama |
|---------------------| - |
| `SubType` | İsteğe bağlı öznitelik.<br /><br /> Çok dosyalı öğe şablonunda alt öğenin türünü belirtir. Bu değer Düzenleyicisi belirlemek için kullanılır, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] öğesini açmak için kullanır. |
| `CustomTool` | İsteğe bağlı öznitelik.<br /><br /> Proje dosyasında CustomTool öğe için ayarlar. |
| `ItemType` | İsteğe bağlı öznitelik.<br /><br /> Öğe için Itemtype proje dosyasında ayarlar. |
| `ReplaceParameters` | İsteğe bağlı öznitelik.<br /><br /> Öğe bir proje şablondan oluşturulduğunda değiştirilmelidir parametre değerleri içerip içermediğini belirten bir Boole değeri. Varsayılan değer `false`. |
| `TargetFileName` | İsteğe bağlı öznitelik.<br /><br /> Şablondan oluşturulan öğenin adını belirtir. Bu öznitelik, bir öğe adı oluşturmak için parametre değiştirme kullanmak için kullanışlıdır. |
  
### <a name="child-elements"></a>Alt öğeleri  
 Yok.  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonu içeriğini belirtir.|  
  
## <a name="text-value"></a>Metin değeri  
 Bir metin değeri gereklidir.  
  
 A `string` şablondaki bir dosyanın adını temsil eden *.zip* dosya.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectItem` İsteğe bağlı bir alt öğesi olan `TemplateContent`.  
  
 `TargetFileName` Özniteliği, parametrelerle dosyaları yeniden adlandırmak için kullanılabilir. Örneğin, dosyayı *MyFile.vb* şablonunun kök dizininde mevcut *.zip* dosyası, ancak istediğiniz dosyanın adı kullanıcı tarafından sağlanan dosya adına göre **Yeni Öğe Ekle**  iletişim kutusunda, aşağıdaki XML kullanabilirsiniz:  
  
```xml  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Bu şablonu kullanarak bir öğe oluşturulduğunda dosya adı girilen kullanıcı adı hesaplanır **Yeni Öğe Ekle** iletişim kutusu. Bu, çok dosyalı öğe şablonları oluştururken kullanışlıdır. Daha fazla bilgi için [nasıl yapılır: çok dosyalı şablonlar oluşturma](../ide/how-to-create-multi-file-item-templates.md) ve [şablon parametreleri](../ide/template-parameters.md).  
  
## <a name="example"></a>Örnek  
 Standart öğesi şablonu için meta veriler aşağıdaki örnekte bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıfı.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Nasıl yapılır: çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)   
 [Şablon parametreleri](../ide/template-parameters.md)