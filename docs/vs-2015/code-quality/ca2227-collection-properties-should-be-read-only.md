---
title: 'CA2227: Koleksiyon Özellikleri salt okunur | Microsoft Docs'
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
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1db0ab6bae6a374726e953e505247896864c7f0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830450"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Koleksiyon özellikleri salt okunur olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir yazılabilir özelliği uygulayan bir tür olan <xref:System.Collections.ICollection?displayProperty=fullName>. Diziler, dizin oluşturucular (Özellikler) 'Öğesini' adı ile ve izin kümeleri, kural tarafından göz ardı edilir.

## <a name="rule-description"></a>Kural Tanımı
 Yazılabilir koleksiyon özelliği kullanıcının koleksiyonun tamamen farklı bir koleksiyon ile değiştirin izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir. Bir hedef koleksiyonunu değiştirme varsa, tercih edilen tasarım deseni koleksiyondaki tüm öğeleri kaldırmak için bir yöntem ve koleksiyonu yeniden doldurmak için bir yöntem eklemektir. Bkz: <xref:System.Collections.ArrayList.Clear%2A> ve <xref:System.Collections.ArrayList.AddRange%2A> yöntemlerinin <xref:System.Collections.ArrayList?displayProperty=fullName> sınıfı bu düzeni gösteren bir örnek.

 İkili hem XML serileştirme koleksiyonlar salt okunur özelliklerini destekler. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Sınıfında uygulayan türler için belirli gereksinimler <xref:System.Collections.ICollection> ve <xref:System.Collections.IEnumerable?displayProperty=fullName> seri hale getirilebilir olması.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için özelliği salt okunur yapma ve tasarım gerektiriyorsa, Temizle ve koleksiyonu yeniden doldurmak için yöntemleri ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir yazılabilir koleksiyon özelliğini türüyle gösterir ve koleksiyonunu nasıl doğrudan değiştirilebilir gösterir. Ayrıca, tercih edilen şekilde salt okunur koleksiyon özelliğini kullanarak değiştirme `Clear` ve `AddRange` yöntemleri gösterilmektedir.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1819: Özellikler diziler döndürmemelidir](../code-quality/ca1819-properties-should-not-return-arrays.md)



