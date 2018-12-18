---
title: Basit veri bağlamayı destekleyen bir kullanıcı denetimi oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 673e510536ab866f3be90da630d3cfa261bb98c6
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305409"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Basit veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Windows uygulamalarında formların üzerindeki verileri görüntülerken, mevcut denetimleri seçebilirsiniz **araç kutusu**, veya standart denetimlerinde kullanılamıyor işlevi uygulamanızı gerektiriyorsa, özel denetimler yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetim oluşturma işlemi gösterilmektedir <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Denetimleri uygulayan <xref:System.ComponentModel.DefaultBindingPropertyAttribute> verilere bağlı bir özellik içerebilir. Bu tür denetimler benzer bir <xref:System.Windows.Forms.TextBox> veya <xref:System.Windows.Forms.CheckBox>.

Denetim yazma ile ilgili daha fazla bilgi için bkz: [tasarım zamanında Windows Forms denetimleri geliştirme](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Veri bağlama senaryoları denetimler yazarken, aşağıdaki veri bağlama özniteliklerden birini uygulamanız gerekir:

|Veri bağlama öznitelik kullanımı|
| - |
|Uygulama <xref:System.ComponentModel.DefaultBindingPropertyAttribute> basit denetimlerinde gibi bir <xref:System.Windows.Forms.TextBox>, tek bir sütun (veya özellik) veri görüntüler. (Bu işlem, bu izlenecek yol sayfasında açıklanmıştır.)|
|Uygulama <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.DataGridView>, veri listeleri'ı (veya tablo) görüntüler. Daha fazla bilgi için [karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Uygulama <xref:System.ComponentModel.LookupBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.ComboBox>, görünen veri listeleri (veya tablo) ancak tek bir sütun veya özelliği sunmak de gerekir. Daha fazla bilgi için [arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Bu izlenecek yol, bir tablodaki tek bir sütun verileri görüntüleyen basit bir denetim oluşturur. Bu örnekte `Phone` sütununun `Customers` Northwind örnek veritabanından tablo. Standart bir telefon numarası biçimi müşterilerin telefon numaralarını kullanarak basit bir kullanıcı denetimi görüntüler bir <xref:System.Windows.Forms.MaskedTextBox> ve maskeyi ayarlamak için bir telefon numarası.

Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:

-   Yeni bir **Windows Forms uygulaması**.

-   Yeni bir **kullanıcı denetimi** projenize.

-   Görsel olarak kullanıcı denetiminin tasarım.

-   Uygulama `DefaultBindingProperty` özniteliği.

-   Bir veri kümesi oluşturmak **veri kaynağı yapılandırması** Sihirbazı.

-   Ayarlama **telefon** sütununda **veri kaynakları** yeni denetimi kullanmak için pencere.

-   Verileri yeni denetimde görüntülemek için bir form oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1.  SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2.  Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (Bir parçası olarak SQL Server Nesne Gezgini yüklü **veri depolama ve işleme** iş yükünde **Visual Studio yükleyicisi**.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Bir Windows Forms uygulaması oluşturma

İlk adım oluşturmaktır bir **Windows Forms uygulaması**:

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#**  veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **SimpleControlWalkthrough**ve ardından **Tamam**.

     **SimpleControlWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi Ekle

Bu izlenecek yol basit bir veri bağlanabilir denetiminden oluşturur bir **kullanıcı denetimi**. Ekleme bir **kullanıcı denetimi** öğesinin **SimpleControlWalkthrough** proje:

1.  Gelen **proje** menüsünde seçin **kullanıcı denetimi Ekle**.

2.  Tür **PhoneNumberBox** ad alanı seçeneğine tıklayıp **Ekle**.

     **PhoneNumberBox** denetim eklenir **Çözüm Gezgini**ve tasarımcıda açılır.

## <a name="design-the-phonenumberbox-control"></a>Tasarım PhoneNumberBox denetimi

Bu izlenecek yolda mevcut bağlı genişletir <xref:System.Windows.Forms.MaskedTextBox> oluşturmak için **PhoneNumberBox** denetimi:

1.  Sürükleme bir <xref:System.Windows.Forms.MaskedTextBox> gelen **araç kutusu** kullanıcı denetiminin tasarım yüzeyine.

2.  Akıllı etiket seçin <xref:System.Windows.Forms.MaskedTextBox> yalnızca sürüklenebilen ve seçin **maskesini ayarlama**.

3.  Seçin **telefon numarası** içinde **giriş maskesi** iletişim kutusu seçeneğine tıklayıp **Tamam** maskeyi ayarlamak için.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama öznitelik Ekle

Basit, destek veri bağlama denetimleri için uygulama <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1.  Anahtar **PhoneNumberBox** kod görünümü denetimi. (Üzerinde **görünümü** menüsünde seçin **kod**.)

2.  Değiştirin **PhoneNumberBox** aşağıdaki:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  Gelen **derleme** menüsünde seçin **Çözümü Derle**.

## <a name="create-a-data-source-from-your-database"></a>Veritabanından bir veri kaynağı oluşturun

Bu adımı kullanan **veri kaynağı yapılandırması** bir veri kaynağı oluşturmak için Sihirbazı'nı temel alan `Customers` Northwind örnek veritabanındaki tablo. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanları yükleme](../data-tools/installing-database-systems-tools-and-samples.md).

1.  Açmak için **veri kaynakları** penceresi, **veri** menüsünde tıklatın **veri kaynaklarını Göster**.

2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.

3.  Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı**ve ardından **sonraki**.

4.  Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdakilerden birini yapın:

    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.

5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.

6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.

7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.

8.  Seçin `Customers` tablosunu ve ardından **son**.

     **NorthwindDataSet** projenize eklenir ve `Customers` tablo görünür **veri kaynakları** penceresi.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Telefon sütunu PhoneNumberBox denetimi kullanmak için ayarlayın

İçinde **veri kaynakları** penceresindeki öğeleri formunuza sürükleyerek önce oluşturulacak denetimi ayarlayabilirsiniz:

1.  Açık **Form1** Tasarımcısı'nda.

2.  Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.

3.  Aşağı açılan oka tıklayın **müşteriler** düğümünü seçip **ayrıntıları** denetim listesinden.

4.  Aşağı açılan oka tıklayın **telefon** sütunu seçip **Özelleştir**.

5.  Seçin **PhoneNumberBox** listesinden **ilişkili denetimler** içinde **veri kullanıcı Arabirimi özelleştirme seçenekleri** iletişim kutusu.

6.  Aşağı açılan oka tıklayın **telefon** sütunu seçip **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Formu için denetimler ekleme

Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** forma penceresi.

Ana form üzerindeki verilere bağlı denetimler oluşturmak için sürükleyin **müşteriler** düğümünden **veri kaynakları** form penceresinden doğrulayın **PhoneNumberBox** denetimi verileri görüntülemek için kullanılan **telefon** sütun.

     Data-bound controls with descriptive labels appear on the form, along with a tool strip (<xref:System.Windows.Forms.BindingNavigator>) for navigating records. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, and <xref:System.Windows.Forms.BindingNavigator> appear in the component tray.

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Tuşuna **F5** uygulamayı çalıştırın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturma sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Tipik bir sonraki adımlardan birkaçı şunlardır:

-   Diğer uygulamalarda yeniden kullanabilir, böylece bir denetim kitaplığı içinde özel kontrollerinizi yapılıyor.

-   Daha karmaşık veri bağlama senaryoları desteklemek denetimler oluşturma. Daha fazla bilgi için [karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) ve [arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Deneti veri kaynakları penceresinden sürüklendiğinde oluşturulacak şekilde ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)