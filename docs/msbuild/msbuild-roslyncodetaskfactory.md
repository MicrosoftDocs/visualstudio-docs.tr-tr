---
title: MSBuild satır içi görevleri ile RoslynCodeTaskFactory | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 841a7d7bbf10fc4bba5ed99d7ffacf1b76f3a079
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204186"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>MSBuild satır içi görevleri RoslynCodeTaskFactory ile
Benzer şekilde [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory satır içi görevleri olarak kullanım için bellek içi görev derlemeleri oluşturmak için platformlar arası Roslyn derleyicileri kullanır.  RoslynCodeTaskFactory görevleri hedef .NET Standard ve .NET Framework ve .NET Core çalışma zamanlarını ve bunun yanı sıra Linux ve Mac OS gibi diğer platformlarda çalışabilir.

>[!NOTE]
>RoslynCodeTaskFactory, yalnızca MSBuild 15,8 ve sonraki sürümlerde kullanılabilir.
  
## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Satır içi göre RoslynCodeTaskFactory ile yapısı
 RoslynCodeTaskFactory satır içi görevleri bir aynı şekilde bildirilir [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), .NET Standard hedefledikleri olan tek fark.  Satır içi görev ve `UsingTask` içerdiği öğesi genellikle dahil edilecek bir *.targets* dosya ve diğer proje dosyaları gerektiği gibi içeri aktarılan. Temel satır içi görev aşağıda verilmiştir. Hiçbir şey yapmaz dikkat edin.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task does nothing. -->  
  <UsingTask  
    TaskName="DoNothing"  
    TaskFactory="RoslynCodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="" />  
      <Using Namespace="" />  
      <Code Type="Fragment" Language="cs">  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 `UsingTask` Öğesi örnekte, görev ve derlendiğinden satır içi görev fabrikasını tanımlayan üç özniteliklere sahip.  
  
-   `TaskName` Öznitelik adları görev, bu durumda, `DoNothing`.  
  
-   `TaskFactory` Öznitelik adları satır içi görev fabrikasını uygulayan bir sınıf.  
  
-   `AssemblyFile` Özniteliği satır içi görev fabrikasını konumunu sağlar. Alternatif olarak, `AssemblyName` genellikle genel derleme önbelleğinde (GAC) bulunan satır içi görev Fabrika sınıfın tam adını belirtmek için özniteliği.  

Kalan öğeleri `DoNothing` görev boştur ve satır içi göre yapısını ve sırası göstermek için sağlanmıştır. Bu konunun ilerleyen bölümlerinde daha sağlam bir örnek gösterilmektedir.  
  
-   `ParameterGroup` Öğesi, isteğe bağlıdır. Belirtilen görev parametrelerini bildirir. Giriş ve çıkış parametreleri hakkında daha fazla bilgi için bkz. [giriş ve çıkış parametreleri](#input-and-output-parameters) bu konuda.  
  
-   `Task` Öğesi açıklar ve görev kaynak kodunu içerir.  
  
-   `Reference` Kodunuzda kullanmakta olduğunuz .NET derlemesine ilişkin başvurular öğesini belirtir. Bu, Visual Studio'da bir projeye bir başvuru ekleme ile eşdeğerdir. `Include` Özniteliği başvurulan derleme yolunu belirtir.  
  
-   `Using` Öğesi erişmek istediğiniz ad alanları listeler. Bu benzer `Using` Visual C# deyimi. `Namespace` Özniteliği eklemek için ad alanını belirtir.  

`Reference` ve `Using` dilden öğeleridir. Satır içi görevleri desteklenen .NET CodeDom diller, örneğin, Visual Basic veya Visual C# herhangi birinde yazılabilir.  
  
> [!NOTE]
>  Tarafından bulunan öğeleri `Task` öğesi görev fabrikasını için bu durumda, kod görev fabrikasını özeldir.  
  
### <a name="code-element"></a>Kod öğesi  
İçinde görüntülenecek son alt öğenin `Task` öğesi `Code` öğesi. `Code` Öğe içeriyor veya bir görevle derlenecek istediğiniz kodu bulur. Yerleştirme `Code` öğesi nasıl, görev yazmak istediğinize bağlıdır.  

`Language` Özniteliği kodunuzu yazıldığı dili belirtir. Kabul edilebilir değerler `cs` için C# ' ta, `vb` Visual Basic için.  

`Type` Özniteliği bulunan kod türünü belirten `Code` öğesi.  
  
-   Varsa değerini `Type` olduğu `Class`, ardından `Code` öğesi içerir, türetilen bir sınıf için kod <xref:Microsoft.Build.Framework.ITask> arabirimi.  
  
-   Varsa değerini `Type` olduğu `Method`, kodu geçersiz kılma tanımlar `Execute` yöntemi <xref:Microsoft.Build.Framework.ITask> arabirimi.  
  
-   Varsa değerini `Type` olduğu `Fragment`, kodu tanımlayan içeriği sonra `Execute` yöntemi, ancak imza veya `return` deyimi.  

Kod genellikle arasında görünür bir `<![CDATA[` işaret ve `]]>` işaretçisi. Kod bir CDATA bölümde olduğundan, ayrılmış karakterleri kaçış hakkında endişelenmeniz gerekmez "\<" veya ">".  

Alternatif olarak, `Source` özniteliği `Code` göreviniz için kod içeren bir dosya konumunu belirtmek için öğesi. Kaynak dosyada kod tarafından belirtilen türde olması gerekir `Type` özniteliği. Varsa `Source` öznitelik varsa varsayılan değer olan `Type` olduğu `Class`. Varsa `Source` olduğundan, varsayılan değer yoksa `Fragment`.  

> [!NOTE]
>  Görev sınıfın kaynak dosyada tanımlarken, sınıf adı ile kabul etmelisiniz `TaskName` karşılık gelen öznitelik [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi.  
  
## <a name="hello-world"></a>Merhaba Dünya  
 Daha güçlü bir satır içi görev RoslynCodeTaskFactory ile aşağıda verilmiştir. HelloWorld görev görüntüler "Hello, world!" Varsayılan hata günlüğünü cihazda olduğu genellikle sistem konsolu veya Visual Studio **çıkış** penceresi. `Reference` Öğesinde örnek yalnızca gösterim amacıyla dahildir.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task displays "Hello, world!" -->  
  <UsingTask  
    TaskName="HelloWorld"  
    TaskFactory="RoslynCodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>  
      <Using Namespace="System.IO"/>  
      <Code Type="Fragment" Language="cs">  
<![CDATA[  
// Display "Hello, world!"  
Log.LogError("Hello, world!");  
]]>  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  

HelloWorld görev adlı bir dosyaya kaydedebilir *HelloWorld.targets*ve şu şekilde bir projeden çağırın.  

```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## <a name="input-and-output-parameters"></a>Girdi ve çıktı parametreleri  
 Satır içi görev parametreleri alt öğeleri olan bir `ParameterGroup` öğesi. Her parametre tanımlayan öğenin adını alır. Aşağıdaki kod parametresi tanımlar `Text`.  
  
```xml  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  

Parametreler, bir veya daha fazla bu öznitelikler içeriyor olabilir:  

-   `Required` İsteğe bağlı bir öznitelik olduğunu `false` varsayılan olarak. Varsa `true`, parametresi gereklidir ve görev çağrılmadan önce bir değer verilmelidir.  
  
-   `ParameterType` İsteğe bağlı bir öznitelik olduğunu `System.String` varsayılan olarak. Bir öğe ya da bir dize gelen ve giden System.Convert.ChangeType kullanarak dönüştürülebilir bir değer herhangi bir tam türü için ayarlanabilir. (Dış bir görev gelen ve giden geçirilebilen başka bir deyişle, her türlü.)  
  
-   `Output` İsteğe bağlı bir öznitelik olduğunu `false` varsayılan olarak. Varsa `true`, parametre değeri Execute metodundan döndürmeden önce verilmelidir.  

Örneğin,  

```xml  
<ParameterGroup>  
    <Expression Required="true" />  
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
    <Tally ParameterType="System.Int32" Output="true" />  
</ParameterGroup>  
```  

şu üç parametreyi tanımlar:  

-   `Expression` System.String türünde gerekli bir giriş parametresi var.  
  
-   `Files` gerekli öğe listesi giriş parametresi var.  
  
-   `Tally` bir çıktı türü System.Int32 parametresidir.  

Varsa `Code` öğesinin `Type` özniteliği `Fragment` veya `Method`, sonra özellikleri her parametre için otomatik olarak oluşturulur. Aksi takdirde, özellikler, görev kaynak kodunda açıkça bildirilmesi gerekir ve parametre tanımlarını tam olarak eşleşmelidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki satır içi görevin bazı iletileri günlüğe kaydeder ve bir dize döndürür.  
  
```xml  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">  
  
    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>
  
    <Target Name="Demo">  
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>  
</Project>  
```  

Bu satır içi görevleri yolları Birleştir ve dosya adını alın.  

```xml  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">  
  
    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>
  
    <Target Name="Demo">  
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>  
</Project>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [İzlenecek yol: satır içi göre oluşturma](../msbuild/walkthrough-creating-an-inline-task.md)
