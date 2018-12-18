---
title: "İzlenecek yol: Outlook'ta tasarlanan form bölgesini içeri aktarma"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 413d2fed56da809b2fdb8c1fad867818e0cce010
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903523"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>İzlenecek yol: Outlook'ta tasarlanan form bölgesini içeri aktarma
  Bu izlenecek yol, bir Microsoft Office Outlook form bölgesi tasarlama ve kullanarak bu form bölgesini Outlook VSTO eklenti projesi almak gösterilmiştir **Yeni Form bölgesi** Sihirbazı. Outlook form bölgesi tasarlama, yerel Outlook denetimleri form bölgesini Outlook verilere bağlama eklemek mümkün kılar. Form bölgesini içeri aktardıktan sonra her denetim olayları işleyebilir.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Outlook form bölgesi tasarımcısı kullanarak bir form bölgesi tasarlama.  
  
- Bir Outlook VSTO eklenti projesine form bölgesi alma.  
  
- Form bölgesinin denetim olaylarını işleme.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] veya [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [ı: oluşturma Outlook form bölgeleri Visual Studio 2008'i kullanarak bunu nasıl?](http://go.microsoft.com/fwlink/?LinkID=130305).  
## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Outlook form bölgesi tasarımcısı kullanarak bir form bölgesi tasarla  
 Bu adımda bir form bölgesinin Outlook tasarım. Ardından kayıt olacak bir kolayca bulunabilen konumuna form bölgesi içine içe aktarabilmesi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Bu örnek form bölgesini tamamen normal görev formu değiştirir. Bu, ana görev önce tamamlanması gereken tüm görevlerin ilerlemesini izlemek için bir yol (önkoşul görevleri) gerçekleştirilen sağlar. Form bölgesinin ön koşul görevlerini listesini görüntüler ve listedeki her görev için tamamlanma durumu gösterir. Kullanıcılar, görev listesine ekleyin ve bunları kaldırın. Bunlar, ayrıca her bir görevin tamamlanma durumunu yenileyebilirsiniz.  
  
### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Outlook form bölgesi tasarımcısı kullanarak bir form bölgesi tasarlama  
  
1.  Microsoft Office Outlook'u başlatın.  
  
2.  Outlook'ta, üzerinde **Geliştirici** sekmesinde **formun**. Daha fazla bilgi için [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  İçinde **tasarım Form** kutusunun **görev**ve ardından **açık**.  
  
4.  Outlook'ta, üzerinde **Geliştirici** sekmesinde **tasarım** grubunda **Yeni Form bölgesi**.  
  
     Yeni form bölgesi açılır. Varsa **alan Seçici** görüntülenmiyorsa, tıklayın **alan Seçici** içinde **Araçları** grubu.  
  
5.  Sürükleme **konu** alan ve **% Complete** alanını **alan Seçici** form bölgesine.  
  
6.  İçinde **Araçları** grubunda **denetimi araç kutusu** açmak için **araç kutusu**.  
  
7.  Bir etiketten sürükleyin **araç kutusu** form bölgesine. Etiketi altındaki konumlandırın **konu** ve **% Complete** alanları.  
  
8.  Etikete sağ tıklayın ve ardından **Gelişmiş Özellikler**.  
  
9. İçinde **özellikleri** penceresinde **açıklamalı alt yazı** özelliğini **üzerinde aşağıdaki görevleri bu görevin bağlı**ayarlayın **genişliği** özelliği **200**ve ardından **Uygula**.  
  
10. Bir ListBox denetiminden sürükleyin **araç kutusu** form bölgesine. Liste kutusunu altına getirin **üzerinde aşağıdaki görevleri bu görevin bağlı** etiketi.  
  
11. Yeni eklediğiniz liste kutusunu seçin.  
  
12. İçinde **özellikleri** penceresinde **genişliği** için **300**ve ardından **Uygula**.  
  
13. Bir etiketten sürükleyin **araç kutusu** form bölgesine. Etiket liste kutusunu altına yerleştirin.  
  
14. Yeni eklediğiniz etiketi seçin.  
  
15. İçinde **özellikleri** penceresinde **açıklamalı alt yazı** özelliğini **bağımlı görevler listesine eklemek için bir görev seçin**ayarlayın **genişliği** özelliğini **200**ve ardından **Uygula**.  
  
16. Bir ComboBox denetimi **araç kutusu** form bölgesine. Birleşik giriş kutusunun altına getirin **bağımlı görevler listesine eklemek için bir görev seçin** etiketi.  
  
17. Yeni eklediğiniz birleşik giriş kutusunu seçin.  
  
18. İçinde **özellikleri** penceresinde **genişliği** özelliğini **300**ve ardından **Uygula**.  
  
19. CommandButton denetimi **araç kutusu** form bölgesine. Birleşik giriş kutusunun yanındaki düğmeyi konumu.  
  
20. Yeni eklediğiniz düğmeyi seçin.  
  
21. İçinde **özellikleri** penceresinde **adı** için **AddDependentTask**ayarlayın **açıklamalı alt yazı** için **bağımlı Görev Ekle**ayarlayın **genişliği** için **100**ve ardından **Uygula**.  
  
22. İçinde **alan Seçici**, tıklayın **yeni**.  
  
23. İçinde **yeni alan** iletişim kutusuna **Hiddenfield'i** içinde **adı** alan ve ardından **Tamam**.  
  
24. Sürükleme **Hiddenfield'i** alanını **alan Seçici** form bölgesine.  
  
25. İçinde **özellikleri** penceresinde **görünür** için **0 - yanlış**ve ardından **Uygula**.  
  
26. Outlook'ta, üzerinde **Geliştirici** sekmesinde **tasarım** grubunda **Kaydet** düğmesine ve ardından **Form Bölgesini Farklı Kaydet**.  
  
     Form bölgesinin adı **TaskFormRegion** ve bilgisayarınızda yerel bir dizine kaydedin.  
  
     Outlook form bölgesi bir Outlook Form Depolama kaydeder (*.ofs*) dosyası. Form bölgesinin adı ile kaydedilmiş *TaskFormRegion.ofs*.  
  
27. Outlook çıkın.  
  
## <a name="create-a-new-outlook-add-in-project"></a>Yeni bir Outlook eklentisi projesi oluşturun  
 Bu adımda, bir Outlook VSTO eklentisi projesi oluşturacaksınız. Bu kılavuzda daha sonra projeye form bölgesini içeri aktaracak.  
  
### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklenti projesi oluşturmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Outlook VSTO eklenti projesinde adlı oluşturun **TaskAddIn**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **çözüm için dizin oluştur**.  
  
3.  Projenin varsayılan proje dizinine kaydedin.  
  
     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="import-the-form-region"></a>Form bölgesini içeri aktarma  
 Kullanarak Outlook VSTO eklentisi projesine Outlook'ta tasarlanan form bölgesini içeri aktarabilirsiniz **yeni Outlook Form bölgesi** Sihirbazı.  
  
### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Form bölgesinin Outlook VSTO eklentisi projesine içeri aktarmak için  
  
1.  İçinde **Çözüm Gezgini**, sağ **TaskAddIn** proje, işaret **Ekle**ve ardından **yeni öğe**.  
  
2.  İçinde **şablonları** bölmesinde **Outlook Form bölgesi**, dosya adı **TaskFormRegion**ve ardından **Ekle**.  
  
     **NewOutlook Form bölgesi** Sihirbazı'nı başlatır.  
  
3.  Üzerinde **nasıl form bölgesi oluşturmak istediğinizi seçin** sayfasında **Outlook Form Depolama (.ofs) dosyasını içeri aktarma**ve ardından **Gözat**.  
  
4.  İçinde **mevcut Outlook Form bölgesi dosyasının konumu** iletişim kutusunda, konumu için Gözat *TaskFormRegion.ofs*seçin **TaskFormRegion.ofs**, tıklayın**Açık**ve ardından **sonraki**.  
  
5.  Üzerinde **oluşturmak istediğiniz form bölgesi türünü seçin** sayfasında **Tümünü Değiştir**ve ardından **sonraki**.  
  
     A *Tümünü Değiştir* form bölgesini Outlook formun tamamını değiştirir. Form bölgesi türleri hakkında daha fazla bilgi için bkz. [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
6.  Üzerinde **açıklayıcı metni sağlayın ve görüntüleme tercihlerinizi seçin** sayfasında **sonraki**.  
  
7.  Üzerinde **bu form bölgesini görüntüleyecek ileti sınıflarını tanımlayın** sayfasında **hangi özel ileti sınıfları bu form bölgesini görüntüleyecek** alanına **IPM. Task.TaskFormRegion**ve ardından **son**.  
  
     A *TaskFormRegion.cs* veya *TaskFormRegion.vb* dosyası projenize eklenir.  
  
## <a name="handle-the-events-of-controls-on-the-form-region"></a>Form bölgesinin denetim olaylarını işleme  
 Form bölgesinin projedeki olduğuna göre işleyen kodu ekleyebilirsiniz `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` olay düğmesinin form bölgesinin Outlook'ta eklenir.  
  
 Ayrıca, kodu ekleyin <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> form bölgesinin göründüğü zaman, form bölgesinin denetimleri güncelleyen olay.  
  
### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Form bölgesinin denetimlerin olaylarını işlemek için  
  
1. İçinde **Çözüm Gezgini**, sağ *TaskFormRegion.cs* veya *TaskFormRegion.vb*ve ardından **Kodu Görüntüle**.  
  
    *TaskFormRegion.cs* veya *TaskFormRegion.vb* Kod Düzenleyicisi'nde açılır.  
  
2. Aşağıdaki kodu ekleyin `TaskFormRegion` sınıfı. Bu kod, form bölgesini Outlook görevleri klasöründe her görevden konu satırı birleşik giriş kutusunu doldurur.  
  
    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]  
  
3. Aşağıdaki kodu ekleyin `TaskFormRegion` sınıfı. Bu kod aşağıdaki görevleri gerçekleştirir:  
  
   - Bulur `Microsoft.Office.Interop.Outlook.TaskItem` çağırarak görevleri klasöründe `FindTaskBySubjectName` yardımcı yöntem ve konu istediğiniz görevin geçirme. Ekleyeceksiniz `FindTaskBySubjectName` sonraki adımda yardımcı yöntemi.  
  
   - Ekler `Microsoft.Office.Interop.Outlook.TaskItem.Subject` ve `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` bağımlı görev liste kutusu değerleri.  
  
   - Form bölgesinin gizli alanı görevin konu ekler. Gizli alan, bu değerleri Outlook öğesinin bir parçası depolar.  
  
     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]  
  
4. Aşağıdaki kodu ekleyin `TaskFormRegion` sınıfı. Bu kod bir yardımcı yöntem sağlar `FindTaskBySubjectName` önceki adımda açıklanan.  
  
    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]  
  
5. Aşağıdaki kodu ekleyin `TaskFormRegion` sınıfı. Bu kod aşağıdaki görevleri gerçekleştirir:  
  
   - Form bölgesinin geçerli tamamlanma durumunu içeren liste kutusunda bağımlı her görevin yeniler.  
  
   - Bağımlı her görevin konusunu almak için gizli metin alanını ayrıştırır. Ardından her tanımlanmadıkça `Microsoft.Office.Interop.Outlook.TaskItem` içinde *görevleri* çağırarak klasör `FindTaskBySubjectName` yardımcı yöntemini ve her görev konusunu geçirerek.  
  
   - Ekler `Microsoft.Office.Interop.Outlook.TaskItem.Subject` ve `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` bağımlı görev liste kutusu değerleri.  
  
     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]  
  
6. Değiştirin `TaskFormRegion_FormRegionShowing` aşağıdaki kod ile olay işleyicisi. Bu kod aşağıdaki görevleri gerçekleştirir:  
  
   - Form bölgesinin göründüğünde form bölgesinin görev konularıyla birleşik giriş kutusunu doldurur.  
  
   - Çağrıları `RefreshTaskListBox` form bölgesinin göründüğü zaman yardımcı yöntemi. Bu öğe daha önce açıldığında, liste kutusuna eklenen herhangi bir bağımlı görevleri görüntüler.  
  
     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]  
  
## <a name="test-the-outlook-form-region"></a>Outlook form bölgesi test  
 Form bölgesinin test etmek için görevler form bölgesinin üzerinde ön koşul görevlerini listesine ekleyin. Önkoşul görev tamamlanma durumunu güncelleştirin ve ardından önkoşul görev listesinde görev güncelleştirilmiş tamamlanma durumunu görüntüleyin.  
  
### <a name="to-test-the-form-region"></a>Form bölgesinin test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
     Outlook'u başlatır.  
  
2.  Outlook'ta, üzerinde **giriş** sekmesinde **yeni öğeler**ve ardından **görev**.  
  
3.  Görev formunda yazın **bağımlı görev** içinde **konu** alan.  
  
4.  Üzerinde **görev** Şerit sekmesinde, **eylemleri** grubunda **Kaydet ve Kapat**.  
  
5.  Outlook'ta, üzerinde **giriş** sekmesinde **yeni öğeler**, tıklayın **diğer öğeler**ve ardından **Form seçin**.  
  
6.  İçinde **Form seçin** iletişim kutusu, tıklayın **TaskFormRegion**ve ardından **açık**.  
  
     **TaskFormRegion** form bölgesi görünür. Bu form, tüm görev formu değiştirir. **Bağımlı görevler listesine eklemek için bir görev seçin** birleşik giriş kutusu Görevler klasöründeki diğer görevlerle doldurulur.  
  
7.  Görev formunda içinde **konu** alanına **birincil görev**.  
  
8.  İçinde **bağımlı görevler listesine eklemek için bir görev seçin** seçin birleşik giriş kutusunun **bağımlı görev**ve ardından **bağımlı Görev Ekle**.  
  
     **%0 tamamlandı--bağımlı görev** görünür **üzerinde aşağıdaki görevleri bu görevin bağlı** liste kutusu. Bu başarıyla işlenen gösterir `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` düğmesinin olayı.  
  
9. Kaydet ve Kapat **birincil görev** öğesi.  
  
10. Outlook'ta bağımlı görev öğesinin yeniden açın.  
  
11. Bağımlı Görev formunda değiştirme **% Complete** alanı **% 50**.  
  
12. Üzerinde **görev** bağımlı görev Şerit sekmesinde, **eylemleri** grubunda **Kaydet ve Kapat**.  
  
13. Yeniden **birincil görev** Outlook'ta öğesi.  
  
     **% 50 oranında tamamlandı--bağımlı görev** artık görünür **üzerinde aşağıdaki görevleri bu görevin bağlı** liste kutusu.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu konulardan Outlook uygulamasının kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Yönetilen denetimleri bir görsel tasarımcıya sürükleyerek form bölgesinin görünümünü tasarlayın hakkında daha fazla bilgi için bkz: [izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Bir Outlook öğesinin şeridinde özelleştirme hakkında bilgi edinmek için [Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).  
  
-   Outlook için bir özel görev bölmesi ekleme hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Form bölgesine çalışma zamanında erişme](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Nasıl yapılır: Outlook'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  