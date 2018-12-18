---
title: XML Şemaları İletişim Kutusu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5357f762d2a7027db92ad1916acb279abdf23157
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693646"
---
# <a name="xml-schemas-dialog-box"></a>XML şemaları iletişim kutusu

**XML şemaları** iletişim kutusu, bir XML belgesi ile ilişkilendirmek için hangi XML Şeması Tanım Dili (XSD) şeması/şemaları seçmek için kullanılır. Şema önbelleğinden bir şema seçin veya önbellekte bulunmayan bir şema belirtin. Seçili şeması/şemaları şema kümesinin bir parçası olarak kabul edilir. Şema kümesini IntelliSense ve ayrıca XML belge doğrulama için kullanılır.

Erişebileceğiniz **XML şemaları** ya da tıklatarak iletişim kutusunu **şemaları** düğmesini belge özellikleri penceresinde veya seçerek **şemaları** gelen**XML** menüsü.

## <a name="uielement-list"></a>UIElement Listesi
 **Kullanın**

 XML Şeması nasıl kullanılacaksa seçin.

-   **Otomatik**. Bu şemayı geçerli belge tarafından kullanımda değildir ancak otomatik ilişkilendirme için kullanılabilir. XML belgesi eşleşen bir ad alanı bildirirse `targetNamespace` bu şemanın şema otomatik olarak ilişkilendirilir ve şema kümesine dahil.

-   **Bu şemayı kullanan**. Bu şemayı geçerli belgesi tarafından kullanılıyor. Ya da kullanıcının açıkça olduğundan bu şemayı bu sütuna tıklayarak kullanılmasını istediğiniz ya da şemayı eşleşmesini temel alan otomatik olarak ilişkili `targetNamespace`.

-   **Seçili şemaları kullanmayın**. Eşleşen bir şemaya sahip olsa bile bu şema geçerli belge tarafından kullanılmaz `targetNamespace`. Bu ayar şema önbelleğinin veya çözüm aynı şemada birden fazla sürümü olduğunda çakışmalarını çözmek için yararlı olabilir.

**Hedef Namespace**

XML şeması ile ilişkili hedef ad alanı görüntüler.

**Dosya adı**

XML Şeması dosya adını görüntüler.

**Ekle**

Açılır **açık XSD şema** form veya iletişim şema kümesine eklemek için ek şemaları seçmenize olanak sağlar. Şemaya bir şema eklediğinizde ayarlayın, **kullanım** sütun değeri ayarlanmış **Bu şemayı kullanan**.

**Kaldır**

Şu anda seçili şeması şema kümesinden kaldırır. Bellek içi şema önbelleğinden ancak dosya sisteminden Bu şemayı kaldırır.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi bileşenleri](../xml-tools/xml-editor-components.md)
- [Nasıl yapılır: kullanılacak XML şemaları seçin](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Şema önbelleği](../xml-tools/schema-cache.md)