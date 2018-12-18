---
title: 'CA2112: Güvenli türler alanları açığa çıkarmamalıdır | Microsoft Docs'
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
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a09093d05758d58828b9d7ca73223243252cb23c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871465"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Güvenli türler alanları açığa çıkarmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı tür ortak alanları içerir ve tarafından güvenli hale getirilen bir [bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Kural Tanımı
 Bağlantı talebi tarafından güvenli türde bir örnek kod erişimi varsa, kod türün alanlarına erişmek için bağlantı talebine sahip değildir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için alanları ortak olmayan ve ortak özellik veya alan verisi döndüren yöntemler ekleyin. LinkDemand güvenlik denetimleri türlerinde türün özellikleri ve yöntemleri erişimi koruyun. Ancak, kod erişim güvenliği alanlar için geçerli değildir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Hem güvenlik sorunlarını ve iyi bir tasarım, ortak alanları özel hale getirerek ihlalleri düzeltmeniz gerekir. Alanın güvenli kalması gereken bilgi tutmazsa bu kuraldan bir uyarıyı gözardı edebileceğini ve alanın içeriklerine güvenmeyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir kitaplık türü oluşur (`SecuredTypeWithFields`) güvenli olmayan alanlarla bir tür (`Distributor`) kitaplığı türün örneğini oluşturabilir ve hatalı geçişleri örnekleri türleri için bunları oluşturma iznine sahip değil ve uygulama kodu Bu tür güvenliğini iznine sahip değil olsa bile bir örneğin alanları okuyabilirsiniz.

 Aşağıdaki kitaplık kodu kuralı ihlal ediyor.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Örnek
 Uygulama koruyan güvenli tür bağlantı isteği nedeniyle bir örneği oluşturulamıyor. Aşağıdaki sınıf güvenli türünün bir örneği elde etmek için uygulamayı etkinleştirir.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama nasıl güvenli bir türün yöntemlerini erişim izni kod kendi alanlarına erişebilir gösterilmektedir.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **SecuredTypeWithFields örneği oluşturuluyor. ** 
 **Güvenli tür alanları: 22, 33**
**güvenli türün alan değiştiriliyor... ** 
 **Önbelleğe nesne alanları: 99, 33**
## <a name="related-rules"></a>İlgili kuralları
 [CA1051: Görünür örnek alanlarını bildirmeyin](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [veri ve modelleme](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



