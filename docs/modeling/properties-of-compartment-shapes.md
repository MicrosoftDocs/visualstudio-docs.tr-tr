---
title: Bölme Şekillerinin Özellikleri
description: Bölme şekillerinin etki alanına özgü bir dilde etki alanı sınıfını görüntülemek için kullanabileceğiniz şekillerden biri olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ec84057bfe7d49760a8f95132a30e8c927f60f0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390834"
---
# <a name="properties-of-compartment-shapes"></a>Bölme Şekillerinin Özellikleri
Bölme şekilleri, etki alanına özgü bir dilde bir etki alanı sınıfı görüntülemek için kullanabileceğiniz şekillerden birisidir. Bölmeleri genişlet ve daralt.

 Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için, [bkz. Domain-Specific Dili Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Bölme şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Varsayılan Genişletme Daraltma Durumu|ise `Expanded` bölmeler oluşturma sırasında gösterilir. ise, `Collapsed` bunlar değildir.|Genişletildi|
|Dolgu Rengi|Bu şeklin dolgu rengi.|Beyaz|
|Dolgu Gradyan Modu|Bu şeklin dolgu gradyan modu.|Yatay|
|Geometri|Bu şeklin geometrisi (Dikdörtgen veya Yuvarlanmış Dikdörtgen).|Dikdörtgen|
|Varsayılan Bağlantı Noktalarına Sahip|ise, `True` şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|Yanlış|
|Tek Bölme üst bilgisi görünür durumda mı?|ve `False` şeklinin tek bir bölmesi varsa bölmenin üst bilgisi görünmez.|Doğru|
|Ana Hat Rengi|Bu şeklin ana hat rengi.|Siyahi|
|Çizgi Çizgi Stili|Bu şeklin ana hat çizgi stili (Solid, Dash, Dot, DashDot, DashDotDot, Custom).|Düz|
|Ana Hat Kalınlığı|Bu şeklin ana hat kalınlığı.|0.03125|
|Metin Rengi|Bu şekille ilişkili metin dekoratörleri için kullanılan renk.|Siyahi|
|Erişim Değiştiricisi|Bölme şeklinin ( veya ) erişim `public` `internal` düzeyi.|Genel|
|Özel Öznitelikler|Bu bölme şeklinden oluşturulan kaynak kod sınıfına öznitelikler eklemek için kullanılır|\<none>|
|Çift Türetilen|ise, `True` hem temel bir sınıf hem de kısmi bir sınıf (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Özel Oluşturucuya Sahip|ise, `True` kaynak kodunda özel bir oluşturucu sağlanır. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Devralma Değiştiricisi|Bölme şeklinden ( veya ) oluşturulan kaynak kod sınıfının `none` devralmanın nasıl olduğunu `abstract` `sealed` açıklar.|Hiçbiri|
|Temel Bölme Şekli|Bu şeklin temel sınıfı.|(yok)|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekle bağlı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu Türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya hiçbiri). Sabitse, özellik değeri araç ipucu olarak kullanılır; değişken ise `Fixed Tooltip Text` araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkili resmi olmayan notlar.|\<none>|
|İlk Yükseklik|Bu şeklin ilk yüksekliği inç olarak. Bölme şekilleri için bu yalnızca üst bilgi bölümünün yüksekliğidir ve yeniden boyutlandırılaamaz.|1|
|İlk Genişlik|Bu şeklin inç olarak ilk genişliği.|1,5|
|Dolgu Rengini Özellik Olarak Açığa Çıkar<br /><br /> Açık Dolgu Gradyan Modu<br /><br /> Ana Hat Rengi Özelliği Olarak Açık<br /><br /> Anahat Çizgi Stilini Özellik Olarak Açığa Çıkar<br /><br /> Ana Hat Kalınlığını Özellik Olarak Açığa Çıkar<br /><br /> Metin Rengini Ortaya Çıkarır|ise, `True` kullanıcı şeklin belirtilen özelliğini ayarlayabilirsiniz. Bunu ayarlamak için şekil tanımına sağ tıklayın ve Ortaya **Çıkar'ı Ekle'ye tıklayın.**|Yanlış|
|Açıklama|Oluşturulan tasarımcıyı belgeley etmek için kullanılır.|\<none>|
|Görünen Ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Araç İpucu Metni Düzeltildi|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help Anahtar Sözcüğü|Bu şekil için F1 yardım dizinini dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))