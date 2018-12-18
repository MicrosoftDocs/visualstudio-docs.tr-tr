---
title: "CA2240: ISerializable'ı doğru uygulayın"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2cf56f8fc692b79ef6e0c1b19bcbd3de4a1f647f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548394"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable'ı doğru uygulayın

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Dışarıdan görünen tür özelleşmemiş <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimi ve aşağıdaki koşullar doğruysa:

- Tür devralır, ancak geçersiz <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> yöntemi ve türü ile işaretli olmayan örnek alanlarını bildirir <xref:System.NonSerializedAttribute?displayProperty=fullName> özniteliği.

- Tür korumalı değil ve türün uyguladığı bir <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> dışarıdan görünür ve geçersiz kılınabilir bir yöntemi.

## <a name="rule-description"></a>Kural açıklaması
 Örnek, devralınan bir türde bildirilen alanları <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimi seri hale getirme işleminde otomatik olarak bulunmaz. Tür alanları içerecek şekilde uygulamalıdır <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi ve Serileştirme Oluşturucu. Alanları serileştirilecek değil, uygulama <xref:System.NonSerializedAttribute> alanları kararı açıkça belirtmek için özniteliği.

 Uygulamaları mühürlendi olmayan türlerde <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi dışarıdan görünür. Bu nedenle, yöntem, türetilen türler tarafından çağrılabilir ve geçersiz kılınabilir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için olun <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi geçersiz kılınabilir ve tüm örnek alanları seri hale getirme işlemine dahil veya açıkça işaretli olduğundan emin olun <xref:System.NonSerializedAttribute> özniteliği.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kural ihlal iki serializable türler gösterir.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek iki önceki ihlalleri geçersiz kılınabilir uygulaması sağlayarak giderir <xref:System.Runtime.Serialization.ISerializable.GetObjectData> kitap sınıfı ve uygulaması sağlayarak `GetObjectData` kitaplığı sınıfta.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>İlgili kuralları

- [CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Serileştirme yöntemlerini doğru uygulama](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)