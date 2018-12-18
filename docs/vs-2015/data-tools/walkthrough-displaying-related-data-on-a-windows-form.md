---
title: 'İzlenecek yol: Bir Windows formunda ilgili verileri görüntüleme | Microsoft Docs'
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 882c8229c105920efe247a54e9525a262e6a3246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282678"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>İzlenecek Yol: Bir Windows Formunda İlgili Verileri Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birçok uygulama senaryolarında birden fazla tablodan veri ve verilerin ne sıklıkla, ilgili tablolardan birlikte çalışmak istediğiniz. Diğer bir deyişle, bir üst-alt ilişkisi ile çalışmak istediğiniz. Örneğin, bir formu bir müşteri kaydı seçerek bu müşterinin siparişlerine burada görüntüler oluşturmak isteyebilirsiniz. İlgili kayıtlara formda görüntüleme elde edilir ayarlayarak <xref:System.Windows.Forms.BindingSource.DataSource%2A> alt özellik <xref:System.Windows.Forms.BindingSource> üst <xref:System.Windows.Forms.BindingSource> (alt tablo değil) ve ayarı <xref:System.Windows.Forms.BindingSource.DataMember%2A> alt özellik <xref:System.Windows.Forms.BindingSource> veri ilişkisine üst ve alt tablolar birbirine bağlar.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Oluşturma bir **Windows uygulama** proje.  
  
-   Oluşturma ve uygulamanızda bir veri kümesi yapılandırma temel alarak `Customers` ve `Orders` kullanarak Northwind veritabanı tabloları [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Verileri görüntülemek için denetimler ekleme `Customers` tablo.  
  
-   Görüntülemek için denetimler ekleme `Orders` temel alan `Customer`.  
  
-   Uygulamayı test etme farklı müşteriler seçme ve Seçilen müşteri için doğru siparişlerin görüntülendiğini doğrulama.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim. Örnek veritabanları kurulumu için bkz: [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama**.  
  
#### <a name="to-create-the-windows-application-project"></a>Windows uygulaması projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Projeyi adlandırın `RelatedDataWalkthrough`.  
  
3.  Seçin **Windows uygulama** tıklatıp **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **RelatedDataWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="creating-the-data-source"></a>Veri Kaynağı Oluşturma  
 Bu adımda dayalı bir veri kümesi oluşturulur `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar.  
  
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
  
8.  Seçin **müşteriler** ve **siparişler** tablolar ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve **müşteriler** tablo görünür **veri kaynakları** penceresi.  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Müşteriler Tablosundan Verileri Görüntülemek için Denetimler Oluşturma  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>Müşteri verilerini (üst kayıtlar) görüntülemek üzere denetimler oluşturmak için  
  
1.  İçinde **veri kaynakları** penceresinde **müşteriler** tablosunu ve ardından açılan oka tıklayın.  
  
2.  Seçin **ayrıntıları** menüsünde.  
  
3.  Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** üstüne penceresinden **Form1**.  
  
     Araç şeridi yanı sıra form üzerindeki verilere bağlı denetimler, tanımlayıcı etiketlerle görünür (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Siparişler Tablosundan Verileri Görüntülemek için Denetimler Oluşturma  
 ![Veri kaynakları penceresi ilişkisini gösteren](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>Her müşterinin (alt kayıtlar) siparişlerini görüntülemek üzere denetimler oluşturmak için  
  
-   İçinde **veri kaynakları** penceresini genişletin **müşteriler** düğüm ve son sütunu seçin **müşteriler** genişletilebilir bir tablo **siparişler** düğümünün altındaki sürükleyerek **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> form ve yeni eklenen <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) ve TableAdapter (`OrdersTableAdapter`) bileşen tepsisine eklenir.  
  
    > [!NOTE]
    >  Açık [Özellikler penceresi](../ide/reference/properties-window.md) seçip **OrdersBindingSource**. İnceleme <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> bağlamanın ilişkili kayıtları görüntüleyecek şekilde nasıl yapılandırıldığını görmek için özellikleri. <xref:System.Windows.Forms.BindingSource.DataSource%2A> Ayarlanır `CustomersBindingSource` (üst tablonun <xref:System.Windows.Forms.BindingSource>), yerine `Orders` tablo. <xref:System.Windows.Forms.BindingSource.DataMember%2A> Özelliği `FK_Orders_Customers`, adı olduğu <xref:System.Data.DataRelation> tabloları birlikte ilişkili nesne.  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
2.  Kullanarak farklı müşterileri seçin **CustomersBindingNavigator** doğrulamak için doğru siparişlerin görüntülenen <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak, ana ayrıntı formu oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bir geliştirmedir:  
  
-   Filtreleme `Customers` kayıtları için Parametreleştirme ekleyerek `Customers` tablo. Bunu yapmak için verileri görüntüleyen herhangi bir denetimi seçin `Customers` tablo akıllı etiket'i tıklatıp seçin **Sorgu Ekle**. Tamamlamak [arama ölçütleri derleyici iletişim kutusu](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d). Daha fazla bilgi için [nasıl yapılır: bir Windows Forms uygulamasına parametreli bir sorgu ekleme](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)   
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Nasıl yapılır: görüntü ilgili verileri bir Windows Forms uygulaması](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [BindingSource bileşenine genel bakış](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [BindingNavigator Denetimine Genel Bakış](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)