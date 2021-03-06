---
title: XML şema Tasarımcısı XML Düzenleyicisi ile tümleştirme
description: XML şema Tasarımcısı ve XML Düzenleyicisi arasındaki tümleştirmeyi ve bir üzerinde yapılan değişikliklerin diğerine nasıl yansıtıldığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fe1bfcd422dbfc5f010ae7819e2fccbeafb8227
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934630"
---
# <a name="integration-with-xml-editor"></a>XML düzenleyicisi ile tümleştirme

XML şema Tasarımcısı XML Düzenleyicisi ile tümleşiktir. XML düzenleyicisinde bir XSD dosyasını değiştirirseniz, değişiklik [XML şema Gezgini](../xml-tools/xml-schema-explorer.md)' nde yansıtılır. [Grafik görünümü](../xml-tools/graph-view.md) veya [içerik modeli görünümü](../xml-tools/content-model-view.md) açık ise, değişiklik de yansıtılır. XML şema Tasarımcısı ve XML Düzenleyicisi arasında aşağıdaki yollarla gezinebilirsiniz:

- XML düzenleyicisinde, bir düğüme sağ tıklayın ve **XML şema Gezgini 'Nde göster**' i seçin.

- Graph görünümünde ve **XML şema Gezgini**' nde bir düğüme çift tıklayın veya bir düğüme sağ tıklayıp **kodu görüntüle**' yi seçin. Içerik modeli görünümünde, bir düğüme sağ tıklayın ve **kodu görüntüle**' yi seçin.

Aşağıdaki ekran görüntüsünde **XML şema Gezgininde** AÇıLAN bir XML şeması gösterilmektedir. **XML şeması Gezgini** , şema kümesini bir ağaç görünümünde görüntüler. XML Düzenleyicisi, şu anda **XML şema Gezgini**'nde etkin olan düğümün metin görünümünü görüntüler.

![XML Düzenleyicisi bölmesindeki bir XML düğümünü ve XML şeması Gezgini bölmesinde şema kümesinin ağaç görünümünü gösteren bir Visual Studio projesinin ekran görüntüsü.](../xml-tools/media/xsddesignerwithxmleditor.gif)

Bazen kodu XML düzenleyicisinde ve grafik tasarımcısında yan yana görmek faydalı olur. Her iki dosyayı aynı anda görüntülemek için, XML düzenleyicisinde herhangi bir yere sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin. Visual Studio Windows menüsünde **Yeni yatay (veya dikey) sekme grubu**' nu seçin.

![Görünüm Tasarımcısı bölmesini, XML Düzenleyicisi bölmesini ve XML şeması Gezgin bölmesini gösteren bir Visual Studio projesinin ekran görüntüsü.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Gezgini](../xml-tools/xml-schema-explorer.md)
