---
title: 'İzlenecek yol: Proje şablonu ile bir Site sütunu proje öğesi oluşturma, bölüm 2 | Microsoft Docs'
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
ms.openlocfilehash: d4512dc15d394cdf2442d8bfcf440ccb31623a29
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942081"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>İzlenecek yol: bir proje şablonu, bölüm 2 ile bir site sütunu proje öğesi oluşturma
  Özel bir SharePoint proje öğesi türünü tanımlar ve bir proje şablonu Visual Studio'da ilişkilendirmek sonra şablon için bir sihirbaz sağlamak isteyebilirsiniz. Sihirbaz, şablonu proje öğesi içeren yeni bir proje oluşturmak için kullanıldığında, kullanıcılardan bilgi toplamak için kullanabilirsiniz. Topladığınız bilgiler, proje öğesini başlatmak için kullanılabilir.  
  
 Bu kılavuzda, örnekte gösterildiği bir Site sütunu proje şablonu için bir sihirbaz ekleyeceksiniz [izlenecek yol: bir proje şablonu, bölüm 1 ile bir Site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Bir kullanıcı bir Site sütunu proje oluşturduğu zaman, sihirbaz site sütunu (örneğin, kendi temel türü ve grup) hakkında bilgi toplar ve bu bilgileri ekler *Elements.xml* yeni proje dosyasında.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Bir proje şablonu ile ilişkili özel bir SharePoint proje öğesi türü için bir sihirbaz oluşturuluyor.  
  
-   Özel sihirbaz Visual Studio'da SharePoint projeleri için yerleşik sihirbazları benzer kullanıcı Arabirimi tanımlama.  
  
-   İki oluşturma *SharePoint komutları* Sihirbazı çalıştığı sırada yerel SharePoint sitesini çağırmak için kullanılır. SharePoint, SharePoint sunucusu nesne modelinde API'leri çağırmak için Visual Studio uzantıları tarafından kullanılan yöntemleri komutlardır. Daha fazla bilgi için [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   SharePoint proje dosyaları sihirbazda topladığınız verilerle başlatmak için değiştirilebilir parametreler kullanma.  
  
-   Her yeni Site sütunu proje örneğinde yeni bir .snk dosyası oluşturuluyor. Bu dosya, böylece SharePoint çözüm derlemesini küresel derleme önbelleğine dağıtılabilir çıkış projesi imzalamak için kullanılır.  
  
-   Hata ayıklama ve test Sihirbazı.  
  
> [!NOTE]  
> Bir dizi örnek iş akışları için [SharePoint iş akışı örnekleri](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu izlemeden için öncelikle SiteColumnProjectItem çözüm tamamlayarak oluşturmanız gerekir [izlenecek yol: bir proje şablonu, bölüm 1 ile bir Site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler de aşağıdakiler gerekir:  
  
- Windows, SharePoint ve Visual Studio'nun desteklenen sürümleri.
  
- Visual Studio SDK. Bu izlenecek yolda **VSIX projesi** proje öğesini dağıtmak üzere bir VSIX paketi oluşturmak için SDK'sı şablonunda. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Aşağıdaki kavramları bilgisi yardımcı, ancak gerekli değildir, bu izlenecek yolu tamamlamak için:  
  
- Visual Studio'da proje ve öğe şablonlarını sihirbazları. Daha fazla bilgi için [nasıl yapılır: Proje şablonlarıyla kullanma sihirbazları](../extensibility/how-to-use-wizards-with-project-templates.md) ve <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimi.  
  
- SharePoint için site sütunları. Daha fazla bilgi için [sütunları](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
## <a name="understand-the-wizard-components"></a>Sihirbaz bileşenlerini anlama
 Bu izlenecek yolda gösterilen Sihirbazı çeşitli bileşenler bulunur. Aşağıdaki tabloda, bu bileşenler açıklanmaktadır.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Sihirbaz uygulamasını|Adlı bir sınıf budur `SiteColumnProjectWizard`, uygulayan <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimi. Bu arabirim, sihirbaz başladığında ve bittiğinde ve Sihirbazı sırasında belirli zamanlarda çalıştığında Visual Studio çağırdığı yöntemleri tanımlar.|  
|Kullanıcı Arabirimi Sihirbazı|Bu adlı bir WPF tabanlı penceresi, `WizardWindow`. Bu pencere adlı iki kullanıcı denetimleri içeren `Page1` ve `Page2`. Bu kullanıcı denetimleri, sihirbazın iki sayfaları temsil eder.<br /><br /> Bu izlenecek yolda, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> sihirbaz uygulamasını yöntemi, kullanıcı Arabirimi Sihirbazı görüntülenir.|  
|Veri modeli Sihirbazı|Bu adlı bir aracı, sınıftır `SiteColumnWizardModel`, kullanıcı Arabirimi Sihirbazı ve sihirbaz uygulamasını arasında bir katmanı sağlar. Bu örnek, sihirbaz uygulamasını ve birbirinden Sihirbazı kullanıcı Arabirimi soyut yardımcı olmak için bu sınıfı kullanır; Bu sınıf, gerekli bir bileşen tüm sihirbazları değil.<br /><br /> Bu kılavuzda, sihirbaz uygulamasını başarılı bir `SiteColumnWizardModel` kullanıcı Arabirimi Sihirbazı gösterildiğinde Sihirbazı penceresine nesne. Kullanıcı Arabirimi Sihirbazı kullanıcı Arabiriminde denetimlerin değerleri kaydedin ve giriş site URL'SİNİN geçerli olduğu doğrulanıyor gibi görevleri gerçekleştirmek için bu nesnenin yöntemleri kullanır. Kullanıcı Sihirbaz sonlandıktan sonra sihirbaz uygulamasını kullanan `SiteColumnWizardModel` kullanıcı arabirimini son durumunu belirlemek için nesne.|  
|Proje imzalama Yöneticisi|Bu adlı bir yardımcı sınıfıdır `ProjectSigningManager`, her yeni proje örneğinde yeni bir key.snk dosyası oluşturmak için Sihirbazı uygulaması tarafından kullanılır.|  
|SharePoint komutları|Sihirbaz çalıştırılırken yerel SharePoint sitesini çağırmak için Sihirbazı veri modeli tarafından kullanılan yöntemleri şunlardır. SharePoint komutları .NET Framework 3.5 hedeflemesi gerekir çünkü bu komutları sihirbaz kodu geri kalanından farklı bir derleme için uygulanır.|  
  
## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için birkaç proje oluşturduğunuz SiteColumnProjectItem çözüme eklemeniz gerekir [izlenecek yol: bir proje şablonu, bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
- Bir WPF projesi. U uygulayacaksınız <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirim ve kullanıcı Arabirimi Sihirbazı bu projeyi tanımlayın.  
  
- SharePoint komutları tanımlayan bir sınıf kitaplığı projesi. Bu projenin.NET Framework 3.5 hedeflemesi gerekir.  
  
  İzlenecek yol, proje oluşturmaya başlayın.  
  
#### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için
  
1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], SiteColumnProjectItem çözümü açın.  
  
2.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SiteColumnProjectItem** çözüm düğümüne seçin **Ekle**ve ardından **YeniProje**.  
  
3.  Üst kısmındaki **Yeni Proje Ekle** iletişim kutusunda, emin **.NET Framework 4.5** .NET Framework sürümleri listesinde seçilir.  
  
4.  Genişletin **Visual C#** düğümü veya **Visual Basic** düğümünü seçip **Windows** düğümü.  
  
5.  Proje şablonları listesinde seçin **WPF kullanıcı denetimi Kitaplığı**, projeyi adlandırın **ProjectTemplateWizard**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **ProjectTemplateWizard** çözüme ve varsayılan UserControl1.xaml dosyasını açar.  
  
6.  UserControl1.xaml dosyayı projeden silin.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projeyi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, SiteColumnProjectItem çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  Üst kısmındaki **Yeni Proje Ekle** iletişim kutusunda **.NET Framework 3.5** .NET Framework sürümleri listesinde.  
  
3.  Genişletin **Visual C#** düğümü veya **Visual Basic** düğümünü seçip **Windows** düğümü.  
  
4.  Seçin **sınıf kitaplığı** proje şablonu, projeyi adlandırın **SharePointCommands**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **SharePointCommands** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
5.  Projeden Class1 kod dosyasını silin.  
  
## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Sihirbaz oluşturmadan önce bazı kod dosyaları ve projeler için derleme başvuruları eklemeniz gerekir.  
  
#### <a name="to-configure-the-wizard-project"></a>Sihirbaz projesini yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProjectTemplateWizard** proje düğümünü ve ardından **özellikleri**.  
  
2.  İçinde **Proje Tasarımcısı**, seçin **uygulama** Visual C# projesi için sekmesinde veya **derleme** Visual Basic projesi için sekmesinde.  
  
3.  Hedef çerçeveyi .NET Framework 4.5 değil .NET Framework 4.5 istemci profili ayarlanmış olduğundan emin olun.  
  
     Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Kısayol menüsünü açın **ProjectTemplateWizard** projesinin **Ekle**ve ardından **yeni öğe**.  
  
5.  Seçin **pencere (WPF)** öğe, öğe adı **WizardWindow**ve ardından **Ekle** düğmesi.  
  
6.  İki ekleme **kullanıcı denetimi (WPF)** proje öğeleri ve bunları **Sayfa1** ve **Page2**.  
  
7.  Dört kod dosyaları projeye ekleyin ve bunları aşağıdaki adlar verin:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Kısayol menüsünü açın **ProjectTemplateWizard** proje düğümünü ve ardından **Başvuru Ekle**.  
  
9. Genişletin **derlemeleri** düğümünü seçin **uzantıları** düğüm ve aşağıdaki derlemelerin yanında bulunan onay kutularını seçin:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Seçin **Tamam** düğmesini derlemeleri projeye ekleyin.  
  
11. İçinde **Çözüm Gezgini**altında **başvuruları** klasör **ProjectTemplateWizard** projesinin **EnvDTE**.  
  
12. İçinde **özellikleri** penceresinde değiştirin **birlikte çalışma türlerini katıştır** özelliğini **False**.  
  
13. Visual Basic projesi geliştiriyorsanız ProjectTemplateWizard ad alanı projenize kullanarak aktarmak **Proje Tasarımcısı**.  
  
     Daha fazla bilgi için [nasıl yapılır: ekleme veya içeri aktarılan ad alanlarını kaldırma &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointcommands projeyi yapılandırmak için
  
1.  İçinde **Çözüm Gezgini**, seçin **SharePointCommands** proje düğümü.  
  
2.  Menü çubuğunda, **proje**, **varolan öğeyi Ekle**.  
  
3.  İçinde **varolan öğeyi Ekle** iletişim kutusu, ProjectTemplateWizard proje için kod dosyaları içeren klasöre gidin ve ardından **CommandIds** kod dosyası.  
  
4.  Yanındaki oku seçin **Ekle** düğmesine ve ardından **bağlantı olarak ekleme** seçeneğini belirleyin.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kod dosyasına ekler **SharePointCommands** projesi bir bağlantı olarak. Kod dosyası bulunan **ProjectTemplateWizard** proje, ancak kodu dosyasında da derlendiğinde **SharePointCommands** proje.  
  
5.  İçinde **SharePointCommands** proje, komutları adlı başka bir kod dosyası ekleyin.  
  
6.  SharePointCommands projeyi seçin ve ardından, menü çubuğunda, **proje** > **Başvuru Ekle**.  
  
7.  Genişletin **derlemeleri** düğümünü seçin **uzantıları** düğüm ve aşağıdaki derlemelerin yanında bulunan onay kutularını seçin:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Seçin **Tamam** düğmesini derlemeleri projeye ekleyin.  
  
## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Sihirbaz modeli, imzalama Yöneticisi ve SharePoint komut kimlikleri oluşturma
 Örnekte aşağıdaki bileşenleri uygulamak için ProjectTemplateWizard proje kodu ekleyin:  
  
- SharePoint komut kimlikleri. Bu dizeler Sihirbazı'nı kullanan SharePoint komutları belirleyin. Bu kılavuzda daha sonra SharePointCommands projeye komutları uygulamak için kod ekleyeceksiniz.  
  
- Sihirbaz veri modeli.  
  
- Proje imzalama Yöneticisi.  
  
  Bu bileşenler hakkında daha fazla bilgi için bkz. [Sihirbazı bileşenlerini anlama](#wizardcomponents).  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>SharePoint komut kimlikleri tanımlamak için
  
1.  ProjectTemplateWizard proje CommandIds kod dosyasını açın ve ardından bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>Sihirbaz modeli oluşturmak için  
  
1.  SiteColumnWizardModel kod dosyasını açın ve bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>Proje imzalama Yöneticisi oluşturmak için  
  
1.  ProjectSigningManager kod dosyasını açın ve ardından bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="create-the-wizard-ui"></a>Sihirbaz kullanıcı Arabirimi oluşturma
 Kullanıcı Arabirimi Sihirbazı penceresinin ve sihirbaz sayfaları için kullanıcı Arabirimi sağlayan iki kullanıcı denetimleri tanımlamak için XAML ekleyin ve penceresi ve kullanıcı denetimleri davranışını tanımlamak için kodu ekleyin. Visual Studio'da SharePoint projeleri için yerleşik sihirbaz, Oluşturma Sihirbazı'nı benzer.  
  
> [!NOTE]  
>  XAML veya kod projenize ekledikten sonra aşağıdaki adımlarda, projenize bazı derleme hataları olacaktır. Sonraki adımlarda kod eklediğinizde, bu hatalar kaybolur.  
  
#### <a name="to-create-the-wizard-window-ui"></a>Sihirbazdan kullanıcı Arabirimi oluşturmak için
  
1.  ProjectTemplateWizard projesinde WizardWindow.xaml dosyası için kısayol menüsünü açın ve ardından **açın** tasarımcıda açmak için.  
  
2.  Tasarımcı XAML görünümünde geçerli XAML aşağıdaki XAML ile değiştirin. Bir başlık içeren bir kullanıcı Arabirimi XAML tanımlayan bir <xref:System.Windows.Controls.Grid> sihirbaz sayfaları içeren ve gezinti düğmeleri penceresinin en altında.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  Bu XAML içinde oluşturulan pencerenin türetilir <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> temel sınıfı. Visual Studio için özel bir WPF iletişim kutusu eklediğinizde, bu sınıftan başka bir Visual Studio iletişim kutusu ile tutarlı bir stil sağlamak için ve oluşabilecek kalıcı iletişim sorunlarını önlemek için iletişim kutusu türetilen öneririz. Daha fazla bilgi için [oluşturma ve yönetme kalıcı iletişim kutuları](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Visual Basic projesi geliştiriyorsanız kaldırmak `ProjectTemplateWizard` ad alanından `WizardWindow` sınıf adını `x:Class` özniteliği `Window` öğesi. XAML ilk satırında öğesidir. İşiniz bittiğinde, ilk satırın aşağıdaki örnekteki gibi görünmelidir.  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  WizardWindow.xaml dosyası için arka plan kod dosyasını açın.  
  
5.  Bu dosyanın içeriğini dışında değiştirin `using` aşağıdaki kod ile dosya üst kısmındaki bildirimleri.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>Sihirbazın ilk sayfasında kullanıcı Arabirimi oluşturmak için
  
1.  ProjectTemplateWizard projesinde Page1.xaml dosyası için kısayol menüsünü açın ve ardından **açın** kullanıcı denetimi Tasarımcısı'nda açın.  
  
2.  Tasarımcı XAML görünümünde geçerli XAML aşağıdaki XAML ile değiştirin. XAML, hata ayıklama için kullanmak istediğiniz yerel siteler URL'sini girebileceğiniz bir metin kutusu içeren bir kullanıcı Arabirimi tanımlar. Kullanıcı Arabirimi ile kullanıcılar projenin korumalı olup olmadığını belirtebilir seçenek düğmeleri de içerir.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Visual Basic projesi geliştiriyorsanız kaldırmak `ProjectTemplateWizard` ad alanından `Page1` sınıf adını `x:Class` özniteliği `UserControl` öğesi. XAML ilk satırında budur. İşiniz bittiğinde, ilk satırı aşağıdaki gibi görünmelidir.  
  
    ```xml  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Dışında Page1.xaml dosyasının içeriğini değiştirin `using` aşağıdaki kod ile dosya üst kısmındaki bildirimleri.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>Sihirbazın ikinci sayfasında kullanıcı Arabirimi oluşturmak için
  
1.  ProjectTemplateWizard projesinde Page2.xaml dosyası için kısayol menüsünü açın ve ardından **açın**.  
  
     Kullanıcı denetimi Tasarımcısı'nda açılır.  
  
2.  XAML Görünümü'nde geçerli XAML aşağıdaki XAML ile değiştirin. XAML site sütunu, site sütunu galeride görüntülenecek altında yerleşik veya özel bir grubu belirtmek için bir birleşik giriş kutusu ve site sütununun adını belirtmek için bir metin kutusu temel türünü seçmek için aşağı açılan listesini içeren bir kullanıcı Arabirimi tanımlar.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Visual Basic projesi geliştiriyorsanız kaldırmak `ProjectTemplateWizard` ad alanından `Page2` sınıf adını `x:Class` özniteliği `UserControl` öğesi. XAML ilk satırında budur. İşiniz bittiğinde, ilk satırı aşağıdaki gibi görünmelidir.  
  
    ```xml  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Dışında Page2.xaml dosyası için arka plan kod dosyasının içeriğini değiştirin `using` aşağıdaki kod ile dosya üst kısmındaki bildirimleri.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implement-the-wizard"></a>Uygulama Sihirbazı
 Sihirbaz ana işlevini uygulayarak tanımlama <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimi. Bu arabirim, sihirbaz başladığında ve bittiğinde ve Sihirbazı sırasında belirli zamanlarda çalıştığında Visual Studio çağırdığı yöntemleri tanımlar.  
  
#### <a name="to-implement-the-wizard"></a>Sihirbazı'nı uygulamak için  
  
1.  ProjectTemplateWizard projesinde SiteColumnProjectWizard kod dosyasını açın.  
  
2.  Bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="create-the-sharepoint-commands"></a>SharePoint komutları oluşturma
 SharePoint sunucusu nesne modeline çağrı iki özel komutlar oluşturur. Bir komut, kullanıcı sihirbazda türleri site URL'SİNİN geçerli olup olmadığını belirler. Kullanıcılar, yeni bir site sütunu için temel olarak kullanmak için hangisinin seçebilmeniz için diğer komutu tüm alan türleri belirtilen SharePoint sitesinden alır.  
  
#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutları tanımlamak için  
  
1.  İçinde **SharePointCommands** proje, komutları kod dosyasını açın.  
  
2.  Bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu aşamada izlenecek yolda, sihirbaz için kodun tümü artık projedir. Hata olmadan derlediğinden emin olmak için projeyi derleyin.  
  
#### <a name="to-build-your-project"></a>Projenizi yapılandırmak için  
  
1.  Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>Proje şablonundan key.snk dosya kaldırma
 İçinde [izlenecek yol: bir proje şablonu, bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), her bir Site sütunu proje örneği imzalamak için kullanılan bir key.snk dosyası oluşturduğunuz proje şablonu içerir. Sihirbaz, artık her proje için yeni bir key.snk dosyası oluşturur çünkü bu key.snk dosya artık gerekli değildir. Key.snk dosyanın proje şablonundan ve bu dosya başvuruları kaldırın.  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Proje şablonundan key.snk dosyayı kaldırmak için  
  
1.  İçinde **Çözüm Gezgini**altında **SiteColumnProjectTemplate** düğümü için kısayol menüsünü açın **key.snk** dosya ve ardından **Sil**.  
  
2.  Görünen onay iletişim kutusundaki seçin **Tamam** düğmesi.  
  
3.  Altında **SiteColumnProjectTemplate** düğümünün SiteColumnProjectTemplate.vstemplate dosyasını açın ve ardından aşağıdaki öğeyi kaldırın.  
  
    ```xml  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Dosyayı kaydedin ve kapatın.  
  
5.  Altında **SiteColumnProjectTemplate** düğümünün ProjectTemplate.csproj veya ProjectTemplate.vbproj dosyasını açın ve ardından aşağıdaki kaldırın `PropertyGroup` bu öğeden.  
  
    ```xml  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ``` 
  
6.  Aşağıdakileri kaldırın `None` öğesi.  
  
    ```xml  
    <None Include="key.snk" />  
    ```  
  
7.  Dosyayı kaydedin ve kapatın.  
  
## <a name="associating-the-wizard-with-the-project-template"></a>Sihirbaz proje şablonu ile ilişkilendirme
 Sihirbaz uyguladıysanız, Sihirbazı ile ilişkilendirmelisiniz **Site sütunu** proje şablonu. Bunu yapmak için tamamlamanız gereken üç yordamı vardır:  
  
1.  Sihirbaz derlemeyi güçlü bir ad ile oturum açın.  
  
2.  Ortak anahtarın Sihirbazı derleme için belirteci alın.  
  
3.  .Vstemplate dosyasında Sihirbazı derlemesine bir başvuru eklemek **Site sütunu** proje şablonu.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Sihirbazı derlemeyi bir katı adla imzalamak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProjectTemplateWizard** proje ve ardından **özellikleri**.  
  
2.  Üzerinde **imzalama** sekmesinde **derlemeyi imzalamayı** onay kutusu.  
  
3.  İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde  **\<yeni … >**.  
  
4.  İçinde **katı ad anahtarı oluştur** iletişim kutusunda, yeni anahtar dosyası için bir ad Temizle girin **anahtar dosyamı bir parolayla korumak** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
5.  Kısayol menüsünü açın **ProjectTemplateWizard** proje ve ardından **derleme** ProjectTemplateWizard.dll dosyası oluşturmak için.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Ortak anahtarın Sihirbazı derleme için belirteci almak için  
  
1.  Üzerinde **Başlat menüsü**, seçin **tüm programlar**, seçin **Microsoft Visual Studio**, seçin **Visual Studio Araçları**, seçin **Geliştirici komut istemi**.  
  
     Visual Studio komut istemi penceresi açılır.  
  
2.  Aşağıdaki komutu çalıştırın değiştirerek *PathToWizardAssembly* ile geliştirme bilgisayarınızda ProjectTemplateWizard projenin ProjectTemplateWizard.dll derlemesi tam yolu:  
  
    ```cmd  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Ortak anahtar belirteci ProjectTemplateWizard.dll derleme için Visual Studio komut istemi penceresine yazılır.  
  
3.  Visual Studio komut istemi penceresini açık tutun. Sonraki yordam sırasında ortak anahtar belirteci gerekir.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.Vstemplate dosyasında Sihirbazı derlemesine bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, genişletme **SiteColumnProjectTemplate** proje düğümünü ve SiteColumnProjectTemplate.vstemplate dosyasını açın.  
  
2.  Dosyanın sonuna, aşağıdaki ekleyin `WizardExtension` öğesi arasında `</TemplateContent>` ve `</VSTemplate>` etiketler. Değiştirin *belirtecinizi* değerini `PublicKeyToken` özniteliği ile önceki yordamda aldığınız ortak anahtar belirteci.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Hakkında daha fazla bilgi için `WizardExtension` öğesi bkz [WizardExtension öğesi &#40;Visual Studio şablonları&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Dosyayı kaydedin ve kapatın.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Değiştirilebilir parametreler proje şablonunda Elements.xml dosyası ekleyin
 Eklemek için birkaç değiştirilebilir parametreler *Elements.xml* SiteColumnProjectTemplate proje dosyasında. Bu parametreleri olarak başlatılır `RunStarted` yönteminde `SiteColumnProjectWizard` daha önce tanımladığınız sınıf. Bir kullanıcı bir Site sütunu proje oluşturduğu zaman, Visual Studio bu parametreleri otomatik olarak değiştirir. *Elements.xml* sihirbazda belirtilen değerlerle yeni proje dosyasında.  
  
 Bir dolar işareti ($) karakteriyle başlayan ve bir belirteç parametredir. Kendi değiştirilebilir parametreler tanımlanmasına ek olarak, tanımlanan ve SharePoint Proje sistemi tarafından başlatılan yerleşik parametrelerini kullanabilirsiniz. Daha fazla bilgi için [değiştirilebilir parametreler](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Değiştirilebilir parametreler için Elements.xml dosyası eklemek için
  
1.  SiteColumnProjectTemplate projenin içeriğini değiştirin *Elements.xml* aşağıdaki XML dosyasıyla.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     Yeni XML değerlerini değiştirir `Name`, `DisplayName`, `Type`, ve `Group` özel değiştirilebilir parametreler için öznitelikleri.  
  
2.  Dosyayı kaydedin ve kapatın.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>VSIX Paketi Ekleme Sihirbazı
 Site sütunu proje şablonu içeren VSIX Paketi Sihirbazı dağıtmak için VSIX projesinde source.extension.vsixmanifest dosyası Sihirbazı proje ve SharePoint komutları proje başvurularını ekleyin.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>VSIX Paketi Sihirbazı'nı eklemek için  
  
1.  İçinde **Çözüm Gezgini**, **SiteColumnProjectItem** ilişkin kısayol menüsünü açın, proje **source.extension.vsixmanifest** dosya ve ardından **Açık**.  
  
     Visual Studio, dosyayı bildirim düzenleyicisinde açar.  
  
2.  Üzerinde **varlıklar** sekmesini düzenleyicinin seçin **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu açılır.  
  
3.  İçinde **türü** listesinde **Microsoft.VisualStudio.Assembly**.  
  
4.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
5.  İçinde **proje** listesinde **ProjectTemplateWizard**ve ardından **Tamam** düğmesi.  
  
6.  Üzerinde **varlıklar** sekmesini düzenleyicinin seçin **yeni** düğmesini tekrar.  
  
     **Yeni varlık Ekle** iletişim kutusu açılır.  
  
7.  İçinde **türü** listesinde, girin **SharePoint.Commands.v4**.  
  
8.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
9. İçinde **proje** listesinde **SharePointCommands** proje ve ardından **Tamam** düğmesi.  
  
10. Menü çubuğunda, **derleme** > **Çözümü Derle**ve ardından çözüm hatasız derlenir emin olun.  
  
## <a name="test-the-wizard"></a>Test Sihirbazı
 Artık Sihirbazı'nı test etmek hazırsınız. İlk olarak, Visual Studio'nun deneysel örneğinde SiteColumnProjectItem çözüm hatalarını ayıklamaya başlayın. Ardından, Site sütunu Proje Sihirbazı, Visual Studio'nun deneysel örneğinde test edin. Son olarak, oluşturun ve site sütunu beklendiği gibi çalıştığını doğrulamak için projeyi çalıştırın.  
  
#### <a name="to-start-debugging-the-solution"></a>Çözüm hata ayıklamayı başlatmak için  
  
1.  Yönetici kimlik bilgileriyle Visual Studio'yu yeniden başlatın ve ardından SiteColumnProjectItem çözümü açın.  
  
2.  ProjectTemplateWizard projesinde SiteColumnProjectWizard kod dosyasını açın ve ardından ilk kod satırına bir kesme noktası ekleyin `RunStarted` yöntemi.  
  
3.  Menü çubuğunda, **hata ayıklama** > **özel durumları**.  
  
4.  İçinde **özel durumları** iletişim kutusunda, emin **sayıcı** ve **kullanıcı-işlenmemiş** onay kutularını **ortak dil çalışma zamanı özel durumları**temizlenir ve ardından **Tamam** düğmesi.  
  
5.  Seçim yaparak hata ayıklamayı Başlat **F5** anahtar veya, menü çubuğundan seçme **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
     Visual Studio için %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 uzantıyı yükleyen ve Visual Studio'nun deneysel örneği başlar. Proje öğesi bu Visual Studio örneğinde test edeceğiz.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Sihirbaz Visual Studio'da Test etmek için  
  
1. Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **dosya** > **yeni** > **proje**.  
  
2. Genişletin **Visual C#** düğümü veya **Visual Basic** (dile bağlı olarak, proje şablonu destekleyen), düğümünü **SharePoint** düğümünü seçin **2010** düğümü.  
  
3. Proje şablonları listesinde seçin **Site sütunu**, projeyi adlandırın **SiteColumnWizardTest**ve ardından **Tamam** düğmesi.  
  
4. Visual Studio'nun diğer örneğindeki kodun daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `RunStarted` yöntemi.  
  
5. Seçerek proje hatalarını ayıklamaya devam **F5** anahtar veya, menü çubuğundan seçme **hata ayıklama** > **devam**.  
  
6. İçinde **SharePoint Özelleştirme Sihirbazı**, hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin ve ardından **sonraki** düğmesi.  
  
7. İkinci sayfasında **SharePoint Özelleştirme Sihirbazı**, aşağıdaki seçimleri yapın:  
  
   - İçinde **türü** listesinde **Boole**.  
  
   - İçinde **grubu** listesinde **özel Hayır sütunları**.  
  
   - İçinde **adı** kutusuna **My Hayır sütun**ve ardından **son** düğmesi.  
  
     İçinde **Çözüm Gezgini**, yeni bir proje görünür ve adlı bir proje öğesi içeren **alan1**, ve Visual Studio açılır ve projenin *Elements.xml* düzenleyicideki dosyada.  
  
8. Doğrulayın *Elements.xml* sihirbazda belirttiğiniz değerleri içerir.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint site sütunu test etmek için  
  
1.  Visual Studio'nun deneysel örneğinde seçin **F5** anahtarı.  
  
     Site sütunu paketlenir ve SharePoint'e dağıtılan sitenin **Site URL'si** projenin özelliği belirtir. Web tarayıcısı bu sitenin varsayılan sayfasına açılır.  
  
    > [!NOTE]  
    >  Varsa **betik hata ayıklamasını devre dışı bırakılmış** iletişim kutusu görüntülenirse, seçin **Evet** proje hatalarını ayıklamaya devam etmek için düğme.  
  
2.  Üzerinde **Site eylemleri** menüsünde seçin **Site Ayarları**.  
  
3.  Site Ayarları sayfasında altında **galeriler**, seçin **Site sütunları** bağlantı.  
  
4.  Site sütunları listesinde doğrulayın bir **özel Hayır sütunları** adlı bir sütun içeren grubu **My Hayır sütun**ve ardından web tarayıcısını kapatın.  
  
## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme
 Proje öğesi testi tamamladıktan sonra proje şablonu Visual Studio'nun deneysel örneği kaldırın.  
  
#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Uzantılar listesinde seçin **Site sütunu**ve ardından **kaldırma** düğmesi.  
  
3.  Görünen iletişim kutusunda **Evet** uzantıyı kaldırın ve ardından istediğinizi onaylamak için düğmeyi **şimdi yeniden Başlat** kaldırma işlemini tamamlamak için düğme.  
  
4.  Visual Studio'nun deneysel örneğinde hem CustomActionProjectItem çözüm açık olduğu örneği kapatın.  
  
     Nasıl dağıtılacağı hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantıları, bakın [sevkiyat Visual Studio uzantıları](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İzlenecek yol: bir proje şablonu, bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint Proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio Şablon Şeması Başvurusu](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
