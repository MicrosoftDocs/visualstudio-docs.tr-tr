---
title: ADO.NET kullanarak basit veri uygulaması oluşturma
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 75043a1716cca0c727eb0530cd63ca715a60424b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064878"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET kullanarak basit veri uygulaması oluşturma

Bir veritabanındaki verileri işleyen bir uygulama oluşturduğunuzda, bağlantı dizeleri tanımlama, veri ekleme ve saklı yordamları çalıştırma gibi temel görevleri gerçekleştirin. Bu konuyu takip ederek, Visual C# veya Visual Basic ve ADO.NET kullanarak basit bir "veriler üzerinden formlar" Windows Forms uygulaması dahilinden bir veritabanıyla etkileşime nasıl bulabilir.  Tüm .NET veri teknolojilerini — LINQ to SQL ve Entity Framework veri kümeleri dahil olmak üzere; sonuç olarak, bu makalede gösterilen bu çok benzer adımları gerçekleştirin.

Bu makalede, hızlı bir şekilde bir veritabanından veri almak için basit bir yol gösterir. Uygulamanızın veri Önemsiz olmayan yollarla değiştirmek ve veritabanını güncellemek gerekiyorsa, Entity Framework ve veri kullanıcı arabirimi denetimleri için temel alınan verilerde yapılan değişiklikler otomatik olarak eşitlenecek bağlama kullanarak düşünmelisiniz.

> [!IMPORTANT]
> Kodu basit tutmak için üretime hazır özel durum işleme içermez.

## <a name="prerequisites"></a>Önkoşullar

Uygulama oluşturmak için gerekir:

-   Visual Studio.

-   SQL Server Express LocalDB. SQL Server Express LocalDB yoksa, buradan yükleyebilirsiniz [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express).

Bu konu, alışık olduğunuz Visual Studio IDE temel işlevsellikle ve bir Windows Forms uygulaması oluşturma, düğmeleri ve diğer denetimleri formlarda projeye form denetimleri ve olay özelliklerini ayarlamak Ekle olduğunu varsayar. Bu görevler konusunda deneyimli değilseniz, tamamlamanızı öneririz [Görselle Başlarken C# ve Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) bu kılavuza başlamadan önce konu.

## <a name="set-up-the-sample-database"></a>Örnek veritabanı kurma

Örnek veritabanı, şu adımları izleyerek oluşturun:

1. Visual Studio'da açın **Sunucu Gezgini** penceresi.

2. Sağ **veri bağlantıları** ve **yeni SQL Server veritabanı oluşturma**.

3. İçinde **sunucu adı** metin kutusuna **(localdb) \mssqllocaldb**.

4. İçinde **yeni veritabanı adı** metin kutusuna **satış**, ardından **Tamam**.

     Boş **satış** veritabanı oluşturulur ve Sunucu Gezgini içindeki veri bağlantıları düğümüne eklenir.

5. Sağ **satış** veri bağlantısını ve ardından **yeni sorgu**.

     Sorgu Düzenleyicisi penceresi açılır.

6. Kopyalama [satış Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) panonuza.

7. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

     Kısa bir süre sonra sorgu işlemi tamamlandıktan ve veritabanı nesnelerini oluşturulur. Veritabanı iki tablo içerir: Müşteri ve sipariş. Bu tablolar başlangıçta herhangi bir veri içermez, ancak oluşturacağınız uygulamayı çalıştırdığınızda veri ekleyebilirsiniz. Veritabanı, dört basit saklı yordamları da içerir.

## <a name="create-the-forms-and-add-controls"></a>Formlar oluşturun ve denetimler ekleme

1. Bir Windows Forms uygulaması projesi oluşturun ve adlandırın **SimpleDataApp**.

    Visual Studio projeyi ve adlı boş bir Windows formu dahil olmak üzere birçok dosyayı oluşturur **Form1**.

2. Üç sahip olacak şekilde iki Windows formunu projenize ekleyin ve ardından bunları aşağıdaki adlar verin:

   -   **Gezinti**

   -   **NewCustomer**

   -   **FillOrCancel**

3. Her form için aşağıdaki resimlerde metin kutularını, düğmeleri ve görüntülenen diğer denetimleri ekleyin. Her denetim için tabloların açıkladığı özellikleri ayarlayın.

   > [!NOTE]
   > Grup kutusu ve etiket denetimleri netlik kazandırır ancak kodda kullanılmaz.

   **Gezinti formu**

   ![Gezinti iletişim kutusu](../data-tools/media/simpleappnav.png)

|Gezinti formu için denetimler|Özellikler|
| - |----------------|
|Düğme|Ad = btnGoToAdd|
|Düğme|Ad = btnGoToFillOrCancel|
|Düğme|Ad = btnExit|

 **NewCustomer formu**

 ![Yeni bir müşteri ekleyin ve sipariş](../data-tools/media/simpleappnewcust.png)

|NewCustomer formu için denetimler|Özellikler|
| - |----------------|
|TextBox|Ad = txtCustomerName|
|TextBox|Ad = Txtcustomerıd<br /><br /> Salt okunur = True|
|Düğme|Ad = btnCreateAccount|
|NumericUpdown|OndalıkBasamaklar = 0<br /><br /> En fazla = 5000<br /><br /> Ad = numOrderAmount|
|DateTimePicker|Biçim = kısa<br /><br /> Ad = dtpOrderDate|
|Düğme|Ad = btnPlaceOrder|
|Düğme|Ad = btnAddAnotherAccount|
|Düğme|Ad = btnAddFinish|

 **FillOrCancel formu**

 ![dolgu veya sipariş iptal et](../data-tools/media/simpleappcancelfill.png)

|FillOrCancel formu için denetimler|Özellikler|
| - |----------------|
|TextBox|Ad = Txtorderıd|
|Düğme|Ad = Btnfindbyorderıd|
|DateTimePicker|Biçim = kısa<br /><br /> Ad = dtpFillDate|
|DataGridView|Ad = dgvCustomerOrders<br /><br /> Salt okunur = True<br /><br /> RowHeadersVisible = yanlış|
|Düğme|Ad = btnCancelOrder|
|Düğme|Ad = btnFillOrder|
|Düğme|Ad = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Bağlantı dizesi Store
 Uygulamanız veritabanına bir bağlantı açmaya çalıştığında, uygulamanızın bağlantı dizesine erişimi olmalıdır. Dizeyi her bir formda el ile girmekten kaçınmak için dizeyi depolamak *App.config* dosya projenizde ve yöntem uygulamanızdaki herhangi bir formdan çağrıldığında dizeyi döndüren bir yöntem oluşturun.

 Sağ tıklayarak bağlantı dizesini bulabilirsiniz **satış** veri bağlantısında **Sunucu Gezgini** seçip **özellikleri**. Bulun **ConnectionString** özelliği, ardından **Ctrl**+**A**, **Ctrl**+**C**  seçip dizesini panoya kopyalayın.

1.  Kullanıyorsanız C#, **Çözüm Gezgini**, genişletme **özellikleri** projesi altındaki ve sonra düğümü **Settings.settings** dosya.
    İçinde Visual Basic kullanıyorsanız, **Çözüm Gezgini**, tıklayın **tüm dosyaları göster**, genişletme **Projem** düğümünü ve ardından açın **Settings.settings** dosya.

2.  İçinde **adı** sütun girin `connString`.

3.  İçinde **türü** listesinden **(bağlantı dizesi)**.

4.  İçinde **kapsam** listesinden **uygulama**.

5.  İçinde **değer** sütunu (olmadan herhangi bir dış tırnak işaretleri) bağlantı dizenizi girin ve ardından değişikliklerinizi kaydedin.

> [!NOTE]
> Gerçek bir uygulamada, bağlantı dizesini açıklandığı gibi güvenli bir saklamalısınız [bağlantı dizeleri ve yapılandırma dosyalarını](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

##  <a name="write-the-code-for-the-forms"></a>Formlar için kodu yazın

Bu bölüm, formunuz işlevin kısa genel bakış bilgileri içerir. Ayrıca formunda bir düğmeye tıklandığında temel mantığını tanımlayan kodu sağlar.

### <a name="navigation-form"></a>Gezinti formu

Uygulamayı çalıştırdığınızda Gezinti formu açılır. **Hesap Ekle** düğmesi NewCustomer formunu açar. **Siparişleri doldurun veya iptal** düğmesi FillOrCancel formunu açar. **Çıkış** düğmesi uygulamayı kapatır.

#### <a name="make-the-navigation-form-the-startup-form"></a>Gezinti biçimini başlangıç biçimi yapın

Kullanıyorsanız C#, **Çözüm Gezgini**açın **Program.cs**ve ardından değiştirmek `Application.Run` satırını şu şekilde: `Application.Run(new Navigation());`

İçinde Visual Basic kullanıyorsanız, **Çözüm Gezgini**açın **özellikleri** penceresinde **uygulama** sekmesine tıklayın ve ardından  **SimpleDataApp.Navigation** içinde **başlangıç formu** listesi.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Boş olay işleyici yöntemi oluşturmak için Gezinti formdaki üç düğme çift tıklayın. Düğmeleri çift de otomatik olarak oluşturulan kod sağlayan bir düğme tıklama olay oluşturmak tasarımcı kod dosyasını ekler.

#### <a name="add-code-for-the-navigation-form-logic"></a>Gezinti formu mantığı için kod ekleyin

Gezinti formu için kod sayfasında tam metot gövdeleri üç düğme için tıklama olay işleyicileri aşağıdaki kodda gösterildiği gibi.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>NewCustomer formu

Ne zaman bir müşteri adı girin ve ardından **hesabı oluştur** düğmesi NewCustomer formu bir müşteri hesabı oluşturur ve SQL Server, yeni müşteri kimliği olarak bir IDENTITY değeri döndürür Ardından bir miktar ve sipariş tarihi belirterek ve seçerek yeni hesap için sipariş yerleştirebilirsiniz **sipariş** düğmesi.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Boş bir tıklama oluşturmak her dört düğme çift tıklayarak NewCustomer formdaki her düğme için olay işleyicisi. Düğmeleri çift de otomatik olarak oluşturulan kod sağlayan bir düğme tıklama olay oluşturmak tasarımcı kod dosyasını ekler.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>NewCustomer formu mantığı için kod ekleyin

NewCustomer formu mantığı tamamlamak için aşağıdaki adımları izleyin.

1. Getir `System.Data.SqlClient` kapsama ad alanı, tam olarak gerekmez, uygun üyelerinin adları.

     ```csharp
     using System.Data.SqlClient;
     ```
     ```vb
     Imports System.Data.SqlClient
     ```

2. Sınıfına aşağıdaki kodda gösterildiği gibi bazı değişkenler ve yardımcı yöntemler ekleyin.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Tam metot gövdeleri dört düğme için tıklama olay işleyicileri aşağıdaki kodda gösterildiği gibi.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>FillOrCancel formu

FillOrCancel formu siparişi kodu girin ve ardından, siparişi döndürmek için bir sorgu çalıştırır **siparişi Bul** düğmesi. Döndürülen satır salt okunur verileri kılavuz çizgilerinde görüntülenir. Seçerseniz, siparişi iptal edilmiş (X) olarak işaretleyebilirsiniz **siparişi iptal et** düğme veya işaretleyebilirsiniz sırası dolu (F) seçerseniz **siparişi** düğmesi. Seçerseniz **siparişi Bul** düğmesini tekrar, güncelleştirilen satır görüntülenir.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Boş oluşturma düğmeleri çift tıklayarak FillOrCancel formu üzerindeki dört düğme için olay işleyicileri tıklayın. Düğmeleri çift de otomatik olarak oluşturulan kod sağlayan bir düğme tıklama olay oluşturmak tasarımcı kod dosyasını ekler.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>FillOrCancel formu mantığı için kod ekleyin

FillOrCancel formu mantığı tamamlamak için aşağıdaki adımları izleyin.

1. Aşağıdaki iki ad alanı, üyelerinin adlarını tam olarak nitelemek zorunda kalmazsınız kapsamın içine alın.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```
     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Aşağıdaki kodda gösterildiği gibi bir değişken ve yardımcı yöntem sınıfına ekleyin.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Tam metot gövdeleri dört düğme için tıklama olay işleyicileri aşağıdaki kodda gösterildiği gibi.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Uygulamanızı test edin

Seçin **F5** oluşturmak ve her Click olay işleyicisini kodladıktan sonra uygulamanızı test etmek için anahtar ve yine kodlamayı bitirdikten sonra sonra.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
