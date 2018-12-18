---
title: Bir eşzamanlılık özel durumunu işleme
ms.date: 09/11/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fef30f836ab27cd7a67d85a04254be0018d5b33e
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388744"
---
# <a name="handle-a-concurrency-exception"></a>Bir eşzamanlılık özel durumunu işleme

Eşzamanlılık özel durumları (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) iki kullanıcı, bir veritabanında aynı verileri aynı anda değiştirme girişiminde oluşturulur. Bu kılavuzda, catch gösterilmektedir bir Windows uygulaması oluşturma bir <xref:System.Data.DBConcurrencyException>hataya neden satırı bulun ve nasıl işleyeceğini bir stratejisi öğrenin.

Bu izlenecek yol aşağıdaki süreci alır:

1. Yeni bir **Windows Forms uygulaması** proje.

2. Northwind Customers tabloyu temel alan yeni bir veri kümesi oluşturursunuz.

3. Bir formla oluşturma bir <xref:System.Windows.Forms.DataGridView> verileri görüntülemek için.

4. Bir veri kümesi, Northwind veritabanındaki Müşteriler tablosunu verilerle doldurun.

5. Kullanım **tablo verilerini Göster** da **Sunucu Gezgini** müşteriler tablo verilerine erişmek ve bir kaydı değiştirmek için.

6. Aynı kaydı başka bir değerle değiştirmek, veri kümesini güncelleştirin ve değişiklikleri gerçekleştirilen bir eşzamanlılık hatası sonuçları veritabanına yazma girişimi.

7. Hata catch, devam etmek ve veritabanını güncelleştirmek belirlemek kullanıcının kayıt farklı sürümlerini görüntüleme veya güncelleştirmeyi iptal eder.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2. Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (Bir parçası olarak SQL Server Nesne Gezgini yüklü **veri depolama ve işleme** iş yükünü Visual Studio Yükleyicisi'nde.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

Yeni bir Windows Forms uygulaması oluşturarak başlayın:

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#** veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **ConcurrencyWalkthrough**ve ardından **Tamam**.

     **ConcurrencyWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**, ve yeni bir form Tasarımcısı'nda açılır.

## <a name="create-the-northwind-dataset"></a>Northwind veri kümesi oluşturma

Ardından, adlı bir veri kümesi oluşturma **NorthwindDataSet**:

1. Üzerinde **veri** menüsünde seçin **ekleme yeni veri kaynağı**.

   Veri Kaynağı Yapılandırma Sihirbazı açılır.

2. Üzerinde **bir veri kaynağı türü seçin** ekranındayken **veritabanı**.

   ![Visual Studio'da veri kaynağı Yapılandırma Sihirbazı](media/data-source-configuration-wizard.png)

3. Bir bağlantı, Northwind örnek veritabanına kullanılabilir bağlantılar listesinden seçin. Bağlantı bağlantılar listesinde kullanılabilir durumda değilse, seçin **yeni bağlantı**.

    > [!NOTE]
    > Bir yerel veritabanı dosyasına bağlıyorsanız seçin **Hayır** sorulduğunda isterseniz ister dosyayı projenize ekleyin.

4. Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** ekranındayken **sonraki**.

5. Genişletin **tabloları** düğümünü seçip alt **müşteriler** tablo. Veri kümesi için varsayılan adı olması gereken **NorthwindDataSet**.

6. Seçin **son** veri kümesini projeye eklenecek.

## <a name="create-a-data-bound-datagridview-control"></a>DataGridView denetimine veri bağlama oluşturun

Bu bölümde, oluşturduğunuz bir <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> sürükleyerek **müşteriler** öğesini **veri kaynakları** Windows formunuza penceresi.

1. Açmak için **veri kaynakları** penceresi, **veri** menüsünde seçin **veri kaynaklarını Göster**.

2. İçinde **veri kaynakları** penceresini genişletin **NorthwindDataSet** düğümüne tıklayın ve ardından **müşteriler** tablo.

3. Tablo düğümü aşağı oku seçip ardından **DataGridView** aşağı açılan listesinde.

4. Tablo boş bir alana formunuzu sürükleyin.

     A <xref:System.Windows.Forms.DataGridView> adlı Denetim **CustomersDataGridView**ve <xref:System.Windows.Forms.BindingNavigator> adlı **CustomersBindingNavigator**, bağlı forma eklenen <xref:System.Windows.Forms.BindingSource>. Bu sırayla NorthwindDataSet'teki Müşteriler tablosunu bağlı olan.

## <a name="test-the-form"></a>Form test

Artık bu noktaya kadar beklendiği gibi davrandığından emin olmak için form test edebilirsiniz:

1. Seçin **F5** uygulamayı çalıştırın.

     Form görünür bir <xref:System.Windows.Forms.DataGridView> bulunan müşteriler tablosundaki verilerle doldurulmuş denetimi.

2. Üzerinde **hata ayıklama** menüsünde **hata ayıklamayı Durdur**.

## <a name="handle-concurrency-errors"></a>Eşzamanlılık hatalarını işleme

Hataların nasıl işleneceğini belirleyen uygulamanızı belirli iş kurallarına bağlıdır. Bu kılavuz için eşzamanlılık hatası işlemek nasıl bir örnek olarak aşağıdaki stratejiyi kullanın.

Uygulama, kullanıcı kaydı üç sürümleriyle sunar:

- Veritabanı geçerli kayıt

- Veri kümesine yüklenmesidir özgün kaydı

- Önerilen değişikliklerin veri kümesi

Kullanıcı daha sonra önerilen sürümü, veritabanı üzerine veya güncelleştirmeyi iptal eder ve yeni değerlerle veritabanından veri kümelerini yenileme mümkün değil.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Eşzamanlılık hata işlemesini etkinleştirmek için

1. Özel hata işleyicisi oluşturun.

2. Kullanıcı için seçenekleri görüntüler.

3. Kullanıcının yanıt işler.

4. Güncelleştirmenin yeniden ya da veri kümesindeki verileri sıfırlayın.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Eşzamanlılık özel durumunu işlemek için kod ekleyin

Bir güncelleştirme gerçekleştirmeyi denedi ve bir özel durum, genellikle özel durumu tarafından sağlanan bilgilerle bir şey istersiniz. Bu bölümde, veritabanını güncellemek için çalışan kod ekleyin. Tüm de ele <xref:System.Data.DBConcurrencyException> , yükseltilebilir, yanı sıra diğer tüm özel durumlar.

> [!NOTE]
> `CreateMessage` Ve `ProcessDialogResults` yöntemleri, izlenecek yolda eklenir.

1. Aşağıdaki kodu ekleyin `Form1_Load` yöntemi:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Değiştirin `CustomersBindingNavigatorSaveItem_Click` çağrılacak yöntem `UpdateDatabase` yöntemi aşağıdaki gibi görünür:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Kullanıcıya görünen seçenekleri

Yeni kod yazdığınız çağrıları `CreateMessage` kullanıcıya hata bilgilerini görüntülemek için yordamı. Bu kılavuz için kaydın farklı sürümlerine kullanıcıya görüntülenecek bir ileti kutusu kullanın. Bu, kullanıcının kaydı değişikliklerle değiştirmek ya da düzenlemeyi iptal etmek isteyip istemediğinizi seçin sağlar. Kullanıcı ileti kutusunda (bir düğmeye tıkladığında) seçeneği seçtikten sonra yanıt geçirilen `ProcessDialogResult` yöntemi.

Aşağıdaki kodu ekleyerek iletiyi oluşturmak **Kod Düzenleyicisi**. Bu aşağıdaki kodu girin `UpdateDatabase` yöntemi:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Kullanıcının yanıt işleme

İleti kutusunda kullanıcının yanıta işlemek için kod da gerekir. Önerilen değişiklik, veritabanındaki geçerli kaydın üzerine veya yerel değişiklikleri iptal ve yenilemek veri tablosu veritabanında şu anda var olan kayıtla seçeneklerdir. Kullanıcı seçerse **Evet**, <xref:System.Data.DataTable.Merge%2A> yöntemi çağrıldığında *preserveChanges* değişkenini **true**. Bu, kaydın orijinal sürümünü artık veritabanında kayıt eşleştiği için başarılı olması güncelleştirme girişimi neden olur.

Önceki bölümde eklenen kodun altına aşağıdaki kodu ekleyin:

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Form test

Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz. Eşzamanlılık ihlalinin benzetimini yapmak için NorthwindDataSet doldurduktan sonra veritabanındaki verileri değiştirme.

1. Seçin **F5** uygulamayı çalıştırın.

2. Form göründükten sonra çalışan bırakın ve geçiş yapmak için Visual Studio IDE.

3. Üzerinde **görünümü** menüsünde seçin **Sunucu Gezgini**.

4. İçinde **Sunucu Gezgini**, uygulamanızı kullanma ve ardından bağlantıyı genişletin **tabloları** düğümü.

5. Sağ **müşteriler** tablosuna sağ tıklayıp ardından **tablo verilerini Göster**.

6. İlk kayda (**ALFKI**), değiştirme **ContactName** için **Maria Anders2**.

    > [!NOTE]
    > Değişikliği kaydetmek için farklı bir satıra gidin.

7. ConcurrencyWalkthrough'ın çalışan forma geçiş yapın.

8. Formdaki ilk kayda (**ALFKI**), değiştirme **ContactName** için **Maria Anders1**.

9. Seçin **Kaydet** düğmesi.

     Eşzamanlılık hatası tetiklenir ve ileti kutusu görünür.

   Seçme **Hayır** güncelleştirmeyi iptal eder ve veri kümesini veritabanında şu anda değerlerini güncelleştirir. Seçme **Evet** önerilen değeri veritabanına yazar.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)