---
title: OnError öğesi (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f89d21441418ae0b5c267c0fea7e8451115afe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228715"
---
# <a name="onerror-element-msbuild"></a>OnError Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Yürütülmek üzere bir veya daha fazla hedef neden `ContinueOnError` özniteliği `false` için başarısız bir görev.  
  
 \<Proje >  
 \<Hedef >  
 \<OnError >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Gerekli öznitelik.<br /><br /> Bir görev başarısız olursa yürütmek için hedefler. Birden çok hedef noktalı virgülle ayırın. Birden çok hedefe, belirtilen sırayla yürütülür.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Hedef](../msbuild/target-element-msbuild.md)|İçin kapsayıcı öğe [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görevleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] yürütür `OnError` öğe varsa, `Target` öğenin görevler başarısız oluyor `ContinueOnError` özniteliğini `ErrorAndStop` (veya `false`). Görev başarısız olduğunda, belirtilen hedef `ExecuteTargets` özniteliği yürütülür. Varsa birden fazla `OnError` hedef öğesinde `OnError` öğeleri görevi başarısız olduğunda sırayla yürütülür.  
  
 Hakkında bilgi için `ContinueOnError` özniteliği için bkz: [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). Hedefleri hakkında daha fazla bilgi için bkz: [hedefleri](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu çalıştırır `TaskOne` ve `TaskTwo` görevleri. Varsa `TaskOne` başarısız olursa [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] değerlendirir `OnError` öğesi ve yürüten `OtherTarget` hedef.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Hedefler](../msbuild/msbuild-targets.md)



