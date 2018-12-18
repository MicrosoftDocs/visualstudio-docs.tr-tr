---
title: ResolveComReference görevi | Microsoft Docs
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
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf70e5c2fe77f275f31ed9966df262d64ed2c23d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179367"
---
# <a name="resolvecomreference-task"></a>ResolveComReference Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir veya daha fazla tür kitaplığı adları veya .tlb dosyaları listesini alır ve bu tür kitaplıklarını disk üzerindeki konumlara giderir.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `ResolveCOMReference` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`DelaySign`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, ortak anahtarı derlemesinde yerleştirir. Varsa `false`, tam olarak derlemeyi imzalar.|  
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametresi.<br /><br /> Ortam değişkenleri, eşittir işareti ile ayrılmış çiftleri dizisi. Bu değişkenler üretilmiş tlbimp.exe ve ek olarak aximp.exe geçirilen veya seçmeli olarak geçersiz kılma, normal ortam engelleme...|  
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tlbimp.exe ve aximp.exe uygun hedef framework çıkış gerekli sarmalayıcı derlemeleri oluşturmak için işlem dışı çalıştırır. Bu parametre, çoklu sürüm desteği sağlar.|  
|`IncludeVersionInInteropName`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, typelib sürümü sarmalayıcı adı dahil edilir. Varsayılan, `false` değeridir.|  
|`KeyContainer`|İsteğe bağlı `String` parametresi.<br /><br /> Ortak/özel bir arada tutan bir kapsayıcıdır belirtir<br /><br /> anahtar çifti.|  
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Bir ortak/özel içeren bir öğeyi belirtir<br /><br /> anahtar çifti.|  
|`NoClassMembers`|İsteğe bağlı `Boolean`parametresi.|  
|`ResolvedAssemblyReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çözümlenen derleme başvurularını belirtir.|  
|`ResolvedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bu görev için giriş olarak sağlanan tür kitaplıklarının fiziksel konuma karşılık gelen tam dosyaları diskte belirtir.|  
|`ResolvedModules`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametresi.|  
|`SdkToolsPath`|İsteğe bağlı [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametre.<br /><br /> Varsa `ExecuteAsTool` olduğu `true`, bu parametre, hedeflenen framework sürümü için SDK araçlarını yola ayarlamanız gerekir.|  
|`StateFile`|İsteğe bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresi.<br /><br /> COM bileşeni zaman damgaları için önbellek dosyası belirtir. Her çalıştırma, yoksa tüm sarmalayıcıları yeniden oluşturulacak.|  
|`TargetFrameworkVersion`|İsteğe bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresi.<br /><br /> Proje hedef framework sürümünü belirtir.<br /><br /> Varsayılan, `String.Empty` değeridir. Hedef framework'ü temel bir başvuru için filtre yoktur anlamına gelir.|  
|`TargetProcessorArchitecture`|İsteğe bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresi.<br /><br /> Tercih edilen hedef İşlemci mimarisi belirtir. Tlbimp.exe/Machine bayrak sonra çeviri geçirildi.<br /><br /> Parametre değeri bir üyesi olmalıdır <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> COM başvuruları tür kitaplığı dosyası yolunu belirtir. Bu parametrede bulunan öğelerin öğe meta verileri içerebilir. Daha fazla bilgi için "TypeLibFiles öğe meta verileri" aşağıdaki bölüme bakın.|  
|`TypeLibNames`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Çözümlenecek tür kitaplığı adları belirtir. Bu parametrede bulunan öğelerin, bazı öğe meta verileri içermelidir. Daha fazla bilgi için "TypeLibNames öğe meta verileri" aşağıdaki bölüme bakın.|  
|`WrapperOutputDirectory`|İsteğe bağlı `String` parametresi.<br /><br /> Disk üzerindeki oluşturulan birlikte çalışma derlemesi yerleştirildiği konum. Bu öğe meta verileri belirtilmezse görev proje dosyasının bulunduğu dizinin mutlak yolu kullanır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="typelibnames-item-metadata"></a>TypeLibNames öğe meta verileri  
 Geçirilen öğeleri için öğe meta verileri kullanılabilir aşağıdaki tabloda açıklanmıştır `TypeLibNames` parametresi.  
  
|Meta Veriler|Açıklama|  
|--------------|-----------------|  
|`GUID`|Öğe meta verileri gerekir.<br /><br /> Tür kitaplığı için GUID. Bu öğe meta verileri belirtilmezse, görev başarısız olur.|  
|`VersionMajor`|Öğe meta verileri gerekir.<br /><br /> Tür kitaplığının ana sürümü. Bu öğe meta verileri belirtilmezse, görev başarısız olur.|  
|`VersionMinor`|Öğe meta verileri gerekir.<br /><br /> Tür kitaplığının bir alt sürümü. Bu öğe meta verileri belirtilmezse, görev başarısız olur.|  
|`LocaleIdentifier`|İsteğe bağlı öğe meta verileri.<br /><br /> Yerel ayar tanımlayıcı (veya LCID) tür kitaplığı için. Bu, bir kullanıcı, bölge veya uygulama tarafından tercih edilen İnsan dil tanımlayan bir 32-bit değeri olarak belirtilir. Bu öğe meta verileri belirtilmezse görev bir varsayılan yerel ayar tanımlayıcı "0" kullanır.|  
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcısı oluşturmak için kullanılan sarmalayıcı aracı belirtir. Bu öğe meta verileri belirtilmezse görev "tlbimp", varsayılan bir sarmalayıcı aracı kullanır. Typelibs'ın büyük/küçük harf duyarsız, kullanılabilir seçenekler şunlardır:<br /><br /> -   `Primary`: Bu sarmalayıcı aracı zaten oluşturulmuş birincil birlikte çalışma derlemesi için COM bileşeni kullanmak istediğinizde kullanın. Bu sarmalayıcı aracı kullandığınızda, görev başarısız olmasına neden olacağından bir sarmalayıcı çıktı dizini belirtmeyin.<br />-   `TLBImp`: Bir COM bileşeni birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracı kullanın.<br />-   `AXImp`: Bir ActiveX denetimi için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracı kullanın.|  
  
## <a name="typelibfiles-item-metadata"></a>TypeLibFiles öğe meta verileri  
 Geçirilen öğeleri için öğe meta verileri kullanılabilir aşağıdaki tabloda açıklanmıştır `TypeLibFiles` parametresi.  
  
|Meta Veriler|Açıklama|  
|--------------|-----------------|  
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcısı oluşturmak için kullanılan sarmalayıcı aracı belirtir. Bu öğe meta verileri belirtilmezse görev "tlbimp", varsayılan bir sarmalayıcı aracı kullanır. Typelibs'ın büyük/küçük harf duyarsız, kullanılabilir seçenekler şunlardır:<br /><br /> -   `Primary`: Bu sarmalayıcı aracı zaten oluşturulmuş birincil birlikte çalışma derlemesi için COM bileşeni kullanmak istediğinizde kullanın. Bu sarmalayıcı aracı kullandığınızda, görev başarısız olmasına neden olacağından bir sarmalayıcı çıktı dizini belirtmeyin.<br />-   `TLBImp`: Bir COM bileşeni birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracı kullanın.<br />-   `AXImp`: Bir ActiveX denetimi için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracı kullanın.|  
  
> [!NOTE]
>  Büyük bir tür kitaplığı görevi doğru dosyanın disk üzerinde çözümlenmesi olasılığını benzersiz şekilde tanımlamak için sağladığınız daha fazla bilgi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [görev temel sınıf](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



