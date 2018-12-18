---
title: Etki Alanı İlişkilerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3ec468ebedbe1d15ddff3527bcf0783b9831247e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966446"
---
# <a name="properties-of-domain-relationships"></a>Etki Alanı İlişkilerinin Özellikleri
Özellikler aşağıdaki tabloda, bir etki alanı ilişkisi ile ilişkilendirilir. Etki alanı ilişkileri hakkında daha fazla bilgi için bkz: [anlama modelleri, sınıfları ve ilişkileri](../modeling/understanding-models-classes-and-relationships.md). Bu özellikler kullanma hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Erişim değiştiricisi|Alan ilişkisine ait erişim düzeyini (`public` veya `internal`).|`public`|
|Özel Öznitelikler|Etki alanına ilişkisinden oluşturulan kaynak kod sınıfı öznitelikler eklemek için kullanılır.|\<yok >|
|Çift oluşturur türetilmiş|Varsa `True`, hem temel sınıf hem de (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) bir kısmi sınıf oluşturulur. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Özel oluşturucu vardır.|Varsa `True`, özel bir oluşturucu kaynak kodunda sağlandığını belirtir. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Devralma değiştiricisi|Etki alanına ilişkisinden oluşturulan kaynak kodu sınıf devralma türü açıklar (`none`, `abstract` veya `sealed`).|\<yok >|
|Yinelenen sağlar|Varsa `True`, etki alanı ilişkisine ait yinelenen bağlantıların aynı iki öğe oluşturulabilir.|`False`|
|Temel ilişki|Etki alanı ilişkisi türetilmişse, etki alanı ilişkisinin temel ilişkisi.|\<yok >|
|Gömme olduğu|Varsa `True`, etki alanı ilişki gömme ilişkisi vardır. Varsa `False`, bir başvuru ilişkisi ilişkidir.|\<her ikisi de >|
|Ad|Etki alanı ilişkisi adı.|Geçerli ad|
|Ad Alanı|Etki alanı ilişkisi ile bağlantılı olan ad alanı.|Geçerli ad alanı|
|Notlar|Etki alanı ilişkisi ile ilişkili resmi olmayan notlar.|\<yok >|
|Açıklama|Kod belge için kullanılır ve oluşturulan tasarımcının kullanıcı Arabiriminde kullanılan açıklaması.|\<yok >|
|Görünen ad|Etki alanı ilişkisi için oluşturulan tasarımcıda görüntülenecek ad.|\<yok >|
|Yardım anahtar sözcüğü|Etki alanı ilişkisi için F1 Yardımı dizini oluşturmak için kullanılan isteğe bağlı anahtar sözcük.|\<yok >|

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)