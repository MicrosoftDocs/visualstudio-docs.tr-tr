---
title: 'CA1822: Üyeleri statik olarak işaretleyin | Microsoft Docs'
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
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7b85d12038d4c505f912dd2f9440829f2c80679c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183501"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Üyeleri statik olarak işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 ile ilgili en son belgeler için bkz. [CA1822: üyeleri statik olarak işaretlemek](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static) docs.microsoft.com'da.  
  
|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|Kategori|Microsoft.Performance|  
|Yeni Değişiklik|Bölünemez - üyesi derlemenin dışında görünür değilse bağımsız olarak, değişiklik. Örnek üyesine ile yalnızca üye değiştirmeniz halinde olmayan en son - `this` anahtar sözcüğü.<br /><br /> -Üye statik bir üyeye bir örnek üyesi değiştirirseniz ve derlemenin dışında görünür kesiliyor.|  
  
## <a name="cause"></a>Sebep  
 Örnek veri erişimi olmayan bir üye statik olarak işaretlenmemiş (paylaşılan [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).  
  
## <a name="rule-description"></a>Kural Tanımı  
 Örnek veri veya çağrı örnek yöntemlerinin erişmez üyeleri işaretlenebilir olarak statik (paylaşılan [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Sanal olmayan arama sitelerini yayma, geçerli nesne işaretçisinin null dışında değer xenapp'i her çağrı çalışma zamanında bir onay engeller. Bu, ölçülebilir kazanç performansını performans duyarlı kodunuz için elde edebilirsiniz. Bazı durumlarda geçerli nesne örneğine erişmek için başarısızlık, bir doğruluk sorununu temsil eder.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Üye statik olarak işaretleyin (veya paylaşılan [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) veya 'this' kullanma / yönteminde ' Me' body, uygun olduğunda.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Daha önce sevk edilen kod düzeltme bir değişiklik olur için bu kuraldan bir uyarıyı bastırmak güvenlidir.  
  
## <a name="related-rules"></a>İlgili kuralları  
 [CA1811: Çağrılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Örneklendirilmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Kullanılmayan yerel öğeleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)

