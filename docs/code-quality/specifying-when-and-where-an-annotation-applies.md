---
title: Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 9d99ebce3adc27039763e11ed4882a20199e8469
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920621"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme
Ek açıklamanın koşullu olduğunda Çözümleyicisi belirtmek için diğer ek açıklamaları gerektirebilir.  Bir işlev zaman uyumlu veya zaman uyumsuz bir değişken varsa, örneğin, işlevi aşağıdaki gibi davranır: zaman uyumlu durumda her zaman sonunda başarılı ancak hemen gerçekleştirilemiyor zaman uyumsuz durumda, bir hata bildirir. İşlev zaman uyumlu olarak çağrıldığında değil döndüğünden çünkü sonuç değeri denetleme kodu Çözümleyicisi için herhangi bir değer sağlar.  Ancak, işlevi zaman uyumsuz olarak adlandırılır ve işlev sonucunu işaretli olduğunda, önemli bir hata meydana gelebilir. Bu örnek kullanmak bir durum gösterilir `_When_` ek açıklama — bu makalenin sonraki bölümlerinde açıklanan — denetimini etkinleştirmek için.

## <a name="structural-annotations"></a>Yapısal ek açıklamaları
 Ne zaman ve nerede ek açıklamaları uygulamak denetlemek için aşağıdaki yapısal ek açıklamaları kullanın.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` bir lvalue döndüren bir ifadedir. Ek açıklamalar `anno-list` tarafından adlı nesneye uygulanır `expr`. Her eklenti için `anno-list`, `expr` ön koşul ek açıklamanın ön koşul yorumlanır ve sonrası koşul IF ek açıklamanın sonrası koşul olarak yorumlanır yorumlanır.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` bir lvalue döndüren bir ifadedir. Ek açıklamalar `anno-list` tarafından adlı nesneye uygulanır `expr`. Her eklenti için `anno-list`, `expr` ön koşul ek açıklamanın önkoşulu yorumlanır ve sonrası koşul IF ek açıklamanın sonrası koşul olarak yorumlanır yorumlanır.<br /><br /> `iter` ek açıklamanın için kapsamlı bir değişken adı (inclusive, `anno-list`). `iter` örtük türüne sahip `long`. Aynı adlı değişkenleri herhangi çevreleyen kapsamdaki değerlendirme sürümünden gizlenir.<br /><br /> `elem-count` bir tamsayı olarak değerlendiren bir ifadedir.|
|`_Group_(anno-list)`|Ek açıklamalar `anno-list` tüm her ek açıklama uygulanan Grup ek açıklama uygulandığı niteleyicisi sahibi olarak kabul edilir.|
|`_When_(expr, anno-list)`|`expr` dönüştürülebilir bir ifade `bool`. Sıfır olduğunda (`true`), belirtilen ek açıklamalar `anno-list` geçerli olarak kabul edilir.<br /><br /> Varsayılan olarak, her eklenti için `anno-list`, `expr` ek açıklamanın bir önkoşulu ve çıktı değerleri kullanarak olarak ek açıklama sonrası bir koşul ise giriş değerleri kullanılarak olarak yorumlanır. Varsayılan değer geçersiz kılmak için kullanabileceğiniz `_Old_` giriş değerleri kullanılması gerektiğini belirtmek için sonrası bir koşul değerlendirirken iç. **Not:** farklı ek açıklamaları kullanılarak gruplarındaki sonucu olarak etkinleştirilmesi `_When_` değişebilir bir değer — Örneğin, `*pLength`— çünkü söz konusu değerlendirilen sonucu `expr` önkoşulu kendi değerlendirilen farklı olabilir sonrası koşuluna neden.|

## <a name="see-also"></a>Ayrıca Bkz.
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [SAL anlama](../code-quality/understanding-sal.md) [işlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md) [işlevdavranışınıyorumlama](../code-quality/annotating-function-behavior.md) [Yapıları ve sınıfları yorumlama](../code-quality/annotating-structs-and-classes.md) [kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md) [iç işlevler](../code-quality/intrinsic-functions.md) [en iyi yöntemler ve örnekler](../code-quality/best-practices-and-examples-sal.md)