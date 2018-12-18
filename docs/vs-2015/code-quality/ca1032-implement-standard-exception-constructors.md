---
title: 'CA1032: Standart özel durum oluşturucuları uygulayın | Microsoft Docs'
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
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: efef441e84c4f1d51c633e3fdcb2da8d1ba3e963
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868618"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standart özel durum oluşturucuları uygulayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir türü genişleten <xref:System.Exception?displayProperty=fullName> ve gerekli tüm oluşturucular bildirmiyor.

## <a name="rule-description"></a>Kural Tanımı
 Özel durum türleri şu oluşturuculardan uygulamanız gerekir:

- Genel NewException()

- Genel NewException(string)

- Genel NewException (dize, özel durum)

- korumalı veya özel NewException (SerializationInfo, StreamingContext)

  Yapıcıların tüm ayarlamasını sağlamaktaki başarısızlık, istisnalarla başa çıkmayı zorlaştırabilir. Örneğin, bir imzaya sahip Oluşturucu `NewException(string, Exception)` diğer özel durumların neden olduğu bir özel durum oluşturmak için kullanılır. Oluşturma ve bir iç (yuvalanmış) özel durum içeren, özel durum örneği harekete Bu oluşturucu, yönetilen kod böyle bir durumda yapmalısınız olduğu. Kural gereği, ilk üç özel durum oluşturucuları ortaktır. Dördüncü Oluşturucu, mühürsüz sınıflar olarak korumalı ve korumalı sınıflardaki özel. Daha fazla bilgi için [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için eksik oluşturucular özel durumu ekleyin ve doğru erişilebilirlik sahip olduğunuzdan emin olun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Genel oluşturucular için farklı erişim düzeyi kullanarak ihlali neden olduğunda bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal eden bir özel durum türünü ve doğru bir şekilde uygulandığından bir özel durum türü içerir.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]



