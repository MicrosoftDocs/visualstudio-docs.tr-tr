---
title: 'İzlenecek yol: bir veri kümesi Tasarımcısı ile oluşturma | Microsoft Docs'
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d77d63cc82b7af6281183b3eae67d09b0454fffb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868267"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>İzlenecek Yol: Veri Kümesi Tasarımcısı ile Veri Kümesi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda, kullanarak bir veri kümesi oluşturacaksınız **veri kümesi Tasarımcısı**. Yeni proje oluşturma ve yeni bir ekleme işleminde sürer **veri kümesi** ona öğesi. Sihirbaz kullanmadan bir veritabanındaki tabloları temel tablo oluşturulacağını öğreneceksiniz.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
- Yeni bir oluşturma **Windows uygulama** proje.  
  
- Boş bir ekleme **veri kümesi** projeye öğe.  
  
- Oluşturma ve bir veri kaynağı ile bir veri kümesi oluşturarak uygulamanızda yapılandırma **veri kümesi Tasarımcısı**.  
  
- Northwind veritabanına bir bağlantı oluşturma **Sunucu Gezgini**.  
  
- Tablo TableAdapter ile veritabanı tablolarında göre veri kümesinde oluşturma.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına (SQL Server veya Access sürümü) erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Yeni bir Windows uygulaması projesi oluşturma  
  
#### <a name="to-create-a-new-windows-application-project"></a>Yeni bir Windows uygulaması projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Bir programlama dili seçin **proje türleri** bölmesi.  
  
3.  Tıklayın **Windows uygulama** içinde **şablonları** bölmesi.  
  
4.  Projeyi adlandırın `DatasetDesignerWalkthrough`ve ardından **Tamam**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeye ekler **Çözüm Gezgini** ve yeni bir form Tasarımcısı'nda görüntüleyin.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Yeni bir veri kümesi için uygulama ekleme  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Projeye yeni bir veri kümesi öğe eklemek için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
2.  İçinde **şablonları** kutusunun **Yeni Öğe Ekle** iletişim kutusu, tıklayın **veri kümesi**.  
  
3.  Veri kümesi adı `NorthwindDataset`ve ardından **Ekle**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adlı bir dosya ekleyecektir **NorthwindDataset.xsd** projeye ve açılır **veri kümesi Tasarımcısı**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Sunucu Gezgini'nde bir veri bağlantısı oluşturma  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Northwind veritabanına bir bağlantı oluşturmak için  
  
1.  Üzerinde **görünümü** menüsünü tıklatın **Sunucu Gezgini**.  
  
2.  İçinde **Sunucu Gezgini**, tıklayın **veritabanına bağlan** düğmesi.  
  
3.  Northwind örnek veritabanına bağlantı oluşturun.  
  
    > [!NOTE]
    >  Northwind SQL Server veya Access sürümü bu izlenecek yol için bağlanabilirsiniz.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Tablo kümesinde oluşturma  
 Bu bölüm veri kümesi için tablo ekleme açıklanmaktadır.  
  
#### <a name="to-create-the-customers-table"></a>Müşteriler tablosu oluşturmak için  
  
1.  Oluşturduğunuz veri bağlantısı genişletin **Sunucu Gezgini**ve ardından **tabloları** düğümü.  
  
2.  Sürükleme **müşteriler** tablosunda **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı**.  
  
     A **müşteriler** veri tablosu ve **CustomersTableAdapter** veri kümesine eklenir.  
  
#### <a name="to-create-the-orders-table"></a>Siparişler tablosu oluşturmak için  
  
-   Sürükleme **siparişler** tablosunda **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı**.  
  
     Bir **siparişler** veri tablosu **orderstableadapter bağdaştırıcısına**ve arasında veri ilişkisi **müşteriler** ve **siparişler** tabloları eklenir veri kümesi.  
  
#### <a name="to-create-the-orderdetails-table"></a>OrderDetails tablo oluşturmak için  
  
-   Sürükleme **sipariş ayrıntıları** tablosunda **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı**.  
  
     Bir **sipariş ayrıntıları** veri tablosu **sipariş DetailsTableAdapter**ve arasında veri ilişkisi **siparişler** ve **sipariş ayrıntıları** tabloları veri kümesine eklenir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
### <a name="to-add-functionality-to-your-application"></a>Uygulamanıza işlev eklemek için  
  
-   Veri kümesini kaydetme.  
  
-   Öğe seçin **veri kaynakları** penceresi ve bunları formunuza sürükleyin. Daha fazla bilgi için [Visual Studio'da verilere Windows Forms bağlama denetimleri](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Daha fazla sorgular için TableAdapter'ları ekleyin. Daha fazla bilgi için [nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Doğrulama mantığı eklemenize <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> veri kümesindeki veri tablolarının olayları. Daha fazla bilgi için [veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)