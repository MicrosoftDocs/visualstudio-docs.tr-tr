---
title: 'Nasıl yapılır: XML şema tasarımcısını XML değişmez değerleri ile kullanma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9858768da0096c98ffb3014f0a52936adbf39019
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931122"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Nasıl yapılır: XML şema tasarımcısını XML değişmez değerleri ile kullanma

Bu konuda, bir Visual Basic projesinde sabit değeri bir XML ile ilişkili bir şeması görüntülemeyi açıklar.

## <a name="to-create-a-new-visual-basic-console-application-project"></a>Yeni bir Visual Basic konsol uygulaması projesi oluşturmak için

1.  Visual Studio'yu başlatın.

2.  Gelen **dosya** menüsünde **yeni**ve ardından **proje**. **Yeni proje** iletişim kutusu görüntülenir. İçin **proje türleri**seçin **diğer diller** seçip **Visual Basic**. İçin **şablonları**, konsol uygulaması'nı seçin. Yazarak `XMLLiterals` içinde **adı** alan ve bir proje konumda **konumu** alan. **Tamam**'ı tıklatın.

     Yeni poject oluşturulur. XMLLiterals proje bir Visual Basic kaynak dosyası içeren *Module1.vb*.

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>Mevcut bir XSD dosyası projeye eklemek için

1.  Yeni bir metin dosyasını Not Defteri'nde açın. XML şema örnek koddan kopyalama [satın alma siparişi şeması](../xml-tools/sample-xsd-file-simple-schema.md) dosyasına yapıştırın.

2.  Dosya adı ile bir konuma kaydedin *PurchaseOrderSchema.xsd*.

3.  İçinde **Çözüm Gezgini**, projenin adını sağ tıklayın, **Ekle**ve ardından **var olan öğe**. **AddExisting öğesi** iletişim kutusu görüntülenir. Gözat *PurchaseOrderSchema.xsd* dosya seçin ve ardından **Ekle**.

     XMLLiterals proje artık iki dosya içeriyor: *Module1.vb* ve *PurchaseOrderSchema.xsd*.

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Projeye dahil XSD dosyası göre bir XML değişmez değer, Visual Basic kodunu eklemek için

1. Değiştirin *Module1.vb* dosyasındaki kodu aşağıdaki kodla:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Herhangi bir XML değişmez değeri ya da bir XML ad alanı alma XML düğümünü sağ tıklatın ve seçin **şema Gezgini'nde Göster**.

    **XML Şeması Gezgini** XML şema kümesi ile ilişkili XML değişmez değeri olan bir Visual Basic dosyası ile yan yana görüntülenir.