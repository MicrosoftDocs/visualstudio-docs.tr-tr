---
title: Anonim metotlar ve kod çözümleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 73ff8dfca29f1ed9896462725886baa87e729100
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280171"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonim Metotlar ve Kod Çözümleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir *anonim yöntem* ada sahip bir yöntemdir. Anonim yöntemler, en sık temsilcinin parametre olarak bir kod bloğu geçirmek için kullanılır.  
  
 Bu konu, Kod Analizi uyarıları ve anonim yöntemler ile ilişkili olan ölçümleri nasıl işlediğini açıklar.  
  
## <a name="anonymous-methods-declared-in-a-member"></a>Bir üye olarak bildirilen anonim yöntemler  
 Uyarılar ve ölçümler bir yöntem veya erişimci gibi bir üye olarak bildirilen anonim yöntemi için yöntem bildiren bir üye ile ilişkili. Bunlar, bu yöntemi çağıran bir üye ile ilişkili değildir.  
  
 Örneğin, sınıfta aşağıdaki bildiriminde bulunan tüm uyarılar **anonymousMethod** karşı harekete Geçirilmemesi gereken **Method1** değil **Method2**.  
  
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
 Uyarılar ve ölçümler için bir satır içi ataması için bir alan olarak bildirilen anonim yöntemi Oluşturucusu ile ilişkilidir. Alan olarak bildirilirse `static` (`Shared` içinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), Ölçümler ve uyarılar, sınıf oluşturucusu ile ilişkili; Aksi takdirde, örnek oluşturucusu ile ilişkilidir.  
  
 Örneğin, sınıfta aşağıdaki bildiriminde bulunan tüm uyarılar **anonymousMethod1** karşı örtük olarak oluşturulan varsayılan oluşturucusu gerçekleştirilecektir **sınıfı**. Bu bulundu oysa **anonymousMethod2** örtük olarak oluşturulan sınıfın Oluşturucusu karşı uygulanır.  
  
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
  
 Bir sınıf birden çok Oluşturucu sahip bir alan için değer atayan bir satır içi anonim yöntem içerebilir. Bu oluşturucu aynı sınıf içinde başka bir oluşturucu zincirine bağlı sürece bu durumda, uyarılar ve ölçümler ile tüm oluşturucular ilişkilendirilir.  
  
 Örneğin, sınıfta aşağıdaki bildiriminde bulunan tüm uyarılar **anonymousMethod** karşı harekete Geçirilmemesi gereken **Class(int)** ve **Class(string)** ancak çalıştırılmaz **Class()**.  
  
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
  
 Bu beklenmeyen görünse de, derleyicinin başka bir oluşturucuya zincir her oluşturucusu için benzersiz bir yöntem çıkardığından bu oluşur. Bu davranış nedeniyle, herhangi bir ihlali, oluşuyor **anonymousMethod** ayrı olarak atlanması gerekir. Yeni bir oluşturucusu varsa bu da anlamına gelen, daha önce karşı gizlenmiş uyarılar **Class(int)** ve **Class(string)** karşı yeni Oluşturucu ayrıca atlanması.  
  
 Bu sorun iki yoldan biriyle getirebilirler. Bildirebilirsiniz **anonymousMethod** ortak bir oluşturucuda, tüm oluşturucular zinciri. Veya tüm oluşturucular tarafından çağrılan başlatma yöntemini bildirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)



