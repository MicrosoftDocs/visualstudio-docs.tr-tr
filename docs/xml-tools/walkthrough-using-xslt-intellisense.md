---
title: 'İzlenecek Yol: XSLT IntelliSense Kullanma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86a71a70296a3b4e49f2cf7c596a7f71063c8297
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693529"
---
# <a name="walkthrough-using-xslt-intellisense"></a>İzlenecek Yol: XSLT IntelliSense Kullanma

Bu anlatımda XSLT IntelliSense otomatik tamamlama değerinin bazı özniteliklerin için nasıl kullanılacağı gösterilir.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>IntelliSense xsl adı özniteliği kullanmak için: param ile ve Call-şablon öğeleri

1.  Aşağıdaki kodda yeni XSLT dosyası ve kopya oluşturun:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2.  Ekle imleci sonra `<xsl:template name="msg23" match="msg23">` ve basın **Enter**. Aşağıdaki yazmaya başlayın `xsl:call-template` öğe:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     Şablon adları listesi görünür `name=""` özniteliği `xsl:call-template` yazarken öğesi.

3.  Ekle imleci sonra `<xsl:call-template name="localized-message">` ve basın **Enter**. Aşağıdaki yazmaya başlayın `xsl:with-param` öğe:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     Parametre adları listesi görünür `name=""` özniteliği `xsl:with-param` öğesi.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>IntelliSense xsl modu özniteliğinde kullanmak için: Uygulama Şablonları öğesi

1.  Aşağıdaki kodda yeni XSLT dosyası ve kopya oluşturun:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2.  Ekle imleci sonra `<xsl:apply-templates select="phone" />` ve basın **Enter**. Aşağıdaki yazmaya başlayın `xsl: apply-templates` öğe:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     Şablon modlarının listesi görünür `mode=""` özniteliği `xsl:apply-templates` öğesi.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Bir xsl:namespace stil öneki ve sonuç önek öznitelikleri IntelliSense kullanılacak-diğer ad öğesi

1.  Aşağıdaki kodda yeni XSLT dosyası ve kopya oluşturun:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2.  Ekle imleci sonra `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` ve basın **Enter**. Aşağıdaki yazmaya başlayın `xsl:namespace-alias` öğe:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Önekleri listesini nasıl görünen fark `stylesheet-prefix` ve `result-prefix` özniteliklerini `xsl:namespace-alias` öğesi.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi IntelliSense özellikleri](../xml-tools/xml-editor-intellisense-features.md)