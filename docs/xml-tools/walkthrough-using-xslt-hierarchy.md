---
title: 'İzlenecek Yol: XSLT Hiyerarşisi Kullanma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 20223a18fa422facc7d7a0a74336402d6d391b0a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693451"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>İzlenecek yol: Kullanmak XSLT hiyerarşisi

XSLT hiyerarşi aracı birçok XML geliştirme görevlerini basitleştirir. XSLT stil sayfasını sık kullandığı `includes` ve `imports` yönergeler. Asıl stil sayfası içinden derleme başlatır, ancak bir XSLT stil sayfası derleme sonucu olarak hata gördüğünüzde, hata asıl stil sayfası'den başka bir kaynaktan gelebilir. Hata düzelttikten veya stil sayfası düzenleme eklenen veya içeri aktarılan stil sayfaları erişim gerektirebilir. Hata ayıklayıcı stil sayfası doğruluk dahil ve içeri aktarılan stil sayfasını açabilir ve bir veya daha fazla dahil edilen stil sayfaları, belirli bir noktada bir kesme noktası eklemek isteyebilirsiniz.

Burada XSLT hiyerarşi aracı yararlı olabilir başka bir senaryo kesme noktaları yerleşik şablon kurallarında koyuyor. Şablon kuralları için özel şablonları stil sayfası her bir modu için oluşturulan ve tarafından çağrılır `xsl:apply-templates` zaman başka bir şablonla eşleşip düğüm. Yerleşik şablonlar kurallarında hata ayıklama uygulamak için XSLT hata ayıklayıcı kurallarla dosyanın geçici klasörde oluşturur ve bunları birlikte asıl stil sayfası derler. Bazı koda atlama olmadan `xsl:apply-template`, asıl stil sayfanızda dahil stil sayfaları bulmak veya bulmak ve yerleşik şablon kurallarıyla stil sayfasını açmak zor olabilir.

Bu konudaki örnek bir başvurulan stil sayfanızda hata ayıklama gösterir.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Başvurulan stil sayfasında hata ayıklamak için

1. Bir XML belgesi Visual Studio'da açın. Bu örnekte aşağıdaki belge kullanır:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. Aşağıdakileri ekleyin *xslincludefile.xsl*:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3.  Aşağıdakileri ekleyin *xslinclude.xsl* dosyası:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4.  Yönerge kesme noktası ekleme `<xsl:include href="xslincludefile.xsl" />`.

5.  Hata ayıklama başlatılamıyor.

6.  Hata ayıklayıcı yönerge durduğunda `<xsl:include href="xslincludefile.xsl" />`, basın **Step Into** düğmesi. Hata ayıklama başvurulan stil sayfanızda devam. Hiyerarşi görünür olduğundan ve doğru yolu Tasarımcı görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: XSLT Profil Oluşturucu](../xml-tools/walkthrough-xslt-profiler.md)