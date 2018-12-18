---
title: 'İzlenecek yol: Outlook form bölgesi tasarlama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 693261bb6894681b613ad0db2f0b3c116109a782
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813693"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>İzlenecek yol: Outlook form bölgesi tasarlama
  Özel form bölgeleri, standart veya özel Microsoft Office Outlook formlarına genişletin. Bu kılavuzda, yeni bir sayfa denetçisi penceresinde bir kişi öğesinin görüntülenen özel form bölgesi tasarlama. Bu form bölgesini kişi için Windows Live yerel arama Web sitesine adres bilgilerini göndererek listelenen her adresinin haritasını görüntüler. Form bölgeleri hakkında daha fazla bilgi için bkz: [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Yeni bir Outlook VSTO eklentisi projesi oluşturma.  
  
-   VSTO eklenti projesine form bölgesi ekleniyor.  
  
-   Form bölgesi düzenini tasarlama.  
  
-   Form bölgesi davranışını özelleştirme.  
  
-   Outlook form bölgesi test etme.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] veya [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") bu konunun video sürümü için bkz: [Video nasıl yapılır: Outlook form bölgesi tasarlama](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## <a name="create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklentisi projesi oluşturun  
 İlk temel bir VSTO eklenti projesi oluşturun.  
  
### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklenti projesi oluşturmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Outlook VSTO eklenti projesinde adlı oluşturun **MapItAddIn**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **çözüm için dizin oluştur**.  
  
3.  Proje herhangi bir dizine kaydedin.  
  
     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO eklenti projesine form bölgesi ekleme  
 Bir Outlook VSTO eklentisi çözüm, bir veya daha fazla Outlook form bölgesi öğesi içerebilir. Form bölgesi öğesi kullanarak projenize ekleme **yeni Outlook Form bölgesi** Sihirbazı.  
  
### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Form bölgesini Outlook VSTO eklenti projesine eklemek için  
  
1.  İçinde **Çözüm Gezgini**seçin **MapItAddIn** proje.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Outlook Form bölgesi**, dosya adı **MapIt**ve ardından **Ekle**.  
  
     **NewOutlook Form bölgesi** Sihirbazı'nı başlatır.  
  
4.  Üzerinde **nasıl form bölgesi oluşturmak istediğinizi seçin** sayfasında **yeni bir form bölgesi tasarla**ve ardından **sonraki**.  
  
5.  Üzerinde **oluşturmak istediğiniz form bölgesi türünü seçin** sayfasında **ayrı**ve ardından **sonraki**.  
  
     A *ayrı* form bölgesi, bir Outlook forma yeni bir sayfa ekler. Form bölgesi türleri hakkında daha fazla bilgi için bkz. [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
6.  Üzerinde **açıklayıcı metni sağlayın ve görüntüleme tercihlerinizi seçin** sayfasında **harita,** içinde **adı** kutusu.  
  
     Kişi öğesi açık olduğunda bu ad Inspector penceresini Şerit üzerinde görünür.  
  
7.  Seçin **bulunan denetçiler oluşturma modu** ve **okuma modundaki denetçiler**ve ardından **sonraki**.  
  
8.  Üzerinde **bu form bölgesini görüntüleyecek ileti sınıflarını tanımlayın** sayfasında, NET **posta iletisi**seçin **kişi**ve ardından **Son**.  
  
     A *MapIt.cs* veya *MapIt.vb* dosyası projenize eklenir.  
  
## <a name="design-the-layout-of-the-form-region"></a>Form bölgesinin düzenini tasarlama  
 Form bölgeleri kullanarak görsel olarak geliştirme *form bölgesi tasarımcısı*. Yönetilen denetimleri form bölgesi tasarımcısı yüzeyine sürükleyebilirsiniz. Tasarımcı kullanın ve **özellikleri** pencere denetimi düzeninin ve görünümünün ayarlamak için.  
  
### <a name="to-design-the-layout-of-the-form-region"></a>Form bölümünün düzenini tasarlamak için  
  
1.  İçinde **Çözüm Gezgini**, genişletme **MapItAddIn** proje ve çift tıklatarak *MapIt.cs* veya *MapIt.vb* Form bölgesinin açmak için Tasarımcı.  
  
2.  Tasarımcıyı sağ tıklatın ve ardından **özellikleri**.  
  
3.  İçinde **özellikleri** penceresinde **boyutu** için **664, 469**.  
  
     Bu form bölgesini haritayı görüntülemek için büyük olmasını sağlar.  
  
4.  Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**.  
  
5.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, ekleme bir **WebBrowser** form bölgesine.  
  
     **WebBrowser** kişi için listelenen her bir adresinin bir harita görüntülenir.  
  
## <a name="customize-the-behavior-of-the-form-region"></a>Form bölgesi davranışını özelleştirme  
 Form bölgesini biçimini özelleştirmek için form bölgesi olay işleyicilerine kod çalışma zamanında davranış ekleyin. Bu form bölgesini için kod, bir Outlook öğesinin özelliklerini inceler ve harita bu form bölgesinin görüntülenip görüntülenmeyeceğini belirler. Form bölgesini görüntüleyen, kod Windows Live Yerel Search'e gider ve Outlook kişi öğesinde listelenen her adresinin haritasını yükler.  
  
### <a name="to-customize-the-behavior-of-the-form-region"></a>Form bölgesi davranışını özelleştirmek için  
  
1. İçinde **Çözüm Gezgini**, sağ tıklayın *MapIt.cs* veya *MapIt.vb*ve ardından **Kodu Görüntüle**.  
  
    *MapIt.cs* veya *MapIt.vb* Kod Düzenleyicisi'nde açılır.  
  
2. Genişletin **Form bölgesi fabrikası** kod bölge.  
  
    Form bölgesi fabrikası sınıfı adlı `MapItFactory` sunulur.  
  
3. Aşağıdaki kodu ekleyin `MapItFactory_FormRegionInitializing` olay işleyicisi. Bir kişi öğesi kullanıcı oturum açtığında bu olay işleyicisinde çağrılır. Aşağıdaki kod, kişi öğesini bir adres içerip içermediğini belirler. Kişi öğesi bir adresi içermiyorsa, bu kod ayarlar <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliği <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> sınıfının **true** ve form bölgesi görüntülenmez. Aksi takdirde, VSTO eklentisi başlatır <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> olay ve form bölgesi görüntüler.  
  
    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4. Aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> olay işleyicisi. Bu kod aşağıdaki görevleri gerçekleştirir:  
  
   - Her adresi kişi öğesini art arda ekler ve bir URL dizesi oluşturur.  
  
   - Çağrıları <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemi <xref:System.Windows.Forms.WebBrowser> nesne ve URL dizesi parametre olarak geçirir.  
  
     Yerel arama Web sitesine, harita, form bölgesinde görünür ve her adresi karalama defterinde sunar.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="test-the-outlook-form-region"></a>Outlook form bölgesi test  
 Projeyi çalıştırdığınızda, Visual Studio Outlook açar. Harita bu form bölgesini görüntülemek için bir kişi öğesi açın. Harita bu form bölgesini biçiminde bir adres içeren herhangi bir kişi öğesinin sayfası olarak görünür.  
  
### <a name="to-test-the-map-it-form-region"></a>Harita bu form bölgesini sınamak için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
     Outlook açılır.  
  
2.  Outlook'ta, üzerinde **giriş** sekmesinde **yeni öğeler**ve ardından **kişi**.  
  
3.  Kişi biçiminde yazın **Ann Beebe** ilgili kişi olarak adlandırın ve ardından aşağıdaki üç adresi belirtin.  
  
    |Adres türü|Adresi|  
    |------------------|-------------|  
    |**İş**|**4567 Main St İstanbul, NY**|  
    |**Giriş**|**1234 Kuzey St. İstanbul, NY**|  
    |**Diğer**|**3456 Main St Seattle, WA**|  
  
4.  Kaydet ve kişi öğesini kapatın.  
  
5.  Yeniden **Ann Beebe** kişi öğesi.  
  
6.  İçinde **Göster** öğenin Şerit grubuna tıklayın **harita,** harita bu form bölgesini açmak için.  
  
     Harita bu form bölgesini görünür ve yerel arama Web sitesine görüntüler. **İş**, **giriş**, ve **diğer** adresleri karalama defteri içinde görünür. Karalama defteri içinde eşleştirmek istediğiniz bir adres seçin.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu konulardan Outlook uygulamasının kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Bir Outlook öğesinin şeridinde özelleştirme hakkında bilgi edinmek için [Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Form bölgesine çalışma zamanında erişme](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [İzlenecek yol: Outlook'ta tasarlanan form bölgesini içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Nasıl yapılır: Outlook'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  