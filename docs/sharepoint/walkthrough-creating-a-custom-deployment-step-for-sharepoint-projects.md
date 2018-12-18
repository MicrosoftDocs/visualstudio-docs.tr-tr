---
title: 'İzlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c74feaed6c108f9dcfb5f2b374a72c34526134b0
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296157"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>İzlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturma
  Bir SharePoint projesi dağıttığınızda, Visual Studio, belirli bir sırayla bir dizi dağıtım adımı yürütür. Visual Studio, birçok yerleşik dağıtım adımlarını içerir, ancak kendi oluşturabilirsiniz.  
  
 Bu kılavuzda, SharePoint çalıştıran sunucudaki çözümlerini yükseltmek için özel bir dağıtım adımı oluşturacaksınız. Visual Studio, birçok görevi, bu tür Geri Çekiliyor veya çözümleri eklemek için yerleşik dağıtım adımlarını içerir, ancak daha fazla bilgi için bir dağıtım adımı içermez. Bir SharePoint çözümünü dağıttığınızda (zaten dağıtılırsa) varsayılan olarak, Visual Studio çözüm ilk çeker. ve sonra da çözümün tamamını yeniden dağıtır. Yerleşik dağıtım adımları hakkında daha fazla bilgi için bkz: [dağıtma, yayımlama ve yükseltme SharePoint çözüm paketleri](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Visual Studio uzantısı oluşturma iki ana görevleri gerçekleştirir:  
  
    -   SharePoint çözümlerini yükseltmek için özel bir dağıtım adımı uzantısını tanımlar.  
  
    -   Uzantısı için belirli bir projenin yürütülen dağıtım adımları olan yeni bir dağıtım yapılandırması tanımlayan bir proje uzantısı oluşturur. Yeni Dağıtım Yapılandırması, özel dağıtım adımını ve birkaç yerleşik dağıtım adımlarını içerir.  
  
-   Uzantı derlemesini çağıran iki özel SharePoint komutu oluşturun. SharePoint komutları için SharePoint sunucusu nesne modelinde API'lerini kullanmayı uzantısı derlemeler tarafından çağrılan yöntemlerdir. Daha fazla bilgi için [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Derlemelerin hem de dağıtmak için Visual Studio Uzantısı (VSIX) paketini derleme.  
  
-   Yeni bir dağıtım adımı test etme.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler ihtiyacınız vardır:  
  
- Windows, SharePoint ve Visual Studio'nun desteklenen sürümleri.
  
- Visual Studio SDK. Bu izlenecek yolda **VSIX projesi** uzantısını dağıtmak için VSIX paketi oluşturmak için SDK'sı şablonunda. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Aşağıdaki kavramları bilgisi yardımcı, ancak gerekli değildir, bu izlenecek yolu tamamlamak için:  
  
- Sunucu nesne modeli için SharePoint kullanma. Daha fazla bilgi için [SharePoint Foundation Sunucu tarafı nesne modeli kullanarak](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
- SharePoint çözümleri. Daha fazla bilgi için [çözümlerine genel bakış](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
- SharePoint çözümleri yükseltme. Daha fazla bilgi için [çözüm yükseltme](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için üç projeleri oluşturmanız gerekir:  
  
- Uzantıyı dağıtmak için VSIX paketi oluşturmak amacıyla bir VSIX projesi.  
  
- Uzantısını uygulayan sınıf kitaplığı projesi. Bu projenin .NET Framework 4.5 hedeflemesi gerekir.  
  
- Özel SharePoint komutları tanımlayan bir sınıf kitaplığı projesi. Bu projenin .NET Framework 3.5 hedeflemesi gerekir.  
  
  İzlenecek yol, proje oluşturmaya başlayın.  
  
#### <a name="to-create-the-vsix-project"></a>VSIX projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **genişletilebilirlik** düğümü.  
  
    > [!NOTE]  
    >  **Genişletilebilirlik** düğümüdür yalnızca, Visual Studio SDK yüklenmiş ise kullanılabilir. Daha fazla bilgi için bu konudaki Önkoşullar bölümüne bakın.  
  
4.  İletişim kutusunun en üstünde **.NET Framework 4.5** .NET Framework sürümleri listesinde.  
  
5.  Seçin **VSIX projesi** şablon, proje adı **UpgradeDeploymentStep**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **UpgradeDeploymentStep** için proje **Çözüm Gezgini**.  
  
#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, UpgradeDeploymentStep çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **Windows** düğümü.  
  
3.  İletişim kutusunun en üstünde **.NET Framework 4.5** .NET Framework sürümleri listesinde.  
  
4.  Seçin **sınıf kitaplığı** proje şablonu, projeyi adlandırın **DeploymentStepExtension**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **DeploymentStepExtension** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
5.  Projeden Class1 kod dosyasını silin.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>SharePoint komutu projeyi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, UpgradeDeploymentStep çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic**ve ardından **Windows** düğümü.  
  
3.  İletişim kutusunun en üstünde **.NET Framework 3.5** .NET Framework sürümleri listesinde.  
  
4.  Seçin **sınıf kitaplığı** proje şablonu, projeyi adlandırın **SharePointCommands**ve ardından **Tamam** düğmesi.  
  
     Visual Studio ekler **SharePointCommands** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
5.  Projeden Class1 kod dosyasını silin.  
  
## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Özel dağıtım adımı oluşturmak için kod yazmadan önce kod dosyaları ve derleme başvurularını ekleyin ve projeleri yapılandırmanız gerekir.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>DeploymentStepExtension projeyi yapılandırmak için
  
1.  İçinde **DeploymentStepExtension** projesinde, aşağıdaki adlara sahip iki kod dosyasını ekleyin:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  DeploymentStepExtension projenin kısayol menüsünü açın ve ardından **Başvuru Ekle**.  
  
3.  Üzerinde **Framework** sekmesinde, System.ComponentModel.Composition derleme için onay kutusunu seçin.  
  
4.  Üzerinde **uzantıları** sekmesinde Microsoft.VisualStudio.SharePoint derleme için onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointCommands projeyi yapılandırmak için
  
1.  İçinde **SharePointCommands** proje, komutları adlı bir kod dosyası ekleyin.  
  
2.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SharePointCommands** proje düğümünü ve ardından **Başvuru Ekle**.  
  
3.  Üzerinde **uzantıları** sekmesinde aşağıdaki derlemeler için onay kutularını seçin ve tıklayın ardından **Tamam** düğmesi  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="define-the-custom-deployment-step"></a>Özel dağıtım adımı tanımlayın
 Yükseltme dağıtım adımı tanımlayan bir sınıf oluşturun. Sınıfının Implements dağıtım adımı tanımlamak için <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> arabirimi. Özel bir dağıtım adımı tanımlamak istediğinizde bu arabirimi uygulayın.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Özel dağıtım adımı tanımlamak için  
  
1.  İçinde **DeploymentStepExtension** proje UpgradeStep kod dosyasını açın ve ardından aşağıdaki kodu yapıştırın.  
  
    > [!NOTE]  
    >  Ne zaman bu kodu ekleyin, proje bazı derleme hataları olacaktır, ancak bunlar kaybolur sonra sonraki adımlarda kod ekleyin.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Özel dağıtım adımını içeren bir dağıtım yapılandırması oluştur
 Birkaç yerleşik dağıtım adımları ve yeni yükseltme dağıtım adımı içeren yeni bir dağıtım yapılandırması için bir proje uzantısı oluşturma. Bu uzantı oluşturarak, SharePoint projelerinde yükseltme dağıtım adımı kullanılacak SharePoint geliştiriciler yardımcı olur.  
  
 Sınıf uygulayan bir dağıtım yapılandırma oluşturmak üzere <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> arabirimi. Bir SharePoint proje uzantısı oluşturma istediğinizde bu arabirimi uygulayın.  
  
#### <a name="to-create-the-deployment-configuration"></a>Dağıtım yapılandırması oluşturmak için  
  
1.  İçinde **DeploymentStepExtension** proje DeploymentConfigurationExtension kod dosyasını açın ve ardından aşağıdaki kodu yapıştırın.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Özel SharePoint komutları oluşturma
 SharePoint için sunucu nesne modeline çağrı iki özel komutlar oluşturur. Tek bir komutta bir çözüm zaten dağıtmış olup olmadığını belirler; bir çözüm diğer komut yükseltilir.  
  
#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutları tanımlamak için  
  
1.  İçinde **SharePointCommands** proje, komutları kod dosyasını açın ve ardından aşağıdaki kodu yapıştırın.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu aşamada izlenecek yolda, özel dağıtım adımını ve SharePoint komutları için kodun tümü kullanıma projeleri. Hata olmadan derleme emin olmak için bunları oluşturun.  
  
#### <a name="to-build-the-projects"></a>Projeleri derlemek için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **DeploymentStepExtension** proje ve ardından **yapı**.  
  
2.  Kısayol menüsünü açın **SharePointCommands** proje ve ardından **yapı**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için VSIX paketi oluşturmak için çözümünüzdeki VSIX projesi kullanın. İlk olarak, VSIX projesinde source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırın. Ardından çözümü oluşturarak VSIX paketini oluşturun.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Yapılandırma ve VSIX paketini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**altında **UpgradeDeploymentStep** ilişkin kısayol menüsünü açın, proje **source.extension.vsixmanifest** dosya ve seçin **Açık**.  
  
     Visual Studio, dosyayı bildirim düzenleyicisinde açar. Source.extension.vsixmanifest dosyası, tüm VSIX paketleri gerektiren extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  İçinde **ürün adı** kutusuna **SharePoint projeleri için yükseltme dağıtım adımı**.  
  
3.  İçinde **Yazar** kutusuna **Contoso**.  
  
4.  İçinde **açıklama** kutusuna **SharePoint projelerinde kullanılabilir bir yükseltme özel dağıtım adımı sağlar**.  
  
5.  İçinde **varlıklar** sekmesini düzenleyicinin seçin **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
6.  İçinde **türü** listesinde **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `MefComponent` extension.vsixmanifest dosyasındaki öğesi. Bu öğe VSIX paketinde bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için [MEFComponent öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
8.  İçinde **proje** listesinde **DeploymentStepExtension**ve ardından **Tamam** düğmesi.  
  
9. Bildirim düzenleyicisinde seçin **yeni** düğmesini tekrar.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
10. İçinde **türü** listesinde, girin **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Bu öğe, Visual Studio Uzantısı'nda dahil etmek istediğiniz özel bir uzantı belirtir. Daha fazla bilgi için [varlık öğesi (VSX şema)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
12. İçinde **proje** listesinde **SharePointCommands**ve ardından **Tamam** düğmesi.  
  
13. Menü çubuğunda, **derleme** > **Çözümü Derle**ve ardından çözüm hata olmadan derlediğinden emin olun.  
  
14. UpgradeDeploymentStep projesi yapı çıkış klasöründe artık UpgradeDeploymentStep.vsix dosyası içerdiğinden emin olun.  
  
     Varsayılan olarak, derleme çıktısı klasörü olduğu... \bin\Debug klasörüne proje dosyanızı içeren klasörün altında.  
  
## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Yükseltme dağıtım adımı test etmek hazırlama
 Yükseltme dağıtım adımı test etmek için örnek çözümü SharePoint sitesine dağıtmanız gerekir. Visual Studio'nun Deneysel örneğindeki uzantıyı hata ayıklayarak başlayın. Ardından bir liste tanımı ve dağıtım adımı test etmek için kullanılacak liste örneği oluşturun ve bunları SharePoint sitesine dağıtabilirsiniz. Ardından, liste tanımı ve liste örneği değiştirebilir ve varsayılan dağıtım işlemi SharePoint sitesinde çözümleri nasıl üzerine yazar göstermek için bunları yeniden dağıtın.  
  
 Daha sonra bu kılavuzda, liste tanımı ve liste örneği değiştireceksiniz ve ardından bunları SharePoint sitesinde yükseltmeniz.  
  
#### <a name="to-start-debugging-the-extension"></a>Uzantı hata ayıklamasını başlatmak için  
  
1.  Yönetici kimlik bilgileriyle Visual Studio'yu yeniden başlatın ve ardından UpgradeDeploymentStep çözümü açın.  
  
2.  DeploymentStepExtension projesinde UpgradeStep kod dosyasını açın ve ardından ilk kod satırına bir kesme noktası ekleyin `CanExecute` ve `Execute` yöntemleri.  
  
3.  Seçim yaparak hata ayıklamayı Başlat **F5** anahtar veya, menü çubuğundan seçme **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
4.  Visual Studio için SharePoint Projects\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade dağıtım adımı için uzantıyı yükleyen ve Visual Studio'nun deneysel örneği başlar. Yükseltme dağıtım adımı bu Visual Studio örneğinde test edeceğiz.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Liste tanımı ve liste örneği ile bir SharePoint projesi oluşturmak için  
  
1. Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **dosya** > **yeni** > **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümü veya **Visual Basic** düğümünü genişletin **SharePoint** düğümünü seçin **2010** düğümü.  
  
3. Emin olun ve iletişim kutusunun en üstünde **.NET Framework 3.5** .NET Framework sürümleri listesinde görünür.  
  
    Projeler için [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ve [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .NET Framework'ün bu sürümü gerekir.  
  
4. Proje şablonları listesinde seçin **SharePoint 2010 projesi**, projeyi adlandırın **EmployeesListDefinition**ve ardından **Tamam** düğmesi.  
  
5. İçinde **SharePoint Özelleştirme Sihirbazı**, hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin.  
  
6. Altında **bu SharePoint çözümünün güven düzeyi nedir**, seçin **Grup çözümü olarak Dağıt** seçenek düğmesini.  
  
   > [!NOTE]  
   >  Yükseltme dağıtım adımı korumalı alana alınan çözümler desteklemiyor.  
  
7. Seçin **son** düğmesi.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] EmployeesListDefinition projesi oluşturur.  
  
8. EmployeesListDefinition proje için kısayol menüsünü açın, **Ekle**ve ardından **yeni öğe**.  
  
9. İçinde **Yeni Öğe Ekle - EmployeesListDefinition** iletişim kutusunda **SharePoint** düğümünü seçip **2010** düğümü.  
  
10. Seçin **listesi** öğe şablonu, öğe adı **çalışanların listesi**ve ardından **Ekle** düğmesi.  
  
     SharePoint Özelleştirme Sihirbazı görünür.  
  
11. Üzerinde **liste ayarlarını seçin** sayfasında, aşağıdaki ayarları doğrulayın ve ardından **son** düğmesi:  
  
    1. **Çalışanların listesi** görünür **hangi adı görüntülemek için listenizi istiyor musunuz?** kutusu.  
  
    2. **Göre özelleştirilebilir bir liste oluşturun:** seçenek düğmesi seçilir.  
  
    3. **Varsayılan (boş)** seçilir **göre özelleştirilebilir bir liste oluşturun:** listesi.  
  
       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir başlık sütunu ve tek boş bir örnek ile çalışanların liste öğesi oluşturur ve listeyi Tasarımcısı açılır.  
  
12. Liste tasarımcısında üzerinde **sütunları** sekmesini, **yeni veya var olan sütun adı yazın** satır ve ardından aşağıdaki sütunları ekleyin **sütun görünen adı** listesi:  
  
    1.  Ad  
  
    2.  Şirket  
  
    3.  İş Telefonu  
  
    4.  E-posta  
  
13. Tüm dosyaları kaydedin ve ardından listeyi Tasarımcısı'nı kapatın.  
  
14. İçinde **Çözüm Gezgini**, genişletin **çalışanların listesi** düğümünü ve ardından **çalışanlar liste örneği** alt düğümü.  
  
15. İçinde *Elements.xml* dosya, varsayılan XML bu dosyada bulunan aşağıdaki XML ile değiştirin. Bu XML adını listeye değişiklikleri **çalışanlar** ve Jim Hance adlı bir çalışan için bilgi ekler.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Kaydet ve Kapat *Elements.xml* dosya.  
  
17. EmployeesListDefinition proje için kısayol menüsünü açın ve ardından **açık** veya **özellikleri**.  
  
     Özellikleri Tasarımcısı açılır.  
  
18. Üzerinde **SharePoint** sekmesi, NET **otomatik hata ayıklamadan sonra** onay kutusunu işaretleyin ve ardından Özellikler kaydedin.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Liste tanımı ve liste örneği dağıtmak için  
  
1.  İçinde **Çözüm Gezgini**, seçin **EmployeesListDefinition** proje düğümü.  
  
2.  İçinde **özellikleri** penceresinde emin **etkin Dağıtım Yapılandırması** özelliği **varsayılan**.  
  
3.  Seçin **F5** tuşunu veya menü çubuğunda, **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
4.  Proje başarıyla oluşturulursa, web tarayıcısı SharePoint sitesine açıldığını doğrulayın, **listeler** Hızlı Başlat çubuğunda öğesi içerir yeni **çalışanlar** listesi ve  **Çalışanların** listesi Jim Hance için giriş içerir.  
  
5.  Web tarayıcısını kapatın.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Liste tanımı ve liste örneği değiştirin ve bunları yeniden dağıtma  
  
1.  EmployeesListDefinition projeyi *Elements.xml* alt öğesi olan dosya **çalışan liste örneği** proje öğesi.  
  
2.  Kaldırma `Data` öğe ve alt öğelerinde harcanan giriş Jim Hance için listeden kaldırmak için.  
  
     İşiniz bittiğinde, aşağıdaki XML dosya içermelidir.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Kaydet ve Kapat *Elements.xml* dosya.  
  
4.  Kısayol menüsünü açın **çalışanların listesi** proje öğesi ve ardından **açık** veya **özellikleri**.  
  
5.  Liste Tasarımcısı'nda **görünümleri** sekmesi.  
  
6.  İçinde **Seçili sütunlar** listesinde **ekleri**ve ardından < bu sütuna taşımanız için bir tuşa **kullanılabilir sütunlar** listesi.  
  
7.  Taşımak için önceki adımı yineleyin **iş telefonu** sütundan **Seçili sütunlar** listesindeki **kullanılabilir sütunlar** listesi.  
  
     Bu eylem, bu alanlar varsayılan görünümden kaldırır. **çalışanlar** SharePoint sitesinde listesi.  
  
8.  Seçim yaparak hata ayıklamayı Başlat **F5** anahtar veya, menü çubuğundan seçme **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
9. Doğrulayın **dağıtım çakışmalarını** iletişim kutusu görüntülenir.  
  
     (Liste örneği) bir çözümü dağıtmak Visual Studio çalıştığında, bu çözümü zaten dağıtılmış olan bir SharePoint sitesi için bu iletişim kutusu görüntülenir. Bu izlenecek yolda daha sonra yükseltme dağıtım adımı yürütürken bu iletişim kutusunda görünmez.  
  
10. İçinde **dağıtım çakışmalarını** iletişim kutusunda **otomatik olarak çözümlemek** seçenek düğmesini.  
  
     Visual Studio, SharePoint sitesindeki bir liste örneği siler, projedeki liste öğesi dağıtır ve ardından SharePoint sitesi açılır.  
  
11. İçinde **listeler** bölümü Hızlı Başlat çubuğuna seçin **çalışanlar** listeleyin ve ardından aşağıdaki ayrıntıları doğrulayın:  
  
    -   **Ekleri** ve **ev telefonu** sütunları, bu liste görünümünde görünmez.  
  
    -   Liste boş olduğu. Kullanıldığında, **varsayılan** çözümü yeniden dağıtmak için Dağıtım Yapılandırması **çalışanlar** listesi yeni boş liste, projenizdeki ile değiştirilmiştir.  
  
## <a name="test-the-deployment-step"></a>Dağıtım adımı test
 Yükseltme dağıtım adımı test etmek artık hazırsınız. İlk olarak, SharePoint liste örneği için bir öğe ekleyin. Sonra liste tanımı ve liste örneği değiştirin, bunlar SharePoint sitesinde yükseltme ve yükseltme dağıtım adımı yeni öğe üzerine değil onaylayın.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>El ile listeye öğe eklemek için  
  
1.  SharePoint sitesindeki Şeritte altında **liste Araçları** sekmesini, **öğeleri** sekmesi.  
  
2.  İçinde **yeni** Grup öğesini **yeni öğe**.  
  
     Alternatif olarak, seçtiğiniz **Yeni Öğe Ekle** bağlantıyı öğe listesi.  
  
3.  İçinde **çalışanları - yeni öğe** penceresi içinde **başlık** kutusuna **tesis Manager**.  
  
4.  İçinde **ad** kutusuna **Andy**.  
  
5.  İçinde **şirket** kutusuna **Contoso**.  
  
6.  Seçin **Kaydet** düğmesi, yeni öğe listesinde göründüğünü doğrulayın ve ardından web tarayıcısını kapatın.  
  
     Bu kılavuzda daha sonra bu öğeyi yükseltme dağıtım adımı bu listenin içeriği üzerine değil doğrulamak için kullanın.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Yükseltme dağıtım adımı test etmek için  
  
1. Visual Studio'nun Deneysel örneğinin içinde **Çözüm Gezgini**, kısayol menüsünü açın **EmployeesListDefinition** proje düğümünü ve ardından **özellikleri**.  
  
    Özellik Düzenleyicisi'ni / Tasarımcısı açılır.  
  
2. Üzerinde **SharePoint** sekmesinde, belirleyin **etkin Dağıtım Yapılandırması** özelliğini **yükseltme**.  
  
    Bu özel dağıtım yapılandırma yeni yükseltme dağıtım adımı içerir.  
  
3. Kısayol menüsünü açın **çalışanların listesi** proje öğesi ve ardından **özellikleri** veya **açık**.  
  
    Özellik Düzenleyicisi'ni / Tasarımcısı açılır.  
  
4. Üzerinde **görünümleri** sekmesini, **e-posta** sütunu seçip **<** bu sütunundan taşımak için anahtar **Seçili sütunlar**listesindeki **kullanılabilir sütunlar** listesi.  
  
    Bu eylem, bu alanlar varsayılan görünümden kaldırır. **çalışanlar** SharePoint sitesinde listesi.  
  
5. Seçim yaparak hata ayıklamayı Başlat **F5** anahtar veya, menü çubuğundan seçme **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
6. Visual Studio'nun diğer örneğindeki kodun daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `CanExecute` yöntemi.  
  
7. Seçin **F5** yeniden tuşunu veya menü çubuğunda, **hata ayıklama** > **devam**.  
  
8. Kod daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `Execute` yöntemi.  
  
9. Seçin **F5** tuşunu veya menü çubuğunda, **hata ayıklama** > **devam** son zaman.  
  
     Web tarayıcısı, SharePoint sitesi açılır.  
  
10. İçinde **listeler** bölümü hızlı başlat alanında seçin **çalışanlar** listeleyin ve ardından aşağıdaki ayrıntıları doğrulayın:  
  
    - Daha önce (Andy için tesis Yöneticisi) el ile eklenen öğeyi yine listesidir.  
  
    - **İş telefonu** ve **e-posta adresi** sütunları, bu liste görünümünde görünmez.  
  
      **Yükseltme** dağıtım yapılandırmasını değiştirir varolan **çalışanlar** SharePoint sitesinde liste örneği. Kullandıysanız **varsayılan** yerine dağıtım yapılandırması **yükseltme** yapılandırma, bir dağıtım çakışma karşılaşırsanız. Visual Studio çözmek çakışma değiştirerek **çalışanlar** listesi ve öğe için Andy, tesis Yöneticisi silinmiş olabilir.  
  
## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme
 Yükseltme dağıtım adımı testi tamamladıktan sonra liste tanımı ve liste örneği SharePoint sitesinden kaldırın ve Visual Studio'dan dağıtım adımı uzantıyı kaldırın.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Liste örneği SharePoint sitesinden kaldırmak için  
  
1.  Açık **çalışanlar** liste zaten açık değilse SharePoint sitesinde listesi.  
  
2.  SharePoint sitesindeki Şeritte seçin **liste Araçları** sekmesine ve ardından **listesi** sekmesi.  
  
3.  İçinde **ayarları** Grup öğesini **listesi ayarları** öğesi.  
  
4.  Altında **izinler ve Yönetim**, seçin **bu listeyi Sil** komutu öğesini **Tamam** listeyi Geri Dönüşüm Kutusu'na göndermek ve ardından web kapatmak istediğinizi onaylamak için Tarayıcı.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Liste tanımı SharePoint sitesinden kaldırmak için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **derleme** > **geri çek**.  
  
     Visual Studio, SharePoint sitesinden liste tanımı geri çeker.  
  
#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Uzantılar listesinde seçin **SharePoint projeleri için yükseltme dağıtım adımı**ve ardından **kaldırma** komutu.  
  
3.  Görünen iletişim kutusunda **Evet** uzantıyı kaldırın ve ardından istediğinizi onaylamak için **şimdi yeniden Başlat** kaldırma işlemini tamamlamak için.  
  
4.  (Deneysel örneği ve Visual Studio'nun UpgradeDeploymentStep çözüm açık olduğu örneği) Visual Studio'nun her iki örneklerini kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
