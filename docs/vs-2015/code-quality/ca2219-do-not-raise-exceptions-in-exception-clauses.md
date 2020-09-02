---
title: 'CA2219: özel durum yan tümcelerinde özel durum yükseltmeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538534"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Özel durum yan tümceleri içinde özel durum harekete geçirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Bölünmez, kırılmamış|

## <a name="cause"></a>Nedeni
 Bir `finally` , Filter veya fault yan tümcesinden bir özel durum atılır.

## <a name="rule-description"></a>Kural Tanımı
 Özel durum yan tümcesinde bir özel durum ortaya çıktığında hata ayıklama zorluğunu büyük ölçüde artırır.

 Bir veya fault yan tümcesinde bir özel durum ortaya çıktığında `finally` , yeni özel durum varsa etkin özel durumu gizler. Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.

 Bir filtre yan tümcesinde bir özel durum harekete geçirilir, çalışma zamanı özel durumu sessizce yakalar ve filtrenin false olarak değerlendirilmesini sağlar. Filtre ve bir filtreden throw bir özel durum arasındaki farkı anlatmak için bir yol yoktur. Bu, filtrenin mantığındaki hataları algılamayı ve hata ayıklamayı zorlaştırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın bu ihlalini onarmak için, bir özel durumu `finally` , bir filtre veya hata tümceciğinden açık bir şekilde yapılandırmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural için bir uyarı bastırmayın. Bir özel durum yan tümcesinde oluşturulan özel durumun, yürütülen koda bir avantaj sağladığı bir senaryo yoktur.

## <a name="related-rules"></a>İlgili kurallar
 [CA1065: Beklenmeyen konumlarda özel durum harekete geçirmeyin](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Tasarım uyarıları](../code-quality/design-warnings.md)
