---
title: WPF ve Entity Framework 6 ile basit veri uygulaması oluşturma
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5993256b41a07c4861ef2def58dc14d7fd849313
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305617"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF ve Entity Framework 6 ile basit veri uygulaması oluşturma

Bu izlenecek yol, Visual Studio'da bir temel "veriler üzerinden formlar" uygulama oluşturma işlemi gösterilmektedir. Uygulama, SQL Server LocalDB, Northwind veritabanı, Entity Framework 6 ve Windows Presentation Foundation kullanır. Temel veri bağlama ile ana öğe-ayrıntı görünümü nasıl gösterir ve ayrıca özel bir bağlama Gezgin düğmeleri için sahip **sonrakine Taşı**, **öncekine taşı**, **taşımak içinbaşlayan**, **Sonuna taşı**, **güncelleştirme** ve **Sil**.

Bu makalede, Visual Studio veri araçları kullanmaya odaklanmıştır ve temel teknolojileri herhangi bir şekilde açıklamak çalışmaz. Bu, XAML, Entity Framework ve SQL temel olarak bilindiğini sahibi olduğunuzu varsayar. Bu örnekte, WPF uygulamaları için standart olan Model-View-ViewModel (MVVM) mimarisi de gösterilmemiştir. Ancak, bazı değişiklikler ile kendi MVVM uygulamasına bu kodu kopyalayın.

## <a name="install-and-connect-to-northwind"></a>Yükleme ve Northwind olarak bağlanma

Bu örnek, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır. ADO.NET veri sağlayıcısının bu ürün için Entity Framework destekliyorsa, diğer SQL veritabanı ürünlerle ekleyebiliyorsa çalışmalıdır.

1.  SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **.NET Masaüstü geliştirmesinden** iş yükü veya tek bir bileşen olarak.

2.  Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (**SQL Server Nesne Gezgini** parçası olarak yüklenen **veri depolama ve işleme** iş yükünde **Visual Studio yükleyicisi**.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

3.  [Yeni bağlantı ekleme](../data-tools/add-new-connections.md) Northwind için.

## <a name="configure-the-project"></a>Proje yapılandırma

1.  Visual Studio'da **dosya** > **yeni** > **proje** ve ardından yeni bir C# WPF uygulaması.

2.  Ardından, Entity Framework 6 için NuGet paketini ekleyin. İçinde **Çözüm Gezgini**, proje düğümünü seçin. Ana menüde seçin **proje** > **NuGet paketlerini Yönet**.

     ![Menü öğesi NuGet paketlerini Yönet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  İçinde **NuGet Paket Yöneticisi**, tıklayarak **Gözat** bağlantı. Entity Framework büyük olasılıkla üst listesinde paketidir. Tıklayın **yükleme** sağ bölmede ve yönergeleri izleyin. Çıkış penceresine, yükleme tamamlandığında size bildirilir.

     ![Entity Framework NuGet paketi](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  Şimdi Northwind veritabanına dayalı bir model oluşturmak için Visual Studio'yu kullanabilirsiniz.

## <a name="create-the-model"></a>Model oluşturma

1. ' Nde proje düğümüne sağ **Çözüm Gezgini** ve **Ekle** > **yeni öğe**. Sol bölmede altında C# düğümünü seçin **veri** ve Orta bölmede seçin **ADO.NET varlık veri modeli**.

   ![Entity Framework modelini yeni proje öğesi](../data-tools/media/raddata-ef-new-project-item.png)

2. Model çağrı `Northwind_model` ve **Tamam**. **Varlık veri modeli Sihirbazı** açılır. Seçin **EF veritabanı Tasarımcısından** ve ardından **sonraki**.

   ![Veritabanından EF modeli](../data-tools/media/raddata-ef-model-from-database.png)

3. Sonraki ekranda, uygulamanızı LocalDB Northwind bağlantı tıklatın seçip **sonraki**.

4. Sihirbazın sonraki sayfasında, tabloları, saklı yordamlar ve Entity Framework modele dahil edilecek diğer veritabanı nesnelerini seçin. Ağaç görünümünde dbo düğümünü genişletin ve seçin **müşteriler**, **siparişler**, ve **sipariş ayrıntıları**. Seçili varsayılan değerleri bırakın ve tıklayın **son**.

    ![Model için veritabanı nesneleri seçin](../data-tools/media/raddata-choose-ef-objects.png)

5. Sihirbazın oluşturduğu C# Entity Framework modelini temsil eden sınıf. Düz eski sınıflardır C# sınıfları ve bunların hangi biz olan veri bağlama WPF kullanıcı arabirimi. *.Edmx* dosya, ilişkileri ve veritabanındaki nesneleri sınıfları ilişkilendirir diğer meta veriler açıklanmaktadır. *.Tt* dosyalarıdır, model ve veritabanı değişiklikleri kaydetme işleyen kod oluşturan T4 şablonları. İçinde bu dosyaları gördüğünüz **Çözüm Gezgini** Northwind_model düğümü altında:

      ![Çözüm Gezgini EF modeli dosyaları](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    İçin tasarımcı yüzeyine *.edmx* dosya bazı özellikler ve ilişkiler modelinde değiştirmenize olanak sağlar. Bu izlenecek yolda tasarımcısını kullanmak için kullanacağız değil.

6. *.Tt* dosyalar genel amaçlı ve bunlardan birinin ObservableCollections gerektiren WPF bağlama ile çalışmak için ince ayarlamalar yapmak gerekiyor. İçinde **Çözüm Gezgini**, bulana kadar Northwind_model düğümünü *Northwind_model.tt*. (Değilsinizdir emin *. Context.tt* doğrudan aşağıdaki dosyasını *.edmx* dosyası.)

   -   İki tekrarlamalarını <xref:System.Collections.ICollection> ile <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   -   İlk geçtiği değiştirme <xref:System.Collections.Generic.HashSet%601> ile <xref:System.Collections.ObjectModel.ObservableCollection%601> 51 satırına yakın bir yerde. HashSet ikinci oluşum değiştirmeyin.

   -   Yalnızca oluşumunu değiştirin <xref:System.Collections.Generic> (yaklaşık olarak 431. satır) ile <xref:System.Collections.ObjectModel>.

7. Tuşuna **Ctrl**+**Shift**+**B** Projeyi derlemek için. Derleme tamamlandığında model sınıfları için veri kaynağı Sihirbazı'nı görülebilir.

Böylece görüntülemek, kodlarda gezinin ve verileri değiştirme XAML sayfası bu model bağlama hazırsınız.

## <a name="databind-the-model-to-the-xaml-page"></a>Veri bağlama modelini XAML sayfası

Kendi veri bağlama kod yazmak mümkündür, ancak bunu sizin için Visual Studio belirlesin daha kolaydır.

1.  Ana menüden **proje** > **yeni veri kaynağı Ekle** ortaya çıkarmak için **veri kaynağı Yapılandırma Sihirbazı**. Seçin **nesne** veritabanına model sınıfları bağlama çünkü:

     ![Veri Kaynağı Yapılandırma Sihirbazı ile nesne kaynağı](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  Seçin **müşteri**. (Siparişleri için kaynakları otomatik olarak müşteri siparişleri Gezinti özelliğinde oluşturulan.)

     ![Varlık sınıfları veri kaynakları olarak ekleyin.](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  **Son**'a tıklayın.

4.  Gidin *MainWindow.xaml* kod görünümünde. XAML bu örneğin amaçları için basit tutuyoruz. MainWindow başlığı daha açıklayıcı bir şeyle değiştirmek ve yüksekliğini ve genişliğini, 600 x 800 şimdilik artırın. Her zaman bunu daha sonra değiştirebilirsiniz. Şimdi bu üç satır tanımları ekleyin ana kılavuza, gezinti düğmelerini, bir müşterinin ayrıntılarını için ve siparişlerinin gösteren bir kılavuz için tek bir satır için:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  Artık *MainWindow.xaml* Tasarımcısı'nda görüntülediğiniz böylece. Bu neden **veri kaynakları** yanındaki Visual Studio penceresinin kenar boşluğundaki bir seçenek olarak görünmesi için pencere **araç kutusu**. Tıklayın penceresini veya başka basın için sekmesinde **Shift**+**Alt**+**D** veya tercih **görünümü**  >  **Diğer Windows** > **veri kaynakları**. Her bir özellik müşteriler sınıf kendi bireysel metin kutusunda görüntülemek için kullanacağız. İlk olarak, oka tıklayarak **müşteriler** birleşik giriş kutusu ve seçin **ayrıntıları**. Ardından, Tasarımcı Orta satırında gitmek istediğiniz bilebilmesi düğümü tasarım yüzeyine orta kısmını sürükleyin. Bunu misplace ise satır XAML daha sonra el ile belirtebilirsiniz. Varsayılan olarak, denetimleri kılavuz öğesi dikey olarak yerleştirilir ancak formda istiyor ancak bu noktada, bunları düzenleyebilirsiniz. Örneğin, bu put mantıklı olabilir **adı** adresi yukarıda üstte metin kutusu. Bu makalede örnek uygulama alanları yeniden sıralar ve bunları iki sütuna yeniden düzenler.

     ![Müşteriler veri kaynağı tek denetimleri bağlama](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     Kod Görünümü'nde, artık yeni bir görebilirsiniz `Grid` öğesinde satır 1 (Orta satırında) üst kılavuz. Üst kılavuz sahip bir `DataContext` eklenmiş bir Collectionviewsource'a başvurduğu özniteliği `Windows.Resources` öğesi. İlk metin kutusunu bağlar, bu veri bağlamı verilen **adresi**, bu adı eşlenir `Address` geçerli bir özellik `Customer` Collectionviewsource'a nesnesi.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  Bir müşteri, pencerenin üst kısmında görünür olduğunda siparişlerini alt yarı görmek istiyorsunuz. Siparişler bir tek kılavuz görünümü denetiminde gösterir. Ana öğe-ayrıntı databinding beklendiği şekilde çalışması ayrı siparişler düğüme olmayan müşteriler sınıfı siparişler özelliğine bağlama önemlidir. İsteğe bağlı olarak Tasarımcı satır 2 geçirir, böylece müşteriler sınıfın siparişler özelliği, form alt yarısında için sürükleyin:

     ![Siparişler sınıflar kılavuz sürükleyin](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio kullanıcı Arabirimi denetimleri modelinde olayları bağlanan tüm bağlama kod üretti. Bazı verileri görmek için gerçekleştirmeniz gereken tek şey model doldurmak için biraz kod yazalım. İlk olarak gidin *MainWindow.xaml.cs* ve MainWindow sınıfının veri bağlamı için bir veri üyesi ekleyin. Sizin için oluşturuldu, bu nesne değişiklikleri ve olayları modelinde izleyen bir denetim gibi davranır. Ayrıca, oluşturucu başlatma mantık ekleyeceksiniz. Üst sınıf şu şekilde görünmelidir:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Ekleme bir `using` yönergesi System.Data.Entity yük uzantı yöntemi kapsam içine almak:

     ```csharp
     using System.Data.Entity;
     ```

     Şimdi, aşağıya inin ve bulma `Window_Loaded` olay işleyicisi. Visual Studio Collectionviewsource'a nesne eklemiştir dikkat edin. Bu model oluşturduğunuzda seçtiğiniz NorthwindEntities nesneyi temsil eder. Kod ekleyelim `Window_Loaded` böylece tüm metodu artık şuna benzer:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  Tuşuna **F5**. Collectionviewsource'a alınan ilk müşterinin ayrıntılarını görmeniz gerekir. Ayrıca, veri kılavuzunda siparişlerini görmeniz gerekir. Biçimlendirme harika, böylece şimdi bunu düzeltelim değildir. Ayrıca, diğer kayıtları görüntülemek ve temel CRUD işlemleri yapmak için bir yol da oluşturabilirsiniz.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Sayfa Tasarımı ayarlamak ve Kılavuzlar yeni müşteriler ve siparişler için ekleyin

Visual Studio tarafından oluşturulan varsayılan düzenleme, uygulamanız için ideal olmadığından bazı el ile XAML içinde değişiklik yapacaksınız. Ayrıca yeni müşteri veya sipariş eklenecek kullanıcıyı etkinleştirmek için "(hangi gerçekten ızgaralar) bazı formlar" gerekir. Yeni müşteri ve sipariş biçimde ekleyebilmesi için ayrı bir verilere bağlı olmayan metin kutuları kümesi gerekir. `CollectionViewSource`. İşleyici yöntemleri Visible özelliğini ayarlayarak herhangi bir zamanda kullanıcının gördüğü hangi kılavuz kontrol. Son olarak, kullanıcının her bir sipariş silmesine izin etkinleştirmek için siparişleri kılavuzunda her satırı için bir silme düğme ekleyin.

İlk olarak, bu stil eklemek `Windows.Resources` öğesinde *MainWindow.xaml*:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

Ardından, tüm dış kılavuz bu işaretleme ile değiştirin:

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Gidin, ekleme, güncelleştirme ve silme için düğme ekleme

Windows Forms uygulamalarında veritabanındaki satırları arasında gezinme ve temel CRUD işlemleri yapmak için düğmeler BindingNavigator nesnesiyle alın. WPF bir BindingNavigator sağlamaz, ancak oluşturmanın kolay. Düğmeleri yatay StackPanel içinde bunu ve düğmeleri arka plan kod yöntemlere bağlı olan komutları ile ilişkilendirin.

Komut mantığını fours bölümü vardır: (1) komutları, (2 bağlamaları, (3) düğmeleri ve arka plan kod (4) komut işleyicileri.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML komutları, bağlamalar ve düğmeleri ekleme

1.  İlk olarak, komutlar ekleme *MainWindow.xaml* içinde dosya `Windows.Resources` öğesi:

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2.  Bir CommandBinding eşleyen bir `RoutedUICommand` arka plan kod yönteme olay. Bu ekleme `CommandBindings` öğeden sonra `Windows.Resources` kapanış etiketi:

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3.  Şimdi ekleyin `StackPanel` gezintiyi ekleme, silme ve güncelleştirme düğmeleri. İlk olarak, bu çalışma stiline ekleyin `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     İkinci olarak, bu kodu yapıştırın hemen sonrasına `RowDefinitions` için dış `Grid` öğesi, üst tarafındaki XAML sayfası:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>MainWindow sınıfının için komut işleyicileri ekleme

Arka plan kod ekleme ve silme yöntemleri dışında düzeydedir. Gezinti Collectionviewsource'a görünümü özellikte yöntemleri çağırarak gerçekleştirilir. `DeleteOrderCommandHandler` Sipariş üzerinde art arda silme yapma işlemi açıklanır. Biz öncelikle ilişkili Order_Details silmeniz gerekir. `UpdateCommandHandler` Yalnızca metin kutularına kullanıcı yapılan değişikliklerle bir mevcut müşteri veya sipariş güncelleştirmeleri yoksa yeni bir müşteri veya sipariş koleksiyona ekler.

Bu işleyici yöntemleri MainWindow sınıfta ekleyin *MainWindow.xaml.cs*. Müşteriler tablosu için Collectionviewsource'a farklı bir ada sahipse, bu yöntemlerin her biri ad ayarlamak gerekir:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Hata ayıklamayı başlatmak için basın **F5**. Müşteri ile sipariş verilerini kılavuz doldurulmuş görürsünüz ve Gezinti düğmelerinin beklenen şekilde çalışması gerekir. Tıklayarak **işleme** veri girdikten sonra yeni müşteri veya sipariş modele eklemek için. Tıklayarak **iptal** verileri kaydetmeden yeni bir müşteri ya da yeni bir sipariş formu dışında yedeklenir. Mevcut müşteriler ve siparişler doğrudan metin kutularındaki düzenlemeler yapabilir ve bu değişiklikleri modele otomatik olarak yazılır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework belgeleri](/ef/)