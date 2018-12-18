---
title: 'İzlenecek yol: bir Azure mobil hizmetinize bağlanan bir WPF masaüstü uygulaması oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9ab2c5bbea358c226407ba83e2a367195ecfef06
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270620"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>İzlenecek yol: bir Azure mobil hizmetinize bağlanan bir WPF masaüstü uygulaması oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF), hızlı bir şekilde depolamak ve veri sağlamak için bir Azure mobil hizmet kullanan modern bir masaüstü uygulaması oluşturmak için kullanabilirsiniz.  
  
##  <a name="Requirements"></a> Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdakiler gerekir:  
  
-   Visual Studio 2015 – WPF geliştirmesini destekleyen herhangi bir sürümü.  
  
-   Etkin bir Microsoft Azure hesabı.  
  
    -   Ücretsiz bir deneme hesabı için kaydolabilirsiniz [burada](http://azure.microsoft.com/pricing/free-trial/).  
  
    -   Etkinleştirebilir [MSDN abone Avantajlarınızı](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). MSDN aboneliğiniz, ücretli Azure hizmetlerinizi kullanabildiğiniz her ay krediler sunar.  
  
## <a name="create-a-project-and-add-references"></a>Bir proje oluşturma ve başvurular ekleme  
 İlk adım, bir WPF projesi oluşturun ve Azure mobil Hizmetler'e bağlanmasına olanak sağlayan bir NuGet paketi eklemektir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, ya da genişletin **Visual C#** veya **Visual Basic** düğüm ve **Windows** düğümünü ve ardından **Windows** düğümünü seçip **Klasik Masaüstü** düğümü.  
  
3.  Şablon listesinde **WPF uygulaması** şablonu.  
  
4.  İçinde **adı** metin kutusuna `WPFQuickStart`ve ardından **Tamam** düğmesi.  
  
     Proje oluşturulur ve proje dosyaları eklenir **Çözüm Gezgini**ve adlı varsayılan uygulama penceresi için tasarımcı **MainWindow.xaml** görüntülenir.  
  
#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Windows Azure mobil hizmetler SDK'sına bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları** düğüm ve **NuGet paketlerini Yönet**.  
  
2.  İçinde **NuGet Paket Yöneticisi**, seçin **arama** girin ve alan `mobileservices`.  
  
3.  Sol bölmede seçin **WindowsAzure.MobileServices**seçip sağ bölmede **yükleme** düğmesi.  
  
    > [!NOTE]
    >  Varsa bir **Önizleme** iletişim kutusu açılır, önerilen değişiklikleri gözden geçirin ve ardından **Tamam** düğmesi.  
  
4.  İçinde **lisans kabulü** iletişim kutusunda, lisans koşulları ve daha sonra bunları seçerek kabul İnceleme **kabul ediyorum** düğmesi.  
  
     Gerekli başvuruları eklenecek **Çözüm Gezgini**.  
  
    > [!NOTE]
    >  Lisans koşullarını kabul etmiyorsanız, seçin **reddediyorum** düğmesi. Gözden geçirme geri kalanını tamamlamak mümkün olmayacaktır.  
  
## <a name="create-the-user-interface"></a>Kullanıcı arabirimi oluşturma  
 Sonraki adımda, uygulama için kullanıcı arabirimi oluşturmaktır. İlk standart yan yana iki bölme Düzen görüntüleyen bir yeniden kullanılabilir kullanıcı denetimi oluşturacaksınız. Ana uygulama penceresini kullanıcı denetimi ekleyin ve girin ve verileri görüntülemek için denetimler ekleme sonra mobil hizmet arka ucu ile etkileşimi tanımlamak için kod yazma.  
  
#### <a name="to-add-a-user-control"></a>Bir kullanıcı denetimi eklemek için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **WPFQuickStart** düğüm ve **Ekle**, **yeni klasör**.  
  
2.  Klasör adı `Common`.  
  
3.  Kısayol menüsünü açın **ortak** klasörü seçin **Ekle**, **kullanıcı denetimi**.  
  
4.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, ad alanını seçin ve girin `QuickStartTask`ve ardından **Ekle** düğmesi.  
  
     Kullanıcı denetimi projeye eklenir ve **QuickStartTask.xaml** dosyası tasarımcıda açılır.  
  
5.  Tasarımcı alt bölmesinde seçin `<Grid>` ve `</Grid>` etiketleri ve bunları aşağıdaki XAML kod ile değiştirin:  
  
    ```xaml  
    <Grid VerticalAlignment="Top">  
            <StackPanel Orientation="Horizontal">  
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">  
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>  
                </Border>  
                <StackPanel>  
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />  
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />  
                </StackPanel>  
            </StackPanel>  
        </Grid>  
    ```  
  
     Bu XAML kodu yer tutucuları sayısı, başlık ve açıklama alanlar için yeniden kullanılabilir bir düzeni oluşturur. Çalışma zamanında yer tutucu metinle aşağıdaki çizimde gösterildiği gibi değiştirilebilir.  
  
     ![QuickStartTask kullanıcı denetimi](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6.  İçinde **Çözüm Gezgini**, genişletme **QuickStartTask.xaml** düğüm ve açık **QuickStartTask.xaml.cs** veya **QuickStartTask.xaml.vb**dosya.  
  
7.  Kod Düzenleyicisi'nde değiştirin `namespace WPFQuickStart.Common` (C#) ad alanı veya `Public Class QuickStartTask` (VB) yöntemini aşağıdaki kod ile:  
  
    ```csharp  
    namespace WPFQuickStart.Common  
    {  
        /// <summary>  
        /// Interaction logic for QuickStartTask.xaml  
        /// </summary>  
        public partial class QuickStartTask : UserControl  
        {  
            public QuickStartTask()  
            {  
                this.InitializeComponent();  
                this.DataContext = this;  
            }  
  
            public int Number  
            {  
                get { return (int)GetValue(NumberProperty); }  
                set { SetValue(NumberProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty NumberProperty =  
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));  
  
            public string Title  
            {  
                get { return (string)GetValue(TitleProperty); }  
                set { SetValue(TitleProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty TitleProperty =  
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
  
            public string Description  
            {  
                get { return (string)GetValue(DescriptionProperty); }  
                set { SetValue(DescriptionProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty DescriptionProperty =  
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
        }  
    }  
    ```  
  
    ```vb  
    Partial Public Class QuickStartTask  
            Inherits UserControl  
  
            Public Sub New()  
                Me.InitializeComponent()  
                Me.DataContext = Me  
            End Sub  
  
            Public Property Number() As Integer  
                Get  
                    Return CInt(Fix(GetValue(NumberProperty)))  
                End Get  
                Set(ByVal value As Integer)  
                    SetValue(NumberProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))  
  
            Public Property Title() As String  
                Get  
                    Return CStr(GetValue(TitleProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(TitleProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
  
            Public Property Description() As String  
                Get  
                    Return CStr(GetValue(DescriptionProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(DescriptionProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
        End Class  
    ```  
  
     Bu kod, çalışma zamanında sayı, başlık ve açıklama alanlarının değerlerini ayarlamak için bağımlılık özellikleri kullanır.  
  
8.  Menü çubuğunda, **derleme**, **derleme WPFQuickStart** kullanıcı denetimi oluşturmak için.  
  
#### <a name="to-create-and-modify-the-main-window"></a>Oluşturma ve ana pencereyi değiştirme  
  
1.  İçinde **Çözüm Gezgini**açın **MainWindow.xaml** dosya.  
  
2.  **Önemli**. Bu C# için yalnızca bir adımdır. Visual Basic kullanıyorsanız, sonraki adıma atlayın. Tasarımcı alt bölmede satırı bulun `xmlns:local=”clr-namespace:WPFQuickStart”` aşağıdaki XAML kod ile değiştirin:  
  
    ```xaml  
    xmlns:local=”clr-namespace:WPFQuickStart.Common”  
    ```  
  
3.  İçinde **özellikleri** penceresinde genişletin **ortak** kategorisi düğümünü seçip **başlık** özelliği ve enter `WPF Todo List` tuşuna basın **Enter**  anahtarı.  
  
     Dikkat **başlık** XAML pencere öğesinde değişiklikler yeni değer ile eşleşmelidir. XAML penceresinde XAML özellikleri değiştirebilirsiniz veya **özellikleri** penceresi ve değişiklikleri eşitlenir.  
  
4.  XAML penceresinde değerini **yükseklik** öğesine `768`ve değerini ayarlama **genişliği** özelliğini `1280`.  
  
     Bu öğeler karşılık **yükseklik** ve **genişliği** bulunan özellikler, **Düzen** kategorisinde **özellikleri** penceresi.  
  
5.  Seçin `<Grid>` ve `</Grid>` etiketleri ve bunları aşağıdaki XAML kod ile değiştirin:  
  
    ```xaml  
    <Grid>  
  
            <Grid Margin="50,50,10,10">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="*" />  
                </Grid.ColumnDefinitions>  
                <Grid.RowDefinitions>  
                    <RowDefinition Height="Auto" />  
                    <RowDefinition Height="*" />  
                </Grid.RowDefinitions>  
  
                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">  
                    <StackPanel>  
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>  
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>  
                    </StackPanel>  
                </Grid>  
  
                <Grid Grid.Row="1">  
                    <StackPanel>  
  
                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />  
  
                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">  
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>  
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>  
                        </StackPanel>  
  
                    </StackPanel>  
                </Grid>  
  
                <Grid Grid.Row="1" Grid.Column="1">  
                    <Grid.RowDefinitions>  
                        <RowDefinition Height="Auto" />  
                        <RowDefinition />  
                    </Grid.RowDefinitions>  
                    <StackPanel>  
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />  
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>  
                    </StackPanel>  
  
                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">  
                        <ListView.ItemTemplate>  
                            <DataTemplate>  
                                <StackPanel Orientation="Horizontal">  
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>  
                                </StackPanel>  
                            </DataTemplate>  
                        </ListView.ItemTemplate>  
                    </ListView>  
  
                </Grid>  
  
            </Grid>  
        </Grid>  
    ```  
  
     Değişiklikler tasarım penceresinde yansıtılır dikkat edin. Yine de kullanıcı arabirimi denetimleri ekleyerek tanımladığınız **araç kutusu** penceresinde ve Özellikler ayarı **özellikleri** penceresi. Tasarımcıda yapılan herhangi bir şey, XAML kod ve bunun tersi de yapılabilir.  
  
     Bu noktada, tasarım, aşağıdaki gibi görünmelidir.  
  
     ![Tasarımcı MainWindow](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    >  Sonraki birkaç yordamları izleyerek sırasında hatalar görebilirsiniz **hata listesi** açıksa. Endişelenmeyin; Kalan yordamları tamamladıktan sonra bu hatalar kaybolur.  
  
6.  İçinde **Çözüm Gezgini**, genişletme **MainWindow.xaml** düğüm ve açık **MainWindow.xaml.cs** veya **MainWindow.xaml.vb** dosya.  
  
7.  Kod Düzenleyicisi'nde, aşağıdaki ekleyin `using` veya `Imports` yönergelerini dosyanın en üstüne:  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    Imports Newtonsoft.Json  
    ```  
  
8.  Tüm kod değiştirmek **WPFQuickStart** ad alanı (C#) veya **sınıfı MainWindow** sınıfı (VB) aşağıdaki kod ile:  
  
    ```csharp  
    namespace WPFQuickStart  
    {  
        /// <summary>  
        /// Interaction logic for MainWindow.xaml  
        /// </summary>  
        public class TodoItem  
        {  
            public string Id { get; set; }  
  
            [JsonProperty(PropertyName = "text")]  
            public string Text { get; set; }  
  
            [JsonProperty(PropertyName = "complete")]  
            public bool Complete { get; set; }  
        }  
  
        public partial class MainWindow : Window  
        {  
            private MobileServiceCollection<TodoItem, TodoItem> items;  
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void InsertTodoItem(TodoItem todoItem)  
            {  
                // This code inserts a new TodoItem into the database. When the operation completes  
                // and Mobile Services has assigned an Id, the item is added to the CollectionView  
                await todoTable.InsertAsync(todoItem);  
                items.Add(todoItem);  
            }  
  
            private async void RefreshTodoItems()  
            {  
                try  
                {  
                    // This code refreshes the entries in the list view by querying the TodoItem table.  
                    // The query excludes completed TodoItems  
                    items = await todoTable  
                        .Where(todoItem => todoItem.Complete == false)  
                        .ToCollectionAsync();  
                    ListItems.ItemsSource = items;  
                }  
                catch (MobileServiceInvalidOperationException e)  
                {  
                    MessageBox.Show(e.Message, "Error loading items");  
                }  
            }  
  
            private async void UpdateCheckedTodoItem(TodoItem item)  
            {  
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService   
                // responds, the item is removed from the list   
                await todoTable.UpdateAsync(item);  
                items.Remove(item);  
            }  
  
            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)  
            {  
                RefreshTodoItems();  
            }  
  
            private void ButtonSave_Click(object sender, RoutedEventArgs e)  
            {  
                var todoItem = new TodoItem { Text = TodoInput.Text };  
                InsertTodoItem(todoItem);  
                TodoInput.Text = "";  
            }  
  
            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)  
            {  
                CheckBox cb = (CheckBox)sender;  
                TodoItem item = cb.DataContext as TodoItem;  
                UpdateCheckedTodoItem(item);  
            }  
  
            protected override void OnActivated(EventArgs e)  
            {  
                RefreshTodoItems();  
            }  
        }  
  
    }  
    ```  
  
    ```vb  
    Public Class TodoItem  
        Public Property Id() As String  
  
        <JsonProperty(PropertyName:="text")>  
        Public Property Text() As String  
  
        <JsonProperty(PropertyName:="complete")>  
        Public Property Complete() As Boolean  
    End Class  
  
    Partial Public Class MainWindow  
        Inherits Window  
  
        Private items As MobileServiceCollection(Of TodoItem, TodoItem)  
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)  
            ' This code inserts a new TodoItem into the database. When the operation completes  
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView  
            Await todoTable.InsertAsync(todoItem)  
            items.Add(todoItem)  
        End Sub  
  
        Private Async Sub RefreshTodoItems()  
            Dim exception As MobileServiceInvalidOperationException = Nothing  
            Try  
                ' This code refreshes the entries in the list view by querying the TodoItem table.  
                ' The query excludes completed TodoItems  
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()  
            Catch e As MobileServiceInvalidOperationException  
                exception = e  
            End Try  
  
            If exception IsNot Nothing Then  
                MessageBox.Show(exception.Message, "Error loading items")  
            Else  
                ListItems.ItemsSource = items  
            End If  
        End Sub  
  
        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)  
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService   
            ' responds, the item is removed from the list   
            Await todoTable.UpdateAsync(item)  
            items.Remove(item)  
        End Sub  
  
        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            RefreshTodoItems()  
        End Sub  
  
        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}  
            InsertTodoItem(todoItem)  
            TodoInput.Text = ""  
        End Sub  
  
        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim cb As CheckBox = DirectCast(sender, CheckBox)  
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)  
            UpdateCheckedTodoItem(item)  
        End Sub  
  
        Protected Overrides Sub OnActivated(ByVal e As EventArgs)  
            RefreshTodoItems()  
        End Sub  
    End Class  
    ```  
  
     Bu kod, zaman uyumsuz yöntemler kullanarak mobil hizmet kullanıcı arabirimi ve veritabanı arasındaki etkileşimi tanımlar.  
  
## <a name="create-the-azure-mobile-service"></a>Azure mobil hizmet oluşturma  
 Microsoft Azure'da bir mobil hizmet oluşturmak için son adımdır verilerinizi depolamak ve ardından hizmet örneği uygulamanızdan başvuru için bir tablo ekleyin.  
  
#### <a name="to-create-a-mobile-service"></a>Bir mobil hizmet oluşturmak için  
  
1.  Bir web tarayıcısı açın ve, Microsoft Azure Portal'da oturum açın ve ardından **mobil Hizmetler** sekmesi.  
  
2.  Seçin **yeni** düğmesini ve ardından iletişim kutusu açılır, **işlem**, **mobil hizmeti, oluşturma**.  
  
3.  İçinde **yeni mobil hizmet** iletişim kutusunda seçin **URL** metin girin `wpfquickstart01`.  
  
    > [!NOTE]
    >  URL sayısal bölümünü değiştirmeniz gerekebilir. Microsoft Azure, her mobil hizmetiniz için benzersiz bir URL gerektirir.  
  
     Bu hizmete URL'sini ayarlar *https://wpfquickstart01.azure-mobile.net/*.  
  
4.  İçinde **veritabanı** listesinde, bir veritabanı seçeneği belirleyin. Bu büyük olasılıkla çok sayıda kullanım vermeyeceğiz bir uygulama olduğundan, seçmek isteyebilirsiniz **ücretsiz 20 MB SQL veritabanı oluşturma** seçeneğini veya zaten aboneliğinizle ilişkili bir ücretsiz veritabanı seçin.  
  
5.  İçinde **bölge** mobil hizmet dağıtma ve ardından istediğiniz veri merkezinde liste öğesini **sonraki** (sağ ok) düğmesini.  
  
    > [!NOTE]
    >  Bu hizmet için varsayılan kullanacağınız **arka UÇ** ayarını **JavaScript**.  
  
6.  Yeni bir veritabanı oluşturuyorsanız **veritabanı ayarlarını belirt** sayfasında **sunucu** liste seçin **yeni SQL veritabanı sunucusu**, girin, **SQL oturum açma ADI** ve **parola**ve ardından **tam** (onay işareti) düğmesi.  
  
7.  Varolan bir veritabanını seçerseniz **veritabanı ayarlarını** girin, **oturum açma PAROLASI** seçip **tam** (onay işareti) düğmesi.  
  
     Mobil hizmet oluşturma işlemi başlayacak. İşlem tamamlandıktan sonra durumu değişir **hazır** ve sonraki adıma geçin.  
  
8.  Portalda, yeni oluşturduğunuz mobil hizmete seçin ve sonra **ANAHTARLARI Yönet** düğmesi.  
  
9. İçinde **erişim anahtarlarını Yönet** iletişim kutusunda, kopyalama **uygulama anahtarı**.  
  
     Bu bir sonraki yordamda kullanacaksınız.  
  
#### <a name="to-create-a-table"></a>Bir tablo oluşturmak için  
  
1.  Microsoft Azure Portalı'nda, mobil hizmetinize ve menü çubuğundan adının yanındaki oka seçin, **veri**ve ardından **ADD A tablo** bağlantı.  
  
2.  İçinde **yeni tablo oluştur** iletişim, **tablo adı** metin kutusuna girin `TodoItem`ve ardından **tam** (onay işareti) düğmesi.  
  
     Tablo oluşturulmasını bekleyin ve ardından son yordama geçin.  
  
#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Mobil hizmet için bir bildirim eklemek için  
  
1.  Visual Studio'ya geri dönün. İçinde **Çözüm Gezgini**, genişletme **App.xaml** (C#) veya **Application.xaml** (Visual Basic) düğüm ve açık **App.xaml.cs** veya  **App.xaml.vb** dosya.  
  
2.  Kod Düzenleyicisi'nde, aşağıdaki ekleyin `using` veya **içeri aktarmalar** yönergelerini dosyanın en üstüne:  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3.  Sınıfına aşağıdaki bildirimi ekleyin değiştirerek *YOUR SERVICE_HERE* hizmetinizin URL'sini adıyla ve değiştirme *YOUR-KEY-HERE* önceki kopyaladığınız uygulama anahtarına sahip yordam:  
  
    ```csharp  
    public static MobileServiceClient MobileService = new MobileServiceClient(  
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",  
                 "YOUR-KEY-HERE"  
             );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     Bu kod Microsoft Azure üzerinde çalışan mobil hizmete erişmesine izin verir.  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 İşte bu kadar – bir Azure mobil hizmetinize erişen WPF masaüstü uygulaması oluşturdunuz. Şimdi kaldı olan uygulamayı çalıştırmak ve nasıl çalıştığını görün.  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
1.  Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat** (veya F5 tuşuna basın).  
  
2.  İçinde **Todoıtem Ekle** metin girin `Do something`ve ardından **Kaydet** düğmesi.  
  
3.  Girin `Do something else`ve ardından **Kaydet** düğmesini tekrar.  
  
     İki girişin eklenen bildirimi **sorgu ve güncelleştirme veri** listesinde, aşağıdaki çizimde gösterildiği gibi.  
  
     ![Todo öğeleri listesine eklenir. ](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4.  Onay kutusunu seçip **başka bir şey** listesinde girişi.  
  
     Bu çağrı **UpdateCheckedTodoItem** yöntemi ve hem liste hem de veritabanı öğeyi kaldırır.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bir Azure arka uç WPF masaüstü uygulaması oldukça basitleştirilmiş bir örneği tamamladınız. Elbette, gerçek bir uygulamada çok daha karmaşık olabilir, ancak aynı temel kavramlar geçerlidir. Bkz: [WPF .NET Framework'teki](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx).  
  
 Renk, şekiller, grafik ve hatta animasyonları ekleyerek kullanıcı arabirimi daha cazip hale getirebilirsiniz. Bkz: [Visual Studio ve Visual Studio için Blend, XAML tasarlama](../designers/designing-xaml-in-visual-studio.md).  
  
 Mevcut SQL veritabanları veya diğer Azure mobil Hizmetleri'ni kullanarak veri kaynaklarına bağlanabilirsiniz. Bkz: [mobil hizmetler belgeleri](http://azure.microsoft.com/services/app-service/mobile/).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: İlk WPF Masaüstü Uygulamam](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [Windows Presentation Foundation ile Modern Masaüstü Uygulamaları Oluşturma](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)



