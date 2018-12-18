---
title: 'İzlenecek yol: INSERT özelleştirme, güncelleştirme ve silme davranışı varlık sınıflarının'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f665d860597bc99d7c9e496c115a82a60d596e09
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305539"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>İzlenecek yol: INSERT, update ve varlık sınıflarının silme davranışını özelleştirme

[LINQ to SQL araçları Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md) oluşturmak ve LINQ to SQL sınıfları (varlık sınıfları) bir veritabanındaki nesnelerde tabanlı düzenlemek için bir görsel tasarım yüzeyi sağlar. Kullanarak [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), SQL veritabanlarına erişim bir LINQ teknolojisi kullanabilirsiniz. Daha fazla bilgi için [LINQ (dil ile tümleşik sorgu)](/dotnet/csharp/linq/).

Varsayılan olarak, güncelleştirmeleri gerçekleştirmek için mantığı, LINQ to SQL çalışma zamanı tarafından sağlanır. Varsayılan çalışma zamanı oluşturur `Insert`, `Update`, ve `Delete` deyimleri tabanlı şemanın tablo (sütun tanımları ve birincil anahtar bilgisi). Varsayılan davranışı kullanmak istemediğinizde, güncelleştirme davranışı yapılandırmak ve gerekli ekleme, güncelleştirme ve silme veritabanındaki verilerle çalışmak için gereken gerçekleştirmek için belirli saklı yordamlar belirleyin. Varlık sınıflarınızı görünümleriyle eşleme, varsayılan davranışı gibi değil oluşturulduğunda, aynı zamanda bunu yapabilirsiniz. Ayrıca, veritabanı saklı yordamlar aracılığıyla tablo erişim gerektirdiğinde varsayılan güncelleştirme davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için [saklı yordamları kullanarak işlemleri özelleştirme](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Bu izlenecek yolda kullanılabilirliğini gerektirir **Insertcustomer**, **UpdateCustomer**, ve **DeleteCustomer** saklı yordamlar için Northwind veritabanı.

Bu izlenecek yol, ' % s'varsayılan LINQ için saklı yordamları kullanarak verileri bir veritabanına geri kaydediliyor SQL çalışma zamanı davranışı için geçersiz kılmak için izlemeniz gereken adımları sağlar.

Bu kılavuz boyunca aşağıdaki görevlerin nasıl gerçekleştirileceğini öğrenin:

-   Yeni bir Windows Forms uygulaması oluşturma ve LINQ to SQL dosyasını ekleyin.

-   İçin Northwind eşlenmiş bir varlık sınıfı oluşturma `Customers` tablo.

-   LINQ to SQL başvuran bir nesne veri kaynağı oluştur `Customer` sınıfı.

-   İçeren bir Windows formu oluşturma bir <xref:System.Windows.Forms.DataGridView> bağlanan `Customer` sınıfı.

-   Uygulama işlevselliği formu için kaydedin.

-   Oluşturma <xref:System.Data.Linq.DataContext> ekleyerek yöntemleri saklı yordamlar için **O/R Tasarımcısı**.

-   Yapılandırma `Customer` saklı yordamları gerçekleştirmek için kullanılacak sınıfı ekler, güncelleştirmeler ve siler.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1.  SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2.  Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (**SQL Server Nesne Gezgini** parçası olarak yüklenir **veri depolama ve işleme** iş yükünde **Visual Studio yükleyicisi**.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Uygulama oluşturma ve SQL sınıflarına LINQ ekleme

SQL sınıflarına LINQ ile çalışma ve bir Windows formunda veri görüntüleme, yeni bir Windows Forms uygulaması oluşturma ve LINQ to SQL sınıfları dosyasına ekleyin.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>SQL sınıflarına LINQ içeren yeni bir Windows Forms uygulaması projesi oluşturmak için

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#**  veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **UpdatingWithSProcsWalkthrough**ve ardından **Tamam**.

     **UpdatingWithSProcsWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

4.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.

5.  Tıklayın **LINQ to SQL sınıfları** şablonu ve türü **Northwind.dbml** içinde **adı** kutusu.

6.  **Ekle**'yi tıklatın.

     Boş bir LINQ to SQL sınıfları dosyası (**Northwind.dbml**) projenize eklenir ve **O/R Tasarımcısı** açılır.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Müşteri varlığı sınıf ve nesne veri kaynağı oluşturma

Veritabanı tabloları tablolardan sürükleyerek eşlenen SQL sınıflarına LINQ oluşturma **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine **O/R Tasarımcısı**. Sonuç, veritabanındaki tabloları eşleştirmek SQL varlık sınıflarına LINQ olur. Varlık sınıflarının oluşturduktan sonra ortak özelliklere sahip diğer sınıflar gibi nesne veri kaynağı olarak kullanılabilir.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Bir müşteri varlık sınıfı oluşturmak ve bir veri kaynağı ile yapılandırmak için

1.  İçinde **Sunucu Gezgini** veya **veritabanı Gezgini**, bulun **müşteri** Northwind örnek veritabanındaki SQL Server sürümünde tablo.

2.  Sürükleme **müşteriler** düğümünden **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine **O/R Tasarımcısı* yüzeyi.

     Adlı bir varlık sınıfı **müşteri** oluşturulur. Müşteriler tablosundaki sütunlara karşılık gelen özelliklerle var. Varlık sınıfı adlı **müşteri** (değil **müşteriler**) olduğundan Müşteriler tablosundan tek bir müşteri temsil eder.

    > [!NOTE]
    > Bu yeniden adlandırma adlandırılır *çoğullaştırma*. Bunu açılıp kapatılabilir [Seçenekler iletişim kutusu](../ide/reference/options-dialog-box-visual-studio.md). Daha fazla bilgi için [nasıl yapılır: açma ve kapatma (O/R Tasarımcısı) çoğullaştırma kapatma](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3.  Üzerinde **derleme** menüsünde tıklatın **derleme UpdatingwithSProcsWalkthrough** Projeyi derlemek için.

4.  Açmak için **veri kaynakları** penceresi, **veri** menüsünde tıklatın **veri kaynaklarını Göster**.

5.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.

6.  Tıklayın **nesne** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

7.  Genişletin **UpdatingwithSProcsWalkthrough** düğümünü bulun ve seçin **müşteri** sınıfı.

    > [!NOTE]
    > Varsa **müşteri** sınıf kullanılabilir değil, Sihirbazı iptal etmeniz, projeyi derleyin ve sihirbazı yeniden çalıştırın.
8.  Tıklayın **son** veri kaynağı oluşturma ve ekleme **müşteri** varlık sınıfı için **veri kaynakları** penceresi.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Müşteri verilerini bir Windows formunda görüntülemek için bir DataGridView oluşturma

Varlık sınıflarına LINQ SQL veri kaynağı öğeleri sürükleyerek bağlı denetimler oluşturmak **veri kaynakları** penceresini bir Windows Form üzerine.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Varlık sınıflarına bağlı denetimler eklemek için

1.  Açık **Form1** Tasarım görünümünde.

2.  Gelen **veri kaynakları** penceresinde Sürükle **müşteri** düğüme **Form1**.

    > [!NOTE]
    > Görüntülenecek **veri kaynakları** penceresinde tıklayın **veri kaynaklarını Göster** üzerinde **veri** menüsü.

3.  Açık **Form1** Kod Düzenleyicisi'nde.

4.  Ancak içine aşağıdaki kodu herhangi bir belirli yöntemi dışında forma genel form ekleyin `Form1` sınıfı:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5.  İçin bir olay işleyicisi oluşturun `Form_Load` olay işleyicisine aşağıdaki kodu ekleyin:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>İşlevlerini uygular

Varsayılan olarak Kaydet düğmesi etkin değildir ve kaydetme işlevinin uygulanmadı. Ayrıca, kod verilere bağlı denetimler nesnesi veri kaynakları için oluşturulan, değiştirilen verileri veritabanına kaydetmek için otomatik olarak eklenmez. Bu bölümde, kaydetmeyi etkinleştirmek açıklanmaktadır düğmesine tıklayın ve kaydetme işlevinin SQL nesnelere LINQ için uygulayın.

### <a name="to-implement-save-functionality"></a>İşlevselliği uygulamak için

1.  Açık **Form1** Tasarım görünümünde.

2.  Kaydet'i seçin düğmesini **CustomerBindingNavigator** (düğme disket simgesi ile).

3.  İçinde **özellikleri** penceresinde **etkin** özelliğini **True**.

4.  Bir olay işleyicisi oluşturun ve kod düzenleyicisine geçmek için Kaydet düğmesine çift tıklayın.

5.  Kaydetme aşağıdaki kodu ekleyin düğmesi olay işleyicisi:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Güncellemelerini (ekleme, güncelleştirme ve silme) için varsayılan davranışı geçersiz kılma

### <a name="to-override-the-default-update-behavior"></a>Güncelleştirme varsayılan davranışı geçersiz kılmak için

1.  LINQ to SQL dosyasını açın **O/R Tasarımcısı**. (Çift **Northwind.dbml** dosyası **Çözüm Gezgini**.)

2.  İçinde **Sunucu Gezgini** veya **veritabanı Gezgini**, Northwind veritabanı genişletin **saklı yordamlar** düğümünü bulun **InsertCustomers**, **UpdateCustomers**, ve **DeleteCustomers** saklı yordamlar.

3.  Üç tüm saklı yordamları üzerine sürükleyin **O/R Tasarımcısı**.

     Yöntemler bölmesini saklı yordamları eklenir <xref:System.Data.Linq.DataContext> yöntemleri. Daha fazla bilgi için [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Seçin **müşteri** varlık sınıfında **O/R Tasarımcısı**.

5.  İçinde **özellikleri** penceresinde **Ekle** özelliği.

6.  Üç nokta simgesine tıklayın (**...** ) yanındaki **kullanım çalışma zamanı** açmak için **davranışı Yapılandır** iletişim kutusu.

7.  Seçin **özelleştirme**.

8.  Seçin **InsertCustomers** yönteminde **Özelleştir** listesi.

9. Tıklayın **Uygula** seçilen sınıf ve davranış için yapılandırmayı kaydetmek için.

    > [!NOTE]
    > Tıkladığınız sürece her bir sınıf/davranışını bileşimi davranışını yapılandırmak devam **Uygula** her değişikliği yaptıktan sonra. Tıklamadan önce sınıf veya davranış değiştirirseniz **Uygula**, bir uyarı iletişim kutusu görünür değişiklikleri uygulamak için bir fırsat sağlar.

10. Seçin **güncelleştirme** içinde **davranışı** listesi.

11. Seçin **özelleştirme**.

12. Seçin **UpdateCustomers** yönteminde **Özelleştir** listesi.

     Listesini denetleyin **yöntem bağımsız değişkenleri** ve **sınıfı özellikleri** ve iki olduğuna dikkat edin **yöntem bağımsız değişkenleri** ve iki **sınıfı özellikleri**tabloda bazı sütunları için. Bu, değişiklikleri izlemek ve denetlemek için eşzamanlılık ihlalleri deyimlerini oluşturmak kolaylaştırır.

13. Harita **Original_CustomerID** metot bağımsız değişkeni **CustomerID (özgün)** sınıf özelliği.

    > [!NOTE]
    > Adları eşleştiğinde varsayılan olarak, yöntem bağımsız değişkenleri sınıfın özelliklerine eşlenir. Özellik adlarının değiştirilir ve tablo arasında varlık sınıfı artık eşleşen if eşlemek için eşdeğer sınıf özelliği'i seçmeniz gerekebilir **O/R Tasarımcısı** doğru eşleme belirlenemiyor. Yöntem bağımsız değişkenleri eşlemek için geçerli bir sınıf özellikleri yoksa, ayrıca, ayarlayabilirsiniz **sınıfı özellikleri** değerini **(hiçbiri)**.

14. Tıklayın **Uygula** seçilen sınıf ve davranış için yapılandırmayı kaydetmek için.

15. Seçin **Sil** içinde **davranışı** listesi.

16. Seçin **özelleştirme**.

17. Seçin **DeleteCustomers** yönteminde **Özelleştir** listesi.

18. Harita **Original_CustomerID** metot bağımsız değişkeni **CustomerID (özgün)** sınıf özelliği.

19. **Tamam**'ı tıklatın.

> [!NOTE]
> Bu belirli yönlendirme sorunu olmamasına karşın, LINQ to SQL ekleme sırasında veritabanı tarafından oluşturulan değerleri otomatik olarak kimlik (otomatik artış), rowguıdcol (veritabanı tarafından oluşturulan GUID) ve zaman damgası sütunları için işleme hatalarının ayıklanabileceğini belirtmekte yarar ve güncelleştirir. Veritabanı üretilmiş değerler diğer sütun türlerinde beklenmedik bir null değer neden olur. Veritabanı tarafından oluşturulan değerleri döndürülecek el ile ayarlamanız <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> için `true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> aşağıdakilerden birine: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), veya [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Uygulamayı test etme

Yeniden doğrulamak için uygulamayı çalıştırmak **UpdateCustomers** saklı yordam doğru veritabanında müşteri kaydı güncelleştirir.

1.  Tuşuna **F5**.

2.  Bir kaydı Güncelleştirme davranışı test kılavuza değiştirin.

3.  INSERT davranışı test etmek için yeni bir kayıt ekleyin.

4.  Değişiklikleri veritabanına kaydetmek için Kaydet düğmesine tıklayın.

5.  Formu kapatın.

6.  Tuşuna **F5** ve güncelleştirilen kaydı ve yeni eklenen kaydı kalıcı olduğunu doğrulayın.

7.  Yeni oluşturduğunuz kaydı silme silme davranışını test etmek için 3. adımı.

8.  Kaydet'e tıklayın düğmesine değişiklikleri gönderme ve veritabanından silinen bir kaydı kaldırın.

9. Formu kapatın.

10. Tuşuna **F5** ve Silinen kaydı veritabanından kaldırıldığını doğrulayın.

    > [!NOTE]
    > Uygulamanızı değerini bağlı olarak SQL Server Express Edition kullanıyorsa **çıkış dizinine Kopyala** özelliği veritabanı dosyasının değişiklikleri bastığınızda görüntülenmeyebilir **F5** 10 adımda.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, SQL varlık sınıflarına LINQ oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu uygulama için yapabileceğiniz bazı geliştirmeler şunları içerir:

- Eşzamanlılık denetimi sırasında güncelleştirmeleri uygulayın. Bilgi için [iyimser eşzamanlılık: genel bakış](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Verilere filtre uygulamak için LINQ sorguları ekleyin. Bilgi için [LINQ sorgularına giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext metotları](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL sorguları](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)