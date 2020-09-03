---
title: 'CA2153: bozuk durum özel durumlarını Işlemeyi önleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 27d837c09e5f2f90796c149bf58d1114d7e6352d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546321"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Bozuk Durum Özel Durumlarını İşlemekten Kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 [Bozuk durum özel durumları (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) , işlemde belleğin bozulma olduğunu gösterir. Bir saldırgan bozuk bellek bölgesine bir yararlanma işlemi gerçekleştirilebileceği takdirde, işlemin çökmesine izin vermek yerine bunları yakalama güvenlik açıklarına yol açabilir.

## <a name="rule-description"></a>Kural Tanımı
 CSE, bir işlemin durumunun bozuk olduğunu ve sistem tarafından yakalanmadığını gösterir. Bozuk durum senaryosunda, bir genel işleyici yalnızca özel özniteliği olan yöntemi işaret ederseniz özel durumu yakalar `HandleProcessCorruptedStateExceptions` . Varsayılan olarak, [ortak dil çalışma zamanı (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) CSEs için catch işleyicilerini çağırmaz.

 İşlemin bu tür özel durumlar yakalanmadan kilitlenmesine izin vermek en güvenli seçenektir, hatta günlük kodu, saldırganların bellek bozulması hatalarından faydalara izin verebilir.

 Bu uyarı, catch (özel durum) veya catch (özel durum belirtimi yok) gibi tüm özel durumları yakalayan genel bir işleyici ile CSEs yakalama sırasında tetiklenir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu uyarıyı çözmek için aşağıdakilerden birini yapmalısınız:

 1. Özniteliği kaldırın `HandleProcessCorruptedStateExceptions` . Bu, CSEs 'nin catch işleyicilerine geçirilmediği varsayılan çalışma zamanı davranışına geri döner.

 2. Özel özel durum türlerini yakalayacak işleyicilerin tercih halinde genel catch işleyicisini kaldırın.  Bu, işleyici kodunun güvenli bir şekilde işleyebileceğini (çok nadir) kabul eden bir CSEs içerebilir.

 3. Özel durumun çağırana geçirilmesini sağlayan catch işleyicisinde CSE 'yi yeniden oluşturun ve çalışan işlemin sona ermesini sağlar.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği

### <a name="violation"></a>Edildiği
 Aşağıdaki sözde kod, bu kural tarafından algılanan kalıbı gösterir.

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

### <a name="solution-1"></a>1\. Çözüm
 HandleProcessCorruptedExceptions özniteliğini kaldırmak, özel durumların işlenmemesini sağlar.

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

### <a name="solution-2"></a>2\. Çözüm
 Genel catch işleyicisini kaldırın ve yalnızca belirli özel durum türlerini yakalayın.

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

### <a name="solution-3"></a>3\. Çözüm
 Özel durumu yeniden oluşturun.

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
