---
title: Arama tabloları kullanarak veri bağlama - Windows Forms denetimleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 07c9cf40952eabcafe9d1587d3e2ae4aa02de3a0
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305092"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Windows Forms'ta veri görüntüleme, mevcut denetimleri seçebilirsiniz **araç kutusu**, veya uygulamanıza işlevsellik standart denetimleri yok gerekiyorsa özel denetimler yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetim oluşturma işlemi gösterilmektedir <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Denetimleri uygulayan <xref:System.ComponentModel.LookupBindingPropertiesAttribute> verilere bağlı üç özellik içerebilir. Bu tür denetimler benzer bir <xref:System.Windows.Forms.ComboBox>.

Denetim yazma ile ilgili daha fazla bilgi için bkz: [denetimleri tasarım zamanında Windows Forms geliştirme](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Yazma denetimleri için veri bağlama senaryoları kullandığınızda, aşağıdaki veri bağlama özniteliklerden birini yapması gerekir:

|Veri bağlama öznitelik kullanımı|
| - |
|Uygulama <xref:System.ComponentModel.DefaultBindingPropertyAttribute> basit denetimlerinde gibi bir <xref:System.Windows.Forms.TextBox>, tek bir sütun (veya özellik) veri görüntüler. Daha fazla bilgi için [basit veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Uygulama <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.DataGridView>, veri listeleri'ı (veya tablo) görüntüler. Daha fazla bilgi için [karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Uygulama <xref:System.ComponentModel.LookupBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.ComboBox>, veri listeleri (veya tablo) görüntüler, ancak tek bir sütun veya özelliği sunmak de gerekir. (Bu işlem, bu izlenecek yol sayfasında açıklanmıştır.)|

Bu kılavuz iki tablodaki verilere bağlanan bir arama denetimi oluşturur. Bu örnekte `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar. Arama denetimine bağlı `CustomerID` alanını `Orders` tablo. Aramak için bu değeri kullanır `CompanyName` gelen `Customers` tablo.

Bu kılavuz boyunca öğreneceksiniz nasıl yapılır:

-   Yeni bir **Windows Forms uygulaması**.

-   Yeni bir **kullanıcı denetimi** projenize.

-   Görsel olarak kullanıcı denetiminin tasarım.

-   Uygulama `LookupBindingProperty` özniteliği.

-   Bir veri kümesi oluşturmak **veri kaynağı yapılandırması** Sihirbazı.

-   Ayarlama **CustomerID** sütunu **siparişler** tablosu **veri kaynakları** penceresinde yeni denetimi kullanmak için.

-   Verileri yeni denetimde görüntülemek için bir form oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1.  SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2.  Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (Bir parçası olarak SQL Server Nesne Gezgini yüklü **veri depolama ve işleme** iş yükünü Visual Studio Yükleyicisi'nde.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-app-project"></a>Bir Windows Forms uygulaması projesi oluşturma

İlk adım oluşturmaktır bir **Windows Forms uygulaması** proje.

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#**  veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **LookupControlWalkthrough**ve ardından **Tamam**.

     **LookupControlWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi Ekle

Bu izlenecek yol, bir arama denetimi oluşturur bir **kullanıcı denetimi**, bu nedenle ekleyin bir **kullanıcı denetimi** öğesinin **LookupControlWalkthrough** proje.

1.  Gelen **proje** menüsünde **kullanıcı denetimi Ekle**.

2.  Tür `LookupBox` içinde **adı** alan ve ardından **Ekle**.

     **LookupBox** denetim eklenir **Çözüm Gezgini**ve tasarımcıda açılır.

## <a name="design-the-lookupbox-control"></a>Tasarım LookupBox denetimi

LookupBox denetim tasarlamak için sürükleyin bir <xref:System.Windows.Forms.ComboBox> gelen **araç kutusu** kullanıcı denetiminin tasarım yüzeyine.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama öznitelik Ekle

Arama söz konusu destek veri bağlama denetimleri için uygulayabileceğiniz <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1.  Anahtar **LookupBox** kod görünümü denetimi. (Üzerinde **görünümü** menüsünde seçin **kod**.)

2.  Değiştirin `LookupBox` aşağıdaki:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Gelen **derleme** menüsünde seçin **Çözümü Derle**.

## <a name="create-a-data-source-from-your-database"></a>Veritabanından bir veri kaynağı oluşturun

Bu adımda, bir veri kaynağı kullanılarak oluşturulur **veri kaynağı yapılandırması** Sihirbazı temel `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar.

1.  Açmak için **veri kaynakları** penceresi, **veri** menüsünde tıklatın **veri kaynaklarını Göster**.

2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.

3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

4.  Üzerinde **veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.

5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.

6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.

7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.

8.  Seçin `Customers` ve `Orders` tablolar ve ardından **son**.

     **NorthwindDataSet** projenize eklenir ve `Customers` ve `Orders` tablolar görünür **veri kaynakları** penceresi.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>LookupBox denetimi kullanmak için Siparişler tablosunun CustomerID sütununda ayarlayın

İçinde **veri kaynakları** penceresindeki öğeleri formunuza sürükleyerek önce oluşturulacak denetimi ayarlayabilirsiniz.

1.  Açık **Form1** Tasarımcısı'nda.

2.  Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.

3.  Genişletin **siparişler** düğümü (bir **müşteriler** düğümünün altındaki **faks** sütunu).

4.  Aşağı açılan oka tıklayın **siparişler** düğümünü seçip **ayrıntıları** denetim listesinden.

5.  Aşağı açılan oka tıklayın **CustomerID** sütun (içinde **siparişler** düğümü) ve **Özelleştir**.

6.  Seçin **LookupBox** listesinden **ilişkili denetimler** içinde **veri kullanıcı Arabirimi özelleştirme seçenekleri** iletişim kutusu.

7.  **Tamam**'ı tıklatın.

8.  Aşağı açılan oka tıklayın **CustomerID** sütunu seçip **LookupBox**.

## <a name="add-controls-to-the-form"></a>Formu için denetimler ekleme

Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** penceresinden **Form1**.

Windows Form üzerindeki verilere bağlı denetimler oluşturmak için sürükleyin **siparişler** düğümünden **veri kaynakları** penceresinden Windows Form doğrulayın **LookupBox** denetimi verileri görüntülemek için kullanılan `CustomerID` sütun.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Müşteriler tablosundan CompanyName ' aramak için denetim bağlama

Arama bağlamaları ayarlamak için ana seçin **müşteriler** düğümünde **veri kaynakları** penceresi ve üzerine birleşik giriş kutusunda Sürükle **CustomerIDLookupBox** üzerinde**Form1**.

Görüntülenecek veri bağlamasını ayarlamak ayarlar bu `CompanyName` gelen `Customers` sürdürürken tablo `CustomerID` değerini `Orders` tablo.

## <a name="run-the-application"></a>Uygulamayı çalıştırın

-   Tuşuna **F5** uygulamayı çalıştırın.

-   Bazı kayıtlarda gezinmek ve doğrulayın `CompanyName` görünür `LookupBox` denetimi.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)