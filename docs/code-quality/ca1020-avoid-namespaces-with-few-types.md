---
title: 'CA1020: Birkaç türü olan ad alanlarından kaçının'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc7a691cb5c5626ea096046e277ec3d1655db0b6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546226"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Birkaç türü olan ad alanlarından kaçının

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Genel ad başka bir ad alanı Beşten az türleri içerir.

## <a name="rule-description"></a>Kural açıklaması

Her ad alanlarınıza mantıksal düzenlemesi vardır ve seyrek doldurulmuş bir ad alanına türleri koymak için geçerli bir nedeni var olduğundan emin olun. Ad alanları, birlikte Çoğu senaryoda kullanılan türler içermelidir. Uygulamalarını karşılıklı olarak birbirini dışlar, ayrı ad alanlarında türleri bulunmalıdır. Örneğin, <xref:System.Web.UI> ad alanı, web uygulamalarında kullanılan türler içerir ve <xref:System.Windows.Forms> ad alanı olarak kullanılan türler içerir [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-tabanlı uygulamaları. Kullanıcı arabirimi özelliklerini denetleyen türleri her iki ad alanına sahip olsa da, bu türleri aynı uygulamada kullanılmak üzere tasarlanmamıştır. Bu nedenle, bunlar ayrı ad alanlarında bulunur. Bir özelliğin bulunabilirliğini artıracağı için dikkatli ad kuruluş de yararlı olabilir. Ad alanı hiyerarşisi inceleyerek kitaplığı tüketicileri bir özelliği uygulayan türler bulabilir olması gerekir.

> [!NOTE]
> Tasarım zamanı türlerinde ve izinlerde bu kılavuzu ile uyum sağlamak için diğer ad alanları içine birleştirilmesini değil. Bu tür, kendi ad alanlarında, ana ad alanının altındaki ait ve ad alanlarını bitmelidir `.Design` ve `.Permissions`sırasıyla.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için tek bir ad alanına birkaç türlerini içeren ad alanları birleştirmek deneyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Ad alanı, diğer ad alanlarında türleri ile kullanılan türler içermediğinde bu kuraldan bir uyarıyı bastırmak güvenlidir.