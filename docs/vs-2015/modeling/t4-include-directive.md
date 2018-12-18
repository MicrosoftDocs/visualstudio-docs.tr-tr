---
title: T4 Include yönergesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e8de721b7f26152cd4e7f5df1ee7eb4d04770511
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835949"
---
# <a name="t4-include-directive"></a>T4 Include Yönergesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonunda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kullanarak başka bir dosyadan metin dahil edebilirsiniz bir `<#@include#>` yönergesi. Koyabilirsiniz `include` yönergelerini ilk sınıf özelliği bloğundan önce metin şablonunda herhangi bir yerindeki `<#+ ... #>`. Eklenen dosyalar ayrıca içerebilir `include` yönergeleriyle birlikte diğer yönergeleri. Bu şablon kodunu ve demirbaş metni şablonlar arasında paylaşmanızı sağlar.  
  
## <a name="using-include-directives"></a>Ekleme Yönergelerini Kullanma  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
- `filePath` mutlak ya da geçerli şablon dosyasına bağıl olabilir.  
  
   Ayrıca belirli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantıları, ekleme kodu dosyalarında aranacak kendi dizinlerini belirtebilir. Örneğin, Görselleştirme ve modelleme SDK'sını (DSL araçları) yüklediğinizde aşağıdaki klasör listeyi içermek için eklenir: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.  
  
   Bu ek içerme klasörleri içeren dosyanın dosya uzantısına bağlı olabilir. Örneğin DSL araçları dahil etme klasörü, yalnızca dosya uzantısına sahip dosyalar dahil olmak üzere erişilebilir `.tt`  
  
- `filePath` "%" ile sınırlandırılan ortam değişkenleri içerebilir. Örneğin:  
  
  ```  
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
  ```  
  
- Eklenen bir dosya adı uzantısının kullanılması gerekmez `".tt"`.  
  
   Gibi başka bir uzantı kullanmak isteyebilirsiniz `".t4"` eklenen dosyalar için. Eklediğinizde, çünkü bir `.tt` bir projeye [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otomatik olarak ayarlar, **özel araç** özelliğini `TextTemplatingFileGenerator`. Tek tek dönüştürülecek dosyaları genellikle eklemek istemezsiniz.  
  
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
  
##  <a name="msbuild"></a> MSBuild hem Visual Studio'da proje özelliklerini kullanma  
 Ekleme yönergesinde $(SolutionDir) gibi Visual Studio makrolarını kullanabilirsiniz, fakat bu makrolar MSBuild'de çalışmaz. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.  
  
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



