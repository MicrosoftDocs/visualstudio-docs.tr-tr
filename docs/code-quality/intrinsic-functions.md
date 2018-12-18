---
title: İç İşlevler
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 0e58f84a48104553e5517d24f746769e6f0959e5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920954"
---
# <a name="intrinsic-functions"></a>İç İşlevler
Bu yan etkileri sahip olmayan bir ifade değil sağlanan SAL deyimde C/C++ bir ifade olabilir — örneğin, ++,--ve bu bağlamda tümüne sahip yan etkileri işlevi çağırır.  SAL ancak, bazı işlev benzeri nesneleri ve SAL ifadelerde kullanılabilir bazı ayrılmış simgeleri sağlar. Bunlar denir *iç işlevler*.

## <a name="general-purpose"></a>Genel amaçlı
 Aşağıdaki instrinsic işlevi ek açıklamalar için SAL genel yardımcı program sağlar.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_Curr_`|Şu anda açıklama nesne eşanlamlısı.  Zaman `_At_` ek açıklama kullanılıyor, `_Curr_` ilk parametre olarak aynı `_At_`.  Aksi takdirde, parametre veya ek açıklama sözcüksel olarak ilişkili olduğu tüm işlevi/dönüş değeri olur.|
|`_Inexpressible_(expr)`|Burada bir arabellek boyutu, ek açıklama ifade kullanarak temsil etmek için çok karmaşık bir durum ifade eder — Örneğin, ne zaman, bir giriş veri kümesi tarama ve sonra sayım hesaplanan üyeleri seçilmiş.|
|`_Nullterm_length_(param)`|`param` Arabellek kadar ancak null Sonlandırıcı hariç öğelerinde sayısıdır. Toplama olmayan, void olmayan türündeki tüm arabelleğe uygulanabilir.|
|`_Old_(expr)`|Önkoşul değerlendirildiğinde `_Old_` giriş değeri döndürür `expr`.  Sonrası koşulunda değerlendirilirken değeri döndürür `expr` bu önkoşulu değerlendirilen gibi.|
|`_Param_(n)`|`n`Parametresinden 1'den sayım bir işleve `n`, ve `n` değişmez değer bir tamsayı sabiti olduğunda. Parametre olarak adlandırılmışsa, bu ek açıklama ada göre parametre erişmek için aynıdır. **Not:** `n` elips tarafından tanımlanan veya işlev prototipleri adları değil kullanıldığı kullanılabilir konumsal parametreler başvurabilir.  |
|`return`|C/C++ anahtar sözcüğü ayrılmış `return` SAL ifadede bir işlevin dönüş değeri belirtmek için kullanılabilir.  Değer yalnızca post kullanılabilir durumda; öncesi durumunda kullanmak için bir sözdizimi hatası var.|

## <a name="string-specific"></a>Belirli dize
 Aşağıdaki iç işlevi ek açıklamaları dizeleri işlenmesini sağlar. Bu işlevlerin dört aynı amaca hizmet eder: önce boş bir sonlandırıcı bulunamadı türdeki öğeleri sayısını döndürmek için. Farkları başvurulan öğelerinde veri türleridir. Null ile sonlandırılmış uzunluğunu belirtmek istiyorsanız, arabellek unutmayın değil karakterlerinden oluşur, kullanın `_Nullterm_length_(param)` önceki bölümdeki ek açıklama.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_String_length_(param)`|`param` dize kadar ancak null Sonlandırıcı hariç öğelerinde sayısıdır. Bu ek açıklama karakter dizesi türleri için ayrılmıştır.|
|`strlen(param)`|`param` dize kadar ancak null Sonlandırıcı hariç öğelerinde sayısıdır. Bu ek açıklama karakter kullanımı diziler ve C çalışma zamanı işlevi benzer ayrılmış [strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param` kadar (ancak dahil değil) dizesinde öğe sayısı null Sonlandırıcı. Bu ek açıklama geniş karakter kullanımı diziler ve C çalışma zamanı işlevi benzer ayrılmış [wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Ayrıca Bkz.
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [SAL anlama](../code-quality/understanding-sal.md) [işlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md) [işlevdavranışınıyorumlama](../code-quality/annotating-function-behavior.md) [Yapıları ve sınıfları yorumlama](../code-quality/annotating-structs-and-classes.md) [kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md) [açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md) [en iyi uygulamalar ve örnekler](../code-quality/best-practices-and-examples-sal.md)