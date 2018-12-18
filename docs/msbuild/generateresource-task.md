---
title: GenerateResource görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c830b640b3efb4e963d62402bbf68d1bc7dff0e9
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176960"
---
# <a name="generateresource-task"></a>GenerateResource görevi
Arasında dönüştürür *.txt* ve *.resx* (XML tabanlı kaynak biçimi) dosyalarını ve ortak dil çalışma zamanı ikili *.resources* katıştırılabilir bir çalışma zamanı ikili dosyaları yürütülebilir veya uydu derlemeleri içine derlenmiş. Bu görevi genellikle dönüştürmek için kullanılan *.txt* veya *.resx* dosyaları *.resources* dosyaları. `GenerateResource` Görev benzer işlevsellik [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `GenerateResource` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalInputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bu görev tarafından yapılan Bağımlılık denetimi için ek girişler içeriyor. Örneğin, böylece güncelleştirildiğinde, tüm kaynaklar yeniden proje ve hedefleri dosyaları genellikle giriş olmalıdır.|  
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametresi.<br /><br /> Bir dizi ad-değer çiftleri iletilmesi gereken ortam değişkenlerini belirtir için üretilmiş *resgen.exe*, ek olarak (veya seçmeli olarak geçersiz kılma) normal ortam bloğu.|  
|`ExcludedInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> İçinden izlenen girişleri güncel denetimi sırasında yok sayılacak yollarını belirtin öğelerinin bir dizisini belirtir.|  
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, çalışan *tlbimp.exe* ve *aximp.exe* uygun hedef framework çıkış gerekli sarmalayıcı derlemeleri oluşturmak için işlem dışı öğesinden. Bu parametre, çoklu hedefleme tanır `ResolveComReferences`.|  
|`FilesWritten`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Yazılan tüm dosya adlarını içeren diske. Varsa bu önbellek dosyası içerir. Bu parametre, temiz uygulamaları için yararlıdır.|  
|`MinimalRebuildFromTracking`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Alır veya izlenen Artımlı derleme kullanılıp kullanılmayacağını belirten bir anahtar ayarlar. Varsa `true`, artımlı derleme açıktır; Aksi takdirde, yeniden derleme zorlanır.|  
|`NeverLockTypeAssemblies`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Yeni bir oluşturulup oluşturulmayacağını belirten bir Boole değeri alır veya ayarlar [AppDomain](/dotnet/api/system.appdomain) kaynakları değerlendirmek için (*.resx*) dosyaları (true) veya yeni bir [AppDomain](/dotnet/api/system.appdomain) yalnızca kaynak dosyaları (false) bir kullanıcının derleme başvurusu.|  
|`OutputResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Oluşturulan dosyalar gibi belirtir *.resources* dosyaları. Bir ad belirtmezseniz, eşleşen giriş dosyasının adı kullanılır ve *.resources* oluşturulan dosyası, giriş dosyasını içeren dizine yerleştirilir.|  
|`PublicClass`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, bir türü kesin belirlenmiş kaynak sınıfı olarak genel bir sınıf oluşturur.|  
|`References`|İsteğe bağlı `String[]` parametresi.<br /><br /> Başvuru türlerinde yüklenecek *.resx* dosyalarını. *.resx* dosya veri öğeleri, bir .NET türü olabilir. Zaman *.resx* dosya okuma, bu çözümlenmelidir. Genellikle, bu kuralları yükleniyor standart türünü kullanarak başarılı bir şekilde çözülür. Derlemelerde sağlarsanız `References`, bunlar daha önceliklidir.<br /><br /> Bu parametre, kesin olarak belirlenmiş kaynaklar için gerekli değildir.|  
|`SdkToolsPath`|İsteğe bağlı `String` parametresi.<br /><br /> SDK Araçları yolunu gibi belirtir *resgen.exe*.|  
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Öğeleri dönüştürmek için belirtir. Bu parametreye geçirilen öğe, şu dosya uzantılarından biri olmalıdır:<br /><br /> -   *.txt*: dönüştürülecek bir metin dosyası uzantısı belirtir. Metin dosyaları yalnızca dize kaynakları içerebilir.<br />-   *.resx*: dönüştürülecek XML tabanlı kaynak dosyası için bir uzantı belirtir.<br />-   *.restext*: aynı biçimi belirtir *.txt*. Bu farklı uzantı, diğer kaynak dosyaları, yapı işleminizde kaynakları içeren kaynak dosyalarını NET bir ayrım yapmak istiyorsanız kullanışlıdır.<br />-   *.Resources*: dönüştürmek bir kaynak dosya uzantısı belirtir.|  
|`StateFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Bağımlılık bağlantıları denetimi hızlandırmak için kullanılan bir isteğe bağlı önbellek dosyası yolunu belirtir *.resx* giriş dosyaları.|  
|`StronglyTypedClassName`|İsteğe bağlı `String` parametresi.<br /><br /> Türü kesin belirlenmiş kaynak sınıfı için sınıf adını belirtir. Bu parametre belirtilmezse, kaynak dosyanın temel adı kullanılır.|  
|`StronglyTypedFilename`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Kaynak dosyası için dosya adını belirtir. Bu parametre belirtilmezse, sınıfın adını dile bağlı olarak değişir uzantılı temel dosya adı olarak kullanılır. Örneğin: *MyClass.cs*.|  
|`StronglyTypedLanguage`|İsteğe bağlı `String` parametresi.<br /><br /> Kesin olarak belirlenmiş kaynak sınıfı kaynağı oluşturulurken kullanılacak dili belirtir. Bu parametre CodeDomProvider tarafından kullanılan dillerden biriyle tam olarak eşleşmelidir. Örneğin: `VB` veya `C#`.<br /><br /> Bu parametre için bir değer aktararak, türü kesin belirlenmiş kaynak oluşturmak için görev isteyin.|  
|`StronglyTypedManifestPrefix`|İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan sınıfın kaynak türü kesin belirlenmiş bir kaynak için kullanılacak kaynak ad alanı ya da bildirim öneki belirtir.|  
|`StronglyTypedNamespace`|İsteğe bağlı `String` parametresi.<br /><br /> Kesin belirlenmiş bir kaynak için oluşturulan sınıf kaynağı için kullanılacak ad alanını belirtir. Bu parametre belirtilmezse, türü kesin belirlenmiş kaynak genel ad alanında görüntülenir.|  
|`TLogReadFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur parametre.<br /><br /> İzleme günlüklerinin okuma temsil eden öğeleri dizisini alır.|  
|`TLogWriteFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur parametre.<br /><br /> Yazma temsil eden öğelerin bir dizisi izleme günlükleri alır.|  
|`ToolArchitecture`|İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> Belirlemek için kullanılan olup olmadığını *Tracker.exe* üretme kullanılması gereken *ResGen.exe*.<br /><br /> Bir üyesine ayrıştırılabilir olmalıdır <xref:Microsoft.Build.Utilities.ExecutableType> sabit listesi. Varsa `String.Empty`, varsayılan mimariyi belirlemek için bir buluşsal yöntem kullanır. Ayrıştırılabilir Microsoft.Build.Utilities.ExecutableType numaralandırma üyesi olmalıdır.|  
|`TrackerFrameworkPath`|İsteğe bağlı `String` parametresi.<br /><br /> İçeren uygun .NET Framework konumun yolunu belirtir *Yol'dan*.<br /><br /> Ayarlanırsa, kullanıcı, sağlamaktan sorumlu sürüyorsa bit genişliğinde *Yol'dan* bunlar geçmesini bit genişliğinde eşleşen *ResGen.exe* bunlar kullanmayı planladığınız. Aksi durumda kümesi, görev geçerli .NET Framework sürümüne göre uygun konuma karar verir.|  
|`TrackerLogDirectory`|İsteğe bağlı `String` parametresi.<br /><br /> Bu görev çalışmasını izleme günlüklerini yerleştirileceği Ara dizini belirtir.|  
|`TrackerSdkPath`|İsteğe bağlı `String` parametresi.<br /><br /> İçeren uygun Windows SDK'sı konumun yolunu belirtir *Tracker.exe*.<br /><br /> Ayarlanırsa, kullanıcı, sağlamaktan sorumlu sürüyorsa bit genişliğinde *Tracker.exe* bunlar geçmesini bit genişliğinde eşleşen *ResGen.exe* bunlar kullanmayı planladığınız. Aksi durumda kümesi, görev geçerli Windows SDK'sını alan uygun konuma karar verir.|  
|`TrackFileAccess`|İsteğe bağlı <xref:System.Boolean> parametresi.<br /><br /> TRUE ise dizin giriş dosyasının göreli dosya yollarını çözümleme için kullanılır.|  
|`UseSourcePath`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, giriş dosyasının dizini göreli dosya yolları çözümlemek için kullanılması gerektiğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çünkü *.resx* dosyaları bağlantılar içerebilir diğer kaynak dosyaları için basitçe karşılaştırmak yeterli değil *.resx* ve *.resources* dosya çıktısı olup olmadığını görmek için zaman damgası güncel. Bunun yerine, `GenerateResource` görev aşağıdaki bağlantıları *.resx* dosyaları ve bağlantılı damgaları Çıkıştaki dosyaların zaman de denetler. Genel olarak kullanılamaz, yani `Inputs` ve `Outputs` içeren hedef üzerinde öznitelikleri `GenerateResource` görev Bu, gerçekten çalıştırılması gereken zaman Atlanan neden.  
  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
 MSBuild 4.0 hedef .NET 3.5 projelerine kullanırken, derleme üzerinde x86 başarısız olabilir kaynakları. Bu sorunu gidermek için hedef AnyCPU derleme olarak oluşturabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `GenerateResource` oluşturulacak görev *.resources* dosyaları tarafından belirtilen dosyalarını `Resx` öğe koleksiyonu.  
  
```xml  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 `GenerateResource` Kullanan görev \<LogicalName > meta verilerini bir \<EmbeddedResource > öğesini bir derlemede gömülü kaynak adı.  
  
 Aşağıdaki kod, adlı katıştırılmış bir kaynağı oluşturur, derleme myAssembly adlı varsayarak *someQualifier.someResource.resources*:  
  
```xml  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Olmadan \<LogicalName > meta verileri, kaynak adlı *myAssembly.myResource.resources*.  Bu örnekte, yalnızca Visual Basic ve Visual C# yapı işlemi için geçerlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
