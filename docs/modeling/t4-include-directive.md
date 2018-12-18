---
title: T4 Include Yönergesi
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b5a05629773334648239a8656577fbe0ae347625
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830710"
---
# <a name="t4-include-directive"></a>T4 Include Yönergesi

Metin şablonunda Visual Studio kullanarak başka bir dosyadan metin içerebilir bir `<#@include#>` yönergesi. Koyabilirsiniz `include` yönergelerini ilk sınıf özelliği bloğundan önce metin şablonunda herhangi bir yerindeki `<#+ ... #>`. Eklenen dosyalar ayrıca içerebilir `include` yönergeleriyle birlikte diğer yönergeleri. Bu şablon kodunu ve demirbaş metni şablonlar arasında paylaşmanızı sağlar.

## <a name="using-include-directives"></a>Ekleme Yönergelerini Kullanma

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` mutlak ya da geçerli şablon dosyasına bağıl olabilir.

   Ayrıca, belirli Visual Studio uzantıları ekleme kodu dosyalarında aranacak kendi dizinlerini belirtebilir. Örneğin, Görselleştirme ve modelleme SDK'sını (DSL araçları) yüklediğinizde aşağıdaki klasör listeyi içermek için eklenir: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.

   Bu ek içerme klasörleri içeren dosyanın dosya uzantısına bağlı olabilir. Örneğin DSL araçları dahil etme klasörü, yalnızca dosya uzantısına sahip dosyalar dahil olmak üzere erişilebilir `.tt`

- `filePath` "%" ile sınırlandırılan ortam değişkenleri içerebilir. Örneğin:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Eklenen bir dosya adı uzantısının kullanılması gerekmez `".tt"`.

   Gibi başka bir uzantı kullanmak isteyebilirsiniz `".t4"` eklenen dosyalar için. Eklediğinizde, çünkü bir `.tt` bir proje, Visual Studio dosyayı otomatik olarak ayarlar, **özel araç** özelliğini `TextTemplatingFileGenerator`. Tek tek dönüştürülecek dosyaları genellikle eklemek istemezsiniz.

   Diğer taraftan, bazı durumlarda, dosya uzantısının ek klasörlerin hangi include dosyalarının aranacağını etkilediğinin farkında olmalısınız. Diğer dosyaları içeren eklediğiniz bir dosya varsa, bu önemli olabilir.

- Eklenen içerik ekleyen metin şablonunun hemen hemen parçasıymış gibi işlenir. Ancak, bir sınıf özelliği bloğu içeren bir dosya dahil edebilirsiniz `<#+...#>` bile `include` yönergesi ve standart denetim blokları ile izlense ardından.

- Kullanım `once="true"` birden fazla başka ekleme dosyasından çağrılırsa bile şablonun yalnızca bir kez eklendiğinden emin olmak için.

   Bu özellik yapar, ekleyebileceğiniz yeniden kullanılabilir T4 kod parçacıkları kitaplığını ayarlama kolayca, endişelenmenize gerek kalmadan çalışır başka bir kod parçacığı zaten bunları eklemiştir.  Örneğin, şablon işleme ve C# oluşturma ile ilgili çok ayrıntılı kod parçacıkları içeren bir kitaplık olduğunu varsayalım.  Buna karşılık, bunlar daha sonra daha uygulamaya özgü şablonlardan kullanabilirsiniz özel durumların gibi bazı daha göreve özel yardımcı programları tarafından kullanılır. Bağımlılık grafiği çizerseniz, bazı iş parçacıklarının birkaç kez dahil edildiğini görürsünüz. Ancak `once` parametresi sonraki eklemeleri engeller.

  **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **TextFile1.t4:**

```
   Output Message 2 (from included file).
<#@include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2.t4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **Sonuç dosyası, MyTextTemplate.txt oluşturuldu:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="msbuild"></a> MSBuild hem Visual Studio'da proje özelliklerini kullanma
 Yönergesinde $(SolutionDir) gibi Visual Studio makrolarını kullanabilirsiniz, ancak bunlar MSBuild içinde çalışmaz. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.

 Proje özelliği tanımlamak için .csproj veya .vbproj dosyanızı düzenleyin. Bu örnek adlı bir özellik tanımlar `myIncludeFolder`:

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Artık proje özelliğinizi metin şablonlarında kullanabilirsiniz, böylece hem Visual Studio hem de MSBuild içinde doğru dönüştürme yapılır:

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```