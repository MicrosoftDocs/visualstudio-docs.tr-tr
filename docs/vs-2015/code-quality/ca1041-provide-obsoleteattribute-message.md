---
title: 'CA1041: ObsoleteAttribute iletisi sağlayın | Microsoft Docs'
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
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f67bbd93816da3bcae389493b74623f0cf4776c0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914729"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute iletisi sağlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir tür veya üye kullanılarak işaretlenmiş bir <xref:System.ObsoleteAttribute?displayProperty=fullName> sahip olmayan bir öznitelik kendi <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> özelliği belirtilmelidir.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.ObsoleteAttribute> kullanım dışı kitaplığı türleri ve üyeleri işaretlemek için kullanılır. Kitaplık Tüketiciler, herhangi bir tür veya üye artık kullanılmıyor olarak işaretlendiğinden kullanımı kaçınmanız gerekir. Desteklenmiyor ve sonunda Kitaplığı'nın daha yeni sürümlerinden kaldırılacak olmasıdır. Bir tür veya üye işaretlendiğinde kullanarak <xref:System.ObsoleteAttribute> derlenir, <xref:System.ObsoleteAttribute.Message%2A> özniteliğinin özelliği görüntülenir. Bu eski türü veya üye kullanıcı bilgilerini sağlar. Bu bilgiler genellikle ne kadar eski türü içerir veya üye kullanılacak kitaplık tasarımcılar ve tercih edilen değişiklik tarafından desteklenecektir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için ekleme `message` parametresi <xref:System.ObsoleteAttribute> Oluşturucusu.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Çünkü bu kuraldan bir uyarıyı bastırmayın <xref:System.ObsoleteAttribute.Message%2A> özelliği geçersiz bir türe veya üyeye hakkında önemli bilgiler sağlar.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, doğru bildirilmiş olan eski bir üye gösterir <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.ObsoleteAttribute?displayProperty=fullName>



