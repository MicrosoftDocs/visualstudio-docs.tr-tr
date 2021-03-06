---
title: Etki Alanı İlişkilerinin Özellikleri
description: Erişim değiştiricisi, custome öznitelikleri gibi bir etki alanı ilişki dükkanı ile ilişkili özellikler hakkında bilgi edinin ve çift türetilmiş bir üretir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc92bbc32a454208f3d455734b7697a2e69037b4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390665"
---
# <a name="properties-of-domain-relationships"></a>Etki Alanı İlişkilerinin Özellikleri
Aşağıdaki tabloda yer alan Özellikler bir etki alanı ilişkisiyle ilişkilendirilir. Etki alanı ilişkileri hakkında daha fazla bilgi için bkz. [modelleri, sınıfları ve Ilişkileri anlama](../modeling/understanding-models-classes-and-relationships.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Erişim değiştiricisi|Etki alanı ilişkisine erişim düzeyi ( `public` veya `internal` ).|`public`|
|Özel Öznitelikler|Etki alanı ilişkisinden oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Double türevi üretir|Eğer `True` bir temel sınıf ve kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Özel Oluşturucusu vardır|İse `True` , kaynak kodda özel bir oluşturucunun sağlandığını gösterir. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Devralma değiştiricisi|Etki alanı ilişkisinden oluşturulan kaynak kodu sınıfının devralım türünü açıklar ( `none` `abstract` veya `sealed` ).|\<none>|
|Yinelemelere izin verir|İse `True` , aynı iki öğe arasında etki alanı ilişkisinin Yinelenen bağlantıları oluşturulabilir.|`False`|
|Temel Ilişkiler|Etki alanı ilişkisi türetildiyse, etki alanı ilişkisinin temel ilişkisi.|\<none>|
|Ekleniyor|İse `True` , etki alanı ilişkisi bir katıştırma ilişkisidir. İse `False` , ilişki bir başvuru ilişkisidir.|\<both>|
|Name|Etki alanı ilişkisinin adı.|Geçerli ad|
|Ad Alanı|Etki alanı ilişkisiyle bağlantılı olan ad alanı.|Geçerli ad alanı|
|Notlar|Etki alanı ilişkisiyle ilişkili resmi olmayan notlar.|\<none>|
|Açıklama|Kodu belgelemek için kullanılan açıklama ve oluşturulan tasarımcının Kullanıcı arabiriminde kullanılır.|\<none>|
|Görünen Ad|Etki alanı ilişkisi için oluşturulan tasarımcıda görüntülenen ad.|\<none>|
|Help anahtar sözcüğü|Etki alanı ilişkisi için F1 yardımını dizine eklemek üzere kullanılan isteğe bağlı anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))