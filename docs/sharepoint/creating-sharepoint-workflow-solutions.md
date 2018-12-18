---
title: SharePoint iş akışı çözümleri oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4e808d93d2ae3039d4c5d79d1c14c65360bba32
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892317"
---
# <a name="create-sharepoint-workflow-solutions"></a>SharePoint iş akışı çözümleri oluşturma

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir SharePoint Web sitesinde liste öğelerini ve belgeleri yaşam döngüsünü yönetme özel iş akışları oluşturmanıza yardımcı olacak araçlar sağlar. Sağlanan öğe, Tasarımcı, bir dizi etkinlik denetimi ve gerekli derleme başvurularını içerir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca içerir **SharePoint Özelleştirme Sihirbazı**, oluşturma ve iş akışlarını yapılandırma yardımcı olmak için.

SharePoint ile ilgili daha fazla bilgi için bkz. [Microsoft SharePoint Ürünleri ve teknolojileri](http://go.microsoft.com/fwlink/?LinkId=178470).

## <a name="workflows-in-sharepoint"></a>SharePoint iş akışlarında
 Bir iş akışı için bir SharePoint kitaplığına veya liste eklediğinizde, bir iş sürecini kitaplık veya liste tüm öğelerde uygular. Bir iş akışının düzenlenmesi ve gözden öğesi gönderme gibi her öğe üzerinde sistem veya kullanıcıların gerçekleştirmesi gereken eylemleri açıklar. Bu eylemler olarak da bilinen, *etkinlikleri*, iş akışının yapı taşlarıdır.

 SharePoint iş akışlarında oluşturabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve bir SharePoint Web sitesine dağıtın. SharePoint için bir iş akışı dağıtıldıktan sonra bunu bir kitaplık veya liste ile ilişkilendirebilirsiniz. Bunun ardından otomatik olarak bir işlem tarafından veya el ile bir kullanıcı tarafından başlatılabilir. İş akışı işlemi hakkında daha fazla bilgi için bkz: [Visual Studio kullanarak SharePoint geliştirme iş akışları](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Özel bir SharePoint iş akışları oluşturun
 İki SharePoint iş akışı projeleri de kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **sıralı iş akışı** ve **Durum makinesi iş akışı**.

 A *sıralı iş akışı* bir dizi adımı temsil eder. Son Etkinlik tamamlanana kadar adımları birbiri ardına gerçekleştirilir. Sıralı iş akışı her zaman kendi yürütme kesinlikle sıralıdır. Çünkü bunlar dış olaylarını almak ve paralel mantık akışları dahil tam yürütme sırası değişebilir. Aşağıdaki çizimde, bir sıralı iş akışı örneği gösterilmektedir.

 ![Sıralı iş akışı](../sharepoint/media/sp-sequential.png "sıralı iş akışı")

 A *Durum makinesi iş akışı* durumları, geçişleri ve eylemleri kümesini temsil eder. Zaman uyumsuz olarak bir Durum makinesi iş akışı adımları yürütün. Bu kişiler mutlaka birbiri ardına gerçekleştirilmediğinden ancak bunun yerine Eylemler ve durumlar tarafından tetiklenen anlamına gelir. Bir durum başlangıç durumu atanır ve ardından, olay tabanlı, geçiş başka bir duruma yapılır. Durum makinesi iş akışı sonuna belirten bir son duruma sahip olabilir. Aşağıdaki diyagramda bir Durum makinesi iş akışı örneği gösterilmektedir.

 ![Durum makinesi iş akışı](../sharepoint/media/sp-state.png "Durum makinesi iş akışı")

 İş akışı türleri hakkında daha fazla bilgi için bkz. [iş akışı türlerini](http://go.microsoft.com/fwlink/?LinkId=178995).

### <a name="use-the-wizard"></a>Sihirbazı'nı kullanma
 Bir SharePoint iş akışı projesinde oluşturduğunuzda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], önce kendi ayarlarında belirttiğiniz **SharePoint Özelleştirme Sihirbazı**. Sihirbazı, bir proje oluşturmak için bu ayarları kullanır. **Çözüm Gezgini**. Bu proje bir kod dosyası, iş akışı dağıtmak için kullanılan birkaç dosyaları içerir ve özel bir SharePoint iş akışı oluşturmak için gereken derlemelere başvurur.

 İş akışını oluşturduktan sonra özelliklerini Özellikler penceresinde değiştirebilirsiniz. Çoğu iş akışı özelliklerini Özellikler penceresinde doğrudan değiştirilebilir rağmen bazı, üç nokta düğmesine tıklamanız gerekir (![ASP.NET Mobil Tasarımcısı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcısı elips")) için bunların değerlerini değiştirin. Bu düğmeyi yeniden **SharePoint Özelleştirme Sihirbazı**. Özelliği öğesini değer değişiklikleri yaptıktan sonra **son** bunları sonlandırmak için düğme.

> [!NOTE]
>  **İş akışı türü** özelliği salt okunurdur ve değiştirilemez. İş akışı türü değiştirmek istiyorsanız, başka bir iş akışı oluşturmanız gerekir.

## <a name="design-a-sharepoint-workflow"></a>Bir SharePoint iş akışı tasarlayın
 İş süreci içinde tüm adımları tanımladıktan sonra kullanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint iş akışı tasarlamak için iş akışı Tasarımcısı. Tasarımcısını açmak için çift tıklayın Workflow1.cs veya içinde Workflow1.vb **Çözüm Gezgini**, ya da bu dosyalar için kısayol menüsünü açın ve ardından **açın**.

### <a name="activities"></a>Etkinlikler
 Bir iş akışı tasarlamak için etkinlikler ekleme **araç kutusu** için bir *iş akışı zamanlama* Tasarımcı üzerinde. Bir iş akışı zamanlama bunlar gerçekleştirilmesini sırada etkinlik dizisini içerir.

 İki tür etkinlik vardır:

- *Basit etkinlikleri* iş, "1 gün için gecikme" veya "Web hizmeti başlatılamıyor." gibi tek bir birim

- *Bileşik etkinlikleri* diğer etkinlikleri içerir; örneğin, bir koşullu etkinlik iki dalı içerebilir.

  Her iki tür etkinlik mevcuttur **araç kutusu**.

  Etkinlikler, özellikleri, yöntemleri ve olayları olabilir. Kullanım **özellikleri** penceresinde etkinliğin özelliklerini ayarlamak için.

  Ayrıca, özel bir etkinlik oluşturabilirsiniz. Daha fazla bilgi için [izlenecek yol: özel site iş akışı faaliyeti oluşturma](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Etkinlikler, aşağıdaki sekmeleri düzenlenir **araç kutusu**:

- **SharePoint iş akışı**

- **Windows iş akışı v3.0**

- **Windows iş akışı v3.5**

  Tüm temel iş akışı etkinlikleri, SharePoint tarafından desteklenir. Daha fazla bilgi için [iş akışı etkinlikleri için Windows SharePoint Services Genel Bakış](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="sharepoint-workflow-activities"></a>SharePoint iş akışı etkinlikleri
 **SharePoint iş akışı** sekmeler içeren özel etkinlikleri kullanmak için [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Bu etkinlikler basitleştirebilir ve geliştirmeye yönelik belge yaşam döngüsü iş akışları. Listelenen etkinlikleri hakkında daha fazla bilgi için **SharePoint iş akışı** sekmesinde bkz [iş akışı etkinlikleri için Windows SharePoint Services Genel Bakış](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="windows-workflow-activities"></a>Windows iş akışı etkinlikleri
 **Windows iş akışı** sekmeler içeren tarafından sağlanan etkinlikler [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Bu etkinlikler, her türden bir Windows iş akışı uygulama için iş akışı tabloları oluşturmak için kullanabilirsiniz.

 Listelenen etkinlikleri hakkında daha fazla bilgi için **Windows iş akışları** sekmesinde bkz [Windows Workflow Foundation etkinlikleri](http://go.microsoft.com/fwlink/?LinkID=156096). Windows Workflow Foundation hakkında daha fazla bilgi için bkz: [Windows Workflow Foundation'a genel bakış](http://go.microsoft.com/fwlink/?LinkID=128632).

### <a name="work-with-activities-in-the-designer"></a>Tasarımcı etkinliklerle çalışma
 Windows iş akışı etkinlikleri ve SharePoint iş akışı etkinlikleri iş akışı zamanlamanızı içerebilir.

 Tasarımcı getirin ve etkinlikleri doğru şekilde yapılandırmanıza yardımcı olması için görsel ipuçları gösterir. Sürükleyin ya da kopyalama iş akışı zamanlama üzerine bir etkinliği Tasarımcı iş akışı bu etkinlik için geçerli konumları gösteren yeşil artı işaretini (+) simgeleri görüntüler. Bir etkinlik ise, geçerli olacağı olmayan bir konumda yerleştiremezsiniz. Örneğin, bir dinleme etkinlik dalda bir gönderme etkinlik ilk etkinlik olarak yerleştiremezsiniz. Daha fazla bilgi için [SharePoint Tasarımcı Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=178476).

## <a name="collect-information-during-the-workflow"></a>İş akışı sırasında bilgi toplamak
 Kullanıcılardan bilgi toplamak isteyebileceğiniz, önceden tanımlanmış zamanlarda iş akışı. Forms veya öğe özelliklerini kullanarak bilgi toplayabilirsiniz.

### <a name="forms"></a>Formlar
 Forms içeren sorular ve yanıtlar vermek üzere kullanıcılar için yollar sağlar, iletişim kutularını gibidir.

 Bir iş akışında kullanılabilecek forms dört tür vardır:

- İlişkilendirme

- Başlatma

- Değişiklik

- Görev

  Bu, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ilişki ve başlatma formları için öğe şablonları içerir. Örneği bir *ilişkilendirme formu* yükleme iş akışı Yöneticisi sağlayan bir girin bir harcama iş akışı için bir harcama sınırına gibi iş akışı ile ilgili parametreler. Örneği bir *başlatma formu* bir iş akışına harcadıkları süre girin kullanıcının bir iş akışının gider olanak sağlar. Bu form türleri hakkında daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Öğe özellikleri
 SharePoint kitaplığına veya listedeki bir öğe özelliklerini kullanarak kullanıcıların bilgilerini de toplayabilir. Ana kod dosyası (Workflow1.cs veya Workflow1.vb) adlı Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties sınıfının bir örneğini bildirir `workflowProperties`. Kullanım `workflowProperties` kitaplık veya liste kodda özelliklerine erişmek için nesne. Bir örnek için bkz. [izlenecek yol: oluşturma ve bir SharePoint iş akışı çözümü hata ayıklama](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Bir SharePoint iş akışı şablonu hata ayıklama
 Diğer hata ayıklama sırasında bir SharePoint iş akışı projesine aynı hataları [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Web tabanlı bir proje. Başladığınızda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcı, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belirttiğiniz ayarları kullanan **SharePoint Özelleştirme Sihirbazı** uygun SharePoint Web sitesini açın ve otomatik olarak iş akışı şablonunu ilişkilendirmek için uygun bir kitaplık veya liste ile. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca ekler [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] için hata ayıklayıcı [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] adlı işlem *w3wp.exe*.

 İş akışı test etmek için onu el ile başlatmanız gerekir. Daha fazla bilgi için bkz: "İş akışı hata ayıklama" bölümünde [SharePoint çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md). Hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Web uygulamasında hata ayıklama, bkz: [web uygulamalarında ve betikte hata ayıklama](../debugger/debugging-web-applications-and-script.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Bir SharePoint iş akışı şablonu dağıtma
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint iş akışı projeleri yalnızca diğer gibi dağıtma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projeleri. Daha fazla bilgi için [paketleme ve dağıtma SharePoint çözümleri](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Genel olarak yeniden kullanılabilir iş akışlarını içeri aktarma
 Siteye yeniden kullanılabilir iş akışlarını oluşturmaya ek olarak, SharePoint Designer oluşturmanızı sağlayan *genel olarak yeniden kullanılabilir iş akışlarını*, herhangi bir SharePoint sitesinin kullanılabilir iş akışlarını olduğu. Yeniden kullanılabilir iş akışını içeri aktarma projede [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] genel olarak yeniden kullanılabilir iş akışları şu anda içeri aktarmaz. Ancak, genel olarak yeniden kullanılabilir iş akışı bir yeniden kullanılabilir iş akışına dönüştürmek için SharePoint Designer'ı kullanın veya iş akışı Dönüştürülmeyen bildirim temelli bir iş akışı olarak alın. Daha fazla bilgi için [var olan bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: Oluşturma ve bir SharePoint iş akışı çözümü hata ayıklama](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Oluşturma ve basit bir hata ayıklama ile adım adım müşteri adayları [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı.|
|[İzlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Bir daha tam özellikli oluşturmak için adım adım müşteri adayları [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ilişki ve başlatma formları ile iş akışını tamamlayın.|
|[İzlenecek yol: bir uygulama sayfasını bir iş akışına ekleme](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Konuyla ilgili derlemeleri [izlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) ek ekleyerek *.aspx* iş akışınıza girdi veri çubuğunda raporları bir uygulama sayfası.|
|[İzlenecek yol: özel site iş akışı faaliyeti oluşturma](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|İki anahtar görevlerin nasıl gerçekleştirileceğini gösterir: site düzeyinde bir iş akışı oluşturma ve bir özel iş akışı etkinliği oluşturun.|
|[İzlenecek yol: bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio'ya içeri aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint Designer 2010 içinde oluşturulan yeniden kullanılabilir bildirim temelli iş akışlarını içeri aktarma gösteren bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint Proje.|

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Derleme ve SharePoint çözümlerinde hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)