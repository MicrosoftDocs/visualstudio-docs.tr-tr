---
title: XML belge doğrulama XML Düzenleyicisi'nde
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04b2e821abbbc7a24ce5b77b7374de617852cf2a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693844"
---
# <a name="xml-document-validation"></a>XML belge doğrulama

XML Düzenleyicisi'ni XML 1.0 sözdizimi denetler ve yazarken veri doğrulama da gerçekleştirir. Düzenleyici bir belge türü tanımı (DTD) ya da bir şema kullanarak doğrulayabilirsiniz. Kırmızı dalgalı alt çizgiler, doğru biçimlendirilmiş XML 1.0 hatalarını vurgulayın. Mavi dalgalı alt çizgiler DTD ya da şema doğrulamasını dayalı semantik hatalar gösterir. Her hata hata listesinde ilişkili bir giriş var. Dalgalı alt çizginin fare duraklatarak, hata iletisi de görüntüleyebilirsiniz.

 Doğrulama kullanılan şemalar eşleştirerek bulunduğunda `targetNamespace` öğenin xmlns bildirimiyle derlenmiş şemanın. Derlenen şemalar, öncelik sırasına göre listelenen aşağıdaki konumlardan birini yüklenir:

-   Belirtilen dosya adından **şemaları** belgenin alan **özellikleri** penceresi.

-   Satır içi şema veya DTD.

-   Bir dış DTD veya bir `xsd:schemaLocation` ve `xsd:noNamespaceSchemaLocation` özniteliği

-   Bir "x-schema" XDR Şema ad alanı URI'si.

Şema boş hedef ad alanı olduğunda şemaları ayrıca aşağıdaki ek konumlarda bulunabilir:

-   Şema içeren başka bir düzenleyici penceresi.

-   Geçerli çözümde şema.

-   Şema önbellek dizini şemadan.

## <a name="xslt-files"></a>XSLT dosyaları
 XSLT dosyasının düzenlenmesi sırasında *xslt.xsd* şema önbelleğinde bulunan dosya doğrulama için kullanılır. Doğrulama hataları Mavi dalgalı alt çizgiler gösterilir. XSLT derleyici hatalarını kırmızı dalgalı alt çizgiler gösterilir.

## <a name="xml-schema-xsd-files"></a>XML şema (XSD) dosyaları
 Bir XML Şeması dosyasının düzenlenmesi sırasında *xsdschema.xsd* şema önbelleğinde bulunan dosya doğrulama için kullanılır. Doğrulama hataları Mavi dalgalı alt çizgiler gösterilir. Derleme hataları kırmızı dalgalı alt çizgi ile de gösterilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)