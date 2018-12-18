---
title: Okuma XML veri kümesine | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6eb85fcef78b4b856c47ccb4436d1314ae440136
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219737"
---
# <a name="read-xml-data-into-a-dataset"></a>Bir veri kümesinin içine XML verileri okuma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
ADO.NET ile XML verileri çalışmak için basit yöntemler sağlar. Bu kılavuzda, bir veri kümesine XML veri yükleyen bir Windows uygulaması oluşturun. Veri kümesi ardından görüntülenen bir <xref:System.Windows.Forms.DataGridView> denetimi. Son olarak, bir XML Şeması XML dosyasının içeriğine göre metin kutusunda görüntülenir.  
  
 Bu izlenecek yol, beş ana adımdan oluşur:  
  
1.  Yeni proje oluşturma  
  
2.  Dataset nesnesine okumak için bir XML dosyası oluşturma  
  
3.  Kullanıcı arabirimi oluşturma  
  
4.  İçinde görüntüleyen veri kümesi oluşturma ve XML dosyası okunurken bir <xref:System.Windows.Forms.DataGridView> denetimi  
  
5.  XML şeması görüntülemek için kod ekleme temel XML dosyasında bir <xref:System.Windows.Forms.TextBox> denetimi  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları Yardım menüsünde açıklanana etkin ayarlarınıza veya sürüm bağlı olarak değişebilir gördüğünüz kullandığınız. Ayarlarınızı değiştirmek için **Araçları** menüsünde**içeri ve dışarı aktarma ayarları**. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
 Bu adımda, bu izlenecek yolda içeren bir Visual Basic veya Visual C# projesi oluşturun.  
  
#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Projeyi adlandırın `ReadingXML`.  
  
3.  Seçin **Windows uygulama**ve ardından **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **ReadingXML** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Dataset nesnesine okumak için XML dosyası oluştur  
 Bu izlenecek yol, bir veri kümesine XML verilerini okuma üzerinde odaklanır olduğundan, bir XML dosyasının içeriğini sağlanır.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Veri kümesine okunacak XML dosyası oluşturmak için  
  
1.  Üzerinde **proje** menüsünde**Yeni Öğe Ekle**.  
  
2.  Seçin **XML dosyası**, dosya adı `authors.xml`ve ardından **Ekle**.  
  
     XML dosyası tasarımcıya yükler ve düzenleme için hazırdır.  
  
3.  XML bildirimi aşağıda düzenleyicisine aşağıdaki kodu yapıştırın:  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4.  Üzerinde **dosya** menüsünde**authors.xml Kaydet**.  
  
## <a name="create-the-user-interface"></a>Kullanıcı arabirimi oluşturma  
 Bu uygulama için kullanıcı arabirimi aşağıdakilerden oluşur:  
  
-   A <xref:System.Windows.Forms.DataGridView> verileri olarak XML dosyasının içeriğini görüntüleyen denetim.  
  
-   A <xref:System.Windows.Forms.TextBox> XML dosyasını XML şemasını görüntüler denetimi.  
  
-   İki <xref:System.Windows.Forms.Button> kontrol eder.  
  
    -   Bir düğme XML dosyasının DataSet'e okur ve görüntüler <xref:System.Windows.Forms.DataGridView> denetimi.  
  
    -   İkinci bir düğme şema veri kümesinden ve aracılığıyla ayıklar bir <xref:System.IO.StringWriter> görüntüler <xref:System.Windows.Forms.TextBox> denetimi.  
  
#### <a name="to-add-controls-to-the-form"></a>Formu için denetimler ekleme  
  
1.  Açık `Form1` Tasarım görünümünde.  
  
2.  Gelen **araç kutusu**, aşağıdaki denetimleri form üzerine sürükleyin:  
  
    -   Bir <xref:System.Windows.Forms.DataGridView> denetimi  
  
    -   Bir <xref:System.Windows.Forms.TextBox> denetimi  
  
    -   İki <xref:System.Windows.Forms.Button> denetimleri  
  
3.  Aşağıdaki özellikleri ayarlayın:  
  
    |Denetim|Özellik|Ayar|  
    |-------------|--------------|-------------|  
    |`TextBox1`|**Çok satırlı**|`true`|  
    ||**Kaydırma çubukları**|**Dikey**|  
    |`Button1`|**Ad**|`ReadXmlButton`|  
    ||**Metin**|`Read XML`|  
    |`Button2`|**Ad**|`ShowSchemaButton`|  
    ||**Metin**|`Show Schema`|  
  
## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Veri kümesi thatreceives XML verileri oluşturma  
 Bu adımda, adlı yeni bir veri kümesi oluşturma `authors`. Veri kümeleri hakkında daha fazla bilgi için bkz. [Visual Studio'daki veri kümesi Araçları](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>XML verileri alan yeni bir veri kümesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, kaynak dosyasını seçin **Form1**ve ardından **Görünüm Tasarımcısı** düğmesini **Çözüm Gezgini** araç çubuğu.  
  
2.  Gelen [araç kutusu, veri sekmesinde](../ide/reference/toolbox-data-tab.md), sürükleyin bir **veri kümesi** üzerine **Form1**.  
  
3.  İçinde **veri kümesi Ekle** iletişim kutusunda **türü belirsiz dataset**ve ardından **Tamam**.  
  
     **DataSet1** bileşen tepsisine eklenir.  
  
4.  İçinde **özellikleri** penceresinde **adı** ve <xref:System.Data.DataSet.DataSetName%2A> özelliklerini`AuthorsDataSet`.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>XML dosyasının DataSet'e okumak için olay işleyicisi oluşturun  
 **Okuma XML** düğmesi kümesine XML dosyasını okur. Üzerinde özelliklerini daha sonra Ayarlar <xref:System.Windows.Forms.DataGridView> veri kümesine bağlanan bir denetim.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>ReadXmlButton_Click olay işleyicisine kod eklemek için  
  
1.  İçinde **Çözüm Gezgini**seçin **Form1**ve ardından **Görünüm Tasarımcısı** düğmesini **Çözüm Gezgini** araç çubuğu.  
  
2.  Seçin **okuma XML** düğmesi.  
  
     **Kod Düzenleyicisi** açılır `ReadXmlButton_Click` olay işleyicisi.  
  
3.  Aşağıdaki kodu yazın `ReadXmlButton_Click` olay işleyicisi:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]  
  
4.  İçinde `ReadXMLButton_Click` olay işleyici kodu, değişiklik `filepath =` doğru yola girişi.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Şema metin kutusunda görüntülemek için olay işleyicisi oluşturun  
 **Göster şema** düğmesi oluşturur bir <xref:System.IO.StringWriter> şema ile doldurulur ve görüntülenen nesne <xref:System.Windows.Forms.TextBox>denetimi.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>ShowSchemaButton_Click olay işleyicisine kod eklemek için  
  
1.  İçinde **Çözüm Gezgini**seçin **Form1**ve ardından **Görünüm Tasarımcısı** düğmesi.  
  
2.  Seçin **Göster şema** düğmesi.  
  
     **Kod Düzenleyicisi** açılır `ShowSchemaButton_Click` olay işleyicisi.  
  
3.  Aşağıdaki kodu yazın `ShowSchemaButton_Click` olay işleyicisi.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Form test  
 Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
1.  Seçin **F5** uygulamayı çalıştırın.  
  
2.  Seçin **okuma XML** düğmesi.  
  
     DataGridView XML dosyasının içeriğini görüntüler.  
  
3.  Seçin **Göster şema** düğmesi.  
  
     XML Şeması XML dosyası için metin kutusu görüntüler.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu izlenecek yol, bir şema XML dosyasının içeriğine göre oluşturma yanı sıra bir XML dosyası okunurken bir veri kümesine ilişkin temel bilgileri size öğretir. Sonraki yapabilecek bazı görevler aşağıda verilmiştir:  
  
-   Veri kümesini ve geri XML olarak yazma verileri düzenleyin. Daha fazla bilgi için bkz. <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Veri kümesindeki verileri düzenleyebilir ve veritabanına yazamadı. Daha fazla bilgi için [verileri kaydetme](../data-tools/saving-data.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Visual Studio'daki XML Araçları](../xml-tools/xml-tools-in-visual-studio.md)

