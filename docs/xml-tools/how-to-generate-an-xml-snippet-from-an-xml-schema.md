---
title: 'Nasıl yapılır: XML şemasından bir XML parçacığını oluştur'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ac437bbbe876d81acc917f011a3051c9c264b6a
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34477684"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Nasıl yapılır: XML şemasından bir XML parçacığını oluştur

XML Düzenleyicisi'ni bir XML Şeması Tanım Dili (XSD) şemadan XML parçacıkları oluşturabilme özelliği vardır. Örneğin, öğe adı yanındaki konumlandırılmış sırada bir XML dosyasına yazma gibi basabilirsiniz **sekmesini** öğesi bu öğe için şema bilgileri üretilen XML verileri ile doldurmak için.

Bu özellik, yalnızca öğeleri üzerinde kullanılabilir. Aşağıdaki kuralları da geçerlidir:

-   Öğe bir ilişkili şema türü olması gerekir; diğer bir deyişle, öğesi ilişkili bazı şemaya göre geçerli olması gerekir. Şema türü soyut olamaz ve türü gerekli öznitelikler içermelidir ve/veya alt öğeleri gerekli.

-   Geçerli öğe Düzenleyicisi'nde özniteliklere boş olmalıdır. Örneğin, tüm geçerli verilmiştir

    -   `<Account`

    -   `<Account>`

    -   `<Account></Account>`

-   İmleç hemen öğe adının sağında yer alması gerekir.

Oluşturulan kod parçacığında, tüm gerekli öznitelikler ve öğeler içerir. Varsa `minOccurs` biri, gerekli en az bu öğenin örnek sayısı en çok 100 örnekleri parçacığı dahil sayısından daha büyük. Herhangi bir kod parçacığını sabit değerleri şema sonucunda bulunan değerleri sabit. `xsd:any` ve `xsd:anyAttribute` öğeleri göz ardı edilir ve hiçbir ek kod parçacığında yapılardan sonucu.

Varsayılan değerler oluşturulan ve düzenlenebilir değerleri olarak kaydedilir. Şema varsayılan bir değer belirtir, bu varsayılan değer kullanılır. Ancak, şema varsayılan değer boş bir dize ise, düzenleyici varsayılan değerleri aşağıdaki şekilde oluşturur:

-   Şema türü herhangi bir sıralama yönü doğrudan veya dolaylı olarak herhangi bir birleşim türü üyeleri yoluyla içeriyorsa, şema nesne modelinde bulunan ilk numaralandırılmış değer varsayılan olarak kullanılır.

-   Şema türü atomik bir tür ise, düzenleyici atomik türünü alır ve atomik tür adı ekler. Türetilen bir basit tür temel basit tür kullanır. Liste türü için atomik türüdür `itemType`. Bir birleşim için atomik türü atomik ilk türdür `memberType`.

## <a name="example"></a>Örnek

 Bu bölümdeki adımları şema oluşturulan XML parçacığını özelliğinin XML Düzenleyicisi'nin nasıl kullanılacağı gösterir.

> [!NOTE]
> Bu yordamlara başlamadan önce şema dosyasını yerel bilgisayarınıza kaydedin.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Yeni bir XML dosyası oluşturmak ve bir XML şeması ile ilişkilendirmek için

1.  Üzerinde **dosya** menüsündeki **yeni**, tıklatıp **dosya**.

2.  Seçin **XML dosyası** içinde **şablonları** bölmesinde ve tıklatın **açık**.

     Yeni bir dosya Düzenleyicisi'nde açılır. Varsayılan XML bildirimi dosyayı içeren `<?xml version="1.0" encoding="utf-8">`.

3.  Belge Özellikleri penceresinde Gözat düğmesine (**...** ) üzerinde **şemaları** alan.

     **XSD şemaları** iletişim kutusu görüntülenir.

4.  **Ekle**'yi tıklatın.

     **Açık XSD şema** iletişim kutusu görüntülenir.

5.  Şema dosyasını seçin ve tıklatın **açık**.

6.  **Tamam**'ı tıklatın.

     XML Şeması sunulmuştur XML belgesi ile ilişkilendirilmiş.

### <a name="to-generate-an-xml-snippet"></a>Bir XML parçacığını oluşturmak için

1.  Tür `<` Düzenleyicisi bölmesinde.

2.  Üye listesi olası öğeleri görüntüler:

     **!--** bir yorum ekleyin.

     **! DOCTYPE** bir belge türü eklemek için.

     **?** bir işlem yönergesi eklemek için.

     **Kişi** kök öğesi eklemek için.

3.  Seçin **kişi** basın ve üye listesi **Enter**.

     Düzenleyici başlangıç etiketi ekler `<Contact` ve sonra öğe adı imleci yerleştirir.

4.  Tuşuna **sekmesini** için XML verileri oluşturmak için `Contact` öğesi dayalı, şema bilgileri.

## <a name="input"></a>Giriş

 Aşağıdaki şema dosyası izlenecek yol tarafından kullanılır.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>Çıkış

 Aşağıdadır ilişkili şema bilgileri temel alarak oluşturulan XML veri `Contact` öğesi. İşaretli öğeleri olarak `bold` XML parçacığını düzenlenebilir alanlara belirleyin.

```xml
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML parçacıkları](../xml-tools/xml-snippets.md)
- [Nasıl yapılır: XML kullanım parçacıkları](../xml-tools/how-to-use-xml-snippets.md)