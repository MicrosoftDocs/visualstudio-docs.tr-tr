---
title: 'Nasıl yapılır: XML şemalarını seçme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a04075c0625eb7b4dc899a4e183588b96eb7eadd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872245"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Nasıl yapılır: kullanılacak XML şemalarını seçin

XML Düzenleyicisi bulunan bir şema önbelleği sağlar *%InstallDir%\Xml\Schemas* dizin. Şema önbelleği, IntelliSense ve XML belgesi doğrulama için kullanılan XML şemaları iyi bilinen içerir.

**Şemaları** belge özelliği kullanmak için bir veya daha fazla XML Şeması Tanım Dili (XSD) şeması/şemaları seçmek için kullanılır. Şemalar şema önbelleğinden seçin ya da önbelleğinde bulunmayan bir şema belirtmenizi sağlar.

Gizli çözüm kullanıcı seçenekleri dosyası'nda belirttiğiniz şemaları kaydedilir (. *suo*), yanı sıra diğer tüm XML belge özellikleri. Sonuç olarak, bu değerleri çözüm bir sonraki açışınızda yeniden girmeniz gerekmez.

> [!NOTE]
> Düzenleyicide bir satır içi şema veya şema tarafından başvurulan kullanarak doğrulayabilirsiniz `xsd:schemaLocation` özniteliği. Daha fazla bilgi için [XML belgesi doğrulama](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Bir XML Şeması, şema önbelleğinden seçmek için

1. Bir dosyasını XML düzenleyicisinde açın.

2. Düğmesine tıklayarak belge Özellikler penceresinde **şemaları** alan.

    **XML şemaları** iletişim kutusu görüntülenir. İletişim kutusu ile tüm şemalar listeler bir. *xsd* şema önbelleğinin uzantısında (başvurulan şemaları dahil olmak üzere *catalog.xml* dosyası) ve ayrıca Visual Studio'da açık geçerli çözüm içinde başvurulan tüm şema bir `xsd:schemaLocation` öznitelik veya başvurulan **şemaları** özelliği.

3. Aşağıdakilerden birini yaparak doğrulama için kullanılacak şemaları seçin:

   - Listelenen bir şema seçin **XML şemaları** iletişim kutusunda, tıklayın **kullanım** sütun tıklayın ve ardından **Bu şemayı kullan**.

     veya

   - Birden çok şema listelenen seçin **XML şemaları** iletişim, sütuna sağ tıklayıp **Bu şemayı kullan**.

4. **Tamam**'ı tıklatın.

    Seçili şemaları listesini geri kopyalanır **şemaları** belge özelliği.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Bir XML Şeması, şema önbelleğine eklemek için

1.  Düğmesine tıklayarak belge Özellikler penceresinde **şemaları** alan.

2.  **Ekle**'yi tıklatın.

     Bu açılır **açık XSD şeması** iletişim.

3.  Gözat ve şemaları şema önbelleğine eklemek için seçin.

4.  Tıklayın **açık**.

     Eklenir şemaları önbelleğe alma ve ise **kullanım** sütun değeri ayarı **Bu şemayı kullan**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Bir XML Şeması, şema önbelleğinden silmek için

1.  Düğmesine tıklayarak belge Özellikler penceresinde **şemaları** alan.

2.  Kaldırın ve ardından şemayı seçin **Kaldır**.

     Şema bellek içi şema önbelleğinden kaldırılıyor ancak dosya sisteminden kaldırılmaz.

    > [!NOTE]
    > Yine de şemanın başvuru varsa bir `schemaLocation` özniteliği veya eşleşen bir `targetNamespace` ardından **Kaldır** otomatik ilişkisi nedeniyle, bu durumda işe yaramaz. Bu durumda, şema olarak işaretlemek önerilir **seçili şemaları kullanma** içinde **kullanın** sütun.

## <a name="see-also"></a>Ayrıca bkz.

- [Şema önbelleği](../xml-tools/schema-cache.md)
- [XML şemaları iletişim kutusu](../xml-tools/xml-schemas-dialog-box.md)
- [XML Düzenleyicisi](../xml-tools/xml-editor.md)