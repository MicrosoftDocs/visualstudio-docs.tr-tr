---
title: Görev öğesi (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9d616e9b3520d3592f3e34a5aa3b95a2c5f722
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304206"
---
# <a name="task-element-msbuild"></a>Görev Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Oluşturur ve yürütür örneği bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görev. Öğe adı, oluşturulan görev adına göre belirlenir.  
  
 \<Proje >  
 \<Hedef >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek koşul. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|İsteğe bağlı öznitelik. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, sonraki görevlerinde [hedef](../msbuild/target-element-msbuild.md) öğesi ile derleme devam yürütülecek ve görevin tüm hataları uyarı olarak kabul edilir.<br />-   **ErrorAndContinue**. Bir görev başarısız olduğunda, sonraki görevlerinde `Target` öğesi ile derleme devam yürütmek ve tüm hataları görev hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, listesindeki kalan görevlere `Target` olmayan öğe ve derleme yürütülür ve tüm `Target` öğesi ve yapı başarısız olduğu değerlendirilir.<br /><br /> .NET Framework 4.5 yalnızca desteklenen önce sürümleri `true` ve `false` değerleri.<br /><br /> Daha fazla bilgi için [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Gerekli görev sınıfının içerir veya daha fazla özellik ile etiketlenmiş `[Required]` özniteliği.<br /><br /> Parametre değeri olarak değerini içeren bir kullanıcı tanımlı görev parametresi. Herhangi bir sayıda parametrelerinde olabilir `Task` her öznitelik eşlemesi görev sınıfının bir .NET özelliğine sahip bir öğe.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Output](../msbuild/output-element-msbuild.md)|Depoları proje dosyasında bir görevden çıkarır. Sıfır veya daha fazla olabilir `Output` görev öğeleri.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Hedef](../msbuild/target-element-msbuild.md)|İçin kapsayıcı öğe [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görevleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `Task` öğesinde bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyası bir görev örneği oluşturur, özellikleri ayarlayan ve yürütür. `Output` Öğesi, özellikler veya başka bir proje dosyasında kullanılacak öğeleri çıkış parametreleri depolar.  
  
 Varsa [OnError](../msbuild/onerror-element-msbuild.md) üst öğeleri `Target` öğesi görev başarısız olursa bir görev, bunlar yine de değerlendirilir ve `ContinueOnError` değeri `false`. Görevler hakkında daha fazla bilgi için bkz. [görevleri](../msbuild/msbuild-tasks.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir örneğini oluşturur [Csc görevi](../msbuild/csc-task.md) sınıfı altı özelliklerini ayarlar ve görev yürütür. Yürütmenin sonrasına, değerini `OutputAssembly` nesnesinin özelliğini adlı bir öğe listesine yerleştirilir `FinalAssemblyName`.  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)



