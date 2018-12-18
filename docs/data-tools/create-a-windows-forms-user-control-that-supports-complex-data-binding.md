---
title: Veri bağlama ile bir Windows Forms kullanıcı denetimi oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7de5cbfe7de8919143cd30517c18f9e5ad6ba598
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305254"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Windows uygulamalarında formların üzerindeki verileri görüntülerken, mevcut denetimleri seçebilirsiniz **araç kutusu**, veya standart denetimlerinde kullanılamıyor işlevi uygulamanızı gerektiriyorsa, özel denetimler yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetim oluşturma işlemi gösterilmektedir <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Denetimleri uygulayan <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> içeren bir `DataSource` ve `DataMember` verilere bağlı özelliği. Bu tür denetimler benzer bir <xref:System.Windows.Forms.DataGridView> veya <xref:System.Windows.Forms.ListBox>.

Denetim yazma ile ilgili daha fazla bilgi için bkz: [denetimleri tasarım zamanında Windows Forms geliştirme](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Veri bağlama senaryoları denetimler yazarken aşağıdaki veri bağlama özniteliklerden birini yapması gerekir:

|Veri bağlama öznitelik kullanımı|
| - |
|Uygulama <xref:System.ComponentModel.DefaultBindingPropertyAttribute> basit denetimlerinde gibi bir <xref:System.Windows.Forms.TextBox>, tek bir sütun (veya özellik) veri görüntüler. Daha fazla bilgi için [basit veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Uygulama <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.DataGridView>, veri listeleri'ı (veya tablo) görüntüler. (Bu işlem, bu izlenecek yol sayfasında açıklanmıştır.)|
|Uygulama <xref:System.ComponentModel.LookupBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.ComboBox>, görünen veri listeleri (veya tablo) ancak tek bir sütun veya özelliği sunmak de gerekir. Daha fazla bilgi için [arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Bu izlenecek yol, bir tablodaki veri satırlarının görüntüleyen bir karmaşık bir denetim oluşturur. Bu örnekte `Customers` Northwind örnek veritabanından tablo. Müşteriler tablosunda karmaşık kullanıcı denetiminin görüntüleyeceği bir <xref:System.Windows.Forms.DataGridView> özel denetimi.

Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:

- Yeni bir **Windows Forms uygulaması**.

- Yeni bir **kullanıcı denetimi** projenize.

- Görsel olarak kullanıcı denetiminin tasarım.

- Uygulama `ComplexBindingProperty` özniteliği.

- Bir veri kümesi oluşturmak [veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png).

- Ayarlama **müşteriler** tablosundaki [veri kaynakları penceresi](add-new-data-sources.md#data-sources-window) yeni karmaşık denetimi kullanmak için.

- Buradan sürükleyerek yeni denetim ekleme **veri kaynakları** penceresinden **Form1**.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

1. Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (Bir parçası olarak SQL Server Nesne Gezgini yüklü **veri depolama ve işleme** iş yükünü Visual Studio Yükleyicisi'nde.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    1. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    1. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Bir Windows Forms uygulaması oluşturma

İlk adım oluşturmaktır bir **Windows Forms uygulaması**:

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

1. Ya da genişletin **Visual C#**  veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

1. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

1. Projeyi adlandırın **ComplexControlWalkthrough**ve ardından **Tamam**.

    **ComplexControlWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi Ekle

Bu izlenecek yol, bir karmaşık veri bağlanabilir denetiminden oluşturduğundan bir **kullanıcı denetimi**, ekleme bir **kullanıcı denetimi** projeye öğe:

1. Gelen **proje** menüsünde seçin **kullanıcı denetimi Ekle**.

1. Tür **ComplexDataGridView** içinde **adı** alan ve ardından **Ekle**.

    **ComplexDataGridView** denetim eklenir **Çözüm Gezgini**ve tasarımcıda açılır.

## <a name="design-the-complexdatagridview-control"></a>Tasarım ComplexDataGridView denetimi

Eklemek için bir <xref:System.Windows.Forms.DataGridView> kullanıcı denetimine sürükleyin bir <xref:System.Windows.Forms.DataGridView> gelen **araç kutusu** kullanıcı denetiminin tasarım yüzeyine.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama öznitelik Ekle

Karmaşık, destek veri bağlama denetimleri için uygulayabileceğiniz <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Anahtar **ComplexDataGridView** kod görünümü denetimi. (Üzerinde **görünümü** menüsünde **kod**.)

1. Değiştirin `ComplexDataGridView` aşağıdaki:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Gelen **derleme** menüsünde seçin **Çözümü Derle**.

## <a name="create-a-data-source-from-your-database"></a>Veritabanından bir veri kaynağı oluşturun

Kullanım **veri kaynağı yapılandırması** bir veri kaynağı oluşturmak için Sihirbazı'nı temel alan `Customers` Northwind örnek veritabanındaki tabloda:

1.  Açmak için **veri kaynakları** penceresi, **veri** menüsünde tıklatın **veri kaynaklarını Göster**.

2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.

3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

4.  Üzerinde **veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.

5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.

6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.

7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.

8.  Seçin `Customers` tablosunu ve ardından **son**.

    **NorthwindDataSet** projenize eklenir ve `Customers` tablo görünür **veri kaynakları** penceresi.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Müşteriler tablosu ComplexDataGridView denetimi kullanmak için ayarlama

İçinde **veri kaynakları** penceresindeki öğeleri formunuza sürükleyerek önce oluşturulacak denetimi ayarlayabilirsiniz:

1. Açık **Form1** Tasarımcısı'nda.

1. Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.

1. Aşağı açılan oka tıklayın **müşteriler** düğümünü seçip **Özelleştir**.

1. Seçin **ComplexDataGridView** listesinden **ilişkili denetimler** içinde **veri kullanıcı Arabirimi özelleştirme seçenekleri** iletişim kutusu.

1. Aşağı açılan oka tıklayın `Customers` tablosuna sağ tıklayıp seçin **ComplexDataGridView** denetim listesinden.

## <a name="add-controls-to-the-form"></a>Formu için denetimler ekleme

Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** formunuza penceresi. Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** forma penceresi. Doğrulayın **ComplexDataGridView** denetimi tablonun verilerini görüntülemek için kullanılır.

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Tuşuna **F5** uygulamayı çalıştırın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak veri bağlamasını destekleyen bir denetim oluşturma sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Tipik bir sonraki adımlardan birkaçı şunlardır:

- Diğer uygulamalarda yeniden kullanabilir, böylece bir denetim kitaplığı içinde özel kontrollerinizi yapılıyor.

- Arama senaryolarını desteklemek denetimler oluşturma. Daha fazla bilgi için [arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Deneti veri kaynakları penceresinden sürüklendiğinde oluşturulacak şekilde ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Forms Denetimleri](/dotnet/framework/winforms/controls/index)