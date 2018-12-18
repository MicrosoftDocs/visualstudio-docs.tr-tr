---
title: 'İzlenecek yol: WPF ve Entity Framework ile WCF veri hizmeti oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3d115c7ea7b2739f49492fb28fe855e2638d972c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889600"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>İzlenecek yol: WPF ve Entity Framework ile WCF veri hizmeti oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu izlenecek yol basit bir oluşturma işlemini gösterir [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] barındırılan bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamasını ve sonra bir Windows Forms uygulamasından erişebilirsiniz.  
  
 Bu izlenecek yolda yapacaklarınız:  
  
-   Konak için bir Web uygulaması oluşturma bir [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Oluşturma bir [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Northwind veritabanındaki Müşteriler tablosunu temsil eden.  
  
-   Oluşturma bir [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   İstemci uygulaması oluşturma ve bir başvuru ekleyin [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Hizmete veri bağlamayı etkinleştirin ve kullanıcı arabirimini oluşturun.  
  
-   İsteğe bağlı olarak, uygulamaya filtreleme yetenekleri ekleyin.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Northwind örnek veritabanı.  
  
     Geliştirme bilgisayarınızda bu veritabanı yoksa, buradan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Yönergeler için [Downloading Sample Databases](http://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).  
  
## <a name="creating-the-service"></a>Hizmeti Oluşturma  
 Oluşturmak için bir [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], bir Web projesi ekleyecek, oluşturun bir [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ve sonra da modelden hizmeti oluşturun.  
  
 İlk adımda hizmeti barındırmak için bir Web projesi ekleyeceksiniz.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>Web projesini oluşturmak için  
  
1. Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#** ve **Web** düğümler ve ardından **ASP. NET Web uygulaması** şablonu.  
  
3. İçinde **adı** metin kutusuna **NorthwindWeb**ve ardından **Tamam** düğmesi.  
  
4. İçinde **yeni ASP.NET projesi** iletişim kutusundaki **bir şablon seçin** listesinde **boş**ve ardından **Tamam** düğmesi.  
  
   Bu adımda oluşturacağınız bir [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Northwind veritabanındaki Müşteriler tablosunu temsil eden.  
  
#### <a name="to-create-the-entity-data-model"></a>Varlık Veri Modeli'ni oluşturmak için  
  
1. Menü çubuğunda, **proje**, **Yeni Öğe Ekle**.  
  
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
   >  Bir iletişim kutusu görüntülenirse, seçin **Evet** dosyayı projenize kaydetmek için.  
  
7. Üzerinde **sürümünüzü seçin** sayfasında **Entity Framework 5.0** seçenek düğmesini ve ardından **sonraki** düğmesi.  
  
   > [!NOTE]
   >  WCF hizmetleri ile Entity Framework 6 en son sürümünü kullanmak için WCF Veri Hizmetleri Entity Framework sağlayıcısı NuGet paketini yüklemeniz gerekir. Bkz: [kullanarak WCF Veri Hizmetleri 5.6.0 Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8. Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümünü **müşteriler** onay kutusunu işaretleyin ve ardından **son** düğmesi.  
  
    Varlık modeli diyagramı görüntülenir ve projenize bir NorthwindModel.edmx dosyası eklenir.  
  
   Bu adımda, veri hizmetini oluşturup test edeceksiniz.  
  
#### <a name="to-create-the-data-service"></a>Veri hizmetini oluşturmak için  
  
1. Menü çubuğunda, **proje**, **Yeni Öğe Ekle**.  
  
2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **Web** düğümünü seçip **WCF Data Service 5.6** öğesi.  
  
3. İçinde **adı** metin kutusuna `NorthwindCustomers`ve ardından **Ekle** düğmesi.  
  
    NorthwindCustomers.svc dosyası görünür **Kod Düzenleyicisi**.  
  
4. İçinde **Kod Düzenleyicisi**, ilk bulun `TODO:` açıklama ve kodu aşağıdakiyle değiştirin:  
  
    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5. Açıklamaları değiştirin `InitializeService` olay işleyicisi aşağıdaki kod ile:  
  
    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6. Menü çubuğunda, **hata ayıklama**, **hata ayıklama olmadan Başlat** hizmeti çalıştırmak için. Bir tarayıcı penceresi açılır ve hizmet için XML şeması görüntülenir.  
  
7. İçinde **adresi** çubuğunda girin `Customers` northwindcustomers.svc URL'SİNİN sonuna seçip **ENTER** anahtarı.  
  
    Müşteriler tablosundaki verilerin bir XML gösterimi görüntülenir.  
  
   > [!NOTE]
   >  Bazı durumlarda, Internet Explorer verileri yanlışlıkla RSS akışı olarak yorumlar. RSS akışlarını görüntüleme seçeneğinin devre dışı bırakıldığından emin olmalısınız. Daha fazla bilgi için [hizmet başvurularında sorun giderme](../data-tools/troubleshooting-service-references.md).  
  
8. Tarayıcı penceresini kapatın.  
  
   Sonraki adımlarda, hizmeti kullanmak üzere bir Windows Forms istemci uygulaması oluşturacaksınız.  
  
## <a name="creating-the-client-application"></a>İstemci Uygulamasını Oluşturma  
 İstemci uygulamasını oluşturmak için ikinci bir proje ekleyecek, projeye bir hizmet başvurusu ekleyecek, bir veri kaynağı yapılandıracak ve hizmetten alınan verileri görüntülemek üzere bir kullanıcı arabirimi oluşturacaksınız.  
  
 İlk adımda, çözüme bir Windows Forms projesi ekleyecek ve bunu başlangıç projesi olarak ayarlayacaksınız.  
  
#### <a name="to-create-the-client-application"></a>İstemci uygulamasını oluşturmak için  
  
1. Menü çubuğunda, dosya **Ekle**, **yeni proje**.  
  
2. İçinde **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#** düğüm ve **Windows** düğümünün seçin **Windows Forms uygulamalarındaki**.  
  
3. İçinde **adı** metin kutusuna `NorthwindClient`ve ardından **Tamam** düğmesi.  
  
4. İçinde **Çözüm Gezgini**, seçin **; northwindclient & lt** proje düğümü.  
  
5. Menü çubuğunda, **proje**, **başlangıç projesi olarak ayarla**.  
  
   Bu adımda, bir hizmet başvurusu ekleyeceksiniz [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] Web projesinde.  
  
#### <a name="to-add-a-service-reference"></a>Hizmet başvurusu eklemek için  
  
1. Menü çubuğunda, **proje**, **hizmet Başvurusu Ekle**.  
  
2. İçinde **hizmet Başvurusu Ekle** iletişim kutusunda **bulma** düğmesi.  
  
    NorthwindCustomers hizmetinin URL'si görünür **adresi** alan.  
  
3. Seçin **Tamam** hizmet başvurusunu eklemek için.  
  
   Bu adımda, hizmete veri bağlamayı etkinleştirmek için bir veri kaynağı oluşturacaksınız.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Hizmete veri bağlamayı etkinleştirmek için  
  
1. Menü çubuğunda, **görünümü**, **diğer Windows**, **veri kaynakları**.  
  
2. İçinde **veri kaynakları** penceresinde seçin **yeni veri kaynağı Ekle** düğmesi.  
  
3. Üzerinde **bir veri kaynağı türü seçin** sayfasının **veri kaynağı Yapılandırma Sihirbazı**, seçin **nesne**ve ardından **sonraki** düğmesi .  
  
4. Üzerinde **veri nesnelerini seçin** sayfasında **; northwindclient & lt** düğümünü ve ardından **gt;northwindclient.servicereference1** düğümü.  
  
5. Seçin **müşteri** onay kutusunu işaretleyin ve ardından **son** düğmesi.  
  
   Bu adımda, hizmetten alınan verileri görüntüleyecek kullanıcı arabirimini oluşturacaksınız.  
  
#### <a name="to-create-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için  
  
1. İçinde **veri kaynakları** penceresinde, kısayol menüsünü açın **müşteriler** düğüm ve **kopyalama**.  
  
2. İçinde **Form1.vb** veya **Form1.cs** form tasarımcısında kısayol menüsünü açın ve seçin **Yapıştır**.  
  
    A <xref:System.Windows.Forms.DataGridView> denetimi, bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeni formuna eklenir.  
  
3. Seçin **CustomersDataGridView** denetimi ve ardından **özellikleri** penceresi kümesi **Dock** özelliğini **dolgu**.  
  
4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **Form1** düğüm ve **kodu görüntüle** Kod Düzenleyicisi'ni açın ve aşağıdaki Imports veya Using deyimini adresindeki eklemek için dosyanın en üstüne:  
  
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
  
6. İçinde **Çözüm Gezgini**, NorthwindCustomers.svc dosyasının kısayol menüsünü açın ve seçin **tarayıcıda görüntüle**. Internet Explorer açılır ve hizmet için XML şeması görüntülenir.  
  
7. Internet Explorer adres çubuğundan URL'yi kopyalayın.  
  
8. 4. adımda eklediğiniz kodda seçin `http://localhost:53161/NorthwindCustomers.svc/` ve az önce kopyaladığınız URL ile değiştirin.  
  
9. Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat** uygulamayı çalıştırın. Müşteri bilgileri görüntülenir.  
  
   Artık, NorthwindCustomers hizmetinden müşterilerin listesini görüntüleyen çalışır bir uygulamanız var. Ek veri hizmeti aracılığıyla kullanıma sunmak isterseniz değiştirebileceğiniz [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Northwind veritabanından ek tablolar içerecek şekilde.  
  
   Bir sonraki isteğe bağlı adımda hizmetin döndürdüğü verileri filtrelemeyi öğreneceksiniz.  
  
## <a name="adding-filtering-capabilities"></a>Filtreleme Yetenekleri Ekleme  
 Bu adımda uygulamayı, müşterinin şehir bilgisine göre verileri filtreleyecek şekilde özelleştireceksiniz.  
  
#### <a name="to-add-filtering-by-city"></a>Şehir bilgisine göre filtreleme eklemek için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **Form1.vb** veya **Form1.cs** düğüm ve **açın**.  
  
2.  Ekleme bir <xref:System.Windows.Forms.TextBox> denetimi ve bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** form.  
  
3.  Kısayol menüsünü açın <xref:System.Windows.Forms.Button> denetlemek ve seçin **kodu görüntüle**ve ardından aşağıdaki kodu ekleyin `Button1_Click` olay işleyicisi:  
  
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
  
4.  Önceki kod içinde `http://localhost:53161/NorthwindCustomers.svc` URL'den ile `Form1_Load` olay işleyicisi.  
  
5.  Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat** uygulamayı çalıştırın.  
  
6.  Metin kutusuna **Londra**ve ardından düğmeyi seçin. Yalnızca Londralı müşteriler görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Nasıl Yapılır: WCF Veri Hizmeti Başvurusunu Güncelleme veya Kaldırma](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)

