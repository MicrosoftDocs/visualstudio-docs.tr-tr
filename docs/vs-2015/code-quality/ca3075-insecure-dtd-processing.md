---
title: 'CA3075: Güvensiz DTD işleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8284f065a829ac7ecc29330fb8a9dad74e92690e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850191"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Güvensiz DTD İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Güvenli olmayan kullanırsanız <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örnekleri veya giriş ve saldırganlar için hassas bilgileri ifşa güvenilmeyen Dış varlık kaynakları, ayrıştırıcının kabul başvurusu.

## <a name="rule-description"></a>Kural Tanımı
 A [belge türü tanımı (DTD'nin)](https://msdn.microsoft.com/library/aa468547.aspx) bir XML ayrıştırıcısı bir belgenin geçerlilik belirlemek iki yöntemden biri tarafından tanımlanan olan [World Wide Web Consortium (W3C) Genişletilebilir Biçimlendirme Dili (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Bu kural, özellikler ve örnekler burada güvenilir olmayan verileri kabul edilir olası geliştiricilerinden uyarmak için çalışmaktadır [bilgilerin açığa çıkması](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) açabilir tehditler [hizmet reddi (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) saldırıları. Bu kuralın ne zaman tetikleyen:

- XmlReaderSettings üzerinde etkin <xref:System.Xml.XmlReader> kullanarak dış XML varlıkları çözümler örneği <xref:System.Xml.XmlUrlResolver>.

- <xref:System.Xml.XmlNode.InnerXml%2A> XML özelliğinde ayarlanır.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> özellik ayrıştırma için ayarlanır.

- Giriş kullanılarak işlenir güvenilmeyen <xref:System.Xml.XmlResolver> yerine <xref:System.Xml.XmlSecureResolver> .

- XmlReader.<xref:System.Xml.XmlReader.Create%2A> yöntemi çağrıldığında bir güvenli <xref:System.Xml.XmlReaderSettings> örneği veya hiç bir örneği yok.

- <xref:System.Xml.XmlReader> Güvenli varsayılan ayarları veya değerleri ile oluşturulur.

  Her durumda, sonuç aynıdır: XML işleneceği makinesinden dosya sistemi veya ağ paylaşımları içeriğinden DoS vektörü olarak kullanılabilir saldırgan için kullanıma sunulacak.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?

- Catch ve doğru yolu bilgi açıklamalardan kaçınmak için tüm XmlTextReader özel durumları işler.

- Kullanım <xref:System.Xml.XmlSecureResolver> XmlTextReader erişebildiği kaynakları sınırlandırmak için.

- İzin verme <xref:System.Xml.XmlReader> ayarlayarak herhangi bir dış kaynağa açmak için <xref:System.Xml.XmlResolver> özelliğini **null**.

- Emin <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> özelliği <xref:System.Data.DataViewManager> güvenilir bir kaynaktan atanır.

  .NET 3.5 ve önceki sürümler

- Güvenilmeyen kaynaklarıyla ayarlayarak uğraşıyorsanız DTD işlemeyi devre dışı <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> özelliğini **true** .

- Tam güven devralma talebi XmlTextReader sınıfı vardır. Bkz: [devralma taleplerini](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) daha fazla bilgi için.

  .NET 4 ve üzeri

- Güvenilmeyen kaynaklarıyla XmlReaderSettings ayarlayarak ilgilenme, XmlReaderSettings etkinleştirmemeye [Engelle veya yoksay](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)

- Load() yöntem tüm sınıfının InnerXml durumlarda XmlReader örneği alır emin olun.

> [!NOTE]
>  Bu kural, hatalı pozitif sonuçları bazı geçerli XmlSecureResolver örneklerinde bildirebilir. Mid 2016 tarafından bu sorunu çözmeye çalışıyoruz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
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



