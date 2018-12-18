---
title: MSBuild Properties1 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c839cebc63e14490f8793feffd4580798779288
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199283"
---
# <a name="msbuild-properties1"></a>MSBuild Properties1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Özellikler, yapıları yapılandırmak için kullanılabilen ad-değer çiftleridir. Özellikler, değerlerin görevlere geçirilmesinde, koşulların değerlendirilmesinde ve proje dosyası boyunca başvurulacak olan değerlerin depolanmasında yararlıdır.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>Bir Proje Dosyasındaki Özellikleri Tanımlama ve Başvurma  
 Özellikler, özelliğin adı alt öğesi olarak içeren bir öğe oluşturularak bildirilir bir [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) öğesi. Örneğin aşağıdaki XML, bir `BuildDir` değerine sahip olan `Build` adında bir özellik oluşturur.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Proje dosyası boyunca özelliklere $(`PropertyName`) söz dizimi kullanılarak başvurulur. Örneğin, önceki örnekteki özellik $(BuildDir) kullanılarak başvurulur.  
  
 Özelliği yeniden tanımlayarak özellik değerlerini değiştirebilirsiniz. Aşağıdaki XML kullanılarak `BuildDir` özelliğine yeni bir değer verilebilir:  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Özellikler, proje dosyasında göründükleri sırayla değerlendirilir. `BuildDir` öğesine ait yeni değerin, eski değer atandıktan sonra bildirilmesi gerekir.  
  
## <a name="reserved-properties"></a>Ayrılmış Özellikler  
 MSBuild, proje dosyası ve MSBuild ikili dosyaları hakkındaki bilgileri depolamak için bazı özellik adlarını saklar. Bu özellikler, diğer özelliklere benzer şekilde $ simgesi kullanılarak başvurulur. Örneğin $(MSBuildProjectFile), dosya adı uzantısı dahil olmak üzere proje dosyasının tüm dosya adını döndürür.  
  
 Daha fazla bilgi için [nasıl yapılır: Proje dosyasının konumunu ve adını başvuru](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) ve [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Ortam Özellikleri  
 Proje dosyalarındaki ortam değişkenlerine, ayrılmış özelliklere başvurduğunuz şekilde başvurabilirsiniz. Örneğin, proje dosyanızda `PATH` ortam değişkenini kullanmak için, $(Yol) işaretini kullanın. Proje, ortam özelliği ile aynı ada sahip bir özellik tanımı içeriyorsa projedeki özellik, ortam değişkeninin değerini geçersiz kılar.  
  
 Her MSBuild projesi bir yalıtılmış ortam bloğuna sahiptir; yalnızca kendi bloğundaki okumaları ve yazmaları görür.  Proje dosyası değerlendirilmeden veya oluşturulmadan önce MSBuild, özellik koleksiyonunu başlattığında yalnızca ortam değişkenlerini okur. Bunun ardından bu ortam özellikleri statiktir, yani her bir araç aynı adlar ve değerler ile başlar.  
  
 İçinde bir ortam değişkeninin geçerli değerini almak için kullanmak [özellik işlevleri](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. Ancak tercih edilen yöntem, <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> görev parametresinin kullanılmasıdır. Bu dize dizisinde ayarlanan ortam özellikleri, sistem ortamı değişkenlerini etkilemeden oluşturulan araca gönderilebilir.  
  
> [!TIP]
>  Tüm ortam değişkenleri, başlangıç özellikleri olması için okunmaz. Adı "386" gibi geçersiz bir MSBuild özellik adı olan tüm ortam değişkenleri göz ardı edilir.  
  
 Daha fazla bilgi için [nasıl yapılır: bir yapı içinde kullanımı ortam değişkenlerini](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="registry-properties"></a>Kayıt Defteri Özellikleri  
 `Hive` öğesinin kayıt defteri kovanı olduğu (örneğin, HKEY_LOCAL_MACHINE), `Key` öğesinin anahtar adı olduğu, `SubKey` öğesinin alt anahtar adı olduğu ve `Value` öğesinin alt anahtarın değeri olduğu aşağıdaki söz dizimini kullanarak sistem kayıt defteri değerlerini okuyabilirsiniz.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Varsayılan alt anahtar değerini almak için `Value` öğesini atın.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Bu kayıt defteri değeri, bir yapı özelliğini başlatmak için kullanılabilir. Örneğin, Visual Studio web tarayıcısı giriş sayfasını temsil eden bir yapı özelliği oluşturmak için şu kodu kullanın:  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Genel Özellikler  
 MSBuild kullanarak komut satırındaki özellikleri ayarlamanızı sağlar **/Property** (veya **/p**) geçin. Bu genel özellik değerleri proje dosyasında ayarlanan özellik değerlerini geçersiz kılar. Bu ortam özellikleri içerir, ancak değiştirilemeyen ayrılmış özellikleri içermez.  
  
 Aşağıdaki örnek genel `Configuration` özelliğini `DEBUG` olarak ayarlar.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 Genel özellikler, MSBuild görevinin `Properties` özniteliğini kullanarak aynı zamanda çoklu bir proje yapısındaki alt projeler için ayarlanabilir veya değiştirilebilir. Daha fazla bilgi için [MSBuild görevi](../msbuild/msbuild-task.md).  
  
 Bir proje etiketinde `TreatAsLocalProperty` özniteliğini kullanarak bir özellik belirtirseniz bu genel özellik değeri, proje dosyasında ayarlanan özellik değerini geçersiz kılmaz. Daha fazla bilgi için [proje öğesi (MSBuild)](../msbuild/project-element-msbuild.md) ve [nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Özellik İşlevleri  
 .NET Framework sürüm 4'ten başlayarak, MSBuild komut dosyalarınızı değerlendirmek için özellik işlevlerini kullanabilirsiniz. MSBuild görevlerini kullanmadan, yapı komut dosyanızdaki sistem saatini okuyabilir, dizeleri karşılaştırabilir, normal ifadeleri eşleştirebilir ve başka birçok eylemi gerçekleştirebilirsiniz.  
  
 Herhangi bir özelliğin üzerinde gerçekleştirmek için dize (örnek) yöntemlerini kullanabilirsiniz ve birçok sistem sınıfının statik yöntemlerini çağırabilirsiniz. Örneğin, bir yapı özelliğini bugünün tarihine aşağıdaki gibi ayarlayabilirsiniz.  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Daha fazla bilgi ve özellik işlevlerin bir listesi için bkz: [özellik işlevleri](../msbuild/property-functions.md).  
  
## <a name="creating-properties-during-execution"></a>Çalıştırma Sırasında Özellik Oluşturma  
 `Target` öğeleri dışında konumlanan özelliklere, bir yapının değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında özellikler aşağıdaki şekilde oluşturulabilir veya değiştirilebilir:  
  
-   Bir özellik herhangi bir görev tarafından yayılabilir. Bir özellik yaymak için [görev](../msbuild/task-element-msbuild.md) bir alt öğesi olmalıdır [çıkış](../msbuild/output-element-msbuild.md) sahip öğe bir `PropertyName` özniteliği.  
  
-   Bir özellik tarafından yayılabilir [CreateProperty](../msbuild/createproperty-task.md) görev. Bu kullanım önerilmiyor.  
  
-   .NET Framework 3.5'de başlayarak `Target` öğeleri, özellik bildirimlerini içerebilen `PropertyGroup` öğelerini içerebilir.  
  
## <a name="storing-xml-in-properties"></a>Özellikler'de XML Depolama  
 Özellikler, değerlerin görevlere geçirilmesini veya günlük bilgilerin görüntülenmesini sağlayabilecek rastgele bir XML içerebilir. Aşağıdaki örnek, XML ve diğer özellik başvurularını içeren bir değere sahip olan `ConfigTemplate` özelliğini gösterir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], ilgili özellik değerlerini kullanarak özellik başvurularını değiştirir. Özellik değerleri göründükleri sırayla atanır. Bu nedenle bu örnekte, `$(MySupportedVersion)`, `$(MyRequiredVersion)` ve `$(MySafeMode)` öğelerinin önceden tanımlanmış olması gerekir.  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild Kavramları](../msbuild/msbuild-concepts.md)  
 [MSBuild](msbuild.md)  
 [Nasıl yapılır: derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md)   
 [Nasıl yapılır: Proje dosyasının konumunu ve adını başvurusu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)   
 [Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Özellik Öğesi (MSBuild)](../msbuild/property-element-msbuild.md)


