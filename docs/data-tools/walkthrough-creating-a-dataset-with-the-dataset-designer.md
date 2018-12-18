---
title: 'İzlenecek Yol: Veri Kümesi Tasarımcısı ile Veri Kümesi Oluşturma'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 32a093e59d918f34ddf5da9cbb5edb13c96b2777
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117933"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>İzlenecek yol: bir veri kümesi Tasarımcısı ile oluşturma

Bu kılavuzda, bir veri kümesini kullanarak oluşturduğunuz **veri kümesi Tasarımcısı**. Yeni proje oluşturma ve yeni bir ekleme işleminde size gereken makaleyi **DataSet** ona öğesi. Sihirbaz kullanmadan bir veritabanı tablolarında temel tabloları oluşturma öğreneceksiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda, SQL Server Express LocalDB ve Northwind örnek veritabanı kullanılır.

1.  SQL Server Express LocalDB yoksa, araçtan yüklemek [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. Visual Studio Yükleyicisi'nde, SQL Server Express LocalDB parçası olarak yüklenebilir **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2.  Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (SQL Server Nesne Gezgini parçası olarak yüklü **veri depolama ve işleme** Visual Studio yükleyicisi iş yükündeki.) Genişletme **SQL Server** düğümü. Yerel veritabanı örneğinde sağ tıklatıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresini açar.

    2. Kopya [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği sıfırdan Northwind veritabanı oluşturur ve veri ile doldurur.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu yürütme tamamlandıktan ve Northwind veritabanı oluşturulur.

## <a name="create-a-new-windows-forms-application-project"></a>Yeni bir Windows Forms uygulaması projesi oluşturma

1. Visual Studio'da üzerinde **dosya** menüsünde, select **yeni** > **proje**.

2. Genişletin **Visual C#** veya **Visual Basic** sol bölmesinde, ardından **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Proje adı **DatasetDesignerWalkthrough**ve ardından **Tamam**.

     Visual Studio projeye ekler **Çözüm Gezgini** ve yeni bir form tasarımcısında görüntüleyin.

## <a name="add-a-new-dataset-to-the-application"></a>Yeni bir veri kümesi için uygulama ekleme

1.  Üzerinde **proje** menüsünde, select **Yeni Öğe Ekle**.

     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

2.  Sol bölmede seçin **veri**seçeneğini belirleyip **DataSet** Orta bölmede.

3.  Veri kümesi adı **NorthwindDataset**ve ardından **Ekle**.

     Visual Studio ekler adlı bir dosya **NorthwindDataset.xsd** projeye ve bunun içinde açılacak **veri kümesi Tasarımcısı**.

## <a name="create-a-data-connection-in-server-explorer"></a>Sunucu Gezgini'nde bir veri bağlantısı oluştur

1.  Üzerinde **Görünüm** menüsünde tıklatın **Sunucu Gezgini**.

2.  İçinde **Sunucu Gezgini**, tıklatın **veritabanına bağlan** düğmesi.

3.  Northwind örnek veritabanı bağlantı oluşturun.

## <a name="create-the-tables-in-the-dataset"></a>Veri kümesini tabloları oluşturma

Bu bölümde, tablolar kümesine eklemek açıklanmaktadır.

### <a name="to-create-the-customers-table"></a>Müşteriler tablosu oluşturmak için

1.  Oluşturduğunuz veri bağlantısı genişletin **Sunucu Gezgini**, genişletin ve ardından **tabloları** düğümü.

2.  Sürükleme **müşteriler** tablosunda **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı**.

     A **müşteriler** veri tablosu ve **TableAdapter** kümesine eklenir.

### <a name="to-create-the-orders-table"></a>Siparişler tablosu oluşturmak için

-   Sürükleme **siparişleri** tablosunda **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı**.

     Bir **siparişleri** veri tablosu **OrdersTableAdapter**ve arasında veri ilişkisi **müşteriler** ve **siparişleri** tabloları eklenir veri kümesi.

### <a name="to-create-the-orderdetails-table"></a>Sipariş Ayrıntıları tablosu oluşturmak için

-   Sürükleme **sipariş ayrıntılarını** tablosunda **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı**.

     Bir **sipariş ayrıntılarını** veri tablosu **OrderDetailsTableAdapter**ve arasında veri ilişkisi **siparişleri** ve **sipariş ayrıntıları** tabloları veri kümesine eklenir.

## <a name="next-steps"></a>Sonraki Adımlar

-   Veri kümesi kaydedin.

-   Öğe seçin **veri kaynakları** penceresi ve bunları bir forma sürükleyin. Daha fazla bilgi için bkz: [bağlamak Windows Forms denetimleri Visual Studio'da verilere](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

-   Daha fazla sorguları TableAdapters ekleyin.

-   Doğrulama mantığı ekleyin <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> kümesindeki veri tabloları olaylar. Daha fazla bilgi için bkz: [veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Veri doğrulama](../data-tools/validate-data-in-datasets.md)