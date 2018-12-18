---
title: MSBuild satır içi görevleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f210aa8e33859f41046edc8e524cbfbeaf5417b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898622"
---
# <a name="msbuild-inline-tasks"></a>MSBuild Satır İçi Görevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild görevleri, derleme uygulayan bir sınıf tarafından genellikle oluşturulur <xref:Microsoft.Build.Framework.ITask> arabirimi. Daha fazla bilgi için [görevleri](../msbuild/msbuild-tasks.md).  
  
 .NET Framework sürüm 4 başlayarak, proje dosyasında görevleri satır içi oluşturabilirsiniz. Görev barındırmak için ayrı bir derleme oluşturmak zorunda değildir. Bu, kaynak kodu izlemek daha kolay ve görev dağıtmayı daha kolay hale getirir. Kaynak kodunu komut dosyasında tümleşiktir.  
  
## <a name="the-structure-of-an-inline-task"></a>Satır içi göre yapısı  
 Satır içi görev tarafından bulunan bir [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi. Satır içi görev ve `UsingTask` içerdiği öğesi genellikle bir .targets dosyasında bulunur ve diğer proje dosyaları gerektiği gibi içeri aktarılan. Temel satır içi görev aşağıda verilmiştir. Hiçbir şey yapmaz dikkat edin.  
  
```  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task does nothing. -->  
  <UsingTask  
    TaskName="DoNothing"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll" >  
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
  
- `TaskName` Öznitelik adları görev, bu durumda, `DoNothing`.  
  
- `TaskFactory` Öznitelik adları satır içi görev fabrikasını uygulayan bir sınıf.  
  
- `AssemblyFile` Özniteliği satır içi görev fabrikasını konumunu sağlar. Alternatif olarak, `AssemblyName` genellikle genel derleme önbelleğinde (GAC) bulunan satır içi görev Fabrika sınıfın tam adını belirtmek için özniteliği.  
  
  Kalan öğeleri `DoNothing` görev boştur ve satır içi göre yapısını ve sırası göstermek için sağlanmıştır. Bu konunun ilerleyen bölümlerinde daha sağlam bir örnek gösterilmektedir.  
  
- `ParameterGroup` Öğesi, isteğe bağlıdır. Belirtilen görev parametrelerini bildirir. Giriş ve çıkış parametreleri hakkında daha fazla bilgi için "Giriş ve çıkış parametreleri" bölümüne bakın.  
  
- `Task` Öğesi açıklar ve görev kaynak kodunu içerir.  
  
- `Reference` Kodunuzda kullanmakta olduğunuz .NET derlemesine ilişkin başvurular öğesini belirtir. Bu, Visual Studio'da bir projeye bir başvuru ekleme ile eşdeğerdir. `Include` Özniteliği başvurulan derleme yolunu belirtir.  
  
- `Using` Öğesi erişmek istediğiniz ad alanları listeler. Bu benzer `Using` Visual C# deyimi. `Namespace` Özniteliği eklemek için ad alanını belirtir.  
  
  `Reference` ve `Using` dilden öğeleridir. Satır içi görevleri desteklenen .NET CodeDom diller, örneğin, Visual Basic veya Visual C# herhangi birinde yazılabilir.  
  
> [!NOTE]
>  Tarafından bulunan öğeleri `Task` öğesi görev fabrikasını için bu durumda, kod görev fabrikasını özeldir.  
  
### <a name="code-element"></a>Code Öğesi  
 İçinde görüntülenecek son alt öğenin `Task` öğesi `Code` öğesi. `Code` Öğe içeriyor veya bir görevle derlenecek istediğiniz kodu bulur. Yerleştirme `Code` öğesi nasıl, görev yazmak istediğinize bağlıdır.  
  
 `Language` Özniteliği kodunuzu yazıldığı dili belirtir. Kabul edilebilir değerler `cs` için C# ' ta, `vb` Visual Basic için.  
  
 `Type` Özniteliği bulunan kod türünü belirten `Code` öğesi.  
  
- Varsa değerini `Type` olduğu `Class`, ardından `Code` öğesi içerir, türetilen bir sınıf için kod <xref:Microsoft.Build.Framework.ITask> arabirimi.  
  
- Varsa değerini `Type` olduğu `Method`, kodu geçersiz kılma tanımlar `Execute` yöntemi <xref:Microsoft.Build.Framework.ITask> arabirimi.  
  
- Varsa değerini `Type` olduğu `Fragment`, kodu tanımlayan içeriği sonra `Execute` yöntemi, ancak imza veya `return` deyimi.  
  
  Kod genellikle arasında görünür bir `<![CDATA[` işaret ve `]]>` işaretçisi. Kod bir CDATA bölümde olduğundan, ayrılmış karakterleri kaçış hakkında endişelenmeniz gerekmez "\<" veya ">".  
  
  Alternatif olarak, `Source` özniteliği `Code` göreviniz için kod içeren bir dosya konumunu belirtmek için öğesi. Kaynak dosyada kod tarafından belirtilen türde olması gerekir `Type` özniteliği. Varsa `Source` öznitelik varsa varsayılan değer olan `Type` olduğu `Class`. Varsa `Source` olduğundan, varsayılan değer yoksa `Fragment`.  
  
> [!NOTE]
>  Görev sınıfın kaynak dosyada tanımlarken, sınıf adı ile kabul etmelisiniz `TaskName` karşılık gelen öznitelik [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi.  
  
## <a name="hello-world"></a>Merhaba Dünya  
 Daha güçlü bir satır içi görev aşağıda verilmiştir. HelloWorld görev görüntüler "Hello, world!" Varsayılan hata günlüğünü cihazda olduğu genellikle sistem konsolu veya Visual Studio **çıkış** penceresi. `Reference` Öğesinde örnek yalnızca gösterim amacıyla dahildir.  
  
```  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task displays "Hello, world!" -->  
  <UsingTask  
    TaskName="HelloWorld"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
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
  
 HelloWorld görev HelloWorld.targets adlı bir dosyaya kaydedin ve şu şekilde bir projeden çağırmak.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## <a name="input-and-output-parameters"></a>Giriş ve çıkış parametreleri  
 Satır içi görev parametreleri alt öğeleri olan bir `ParameterGroup` öğesi. Her parametre tanımlayan öğenin adını alır. Aşağıdaki kod parametresi tanımlar `Text`.  
  
```  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  
  
 Parametreler, bir veya daha fazla bu öznitelikler içeriyor olabilir:  
  
- `Required` İsteğe bağlı bir öznitelik olduğunu `false` varsayılan olarak. Varsa `true`, parametresi gereklidir ve görev çağrılmadan önce bir değer verilmelidir.  
  
- `ParameterType` İsteğe bağlı bir öznitelik olduğunu `System.String` varsayılan olarak. Bir öğe ya da bir dize gelen ve giden System.Convert.ChangeType kullanarak dönüştürülebilir bir değer herhangi bir tam türü için ayarlanabilir. (Dış bir görev gelen ve giden geçirilebilen başka bir deyişle, her türlü.)  
  
- `Output` İsteğe bağlı bir öznitelik olduğunu `false` varsayılan olarak. Varsa `true`, parametre değeri Execute metodundan döndürmeden önce verilmelidir.  
  
  Örneğin,  
  
```  
<ParameterGroup>  
    <Expression Required="true" />  
      <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
    <Tally ParameterType="System.Int32" Output="true" />  
</ParameterGroup>  
```  
  
 şu üç parametreyi tanımlar:  
  
- `Expression` System.String türünde gerekli bir giriş parametresi var.  
  
- `Files` gerekli öğe listesi giriş parametresi var.  
  
- `Tally` bir çıktı türü System.Int32 parametresidir.  
  
  Varsa `Code` öğesinin `Type` özniteliği `Fragment` veya `Method`, sonra özellikleri her parametre için otomatik olarak oluşturulur. Aksi takdirde, özellikler, görev kaynak kodunda açıkça bildirilmesi gerekir ve parametre tanımlarını tam olarak eşleşmelidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki satır içi görev her geçtiği yeri söz konusu dosyanın belirtecinde verilen değeri ile değiştirir.  
  
```  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="12.0">  
  
  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll">  
    <ParameterGroup>  
      <Path ParameterType="System.String" Required="true" />  
      <Token ParameterType="System.String" Required="true" />  
      <Replacement ParameterType="System.String" Required="true" />  
    </ParameterGroup>  
    <Task>  
      <Code Type="Fragment" Language="cs"><![CDATA[  
string content = File.ReadAllText(Path);  
content = content.Replace(Token, Replacement);  
File.WriteAllText(Path, content);  
  
]]></Code>  
    </Task>  
  </UsingTask>  
  
  <Target Name='Demo' >  
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [İzlenecek Yol: Satır İçi Göre Oluşturma](../msbuild/walkthrough-creating-an-inline-task.md)



