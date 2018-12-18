---
title: Dekoratörlerin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0265146f5b8d03c7b3ac5f2b08b0cb384c3e45a5
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967109"
---
# <a name="properties-of-decorators"></a>Dekoratörlerin Özellikleri
Dekoratörler simgeler, metin veya şekil veya diyagram üzerinde bağlayıcı görünebilir Genişlet/Daralt ayraç ' dir. Aşağıdaki tablolar, dekoratör üç tür özelliklerini gösterir. Bazı özellikler, yalnızca şekli dekoratörler veya yalnızca bağlayıcı dekoratörler görünür.

 Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikler kullanma hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Dekoratör Genişlet/Daralt

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|displayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Daralt Dekoratör genişletin|
|Ad|Dekoratörün adı.|ExpandCollapseDecorator|
|Notlar|Bu dekoratör ile ilişkili resmi olmayan notlar.|\<yok >|
|HorizontalOffset|Dekoratörün varsayılan konumuna inç cinsinden yatay uzaklık. (Şekiller üzerinde yalnızca.)|0|
|VerticalOffset|İnç, dekoratörün varsayılan konumuna göre dikey uzaklık. (Şekiller üzerinde yalnızca.)|0|
|OffsetFromLine|Dekoratörün satırından inç, varsayılan konumuna göre uzaklığı. (Bağlayıcı üzerinde yalnızca.)|0|
|OffsetFromShape|Dekoratörün şekilden inç cinsinden, varsayılan konumuna göre uzaklığı. (Bağlayıcı üzerinde yalnızca.)|0|
|Konum|Dekoratörün varsayılan konumuna.|SourceTop|

## <a name="icon-decorator"></a>Dekoratör simgesi

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|DefaultIcon|Görüntülenecek simge veya resim dosyasının yolu.|\<yok >|
|displayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Dekoratör simgesi|
|Ad|Dekoratörün adı.|Şeklindeki Icondecorator|
|Notlar|Dekoratör ile ilişkili resmi olmayan notlar.|\<yok >|
|HorizontalOffset|Dekoratörün varsayılan konumuna inç cinsinden yatay uzaklık. (Şekiller üzerinde yalnızca.)|0|
|VerticalOffset|İnç, dekoratörün varsayılan konumuna göre dikey uzaklık. (Şekiller üzerinde yalnızca.)|0|
|OffsetFromLine|Dekoratörün satırından inç, varsayılan konumuna göre uzaklığı. (Bağlayıcı üzerinde yalnızca.)|0|
|OffsetFromShape|Dekoratörün şekilden inç cinsinden, varsayılan konumuna göre uzaklığı. (Bağlayıcı üzerinde yalnızca.)|0|
|Konum|Dekoratörün varsayılan konumuna.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|DefaultText|Görüntülenecek varsayılan metin.|Etiketle|
|displayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Etiketle|
|FontSize|Dekoratörde görüntülenen metnin yazı tipi boyutu.|8|
|fontStyle|Dekoratörde görüntülenen metnin yazı tipi stili.|Normal|
|Ad|Dekoratörün adı.|Etiketle|
|Notlar|Dekoratör ile ilişkili resmi olmayan notlar.|\<yok >|
|HorizontalOffset|Dekoratörün varsayılan konumuna inç cinsinden yatay uzaklık. (Şekiller üzerinde yalnızca.)|0|
|VerticalOffset|İnç, dekoratörün varsayılan konumuna göre dikey uzaklık. (Şekiller üzerinde yalnızca.)|0|
|OffsetFromLine|Dekoratörün satırından inç, varsayılan konumuna göre uzaklığı. (Bağlayıcı üzerinde yalnızca.)|0|
|OffsetFromShape|Dekoratörün şekilden inç cinsinden, varsayılan konumuna göre uzaklığı. (Bağlayıcı üzerinde yalnızca.)|0|
|Konum|Dekoratörün varsayılan konumuna.|TargetBottom|

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)