---
title: RegisterAssembly görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1e3eb6108ac96716895ff996b043bc486c16e38
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155444"
---
# <a name="registerassembly-task"></a>RegisterAssembly görevi
Belirtilen derleme içindeki meta veriyi okur ve oluşturmak COM istemcilerinin veren kayıt defterine gerekli girişleri ekler [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] şeffaf bir şekilde sınıfları. Bu görevin benzer, ancak aynı, davranıştır [Regasm.exe (derleme kayıt aracı)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `RegisterAssembly` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Assemblies`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Derlemeleri com ile Kaydettirilecek belirtir|  
|`AssemblyListFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Arasında durumu hakkındaki bilgileri içeren `RegisterAssembly` görev ve [UnregisterAssembly](../msbuild/unregisterassembly-task.md) görev. Bu bilgiler engeller `UnregisterAssembly` kaydetmek için başarısız bir derleme kaydını çalışılıyor görevin `RegisterAssembly` görev.|  
|`CreateCodeBase`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, genel derleme önbelleğinde yüklü olmayan bir derleme için dosya yolunu belirtir. kayıt defterinde bir kod temeli girişi oluşturur. Sonrasında genel derleme önbelleğine kaydettiriyor olduğunuz derlemeyi yükleyecekseniz bu seçeneği belirtmemelisiniz.|  
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Belirtilen bütünleştirilmiş koddan oluşturmak için tür kitaplığını belirtir. Üretilmiş tür kitaplığını derleme içinde tanımlanmış erişilebilir türlerin tanımlarını içerir. Tür kitaplığını, aşağıdaki koşullar doğruysa yalnızca oluşturulur:<br /><br /> -Bir tür kitaplığı adının bu konumda mevcut değil.<br />-Bir tür kitaplığı var, ancak geçirilen derlemesinden daha eski.<br /><br /> Tür kitaplığını geçirilen derlemeden daha yeniyse, yeni bir tane oluşturulmaz, ancak derleme hala kaydedilir.<br /><br /> Bu parametre belirtilmezse, aynı sayıda öğe olmalıdır `Assemblies` parametresi veya görev başarısız olur. Giriş belirtilmezse, görev varsayılan derleme adını ve uzantısını öğesinin değiştirin *.tlb*.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `RegisterAssembly` tarafından belirtilen derlemeyi kaydetmek üzere görev `MyAssemblies` öğe koleksiyonu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)