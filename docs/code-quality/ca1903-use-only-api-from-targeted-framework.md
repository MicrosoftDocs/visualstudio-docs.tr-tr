---
title: 'CA1903: Yalnızca hedeflenen çerçeveden API kullanın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1d42a74cfaf93ba0e8e5aec7e15c522d2e26b7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822819"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Yalnızca hedeflenen çerçeveden API kullanın

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategori|Microsoft.Portability|
|Yeni Değişiklik|-Bir açıkça görünen üyenin veya türün karşı imza tetiklendiğinde kesiliyor.<br /><br /> Bir yöntemin gövdesinde tetiklendiğinde bölünemez -.|

## <a name="cause"></a>Sebep
 Bir üyenin veya türün bir üyesi veya hizmet paketi bulunmayan projenin hedeflenen çerçeve ile sunulan türü kullanıyor.

## <a name="rule-description"></a>Kural açıklaması
 .NET Framework 2.0 Service Pack 1 ve 2, .NET Framework 3.0 Service Pack 1 ve 2 ve .NET Framework 3.5 Service Pack 1'de yeni üyeleri ve türleri dahil edilmişti. Önemli .NET Framework sürümlerini hedefleyen projeler, yeni API'leri yanlışlıkla bu bağımlılıkları alabilir. Bu bağımlılığı önlemek için bu kural herhangi bir yeni üyeler ve varsayılan olarak projenin hedef çerçevesi ile bulunmayan türleri kullanımları tetikler.

 **Hedef Framework ve hizmet paketi bağımlılıkları**

|||
|-|-|
|Hedef Framework'ü olduğunda|Kullanımları sürümünde üyeleri üzerinde harekete geçirilir|
|.NET Framework 2.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1 |
|.NET Framework 4|Yok|

 Bir projenin hedef Framework'ü değiştirmek için bkz: [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Hizmet paketi bağımlılığı kaldırmak için yeni üyenin veya türün tüm kullanımları kaldırın. Bu kasıtlı bir bağımlılık ise, uyarı veya bu kuralını devreden çıkar.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Belirtilen hizmet paketinin bilinçli bağımlı değilse bu kuraldan bir uyarıyı bastırmayın. Bu durumda, uygulamanız bu hizmet paketinin yüklü olmadığı sistemlerde çalıştırmak başarısız olabilir. Bu uyarının gösterilmemesi veya bu kasıtlı bir bağımlılık ise bu kuralı devre dışı bırakabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yalnızca .NET 2.0 Service Pack 1'de kullanılabilir olan DateTimeOffset türü kullanan bir sınıfı gösterir. Bu örnek, .NET Framework 2.0 proje özelliklerini hedef çerçeve açılır listede seçilen gerektirir.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yukarıda açıklanan ihlali kullanımları DateTimeOffset türü DateTime türü ile değiştirerek düzeltir.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Taşınabilirlik Uyarıları](../code-quality/portability-warnings.md)
- [Belirli Bir .NET Framework Sürümünü Hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md)