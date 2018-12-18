---
title: MSBuild özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c8835dab5ca866762a7d2b0e6cad1d0d80726b0
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879207"
---
# <a name="msbuild-properties"></a>MSBuild özellikleri
Özellikler, yapıları yapılandırmak için kullanılabilen ad-değer çiftleridir. Özellikler, değerlerin görevlere geçirilmesinde, koşulların değerlendirilmesinde ve proje dosyası boyunca başvurulacak olan değerlerin depolanmasında yararlıdır.  
  
## <a name="define-and-reference-properties-in-a-project-file"></a>Kaynağı tanımlama ve başvurma bir proje dosyası özellikleri  
 Özellikler, özelliğin adı alt öğesi olarak içeren bir öğe oluşturularak bildirilir bir [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) öğesi. Örneğin aşağıdaki XML, bir `BuildDir` değerine sahip olan `Build` adında bir özellik oluşturur.  
  
```xml  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Proje dosyası boyunca özelliklere söz dizimi $ kullanılarak başvurulur (\<PropertyName >). Örneğin, önceki örnekteki özellik $(BuildDir) kullanılarak başvurulur.  
  
 Özelliği yeniden tanımlayarak özellik değerlerini değiştirebilirsiniz. Aşağıdaki XML kullanılarak `BuildDir` özelliğine yeni bir değer verilebilir:  
  
```xml  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Özellikler, proje dosyasında göründükleri sırayla değerlendirilir. `BuildDir` öğesine ait yeni değerin, eski değer atandıktan sonra bildirilmesi gerekir.  
  
## <a name="reserved-properties"></a>Ayrılmış Özellikler  
 MSBuild, proje dosyası ve MSBuild ikili dosyaları hakkındaki bilgileri depolamak için bazı özellik adlarını saklar. Bu özellikler, diğer özelliklere benzer şekilde $ simgesi kullanılarak başvurulur. Örneğin $(MSBuildProjectFile), dosya adı uzantısı dahil olmak üzere proje dosyasının tüm dosya adını döndürür.  
  
 Daha fazla bilgi için [nasıl yapılır: Proje dosyasının konumunu ve adını başvuru](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) ve [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Ortam özellikleri  
 Proje dosyalarındaki ortam değişkenlerine, ayrılmış özelliklere başvurduğunuz şekilde başvurabilirsiniz. Örneğin, proje dosyanızda `PATH` ortam değişkenini kullanmak için, $(Yol) işaretini kullanın. Proje, ortam özelliği ile aynı ada sahip bir özellik tanımı içeriyorsa projedeki özellik, ortam değişkeninin değerini geçersiz kılar.  
  
 Her MSBuild projesi bir yalıtılmış ortam bloğuna sahiptir; yalnızca kendi bloğundaki okumaları ve yazmaları görür.  Proje dosyası değerlendirilmeden veya oluşturulmadan önce MSBuild, özellik koleksiyonunu başlattığında yalnızca ortam değişkenlerini okur. Bunun ardından bu ortam özellikleri statiktir, yani her bir araç aynı adlar ve değerler ile başlar.  
  
 İçinde bir ortam değişkeninin geçerli değerini almak için kullanmak [özellik işlevleri](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. Ancak tercih edilen yöntem, <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> görev parametresinin kullanılmasıdır. Bu dize dizisinde ayarlanan ortam özellikleri, sistem ortamı değişkenlerini etkilemeden oluşturulan araca gönderilebilir.  
  
> [!TIP]
>  Tüm ortam değişkenleri, başlangıç özellikleri olması için okunmaz. Değil geçerli bir MSBuild özellik adı, "386" gibi adları olan tüm ortam değişkenleri göz ardı edilir.  
  
 Daha fazla bilgi için [nasıl yapılır: derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="registry-properties"></a>Kayıt defteri özellikleri  
 Aşağıdaki söz dizimini kullanarak sistem kayıt defteri değerlerini okuyabilirsiniz burada `Hive` kayıt defteri kovanı olduğu (örneğin, **HKEY_LOCAL_MACHINE**), `Key` anahtar adı `SubKey` alt anahtar adı ve `Value`alt değeridir.  
  
```xml  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Varsayılan alt anahtar değerini almak için `Value` öğesini atın.  
  
```xml  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Bu kayıt defteri değeri, bir yapı özelliğini başlatmak için kullanılabilir. Örneğin, Visual Studio web tarayıcısı giriş sayfasını temsil eden bir yapı özelliği oluşturmak için şu kodu kullanın:  
  
```xml  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Genel Özellikler  
 MSBuild kullanarak komut satırındaki özellikleri ayarlamanızı sağlar **-özellik** (veya **-p**) geçin. Bu genel özellik değerleri proje dosyasında ayarlanan özellik değerlerini geçersiz kılar. Bu ortam özellikleri içerir, ancak değiştirilemeyen ayrılmış özellikleri içermez.  
  
 Aşağıdaki örnek genel `Configuration` özelliğini `DEBUG` olarak ayarlar.  
  
```cmd  
msbuild.exe MyProj.proj -p:Configuration=DEBUG  
```  
  
 Genel özellikler, MSBuild görevinin `Properties` özniteliğini kullanarak aynı zamanda çoklu bir proje yapısındaki alt projeler için ayarlanabilir veya değiştirilebilir. Genel özellikler de iletilir alt projeler sürece `RemoveProperties` MSBuild görevinin özniteliği değil iletmek için özelliklerin listesini belirtmek için kullanılır. Daha fazla bilgi için [MSBuild görevi](../msbuild/msbuild-task.md).
  
 Bir proje etiketinde `TreatAsLocalProperty` özniteliğini kullanarak bir özellik belirtirseniz bu genel özellik değeri, proje dosyasında ayarlanan özellik değerini geçersiz kılmaz. Daha fazla bilgi için [proje öğesi (MSBuild)](../msbuild/project-element-msbuild.md) ve [nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Özellik işlevleri  
 .NET Framework sürüm 4'ten başlayarak, MSBuild komut dosyalarınızı değerlendirmek için özellik işlevlerini kullanabilirsiniz. MSBuild görevlerini kullanmadan, yapı komut dosyanızdaki sistem saatini okuyabilir, dizeleri karşılaştırabilir, normal ifadeleri eşleştirebilir ve başka birçok eylemi gerçekleştirebilirsiniz.  
  
 Herhangi bir özelliğin üzerinde gerçekleştirmek için dize (örnek) yöntemlerini kullanabilirsiniz ve birçok sistem sınıfının statik yöntemlerini çağırabilirsiniz. Örneğin, bir yapı özelliğini bugünün tarihine aşağıdaki gibi ayarlayabilirsiniz.  
  
```xml  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Daha fazla bilgi ve özellik işlevlerin bir listesi için bkz: [özellik işlevleri](../msbuild/property-functions.md).  
  
## <a name="create-properties-during-execution"></a>Yürütme sırasında özellikleri oluşturma  
 `Target` öğeleri dışında konumlanan özelliklere, bir yapının değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında özellikler aşağıdaki şekilde oluşturulabilir veya değiştirilebilir:  
  
-   Bir özellik herhangi bir görev tarafından yayılabilir. Bir özellik yaymak için [görev](../msbuild/task-element-msbuild.md) bir alt öğesi olmalıdır [çıkış](../msbuild/output-element-msbuild.md) sahip öğe bir `PropertyName` özniteliği.  
  
-   Bir özellik tarafından yayılabilir [CreateProperty](../msbuild/createproperty-task.md) görev. Bu kullanım önerilmiyor.  
  
-   .NET Framework 3.5'de başlayarak `Target` öğeleri, özellik bildirimlerini içerebilen `PropertyGroup` öğelerini içerebilir.  
  
## <a name="store-xml-in-properties"></a>Store XML özellikleri  
 Özellikler, değerlerin görevlere geçirilmesini veya günlük bilgilerin görüntülenmesini sağlayabilecek rastgele bir XML içerebilir. Aşağıdaki örnek, XML ve diğer özellik başvurularını içeren bir değere sahip olan `ConfigTemplate` özelliğini gösterir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], ilgili özellik değerlerini kullanarak özellik başvurularını değiştirir. Özellik değerleri göründükleri sırayla atanır. Bu nedenle bu örnekte, `$(MySupportedVersion)`, `$(MyRequiredVersion)` ve `$(MySafeMode)` öğelerinin önceden tanımlanmış olması gerekir.  
  
```xml  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)"  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild.md)  
 [Nasıl yapılır: derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md)   
 [Nasıl yapılır: Proje dosyasının konumunu ve adını başvurusu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)   
 [Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)
