---
title: GenerateResource görevi | Microsoft Docs
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
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6686e34ade66a3d4f2ec8ef23c9649bb5d7a1c47
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212504"
---
# <a name="generateresource-task"></a>GenerateResource Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Arasında .txt, .resx (XML tabanlı kaynak biçimi) dosyalarını ve çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemeleri haline getirilebilen ortak dil çalışma zamanı ikili .resources dosyalarına dönüştürür. Bu görev, genellikle için .resource dosyaları .txt veya .resx dosyalarına dönüştürmek için kullanılır. `GenerateResource` Görev benzer işlevsellik [resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `GenerateResource` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalInputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bu görev tarafından yapılan Bağımlılık denetimi için ek girişler içeriyor. Örneğin, böylece güncelleştirildiğinde, tüm kaynaklar yeniden proje ve hedefleri dosyaları genellikle giriş olmalıdır.|  
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametresi.<br /><br /> Belirtir ortam için üretilmiş resgen.exe, ek olarak geçirilmelidir değişkenleri (veya seçmeli olarak geçersiz kılmak) ad-değer çiftleri dizisi normal ortam bloğu.|  
|`ExcludedInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> İçinden izlenen girişleri güncel denetimi sırasında yok sayılacak yollarını belirtin öğelerinin bir dizisini belirtir.|  
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tlbimp.exe ve aximp.exe uygun hedef framework çıkış gerekli sarmalayıcı derlemeleri oluşturmak için işlem dışı çalıştırır. Bu parametre, çoklu hedefleme tanır `ResolveComReferences`.|  
|`FilesWritten`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Yazılan tüm dosya adlarını içeren diske. Varsa bu önbellek dosyası içerir. Bu parametre, temiz uygulamaları için yararlıdır.|  
|`MinimalRebuildFromTracking`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Alır veya izlenen Artımlı derleme kullanılıp kullanılmayacağını belirten bir anahtar ayarlar. Varsa `true`, artımlı derleme açıktır; Aksi takdirde, yeniden derleme zorlanır.|  
|`NeverLockTypeAssemblies`|İsteğe bağlı `Boolean` parametresi.<br /><br /> .Resources dosyaları gibi oluşturulan dosyalarının adını belirtir. Bir ad belirtmezseniz, eşleşen giriş dosyasının adı kullanılır ve oluşturulan bir .resources dosyası, giriş dosyasını içeren dizine yerleştirilir.|  
|`OutputResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> .Resources dosyaları gibi oluşturulan dosyalarının adını belirtir. Bir ad belirtmezseniz, eşleşen giriş dosyasının adı kullanılır ve oluşturulan bir .resources dosyası, giriş dosyasını içeren dizine yerleştirilir.|  
|`PublicClass`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, bir türü kesin belirlenmiş kaynak sınıfı olarak genel bir sınıf oluşturur.|  
|`References`|İsteğe bağlı `String[]` parametresi.<br /><br /> Başvurular, .resx dosyaları içindeki türler yüklenemedi. Resx dosyası veri öğeleri, bir .NET türü olabilir. .Resx dosyasını okuduğunda, bu çözülmesi gerekir. Genellikle, bu kuralları yükleniyor standart türünü kullanarak başarılı bir şekilde çözülür. Derlemelerde sağlarsanız `References`, bunlar daha önceliklidir.<br /><br /> Bu parametre, kesin olarak belirlenmiş kaynaklar için gerekli değildir.|  
|`SdkToolsPath`|İsteğe bağlı `String` parametresi.<br /><br /> Resgen.exe gibi SDK Araçları yolunu belirtir.|  
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Öğeleri dönüştürmek için belirtir. Bu parametreye geçirilen öğe, şu dosya uzantılarından biri olmalıdır:<br /><br /> -   `.txt`: Dönüştürülecek bir metin dosyası uzantısı belirtir. Metin dosyaları yalnızca dize kaynakları içerebilir.<br />-   `.resx`: Dönüştürülecek XML tabanlı kaynak dosyası için bir uzantı belirtir.<br />-   `.restext`: .txt aynı biçimi belirtir. Bu farklı uzantı, diğer kaynak dosyaları, yapı işleminizde kaynakları içeren kaynak dosyalarını NET bir ayrım yapmak istiyorsanız kullanışlıdır.<br />-   `.resources`: Dönüştürmek bir kaynak dosya uzantısı belirtir.|  
|`StateFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Giriş dosyalarını .resx bağlantılar denetimi bağımlılık hızlandırmak için kullanılan bir isteğe bağlı önbellek dosyası yolunu belirtir.|  
|`StronglyTypedClassName`|İsteğe bağlı `String` parametresi.<br /><br /> Türü kesin belirlenmiş kaynak sınıfı için sınıf adını belirtir. Bu parametre belirtilmezse, kaynak dosyanın temel adı kullanılır.|  
|`StronglyTypedFilename`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Kaynak dosyası için dosya adını belirtir. Bu parametre belirtilmezse, sınıfın adını dile bağlı olarak değişir uzantılı temel dosya adı olarak kullanılır. Örneğin: `MyClass.cs`|  
|`StronglyTypedLanguage`|İsteğe bağlı `String` parametresi.<br /><br /> Kesin olarak belirlenmiş kaynak sınıfı kaynağı oluşturulurken kullanılacak dili belirtir. Bu parametre CodeDomProvider tarafından kullanılan dillerden biriyle tam olarak eşleşmelidir. Örneğin: `VB` veya `C#`.<br /><br /> Bu parametre için bir değer aktararak, türü kesin belirlenmiş kaynak oluşturmak için görev isteyin.|  
|`StronglyTypedManifestPrefix`|İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan sınıfın kaynak türü kesin belirlenmiş bir kaynak için kullanılacak kaynak ad alanı ya da bildirim öneki belirtir.|  
|`StronglyTypedNamespace`|İsteğe bağlı `String` parametresi.<br /><br /> Kesin belirlenmiş bir kaynak için oluşturulan sınıf kaynağı için kullanılacak ad alanını belirtir. Bu parametre belirtilmezse, türü kesin belirlenmiş kaynak genel ad alanında görüntülenir.|  
|`TLogReadFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur parametre.<br /><br /> İzleme günlüklerinin okuma temsil eden öğeleri dizisini alır.|  
|`TLogWriteFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur parametre.<br /><br /> Yazma temsil eden öğelerin bir dizisi izleme günlükleri alır.|  
|`ToolArchitecture`|İsteğe bağlı [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametre.<br /><br /> Tracker.exe ResGen.exe üretme kullanılacak gerekli olup olmadığını belirlemek için kullanılır.<br /><br /> Bir üyesine ayrıştırılabilir olmalıdır <xref:Microsoft.Build.Utilities.ExecutableType> sabit listesi. Varsa `String.Empty`, varsayılan mimariyi belirlemek için bir buluşsal yöntem kullanır. Ayrıştırılabilir Microsoft.Build.Utilities.ExecutableType numaralandırma üyesi olmalıdır.|  
|`TrackerFrameworkPath`|İsteğe bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresi.<br /><br /> Yol'dan içeren uygun .NET Framework konumun yolunu belirtir.<br /><br /> Dikkat ederek sorumluluğunu kümesi, kullanıcının aldığı durumlarda bunlar geçirmek Yol'dan mi kullanmak istediğiniz ResGen.exe genişliğinde eşleşir. Aksi durumda kümesi, görev geçerli .NET Framework sürümüne göre uygun konuma karar verir.|  
|`TrackerLogDirectory`|İsteğe bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresi.<br /><br /> Bu görev çalışmasını izleme günlüklerini yerleştirileceği Ara dizini belirtir.|  
|`TrackerSdkPath`|İsteğe bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresi.<br /><br /> Tracker.exe içeren uygun Windows SDK'sı konumun yolunu belirtir.<br /><br /> Dikkat ederek sorumluluğunu kümesi, kullanıcının aldığı durumlarda bunlar geçirmek Tracker.exe mi kullanmak istediğiniz ResGen.exe genişliğinde eşleşir. Aksi durumda kümesi, görev geçerli Windows SDK'sını alan uygun konuma karar verir.|  
|`TrackFileAccess`|İsteğe bağlı [Boolean] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) parametre.<br /><br /> TRUE ise dizin giriş dosyasının göreli dosya yollarını çözümleme için kullanılır.|  
|`UseSourcePath`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, giriş dosyasının dizini göreli dosya yolları çözümlemek için kullanılması gerektiğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .Resx dosyalarını diğer kaynak dosyalarla bağlantılar içeriyor olabileceğinden, çıkışlar güncel olup olmadığını görmek için .resx ve .resource dosyasını zaman damgaları Karşılaştırılacak yeterli değildir. Bunun yerine, `GenerateResource` görev .resx dosyalarındaki bağlantıları izler ve bağlantılı damgaları Çıkıştaki dosyaların zaman de denetler. Genel olarak kullanılamaz, yani `Inputs` ve `Outputs` içeren hedef üzerinde öznitelikleri `GenerateResource` görev Bu, gerçekten çalıştırılması gereken zaman Atlanan neden.  
  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
 MSBuild 4.0 hedef .NET 3.5 projelerine kullanırken, derleme üzerinde x86 başarısız olabilir kaynakları. Bu sorunu gidermek için hedef AnyCPU derleme olarak oluşturabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `GenerateResource` tarafından belirtilen dosyalarını .resources dosyaları üretmek için görev `Resx` öğe koleksiyonu.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 `GenerateResource` Kullanan görev \<LogicalName > meta verilerini bir \<EmbeddedResource > öğesini bir derlemede gömülü kaynak adı.  
  
 Aşağıdaki kod, derleme myAssembly adlı varsayarak someQualifier.someResource.resources adlı katıştırılmış bir kaynağı oluşturur:  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Olmadan \<LogicalName > meta verileri, kaynak adı myAssembly.myResource.resources.  Bu örnekte, yalnızca Visual Basic ve Visual C# yapı işlemi için geçerlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



