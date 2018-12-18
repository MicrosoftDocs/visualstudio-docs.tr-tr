---
title: 'CA2153: Bozuk Durum Özel Durumlarını İşlemekten Kaçının'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5043c8cb9cefb8ffdb600083ba2dc4bb49d5e3f5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547532"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Bozuk Durum Özel Durumlarını İşlemekten Kaçının

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

[Bozuk durum özel durumlar (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) belirtmek, Bellek Bozulması işleminizde mevcut. Bir saldırgan bozuk bir bellek bölgesini bir yararlanma yerleştirebilirsiniz, kilitlenme işlemine izin vermek yerine bu yakalama güvenlik açıklarına neden olabilir.

## <a name="rule-description"></a>Kural açıklaması

CSE, bir işlemin durumunu olduğundan bozuk ve sistem tarafından yakalandı, gösterir. Yönteminizi uygun ile işaretlerseniz bozuk durumda senaryosunda, genel işleyicisi özel durumu yalnızca yakalar. `HandleProcessCorruptedStateExceptions` özniteliği. Varsayılan olarak, [ortak dil çalışma zamanı (CLR)](/dotnet/standard/clr) catch işleyicileri CSE'ler için çağırma kullanılamaz.

Bu tür özel durumları yakalama olmadan kilitlenme işleme bile kod günlük olarak en güvenli seçenek vermektir Bellek Bozulması hataları yararlanmaya saldırganlar izin verebilirsiniz.

Catch(exception) veya catch (özel durum belirtimi olmadan) gibi tüm özel durumları yakalayan bir genel işleyici ile CSE'ler yakalama bu uyarıyı tetikler.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu uyarıyı çözmek için şunlardan birini yapın:

- Kaldırma `HandleProcessCorruptedStateExceptions` özniteliği. Bu, burada CSE'ler catch işleyicileri geçirilen değil varsayılan çalışma zamanı davranışı geri döner.

- Belirli bir özel durum türleri catch işleyicileri in preference of genel catch işleyicisi kaldırın. Bu işleyici kodu bunları güvenli bir şekilde işleyebilir (nadir) varsayılarak CSE'ler içerebilir.

- CSE, özel durum çağırana geçirilir ve çalışan işlemi sonlandırarak içinde sonuçlanır catch işleyicisi rethrow.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği

### <a name="violation"></a>İhlali

Bu kural tarafından algılanan düzeni aşağıdaki sözde kod göstermektedir.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>Çözüm 1

HandleProcessCorruptedExceptions öznitelik kaldırma, özel durumları değil işlenmesi sağlar.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>Çözüm 2

Genel bir catch işleyicisi kaldırın ve yalnızca belirli bir özel durum türleri yakalayın.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>Çözüm 3

Özel durumu yeniden.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```