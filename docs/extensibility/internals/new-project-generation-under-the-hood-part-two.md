---
title: 'Yeni proje oluşturma: altyapı öğeleri, iki bölüm | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38f2a4a84c6223c2e195c3d703f52d7fd5b18c86
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837535"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm İki
İçinde [yeni proje oluşturma: başlık altında Kısım](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) gördüğümüz nasıl **yeni proje** iletişim kutusu doldurulur. Seçtiğiniz varsayalım bir **Visual C# Windows uygulaması**, doldurulmuş **adı** ve **konumu** metin kutuları ve tıklandı Tamam.  
  
## <a name="generating-the-solution-files"></a>Çözüm dosyaları oluşturma  
 Bir uygulama şablonunu seçme yönlendirir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sıkıştırmasını açın ve karşılık gelen .vstemplate dosyasını açın ve bu dosyayı XML komutlar yorumlamak için bir şablon başlatın. Bu komutlar, yeni veya mevcut çözümde proje ve proje öğeleri oluşturur.  
  
 Şablonun .vstemplate dosyasını içeren .zip klasöründen öğe şablonları adlı kaynak dosyalarını ayıklar. Şablonu bu dosyaları yeni projeye uygun şekilde özelleştirme kopyalar.  
  
### <a name="template-parameter-replacement"></a>Şablon parametre değiştirme  
 Şablonun yeni bir projeye bir öğe şablonunu kopyaladığında, herhangi bir şablon parametre dosyasını özelleştirmek için dizeleriyle değiştirir. Bir şablon parametre öncesinde ve örneğin bir dolar işareti tarafından izlenen özel bir belirteç, $date$ içindir.  
  
 Bir normal proje öğesi şablon göz atalım. Ayıklayın ve Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründeki Program.cs inceleyin.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Basit adlı yeni bir Windows uygulaması projesi oluşturursanız, şablon değiştirir `$safeprojectname$` projenin adı ile parametre.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Şablon parametreleri tam bir listesi için bkz. [şablon parametreleri](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Bir görünüm içindeki bir. VSTemplate dosyası  
 Temel .vstemplate dosyası bu biçime sahip  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 İnceledik \<TemplateData > konusundaki [yeni proje oluşturma: başlık altında Kısım](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Bu bölümdeki etiketleri görünümünü denetlemek için kullanılan **yeni proje** iletişim kutusu.  
  
 Etiketleri \<TemplateContent > bölüm denetimi oluşturma yeni projeleri ve proje öğeleri. İşte \<TemplateContent > \Program Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasörüne cswindowsapplication.vstemplate dosyasından bölümü.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 \<Proje > Etiket denetimleri olan bir proje oluşturma ve \<ProjectItem > etiketi, bir proje öğesi oluşturulmasını denetler. ' % S'parametre ReplaceParameters true ise, şablon proje dosyası veya öğe tüm şablon parametrelerinde özelleştireceksiniz. Bu durumda, tüm proje öğeleri, Settings.settings dışında özelleştirilir.  
  
 TargetFileName parametresi sonuçta elde edilen proje dosyası veya öğe göreli yolunu ve adını belirtir. Bu bir klasör yapısını projenizi oluşturmanızı sağlar. Proje öğesi, bu bağımsız değişkeni belirtmezseniz, proje öğesi şablon olarak aynı ada sahip.  
  
 Sonuçta elde edilen Windows uygulama klasör yapısı şuna benzer:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 İlk ve tek \<Proje > etiketinde şablon okuma:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Bu, kopyalama ve şablon öğesi windowsapplication.csproj özelleştirme Simple.csproj proje dosyası oluşturmak için yeni bir proje şablonu bildirir.  
  
### <a name="designers-and-references"></a>Tasarımcılar ve başvuruları  
 Özellikleri klasörü mevcut olduğundan ve beklediğiniz dosyaları içerir, Çözüm Gezgini'nde görebilirsiniz. Ancak proje hakkında atıfta bulunan ve Resources.resx için Resources.Designer.cs ve Form1.Designer.cs Form1.cs için gibi tasarımcı dosyası bağımlılıkları?  Bunu oluşturulduğunda bu Simple.csproj dosyasında ayarlanır.  
  
 İşte \<ItemGroup > Proje başvuruları oluşturan Simple.csproj'nden:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Çözüm Gezgini'nde görünen altı proje başvurularını bunlar görebilirsiniz. Başka bir bölümünden işte \<ItemGroup >. Açıklık için kod satır sayısını silinmiş. Bu bölümde Settings.Designer.cs üzerinde Settings.settings bağımlı hale getirir:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm Bir](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)