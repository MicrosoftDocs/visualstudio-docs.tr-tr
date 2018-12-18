---
title: XML Kod Parçacıkları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07ddb1dd64e5d972c23a032cb1eb752515d92ab6
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693857"
---
# <a name="xml-snippets"></a>XML parçacıkları

XML Düzenleyicisi adlı bir özellik sunar *XML parçacıkları*, XML dosyalarını daha hızlı bir şekilde oluşturmanızı sağlar. Dosyalarınızı ekleyerek XML parçacıkları yeniden kullanabilirsiniz. XML verilerini bir XML Şeması Tanım Dili (XSD) şemasını temel alan de oluşturabilirsiniz.

## <a name="reusable-xml-snippets"></a>Yeniden kullanılabilir XML parçacıkları

Bazı genel görevleri kapsayan birçok parçacıkları XML Düzenleyicisi'ni içerir. Bu, XML dosyalarını daha kolay oluşturmanıza olanak sağlar. Örneğin, "Karmaşık türü dizisi öğesi" ve "Basit türü öğesi" parçacıkları kullanarak bir XML Şeması yazma seçerseniz, aşağıdaki XML metin dosyasına ekler. Ardından değişeceğinden `name` gereksinimlerinize uygun olarak değeri.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

 İki yolla parçacıkları ekleyebilirsiniz. **Ekle parçacığı** komutu XML parçacığını İmleç konumuna ekler. **Surround With** komutu seçili metninin çevresindeki XML parçacığını sarmalar. Her iki komutlar ya da kullanılabilir gelen **IntelliSense** altında alt **Düzenle** menüsünde veya Düzenleyicisi kısayol menüsünden.

 Daha fazla bilgi için bkz: [nasıl yapılır: kullanım XML parçacıkları](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Şema oluşturulan XML parçacıkları
 XML Düzenleyicisi'ni, aynı zamanda bir XML şemasından bir XML parçacığını oluşturmak için silebilir. Bu özellik, bu öğe için şema bilgileri üretilen XML öğeleri olan bir öğe doldurmak sağlar.

 Daha fazla bilgi için bkz: [nasıl yapılır: XML şemasından bir XML parçacığını oluşturmak](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Yeni XML parçacıkları oluşturma
 Dahil edilen parçacıkları yanı sıra [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio varsayılan olarak da oluşturabilir ve kendi XML parçacıkları kullanın.

 Daha fazla bilgi için bkz: [nasıl yapılır: XML oluşturmak parçacıkları](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)