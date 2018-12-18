---
title: Yapıları ve sınıfları yorumlama | Microsoft Docs
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
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 965a823c658516edf247f6a99d23d189097b31f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801491"
---
# <a name="annotating-structs-and-classes"></a>Yapıları ve Sınıfları Yorumlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
-   `_Struct_size_bytes_(size)`  
  
     Readable ve writable öğeleri (veya boyutunu bayt) tarafından belirtilen sahip bir alan `size`.  
  
     Yapı ya da sınıf bildirimi için geçerlidir.  Geçerli bir nesne türü tarafından belirtilen bayt sayısı ile bildirilen türünden daha büyük olabileceğini gösterir `size`.  Örneğin:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Arabellek boyutu parametresinin bayt `pM` türü `MyStruct *` olmasını alınır:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL'yi anlama](../code-quality/understanding-sal.md)   
 [İşlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md)   
 [İşlev davranışını yorumlama](../code-quality/annotating-function-behavior.md)   
 [Kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md)   
 [Açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [İç işlevleri](../code-quality/intrinsic-functions.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)



