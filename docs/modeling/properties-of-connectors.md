---
title: Bağlayıcıların Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e26401247c2b6cefc3d86dbd5b6e80adfe473937
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967317"
---
# <a name="properties-of-connectors"></a>Bağlayıcıların Özellikleri
Bağlayıcılar, etki alanı ilişkileri oluşturulan tasarımcıda temsil eder.

 Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikler kullanma hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Bağlayıcılar aşağıdaki tabloda listelenen özellikleri vardır.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Renk|Bu bağlayıcının rengi.|Siyah|
|Kesik çizgi stili|Bu bağlayıcının (düz, kesik çizgi, nokta, çizgi nokta, çizgi nokta nokta veya özel) satırı için çizgi stili.|Düz|
|Kaynak uç stili|(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond veya hiçbiri) bu bağlayıcının kaynak uç stili.|Yok.|
|Hedef uç stili|(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond veya hiçbiri) bu bağlayıcının hedef uç stili.|Yok.|
|Metin rengi|Bu bağlayıcıyla ilişkili metin dekoratörleri için kullanılan renk.|Siyah|
|Kalınlığı|Bu bağlayıcının inç cinsinden ölçülen çizgi kalınlığı.|0.03125|
|Erişim değiştiricisi|Sınıf erişim düzeyini (`public` veya `internal`).|Ortak|
|Özel Öznitelikler|Bu bağlayıcı oluşturulan kaynak kod sınıfı öznitelikler eklemek için kullanılır.|\<yok >|
|Çift oluşturur türetilmiş|Varsa `True`, hem temel sınıf hem de (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) bir kısmi sınıf oluşturulur. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel oluşturucu vardır.|Varsa `True`, kaynak kodunda özel bir oluşturucu sağlanacaktır. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Devralma bağlayıcısından oluşturulan kaynak kodu sınıf türünü açıklar (`none`, `abstract` veya `sealed`).|yok|
|Temel bağlayıcı|Bu bağlayıcının temel sınıf.|(hiçbiri)|
|Ad|Bu bağlayıcı adı.|Geçerli ad|
|Ad Alanı|Bu bağlayıcı ile bağlantılı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu türü|Nasıl bir araç ipucu (sabit, değişken veya hiçbiri) tanımlanır. Fixed ise ardından değerini `Fixed Tooltip Text` özelliği, araç ipucu olarak kullanılır; ardından değişken durumunda, araç ipucu özel kodda tanımlanır.|\<yok >|
|Notlar|Bu bağlayıcı ile ilişkilendirilen resmi olmayan notlar.|\<yok >|
|Yönlendirme stilini|Bağlayıcıyı yönlendirmek için kullanılan stil. A `Rectilinear` bağlayıcı yapar dik açılı kapatır gerekli; bir `Straight` Bağlayıcısı yok.|Dönüşler|
|Özellik olarak kullanıma sunulan rengi<br /><br /> Özellik olarak kullanıma sunulan kesik çizgi stili<br /><br /> Özellik olarak kullanıma sunulan kalınlığı<br /><br /> Kullanıma sunan metin rengi|Varsa `True`, kullanıcının belirtilen özelliği bir şeklin ayarlayabilirsiniz. Bunu ayarlamak için Şekil tanımı sağ tıklatıp **ekleme kullanıma sunulan**.|False|
|Açıklama|Oluşturulan tasarımcının belge için kullanılır.|\<yok >|
|Görünen ad|Bu bağlayıcı için oluşturulan tasarımcıda görüntülenecek ad.|\<yok >|
|Sabit araç ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<yok >|
|Yardım anahtar sözcüğü|Bu öğe için F1 Yardımı dizini oluşturmak için kullanılan anahtar sözcüğü.|\<yok >|

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)