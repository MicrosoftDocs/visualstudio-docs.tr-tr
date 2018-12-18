---
title: Genel Metotlar için birim testleri
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ced33798841a732773310a902c0d51568bc36fe7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067566"
---
# <a name="unit-tests-for-generic-methods"></a>Genel metotlar için birim testleri

Diğer yöntemleri için tam olarak yaptığınız gibi genel metotlar için birim testleri oluşturabilirsiniz. Aşağıdaki bölümler ve örnekleri, genel metotlar için birim testleri oluşturma hakkında bilgi sağlar.

## <a name="type-arguments-and-type-constraints"></a>Tür bağımsız değişkeni ve tür kısıtlamaları

Ne zaman Visual Studio'nun oluşturduğu genel bir sınıf için bir birim testi gibi `MyList<T>`, iki yöntem oluşturur: bir genel yardımcı ve bir test yöntemi. Varsa `MyList<T>` bir veya daha fazla tür kısıtlamaları var, tür bağımsız değişkeni tür kısıtlamaları karşılaması gerekir. İzin verilen tüm girişleri için beklendiği gibi genel test works altında kod emin olmak için test yöntemini test etmek istediğiniz tüm kısıtlamalar ile genel yardımcı yöntemi çağırır.

## <a name="examples"></a>Örnekler
 Aşağıdaki örnekler, genel türler için birim testleri gösterir:

-   [Düzenleme oluşturulan test kodu](#EditingGeneratedTestCode). Bu örnekte oluşturulan Test kodu ve Test kodu düzenlenmiş iki bölümü vardır. Bu genel bir yöntemi yararlı test yönteme oluşturulan ham test kodu düzenleme gösterir.

-   [Bir tür kısıtlaması kullanın](#TypeConstraintNotSatisfied). Bu örnek, bir tür kısıtlaması kullanan bir genel yöntem için birim testi gösterir. Bu örnekte, tür kısıtlaması karşılanmıyor.

###  <a name="EditingGeneratedTestCode"></a> Örnek 1: Oluşturulan test kodu düzenleme
 Bu bölümdeki test kodu adlı bir test altındaki kod yöntemi test `SizeOfLinkedList()`. Bu yöntem, bağlantılı listesinde düğüm sayısını belirten bir tamsayı döndürür.

 Visual Studio Enterprise tarafından oluşturulan gibi ilk kod örneği bölümde oluşturulan Test kodu, düzenlenmemiş test kodu gösterir. ' % S'bölümünde düzenlenen Test kodu, ikinci örnek, iki farklı veri türleri için SizeOfLinkedList yöntemi çalışmasını test nasıl yapabileceğiniz gösterir `int` ve `char`.

 Bu kod, iki yöntem göstermektedir:

-   bir test yardımcı yöntem `SizeOfLinkedListTestHelper<T>()`. Varsayılan olarak, bir test yardımcı yöntem adını "TestHelper" vardır.

-   bir test yöntemi `SizeOfLinkedListTest()`. Her test yönteminin TestMethod özniteliği ile işaretlenir.

#### <a name="generated-test-code"></a>Oluşturulan test kodu
 Aşağıdaki test kodunu kaynaklandığı `SizeOfLinkedList()` yöntemi. Bu düzenlenmemiş oluşturulan test olduğundan, doğru test SizeOfLinkedList yöntemi için değiştirilmelidir.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T); // TODO: Initialize to an appropriate value
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value
    int expected = 0; // TODO: Initialize to an appropriate value
    int actual;
    actual = target.SizeOfLinkedList();
    Assert.AreEqual(expected, actual);
    Assert.Inconclusive("Verify the correctness of this test method.");
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
   SizeOfLinkedListTestHelper<GenericParameterHelper>();
}
```

 Önceki kodda, genel tür parametresidir `GenericParameterHelper`. Aşağıdaki örnekte gösterildiği gibi belirli veri türlerini sağlamak üzere düzenleyebilirsiniz ancak bu bildirimi düzenleme olmadan test çalıştırabilirsiniz.

#### <a name="edited-test-code"></a>Düzenlenen test kodu
 Aşağıdaki kodda, test yöntemi ve test yardımcı yöntemi başarıyla test kodu test altındaki yöntemi okunmaları düzenlenmiş `SizeOfLinkedList()`.

##### <a name="test-helper-method"></a>Test yardımcı yöntemi
 Test yardımcı yöntemi, 1 ile 5. adım olarak etiketlenmiş kod satırlarına karşılık gelen aşağıdaki adımları gerçekleştirir.

1.  Genel olarak bağlı bir liste oluşturun.

2.  Dört düğüm bağlı listeye ekleyin. Bu düğümler içeriğini veri türü bilinmiyor.

3.  Bağlantılı listesinin beklenen boyut değişkene atayın `expected`.

4.  İşlem bağlantılı liste gerçek boyutuna ve değişkene atayın `actual`.

5.  Karşılaştırma `actual` ile `expected` bir onay deyimi içinde. Gerçek beklenen eşit değilse, test başarısız olur.

##### <a name="test-method"></a>Test yöntemi
 Test yöntemi SizeOfLinkedListTest adlı test çalıştırdığınızda, çağrılan kod derlenir. Bu adım 6 ve 7. adım olarak etiketlenmiş kod satırlarına karşılık gelen aşağıdaki adımları gerçekleştirir.

1.  Belirtin `<int>` test için çalıştığını doğrulamak için test yardımcı yöntemini çağırdığınızda `integer` değişkenleri.

2.  Belirtin `<char>` test için çalıştığını doğrulamak için test yardımcı yöntemini çağırdığınızda `char` değişkenleri.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T);
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1
    for (int i = 0; i < 4; i++) // step 2
    {
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);
        target.Append(newNode);
    }
    int expected = 5; // step 3
    int actual;
    actual = target.SizeOfLinkedList(); // step 4
    Assert.AreEqual(expected, actual); // step 5
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> Her zaman SizeOfLinkedListTest test çalıştırmaları, kendi TestHelper yöntemi iki kez çağrılır. Onay deyimi geçirmek test için her zaman true olarak değerlendirilmesi gerekir. Test başarısız olursa, arama, belirtilen olup olmadığını, açık olmayabilecek `<int>` veya belirtilen çağrı `<char>` başarısız olmasına neden. Yanıt bulmak için çağrı yığınını incelemek veya test yönteminizde kesme noktaları ayarlayın ve ardından test çalıştırılırken hata ayıklama. Daha fazla bilgi için [nasıl yapılır: ASP.NET çözümü'nde bir test çalıştırılırken hata ayıklama](https://msdn.microsoft.com/Library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).


###  <a name="TypeConstraintNotSatisfied"></a> Örnek 2: bir tür kısıtlaması kullanma
 Bu örnek, bir birim testi karşılanmadı bir tür kısıtlaması kullanan bir genel yöntem için gösterir. İlk bölüm, kod test altındaki kod projesi gösterir. Tür kısıtlaması vurgulanır.

 İkinci bölümde test projesinden kod gösterilmektedir.

#### <a name="code-under-test-project"></a>Test altındaki kod projesi

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
using System.Text;

namespace ClassLibrary2
{
    public class Employee
    {
        public Employee(string s, int i)
        {
        }
    }

    public class GenericList<T> where T : Employee
    {
        private class Node
        {
            private T data;
            public T Data
            {
                get { return data; }
                set { data = value; }
            }
        }
    }
}
```

#### <a name="test-project"></a>Test projesi

Tüm yeni oluşturulan birim testlerinde olduğu gibi yetersiz olmayan Assert deyimleri yararlı sonuçlar döndürebilir sağlamak için bu birim testi eklemeniz gerekir. Bunları TestMethod özniteliği ile işaretlenmiş yöntem, ancak bu test için adında "TestHelper" yöntem eklemeyin `DataTestHelper<T>()`.

 Bu örnekte, genel tür parametresi `T` kısıtlamasına sahip `where T : Employee`. Bu kısıtlama test yönteminde karşılanmıyor. Bu nedenle, `DataTest()` yöntemi içeren uyarıları gereksinim üzerinde yerleştirilen tür kısıtlaması sağlamak için bir onay deyimi `T`. Bu onay deyimi ileti aşağıdaki gibidir: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

 Diğer bir deyişle, çağırdığınızda `DataTestHelper<T>()` yöntemi test yönteminden `DataTest()`, türünde bir parametre geçmelidir `Employee` veya türetilmiş bir sınıf `Employee`.

 `using ClassLibrary2;`

 `using Microsoft.VisualStudio.TestTools.UnitTesting;`

 `namespace TestProject1`

```csharp
{
    [TestClass()]
    public class GenericList_NodeTest
    {

        public void DataTestHelper<T>()
            where T : Employee
        {
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value
            T expected = default(T); // TODO: Initialize to an appropriate value
            T actual;
            target.Data = expected;
            actual = target.Data;
            Assert.AreEqual(expected, actual);
            Assert.Inconclusive("Verify the correctness of this test method.");
        }

        [TestMethod()]
        public void DataTest()
        {
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +
            "Please call DataTestHelper<T>() with appropriate type parameters.");
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Birim testi kod](../test/unit-test-your-code.md)
