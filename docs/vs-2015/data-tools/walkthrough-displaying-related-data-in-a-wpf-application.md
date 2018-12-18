---
title: 'İzlenecek yol: WPF uygulamasında ilgili verileri görüntüleme | Microsoft Docs'
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1fc90acf94fde0ef815fc3a487412bba8e8257ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913143"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>İzlenecek Yol: Bir WPF Uygulamasında İlgili Verileri Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda, üst/alt ilişkisine sahip veritabanı tablolarındaki verileri görüntüleyen bir WPF uygulaması oluşturacaksınız. Veri varlıkları bir varlık veri modeli içinde kapsüllenir. Üst varlığın siparişler bir dizi için genel bakış bilgileri içerir. Bu varlığın her bir özellik, farklı bir denetime uygulamadaki bağlıdır. Alt varlık her sipariş ayrıntılarını içerir. Bu veri kümesini bağlı bir <xref:System.Windows.Controls.DataGrid> denetimi.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Bir WPF uygulamasını ve verileri AdventureWorksLT örnek veritabanını kullanarak oluşturulan bir varlık veri modeli oluşturuluyor.  
  
- Bir dizi siparişler kümesi için genel bakış bilgilerini gösteren verilere bağlı denetimler oluşturma. Bir üst varlıktan sürükleyerek denetimleri oluşturma **veri kaynakları** penceresine **WPF Tasarımcısı**.  
  
- Oluşturma bir <xref:System.Windows.Controls.DataGrid> her biri için ilgili ayrıntıları gösteren denetim seçili sırası. Bir alt varlık sürükleyerek denetimleri oluşturma **veri kaynakları** pencereyi bir pencere içinde **WPF Tasarımcısı**.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Çalışan bir SQL Server veya SQL Server bağlı AdventureWorksLT örnek veritabanı içeren bir Express örneğine erişim. AdventureWorksLT veritabanı indirebileceğiniz [CodePlex Web site](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Aşağıdaki kavramları bilgisi de faydalıdır, ancak izlenecek yolu tamamlamak için gerekli değil:  
  
- Varlık veri modelleri ve ADO.NET varlık çerçevesi. Daha fazla bilgi için [Entity Framework'e Genel Bakış](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- WPF Tasarımcısı ile çalışma. Daha fazla bilgi için [WPF ve Silverlight Tasarımcısı genel bakış](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- WPF veri bağlaması. Daha fazla bilgi için [Data Binding Overview](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Sipariş kayıtları görüntülemek için yeni bir WPF projesi oluşturun.  
  
#### <a name="to-create-a-new-wpf-project"></a>Yeni bir WPF projesi oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Genişletin **Visual C#** veya **Visual Basic**ve ardından **Windows**.  
  
4.  Emin olun **.NET Framework 4** iletişim kutusunun üstündeki birleşik giriş kutusunda seçilir. <xref:System.Windows.Controls.DataGrid> Bu izlenecek yolda kullandığınız denetim, yalnızca .NET Framework 4'te kullanılabilir.  
  
5.  Seçin **WPF uygulaması** proje şablonu.  
  
6.  İçinde **adı** kutusuna `AdventureWorksOrdersViewer`.  
  
7.  **Tamam**'ı tıklatın.  
  
     Visual Studio oluşturur `AdventureWorksOrdersViewer` proje.  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>Uygulama için bir varlık veri modeli oluşturma  
 Verilere bağlı denetimler oluşturabilmeniz için uygulamanız için bir veri modeli tanımlamanızı ve kendisine eklemeniz gerekir **veri kaynakları** penceresi. Bu kılavuzda, bir varlık veri modeline veri modelidir.  
  
#### <a name="to-create-an-entity-data-model"></a>Bir varlık veri modeli oluşturmak için  
  
1. Üzerinde **veri** menüsünü tıklatın **yeni veri kaynağı Ekle** açmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
2. Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı**ve ardından **sonraki**.  
  
3. Üzerinde **veritabanı modeli seçin** sayfasında **varlık veri modeli**ve ardından **sonraki**.  
  
4. Üzerinde **Choose Model Contents** sayfasında **veritabanından Oluştur**ve ardından **sonraki**.  
  
5. Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdakilerden birini yapın:  
  
   - AdventureWorksLT örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir haldeyse, onu seçin.  
  
      veya  
  
   - Tıklayın **yeni bağlantı** ve AdventureWorksLT veritabanına bağlantı oluşturun.  
  
     Emin olun **varlığı App.Config dosyasındaki bağlantı ayarlarını Kaydet** seçeneği seçilidir ve ardından **sonraki**.  
  
6. Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları**ve ardından aşağıdaki tablolar'ı seçin:  
  
   -   **Satış siparişi ayrıntısını**  
  
   -   **SalesOrderHeader**  
  
7. **Son**'a tıklayın.  
  
8. Projeyi oluşturun.  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>Görüntüleyen siparişleri kontrol veri bağlama oluşturma  
 Sürükleyerek siparişi kayıtlarını görüntüleyen denetimler oluşturma `SalesOrderHeaders` varlıktan **veri kaynakları** penceresinden WPF tasarımcısına.  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Siparişi kayıtlarını verilere bağlı denetimler oluşturmak için  
  
1. İçinde **Çözüm Gezgini**, MainWindow.xaml çift tıklayın.  
  
    WPF Tasarımcısı'nda penceresi açılır.  
  
2. XAML Düzenle böylece **yükseklik** ve **genişliği** özellikleri için 800 ayarlanır  
  
3. İçinde **veri kaynakları** penceresinde açılan menüsüne tıklayın **SalesOrderHeaders** düğümünü seçip alt **ayrıntıları**.  
  
4. Genişletin **SalesOrderHeaders** düğümü.  
  
5. Yanındaki açılır menüyü tıklayın **SalesOrderID** seçip **ComboBox**.  
  
6. Her biri aşağıdaki alt düğümleri için **SalesOrderHeaders** düğümü, açılan menüsünün yanındaki düğümü tıklatın ve seçin **hiçbiri**:  
  
   - **RevisionNumber**  
  
   - **OnlineOrderFlag**  
  
   - **ShipToAddressID**  
  
   - **BillToAddressID**  
  
   - **CreditCardApprovalCode**  
  
   - **Ara toplam**  
  
   - **TaxAmt**  
  
   - **Nakliye**  
  
   - **ROWGUID**  
  
   - **ModifiedDate**  
  
     Bu eylem, Visual Studio, bir sonraki adımda bu düğümler için verilere bağlı denetimler oluşturmanızı engeller. Bu kılavuz için son kullanıcı bu verileri görme gerekmez varsayılır.  
  
7. Gelen **veri kaynakları** penceresinde Sürükle **SalesOrderHeaders** penceresinde düğüme **WPF Tasarımcısı**.  
  
    Visual Studio'nun oluşturduğu verilere bağlı denetimler kümesini oluşturan XAML **SalesOrderHeaders** varlık ve kod veri yükler. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8. Tasarımcıda birleşik giriş kutusunun yanındaki tıklayın **satış siparişi kodu** etiketi.  
  
9. İçinde **özellikleri** yanındaki onay kutusunu penceresinde **IsReadOnly** özelliği.  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Sipariş ayrıntılarını görüntüleyen bir DataGrid oluşturma  
 Oluşturma bir <xref:System.Windows.Controls.DataGrid> sürükleyerek sipariş ayrıntılarını gösteren denetim `SalesOrderDetails` varlıktan **veri kaynakları** penceresinden WPF tasarımcısına.  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Sipariş ayrıntılarını gösteren bir DataGrid oluşturmak için  
  
1. İçinde **veri kaynakları** penceresinde bulun **SalesOrderDetails** alt düğümü **SalesOrderHeaders** düğümü.  
  
   > [!NOTE]
   >  Ayrıca bir **SalesOrderDetails** eşi olan düğümün **SalesOrderHeaders** düğümü. Alt düğüm seçtiğinizden emin olun **SalesOrderHeaders** düğümü.  
  
2. Alt genişletin **SalesOrderDetails** düğümü.  
  
3. Her biri aşağıdaki alt düğümleri için **SalesOrderDetails** düğümü, açılan menüsünün yanındaki düğümü tıklatın ve seçin **hiçbiri**:  
  
   - **SalesOrderID**  
  
   - **SalesOrderDetailID**  
  
   - **ROWGUID**  
  
   - **ModifiedDate**  
  
     Bu eylem, bu verileri dahil olmak üzere Visual Studio engeller <xref:System.Windows.Controls.DataGrid> sonraki adımda oluşturduğunuz denetimi. Bu kılavuz için son kullanıcı bu verileri görme gerekmez varsayılır.  
  
4. Gelen **veri kaynakları** penceresinde Alt sürükleyin **SalesOrderDetails** penceresinde düğüme **WPF Tasarımcısı**.  
  
    Visual Studio'nun oluşturduğu yeni bir veri bağlama tanımlamak için XAML <xref:System.Windows.Controls.DataGrid> denetimi ve denetimi Tasarımcısı'nda görünür. Visual Studio ayrıca güncellemeleri oluşturulan `GetSalesOrderHeadersQuery` verilerine dahil edilecek arka plan kod dosyasında yöntemini **SalesOrderDetails** varlık.  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Derleme ve siparişi kayıtlarını görüntülediğini doğrulamak için uygulamayı çalıştırın.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Tuşuna **F5**.  
  
     Uygulamayı derler ve çalıştırır. Aşağıdakileri doğrulayın:  
  
    -   **Satış siparişi kodu** birleşik giriş kutusu görüntüler **71774**. Bu varlıktaki ilk sırada kimliğidir.  
  
    -   Her siparişi için seçtiğiniz **satış siparişi kodu** Kombo kutusu ayrıntılı sipariş bilgilerini görüntülendiği <xref:System.Windows.Controls.DataGrid>.  
  
2.  Uygulamayı kapatın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzu tamamladıktan sonra nasıl kullanacağınızı öğrenin **veri kaynakları** WPF bağlama için Visual Studio penceresinde başka türde veri kaynaklarını denetler. Daha fazla bilgi için [denetimleri bir WCF veri hizmetine WPF bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) ve [bağlama WPF denetimlerini bir veri kümesine](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)