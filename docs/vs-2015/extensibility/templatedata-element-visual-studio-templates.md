---
title: TemplateData öğesi (Visual Studio şablonları) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29b481c8560e47dff4c4fadca9dab869e4f5b361
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743773"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablonu kategorilere ayırır ve nasıl görüntülendiğini tanımlar **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.  
  
 \<VSTemplate >  
 \<TemplateData >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Ad](../extensibility/name-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Ya da göründüğü gibi şablonunun adını belirtir. **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|  
|[Açıklama](../extensibility/description-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonun açıklaması da içinde göründüğü gibi belirtir **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|  
|[Simgesi](../extensibility/icon-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Yol ve dosya adı ya da görünür simge olarak hizmet veren bir görüntü dosyasının belirtir **yeni proje** veya **Yeni Öğe Ekle** şablon için bir iletişim kutusu.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Belirtilen grubun altında görünmesi proje şablonu kategorilere ayırır **yeni proje** iletişim kutusu.|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Proje şablonu içinde belirtilen kategori altında görünmesi sınıflandırır **yeni proje** iletişim kutusu.|  
|[Templateıd](../extensibility/templateid-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablon kimliğini belirtir.|  
|[Templategroupıd](../extensibility/templategroupid-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablon Grup kimliğini belirtir.|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Ya da göründüğü gibi aynı kategoride bulunan diğer şablonlar arasında şablonunu düzenlemek için kullanılan bir değer belirtir **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Proje bir örneğinin üzerinde içeren bir klasör oluşturulup oluşturulmayacağını belirtir.|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Oluşturulduğunda, Visual Studio Proje sistemi oluşturacak proje veya öğe için ad belirtir.|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Visual Studio Proje sistemi oluşturulduğunda bir proje veya öğe için varsayılan adı oluşturmak olup olmadığını belirtir.|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Geçici bir proje olarak proje oluşturulup oluşturulamayacağını belirtir.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Belirtir olup olmadığını **Gözat** düğmesi kullanılabilir **yeni proje** iletişim kutusunda, böylece kullanıcıların kolayca yeni bir proje kaydedildiği varsayılan dizini değiştirebilirsiniz.|  
|[Gizli](../extensibility/hidden-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablon ya da görüntülenip görüntülenmeyeceğini belirtir **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablonda görüntüler üst kategori sayısını belirtir **yeni proje** iletişim kutusu.|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|İsteğe bağlı öğe.|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Belirtir olup olmadığını **konumu** metin kutusu **yeni proje** iletişim kutusu etkin, devre dışı veya gizli proje şablonu.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablonu yalnızca belirli en düşük sürüm ve sonraki sürümlerinde, .NET Framework'ü destekliyorsa, bu öğeyi kullanırsınız.|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablon web projeleri için bir ana sayfa destekleyip desteklemediğini belirtir.|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Belirtir olup olmadığını şablonu web projeleri için kod ayırma veya arka plan kod sayfa modeli destekler.|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablon birden çok dil için aynı olup olmadığını ve olup olmadığını belirtir **dil** seçeneği kullanılabilir **yeni proje** iletişim kutusu.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Platformunu belirtir, proje şablonu hedefler. Bu öğe bir proje şablonu oluşturmak için kullanıldığını belirtir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Proje şablonu, öğe şablonu veya başlangıç Seti için meta veriler içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `TemplateData` gerekli bir öğedir.  
  
 İsteğe bağlı bir öğeyle eklemezseniz, o öğe için varsayılan değer kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir proje şablonu için meta verileri gösterir. bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] uygulama.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)

