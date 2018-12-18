---
title: Görüntü Şekillerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 20da1fc95160be69c1388f9d2986c7dc254eefa2
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967135"
---
# <a name="properties-of-image-shapes"></a>Görüntü Şekillerinin Özellikleri

Resim şekilleri, etki alanı sınıfları oluşturulan tasarımcıda nasıl göründüğünü belirlemek için kullanabilirsiniz. Bir resim şekli ayarlayarak tanımlarsanız `Image` önceden tanımlanmış bir görüntü dosyasına sınıfın özelliği. Aşağıdaki biçimleri desteklenir:

- .gif

- .jpg

- .JPEG

- .bmp

- .wmf

- .emf

- .PNG

Görüntü dosyaları gibi tasarımcı kaynak dosyaları bulunan varsayılan olarak, **kaynakları** klasöründe **Dsl** proje.

Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikler kullanma hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

Resim şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu rengi|Bu şeklin dolgu rengi.|Beyaz|
|Dolgu gradyanı modu|Bu şeklin dolgu gradyanı modu.|Yatay|
|Varsayılan bağlantı noktalarını içerir|Varsa `True`şeklin üst, alt, sol kullanır ve doğru bağlantı noktaları oluşturulan tasarımcıdaki.|False|
|Anahat rengi|Bu şeklin ana hat rengi.|Siyah|
|Ana hat kesik çizgi stili|(Düz, kesik çizgi, nokta, çizgi nokta, çizgi nokta nokta veya özel), bu şeklin ana hat kesik çizgi stilinin.|Düz|
|Anahat kalınlığı|Bu şeklin ana hat kalınlığı.|0.03125|
|Metin rengi|Bu şeklin ile ilişkili metin dekoratörleri için kullanılan renk.|Siyah|
|Erişim değiştiricisi|Geometri şekli (public veya internal) erişim değiştiricisi.|Ortak|
|Özel Öznitelikler|Bu şekle oluşturulan kaynak kod sınıfı öznitelikler eklemek için kullanılır.|\<yok >|
|Çift oluşturur türetilmiş|Varsa `True`, hem temel sınıf hem de (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) bir kısmi sınıf oluşturulur. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel oluşturucu vardır.|Varsa `True`, kaynak kodunda özel bir oluşturucu sağlanacaktır. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Görüntü şekilden oluşturulan kaynak kodu sınıf devralma türü açıklar (`none`, `abstract` veya `sealed`).|yok|
|Temel resim şekli|Bu şeklin temel sınıf.|(hiçbiri)|
|Ad|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şeklin ile bağlantılı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu türü|(Sabit, değişken veya hiçbiri) araç ipucu tanımlandığı yerde. Fixed ise ardından değerini `Fixed Tooltip Text` özelliği, araç ipucu olarak kullanılır; ardından değişken durumunda, araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkilendirilmiş resmi olmayan notlar.|\<yok >|
|İlk yükseklik|Bu şeklin inç cinsinden başlangıç yüksekliği.|1.|
|Başlangıç genişliği|Bu şeklin inç cinsinden başlangıç genişliği.|1,5|
|Özellik olarak kullanıma sunulan dolgu rengi<br /><br /> İfşa edilen dolgu gradyanı modu<br /><br /> Ana hat rengi özellik olarak kullanıma sunulan<br /><br /> Ana hat kesik çizgi stilinin özellik olarak kullanıma sunulan<br /><br /> Anahat kalınlığı özellik olarak kullanıma sunulan<br /><br /> Kullanıma sunan metin rengi|Varsa `True`, kullanıcının belirtilen özelliği bir şeklin ayarlayabilirsiniz. Bunu ayarlamak için Şekil tanımı sağ tıklatıp **ekleme kullanıma sunulan**.|False|
|Açıklama|Oluşturulan tasarımcının belge için kullanılır.|\<yok >|
|Görünen ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<yok >|
|Sabit araç ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<yok >|
|Yardım anahtar sözcüğü|Bu öğe için F1 Yardımı dizini oluşturmak için kullanılan anahtar sözcüğü.|\<yok >|
|Görüntü|Bu şeklin için kullanılan görüntü dosyasının yolu.|\<yok >|

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)