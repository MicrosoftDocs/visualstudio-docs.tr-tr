---
title: Yönetilen kod için yönetilen minimum Kurallar kural kümesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 83f8654a3cca246fa4853add231008e2fadbfc1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667908"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Yönetilen kod için Yönetilen Minimum Kurallar kural kümesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen minimum kurallar, olası güvenlik delikleri, uygulama kilitlenmesi ve diğer önemli mantık ve tasarım hataları da dahil olmak üzere kodunuzda en kritik sorunlara odaklanmaktadır. Bu kural kümesini, projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmelisiniz.

|Kural|Açıklama|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Atılabilen alanlara sahip türler atılabilir olmalıdır|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Boş sonlandırıcıları kaldırın|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Atılabilen alanlar atılmalıdır|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin|
