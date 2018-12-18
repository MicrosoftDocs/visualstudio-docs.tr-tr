---
title: 'CA1822: Üyeleri statik olarak işaretleyin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b90b3dedfb76d222a8d9344c81410327de09e153
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894540"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Üyeleri statik olarak işaretleyin

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Kategori|Microsoft.Performance|
|Yeni Değişiklik|Bölünemez - üyesi derlemenin dışında görünür değilse bağımsız olarak, değişiklik. Örnek üyesine ile yalnızca üye değiştirmeniz halinde olmayan en son - `this` anahtar sözcüğü.<br /><br /> -Üye statik bir üyeye bir örnek üyesi değiştirirseniz ve derlemenin dışında görünür kesiliyor.|

## <a name="cause"></a>Sebep
 Örnek veri erişimi olmayan bir üye statik olarak işaretlenmemiş (paylaşılan [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Kural açıklaması
 Örnek veri veya çağrı örnek yöntemlerinin erişmez üyeleri işaretlenebilir olarak statik (paylaşılan [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Sanal olmayan arama sitelerini yayma, geçerli nesne işaretçisinin null dışında değer xenapp'i her çağrı çalışma zamanında bir onay engeller. Bu, ölçülebilir kazanç performansını performans duyarlı kodunuz için elde edebilirsiniz. Bazı durumlarda geçerli nesne örneğine erişmek için başarısızlık, bir doğruluk sorununu temsil eder.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Üye statik olarak işaretleyin (veya paylaşılan [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) veya 'this' kullanma / yönteminde ' Me' body, uygun olduğunda.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Daha önce sevk edilen kod düzeltme bir değişiklik olur için bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="related-rules"></a>İlgili kuralları
 [CA1811: Çağrılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Örneklendirilmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Kullanılmayan yerel öğeleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)