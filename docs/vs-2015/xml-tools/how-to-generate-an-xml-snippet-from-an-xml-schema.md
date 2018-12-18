---
title: 'Nasıl yapılır: XML şemasından XML kod parçacığı oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6eb03fba400e20227155a2528b8aaf0b28f7761a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951476"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Nasıl yapılır: XML şemasından XML kod parçacığı oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Düzenleyicisi'ni XML Şeması Tanım Dili (XSD) şemasından XML kod parçacıklarını oluşturma özelliğine sahiptir. Örneğin, öğe adı yanındaki konumlandırılmış olsa bir XML dosyasına yazma gibi öğenin o öğe için şema bilgileri üretilen XML verileri ile doldurmak için SEKME tuşuna basabilirsiniz.  
  
 Bu özellik yalnızca öğeleri üzerinde kullanılabilir. Ayrıca, aşağıdaki kurallar geçerlidir:  
  
- Öğesi, bir ilişkili şema türü olması gerekir; diğer bir deyişle, öğe ilişkili bazı şemaya göre geçerli olmalıdır. Şema türü soyut olamaz ve türü gerekli öznitelikler içermelidir ve/veya alt öğeleri gereklidir.  
  
- Geçerli öğe düzenleyicide özniteliklere boş olmalıdır. Örneğin, tüm geçerli aşağıda verilmiştir  
  
  -   `<Account`  
  
  -   `<Account>`  
  
  -   `<Account></Account>`  
  
- İmleç hemen öğe adı sağa bulunmalıdır.  
  
  Oluşturulan kod parçacığı, tüm gerekli öznitelikler ve öğeler içerir. Varsa `minOccurs` biri, gerekli en az o öğenin örnek sayısı en çok 100 örnek kod parçacığında dahil edilenlerden daha büyüktür. Herhangi bir sabit değerlerini sabit değerleri kod parçacığında şema sonucu bulunamadı. `xsd:any` ve `xsd:anyAttribute` öğeleri göz ardı edilir ve hiçbir ek kod parçacığı yapılardan neden.  
  
  Varsayılan değerleri oluşturulur ve düzenlenebilir değerleri Not. Şema varsayılan değeri belirtiyorsa, bu varsayılan değer kullanılır. Ancak, şema varsayılan değer boş bir dize ise, düzenleyici varsayılan değerleri aşağıdaki şekilde oluşturur:  
  
- Şema türü herhangi bir sabit listesi modelleri, doğrudan veya dolaylı olarak herhangi bir birleşim tipinin üye yoluyla içeriyorsa şema nesne modeli içinde bulunan ilk numaralandırılmış değer varsayılan olarak kullanılır.  
  
- Şema türü atomik bir tür ise, düzenleyici atomik türü alır ve atomik tür adını ekler. Türetilen bir basit türü için temel bir basit türü kullanır. Atomik türü için listeyi türdür `itemType`. Atomik türü bir birleşimin atomik ilk türüdür `memberType`.  
  
## <a name="example"></a>Örnek  
 Bu bölümdeki adımlar, şema tarafından oluşturulan XML kod parçacığı özelliği XML Düzenleyicisi'nin kullanımını gösterir.  
  
> [!NOTE]
>  Bu yordamlar başlatmadan önce şema dosyasını yerel bilgisayarınıza kaydedin.  
  
#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Yeni bir XML dosyası oluşturun ve bir XML şeması ile ilişkilendirmek için  
  
1.  Üzerinde **dosya** menüsünde **yeni**, tıklatıp **dosya**.  
  
2.  Seçin **XML dosyası** içinde **şablonları** bölmesi ve tıklatın **açık**.  
  
     Yeni bir dosya düzenleyicide açılır. Varsayılan XML bildirimi dosyasını içeren `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Belge Özellikler penceresinde, Gözat düğmesine tıklayın (**...** ) üzerinde **şemaları** alan.  
  
     **XSD şemaları** iletişim kutusu görüntülenir.  
  
4.  **Ekle**'yi tıklatın.  
  
     **Açık XSD şeması** iletişim kutusu görüntülenir.  
  
5.  Şema dosyası seçin ve tıklayın **açık**.  
  
6.  **Tamam**'ı tıklatın.  
  
     XML Şeması sunulmuştur XML belge ile ilişkilendirilmiş.  
  
#### <a name="to-generate-an-xml-snippet"></a>XML kod parçacığı oluşturmak için  
  
1.  Tür `<` Düzenleyicisi bölmesinde.  
  
2.  Üye listesi, mümkün olan öğeleri görüntüler:  
  
     **!--** açıklama eklemek için.  
  
     **! DOCTYPE** belge türü eklemek için.  
  
     **?** bir işlem yönergesi eklemek için.  
  
     **İlgili kişi** kök öğe eklemek için.  
  
3.  Seçin **kişi** üye listesi ve ENTER tuşuna basın.  
  
     Düzenleyici başlangıç etiketi ekler `<Contact` ve imleci öğe adından sonra konumlandırır.  
  
4.  XML verileri oluşturmak için TAB'a basın `Contact` öğesi üzerinde şema bilgilerini temel.  
  
### <a name="input"></a>Giriş  
 Aşağıdaki şema dosyası izlenecek yol tarafından kullanılır.  
  
```  
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
 İle ilişkili şema bilgilere dayanarak oluşturulan XML verileri aşağıdadır `Contact` öğesi. İşaretli öğeleri olarak `bold` düzenlenebilir XML kod parçacığı alanlarını belirleyin.  
  
```  
<Contact>  
  <Name>name</Name>  
  <Title>title</Title>  
  <Phone>  
    <Number>number</Number>  
    <Type>Voice</Type>  
  </Phone>  
</Contact>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML kod parçacıkları](../xml-tools/xml-snippets.md)   
 [Nasıl Yapılır: XML Kod Parçacıklarını Kullanma](../xml-tools/how-to-use-xml-snippets.md)



