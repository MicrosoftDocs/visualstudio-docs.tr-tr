---
title: 'İzlenecek yol: birden çok sorgu içeren bir TableAdapter oluşturma | Microsoft Docs'
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4226fc805ed0335109d0a6b98f1235ae46de1664
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206706"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>İzlenecek yol: Birden Çok Sorgu İçeren bir TableAdapter Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda, kullanarak veri kümesinde bir TableAdapter oluşturacaksınız [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). İzlenecek yol içinde ikinci bir sorgu oluşturma işlemi boyunca sürer [TableAdapter](../data-tools/tableadapter-overview.md) kullanarak [TableAdapters düzenleme](../data-tools/editing-tableadapters.md) içinde [veri kümesi Tasarımcısı](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Yeni bir oluşturma **Windows uygulama** proje.  
  
-   Oluşturma ve bir veri kümesi oluşturarak uygulamanızda bir veri kaynağı yapılandırma **veri kaynağı Yapılandırma Sihirbazı**.  
  
-   Yeni veri kümesi içinde açma **veri kümesi Tasarımcısı**.  
  
-   İle Tableadapter'a sorgular ekleme **TableAdapter sorgu Yapılandırma Sihirbazı'nı**.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına (SQL Server veya Access sürümü) erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application"></a>Yeni bir Windows uygulaması oluşturma  
 İlk adım bir Windows uygulaması oluşturmaktır.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Yeni bir Windows uygulaması projesi oluşturmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Bir programlama dili seçin **proje türleri** bölmesi.  
  
3.  Tıklayın **Windows uygulama** içinde **şablonları** bölmesi.  
  
4.  Projeyi adlandırın `TableAdapterQueriesWalkthrough`ve ardından **Tamam**.  
  
     Visual Studio projeyi ekler **Çözüm Gezgini** ve tasarımcıda yeni bir form görüntüler.  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>Bir TableAdapter ile veritabanı veri kaynağı oluşturma  
 Bu adımda, bir veri kaynağı kullanılarak oluşturulur **veri kaynağı Yapılandırma Sihirbazı** göre `Customers` Northwind örnek veritabanındaki tablo. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
         veya  
  
    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.  
  
5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
6.  Tıklayın **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.  
  
7.  Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.  
  
8.  Seçin **müşteriler** tablosunu ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve **müşteriler** tablo görünür **veri kaynakları** penceresi.  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>Veri kümesi Tasarımcısı'nda veri kümesini açma  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>Veri kümesini veri kümesi Tasarımcısı'nda açmak için  
  
1.  Sağ **NorthwindDataset** içinde **veri kaynakları** penceresi.  
  
2.  Kısayol menüsünde **tasarımcı ile DataSet Düzenle**.  
  
     Nda NorthwindDataset açılır **veri kümesi Tasarımcısı**.  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>Customerstableadapter'a ikinci sorgu ekleme  
 Sihirbaz, veri kümesi ile oluşturulan bir **müşteriler** veri tablosu ve **CustomersTableAdapter**. Kılavuzun bu bölümünde, ikinci bir sorgu ekler **CustomersTableAdapter**.  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>CustomersTableAdapter öğesine bir sorgu ekleme  
  
1.  Sürükleme bir **sorgu** gelen **veri kümesi** sekmesinde **araç kutusu** üzerine **müşteriler** tablo.  
  
     [TableAdapters düzenleme](../data-tools/editing-tableadapters.md) açılır.  
  
2.  Seçin **SQL deyimi kullan**ve ardından **sonraki**.  
  
3.  Seçin **satır döndüren SELECT**ve ardından **sonraki**.  
  
4.  Okunması sorguya bir WHERE yan tümcesi ekleyin:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Northwind'in Access sürümünü kullanıyorsanız değiştirin @City bir soru işaretiyle parametresi. (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  Üzerinde **oluşturmak için yöntemlerini seçin** sayfasında, ad **DataTable Doldur** yöntemi `FillByCity`.  
  
    > [!NOTE]
    >  Yönteme **DataTable Döndür** Bu izlenecek yolda, bu nedenle onay kutusunu temizleyin veya varsayılan adı bırakın kullanılmaz.  
  
6.  Tıklayın **sonraki** ve Sihirbazı tamamlayın.  
  
     **FillByCity** sorgu eklenir **CustomersTableAdapter**.  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>Formda ek sorgu yürütmek için kod ekleme  
  
#### <a name="to-execute-the-query"></a>Sorguyu yürütmek için  
  
1.  Seçin **Form1** içinde **Çözüm Gezgini**, tıklatıp **Görünüm Tasarımcısı**.  
  
2.  Sürükleme **müşteriler** düğümünden **veri kaynakları** penceresine **Form1**.  
  
3.  Seçerek kod görünümüne değiştirin **kod** gelen **görünümü** menüsü.  
  
4.  Değiştirin `Form1_Load` çalıştırmak için aşağıdaki olay işleyicisini `FillByCity` sorgu.  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>Uygulamayı Çalıştırma  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
-   F5 tuşuna basın.  
  
-   Kılavuz, müşterilerle doldurulur bir `City` değerini `Seattle`.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
### <a name="to-add-functionality-to-your-application"></a>Uygulamanıza işlev eklemek için  
  
-   Ekleme bir <xref:System.Windows.Forms.TextBox> denetimi ve <xref:System.Windows.Forms.Button> denetlemek ve değeri metin kutusunda sorguya iletin. (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   Doğrulama mantığı eklemenize <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> veri kümesindeki veri tablolarının olay. Daha fazla bilgi için [veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Tableadapter'lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)   
 [Nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md)   
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)