---
title: Öznitelik sözlüğü | Microsoft Intellitest Geliştirici Test aracı
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0a83a7bd2fc40862411bbfd85f72b804318983c5
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294220"
---
# <a name="attribute-glossary"></a>Öznitelik sözlüğü

## <a name="attributes-by-namespace"></a>Ad alanı öznitelikleri

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)<p />

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)<p />

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)<p />

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)<p />

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Bu öznitelik yönetilen değeri olamaz onaylar **null**. İçin eklenebilir:

* bir **parametre** parametreli bir test yöntemi

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* bir **alan**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* A **türü**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Ayrıca bir test bütünleştirilmiş kodu, test düzeni veya test yöntemi bağlanabilir; Bu durumda ilk bağımsız değişken, hangi alanın ya da türü varsayımların uygulamak belirtmeniz gerekir. Öznitelik, bir tür için geçerli olduğu durumlarda bu biçimsel türüyle tüm alanlar için geçerlidir.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Bu öznitelik içeren bir sınıf işaretler *araştırmaları*. MSTest eşdeğerdir **TestClassAttribute** (veya NUnit **TestFixtureAttribute**). Bu öznitelik isteğe bağlıdır.

İşaretlenmiş sınıfların [PexClass](#pexclass) olmalıdır *varsayılan atmamalıdır*:

* Genel olarak dışarı aktarılan tür
* varsayılan oluşturucu
* soyut değil

Sınıfı, bu gereksinimleri karşılamıyorsa, bir hata bildirilir ve araştırma başarısız olur.

Bu sınıfları oluşturmak için de kesinlikle önerilir **kısmi** Intellitest kapsamındaki sınıf, ancak ayrı bir dosyada yeni testler oluşturabilmesi. Bu yaklaşım nedeniyle çoğu sorunu çözdü [görünürlük](input-generation.md#visibility) ve tipik bir teknik de C#.

**Ek suite ve kategoriler**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Test edilen türünü belirterek**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Sınıfı yöntemleri ile ek açıklama içerebilir [PexMethod](#pexmethod). Intellitest ayrıca anlayan [ayarlama ve ayırma yöntemleri](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Bu öznitelik oluşturmak için bir tür tanımlama grubu sağlar. bir [genel parametreli birim testine](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Bu öznitelik bir yöntem olarak işaretler. bir [parametreli birim testine](test-generation.md#parameterized-unit-testing).
Yöntem ile işaretlenmiş bir sınıf içinde bulunmalıdır [PexClass](#pexclass) özniteliği.

Intellitest, arama, Geleneksel, parametresiz testleri oluşturacağını [parametreli birim testine](test-generation.md#parameterized-unit-testing) farklı parametrelerle.

Parametreli birim testi:

* bir örnek yöntemi olmalıdır
* olmalıdır [görünür](input-generation.md#visibility) hangi testlerin yerleştirilir göre test sınıfına [ayarlar Şelalesi](settings-waterfall.md)
* herhangi bir sayıda parametre alabilir
* Genel olabilir

**Örnek**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Bu öznitelik tüm araştırmaları için varsayılan ayarı geçersiz kılmak için derleme düzeyinde ayarlanabilir.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Bu öznitelik geçerli bir test projesi tarafından test edilmiş bir derleme belirtir. 

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Bu öznitelik, bir derlemeyi gerçekleştirilmeyecek belirtmek için kullanılır.

**Örnek**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Bu öznitelik, belirli bir tür (soyut) temel türler veya arabirimleri oluşturmak için kullanabileceğiniz Intellitest söyler.

**Örnek**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Bu öznitelik ekli ise bir [PexMethod](#pexmethod) (veya bir [PexClass](#pexclass), test başarısız olduğunda belirten varsayılan Intellitest mantığı değiştirir. Belirtilen özel durum oluşturursa bile test başarısız olarak değerlendirilmeyecek.

**Örnek**

Şu test belirten oluşturucusunun **yığın** oluşturabilecek bir **üretiliyor**:

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Filtre (Bu da derleme veya test düzeyinde tanımlanabilir) aşağıdaki gibi bir düzen için eklenir:

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>Geri bildirim var mı?

Fikirlerinizi gönderin ve özellik istekleri [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
