---
title: 'İzlenecek Yol: N Katmanlı Bir Veri Uygulaması Oluşturma'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 71c1c8dbaf34613d07ce29fa3f5e08d8e9c6961f
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305708"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>İzlenecek yol: n katmanlı veri uygulaması oluşturma
*N katmanlı* veri uygulamaları verilere erişen ve birden çok mantıksal katmana ayrılmış uygulamalarıdır veya *katmanları*. Uygulama bileşenlerini farklı katmanlara ayırmak uygulamanızın yönetilebilirliğini ve ölçeklenebilirliğini artırır. Bunu, tüm çözümü yeniden tasarlamanıza gerek kalmadan tek bir katmana uygulanabilen yeni teknolojilerin daha kolay benimsenmesini sağlayarak yapar. N katmanlı mimaride bir sunu katmanı, bir orta katman ve bir veri katmanı bulunur. Orta katmanda genellikle bir veri erişim katmanı, iş mantığı katmanı ve kimlik doğrulaması ve doğrulama gibi paylaşılan bileşenler bulunur. Veri katmanında ilişkisel bir veritabanı vardır. N katmanlı uygulamalar hassas bilgileri orta katmanın veri erişimi katmanında depolayarak sunu katmanına erişimi olan son kullanıcılardan uzakta tutulmasını sağlar. Daha fazla bilgi için [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md).

N katmanlı uygulamada çeşitli katmanları ayırma yollarından biri, uygulamanıza eklemek istediğiniz her katman için ayrı projeler oluşturmaktır. Türü belirtilmiş veri kümelerinde, üretilen veri kümesinin ve `DataSet Project` kodunun gitmesi gereken projeleri belirleyen bir `TableAdapter` özelliği bulunur.

Bu izlenecek yolda, veri kümesi nasıl ayrıldığı gösterilir ve `TableAdapter` kullanarak farklı sınıf kitaplığı projelerine koda **veri kümesi Tasarımcısı**. Veri kümesini ve TableAdapter kodunu ayırdıktan sonra oluşturduğunuz bir [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) hizmetinin veri erişim katmanına çağrı. Son olarak, sunu katmanı olarak bir Windows Forms uygulaması oluşturun. Bu katman veri hizmetindeki verilere erişir.

Bu kılavuz boyunca aşağıdaki adımları gerçekleştirin:

-   Birden çok proje içeren yeni bir n katmanlı çözüm oluşturma.

-   N katmanlı çözüme iki sınıf kitaplığı ekleme.

-   Kullanarak bir türü belirtilmiş veri kümesi oluşturma **veri kaynağı Yapılandırma Sihirbazı**.

-   Oluşturulan ayrı [TableAdapters](create-and-configure-tableadapters.md) ve veri kümesi kodunu farklı projelere.

-   Veri erişim katmanına çağrı göndermek için bir Windows Communication Foundation (WCF) hizmeti oluşturma.

-   Veri erişim katmanından veri almak için hizmet içinde işlevler oluşturma.

-   Sunu katmanı olarak hizmet verecek bir Windows Forms uygulaması oluşturma.

-   Veri kaynağına bağlanan Windows Forms denetimleri oluşturma.

-   Veri tablolarını doldurmak için kod yazma.

![video bağlantısı](../data-tools/media/playvideo.gif) bu konunun video sürümü için bkz: [Video nasıl yapılır: bir n katmanlı veri uygulaması oluşturma](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Önkoşullar
Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **.NET Masaüstü geliştirmesinden** iş yükü veya tek bir bileşen olarak.

2. Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (**SQL Server Nesne Gezgini** parçası olarak yüklenen **veri depolama ve işleme** iş yükünü Visual Studio Yükleyicisi'nde.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>(DataEntityTier) veri kümesini tutacak n katmanlı çözüm ve sınıf kitaplığı oluşturma
 Bu kılavuzun ilk adımı bir çözüm ve iki sınıf kitaplığı projesi oluşturmaktır. Birinci sınıf kitaplığı veri kümesini tutar (oluşturulan yazılan `DataSet` sınıfı ve uygulama verilerini tutacak DataTable). Bu proje uygulamanın veri varlık katmanı olarak kullanılır ve genellikle orta katmanda bulunur. Veri kümesi, ilk veri kümesi oluşturur ve otomatik olarak kod iki sınıf kitaplığına ayırır.

> [!NOTE]
> Tıklamadan önce projeyi ve çözümü doğru adlandırdığınızdan emin olun **Tamam**. Böylece bu kılavuzu tamamlamanız kolaylaşır.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>N katmanlı çözüm ve DataEntityTier sınıf kitaplığı oluşturmak için

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#**  veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **sınıf kitaplığı** proje türü.

4. Projeyi adlandırın **DataEntityTier**.

5. Çözüm adı **NTierWalkthrough**ve ardından **Tamam**.

     DataEntityTier projesini içeren bir NTierWalkthrough çözümü oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>(DataAccessTier) TableAdapter bağdaştırıcılarını tutacak sınıf kitaplığı oluşturma
 DataEntityTier projesini oluşturduktan sonraki adım başka bir sınıf kitaplığı projesi oluşturmaktır. Bu proje oluşturulan TableAdapter bağdaştırıcılarını tutar ve çağrılır *veri erişim katmanında* uygulama. Veri erişim katmanında, veritabanına bağlanmak için gereken bilgiler bulunur ve genelde orta katmanda yer alır.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>TableAdapter'ları için ayrı bir sınıf kitaplığı oluşturmak için

1. Çözüme sağ **Çözüm Gezgini** ve **Ekle** > **yeni proje**.

2. İçinde **yeni proje** Orta bölmede, Seç iletişim kutusu **sınıf kitaplığı**.

3. Projeyi adlandırın **DataAccessTier** ve **Tamam**.

     DataAccessTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="create-the-dataset"></a>Veri kümesi oluşturma
 Sonraki adım türü belirtilmiş bir veri kümesi oluşturmaktır. Türü belirtilmiş veri kümeleri, her iki veri kümesi sınıfıyla oluşturulur (dahil olmak üzere `DataTables` sınıflar) ve `TableAdapter` tek bir projede sınıfları. (Tüm sınıflar tek dosyada oluşturulur.) Veri kümesi ve TableAdapters öğelerini farklı projelere ayırdığınızda, bırakarak diğer projeye taşınır dataset sınıfı olduğu `TableAdapter` sınıfları özgün projede. Bu nedenle, veri kümesini sonuçta (DataAccessTier projesi) TableAdapter bağdaştırıcılarını içerecek projede oluşturun. Kullanarak bir veri kümesi oluşturma **veri kaynağı Yapılandırma Sihirbazı**.

> [!NOTE]
> Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: örnek veritabanları yükleme](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1. Seçin **DataAccessTier** içinde **Çözüm Gezgini**.

2. Üzerinde **veri** menüsünde **veri kaynaklarını Göster**.

   **Veri kaynakları** penceresi açılır.

3. İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.

4. Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı** seçip **sonraki**.

5. Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdaki eylemlerden birini gerçekleştirin:

     Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

     veya

     Seçin **yeni bağlantı** açmak için **Bağlantı Ekle** iletişim kutusu.

6. Veritabanına parola gerekiyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.

    > [!NOTE]
    > Bir yerel veritabanı dosyası (SQL Server'a bağlanmak yerine) seçtiyseniz projeye dosya eklemek isteyip istemediğiniz sorulabilir. Seçin **Evet** veritabanı dosyası projeye eklenecek.

7. Seçin **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.

8. Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.

9. Onay kutularını işaretleyin **müşteriler** ve **siparişler** tabloları ve ardından **son**.

     NorthwindDataSet DataAccessTier projesine eklenir ve görünür **veri kaynakları** penceresi.

## <a name="separate-the-tableadapters-from-the-dataset"></a>TableAdapter bağdaştırıcılarını veri kümesinden ayırmak.
 Veri kümesi oluşturduktan sonra, üretilen veri kümesi sınıfını TableAdapter bağdaştırıcılarından ayırın. Ayarlayarak bunu **DataSet projesi** özelliğini ayrılmış veri kümesi sınıfını depolayacak projenin adı.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>TableAdapter Bağdaştırıcılarını Veri Kümesinden ayırmak için

1. Çift **NorthwindDataSet.xsd** içinde **Çözüm Gezgini** açmak için **veri kümesi Tasarımcısı**.

2. Tasarımcı üzerinde boş bir alanı seçin.

3. Bulun **DataSet projesi** düğümünde **özellikleri** penceresi.

4. İçinde **DataSet projesi** listesinden **DataEntityTier**.

5. Üzerinde **derleme** menüsünde **Çözümü Derle**.

   Veri kümesi ve TableAdapter bağdaştırıcıları iki sınıf kitaplığı projesine ayrılır. Başlangıçta tüm veri kümesini içeren proje (`DataAccessTier`) şimdi yalnızca TableAdapter bağdaştırıcıları içerir. Proje **DataSet projesi** özelliği (`DataEntityTier`) türü belirtilmiş veri kümesi içerir: *NorthwindDataSet.Dataset.Designer.vb* (veya  *NorthwindDataSet.Dataset.Designer.cs*).

> [!NOTE]
> Veri kümelerini ve TableAdapter bağdaştırıcılarını ayırdığınızda (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları taşınmaz otomatik olarak. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

## <a name="create-a-new-service-application"></a>Yeni bir hizmet uygulaması oluşturma
Bu izlenecek yol, bir WCF hizmetini kullanarak veri erişim katmanında erişmek için bu nedenle şimdi yeni bir WCF hizmeti uygulaması oluşturma gösterilmektedir.

### <a name="to-create-a-new-wcf-service-application"></a>Yeni bir WCF Hizmeti uygulaması oluşturmak için

1. Çözüme sağ **Çözüm Gezgini** ve **Ekle** > **yeni proje**.

2. İçinde **yeni proje** iletişim kutusunda, sol bölmesinde, **WCF**. Orta bölmede seçin **WCF hizmet Kitaplığı**.

3. Projeyi adlandırın **DataService** seçip **Tamam**.

     DataService projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Müşteriler ve siparişler verileri döndürmek için veri erişim katmanında yöntemler oluşturma
 Veri hizmetinin veri erişim katmanında iki yöntem çağırmak sahiptir: `GetCustomers` ve `GetOrders`. Bu yöntemler Northwind döndürür `Customers` ve `Orders` tablolar. Oluşturma `GetCustomers` ve `GetOrders` yöntemleri `DataAccessTier` proje.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Veri erişim katmanında Customers tablosunu döndüren bir yöntem oluşturmak için

1. İçinde **Çözüm Gezgini**, çift **NorthwindDataset.xsd** veri kümesini açın.

2. Sağ **CustomersTableAdapter** tıklatıp **Sorgu Ekle**.

3. Üzerinde **komut türü seçin** sayfasında, varsayılan değerini bırakın **SQL deyimi kullan** tıklatıp **sonraki**.

4. Üzerinde **bir sorgu türü seçin** sayfasında, varsayılan değerini bırakın **satır döndüren SELECT** tıklatıp **sonraki**.

5. Üzerinde **bir SQL SELECT deyimi belirtin** sayfasında varsayılan sorguyu bırakın ve tıklayın **sonraki**.

6. Üzerinde **oluşturmak için yöntemlerini seçin** sayfasında **GetCustomers** için **yöntem adı** içinde **DataTable Döndür** bölümü.

7. **Son**'a tıklayın.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Veri erişim katmanında Orders tablosunu döndüren bir yöntem oluşturmak için

1. Sağ **orderstableadapter bağdaştırıcısına** tıklatıp **Sorgu Ekle**.

2. Üzerinde **komut türü seçin** sayfasında, varsayılan değerini bırakın **SQL deyimi kullan** tıklatıp **sonraki**.

3. Üzerinde **bir sorgu türü seçin** sayfasında, varsayılan değerini bırakın **satır döndüren SELECT** tıklatıp **sonraki**.

4. Üzerinde **bir SQL SELECT deyimi belirtin** sayfasında varsayılan sorguyu bırakın ve tıklayın **sonraki**.

5. Üzerinde **oluşturmak için yöntemlerini seçin** sayfasında **GetOrders** için **yöntem adı** içinde **DataTable Döndür** bölümü.

6. **Son**'a tıklayın.

7. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Veri varlığı için başvuru ve veri erişimi katmanlarına veri hizmetine ekleme
 Veri hizmetinin veri kümesinden ve TableAdapter bağdaştırıcıları bilgi gerektirdiğinden, başvuruları eklemek **DataEntityTier** ve **DataAccessTier** projeleri.

### <a name="to-add-references-to-the-data-service"></a>Veri hizmetine başvuru eklemek için

1. Sağ **DataService** içinde **Çözüm Gezgini** tıklatıp **Başvuru Ekle**.

2. Tıklayın **projeleri** sekmesinde **Başvuru Ekle** iletişim kutusu.

3. Her ikisini de seçin **DataAccessTier** ve **DataEntityTier** projeleri.

4. **Tamam**'ı tıklatın.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Veri erişim katmanında GetCustomers ve GetOrders yöntemlerini çağırmak için hizmete işlev ekleme
 Şimdi veri erişim katmanında veri döndürme yöntemleri bulunduğuna göre, veri erişim katmanındaki yöntemleri çağırmak için veri hizmetinde yöntemler oluşturun.

> [!NOTE]
> C# projelerinde aşağıdaki kodu derlemek için `System.Data.DataSetExtensions` derlemesine bir başvuru eklemeniz gerekir.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Veri hizmetinde GetCustomers ve GetOrders işlevlerini oluşturmak için

1. İçinde **DataService** proje, çift **Iservice1.vb** veya **Iservice1.cs**.

2. Altında aşağıdaki kodu ekleyin **hizmet işlemlerinizi buraya ekleyin** açıklaması:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3. DataService projesinde çift **Service1.vb** (veya **Service1.cs**).

4. Aşağıdaki kodu ekleyin **Service1** sınıfı:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Veri hizmetinden verileri görüntülemek için bir sunu katmanı oluşturma
 Çözüm içeriyor artık daha verileri çağıran yöntemleri veri hizmetine erişim katmanı, veri hizmetine çağrı yapan başka bir proje oluşturun ve verileri kullanıcılara sunacak. Bu kılavuz için bir Windows Forms uygulaması oluşturun; bu n katmanlı uygulamanın sunu katmanıdır.

### <a name="to-create-the-presentation-tier-project"></a>Sunu katmanı projesi oluşturmak için

1. Çözüme sağ **Çözüm Gezgini** ve **Ekle** > **yeni proje**.

2. İçinde **yeni proje** iletişim kutusunda, sol bölmesinde, **Windows Masaüstü**. Orta bölmede seçin **Windows Forms uygulaması**.

3. Projeyi adlandırın **PresentationTier** tıklatıp **Tamam**.

    PresentationTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>PresentationTier projesini başlangıç projesi olarak ayarla
Biz belirleyeceğim **PresentationTier** sunan ve verilerle etkileşime giren gerçek istemci uygulaması olduğundan çözüm için başlangıç projesi olarak proje.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Yeni sunu katmanı projesini başlangıç projesi olarak ayarlamak için

-   İçinde **Çözüm Gezgini**, sağ **PresentationTier** tıklatıp **başlangıç projesi olarak ayarla**.

## <a name="add-references-to-the-presentation-tier"></a>Sunu katmanına başvuru ekleme
 İstemci uygulaması, hizmetteki yöntemlere erişmek için bir veri hizmetine hizmet başvurusu PresentationTier gerektirir. Buna ek olarak, WCF hizmeti tür paylaşımını etkinleştirmek için veri kümesine bir başvuru gerektirir. Veri hizmeti aracılığıyla tür paylaşımı etkinleştirilinceye kadar kısmi veri kümesi sınıfına eklenen kod sunu katmanı kullanılamıyor. Satır ve sütun değişikliği olaylarını veri tablosunun bir doğrulama kodu gibi bir kod genellikle eklediğinden bu kodu istemcisinden erişmek isteyeceksiniz olasıdır.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Sunu katmanına bir başvuru eklemek için

1. İçinde **Çözüm Gezgini**, sağ **PresentationTier** seçip **Başvuru Ekle**.

2. İçinde **Başvuru Ekle** iletişim kutusunda **projeleri** sekmesi.

3. Seçin **DataEntityTier** ve **Tamam**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Sunu katmanına bir hizmet başvurusu eklemek için

1. İçinde **Çözüm Gezgini**, sağ **PresentationTier** seçip **hizmet Başvurusu Ekle**.

2. İçinde **hizmet Başvurusu Ekle** iletişim kutusunda **bulma**.

3. Seçin **Service1** ve **Tamam**.

    > [!NOTE]
    > Geçerli bilgisayarda birden çok hizmeti varsa, bu kılavuzda daha önce oluşturduğunuz hizmeti seçin (içeren hizmete `GetCustomers` ve `GetOrders` yöntemleri).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Veri hizmetinin döndürdüğü verileri görüntülemek için forma DataGridView görünümleri ekleme
 Veri hizmetine hizmet başvurusunu ekledikten sonra **veri kaynakları** penceresi hizmet tarafından döndürülen verilerle otomatik olarak doldurulur.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Forma iki DataGridView veri bağlama öğesi eklemek için

1. İçinde **Çözüm Gezgini**seçin **PresentationTier** proje.

2. İçinde **veri kaynakları** penceresini genişletin **NorthwindDataSet** bulun **müşteriler** düğümü.

3. Sürükleme **müşteriler** düğümünü Form1 üzerine.

4. İçinde **veri kaynakları** penceresinde genişletin **müşteriler** düğüm ve ilgili bulun **siparişler** düğümü ( **siparişler** düğümüyle içindeiçiçegeçmiş **Müşteriler** düğümü).

5. İlgili sürükleyin **siparişler** düğümünü Form1 üzerine.

6. Formda boş bir alanı çift tıklayarak bir `Form1_Load` olay işleyicisi oluşturun.

7. Aşağıdaki kodu ekleyin `Form1_Load` olay işleyicisi.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Hizmet tarafından izin verilen en büyük ileti boyutunu artırma
İçin varsayılan değer `maxReceivedMessageSize` hizmetinden alınan verileri tutabilecek kadar büyük değil `Customers` ve `Orders` tablolar. Aşağıdaki adımlarda değeri 6553600 artırırsınız. Hizmet başvurusu otomatik olarak güncelleştirir istemcide değerini değiştirin.

> [!NOTE]
> Varsayılan alt sınır boyutu hizmet reddi (DoS) saldırılarına maruz kalmayı sınırlamak içindir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>MaxReceivedMessageSize değerini artırmak için

1. İçinde **Çözüm Gezgini**, çift **app.config** dosyası **PresentationTier** proje.

2. Bulun **maxReceivedMessage** boyut özniteliğini ve bir değerle değiştirmek `6553600`.

## <a name="test-the-application"></a>Uygulamayı test etme
Tuşlarına basarak uygulamayı çalıştırmak **F5**. Verilerden `Customers` ve `Orders` tabloları veri hizmetinden alınır ve formda görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar
 Uygulama gereksinimlerinize bağlı olarak, Windows tabanlı bir uygulama içinde ilgili verileri kaydettikten sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Örneğin, bu uygulamada aşağıdaki geliştirmeleri yapabilirsiniz:

-   Veri kümesine doğrulama ekleme.

-   Verileri tekrar veritabanında güncelleştirmek için hizmete ek yöntemler ekleme.

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı uygulamalarda veri kümeleriyle çalışma](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)