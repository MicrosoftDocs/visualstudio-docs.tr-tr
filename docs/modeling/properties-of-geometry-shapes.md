---
title: Geometri Şekillerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2159a7954059eedb0d5100cb41a33b47f7577e93
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967265"
---
# <a name="properties-of-geometry-shapes"></a>Geometri Şekillerinin Özellikleri
Geometrik şekiller, etki alanı sınıfların örneklerini bir etki alanına özgü dil nasıl görüntüleneceğini belirtmek için kullanabilirsiniz. Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikler kullanma hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Geometrik Şekiller aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu rengi|Bu şeklin dolgu rengi.|Beyaz|
|Dolgu gradyanı modu|(Yatay, dikey, İleri Köşegen, geriye köşegen veya hiçbiri), bu şeklin dolgu gradyanı modu.|Yatay|
|Geometri|Bu şeklin (dikdörtgen, yuvarlak köşeli dikdörtgen, elips veya daire) geometri.|Dikdörtgen|
|Varsayılan bağlantı noktalarını içerir|Varsa `True`şeklin üst, alt, sol kullanır ve doğru bağlantı noktaları oluşturulan tasarımcıdaki.|False|
|Anahat rengi|Bu şeklin ana hat rengi.|Siyah|
|Ana hat kesik çizgi stili|(Düz, kesik çizgi, nokta, çizgi nokta, çizgi nokta nokta veya özel), bu şeklin ana hat kesik çizgi stilinin.|Düz|
|Anahat kalınlığı|Bu şeklin ana hat kalınlığı.|0.03125|
|Metin rengi|Bu şeklin ile ilişkili metin dekoratörleri için kullanılan renk.|Siyah|
|Erişim değiştiricisi|Erişim değiştiricisi bir sınıfın (public veya internal).|Ortak|
|Özel Öznitelikler|Bu şeklin için oluşturulan kaynak kod sınıfı öznitelikler eklemek için kullanılır.|\<yok >|
|Çift oluşturur türetilmiş|Varsa `True`, hem temel sınıf hem de (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) bir kısmi sınıf oluşturulur. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel oluşturucu vardır.|Varsa `True`, kaynak kodunda özel bir oluşturucu sağlanacaktır. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Devralma şekilden oluşturulan kaynak kodu sınıf türünü açıklar (`none`, `abstract` veya `sealed`).|yok|
|Temel geometrik şekil|Bu şeklin temel sınıf.|(hiçbiri)|
|Ad|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şeklin ile bağlantılı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu türü|Nasıl bir araç ipucu (sabit, değişken veya hiçbiri) tanımlanır. Fixed ise ardından değerini `Fixed Tooltip Text` özelliği, araç ipucu olarak kullanılır; ardından değişken durumunda, araç ipucu özel kodda tanımlanır.|Yok.|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar.|\<yok >|
|İlk yükseklik|Bu şeklin inç cinsinden başlangıç yüksekliği.|1.|
|Başlangıç genişliği|Bu şeklin inç cinsinden başlangıç genişliği.|1,5|
|Özellik olarak kullanıma sunulan dolgu rengi<br /><br /> İfşa edilen dolgu gradyanı modu<br /><br /> Ana hat rengi özellik olarak kullanıma sunulan<br /><br /> Ana hat kesik çizgi stilinin özellik olarak kullanıma sunulan<br /><br /> Anahat kalınlığı özellik olarak kullanıma sunulan<br /><br /> Kullanıma sunan metin rengi|Varsa `True`, kullanıcının belirtilen özelliği bir şeklin ayarlayabilirsiniz. Bunu ayarlamak için Şekil tanımı sağ tıklatıp **ekleme kullanıma sunulan**.|False|
|Açıklama|Oluşturulan tasarımcının belgelemek için kullanılan bir açıklaması.|\<yok >|
|Görünen ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<yok >|
|Sabit araç ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<yok >|
|Yardım anahtar sözcüğü|Bu şeklin için F1 Yardımı dizini oluşturmak için kullanılan anahtar sözcüğü.|\<yok >|

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)