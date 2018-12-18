---
title: T4 Metin Şablonu Yazma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0d697f1fed2a7b17862ff4c6f72488674859f754
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967304"
---
# <a name="writing-a-t4-text-template"></a>T4 Metin Şablonu Yazma
Bir metin şablonu, ondan oluşturulan metni içerir. Örneğin, bir web sayfası oluşturan bir şablonu içerir "\<html >..." ve tüm diğer standart bölümlerini bir HTML sayfası. Şablona eklenmiş olan *denetim blokları*, program kodu parçalarını olduğu. Denetim blokları, değişken değerlerini sağlayın ve bölümlerini koşullu ve tekrarlanan olmasını sağlar.

 Bu yapı, bir şablon geliştirin, çünkü oluşturulan dosyanın bir prototip ile başlayın ve artımlı olarak sonucun değişebileceğini denetim blokları eklemek kolay hale getirir.

 Metin şablonları aşağıdaki bölümden oluşur:

-   **Yönergeleri** -şablonu nasıl işleneceğini denetleyen öğeleri.

-   **Metin blokları** - içerik çıkışa doğrudan kopyalanır.

-   **Denetim blokları** -program değişken değerleri metnine ekler ve koşullu veya yinelenen bölümleri metin denetimlerini kodu.

Bu konudaki örnekleri denemek için bunları bir şablon dosyasına açıklandığı gibi kopyalayın [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Şablon dosyası düzenleme sonra dosyayı kaydedin ve ardından çıkışı inceleyebileceğiniz **.txt** dosya.

## <a name="directives"></a>Yönergeler
 Metin şablonu yönergeleri, metin şablon oluşturma altyapısı dönüştürme kodu ve çıktı dosyası oluşturma hakkında genel yönergeler sağlar.

 Örneğin, aşağıdaki yönerge çıkış dosyası .txt uzantısı olması gerektiğini belirtir:

```
<#@ output extension=".txt" #>
```

 Yönergeleri hakkında daha fazla bilgi için bkz: [T4 metin şablonu yönergeleri](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Metin blokları
 Bir metin bloğu doğrudan çıkış dosyasına metin ekler. Hiçbir özel biçimlendirme metin blokları için yoktur. Örneğin, aşağıdaki metin şablonu "Hello" sözcüğünü içeren bir metin dosyası oluşturur:

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Denetim blokları
 Denetim, şablonlarını dönüştürmek için kullanılan program kod bölümlerini taşlarıdır. Varsayılan C# kullanın ancak dildir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], bu yönerge dosyasının başında yazabilirsiniz:

```
<#@ template language="VB" #>
```

 Denetim blokları, kod yazdığınız dil için oluşturulan metnin dilini ilişkili değildir.

### <a name="standard-control-blocks"></a>Standart denetim blokları
 Standart denetim bloğu, çıkış dosyasının bir kısmını oluşturduğu program kodu bölümüdür.

 Metin blokları ve standart denetim blokları ile bir şablon dosyasındaki herhangi bir sayıda karıştırabilirsiniz. Bununla birlikte, içinde başka bir denetim bloğu yerleştirilemiyor. Her standart denetim bloğu simgeleri tarafından sınırlandırılmıştır `<# ... #>`.

 Örneğin, aşağıdaki denetim bloğu ve metin bloğu satırı içerecek şekilde çıkış dosyası neden "0, 1, 2, 3, 4 Merhaba!":

```
<#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Açık kullanmak yerine `Write()` ifadeleri, metin ve kod ayırma. Aşağıdaki örnek "Hello!" yazdırır. dört kez:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Bir metin ekleyebilirsiniz yerde engelleyecek bir `Write();` deyimine kodda izin.

> [!NOTE]
>  Bir metin bloğu veya koşullu bir döngü gibi bileşik deyim içinde eklediğinizde, her zaman küme ayraçları {…} kullanın metin bloğu içerecek şekilde.

### <a name="expression-control-blocks"></a>İfade denetim blokları
 Bir ifade denetim bloğu bir ifadeyi değerlendirir ve bir dizeye dönüştürür. Bu çıktı dosyasına eklenir.

 İfade denetim blokları ile simgeleriyle ayrılmıştır. `<#= ... #>`

 Örneğin, aşağıdaki denetim bloğu "5" içerecek şekilde çıkış dosyası oluşturulmamasını sağlar:

```
<#= 2 + 3 #>
```

 Açılış sembol için üç karakter olduğunu göreceksiniz "< #=".

 İfade, kapsam içi herhangi bir değişken içerebilir. Örneğin, bu bloktaki satır numaralarıyla yazdırır:

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Sınıf özelliği denetim blokları
 Bir sınıf özelliği denetim bloğu, özellikler, yöntemler veya ana dönüşüm dahil edilmemesi gereken herhangi bir kod tanımlar. Sınıf özelliği bloklarını yardımcı işlevleri için sıkça kullanılır.  Genellikle, böylece olabilir sınıf özelliği bloklarını ayrı dosyalarda yerleştirilir [dahil](#Include) birden fazla metin şablonu tarafından.

 Sınıf özelliği denetim blokları ile simgeleriyle ayrılmıştır. `<#+ ... #>`

 Örneğin, şu şablon dosyası bildirir ve bir yöntem kullanır:

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Sınıf özellikleri, yazıldığı dosyanın sonunda yerleştirilmelidir. Ancak, `<#@include#>` olsa bile bir sınıf özelliği içeren bir dosya `include` yönergesi standart blokları ve metin tarafından izlenen.

 Denetim blokları hakkında daha fazla bilgi için bkz: [metin şablonu denetim blokları](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Sınıf özelliği bloklarını, metin blokları içerebilir
 Metin oluşturan bir yöntem yazabilirsiniz. Örneğin:

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 Birden fazla şablon tarafından eklenen ayrı bir dosyada metin oluşturan bir yöntem yerleştirmek özellikle yararlıdır.

## <a name="using-external-definitions"></a>Dış tanımlar kullanma

### <a name="assemblies"></a>Derlemeleri
 Kod blokları şablonunuzun en sık tanımlanan kullanım türleri kullanılabilir System.dll gibi .NET derlemeleri. Ayrıca, diğer .NET derlemelerini veya kendi derlemelere başvurabilir. Bir yol veya bir derlemenin tanımlayıcı ad sağlayabilirsiniz:

```
<#@ assembly name="System.Xml" #>
```

 Mutlak yol adlarını kullanmanız veya yol adına standart makro adları kullanın. Örneğin:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 Derleme yönergesinin hiçbir etkisi yoktur bir [önceden işlenmiş metin şablonu](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Daha fazla bilgi için [T4 derleme yönergesi](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Ad Alanları
 İçeri aktarma yönergesini aynıdır `using` yan tümcesinde C# veya `imports` Visual Basic'te yan tümcesi. Tam adı kullanmadan kodunuzdaki türleri başvurmak olanak tanır:

```
<#@ import namespace="System.Xml" #>
```

 Kadar kullanabileceğiniz `assembly` ve `import` yönergeleri yazarken istiyor. Metin ve denetim blokları önce bunları yerleştirmeniz gerekir.

 Daha fazla bilgi için [T4 içe aktarma yönergesi](../modeling/t4-import-directive.md).

### <a name="Include"></a> Kod ve metin gibi
 `include` Yönergesi, başka bir şablon dosyasından metin ekler. Örneğin, bu yönerge içeriğini ekler `test.txt`.

```
<#@ include file="c:\test.txt" #>
```

 Eklenen içerik ekleyen metin şablonunun hemen hemen parçasıymış gibi işlenir. Ancak, bir sınıf özelliği bloğu içeren bir dosya dahil edebilirsiniz `<#+...#>` bile içerme yönergesi ve standart denetim blokları ile izlense izlenir.

 Daha fazla bilgi için [T4 dahil yönergesi](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Yardımcı program yöntemleri
 Çeşitli yöntemler vardır gibi `Write()` , her zaman bir denetim bloğu içinde kullanılabilir. Bunlar, çıkış Girintile yardımcı olur ve hata raporlama yöntemler içerir.

 Kendi yardımcı program yöntemleri kümesini de yazabilirsiniz.

 Daha fazla bilgi için [metin şablonu yardımcı program yöntemleri](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Veri ve modelleri dönüştürme
 Bir metin şablonu için en kullanışlı uygulama modeli, veritabanı veya veri dosyası gibi bir kaynaktaki içeriği temel malzeme oluşturmaktır. Şablonunuzu ayıklar ve verileri yeniden biçimlendirir. Şablonları koleksiyonu gibi bir kaynak birden fazla dosyaya dönüştürebilirsiniz.

 Kaynak dosyayı okumak için birçok yaklaşım vardır.

 **Bir metin şablonu dosyasını oku**. Bu şablona veri almak için en basit yoludur:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Bir dosya gezilebilir bir model olarak yük**. Metin şablonu kodunuzu gidebilirsiniz bir model verileri okumak daha güçlü bir yöntemdir. Örneğin, bir XML dosyasını yükleyin ve XPath ifadeleri ile gidin. Ayrıca kullanabileceğinizi [XSD.exe'nin](http://go.microsoft.com/fwlink/?LinkId=178765) ile okuyabilir XML veri sınıfları kümesi oluşturmak için.

 **Bir diyagram veya form model dosyasını düzenleyin.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] bir modeli diyagramı veya Windows form olarak düzenlemenize olanak tanıyan araçlar sağlar. Bu, oluşturulan uygulamayı kullanıcılarla model tartışmak kolaylaştırır. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Ayrıca, modeli yapısını yansıtan türü kesin belirlenmiş sınıf kümesi oluşturur. Daha fazla bilgi için [bir etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Tasarım zamanı şablonları göreli dosya yolları
 İçinde bir [tasarım zamanı metin şablonu](../modeling/design-time-code-generation-by-using-t4-text-templates.md)başvuru bir dosyayı bir konuma göre metin şablonu kullanmak istiyorsanız `this.Host.ResolvePath()`. Ayrıca ayarlamanız gerekir `hostspecific="true"` içinde `template` yönergesi:

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>
```

Ana bilgisayar tarafından sağlanan diğer hizmetlere de edinebilirsiniz. Daha fazla bilgi için [erişme Visual Studio'ya veya diğer Konaklara bir şablondan](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Tasarım zamanı metin şablonları ayrı bir AppDomain içinde çalıştırın

 Farkında olmalıdır, bir [tasarım zamanı metin şablonu](../modeling/design-time-code-generation-by-using-t4-text-templates.md) ana uygulamadan ayrı bir AppDomain içinde çalışır. Çoğu durumda bu önemli değildir, ancak belirli karmaşık durumlarda kısıtlamaları keşfedebilirsiniz. Örneğin, ayrı bir hizmetten veri ya da şablonu dışına geçirmek istiyorsanız, hizmet seri hale getirilebilir bir API sağlamanız gerekir.

 (Bu doğru değilse bir [çalışma zamanı metin şablonu](../modeling/run-time-text-generation-with-t4-text-templates.md), kodunuzun geri kalanı ile birlikte derlenmiş kod sağlar.)

## <a name="editing-templates"></a>Şablon düzenleme
 Özel metin şablonu düzenleyicileri, Uzantı Yöneticisi çevrimiçi Galeri'den indirilebilir. Üzerinde **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**. Tıklayın **çevrimiçi galeri**ve ardından arama aracını kullanın.

## <a name="related-topics"></a>İlgili konular

|Görev|Konu|
|-|-|
|Bir şablon yazma.|[T4 Metin Şablonları Yazma Yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Program kodunu metin oluşturmak.|[Metin şablonu yapısı](../modeling/writing-a-t4-text-template.md)|
|Visual Studio çözümü içinde dosyaları oluşturur.|[T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Visual Studio dışında metin oluşturma çalıştırın.|[TextTransform Yardımcı Programı ile Dosya Oluşturma](../modeling/generating-files-with-the-texttransform-utility.md)|
|Bir etki alanına özgü dil biçiminde verilerinizi dönüştürün.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|
