---
title: 'İzlenecek yol: XSLT IntelliSense kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ad8345f7a7dfd4d875dc33989b85ba74421ad04a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266805"
---
# <a name="walkthrough-using-xslt-intellisense"></a>İzlenecek Yol: XSLT IntelliSense Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu yönerge, XSLT IntelliSense otomatik tamamlama için bazı özniteliklerin değeri kullanma işlemini gösterir.  
  
### <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Xsl ad özniteliğinde IntelliSense kullanılacak: param ile ve Call-şablon öğeleri  
  
1.  Aşağıdaki kodda, yeni XSLT dosyası ve kopya oluşturun:  
  
    ```  
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
  
2.  İmlecinizi sonra Ekle `<xsl:template name="msg23" match="msg23">` ve ENTER tuşuna basın. Aşağıdaki yazmaya başlayın `xsl:call-template` öğesi:  
  
    ```  
    <xsl:call-template name="localized-message">  
    </xsl:call-template>  
    ```  
  
     Şablon adları listesi görünür `name=""` özniteliği `xsl:call-template` yazarken öğesi.  
  
3.  İmlecinizi sonra Ekle `<xsl:call-template name="localized-message">` ve ENTER tuşuna basın. Aşağıdaki yazmaya başlayın `xsl:with-param` öğesi:  
  
    ```  
    <xsl:with-param name="msgcode">msg23</xsl:with-param>  
    ```  
  
     Parametre adları listesi görünür `name=""` özniteliği `xsl:with-param` öğesi.  
  
### <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Xsl modu özniteliğinde IntelliSense kullanmak için: Uygulama Şablonları öğesi  
  
1.  Aşağıdaki kodda, yeni XSLT dosyası ve kopya oluşturun:  
  
    ```  
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
  
2.  İmlecinizi sonra Ekle `<xsl:apply-templates select="phone" />` ve ENTER tuşuna basın. Aşağıdaki yazmaya başlayın `xsl: apply-templates` öğesi:  
  
    ```  
    <xsl:apply-templates select="phone"  mode="accountNumber">  
    ```  
  
     Şablon modlarının listesi görünür `mode=""` özniteliği `xsl:apply-templates` öğesi.  
  
### <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>IntelliSense bir xsl: namespace stil sayfası öneki ve sonuç önek öznitelikleri kullanılacak-diğer ad öğesi  
  
1.  Aşağıdaki kodda, yeni XSLT dosyası ve kopya oluşturun:  
  
    ```  
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
  
2.  İmlecinizi sonra Ekle `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` ve ENTER tuşuna basın. Aşağıdaki yazmaya başlayın `xsl:namespace-alias` öğesi:  
  
    ```  
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>  
    ```  
  
     Ön ek listesini nasıl göründüğü fark `stylesheet-prefix` ve `result-prefix` özniteliklerini `xsl:namespace-alias` öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Düzenleyicisi IntelliSense Özellikleri](../xml-tools/xml-editor-intellisense-features.md)



