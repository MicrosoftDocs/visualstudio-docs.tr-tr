---
title: Outlook form bölgeleri oluşturma
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5d4aed381841d5f88209aefdcff641a2a821f01
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673087"
---
# <a name="create-outlook-form-regions"></a>Outlook form bölgeleri oluşturma
  Form bölgeleri, Microsoft Office Outlook formları özelleştirmek için kullanabilirsiniz. Visual Studio tasarlamak, geliştirmek ve hata ayıklama form bölgeleri kolaylaştıran gelişmiş araçlar sağlar.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:  
  
-   [Form bölgeleri kullanmanın avantajları](#Enhance)  
  
-   [Outlook form bölgesi projenize ekleyin.](#Adding)  
  
-   [Form bölgesi tasarımcısı kullanma](#UsingFormRegionDesigner)  
  
-   [Outlook'ta tasarlanan form bölgesini kullanın](#UsingFormRegionDesignedOutlook)  
  
-   [Form bölgesi için özel kod ekleme](#AddingCustomCode)  
  
-   [Proje derleme](#Building)  
  
-   [Form bölgesini hata ayıklama](#Debugging)  
  
-   [Form bölgesine dağıtma](#Deploying)  
  
##  <a name="Enhance"></a> Form bölgeleri kullanmanın avantajları  
 Form bölgeleri, geleneksel Outlook Form geliştirmesine birçok geliştirme sunar:  
  
- Varsayılan sayfayı standart herhangi formunun özelleştirin.  
  
- Herhangi bir standart formun 12 adede kadar ek sayfaları ekleyin.  
  
- Değiştirin veya herhangi bir standart biçimde geliştirebilirsiniz.  
  
- Özel kullanıcı Arabirimi, okuma bölmesinde ve denetçiler görüntüleyebilirsiniz.  
  
  Daha fazla bilgi için [özelleştirme form sayfaları ve form bölgeleri](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).  
  
##  <a name="Adding"></a> Outlook form bölgesi projenize ekleyin.  
 Kullanabileceğiniz **yeni Outlook Form bölgesi** yeni bir form bölgesi tasarla ya da Outlook'ta tasarlanan form bölgesini içeri aktarma Sihirbazı. Ayrıca, Outlook VSTO eklentisi başka bir projede kullanılan bir form bölgesi varsa, var olan form bölgesinin yeniden kullanabilirsiniz.  
  
###  <a name="CreatingFormRegion"></a> Sihirbazı kullanarak yeni bir form bölgesi oluşturma  
 Form bölgesi oluşturmak için bir **Outlook Form bölgesi** Outlook VSTO eklenti projesinde öğesine. Bu başlatır **yeni Outlook Form bölgesi** Sihirbazı.  
  
 Sihirbaz, yeni bir form bölgesi tasarla ya da Outlook'ta tasarlanan form bölgesini içeri aktarmak istediğinizi belirtmek için kullanın. Yeni form bölgesi tasarlama hakkında daha fazla bilgi için bkz. [form bölgesi tasarımcısı kullanma](#UsingFormRegionDesigner). Outlook'ta tasarlanan form bölgesini kullanma hakkında daha fazla bilgi için bkz. [Outlook'ta tasarlanan form bölgesini içeri aktarma](#UsingFormRegionDesignedOutlook).  
  
 Oluşturmak istediğiniz form bölgesi türünü belirtmek için bu sihirbazı kullanın. Aşağıdaki tabloda her bir form bölgesinin türünü açıklar.  
  
|Bölge türü|Açıklama|  
|-----------------|-----------------|  
|Ayrı|Form bölgesinin Outlook formunda yeni bir sayfa olarak ekler.|  
|Bitişik|Form bölgesinin Outlook formun varsayılan sayfasını altına ekler.|  
|Değiştirme|Form bölgesini Outlook formun varsayılan sayfasını değiştirir yeni bir sayfa olarak ekler.|  
|Tümünü Değiştir|Tüm Outlook form, form bölgesi ile değiştirir.|  
  
 Sihirbaz, görünen koşulları belirtmek ve genişletmek için form türünü seçmek için de kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Sihirbazda yaptığınız seçimlere diğer sihirbaz sayfalarında kullanılabilir seçenekleri etkiler. Örneğin, **bitişik** veya **ayrı** içinde **yeni bir Outlook Form bölgesi oluşturabilir** sayfası, ardından **başlık** ve **Açıklama** alanları kullanılamaz **açıklayıcı metni sağlayın ve görüntüleme tercihlerinizi seçin** sayfası. Outlook bitişik veya ayrı bir form bölgesi gösterildiğinde bu alanlar kullanmadığından budur.  
  
#### <a name="form-region-files"></a>Form bölgesi dosyaları  
 Tamamlandığında, **yeni Outlook Form bölgesi** Sihirbazı, Visual Studio otomatik olarak aşağıdaki dosyaları projenize ekler:  
  
-   Form bölgesi kod dosyası. Bu dosya için belirttiğiniz ada sahip **Outlook Form bölgesi** öğesi **Yeni Öğe Ekle** iletişim kutusu. Bu dosya için form bölgesi olaylarını işlemek için kod ekleyin.  
  
-   Form bölgesi Tasarımcısı kod dosyası. Bu dosya, form bölgesi tasarımcısı tarafından yaratılan kodu içerir ve be doğrudan düzenlenemez.  
  
-   Outlook Form Depolama (*.ofs*) dosyası.  
  
    > [!NOTE]  
    >  Outlook'ta tasarlanan form bölgesini içeri aktarırsanız bu dosya projeye eklenir.  
  
#### <a name="form-region-factory-class"></a>Form bölgesi fabrikası sınıfı  
 Form bölgesi dosyasını uygulayan bir parçalı sınıf içeren <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> arabirimi. Bu form bölgesi fabrikası sınıftır. Form bölgesi fabrikası sınıfı form bölgesinin yeni örneklerini oluşturmaktan sorumludur.  
  
 Bu sınıf genişleterek bulabileceğinizi **Form bölgesi fabrikası** bölge.  
  
 **Yeni Outlook Form bölgesi** sihirbaz iç form bölgesinin adını bu sınıf ve form bölgesinin ileti sınıfları için öznitelikler ekler. Dosyayı projeye eklendikten sonra bu öznitelikleri el ile değiştirebilirsiniz.  
  
 Form bölgesi fabrikası sınıfı çoğunu form bölgesi tasarımcısı dosyasında gerçekleştirilir. Ancak, `FormRegionInitializing` form bölgesi kod dosyasında olay işleyicisi Internet'e açık. Outlook form bölgesi görüntülemesi gerekip gerekmediğini belirtmek için bu olay işleyicisi kullanabilirsiniz. Daha fazla bilgi için [form bölgesi olaylarını işleme](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a> Varolan bir form bölgesi projenize ekleyin.  
 Başka bir Outlook projesinde kullanılan Outlook form bölgesi varsa, onu geçerli Outlook VSTO eklenti projenizde kullanarak tekrar kullanabilirsiniz **varolan öğeyi Ekle** iletişim kutusu.  
  
 Var olan form bölgesinin bir kod dosyası olması gerekir (*.vb* veya *.cs*); Outlook Form Depolama eklenemiyor (*.ofs*) kullanarak dosyaları **varolan öğeyi Ekle** iletişim kutusu. Ancak, bir Outlook Form Depolama dosyasını içeri aktararak yeni bir form bölgesi oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a> Form bölgesi tasarımcısı kullanma  
 Form bölgesi tasarımcısı düzeninin ve görünümünün bir form bölgesinin tasarlamanıza yardımcı olur. Yönetilen denetimleri Tasarımcı yüzeyine sürükleyin, olay işleyicileri açmak için denetimleri çift tıklayın ve kümesinde özellikleri **özellikleri** penceresi.  
  
> [!NOTE]  
>  Form bölgesinin Outlook'ta görünümünü etkileyen özellikler bulabilirsiniz **bildirim** düğümünde **özellikleri** penceresi.  
  
 Form bölgesi tasarımcısı yalnızca seçerseniz kullanılabilir **yeni bir Form Bölgesi Tasarla** içinde **nasıl form bölgesi oluşturmak istediğinizi seçin** sayfasının **yeni Outlook Form bölgesi** Sihirbaz.  
  
 Form bölgesi Tasarımcısı'nı açmak için üç yolu vardır:  
  
- İçinde **Çözüm Gezgini**, form bölgesi kod dosyasına çift tıklayın.  
  
- İçinde **Çözüm Gezgini**form bölgesi kod dosyasına sağ tıklayın ve ardından **Görünüm Tasarımcısı**.  
  
- İçinde **Çözüm Gezgini**, form bölgesi kod dosyası seçin ve ardından **görünümü** menüsünde tıklatın **Tasarımcısı**.  
  
  Sadece yönetilen denetimleri form bölgesi tasarımcısı destekler. Yerel Outlook denetimleri ekleyemezsiniz.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Outlook'ta tasarlanan form bölgesini içeri aktarma  
 Outlook'ta tasarlarken, form bölgesinin yerel Outlook denetimler ekleyebilirsiniz. Yerel Outlook denetimleri, tasarım zamanında Outlook verileri bağlamanıza olanak sağlar. Ancak, yönetilen denetimleri eklemek veya form bölgesi tasarımını değiştirmek için daha sonra form bölgesi tasarımcısı kullanamazsınız.  
  
 Bir Outlook VSTO eklenti projesine form bölgeleri kullanarak aktarabilirsiniz **yeni Outlook Form bölgesi** Sihirbazı. Üzerinde **nasıl form bölgesi oluşturmak istediğinizi seçin** sayfasında **Outlook Form Depolama (.ofs) dosyasını içeri aktarma**. Ardından, bir Outlook Form Depolama dosyasının konumuna göz atabilirsiniz (*.ofs*) dosyası. (Outlook form bölgeleri olarak kaydeder *.ofs* dosyalarını.)  
  
 **Yeni Outlook Form bölgesi** Sihirbazı kopyaları *.ofs* dosyası proje dizinine ve denetimi form bölgesi tasarımcısı dosyası başvuruları ekler. Ardından, form bölgesi kod dosyasında denetim olayları işleyebilir.  
  
 Visual Basic projesinde olayları işlemek için Kod Düzenleyicisi'nin üst yöntemi adı listesinden bir olay seçin.  
  
 Olayları işlemek için bir C# proje, denetim olayları abone <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> yöntemi. Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan &#40;C&#35; Programlama Kılavuzu&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).  
  
 Form bölgesi özelliklerini değiştirebilirsiniz `InitializeManifest` form bölgesi fabrikası sınıfının yöntemi.  
  
> [!NOTE]  
>  Form bölgesini içeri aktarmak için geliştirme bilgisayarında yüklü olan Outlook aynı sürümünü hedefleyen bir projede çalışıyor olmalıdır. Outlook 2010 yüklüyse, örneğin, form bölgesi olacak yalnızca iş projesinde içeri aktarma kullanılarak oluşturulmuş **Outlook 2010 Eklentisi** proje şablonu.  
  
### <a name="update-an-imported-form-regions-design"></a>Bir içeri aktarılan form bölgesinin tasarımını güncelleştir  
 Ekleme, kaldırma veya form bölgesinin denetimlere değiştirme. Bunu yapmadan önce form bölgesi kod dosyasına eklemiş olduğunuz koddan yedekleyin. Ardından, açın *.ofs* dosyası Outlook'taki form bölgesini değiştirin ve değişiklikleri kaydedin. Kullanım **yeni Outlook Form bölgesi** değiştirilmiş içeri aktarmak için sihirbaz *.ofs* dosya. Ardından, kodunuzu yeni form bölgesi kod dosyasına yapıştırabilirsiniz.  
  
##  <a name="AddingCustomCode"></a> Form bölgesi için özel kod ekleme  
 <xref:Microsoft.Office.Tools.Outlook> Ad alanı, form bölgesini temsil eden sınıfları, form bölgesini görüntüleyen Outlook öğesine ve diğer yararlı öğelere erişim sağlar. **Outlook Form bölgesi** öğesine otomatik olarak projedeki bu derlemeye bir başvuru ekler ve uygun ekler **kullanarak** veya **içeri aktarmalar** en üstündeki deyimi Form bölgesi kod dosyası.  
  
 Sınıfları, yöntemleri ve özellikleri kullanabilirsiniz `Microsoft.Office.Interop.Outlook` , Outlook programlama görevlerinin çoğunu gerçekleştirmek için ad alanı. Outlook nesne modeli hakkında daha fazla bilgi için bkz: [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md). Outlook nesne modelini kullanmak için bkz tipik görev örnekleri için [Outlook çözümleri](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a> Form bölgesi olaylarını işleme  
 **Outlook Form bölgesi** öğesi aşağıdaki üç olay işleyicileri form bölgesi kod dosyasına otomatik olarak ekler.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|FormRegionInitializing|Form bölgesi başlatılmadan önce gerçekleşir. Outlook form bölgesi görüntülemesi gerekip gerekmediğini belirlemek için bu olay işleyicisi koşullarında kontrol edebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Outlook'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Form bölgesinin örneği oluşturulur ancak form bölgesi görünmeden önce sonra gerçekleşir.|  
|FormRegionClosed|Form bölgesinin kapatılmadan hemen önce gerçekleşir.|  
  
##  <a name="Building"></a> Proje derleme  
 Form bölgesini içeren bir Outlook VSTO eklentisi projesi oluşturduğunuzda, Visual Studio aşağıdaki bilgileri kayıt defterine ekler:  
  
- Bir veya daha fazla form bölgeleri ile ilişkili her ileti sınıfı için bir anahtar.  
  
- Her form bölgesi ve Outlook VSTO eklentisi adını temsil eden bir ilişkili değer için bir giriş.  
  
  Outlook form bölgeleri yüklemek için bu bilgileri kullanır.  
  
##  <a name="Debugging"></a> Form bölgesini hata ayıklama  
 VSTO Outlook form bölgesi yeterlidir, diğer yaptığınız gibi içeren eklenti ayıklayabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeleri. Başladığınızda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcı, Visual Studio otomatik olarak Outlook'u başlatır.  
  
 Form bölgesinin görüntülemek için uygun olan Outlook öğesi açmanız gerekir. Bitişik bir form bölgesi bir posta öğesinin alt kısmına eklenir, örneğin, bir posta öğesini açın.  
  
##  <a name="Deploying"></a> Form bölgesine dağıtma  
 Form bölgeleri ilişkili Outlook VSTO eklentisi ile otomatik olarak dağıtılır. Bu nedenle, bir form bölgesi dağıtmak için hiçbir özel görevleri yapmak gerekmez. VSTO eklentileri dağıtma hakkında daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Yönergeler için Outlook form bölgeleri oluşturma](../vsto/guidelines-for-creating-outlook-form-regions.md)|Form bölgeleri, en iyi duruma getirmek ve olası sorunları önlemenize yardımcı olacak bilgiler sağlar.|  
|[Nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Form bölgesini standart veya özel bir Microsoft Office Outlook biçimini kullanarak genişletmek için oluşturma işlemi gösterilmektedir **yeni Outlook Form bölgesi** Sihirbazı.|  
|[Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Form bölgesi her bir öğenin ileti sınıfıyla ilişkilendirme tarafından bir form bölgesi hangi Microsoft Office Outlook öğeleri görüntüleneceğini belirtebilirsiniz açıklanmaktadır.|  
|[İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)|Yeni bir sayfa denetçisi penceresinde bir kişi öğesinin görüntülenen özel form bölgesi tasarlama işlemi gösterilmektedir.|  
|[İzlenecek yol: Outlook'ta tasarlanan form bölgesini içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Bir Microsoft Office Outlook form bölgesi tasarlama ve kullanarak bu form bölgesini Outlook VSTO eklenti projesi alma gösterilmektedir **yeni Outlook Form bölgesi** Sihirbazı.|  
|[Form bölgesine çalışma zamanında erişme](../vsto/accessing-a-form-region-at-run-time.md)|Görüntüleme, gizleme veya denetimleri form bölgesini değiştirmek için kod yazma ve kullanarak diğer bölgelerden projenizdeki kodu çalıştırmak kullanıcıların açıklar `Globals` sınıfı.|  
|[Nasıl yapılır: Outlook'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Microsoft Office Outlook, belirli bir öğe için bir form bölgesini görüntülemesini engelleme işlemi gösterilmektedir.|  
|Form bölgesinin göründüğü Outlook öğesine erişmek nasıl gösterir.|  
|[Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)|Bir Outlook öğesine yanıt vermesine olanak sağlayan açıklar.|  
  
