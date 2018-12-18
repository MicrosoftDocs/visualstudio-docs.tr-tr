---
title: 'İzlenecek yol: bir Silverlight Web parçası oluşturma SharePoint için OData görüntüleyen | Microsoft Docs'
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67742078cefcd0608d1cff9a5bab609053544392
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296118"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>İzlenecek yol: SharePoint için OData görüntüleyen bir Silverlight web bölümü oluşturma
  SharePoint 2010 listesi verilerini OData yoluyla kullanıma sunar. SharePoint'te, OData hizmeti ListData.svc RESTful hizmeti tarafından uygulanır. Bu izlenecek yol, bir Silverlight uygulamasını barındıran bir SharePoint web bölümü oluşturma işlemi gösterilmektedir. Silverlight uygulaması ListData.svc kullanarak SharePoint duyuru listesi bilgilerini görüntüler. Daha fazla bilgi için [SharePoint Foundation REST arabirimi](http://go.microsoft.com/fwlink/?LinkId=225999) ve [açık veri Protokolü](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Microsoft Windows ve SharePoint sürümleri desteklenir.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Bir Silverlight uygulaması ile Silverlight web bölümü oluşturma
 İlk olarak, Visual Studio'da bir Silverlight uygulaması oluşturursunuz. Silverlight uygulaması, SharePoint duyuruları listeden ListData.svc hizmetini kullanarak verileri alır.  
  
> [!NOTE]  
>  Silverlight 4.0 önce hiçbir sürümü, SharePoint listesini veri başvurmak için gerekli arabirimlere destekler.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Bir Silverlight uygulaması ve Silverlight web bölümü oluşturmak için
  
1. Menü çubuğunda, **dosya** > **yeni** > **proje** görüntülenecek **yeni proje** iletişim kutusu.  
  
2. Genişletin **SharePoint** ya da düğümünde **Visual C#** veya **Visual Basic**ve ardından **2010** düğümü.  
  
3. Şablonlar bölmesinde seçin **SharePoint 2010 Silverlight Web Bölümü** şablonu.  
  
4. İçinde **adı** kutusuna **SLWebPartTest** seçip **Tamam** düğmesi.  
  
    **SharePoint Özelleştirme Sihirbazı** iletişim kutusu görüntülenir.  
  
5. Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, site tanımı hata ayıklamak istediğiniz sunucu için SharePoint sitesi URL'sini girin veya varsayılan konumu kullanın (http://<em>sistem adı</em>/) .  
  
6. İçinde **bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, seçin **Grup çözümü olarak Dağıt** seçenek düğmesini.  
  
    Bu örnek Grup çözümü kullansa da, Silverlight web bölümü proje grubu ya da korumalı çözüm olarak dağıtılabilir. Korumalı çözümler ve Grup çözümleri hakkında daha fazla bilgi için bkz. [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md).  
  
7. İçinde **nasıl Silverlight Web Bölümü ilişkilendirmek istiyorsunuz** bölümünü **Silverlight yapılandırma bilgilerini belirtmek** sayfasında **yeni bir Silverlight projesi oluşturma ve web bölümüyle ilişkilendir** seçenek düğmesini.  
  
8. Değişiklik **adı** için **SLApplication**ayarlayın **dil** ya da **Visual Basic** veya **Visual C#**, ve ardından **Silverlight sürümü** için **Silverlight 4.0**.  
  
9. Seçin **son** düğmesi. Projeleri görünür **Çözüm Gezgini**.  
  
     Çözüm iki proje içermektedir: bir Silverlight uygulaması ile bir Silverlight web bölümü. Silverlight uygulaması alır ve SharePoint listesi verileri görüntüler ve Silverlight web bölümü, SharePoint'te görüntülemek etkinleştirme Silverlight uygulaması barındırır.  
  
## <a name="customize-the-silverlight-application"></a>Silverlight uygulamasını özelleştirme
 Kod ve tasarım öğelerini Silverlight uygulamasına ekleyin.  
  
#### <a name="to-customize-the-silverlight-application"></a>Silverlight uygulaması özelleştirmek için
  
1.  Silverlight uygulamasında System.Windows.Data bir bütünleştirilmiş kod başvurusu ekleyin. Daha fazla bilgi için [nasıl yapılır: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları**ve ardından **hizmet Başvurusu Ekle**.  
  
    > [!NOTE]  
    >  Visual Basic kullanıyorsanız seçmelisiniz **tüm dosyaları göster** simgesi en üstündeki **Çözüm Gezgini** görüntülenecek **başvuruları** düğümü.  
  
3.  Adresi kutusunda **hizmet Başvurusu Ekle** iletişim kutusunda, SharePoint sitenizin URL'sini girin **http://MySPSite**ve ardından **Git** düğmesi.  
  
     Silverlight SharePoint OData hizmeti ListData.svc bulduğunda, tam hizmet URL'si ile adresini değiştirir. Bu örnekte, http://myserver olur http://myserver/_vti_bin/ListData.svc.  
  
4.  Seçin **Tamam** projesine hizmet başvurusu eklemek için düğme ve ServiceReference1 varsayılan hizmet adını kullanın.  
  
5.  Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
6.  Projenin SharePoint hizmetini temel alan yeni bir veri kaynağı ekleyin. Bu, menü çubuğunda yapmak için **görünümü** > **diğer Windows** > **veri kaynakları**.  
  
     **Veri kaynakları** penceresi tüm görevler, duyuruları ve takvim gibi kullanılabilir SharePoint listesi verileri gösterir.  
  
7.  Duyurular listesi verileri Silverlight uygulamasına ekleyin. "Duyuruları" ndan sürükleyebilirsiniz **veri kaynakları** Silverlight tasarımcıya penceresi.  
  
     Bu, SharePoint sitesinin Duyurular listesi için ilişkili bir kılavuz denetimi oluşturur.  
  
8.  Kılavuz Denetimi Silverlight sayfaya sığacak şekilde yeniden boyutlandırın.  
  
9. MainPage.xaml kod dosyasında (*MainPage.xaml.cs* Visual C# veya *MainPage.xaml.vb* Visual Basic için), aşağıdaki ad alanı başvurularını ekleyin.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. Aşağıdaki değişken bildirimlerini sınıfının üstüne ekleyin.  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
   
11. Değiştirin `UserControl_Loaded` aşağıdaki yordamı.  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
     Değiştirdiğinizden emin olun *ServerName* SharePoint çalıştıran sunucunuzun adı ile yer tutucu.  
  
12. Hata işleme yordamını ekleyin.  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
       
## <a name="modify-the-silverlight-web-part"></a>Silverlight web bölümü Değiştir
 Bir Silverlight hata ayıklamayı etkinleştirmek için Silverlight web bölümü projesi özelliğini değiştirin.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Silverlight web bölümü değiştirmek için  
  
1.  Silverlight web bölümü projesi için kısayol menüsünü açın (**SLWebPartTest**) ve ardından **özellikleri**.  
  
2.  İçinde **özellikleri** penceresinde seçin **SharePoint** sekmesi.  
  
3.  Zaten seçili değilse, seçin **(betik hata ayıklaması yerine) etkinleştirmek için Silverlight hata ayıklama** onay kutusu.  
  
4.  Projeyi kaydedin.  
  
## <a name="test-the-silverlight-web-part"></a>Silverlight web bölümünü sınama
 Yeni bir Silverlight web parçası, SharePoint listesini veri düzgün şekilde görüntülenmesini sağlamak için SharePoint'e test edin.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Silverlight web bölümü test etmek için  
  
1.  Seçin **F5** anahtarı oluşturun ve SharePoint çözümü çalıştırın.  
  
2.  SharePoint'te üzerinde **Site eylemleri** menüsünde seçin **yeni sayfa**.  
  
3.  İçinde **yeni sayfa** iletişim kutusunda, bir başlık girin **SL Web bölümünü sınama**ve ardından **Oluştur** düğmesi.  
  
4.  Sayfa tasarımcısında üzerinde **düzenleme araçları** sekmesini, **Ekle**.  
  
5.  Sekme şeridi seçin **Web Bölümü**.  
  
6.  İçinde **kategorileri** kutusunda **özel** klasör.  
  
7.  İçinde **Web Bölümleri** listesinde, Silverlight web bölümünü seçin ve ardından **Ekle** tasarımcıya web bölümü eklemek için Ekle düğmesine.  
  
8.  Tüm eklemeleri, istediğiniz web sayfasına yaptıktan sonra Seç **sayfa** sekmesine ve ardından **Kaydet ve Kapat** araç çubuğu düğmesi.  
  
     Silverlight web bölümü artık SharePoint sitesinden duyuru verileri görüntüleme. Varsayılan olarak, SharePoint sitesi sayfalarının listeden sayfa depolanır.  
  
    > [!NOTE]  
    >  Silverlight veri alanlarında erişirken, Silverlight web uygulamaları yararlanmak için kullanılan güvenlik açıklarına karşı korur. Silverlight'ta uzaktan verilere erişirken sorun yaşarsanız bkz [bir hizmet üzerinden etki alanı sınırlarında kullanılabilir hale getirme](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [SharePoint çözüm paketleri yükseltme dağıtma ve yayımlama](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
