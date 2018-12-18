---
title: 'CA1801: kullanılmayan parametreleri gözden geçir | Microsoft Docs'
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
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b0946e315aef0c333207d49eb14820d287a9b361
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269691"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Kullanılmayan parametreleri gözden geçir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 ile ilgili en son belgeler için bkz. [CA1801: kullanılmayan parametreleri gözden geçir](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters) docs.microsoft.com'da.  
  
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Kategori|Microsoft.Usage|  
|Yeni Değişiklik|Üyesi yaptığınız değişiklikler ne olursa olsun derlemenin dışında görünür değilse olmayan son -.<br /><br /> Üye kendi gövdesi içindeki bir parametre kullanmak için değiştirmeniz halinde olmayan en son -.<br /><br /> -Parametresini kaldırın ve derlemenin dışında görünür olup olmadığını kesiliyor.|  
  
## <a name="cause"></a>Sebep  
 Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir. Bu kural, aşağıdaki yöntemlerden incelemez:  
  
-   Temsilci tarafından başvurulan yöntemleri.  
  
-   Olay işleyicileri kullanılan yöntemleri.  
  
-   Yöntemleri ile bildirilmiş `abstract` (`MustOverride` Visual Basic) değiştirici.  
  
-   Yöntemleri ile bildirilmiş `virtual` (`Overridable` Visual Basic) değiştirici.  
  
-   Yöntemleri ile bildirilmiş `override` (`Overrides` Visual Basic) değiştirici.  
  
-   Yöntemleri ile bildirilmiş `extern` (`Declare` deyimi Visual Basic) değiştirici.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Parametreleri onlara erişmek için hata doğruluk hiçbir olduğundan emin olmak için yöntemin gövdesinde kullanılmayan sanal olmayan yöntemlerde gözden geçirin. Kullanılmayan parametreler Bakım ve performans ücret yansıtılmaz.  
  
 Bazen bu kuralın ihlalini yöntemi bir uygulama hatasını işaret edebilir. Örneğin, bir parametre yöntemin gövdesinde kullanılmış. Parametre geriye dönük uyumluluk nedeniyle zorundaysa bu kuralın uyarılarını gizle.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Bu kural ihlalini düzeltmek için kullanılmayan (önemli bir değişiklik) parametreyi kaldırın veya yöntem gövdesi (bir hataya neden olmayan değişiklik) parametresini kullanın.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Daha önce sevk edilen kod düzeltme bir değişiklik olur için bu kuraldan bir uyarıyı bastırmak güvenlidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki yöntem gösterir. Bir yöntem kuralı ihlal etmektedir ve kural başka bir yöntem karşılar.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]  
  
## <a name="related-rules"></a>İlgili kuralları  
 [CA1811: Çağrılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Örneklendirilmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Kullanılmayan yerel öğeleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)

