---
title: SGen görevi | Microsoft Docs
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
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9e1d87b895108ac890ace3f077d4c1c0a26d8bf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268040"
---
# <a name="sgen-task"></a>SGen Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir XML serileştirme derleme türleri için belirtilen derlemesinde oluşturur. Bu görevi, XML serileştiricisi Oluşturma Aracı (Sgen.exe) sarmalar. Daha fazla bilgi için [XML serileştiricisi Oluşturma Aracı (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `SGen` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BuildAssemblyName`|Gerekli `String` parametresi.<br /><br /> Serileştirme kod oluşturmak için derleme.|  
|`BuildAssemblyPath`|Gerekli `String` parametresi.<br /><br /> Serileştirme kod oluşturmak için derleme yolu.|  
|`DelaySign`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tam olarak imzalı bir derleme istediğinizi belirtir. Varsa `false`, yalnızca derleme içinde ortak anahtar yerleştirmek istediğinizi belirtir.<br /><br /> Bu parametre ile birlikte kullanılmadığı sürece hiçbir etkisi olmaz `KeyFile` veya `KeyContainer` parametresi.|  
|`KeyContainer`|İsteğe bağlı `String` parametresi.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalar. Görev, ardından son derlemeyi özel anahtarla imzalar.|  
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Bir derlemeyi imzalamak için kullanılacak bir anahtar çifti veya bir ortak anahtar belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar.|  
|`Platform`|İsteğe bağlı `String` parametresi.<br /><br /> Alır veya çıkış derlemesi oluşturmak için kullanılan derleyici platformu ayarlar. Bu parametre değerini alabilir `x86`, `x64`, veya `anycpu`. Varsayılan değer `anycpu`.|  
|`References`|İsteğe bağlı `String[]` parametresi.<br /><br /> XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir.|  
|`SdkToolsPath`|İsteğe bağlı `String` parametresi.<br /><br /> Resgen.exe gibi SDK Araçları yolunu belirtir.|  
|`SerializationAssembly`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Oluşturulan serileştirme bütünleştirilmiş kod içeriyor.|  
|`SerializationAssemblyName`|İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan serileştirme bütünleştirilmiş kodun adını belirtir.|  
|`ShouldGenerateSerializer`|Gerekli `Boolean` parametresi.<br /><br /> Varsa `true`, SGen görevi bir serileştirme derlemesi oluştur.|  
|`Timeout`|İsteğe bağlı `Int32` parametresi.<br /><br /> Sonra yürütülebilir görev sonlandırıldığından, milisaniye cinsinden süre miktarını belirtir. Varsayılan değer `Int.MaxValue`, hiçbir zaman aşımı süresi olduğunu gösterir.|  
|`ToolPath`|İsteğe bağlı `String` parametresi.<br /><br /> Görev temel yürütülebilir dosya (sgen.exe) burada yükleyecek konumu belirtir. Bu parametre belirtilmezse görev çalışıyor framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`Types`|İsteğe bağlı `String[]` parametresi.<br /><br /> Alır veya ayarlar için serileştirme kod oluşturmak için belirli türlerinin bir listesi. SGen bu tür için yalnızca serileştirme kod oluşturur.|  
|`UseProxyTypes`|Gerekli `Boolean` parametresi.<br /><br /> Varsa `true`, SGen görevi XML Web hizmeti proxy türleri için yalnızca serileştirme kod oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.ToolTask> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [MSBuild Kavramları](../msbuild/msbuild-concepts.md)



