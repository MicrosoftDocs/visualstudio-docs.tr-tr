---
title: 'İzlenecek yol: bir SharePoint proje uzantısı oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8d68347f2b6b9f538555e05c91b15dcb045b46d6
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295988"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>İzlenecek yol: bir SharePoint proje uzantısı oluşturma
  Bu izlenecek yol, bir SharePoint proje uzantısı oluşturma işlemini gösterir. Bir proje ne zaman eklenmiş, silinmiş veya yeniden adlandırılmış gibi proje düzeyinde olaylara yanıt vermek için bir proje uzantısı'nı kullanabilirsiniz. Ayrıca, özel özellikler ekleme veya bir özellik değeri değiştiğinde yanıt. Proje öğesi uzantıları, proje uzantılarını belirli bir SharePoint proje türüyle ilişkilendirilemez. Bir proje uzantısı oluşturma, herhangi bir türden SharePoint projesi açıldığında uzantınızı yüklediği [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Bu izlenecek yolda oluşturulan herhangi bir SharePoint projesine eklenen özel bir Boolean özelliği oluşturacağınız [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Ayarlandığında **True**, yeni özellik ekler veya projenize görüntüler kaynak klasörüne eşlenir. Ayarlandığında **False**, varsa resimler klasöründeki kaldırıldı. Daha fazla bilgi için [nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Oluşturma bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantısı SharePoint projeleri için şunları yapar:  
  
    -   Özel proje özelliği için Özellikler penceresini ekler. Özelliği için herhangi bir SharePoint projesine uygulanır.  
  
    -   Bir projeye eşlemeli klasörleri eklemek için SharePoint Proje nesne modeli kullanır.  
  
    -   Kullanan [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otomasyon nesne modeli (DTE) projeden eşlenmiş klasör silinemedi.  
  
-   Oluşturma bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proje özelliğin uzantı derlemesini dağıtmak için paket uzantısı (VSIX).  
  
-   Hata ayıklama ve test proje özelliği.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler ihtiyacınız vardır:  
  
-   Desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu izlenecek yolda **VSIX projesi** şablonunda [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] proje özelliği uzantısını dağıtmak için VSIX paketi oluşturmak için. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için iki proje oluşturmanız gerekir:  
  
- Proje uzantısını dağıtmak için VSIX paketi oluşturmak üzere bir VSIX projesi.  
  
- Proje uzantısını uygulayan sınıf kitaplığı projesi.  
  
  İzlenecek yol, proje oluşturmaya başlayın.  
  
#### <a name="to-create-the-vsix-project"></a>VSIX projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **genişletilebilirlik** düğümü.  
  
    > [!NOTE]  
    >  Bu düğüm, yalnızca Visual Studio SDK'yı yüklerseniz kullanılabilir. Daha fazla bilgi için bu konudaki Önkoşullar bölümüne bakın.  
  
4.  İletişim kutusunun en üstünde **.NET Framework 4.5** .NET Framework sürümleri listesinden seçip **VSIX projesi** şablonu.  
  
5.  İçinde **adı** kutusuna **ProjectExtensionPackage**ve ardından **Tamam** düğmesi.  
  
     **ProjectExtensionPackage** proje görünür **Çözüm Gezgini**.  
  
#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **Windows**.  
  
3.  İletişim kutusunun en üstünde **.NET Framework 4.5** .NET Framework sürümleri listesinden seçip **sınıf kitaplığı** proje şablonu.  
  
4.  İçinde **adı** kutusuna **ProjectExtension**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **ProjectExtension** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
5.  Projeden Class1 kod dosyasını silin.  
  
## <a name="configure-the-project"></a>Proje yapılandırma
 Proje uzantısını oluşturmak için kod yazmadan önce kod dosyalarını ve derleme referanslarını uzantı projesine ekleyin.  
  
#### <a name="to-configure-the-project"></a>Proje yapılandırma  
  
1.  Adlı bir kod dosyası Ekle **CustomProperty** ProjectExtension projeye.  
  
2.  Kısayol menüsünü açın **ProjectExtension** proje ve ardından **Başvuru Ekle**.  
  
3.  İçinde **başvuru Yöneticisi - CustomProperty** iletişim kutusunda **Framework** düğüm ve System.ComponentModel.Composition ve System.Windows.Forms öğelerini derlemeleri yanındaki onay kutusunu seçin.  
  
4.  Seçin **uzantıları** düğümünün Microsoft.VisualStudio.SharePoint ve EnvDTE derlemeleri yanındaki onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
5.  İçinde **Çözüm Gezgini**altında **başvuruları** klasör **ProjectExtension** projesinin **EnvDTE**.  
  
6.  İçinde **özellikleri** penceresinde değişiklik **birlikte çalışma türlerini katıştır** özelliğini **False**.  
  
## <a name="define-the-new-sharepoint-project-property"></a>Yeni SharePoint proje özelliği tanımlayın
 Proje uzantısı ve yeni proje özelliği davranışını tanımlayan bir sınıf oluşturun. Yeni proje uzantısı sınıfının Implements tanımlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> arabirimi. Bir SharePoint proje uzantısı tanımlamak istediğinizde bu arabirimi uygulayın. Ayrıca, ekleme <xref:System.ComponentModel.Composition.ExportAttribute> sınıfa. Bu öznitelik sağlayan [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bulmak ve yüklemek için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> uygulaması. Geçirmek <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> türü özniteliğin Oluşturucusu.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Yeni SharePoint proje özelliği tanımlamak için  
  
1.  Aşağıdaki kod CustomProperty kod dosyasına yapıştırın.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="build-the-solution"></a>Çözümü derleyin
 Ardından, hata olmadan derlediğinden emin olmak için çözümü oluşturun.  
  
#### <a name="to-build-the-solution"></a>Çözümü derlemek için  
  
1.  Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Proje özelliği uzantısını dağıtmak için VSIX paketi oluşturma
 Proje uzantısını dağıtmak için bir VSIX paketi oluşturmak üzere çözümünüzdeki VSIX projesi kullanın. İlk olarak, VSIX projesine dahil olan source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırın. Ardından çözümü oluşturarak VSIX paketini oluşturun.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Yapılandırma ve VSIX paketini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**source.extension.vsixmanifest dosyası için kısayol menüsünü açın ve ardından **açın** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dosya bildirim Tasarımcısı'nda açılır. Görüntülenen bilgileri **meta verileri** sekmesi de görüntülenir **Uzantılar ve güncelleştirmeler**. Tüm VSIX paketleri.vsixmanifest uzantı dosyası gerektirir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  İçinde **ürün adı** kutusuna **özel Proje özelliği**.  
  
3.  İçinde **Yazar** kutusuna **Contoso**.  
  
4.  İçinde **açıklama** kutusuna **görüntüleri kaynak klasörünü projeye eşleme değiştirir özel bir SharePoint proje özelliği**.  
  
5.  Seçin **varlıklar** sekmesine ve ardından **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
6.  İçinde **türü** listesinde **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `MEFComponent` extension.vsixmanifest dosyasındaki öğesi. Bu öğe VSIX paketinde bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için [MEFComponent öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  İçinde **kaynak** listesinde **mevcut çözümde bir proje** seçenek düğmesini.  
  
8.  İçinde **proje** listesinde **ProjectExtension**.  
  
     Bu değer, projede oluşturmakta olduğunuz derleme adını tanımlar.  
  
9. Seçin **Tamam** kapatmak için **yeni varlık Ekle** iletişim kutusu.  
  
10. Menü çubuğunda, **dosya** > **Tümünü Kaydet** olduğunda, son ve bildirim Tasarımcısı'nı kapatın.  
  
11. Menü çubuğunda, **derleme** > **Çözümü Derle**ve ardından projenin hata olmadan derlediğinden emin olun.  
  
12. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProjectExtensionPackage** projesini ve ardından **klasörü dosya Gezgini'nde Aç** düğmesi.  
  
13. İçinde **dosya Gezgini**ProjectExtensionPackage projesi için derleme çıktısı klasörü açın ve ardından klasör ProjectExtensionPackage.vsix adlı bir dosya içerdiğini doğrulayın.  
  
     Varsayılan olarak, derleme çıktısı klasörü olduğu... \bin\Debug klasörüne proje dosyanızı içeren klasörün altında.  
  
## <a name="test-the-project-property"></a>Proje özelliği test etme
 Özel proje özelliği test etmek artık hazırsınız. Yeni proje özelliği uzantıyı deneysel örneğinde test etmek ve hata ayıklama en kolayıdır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Bu örneği [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir VSIX veya diğer genişletilebilirlik projesi çalıştırdığınızda oluşturulur. Proje hatalarını ayıklamaya sonra uzantıyı yüklemek ve hata ayıklamak ve normal bir kopyasında test devam [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Hata ayıklayın ve Visual Studio'nun deneysel örneğinde uzantıyı test etmek için  
  
1.  Yeniden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yönetici kimlik bilgilerini ve ProjectExtensionPackage çözümü açın.  
  
2.  Projenizin hata ayıklama derlemesi seçerek Başlat **F5** anahtar veya, menü çubuğundan seçme **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Proje Property\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom için uzantıyı yükleyen ve deneysel örneği başlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  Deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Grup çözümü için bir SharePoint projesi oluşturun ve sihirbazdaki diğer değerler için varsayılan değerleri kullanın.  
  
    1.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
    2.  Üst kısmındaki **yeni proje** iletişim kutusunda **.NET Framework 3.5** .NET Framework sürümleri listesinde.  
  
         SharePoint araç uzantıları gerektirir, bu sürümündeki Özellikler [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  Altında **şablonları** düğümünü genişletin **Visual C#** veya **Visual Basic** düğümünü seçin **SharePoint** düğümünün seçin**2010** düğümü.  
  
    4.  Seçin **SharePoint 2010 projesi** şablonunu ve enter **ModuleTest** projenizin adı olarak.  
  
4.  İçinde **Çözüm Gezgini**, seçin **ModuleTest** proje düğümü.  
  
     Yeni bir özel özellik **harita resimler klasöründeki** görünür **özellikleri** varsayılan değerini penceresiyle **False**.  
  
5.  Bu özelliğin değerini değiştirmek **True**.  
  
     Bir görüntü kaynak klasörünü, SharePoint projesine eklenir.  
  
6.  Bu özelliğin değerini durumuna döndürün **False**.  
  
     Seçerseniz **Evet** düğmesine **resimler klasörünü Sil?** iletişim kutusu, görüntüleri kaynak klasörünü, SharePoint projeden silinir.  
  
7.  Deneysel örneği kapatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint projeleri genişletme](../sharepoint/extending-sharepoint-projects.md)   
 [Nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [SharePoint Proje sistem türleri ve diğer Visual Studio Proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [SharePoint Proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint araç uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
