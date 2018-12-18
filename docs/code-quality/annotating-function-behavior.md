---
title: İşlev Davranışını Yorumlama
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7ee46c277574b9ceec2c4b0a26685570d305990f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899361"
---
# <a name="annotating-function-behavior"></a>İşlev Davranışını Yorumlama
Ek açıklama olarak [işlev parametrelerini ve dönüş değerleri](../code-quality/annotating-function-parameters-and-return-values.md), tüm işlevi özelliklerini açıklama ekleyebilirsiniz.

## <a name="function-annotations"></a>İşlev ek açıklamaları
 Aşağıdaki ek açıklamaları işlevi bir bütün olarak uygulanır ve nasıl davranacağını veya bu doğru olmasını bekler.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Tek başına üzere tasarlanmamıştır; Bunun yerine, bir koşul ile kullanılacak olan `_When_` ek açıklama. Daha fazla bilgi için bkz: [belirtirken ve bir ek açıklama geçerli olduğu](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name` Parametredir de görünür rasgele bir dizeyi bir `_Function_class_` bazı işlevler bildiriminde ek açıklama.  `_Called_from_function_class_` şu anda ayrıştırılıyor işlevi kullanarak ek açıklama eklenmişse sıfır olmayan döndürür `_Function_class_` , aynı değere sahip `name`; Aksi halde, sıfır döndürür.|
|`_Check_return_`|Dönüş değeri açıklama ekler ve arayan da incelemelisiniz durumları. Void bağlamda işlevi çağrıldıysa denetleyicisi bir hata bildirir.|
|`_Function_class_(name)`|`name` Kullanıcı tarafından belirlenen rasgele bir dizeyi bir parametredir.  Diğer ad alanlarını farklı bir ad alanı bulunmaktadır. İşlev, işlev işaretçisi veya — en usefully — bir işlev işaretçisi türü, bir veya daha fazla işlevi sınıflarına ait olarak atanabilir.|
|`_Raises_SEH_exception_`|Her zaman yapılan bir yapılandırılmış özel durum işleyicisi (SEH) özel durumu oluşturan işlevi açıklama ekler `_When_` ve `_On_failure_` koşulları. Daha fazla bilgi için bkz: [belirtirken ve bir ek açıklama geçerli olduğu](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|İsteğe bağlı olarak SEH istisna tabi yükseltmek bir işlev açıklama ekler `_When_` ve `_On_failure_` koşulları.|
|`_Must_inspect_result_`|Dönüş değeri, parametreler ve genel öğeleri dahil olmak üzere, herhangi bir çıktı değer açıklama ekler.  Çözümleyici açıklamalı nesnesindeki değeri değil sonradan Denetlenmekte bir hata bildirir. Koşullu bir ifadede kullanılan, çıktı parametresi atanan veya genel veya parametre olarak geçirilen olup olmadığını "Denetleme" içerir.  Dönüş değerleri için `_Must_inspect_result_` gelir `_Check_return_`.|
|`_Use_decl_annotations_`|Bir işlev tanımı (işlev gövdesi olarak da bilinir), listenin üst bilgisindeki açıklamalarının yerine kullanılabilir.  Zaman `_Use_decl_annotations_` olan de sahip tanımında mevcut olup olmadığını olarak kullanıldığında, aynı işlevi için bir kapsam içinde üstbilgisi görünür ek açıklamalar kullanılan `_Use_decl_annotations_` ek açıklama.|

## <a name="successfailure-annotations"></a>Başarı/hata ek açıklamaları
 Bir işlev başarısız olabilir ve yaptığında, sonuçları tamamlanmamış veya işlev başarılı olduğunda sonuçlarından farklı.  Aşağıdaki listede ek açıklamalar hatası davranışı express için yollar sağlar.  Bu ek açıklamalar kullanmak için bunları başarısını belirlemek etkinleştirmeniz gerekir; Bu nedenle, bir `_Success_` ek açıklama gereklidir.  Dikkat `NTSTATUS` ve `HRESULT` zaten bir `_Success_` ; yerleşik ek açıklama ancak kendi belirtirseniz, `_Success_` ek açıklamayı `NTSTATUS` veya `HRESULT`, yerleşik ek açıklama geçersiz kılar.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_Always_(anno_list)`|Eşdeğer `anno_list _On_failure_(anno_list)`; diğer bir deyişle, ek açıklamalar `anno_list` işlevi başarılı olup olmadığına bakılmaksızın uygulayın.|
|`_On_failure_(anno_list)`|Kullanılacak yalnızca `_Success_` işlevi açıklama eklemek için de kullanılır — açıkça ya da örtük olarak aracılığıyla `_Return_type_success_` bir typedef üzerinde. Zaman `_On_failure_` bir işlevi parametresi veya dönüş değeri, her ek açıklama içinde ek açıklama varsa `anno_list` (saat) olarak kodlanmış sanki gibi davranır `_When_(!expr, anno)`, burada `expr` parametresi gerekli `_Success_` ek açıklama. Kapsanan uygulamasının buna `_Success_` sonrası koşulların tümü için geçerli değildir `_On_failure_`.|
|`_Return_type_success_(expr)`|Typedef için uygulanabilir. Tüm İşlevler, yazın ve açıkça bulunmayan o return gösterir `_Success_` sahip oldukları gibi açıklama `_Success_(expr)`. `_Return_type_success_` bir işlev veya işlev işaretçisi typedef kullanılamaz.|
|`_Success_(expr)`|`expr` bir rvalue döndüren bir ifadedir. Zaman `_Success_` ek açıklama varsa bir işlev bildirimi veya tanımı, her ek açıklama (`anno`) işlevi ve sonrası koşulu olarak kodlanmış gibi davranır `_When_(expr, anno)`. `_Success_` Ek açıklama parametreleri değil, bir işlev yalnızca üzerinde kullanılabilir veya dönüş türü. En çok bir olabilir `_Success_` bir işlev ve ek açıklamayı birinde olamaz `_When_`, `_At_`, veya `_Group_`. Daha fazla bilgi için bkz: [belirtirken ve bir ek açıklama geçerli olduğu](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Ayrıca Bkz.
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [SAL anlama](../code-quality/understanding-sal.md) [işlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md) [yapıları ve sınıflarıyorumlama](../code-quality/annotating-structs-and-classes.md) [Kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md) [açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md) [iç işlevler](../code-quality/intrinsic-functions.md) [en iyi uygulamalar ve Örnekler](../code-quality/best-practices-and-examples-sal.md)