---
title: WPF ve Entity Framework 6 ile basit veri uygulaması oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac3db033b9e8055c28f29d54027df5fadf156742
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922204"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF ve Entity Framework 6 ile basit veri uygulaması oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu kılavuzu, Visual Studio ile SQL Server LocalDB, Northwind veritabanı, Entity Framework 6 ve Windows Presentation Foundation temel "veriler üzerinden formlar" uygulama oluşturma işlemi gösterilmektedir. Temel veri bağlama ile ana öğe-ayrıntı görünümü nasıl gösterir ve ayrıca bir özel "bağlama"Sonrakine Taşı"için düğmeleriyle"Taşıma "Başlangıca Taşı" önceki,""taşıma sona erdirmek "Gezgin" sahip "Güncelleştir" ve "Sil"  
  
 Bu makalede, Visual Studio veri araçları kullanmaya odaklanmıştır ve temel teknolojileri herhangi bir şekilde açıklamak çalışmaz. Bu, XAML, Entity Framework ve SQL temel olarak bilindiğini sahibi olduğunuzu varsayar. Bu örnek WPF uygulamaları için standart MVVM mimari, ayrıca göstermemiz gerekmez. Ancak, çok az sayıda değişiklikler ile kendi MVVM uygulamasına bu kodu kopyalayın.  
  
## <a name="install-and-connect-to-northwind"></a>Yükleme ve Northwind olarak bağlanma  
 Bu örnek, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır. ADO.NET veri sağlayıcısının bu ürün için Entity Framework destekliyorsa, aynı zamanda diğer SQL veritabanı ürünlerle çalışması gerekir.  
  
1.  Henüz yapmadıysanız, SQL Server 2014 LocalDB Express gelen 32 bit yükleme [SQL Server sürümleri indirme sayfasına](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx).  
  
2.  Buradaki yönergeleri izleyerek Northwind örnek veritabanını yüklemek: [yüklemek SQL Server örnek veritabanları](../data-tools/install-sql-server-sample-databases.md).  
  
3.  [Yeni bağlantı ekleme](../data-tools/add-new-connections.md) Northwind için.  
  
## <a name="configure-the-project"></a>Proje yapılandırma  
  
1.  Visual Studio'da **dosya &#124; yeni proje** ve ardından yeni bir C# WPF uygulaması oluşturun.  
  
2.  NuGet paketi için Entity Framework 6 sonraki ekleyeceğiz. Çözüm Gezgini'nde proje düğümünü seçin. Ana menüde seçin **proje &#124; NuGet paketlerini Yönet...**  
  
     ![Menü öğesi NuGet paketlerini Yönet](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  NuGet Paket Yöneticisi'nde tıklayarak **Gözat** bağlantı. Entity Framework büyük olasılıkla üst listesinde paketidir. Tıklayın **yükleme** sağ bölmede ve yönergeleri izleyin. Yükleme tamamlandığında, çıkış penceresine size bildirir.  
  
     ![Entity Framework NuGet paketi](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Northwind veritabanına dayalı bir model oluşturmak için Visual Studio artık kullanabiliriz.  
  
## <a name="create-the-model"></a>Model oluşturma  
  
1. Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve seçin **Ekle &#124; yeni öğe**. Sol bölmede, C# düğümü seçin **veri** ve Orta bölmede seçin **ADO.NET varlık veri modeli**.  
  
    ![Entity Framework modelini yeni proje öğesi](../data-tools/media/raddata-ef-new-project-item.png "raddata EF yeni proje öğesi")  
  
2. Model çağrı `Northwind_model` ve Tamam'ı seçin. Bu işlem sonrasında **varlık veri modeli Sihirbazı**. Seçin **EF veritabanı Tasarımcısından** ve ardından **sonraki**.  
  
    ![EF modeli veritabanından](../data-tools/media/raddata-ef-model-from-database.png "raddata veritabanından EF modeli")  
  
3. Sonraki ekranda, uygulamanızı LocalDB Northwind bağlantı tıklatın seçip **sonraki**.  
  
4. Sihirbazın sonraki sayfasında tabloları, saklı yordamlar ve Entity Framework modele dahil edilecek diğer veritabanı nesnelerini seçin. Ağaç görünümünde dbo düğümünü genişletin ve müşteri, sipariş ve sipariş ayrıntıları seçin. Varsayılan seçili bırakın ve tıklayın **son**.  
  
    ![Model için veritabanı nesneleri seçmenizi](../data-tools/media/raddata-choose-ef-objects.png "raddata EF nesneleri seçin")  
  
5. Sihirbaz, Entity Framework modelini temsil eden C# sınıfları oluşturur. Bunlar düz eski C# sınıfları ve bunların ne yapacağız veri bağlama WPF kullanıcı arabirimi. .Edmx dosyasını, ilişkileri ve veritabanındaki nesneleri sınıfları ilişkilendirir diğer meta veriler açıklanmaktadır.  Kodunu oluşturmak T4 şablonlarını model üzerinde çalışır ve değişiklikleri veritabanına kaydetmek .tt dosyalarıdır. Tüm bu Çözüm Gezgini'nde düğümü altındaki dosyaları Northwind_model görebilirsiniz:  
  
    ![Çözüm Gezgini EF modeli dosyaları](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata Çözüm Gezgini EF modeli dosyaları")  
  
    Tasarımcı yüzeyine .edmx dosyası için bazı özellikler ve ilişkiler modelinde değiştirmenize olanak sağlar. Bu izlenecek yolda tasarımcısını kullanmak için kullanacağız değil.  
  
6. .Tt dosyaları genel amaçlı ve bunlardan birinin ObservableCollections gerektiren WPF bağlama ile çalışmak için ince ayarlamalar yapmak gerekiyor.  Çözüm Gezgini'nde, Northwind_model.tt bulana kadar Northwind_model düğümünü genişletin. (Emin olun **değil** , *. Doğrudan .edmx dosyası olan bağlam .tt dosyası).  
  
   -   İki tekrarlamalarını <xref:System.Collections.ICollection> ile <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
   -   İlk geçtiği değiştirme <xref:System.Collections.Generic.HashSet%601> ile <xref:System.Collections.ObjectModel.ObservableCollection%601> 51 satırına yakın bir yerde. HashSet ikinci oluşum değiştirmeyin  
  
   -   Yalnızca oluşumunu değiştirin <xref:System.Collections.Generic> (yaklaşık olarak satır 334) ile <xref:System.Collections.ObjectModel>.  
  
7. Tuşuna **Ctrl + Shift + B** Projeyi derlemek için. Derleme tamamlandığında model sınıfları için veri kaynağı Sihirbazı'nı görülebilir.  
  
   Şimdi biz görüntülemek, gezinebilir ve verileri değiştirme, XAML sayfası bu model bağlama hazırız.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Veri bağlama modelini XAML sayfası  
 Kendi veri bağlama kod yazmak mümkündür, ancak bunu sizin için Visual Studio belirlesin daha kolaydır.  
  
1.  Ana menüden **proje &#124; yeni veri kaynağı Ekle** ortaya çıkarmak için **veri kaynağı Yapılandırma Sihirbazı**. Seçin **nesne** veritabanına model sınıfları bağlıyoruz çünkü:  
  
     ![Veri Kaynağı Yapılandırma Sihirbazı ile nesne kaynağı](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata nesne kaynağı ile veri kaynağı Yapılandırma Sihirbazı")  
  
2.  Müşteri seçin.  (Otomatik olarak kaynakları siparişleri için müşteri siparişleri Gezinti özelliğinden oluşturulacak.)  
  
     ![Veri kaynağı olarak varlık sınıflarının ekleme](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Ekle varlık sınıfları veri kaynakları olarak")  
  
3.  Tıklayın **son**  
  
4.  Kod Görünümü'nde MainWindow.xaml gidin. Bu örneğin amacı doğrultusunda XAML çok basit tutmak için kullanacağız. MainWindow başlığı daha açıklayıcı bir şeyle değiştirmek ve yüksekliğini ve genişliğini, 600 x 800 şimdilik artırın. Her zaman bunu daha sonra değiştirebilirsiniz. Şimdi bu üç satır tanımları ana kılavuz, bir müşterinin ayrıntıları siparişlerinin gösteren bir kılavuz için bir gezinti düğmeleri için bir satır ekleyin:  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5.  Artık tasarımcıda görüntülediğiniz şekilde MainWindow.xaml açın. Bu, Visual Studio penceresinin kenar araç kutusu yanında bir seçenek olarak görünmesi veri kaynakları penceresi neden olur. Tıklayın penceresini veya başka basın için sekmesinde **Shift + Alt + D** veya tercih **görünümü &#124; diğer Windows &#124; veri kaynakları**. Her bir özellik müşteriler sınıf kendi bireysel metin kutusunda görüntülemek için kullanacağız. İlk olarak müşterilerin birleşik giriş kutusunda oku tıklatın ve seçin **ayrıntıları**. Tasarımcı Orta satırında gitmek istediğiniz bilebilmesi düğümünü orta kısmını tasarım yüzeyi sürükleyin.  Bunu misplace ise satır XAML daha sonra el ile belirtebilirsiniz. Varsayılan olarak, denetimleri kılavuz öğesi dikey olarak yerleştirilir ancak formda istiyor ancak bu noktada, bunları düzenleyebilirsiniz.  Örneğin, bu adresi yukarıda üstte adı metin kutusunda koymak için mantıklı olabilir. Bu makalede örnek uygulama alanları yeniden sıralar ve bunları iki sütuna yeniden düzenler.  
  
     ![Tek denetimleri müşterilerin veri kaynağı bağlama](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata müşteriler veri kaynağı tek denetimleri bağlama")  
  
     Kod Görünümü'nde, artık yeni bir görebilirsiniz `Grid` öğesinde satır 1 (Orta satırında) üst kılavuz. Üst kılavuz sahip bir `DataContext` eklenmiş olan bir Collectionviewsource'a başvurduğu özniteliği `Windows.Resources` öğesi. İlk metin kutusuna, örneğin, bu veri bağlamı verilen "adı yönelik olarak" bağlamalar eşlenmiş durumda `Address` geçerli bir özellik `Customer` Collectionviewsource'a nesnesi.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6.  Bir müşteri, pencerenin üst kısmında görünür olduğunda siparişlerini alt yarı görmek istiyoruz. Tek bir kılavuz görünümü denetimi siparişler göstereceğiz. Ana öğe-ayrıntı databinding beklendiği şekilde çalışması biz değil ayrı siparişler düğüme müşteriler sınıfı siparişler özelliğine bağlama önemlidir. Aşağıdaki çizim dikkat edin! İsteğe bağlı olarak Tasarımcı satır 2 geçirir, böylece müşteriler sınıfın siparişler özelliği, form alt yarısında için sürükleyin:  
  
     ![Siparişler sınıflar kılavuz sürükleyin](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata Sürükle siparişler kılavuz sınıfları")  
  
7.  Visual Studio kullanıcı Arabirimi denetimleri modelinde olayları bağlanan tüm bağlama kod üretti. Bazı verileri görmek için yapmanız gereken tek şey model doldurmak için biraz kod yazalım. İlk şimdi MainWindow.xaml.cs için gidin ve veri bağlamı için MainWindow sınıfının veri üyesi ekleyin. Bizim için oluşturuldu, bu nesne değişiklikleri ve olayları modelinde izleyen bir denetim gibi davranır. Burada olmakla birlikte, daha sonra yeni bir müşteri ya da yeni sipariş eklemek için kullanacağız iki üyesi ekleyeceğiz. Oluşturucu başlatma mantığı de ekleyeceğiz. Bizim sınıfının üstüne şu şekilde görünmelidir:  
  
    ```csharp  
    public partial class MainWindow : Window  
       {  
           public Customer newCustomer { get; set; }  
           public Order newOrder { get; set; }  
  
           NorthwindEntities context = new NorthwindEntities();  
           CollectionViewSource custViewSource;  
           CollectionViewSource ordViewSource;  
  
           public MainWindow()  
           {  
               InitializeComponent();  
               newCustomer = new Customer();  
               newOrder = new Order();  
               custViewSource = ((CollectionViewSource)  
                   (FindResource("customerViewSource")));  
               ordViewSource = ((CollectionViewSource)  
                   (FindResource("customerOrdersViewSource")));  
               DataContext = this;  
           }  
    ```  
  
     Ekleme bir `using` yönergesi System.Data.Entity yük uzantı yöntemi kapsam içine almak:  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     Şimdi aşağıya kayın ve Window_Loaded olay işleyicisi bulun. Visual Studio Collectionviewsource'a nesne bizim için eklediğini dikkat edin. Bu modeli oluşturduk seçtik NorthwindEntities nesneyi temsil eder. Şimdi kod için Window_loaded ekleyebilirsiniz, böylece tüm metodu artık şuna benzer:  
  
    ```csharp  
    private void Window_Loaded(object sender, RoutedEventArgs e)  
        {  
            // Load is an extension method on IQueryable,    
            // defined in the System.Data.Entity namespace.   
            // This method enumerates the results of the query,    
            // similar to ToList but without creating a list.   
            // When used with Linq to Entities this method    
            // creates entity objects and adds them to the context.   
            context.Customers.Load();  
  
            // After the data is loaded call the DbSet<T>.Local property    
            // to use the DbSet<T> as a binding source.   
            custViewSource.Source = context.Customers.Local;  
        }  
    ```  
  
8.  Tuşuna **F5**. Collectionviewsource'a ve siparişlerinin veri kılavuzunda içine alınan ilk müşterinin ayrıntılarını görmeniz gerekir. Biçimlendirme harika, böylece şimdi bunu düzeltelim değildir. diğer kayıtları görüntülemek için bir yol oluşturma ve temel CRUD işlemleri yapın.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Sayfa Tasarımı ayarlamak ve Kılavuzlar yeni müşteriler ve siparişler için ekleyin  
 Visual Studio tarafından oluşturulan varsayılan düzenleme uygulamamız için ideal olmadığından bazı değişiklikler el ile XAML içinde oluşturacağız. Biz de yeni bir müşteri ya da yeni sipariş eklenecek kullanıcıyı etkinleştirmek için "(hangi gerçekten ızgaralar) bazı formlar" gerekir.    Yeni müşteri ve sipariş biçimde ekleyebilmesi için ayrı bir verilere bağlı olmayan metin kutuları kümesi gerekiyor `CollectionViewSource`. Biz işleyici yöntemleri Visible özelliğini ayarlayarak herhangi bir zamanda kullanıcının gördüğü hangi kılavuz kontrol.  
  
 Son olarak, her bir sipariş silmek bir kullanıcı etkinleştirmek için siparişleri kılavuzunda her satırı için Sil düğmesini ekleyeceğiz.  
  
 İlk olarak, bu stilleri için Windows.Resources ekleyin:  
  
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
<Grid >  
     <Grid.RowDefinitions>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="*"/>  
     </Grid.RowDefinitions>  
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
     </StackPanel>  
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
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
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
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
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
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>  
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
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Git, ekleme, güncelleştirme ve silme için düğme ekleme  
 Windows Forms uygulamalarında veritabanındaki satırları arasında gezinme ve temel CRUD işlemleri yapmak için düğmeler BindingNavigator nesnesiyle alın. WPF bir BindingNavigator sağlamaz, ancak bunlar yapmak çok kolay. Düğmeleri yatay StackPanel alt satırdaki sayfa ızgaranın içine bunu ve biz düğmeleri arka plan kod yöntemlere bağlı olan komutları ile ilişkilendireceksiniz.  
  
 Komut mantığını fours bölümü vardır: (1) komutları, (2 bağlamaları, (3) düğmeleri ve arka plan kod (4) komut işleyicileri.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML komutları, bağlamalar ve düğmeleri ekleme  
  
1.  İlk olarak, bizim Windows.Resources öğesi içinde MainWindow.XAML dosyasındaki komutlar ekleyelim:  
  
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
  
2.  Bir CommandBinding RoutedUICommand olay arkasındaki kodda bir yöntemi eşleştirir. Bu CommandBindings öğesi kapanış etiketi Windows.Resources sonra ekleyin:  
  
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
  
3.  Şimdi şimdi Gezinti ile StackPanel ekleyin, ekleme, silme ve güncelleştirme düğmeleri. İlk olarak, bu stil için Windows.Resources ekleyin:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     Artık XAML sayfasının üst dış kılavuz öğesi için RowDefinitions hemen sonra bu kodu yapıştırın:  
  
    ```xaml  
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
    </StackPanel>  
    ```  
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>MainWindow sınıfının için komut işleyicileri ekleme  
  
1.  Arka plan kod ekleme ve silme yöntemleri dışında düzeydedir. Gezinti Collectionviewsource'a görünümü özellikte yöntemleri çağırarak gerçekleştirildiğini unutmayın. Bir sipariş üzerinde art arda silme gerçekleştirme DeleteOrderCommandHandler gösterir. Biz öncelikle ilişkili Order_Details silmeniz gerekir. UpdateCommandHandler koleksiyona yeni bir müşteri ekler, aksi takdirde yalnızca varolan nesne ne olursa olsun metin kutularına yapılan kullanıcı değişiklik ile güncelleştirir.  
  
2.  Bu işleyici yöntemleri MainWindow.xaml.cs MainWindow sınıfta ekleyin, ardından, Collectionviewsource'a Müşteriler tablosu için farklı bir ada sahipse, bu yöntemlerin her biri ad ayarlamak gerekecektir:  
  
    ```csharp  
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToLast();  
    }  
  
    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToPrevious();  
    }  
  
    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToNext();  
    }  
  
    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToFirst();  
    }  
  
    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // If existing window is visible, then delete the customer and all their orders.  
        // In a real application, you should add warnings and allow a user to cancel the operation.  
        var cur = custViewSource.View.CurrentItem as Customer;  
  
        var cust = (from c in context.Customers  
                    where c.CustomerID == cur.CustomerID  
                    select c).FirstOrDefault();  
  
        if (cust != null)  
        {  
            foreach (var ord in cust.Orders.ToList())  
            {  
                Delete_Order(ord);  
            }  
            context.Customers.Remove(cust);  
        }  
        context.SaveChanges();  
        custViewSource.View.Refresh();  
    }  
  
    // Commit changes from the new customer form, the new order form,  
    // or edits made to the existing customer form.  
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        if (newCustomerGrid.IsVisible)  
        {  
            // Create a new object because the old one  
            // is being tracked by EF now.  
            newCustomer = new Customer();   
            newCustomer.Address = add_addressTextBox.Text;  
            newCustomer.City = add_cityTextBox.Text;  
            newCustomer.CompanyName = add_companyNameTextBox.Text;  
            newCustomer.ContactName = add_contactNameTextBox.Text;  
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;  
            newCustomer.Country = add_countryTextBox.Text;  
            newCustomer.CustomerID = add_customerIDTextBox.Text;  
            newCustomer.Fax = add_faxTextBox.Text;  
            newCustomer.Phone = add_phoneTextBox.Text;  
            newCustomer.PostalCode = add_postalCodeTextBox.Text;  
            newCustomer.Region = add_regionTextBox.Text;  
  
            // Perform very basic validation  
            if (newCustomer.CustomerID.Length == 5)  
            {  
                // Insert the new customer at correct position:  
                int len = context.Customers.Local.Count();  
                int pos = len;  
                for (int i = 0; i < len; ++i)  
                {  
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)  
                    {  
                        pos = i;  
                        break;  
                    }  
                }  
                context.Customers.Local.Insert(pos, newCustomer);  
                custViewSource.View.Refresh();  
                custViewSource.View.MoveCurrentTo(newCustomer);  
            }  
            else  
            {  
                MessageBox.Show("CustomerID must have 5 characters.");  
            }  
  
            newCustomerGrid.Visibility = Visibility.Collapsed;  
            existingCustomerGrid.Visibility = Visibility.Visible;  
        }  
        else if (newOrderGrid.IsVisible)  
        {  
            // Order ID is auto-generated so we don't set it here.  
            // For CustomerID, address, etc we use the values from current customer.  
            // User can modify these in the datagrid after the order is entered.  
  
            newOrder.OrderDate = add_orderDatePicker.SelectedDate;  
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;  
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;  
            try  
            {  
                // Exercise for the reader if you are using Northwind:  
                // Add the Northwind Shippers table to the model.  
                // Acceptable ShipperID values are 1, 2, or 3.  
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"  
                    || add_ShipViaTextBox.Text == "3")  
                {  
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);  
                }  
                else  
                {  
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");  
                    return;  
                }  
            }  
            catch  
            {  
                MessageBox.Show("Ship Via must be convertible to int");  
                return;  
            }  
            try  
            {  
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);  
            }  
            catch  
            {  
                MessageBox.Show("Freight must be convertible to decimal.");  
                return;  
            }  
  
            // Add the order into the EF model  
            context.Orders.Add(newOrder);  
            ordViewSource.View.Refresh();  
        }  
  
        // Save the changes, either for a new customer, a new order  
        // or an edit in an existing customer or order  
        context.SaveChanges();  
    }  
  
    // Sets up the form so that user can enter data. Data is later  
    // saved when user clicks Commit.  
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Visible;  
  
        // Clear all the text boxes before adding a new customer.  
        foreach (var child in newCustomerGrid.Children)  
        {  
            var tb = child as TextBox;  
            if (tb != null)  
            {  
                tb.Text = "";  
            }  
        }  
    }  
  
    private void NewOrder_click(object sender, RoutedEventArgs e)  
    {  
        var cust = custViewSource.View.CurrentItem as Customer;  
        if (cust == null)  
        {  
            MessageBox.Show("No customer selected.");  
            return;  
        }  
  
        newOrder.CustomerID = cust.CustomerID;  
  
        // Get address and other mostly constant fields from   
        // an existing order, if one exists  
        var coll = custViewSource.Source as IEnumerable<Customer>;  
        var lastOrder = (from c in coll  
                         from ord in c.Orders  
                         select ord).LastOrDefault();  
        if (lastOrder != null)  
        {  
            newOrder.ShipAddress = lastOrder.ShipAddress;  
            newOrder.ShipCity = lastOrder.ShipCity;  
            newOrder.ShipCountry = lastOrder.ShipCountry;  
            newOrder.ShipName = lastOrder.ShipName;  
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;  
            newOrder.ShipRegion = lastOrder.ShipRegion;  
        }  
  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.UpdateLayout();  
        newOrderGrid.Visibility = Visibility.Visible;  
    }  
  
    // Cancels any input into the new customer form  
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        add_addressTextBox.Text = "";  
        add_cityTextBox.Text = "";  
        add_companyNameTextBox.Text = "";  
        add_contactNameTextBox.Text = "";  
        add_contactTitleTextBox.Text = "";  
        add_countryTextBox.Text = "";  
        add_customerIDTextBox.Text = "";  
        add_faxTextBox.Text = "";  
        add_phoneTextBox.Text = "";  
        add_postalCodeTextBox.Text = "";  
        add_regionTextBox.Text = "";  
  
        existingCustomerGrid.Visibility = Visibility.Visible;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
    }  
  
    private void Delete_Order(Order order)  
    {  
        // Find the order in the EF model.  
        var ord = (from o in context.Orders.Local  
                   where o.OrderID == order.OrderID  
                   select o).FirstOrDefault();  
  
        // Delete all the order_details that have  
        // this Order as a foreign key  
        foreach (var detail in ord.Order_Details.ToList())  
        {  
            context.Order_Details.Remove(detail);  
        }  
  
        // Now it's safe to delete the order.  
        context.Orders.Remove(ord);  
        context.SaveChanges();  
  
        // Update the data grid.  
        ordViewSource.View.Refresh();  
    }  
  
    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // Get the Order in the row in which the Delete button was clicked.  
        Order obj = e.Parameter as Order;  
        Delete_Order(obj);  
    }  
    ```  
  
3.  Tuşuna **F5**. Verilerinizi görürsünüz ve Gezinti düğmelerinin beklenen şekilde çalışması gerekir. "Veri girdikten sonra yeni müşteri veya sipariş modele eklemek için işleme" üzerinde tıklayın.  Yeni bir müşteri ya da yeni bir sipariş formu kaydetmeden dışında yedeklemek için "İptal"'i tıklatın. Mevcut müşteriler ve siparişler doğrudan metin kutularındaki düzenlemeleri yapın ve bu değişiklikleri modele otomatik olarak yazılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET için Visual Studio veri Araçları](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework belgeleri](https://msdn.microsoft.com/data/ee712907.aspx)

