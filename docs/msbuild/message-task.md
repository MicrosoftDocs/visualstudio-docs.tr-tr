---
title: İleti görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0b61bf9def1ba37667302850527715eed1db4ff
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178338"
---
# <a name="message-task"></a>İleti görevi
Derleme sırasında bir ileti kaydeder.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `Message` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Importance`|İsteğe bağlı `String` parametresi.<br /><br /> İletinin önemini belirtir. Bu parametre değerini alabilir `high`, `normal` veya `low`. Varsayılan değer `normal` şeklindedir.|  
|`Text`|İsteğe bağlı `String` parametresi.<br /><br /> Oturum hata metni.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Message` Görev sağlayan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projeleri günlükçüleri farklı derleme işlemindeki adımları sırasında sorun iletileri.  
  
 Varsa `Condition` parametresi değerlendirilen `true`, değerini `Text` parametresi kaydedilir ve yapı yürütülmeye devam eder. Varsa bir `Condition` parametresi mevcut değil, ileti metnini günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [elde derleme günlükleri](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Varsayılan olarak MSBuild konsol Oluşturucusu'na ileti gönderilir. Bu ayarı değiştirilebilir <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> parametresi. Günlükçü yorumlar `Importance` parametresi.  
  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, tüm kayıtlı günlükçüler için iletileri günlüğe kaydeder.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Derleme günlükleri alın](../msbuild/obtaining-build-logs-with-msbuild.md)