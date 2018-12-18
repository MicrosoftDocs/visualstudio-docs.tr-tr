---
title: 'İzlenecek yol: Sunucu gezginini Web bölümlerini görüntülemek üzere genişletme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d32f76965c0dbef359e54bda114221e460a9bfd
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296391"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>İzlenecek yol: Sunucu Gezgini, web bölümlerini görüntülemek üzere genişletme
  Visual Studio'da kullanabileceğiniz **SharePoint bağlantıları** düğümünün **Sunucu Gezgini** bileşenleri SharePoint sitelerinde görüntülemek için. Ancak, **Sunucu Gezgini** bazı bileşenler varsayılan olarak görüntülemez. Bu kılavuzda, genişletme **Sunucu Gezgini** böylece Web Bölümü Galerisi'ne görüntüler her SharePoint sitesine bağlı.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Visual Studio uzantısı oluşturma genişletir **Sunucu Gezgini** aşağıdaki yollarla:  
  
    -   Uzantı ekler bir **Web Bölümü Galerisi'ne** içindeki her bir SharePoint sitesi düğümün altında düğüm **Sunucu Gezgini**. Bu yeni düğüm her Web Bölümünü Web Bölümü galerisinde sitesinde temsil eden alt düğümleri içerir.  
  
    -   Uzantının yeni bir Web Bölümü örneğinin temsil eden bir düğüm türünü tanımlar. Bu yeni düğüm türü altındaki Yeni alt düğümleri temelini **Web Bölümü Galerisi'ne** düğümü. Yeni Web Bölümü düğüm türü bilgilerini görüntüler **özellikleri** penceresi hakkında temsil ettiği bir Web Bölümü. Düğüm türü için Web Bölümü ile ilgili diğer görevleri gerçekleştirmek için bir başlangıç noktası olarak kullanabileceğiniz bir özel kısayol menü öğesi de içerir.  
  
-   Uzantı derlemesini çağıran iki özel SharePoint komutu oluşturun. SharePoint komutları için SharePoint sunucusu nesne modelinde API'lerini kullanmayı uzantısı derlemeler tarafından çağrılan yöntemlerdir. Bu kılavuzda, yerel geliştirme bilgisayarında SharePoint sitesinde Web bölümü bilgilerini almak komutları oluşturun. Daha fazla bilgi için [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Uzantıyı dağıtmak için Visual Studio Uzantısı (VSIX) paketini derleme.  
  
-   Hata ayıklama ve uzantıyı test etme.  
  
> [!NOTE]  
>  İstemci nesne modelini SharePoint için bunun yerine sunucu nesne modeli kullanır. Bu kılavuzda alternatif bir sürümü için bkz: [izlenecek yol: bir sunucu Gezgini uzantısında SharePoint istemcisi nesne modelini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler ihtiyacınız vardır:  
  
- Windows, SharePoint ve Visual Studio'nun desteklenen sürümleri.  
  
- Visual Studio SDK. Bu izlenecek yolda **VSIX projesi** proje öğesini dağıtmak üzere bir VSIX paketi oluşturmak için SDK'sı şablonunda. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Aşağıdaki kavramları bilgisi yardımcı, ancak gerekli değildir, bu izlenecek yolu tamamlamak için:  
  
- Sunucu nesne modeli için SharePoint kullanma. Daha fazla bilgi için [SharePoint Foundation Sunucu tarafı nesne modeli kullanarak](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
- SharePoint çözümlerinde Web Bölümleri. Daha fazla bilgi için [Web bölümlerine genel bakış](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için üç projeleri oluşturmanız gerekir:  
  
- Uzantıyı dağıtmak için VSIX paketi oluşturmak amacıyla bir VSIX projesi.  
  
- Uzantısını uygulayan sınıf kitaplığı projesi. Bu projenin .NET Framework 4.5 hedeflemesi gerekir.  
  
- Özel SharePoint komutları tanımlayan bir sınıf kitaplığı projesi. Bu projenin.NET Framework 3.5 hedeflemesi gerekir.  
  
  İzlenecek yol, proje oluşturmaya başlayın.  
  
#### <a name="to-create-the-vsix-project"></a>VSIX projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **genişletilebilirlik** düğümü.  
  
    > [!NOTE]  
    >  **Genişletilebilirlik** düğümüdür yalnızca, Visual Studio SDK yüklenmiş ise kullanılabilir. Daha fazla bilgi için bu konudaki Önkoşullar bölümüne bakın.  
  
4.  İletişim kutusunun en üstünde **.NET Framework 4.5** .NET Framework sürümleri listesinde.  
  
5.  Seçin **VSIX projesi** şablon, proje adı **WebPartNode**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **WebPartNode** için proje **Çözüm Gezgini**.  
  
#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümü veya **Visual Basic** düğümünü ve ardından seçin **Windows** düğümü.  
  
3.  İletişim kutusunun en üstünde **.NET Framework 4.5** .NET Framework sürümleri listesinde.  
  
4.  Proje şablonları listesinde seçin **sınıf kitaplığı**, projeyi adlandırın **WebPartNodeExtension**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **WebPartNodeExtension** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
5.  Projeden Class1 kod dosyasını silin.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projeyi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümü veya **Visual Basic** düğümünü seçip **Windows** düğümü.  
  
3.  İletişim kutusunun en üstünde **.NET Framework 3.5** .NET Framework sürümleri listesinde.  
  
4.  Proje şablonları listesinde seçin **sınıf kitaplığı**, projeyi adlandırın **WebPartCommands**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **WebPartCommands** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
5.  Projeden Class1 kod dosyasını silin.  
  
## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Uzantısını oluşturmak için kod yazmadan önce kod dosyaları ve derleme başvurularını ekleyin ve proje ayarlarını yapılandırmanız gerekir.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>WebPartNodeExtension projeyi yapılandırmak için
  
1.  WebPartNodeExtension projesinde aşağıdaki adlara sahip dört kod dosyaları ekleyin:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Kısayol menüsünü açın **WebPartNodeExtension** proje ve ardından **Başvuru Ekle**.  
  
3.  İçinde **başvuru Yöneticisi - WebPartNodeExtension** iletişim kutusunda **Framework** sekmesini ve ardından her biri aşağıdaki derlemeler için onay kutusunu seçin:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Seçin **uzantıları** sekmesinde Microsoft.VisualStudio.SharePoint derleme için onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
5.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **WebPartNodeExtension** proje düğümünü ve ardından **özellikleri**.  
  
     **Proje Tasarımcısı** açılır.  
  
6.  Seçin **uygulama** sekmesi.  
  
7.  İçinde **varsayılan ad alanı** kutusu (C#) veya **kök ad alanı** kutusunu ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), girin **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Webpartcommands projeyi yapılandırmak için
  
1.  WebPartCommands projesinde WebPartCommands adlı bir kod dosyası ekleyin.  
  
2.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **WebPartCommands** projesinin düğüm **Ekle**ve ardından **var olan öğe**.  
  
3.  İçinde **varolan öğeyi Ekle** iletişim kutusunda, WebPartNodeExtension proje için kod dosyaları içeren klasöre gidin ve ardından WebPartNodeInfo ve WebPartCommandIds kod dosyaları seçin.  
  
4.  Yanındaki oku seçin **Ekle** düğmesine ve ardından **bağlantı olarak ekleme** menüde görünür.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kod dosyaları bağlantı olarak WebPartCommands projeye ekler. Sonuç olarak, kod dosyaları WebPartNodeExtension projede bulunur, ancak kod dosyalarında WebPartCommands projede da derlenir.  
  
5.  Kısayol menüsünü açın **WebPartCommands** yeniden projesini ve ardından **Başvuru Ekle**.  
  
6.  İçinde **başvuru Yöneticisi - WebPartCommands** iletişim kutusunda **uzantıları** sekmesi, her biri aşağıdaki derlemeler için onay kutusunu işaretleyin ve ardından **Tamam** Düğme:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **WebPartCommands** yeniden proje ve ardından **özellikleri**.  
  
     **Proje Tasarımcısı** açılır.  
  
8.  Seçin **uygulama** sekmesi.  
  
9. İçinde **varsayılan ad alanı** kutusu (C#) veya **kök ad alanı** kutusunu ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), girin **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="create-icons-for-the-new-nodes"></a>Simgeler için yeni düğümler oluşturma
 Oluşturmak için iki simgeyi **Sunucu Gezgini** uzantısı: yeni bir simge **Web Bölümü Galerisi'ne** düğüm ve her bir alt Web Bölümü düğümün altında başka bir simge **Web Bölümü Galerisi'ne** düğüm. Bu kılavuzda daha sonra bu simgeleri düğümleri ile ilişkilendiren kod yazacaksınız.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Düğümler için simgeler oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **WebPartNodeExtension** proje ve ardından **özellikleri**.  
  
2.  **Proje Tasarımcısı** açılır.  
  
3.  Seçin **kaynakları** sekmesine ve ardından **bu projenin varsayılan kaynak dosyası içermiyor. Oluşturmak için buraya tıklayın** bağlantı.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir kaynak dosyası oluşturur ve tasarımcıda açılır.  
  
4.  En üstünde Tasarımcısı'nın yanındaki oku seçin **kaynak Ekle** menü komutunu ve ardından **yeni Simge Ekle** menüde görünür.  
  
5.  İçinde **yeni kaynak Ekle** iletişim kutusunda, yeni simgesine adı **WebPartsNode**ve ardından **Ekle** düğmesi.  
  
     İçinde yeni simge açıldıktan **Resim Düzenleyicisi**.  
  
6.  Simgenin 16 x 16 sürümü kolayca tanıyacak bir tasarıma sahip olacak şekilde düzenleyin.  
  
7.  Simgenin 32 x 32 sürümü için kısayol menüsünü açın ve ardından **Sil görüntü türü**.  
  
8.  İkinci simgeyi Proje kaynakları eklemek için 8 ile 5 arasındaki adımları yineleyin ve bu simgeyi ad **WebPart**.  
  
9. İçinde **Çözüm Gezgini**altında **kaynakları** klasör **WebPartNodeExtension** ilişkin kısayol menüsünü açın, proje **WebPartsNode.ico**.  
  
10. İçinde **özellikleri** penceresinde yanındaki oku seçin **derleme eylemi**ve ardından **gömülü kaynak** menüsünde görünür.  
  
11. Son iki adımı yineleyin **WebPart.ico**.  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Sunucu Gezginine Web Bölümü Galerisi'ne düğüm ekleme
 Ekleyen yeni bir sınıf oluşturmanız **Web Bölümü Galerisi'ne** her SharePoint sitesi düğüme düğüm. Sınıf uygular yeni düğümü eklemek için <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> arabirimi. Mevcut bir düğümün davranışını genişletmek istediğinizde bu arabirimi uygulayan **Sunucu Gezgini**, bir düğüm için bir alt düğüm ekleme gibi.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Sunucu Gezgini Web Bölümü Galerisi'ne düğümü eklemek için
  
1.  WebPartNodeExtension proje SiteNodeExtension kod dosyasını açın ve ardından aşağıdaki kodu yapıştırın.  
  
    > [!NOTE]  
    >  Ne zaman bu kodu ekleyin, proje bazı derleme hataları olacaktır, ancak bunlar kaybolur sonra sonraki adımlarda kod ekleyin.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Bir web bölümü temsil eden bir düğüm türünü tanımlayın
 Yeni bir Web Bölümü temsil eden bir düğüm türünü tanımlayan bir sınıf oluşturun. Visual Studio altında alt düğümler görüntülemek için bu yeni düğüm türü kullanır **Web Bölümü Galerisi'ne** düğümü. Her alt düğümü SharePoint sitesindeki tek bir Web Bölümü temsil eder.  
  
 Yeni bir düğüm türü, sınıfın uyguladığı tanımlamak için <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> arabirimi. Düğümünde yeni bir tür tanımlamak istediğinizde bu arabirimi uygulayan **Sunucu Gezgini**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Web bölümü düğüm türü tanımlamak için
  
1.  WebPartNodeExtension proje WebPartNodeTypeProvder kod dosyasını açın ve ardından aşağıdaki kodu yapıştırın.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="define-the-web-part-data-class"></a>Web bölümü veri sınıfı tanımlayın
 Tek bir Web Bölümü SharePoint sitesinde hakkında veri içeren bir sınıfı tanımlar. Bu kılavuzda daha sonra sitedeki her bir Web Bölümü ilişkin verileri alır ve ardından verileri için bu sınıfın örneklerinin atayan özel bir SharePoint komutu oluşturacaksınız.  
  
#### <a name="to-define-the-web-part-data-class"></a>Web bölümü veri sınıfını tanımlamak için
  
1.  WebPartNodeExtension proje WebPartNodeInfo kod dosyasını açın ve ardından aşağıdaki kodu yapıştırın.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="define-the-ids-for-the-sharepoint-commands"></a>SharePoint komutları için kimlikleri tanımlayın
 Özel SharePoint komutları tanımlamak birkaç dizeyi tanımlar. Bu kılavuzda daha sonra şu komutları uygular.  
  
#### <a name="to-define-the-command-ids"></a>Komut kimlikleri tanımlamak için
  
1.  WebPartNodeExtension proje WebPartCommandIds kod dosyasını açın ve ardından aşağıdaki kodu yapıştırın.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Özel SharePoint komutları oluşturma
 SharePoint sitesinde Web bölümleri hakkında veri almak SharePoint sunucusu nesne modeline çağrı özel komutlar oluşturur. Her bir komuttur olan bir yönteme <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> uygulanmış.  
  
#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutları tanımlamak için  
  
1.  WebPartCommands proje WebPartCommands kod dosyasını açın ve ardından aşağıdaki kodu yapıştırın.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 İzlenecek yol için tüm kod içinde bu noktada **Web Bölümü Galerisi'ne** düğüm ve SharePoint komutlarını kullanıma projeleri. Hem projede hata olmadan derleme emin olmak için çözümü oluşturun.  
  
#### <a name="to-build-the-solution"></a>Çözümü derlemek için  
  
1.  Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
    > [!WARNING]  
    >  Bu noktada, VSIX bildirim dosyası yazma için bir değer olmadığından WebPartNode proje derleme hatası olabilir. Sonraki adımlarda bir değer eklediğinizde, bu hata kaybolur.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için VSIX paketi oluşturmak için çözümünüzdeki VSIX projesi kullanın. İlk olarak, VSIX projesinde source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırın. Ardından çözümü oluşturarak VSIX paketini oluşturun.  
  
#### <a name="to-configure-the-vsix-package"></a>VSIX paketini yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, WebPartNode projesi altında açın **source.extension.vsixmanifest** bildirim düzenleyicisini dosyasında.  
  
     Source.extension.vsixmanifest dosyası, tüm VSIX paketleri gerektiren extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  İçinde **ürün adı** kutusuna **Sunucu Gezgini için Web Bölümü Galerisi düğümü**.  
  
3.  İçinde **Yazar** kutusuna **Contoso**.  
  
4.  İçinde **açıklama** kutusuna **Sunucu Gezgininde SharePoint bağlantıları için özel bir Web Bölümü Galerisi'ne düğümü ekler. Bu uzantı, sunucu nesne modeline çağrı için özel bir SharePoint komutu kullanır.**  
  
5.  Seçin **varlıklar** Düzenleyici sekmesini ve ardından **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
6.  İçinde **türü** listesinde **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `MefComponent` extension.vsixmanifest dosyasındaki öğesi. Bu öğe VSIX paketinde bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için [MEFComponent öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
8.  İçinde **proje** listesinde **WebPartNodeExtension** seçip **Tamam** düğmesi.  
  
9. Bildirim düzenleyicisinde seçin **yeni** düğmesini tekrar.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
10. İçinde **türü** kutusuna **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Bu öğe, Visual Studio Uzantısı'nda dahil etmek istediğiniz özel bir uzantı belirtir. Daha fazla bilgi için [varlık öğesi (VSX şema)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. İçinde **kaynak** listesinde **mevcut çözümde bir proje** liste öğesi.  
  
12. İçinde **proje** listesinde **WebPartCommands**ve ardından **Tamam** düğmesi.  
  
13. Menü çubuğunda, **derleme** > **Çözümü Derle**ve ardından çözüm hata olmadan derlediğinden emin olun.  
  
14. WebPartNode projesi yapı çıkış klasöründe artık WebPartNode.vsix dosyası içerdiğinden emin olun.  
  
     Varsayılan olarak, derleme çıktısı klasörü olduğu... \bin\Debug klasörüne proje dosyanızı içeren klasörün altında.  
  
## <a name="test-the-extension"></a>Uzantıyı test etmek
 Yeni test etmek artık hazırsınız **Web Bölümü Galerisi'ne** düğümünde **Sunucu Gezgini**. İlk olarak, Visual Studio'nun Deneysel örneğindeki uzantıyı hatalarını ayıklamaya başlayın. Ardından, yeni kullanın **Web Bölümleri** deneysel örneğinde düğümünde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>Uzantı hata ayıklamasını başlatmak için  
  
1.  Yeniden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yönetici kimlik bilgilerini ve WebPartNode çözümü açın.  
  
2.  WebPartNodeExtension projesinde SiteNodeExtension kod dosyasını açın ve ardından ilk kod satırına bir kesme noktası ekleyin `NodeChildrenRequested` ve `CreateWebPartNodes` yöntemleri.  
  
3.  Seçin **F5** hata ayıklamayı başlatmak için anahtar.  
  
     Visual Studio için sunucu Explorer\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Bölümü Galerisi düğüm uzantısı için uzantıyı yükleyen ve Visual Studio'nun deneysel örneği başlar. Proje öğesi bu Visual Studio örneğinde test edeceksiniz.  
  
#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için  
  
1.  Deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], menü çubuğunda, **görünümü** > **Sunucu Gezgini**.  
  
2.  Test etmek için kullanmak istediğiniz SharePoint sitesi altında görünmüyorsa, aşağıdaki adımları gerçekleştirin **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**:  
  
    1.  İçinde **Sunucu Gezgini**, kısayol menüsünü açın **SharePoint bağlantıları**ve ardından **Bağlantı Ekle**.  
  
    2.  İçinde **SharePoint bağlantısı ekleme** iletişim kutusunda, bağlanmak ve ardından istediğiniz SharePoint sitesi için URL'yi girin **Tamam** düğmesi.  
  
         Geliştirme bilgisayarınızda SharePoint sitesini belirtmek için girin **http://localhost**.  
  
3.  (Site URL'sini görüntüleyen) site bağlantı düğümü genişletin ve ardından bir alt site düğümünü genişletin (örneğin, **ekip sitesi**).  
  
4.  Doğrulayın diğer örneğindeki kodun [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] daha önce ayarladığınız kesme noktasında durur `NodeChildrenRequested` yöntemi ve ardından **F5** proje hatalarını ayıklamaya devam etmek için.  
  
5.  Visual Studio'nun deneysel örneğinde adlı yeni bir düğüm doğrulayın **Web Bölümü Galerisi'ne** en üst düzey sitesi düğümünde görünür ve genişletin **Web Bölümü Galerisi'ne** düğümü.  
  
6.  Visual Studio'nun diğer örneğindeki kodun daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `CreateWebPartNodes` yöntemini seçip **F5** proje hatalarını ayıklamaya devam etmek için anahtarı.  
  
7.  Visual Studio'nun deneysel örneğinde bağlı sitesindeki tüm Web Bölümleri altında göründüğünü doğrulayın. **Web Bölümü Galerisi'ne** düğümünde **Sunucu Gezgini**.  
  
8.  İçinde **Sunucu Gezgini**, Web Bölümleri biri için kısayol menüsünü açın ve ardından **özellikleri**.  
  
9. Örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayıkladığınız, Web bölümünü ayrıntılarını göründüğünü doğrulayın **özellikleri** penceresi.  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Visual Studio'dan uzantıyı kaldırın
 Uzantısını denetlemeniz bittikten sonra Visual Studio'dan uzantıyı kaldırın.  
  
#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için  
  
1.  Deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], menü çubuğunda, **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Uzantılar listesinde seçin **Web Bölümü Galerisi düğüm uzantısı için Sunucu Gezgini**ve ardından **kaldırma** düğmesi.  
  
3.  Görünen iletişim kutusunda **Evet** uzantıyı kaldırın ve ardından istediğinizi onaylamak için düğmeyi **şimdi yeniden Başlat** kaldırma işlemini tamamlamak için düğme.  
  
4.  (Deneysel örneği ve Visual Studio'nun WebPartNode çözüm açık olduğu örneği) Visual Studio'nun her iki örneklerini kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [İzlenecek yol: bir sunucu Gezgini uzantısında SharePoint istemcisi nesne modelini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)   
 [Simge veya başka görüntü oluşturma &#40;simgeler için görüntü Düzenleyicisi&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
