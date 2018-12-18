---
title: 'Nasıl yapılır: XML dosyalarını düzenleme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3754bcf87d77a3a67801ef7f9df8e07dc687b052
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549135"
---
# <a name="how-to-edit-xml-files"></a>Nasıl yapılır: XML dosyalarını düzenleme

XML Düzenleyicisi'ni XML dosyaları için yeni düzenleyicisidir. Visual Studio Proje ile ilişkili bir dosya veya tek başına bir XML dosyası üzerinde kullanılabilir. XML Düzenleyicisi'ni aşağıdaki dosya uzantıları ile ilişkilidir: *.config*, *.dtd*, *.xml*, *.xsd*, *.xdr*, *.xsl*, *.xslt*, ve *.vssettings*. XML Düzenleyicisi'ni, belirli bir düzenleyici kayıtlı olan ve XML veya DTD içeriği içeren başka bir dosya türü ile de ilişkilidir.

> [!NOTE]
> XHTML belgeleri, HTML düzenleyicisi tarafından işlenir.

## <a name="to-edit-an-xml-file"></a>Bir XML dosyası düzenlemek için

1.  Düzenlemek istediğiniz dosyayı çift tıklatın.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Yeni bir XML dosyası için bir proje eklemek için

1.  Gelen **proje** menüsünde, select **Yeni Öğe Ekle**.

2.  Seçin **XML dosyası** gelen **şablonları** bölmesi.

3.  Dosya adını girin **adı** alan ve tuşuna **Ekle**.

     XML dosyası projeye eklenir ve XML Düzenleyicisi'nde açılır. Varsayılan XML bildirimi dosyayı içeren `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="to-add-an-existing-xml-file-to-a-project"></a>Varolan bir XML dosyasını bir projeye eklemek için

1.  Gelen **proje** menüsünde, select **varolan öğeyi Ekle**.

     **Varolan öğeyi Ekle** iletişim kutusu görüntülenir.

2.  Bir XML dosyasını seçip tuşuna **Ekle**.

## <a name="to-create-a-new-xml-or-xslt-file"></a>Yeni bir XML veya XSLT dosyası oluşturmak için

1.  Gelen **dosya** menüsünde, select **yeni**.

     **Yeni dosya** iletişim kutusu görüntülenir.

2.  Seçin **XML dosyası** yeni bir XML dosyası; oluşturmak veya seçmek için **XSLT dosyası** yeni bir XSLT stil sayfası oluşturmak için.

3.  Tıklatın **açık**.

## <a name="to-create-a-project-for-xml-files"></a>XML dosyaları için bir proje oluşturmak için

1.  Gelen **dosya** menüsünde, select **yeni**ve ardından **proje**.

     **Yeni proje** iletişim kutusu görüntülenir.

2.  Kod dili, select seçin **boş proje**, tıklatıp **Tamam**.

3.  XML dosyaları projeye ekleyin.

     XML Düzenleyicisi'ni bu projeye eklemek şemaları bulur ve bunları doğrulama ve IntelliSense herhangi bir XML, şema veya bu proje açıkken düzenlediğiniz XSLT dosyaları için kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)
- [XML belge özellikleri, özellik penceresi](../xml-tools/xml-document-properties-properties-window.md)
- [Nasıl yapılır: bir XML belgesinden bir XML Şeması oluşturun](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)