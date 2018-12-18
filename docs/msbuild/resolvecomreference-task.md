---
title: ResolveComReference görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f13efe45547b657f9e07c12d8eee4160ec7b95e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152405"
---
# <a name="resolvecomreference-task"></a>ResolveComReference görevi
Liste bir veya daha fazla türdeki kitaplık adlarını alır veya *.tlb* dosyaları ve disk üzerindeki konumlara bu tür kitaplıklarını giderir.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `ResolveCOMReference` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`DelaySign`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, ortak anahtarı derlemesinde yerleştirir. Varsa `false`, tam olarak derlemeyi imzalar.|  
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametresi.<br /><br /> Ortam değişkenleri, eşittir işareti ile ayrılmış çiftleri dizisi. Bu değişkenler geçirilir için üretilmiş *tlbimp.exe* ve *aximp.exe* ayrıca çok ya da seçmeli olarak, normal bir ortam bloğuna geçersiz kılma...|  
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, çalışan *tlbimp.exe* ve *aximp.exe* uygun hedef framework çıkış gerekli sarmalayıcı derlemeleri oluşturmak için işlem dışı öğesinden. Bu parametre, çoklu sürüm desteği sağlar.|  
|`IncludeVersionInInteropName`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, typelib sürümü sarmalayıcı adı dahil edilir. Varsayılan, `false` değeridir.|  
|`KeyContainer`|İsteğe bağlı `String` parametresi.<br /><br /> Tutan bir ortak/özel anahtar çifti kapsayıcı belirtir.|  
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Bir ortak/özel anahtar çifti içeren bir öğeyi belirtir.|  
|`NoClassMembers`|İsteğe bağlı `Boolean`parametresi.|  
|`ResolvedAssemblyReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çözümlenen derleme başvurularını belirtir.|  
|`ResolvedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bu görev için giriş olarak sağlanan tür kitaplıklarının fiziksel konuma karşılık gelen tam dosyaları diskte belirtir.|  
|`ResolvedModules`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametresi.|  
|`SdkToolsPath`|İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> Varsa `ExecuteAsTool` olduğu `true`, bu parametre, hedeflenen framework sürümü için SDK araçlarını yola ayarlamanız gerekir.|  
|`StateFile`|İsteğe bağlı `String` parametresi.<br /><br /> COM bileşeni zaman damgaları için önbellek dosyası belirtir. Her çalıştırma, yoksa tüm sarmalayıcıları yeniden oluşturulacak.|  
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametresi.<br /><br /> Proje hedef framework sürümünü belirtir.<br /><br /> Varsayılan, `String.Empty` değeridir. Hedef framework'ü temel bir başvuru için filtre yoktur anlamına gelir.|  
|`TargetProcessorArchitecture`|İsteğe bağlı `String` parametresi.<br /><br /> Tercih edilen hedef İşlemci mimarisi belirtir. Geçirilen *tlbimp.exe*  /bayrağı makine çevirisi sonra.<br /><br /> Parametre değeri bir üyesi olmalıdır <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> COM başvuruları tür kitaplığı dosyası yolunu belirtir. Bu parametrede bulunan öğelerin öğe meta verileri içerebilir. Daha fazla bilgi için bkz [TypeLibFiles meta veri öğesi](#typelibfiles-item-metadata) aşağıda.|  
|`TypeLibNames`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Çözümlenecek tür kitaplığı adları belirtir. Bu parametrede bulunan öğelerin, bazı öğe meta verileri içermelidir. Daha fazla bilgi için bkz [TypeLibNames meta veri öğesi](#typelibnames-item-metadata) aşağıda.|  
|`WrapperOutputDirectory`|İsteğe bağlı `String` parametresi.<br /><br /> Disk üzerindeki oluşturulan birlikte çalışma derlemesi yerleştirildiği konum. Bu öğe meta verileri belirtilmezse görev proje dosyasının bulunduğu dizinin mutlak yolu kullanır.|  
  
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
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [görev taban sınıfı](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)