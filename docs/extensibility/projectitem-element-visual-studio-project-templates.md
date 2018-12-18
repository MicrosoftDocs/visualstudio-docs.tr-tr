---
title: ProjectItem öğesi (Visual Studio Proje şablonları) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 585615c07d9f11f75468bccde1bae05a355bf98f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899961"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem öğesi (Visual Studio Proje şablonları)
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
| Öznitelik | Açıklama |
|---------------------| - |
| `TargetFileName` | İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda proje öğesi yolunu ve adını belirtir. Bu öznitelik, bir dizin yapısına dizin yapısının farklı şablonu oluşturmak için kullanışlıdır *.zip* dosyası veya bir öğe adı oluşturmak için parametre değiştirme kullanma. |
| `ReplaceParameters` | İsteğe bağlı öznitelik.<br /><br /> Öğe bir proje şablondan oluşturulduğunda değiştirilmelidir parametre değerleri içerip içermediğini belirten bir Boole değeri. Varsayılan değer `false`. |
| `OpenInEditor` | İsteğe bağlı öznitelik.<br /><br /> Öğesi içinde kendi ilgili Düzenleyicisi'nde açtığınız olup olmadığını belirten bir Boole değeri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir proje şablondan oluşturulduğunda.<br /><br /> `OpenInWebBrowser` Ve `OpenInHelpBrowser` öznitelikleri yoksayıldı sahip bir öğe üzerinde bir `OpenInEditor` değerini `true`.<br /><br /> Varsayılan değer `false` şeklindedir. |
| `OpenInWebBrowser` | İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda öğesi Web tarayıcısını açık olup olmadığını belirten bir Boole değeri.<br /><br /> Web tarayıcısında, HTML dosyaları ve projeye yerel olan metin dosyaları açabilirsiniz. Dış URL bu özniteliği ile açılamaz.<br /><br /> Varsayılan değer `false` şeklindedir. |
| `OpenInHelpBrowser` | İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda öğesi Yardım Görüntüleyicisi'nde açtığınız olup olmadığını belirten bir Boole değeri.<br /><br /> HTML dosyaları ve metin dosyaları projeye yerel Yardım tarayıcıda açabilirsiniz. Dış URL bu özniteliği ile açılamaz.<br /><br /> Varsayılan değer `false` şeklindedir. |
| `OpenOrder` | İsteğe bağlı öznitelik.<br /><br /> Öğeleri, ilgili düzenleyicilerde açılacak sırasını temsil eden sayısal bir değer belirtir. Tüm değerlerin 10'ın katları olmalıdır. Daha yüksek olan öğeler `OpenOrder` değerleri ilk kez açıldığında. |
  
### <a name="child-elements"></a>Alt öğeleri  
 Yok.  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Projeye eklemek için dizinleri ve dosyaları belirtir.|  
  
## <a name="text-value"></a>Metin değeri  
 Bir metin değeri gereklidir.  
  
 A `string` şablon dosyasının adı veya yolu temsil *.zip* dosya.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectItem` İsteğe bağlı bir alt öğesi olan `Project`.  
  
 `TargetFileName` Öznitelik, bir dizin yapısına dizin yapısının farklı şablonu oluşturmak için kullanılabilir *.zip* dosya. Örneğin, dosyayı *MyFile.vb* şablon kök dizininde mevcut *.zip* dosya, ancak isterseniz adlı bir dizinde yerleştirilecek dosya *CustomFiles* tüm projelerde Şablondan oluşturulan, aşağıdaki XML kullanırsınız:  
  
```xml  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName` Özniteliği de kullanılabilir, uluslararası karakter, dosya adlarını içeren dosyaları yeniden adlandırmak için. Örneğin, bir şablon *.zip* dosya Unicode karakterleri, dosya adları içeremez, dosyanın içine sıkıştırılabilir önce kaydedilmelidir şekilde bir *.zip* dosya. `TargetFileName` Özniteliği, dosyanın adı özgün Unicode dosya adı ayarlamak için kullanılabilir.  
  
 `TargetFileName` Özniteliği de parametrelere sahip dosyaları yeniden adlandırmak için kullanılabilir. Aşağıdaki yordam, dosyayı yeniden adlandırmak açıklanmaktadır *MyFile.vb*, şablonun kök dizininde mevcut *.zip* dosyasına proje adına göre bir dosya adı.  
  
### <a name="to-rename-files-with-parameters"></a>Parametrelerle dosyaları yeniden adlandırmak için  
  
1. Aşağıdaki XML'de kullanmak *.vstemplate* dosyası:  
  
   ```xml  
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
   ```  
  
2. Proje dosyasını açın (*.vbproj* için bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Proje) bir metin düzenleyicisinde veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3. Proje dosyasında aşağıdaki XML'e benzer satırı bulun:  
  
   ```xml  
   <Compile Include="MyFile.vb">  
   ```  
  
4. Kod satırının şu XML ile değiştirin:  
  
   ```xml  
   <Compile Include="$safeprojectname$.vb">  
   ```  
  
    Bu şablondan bir proje oluşturulduğunda dosya adı girilen kullanıcı adı hesaplanır **yeni proje** olan tüm güvenli olmayan karakterleri ve boşlukları kaldırılmış bir iletişim kutusu. Daha fazla bilgi için [şablon parametreleri](../ide/template-parameters.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Şablon parametreleri](../ide/template-parameters.md)   
 [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)