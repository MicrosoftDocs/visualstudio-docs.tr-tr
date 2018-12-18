---
title: "İzlenecek yol: bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio'ya içeri aktarma | Microsoft Docs"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 249799bc9daf13992bd9fe03dff8c86263f91263
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851484"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>İzlenecek yol: bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio'ya içeri aktarma
  Bu kılavuzda SharePoint Designer 2010 içinde oluşturulan bir yeniden kullanılabilir iş akışını içeri aktarma gösteren bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint iş akışı projesi.  
  
 SharePoint Tasarımcısı'nda oluşturulan iş akışları veya *bildirim temelli iş akışları*, oluşur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] yerine kod deyimlerini. SharePoint Designer 2010 tanıtır *yeniden kullanılabilir iş akışlarını*, farklı listelerinde SharePoint siteleri tarafından kullanılan taşınabilir, bildirim temelli iş akışları olduğu.  
  
 Oluşturulan iş akışları [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], sıralı ve durum makine iş akışları gibi adlı *kod iş akışları*. Kod iş akışları, XML dosyalarını ve kullanıcılar iş akışının davranışını özelleştirmek kod modülleri oluşur.  
  
 Visual Studio, SharePoint Designer 2010'da oluşturulan yeniden kullanılabilir iş akışlarını içeri aktarma ve SharePoint siteleriniz kullanmak için kodu iş akışları dönüştürmek sağlar.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Basit, yeniden kullanılabilir iş akışı, SharePoint Tasarımcısı'nda oluşturma.  
  
- SharePoint Designer yeniden kullanılabilir iş akışını dışarı aktarma bir *.wsp* dosya ve SharePoint içinde.  
  
- İçeri aktarma *.wsp* doyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] içeri aktarma yeniden kullanılabilir iş akışı projesi kullanarak.  
  
- Kod ekleyerek iş akışını değiştirme.  
  
- İçeri aktarılan iş akışı, bir SharePoint sitesinde kullanma.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] ve SharePoint.  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010'u.  
  
## <a name="create-target-sharepoint-subsites"></a>Hedef SharePoint alt siteleri oluşturma
 İlk olarak, iki yeni SharePoint alt siteleri oluşturun: biri dönüştürülmüş iş akışlarını barındırmak için başka bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışlarından barındırmak için.  
  
#### <a name="to-create-sharepoint-subsites"></a>SharePoint alt siteleri oluşturmak için  
  
1. SharePoint Designer 2010'da, menü çubuğunda, **dosya** > **yeni boş bir Web sitesi**.  
  
2. İçinde **yeni boş bir Web sitesi** iletişim kutusunda, istediğiniz iş akışı oluşturmak veya http:// değerini kullanmak için bir SharePoint sitesine<em>SystemName</em>/ seçip **Tamam** düğmesi.  
  
    Giriş sayfası görüntülenir.  
  
3. İçinde **alt** bölümünde, seçin **yeni** düğmesi.  
  
4. İçinde **yeni** iletişim kutusunda **SharePoint şablonları** sol bölmedeki listeden seçip **ekip sitesi** sağ bölmedeki listeden.  
  
5. İçinde **Web sitesi konumunu belirtin** kutusunda, sözcüğü değiştirmek **alt** ile URL'deki **SPD1**ve ardından **Tamam** düğmesi.  
  
    Bu, SharePoint Tasarımcısı içinde yeni alt açar. SharePoint Designer'ın bu örneği kapatın ve ilk örneğine (üst düzey site) geri dönün.  
  
6. İkinci alt sözcüğü değiştirerek bu kez oluşturmak için 3-5 arasındaki adımları yineleyin **alt** içinde [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] ile **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışını oluşturma
 SharePoint Bu örnek için kullanabileceğiniz tüm yeniden kullanılabilir iş akışlarını içermediğinden, bir oluşturacaksınız. Bir kullanıcı belirli bir başlığa sahip görev listesine yeni bir görev girdiğinde bu basit bir iş akışında, görev, kullanıcıya atanır.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer yeniden kullanılabilir iş akışı oluşturmak için
  
1.  İçinde **alt** bölümünde, seçin **SPD1** değiştirmek için site.  
  
2.  Şerit üzerinde **yeniden kullanılabilir iş akışını** düğmesi.  
  
     Yeniden kullanılabilir iş akışı oluşturma sihirbazı görünür.  
  
3.  İçinde **adı** kutusuna **SPD görev iş akışı**.  
  
4.  İçinde **içerik türü** listesinde **görev**ve ardından **Tamam** düğmesi.  
  
     İş Akışı Tasarımcısı SharePoint iş akışı Tasarımcısı'nda açılır.  
  
5.  İş akışı tasarımcısında, 1. Adım'ı seçin ve ardından, Şerit üzerinde **koşul** düğmesi.  
  
6.  Koşullar listesinde seçin **geçerli öğesi alanı değeri eşitse**.  
  
     Bu adım adlı bir koşul ekler **alanı değere eşitse**.  
  
7.  İçinde **alanı değere eşitse** koşul öğesini **alan** bağlantı.  
  
8.  Değerler listesinde seçin **başlık**.  
  
9. İçinde **alanı değere eşitse** koşul öğesini **değer** bağlantı.  
  
10. Kutusuna **yeni görev**.  
  
     Koşul deyimi artık okur **varsa geçerli madde: Başlık eşittir yeni görev**.  
  
11. Koşul deyimi altındaki seçin ve ardından, Şerit üzerinde **eylem** düğmesi.  
  
12. Eylemler listesinde seçin **geçerli öğe kümesi alanında**.  
  
13. İçinde **değer kümesi alanıyla** eylemi seçin **alan** bağlantısını ve ardından listeden seçin **atanan**.  
  
14. İçinde **değer kümesi alanıyla** eylemi seçin **değeri** bağlamak ve ardından, var olan kullanıcıları ve grupları listesinde **öğesini oluşturan kullanıcı**.  
  
15. Seçin **Ekle** düğmesine ve ardından **Tamam** düğmesi.  
  
     ACTION deyimi artık okur **atanan ayarlanacak için geçerli madde: oluşturan**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Kaydet ve yeniden kullanılabilir iş akışı dağıtma
 Çünkü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yalnızca içeri aktarabilirsiniz *.wsp* dosyaları, yeniden kullanılabilir iş akışı olarak kaydetmelisiniz bir *.wsp* dosya ve içine aktarmadan önce SharePoint'e dağıtmanıza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Aşağıdaki yordamı gerçekleştirmeden bir çalışma zamanı hatası alırsanız, SharePoint sitesine erişimi olan bir sisteme yordamı uygulamak zorunda.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Yeniden kullanılabilir iş akışını kaydetmek ve dağıtmak için  
  
1.  SharePoint Designer'ın en üstünde **Kaydet** ilerlemenizi kaydetmek için düğmesine ve ardından **Yayımla** düğme akışına dağıtmak için **SPD1** SharePoint sitesi .  
  
2.  Gezinti bölmesinde **iş akışları** nesne.  
  
3.  Altında **yeniden kullanılabilir iş akışını**, seçin **SPD görev iş akışı**.  
  
4.  Şerit üzerinde **şablon olarak Kaydet** iş akışı olarak kaydetmek için bir *.wsp* dosya.  
  
5.  Açık **SPD1** bir tarayıcıda görüntülemek için SharePoint sitesi *.wsp* SharePoint'te dosya.  
  
6.  Hızlı Başlat çubuğunda **kitaplıkları** bağlantı.  
  
7.  İçinde **belge kitaplıkları** bölümünde, seçin **sitesi varlıklarını** bağlantı.  
  
     **SPD görev iş akışı** dosyası, diğer site varlıklarla listelenir.  
  
8.  Dosyalar listesinde, bu dosyanın adını seçin  
  
9. İçinde **dosya indirme** iletişim kutusunda **Kaydet** kaydetmek için *.wsp* yerel sisteminizde dosyanın.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>.Wsp dosyasını Visual Studio'ya içeri aktarma
 İçeri aktarma *.wsp* doyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir yeniden kullanılabilir iş akışını içeri aktar projesi kullanarak. Bu proje iş akışını yeniden kullanılabilir, bildirim temelli bir iş akışından bir kod iş akışına dönüştürür. İş akışı dönüştürüldükten sonra kod davranışını değiştirmek için kullanın.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Bir iş akışını .wsp dosyasından içeri aktarmak ve değiştirmek için  
  
1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunda **SharePoint** ya da düğümünde **Visual C#** veya **Visual Basic**, seçin**2010** düğümü.  
  
3. İçinde **şablonları** bölmesinde seçin **yeniden kullanılabilir SharePoint 2010 iş akışını içeri aktar** şablon adı projenin bırakın **WorkflowImportProject1**seçin **Tamam** düğmesi.  
  
    SharePoint Özelleştirme Sihirbazı görünür.  
  
4. Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtin** want [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] daha önce oluşturduğunuz ikinci SharePoint alt site için: http://<em>sistem adı</em>/SPD2.  
  
5. İçinde **bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, seçin **Grup çözümü olarak Dağıt** seçenek düğmesini ve ardından **sonraki** düğmesi.  
  
    Korumalı hakkında daha fazla bilgi için küme çözümleri bkz [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md).  
  
6. İçinde **yeni proje kaynağını belirtin** sayfasında, daha önce kaydettiğiniz konuma gidin sistem üzerindeki *.wsp* dosya, dosyayı açın ve ardından **sonraki** düğmesi.  
  
   > [!NOTE]  
   >  Seçin **son** içindeki kullanılabilir tüm öğeleri içe aktarmak için düğmeyi *.wsp* dosya.  
  
    Bu, yeniden kullanılabilir iş akışlarını içeri aktarma için kullanılabilir bir listesini görüntüler.  
  
7. İçinde **içeri aktarılacak öğeleri seçin** kutusunda **SPD görev iş akışı** iş akışı ve ardından **son** düğmesi.  
  
    İçeri aktarma işlemi tamamlandıktan sonra bir proje adlı **WorkflowImportProject1** adlı bir iş akışı içeren oluşturulan **SPD_Workflow_TestFT**. İş akışının tanımı dosyası bu klasörde olduğu *Elements.xml* ve iş akışı Tasarımcısı dosyası (*.xoml*). Tasarımcı iki dosya içerir: kurallar dosyası (.rules) ve arka plan kod dosyası (ya da *.cs* veya *.vb*projenizin programlama diline bağlı olarak).  
  
8. İçinde **Çözüm Gezgini**, silme **diğer içeri aktarılan dosyaları** klasör.  
  
9. İçinde *Elements.xml* dosya, silme `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. İçinde **Çözüm Gezgini**, seçin **WorkflowImportProject1**ve ardından, menü çubuğunda, **proje** > **başlangıç projesi olarak ayarla**  ayarlanacak **WorkflowImportProject1** başlangıç öğesi olarak.  
  
     Hemen projede hata ayıklaması yaparken bu listede görüntülenir.  
  
11. Çünkü **yeniden kullanılabilir SharePoint 2010 iş akışını içeri aktarma** şablonu içeri aktarılan iş akışının ilişkilendirme özellik değerlerini alma değil, bunları girmeniz gerekir. Bunu yapmak için:  
  
    1.  İçinde **Çözüm Gezgini**, seçin **SPD_Workflow_TestFT** düğümü.  
  
    2.  Üç noktayı seçin (![ASP.NET Mobil Tasarımcısı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcısı elips")) gibi bir liste özelliklerinin yanında düğmesini **hedef liste** özelliği.  
  
    3.  SharePoint Özelleştirme Sihirbazı'nda bulunan eksik değerleri doldurun ve ardından **son** düğmesi.  
  
12. .Xoml dosyayı seçin ve ardından, menü çubuğunda, **görünümü** > **Tasarımcısı** alınan iş akışı iş akışı Tasarımcısı'nda görüntülenecek.  
  
13. İçinde **Windows iş akışı v3.0** düğümünün **araç kutusu**, aşağıdaki adımlardan birini gerçekleştirin:  
  
    - Kısayol menüsünü açın **kod** etkinliğini seçip **kopyalama**. İş Akışı Tasarımcısı'nda altındaki kısayol menüsünü açın **SequenceActivity1** etkinliğini seçip **Yapıştır**.  
  
    - Sürükleme **kod** etkinliğinden **araç kutusu** iş akışı Tasarımcısı için ve altındaki satıra bağlayın **SequenceActivity1** etkinlik.  
  
      Bu etkinlik adlı iş akışı Tasarımcısı için ekler **CodeActivity1**. Bu etkinlik, kullanıcı iş akışı başladığında duyuruları listesinde bir duyuru oluşturur kod bir eylem ekleyeceksiniz.  
  
14. Aşağıdaki adım kümelerinden birini uygulayın:  
  
    -   Çift **CodeActivity1** bir olay işleyicisi oluşturmak ve kodu görüntüleyin.  
  
    -   İçinde **özellikleri** penceresi **CodeActivity1**, değerini **ExecuteCode** özelliğini **codeActivity_ExecuteCode**.  
  
15. Varolan altında aşağıdaki **kullanarak** veya **içeri aktarmalar** ifadeleri:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Değiştirin `codeActivity1_ExecuteCode` aşağıdaki:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Projeyi dağıtma ve iş akışını ilişkilendirmek
 Ardından, WorkflowImportProject1 çalıştırma bir SharePoint sitesine dağıtma ve ardından iş akışını görüntülemek ve değiştirilmiş, test etmek için görev listesi ile ilişkilendirmek için iş akışı dönüştürülür.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Projeyi dağıtmak ve iş akışını ilişkilendirmek için  
  
1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seçin **F5** çalıştırın ve dönüştürülmüş iş akışı projesi dağıtmak için anahtar.  
  
2.  Hızlı Başlat çubuğunda **görevleri** Görevler listesini görüntülemek için bağlantı.  
  
3.  Üzerinde **liste Araçları** sekmesini, **öğeleri** düğmesine ve ardından **yeni öğe** düğmesi.  
  
     **Görevler - yeni öğe** iletişim kutusu açılır.  
  
4.  İçinde **başlık** kutusuna **yeni görev**ve ardından **Kaydet** düğmesi.  
  
5.  Üzerinde **liste Araçları** sekmesini, **listesi** düğmesine ve ardından **listesi ayarları** düğmesi.  
  
     **Listesi ayarları** sayfası görüntülenir.  
  
6.  İçinde **izinler ve Yönetim** bölümünde, seçin **iş akışı ayarları** bağlantı.  
  
     **İş akışı ayarları** sayfası görüntülenir.  
  
7.  Seçin **bir iş akışı Ekle** bağlantı.  
  
8.  İçinde **iş akışı** listesinde **WorkflowImportProject1 - SPD iş akışı Test**.  
  
9. İçinde **adı** kutusuna **SPD iş akışı Test**ve ardından **Tamam** düğmesi.  
  
10. Hızlı Başlat çubuğunda **görevleri** listesi.  
  
11. Yanındaki oku seçin **yeni görev**ve ardından listeden seçin **iş akışları**.  
  
12. İçinde **yeni bir iş akışının başlatılacağı** bölümünde, için bağlantıyı seçin **SPD iş akışı Test**ve ardından **Başlat** iş akışını başlatmak için düğmeye.  
  
    > [!NOTE]  
    >  Alternatif olarak, otomatik-bir iş akışı içeren bir liste iş akışı ayarları sihirbazını çalıştırma ve otomatik ilişkilendirilmesine yönelik iş akışı ayarlayarak ilişkilendirme.  
  
     İki eylem iş akışı tarafından gerçekleştirilen dikkat edin: görevin içinde göründüğü adınız **atanmış** sütun ve duyuru görünür **duyuruları** listesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)   
 [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
