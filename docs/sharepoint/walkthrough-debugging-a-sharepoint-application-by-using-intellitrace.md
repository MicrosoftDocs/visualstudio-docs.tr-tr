---
title: "İzlenecek yol: IntelliTrace'i kullanarak SharePoint uygulamasında hata ayıklama | Microsoft Docs"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 59f801c79c8bb19a63064bdac2fe717ee3e3a845
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295592"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>İzlenecek yol: IntelliTrace'i kullanarak SharePoint uygulamasında hata ayıklama

IntelliTrace'i kullanarak SharePoint çözümleri daha kolay ayıklayabilirsiniz. Geleneksel hata ayıklayıcılar, geçerli şu anda yalnızca bir anlık görüntüsünü bir çözüm sağlar. Ancak, IntelliTrace, çözümünüzde oluştu geçmiş olaylar, bunlar oluştu ve koda gitmek bağlamı gözden geçirmek için kullanabilirsiniz.

 Bu yönerge, dağıtılmış uygulamalardan IntelliTrace verilerini toplamak için Microsoft Monitoring Agent'ı kullanarak bir SharePoint 2010 veya SharePoint 2013 proje Visual Studio'da hata ayıklama gösterir. Bu verileri analiz etmek için Visual Studio Enterprise'ı kullanmanız gerekir. Bu proje özelliği etkin olduğunda, görev listesi ve duyuru duyuruları listesine bir görev ekler. özellik alıcısı içerir. Özelliği devre dışı bırakıldığında, görevi tamamlandı olarak işaretlenir ve ikinci bir duyuru duyuruları listesine eklenir. Ancak, proje düzgün çalışmasını engelleyen bir mantıksal hatayla yordamı içerir. Bulun ve hatayı düzeltmek için IntelliTrace kullanarak.

 **İçin geçerlidir:** Visual Studio'da oluşturulan SharePoint 2010 ve SharePoint 2013 çözümleri için bu konudaki bilgiler, geçerlidir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [Özellik alıcısı oluşturma](#BKMK_CreateReceiver)

- [Özellik alıcısına kod ekleme](#BKMK_AddCode)

- [Test projesi](#BKMK_Test1)

- [Microsoft Monitoring Agent'ı kullanarak IntelliTrace verilerini toplama](#BKMK_CollectDiagnosticData)

- [SharePoint çözümünü düzeltmek ve hata ayıklama](#BKMK_DebugSolution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Windows ve SharePoint sürümleri desteklenir.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Özellik alıcısı oluşturma

İlk olarak, özellik alıcısı olan boş bir SharePoint projesi oluşturun.

1. Bir SharePoint 2010 veya SharePoint 2013 çözüm projesi oluşturun ve adlandırın **IntelliTraceTest**.

     **SharePoint Özelleştirme Sihirbazı** görünürse, hangi SharePoint sitesini projenizi ve çözümün güven düzeyini belirtebilirsiniz.

2. Seçin **Grup çözümü olarak Dağıt** seçenek düğmesini ve ardından **son** düğmesi.

     IntelliTrace sadece grup çözümlerini üzerinde çalışır.

3. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **özellikleri** düğümünü seçip **Özellik Ekle**.

     *Feature1.Feature* görünür.

4. Feature1.feature için kısayol menüsünü açın ve ardından **olay alıcısı Ekle** kod modülünde özelliğini eklemek için.

## <a name="add-code-to-the-feature-receiver"></a>Özellik alıcısına kod ekleme

Ardından, özellik alıcısı içindeki iki yöntem için kodu ekleyin: `FeatureActivated` ve `FeatureDeactivating`. Bir özellik etkin ya da SharePoint'te sırasıyla devre dışı olduğunda bu yöntemleri tetikler.

1. Üst kısmındaki `Feature1EventReceiver` sınıfı, alt site ve SharePoint sitesi belirtmeniz değişkenler bildirilmektedir aşağıdaki kodu ekleyin:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Değiştirin `FeatureActivated` yöntemini aşağıdaki kod ile:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
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
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Değiştirin `FeatureDeactivating` yöntemini aşağıdaki kod ile:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!"); 
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>Test projesi

Özellik alıcısına kod eklenir ve veri toplayıcısı çalışıyor, dağıtın ve düzgün çalışıp çalışmadığını test etmek için SharePoint çözümü çalıştırın.

> [!IMPORTANT]
> Bu örnekte, FeatureDeactivating olay işleyicisinde bir hata oluşturulur. Bu kılavuzda daha sonra bu hata, oluşturduğunuz veri toplayıcı .iTrace dosyasını kullanarak bulun.

1. Çözümü dağıtmak için SharePoint ve SharePoint sitesi bir tarayıcıda açın.

     Özelliği otomatik olarak etkinleştirir, duyuru ve bir görev eklemek, özellik alıcısı neden olur.

2. Duyuruları ve görev listelerinin içeriğini görüntüler.

     Adlı yeni bir duyuru Duyurular listesi olmalıdır **özelliği etkinleştirildi: IntelliTraceTest_Feature1**, ve görev listesi, adında yeni bir görev olmalıdır **özelliği devre dışı bırak: IntelliTraceTest_ Özellik1**. Bu öğelerden herhangi biri eksik özellik etkin olup olmadığını doğrulayın. Etkin değilse, bunu etkinleştirin.

3. Bu özellik aşağıdaki adımları gerçekleştirerek devre dışı bırakın:

   1. Üzerinde **Site eylemleri** SharePoint menüsünde **Site Ayarları**.

   2. Altında **Site eylemleri**, seçin **site özelliklerini Yönet** bağlantı.

   3. Yanındaki **IntelliTraceTest özellik1**, seçin **devre dışı bırak** düğmesi.

   4. Uyarı sayfasında, **bu özelliği devre dışı** bağlantı.

      FeatureDeactivating() olay işleyicisi, bir hata oluşturur.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Microsoft Monitoring Agent'ı kullanarak IntelliTrace verilerini toplama

Microsoft Monitoring Agent'ı SharePoint çalıştıran sisteminde yükleme yapıyorsanız, IntelliTrace döndüren genel bilgileri daha fazla özel veriler kullanarak SharePoint çözümleri ayıklayabilirsiniz. Aracı, Visual Studio'nun dışında SharePoint çözüm çalıştırmalarınızı çalışırken hata ayıklama bilgileri yakalamak için PowerShell cmdlet'lerini kullanarak çalışır.

> [!NOTE]
> Bu örnek için bu bölümdeki yapılandırma bilgilerini özeldir. Diğer yapılandırma seçenekleri hakkında daha fazla bilgi için bkz. [IntelliTrace collector kullanarak](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

1. SharePoint çalıştıran bilgisayarda [Microsoft İzleme Aracısı'nı ayarlayın ve çözümünüzü izlemek başlangıç](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

2. Özelliği devre dışı bırakın:

   1. Üzerinde **Site eylemleri** SharePoint menüsünde **Site Ayarları**.

   2. Altında **Site eylemleri**, seçin **site özelliklerini Yönet** bağlantı.

   3. Yanındaki **IntelliTraceTest özellik1**, seçin **devre dışı bırak** düğmesi.

   4. Uyarı sayfasında, **bu özelliği devre dışı** bağlantı.

      (Bu durumda, söz konusu FeatureDeactivating() olay işleyicisi hata) nedeniyle bir hata oluşur.

3. PowerShell penceresinde çalıştırın [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) SharePoint çözümünüzü yeniden .iTrace dosyası oluşturun ve izlemeyi durdurmak için komutu.

     **Stop-WebApplicationMonitoring***"\<SharePointSite >\\< SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>SharePoint çözümünü düzeltmek ve hata ayıklama

Artık SharePoint çözüm hatayı bulmak ve için Visual Studio'da IntelliTrace günlük dosyası görüntüleyebilirsiniz.

1. \IntelliTraceLogs klasöründe, Visual Studio'da .iTrace dosyasını açın.

     **IntelliTrace özeti** sayfası görüntülenir. Hata işlenmemiş olduğundan, bir SharePoint bağıntı kimliği (GUID) işlenmeyen özel durum alanında görünür **analiz** bölümü. Seçin **çağrı yığını** hatanın oluştuğu çağrı yığınını görüntülemek istediğiniz düğmesi.

2. Seçin **özel durum hata ayıkla** düğmesi.

     İstenirse, sembol dosyalarını yükleyin. İçinde **IntelliTrace** penceresinde özel durum olarak vurgulanır "sayıcı: önemli bir hata oluştu!".

     IntelliTrace penceresinde başarısız kodunu görüntülemek için özel durum seçin.

3. SharePoint çözüm açılırken ve ardından ya da kullanıma yorum veya kaldırarak hata düzeltme **throw** FeatureDeactivating() yordamı üst kısmındaki deyimi.

4. Visual Studio çözümü yeniden oluşturun ve SharePoint için yeniden dağıtın.

5. Bu özellik aşağıdaki adımları gerçekleştirerek devre dışı bırakın:

    1. Üzerinde **Site eylemleri** SharePoint menüsünde **Site Ayarları**.

    2. Altında **Site eylemleri**, seçin **site özelliklerini Yönet** bağlantı.

    3. Yanındaki **IntelliTraceTest özellik1**, seçin **devre dışı bırak** düğmesi.

    4. Uyarı sayfasında, **bu özelliği devre dışı** bağlantı.

6. Görev listesini açın ve doğrulayın **durumu** devre dışı bırak görev değerini "tamamlandı" ve kendi **% Complete** % 100 değerdir.

     Kod artık düzgün şekilde çalışır.

## <a name="see-also"></a>Ayrıca bkz.

[Doğrulayın ve SharePoint kodu hatalarını ayıklama](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[İzlenecek yol: Birim testleri kullanarak SharePoint kodunu doğrulayın.](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
