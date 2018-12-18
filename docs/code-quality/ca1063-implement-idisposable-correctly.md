---
title: "CA1063: IDisposable'ı doğru uygulayın"
ms.date: 02/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: e202c35ee6bd8353170e758629b1cc6e739b775d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080977"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable'ı doğru uygulayın

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

<xref:System.IDisposable?displayProperty=nameWithType> Arabirimi düzgün uygulanmadı. Olası nedenler:

- <xref:System.IDisposable> sınıfta reimplemented.

- Sonlandırma reoverridden.

- Dispose() geçersiz kılınır.

- Dispose() yöntemini public değil [korumalı](/dotnet/csharp/language-reference/keywords/sealed), veya adlandırılmış **Dispose**.

- Dispose(bool) korumalı, sanal veya korumasız değil.

- Korumasız türlerinde Dispose(true) Dispose() çağırmalıdır.

- Mühürlenmemiş türler için her ikisi de Dispose(bool) veya temel sınıf Sonlandırıcı Finalize uygulama çağırmaz.

Bu düzenleri herhangi birinin ihlali CA1063 uyarı tetikler.

Bildirir ve uygulayan her tür <xref:System.IDisposable> arabirimi kendi korumalı sanal void Dispose(bool) yönteminin sağlamalıdır. Dipose(true) Dispose() çağırmalıdır ve sonlandırıcı Dispose(false) yöntemini çağırması gerekir. Bildirir ve uygulayan bir tür oluşturursanız <xref:System.IDisposable> arabirimi Dispose(bool) tanımlamanız ve bunu çağırmanız gerekir. Daha fazla bilgi için [(.NET Kılavuzu) yönetilmeyen kaynakları Temizleme](/dotnet/standard/garbage-collection/unmanaged) ve [Dispose deseni](/dotnet/standard/design-guidelines/dispose-pattern).

## <a name="rule-description"></a>Kural açıklaması

Tüm <xref:System.IDisposable> türleri uygulayan [Dispose deseni](/dotnet/standard/design-guidelines/dispose-pattern) doğru.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Kesip kodunuzu inceleyebilir ve aşağıdaki çözümlerden birini, bu ihlali düzeltir belirleyin:

- Kaldırma <xref:System.IDisposable> türünüz uygulanır ve temel sınıfın Dispose uygulamasını geçersiz kılın arabirimleri listesinden.

- Sonlandırıcıyı, türünden kaldırın, Dispose (bool disposing) yöntemini geçersiz kılın ve sonlandırma mantığını 'disposing ' değerinin false olduğu kod yoluna koyun.

- Dispose (bool disposing) yöntemini geçersiz kılın ve atma mantığını 'disposing ' değerinin true olduğu kod yoluna koyun.

- Dispose() genel olarak bildirildiğinden emin olun ve [korumalı](/dotnet/csharp/language-reference/keywords/sealed).

- Yeniden adlandırmak için dispose yöntemini **Dispose** ve genel olarak bildirildiğinden emin olun ve [korumalı](/dotnet/csharp/language-reference/keywords/sealed).

- Emin Dispose(bool) korumalı olarak bildirilir, virtual ve unsealed olun.

- Dispose() ve böylece onu Dispose(true) yöntemini, değiştirme, daha sonra çağırır <xref:System.GC.SuppressFinalize%2A> geçerli nesne örneğinde (`this`, veya `Me` Visual Basic'te) ve ardından döndürür.

- Dispose(false) yöntemini çağıracak ve sonra döndürür, sonlandırıcı değiştirin.

- Bildirir ve uygulayan bir tür oluşturursanız <xref:System.IDisposable> emin olun, arabirim uygulamasını <xref:System.IDisposable> Bu bölümde daha önce açıklanan deseni izler.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği

Aşağıdaki sözde kod Dispose(bool) yönetilen kullanan bir sınıf içinde nasıl uygulanması gerekir ve yerel kaynaklara genel bir örnek sağlar.

```csharp
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
    // own unmanaged resources, but leave the other methods
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

## <a name="see-also"></a>Ayrıca bkz.

- [Dispose deseni (Çerçeve tasarım yönergeleri)](/dotnet/standard/design-guidelines/dispose-pattern)
- [(.NET Kılavuzu) yönetilmeyen kaynakları temizleme](/dotnet/standard/garbage-collection/unmanaged)