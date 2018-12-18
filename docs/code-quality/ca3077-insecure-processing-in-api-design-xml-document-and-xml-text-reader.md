---
title: 'CA3077: API Tasarımı, XML Belgesi ve XML Metin Okuyucusunda Güvensiz İşleme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c8d90883f2aac5389ec0787fee08749da363e747
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821961"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: API Tasarımı, XML Belgesi ve XML Metin Okuyucusunda Güvensiz İşleme

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir API tasarlamaya XMLDocument ve XMLTextReader türetilmiş olduğunda, dikkatli olmanızı <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Kullandığınızda güvensiz XmlReaderSettings örnekleri başvuran veya dış varlık kaynakları çözümleme XML'de güvenli olmayan değerleri ayarlama bilgileri açığa çıkmasına neden olabilir.

## <a name="rule-description"></a>Kural açıklaması
 A *belge türü tanımı (DTD'nin)* bir XML ayrıştırıcısı bir belgenin geçerlilik belirlemek iki yöntemden biri tarafından tanımlanan olan [World Wide Web Consortium (W3C) Genişletilebilir Biçimlendirme Dili (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Bu kural, özellikler ve örnekler burada güvenilir olmayan verileri kabul edilir olası geliştiricilerinden uyarmak için çalışmaktadır [bilgilerin açığa çıkması](/dotnet/framework/wcf/feature-details/information-disclosure) açabilir tehditler [hizmet reddi (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) saldırıları. Bu kuralın ne zaman tetikleyen:

- <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XmlTextReader> sınıfları DTD işleme için varsayılan çözümleyici değerleri kullanın.

- XmlDocument için tanımlı hiçbir oluşturucu veya XmlTextReader türetilmiş sınıflar güvenli bir değerle için kullanılan <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

- Catch ve doğru yolu bilgi açıklamalardan kaçınmak için tüm XmlTextReader özel durumları işler.

- Kullanım <xref:System.Xml.XmlSecureResolver>XmlTextReader erişebileceği kaynakları sınırlandırmak için XmlResolver yerine.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Giriş güvenilir bir kaynaktan olduğu biliniyorsa emin olmadığınız sürece, bir kuraldan bu uyarıyı bastırmayın.

## <a name="pseudo-code-examples"></a>Sözde kod örnekleri

### <a name="violation"></a>İhlali

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```