---
title: 'İzlenecek yol: öğe şablonu ile özel bir eylem proje öğesi oluşturma, bölüm 2 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c37ab6f42be8e363dcba8a3e2aa6ef78816bff0
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296248"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>İzlenecek yol: bir öğe şablonu, bölüm 2 ile özel bir eylem proje öğesi oluşturma
  Özel bir SharePoint proje öğesi türünü tanımlar ve Visual Studio'da bir öğe şablonunu ilişkilendirmek sonra şablon için bir sihirbaz sağlamak isteyebilirsiniz. Sihirbaz, şablonunuzu yeni bir proje öğesi örneğini bir projeye eklemek için kullandıkları, kullanıcılardan bilgi toplamak için kullanabilirsiniz. Topladığınız bilgiler, proje öğesini başlatmak için kullanılabilir.  
  
 Bu kılavuzda, örnekte gösterildiği özel bir eylem proje öğesi için bir sihirbaz ekleyeceksiniz [izlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Bir kullanıcı bir SharePoint projesine özel bir eylem proje öğesi eklediğinde, sihirbaz özel eylem (örneğin, konumunu ve son kullanıcı seçtiğinde gidilecek URL'yi) hakkında bilgi toplar ve bu bilgileri ekler *Elements.xml* dosyasında yeni proje öğesi.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Bir öğe şablonu ile ilişkili özel bir SharePoint proje öğesi türü için bir sihirbaz oluşturuluyor.  
  
-   Özel sihirbaz Visual Studio'da SharePoint Proje öğeleri için yerleşik sihirbazları benzer kullanıcı Arabirimi tanımlama.  
  
-   SharePoint proje dosyaları sihirbazda topladığınız verilerle başlatmak için değiştirilebilir parametreler kullanma.  
  
-   Hata ayıklama ve test Sihirbazı.  
  
> [!NOTE]  
>  Bir örnekten indirebileceğiniz [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , özel etkinlikler için iş akışı oluşturma işlemi gösterilmektedir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu izlemeden için öncelikle CustomActionProjectItem çözüm tamamlayarak oluşturmanız gerekir [izlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler de aşağıdakiler gerekir:  
  
- Windows, SharePoint ve Visual Studio'nun desteklenen sürümleri.
  
- Visual Studio SDK. Bu izlenecek yolda **VSIX projesi** proje öğesini dağıtmak üzere bir VSIX paketi oluşturmak için SDK'sı şablonunda. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Aşağıdaki kavramları bilgisi yardımcı, ancak gerekli değildir, bu izlenecek yolu tamamlamak için:  
  
- Visual Studio'da proje ve öğe şablonlarını sihirbazları. Daha fazla bilgi için [nasıl yapılır: Proje şablonlarıyla kullanma sihirbazları](../extensibility/how-to-use-wizards-with-project-templates.md) ve <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimi.  
  
- SharePoint özel eylemler. Daha fazla bilgi için [özel eylem](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="create-the-wizard-project"></a>Sihirbazı proje oluşturma
 Bu izlenecek yolu tamamlamak için bir proje oluşturduğunuz CustomActionProjectItem çözüme eklemelisiniz [izlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). U uygulayacaksınız <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirim ve kullanıcı Arabirimi Sihirbazı bu projeyi tanımlayın.  
  
#### <a name="to-create-the-wizard-project"></a>Sihirbazı proje oluşturmak için  
  
1.  Visual Studio'da CustomActionProjectItem çözümü açın  
  
2.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
3.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **Windows** düğümü.  
  
4.  Üst kısmındaki **yeni proje** iletişim kutusunda, emin **.NET Framework 4.5** .NET Framework sürümleri listesinde seçilir.  
  
5.  Seçin **WPF kullanıcı denetimi Kitaplığı** proje şablonu, projeyi adlandırın **ItemTemplateWizard**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **ItemTemplateWizard** çözüme bir proje.  
  
6.  UserControl1 öğenin projeden silin.  
  
## <a name="configure-the-wizard-project"></a>Sihirbaz projesini yapılandırma
 Sihirbaz oluşturmadan önce bir Windows Presentation Foundation (WPF) penceresi, bir kod dosyası ve bütünleştirilmiş kod başvuruları projeye eklemeniz gerekir.  
  
#### <a name="to-configure-the-wizard-project"></a>Sihirbaz projesini yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünden açın **ItemTemplateWizard** proje düğümünü ve ardından **özellikleri**.  
  
2.  İçinde **Proje Tasarımcısı**, hedef çerçeveyi .NET Framework 4.5 olarak ayarlandığından emin olun.  
  
     Visual C# projeleri için bu değeri ayarlayabilirsiniz **uygulama** sekmesi. Visual Basic projeleri için bu değeri ayarlayabilirsiniz **derleme** sekmesi. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  İçinde **ItemTemplateWizard** eklemek, proje bir **pencere (WPF)** öğesi projeye ekleyin ve ardından öğe adı **WizardWindow**.  
  
4.  CustomActionWizard ve dizeleri adlı iki kod dosyasını ekleyin.  
  
5.  Kısayol menüsünü açın **ItemTemplateWizard** proje ve ardından **Başvuru Ekle**.  
  
6.  İçinde **başvuru Yöneticisi - ItemTemplateWizard** iletişim kutusunun **derlemeleri** düğümünü seçin **uzantıları** düğümü.  
  
7.  Ve aşağıdaki derlemelerin yanında bulunan onay kutularını işaretleyin ve ardından **Tamam** düğmesi:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  İçinde **Çözüm Gezgini**, **başvuruları** ItemTemplateWizard proje için klasör seçme **EnvDTE** başvuru.  
  
9. İçinde **özellikleri** penceresinde değiştirin **birlikte çalışma türlerini katıştır** özelliğini **False**.  
  
## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Özel Eylemler için kimlik dizeleri ve varsayılan konumunu tanımlayın
 Her özel eylem bir konum ve belirtilen kimliği olan `GroupID` ve `Location` özniteliklerini `CustomAction` öğesinde *Elements.xml* dosya. Bu adımda, bazı ItemTemplateWizard projesinde bu öznitelikler için geçerli dizeleri tanımlayın. Bu izlenecek yolu tamamlamak, bu dizeler yazılan *Elements.xml* kullanıcılar Sihirbazı'nda bir konum ve kimlik belirttiğinizde özel eylem proje öğesi dosya.  
  
 Kolaylık olması için bu örnek yalnızca bir alt kümesini kimlikleri ve kullanılabilir varsayılan konumları destekler. Tam bir listesi için bkz [varsayılan özel eylem konumları ve kimlikleri](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Varsayılan konum ve kimlik dizeleri tanımlamak için
  
1.  Açık.  
  
2.  İçinde **ItemTemplateWizard** proje, dizeleri kod dosyasındaki kodu aşağıdaki kodla değiştirin.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="create-the-wizard-ui"></a>Sihirbaz kullanıcı Arabirimi oluşturma
 Kullanıcı Arabirimi Sihirbazı tanımlamak için XAML ekleyin ve bazı denetimleri sihirbazda kimliği dizelere bağlamak için kod ekleyin. Visual Studio'da SharePoint projeleri için yerleşik sihirbaz, Oluşturma Sihirbazı'nı benzer.  
  
#### <a name="to-create-the-wizard-ui"></a>Sihirbaz kullanıcı Arabirimi oluşturmak için
  
1.  İçinde **ItemTemplateWizard** ilişkin kısayol menüsünü açın, proje **WizardWindow.xaml** dosya ve ardından **açın** tasarımcıda açmak için.  
  
2.  XAML Görünümü'nde geçerli XAML aşağıdaki XAML ile değiştirin. XAML başlık içerir, denetimleri özel eylem ve Gezinti düğmelerinin pencerenin alt kısmındaki davranışını belirtmek için bir kullanıcı Arabirimi tanımlar.  
  
    > [!NOTE]  
    >  Bu kodu ekledikten sonra projenizi bazı derleme hataları olacaktır. Sonraki adımlarda kod eklediğinizde, bu hatalar kaybolur.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  Bu XAML içinde oluşturulan pencerenin türetilir <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> temel sınıfı. Visual Studio için özel bir WPF iletişim kutusu eklediğinizde, bu sınıf diğer iletişim kutuları Visual Studio ile tutarlı bir stil sağlamak için ve kalıcı iletişim kutuları ile oluşabilecek sorunları önlemek için iletişim kutusu türetilmesi öneririz. Daha fazla bilgi için [oluşturma ve yönetme kalıcı iletişim kutuları](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Visual Basic projesi geliştiriyorsanız kaldırmak `ItemTemplateWizard` ad alanından `WizardWindow` sınıf adını `x:Class` özniteliği `Window` öğesi. XAML ilk satırında öğesidir. İşiniz bittiğinde, ilk satırı aşağıdaki koda benzemelidir:  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  WizardWindow.xaml dosyası için arka plan kod dosyasında geçerli kodu aşağıdaki kodla değiştirin.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implement-the-wizard"></a>Uygulama Sihirbazı
 Sihirbaz işlevselliğini uygulayarak tanımlama <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimi.  
  
#### <a name="to-implement-the-wizard"></a>Sihirbazı'nı uygulamak için  
  
1.  İçinde **ItemTemplateWizard** projesini açarsanız **CustomActionWizard** kod dosyası ve ardından bu dosyadaki geçerli kodu aşağıdaki kodla değiştirin:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu aşamada izlenecek yolda, sihirbaz için kodun tümü artık projedir. Hata olmadan derlediğinden emin olmak için projeyi derleyin.  
  
#### <a name="to-build-your-project"></a>Projenizi yapılandırmak için  
  
1.  Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
## <a name="associate-the-wizard-with-the-item-template"></a>Sihirbazı öğe şablonu ile ilişkilendirme
 Sihirbaz uyguladıysanız, kendisiyle ilişkilendirmelisiniz **özel eylem** üç ana adımları tamamlayarak öğe şablonu:  
  
1.  Sihirbaz derlemeyi güçlü bir ad ile oturum açın.  
  
2.  Ortak anahtarın Sihirbazı derleme için belirteci alın.  
  
3.  .Vstemplate dosyasında Sihirbazı derlemesine bir başvuru eklemek **özel eylem** öğe şablonu.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Sihirbazı derlemeyi bir katı adla imzalamak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünden açın **ItemTemplateWizard** proje düğümünü ve ardından **özellikleri**.  
  
2.  Üzerinde **imzalama** sekmesinde **derlemeyi imzalamayı** onay kutusu.  
  
3.  İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde  **\<yeni … >**.  
  
4.  İçinde **katı ad anahtarı oluştur** iletişim kutusunda, temiz bir ad girin **anahtar dosyamı bir parolayla korumak** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
5.  Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Ortak anahtarın Sihirbazı derleme için belirteci almak için  
  
1.  Bir Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın. komut, değiştirme *PathToWizardAssembly* ItemTemplateWizard.dll derlemesi ItemTemplateWizard projenin geliştirme için tam yoluyla bilgisayar.  
  
    ```xml  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Ortak anahtar belirteci için *ItemTemplateWizard.dll* derleme, Visual Studio komut istemi penceresine yazılır.  
  
2.  Visual Studio komut istemi penceresini açık tutun. Sonraki yordamı tamamlamak için ortak anahtar belirteci gerekir.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.Vstemplate dosyasında Sihirbazı derlemesine bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, genişletme **ItemTemplate** proje düğümünü ve ardından açın *ItemTemplate.vstemplate* dosya.  
  
2.  Dosyanın sonuna, aşağıdaki ekleyin `WizardExtension` öğesi arasında `</TemplateContent>` ve `</VSTemplate>` etiketler. Değiştirin *YourToken* değerini `PublicKeyToken` özniteliği ile önceki yordamda aldığınız ortak anahtar belirteci.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Hakkında daha fazla bilgi için `WizardExtension` öğesi bkz [WizardExtension öğesi &#40;Visual Studio şablonları&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Dosyayı kaydedin ve kapatın.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Değiştirilebilir parametreler için ekleme *Elements.xml* öğe şablonu dosyasında
 Eklemek için birkaç değiştirilebilir parametreler *Elements.xml* ItemTemplate proje dosyasında. Bu parametreleri olarak başlatılır `PopulateReplacementDictionary` yönteminde `CustomActionWizard` daha önce tanımladığınız sınıf. Bir kullanıcı, bir özel eylem proje öğesi projeye eklediğinde, Visual Studio bu parametreleri otomatik olarak değiştirir. *Elements.xml* sihirbazda belirtilen değerlerle yeni proje öğesi dosya.  
  
 Bir parametredir başlar ve dolar işareti ($) karakteri ile biten bir belirteçtir. Kendi değiştirilebilir parametreler tanımlanmasına ek olarak, SharePoint Proje sistemi başlatır ve yerleşik parametrelerini kullanabilirsiniz. Daha fazla bilgi için [değiştirilebilir parametreler](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Değiştirilebilir parametreler için eklenecek *Elements.xml* dosyası
  
1.  ItemTemplate projenin içeriğini değiştirin *Elements.xml* aşağıdaki XML dosyasıyla.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Yeni XML değerlerini değiştirir `Id`, `GroupId`, `Location`, `Description`, ve `Url` değiştirilebilir parametreler için öznitelikleri.  
  
2.  Dosyayı kaydedin ve kapatın.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>VSIX Paketi Ekleme Sihirbazı
 Proje öğesi içeren VSIX paketi ile dağıtılır, VSIX projesinde source.extension.vsixmanifest dosyası içinde bir sihirbaz projesinin başvuru ekleyin.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>VSIX Paketi Sihirbazı'nı eklemek için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünden açın **source.extension.vsixmanifest** CustomActionProjectItem projeye dosya ve ardından **açın** açmak için bildirim düzenleyicisini dosyasında.  
  
2.  Bildirim düzenleyicisinde seçin **varlıklar** sekmesine ve ardından seçin **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
3.  İçinde **türü** listesinde **Microsoft.VisualStudio.Assembly**.  
  
4.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
5.  İçinde **proje** listesinde **ItemTemplateWizard**ve ardından **Tamam** düğmesi.  
  
6.  Menü çubuğunda, **derleme** > **Çözümü Derle**ve ardından çözüm hata olmadan derlediğinden emin olun.  
  
## <a name="test-the-wizard"></a>Test Sihirbazı
 Artık Sihirbazı'nı test etmek hazırsınız. Visual Studio'nun deneysel örneğinde CustomActionProjectItem çözüme hata ayıklaması için ilk olarak başlatın. Ardından sihirbaz özel eylem proje öğesi için bir SharePoint projesi Visual Studio'nun deneysel örneğinde test. Son olarak, derleme ve özel eylemin beklendiği gibi çalıştığını doğrulamak için SharePoint Proje çalıştırın.  
  
#### <a name="to-start-to-debug-the-solution"></a>Çözüm hata ayıklamayı başlatmak için  
  
1.  Yönetici kimlik bilgileriyle Visual Studio'yu yeniden başlatın ve ardından CustomActionProjectItem çözümü açın.  
  
2.  ItemTemplateWizard projesinde CustomActionWizard kod dosyasını açın ve ardından ilk kod satırına bir kesme noktası ekleyin `RunStarted` yöntemi.  
  
3.  Menü çubuğunda, **hata ayıklama** > **özel durumları**.  
  
4.  İçinde **özel durumları** iletişim kutusunda, emin **sayıcı** ve **kullanıcı-işlenmemiş** onay kutularını **ortak dil çalışma zamanı özel durumları**temizlenir ve ardından **Tamam** düğmesi.  
  
5.  Seçim yaparak hata ayıklamayı Başlat **F5** anahtar, veya, menü çubuğundan seçme **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
     Visual Studio, eylem proje Item\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom için uzantıyı yükleyen ve Visual Studio'nun deneysel örneği başlar. Proje öğesi bu Visual Studio örneğinde test edeceğiz.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Sihirbaz Visual Studio'da Test etmek için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **dosya** > **yeni** > **proje**.  
  
2.  Genişletin **Visual C#** veya **Visual Basic** (dile bağlı olarak, öğe şablonu destekleyen), düğümünü **SharePoint** düğümünü seçip **2010** düğümü.  
  
3.  Proje şablonları listesinde seçin **SharePoint 2010 projesi**, projeyi adlandırın **CustomActionWizardTest**ve ardından **Tamam** düğmesi.  
  
4.  İçinde **SharePoint Özelleştirme Sihirbazı**, hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin ve ardından **son** düğmesi.  
  
5.  İçinde **Çözüm Gezgini**, proje düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni öğe**.  
  
6.  İçinde **Yeni Öğe Ekle - CustomItemWizardTest** iletişim kutusunda **SharePoint** düğümünü ve ardından **2010** düğümü.  
  
7.  Proje öğeleri listesinde seçin **özel eylem** öğesi ekleyin ve ardından **Ekle** düğmesi.  
  
8.  Visual Studio'nun diğer örneğindeki kodun daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `RunStarted` yöntemi.  
  
9. Seçerek proje hatalarını ayıklamaya devam **F5** anahtar veya, menü çubuğundan seçme **hata ayıklama** > **devam**.  
  
     SharePoint Özelleştirme Sihirbazı görünür.  
  
10. Altında **konumu**, seçin **listesini düzenle** seçenek düğmesini.  
  
11. İçinde **Grup Kimliği** listesinde **iletişimleri**.  
  
12. İçinde **başlık** kutusuna **SharePoint Geliştirici Merkezi**.  
  
13. İçinde **açıklama** kutusuna **SharePoint Geliştirici Merkezi Web sitesi açılır**.  
  
14. İçinde **URL** kutusuna **https://docs.microsoft.com/sharepoint/dev/** ve ardından **son** düğmesi.  
  
     Visual Studio adlı bir öğe ekler **CustomAction1** açar ve proje için *Elements.xml* düzenleyicideki dosyada. Doğrulayın *Elements.xml* sihirbazda belirttiğiniz değerleri içerir.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Özel eylem, SharePoint'te test etmek için  
  
1.  Visual Studio'nun deneysel örneğinde seçin **F5** tuşunu veya menü çubuğunda, **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
     Özel eylem paketlenir ve tarafından belirtilen SharePoint sitesine dağıtılan **Site URL'si** projeyi ve web tarayıcısı özelliği bu sitenin varsayılan sayfasına açılır.  
  
    > [!NOTE]  
    >  Varsa **betik hata ayıklamasını devre dışı bırakılmış** iletişim kutusu görüntülenirse, seçin **Evet** düğmesi.  
  
2.  SharePoint sitesinin listeleri alanında seçin **görevleri** bağlantı.  
  
     **Görevleri - tüm** sayfası görüntülenir.  
  
3.  Üzerinde **liste Araçları** sekmesini Şeritine seçin **listesi** sekmesinde, daha sonra **ayarları** Grup öğesini **listesi ayarları**.  
  
     **Listesi ayarları** sayfası görüntülenir.  
  
4.  Altında **iletişimleri** sayfanın üst kısımda başlığı seçin **SharePoint Geliştirici Merkezi** bağlantı, tarayıcının Web sitesi açılır doğrulayın https://docs.microsoft.com/sharepoint/dev/ve sonra Tarayıcıyı kapatın.  
  
## <a name="cleaning-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme
 Proje öğesi testi tamamladıktan sonra proje öğesi şablonu Visual Studio'nun deneysel örneği kaldırın.  
  
#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Uzantılar listesinde seçin **özel eylem proje öğesi** uzantısı seçip **kaldırma** düğmesi.  
  
3.  Görünen iletişim kutusunda **Evet** uzantıyı kaldırın ve ardından istediğinizi onaylamak için düğmeyi **şimdi yeniden Başlat** kaldırma işlemini tamamlamak için düğme.  
  
4.  (Deneysel örneği ve Visual Studio'nun CustomActionProjectItem çözüm açık olduğu örneği) Visual Studio'nun her iki örneklerini kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İzlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Öğe şablonları ve SharePoint Proje öğeleri için proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio Şablon Şeması Başvurusu](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Nasıl yapılır: sihirbazları proje şablonlarıyla kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Varsayılan özel eylem konumları ve kimlikleri](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
