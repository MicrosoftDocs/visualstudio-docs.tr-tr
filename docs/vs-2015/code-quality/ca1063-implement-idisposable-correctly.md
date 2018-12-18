---
title: 'CA1063: IDisposable doğru | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 94d13514800bac80723031c6bba7920d28ac83e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877302"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable'ı doğru uygulayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 `IDisposable` doğru uygulanmadı. Bu sorun için bazı nedenler aşağıda listelenmiştir:

- IDisposable sınıfta yeniden uygulanmış olur.

- Sonlandırma yeniden geçersiz kılınır.

- Dispose geçersiz kılınır.

- Dispose() public değil korumalı ya da Dispose adlı.

- Dispose(bool) korumalı, sanal veya korumasız değil.

- Korumasız türlerinde Dispose(true) Dispose() çağırmalıdır.

- Mühürlenmemiş türler için her ikisi de Dispose(bool) veya büyük/küçük harf Sonlandırıcıları Finalize uygulama çağırmaz.

  Bu desenleri herhangi birinin ihlali bu uyarıyı tetikleyecektir.

  Kendi korumalı sanal void Dispose(bool) yönteminin her korumasız kök IDisposable tür sağlamanız gerekir. Dipose(true) Dispose() çağırmalıdır ve Finalize Dispose(false) yöntemini çağırması gerekir. Bir korumasız kök IDisposable tür oluşturuyorsanız, Dispose(bool) tanımlayın ve bunu çağırmanız gerekir. Daha fazla bilgi için [Cleaning Up Unmanaged Resources](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) içinde [çerçeve tasarım yönergeleri](http://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) .NET Framework belgelerinin bölümü.

## <a name="rule-description"></a>Kural Tanımı
 Tüm IDisposable türleri Dispose kalıbını doğru uygulamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Kesip kodunuzu inceleyebilir ve aşağıdaki çözümlerden birini, bu ihlali düzeltir belirleyin.

-   IDisposable tarafından uygulanan arabirimler listesinden kaldırın {0} ve temel sınıfın Dispose uygulamasını geçersiz kılın.

-   Sonlandırıcı türünden kaldırın {0}, Dispose (bool disposing) yöntemini geçersiz kılın ve sonlandırma mantığını 'disposing ' değerinin false olduğu kod yoluna koyun.

-   Kaldırma {0}, Dispose (bool disposing) yöntemini geçersiz kılın ve atma mantığını 'disposing ' değerinin true olduğu kod yoluna koyun.

-   Emin {0} genel olarak bildirildi ve korumalı.

-   Yeniden adlandırma {0} yöntemini 'Dispose' ve onu public ve sealed olarak bildirildiğinden emin olun.

-   Emin olun {0} korumalı olarak sanal bildirilen ve korumasız.

-   Değiştirme {0} Dispose(true) çağırır, böylece daha sonra GC çağırır. IDisposable.Dispose geçerli nesne örneğinde ('this' veya 'Me' [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) ve ardından döndürür.

-   Değiştirme {0} böylece Dispose(false) yöntemini çağıracak ve sonra döndürür.

-   Bir korumasız kök IDisposable sınıfı yazıyorsanız, aşağıdaki IDisposable uygulamasını daha önce bu bölümde açıklanan desene uygun olduğunu emin olun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği
 Aşağıdaki sözde kod Dispose(bool) yönetilen kullanan bir sınıf içinde nasıl uygulanması gerekir ve yerel kaynaklara genel bir örnek sağlar.

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```



