---
title: WriteCodeFragment görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6246c66299bb713c8b024feefa12eb883e2c0c76
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231099"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment görevi
Geçici bir kod dosyası belirtilen oluşturulan kod parçasını oluşturur. Dosya silinmez.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `WriteCodeFragment` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AssemblyAttributes`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Yazmak için öznitelikler açıklaması. Öğe `Include` tam tür adı, örneğin, "System.AssemblyVersionAttribute" özniteliğinin değeridir.<br /><br /> Her meta verileri bir parametrenin türü olmalıdır ad-değer çiftidir `String`. Bazı öznitelikler, oluşturucu konumsal bağımsız değişkenleri yalnızca izin verir. Ancak, herhangi bir öznitelik gibi bağımsız değişkenler kullanabilirsiniz. Konumsal Oluşturucusu öznitelikleri ayarlamak için "_Parameter1", "_Parameter2" ve benzeri benzer meta veri adları kullanın.<br /><br /> Bir parametre dizini atlanamaz.|  
|`Language`|Gerekli `String` parametresi.<br /><br /> Kod üretmek için kod dilini belirtir.<br /><br /> `Language` CodeDom sağlayıcısının kullanılabilir olduğu herhangi bir dilde Örneğin, "C#" veya "VisualBasic" olabilir. Bu dil için varsayılan dosya adı uzantısı yayılan dosyası gerekir.|  
|`OutputDirectory`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Oluşturulan kodun, genellikle Ara klasörü hedef klasör belirtir.|  
|`OutputFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Oluşturulan dosyanın yolunu belirtir. Dosya adını kullanarak bu parametre olarak ayarlanırsa hedef klasör dosya adına eklenir. Bir kök kullanarak olarak ayarlanırsa hedef klasöre göz ardı edilir.<br /><br /> Bu parametre ayarlanmazsa, çıktı dosyası adını hedef klasör, rastgele dosya adını ve belirtilen dil için varsayılan dosya adı uzantısı ' dir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tabloda listelenen parametreleri sahip olmaya ek olarak, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)