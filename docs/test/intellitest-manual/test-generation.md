---
title: Test oluşturma | Microsoft Intellitest Geliştirici Test aracı
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 20bacca2343cb2689ed52096c1a9b0d9c3d74703
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295871"
---
# <a name="test-generation"></a>Test oluşturma

Geleneksel birim testi bir test birkaç şey oluşur:

* A [dizisi yöntem çağrıları](test-generation.md#test-generators)
* Bağımsız değişkenler ile yöntem de çağrıldığında; bağımsız değişkenler [test girişleri](input-generation.md)
* Amaçlanan bir davranış belirten bir dizi tarafından test edilen uygulamanın doğrulama [onaylar](#assumptions-and-assertions)

Bir örnek test yapısı şöyledir:

```csharp
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

Intellitest ilgili bağımsız değişken değerlerini otomatik olarak genellikle daha fazla genel belirleyebilir [parametreli birim testleri](#parameterized-unit-testing), bir dizi yöntem çağrıları ve onaylar sağlayın.

<a name="test-generators"></a>
## <a name="test-generators"></a>Test oluşturucuları

Intellitest, test çalışmaları yürütmek için test edilen uygulama yöntemlerinin bir dizi seçerek ve ardından türetilmiş verilerinde onaylar denetlenirken yöntemleri için girişler oluşturma oluşturur.

A [parametreli birim testine](#parameterized-unit-testing) doğrudan bir dizi yöntem çağrıları, gövdesinde durumları.

Nesneleri oluşturmak Intellitest gerektiğinde, Oluşturucular ve Fabrika yöntemleri çağrıları dizisi gerektiği gibi otomatik olarak eklenir.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Parametreli birim testi

*Parametreleştirilmiş birim testleri* (PUTs) olan parametre testleri. Geleneksel birim testleri, farklı olarak genellikle olan yöntemleri kapalı, herhangi bir dizi parametrenin PUTs yararlanın. Bu basit mi? Evet - Burada, Intellitest dener [girişlerinin (küçük) kümesi oluşturma](input-generation.md) , [tam olarak karşılamak](input-generation.md#dynamic-code-coverage) kodu test çalıştırmasından erişilebilir.

PUTs kullanılarak tanımlanır [PexMethod](attribute-glossary.md#pexmethod) MSTest (veya NUnit, xUnit) benzer bir biçimde özel öznitelik. PUTs olan örnek yöntemleri ile etiketlenmiş sınıflardaki mantıksal olarak gruplanmış [PexClass](attribute-glossary.md#pexclass). Aşağıdaki örnek, depolanan basit bir PUT gösterir **MyPexTest** sınıfı:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

Burada **ReplaceFirstChar** yerini alan bir dizenin ilk karakteri bir yöntemdir:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Bu testin Intellitest otomatik olarak yapabilirsiniz [girdiler](input-generation.md) kapsayan çok sayıda test edilmiş kod yürütme yollarını PUT için. Her işlem, bir farklı yürütme yolunu alır "seri" birim testi kapsayan giriş:

```csharp
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Genel parametreli birim testi

Parametreli birim testleri, genel yöntemlerin olabilir. Bu durumda, kullanıcı yöntemi kullanarak örneği oluşturmak için kullanılan türler belirtmelidir [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

```csharp
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Özel durumlara izin vermek

Intellitest, beklenen özel durumlar önceliklendirme özel durumları ve beklenmeyen özel durum yardımcı olmak için çok sayıda doğrulama öznitelikleri sağlar.

Beklenen özel durumlar oluşturmaya uygun ek negatif test çalışmalarıyla gibi **ExpectedException (typeof (*xxx*))**, başarısız olan test çalışmalarını beklenmeyen özel durum oluşturur.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Doğrulayıcıları şunlardır:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): bir belirli özel durum türü yerden sağlar
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): belirtilen bir derlemeden bir belirli özel durum türü sağlar
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): Belirtilen türden bir belirli özel durum türü sağlar
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): test edilen türünden bir belirli özel durum türü sağlar.

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>İç test türleri

"Intellitest bunları görebilirsiniz sürece iç türleri sınayabilirsiniz". Türlerini görmek Intellitest için aşağıdaki öznitelik Visual Studio Intellitest sihirbazları tarafından ürün veya test projenize eklenir:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Varsayımlar ve onaylar

Kullanıcılar kullanabilir varsayımlar ve Onaylamalar express [önkoşulları](#precondition) (tahminler) ve [koşul sonralarına](#postcondition) (onaylar) testlerini hakkında. Intellitest parametre değerlerini bir dizi oluşturur ve "kod keşfediyor", bir varsayım test ihlal ediyor. Bu durum oluştuğunda, bu yol için bir test oluşturmaz ancak sessizce yoksayar.

Onaylardır iyi bilinen bir kavram normal birim test çerçeveleri, Intellitest zaten "yerleşik anlaması için" **Assert** her desteklenen test çerçevesi tarafından sağlanan sınıfları. Ancak, çoğu çerçeveleri sağlamadığı bir **varsay** sınıfı. Bu durumda, Intellitest sağlar [PexAssume](static-helper-classes.md#pexassume) sınıfı. Var olan bir test çerçevesi kullanmak istemiyorsanız, Intellitest de sahip [PexAssert](static-helper-classes.md#pexassert) sınıfı.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

Özellikle, nullness olmayan varsayımına özel bir öznitelik kodlanmış olmalıdır:

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Önkoşulu

Bir yöntemin bir önkoşulu yöntemi başarılı koşullar ifade eder.

Parametreleri ve nesne durumu denetleme ve atma önkoşuluna zorlanan genellikle bir **ArgumentException** veya **InvalidOperationException** bunu ihlal edilirse.

Intellitest, önkoşulu olarak bir [parametreli birim testine](#parameterized-unit-testing) ile ifade [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Sonkoşul

Bir yöntemin Sonkoşul kendi önkoşulları başlangıçta geçerli olduğu varsayılırsa yöntem yürütme sırasında ve sonrasında tutmak zorunda koşullarına ifade eder.

Genellikle, Sonkoşul çağrıları olarak zorunlu kılınmıştır **Assert** yöntemleri.

Intellitest, Sonkoşul biri ile bir [parametreli birim testine](#parameterized-unit-testing) ile ifade [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Test hataları
Oluşturulan bir test çalışması başarısız olduğunda?

1. İçinde sonlanmamasına varsa [yol sınırları yapılandırılmış](exploration-bounds.md), sürece hata olarak kabul [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) seçeneği ayarlanır

1. Test oluşturursa bir **PexAssumeFailedException**, başarılı. Ancak, bunu genellikle sürece filtre [TestEmissionFilter](exploration-bounds.md#testemissionfilter) ayarlanır **tüm**

1. Test ihlal ediyorsa bir [onaylama](#assumptions-and-assertions); Örneğin, başarısız bir birim testi çerçevesi bir onaylama ihlali özel özel durum atma

Yukarıdakilerin hiçbiri karar oluşturmak, bir özel durum oluşturmaz ve yalnızca, test başarılı olur. Onaylama ihlalleri, tıpkı özel durumlar olarak kabul edilir.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Kurulum ve kapatabilirsiniz

Parçası olarak test çerçeveleri ile tümleştirme, algılama ve çalışan Intellitest destekler, Kurulum ve ayırma yöntemleri.

**Örnek**

```csharp
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}
```

<a name="further-reading"></a>
## <a name="further-reading"></a>Daha fazla bilgi

* [Test kodu bağlama](https://blogs.msdn.microsoft.com/devops/2015/04/18/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Hepsini yönetmek için bir test](https://blogs.msdn.microsoft.com/devops/2015/07/05/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Geri bildirim var mı?

Fikirlerinizi gönderin ve özellik istekleri [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).