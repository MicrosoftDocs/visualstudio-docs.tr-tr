---
title: 'İzlenecek yol: WPF ve Entity Framework ile WCF veri hizmeti oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cbafb006091956ce5359bc6b575accd057b2ee37
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305357"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>İzlenecek yol: WPF ve Entity Framework ile WCF veri hizmeti oluşturma
Bu izlenecek yol basit bir oluşturma işlemini gösterir [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] barındırılan bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulamasını ve sonra bir Windows Forms uygulamasından erişebilirsiniz.

Bu kılavuzda:

- Konak için bir web uygulaması oluşturma bir [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Oluşturma bir [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] temsil eden `Customers` Northwind veritabanındaki tablo.

- Oluşturma bir [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- İstemci uygulaması oluşturma ve bir başvuru ekleyin [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Hizmete veri bağlamayı etkinleştirin ve kullanıcı arabirimini oluşturun.

- İsteğe bağlı olarak, uygulamaya filtreleme yetenekleri ekleyin.

## <a name="prerequisites"></a>Önkoşullar
Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2. Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (**SQL Server Nesne Gezgini** parçası olarak yüklenen **veri depolama ve işleme** iş yükünü Visual Studio Yükleyicisi'nde.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="creating-the-service"></a>Hizmeti Oluşturma
Oluşturmak için bir [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], bir web projesi ekleyecek, oluşturun bir [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]ve sonra da modelden hizmeti oluşturun.

İlk adımda hizmeti barındırmak için bir web projesi ekleyin.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Web projesi oluşturmak için

1. Menü çubuğunda, **dosya** > **yeni** > **proje**.

2. İçinde **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#**  ve **Web** düğümleri seçin**ASP.NET Web uygulaması** şablonu.

3. İçinde **adı** metin kutusuna **NorthwindWeb**ve ardından **Tamam** düğmesi.

4. İçinde **yeni ASP.NET projesi** iletişim kutusundaki **bir şablon seçin** listesinde **boş**ve ardından **Tamam** düğmesi.

Sonraki adımda oluşturduğunuz bir [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] temsil eden `Customers` Northwind veritabanındaki tablo.

### <a name="to-create-the-entity-data-model"></a>Varlık Veri Modeli'ni oluşturmak için

1. Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **veri** düğümünü seçip **ADO.NET varlık veri modeli** öğesi.

3. İçinde **adı** metin kutusuna `NorthwindModel`ve ardından **Ekle** düğmesi.

     Varlık Veri Modeli Sihirbazı görüntülenir.

4. Varlık veri modeli Sihirbazı içinde üzerinde **Choose Model Contents** sayfasında **EF veritabanı Tasarımcısından** öğesi ekleyin ve ardından **sonraki** düğmesi.

5. Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdaki adımlardan birini gerçekleştirin:

    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         veya

    -   Seçin **yeni bağlantı** yeni bir veri bağlantısı yapılandırmak için düğmeye. Daha fazla bilgi için [yeni bağlantı ekleme](../data-tools/add-new-connections.md).

6. Veritabanına parola gerekiyorsa seçin **Evet, bağlantı dizesini hassas verileri eklemek** seçenek düğmesini ve ardından **sonraki** düğmesi.

    > [!NOTE]
    > Bir iletişim kutusu görüntülenirse, seçin **Evet** dosyayı projenize kaydetmek için.

7. Üzerinde **sürümünüzü seçin** sayfasında **Entity Framework 5.0** seçenek düğmesini ve ardından **sonraki** düğmesi.

    > [!NOTE]
    > WCF hizmetleri ile Entity Framework 6 en son sürümünü kullanmak için WCF Veri Hizmetleri Entity Framework sağlayıcısı NuGet paketini yüklemeniz gerekir. Bkz: [kullanarak WCF Veri Hizmetleri 5.6.0 Entity Framework 6 +](https://blogs.msdn.microsoft.com/odatateam/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümünü **müşteriler** onay kutusunu işaretleyin ve ardından **son** düğmesi.

     Varlık modeli diyagramı görüntülenir ve *NorthwindModel.edmx* dosyası projenize eklenir.

Sonraki adımda, oluşturun ve veri hizmetini test edin.

### <a name="to-create-the-data-service"></a>Veri hizmetini oluşturmak için

1. Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **Web** düğümünü seçip **WCF Data Service 5.6** öğesi.

3. İçinde **adı** metin kutusuna `NorthwindCustomers`ve ardından **Ekle** düğmesi.

     **NorthwindCustomers.svc** dosya görünür **Kod Düzenleyicisi**.

4. İçinde **Kod Düzenleyicisi**, ilk bulun `TODO:` açıklama ve kodu aşağıdakiyle değiştirin:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5. Açıklamaları değiştirin `InitializeService` olay işleyicisi aşağıdaki kod ile:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6. Menü çubuğunda, **hata ayıklama** > **hata ayıklama olmadan Başlat** hizmeti çalıştırmak için. Bir tarayıcı penceresi açılır ve hizmet için XML Şeması görüntülenir.

7. İçinde **adresi** çubuğunda girin `Customers` URL'sini sonunda **NorthwindCustomers.svc**ve ardından **Enter** anahtarı.

     Verileri bir XML temsilini `Customers` tablo görünür.

    > [!NOTE]
    > Bazı durumlarda, Internet Explorer verileri yanlışlıkla RSS akışı olarak yorumlar. RSS akışlarını görüntüleme seçeneğinin devre dışı bırakıldığından emin olmalısınız. Daha fazla bilgi için [hizmet başvurularında sorun giderme](../data-tools/troubleshooting-service-references.md).

8. Tarayıcı penceresini kapatın.

Sonraki adımlarda hizmeti kullanmak üzere bir Windows Forms istemci uygulaması oluşturun.

## <a name="creating-the-client-application"></a>İstemci Uygulamasını Oluşturma
 İstemci uygulamasını oluşturmak için ikinci bir proje ekleyecek, projeye bir hizmet Başvurusu Ekle, bir veri kaynağını yapılandırmak ve hizmetinden verileri görüntülemek için bir kullanıcı arabirimi oluşturma.

 İlk adım, bir Windows Forms projesi çözüme ekleyin ve başlangıç projesi olarak ayarlayın.

### <a name="to-create-the-client-application"></a>İstemci uygulamasını oluşturmak için

1. Menü çubuğunda, dosya **Ekle** > **yeni proje**.

2. İçinde **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#**  düğümünü seçin **Windows** düğümünü seçin **Windows Forms uygulamalarındaki**.

3. İçinde **adı** metin kutusuna `NorthwindClient`ve ardından **Tamam** düğmesi.

4. İçinde **Çözüm Gezgini**, seçin **; northwindclient & lt** proje düğümü.

5. Menü çubuğunda, **proje**, **başlangıç projesi olarak ayarla**.

Sonraki adımda, bir hizmet Başvurusu Ekle [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] web projesinde.

### <a name="to-add-a-service-reference"></a>Hizmet başvurusu eklemek için

1. Menü çubuğunda, **proje** > **hizmet Başvurusu Ekle**.

2. İçinde **hizmet Başvurusu Ekle** iletişim kutusunda **bulma** düğmesi.

     NorthwindCustomers hizmetinin URL'si görünür **adresi** alan.

3. Seçin **Tamam** hizmet başvurusunu eklemek için.

Sonraki adımda, hizmete veri bağlamayı etkinleştirmek için bir veri kaynağı yapılandırın.

### <a name="to-enable-data-binding-to-the-service"></a>Hizmete veri bağlamayı etkinleştirmek için

1. Menü çubuğunda, **görünümü** > **diğer Windows** > **veri kaynakları**.

   **Veri kaynakları** penceresi açılır.

2. İçinde **veri kaynakları** penceresinde seçin **yeni veri kaynağı Ekle** düğmesi.

3. Üzerinde **bir veri kaynağı türü seçin** sayfasının **veri kaynağı Yapılandırma Sihirbazı**, seçin **nesne**ve ardından **sonraki** düğmesi .

4. Üzerinde **veri nesnelerini seçin** sayfasında **; northwindclient & lt** düğümünü ve ardından **gt;northwindclient.servicereference1** düğümü.

5. Seçin **müşteri** onay kutusunu işaretleyin ve ardından **son** düğmesi.

Sonraki adımda, hizmetten alınan verileri görüntüleyen bir kullanıcı arabirimi oluşturun.

### <a name="to-create-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için

1. İçinde **veri kaynakları** penceresinde, kısayol menüsünü açın **müşteriler** düğüm ve **kopyalama**.

2. İçinde **Form1.vb** veya **Form1.cs** form tasarımcısında kısayol menüsünü açın ve seçin **Yapıştır**.

    A <xref:System.Windows.Forms.DataGridView> denetimi, bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeni formuna eklenir.

3. Seçin **CustomersDataGridView** denetimi ve ardından **özellikleri** penceresi kümesi **Dock** özelliğini **dolgu**.

4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **Form1** düğüm ve **kodu görüntüle** Kod Düzenleyicisi'ni açın ve aşağıdakileri ekleyin `Imports` veya `Using`deyimini dosyanın üst:

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. Aşağıdaki kodu ekleyin `Form1_Load` olay işleyicisi:

   ```vb
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
           Dim proxy As New NorthwindEntities _
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
           Me.CustomersBindingSource.DataSource = proxy.Customers
       End Sub
   ```

   ```csharp
   private void Form1_Load(object sender, EventArgs e)
   {
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
   this.CustomersBindingSource.DataSource = proxy.Customers;
   }
   ```

6. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **NorthwindCustomers.svc** seçin ve dosya **tarayıcıda görüntüle**. Internet Explorer açılır ve hizmet için XML Şeması görüntülenir.

7. Internet Explorer adres çubuğundan URL'yi kopyalayın.

8. 4. adımda eklediğiniz kodda seçin `http://localhost:53161/NorthwindCustomers.svc/` ve az önce kopyaladığınız URL ile değiştirin.

9. Menü çubuğunda, **hata ayıklama** > **hata ayıklamayı Başlat** uygulamayı çalıştırın. Müşteri bilgileri gösterilir.

   Artık, NorthwindCustomers hizmetinden müşterilerin listesini görüntüleyen çalışır bir uygulamanız var. Ek veri hizmeti aracılığıyla kullanıma sunmak isterseniz değiştirebileceğiniz [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Northwind veritabanından ek tablolar içerecek şekilde.

Sonraki isteğe bağlı adımda hizmetin döndürdüğü verileri filtreleme hakkında bilgi edinin.

## <a name="adding-filtering-capabilities"></a>Filtreleme Yetenekleri Ekleme
 Bu adımda, uygulama verileri müşterinin Şehir bilgisine göre filtrelemek için özelleştirin.

### <a name="to-add-filtering-by-city"></a>Şehir bilgisine göre filtreleme eklemek için

1. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **Form1.vb** veya **Form1.cs** düğüm ve **açın**.

2. Ekleme bir <xref:System.Windows.Forms.TextBox> denetimi ve bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** form.

3. Kısayol menüsünü açın <xref:System.Windows.Forms.Button> denetim öğesini **kodu görüntüle**ve ardından aşağıdaki kodu ekleyin `Button1_Click` olay işleyicisi:

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4. Önceki kod içinde `http://localhost:53161/NorthwindCustomers.svc` URL'den ile `Form1_Load` olay işleyicisi.

5. Menü çubuğunda, **hata ayıklama** > **hata ayıklamayı Başlat** uygulamayı çalıştırın.

6. Metin kutusuna **Londra**ve ardından düğmeyi seçin. Yalnızca Londralı müşteriler görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Nasıl yapılır: ekleme, güncelleştirme veya WCF veri hizmeti başvurusunu Kaldır](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)