---
title: 'İzlenecek yol: Tasarımcı kullanarak bir Web Bölümü SharePoint için oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b5cfd9afaf0c37dcf267c63641b7917efe4c249
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831822"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>İzlenecek yol: Tasarımcı kullanarak bir web bölümü SharePoint için oluşturma

Bir SharePoint sitesi için web bölümleri oluşturursanız kullanıcılarınız doğrudan içeriğini, görünümünü ve bu sitedeki sayfaların davranışını bir tarayıcı kullanarak değiştirebilirsiniz. Bu kılavuzda SharePoint kullanarak görsel olarak bir web bölümü oluşturma işlemi gösterilmektedir **görsel Web Bölümü** Visual Studio'daki proje şablonu.

Oluşturacağınız web bölümü, aylık takvim görünümü ve her takvim listesi için bir onay kutusu sitesinde görüntüler. Kullanıcılar, istedikleri Takvim listelerini onay kutularını seçerek aylık takvim görünümüne dahil için belirtebilirsiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Kullanarak bir web bölümü oluşturma **görsel Web Bölümü** proje şablonu.
- Visual Studio'da Visual Web Developer Tasarımcısını kullanarak web bölümü tasarlama.
- Web bölümünde denetimlerin olaylarını işlemek için kod ekleme.
- SharePoint web bölümünü sınama.

    > [!NOTE]
    > Bilgisayarınız aşağıdaki yönergelerde yer farklı adlar veya konumlar kullanıcı arabirimi öğelerinden bazıları için Visual Studio için gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Bkz: [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Windows ve SharePoint sürümleri desteklenir.

## <a name="create-a-web-part-project"></a>Bir web bölümü projesi oluşturma

İlk olarak kullanarak bir web bölümü projesi oluşturma **görsel Web Bölümü** proje şablonu.

1. Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanarak **yönetici olarak çalıştır** seçeneği.

2. Menü çubuğunda, **dosya** > **yeni** > **proje**.

     **Yeni proje** iletişim kutusu görüntülenir.

3. İçinde **yeni proje** iletişim kutusunda, ya da altında **Visual C#** veya **Visual Basic**, genişletme **Office/SharePoint**, seçin **SharePoint çözümleri** kategorisi.

4. Şablonlar listesinde seçin **SharePoint 2013 - görsel Web Bölümü** şablonu seçip **Tamam** düğmesi.

     **SharePoint Özelleştirme Sihirbazı** görünür. Bu sihirbazı kullanarak, proje ve çözüm güven düzeyini hata ayıklama için kullanacağınız siteyi belirtebilirsiniz.

5. İçinde **bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, seçin **Grup çözümü olarak Dağıt** seçenek düğmesini.

6. Seçin **son** varsayılan yerel SharePoint sitesini kabul etmek için düğmeyi.

## <a name="designing-the-web-part"></a>Web bölümünü tasarlama

Denetimleri ekleyerek web bölümü tasarlamak **araç kutusu** Visual Web Developer tasarımcısının yüzeyine bırakın.

1. Visual Web Developer Tasarımcısı'üzerinde **tasarım** Tasarım görünümüne geçmek için sekmesinde.

2. Menü çubuğunda, **görünümü** > **araç kutusu**.

3. İçinde **standart** düğümünün **araç kutusu**, seçin **CheckBoxList** denetlemek ve ardından aşağıdaki adımlardan birini gerçekleştirin:

    - Kısayol menüsünü açın **CheckBoxList** denetim öğesini **kopyalama**Tasarımcısı'nda ilk satır için kısayol menüsünü açın ve ardından **Yapıştır**.

    - Sürükleme **CheckBoxList** denetimi **araç kutusu**ve denetimi tasarımcıdaki birinci satıra bağlayın.

4. Önceki adımı yineleyin ancak bir düğme tasarımcının sonraki satırına taşıyın.

5. Tasarımcısı'nda **Button1** düğmesi.

6. Menü çubuğunda, **görünümü** > **Özellikler penceresi**.

     **Özellikleri** penceresi açılır.

7. İçinde **metin** düğmenin özellik girin **güncelleştirme**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Web bölümünde denetim olaylarını işleme

Kullanıcının Ana Takvim görünümüne takvimler ekleme olanak tanıyan kodu ekleyin.

1. Aşağıdaki adım kümelerinden birini uygulayın:

   - Tasarımcıda çift **güncelleştirme** düğmesi.

   - İçinde **özellikleri** penceresi **güncelleştirme** düğmesini öğesini **olayları** düğmesi. İçinde **tıklayın** özelliği girin **Button1_Click**ve ardından Enter tuşuna basın.

     Kullanıcı denetimi kod dosyası Kod düzenleyicisinde açar ve `Button1_Click` olay işleyicisi görünür. Daha sonra bu olay işleyicisi için kod ekleyeceksiniz.

2. Kullanıcı denetimi kod dosyasının en üstüne aşağıdaki deyimleri ekleyin.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Aşağıdaki kod satırını ekleyin `VisualWebPart1` sınıfı. Bu kod, bir aylık takvim görünümü denetimini bildirir.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Değiştirin `Page_Load` yöntemi `VisualWebPart1` aşağıdaki kodla sınıfı. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Kullanıcı denetimine aylık takvim görüntüsü ekler.

   - Sitede her takvim listesi için bir onay kutusu ekler.

   - Takvim görünümünde görüntülenen öğesinin her türü için bir şablon belirtir.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Değiştirin `Button1_Click` yöntemi `VisualWebPart1` aşağıdaki kodla sınıfı. Bu kod, seçilen takvimlerdeki öğeleri Ana Takvim görünümüne ekler.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Web bölümünü sınama

Projeyi çalıştırdığınızda, SharePoint sitesi açılır. Otomatik olarak web bölümünü SharePoint içindeki Web Bölümü Galerisi'ne eklenir. Bu projeyi test etmek için aşağıdaki görevleri gerçekleştirmeniz:

- Her iki ayrı takvim için bir olay ekleyin.
- Web bölümünü web bölümü sayfasına ekleyin.
- Aylık takvim görünümüne dahil edilecek listeleri belirtin.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Sitedeki Takvim listelerine olay eklemek için

1. Visual Studio'da **F5** anahtarı.

     SharePoint sitesi açılır ve [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] sayfada Hızlı Başlatma çubuğu görüntülenir.

2. Hızlı Başlat çubuğunda altında **listeler**, seçin **Takvim** bağlantı.

     **Takvim** sayfası görüntülenir.

     Hızlı Başlat çubuğunda Takvim bağlantısı görüntülenirse, seçin **Site içeriği** bağlantı. Site içerikleri sayfasında görünmüyorsa bir **Takvim** öğesi, oluşturun.

3. Takvim sayfasında bir gün seçin ve ardından **Ekle** bir olay eklemek için seçilen günün bağlantı.

4. İçinde **başlık** kutusuna **varsayılan takvim olayı**ve ardından **Kaydet** düğmesi.

5. Seçin **Site içeriği** bağlantısını ve ardından **uygulama ekleme** Döşe.

6. Üzerinde **Oluştur** sayfasında **Takvim** yazın, takvimi adlandırın ve ardından **Oluştur** düğmesi.

7. Yeni takvime bir olay ekleyin, olay adı **olayı özel takvimde**ve ardından **Kaydet** düğmesi.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Web bölümünü web bölümü sayfasına eklemek için

1. Üzerinde **Site içeriği** sayfasını açık **Site sayfaları** klasör.

2. Şerit üzerinde **dosyaları** sekmesini **yeni belge** menüsünde ve ardından **Web Bölümü sayfası** komutu.

3. Üzerinde **yeni Web Bölümü sayfası** sayfasında, sayfanın adını **SampleWebPartPage.aspx**ve ardından **Oluştur** düğmesi.

     Web bölümü sayfası görüntülenir.

4. Web bölümü sayfasının üst bölgede seçin **Ekle** sekmesine ve ardından **Web Bölümü** düğmesi.

5. Seçin **özel** klasörü seçin **VisualWebPart1** web bölümünü ve ardından **Ekle** düğmesi.

     Web bölümü sayfada görüntülenir. Aşağıdaki denetimler web bölümünde görüntülenir:

    - Aylık takvim görünümü.

    - Bir **güncelleştirme** düğmesi.

    - A **Takvim** onay kutusu.

    - A **özel Takvim** onay kutusu.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Aylık takvim görünümüne dahil edilecek listeleri belirtin

Web bölümünde aylık takvim görünümüne eklemek ve ardından istediğiniz takvimleri belirtin **güncelleştirme** düğmesi.

Belirtilen tüm takvimlerdeki olaylar, aylık takvim görünümü'nde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

[SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Nasıl yapılır: bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[İzlenecek yol: SharePoint için bir web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
