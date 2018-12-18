---
title: Anonim Metotlar ve Kod Çözümleme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e069976badeffbce04b2f245277426441d3df2f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31892709"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonim Metotlar ve Kod Çözümleme
Bir *anonim yöntemi* bir ada sahip bir yöntemdir. Anonim yöntemler, en sık kod bloğu temsilci parametre olarak geçirmek için kullanılır.

 Bu konu, Kod Analizi uyarıları ve anonim yöntemler ile ilişkili olan ölçümleri nasıl işlediğini açıklar.

## <a name="anonymous-methods-declared-in-a-member"></a>Bir üyeyi bildirilen anonim yöntemler
 Uyarılar ve ölçümleri yöntemi veya erişimci gibi bir üye olarak bildirilen bir anonim yöntemi için yöntem bildirir üye ile ilişkili. Bunlar yöntemini çağırır üye ile ilişkili değildir.

 Örneğin, sınıfta aşağıdaki bildirimi içinde bulunan tüm uyarılar **anonymousMethod** karşı oluşmalıdır **Method1** ve **Method2**.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Satır içi anonim yöntemler
 Uyarılar ve satır içi atamaya bir alan olarak bildirilen bir anonim yöntemi için ölçümleri Oluşturucusu ile ilişkilidir. Alan olarak bildirilirse `static` (`Shared` içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), uyarılar ve ölçümleri sınıfı oluşturucusu ile ilişkili; Aksi takdirde, örnek oluşturucu ile ilişkilendirilmiş.

 Örneğin, sınıfta aşağıdaki bildirimi içinde bulunan tüm uyarılar **anonymousMethod1** karşı örtük olarak oluşturulmuş varsayılan oluşturucusunun gerçekleştirilecektir **sınıfı**. Bu bulundu ancak **anonymousMethod2** örtük olarak oluşturulmuş sınıf oluşturucu karşı uygulanır.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

 Bir sınıfın birden çok oluşturucular sahip bir alan için değer atayan bir satır içi anonim yöntemi içerebilir. Bu oluşturucu aynı sınıfın başka bir oluşturucuda bağlı sürece bu durumda, uyarılar ve ölçümler ile tüm oluşturucular ilişkilendirilir.

 Örneğin, sınıfta aşağıdaki bildirimi içinde bulunan tüm uyarılar **anonymousMethod** karşı oluşmalıdır **Class(int)** ve **Class(string)** ancak değil karşı **Class()**.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

 Bu beklenmeyen görünse de, bu başka bir oluşturucuya zincir bağlanmayan her oluşturucusu için benzersiz bir yöntem derleyici çıkarır nedeniyle oluşur. Bu davranış nedeniyle, herhangi bir ihlali, oluşuyor **anonymousMethod** ayrı olarak atlanması gerekir. Yeni bir oluşturucu ise, bu da anlamına sunulan, daha önce karşı gösterilmedi uyarıları **Class(int)** ve **Class(string)** karşı new Oluşturucusu ayrıca atlanması gerekir.

 İki yöntemden biri bu soruna geçici bir çözüm çalışabilir. Bildirebilirsiniz **anonymousMethod** ortak oluşturucusunda, tüm oluşturucular zinciri. Veya, tüm oluşturucular tarafından çağrılan başlatma yöntemini de bildirebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilen kod kalitesini analiz etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)