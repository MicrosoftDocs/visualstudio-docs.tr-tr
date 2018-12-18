---
title: Statik yardımcı sınıfları | Microsoft Intellitest Geliştirici Test aracı
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5c635c8fb3def61b8278b7b7c4b66aa196d82b8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000483"
---
# <a name="static-helper-classes"></a>Statik yardımcı sınıfları

Intellitest yazılırken kullanılan statik yardımcı sınıf kümesi sağlar [parametreli birim testleri](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): girişler varsayımlar tanımlamak için kullanılan ve istenmeyen girişleri filtreleme için kullanışlıdır
* [PexAssert](#pexassert): test Çerçevenizi bir sağlamıyorsa kullanmak için bir basit onaylama sınıfı
* [PexChoose](#pexchoose): ek test girişlerinin Intellitest yöneten bir akış
* [PexObserve](#pexobserve): somut değerleri kaydeder ve isteğe bağlı olarak, bunları oluşturulan kodda doğrular

Bazı sınıflar en düşük düzeyde bir Intellitest mantık altyapısıyla etkileşime izin ver:

* [PexSymbolicValue](#pexsymbolicvalue): inceleyin veya sembolik kısıtlamalar değişkenlerinin değiştirmek için yardımcı programlar

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Varsayımlar, gibi ifade etmek için kullanılan bir statik sınıf [önkoşulları](test-generation.md#precondition), [parametreli birim testleri](test-generation.md#parameterized-unit-testing). Bu sınıftaki yöntemleri, istenmeyen test girdileri filtrelemek için kullanılabilir.

Giriş, bazı test için varsayılan koşul tutmazsa bir **PexAssumeFailedException** oluşturulur. Bu test sessizce yok sayılacak neden olur.

**Örnek**

Aşağıdaki parametreli test değil dikkate alacaktır **j = 0**:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Açıklamalar**

Yukarıdaki kod neredeyse eşdeğerdir:

```csharp
     if (j==0)
          return;
```

dışında başarısız **PexAssume** sonuçları test çalışması yok. Durumunda, bir **varsa** deyimi, Intellitest karşılamak için ayrı bir test çalışması oluşturur **ardından** dalı **varsa** deyimi.

**PexAssume** varsayımları temel dize, diziler ve koleksiyonlar için özel iç içe geçmiş sınıflar da içerir.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Onayları, gibi ifade etmek için kullanılan bir statik sınıf [koşul sonralarına](test-generation.md#postcondition), [parametreli birim testleri](test-generation.md#parameterized-unit-testing).

Giriş, bazı test için koşul olarak onaylanan tutmazsa bir **PexAssertFailedException** oluşturulur, testin başarısız olmasına neden olur.

**Örnek**

Bir tamsayının mutlak değeri pozitif olduğunu onaylar:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Bir testi uygulamak için kullanılan yardımcı giriş değerlerini sağlayan bir statik sınıf [parametreli Mocks](input-generation.md#parameterized-mocks).

**PexChoose** sınıfı yardımcı bir testin geçtiğini veya belirli bir giriş değerleri için başarısız olup olmadığını belirlemede. **PexChoose** de denir giriş değerleri yalnızca sağlar *seçenekleri*. Bunu hala kadar giriş değerleri kısıtlamak için ve bir testi geçer veya başarısız olduğunda tanımlayan bir onayları yazılacak kullanıcıdır.

**İşlem modları**

**PexChoose** sınıfı iki modda çalışabilir:

* Intellitest, test ve test edilmiş kod sırasında sembolik bir analizini yaparken [giriş oluşturma](input-generation.md)Seçici rastgele değerler döndürür ve Intellitest, test ve test edilmiş kod her değerin nasıl kullanıldığını izler. Intellitest, test ve test edilmiş kod farklı yürütme yolları tetiklemek için ilgili değerleri oluşturur.

* Belirli test durumları için oluşturulan kod, seçim sağlayıcısını belirli bir biçimde ayarlar, böylece bu tür bir test çalışması yeniden yürütülmesi belirli bir yürütme yolu tetiklemek için belirli bir seçenek yapar.

**Kullanım**

* Basit Arama **PexChoose.Value** yeni bir değer oluşturmak için:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Adlandırılmış değerler oturum için statik bir sınıf.

Intellitest kodu inceler, **PexObserve** hesaplanan değerler, biçimlendirilmiş dize gösterimini kullanarak kaydetmek için kullanılır. Değerlerin benzersiz adlarıyla ilişkilendirilir.

```csharp
PexObserve.Value<string>("result", result);
```

**Örnek**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}


// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a); 
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Statik sınıf parametreler üzerinde kısıtlama yoksay ve değerleri ile ilişkili bir sembolik bilgi yazdırmak için kullanılır.

**Kullanım**

Normalde, Intellitest tüm yürütme yolları kod yürütme sırasında kapsayacak şekilde çalışır. Ancak, özellikle varsayım ve onaylama koşulları ile ilgili işlem yapılırken, tüm olası durumların araştırmanız gereken değil.

**Örnek**

Bu örnek uygulamasını gösterir **PexAssume.Arrays.ElementsAreNotNull** yöntemi. Yönteminde farklı boyutlarda dizinin oluşturulmaya çalışılırken Intellitest önlemek için dizi değeri lengh kısıtlamalar yoksayın. Kısıtlamalar yalnızca burada göz ardı edilir. Test edilen kod için farklı dizisi uzunluklarının farklı davranır, Intellitest farklı boyutlu diziler kısıtlamaları test edilmiş kod üretilemiyor.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Geri bildirim var mı?

Fikirlerinizi gönderin ve özellik istekleri [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).