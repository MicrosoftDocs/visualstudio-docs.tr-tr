---
title: 'İzlenecek yol: çalışma zamanında Şerit denetimlerini güncelleştirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 40072b1dcd6b24f552a3c87c8241ea4498229053
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389156"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>İzlenecek yol: çalışma zamanında Şerit denetimlerini güncelleştirme

Bu yönerge, Şerit nesne modeline Şerit Office uygulamasına yüklendikten sonra Şerit denetimlerini güncelleştirme için nasıl kullanılacağını gösterir.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Örneğin, Northwind örnek veritabanıyla kurulan bir birleşik giriş kutusu ve Microsoft Office Outlook menüde doldurmak için veri çeker. Bu denetimleri otomatik olarak seçtiğiniz öğeler doldurmak alanları gibi **için** ve **konu** bir e-posta iletisi.

Bu izlenecek yol aşağıdaki görevleri gösterir:

-   Yeni bir Outlook VSTO eklentisi projesi oluşturun.

-   Özel Şerit grubuna tasarlayın.

-   Özel bir grup yerleşik bir sekmeyi ekleyin.

-   Çalışma zamanında Şerit üzerindeki denetimleri güncelleştirin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklentisi projesi oluşturun

İlk olarak bir Outlook VSTO eklentisi projesi oluşturun.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklenti projesi oluşturmak için

1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Outlook VSTO eklenti projesinde adlı oluşturun **Çalışma_Zamanında_Şerit_Güncelleme**.

2.  İçinde **yeni proje** iletişim kutusunda **çözüm için dizin oluştur**.

3.  Projenin varsayılan proje dizinine kaydedin.

     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Özel Şerit grubuna tasarlama

Bir kullanıcı yeni bir posta iletisi yazdığında, bu örnek için Şerit görünür. Şerit için özel bir grup oluşturmak için öncelikle bir Şerit öğesi projenize ekleyin ve ardından grubun Şerit Tasarımcısında tasarım. Bu özel grup adları çekerek müşterilere takip e-posta iletilerini oluşturmak ve veritabanı geçmişleri sipariş yardımcı olur.

### <a name="to-design-a-custom-group"></a>Özel bir grup tasarlamak için

1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.

2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Şerit (Görsel Tasarımcı)**.

3.  Yeni Şeridin adını değiştirmek **CustomerRibbon**ve ardından **Ekle**.

     *CustomerRibbon.cs* veya *CustomerRibbon.vb* dosyası Şerit Tasarımcısı'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4.  Şerit Tasarımcısı seçmek için tıklayın.

5.  İçinde **özellikleri** penceresinde, aşağı açılan oku tıklatın **RibbonType** özelliği ve ardından **Microsoft.Outlook.Mail.Compose**.

     Bu kullanıcı Outlook'ta yeni bir posta iletisi yazdığında Şerit sağlar.

6.  Şerit Tasarımcısı'nda tıklatın **Group1** seçin.

7.  İçinde **özellikleri** penceresinde **etiket** için **Müşteri satın alımları**.

8.  Gelen **Office Şerit denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **ComboBox** üzerine **Müşteri satın alımları** grubu.

9. Tıklayın **ComboBox1** seçin.

10. İçinde **özellikleri** penceresinde **etiket** için **müşteriler**.

11. Gelen **Office Şerit denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **menü** üzerine **Müşteri satın alımları** grubu.

12. İçinde **özellikleri** penceresinde **etiket** için **ürün satın**.

13. Ayarlama **dinamik** için **true**.

     Bu, ekleme ve denetimler menüsünden çalışma zamanında Şerit Office uygulamasına yüklendikten sonra kaldırma sağlar.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Yerleşik bir sekmeyi özel grup ekleme

Yerleşik bir sekmeyi bir Outlook Gezgini veya denetçisinin Şerit üzerinde zaten var olan bir sekmedir. Bu yordamda, özel bir grup yerleşik bir sekmeyi ekleyin ve sonra sekmede özel grubu konumunu belirtin.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Yerleşik bir sekmeyi özel bir grup eklemek için

1.  Tıklayın **TabAddins (yerleşik)** seçmek için sekmesinde.

2.  İçinde **özellikleri** penceresini genişletin **ControlId** özelliği ve ardından **OfficeId** için **TabNewMailMessage**.

     Bu ekler **Müşteri satın alımları** grubunu **iletileri** yeni bir posta iletisi içinde görüntülenen bir Şerit sekmesinde.

3.  Tıklayın **Müşteri satın alımları** grubu seçin.

4.  İçinde **özellikleri** penceresinde genişletin **konumu** özelliğinin yanındaki açılan oka tıklayın **PositionType** özelliği ve ardından  **BeforeOfficeId**.

5.  Ayarlama **OfficeId** özelliğini **GroupClipboard**.

     Bu konumlandırır **Müşteri satın alımları** önce Grup **Pano** grubunu **iletileri** sekmesi.

## <a name="create-the-data-source"></a>Veri kaynağı oluşturma

Kullanım **veri kaynakları** penceresinin bir türü belirtilmiş veri kümesi projenize ekleyin.

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1.  Üzerinde **veri** menüsünü tıklatın **yeni veri kaynağı Ekle**.

     Bu başlatır **veri kaynağı Yapılandırma Sihirbazı**.

2.  Seçin **veritabanı**ve ardından **sonraki**.

3.  Seçin **veri kümesi**ve ardından **sonraki**.

4.  Northwind örnek Microsoft SQL Server Compact 4.0 veritabanını bir veri bağlantısı seçin veya yeni bir bağlantı kullanarak eklemek **yeni bağlantı** düğmesi.

5.  Bağlantı seçili veya oluşturulduktan sonra tıklayın **sonraki**.

6.  Tıklayın **sonraki** bağlantı dizesini kaydedin.

7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları**.

8.  Aşağıdaki tabloların her biri yanındaki onay kutusunu seçin:

    1.  **Müşteriler**

    2.  **Sipariş Ayrıntıları**

    3.  **Siparişler**

    4.  **Ürünler

9. **Son**'a tıklayın.

## <a name="update-controls-in-the-custom-group-at-runtime"></a>Özel grup çalışma zamanında güncelleştirme denetimleri

Şerit nesne modeline, aşağıdaki görevleri gerçekleştirmek için kullanın:

-   Müşteri adları Ekle **müşteriler** birleşik giriş kutusu.

-   Menü ve düğme denetimleri ekleme **satın alınan ürünlerle** satış orders ve products temsil eden bir menü satılır.

-   Kime, konu ve gövde doldurmak verileri kullanarak yeni e-posta iletileri alanlarının **müşteriler** birleşik giriş kutusu ve **satın alınan ürünlerle** menüsü.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Şerit nesne modelini kullanarak özel grup denetimleri güncelleştirmek için

1. Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.

2. İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET** sekmesinde **System.Data.Linq** derleme ve ardından **Tamam**.

    Bu derleme, dil ile tümleşik sorgu (LINQ) kullanmak için sınıflar içerir. LINQ denetimleri özel grup Northwind veritabanındaki verilerle doldurmak için kullanın.

3. İçinde **Çözüm Gezgini**, tıklayın **CustomerRibbon.cs** veya **CustomerRibbon.vb** seçin.

4. Üzerinde **görünümü** menüsünde tıklatın **kod**.

    Kod Düzenleyicisi'nde Şerit kod dosyasını açar.

5. Şerit kod dosyasının en üstüne aşağıdaki deyimleri ekleyin. Bu deyimler, LINQ ad alanları ve Outlook birincil birlikte çalışma derlemesi (PIA) ad alanı için kolay erişim sağlar.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Aşağıdaki kodu ekleyin `CustomerRibbon` sınıfı. Bu kod, veri tablosu ve müşteri, siparişler, sipariş ayrıntılarını ve ürün tabloları Northwind veritabanının bilgileri depolamak için kullanacağı tablo bağdaştırıcıları bildirir.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Aşağıdaki kod bloğunu ekleyin `CustomerRibbon` sınıfı. Bu kod, Şerit denetimlerini çalışma zamanında oluşturma üç yardımcı yöntemler ekler.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Değiştirin `CustomerRibbon_Load` olay işleyicisi yöntemini aşağıdaki kodla. Bu kod, aşağıdaki görevleri gerçekleştirmek için bir LINQ Sorgu kullanır:

   - Doldurma **müşteriler** Northwind veritabanındaki kimliği ve 20 müşteriniz adını kullanarak birleşik giriş kutusu.

   - Çağrıları `PopulateSalesOrderInfo` yardımcı yöntemi. Bu yöntem güncelleştirmeleri **AlınanÜrünler** şu anda seçilen müşteriye ait satış siparişi sayılarla menüsü.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Aşağıdaki kodu ekleyin `CustomerRibbon` sınıfı. Bu kod, aşağıdaki görevleri gerçekleştirmek için LINQ sorguları kullanır:

   - Bir menüye ekler **AlınanÜrünler** her satış siparişi menüsünü ise seçili müşterilerle ilgili.

   - Her alt satış siparişine ilgili ürünler için düğmeler ekler.

   - Olay işleyicileri için her bir düğme ekler.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. İçinde **Çözüm Gezgini**, Şerit kod dosyasına çift tıklayın.

     Şerit Tasarımcısı açılır.

11. Şerit Tasarımcısı'nda çift **müşteriler** birleşik giriş kutusu.

     Kod Düzenleyicisi'nde Şerit kod dosyasını açar ve `ComboBox1_TextChanged` olay işleyicisi görünür.

12. Değiştirin `ComboBox1_TextChanged` aşağıdaki kod ile olay işleyicisi. Bu kod aşağıdaki görevleri gerçekleştirir:

    - Çağrıları `PopulateSalesOrderInfo` yardımcı yöntemi. Bu yöntem güncelleştirmeleri **satın alınan ürünlerle** ise seçili müşterilerle ilgili Siparişler menüsü.

    - Çağrıları `PopulateMailItem` yardımcı yöntem ve Seçilen müşteri adı geçerli metin geçirir. Bu yöntem Kime, konu ve gövde doldurur yeni posta iletileri alanları.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Aşağıdaki `Click` olay işleyicisine `CustomerRibbon` sınıfı. Bu kod, yeni e-posta iletisinin gövdesi alanına seçili ürünlerin adını ekler.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Aşağıdaki kodu ekleyin `CustomerRibbon` sınıfı. Bu kod aşağıdaki görevleri gerçekleştirir:

    - Şu anda seçili müşteri e-posta adresini kullanarak yeni bir e-posta iletisinin Kime satırına doldurur.

    - Yeni e-posta iletisinin konu ve gövde alanlara metin ekler.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Özel grup denetimleri test

Outlook'ta yeni bir posta formu açtığınızda özel bir grup adlı **Müşteri satın alımları** görünür **iletileri** Şerit sekmesi.

Bir müşteri takip e-posta iletisi oluşturmak için bir müşteri seçin ve ardından müşteri tarafından satın alınan ürünleri seçin. Denetimlerde **Müşteri satın alımları** Grup çalışma zamanında Northwind veritabanındaki verilerle güncelleştirilir.

### <a name="to-test-the-controls-in-the-custom-group"></a>Özel grup denetimleri sınamak için

1.  Tuşuna **F5** projeyi çalıştırın.

     Outlook'u başlatır.

2.  Outlook'ta, üzerinde **dosya** menüsünde **yeni**ve ardından **posta iletisi**.

     Aşağıdaki eylemler gerçekleşir:

    -   Yeni bir posta iletisi Inspector penceresi görünür.

    -   Üzerinde **ileti** Şerit sekmesinde **Müşteri satın alımları** grup görünür önce **Pano** grubu.

    -   **Müşteriler** grubu birleşik giriş kutusunda, Northwind veritabanındaki müşteriler adları ile güncelleştirilir.

3.  Üzerinde **ileti** Şerit sekmesinde, **Müşteri satın alımları** grubunda, müşteriden seçin **müşteriler** birleşik giriş kutusu.

     Aşağıdaki eylemler gerçekleşir:

    -   **Satın alınan ürünlerle** menüsünde, Seçilen müşteri için her bir satış siparişi göstermek için güncelleştirilir.

    -   Her bir satış siparişi alt, o sırada satın alınan ürünleri göstermek için güncelleştirilir.

    -   Seçilen müşteri e-posta adresine eklenen **için** posta iletisi konu ve e-posta iletisinin gövdesi, satır metin ile doldurulur.

4.  Tıklayın **ürünler satın alma işlemleri** menüsünden herhangi bir satış siparişinin noktası ve bir ürün satış siparişi'ye tıklayın.

     Ürün adı, e-posta iletisinin gövdesine eklenir.

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki konulardan Office UI özelleştirme hakkında daha fazla bilgi edinebilirsiniz:

-   Tüm belge düzeyi özelleştirmesine Bağlam tabanlı UI ekleyin. Daha fazla bilgi için [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

-   Bir standart veya özel Microsoft Office Outlook biçimini genişletin. Daha fazla bilgi için [izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).

-   Özel görev bölmesini Outlook ekleyin. Daha fazla bilgi için [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerite Genel Bakış](../vsto/ribbon-overview.md)
- [Dil ile Tümleşik Sorgu (LINQ)](/dotnet/csharp/linq/index)
- [Nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)
- [Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)
- [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)
- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Nasıl yapılır: Şerit Şerit Tasarımcısından Şerit XML'ine verebilir.](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Nasıl yapılır: kullanıcı arayüzü hatalarını gösterme eklentisi](../vsto/how-to-show-add-in-user-interface-errors.md)