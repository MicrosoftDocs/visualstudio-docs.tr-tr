---
title: İzlenecek yol:, iş verileri kullanarak SharePoint'te dış liste oluşturma | Microsoft Docs
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 18848f0ebd6ffa289ea09553de82f5b9eb893181
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295845"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>İzlenecek yol:, iş verileri kullanarak SharePoint'te dış liste oluşturma

Arka uç sunucu uygulamaları, Web Hizmetleri ve veritabanları iş verilerini görüntülemek SharePoint İş Verileri Bağlantısı (BDC) hizmeti sağlar.

Bu kılavuzda örnek veritabanında kişiler hakkında bilgi döndüren BDC hizmeti için bir model oluşturulacağını gösterir. Ardından, bu modeli kullanarak da SharePoint'te dış liste oluşturur.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Proje oluşturma.
- Modele bir varlık ekleme.
- Bir Bulucu yöntemi ekleme.
- Belirli bir Bulucu yöntemi ekleme.
- Projeyi test etme.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Windows ve SharePoint sürümleri desteklenir.

- AdventureWorks örnek veritabanına erişim. AdventureWorks veritabanını yükleme hakkında daha fazla bilgi için bkz. [SQL Server örnek veritabanları](http://go.microsoft.com/fwlink/?LinkID=117483).

## <a name="create-a-project-that-contains-a-bdc-model"></a>İVB Modeli içeren bir proje oluşturun

1. Visual Studio menü çubuğunda seçin **dosya** > **yeni** > **proje**.

     **Yeni proje** iletişim kutusu açılır.

2. Ya da altında **Visual C#** veya **Visual Basic**, genişletme **SharePoint** düğümünü seçip **2010** öğesi.

3. İçinde **şablonları** bölmesinde seçin **SharePoint 2010 projesi**, projeyi adlandırın **AdventureWorksTest**ve ardından **Tamam** düğmesi .

     **SharePoint Özelleştirme Sihirbazı** görünür. Bu Sihirbazı'nda, projede hata ayıklamak ve çözümün güven düzeyini ayarlamak için kullanacağınız siteyi belirtebilirsiniz.

4. Seçin **Grup çözümü olarak Dağıt** güven düzeyi ayarlamak için seçenek düğmesini.

5. Seçin **son** varsayılan yerel SharePoint sitesini kabul etmek için düğmeyi.

6. İçinde **Çözüm Gezgini**, SharePoint proje düğümünü seçin.

7. Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.

     **Yeni Öğe Ekle** iletişim kutusu açılır.

8. İçinde **şablonları** bölmesinde seçin **iş verileri bağlantı modeli (yalnızca Grup çözümü)**, projeyi adlandırın **AdventureWorksContacts**seçip **Ekle** düğmesi.

## <a name="add-data-access-classes-to-the-project"></a>Projeye veri erişim sınıfları ekleme

1. Menü çubuğunda, **Araçları** > **veritabanına bağlan**.

     **Bağlantı Ekle** iletişim kutusu açılır.

2. SQL Server AdventureWorks örnek veritabanına bir bağlantı ekleyin.

     Daha fazla bilgi için [Bağlantı Ekle/Değiştir (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. İçinde **Çözüm Gezgini**, proje düğümünü seçin.

4. Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.

5. İçinde **yüklü şablonlar** bölmesinde seçin **veri** düğümü.

6. İçinde **şablonları** bölmesinde seçin **LINQ to SQL sınıfları**.

7. İçinde **adı** kutusunda, belirtin **AdventureWorks**ve ardından **Ekle** düğmesi.

     Bir .dbml dosyası projenize eklenir ve Object Relational Designer (O/R Tasarımcısı) açar.

8. Menü çubuğunda, **görünümü** > **Sunucu Gezgini**.

9. İçinde **Sunucu Gezgini**, AdventureWorks örnek veritabanını temsil eden düğümü genişletin ve ardından **tabloları** düğümü.

10. Ekleme **Contact (kişi)** O/R Tasarımcısı üzerine tablo.

     Bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görünür. Varlık sınıfı Contact (kişi) tablosunda sütun eşleme özelliğe sahiptir.

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Varsayılan varlığı İVB modelinden kaldırma

**İş verileri bağlantı modeli** proje Entity1 için model adlı bir varsayılan varlığı ekler. Bu varlık kaldırın. Daha sonra yeni bir varlık ekleyeceksiniz. Boş bir model ile başlayarak, izlenecek yolu tamamlamak için gerekli adımların sayısını azaltır.

1. İçinde **Çözüm Gezgini**, genişletme **BdcModel1** düğümünü ve ardından açın *BdcModel1.bdcm* dosya.

2. İş Verileri Bağlantısı modeli dosyası İVB Tasarımcısı'nda açılır.

3. Kısayol menüsünü Tasarımcısı'nda **Entity1**ve ardından **Sil**.

4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın *Entity1.vb* (Visual Basic'te) veya *Entity1.cs* (C# içinde) ve ardından **Sil** .

5. Kısayol menüsünü açın *Entity1Service.vb* (Visual Basic'te) veya *Entity1Service.cs* (C# içinde) ve ardından **Sil**.

## <a name="add-an-entity-to-the-model"></a>Modele bir varlık ekleme

Modele bir varlık ekleme. Visual Studio'dan varlıkları ekleyebilirsiniz **araç kutusu** İVB tasarımcıya.

1. Menü çubuğunda, **görünümü** > **araç kutusu**.

2. Üzerinde **BusinessDataConnectivity** sekmesinde **araç kutusu**, ekleme bir **varlık** İVB tasarımcıya.

     Yeni varlık tasarımcısında görüntülenir. Visual Studio adlı bir dosyayı ekler *EntityService.vb* (Visual Basic'te) veya *EntityService.cs* (C# ' de) projesi.

3. Menü çubuğunda, **görünümü** > **özellikleri** > **penceresi**.

4. İçinde **özellikleri** penceresinde **adı** özellik değerini **kişi**.

5. Tasarımcıda varlık için kısayol menüsünü açın, **Ekle**ve ardından **tanımlayıcı**.

     Yeni bir tanımlayıcı varlık üzerinde görünür.

6. İçinde **özellikleri** penceresinde için tanımlayıcı adını değiştirmek **ilgili kişi kimliği**.

7. İçinde **tür adı** listesinde **System.Int32**.

## <a name="add-a-specific-finder-method"></a>Belirli bir Bulucu yöntemi ekleme

Belirli bir kişi görüntülenecek BDC hizmeti etkinleştirmek için belirli bir Bulucu yöntemi eklemeniz gerekir. Bir kullanıcı bir listede bir öğe seçer ve ardından seçer belirli Bulucu metodunu BDC hizmeti çağırır **görünüm öğesi** Şeritteki düğme.

Kullanarak, kişi varlığı için belirli bir Bulucu yöntemi eklemek **BDC yöntem ayrıntıları** penceresi. Belirli bir varlığa dönmek için yöntemine kod ekleyin.

1. İVB Tasarımcısı'üzerinde **kişi** varlık.

2. Menü çubuğunda, **görünümü** > **diğer Windows** > **BDC yöntem ayrıntıları**.

     BDC yöntem Ayrıntıları penceresi açılır.

3. İçinde **bir yöntem ekleyin** listesinde **belirli Bulucu metodu Oluştur**.

     Visual Studio modele aşağıdaki öğeleri ekler. Bu öğelerin görünür **BDC yöntem ayrıntıları** penceresi.

    - Readıtem adlı bir yöntem.

    - Yöntemi giriş parametresi.

    - Yöntemin bir dönüş parametresi.

    - Her parametre için bir tür tanımlayıcı.

    - Yöntemi için yöntem örneği.

4. İçinde **BDC yöntem ayrıntıları** penceresinde için açılan listeden açmak **kişi** tür tanımlayıcısı ve ardından **Düzenle**.

     **BDC Gezgini** açılır ve modelin hiyerarşik bir görünümü sağlar.

5. İçinde **özellikleri** penceresinde yanındaki listeyi açın **TypeName** özelliği seçin **geçerli proje** sekmesine ve ardından **kişi**özelliği.

6. İçinde **BDC Gezgini**, kısayol menüsünü açın **kişi**ve ardından **tür tanımlayıcı Ekle**.

     Adlı yeni bir tür tanımlayıcı **TypeDescriptor1** görünür **BDC Gezgini**.

7. İçinde **özellikleri** penceresinde **adı** özellik değerini **ilgili kişi kimliği**.

8. Listeyi açmak **TypeName** özelliği ve ardından **Int32**.

9. Listeyi açmak **tanımlayıcı** özelliği ve ardından **ilgili kişi kimliği**.

10. Aşağıdaki alanların her biri için bir tür tanımlayıcı oluşturmak için 6. adımı yineleyin.

    |Ad|Tür adı|
    |----------|---------------|
    |FirstName|System.String|
    |Soyadı|System.String|
    |Telefon|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. İVB tasarımcısında üzerinde **kişi** açık olan varlığı **Readıtem** yöntemi.

     Kişi hizmeti kod dosyasını Kod düzenleyicisinde açılır.

12. İçinde `ContactService` sınıfı, yerine `ReadItem` yöntemini aşağıdaki kod ile. Bu kod aşağıdaki görevleri gerçekleştirir:

    - Bir kaydı ilgili kişi AdventureWorks veritabanı tablosundan alır.

    - Bir kişi varlığı İVB hizmetine döndürür.

    > [!NOTE]
    > Değiştirin `ServerName` alanını sunucunuzun adıyla.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Bir Bulucu yöntemi ekleme

Kişiler bir listede görüntülenecek BDC hizmeti etkinleştirmek için bir Bulucu yöntemi eklemeniz gerekir. Kullanarak kişi varlığa bir Bulucu yöntemi ekleme **BDC yöntem ayrıntıları** penceresi. Bir varlık koleksiyonunu BDC hizmeti için döndürülecek yöntemine kod ekleyin.

1. İVB tasarımcısında **kişi** varlık.

2. İçinde **BDC yöntem ayrıntıları** penceresinde Daralt **Readıtem** düğümü.

3. İçinde **bir yöntem ekleyin** altında listesinde **ReadList** yöntemi seçin **Bulucu metodu Oluştur**.

     Visual Studio, bir tür tanımlayıcı bir yöntem ve bir dönüş parametresi ekler.

4. İVB tasarımcısında üzerinde **kişi** açık olan varlığı **ReadList** yöntemi.

     Kişi hizmeti kod dosyasını Kod düzenleyicisinde açılır.

5. İçinde `ContactService` sınıfı, yerine `ReadList` yöntemini aşağıdaki kod ile. Bu kod aşağıdaki görevleri gerçekleştirir:

   - AdventureWorks veritabanının kişiler tablosundan verileri alır.

   - BDC hizmeti için bir kişi varlıkların listesini döndürür.

     > [!NOTE]
     > Değiştirin `ServerName` alanını sunucunuzun adıyla.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Test projesi

Projeyi çalıştırdığınızda SharePoint sitesi açılır ve Visual Studio için iş verileri bağlantı hizmeti modelinizi ekler. Kişi varlığı başvuran SharePoint'te dış liste oluşturun. AdventureWorks veritabanı kişileri veri listesinde görünür.

> [!NOTE]
> Çözümünüzü hata ayıklama yapılabilmesi SharePoint güvenlik ayarlarınızı değiştirmeniz gerekebilir. Daha fazla bilgi için [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Seçin **F5** anahtarı.

     SharePoint sitesi açılır.

2. Üzerinde **Site eylemleri** menüsünde seçin **diğer seçenekler** komutu.

3. Üzerinde **Oluştur** sayfasında **dış liste** şablonu seçip **Oluştur** düğmesi.

4. Özel liste adı **kişiler**.

5. Yanındaki Gözat düğmesini seçin **dış içerik türü** alan.

6. İçinde **dış içerik türü Seçici** iletişim kutusunda **AdventureWorksContacts.BdcModel1.Contact** öğesi ekleyin ve ardından **Oluştur** düğmesi.

     SharePoint kişilerden AdventureWorks örnek veritabanı içeren bir dış liste oluşturur.

7. Belirli Bulucu metodunu test etmek için listeden bir kişi seçin.

8. Şerit üzerinde **öğeleri** sekmesine ve ardından **görünüm öğesi** komutu.

     Seçtiğiniz kişi ayrıntılarını bir form üzerinde görünür.

## <a name="next-steps"></a>Sonraki adımlar

Tasarım modelleri için aşağıdaki konulardan SharePoint BDC hizmeti hakkında daha fazla bilgi edinebilirsiniz:

- [Nasıl yapılır: bir yaratıcı metodu ekleme](../sharepoint/how-to-add-a-creator-method.md).
- [Nasıl yapılır: bir güncelleyici metodu ekleme](../sharepoint/how-to-add-an-updater-method.md).
- [Nasıl yapılır: bir Silici metodu ekleme](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Ayrıca bkz.

[İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)  
[İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)  
[BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)  
[İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)
