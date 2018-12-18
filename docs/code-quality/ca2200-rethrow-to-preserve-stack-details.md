---
title: 'CA2200: Yığın ayrıntılarını korumak için yeniden fırlatma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1cc85931ed51bcd3df3a044452af59a530746805
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550897"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Yığın ayrıntılarını korumak için yeniden fırlatma

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Bir özel durum yeniden oluşur ve özel durum açıkça belirtilen `throw` deyimi.

## <a name="rule-description"></a>Kural açıklaması

Bir özel durum sonra bunu izleme bilgileri parçası yığın izlemesi aşağıdadır. Yığın izlemesi, özel durum oluşturur ve özel durumu yakalar yöntemi ile biten yöntem ile başlayan yöntemi çağrı hiyerarşisini listesidir. Özel durum belirterek yeniden durum varsa `throw` deyimi, yığın izlemesi geçerli bir yöntem yeniden başlatılır ve özel durum döndüren özgün yöntem ile geçerli yöntemi arasındaki yöntem çağrılarını listesini kaybolur. Özel durum ile özgün yığın izleme bilgileri tutmak için kullanın `throw` özel durum belirtmeden deyimi.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için özel durum açıkça belirtmeden özel durumu yeniden.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir yöntemi gösterir `CatchAndRethrowExplicitly`, kural ve bir yöntem ihlal `CatchAndRethrowImplicitly`, kural karşılar.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]