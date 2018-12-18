---
title: Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7af8fc49896549fd553c8262b04e9d02f76f06e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058317"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları

Bu makalede, Fakes kod oluşturma ve derleme seçeneklerini ve sorunlarını açıklar ve üretilen Fakes türleri, üyeler ve parametrelerini adlandırma kurallarını açıklar.

**Gereksinimler**

-   Visual Studio Enterprise
-   Bir .NET Framework projesi

> [!NOTE]
> .NET standard projeleri desteklenmez.

## <a name="code-generation-and-compilation"></a>Kod oluşturma ve derleme

### <a name="configure-code-generation-of-stubs"></a>Koçanların kod oluşturma yapılandırma

Koçan türler oluşturulmasını içeren bir XML dosyasında yapılandırılır *.fakes* dosya uzantısı. Fakes framework yapı işleminde özel MSBuild görevleri ile tümleştirir ve bu dosyaları derleme sırasında algılar. Fakes Kod Oluşturucusu bir derleme içine Koçan türleri derler ve projeye başvuruyu ekler.

Aşağıdaki örnek içinde tanımlanan Koçan türleri gösterilmektedir *FileSystem.dll*:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Tür filtreleme

Filtreler ayarlanabilir *.fakes* hangi türlerin heline getirilmesi gereken kısıtlamak için dosya. Temizle, Ekle, Kaldır öğelerini seçili türlerinin listesini oluşturmak için StubGeneration öğesinin altındaki sınırsız sayıda ekleyebilirsiniz.

Örneğin, aşağıdaki *.fakes* dosya türleri System ve System.IO ad alanları altında için saplamalar oluşturur, ancak System içinde "Handle" içeren her türü dışlar:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Clear />
    <Add Namespace="System!" />
    <Add Namespace="System.IO!"/>
    <Remove TypeName="Handle" />
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

Filtre dizeleri nasıl yapılması gerektiğini tanımlamak için basit bir dil bilgisi kullanın:

-   Filtreleri, varsayılan olarak büyük küçük harf duyarsız; eşleşen alt dizenin filtreleri uygulayın:

     `el` "hello" ile eşleşir

-   Ekleme `!` isteğe bağlı olarak filtre sonuna kadar kesin bir büyük küçük harfe duyarlı eşleşme yapar:

     `el!` "hello" ile eşleşmiyor

     `hello!` "hello" ile eşleşir

-   Ekleme `*` filtre sonuna kadar dizenin önek eşleşen kolaylaştırır:

     `el*` "hello" ile eşleşmiyor

     `he*` "hello" ile eşleşir

-   Noktalı virgülle ayrılmış bir liste içinde birden çok filtre ayırım yaparak birleştirilebilir.

     `el;wo` "hello" ve "world" ile eşleşir

### <a name="stub-concrete-classes-and-virtual-methods"></a>Saplama somut sınıflar ve sanal yöntemler

Varsayılan olarak, Koçan türleri korumalı olmayan tüm sınıflar için oluşturulur. Soyut sınıfların Koçan türlerini kısıtlamak mümkündür *.fakes* yapılandırma dosyası:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Types>
      <Clear />
      <Add AbstractClasses="true"/>
    </Types>
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

### <a name="internal-types"></a>Dahili türler

Shim/dolgu türlerini ve Koçan türleri üretilen Fakes derlemeye görülebilen türler için Fakes Kod Oluşturucusu oluşturur. Shimmed derleme dahili türlerini Fakes ve test derlemeniz görünür hale getirmek için ekleme <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini shimmed derleme kodu, oluşturulan Fakes derlemesine ve test derlemesine görünürlük sağlar. Örnek buradadır:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **Kesin adlandırılmış derlemelerin iç türleri**

 Shimmed derleme kesin şekilde adlandırıldığında ve derlemenin iç türlerine erişmek istediğiniz varsa:

-   Hem test derlemeniz hem de Fakes derlemeniz kesin adlandırılmış olmalıdır.

-   Test ve Fakes derlemesinin ortak anahtarlarını ekleme **Internalsvisibletoattribute** shimmed derlemelerdeki öznitelikleri. Shimmed derleme kesin şekilde adlandırıldığında dolgu kullanılan derleme koduna örnek öznitelikleri nasıl görüneceğini aşağıda verilmiştir:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Shimmed derleme güçlü adlandırılırsa Fakes framework otomatik olarak oluşturulan Fakes derlemeleri imzalar. Test derlemesi strong oturum gerekir. Bkz: [tanımlayıcı adlandırılmış derlemeler](/dotnet/framework/app-domains/strong-named-assemblies).

Fakes çerçevesi, bu kod parçacığı eklemek için bir başlangıç noktası olarak kullanabilmeniz için oluşturulan tüm derlemeleri imzalamak için aynı anahtarı kullanır. **InternalsVisibleTo** özniteliğini shimmed derleme kodunuza fakes derlemesi.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Fakes derlemesi için farklı bir ortak anahtar belirtebilirsiniz, bir anahtar gibi tam yolunu belirterek shimmed derleme için oluşturduğunuz *.snk* olarak alternatif anahtarı içeren dosyayı `KeyFile` özniteliği değeri `Fakes` \\ `Compilation` öğesinin *.fakes* dosya. Örneğin:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Daha sonra diğer ortak anahtarını kullanmak zorunda *.snk* shimmed derleme kodunda Fakes derlemesinin Internalvisibleto özniteliğinin ikinci parametre olarak dosya:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

Yukarıdaki değerleri örnekte `Alternate_public_key` ve `Test_assembly_public_key` aynı olabilir.

### <a name="optimize-build-times"></a>Derleme zamanlarını iyileştirme

Fakes derlemelerinin derlemesi yapım sürenizi önemli ölçüde artırabilir. Ayrı merkezi bir proje içinde .NET System derlemeleri için Fakes derlemeleri ve üçüncü taraf derlemeler oluşturarak derleme zamanını en aza indirebilirsiniz. Bu tür derlemeler makinenizde nadiren değiştiğinden, oluşturulan Fakes derlemeleri diğer projelerde yeniden kullanabilirsiniz.

Birim test projelerinizden proje klasöründeki FakesAssemblies altında yerleştirilen derlenmiş Fakes derlemelerden açıkça başvuru ekleyin.

1.  Test projelerinizle eşleşen .NET çalışma zamanı sürümünü ile yeni bir sınıf kitaplığı oluşturun. Şimdi fakes.prebuild diye çağıralım. Kaldırma *class1.cs* gerekli proje dosyası.

2.  Tüm sistem başvuru ekleyin ve üçüncü taraf derlemeler için Fakes gerekir.

3.  Ekleme bir *.fakes* her derleme için dosya ve oluşturun.

4.  Test projenizden

    -   Fakes çalışma zamanı DLL başvuru sahip olduğunuzdan emin olun:

         *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    -   Fakes oluşturduğunuz her derleme için karşılık gelen DLL dosyasına bir başvuru ekleyin *Fakes.Prebuild\FakesAssemblies* projenizin klasör.

### <a name="avoid-assembly-name-clashing"></a>Derleme adı çakışan kaçının

Bir ekip ortamında, tüm yapı çıkışları tek bir dizin içinde birleştirilir. Birden çok proje Fakes kullanıyorsanız, farklı sürümlerine ait Fakes derlemeler birbirini geçersiz kılma meydana getirebilir. Örneğin TestProject1 fakes *mscorlib.dll* .NET Framework 2.0 ve TestProject2 fakes gelen *mscorlib.dll* .NET Framework 4 için her ikisi için yield bir *mscorlib. Fakes.dll* Fakes derlemesi.

 Bu sorunu önlemek için Fakes otomatik olarak sürüm nitelikli Fakes derleme adı proje-olmayan başvurular için eklerken oluşturmalısınız *.fakes* dosyaları. Fakes derleme adı oluştururken bir sürüm nitelikli Fakes derleme adı bir sürüm numarası gömer:

 Bir derleme MyAssembly ve sürüm 1.2.3.4, Fakes derleme adı MyAssembly.1.2.3.4.fakes'dir.

 Değiştirebilir veya içindeki derleme öğesinin Version özniteliği düzenleyerek bu sürümü kaldırmanız *.fakes*:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Fakes adlandırma kuralları

### <a name="shim-type-and-stub-type-naming-conventions"></a>Dolgu ve Koçan türleri adlandırma kuralları yazın

 **Ad Alanları**

- . Fakes sonekini ad alanına eklenir.

   Örneğin, `System.Fakes` ad alanı System ad alanının Shim/dolgu türlerini içerir.

- Global.Fakes boş ad alanını dolgu türünü içerir.

  **Tür adları**

- Dolgu/Shim öneki Dolgu türü adı yapılandırmak için tür adına eklenir.

   Örneğin, ShimExample Example türünün shim türüdür.

- Stub öneki stub türü adı yapılandırmak için tür adına eklenir.

   Örneğin, Stubıexample IExample türünün stub türüdür.

  **Tür argümanları ve iç içe tür yapıları**

- Genel tür argümanları kopyalanır.

- İç içe tür yapıları shim türleri için kopyalanır.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Adlandırma kuralları shim temsilci özelliği veya stub temsilci alanı

**Temel kurallar** alanının adlandırma, boş bir isimden başlama:

- Yöntem adı eklenir.

- Yöntem adı açık arabirim uygulaması ise noktalar kaldırılır.

- Yöntem genelse, `Of` *n* nereden eklenir *n* genel yöntem bağımsız değişken sayısı.

  **Özel yöntem adları** gibi özellik alıcı veya ayarlayıcılar aşağıdaki tabloda açıklandığı gibi değerlendirilir:

|Yöntem ise...|Örnek|Yöntem adı eklenmiş|
|-|-|-|
|A **Oluşturucusu**|`.ctor`|`Constructor`|
|Statik **Oluşturucusu**|`.cctor`|`StaticConstructor`|
|Bir **erişimci** yöntemiyle iki kısımdan adı "_" (örneğin, özellik alıcıları) tarafından ayrılmış|*kind_name* (ortak büyük/küçük harf, ancak ECMA tarafından zorlanan değil)|*NameKind*, burada her iki parçayı büyük harfli takas ve|
||Özelliğin alıcısı `Prop`|`PropGet`|
||Özelliğin Ayarlayıcısı `Prop`|`PropSet`|
||Olay ekleyici|`Add`|
||Olay kaldırıcısı|`Remove`|
|Bir **işleci** iki bölümden oluşur|`op_name`|`NameOp`|
|Örneğin: + işleci|`op_Add`|`AddOp`|
|İçin bir **dönüştürme işleci**, dönüş türü eklenir.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Alıcılar ve ayarlayıcılar Dizin oluşturucuların** özelliğine benzer şekilde değerlendirilir. Bir dizin oluşturucu için varsayılan ad `Item`.
> - **Parametre türü** adları dönüştürülür ve birleştirilir.
> - **Dönüş türü** aşırı yükleme belirsizliği olmadıkça göz ardı edilir. Aşırı yükleme amiguity ise, dönüş türü adının sonuna eklenir.

### <a name="parameter-type-naming-conventions"></a>Parametre türü adlandırma kuralları

|Verilen|Eklenen dizedir...|
|-|-|
|A **türü**`T`|T<br /><br /> Ad alanı, iç içe yapı ve genel tikler iptal bırakılır.|
|Bir **çıkış parametresi**`out T`|`TOut`|
|A **ref parametresi** `ref T`|`TRef`|
|Bir **dizi türü**`T[]`|`TArray`|
|A **çok boyutlu dizi** türü `T[ , , ]`|`T3`|
|A **işaretçi** türü `T*`|`TPtr`|
|A **genel tür**`T<R1, ...>`|`TOfR1`|
|A **genel tür bağımsız değişkeni** `!i` türü `C<TType>`|`Ti`|
|A **genel metot argümanı** `!!i` yöntemi `M<MMethod>`|`Mi`|
|A **iç içe türü**`N.T`|`N` , ardından eklenir `T`|

### <a name="recursive-rules"></a>Özyinelemeli kurallar

Aşağıdaki kurallar özyinelemeli olarak uygulanır şunlardır:

-   Fakes kullandığından C# geçersiz oluşturur herhangi bir karakter Fakes derlemeleri oluşturmak için C# belirteci "_" (alt çizgi) kaçış.

-   Bildirim türü herhangi bir üyesi ile elde edilen adı çakışıyor, 01 ile başlayan iki basamaklı sayaç ekleyerek bir numaralandırma şeması kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
