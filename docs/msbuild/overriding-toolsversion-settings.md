---
title: ToolsVersion ayarlarını geçersiz kılma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f0abe9db7178678c4ffda7f4179117817b3add6
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879321"
---
# <a name="override-toolsversion-settings"></a>ToolsVersion ayarlarını geçersiz kıl
Araç projeleri ve çözümleri üç yoldan biriyle değiştirebilirsiniz:  
  
1.  Kullanarak `-ToolsVersion` geçin (veya `-tv`, kısaca) oluşturduğunuzda proje veya çözümü komut satırından.  
  
2.  Ayarlayarak `ToolsVersion` MSBuild görev parametresi.  
  
3.  Ayarlayarak `$(ProjectToolsVersion)` bir çözüm dahilindeki projede özelliği. Bu, diğer projelerden farklı bir araç kümesi sürümü ile bir çözümde bir proje oluşturmanıza olanak sağlar.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Projeler ve çözümler komut satırı derlemelerinde ToolsVersion ayarlarını geçersiz kıl  
 Visual Studio projeleri genellikle proje dosyasında belirtilen ToolsVersion ile oluşturulmasına kullanabileceğiniz `-ToolsVersion` (veya `-tv`) anahtarını komut satısına değeri geçersiz kılmak ve tüm projelerin ve bunların-projeler oluşturmak için farklı araç takımıyla bağımlılıkları. Örneğin:  
  
```cmd  
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug  
```  
  
 Bu örnekte, tüm projeler ToolsVersion 12.0 kullanılarak oluşturulur. (Ancak bakın [öncelik sırası](#order-of-precedence) bu konunun devamındaki.)  
  
 Kullanırken `-tv` anahtarını komut satısına, isteğe bağlı olarak kullanabileceğiniz `$(ProjectToolsVersion)` çözümdeki diğer projelerden farklı bir ToolsVersion değeriyle derlenmesine bireysel projelerdeki özelliği.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>MSBuild görevinin ToolsVersion parametresini kullanarak ToolsVersion ayarlarını geçersiz kıl  
 MSBuild görevi, başka bir derleme için bir proje için birincil yoludur. Projede belirtilenden farklı bir ToolsVersion ile bir projeyi derlemek MSBuild görevi etkinleştirmek için adlandırılmış bir isteğe bağlı görev parametresi sağlar `ToolsVersion`. Aşağıdaki örnek bu parametrenin nasıl kullanılacağını gösterir:  
  
1.  Adlı bir dosya oluşturun *projectA.proj* ve aşağıdaki kodu içeren:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2.  Adlı başka bir dosya oluşturun *projectB.proj* ve aşağıdaki kodu içeren:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  Bir komut isteminde aşağıdaki komutu girin:  
  
    ```cmd  
    msbuild projectA.proj -t:go -toolsversion:3.5  
    ```  
  
4.  Aşağıdaki çıktı görünür. İçin `projectA`, `-toolsversion:3.5` komut satırında ayarını geçersiz kılar `ToolsVersion=12.0` ayarı `Project` etiketi.  
  
     `ProjectB` bir görev tarafından çağrılır `projectA`. Bu görevin `ToolsVersion=2.0`, diğer kılan `ToolsVersion` ayarlarını `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Öncelik sırası  
 Yüksekten en düşüğe öncelik sırasını belirlemek için kullanılan `ToolsVersion` olan:  
  
1.  `ToolsVersion` Varsa projeyi oluşturmak için kullanılan MSBuild görevindeki özniteliği.  
  
2.  `-toolsversion` (Veya `-tv`) varsa msbuild.exe komutunda kullanılan anahtar.  
  
3.  Ortam değişkenini `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` ayarlanır ve ardından geçerli kullanın `ToolsVersion`.  
  
4.  Ortam değişkenini `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` ayarlanır ve `ToolsVersion` tanımlanan dosya geçerli projede büyükse `ToolsVersion`, geçerli kullanın `ToolsVersion`.  
  
5.  Ortam değişkenini `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlandığında, veya `ToolsVersion` aşağıdaki adımlar kullanılır, ayarlanmadı:  
  
    1.  `ToolsVersion` Özniteliği [proje](../msbuild/project-element-msbuild.md) proje dosyasının öğesi. Bu öznitelik mevcut değilse geçerli sürüm olduğu varsayılır.  
  
    2.  Varsayılan Araçlar sürümü, *MSBuild.exe.config* dosya.  
  
    3.  Kayıt defterindeki varsayılan Araçlar sürümü. Daha fazla bilgi için [standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Ortam değişkenini `MSBUILDLEGACYDEFAULTTOOLSVERSION` aşağıdaki adımlar kullanılır, ayarlanmadı:  
  
    1.  Ortam değişkenini `MSBUILDDEFAULTTOOLSVERSION` ayarlanmış bir `ToolsVersion` var, bunu kullanın.  
  
    2.  Varsa `DefaultOverrideToolsVersion` ayarlanır *MSBuild.exe.config*, bunu kullanın.  
  
    3.  Varsa `DefaultOverrideToolsVersion` kayıt defterinde ayarlanırsa, bunu kullanın.  
  
    4.  Aksi takdirde geçerli kullanın `ToolsVersion`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çoklu sürüm desteği](../msbuild/msbuild-multitargeting-overview.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)