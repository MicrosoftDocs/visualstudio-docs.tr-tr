---
title: 'CA1058: Türler belirli temel türleri aşmamalıdır | Microsoft Docs'
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
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a4ffbe3b359f2c58f8e301b9176981a2037c17f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912441"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Türler belli temel türleri genişletmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen tür belirli temel türleri genişletir. Şu anda, bu kural aşağıdaki türlerden türetilen türler raporları:

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.Xml.XmlDocument?displayProperty=fullName>

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.Queue?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Kural Tanımı
 İçin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürüm 1 tavsiye yeni özel durumlar türetmek için <xref:System.ApplicationException>. Öneri değiştirildi ve yeni özel durumlar türetilmelidir <xref:System.Exception?displayProperty=fullName> veya içinde alt sınıflarından birini <xref:System> ad alanı.

 Öğesinin oluşturmayın <xref:System.Xml.XmlDocument> , temel alınan bir nesne modeli veya veri kaynağı, bir XML görünümünü oluşturmak istiyorsanız.

### <a name="non-generic-collections"></a>Genel olmayan koleksiyon
 Kullanın ve/veya mümkün olduğunda genel koleksiyonları genişletin. Daha önce sevk sürece genel olmayan koleksiyon kodunuzda genişletmez.

 **Yanlış kullanım örnekleri**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Doğru kullanım örnekleri**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için farklı bir temel tür ya da bir genel koleksiyon tür türetilir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Hakkında ihlalleri bu kuraldan bir uyarıyı bastırmayın <xref:System.ApplicationException>. Hakkında ihlalleri bu kuraldan bir uyarıyı bastırmak güvenlidir <xref:System.Xml.XmlDocument>. Kodu önceden yayımlanan, genel olmayan koleksiyonu hakkında bir uyarı bastırmak güvenlidir.



