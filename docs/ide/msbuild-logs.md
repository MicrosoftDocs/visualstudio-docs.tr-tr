---
title: MSBuild sorunları için sorun giderme ve günlük oluşturma
description: Visual Studio projenizde derleme sorunlarının nasıl tanınabileceği hakkında bilgi edinin ve gerekirse, araştırma için Microsoft 'a göndermek üzere bir günlük oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/08/2021
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: 3496eb5a0e8f699a994037ccc853a76e4f93e4ee
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225230"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>MSBuild sorunları için sorun giderme ve günlük oluşturma

Aşağıdaki yordamlar Visual Studio projenizde derleme sorunlarını tanılamanıza yardımcı olabilir ve gerekirse, araştırma için Microsoft 'a göndermek üzere bir günlük oluşturabilir.

## <a name="a-property-value-is-ignored"></a>Özellik değeri yoksayıldı

Bir proje özelliği belirli bir değere ayarlanmış gibi görünüyorsa, ancak derleme üzerinde hiçbir etkisi yoksa, aşağıdaki adımları izleyin:

1. Visual Studio sürümünüze karşılık gelen Visual Studio Geliştirici Komut İstemi açın.
1. Çözüm yolu, yapılandırmanız ve proje adınız için değerleri değiştirdikten sonra aşağıdaki komutu çalıştırın:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Bu komut bir "önceden işlenmiş" MSBuild proje dosyası (out.xml) oluşturur. Nerede tanımlandığını görmek için bu dosyada belirli bir özelliği arayabilirsiniz.

Bir özelliğin son tanımı, yapılandırmanın tükettiği şeydir. Özellik iki kez ayarlanırsa ikinci değer birincinin üzerine yazar. Ayrıca, MSBuild projeyi çeşitli geçişlerde değerlendirir:

- PropertyGroups ve Imports
- ItemDefinitionGroups
- ItemGroups
- Targets

Bu nedenle, aşağıdaki sıra verilmiştir:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

"MyFile.txt" öğesi için "MyMetadata" değeri, derleme sırasında "B" olarak değerlendirilir ("A" değil ve boş değil)

## <a name="incremental-build-is-building-more-than-it-should"></a>Artımlı derleme şundan daha fazla oluşturuyor

MSBuild, bir projeyi veya proje öğesini gereksiz şekilde yeniden derlense, ayrıntılı veya ikili derleme günlüğü oluşturun. Gereksiz yere oluşturulmuş veya derlenen dosyanın günlüğünde arama yapabilirsiniz. Çıktı şuna benzer:

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Visual Studio IDE 'de oluşturuyorsanız (ayrıntılı çıkış penceresi ayrıntı düzeyi ile), **Çıkış penceresi** her projenin güncel olmayan nedenini görüntüler:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log-at-the-command-prompt"></a>Komut isteminde ikili MSBuild günlüğü oluşturma

1. Visual Studio sürümünüz için Geliştirici Komut İstemi açın

1. Komut isteminden aşağıdaki komutlardan birini çalıştırın. (Gerçek projenizi ve yapılandırma değerlerinizi kullanmayı unutmayın.):

   ```cmd
   Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
   ```

   veya

   ```cmd
   Msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
   ```

MSBuild *. binlog* dosyası, MSBuild 'i çalıştırdığınız dizinde oluşturulur.

## <a name="create-a-binary-msbuild-log-by-using-the-project-system-tools-extension"></a>Proje sistemi araçları uzantısını kullanarak ikili MSBuild günlüğü oluşturma

1. [Proje sistemi araçları uzantısını](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools)indirin ve yükleyin.

1. Uzantı yüklendikten sonra,   >  **diğer pencereleri** görüntüle menüsünde bazı yeni öğeler görüntülenir.

   ![Diğer pencereler menüsü](../ide/media/view-menu.png)

1.   >    >  Visual Studio 'da **derleme günlüğü** penceresini göstermek için diğer Windows **derlemesi günlüğünü** görüntüle ' yi seçin. Proje sisteminde hem normal hem de tasarım zamanı derlemelerini kaydetmeye başlamak için ilk araç çubuğu simgesini seçin.

   ![Derleme günlüğü penceresi](../ide/media/build-logging-click-to-record.png)

1. Bir yapı kaydedildikten sonra, derleme günlüğü penceresinde görünür. Öğeye sağ tıklayın ve *. binlog* dosyanızı kaydetmek için bağlam menüsünde **günlükleri kaydet** ' i seçin.

   ![Derleme günlüğü bağlam menüsü](../ide/media/build-logging-context-menu.png)

[MSBuild yapılandırılmış günlük görüntüleyicisini](http://www.msbuildlog.com/)kullanarak *. binlog* dosyalarınızı görüntüleyebilir ve arayabilirsiniz.

## <a name="create-a-detailed-log"></a>Ayrıntılı günlük oluşturma

1. Visual Studio ana menüsünde, **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  > **derleme ve çalıştırma**' ya gidin.
1. **MSBuild proje derlemesi ayrıntı düzeyini** her iki Birleşik giriş kutusunda **ayrıntılı** olarak ayarlayın. En üstteki bir denetim **Çıkış penceresi** ayrıntı düzeyi oluşturur ve ikinci bir denetim derleme \<projectname\> sırasında her projenin ara dizininde oluşturulan. log dosyasında ayrıntı düzeyi oluşturur.
2. Visual Studio Geliştirici komut isteminden, şu komutlardan birini girerek gerçek yol ve yapılandırma değerlerinizi değiştirin:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    veya

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    MSBuild 'i çalıştırdığınız dizinde MSBuild. log dosyası oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
