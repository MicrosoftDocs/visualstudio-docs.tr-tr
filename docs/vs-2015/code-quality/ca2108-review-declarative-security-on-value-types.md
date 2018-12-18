---
title: 'CA2108: Değer türleri üzerinde bildirimsel güvenliği gözden geçirin | Microsoft Docs'
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
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b437fa656c2a2d0650463fd0ab78119f67099ac7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889673"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Değer türleri üzerinde bildirimsel güvenliği gözden geçirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Ortak veya korunan değer türü tarafından güvenliği sağlanan bir [veri ve modelleme](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) veya [bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Kural Tanımı
 Değer türleri ayrılan ve diğer oluşturucular yürütmeden önce kendi varsayılan oluşturucu tarafından başlatılır. Bir değer türü, isteğe bağlı ya da LinkDemand tarafından güvenlik altına alınır ve arayan güvenlik denetimi, herhangi bir oluşturucu dışında uygun izinlere sahip değil'de varsayılan başarısız olur ve bir güvenlik özel durumu oluşturulur. Değer türü serbest değil; kendi varsayılan oluşturucu tarafından ayarlanmış durumda kalır. Değer türü örneğini geçirir bir çağıranın oluşturun veya örnek erişim izni olduğunu varsaymayın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Güvenlik denetimi türünden kaldırın ve onun yerine kullanmak yöntem düzeyi güvenlik denetimleri sürece bu kural ihlalini düzeltmek olamaz. Bu şekilde ihlali düzeltme değer türü örneklerini alma gelen yetersiz izinlerle çağıranlar önlemez unutmayın. Bir değer türü örneği, varsayılan durumunda, hassas bilgileri kullanıma sunmuyor ve zararlı bir biçimde kullanılamaz emin olmanız gerekir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Herhangi bir çağıranın varsayılan durumuna içinde değer türüne örneklerini güvenlik tehdit taşıyor olmadan elde bu kuraldan bir uyarıyı gösterilmemesini sağlayabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal eden bir değer türü içeren bir kitaplık gösterir. Unutmayın `StructureManager` türü, değer türü örneğini geçirir bir çağıranın oluşturun veya örnek erişim izni olduğunu varsayar.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama kitaplığın zayıflık gösterir.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Özel oluşturucu yapısı: istek başarısız oldu. ** 
 **Yeni değerleri SecuredTypeStructure 100 100**
**yeni değerleri SecuredTypeStructure 200 200**
## <a name="see-also"></a>Ayrıca Bkz.
 [Bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [veri ve modelleme](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



