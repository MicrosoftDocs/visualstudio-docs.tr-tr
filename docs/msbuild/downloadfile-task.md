---
title: DownloadFile görev | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14b5daafbc4c11547515b9d77be2877eb07bcb8b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945350"
---
# <a name="downloadfile-task"></a>DownloadFile görevi
Köprü Metni Aktarım Protokolü (HTTP) kullanılarak belirtilen dosyaları indirir.

>[!NOTE]
>DownloadFile görev, yalnızca MSBuild 15,8 ve sonraki sürümlerde kullanılabilir.
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `DownloadFile` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`DestinationFileName`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi<br /><br /> İndirilen Dosya için kullanılacak ad.  Varsayılan olarak, dosya adı türetilmiş `SourceUrl` veya uzak sunucu.|
|`DestinationFolder`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Dosyayı indirmek için hedef klasörü belirtir.  Henüz yoksa klasörü oluşturduysanız.|
|`DownloadedFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> İndirilen dosyayı belirtir.|
|`Retries`|İsteğe bağlı `Int32` parametresi.<br /><br /> İndirmek, önceki tüm denemeler başarısız olursa denemek için kaç kez belirtir. Varsayılan olarak sıfırdır.|  
|`RetryDelayMilliseconds`|İsteğe bağlı `Int32` parametresi.<br /><br /> Milisaniye cinsinden gerekli yeniden denemeler arasındaki gecikmeyi belirtir. Varsayılan olarak 5000.|  
|`SkipUnchangedFiles`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, değiştirilmemiş olan dosyalar indiriliyor atlar. Varsayılan olarak `true`. `DownloadFile` Görev, bunlar aynı boyutta varsa ve aynı son değiştirme tarihine göre uzak sunucunun değiştirilmemiş dosyaları dikkate alır. <br /><br />**Not:** dosyaların son değiştirilme tarihini dosyanın yeniden yüklenmesine neden olacak tüm HTTP sunucuları belirtin.|
|`SourceUrl`|Gerekli `String` parametresi.<br /><br /> İndirmek için URL'yi belirtir.|
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir dosya yükler ve içinde içerir `Content` önce projeyi yapılandırma öğeleri.
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>  
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>  

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
