---
title: Formlar arasında veri geçirme | Microsoft Docs
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9f28902673018a4ae90fbb2ed83e741be99fbfc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204834"
---
# <a name="pass-data-between-forms"></a>Formlar arasında veri geçirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu izlenecek yolda, verileri bir biçimden diğerine geçirmek için adım adım yönergeler sağlar. Müşteriler ve siparişler tablolarından Northwind kullanarak, bir form kullanıcıların bir müşteri seçmesine izin verir ve Seçilen müşteri siparişleri ikinci bir form görüntüler. Bu izlenecek yol, ikinci formdaki verileri ilk formdan alan bir yöntem oluşturma işlemi gösterilmektedir.  
  
> [!NOTE]
>  Bu yönerge, formlar arasında veri iletmek için yalnızca bir yol gösterir. Bir ortak özellik oluşturma verilerle ilk formdan ayarlanabilir veya forma veri almak için ikinci bir oluşturucu oluşturma gibi verileri geçirmek için diğer seçenekleri vardır.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Yeni bir oluşturma **Windows uygulama** proje.  
  
-   Oluşturma ve yapılandırma ile dataset [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Form üzerinde öğelerinden sürüklendiğinde oluşturulacak denetimi seçerek **veri kaynakları** penceresi. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Öğe sürükleyerek veriye bağlı denetim oluşturma **veri kaynakları** forma penceresi.  
  
-   Verileri görüntülemek için bir kılavuz ikinci bir form oluşturuluyor.  
  
-   Belirli bir müşterinin siparişlerini getirilecek TableAdapter sorgu oluşturma.  
  
-   Formlar arasında veri geçirme.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-the-windows-application"></a>Windows uygulaması oluşturma  
  
#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Projeyi adlandırın `PassingDataBetweenForms`.  
  
3.  Seçin **Windows Forms uygulaması**, tıklatıp **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **PassingDataBetweenForms** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="create-the-data-source"></a>Veri kaynağı oluşturma  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.  
  
3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
4.  Üzerinde **veritabanı modeli seçin** sayfasında, **veri kümesi** belirtilir ve ardından **sonraki**.  
  
5.  Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdakilerden birini yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.  
  
6.  Veritabanınız parola gerektiriyorsa ve hassas verileri eklemek için seçeneği etkinse bu seçeneği belirleyin ve ardından **sonraki**.  
  
7.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.  
  
8.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.  
  
9. Seçin **müşteriler** ve **siparişler** tablolar ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve **müşteriler** ve **siparişler** tablolar görünür **veri kaynakları** penceresi.  
  
## <a name="create-the-first-form-form1"></a>İlk formu (Form1) oluşturma  
 Verilere bağlı kılavuz oluşturabilirsiniz (bir <xref:System.Windows.Forms.DataGridView> denetimi), sürükleyerek **müşteriler** düğümünden **veri kaynakları** forma penceresi.  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Form üzerinde bir verilere bağlı kılavuz oluşturmak için  
  
-   Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** penceresinden **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için görünür **Form1**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
## <a name="create-the-second-form-form2"></a>İkinci form (Form2) oluşturma  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Verileri geçirmek için ikinci bir form oluşturma  
  
1.  Gelen **proje** menüsünde seçin **Windows formu eklemek**.  
  
2.  Varsayılan adı bırakın **Form2**, tıklatıp **Ekle**.  
  
3.  Ana sürükleyin **siparişler** düğümünden **veri kaynakları** penceresinden **Form2**.  
  
     A <xref:System.Windows.Forms.DataGridView> ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için görünür **Form2**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
4.  Silme **OrdersBindingNavigator** bileşeni Tepsi öğesinden.  
  
     **OrdersBindingNavigator** kaybolur **Form2**.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>TableAdapter sorgusu Form1 Seçilen müşteri siparişleri yüklenecek Form2 ekleyin  
  
#### <a name="to-create-a-tableadapter-query"></a>TableAdapter sorgusu oluşturmak için  
  
1.  Çift **NorthwindDataSet.xsd** dosyası **Çözüm Gezgini**.  
  
2.  Sağ **orderstableadapter bağdaştırıcısına**seçip **Sorgu Ekle**.  
  
3.  Varsayılan seçenek olan bırakın **SQL deyimi kullan**ve ardından **sonraki**.  
  
4.  Varsayılan seçenek olan bırakın **satır döndüren SELECT**ve ardından **sonraki**.  
  
5.  Döndürülecek sorguya bir WHERE yan tümcesi ekleyin `Orders` göre `CustomerID`. Sorgu aşağıdakine benzemelidir:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Veritabanınız için doğru parametre sözdizimini doğrulayın. Örneğin, Microsoft Access, WHERE yan tümcesi şöyle görünmelidir: `WHERE CustomerID = ?`.  
  
6.  **İleri**'ye tıklayın.  
  
7.  İçin **DataTableMethod ad girme**, türü `FillByCustomerID`.  
  
8.  NET **DataTable Döndür** seçeneğini ve ardından **sonraki**.  
  
9. **Son**'a tıklayın.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Verileri geçirmek için Form2 üzerinde bir yöntem oluşturma  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Verileri geçirmek için bir yöntem oluşturmak için  
  
1.  Sağ **Form2**seçip **kodu görüntüle** açmak için **Form2** içinde **Kod Düzenleyicisi**.  
  
2.  Aşağıdaki kodu ekleyin **Form2** sonra `Form2_Load` yöntemi:  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Veri iletmek ve Form2 görüntülemek için Form1 üzerinde bir yöntem oluşturma  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Form2 için veri iletmek için bir yöntem oluşturmak için  
  
1.  İçinde **Form1**müşteri veri kılavuzu sağ tıklayın ve ardından **özellikleri**.  
  
2.  İçinde **özellikleri** penceresinde tıklayın **olayları**.  
  
3.  Çift **CellDoubleClick** olay.  
  
     Kod Düzenleyicisi görünür.  
  
4.  Yöntem tanımını aşağıdaki örnekle eşleşecek şekilde güncelleştirin:  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>Uygulamayı çalıştırın  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
-   Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
-   Bir müşteri kaydı çift **Form1** açmak için **Form2** müşterinin sipariş.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak, formlar arasında veri geçirme sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:  
  
-   Eklemek veya veritabanı nesnelerini kaldırmak için veri kümesini düzenleme. Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Verileri yeniden veritabanına kaydetme işlevselliği ekleme. Daha fazla bilgi için [verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

