---
title: 'CA2153: Bozuk durum özel durumlarını işlemekten kaçının | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 00e475fa90e0a9976105e4c9c645746427366f32
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869957"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Bozuk Durum Özel Durumlarını İşlemekten Kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 [Bozuk durum özel durumlar (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) belirtmek, Bellek Bozulması işleminizde mevcut. Bir saldırgan bozuk bir bellek bölgesini bir yararlanma yerleştirebilirsiniz, kilitlenme işlemine izin vermek yerine bu yakalama güvenlik açıklarına neden olabilir.

## <a name="rule-description"></a>Kural Tanımı
 CSE, bir işlemin durumunu olduğundan bozuk ve sistem tarafından yakalandı, gösterir. Yönteminizi uygun ile işaretlerseniz bozuk durumda senaryosunda, genel işleyicisi özel durumu yalnızca yakalar. `HandleProcessCorruptedStateExceptions` özniteliği. Varsayılan olarak, [ortak dil çalışma zamanı (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) catch işleyicileri CSE'ler için çağırma kullanılamaz.

 Bu tür özel durumları yakalama olmadan kilitlenme işleme bile kod günlük olarak en güvenli seçenek vermektir Bellek Bozulması hataları yararlanmaya saldırganlar izin verebilirsiniz.

 Catch(exception) veya catch (özel durum belirtimi olmadan) gibi tüm özel durumları yakalayan bir genel işleyici ile CSE'ler yakalama bu uyarıyı tetikler.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu uyarıyı çözümlemek için aşağıdakilerden birini yapmalısınız:

 1. Kaldırma `HandleProcessCorruptedStateExceptions` özniteliği. Bu, burada CSE'ler catch işleyicileri geçirilen değil varsayılan çalışma zamanı davranışı geri döner.

 2. Belirli bir özel durum türleri catch işleyicileri in preference of genel catch işleyicisi kaldırın.  Bu işleyici kodu bunları güvenli bir şekilde işleyebilir (çok nadir) varsayılarak CSE'ler içerebilir.

 3. CSE yeniden özel durum çağırana geçirilir ve çalışan işlemi sonlandırarak içinde sonuçlanır sağlayan catch işleyicisi oluşturur.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği

### <a name="violation"></a>İhlali
 Bu kural tarafından algılanan düzeni aşağıdaki sözde kod göstermektedir.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Çözüm 1
 HandleProcessCorruptedExceptions öznitelik kaldırma, özel durumları değil işlenmesi sağlar.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Çözüm 2
 Genel bir catch işleyicisi kaldırın ve yalnızca belirli bir özel durum türleri yakalayın.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Çözüm 3
 Özel durum yeniden oluşturun.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```



