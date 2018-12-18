---
title: 'CA3077: API tasarımı, XML belgesi ve XML metin okuyucusunda güvensiz işleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0e75f86b958d0f2602a3f32830e8c6f18c185584
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925096"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: API Tasarımı, XML Belgesi ve XML Metin Okuyucusunda Güvensiz İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir API tasarlamaya XMLDocument ve XMLTextReader türetilmiş olduğunda, dikkatli olmanızı <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Kullandığınızda güvensiz XmlReaderSettings örnekleri başvuran veya dış varlık kaynakları çözümleme XML'de güvenli olmayan değerleri ayarlama bilgileri açığa çıkmasına neden olabilir.

## <a name="rule-description"></a>Kural Tanımı
 A [belge türü tanımı (DTD'nin)](https://msdn.microsoft.com/library/aa468547.aspx) bir XML ayrıştırıcısı bir belgenin geçerlilik belirlemek iki yöntemden biri tarafından tanımlanan olan [World Wide Web Consortium (W3C) Genişletilebilir Biçimlendirme Dili (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Bu kural, özellikler ve örnekler burada güvenilir olmayan verileri kabul edilir olası geliştiricilerinden uyarmak için çalışmaktadır [bilgilerin açığa çıkması](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) açabilir tehditler [hizmet reddi (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) saldırıları. Bu kuralın ne zaman tetikleyen:

-   <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XmlTextReader> sınıfları DTD işleme için varsayılan çözümleyici değerleri kullanın.

-   XmlDocument için tanımlı hiçbir oluşturucu veya XmlTextReader türetilmiş sınıflar güvenli bir değerle için kullanılan <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?

-   Catch ve doğru yolu bilgi açıklamalardan kaçınmak için tüm XmlTextReader özel durumları işler.

-   Kullanım <xref:System.Xml.XmlSecureResolver>XmlTextReader erişebileceği kaynakları sınırlandırmak için XmlResolver yerine.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
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



