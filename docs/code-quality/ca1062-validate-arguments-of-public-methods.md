---
title: 'CA1062: Genel yöntemlerin bağımsız değişkenlerini doğrulayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c5894eaf321204ace98a55a3d08411d61207ff7c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857570"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Genel yöntemlerin bağımsız değişkenlerini doğrulayın

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Dışarıdan görünen bir yöntem başvuru bağımsız değişkenlerinden biri, bağımsız değişkenin olup olmadığını doğrulamadan başvurusunu `null` (`Nothing` Visual Basic'te).

## <a name="rule-description"></a>Kural açıklaması

Dışarıdan görünen yöntemlere geçirilen tüm başvuru bağımsız değişkenleri karşı denetlenmesi `null`. Uygunsa, throw bir <xref:System.ArgumentNullException> bağımsız değişken olduğunda `null`.

Ortak veya korumalı olarak bildirildiğinden, bilinmeyen bir derlemeden bir yöntem çağrılabilir, yöntemin tüm parametreleri doğrulamalıdır. Yalnızca bilinen derlemeler tarafından çağrılacak yöntem tasarlanmışsa, yöntemin iç yapmanız ve uygulama gerekir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> yöntemi içeren derlemeye özniteliği.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için her başvuru bağımsız değişkeni karşı doğrulama `null`.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Başvurusu kaldırılmış parametresi işlevdeki başka bir yöntem çağrısı tarafından doğrulanmıştır eminseniz bu kuraldan bir uyarıyı gösterilmemesini sağlayabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kuralını ihlal eden bir yöntem ve kural karşılayan bir yöntemi gösterir.

 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Örnek

Kopya oluşturucuları, alan veya başvuru nesneleri olan özellikleri de CA1062 kuralı ihlal edebilir. Kopya oluşturucuya geçirilen kopyalanan nesne olabileceğinden ihlali meydana `null` (`Nothing` Visual Basic'te). İhlali gidermek için kopyalanan nesnenin null olup olmadığını denetleyin için bir statik (Visual Basic'te Shared) yöntemi kullanın.

Aşağıdaki `Person` sınıfı örneği `other` geçirilen nesne `Person` kopya Oluşturucu olabilir `null`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Örnek

Aşağıdaki düzenlendi `Person` örnek, `other` kopya oluşturucusuna geçirilen nesne null işaretli ilk `PassThroughNonNull` yöntemi.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```