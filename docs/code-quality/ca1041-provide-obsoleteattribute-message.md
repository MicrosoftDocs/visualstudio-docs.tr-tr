---
title: 'CA1041: ObsoleteAttribute iletisi sağlayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d8e8a4be147a786da06f3fdb7f961a7b36aa85a4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546968"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute iletisi sağlayın

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir tür veya üye kullanılarak işaretlenmiş bir <xref:System.ObsoleteAttribute?displayProperty=fullName> sahip olmayan bir öznitelik kendi <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> özelliği belirtilmelidir.

## <a name="rule-description"></a>Kural açıklaması
 <xref:System.ObsoleteAttribute> kullanım dışı kitaplığı türleri ve üyeleri işaretlemek için kullanılır. Kitaplık Tüketiciler, herhangi bir tür veya üye artık kullanılmıyor olarak işaretlendiğinden kullanımı kaçınmanız gerekir. Desteklenmiyor ve sonunda Kitaplığı'nın daha yeni sürümlerinden kaldırılacak olmasıdır. Bir tür veya üye işaretlendiğinde kullanarak <xref:System.ObsoleteAttribute> derlenir, <xref:System.ObsoleteAttribute.Message%2A> özniteliğinin özelliği görüntülenir. Bu eski türü veya üye kullanıcı bilgilerini sağlar. Bu bilgiler genellikle ne kadar eski türü içerir veya üye kullanılacak kitaplık tasarımcılar ve tercih edilen değişiklik tarafından desteklenecektir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için ekleme `message` parametresi <xref:System.ObsoleteAttribute> Oluşturucusu.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Çünkü bu kuraldan bir uyarıyı bastırmayın <xref:System.ObsoleteAttribute.Message%2A> özelliği geçersiz bir türe veya üyeye hakkında önemli bilgiler sağlar.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, doğru bildirilmiş olan eski bir üye gösterir <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Ayrıca bkz.
 <xref:System.ObsoleteAttribute?displayProperty=fullName>