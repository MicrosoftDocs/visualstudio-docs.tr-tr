---
title: 'CA2236: ISerializable türler üzerinde taban sınıf yöntemleri çağırabilir | Microsoft Docs'
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
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bcde222020ca18b918ad694abe42c2c76a4a613c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886688"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir tür uygulayan türünden türer <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimi ve aşağıdaki koşullar doğruysa:

-   Diğer bir deyişle, bir Oluşturucu ile seri hale getirme oluşturucusunu türün uyguladığı <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> parametre imzası, temel türün seri hale getirme oluşturucusunu çağırmaz, ancak.

-   Türün uyguladığı <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> yöntemi ancak arama <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> temel türün yöntemi.

## <a name="rule-description"></a>Kural Tanımı
 Bir özel seri hale getirme işleminde bir türün uyguladığı <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> kendi alanlarına ve seri durumdan çıkarılamıyor alanlar için seri hale getirme oluşturucusunu serileştirmek için yöntemi. Türü uygulayan türünden türer, <xref:System.Runtime.Serialization.ISerializable> arabirim, temel tür <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi ve Serileştirme Oluşturucusu çağrılabilir seri hale getirmek/sona erdirme olanağı-serialize için temel türün alanları. Aksi takdirde, türü değil sıralanabilir ve doğru şekilde json'dan seri. Türetilmiş tür yeni alanları eklemez, türü uygulamak gerekmez, unutmayın <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi ya da seri hale getirme oluşturucusunu veya temel tür eşdeğeri arayın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için temel tür çağrı <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi veya serileştirme Oluşturucu öğelerinden karşılık gelen türetilmiş tür yöntem veya Oluşturucu.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kural seri hale getirme oluşturucusunu çağırarak karşılayan türetilmiş bir tür gösterir ve <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi temel sınıf.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serileştirme yöntemlerini doğru uygulama](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)



