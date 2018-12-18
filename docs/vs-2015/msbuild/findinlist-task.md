---
title: Findınlist görevi | Microsoft Docs
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
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4a9d6a1fc6dbf8f160400ffae10a4a5fb355f3d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206810"
---
# <a name="findinlist-task"></a>FindInList Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Belirtilen bir listede eşleşen itemspec sahip bir öğe bulur.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır [Findınlist görevi](../msbuild/findinlist-task.md).  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`CaseSensitive`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`arama büyük/küçük harfe; Aksi takdirde, bu değildir. Varsayılan değer `true`.|  
|`FindLastMatch`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, son eşleşmenin döndürür; Aksi takdirde, ilk eşleşmeyi döndürür. Varsayılan değer `false`.|  
|`ItemFound`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıkış parametresi.<br /><br /> İlk eşleşen öğe listesinde varsa bulunamadı.|  
|`ItemSpecToFind`|Gerekli `String` parametresi.<br /><br /> Aranacak itemspec.|  
|`List`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> İtemspec için aranacak listesi.|  
|`MatchFileNameOnly`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, yalnızca dosya adı kısmını itemspec karşı eşleşen; Aksi takdirde, tüm itemspec karşı ile eşleşen. Varsayılan değer `true`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



