---
title: Görev yazma | Microsoft Docs
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
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8cc7968664f201482647861a031a27c850611c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914716"
---
# <a name="task-writing"></a>Görev Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Görevler, derleme işlemi sırasında çalışan kodu sağlar. Görevleri hedeflerin yer alır. Tipik Görevler içeren bir kitaplık ile birlikte gelir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], ve kendi görevleri de oluşturabilirsiniz. Dahil olan görev Kitaplığı hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], bkz: [görev başvurusu](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Görevler  
 Görevlerin örneklerindendir [kopyalama](../msbuild/copy-task.md), bir veya daha fazla dosyaları kopyalayan [MakeDir](../msbuild/makedir-task.md), bir dizin oluşturur ve [Csc](../msbuild/csc-task.md), hangi derler [!INCLUDE[csprcs](../includes/csprcs-md.md)] kaynak kodu dosyaları. Her görev uygulayan bir .NET sınıfı uygulanır <xref:Microsoft.Build.Framework.ITask> Microsoft.Build.Framework.dll derlemede tanımlanan arabirimi.  
  
 Bir görev uygularken kullanabileceğiniz iki yaklaşım vardır:  
  
- Uygulama <xref:Microsoft.Build.Framework.ITask> doğrudan arabirim.  
  
- Sınıfınıza Yardımcısı sınıfından türetilen <xref:Microsoft.Build.Utilities.Task>, Microsoft.Build.Utilities.dll derlemesinde tanımlanmıştır. Görev ITask uygular ve bazı ITask üyeleri varsayılan uygulamalarını sağlar. Ayrıca, günlük kaydı daha kolay olur.  
  
  Her iki durumda da adlı bir yöntem sınıfa eklemelisiniz `Execute`, görev çalıştırıldığında çağrılan yöntemi. Bu yöntem parametre almayan ve döndüren bir `Boolean` değer: `true` görev başarılı olursa veya `false` başarısız olduğunda. Aşağıdaki örnek, hiçbir eylem gerçekleştirmeyen ve döndüren bir görevi gösterir `true`.  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 Bu görev aşağıdaki proje dosyasını çalıştırır:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Görevler çalıştırıldığında görev sınıfını .NET özellikleri oluşturursanız, bunlar da girişleri Proje dosyasından alabilir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Bu özellikler görevin çağrılmadan hemen önce ayarlar `Execute` yöntemi. Bir dize özelliği oluşturmak için görev kod aşağıdaki gibi kullanın:  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Bu görev ve ayarlar aşağıdaki dosya çalıştırmaları proje `MyProperty` için belirtilen değer:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Görevleri kaydediliyor  
 Bir görev olarak çalıştırmak için bir proje yayınlanıyorsa [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bulma görevi sınıfı içeren derlemeyi bilmeniz gerekir. Görevleri kullanarak kayıtlı [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Microsoft.Common.Tasks dosyasıdır listesini içeren bir proje dosyası `UsingTask` ile sağlanan tüm görevler Kaydet öğeleri [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Bu dosya, her proje oluşturma sırasında otomatik olarak dahil edilir. Microsoft.Common.Tasks içinde kayıtlı bir görevi de geçerli proje dosyasında kayıtlı değilse, geçerli proje dosyası öncelik kazanır; diğer bir deyişle, kendi görevle aynı ada sahip bir varsayılan görev geçersiz kılabilirsiniz.  
  
> [!TIP]
>  İle sağlanan görevlerinin listesini görebilirsiniz [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Microsoft.Common.Tasks içeriğini görüntüleyerek.  
  
## <a name="raising-events-from-a-task"></a>Bir görevden olaylar oluşturma  
 Göreviniz türetildiği varsa <xref:Microsoft.Build.Utilities.Task> yardımcı sınıf kullanabileceğiniz aşağıdaki yardımcı yöntemlerinden herhangi birini üzerinde <xref:Microsoft.Build.Utilities.Task> yakalandı ve herhangi kayıtlı günlükçüleri tarafından görüntülenen olay için sınıf:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Bir görev uygulayacaksa <xref:Microsoft.Build.Framework.ITask> doğrudan, yine de bu olayları tetikleyebilen ancak IBuildEngine arabirimini kullanmanız gerekir. Aşağıdaki örnek, ITask uygular ve özel bir olayı oluşturan bir görev gösterir:  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## <a name="requiring-task-parameters-to-be-set"></a>Ayarlanacak gerektiren görev parametreleri  
 Bu özelliklerin değerlerini görevi çalıştıran herhangi bir proje dosyasını ayarlamanız gerekir ya da yapı başarısız belirli görev özellikleri "gerekli" olarak işaretleyebilirsiniz. Uygulama `[Required]` görev .NET özelliğinin şu şekilde özniteliğini:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` Özniteliği tarafından tanımlanan <xref:Microsoft.Build.Framework.RequiredAttribute> içinde <xref:Microsoft.Build.Framework> ad alanı.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Bu aşağıdaki [!INCLUDE[csprcs](../includes/csprcs-md.md)] sınıfı türetme bir görevi gösterir <xref:Microsoft.Build.Utilities.Task> yardımcı sınıfı. Bu görevi döndürür `true`, işlemin başarılı olduğunu gösteren.  
  
### <a name="code"></a>Kod  
  
```  
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Bu aşağıdaki [!INCLUDE[csprcs](../includes/csprcs-md.md)] sınıfı gösteren bir görevi gerçekleştirme <xref:Microsoft.Build.Framework.ITask> arabirimi. Bu görevi döndürür `true`, işlemin başarılı olduğunu gösteren.  
  
### <a name="code"></a>Kod  
  
```  
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Bu [!INCLUDE[csprcs](../includes/csprcs-md.md)] sınıf türetildiği bir görevi gösterir <xref:Microsoft.Build.Utilities.Task> yardımcı sınıfı. Gerekli dize özelliğine sahiptir ve tüm kayıtlı günlükçüleri tarafından görüntülenen bir olay başlatır.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleTask3#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs#1)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, önceki örnek görev SimpleTask3 çağırma bir proje dosyasını göstermektedir.  
  
### <a name="code"></a>Kod  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



