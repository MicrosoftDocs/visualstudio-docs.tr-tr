---
title: XML Araçları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f87c06e2bfc3885c0f52230e927933ff3cb0d87c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055004"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio'daki XML araçları

*Genişletilebilir Biçimlendirme Dili (XML)* veri tanımlamak için bir biçim sağlayan bir biçimlendirme dilidir. Bu, birden çok platformda daha kesin bildirimleri içerik ve daha anlamlı arama sonuçlarının kolaylaştırır. Ayrıca, XML veri sunudan ayrımı sağlar. Örneğin, HTML etiketleri tarayıcıya kalın veya italik verileri görüntülemek için kullandığınız; XML etiketleri yalnızca şehir adı, sıcaklık ve barometric baskısı gibi verileri tanımlamak için kullanın. XML biçiminde, bir tarayıcıda verileri sunmak için Genişletilebilir Stil Sayfası Dili (XSL) gibi stil sayfaları ve geçişli stil sayfaları (CSS) kullanırsınız. XML verileri, sunu ve işlem ayırır. Bu, görüntülemek ve farklı bir stil sayfaları ve uygulamaları uygulayarak istediğiniz verileri işlemek sağlar.

XML Web üzerinden teslimat için optimize edilmiştir SGML bir alt kümesidir. Bu, World Wide Web Consortium (W3C) tarafından tanımlanır. Bu Standardizasyon yapılandırılmış verileri Tekdüzen ve uygulamaları veya satıcılar bağımsız olduğunu garanti eder.

Visual Studio ve .NET Framework özelliklerinin çoğu özünde XML'dir. Aşağıdaki makale listesi için XML ilgili olan ve Visual Studio ve .NET Framework içinde sunulan özellikler ve Araçlar adları.

Daha fazla bilgi için <xref:System.Xml?displayProperty=fullName> belgeleri.

## <a name="reference"></a>Başvuru

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) sunan [XML Düzenleyicisi](http://go.microsoft.com/fwlink/?LinkId=228249) ayrıştırma ağacı aracılığıyla [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) XML belgeleri için.

[XML standartları başvurusu](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) XML, belge türü tanımı (DTD'nin), XML Şeması Tanım Dili (XSD) ve XSLT de dahil olmak üzere, XML teknolojileri hakkında bilgi sağlar.

<xref:System.Xml?displayProperty=fullName> Sınıfları ve oluşturan diğer öğeleri açıklayan <xref:System.Xml> ad alanı ve her bir öğede daha ayrıntılı bilgi için bağlantılar sağlar.

<xref:System.Xml.Serialization?displayProperty=fullName> Sınıfları ve oluşturan diğer öğeleri açıklayan <xref:System.Xml.Serialization> ad alanı ve her öğeyle ilgili daha ayrıntılı bilgi için bağlantılar sağlar.

## <a name="related-sections"></a>İlgili bölümler

[XML belge nesne modeli (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom) Describes nasıl <xref:System.Xml.XmlDocument> ve onun ilişkili sınıfları W3C belge nesne modeli (çekirdek) Düzey 1 ve 2. düzey ad alanı desteği belirtimleri ile uyumlu.

[XmlReader ve XmlWriter ile XML verileri işleme](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc189001\(v\=vs.95\))

[XSLT dönüşümleri](/dotnet/standard/data/xml/xslt-transformations) Describes nasıl <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT 1.0 öneri uygular.

[XPath veri modelini kullanarak XML verilerini işleme](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model) Describes nasıl <xref:System.Xml.XPath.XPathNavigator> sınıfı içinde depolanan XML verileri işleyebilir bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne. <xref:System.Xml.XPath.XPathNavigator> Sınıfı XQuery 1.0 ve XPath 2.0 veri modeline dayanır ve gidin ve XML verileri düzenlemek için kullanılabilir.

[XML şema nesne modeli (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som) oluşturmak ve XML şemaları sağlayarak işlemek için kullanılan sınıfları açıklar bir <xref:System.Xml.Schema.XmlSchema> yüklemek ve bir şema düzenlemek için sınıf.