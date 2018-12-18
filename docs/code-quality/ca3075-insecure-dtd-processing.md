---
title: 'CA3075: Güvensiz DTD İşleme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b83fbf98143511bac19bef1fb2b528c71517a55f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823015"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Güvensiz DTD İşleme

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Güvenli olmayan kullanırsanız <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örnekleri veya giriş ve saldırganlar için hassas bilgileri ifşa güvenilmeyen Dış varlık kaynakları, ayrıştırıcının kabul başvurusu.

## <a name="rule-description"></a>Kural açıklaması

A *belge türü tanımı (DTD'nin)* bir XML ayrıştırıcısı bir belgenin geçerlilik belirlemek iki yöntemden biri tarafından tanımlanan olan [World Wide Web Consortium (W3C) Genişletilebilir Biçimlendirme Dili (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Bu kural, özellikler ve örnekler burada güvenilir olmayan verileri kabul edilir olası geliştiricilerinden uyarmak için çalışmaktadır [bilgilerin açığa çıkması](/dotnet/framework/wcf/feature-details/information-disclosure) açabilir tehditler [hizmet reddi (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) saldırıları. Bu kuralın ne zaman tetikleyen:

- XmlReaderSettings üzerinde etkin <xref:System.Xml.XmlReader> kullanarak dış XML varlıkları çözümler örneği <xref:System.Xml.XmlUrlResolver>.

- <xref:System.Xml.XmlNode.InnerXml%2A> XML özelliğinde ayarlanır.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> özellik ayrıştırma için ayarlanır.

- Giriş kullanılarak işlenir güvenilmeyen <xref:System.Xml.XmlResolver> yerine <xref:System.Xml.XmlSecureResolver> .

- XmlReader.<xref:System.Xml.XmlReader.Create%2A> yöntemi çağrıldığında bir güvenli <xref:System.Xml.XmlReaderSettings> örneği veya hiç bir örneği yok.

- <xref:System.Xml.XmlReader> Güvenli varsayılan ayarları veya değerleri ile oluşturulur.

Her durumda, sonuç aynıdır: XML işleneceği makinesinden dosya sistemi veya ağ paylaşımları içeriğinden DoS vektörü olarak kullanılabilir saldırgan için kullanıma sunulacak.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

- Catch ve doğru yolu bilgi açıklamalardan kaçınmak için tüm XmlTextReader özel durumları işler.

- Kullanım <xref:System.Xml.XmlSecureResolver> XmlTextReader erişebildiği kaynakları sınırlandırmak için.

- İzin verme <xref:System.Xml.XmlReader> ayarlayarak herhangi bir dış kaynağa açmak için <xref:System.Xml.XmlResolver> özelliğini **null**.

- Emin <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> özelliği <xref:System.Data.DataViewManager> güvenilir bir kaynaktan atanır.

**.NET 3.5 ve önceki sürümler**

- Güvenilmeyen kaynaklarıyla ayarlayarak uğraşıyorsanız DTD işlemeyi devre dışı <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> özelliğini **true** .

- Tam güven devralma talebi XmlTextReader sınıfı vardır.

**.NET 4 ve üzeri**

- Güvenilmeyen kaynaklarıyla ayarlayarak ilgilenme, XmlReaderSettings etkinleştirmemeye <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> özelliğini **yasakla** veya **Yoksay**.

- Load() yöntem tüm sınıfının InnerXml durumlarda XmlReader örneği alır emin olun.

> [!NOTE]
> Bu kural, hatalı pozitif sonuçları bazı geçerli XmlSecureResolver örneklerinde bildirebilir.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Giriş güvenilir bir kaynaktan olduğu biliniyorsa emin olmadığınız sürece, bir kuraldan bu uyarıyı bastırmayın.

## <a name="pseudo-code-examples"></a>Sözde kod örnekleri

### <a name="violation"></a>İhlali

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>İhlali

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>İhlalleri

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>İhlali

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>İhlali

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>İhlali

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>İhlalleri

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```