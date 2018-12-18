---
title: T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: dde7b368297979e53d4ee09b75961652749d3321
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380749"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma

Visual Studio çalışma zamanı metin şablonları kullanarak uygulamanızdaki çalışma zamanında metin dizesi oluşturabilirsiniz. Visual Studio burada uygulama yürütür bilgisayar yok. Derleme zamanında çalışma zamanında yürütülen kod şablonu oluşturduğundan çalışma zamanı şablonları bazen "önceden işlenmiş metin şablonlarını" olarak adlandırılır.

Oluşturulan dize ve program kod parçalarını görüneceği şekilde her bir metin karışımını şablonudur. Program parçalarını dize değişkeni bölümleri için değerler sağlayın ve ayrıca koşullu ve tekrarlanan bölümleri denetimi.

Örneğin, aşağıdaki şablonu, bir HTML raporu oluşturur bir uygulamada kullanılabilir.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Şablon değişken parçaları program kodu ile değiştirilmiş bir HTML sayfası olduğuna dikkat edin. Böyle bir sayfa tasarımını, statik bir HTML sayfası prototipi yazarak gelebilecek. Tablo ve değişken diğer bölümleri değişen içeriği sonraki bir gün oluşturduğu program kod ile değiştirmeniz.

Şablon kullanarak kendi uygulama yapar, örneğin, uzun bir dizisinden yazma deyimleri, daha son formun çıktıyı görmek daha kolay olur. Çıkış biçimine değişiklik yapmasını daha kolay ve daha güvenilir.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Herhangi bir uygulama çalışma zamanı metin şablonu oluşturma

### <a name="to-create-a-run-time-text-template"></a>Bir çalışma zamanı metin şablonu oluşturmak için

1. Çözüm Gezgini'nde projenizin kısayol menüsünden seçin **Ekle** > **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **çalışma zamanı metin şablonu**. (Visual Basic'te konum altında **ortak öğeler** > **genel**.)

3. Şablon dosyanız için bir ad yazın.

    > [!NOTE]
    > Şablon dosyası adı, oluşturulan kodda bir sınıf adı olarak kullanılacaktır. Bu nedenle, boşluk veya noktalama işareti olmamalıdır.

4. Seçin **ekleme**.

    Yeni bir dosya uzantısı olan oluşturulduğunda **.tt**. Kendi **özel araç** özelliği **TextTemplatingFilePreprocessor**. Aşağıdaki satırları aşağıdakileri içerir:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Bir çalışma zamanı şablonu için mevcut bir dosyayı dönüştürme

Bir şablon oluşturmak için en iyi yolu, var olan bir çıkış örneğidir dönüştürülmesidir. Örneğin, HTML dosyaları, uygulama oluşturacak, bir düz HTML dosyası oluşturarak başlayabilirsiniz. Görünümünü doğru olduğunu ve doğru çalıştığından emin olun. Ardından Visual Studio projenize ekleyin ve şablona dönüştürebilirsiniz.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Var olan bir metin dosyası için bir çalışma zamanı şablonu dönüştürmek için

1. Dosyayı Visual Studio projenize ekleyin. Çözüm Gezgini'nde projenizin kısayol menüsünden seçin **Ekle** > **var olan öğe**.

2. Dosya kümesi **özel Araçlar** özelliğini **TextTemplatingFilePreprocessor**. Çözüm Gezgini içinde dosyanın kısayol menüsünden seçin **özellikleri**.

    > [!NOTE]
    > Özellik zaten ayarlanmışsa, bu olduğundan emin olun **TextTemplatingFilePreprocessor** değil **TextTemplatingFileGenerator**. Uzantı zaten olan bir dosya eklerseniz bu durum ortaya çıkabilir **.tt**.

3. İçin dosya adı uzantısını değiştiren **.tt**. Bu adım isteğe bağlı olsa da, dosyanın yanlış bir düzenleyicide açmayı önlemek yardımcı olur.

4. Dosya adının ana bölümünden herhangi bir boşluk veya noktalama işareti kaldırın. Örneğin, "My Web Page.tt" yanlış olacaktır, ancak "MyWebPage.tt" doğrudur. Dosya adı, oluşturulan kodda bir sınıf adı olarak kullanılacaktır.

5. Aşağıdaki satırı dosyasının başına ekleyin. Visual Basic projesinde çalışıyorsanız, "C#" "VB" ile değiştirin.

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Çalışma zamanı şablon içeriği

### <a name="template-directive"></a>Şablon yönergesi

Dosyasını oluştururken olduğu gibi şablon ilk satırını alın:

`<#@ template language="C#" #>`

Language parametresini, projenizin dil bağlı olacaktır.

### <a name="plain-content"></a>Düz içerik

Düzen **.tt** uygulamanızı oluşturmak için istediğiniz metni içeren dosya. Örneğin:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Katıştırılmış program kodu

Program kodu arasında ekleyebilirsiniz `<#` ve `#>`. Örneğin:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Deyimleri arasında eklenmiş olduğunu fark `<# ... #>` ve ifadeleri arasına eklenir `<#= ... #>`. Daha fazla bilgi için [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Şablon kullanma

### <a name="the-code-built-from-the-template"></a>Şablondan oluşturulan kod

Kaydettiğinizde **.tt** dosya, bir yan kuruluşu çalışanı **.cs** veya **.vb** dosyası oluşturulur. Bu dosyada görmek için **Çözüm Gezgini**, genişletme **.tt** dosya düğümü. Bir Visual Basic projesinde önce seçin **tüm dosyaları göster** içinde **Çözüm Gezgini** araç çubuğu.

Adlı yöntemi içeren bir parçalı sınıf dosyası içerdiğine dikkat edin `TransformText()`. Uygulamanızdan bu yöntem çağırabilirsiniz.

### <a name="generating-text-at-run-time"></a>Çalışma zamanında metin oluşturma

Uygulama kodunuzda bu çağrısıyla kullanarak şablonunuzu içeriğini oluşturabilirsiniz:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Oluşturulan sınıfın belirli bir ad alanında yerleştirmek için ayarlanmış **özel aracı Namespace** metin şablonu dosyasının özelliği.

### <a name="debugging-runtime-text-templates"></a>Hata ayıklama çalışma zamanı metin şablonları

Hata ayıklama ve çalışma zamanı metin şablonları aynı şekilde sıradan bir kod olarak test edin.

Metin şablonunda bir kesme noktası ayarlayabilirsiniz. Uygulamayı Visual Studio'dan hata ayıklama modunda başlatmak, kodda adım adım ve her zamanki yolla watch nevyhodnocovat.

### <a name="passing-parameters-in-the-constructor"></a>Oluşturucuda parametre geçirme

Genellikle bir şablon uygulamanın diğer kısımlarını bazı veriler almanız gerekir. Bunu kolaylaştırmak için şablon tarafından oluşturulan bir kısmi sınıf kodudur. Aynı sınıfın başka bir bölümünü başka bir dosyaya projenizde oluşturabilirsiniz. Bu dosya bir oluşturucuyla parametreleri, özellikler ve şablonda gömülü kod tarafından hem uygulama geri kalanı tarafından erişilebilen işlevleri içerebilir.

Örneğin, ayrı bir dosya oluşturabilirsiniz **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

Şablon dosyanızda **MyWebPage.tt**, şunu yazabilirsiniz:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Bu şablonu kullanmak için:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Visual Basic'te Oluşturucu parametresi

Visual Basic'te, ayrı bir dosya **MyWebPageCode.vb** içerir:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Şablon dosyasını içerebilir:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Şablon çağrılan oluşturucuda parametre geçirerek:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Şablon özelliklerinde veri geçirme

Şablon sınıfı bir parçalı sınıf tanımında genel özellikler eklemek için alternatif bir veri yolu şablon var. Uygulamanızı çağırmadan önce özellikleri ayarlayabilirsiniz `TransformText()`.

Ayrıca, Şablon sınıfı bir kısmi tanımı alanlar ekleyebilirsiniz. Bu, şablonun birbirini izleyen yürütmeleri arasında veri iletmek sağlar.

### <a name="use-partial-classes-for-code"></a>Kısmi sınıflar için kod kullanın.

Kodun büyük gövdeleri şablonlarında yazılmasını önlemek birçok geliştiricinin tercih. Bunun yerine, şablon dosyası olarak aynı ada sahip bir kısmi sınıftaki yöntemleri tanımlayabilirsiniz. Şablondan bu yöntemi çağırın. Bu şekilde, daha fazla şablon gösterir açıkça hedef çıkış dizesi gibi görünecektir. Görünüm hakkında tartışmalar sonucun görüntülediği verileri oluşturma mantığından ayrılabilir.

### <a name="assemblies-and-references"></a>Derlemeleri ve başvuruları

Bir .NET veya diğer derleme gibi başvurmak için şablon kodunuz istiyorsanız **System.Xml.dll**, projenizin ekleme **başvuruları** her zamanki şekilde.

Bir ad alanı aynı şekilde içeri aktarmak istiyorsanız bir `using` deyimi, bunu yapabilirsiniz ile `import` yönergesi:

```
<#@ import namespace="System.Xml" #>
```

Bu yönergeler, dosyanın başında hemen sonra yerleştirilmelidir `<#@template` yönergesi.

### <a name="shared-content"></a>Paylaşılan içeriği

Çeşitli şablonlar arasında paylaşılan metin varsa, ayrı bir dosyada yerleştirin ve her dosyada görünmesi gerekir içerir:

```
<#@include file="CommonHeader.txt" #>
```

Eklenen İçerik herhangi bir program kodu ve düz metin karışımını içerebilir ve diğer içerebilir yönergeleri ve diğer yönergeleri içerir.

INCLUDE yönergesi, bir şablon dosyası ya da eklenen dosyadaki metni içinde her yerde kullanılabilir.

### <a name="inheritance-between-run-time-text-templates"></a>Çalışma zamanı metin şablonları arasında devralmayı

Çalışma zamanı şablonları, soyut bir temel sınıf şablonu yazarak arasında içerik paylaşabilirsiniz. Kullanım `inherits` parametresinin `<@#template#>` başka bir çalışma zamanı Şablon sınıfı başvurmak için yönergesi.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Devralma deseni: temel yöntemlerini parçaları

Aşağıdaki örnekte kullanılan deseni, aşağıdaki noktalara dikkat edin:

- Temel sınıf `SharedFragments` sınıf özelliği bloklarını içinde yöntemlerini `<#+ ... #>`.

- Boş metin temel sınıfı içerir. Bunun yerine, tüm alt metin bloğu içinde sınıf özellik yöntemleri oluşur.

- Türetilmiş sınıf içinde tanımlanan yöntemleri çağırır `SharedFragments`.

- Uygulama çağrıları `TextTransform()` yöntemi türetilmiş sınıfın temel sınıf dönüştürme değil ancak `SharedFragments`.

- Hem temel sınıfını hem türetilen sınıflarını çalışma zamanı metin şablonları, diğer bir deyişle, **özel araç** özelliği **TextTemplatingFilePreprocessor**.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Sonuçta elde edilen çıktı:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Devralma deseni: Temel gövdesinde metin

Şablon devralma kullanarak bu alternatif yaklaşım içinde metnin toplu temel şablonunda tanımlanır. Türetilmiş şablonlara veri sağlar ve metin temel içeriğinize uyan parça.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Uygulama kodu:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Sonuç çıktısı:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>İlgili Konular

Tasarım zamanı şablonları: kod üretmek için bir şablon kullanmak istiyorsanız, uygulamanızın bir parçası haline gelir, bkz: [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Çalışma zamanı şablonları, şablonları ve bunların içeriğini derleme zamanında burada belirlenir, herhangi bir uygulamada kullanılabilir. Ancak, çalışma zamanında değiştirme şablonlardan metin oluşturan Visual Studio uzantısı yazmak istiyorsanız bkz [bir VS uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma ve T4 Metin Şablonları](../modeling/code-generation-and-t4-text-templates.md)
- [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)
- [T4 araç kutusu](http://olegsych.com/T4Toolbox/)
