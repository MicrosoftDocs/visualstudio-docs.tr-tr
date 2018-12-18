---
title: 'CA1810: Başvuru türü statik alanları satır içi | Microsoft Docs'
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
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e4d7ffbe4fc821ffd70b0bb299b2a4738d63873b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862690"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Başvuru türü statik alanları satır içi başlatın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategori|Microsoft.Performance|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir başvuru türü açık bir statik Oluşturucu bildirir.

## <a name="rule-description"></a>Kural Tanımı
 Bir tür açık statik yapıcı bildirdiğinde, JIT derleyici her bir statik yöntemi kontrol ekler ve türün yapıcı örneği statik yapıcının daha önceden çağrıldığından emin olur. Statik başlatma, statik bir üyeye erişildiğinde veya türünün bir örneği oluşturulduğunda tetiklenir. Ancak, statik başlatma türünün bir değişkeni bildirmek, ancak bunu olabilen başlatma genel durumu değişirse önemli kullanmayın tetiklenmiyor.

 Tüm statik veriler başlatılmış satır içi ve açık bir statik Oluşturucu bildirimi yapılmadı, Microsoft Ara dil (MSIL) derleyicileri ekleme `beforefieldinit` bayrağı ve MSIL türüne statik verinin başlatır örtük bir statik Oluşturucu, tanımı. JIT derleyicisi karşılaştığında `beforefieldinit` bayrak, çoğu zaman statik Oluşturucu denetimleri eklenmez. Statik başlatma, tüm statik alanları erişebilmek için önce ancak statik bir yöntemi veya örnek oluşturucusu olmayan çağrılmadan önce bir süre sonra gerçekleşmesi için sağlanır. Bu statik başlatma türünde bir değişken bildirildikten sonra herhangi bir zamanda meydana gelebilir unutmayın.

 Statik oluşturucu denetimleri performansı düşürebilir. Genellikle bir statik Oluşturucu, yalnızca statik alanları, servis talebi, yalnızca statik başlatmanın emin olmalısınız statik bir alana erişim ilk önce oluştuğu başlatmak için kullanılır. `beforefieldinit` Davranıştır bu ve diğer birçok tür için uygun. Yalnızca statik başlatma genel durumunu etkiler ve aşağıdaki koşullardan biri uygunsuz olur:

-   Genel durum üzerindeki etkisini, pahalıdır ve türü kullanılmaz, gerekli değildir.

-   Genel durum etkileri herhangi türü statik alanları erişmeden erişilebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Performans önemli değilse bu kuraldan bir uyarıyı bastırmak güvenlidir; türün statik bir yöntem çağrılır veya türünün bir örneği oluşturulduktan önce gerçekleşmesi için statik başlatma tarafından neden genel durum değişiklikleri pahalıdır veya gerekir veya garanti.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir tür gösterir `StaticConstructor`, kural ve bir tür ihlal `NoStaticConstructor`, kural karşılamak için satır içi başlatma ile statik oluşturucuyu değiştirir.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Ek unutmayın `beforefieldinit` bayrağının MSIL tanımında `NoStaticConstructor` sınıfı.

 **Genel .class otomatik ANSI StaticConstructor** **genişletir [mscorlib]System.Object**
 **{**
 **} / / son StaticConstructorsınıfı** 
 **.class genel otomatik ANSI beforefiledinit NoStaticConstructor** **genişletir [mscorlib]System.Object**
 **{** 
 **} / / son NoStaticConstructor sınıfı**
## <a name="related-rules"></a>İlgili kuralları
 [CA2207: Değer türü statik alanları satır içi başlatın](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)



