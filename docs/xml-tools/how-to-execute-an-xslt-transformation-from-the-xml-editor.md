---
title: "Nasıl yapılır: XML Düzenleyicisi'nden XSLT dönüştürmesi yürütme"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 892f82d64bb022c20c786a996bf9f89cf557b4c2
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548306"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Nasıl yapılır: XML Düzenleyicisi'nden XSLT dönüştürmesi yürütme

XML Düzenleyicisi'ni dönüştürme gerçekleştirmek ve çıktı görüntülemek XSLT stil sayfasını bir XML belgesi ile ilişkilendirmenizi sağlar. XSLT dönüşümü sonuç çıktısı, yeni bir belge penceresi görüntülenir.

**Çıkış** özelliği, çıktı için dosya adını belirtir. Varsa **çıkış** özelliği boşsa, bir dosya adı, geçici dizinde oluşturulur. Dosya uzantısı dayanır `xsl:output` stilinize öğesinde sayfa ve olabilir. *XML*,. *txt* veya. *htm*.

Varsa **çıkış** özelliği, bir dosya adıyla belirtir bir. *htm* veya. *HTML* XSLT çıkış uzantısıdır kullanarak önizleme uygulanan [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer. Diğer tüm dosya uzantıları tarafından seçilen varsayılan Düzenleyicisi'ni kullanarak açıldığından [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio. Örneğin, dosya uzantısı varsa. *xml*, Visual Studio XML Düzenleyicisi'ni kullanır.

## <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Bir XML belgesinden XSLT dönüştürmesi yürütmek için

1.  Bir XML belgesi XML düzenleyicisinde açın.

2.  XSLT stil sayfasını XML belgesi ile ilişkilendirin.

    -   Ekleme bir `xml-stylesheet` işleme yönergesi için XML belgesi. Örneğin, aşağıdaki satırı ekleyin `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` belge giriş için.

         -veya-

    -   XSLT stil sayfası kullanılarak eklemek **özellikleri** penceresi. Belgedeki **Özellikler penceresini**, tıklatın **Gözat** için düğmesini **stil sayfası** alanına XSLT stil sayfası seçin ve'ı tıklatın **açmak**.

3.  Tıklatın **ShowXSL çıkış** düğmesini **XML Düzenleyicisi** araç.

    > [!NOTE]
    > XML belgesi ile ilişkili bir stil sayfası ise, bir iletişim kutusu kullanmak için stil sayfası girmenizi ister.
    >
    >  XSLT dönüşümü sonuç çıktısı, yeni bir belge penceresi görüntülenir.

## <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT dönüşümü XSLT stil sayfası içinden çalıştırmak için

1.  XSLT stil sayfasını XML düzenleyicisinde açın.

2.  Bir XML belgesi belirtin **giriş** belgenin alan **özellikleri** penceresi.

    > [!NOTE]
    > XML belge dönüştürme için kullanılan giriş belgedir. XSLT dönüşümü başlatıldığında, bir belge belirtilmezse **Dosya Aç** iletişim kutusu görüntülenir ve o anda bir belge belirtebilirsiniz.

3.  Tıklatın **ShowXSLT çıkış** düğmesini **XML Düzenleyicisi** araç.

     XSLT dönüşümü sonuç çıktısı, yeni bir belge penceresi görüntülenir.

## <a name="to-provide-a-different-output-file-name"></a>Farklı çıktı dosyası adını sağlamak için

1.  Bir dosya adı belirtin **çıkış** belgenin alan **özellikleri** penceresi.

2.  Tıklatın **ShowXSLT çıkış** düğmesini **XML Düzenleyicisi** araç.

     XSLT dönüşümü sonuç çıktısı bir yeni belge penceresinde görüntülenir ve çıkış penceresinde kullanılan Düzenleyicisi'nin dosya uzantısı bağlıdır, **çıkış** belge özelliği.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)