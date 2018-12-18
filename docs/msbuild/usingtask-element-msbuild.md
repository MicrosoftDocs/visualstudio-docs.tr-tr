---
title: UsingTask öğesi (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28dba0a2b386cef00daf4827609ce9762c667067
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892967"
---
# <a name="usingtask-element-msbuild"></a>UsingTask öğesi (MSBuild)
Başvurulduğundan görev eşleyen bir [görev](../msbuild/task-element-msbuild.md) görev uygulamasını içeren derlemenin öğesi.  

 \<Proje >  
 \<UsingTask >  

## <a name="syntax"></a>Sözdizimi  

```xml  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  

### <a name="attributes"></a>Öznitelikler  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`AssemblyName`|Her iki `AssemblyName` özniteliği veya `AssemblyFile` özniteliği gereklidir.<br /><br /> Yüklenecek derlemenin adı. `AssemblyName` Özniteliği güçlü adlandırma gerekli olmamasına rağmen tanımlayıcı adlı derlemeler kabul eder. Bu özniteliği kullanarak bir derlemeyi kullanarak yükleme için eşdeğer <xref:System.Reflection.Assembly.Load%2A> .NET yöntemi.<br /><br /> Bu öznitelik, kullanamazsınız `AssemblyFile` özniteliği kullanılır.|  
|`AssemblyFile`|Ya da `AssemblyName` veya `AssemblyFile` özniteliği gereklidir.<br /><br /> Derlemenin dosya yolu. Bu öznitelik, tam yol veya göreli yolları kabul eder. Göreli yolları proje dosyası veya hedefler dosyasının dizinine göreli olduğundan burada `UsingTask` öğesi bildirilir. Bu özniteliği kullanarak bir derlemeyi kullanarak yükleme için eşdeğer <xref:System.Reflection.Assembly.LoadFrom%2A> .NET yöntemi.<br /><br /> Bu öznitelik, kullanamazsınız `AssemblyName` özniteliği kullanılır.|  
|`TaskFactory`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen bir örneğini oluşturmaktan sorumlu bir bütünleştirilmiş kod sınıfı belirtir `Task` adı.  Kullanıcı ayrıca belirtebilir bir `TaskBody` görev fabrikasını alır ve görev oluşturmak için kullandığı bir alt öğesi olarak. İçeriğini `TaskBody` için görev fabrikasını özgüdür.|  
|`TaskName`|Gerekli öznitelik.<br /><br /> Derlemeden başvurulacak görev adı. Belirsizlikler mümkün ise bu öznitelik her zaman tam bir ad belirtmeniz gerekir. Belirsizlikler varsa, MSBuild beklenmeyen sonuçlara neden bir rastgele eşleşme seçer.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Alt öğeleri  

|Öğe|Açıklama|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Oluşturulan bir görev üzerinde görünen parametre kümesi tarafından belirtilen `TaskFactory`.|  
|[Görev](../msbuild/task-element-msbuild.md)|Geçirilen verileri `TaskFactory` görev örneği oluşturmak için.|  

### <a name="parent-elements"></a>Üst öğeler  

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Gerekli kök öğesi bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası. |

## <a name="remarks"></a>Açıklamalar  
 İçinde ortam değişkenleri, komut satırı özelliklerini, proje düzeyi özellikleri ve proje öğelerini başvurulabilir `UsingTask` ya da doğrudan veya bir içeri aktarılan proje dosyası proje dosyasında bulunan öğeleri. Daha fazla bilgi için [görevleri](../msbuild/msbuild-tasks.md).  

> [!NOTE]
>  Proje düzeyi özellikleri ve öğeleri varsa hiçbir anlamı `UsingTask` öğesi birinden geliyor *.tasks* genel olarak MSBuild altyapı kaydedilen dosyalar. Proje düzeyi değerleri MSBuild'e genel değildir.  

 MSBuild 4. 0'da, görevleri kullanarak gelen yüklenebilir *.overridetask* dosyaları.  

## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `UsingTask` öğesi ile bir `AssemblyName` özniteliği.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `UsingTask` öğesi ile bir `AssemblyFile` özniteliği.  

```xml  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
