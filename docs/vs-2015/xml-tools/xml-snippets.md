---
title: XML kod parçacıklarını | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf1ebeb70931e2e12f056ecfbaa45a6833e031df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183969"
---
# <a name="xml-snippets"></a>XML Kod Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Düzenleyicisi adlı bir özellik sunar *XML kod parçacıklarını*, XML dosyalarını daha hızlı bir şekilde oluşturmanızı sağlar. XML kod parçacıklarını dosyalarınızı ekleyerek yeniden kullanabilirsiniz. XML veri bir XML Şeması Tanım Dili (XSD) şemaya göre de oluşturabilirsiniz.  
  
## <a name="reusable-xml-snippets"></a>Yeniden kullanılabilir XML kod parçacıkları  
 XML Düzenleyicisi'ni bazı genel görevleri kapsayan çok sayıda kod parçacıkları içerir. Bu XML dosyaları daha bir kolayca oluşturmanıza olanak sağlar. Örneğin, "Karmaşık türü dizisi öğesi" ve "Basit türü öğesi" kod parçacıkları kullanarak bir XML Şeması yazıyorsanız dosyanıza aşağıdaki XML metni ekler. Ardından değiştirirsiniz `name` gereksinimlerinize uyacak şekilde değeri.  
  
```  
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
  
 Kod parçacıkları iki yolla ekleyebilirsiniz. **Parçacık Ekle** komut İmleç konumuna XML kod parçacığı ekler. **Surround With** komut XML kod parçacığı seçili metin etrafına sarmalar. Her iki komutu ya da kullanılabilir gelen **IntelliSense** altında alt **Düzenle** menüsünden veya Düzenleyicisi kısayol menüsünden.  
  
 Daha fazla bilgi için [nasıl yapılır: XML Parçacıkları kullanma](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Şema tarafından oluşturulan XML kod parçacıkları  
 XML Düzenleyicisi'ni XML şemasından XML kod parçacığı oluşturma olanağı da vardır. Bu özellik, öğenin o öğe için şema bilgileri üretilen XML öğeleri ile doldurmak verir.  
  
 Daha fazla bilgi için [nasıl yapılır: bir XML kod parçacığı öğesinden bir XML şeması oluşturmak](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Yeni kod parçacıkları oluşturma  
 İçerdiği parçacıkları yanı sıra [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio varsayılan olarak da oluşturabilir ve kendi XML kod parçacıklarını kullanma.  
  
 Daha fazla bilgi için [nasıl yapılır: XML kod parçacıklarını oluşturma](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)



