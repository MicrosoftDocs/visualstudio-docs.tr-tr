---
title: Yapıları ve Sınıfları Yorumlama
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: e4294284ff2911fd05cc771bf4deaad368e3c28b
ms.sourcegitcommit: 95aedf723c6be5272c3c5a2911cb2bdec50e2148
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47228831"
---
# <a name="annotating-structs-and-classes"></a>Yapıları ve Sınıfları Yorumlama
Yapı ve sınıf üyeleri okuduğunuzda gibi davranan ek açıklamalar kullanarak açıklama ekleyebilirsiniz; herhangi bir işlev çağrısı veya bir parametre veya bir sonuç değeri kapsayan yapısı gerektirir. işlev girişi/çıkışı en doğru olduğu varsayılmıştır.

## <a name="struct-and-class-annotations"></a>Yapı ve sınıf ek açıklamaları

-   `_Field_range_(low, high)`

     Aralık (dahil) gelen alanın bulunduğu `low` için `high`.  Eşdeğer `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` uygun önceki veya sonraki koşullarını kullanarak ek açıklamalı nesneye uygulanan.

-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Öğeleri (veya bayt) belirtilen bir yazılabilir boyut sahip bir alan `size`.

-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Öğeleri (veya bayt) belirtilen bir yazılabilir boyut sahip bir alan `size`ve `count` okunabilir bu öğelerin (bayt).

-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Readable ve writable öğeleri (veya boyutunu bayt) tarafından belirtilen sahip bir alan `size`.

-   `_Field_z_`

     Null ile sonlandırılmış bir dize sahip bir alan.

-   `_Struct_size_bytes_(size)`

     Yapı ya da sınıf bildirimi için geçerlidir.  Geçerli bir nesne türü tarafından belirtilen bayt sayısı ile bildirilen türünden daha büyük olabileceğini gösterir `size`.  Örneğin:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Arabellek boyutu parametresinin bayt `pM` türü `MyStruct *` olmasını alınır:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [SAL anlama](../code-quality/understanding-sal.md) [işlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md) [işlevdavranışınıyorumlama](../code-quality/annotating-function-behavior.md) [Kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md) [açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md) [iç işlevleri](../code-quality/intrinsic-functions.md) [en iyi uygulamalar ve Örnekleri](../code-quality/best-practices-and-examples-sal.md)
