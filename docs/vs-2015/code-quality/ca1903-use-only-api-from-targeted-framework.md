---
title: 'CA1903: Yalnızca hedeflenen çerçeveden API kullanın. | Microsoft Docs'
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
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c23b25029775cd3abca84e695c50b5a0fdf68cf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191587"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Yalnızca hedeflenen çerçeveden API kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 ile ilgili en son belgeler için bkz. [CA1903: Yalnızca hedeflenen çerçeveden API kullanın](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework) docs.microsoft.com'da.  
  
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Kategori|Microsoft.Portability|  
|Yeni Değişiklik|-Bir açıkça görünen üyenin veya türün karşı imza tetiklendiğinde kesiliyor.<br /><br /> Bir yöntemin gövdesinde tetiklendiğinde olmayan son -.|  
  
## <a name="cause"></a>Sebep  
 Bir üyenin veya türün bir üyesi veya hizmet paketi bulunmayan projenin hedeflenen çerçeve ile sunulan türü kullanıyor.  
  
## <a name="rule-description"></a>Kural Tanımı  
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
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Hizmet paketi bağımlılığı kaldırmak için yeni üyenin veya türün tüm kullanımları kaldırın. Bu kasıtlı bir bağımlılık ise, uyarı veya kuralın devre dışı.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Belirtilen hizmet paketinin bilinçli bağımlı değilse bu kuraldan bir uyarıyı bastırmayın. Bu durumda, uygulamanız bu hizmet paketinin yüklü olmadığı sistemlerde çalıştırmak başarısız olabilir. Bu uyarının gösterilmemesi veya bu kasıtlı bir bağımlılık ise bu kuralı devre dışı bırakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yalnızca .NET 2.0 Service Pack 1'de kullanılabilir olan DateTimeOffset türü kullanan bir sınıfı gösterir. Bu örnek, .NET Framework 2.0 proje özelliklerini hedef çerçeve açılır listede seçilen gerektirir.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yukarıda açıklanan ihlali kullanımları DateTimeOffset türü DateTime türü ile değiştirerek düzeltir.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Taşınabilirlik uyarıları](../code-quality/portability-warnings.md)   
 [Belirli Bir .NET Framework Sürümünü Hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md)

