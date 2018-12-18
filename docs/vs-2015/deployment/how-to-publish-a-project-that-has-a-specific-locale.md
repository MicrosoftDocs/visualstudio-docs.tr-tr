---
title: 'Nasıl yapılır: özel yerel ayara sahip olan bir projeyi yayımlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: a08c7cc22129a783e692c437724114b3f44888a3
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607789"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Nasıl yapılır: Özel Yerel Ayara Sahip Olan Bir Projeyi Yayımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı yerel ayarlara sahip bileşenleri içeren bir uygulama için durumdur. Bu senaryoda, birkaç proje sahip bir çözüm oluşturun ve ardından her yerel ayar için ayrı projeler yayımlama. Bu yordam, bir makro 'tr' yerel ayarı kullanarak bir çözümde ilk projenizi yayımlamak için nasıl kullanılacağını gösterir. Bu yordamı 'tr' dışında bir yerel ayar ile deneyin istiyorsanız, ayarladığınızdan emin olun `localeString` (örneğin, 'de' veya 'de-DE') kullanarak yerel ayarına uyan makroda.  
  
> [!NOTE]
>  Bu makro kullandığınızda, yayımlama konumu geçerli bir URL ya da evrensel adlandırma kuralı (UNC) paylaşımı olmalıdır. Ayrıca, Internet Information Services (IIS) bilgisayarınızda yüklü olması gerekir. IIS yüklemek için **Başlat** menüsünü tıklatın **Denetim Masası**. Çift **Program Ekle veya Kaldır**. İçinde **Program Ekle veya Kaldır**, tıklayın **Windows Bileşenlerini Ekle/Kaldır**. İçinde **Windows Bileşenleri Sihirbazı'nı**seçin **Internet Information Services (IIS)** onay kutusuna **bileşenleri** listesi. Ardından **son** sihirbazı kapatın.  
  
### <a name="to-create-the-publishing-macro"></a>Yayımlama makro oluşturmak için  
  
1.  Makro Gezgini açmak için **Araçları** menüsünde **makroları**ve ardından **Macro Gezgini**.  
  
2.  Yeni bir makro modülü oluşturun. Makro Gezgini'nde seçin **Mymacros'u**. Üzerinde **Araçları** menüsünde **makroları**ve ardından **yeni makrosu modül**. Modül adı **PublishSpecificCulture olarak**.  
  
3.  Makro Gezgini'nde **Mymacros'u** düğümünü ve ardından açın **PublishAllProjects** çift tıklayarak Modülü (veya **Araçları** menüsünde, **Makroları**ve ardından **Macros IDE**).  
  
4.  Sonra modülü Macros IDE içinde aşağıdaki kodu ekleyin `Import` ifadeleri:  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certificate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  IDE makroları kapatın. Visual Studio'da odağa döndürür.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Belirli bir yerel ayar için bir projeyi yayımlamak için  
  
1.  Bir Visual Basic Windows uygulaması projesi oluşturmak için **dosya** menüsünde **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Windows uygulama** gelen **Visual Basic** düğümü. Projeyi adlandırın **PublishLocales'i**.  
  
3.  Form1'i tıklatın. İçinde **özellikleri** penceresinin altında **tasarım**, değiştirme **dil** özelliğinden **(varsayılan)** için **İngilizce**. Değişiklik **metin** özellik formun **MyForm**.  
  
     Gerekene kadar yerelleştirilmiş kaynak DLL'leri oluşturulmaz unutmayın. Örneğin, yeni yerel belirttikten sonra metin denetimlerinden birini ya da bir formu değiştirdiğinizde, bunlar oluşturulur.  
  
4.  Visual Studio IDE kullanarak PublishLocales'i yayımlayın.  
  
     İçinde **Çözüm Gezgini**, PublishLocales'i seçin. Üzerinde **proje** menüsünde **özellikleri**. Proje Tasarımcısı'nda üzerinde **Yayımla** sayfasında, bir yayımlama konumu belirtin **http://localhost/PublishLocales**ve ardından **Şimdi Yayımla**.  
  
     Yayımlama Web sayfası görüntülendiğinde, kapatın. (Bu adım için projeyi yayımlamanız yeterlidir; yüklemeniz gerekmez.)  
  
5.  Visual Studio komut istemi penceresinde makrosu çağırarak PublishLocales'i yeniden yayımlayın. Komut İstemi penceresini görüntülemek için **görünümü** menüsünde **diğer Windows** ve ardından **komut penceresi**, ya da CTRL + ALT + A tuşlarına basın. Komut İstemi penceresine `macros`; otomatik tamamlama, uygun makroları listesini sağlar. Aşağıdaki makro seçin ve ENTER tuşuna basın:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  Yayımlama işlemi başarılı olduğunda, "yayınlama için PublishLocales\PublishLocales.vbproj başarılı. belirten bir ileti oluşturur Yayımlama dili 'tr' oluştu. " Tıklayın **Tamam** ileti kutusunda. Yayımlama Web sayfası görüntülendiğinde **yükleme**.  
  
7.  C:\Inetpub\wwwroot\PublishLocales\en içine bakın. Yüklenen dosyalar bildirimleri, setup.exe ve yerelleştirilmiş kaynak DLL'si yanı sıra Yayımla Web sayfası dosyası gibi görmeniz gerekir. (Varsayılan olarak, ClickOnce ve exe ve dll .deploy uzantısını ekler; bu dağıtımdan sonra bu uzantıyı kaldırabilirsiniz.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Makrolar geliştirme ortamı](http://msdn.microsoft.com/en-us/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Makro Gezgini penceresi](http://msdn.microsoft.com/en-us/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [Nasıl yapılır: Düzenle ve makroları program aracılığıyla oluşturma](http://msdn.microsoft.com/en-us/6716f820-1feb-48ad-a718-27eb6b473c5a)



