---
title: 'CA1003: Genel olay işleyici örnekleri kullan | Microsoft Docs'
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
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3c2cf2ad59f7ade337c84f13133bb5181afb615
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929094"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Genel olay işleyici örnekleri kullan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Void döndüren, imzası iki parametre (Birincisi nesne ve ikincisi Eventargs'a atanamaz türü) ve içeren derleme hedefleri içeren bir temsilci türü içeren [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Kural Tanımı
 Önce [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]olay işleyicisine özel bilgi geçirmek için yeni bir temsilci öğesinden türetilen bir sınıf belirtilen bildirilmesi gerekiyordu <xref:System.EventArgs?displayProperty=fullName> sınıfı. Bu artık geçerlidir [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], sunulan <xref:System.EventHandler%601?displayProperty=fullName> temsilci. Bu genel temsilcinin türetilen herhangi bir sınıf sağlar <xref:System.EventArgs> olay işleyicisi ile birlikte kullanılacak.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için temsilci kaldırın ve kullanımını koyacağınız <xref:System.EventHandler%601?displayProperty=fullName> temsilci. Temsilci tarafından otomatik olarak oluşturulan ise [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derleyici, olay bildirimi, kullanılacak söz dizimi değiştirilebilir <xref:System.EventHandler%601?displayProperty=fullName> temsilci.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralını ihlal eden bir temsilci gösterir. İçinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] örnek, Yorumlar kural karşılamak için örnek değiştirmek nasıl açıklanmaktadır. C# örnek için değiştirilen kodunu gösteren bir örnek izler.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, önceki örnekte, kural karşılar ve kullanımını değiştirir temsilci bildirimi kaldırır. `ClassThatRaisesEvent` ve `ClassThatHandlesEvent` yöntemleri kullanarak <xref:System.EventHandler%601?displayProperty=fullName> temsilci.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Koleksiyonlar genel arabirim uygulamalıdır](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Genel türlerde statik üyeleri belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanmayın](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Uygun yerlerde genel türler kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel Türler](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



