---
title: 'CA1504: yanıltıcı alan adlarını gözden geçirin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d375b64bbc877cb377157f13b3e4cfa7c7cf1592
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547881"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Yanıltıcı alan adlarını gözden geçirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategori|Microsoft. Bakımolmaması|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir örnek alanının adı "s_" ile başlar veya bir `static` ( `Shared` ın [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) alanının adı "m_" ile başlar.

## <a name="rule-description"></a>Kural Tanımı
 "S_" ile başlayan alan adları, birçok kullanıcı tarafından statik verilerle ilişkilendirilir. Benzer şekilde, "m_" ile başlayan alan adları, örnek (üye) verilerle ilişkilendirilir. Daha kolay yönetilebilir kod için adlar genellikle kullanılan kurallara uymalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, uygun öneki kullanarak alanı yeniden adlandırın. Alternatif olarak, değiştirici ekleyerek veya kaldırarak alanı geçerli sonek ile kabul edin `static` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.
