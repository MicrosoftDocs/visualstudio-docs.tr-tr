---
title: 'İzlenecek yol: bir SharePoint proje öğesi türünü genişletme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 756486daa709efd6ce1ff697d6d190bb7f4a2e34
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295728"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>İzlenecek yol: bir SharePoint proje öğesi türünü genişletme
  Kullanabileceğiniz **iş verileri bağlantı modeli** SharePoint'te İş Verileri Bağlantısı (BDC) hizmeti için bir model oluşturmak için proje öğesi. Varsayılan olarak, bu proje öğesini kullanarak model oluşturduğunuzda modeldeki veriler kullanıcılara görüntülenmez. Ayrıca, kullanıcıların verileri görüntülemesini sağlamak için SharePoint'te bir dış liste oluşturmanız gerekir.  
  
 Bu kılavuzda, bir uzantı için oluşturacağınız **iş verileri bağlantı modeli** proje öğesi. Geliştiriciler, BDC modeli verileri görüntüler, projede bir dış liste oluşturmak için uzantıyı kullanabilir. Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Visual Studio uzantısı oluşturma iki ana görevleri gerçekleştirir:  
  
    -   Bu, BDC modelindeki verileri görüntüleyen bir dış liste oluşturur. Uzantı SharePoint Proje sistemi için nesne modeli oluşturmak için kullanır. bir *Elements.xml* listeyi tanımlayan dosya. Böylece BDC modeliyle birlikte dağıtılır de proje dosyası ekler.  
  
    -   Bir kısayol menü öğesi ekler **iş verileri bağlantı modeli** proje öğelerinde **Çözüm Gezgini**. Geliştiriciler, BDC modeli için bir dış liste oluşturmak için bu menü öğesine tıklayabilirsiniz.  
  
-   Uzantı derlemesini dağıtmak için Visual Studio Uzantısı (VSIX) paketini derleme.  
  
-   Uzantıyı test etme.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler ihtiyacınız vardır:  
  
- Microsoft Windows, SharePoint ve Visual Studio'nun desteklenen sürümleri.  
  
- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu izlenecek yolda **VSIX projesi** proje öğesini dağıtmak üzere bir VSIX paketi oluşturmak için SDK'sı şablonunda. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Aşağıdaki kavramları bilgisi yardımcı, ancak gerekli değildir, bu izlenecek yolu tamamlamak için:  
  
- BDC hizmeti [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Daha fazla bilgi için [BDC mimarisi](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
- BDC modelleri için XML şeması. Daha fazla bilgi için [BDC modeli altyapısı](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için iki proje oluşturmanız gerekir:  
  
- Proje öğesi uzantısını dağıtmak için VSIX paketi oluşturmak üzere bir VSIX projesi.  
  
- Proje öğesi uzantısını uygulayan sınıf kitaplığı projesi.  
  
  İzlenecek yol, proje oluşturmaya başlayın.  
  
#### <a name="to-create-the-vsix-project"></a>VSIX projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **genişletilebilirlik** düğümü.  
  
    > [!NOTE]  
    >  **Genişletilebilirlik** düğümüdür yalnızca, Visual Studio SDK yüklenmiş ise kullanılabilir. Daha fazla bilgi için bu konudaki Önkoşullar bölümüne bakın.  
  
4.  Üst kısmındaki listede **yeni proje** iletişim kutusunda **.NET Framework 4.5**.  
  
     SharePoint araç uzantıları .NET Framework'ün bu sürümünde özellikleri gerektirir.  
  
5.  Seçin **VSIX projesi** şablonu.  
  
6.  İçinde **adı** kutusuna **GenerateExternalDataLists**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **GenerateExternalDataLists** için proje **Çözüm Gezgini**.  
  
7.  Source.extension.vsixmanifest dosyası otomatik olarak açılmazsa GenerateExternalDataLists projesinde kısayol menüsünü açın ve ardından **açın**  
  
8.  Source.extension.vsixmanifest dosyası boş olmayan bir girdisi olduğunu doğrulayın (Contoso girin) Yazar alanı için dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **GenerateExternalDataLists** çözüm düğümüne seçin **Ekle**ve ardından **YeniProje**.  
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **Windows** düğümü.  
  
3.  İletişim kutusunun üst kısmındaki listede seçin **.NET Framework 4.5**.  
  
4.  Proje şablonları listesinde seçin **sınıf kitaplığı**.  
  
5.  İçinde **adı** kutusuna **Bdcprojectıtemextension**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **Bdcprojectıtemextension** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
6.  Projeden Class1 kod dosyasını silin.  
  
## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Proje öğesi uzantısını oluşturmak için kod yazmadan önce kod dosyalarını ve derleme referanslarını uzantı projesine ekleyin.  
  
#### <a name="to-configure-the-project"></a>Proje yapılandırma  
  
1.  Bdcprojectıtemextension projesinde aşağıdaki adlara sahip iki kod dosyasını ekleyin:  
  
    -   Projectıtemextension  
  
    -   GenerateExternalDataLists  
  
2.  Bdcprojectıtemextension projesini seçin ve ardından, menü çubuğunda, **proje** > **Başvuru Ekle**.  
  
3.  Altında **derlemeleri** düğümünü seçin **Framework** düğüm ve aşağıdaki derlemelerin her biri için onay kutusunu seçin:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  Altında **derlemeleri** düğümünü seçin **uzantıları** düğüm ve onay kutusunu seçin aşağıdaki derleme:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Seçin **Tamam** düğmesi.  
  
## <a name="define-the-project-item-extension"></a>Proje öğesi uzantısı tanımlama
 Uzantıyı tanımlayan bir sınıf oluşturmanız **iş verileri bağlantı modeli** proje öğesi. Sınıfının Implements uzantısı tanımlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> arabirimi. Varolan bir proje öğesi türünü genişletmek istediğinizde bu arabirimi uygulayın.  
  
#### <a name="to-define-the-project-item-extension"></a>Proje öğe uzantısını tanımlamak için  
  
1.  Aşağıdaki kodu Projectıtemextension kod dosyasına yapıştırın.  
  
    > [!NOTE]  
    >  Bu kodu ekledikten sonra projeyi bazı derleme hataları olacaktır. Sonraki adımlarda kod eklediğinizde, bu hatalar kaybolur.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="create-the-external-data-lists"></a>Dış veri listeleri oluşturma
 Kısmi bir tanımını ekleyin `GenerateExternalDataListsExtension` İVB Modeli her varlık için bir dış veri listesi oluşturan sınıf. Dış veri listesi oluşturmak için bu kod önce İVB modelindeki varlık verilerini XML verilerini İVB Modeli dosyasında ayrıştırarak okur. Sonra İVB modelini temel alıyor ve bu liste örneğini projeye ekler. bir liste örneği oluşturur.  
  
#### <a name="to-create-the-external-data-lists"></a>Dış veri listeleri oluşturmak için  
  
1.  Aşağıdaki kodu GenerateExternalDataLists kod dosyasına yapıştırın.  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu aşamada izlenecek yolda, proje öğesi uzantısı için kodun tümü artık projedir. Projenin hata olmadan derlediğinden emin olmak için çözümü oluşturun.  
  
#### <a name="to-build-the-solution"></a>Çözümü derlemek için  
  
1.  Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Proje öğesi uzantısını dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için VSIX paketi oluşturmak için çözümünüzdeki VSIX projesi kullanın. İlk olarak, VSIX projesine dahil olan source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırın. Ardından çözümü oluşturarak VSIX paketini oluşturun.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Yapılandırma ve VSIX paketini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**source.extension.vsixmanifest dosyası için kısayol menüsünü GenerateExternalDataLists projesi içinde açın ve ardından **açın**.  
  
     Visual Studio, dosyayı bildirim düzenleyicisinde açar. .Vsixmanifest uzantı dosyası temeli, tüm VSIX paketleri tarafından gerekli source.extension.vsixmanifest dosyasıdır. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  İçinde **ürün adı** kutusuna **dış veri listesi Oluşturucu**.  
  
3.  İçinde **Yazar** kutusuna **Contoso**.  
  
4.  İçinde **açıklama** kutusuna **dış veri listeleri oluşturmak için kullanılan iş verileri bağlantısı modeli proje öğeleri için bir uzantı**.  
  
5.  Üzerinde **varlıklar** sekmesini düzenleyicinin seçin **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
6.  İçinde **türü** listesinde **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `MefComponent` extension.vsixmanifest dosyasındaki öğesi. Bu öğe VSIX paketinde bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için [MEFComponent öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
8.  İçinde **proje** listesinde **Bdcprojectıtemextension**ve ardından **Tamam** düğmesi.  
  
9. Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
10. Projeyi derler ve hata olmadan derler emin olun.  
  
11. GenerateExternalDataLists projesinin yapı çıkış klasöründe artık GenerateExternalDataLists.vsix dosyasının olduğundan emin olun.  
  
     Varsayılan olarak, derleme çıktısı klasörü olduğu... \bin\Debug klasörüne proje dosyanızı içeren klasörün altında.  
  
## <a name="test-the-project-item-extension"></a>Proje öğesi uzantısını test etme
 Artık proje öğe uzantısını test etmeye hazırsınız. İlk olarak, Visual Studio'nun deneysel örneğinde bulunan uzantı projesinin hatalarını ayıklamaya başlayın. Ardından, BDC modeli için bir dış liste oluşturmak için Visual Studio'nun Deneysel örneğindeki uzantıyı kullanın. Son olarak, beklendiği gibi çalıştığını doğrulamak için SharePoint sitesinde dış listeyi açın.  
  
#### <a name="to-start-debugging-the-extension"></a>Uzantı hata ayıklamasını başlatmak için  
  
1.  Gerekirse, yönetici kimlik bilgileriyle Visual Studio'yu yeniden başlatın ve ardından GenerateExternalDataLists çözümünü açın.  
  
2.  Bdcprojectıtemextension projesinde Projectıtemextension kod dosyasını açın ve ardından kod satırına bir kesme noktası ekleyin `Initialize` yöntemi.  
  
3.  GenerateExternalDataLists kod dosyasını açın ve ardından ilk kod satırına bir kesme noktası ekleyin `GenerateExternalDataLists_Execute` yöntemi.  
  
4.  Seçim yaparak hata ayıklamayı Başlat **F5** anahtar veya, menü çubuğundan seçme **hata ayıklama** > **hata ayıklamayı Başlat**.  
  
     Visual Studio, uzantıyı %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data listesi generator\1. 0'dizinine yükler ve Visual Studio'nun deneysel örneği başlar. Proje öğesi bu Visual Studio örneğinde test edeceksiniz.  
  
#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **dosya** > **yeni** > **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **şablonları** düğümünü genişletin **Visual C#** düğümünü genişletin **SharePoint** düğümünü ve ardından seçin **2010**.  
  
3.  İletişim kutusunun üst kısmındaki listede olduğundan emin olun **.NET Framework 3.5** seçilir. Projeler için [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .NET Framework'ün bu sürümü gerekir.  
  
4.  Proje şablonları listesinde seçin **SharePoint 2010 projesi**.  
  
5.  İçinde **adı** kutusuna **SharePointProjectTestBDC**ve ardından **Tamam** düğmesi.  
  
6.  SharePoint Özelleştirme Sihirbazı'nda hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin **Grup çözümü olarak Dağıt**ve ardından **son** düğmesi.  
  
7.  SharePointProjectTestBDC projesi için kısayol menüsünü açın, **Ekle**ve ardından **yeni öğe**.  
  
8.  İçinde **newItem - SharePointProjectTestBDC Ekle** iletişim kutusunda, yüklenen dil düğümünü genişletin, **SharePoint** düğümü.  
  
9. Seçin **2010** düğümünü seçip **iş verileri bağlantı modeli (yalnızca Grup çözümü)** şablonu.  
  
10. İçinde **adı** kutusuna **TestBDCModel**ve ardından **Ekle** düğmesi.  
  
11. Visual Studio'nun diğer örneğindeki kodun ayarladığınız kesme noktasında durduğunu doğrulayın `Initialize` Projectıtemextension kod dosyasının yöntemi.  
  
12. Visual Studio'nun durdurulmuş örneğinde seçin **F5** tuşunu veya menü çubuğunda **hata ayıklama** > **devam** proje hatalarını ayıklamaya devam etmek için.  
  
13. Visual Studio'nun deneysel örneğinde seçin **F5** tuşunu veya menü çubuğunda, **hata ayıklama** > **hata ayıklamayı Başlat** derlemek, dağıtmak veya çalıştırmak **TestBDCModel** proje.  
  
     Web tarayıcısı SharePoint sitesinin, hata ayıklama için belirtilmiş varsayılan sayfasına açılır.  
  
14. Doğrulayın **listeler** bölümünde hızlı başlat alanında henüz projedeki varsayılan İVB modelini temel alan bir liste içermiyor. Öncelikle, SharePoint kullanıcı arabirimini kullanarak ya da proje öğesi uzantısını kullanarak bir dış veri listesi oluşturmanız gerekir.  
  
15. Web tarayıcısını kapatın.  
  
16. TestBDCModel projesinin açık olduğu Visual Studio örneğinde, kısayol menüsünü açın **TestBDCModel** düğümünde **Çözüm Gezgini**ve ardından **dış veri oluşturma Liste**.  
  
17. Visual Studio'nun diğer örneğindeki kodun ayarladığınız kesme noktasında durduğunu doğrulayın `GenerateExternalDataLists_Execute` yöntemi. Seçin **F5** tuşunu veya menü çubuğunda, **hata ayıklama** > **devam** proje hatalarını ayıklamaya devam etmek için.  
  
18. Visual Studio'nun deneysel örneğinde adlı bir örnek ekler **Entity1DataList** TestBDCModel proje ve örnek ayrıca oluşturur adlı bir özellik **Özellik2** listesi örneği.  
  
19. Seçin **F5** tuşunu veya menü çubuğunda, **hata ayıklama** > **hata ayıklamayı Başlat** derlemek, dağıtmak veya TestBDCModel projesini çalıştırın.  
  
     Web tarayıcısı SharePoint sitesinin, hata ayıklama için kullanılan varsayılan sayfasına açılır.  
  
20. İçinde **listeler** bölümü hızlı başlat alanında seçin **Entity1DataList** listesi.  
  
21. Listenin, ıdentifier1 değeri 0 ve ileti değeri Hello World olan bir öğeye ek olarak ıdentifier1 ve Message, adlandırılmış sütunlar içerdiğini doğrulayın.  
  
     **İş verileri bağlantı modeli** proje şablonu, tüm bu verileri sağlayan varsayılan BDC modelini oluşturur.  
  
22. Web tarayıcısını kapatın.  
  
## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme
 Proje öğesi uzantısını denetlemeniz bittikten sonra dış listeyi ve BDC modelini SharePoint sitesinden kaldırmak ve Visual Studio'dan proje öğesi uzantısını kaldırın.  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Dış veri listesini SharePoint sitesinden kaldırmak için  
  
1.  SharePoint sitesinin hızlı başlat alanında seçin **Entity1DataList** listesi.  
  
2.  SharePoint sitesindeki Şeritte seçin **listesi** sekmesi.  
  
3.  Üzerinde **listesi** sekmesinde **ayarları** Grup öğesini **listesi ayarları**.  
  
4.  Altında **izinler ve Yönetim**, seçin **bu listeyi Sil**ve ardından **Tamam** listeyi Geri Dönüşüm Kutusu'na göndermek istediğinizi onaylayın.  
  
5.  Web tarayıcısını kapatın.  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>BDC modelini SharePoint sitesinden kaldırmak için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **derleme** > **geri çek**.  
  
     Visual Studio, SharePoint sitesinden BDC modelini kaldırır.  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Visual Studio'dan proje öğesi uzantısını kaldırmak için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Uzantılar listesinde seçin **dış veri listesi Oluşturucu**ve ardından **kaldırma** düğmesi.  
  
3.  Görünen iletişim kutusunda **Evet** uzantının yüklemesini kaldırmak istediğinizi onaylayın.  
  
4.  Seçin **şimdi yeniden Başlat** kaldırma işlemini tamamlamak için.  
  
5.  (Deneysel örneği ve GenerateExternalDataLists çözümünün açık olduğu örneği) Visual Studio'nun her iki örneklerini kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint Proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)   
 [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  
