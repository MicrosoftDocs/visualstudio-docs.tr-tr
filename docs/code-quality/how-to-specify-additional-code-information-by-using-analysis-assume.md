---
title: 'Nasıl yapılır: _Analysis_assume kullanarak ek kod bilgileri belirtme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ce8102bbc790019490c4dc2a2ccbfab7d8c33981
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031533"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Nasıl yapılır: _Analysis_assume kullanarak ek kod bilgileri belirtme
Çözümleme işleminin yardımcı olmak ve Uyarıları azaltmak C/C++ kodu için kod analizi aracı için ipuçları sağlayabilir. Ek bilgi sağlamak için aşağıdaki işlev kullanın:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -true değerlendirileceği varsayılır herhangi bir ifade.

 Kod çözümleme aracı ifade tarafından temsil edilen koşul işlevi burada görünür ve ifade, örneğin, bir değişkene atama tarafından değiştirilinceye kadar doğrudur noktasında doğru olduğunu varsayar.

> [!NOTE]
>  `_Analysis_assume` kodu iyileştirme etkilemez. Kod çözümleme aracı dışında `_Analysis_assume` no-op tanımlanır.

## <a name="example"></a>Örnek
 Aşağıdaki kod `_Analysis_assume` kod çözümleme uyarısı düzeltmek için [C6388](../code-quality/c6388.md):

```
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [__assume](/cpp/intrinsics/assume)