---
title: 'Nasıl yapılır: birden çok proje şablonu oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eee52a4f77c7d3a07b237f01877c5cba30e53900
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950855"
---
# <a name="how-to-create-multi-project-templates"></a>Nasıl Yapılır: Birden Çok Proje Şablonu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. Ne zaman bir proje bir çoklu proje şablonunu temel alarak oluşturulur **yeni proje** iletişim kutusu, şablondaki her proje, çözüme eklenir.  
  
 Birden çok proje şablonu, sıkıştırılmış bir .zip dosyasına aşağıdaki öğeleri içermelidir:  
  
- Tüm birden çok proje şablonu için kök .vstemplate dosyası. Bu kök .vstemplate dosyası meta verilerini içeren, **yeni proje** iletişim kutusunu görüntüler; bu şablonda projeler için .vstemplate dosyaları nerede bulacağını belirler. Bu dosya .zip dosyasının kök dizininde olması gerekir.  
  
- Tam proje şablonu için gerekli dosyaları içeren bir veya daha fazla klasör. Bu proje için tüm kod dosyaları ve proje için bir .vstemplate dosyası içerir.  
  
  Örneğin, iki proje içeren bir birden çok proje şablonu .zip dosyası, aşağıdaki dosyaları ve dizinleri sahip olabilirsiniz:  
  
  MultiProjectTemplate.vstemplate  
  
  \Project1\Project1.vstemplate  
  
  \Project1\Project1.vbproj  
  
  \Project1\Class.vb  
  
  \Project2\Project2.vstemplate  
  
  \Project2\Project2.vbproj  
  
  \Project2\Class.vb  
  
  Birden çok proje şablonu için kök .vstemplate dosyası bir tek proje şablonundan aşağıdaki yollarla farklıdır:  
  
- `Type` Özniteliği `VSTemplate` ögesinin değeri `ProjectGroup`. Örneğin:  
  
  ```  
  <VSTemplate Version="2.0.0" Type="ProjectGroup"  
      xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
  ```  
  
- `TemplateContent` Öğesi içeren bir `ProjectCollection` bir veya daha fazla olan öğeyi `ProjectTemplateLink` yolları dahil edilen projenin .vstemplate dosyaları tanımlayan öğeler. Örneğin:  
  
  ```  
  <TemplateContent>  
      <ProjectCollection>  
          <ProjectTemplateLink>  
              Project1\Project1.vstemplate  
          </ProjectTemplateLink>  
          <ProjectTemplateLink>  
              Project2\Project2.vstemplate  
          </ProjectTemplateLink>  
      </ProjectCollection>  
  </TemplateContent>  
  ```  
  
  Birden çok proje şablonu da normal şablonlarından farklı davranır. Birden çok proje şablonu aşağıdaki benzersiz özelliklere sahiptir:  
  
- Birden çok proje şablonu tek tek projelerde adlarına göre atanamaz **yeni proje** iletişim kutusu. Bunun yerine, `ProjectName` özniteliği `ProjectTemplateLink` öğenin her proje için adı belirtin. Daha fazla bilgi için aşağıdaki bölümde ilk örnekte bakın.  
  
- Birden çok proje şablonu, farklı dillerde yazılmış projeler içerebilir, ancak tüm şablon yalnızca bir kategoriye göre de kullanarak konulabilir `ProjectType` öğesi.  
  
### <a name="to-create-a-multi-project-template"></a>Birden çok proje şablonu oluşturmak için  
  
1.  Birden çok proje şablonuna dahil etme projeleri oluşturun.  
  
2.  Her proje için .vstemplate dosyaları oluşturur. Daha fazla bilgi için [nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md).  
  
3.  Kök .vstemplate dosyası, birden çok proje şablonu meta verileri içerecek şekilde oluşturun. Daha fazla bilgi için aşağıdaki bölümde ilk örnekte bakın.  
  
4.  Dosya ve klasörler, şablona dahil, seçime sağ tıklayın, seçin **göndermek için**ve ardından **sıkıştırılmış (daraltılmış) klasör**. Dosya ve klasörlerin bir .zip dosyasına sıkıştırılır.  
  
5.  .Zip şablon dosyası koymak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje şablonu dizini. Varsayılan olarak, bu \My Documents\Visual Studio dizindir *sürüm*\Templates\ProjectTemplates\\.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir temel çoklu proje kök .vstemplate dosyası gösterilmektedir. Bu örnekte, şablon iki proje içermektedir `My Windows Application` ve `My Class Library`. `ProjectName` Özniteliği `ProjectTemplateLink` öğesi adını ayarlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu projeye atanacak. Varsa `ProjectName` özniteliği mevcut değilse, .vstemplate dosyasının adı proje adı olarak kullanılır.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte `SolutionFolder` projeleri iki gruplara bölmek için öğe `Math Classes` ve `Graphics Classes`. Bu şablon, ikisi her çözüm klasöründe yer alır, dört proje içerir.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)   
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder öğesi (Visual Studio şablonları)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink Öğesi (Visual Studio Şablonları)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)



