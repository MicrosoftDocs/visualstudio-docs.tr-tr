---
title: Bir veri kümesinin içine XML verileri okuma
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1e43d118a5fcfe00a8eb6eaa7f34a17ff1f6a4be
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389221"
---
# <a name="read-xml-data-into-a-dataset"></a>Bir veri kümesinin içine XML verileri okuma

ADO.NET ile XML verileri çalışmak için basit yöntemler sağlar. Bu kılavuzda, bir veri kümesine XML veri yükleyen bir Windows uygulaması oluşturun. Veri kümesi ardından görüntülenen bir <xref:System.Windows.Forms.DataGridView> denetimi. Son olarak, bir XML Şeması XML dosyasının içeriğine göre metin kutusunda görüntülenir.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

Bu adımda, bir Visual Basic veya Visual C# projesi oluşturun.

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#** veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **ReadingXML**ve ardından **Tamam**.

   **ReadingXML** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Dataset nesnesine okumak için XML dosyası oluştur

Bu izlenecek yol, bir veri kümesine XML verilerini okuma üzerinde odaklanır olduğundan, bir XML dosyasının içeriğini sağlanır.

1. Üzerinde **proje** menüsünde **Yeni Öğe Ekle**.

2. Seçin **XML dosyası**, dosya adı **authors.xml**ve ardından **Ekle**.

   XML dosyası tasarımcıya yükler ve düzenleme için hazırdır.

3. Aşağıdaki XML veri Düzenleyicisi XML bildirimi aşağıda yapıştırın:

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

4. Üzerinde **dosya** menüsünde **authors.xml Kaydet**.

## <a name="create-the-user-interface"></a>Kullanıcı arabirimi oluşturma

Bu uygulama için kullanıcı arabirimi aşağıdakilerden oluşur:

-   A <xref:System.Windows.Forms.DataGridView> verileri olarak XML dosyasının içeriğini görüntüleyen denetim.

-   A <xref:System.Windows.Forms.TextBox> XML dosyasını XML şemasını görüntüler denetimi.

-   İki <xref:System.Windows.Forms.Button> kontrol eder.

    -   Bir düğme XML dosyasının DataSet'e okur ve görüntüler <xref:System.Windows.Forms.DataGridView> denetimi.

    -   İkinci bir düğme şema veri kümesinden ve aracılığıyla ayıklar bir <xref:System.IO.StringWriter> görüntüler <xref:System.Windows.Forms.TextBox> denetimi.

### <a name="to-add-controls-to-the-form"></a>Formu için denetimler ekleme

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

## <a name="create-the-dataset-that-receives-the-xml-data"></a>XML veri alan veri kümesi oluşturma

Bu adımda, adlı yeni bir veri kümesi oluşturma `authors`. Veri kümeleri hakkında daha fazla bilgi için bkz. [Visual Studio'daki veri kümesi Araçları](../data-tools/dataset-tools-in-visual-studio.md).

1.  İçinde **Çözüm Gezgini**, kaynak dosyasını seçin **Form1**ve ardından **Görünüm Tasarımcısı** düğmesini **Çözüm Gezgini** araç çubuğu.

2.  Gelen [araç kutusu, veri sekmesi](../ide/reference/toolbox-data-tab.md), sürükleyin bir **veri kümesi** üzerine **Form1**.

3.  İçinde **veri kümesi Ekle** iletişim kutusunda **türü belirsiz dataset**ve ardından **Tamam**.

     **DataSet1** bileşen tepsisine eklenir.

4.  İçinde **özellikleri** penceresinde **adı** ve <xref:System.Data.DataSet.DataSetName%2A> özelliklerini`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>XML dosyasının DataSet'e okumak için olay işleyicisi oluşturun

**Okuma XML** düğmesi kümesine XML dosyasını okur. Üzerinde özelliklerini daha sonra Ayarlar <xref:System.Windows.Forms.DataGridView> veri kümesine bağlanan bir denetim.

1.  İçinde **Çözüm Gezgini**seçin **Form1**ve ardından **Görünüm Tasarımcısı** düğmesini **Çözüm Gezgini** araç çubuğu.

2.  Seçin **okuma XML** düğmesi.

     **Kod Düzenleyicisi** açılır `ReadXmlButton_Click` olay işleyicisi.

3.  Aşağıdaki kodu yazın `ReadXmlButton_Click` olay işleyicisi:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  İçinde `ReadXMLButton_Click` olay işleyici kodu, değişiklik `filepath =` doğru yola girişi.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Şema metin kutusunda görüntülemek için olay işleyicisi oluşturun

**Göster şema** düğmesi oluşturur bir <xref:System.IO.StringWriter> şema ile doldurulur ve görüntülenen nesne <xref:System.Windows.Forms.TextBox>denetimi.

1.  İçinde **Çözüm Gezgini**seçin **Form1**ve ardından **Görünüm Tasarımcısı** düğmesi.

2.  Seçin **Göster şema** düğmesi.

     **Kod Düzenleyicisi** açılır `ShowSchemaButton_Click` olay işleyicisi.

3.  Aşağıdaki kodu yapıştırın `ShowSchemaButton_Click` olay işleyicisi.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Form test

Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.

1.  Seçin **F5** uygulamayı çalıştırın.

2.  Seçin **okuma XML** düğmesi.

     DataGridView XML dosyasının içeriğini görüntüler.

3.  Seçin **Göster şema** düğmesi.

     XML Şeması XML dosyası için metin kutusu görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

Bu izlenecek yol, bir şema XML dosyasının içeriğine göre oluşturma yanı sıra bir XML dosyası okunurken bir veri kümesine ilişkin temel bilgileri size öğretir. Sonraki yapabilecek bazı görevler aşağıda verilmiştir:

-   Veri kümesini ve geri XML olarak yazma verileri düzenleyin. Daha fazla bilgi için bkz. <xref:System.Data.DataSet.WriteXml%2A>.

-   Veri kümesindeki verileri düzenleyebilir ve veritabanına yazamadı.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [Visual Studio'daki XML araçları](../xml-tools/xml-tools-in-visual-studio.md)