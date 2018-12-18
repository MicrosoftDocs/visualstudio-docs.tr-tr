---
title: 'Nasıl yapılır: hedefleri ve görevleri yapılandırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce147a9a393b30111f3f76f605e327b70206ad7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49264068"
---
# <a name="how-to-configure-targets-and-tasks"></a>Nasıl Yapılır: Hedefleri ve Görevleri Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bunlar geliştirme bilgisayarının ortamı bağımsız olarak hedef ortamdaki çalıştırmak için seçili MSBuild görevleri ayarlanabilir. Örneğin, bir 64 bit bilgisayar hedefleri 32 bit mimari bir uygulama oluşturmak için kullandığınızda, seçili görevleri bir 32 bit işlemde çalıştırılır.  
  
> [!NOTE]
>  Bir derleme görevi, Visual C# veya Visual Basic gibi bir .NET dilinde yazılmış ve yerel kaynakları veya araçları kullanmaz, uyarlama olmadan herhangi bir hedef bağlamında çalışır.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask öznitelikleri ve görev parametreleri  
 Aşağıdaki `UsingTask` öznitelikleri belirli derleme sürecinde bir görevin tüm işlemleri etkiler:  
  
-   `Runtime` Öznitelik varsa, ortak dil çalışma zamanı (CLR) sürümünü ayarlar ve bu değerlerden herhangi birini alabilir: `CLR2`, `CLR4`, `CurrentRuntime`, veya `*` (çalışma zamanı herhangi).  
  
-   `Architecture` Öznitelik varsa, platform ve bit genişliği ayarlar ve bu değerlerden herhangi birini alabilir: `x86`, `x64`, `CurrentArchitecture`, veya `*` (herhangi bir mimari).  
  
-   `TaskFactory` Özniteliği varsa, ayarlar oluşturur ve görev örneğini çalıştıran ve yalnızca değerini alır görev fabrikasını `TaskHostFactory`. Daha fazla bilgi için bu belgenin sonraki bölümlerinde görev oluşturucular bölümüne bakın.  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Ayrıca `MSBuildRuntime` ve `MSBuildArchitecture` tek bir görev hedef bağlamını ayarlamak için parametreleri.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 MSBuild görevi çalışmadan önce bir eşleştirme için görünüyor `UsingTask` aynı hedef bağlam sahip.  Belirtilen parametreleri `UsingTask` ancak eşleştirilecek karşılık gelen görevin değil olarak kabul edilir.  Görev ancak karşılık gelen içinde belirtilen parametreleri `UsingTask` eşleştirilecek değerlendirilir. Parametre değerlerini ya da belirtilmezse `UsingTask` veya değerleri varsayılan olarak, görev `*` (herhangi bir parametre).  
  
> [!WARNING]
>  Birden fazla ise `UsingTask` var ve tüm eşleşen sahip `TaskName`, `Runtime`, ve `Architecture` öznitelikleri, değerlendirilecek sonuncu diğerleri değiştirir.  
  
 MSBuild görevi parametreleri ayarlarsanız bulmaya çalışır bir `UsingTask` , aşağıdaki parametrelerle eşleşen veya en azından, bunları çakışıyor değil.  Birden fazla `UsingTask` aynı hedef bağlamı belirtebilirsiniz.  Örneğin, farklı bir hedef ortamlar için farklı yürütülebilir dosyaları içeren bir görev bu şuna benzeyebilir:  
  
```  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>Görev Oluşturucular  
 Bir görev çalıştırılmadan önce MSBuild geçerli yazılım bağlamında çalışacak şekilde belirlenmiş olup olmadığını denetler.  Görev şekilde belirlendiyse, MSBuild bunu geçerli işlemde çalışan AssemblyTaskFactory geçirir; Aksi takdirde, MSBuild görevi görev hedef bağlam eşleşen bir işlemde çalıştırır TaskHostFactory geçirir. Geçerli bağlamı ve hedef bağlam aynı olsa bile, çalıştırılacak bir görev zorlayabilirsiniz çıkış ayarlayarak işlem (için yalıtımı, güvenlik veya diğer nedenlerle) `TaskFactory` için `TaskHostFactory`.  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Hayalet görev parametreleri  
 Gibi diğer görev parametreleri, `MSBuildRuntime` ve `MSBuildArchitecture` derleme özelliklerinden ayarlayabilirsiniz.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Diğer görev parametreleri aksine `MSBuildRuntime` ve `MSBuildArchitecture` görev için görünür değildir.  İçinde çalıştığı bağlamı kullanan bir görev yazmak için .NET Framework çağrı yaparak içerik test, veya diğer görev parametreleri aracılığıyla bağlam bilgilerini geçirmek için derleme özelliklerini kullanın.  
  
> [!NOTE]
>  `UsingTask` öznitelikleri araç takımını kullanmanız ve ortam özelliklerinden ayarlayabilirsiniz.  
  
 `MSBuildRuntime` Ve `MSBuildArchitecture` parametreleri hedef bağlam, aynı zamanda en sınırlı kapsamı en esnek bir yolunu sağlar.  Bir yandan, çünkü bunlar görev örneği kendisini ayarlamak ve çalıştırmak üzere görev olana kadar değerlendirilmeyen, değerlendirme süresi hem de derleme sırasında mevcut özelliklerin tam kapsamı değerinden türetebilirsiniz.  Öte yandan, bu parametreler yalnızca belirli bir hedefe bir görev belirli bir örneği için geçerlidir.  
  
> [!NOTE]
>  Görev parametreleri olmayan görev ana bağlamında, üst düğüm bağlamında değerlendirilir. Çalışma zamanı veya mimarisi-(örneğin, Program dosyalarının konumu) bağımlıdır ortam değişkenlerini üst düğümün eşleşen değeri değerlendirir.  Aynı ortam değişkenini görev tarafından doğrudan salt okunursa, ancak bunu doğru görev ana bağlamında değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hedefleri ve Görevleri Yapılandırma](../msbuild/configuring-targets-and-tasks.md)



