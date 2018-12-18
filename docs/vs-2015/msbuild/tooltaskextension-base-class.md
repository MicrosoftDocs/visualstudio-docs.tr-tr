---
title: ToolTaskExtension taban sınıfı | Microsoft Docs
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
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa6ec44c857d8b8e229d8f34658e8a9d448fcb19
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221292"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension Taban Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Birçok görevi devralacak <xref:Microsoft.Build.Tasks.ToolTaskExtension> öğesinden devralan sınıf <xref:Microsoft.Build.Utilities.ToolTask> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu devralma zincirini aktarımlar görevleri birkaç parametre ekler. Bu parametreler, bu belgede listelenir.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda temel sınıflarının parametreler açıklanmıştır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine> parametresi.<br /><br /> Görevler için kullanılabilir derleme altyapısı arabirimi belirtir. Yapı altyapısının geri içine çağırmak görevlere izin vermek için bu parametreyi otomatik olarak ayarlar.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine2> parametresi.<br /><br /> Görevler için kullanılabilir derleme altyapısı arabirimi belirtir. Yapı altyapısının geri içine çağırmak görevlere izin vermek için bu parametreyi otomatik olarak ayarlar.<br /><br /> Bu sınıftan devralmayı görev yazarları, değerinden dönüştürme gerekmez. böylece bu kullanışlı bir özelliktir `IBuildEngine` için `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine3> parametresi.<br /><br /> Ana bilgisayar tarafından sağlanan yapı altyapısı arabirimi belirtir.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A>|İsteğe bağlı `bool` parametresi.<br /><br /> Ayarlandığında `true`, bu görev geçişlerini **/Q** cmd.exe komut satırı sağlayacak şekilde komut satırı stdout kopyalanmaz.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>|İsteğe bağlı `String` dizi parametresi.<br /><br /> Ortam değişkenleri, eşittir işareti ile ayrılmış çiftleri dizisi. Bu değişkenler, geçirilen ek olarak üretilmiş yürütülebilir dosya ya da seçmeli olarak geçersiz kılma normal ortam bloğu.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A>|İsteğe bağlı `Int32` çıkış parametresi salt okunur.<br /><br /> Yürütülen komutun tarafından sağlanan çıkış kodu belirtir. Görev hataları günlüğe, ancak çıkış kodu 0 (başarılı) işlem gerekiyordu, bu -1 olarak ayarlanır.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskHost> parametresi.<br /><br /> (Null olabilir) konak nesne örneğini belirtir. Yapı altyapısının, IDE konak bir konak nesnesi bu belirli görev ile ilişkili varsa bu özelliği ayarlar.|  
|<xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A>|İsteğe bağlı <xref:Microsoft.Build.Utilities.TaskLoggingHelper> salt okunur parametre.<br /><br /> Örneğini alır bir <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> görev günlük yöntemlerini içeren sınıf.|  
|<xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A>|Seçenek `bool` parametresi.<br /><br /> Varsa `true`, standart hata akışına alınan tüm iletileri, hata olarak kaydedilir.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A>|İsteğe bağlı `String` parametresi.<br /><br /> Standart çıkış akışı'ndan metin oturum kullanılacak önemi.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A>|İsteğe bağlı `String` parametresi.<br /><br /> Standart çıkış akışı'ndan metin oturum kullanılacak önemi.|  
|<xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A>|İsteğe bağlı sanal `Int32` parametresi.<br /><br /> Sonra yürütülebilir görev sonlandırıldığından, milisaniye cinsinden süre miktarını belirtir. Varsayılan değer `Int.MaxValue`, hiçbir zaman aşımı süresi olduğunu gösterir. Zaman aşımını milisaniye cinsindendir.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A>|İsteğe bağlı sanal `string` parametresi.<br /><br /> Projeleri, bu bir ToolName geçersiz kılmak için uygulayabilir. Görevler bu ToolName korumak için geçersiz kılabilir.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A>|İsteğe bağlı `string` parametresi.<br /><br /> Burada temel yürütülebilir dosya görev yükler konumu belirtir. Bu parametre belirtilmezse görev çalışıyor framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|<xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A>|İsteğe bağlı `bool` parametresi.<br /><br /> Ayarlandığında `true`, bu görev, komut satırı için bir toplu iş dosyası oluşturur ve bu komutu yürütmek yerine doğrudan komut işleyicisi kullanarak yürütür.|  
|<xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A>|İsteğe bağlı `bool` parametresi.<br /><br /> Ayarlandığında `true`, görevi yürüttüğünde bu görevi düğümü verir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)



