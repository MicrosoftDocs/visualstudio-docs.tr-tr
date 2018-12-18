---
title: 'CA2227: Koleksiyon özellikleri salt okunur olmalıdır'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: f1bbd3e6ba97d969694e7d2142978c12552b3c50
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860257"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Koleksiyon özellikleri salt okunur olmalıdır

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Dışarıdan görünen, yazılabilir bir özellik uygulayan bir tür olan <xref:System.Collections.ICollection?displayProperty=fullName>. Bu kural, diziler, dizin oluşturucular (Özellikler) 'Öğesini' adı ile ve izin kümeleri yok sayar.

## <a name="rule-description"></a>Kural açıklaması

Yazılabilir koleksiyon özelliği kullanıcının koleksiyonun tamamen farklı bir koleksiyon ile değiştirin izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak hala ayarlamak tek tek üyeleri sağlar. Bir hedef koleksiyonunu değiştirme varsa, tercih edilen tasarım deseni tüm öğeleri koleksiyondan kaldırmak için bir yöntem ve koleksiyonu yeniden doldurmak için bir yöntem eklemektir. Bkz: <xref:System.Collections.ArrayList.Clear%2A> ve <xref:System.Collections.ArrayList.AddRange%2A> yöntemlerinin <xref:System.Collections.ArrayList?displayProperty=fullName> sınıfı bu düzeni gösteren bir örnek.

İkili hem XML serileştirme koleksiyonlar salt okunur özelliklerini destekler. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Sınıfında uygulayan türler için belirli gereksinimler <xref:System.Collections.ICollection> ve <xref:System.Collections.IEnumerable?displayProperty=fullName> seri hale getirilebilir olması.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için özelliği salt okunur yapma. Tasarım gerektiriyorsa, temizlemek ve koleksiyon derlenmeye yöntemleri ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Özelliğin parçası ise uyarıyı gözardı edebileceğini bir [veri aktarım nesnesini (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) sınıfı.

Aksi takdirde, bu kuraldan uyarıları bastırmayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yazılabilir koleksiyon özelliğini türüyle gösterir ve koleksiyonunu nasıl doğrudan değiştirilebilir gösterir. Ayrıca, bu salt okunur koleksiyon özelliğini kullanarak değiştirme tercih edilen şekilde gösterir `Clear` ve `AddRange` yöntemleri.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>İlgili kuralları

- [CA1819: Özellikler diziler döndürmemelidir](../code-quality/ca1819-properties-should-not-return-arrays.md)