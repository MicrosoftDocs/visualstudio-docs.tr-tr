---
title: 'İzlenecek yol: bir SharePoint uygulaması için profil oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5db5e9408a64df80311667267561ee69234fd7d5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852758"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>İzlenecek yol: bir SharePoint uygulama profili
  Bu izlenecek yol, profil oluşturma araçlarını Visual Studio'da bir SharePoint uygulama performansını iyileştirmek için nasıl kullanılacağını gösterir. Örneğin, özellik olayı alıcısını performansını düşürür bir boşta döngü içeren bir SharePoint özelliği olay alıcısı uygulamasıdır. Visual Studio profil oluşturucu, bulun ve proje en pahalı (yavaş gerçekleşir) parçası olarak da bilinen ortadan sağlar *etkin yolu*.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- [Bir özellik ve özellik olayı alıcısını ekleme](#BKMK_AddFtrandFtrEvntReceiver).  
  
- [Yapılandırma ve SharePoint uygulaması dağıtma](#BKMK_ConfigSharePointApp).  
  
- [SharePoint uygulaması çalıştıran](#BKMK_RunSPApp).  
  
- [Görüntüleme ve profil oluşturma sonuçları yorumlayarak destek sağlama](#BKMK_ViewResults).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Microsoft Windows ve SharePoint sürümleri desteklenir.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-sharepoint-project"></a>Bir SharePoint projesi oluşturma
 İlk olarak, bir SharePoint projesi oluşturun.  
  
#### <a name="to-create-a-sharepoint-project"></a>Bir SharePoint projesi oluşturmak için  
  
1. Menü çubuğunda, **dosya** > **yeni** > **proje** görüntülenecek **yeni proje** iletişim kutusu.  
  
2. Genişletin **SharePoint** ya da düğümünde **Visual C#** veya **Visual Basic**ve ardından **2010** düğümü.  
  
3. Şablonlar bölmesinde seçin **SharePoint 2010 projesi** şablonu.  
  
4. İçinde **adı** kutusuna **ProfileTest**ve ardından **Tamam** düğmesi.  
  
    **SharePoint Özelleştirme Sihirbazı** görünür.  
  
5. Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, site tanımı hata ayıklamak istediğiniz sunucu için SharePoint sitesi URL'sini girin veya varsayılan konumu kullanın (http://<em>sistem adı</em>/) .  
  
6. İçinde **bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, seçin **Grup çözümü olarak Dağıt** seçenek düğmesini.  
  
    Şu anda, yalnızca profili Grup çözümlerini kullanabilirsiniz. Grup çözümlerini karşı korumalı çözümler hakkında daha fazla bilgi için bkz. [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Seçin **son** düğmesi. Proje görünür **Çözüm Gezgini**.  
  
## <a name="add-a-feature-and-feature-event-receiver"></a>Bir özellik ve özelliği olay alıcısı Ekle
 Ardından, bir özellik proje özelliği için bir olay alıcısı birlikte ekleyin. Bu olay alıcısı, profili oluşturulacak kodu içerecek.  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>Bir özellik ve özellik olayı alıcısını eklemek için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **özellikleri** düğümünü seçin **Özellik Ekle**ve adı varsayılan değerde bırakın **özellik1**.  
  
2.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **özellik1**ve ardından **olay alıcısı Ekle**.  
  
     Bu, özellikle birden çok derleme dışı bırakılan olay işleyicileri için bir kod dosyası ekler ve dosyasını düzenleme için açar.  
  
3.  Olay alıcısı sınıfında, aşağıdaki değişken bildirimlerini ekleyin.  
  
    ```vb  
    ' SharePoint site/subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site/subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
4.  Değiştirin `FeatureActivated` aşağıdaki kodla yordamı.  
  
    ```vb  
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add a new announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    ' Waste some time.  
                    TimeCounter()  
                    ' Update the list.  
                    listItem.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add a new announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +   
    DateTime.Now.ToString();  
                    // Waste some time.  
                    TimeCounter();  
                    // Update the list.  
                    listItem.Update();                          
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
5.  Aşağıdaki yordam Ekle `FeatureActivated`yordamı.  
  
    ```vb  
  
    Public Sub TimeCounter()  
        Dim result As Integer  
        For i As Integer = 0 To 99999  
            For j As Integer = 0 To 9999  
                result = i * j  
            Next j  
        Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void TimeCounter()  
    {  
        for (int i = 0; i < 100000; i++)  
        {  
            for (int j = 0; j < 10000; j++)  
            {  
                int result = i * j;  
            }  
        }  
    }  
    ```  
  
6.  İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın (**ProfileTest**) ve ardından **özellikleri**.  
  
7.  İçinde **özellikleri** iletişim kutusunda **SharePoint** sekmesi.  
  
8.  İçinde **etkin Dağıtım Yapılandırması** listesinde **Hayır etkinleştirme**.  
  
     Bu dağıtım yapılandırması seçme özelliği daha sonra SharePoint el ile etkinleştirmek sağlar.  
  
9. Projeyi kaydedin.  
  
## <a name="configure-and-deploy-the-sharepoint-application"></a>Yapılandırma ve SharePoint uygulaması dağıtma
 SharePoint Proje hazır olduğuna göre yapılandırın ve SharePoint sunucusuna dağıtın.  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Yapılandırma ve SharePoint uygulaması dağıtma  
  
1.  Üzerinde **Çözümle** menüsünde seçin **performans Sihirbazını Başlat**.  
  
2.  ' Nın sayfasında **performans Sihirbazı**, leave yöntemi olarak profil oluşturma **CPU örnekleme** ve **sonraki** düğmesi.  
  
     Bir profil oluşturma yöntemlerini durumlarda profil oluşturma daha gelişmiş kullanılabilir. Daha fazla bilgi için [anlama performans koleksiyon metotları](/visualstudio/profiling/understanding-performance-collection-methods).  
  
3.  İki sayfasındaki **performans Sihirbazı**, profil hedefi olarak bırakın **ProfileTest** ve **sonraki** düğmesi.  
  
     Bir çözümde birden çok proje varsa, bunlar bu listede görüntülenir.  
  
4.  Üç sayfasındaki **performans Sihirbazı**temizleyin **Katman etkileşimi profil oluşturmayı etkinleştir** onay kutusunu işaretleyin ve ardından **sonraki** düğmesi.  
  
     Ve sayısını göstermek için bir web sayfası istenen katman etkileşim profili oluşturma (TIP) özelliği, veritabanlarında sorgulama uygulamalarının performansını ölçmek için kullanışlıdır. Verilerin bu örnek için gerekli olmadığı için Biz bu özellik etkin değildir.  
  
5.  Dört sayfasındaki **performans Sihirbazı**, bırakın **Sihirbaz sonlandıktan sonra profil oluşturmayı Başlat** seçili onay kutusunu işaretleyin ve ardından **son** düğmesi.  
  
     Sihirbaz, uygulama sunucusunda profil oluşturmayı etkinleştirir, görüntüler **performans Gezgini** penceresi ve sonra yapı dağıtır ve SharePoint uygulaması çalışır.  
  
## <a name="run-the-sharepoint-application"></a>SharePoint uygulaması çalıştırma
 SharePoint özelliği etkinleştir tetikleme `FeatureActivation` olay kodu çalıştırmak için.  
  
#### <a name="to-run-the-sharepoint-application"></a>SharePoint uygulamayı çalıştırmak için  
  
1.  SharePoint'te açın **Site eylemleri** menüsünü seçip **Site Ayarları**.  
  
2.  İçinde **Site eylemleri** listesinde **site özelliklerini Yönet** bağlantı.  
  
3.  İçinde **özellikleri** listesinde **etkinleştirme** düğmesinin yanındaki **ProfileTest özellik1**.  
  
     Çağrılma yeri boşta döngü nedeniyle bu, bunu yaptığınızda bir duraklama olan `FeatureActivated` işlevi.  
  
4.  Üzerinde **hızlı başlatma** çubuğundan **listeler** ve ardından **listeler** listesinde **duyuruları**.  
  
     Yeni bir duyuru özelliği etkinleştirildi belirten listeye eklendiğini dikkat edin.  
  
5.  SharePoint sitesi kapatın.  
  
     SharePoint kapattıktan sonra Profil Oluşturucu oluşturur ve bir örnek profili oluşturma raporu görüntüler ve .vsp dosyası olarak kaydeder **ProfileTest** projesinin klasörüne.  
  
## <a name="view-and-interpret-the-profile-results"></a>Görüntüleme ve profili sonuçları yorumlama
 Çalıştırın ve SharePoint uygulama profili, test sonuçlarını görüntüleyin.  
  
#### <a name="to-view-and-interpret-the-profile-results"></a>Görüntüleme ve profili sonuçları yorumlama
  
1.  İçinde **en bireysel işleri yapan işlevler** bölümde örnek profili oluşturma raporu dikkat `TimeCounter` listesinin en üstüne olduğu.  
  
     Bu konum belirten `TimeCounter` büyük uygulama performans sorunlarını biri anlamı örnekleri, en yüksek sayısını işlevleriyle biriydi. Bu durumda değilse bu şekilde tanıtım amacıyla tasarlanmış bilerek olduğundan, ancak önler.  
  
2.  İçinde **en bireysel işleri yapan işlevler** bölümünde, seçin `ProcessRequest` Maliyet dağıtımı görüntülemek için bağlantıyı `ProcessRequest` işlevi.  
  
     İçinde **işlevlerin çağrılma** bölümü `ProcessRequest`, dikkat **FeatureActiviated** işlevi listelenmiş olarak en pahalı işlevini çağırdı.  
  
3.  İçinde **işlevlerin çağrılma** bölümünde, seçin **FeatureActivated** düğmesi.  
  
     İçinde **işlevlerin çağrılma** bölümü **FeatureActivated**, `TimeCounter` işlevi listelenmiş olarak en pahalı işlevini çağırdı. İçinde **işlev kod görünümü** bölmesinde, vurgulanmış kodu (`TimeCounter`) etkin olduğundan ve düzeltme gerekmesi halinde gösterir.  
  
4.  Örnek profili oluşturma raporu kapatın.  
  
     İstediğiniz zaman tekrar raporu görüntülemek için .vsp açın **performans Gezgini** penceresi.  
  
## <a name="fix-the-code-and-reprofile-the-application"></a>Kodu düzeltin ve uygulama reprofile
 Etkin nokta işlevi SharePoint uygulaması olarak belirlenmiştir, bunu düzeltin.  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>Kodu düzeltin ve uygulama reprofile  
  
1.  Açıklama özelliği olay alıcısı kodda `TimeCounter` yöntem çağrısı `FeatureActivated` çağırılmasını önlemek için.  
  
2.  Projeyi kaydedin.  
  
3.  İçinde **performans Gezgini**, Hedefler klasörü açın ve ardından **ProfileTest** düğümü.  
  
4.  Üzerinde **performans Gezgini** araç, **eylemleri** sekmesini, **profil oluşturmayı Başlat** düğmesi.  
  
     Uygulama reprofiling önce profil oluşturma özelliklerinden herhangi birini değiştirmek isterseniz seçin **performans Sihirbazını Başlat** yerine düğme.  
  
5.  Bölümündeki yönergeleri **SharePoint uygulaması çalıştıran** bölümünde, bu konudaki daha önce.  
  
     Bu özellik, boşta döngü çağrısı ortadan göre çok daha hızlı etkinleştirmelisiniz. Örnek profili oluşturma raporu bu yansıtmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Performans Gezgini](/visualstudio/profiling/performance-explorer)   
 [Performans oturumuna genel bakış](/visualstudio/profiling/performance-session-overview)   
 [Performans profili oluşturma Başlangıç Kılavuzu](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Visual Studio Profiler uygulama performans sorunlarını bulun](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
