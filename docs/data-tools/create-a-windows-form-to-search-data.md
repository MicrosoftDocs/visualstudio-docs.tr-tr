---
title: Veri aramak için Windows Form oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 15cfd136050d9a0e3fca89964c5a9712b7b5ae06
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159899"
---
# <a name="create-a-windows-form-to-search-data"></a>Veri aramak için Windows Form oluşturma

Sık rastlanan bir uygulama senaryosu seçilen verileri form üzerinde görüntülemektir. Örneğin, belirli bir müşterinin siparişlerini veya belirli bir siparişin ayrıntılarını görüntülemek isteyebilirsiniz. Bu senaryoda, kullanıcı bilgileri forma girer ve sonra kullanıcının girişi parametre olarak kullanılarak bir sorgu yürütülür; diğer bir deyişle veriler parametreli bir sorgu temel alınarak seçilir. Sorgu sadece kullanıcı tarafından girilen ölçütleri karşılayan verileri getirir. Bu kılavuzda, belirli bir şehirdeki müşterileri getiren bir sorgu oluşturma ve kullanıcı arabirimini kullanıcıların şehir adı girip bir düğmeye basarak sorguyu çalıştırabilecekleri şekilde değiştirme işlemleri gösterilmiştir.

Parametreli sorgular kullanılması, veritabanının kayıtları hızla filtreleyerek işini en iyi şekilde yapmasını sağlayarak uygulamanızın verimli çalışmasına yardımcı olur. Buna karşılık, tüm veritabanı tablosunu istek, ağ üzerinden aktar ve ardından istediğiniz kayıtları bulmak için uygulama mantığı kullanmak, uygulamanızın yavaş ve verimli hale gelebilir.

Bir TableAdapter (ve denetimleri için parametre değerlerini kabul etmek ve sorguyu yürütmek için) kullanarak parametreli sorgular ekleyebilirsiniz **arama ölçütü Oluşturucu** iletişim kutusu. İletişim kutusunu seçerek açın **Sorgu Ekle** komutunu **veri** menü (veya herhangi bir TableAdapter akıllı etiketinde).

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

-   Yeni bir oluşturma **Windows Forms uygulaması** proje.

-   Oluşturma ve veri kaynağı ile uygulamanızda yapılandırma **veri kaynağı yapılandırması** Sihirbazı.

-   İçindeki öğelerin bırakma türünü ayarlama **veri kaynakları** penceresi.

-   Öğeleri sürükleyerek verileri görüntüleyen denetimler oluşturma **veri kaynakları** forma penceresi.

-   Formdaki verileri görüntülemek için denetimler ekleme.

-   Tamamlama **arama ölçütü Oluşturucu** iletişim kutusu.

-   Parametreleri forma girme ve parametreli sorguyu yürütme.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1.  SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2.  Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (Bir parçası olarak SQL Server Nesne Gezgini yüklü **veri depolama ve işleme** iş yükünde **Visual Studio yükleyicisi**.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-application"></a>Windows Forms uygulaması oluşturma

İlk adım bir Windows Forms uygulaması oluşturmaktır. Projeye bir ad atamak Bu adımda isteğe bağlıdır, ancak daha sonra projeyi kaydetmek çünkü Buraya bir ad vermeniz:

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#** veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **WindowsSearchForm**ve ardından **Tamam**.

     **WindowsSearchForm** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="create-the-data-source"></a>Veri kaynağı oluşturma

Bu adımda veri kaynağı kullanarak bir veritabanı oluşturulur **veri kaynağı yapılandırması** Sihirbazı:

1.  Açmak için **veri kaynakları** penceresi, **veri** menüsünde tıklatın **veri kaynaklarını Göster**.

2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.

3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

4.  Üzerinde **veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.

5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.

6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.

7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.

8.  Seçin **müşteriler** tablosunu ve ardından **son**.

     **NorthwindDataSet** projenize eklenir ve **müşteriler** tablo görünür **veri kaynakları** penceresi.

## <a name="create-the-form"></a>Form oluşturma

Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** formunuza penceresi:

1.  Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.

2.  Sürükleme **müşteriler** düğümünden **veri kaynakları** penceresinden formunuza.

     A <xref:System.Windows.Forms.DataGridView> ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Sorguya parametreleme (arama işlevselliği) ekleme

Özgün kullanarak sorgu, WHERE yan tümcesi ekleyebilirsiniz **arama ölçütü Oluşturucu** iletişim kutusunda:

1.  Seçin <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **Sorgu Ekle** üzerinde **veri** menüsü.

2.  Tür **FillByCity** içinde **yeni sorgu adı** alanı **arama ölçütü Oluşturucu** iletişim kutusu.

3.  Ekleme `WHERE City = @City` sorguya **sorgu metni** alan.

     Sorgu aşağıdakine benzemelidir:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Erişim ve OLE DB veri kaynakları, soru işareti kullanın ('? ') parametreleri belirtmek için bu nedenle WHERE yan tümcesi şuna benzeyecektir: `WHERE City = ?`.

4.  Tıklayın **Tamam** kapatmak için **arama ölçütü Oluşturucu** iletişim kutusu.

     A **FillByCityToolStrip** formuna eklenir.

## <a name="test-the-application"></a>Uygulamayı test etme

Uygulamayı çalıştıran formunuza açar ve giriş olarak parametreyi almak hazır hale getirir:

1.  Tuşuna **F5** uygulamayı çalıştırın.

2.  Tür **Londra** içine **Şehir** metin kutusuna ve ardından **FillByCity**.

     Veri Kılavuzu ölçütlere uyan müşterilerle doldurulur. Bu örnekte, veri kılavuzu yalnızca değeri olan müşterileri görüntüler **Londra** içinde kendi **Şehir** sütun.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, parametreli form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

-   İlgili verileri görüntüleyen denetimler ekleme. Daha fazla bilgi için [veri kümelerindeki ilişkiler](relationships-in-datasets.md).

-   Veritabanı nesneleri eklemek veya çıkarmak için veri kümesini düzenleme. Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
