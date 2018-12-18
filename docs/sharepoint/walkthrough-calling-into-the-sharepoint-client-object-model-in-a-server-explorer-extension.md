---
title: 'İzlenecek yol: Sunucu Gezgini uzantısında SharePoint istemcisi nesne modelini çağırma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f4510aa820e0f82c2fcd73ccb83ed0f8120a1399
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296040"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>İzlenecek yol: bir sunucu Gezgini uzantısında SharePoint istemcisi nesne modelini çağırma
  Bu izlenecek yol için bir uzantı SharePoint istemci nesne modelini nasıl çağırılacağını **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**. SharePoint istemci nesne modelini kullanma hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Oluşturma bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] genişleten uzantısı **SharePoint bağlantıları** düğümünün **Sunucu Gezgini** aşağıdaki yollarla:  
  
    -   Uzantı ekler bir **Web Bölümü Galerisi'ne** içindeki her bir SharePoint sitesi düğümün altında düğüm **Sunucu Gezgini**. Bu yeni düğüm her Web Bölümünü Web Bölümü galerisinde sitesinde temsil eden alt düğümleri içerir.  
  
    -   Uzantının yeni bir Web Bölümü örneğinin temsil eden bir düğüm türünü tanımlar. Bu yeni düğüm türü altındaki Yeni alt düğümleri temelini **Web Bölümü Galerisi'ne** düğümü. Yeni Web Bölümü düğüm türü bilgilerini görüntüler **özellikleri** penceresi hakkında düğümünü temsil eder. Web Bölümü.  
  
-   Uzantıyı dağıtmak için Visual Studio Uzantısı (VSIX) paketini derleme.  
  
-   Hata ayıklama ve uzantıyı test etme.  
  
> [!NOTE]  
>  Bu anlatımda oluşturduğunuz uzantıyı oluşturduğunuz uzantıyı benzer [izlenecek yol: Sunucu Gezgini web bölümlerini görüntülemek üzere genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Bu kılavuzda SharePoint sunucu nesne modeli kullanılır, ancak bu izlenecek yol, istemci nesne modelini kullanarak gerçekleştirdiğiniz görevlerin gerçekleştirir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler ihtiyacınız vardır:  
  
-   Windows, SharePoint ve Visual Studio'nun desteklenen sürümleri.
  
-   Visual Studio SDK. Bu izlenecek yolda **VSIX projesi** uzantısını dağıtmak için VSIX paketi oluşturmak için SDK'sı şablonunda. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
Aşağıdaki kavramları bilgisi yardımcı, ancak gerekli değildir, bu izlenecek yolu tamamlamak için:  
  
-   SharePoint istemci nesne modelini kullanma. Daha fazla bilgi için [yönetilen istemci nesne modelini](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   SharePoint Web Bölümleri. Daha fazla bilgi için [Web bölümlerine genel bakış](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için iki proje oluşturmanız gerekir:  
  
- Dağıtmak için VSIX paketi oluşturmak üzere bir VSIX projesi **Sunucu Gezgini** uzantısı.  
  
- Uygulayan bir sınıf kitaplığı projesi **Sunucu Gezgini** uzantısı.  
  
  İzlenecek yol, proje oluşturmaya başlayın.  
  
#### <a name="to-create-the-vsix-project"></a>VSIX projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **genişletilebilirlik**.  
  
    > [!NOTE]  
    >  **Genişletilebilirlik** düğümüdür yalnızca, Visual Studio SDK yüklenmiş ise kullanılabilir. Daha fazla bilgi için bu konudaki Önkoşullar bölümüne bakın.  
  
4.  İletişim kutusunun en üstünde **.NET Framework 4.5** .NET Framework sürümleri listesinde.  
  
     SharePoint araç uzantıları .NET Framework'ün bu sürümünde özellikleri gerektirir.  
  
5.  Seçin **VSIX projesi** şablonu.  
  
6.  İçinde **adı** kutusuna **WebPartNode**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **WebPartNode** için proje **Çözüm Gezgini**.  
  
#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **Windows**.  
  
3.  İletişim kutusunun en üstünde **.NET Framework 4.5** .NET Framework sürümleri listesinde.  
  
4.  Proje şablonları listesinde seçin **sınıf kitaplığı**.  
  
5.  İçinde **adı** kutusuna **WebPartNodeExtension**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **WebPartNodeExtension** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
6.  Projeden Class1 kod dosyasını silin.  
  
## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Uzantısını oluşturmak için kod yazmadan önce kod dosyaları ve derleme başvuruları projenize ekleyin ve varsayılan ad alanı güncelleştirmeniz gerekir.  
  
#### <a name="to-configure-the-project"></a>Proje yapılandırma  
  
1.  İçinde **WebPartNodeExtension** proje, SiteNodeExtension ve WebPartNodeTypeProvider adlı iki kod dosyasını ekleyin.  
  
2.  WebPartNodeExtension proje için kısayol menüsünü açın ve ardından **Başvuru Ekle**.  
  
3.  İçinde **başvuru Yöneticisi - WebPartNodeExtension** iletişim kutusunda **Framework** düğüm ve onay kutularını seçin System.ComponentModel.Composition ve System.Windows.Forms bütünleştirilmiş kodları.  
  
4.  Seçin **uzantıları** düğümü, her biri aşağıdaki derlemeler için onay kutusunu işaretleyin ve ardından **Tamam** düğmesi:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Kısayol menüsünü açın **WebPartNodeExtension** proje ve ardından **özellikleri**.  
  
     **Proje Tasarımcısı** açılır.  
  
6.  Seçin **uygulama** sekmesi.  
  
7.  İçinde **varsayılan ad alanı** kutusu (C#) veya **kök ad alanı** (Visual Basic) kutusuna **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="create-icons-for-the-new-nodes"></a>Simgeler için yeni düğümler oluşturma
 Oluşturmak için iki simgeyi **Sunucu Gezgini** uzantısı: yeni bir simge **Web Bölümü Galerisi'ne** düğüm ve her bir alt Web Bölümü düğümün altında başka bir simge **Web Bölümü Galerisi'ne** düğüm. Bu kılavuzda daha sonra bu simgeleri düğümleri ile ilişkilendiren kod yazacaksınız.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Düğümler için simgeler oluşturmak için  
  
1.  İçinde **Proje Tasarımcısı** WebPartNodeExtension proje için seçme **kaynakları** sekmesi.  
  
2.  Bağlantıyı seçin **bu projenin varsayılan kaynak dosyası içermiyor. Oluşturmak için buraya tıklayın.**  
  
     Visual Studio, bir kaynak dosyası oluşturur ve tasarımcıda açılır.  
  
3.  Tasarımcı üstüne oku seçin **kaynak Ekle** menü komutunu ve ardından **yeni Simge Ekle**.  
  
4.  Girin **WebPartsNode** için yeni simgesine adlandırın ve ardından **Ekle** düğmesi.  
  
     İçinde yeni simge açıldıktan **Resim Düzenleyicisi**.  
  
5.  Simgenin 16 x 16 sürümü kolayca tanıyacak bir tasarıma sahip olacak şekilde düzenleyin.  
  
6.  Simgenin 32 x 32 sürümü için kısayol menüsünü açın ve ardından **Sil görüntü türü**.  
  
7.  3 ila 7 ikinci simgeyi Proje kaynakları eklemek için adımları yineleyin ve bu simgeyi ad **WebPart**.  
  
8.  İçinde **Çözüm Gezgini**, **kaynakları** klasör **WebPartNodeExtension** projesinin *WebPartsNode.ico*.  
  
9. İçinde **özellikleri** penceresini açık **derleme eylemi** listeleyin ve ardından **gömülü kaynak**.  
  
10. Son iki adımı yineleyin *WebPart.ico*.  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Sunucu Gezginine web bölümü galerisinde düğüm ekleme
 Ekleyen yeni bir sınıf oluşturmanız **Web Bölümü Galerisi'ne** her SharePoint sitesi düğüme düğüm. Sınıf uygular yeni düğümü eklemek için <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> arabirimi. Mevcut bir düğümün davranışını genişletmek istediğinizde bu arabirimi uygulayan **Sunucu Gezgini**, bir düğüme yeni bir alt düğüm ekleme gibi.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Sunucu Gezgini web bölümü galerisinde düğümü eklemek için
  
1.  Aşağıdaki kodu yapıştırın **SiteNodeExtension** kod dosyası **WebPartNodeExtension** proje.  
  
    > [!NOTE]  
    >  Bu kodu ekledikten sonra projeyi bazı derleme hataları olacaktır. Sonraki adımlarda kod eklediğinizde, bu hatalar kaybolur.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Bir web bölümü temsil eden bir düğüm türünü tanımlayın
 Yeni bir Web Bölümü temsil eden bir düğüm türünü tanımlayan bir sınıf oluşturun. Visual Studio altında alt düğümler görüntülemek için bu yeni düğüm türü kullanır **Web Bölümü Galerisi'ne** düğümü. Bu alt düğümler, SharePoint sitesindeki tek bir Web Bölümü temsil eder.  
  
 Yeni bir düğüm türü, sınıfın uyguladığı tanımlamak için <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> arabirimi. Düğümünde yeni bir tür tanımlamak istediğinizde bu arabirimi uygulayan **Sunucu Gezgini**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Web bölümü düğüm türü tanımlamak için
  
1.  Aşağıdaki kodu yapıştırın **WebPartNodeTypeProvider** kod dosyası **WebPartNodeExtension** proje.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 İzlenecek yol için tüm kod içinde bu noktada **Web Bölümü Galerisi'ne** düğümünü projede sunuldu. Derleme **WebPartNodeExtension** hata olmadan derlediğinden emin olmak için proje.  
  
#### <a name="to-build-the-project"></a>Projeyi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **WebPartNodeExtension** proje ve ardından **yapı**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için VSIX paketi oluşturmak için çözümünüzdeki VSIX projesi kullanın. İlk olarak, projeye dahil olan source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırın. Ardından çözümü oluşturarak VSIX paketini oluşturun.  
  
#### <a name="to-configure-the-vsix-package"></a>VSIX paketini yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, **WebPartNode** projesini açarsanız **source.extension.vsixmanifest** bildirim düzenleyicisini dosyasında.  
  
     Source.extension.vsixmanifest dosyası, tüm VSIX paketleri gerektiren extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  İçinde **ürün adı** kutusuna **Sunucu Gezgini için Web Bölümü Galerisi düğümü**.  
  
3.  İçinde **Yazar** kutusuna **Contoso**.  
  
4.  İçinde **açıklama** kutusuna **Sunucu Gezgininde SharePoint bağlantıları için özel bir Web Bölümü Galerisi'ne düğüm ekler**.  
  
5.  Üzerinde **varlıklar** sekmesini düzenleyicinin seçin **yeni** düğmesi.  
  
6.  İçinde **yeni varlık Ekle** iletişim kutusundaki **türü** listesinde **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `MefComponent` extension.vsixmanifest dosyasındaki öğesi. Bu öğe VSIX paketinde bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için [MEFComponent öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
8.  İçinde **proje** listesinde **WebPartNodeExtension**ve ardından **Tamam** düğmesi.  
  
9. Menü çubuğunda, **derleme** > **Çözümü Derle**ve ardından çözüm hata olmadan derlediğinden emin olun.  
  
10. WebPartNode projesi yapı çıkış klasöründe artık WebPartNode.vsix dosyası içerdiğinden emin olun.  
  
     Varsayılan olarak, derleme çıktısı klasörü olduğu... \bin\Debug klasörüne proje dosyanızı içeren klasörün altında.  
  
## <a name="test-the-extension"></a>Uzantıyı test etmek
 Yeni test etmek artık hazırsınız **Web Bölümü Galerisi'ne** düğümünde **Sunucu Gezgini**. Visual Studio'nun bir deneysel örneğinde bulunan uzantı projesinin hatalarını ayıklamak ilk olarak başlatın. Daha sonra yeni kullanın **Web Bölümleri** Visual Studio'nun deneysel örneğinde düğümü.  
  
#### <a name="to-start-debugging-the-extension"></a>Uzantı hata ayıklamasını başlatmak için  
  
1.  Yönetici kimlik bilgileriyle Visual Studio'yu yeniden başlatın ve ardından açın **WebPartNode** çözüm.  
  
2.  WebPartNodeExtension projeyi **SiteNodeExtension** kod dosyası ve bir kesme noktası ilk kod satırlarını eklemek `NodeChildrenRequested` ve `CreateWebPartNodes` yöntemleri.  
  
3.  Seçin **F5** hata ayıklamayı başlatmak için anahtar.  
  
     Visual Studio için sunucu Explorer\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Bölümü Galerisi düğüm uzantısı için uzantıyı yükleyen ve Visual Studio'nun deneysel örneği başlar. Proje öğesi bu Visual Studio örneğinde test edeceğiz.  
  
#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **görünümü** > **Sunucu Gezgini**.  
  
2.  Test etmek için kullanmak istediğiniz SharePoint sitesi altında göründüğünü doğrulayın **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**. Bu listede yoksa aşağıdaki adımları izleyin:  
  
    1.  Kısayol menüsünü açın **SharePoint bağlantıları**ve ardından **Bağlantı Ekle**.  
  
    2.  İçinde **SharePoint bağlantısı ekleme** iletişim kutusunda, bağlanmak ve ardından istediğiniz SharePoint sitesi için URL'yi girin **Tamam** düğmesi.  
  
         Geliştirme bilgisayarınızda SharePoint sitesini belirtmek için şunu yazın **http://localhost**.  
  
3.  (Site URL'sini görüntüleyen) site bağlantı düğümü genişletin ve ardından bir alt site düğümünü genişletin (örneğin, **ekip sitesi**).  
  
4.  Visual Studio'nun diğer örneğindeki kodun daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `NodeChildrenRequested` yöntemini seçip **F5** proje hatalarını ayıklamaya devam etmek için anahtarı.  
  
5.  Visual Studio'nun deneysel örneğinde genişletin **Web Bölümü Galerisi'ne** düğümü, üst düzey site düğümü altında görüntülenir.  
  
6.  Visual Studio'nun diğer örneğindeki kodun daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `CreateWebPartNodes` yöntemini seçip **F5** proje hatalarını ayıklamaya devam etmek için anahtarı.  
  
7.  Visual Studio'nun deneysel örneğinde bağlı sitesindeki tüm Web Bölümleri altında göründüğünü doğrulayın. **Web Bölümü Galerisi'ne** düğümünde **Sunucu Gezgini**.  
  
8.  Bir Web Bölümü için kısayol menüsünü açın ve ardından **özellikleri**.  
  
9. İçinde **özellikleri** penceresinde Web bölümünü ayrıntılarını göründüğünü doğrulayın.  
  
10. İçinde **Sunucu Gezgini**, aynı Web Bölümü için kısayol menüsünü açın ve ardından **iletisini görüntüle**.  
  
     Görüntülenen ileti kutusunda **Tamam** düğmesi.  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Visual Studio'dan uzantıyı kaldırın
 Uzantısını denetlemeniz bittikten sonra bunu Visual Studio'dan kaldırın.  
  
#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Uzantılar listesinde seçin **Sunucu Gezgini için Web Bölümü Galerisi düğümü**ve ardından **kaldırma** düğmesi.  
  
3.  Görünen iletişim kutusunda **Evet** düğmesi.  
  
4.  Seçin **şimdi yeniden Başlat** kaldırma işlemini tamamlamak için düğme.  
  
     Proje öğesi de kaldırıldığında kaldırılır.  
  
5.  (Deneysel örneği ve Visual Studio'nun WebPartNode çözüm açık olduğu örneği) Visual Studio'nun her iki örneklerini kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [İzlenecek yol: Sunucu Gezgini, web bölümlerini görüntülemek üzere genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)   
 [Simge veya başka görüntü oluşturma &#40;simgeler için görüntü Düzenleyicisi&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)