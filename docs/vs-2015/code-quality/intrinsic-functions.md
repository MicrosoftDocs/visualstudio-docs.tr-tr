---
title: İç işlevler | Microsoft Docs
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
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7258092b79ca0c10079a986e2a80b34c25660054
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788114"
---
# <a name="intrinsic-functions"></a>İç İşlevler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SAL bir ifadede, yan etkilere sahip olmayan bir ifade olması şartıyla C/C++ ifade olabilir — örneğin, ++,--ve işlev çağrıları bu bağlamda tümüne sahip yan etkiler.  SAL ancak, bazı işlev benzeri nesnelerin ve SAL ifadelerde kullanılabilir ayrılmış bazı semboller sağlar. Bunlar olarak adlandırılır *iç işlevleri*.  
  
## <a name="general-purpose"></a>Genel amaçlı  
 Aşağıdaki instrinsic işlevi ek açıklamalar için SAL genel yardımcı programını sağlar.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|`_Curr_`|Şu anda Not eklenen nesne için bir eşanlamlı.  Zaman `_At_` ek açıklama, kullanımda olan `_Curr_` ilk parametre olarak aynı `_At_`.  Aksi takdirde, parametre veya ek açıklama sözcüksel olarak ilişkili olduğu tüm işlevi dönüş değeridir.|  
|`_Inexpressible_(expr)`|Burada bir arabellek boyutu ek açıklama ifadesi kullanılarak temsil etmek için çok karmaşık bir durum ifade eder — Örneğin, ne zaman, bir giriş veri kümesi tarama ve sonra sayım hesaplanan üyeler seçili.|  
|`_Nullterm_length_(param)`|`param` en fazla arabellek ancak bir null Sonlandırıcı içermeden öğeleri sayısıdır. Toplama olmayan, void olmayan tür herhangi bir arabellek için uygulanabilir.|  
|`_Old_(expr)`|Önkoşul değerlendirildiğinde `_Old_` giriş değeri döndürür `expr`.  Sonrası koşulu değerlendirilirken, değeri döndürür. `expr` önkoşulu değerlendirilen gibi.|  
|`_Param_(n)`|`n`Parametresinden 1'den sayım, bir işleve `n`, ve `n` değişmez değer bir tamsayı sabitidir. Parametre ise, bu ek açıklama parametre adıyla erişmek için aynıdır. **Not:** `n` üç nokta tanımlanan ya da adları değil kullanıldığı işlev prototiplerinde kullanılabilir konumsal parametreleri başvurabilir.|  
|`return`|C/C++ ayrılmış anahtar sözcüğü `return` SAL ifadesinde bir işlev dönüş değeri belirtmek için kullanılabilir.  Değer yalnızca post kullanılabilir durumdadır; öncesi durumunda kullanmak için bir söz dizimi hatası var.|  
  
## <a name="string-specific"></a>Belirli dize  
 Şu iç işlev ek açıklamaları, dizeleri işlenmesini etkinleştirin. Bu işlevlerin dört aynı amaca hizmet eder: null Sonlandırıcı önce bulunan tür öğelerinin sayısını döndürmek için. Fark başvurulan öğeleri veri türleri vardır. Null ile sonlandırılmış uzunluğunu belirtmek istiyorsanız, arabellek Not değil karakterlerinden oluşan, kullanın `_Nullterm_length_(param)` önceki bölümde ek açıklama.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` dize kadar ancak bir null Sonlandırıcı içermeden öğeleri sayısıdır. Bu ek açıklama karakter dize türleri için ayrılmıştır.|  
|`strlen(param)`|`param` dize kadar ancak bir null Sonlandırıcı içermeden öğeleri sayısıdır. Bu ek açıklama ayrılmış karakter kullanın, diziler ve C çalışma zamanı işlevi benzer [strlen()](http://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
|`wcslen(param)`|`param` en fazla (ancak dahil değil) dizedeki öğe sayısı null Sonlandırıcı. Bu ek açıklama geniş karakter kullanın, diziler ve C çalışma zamanı işlevi benzer ayrılmış [wcslen ()](http://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL'yi anlama](../code-quality/understanding-sal.md)   
 [İşlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md)   
 [İşlev davranışını yorumlama](../code-quality/annotating-function-behavior.md)   
 [Yapıları ve sınıfları yorumlama](../code-quality/annotating-structs-and-classes.md)   
 [Kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md)   
 [Açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)



