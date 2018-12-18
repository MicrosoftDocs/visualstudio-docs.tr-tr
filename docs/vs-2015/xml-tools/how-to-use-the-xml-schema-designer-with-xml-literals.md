---
title: 'Nasıl yapılır: XML şema tasarımcısını XML değişmez değerleri ile kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 592886a1cfe9d0ffc9c7165729cede3340bc65c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218380"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Nasıl yapılır: XML şema tasarımcısını XML değişmez değerleri ile kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu konuda, bir Visual Basic projesinde sabit değeri bir XML ile ilişkili bir şeması görüntülemeyi açıklar.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Yeni bir Visual Basic konsol uygulaması projesi oluşturmak için  
  
1.  Visual Studio 2010'u başlatın.  
  
2.  Gelen **dosya** menüsünde **yeni**ve ardından **proje**. **Yeni proje** iletişim kutusu görüntülenir. İçin **proje türleri**seçin **diğer diller** seçip **Visual Basic**. İçin **şablonları**, konsol uygulaması'nı seçin. Yazarak `XMLLiterals` içinde **adı** alan ve bir proje konumda **konumu** alan. **Tamam**'ı tıklatın.  
  
     Yeni poject oluşturulur. XMLLiterals proje bir Visual Basic kaynak dosyası, Module1.vb içeriyor.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Mevcut bir XSD dosyası projeye eklemek için  
  
1.  Açık bir yeni metin dosyası içinde Notepad.Copy XML şema örnek koddan [satınalma siparişi şeması](../xml-tools/sample-xsd-file-simple-schema.md) dosyasına yapıştırın.  
  
2.  Dosya PurchaseOrderSchema.xsd ada sahip bir konuma kaydedin.  
  
3.  Çözüm Gezgini'nde proje adına sağ tıklayın, seçin **Ekle**ve ardından **mevcut öğe...** . **AddExisting öğesi** iletişim kutusu görüntülenir. PurchaseOrderSchema.xsd dosyasına gidin, seçin ve ardından **Ekle**.  
  
     XMLLiterals proje artık iki dosya içeriyor: Module1.vb ve PurchaseOrderSchema.xsd.  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Projeye dahil XSD dosyası göre bir XML değişmez değer, Visual Basic kodunu eklemek için  
  
1.  Module1.vb dosyasındaki kodu aşağıdaki kodla değiştirin:  
  
    ```  
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
  
2.  Herhangi bir XML değişmez değeri ya da bir XML ad alanı alma XML düğümünü sağ tıklatın ve seçin **şema Gezgini'nde Göster**.  
  
     XML şema Gezgini'ni ayarlama XML değişmez değer assotiated XML şeması ile sahip bir Visual Basic dosyası ile yan yana görüntülenir.



