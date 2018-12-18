---
title: İşlev davranışını yorumlama | Microsoft Docs
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
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88213e1cd8112aecac527f7d72d2d74dbf10c559
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783135"
---
# <a name="annotating-function-behavior"></a>İşlev Davranışını Yorumlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ek açıklama olarak [işlev parametrelerini ve dönüş değerleri](../code-quality/annotating-function-parameters-and-return-values.md), tüm işlev özelliklerinin açıklama ekleyebilirsiniz.  
  
## <a name="function-annotations"></a>İşlev ek açıklamaları  
 Şu ek açıklamaları işlevi bir bütün olarak uygular ve nasıl davranacağını ya da true olması beklenen açıklar.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Tek başına duramaz tasarlanmamıştır; Bunun yerine, bir koşul ile kullanılmak üzere olduğu `_When_` ek açıklama. Daha fazla bilgi için [belirtirken ve ek açıklama bir'burada geçerli](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name` Ayrıca şurada görünür rastgele bir dize parametresi, bir `_Function_class_` bazı işlevlerin bildiriminde ek açıklama.  `_Called_from_function_class_` şu anda analiz ediliyor işlevi kullanılarak eklenmişse sıfır döndürür `_Function_class_` aynı değerine sahip `name`; Aksi takdirde, sıfır döndürür.|  
|`_Check_return_`|Dönüş değeri açıklama ekler ve onu çağıran incelemelisiniz durumları. Void bir bağlamda işlev çağrılırsa denetleyicisi bir hata bildirir.|  
|`_Function_class_(name)`|`name` Parametresi, kullanıcı tarafından belirlenen rastgele bir dize.  Diğer ad alanlarını farklı bir ad alanında bulunmaktadır. Bir işlev, işlev işaretçisi veya — en usefully — bir işlev işaretçisi türü, bir veya daha fazla işlev sınıflarına ait olarak atanabilir.|  
|`_Raises_SEH_exception_`|Her zaman konusu yapılandırılmış özel durum işleyicisi (SEH) özel durum oluşturan bir işlev açıklama ekler `_When_` ve `_On_failure_` koşulları. Daha fazla bilgi için [belirtirken ve ek açıklama bir'burada geçerli](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|İsteğe bağlı olarak bir SEH özel yapılan neden olabilir bir işlev açıklama ekler `_When_` ve `_On_failure_` koşulları.|  
|`_Must_inspect_result_`|Dönüş değeri, parametreler ve genel öğeleri dahil olmak üzere, herhangi bir çıkış değeri açıklama ekler.  Çözümleyici açıklamalı nesnesindeki değeri değil sonradan Denetlenmekte bir hata bildirir. Koşullu ifadede kullanılır, çıkış parametresi atanan veya genel veya bir parametre olarak geçen "Denetleme" içerir.  Dönüş değerleri için `_Must_inspect_result_` gelir `_Check_return_`.|  
|`_Use_decl_annotations_`|Bir işlev tanımı (işlev gövdesi olarak da bilinir), üst bilgisindeki ek açıklamaları listesi yerine kullanılabilir.  Zaman `_Use_decl_annotations_` olan kullanıldığında, ayrıca sahip tanımında mevcut olmaları durumunda ek açıklamalar aynı işlevin bir kapsamdaki üstbilgi görünür kullanılır `_Use_decl_annotations_` ek açıklama.|  
  
## <a name="successfailure-annotations"></a>Başarı/başarısızlık ek açıklamaları  
 Bir işlev başarısız olur ve yaptığında, sonuçları tamamlanmamış veya işlevi başarılı olduğunda sonuçlardan farklılık gösterir.  Aşağıdaki listede ek açıklamalar hata davranışına express için yollar sağlar.  Bu ek açıklamaları kullanmak için başarıyı belirlemek bunları etkinleştirmeniz gerekir; Bu nedenle, bir `_Success_` eklenti gereklidir.  Dikkat `NTSTATUS` ve `HRESULT` zaten bir `_Success_` ; yerleşik ek açıklama ancak kendi belirtirseniz `_Success_` üzerindeki ek açıklama `NTSTATUS` veya `HRESULT`, yerleşik ek açıklama onu geçersiz kılar.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Eşdeğer `anno_list _On_failure_(anno_list)`; diğer bir deyişle, ek açıklamalar `anno_list` işlev başarılı olup olmadığını uygulayın.|  
|`_On_failure_(anno_list)`|Kullanılacak yalnızca `_Success_` işlev açıklama eklemek için de kullanılır — açıkça veya dolaylı olarak aracılığıyla `_Return_type_success_` bir TypeDef. Zaman `_On_failure_` bir işlevi parametre veya dönüş değeri, her ek açıklaması içinde ek açıklama varsa `anno_list` (Milattan) olarak kodlandıysa yokmuş gibi davranır `_When_(!expr, anno)`burada `expr` gerekli parametresi `_Success_` ek açıklama. Örtük uygulama buna `_Success_` tüm sonrası koşulları için geçerli değildir `_On_failure_`.|  
|`_Return_type_success_(expr)`|Tür tanımı uygulanabilir. Tüm İşlevler, yazın ve açıkça olmadığı döndüren gösterir `_Success_` bunlar varmış gibi ek açıklamalı `_Success_(expr)`. `_Return_type_success_` bir işlev veya bir işlev işaretçisi typedef kullanılamaz.|  
|`_Success_(expr)`|`expr` bir rvalue döndüren bir ifadedir. Zaman `_Success_` ek açıklama bir işlev bildirimi veya tanımı, her ek açıklama var (`anno`) işlev ve sonrası koşulu olarak kodlandıysa gibi davranır `_When_(expr, anno)`. `_Success_` Ek açıklama parametrelerinin değil, bir işlev yalnızca üzerinde kullanılabilir veya dönüş türü. En fazla bir olabilir `_Success_` bir işlev ve üzerindeki ek açıklama içinde olamaz `_When_`, `_At_`, veya `_Group_`. Daha fazla bilgi için [belirtirken ve ek açıklama bir'burada geçerli](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL'yi anlama](../code-quality/understanding-sal.md)   
 [İşlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Yapıları ve sınıfları yorumlama](../code-quality/annotating-structs-and-classes.md)   
 [Kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md)   
 [Açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [İç işlevleri](../code-quality/intrinsic-functions.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)



