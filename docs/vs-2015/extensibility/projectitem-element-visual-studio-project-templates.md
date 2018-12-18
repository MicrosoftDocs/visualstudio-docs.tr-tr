---
title: ProjectItem öğesi (Visual Studio Proje şablonları) | Microsoft Docs
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
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bca26cba66169758aa882535c07846cfa451d172
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737075"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem Öğesi (Visual Studio Proje Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje şablonunda içeren bir dosyayı belirtir.  
  
> [!NOTE]
>  `ProjectItem` Öğesi şablonu için bir proje veya bir öğe olmasına bağlı olarak farklı öznitelikleri kabul eder. Bu konu başlığı altında açıklanır `ProjectItem` öğesi için proje şablonları. Bir açıklaması için `ProjectItem` öğesi için öğe şablonları görmek [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Proje >  
 \<ProjectItem >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`TargetFileName`|İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda proje öğesi yolunu ve adını belirtir. Bu öznitelik, şablon .zip dosyasında dizin yapısının farklı bir dizin yapısı oluşturmak için veya bir öğe adı oluşturmak için parametre değiştirme kullanmak için kullanışlıdır.|  
|`ReplaceParameters`|İsteğe bağlı öznitelik.<br /><br /> Öğe bir proje şablondan oluşturulduğunda değiştirilmelidir parametre değerleri içerip içermediğini belirten bir Boole değeri. Varsayılan değer `false`.|  
|`OpenInEditor`|İsteğe bağlı öznitelik.<br /><br /> Öğesi içinde kendi ilgili Düzenleyicisi'nde açtığınız olup olmadığını belirten bir Boole değeri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir proje şablondan oluşturulduğunda.<br /><br /> `OpenInWebBrowser` Ve `OpenInHelpBrowser` öznitelikleri yoksayıldı sahip bir öğe üzerinde bir `OpenInEditor` değerini `true`.<br /><br /> Varsayılan değer `false` şeklindedir.|  
|`OpenInWebBrowser`|İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda öğesi Web tarayıcısını açık olup olmadığını belirten bir Boole değeri.<br /><br /> Web tarayıcısında, HTML dosyaları ve projeye yerel olan metin dosyaları açabilirsiniz. Dış URL bu özniteliği ile açılamaz.<br /><br /> Varsayılan değer `false` şeklindedir.|  
|`OpenInHelpBrowser`|İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda öğesi Yardım Görüntüleyicisi'nde açtığınız olup olmadığını belirten bir Boole değeri.<br /><br /> HTML dosyaları ve metin dosyaları projeye yerel Yardım tarayıcıda açabilirsiniz. Dış URL bu özniteliği ile açılamaz.<br /><br /> Varsayılan değer `false` şeklindedir.|  
|`OpenOrder`|İsteğe bağlı öznitelik.<br /><br /> Öğeleri, ilgili düzenleyicilerde açılacak sırasını temsil eden sayısal bir değer belirtir. Tüm değerlerin 10'ın katları olmalıdır. Daha yüksek olan öğeler `OpenOrder` değerleri ilk kez açıldığında.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Projeye eklemek için dizinleri ve dosyaları belirtir.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 A `string` şablon .zip dosyası bir dosya adı veya yolu temsil.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectItem` İsteğe bağlı bir alt öğesi olan `Project`.  
  
 `TargetFileName` Özniteliği, şablon .zip dosyasında dizin yapısının farklı bir dizin yapısı oluşturmak için kullanılabilir. Örneğin, dosya `MyFile.vb` şablon .zip dosyasının kök dizininde mevcut ancak dosya adlı bir dizinde yerleştirilmesini istediğiniz `CustomFiles` şablondan oluşturulan tüm projelerde, aşağıdaki XML kullanabilirsiniz:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName` Özniteliği de kullanılabilir, uluslararası karakter, dosya adlarını içeren dosyaları yeniden adlandırmak için. Örneğin, dosyayı bir .zip dosyasına sıkıştırılmış önce kaydedilmelidir şekilde şablon .zip dosyasını Unicode karakterleri, dosya adları içeremez. `TargetFileName` Özniteliği, dosyanın adı özgün Unicode dosya adı ayarlamak için kullanılabilir.  
  
 `TargetFileName` Özniteliği de parametrelere sahip dosyaları yeniden adlandırmak için kullanılabilir. Aşağıdaki yordam, dosyayı yeniden adlandırmak açıklanmaktadır `MyFile.vb`, proje adına göre bir dosya adı şablon .zip dosyasının kök dizininde bulunmaktadır.  
  
### <a name="to-rename-files-with-parameters"></a>Parametrelerle dosyaları yeniden adlandırmak için  
  
1.  .Vstemplate dosyasında aşağıdaki XML'i kullanın:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Proje dosyasını açın (.vbproj için bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Proje) bir metin düzenleyicisinde veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Proje dosyasında aşağıdaki XML'e benzer satırı bulun:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Kod satırının şu XML ile değiştirin:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Bu şablondan bir proje oluşturulduğunda dosya adı girilen kullanıcı adı hesaplanır **yeni proje** olan tüm güvenli olmayan karakterleri ve boşlukları kaldırılmış bir iletişim kutusu. Daha fazla bilgi için [şablon parametreleri](../ide/template-parameters.md).  
  
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
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
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
 [Şablon parametreleri](../ide/template-parameters.md)   
 [ProjectItem Öğesi (Visual Studio Öğe Şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)

