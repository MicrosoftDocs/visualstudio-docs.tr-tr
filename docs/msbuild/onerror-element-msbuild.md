---
title: OnError öğesi (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c33f32e46621bb2f56231b2c992712fd42126f1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841396"
---
# <a name="onerror-element-msbuild"></a>OnError öğesi (MSBuild)
Yürütülmek üzere bir veya daha fazla hedef neden `ContinueOnError` özniteliği `false` için başarısız bir görev.  

 \<Proje >  
 \<Hedef >  
 \<OnError >  

## <a name="syntax"></a>Sözdizimi  

```xml  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  

### <a name="attributes"></a>Öznitelikler  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Gerekli öznitelik.<br /><br /> Bir görev başarısız olursa yürütmek için hedefler. Birden çok hedef noktalı virgülle ayırın. Birden çok hedefe, belirtilen sırayla yürütülür.|  

### <a name="child-elements"></a>Alt öğeleri  
 Yok.  

### <a name="parent-elements"></a>Üst öğeler  

| Öğe | Açıklama |
| - | - |
| [Hedef](../msbuild/target-element-msbuild.md) | İçin kapsayıcı öğe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevleri. |

## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] yürütür `OnError` öğe varsa, `Target` öğenin görevler başarısız oluyor `ContinueOnError` özniteliğini `ErrorAndStop` (veya `false`). Görev başarısız olduğunda, belirtilen hedef `ExecuteTargets` özniteliği yürütülür. Varsa birden fazla `OnError` hedef öğesinde `OnError` öğeleri görevi başarısız olduğunda sırayla yürütülür.  

 Hakkında bilgi için `ContinueOnError` özniteliği için bkz: [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). Hedefleri hakkında daha fazla bilgi için bkz: [hedefleri](../msbuild/msbuild-targets.md).  

## <a name="example"></a>Örnek  
 Aşağıdaki kodu çalıştırır `TaskOne` ve `TaskTwo` görevleri. Varsa `TaskOne` başarısız olursa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] değerlendirir `OnError` öğesi ve yürüten `OtherTarget` hedef.  

```xml  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Hedefler](../msbuild/msbuild-targets.md)
