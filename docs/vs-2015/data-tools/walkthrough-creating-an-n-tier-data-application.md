---
title: 'İzlenecek yol: bir N katmanlı veri uygulaması oluşturma | Microsoft Docs'
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
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 37876502a464e263ebd6803216b29bd62b65af5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890185"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>İzlenecek Yol: N Katmanlı Bir Veri Uygulaması Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
N-katmanı * veri uygulamaları verilere erişen ve birden çok mantıksal katmana ayrılmış uygulamalarıdır veya *katmanları*. Uygulama bileşenlerini farklı katmanlara ayırmak uygulamanızın yönetilebilirliğini ve ölçeklenebilirliğini artırır. Bunu, tüm çözümü yeniden tasarlamanıza gerek kalmadan tek bir katmana uygulanabilen yeni teknolojilerin daha kolay benimsenmesini sağlayarak yapar. N katmanlı mimaride bir sunu katmanı, bir orta katman ve bir veri katmanı bulunur. Orta katmanda genellikle bir veri erişim katmanı, iş mantığı katmanı ve kimlik doğrulaması ve doğrulama gibi paylaşılan bileşenler bulunur. Veri katmanında ilişkisel bir veritabanı vardır. N katmanlı uygulamalar hassas bilgileri orta katmanın veri erişimi katmanında depolayarak sunu katmanına erişimi olan son kullanıcılardan uzakta tutulmasını sağlar. Daha fazla bilgi için [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md).  
  
 N katmanlı uygulamada çeşitli katmanları ayırma yollarından biri, uygulamanıza eklemek istediğiniz her katman için ayrı projeler oluşturmaktır. Türü belirtilmiş veri kümelerinde, üretilen veri kümesinin ve `DataSet Project` kodunun gitmesi gereken projeleri belirleyen bir `TableAdapter` özelliği bulunur.  
  
 Bu izlenecek yolda, veri kümesi nasıl ayrıldığı gösterilir ve `TableAdapter` kullanarak farklı sınıf kitaplığı projelerine koda **veri kümesi Tasarımcısı**. Veri kümesini ve TableAdapter kodunu ayırdıktan sonra oluşturacağınız bir [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) hizmetinin veri erişim katmanına çağrı. Son olarak, sunu katmanı olarak bir Windows Forms uygulaması oluşturacaksınız. Bu katman veri hizmetindeki verilere erişir.  
  
 Bu kılavuzda aşağıdaki adımları gerçekleştireceksiniz:  
  
- Birden fazla proje içeren yeni bir n katmanlı çözüm oluşturma.  
  
- N katmanlı çözüme iki sınıf kitaplığı ekleme.  
  
- Kullanarak bir türü belirtilmiş veri kümesi oluşturma **veri kaynağı Yapılandırma Sihirbazı**.  
  
- Oluşturulan ayrı [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) ve veri kümesi kodunu farklı projelere.  
  
- Veri erişim katmanına çağrı göndermek için bir Windows Communication Foundation (WCF) hizmeti oluşturma.  
  
- Veri erişim katmanından veri almak için hizmet içinde işlevler oluşturma.  
  
- Sunu katmanı olarak hizmet verecek bir Windows Forms uygulaması oluşturma.  
  
- Veri kaynağına bağlanan Windows Forms denetimleri oluşturma.  
  
- Veri tablolarını doldurmak için kod yazma.  
  
  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") bu konunun video sürümü için bkz: [Video nasıl yapılır: bir N katmanlı veri uygulaması oluşturma](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekenler:  
  
-   Northwind örnek veritabanına erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Veri Kümesini Tutacak N Katmanlı Çözüm ve Sınıf Kitaplığı Oluşturma (DataEntityTier)  
 Bu kılavuzun ilk adımı bir çözüm ve iki sınıf kitaplığı projesi oluşturmaktır. Birinci sınıf kitaplığı veri kümesini tutacaktır (uygulama verilerini tutacak, üretilen türü belirtilmiş DataSet sınıfı ve DataTable tabloları). Bu proje uygulamanın veri varlık katmanı olarak kullanılır ve genellikle orta katmanda bulunur. [Oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md) ilk veri kümesini oluşturmak ve otomatik olarak kod iki sınıf kitaplığına ayırmak için kullanılır.  
  
> [!NOTE]
>  Tıklamadan önce projeyi ve çözümü doğru adlandırdığınızdan emin olun **Tamam**. Böylece bu kılavuzu tamamlamanız kolaylaşır.  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>N katmanlı çözüm ve DataEntityTier sınıf kitaplığı oluşturmak için  
  
1.  Gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
    > [!NOTE]
    >  **Veri kümesi Tasarımcısı** desteklenir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ve C# projeleri. Yeni projeyi bu dillerden birinde oluşturun.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde tıklayın **Windows**.  
  
3.  Tıklayın **sınıf kitaplığı** şablonu.  
  
4.  Projeyi adlandırın **DataEntityTier**.  
  
5.  Çözüm adı **NTierWalkthrough**.  
  
6.  **Tamam**'ı tıklatın.  
  
     DataEntityTier projesini içeren bir NTierWalkthrough çözümü oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>TableAdapter Bağdaştırıcılarını Tutacak Sınıf Kitaplığı Oluşturma (DataAccessTier)  
 DataEntityTier projesini oluşturduktan sonraki adım başka bir sınıf kitaplığı projesi oluşturmaktır. Bu proje oluşturulan tutacak `TableAdapter`s ve çağrılır *veri erişim katmanında* uygulama. Veri erişim katmanında, veritabanına bağlanmak için gereken bilgiler bulunur ve genelde orta katmanda yer alır.  
  
#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>TableAdapter bağdaştırıcılarına yönelik yeni sınıf kitaplığı oluşturmak için  
  
1.  Gelen **dosya** menüsünden NTierWalkthrough çözümüne yeni bir proje ekleyin.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **şablonları** bölmesinde tıklayın **sınıf kitaplığı**.  
  
3.  Projeyi adlandırın **DataAccessTier** tıklatıp **Tamam**.  
  
     DataAccessTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.  
  
## <a name="creating-the-dataset"></a>Veri Kümesi Oluşturma  
 Sonraki adım türü belirtilmiş bir veri kümesi oluşturmaktır. Türü belirtilmiş veri kümeleri, her iki veri kümesi sınıfıyla (DataTable sınıfları dahil) ve `TableAdapter` sınıflarıyla tek bir projede oluşturulur. (Tüm sınıflar tek dosyada oluşturulur.) Veri kümesini ve `TableAdapter` bağdaştırıcılarını farklı projelere ayırdığınızda veri kümesi sınıfı diğer projeye taşınır, `TableAdapter` sınıfları özgün projede kalır. Bu nedenle, veri kümesini sonuçta `TableAdapter` bağdaştırıcılarını içerecek projede oluşturun (DataAccessTier projesi). Kullanarak bir veri kümesi oluşturacaksınız **veri kaynağı Yapılandırma Sihirbazı**.  
  
> [!NOTE]
>  Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma  
  
1.  DataAccessTier olarak tıklayın **Çözüm Gezgini**.  
  
2.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
3.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
4.  Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı** ve ardından **sonraki**.  
  
5.  Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdaki eylemlerden birini gerçekleştirin:  
  
     Northwind örnek veritabanıyla kurulan veri bağlantısı açılan listede kullanılabilir durumdaysa bu bağlantıya tıklayın.  
  
     veya  
  
     Tıklayın **yeni bağlantı** açmak için **Bağlantı Ekle** iletişim kutusu.  
  
6.  Veritabanına parola gerekiyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
    > [!NOTE]
    >  Bir yerel veritabanı dosyası (SQL Server'a bağlanmak yerine) seçtiyseniz projeye dosya eklemek isteyip istemediğiniz sorulabilir. Tıklayın **Evet** veritabanı dosyası projeye eklenecek.  
  
7.  Tıklayın **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.  
  
8.  Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.  
  
9. Onay kutularına **müşteriler** ve **siparişler** tablolar ve ardından **son**.  
  
     NorthwindDataSet DataAccessTier projesine eklenir ve görünür **veri kaynakları** penceresi.  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>TableAdapter Bağdaştırıcılarını Veri Kümesinden Ayırma  
 Veri kümesi oluşturduktan sonra, üretilen veri kümesi sınıfını TableAdapter bağdaştırıcılarından ayırın. Ayarlayarak bunu **DataSet projesi** özelliğini ayrılmış veri kümesi sınıfını depolayacak projenin adı.  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>TableAdapter Bağdaştırıcılarını Veri Kümesinden ayırmak için  
  
1. Çift **NorthwindDataSet.xsd** içinde **Çözüm Gezgini** açmak için **veri kümesi Tasarımcısı**.  
  
2. Tasarımcı üzerinde boş bir alana tıklayın.  
  
3. Bulun **DataSet projesi** düğümünde **özellikleri** penceresi.  
  
4. İçinde **DataSet projesi** listesinde **DataEntityTier**.  
  
5. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
   Veri kümesi ve TableAdapter bağdaştırıcıları iki sınıf kitaplığı projesine ayrılır. Başlangıçta tüm veri kümesini (DataAccessTier) içeren projede şimdi yalnızca TableAdapter bağdaştırıcıları bulunur. Proje **DataSet projesi** özelliği (DataEntityTier) türü belirtilmiş veri kümesi içerir: NorthwindDataSet.Dataset.Designer.vb (veya NorthwindDataSet.Dataset.Designer.cs).  
  
> [!NOTE]
>  Veri kümelerini ve TableAdapter bağdaştırıcılarını ayırdığınızda (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları taşınmaz otomatik olarak. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.  
  
## <a name="creating-a-new-service-application"></a>Yeni Hizmet Uygulaması Oluşturma  
 Bu kılavuz bir WCF hizmetini kullanarak veri erişim katmanına nasıl erişileceğini gösterdiğinden yeni bir WCF hizmeti uygulaması oluşturun.  
  
#### <a name="to-create-a-new-wcf-service-application"></a>Yeni bir WCF Hizmeti uygulaması oluşturmak için  
  
1.  Gelen **dosya** menüsünden NTierWalkthrough çözümüne yeni bir proje ekleyin.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde tıklayın **WCF**. İçinde **şablonları** bölmesinde tıklayın **WCF hizmet Kitaplığı**.  
  
3.  Projeyi adlandırın **DataService** tıklatıp **Tamam**.  
  
     DataService projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Müşteri ve Sipariş Verilerini Döndürmek İçin Veri Erişim Katmanında Yöntemler Oluşturma  
 Veri hizmetinin veri erişim katmanında iki yöntem çağırması gerekir: GetCustomers ve GetOrders. Bu yöntemler Northwind Customers ve Orders tablolarını döndürür. DataAccessTier projesinde GetCustomers ve GetOrders yöntemlerini oluşturun.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Veri erişim katmanında Customers tablosunu döndüren bir yöntem oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, açmak için northwindDataSet.XSD'ye çift [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md).  
  
2.  CustomersTableAdapter sağ tıklatıp **Sorgu Ekle** açmak için [TableAdapters düzenleme](../data-tools/editing-tableadapters.md).  
  
3.  Üzerinde **komut türü seçin** sayfasında, varsayılan değerini bırakın **SQL deyimi kullan** tıklatıp **sonraki**.  
  
4.  Üzerinde **bir sorgu türü seçin** sayfasında, varsayılan değerini bırakın **satır döndüren SELECT** tıklatıp **sonraki**.  
  
5.  Üzerinde **bir SQL SELECT deyimi belirtin** sayfasında varsayılan sorguyu bırakın ve tıklayın **sonraki**.  
  
6.  Üzerinde **oluşturmak için yöntemlerini seçin** sayfasında **GetCustomers** için **yöntem adı** içinde **DataTable Döndür** bölümü.  
  
7.  **Son**'a tıklayın.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Veri erişim katmanında Orders tablosunu döndüren bir yöntem oluşturmak için  
  
1.  Orderstableadapter bağdaştırıcısına sağ tıklatıp **Sorgu Ekle**.  
  
2.  Üzerinde **komut türü seçin** sayfasında, varsayılan değerini bırakın **SQL deyimi kullan** tıklatıp **sonraki**.  
  
3.  Üzerinde **bir sorgu türü seçin** sayfasında, varsayılan değerini bırakın **satır döndüren SELECT** tıklatıp **sonraki**.  
  
4.  Üzerinde **bir SQL SELECT deyimi belirtin** sayfasında varsayılan sorguyu bırakın ve tıklayın **sonraki**.  
  
5.  Üzerinde **oluşturmak için yöntemlerini seçin** sayfasında **GetOrders** için **yöntem adı** içinde **DataTable Döndür** bölümü.  
  
6.  **Son**'a tıklayın.  
  
7.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Veri Hizmetinin Veri Varlığı ve Veri Erişimi Katmanlarına Başvuru Ekleme  
 Veri hizmetinin veri kümesinden ve TableAdapter bağdaştırıcılarından bilgi alması gerektiğinden DataEntityTier ve DataAccessTier projelerine başvurular ekleyin.  
  
#### <a name="to-add-references-to-the-data-service"></a>Veri hizmetine başvuru eklemek için  
  
1.  DataService olarak sağ **Çözüm Gezgini** tıklatıp **Başvuru Ekle**.  
  
2.  Tıklayın **projeleri** sekmesinde **Başvuru Ekle** iletişim kutusu.  
  
3.  Her ikisini de seçin **DataAccessTier** ve **DataEntityTier** projeleri.  
  
4.  **Tamam**'ı tıklatın.  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Veri Erişim Katmanındaki GetCustomers ve GetOrder Yöntemlerini Çağırmak İçin Hizmete İşlev Ekleme  
 Şimdi veri erişim katmanında veri döndürme yöntemleri bulunduğuna göre, veri erişim katmanındaki yöntemleri çağırmak için veri hizmetinde yöntemler oluşturun.  
  
> [!NOTE]
>  C# projelerinde aşağıdaki kodu derlemek için `System.Data.DataSetExtensions` derlemesine bir başvuru eklemeniz gerekir.  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Veri hizmetinde GetCustomers ve GetOrders işlevlerini oluşturmak için  
  
1.  İçinde **DataService** proje, Iservice1.vb veya Iservice1.cs öğesine çift tıklayın.  
  
2.  Altında aşağıdaki kodu ekleyin **hizmet işlemlerinizi buraya ekleyin** açıklaması:  
  
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
  
3.  DataService projesinde Service1.vb (veya Service1.cs) öğesine çift tıklayın.  
  
4.  Aşağıdaki kodu Service1 sınıfına ekleyin:  
  
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
  
5.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Veri Hizmetinden Verileri Görüntülemek İçin Bir Sunu Katmanı Oluşturma  
 Şimdi çözümde veri erişim katmanına çağrı gönderen yöntemler bulunduğuna göre, veri hizmetine çağrı gönderecek ve verileri kullanıcılara sunacak başka bir proje oluşturun. Bu kılavuz için bir Windows Forms uygulaması oluşturun; bu n katmanlı uygulamanın sunu katmanıdır.  
  
#### <a name="to-create-the-presentation-tier-project"></a>Sunu katmanı projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünden NTierWalkthrough çözümüne yeni bir proje ekleyin.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde tıklayın **Windows**. İçinde **şablonları** bölmesinde tıklayın **Windows Forms uygulaması**.  
  
3.  Projeyi adlandırın **PresentationTier** tıklatıp **Tamam**.  
  
4.  PresentationTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>PresentationTier Projesini Başlangıç Projesi Olarak Ayarlama  
 Sunu katmanı verileri sunmak ve verilerle etkileşimde bulunmak için kullanılan gerçek istemci uygulaması olduğundan PresentationTier projesini Başlangıç projesi olarak ayarlamanız gerekir.  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Yeni sunu katmanı projesini Başlangıç projesi olarak ayarlamak için  
  
-   İçinde **Çözüm Gezgini**, sağ **PresentationTier** tıklatıp **başlangıç projesi olarak ayarla**.  
  
## <a name="adding-references-to-the-presentation-tier"></a>Sunu Katmanına Başvuru Ekleme  
 PresentationTier istemci uygulaması, hizmetteki yöntemlere erişmek için veri hizmetine yönelik bir hizmet başvurusu gerektirir. Buna ek olarak, WCF hizmeti tür paylaşımını etkinleştirmek için veri kümesine bir başvuru gerektirir. Veri hizmeti aracılığıyla tür paylaşımı etkinleştirilinceye kadar kısmi veri kümesi sınıfına eklenen kod sunu katmanı tarafından kullanılamaz. Genelde veri tablosundaki satır ve sütun değişikliği olaylarını doğrulama gibi bir kod ekleyeceğiniz için büyük olasılıkla bu koda istemcisinden erişmek isteyeceksiniz.  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Sunu katmanına bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, PresentationTier sağ tıklatıp **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **projeleri** sekmesi.  
  
3.  Seçin **DataEntityTier** tıklatıp **Tamam**.  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Sunu katmanına bir hizmet başvurusu eklemek için  
  
1.  İçinde **Çözüm Gezgini**, PresentationTier sağ tıklatıp **hizmet Başvurusu Ekle**.  
  
2.  İçinde **hizmet Başvurusu Ekle** iletişim kutusu, tıklayın **bulma**.  
  
3.  Seçin **Service1** tıklatıp **Tamam**.  
  
    > [!NOTE]
    >  Geçerli bilgisayarda birden çok hizmetiniz varsa, bu kılavuzda önceden oluşturduğunuz hizmeti seçin (GetCustomers ve GetOrders yöntemlerini içeren hizmet).  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Veri Hizmetinin Döndürdüğü Verileri Görüntülemek İçin Forma DataGridView Görünümleri Ekleme  
 Veri hizmetine hizmet başvurusunu ekledikten sonra **veri kaynakları** penceresi hizmet tarafından döndürülen verilerle otomatik olarak doldurulur.  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Forma iki DataGridView veri bağlama öğesi eklemek için  
  
1.  İçinde **Çözüm Gezgini**, PresentationTier projesini seçin.  
  
2.  İçinde **veri kaynakları** penceresini genişletin **NorthwindDataSet** bulun **müşteriler** düğümü.  
  
3.  Sürükleme **müşteriler** düğümünü Form1 üzerine.  
  
4.  İçinde **veri kaynakları** penceresinde genişletin **müşteriler** düğüm ve ilgili bulun **siparişler** düğümü ( **siparişler** düğümüyle içindeiçiçegeçmiş **Müşteriler** düğümü).  
  
5.  İlgili sürükleyin **siparişler** düğümünü Form1 üzerine.  
  
6.  Formda boş bir alanı çift tıklayarak bir `Form1_Load` olay işleyicisi oluşturun.  
  
7.  Aşağıdaki kodu ekleyin `Form1_Load` olay işleyicisi.  
  
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
  
## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Hizmet Tarafından İzin Verilen En Büyük İleti Boyutunu Artırma  
 Hizmet, Customers ve Orders tablolarından veri döndürdüğünden, maxReceivedMessageSize için varsayılan değer verileri tutabilecek kadar büyük değildir ve artırılması gerekir. Bu kılavuz için değeri 6553600 olarak değiştirin. İstemcideki değeri değişirin; bunu yaptığınızda hizmet başvurusu otomatik olarak güncelleştirilir.  
  
> [!NOTE]
>  Varsayılan alt sınır boyutu hizmet reddi (DoS) saldırılarına maruz kalmayı sınırlamak içindir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>MaxReceivedMessageSize değerini artırmak için  
  
1.  İçinde **Çözüm Gezgini**, PresentationTier projesindeki app.config dosyasına çift tıklayın.  
  
2.  Bulun **maxReceivedMessage** boyut özniteliğini ve bir değerle değiştirmek `6553600`.  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulamayı çalıştırın. Veriler veri hizmetinden alınır ve formda görüntülenir.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  F5 tuşuna basın.  
  
2.  Customers ve Orders tablolarındaki veriler veri hizmetinden alınır ve formda görüntülenir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak, Windows tabanlı bir uygulama içinde ilgili verileri kaydettikten sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Örneğin, bu uygulamada aşağıdaki geliştirmeleri yapabilirsiniz:  
  
-   Veri kümesine doğrulama ekleme. Bilgi için [izlenecek yol: bir N katmanlı veri uygulamasına doğrulama ekleme](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).  
  
-   Verileri tekrar veritabanında güncelleştirmek için hizmete ek yöntemler ekleme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [N katmanlı uygulamalarda veri kümeleriyle çalışma](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)   
 [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)

