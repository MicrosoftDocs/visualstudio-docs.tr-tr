---
title: Özellikler, görev listesi, çıktı ve Seçenekler Windows genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebff9aaeb49d99b26b92d1908e22397b9ab0a20d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868696"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Özellikleri, görev listesi, çıktı ve Seçenekler pencerelerini genişletme
Visual Studio'da herhangi bir araç penceresine erişebilirsiniz. Bu izlenecek yol, araç penceresi hakkında bilgi yeni bir tümleştirme işlemi açıklanır **seçenekleri** sayfası ve yeni bir ayar **özellikleri** sayfası ve nasıl için yazacağınız **görevlistesi** ve **çıkış** windows.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Araç penceresi içeren bir uzantı oluşturma  
  
1.  Adlı bir proje oluşturma **TodoList** VSIX şablonuyla ve adlı bir özel araç penceresi öğesi şablonu ekleme **TodoWindow**.  
  
    > [!NOTE]
    >  Araç penceresi içeren bir uzantı oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Araç penceresi ayarlama  
 Bir metin kutusunda, yeni bir ToDo öğesi, listesine yeni öğe eklemek için bir düğme ve listedeki öğeleri görüntülemek için bir ListBox türüne ekleyin.  
  
1.  İçinde *TodoWindow.xaml*, düğme, metin kutusu ve StackPanel denetimleri UserControl Sil.  
  
    > [!NOTE]
    >  Bu silmediği **button1_Click** olay işleyicisi, daha sonraki bir adımda yeniden kullanır.  
  
2.  Gelen **tüm WPF denetimleri** bölümünü **araç kutusu**, sürükleyin bir **tuval** kılavuz denetimi.  
  
3.  Sürükleme bir **TextBox**, **düğmesi**ve **ListBox** tuvaline. Metin kutusu ve düğme aynı düzeyde olan ve bunları aşağıda resimde olduğu gibi penceresinin rest ListBox doldurur öğeleri düzenleyin.  
  
     ![Araç penceresi tamamlandı](../extensibility/media/t5-toolwindow.png "T5 araç penceresi")  
  
4.  XAML bölmesinde düğmeyi bulmak ve içerik özelliğinin değerini **Ekle**. Düğme denetimi için düğme olayı işleyicisi ekleyerek yeniden bir `Click="button1_Click"` özniteliği. Tuval bloğu gibi görünmelidir:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
### <a name="customize-the-constructor"></a>Oluşturucu özelleştirme  
  
1.  İçinde *TodoWindowControl.xaml.cs* dosyasında, aşağıdaki using deyimi:  
  
    ```csharp  
    using System;  
    ```  
  
2.  TodoWindow genel bir başvuru ekleyin ve TodoWindow parametre TodoWindowControl oluşturucuya sahip. Kod gibi görünmelidir:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  İçinde *TodoWindow.cs*, TodoWindowControl Oluşturucusu TodoWindow parametre içerecek şekilde değiştirin. Kod gibi görünmelidir:  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>Seçenekler sayfası oluşturma  
 Bir sayfada sağladığınız **seçenekleri** iletişim kutusunu kullanıcılar araç penceresi ayarlarını değiştirebilirsiniz. Seçenekler sayfası oluşturma seçenekleri ve bir girişi tanımlayan iki sınıfı gerektirir *TodoListPackage.cs* veya *TodoListPackage.vb* dosya.  
  
1. Adlı bir sınıf ekleyin `ToolsOptions.cs`. Olun `ToolsOptions` sınıf türünden devralınır <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
   ```csharp  
   class ToolsOptions : DialogPage  
   {  
   }  
   ```  
  
2. Aşağıdaki using deyimi:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
3. Bu kılavuzda açıklanan seçenekler sayfası DaysAhead adlı yalnızca bir seçenek sağlar. Adlı bir özel alan eklemek **daysAhead** ve adlı bir özellik **DaysAhead** için `ToolsOptions` sınıfı:  
  
   ```csharp  
   private double daysAhead;  
  
   public double DaysAhead  
   {  
       get { return daysAhead; }  
       set { daysAhead = value; }  
   }  
   ```  
  
   Şimdi, projeyi Bu seçenekler sayfası farkında olmanız gerekir.  
  
### <a name="make-the-options-page-available-to-users"></a>Seçenekler sayfası kullanıcılar için kullanılabilir yap  
  
1.  İçinde *TodoWindowPackage.cs*, ekleme bir <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> için `TodoWindowPackage` sınıfı:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  İlk parametre olarak ProvideOptionPage Oluşturucu sınıf türüdür `ToolsOptions`, daha önce oluşturduğunuz. İkinci parametresi, "ToDo" kategorisinde adıdır **seçenekleri** iletişim kutusu. Üçüncü parametresi, "Genel" şeklindedir kategorisidir **seçenekleri** iletişim kutusu burada seçenekler sayfası kullanıma sunulacaktır. Dizeler için kaynak kimliklerini sonraki iki parametreleridir; İlk kategori adıdır ve ikinci kategori adıdır. Son parametresi, bu sayfada Otomasyon kullanılarak erişilebilir olup olmadığını belirler.  
  
     Seçenekler sayfası, bir kullanıcı oturum açtığında, aşağıdaki resimde benzemelidir.  
  
     ![Seçenekler sayfası](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Kategorisinin **ToDo** ve kategori **genel**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Veri ve özellik penceresini kullanılabilir yapın  
 Adlı bir sınıf oluşturarak, yapılacaklar listesi bilgilerini kullanılabilir yapabilirsiniz `TodoItem` Yapılacaklar listesinde, tek tek öğeler hakkındaki bilgileri depolar.  
  
1.  Adlı bir sınıf ekleyin `TodoItem.cs`.  
  
     Araç penceresi kullanıcılar için kullanılabilir olduğunda, liste öğeleri Todoıtems tarafından temsil edilir. Kullanıcı bu öğelerden birini liste kutusunda seçtiğinde **özellikleri** pencere öğesi hakkında bilgi görüntüler.  
  
     Veri kullanılabilir hale getirmek için **özellikleri** iki özel özniteliklere sahip genel özelliklerini veri özelliğini penceresinde `Description` ve `Category`. `Description` en altında görüntülenen metin **özellikleri** penceresi. `Category` özelliğin ne zaman nerede görüneceğini belirler **özellikleri** penceresi görüntülenir **kategorilere göre** görünümü. Aşağıdaki resimde, **özellikleri** penceresi konusu **kategorilere göre** görünümü **adı** özelliğinde **ToDo alanları** kategorisi Seçili açıklaması **adı** özelliği, pencerenin alt kısmında görüntülenir.  
  
     ![Özellikler penceresi](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Aşağıdaki using deyimlerini *TodoItem.cs* dosya.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Ekleme `public` sınıf bildirimine erişim değiştiricisi.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     İki özelliği Ekle `Name` ve `DueDate`. Şimdi `UpdateList()` ve `CheckForErrors()` daha sonra.  
  
    ```csharp  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  Kullanıcı denetimi için özel bir başvuru ekleyin. Kullanıcı denetimi ve bu ToDo öğesi için ad alan bir oluşturucu ekleyin. Değeri bulmak için `daysAhead`, Seçenekler sayfasında özellik alır.  
  
    ```csharp  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  Çünkü örneklerini `TodoItem` sınıfı liste kutusunda depolanır ve ListBox'ın arayacağı `ToString` işlevi gerekir aşırı `ToString` işlevi. Aşağıdaki kodu ekleyin *TodoItem.cs*Oluşturucu sonra ve sınıf bitmeden önce.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  İçinde *TodoWindowControl.xaml.cs*, saptama yöntemleri ekleme `TodoWindowControl` sınıfının `CheckForError` ve `UpdateList` yöntemleri. Bunları ProcessDialogChar sonra ve dosyanın sonundan önce yerleştirin.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError` Yöntemi üst nesne ile aynı ada sahip bir yöntemi çağırır ve bu yöntem herhangi bir hata oluşmuş ve doğru bir şekilde işlemek kontrol eder. `UpdateList` Yöntemi, üst denetimin liste kutusunda güncelleştirilir; yöntem olduğunda çağrılır `Name` ve `DueDate` bu sınıfı değişiklik özellikleri. Bunlar daha sonra uygulanacaktır.  
  
## <a name="integrate-into-the-properties-window"></a>Özellikler penceresine tümleştirin  
 Artık için bağlı ListBox yöneten kod yazma **özellikleri** penceresi.  
  
 Düğme değiştirmeli işleyici metin okuma, bir Todoıtem'ı oluşturmak için tıklayın ve liste kutusuna ekler.  
  
1.  Varolan `button1_Click` işlevi koduyla yeni bir Todoıtem'ı oluşturan ve liste kutusuna ekler. Çağrı `TrackSelection()`, hangi tanımlanması daha sonra.  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Tasarım görünümünde ListBox denetimini seçin. İçinde **özellikleri** penceresinde **olay işleyicileri** düğmesine tıklayın ve bulma **SelectionChanged** olay. Metin kutusunda doldurun **listBox_SelectionChanged**. Bunun yapılması, bir saplama SelectionChanged işleyici ekler ve olaya atar.  
  
3.  Uygulama `TrackSelection()` yöntemi. Alma olması gerektiğinden <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Hizmetleri, olan yaptığınız <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl tarafından erişilebilir. Aşağıdaki yöntemi ekleyin `TodoWindow` sınıfı:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Aşağıdaki using deyimlerini *TodoWindowControl.xaml.cs*:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  SelectionChanged işleyicisinde aşağıdaki gibi doldurun:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  Şimdi, ile tümleştirme sağlayan TrackSelection işlevi doldurun **özellikleri** penceresi. Kullanıcının liste kutusuna öğe ekler veya ListBox bir öğeye tıklamasının ardından bu işlev çağrılır. ListBox içeriği için bir SelectionContainer ekler ve için SelectionContainer geçirir **özellikleri** pencerenin <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> olay işleyicisi. TrackSelection hizmet kullanıcı arabirimini (UI) içinde seçilen nesneleri izler ve bunların özelliklerini görüntüler  
  
    ```csharp  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     Artık bir sınıf sahip olduğunuza göre **özellikleri** penceresi kullanabilir, facebook veya **özellikleri** penceresi araç penceresi. Kullanıcı araç penceresi, liste kutusunda bulunan bir öğeye tıkladığında **özellikleri** penceresi uygun şekilde güncelleştirilmelidir. Benzer şekilde, kullanıcı değiştiğinde bir ToDo öğesi içinde **özellikleri** penceresinde ilişkilendirilen öğenin güncelleştirilmelidir.  
  
7.  Şimdi UpdateList işlev kodu geri kalanını ekleyin *TodoWindowControl.xaml.cs*. Bırakma ve değiştirilen Todoıtem liste kutusundan yeniden eklemeniz gerekir.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Kodunuzu test edin. Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir.  
  
9. Açık **Araçları** > **seçenekleri** sayfası. Sol bölmede ToDo kategori görmeniz gerekir. Kategoriler alfabetik olarak listelenir, böylece altında Ts bakın.  
  
10. Üzerinde **Todo** seçenekler sayfası, görmeniz `DaysAhead` özelliğini **0**. Değiştirin **2**.  
  
11. Üzerinde **görünüm / diğer Windows** menüsünde, açık **TodoWindow**. Tür **EndDate** metin kutusuna tıklayıp **Ekle**.  
  
12. Liste kutusunda bir tarihi bugünden sonraki iki gün görmeniz gerekir.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Görev listesi öğeleri ve çıkış penceresine metin ekleme  
 İçin **görev listesi**, yeni bir nesne türü görev oluşturun ve ardından o görev nesnesine ekleme **görev listesi** çağırarak kendi `Add` yöntemi. Yazılacak **çıkış** penceresinde çağırmanızı kendi `GetPane` bölmesi nesnesi ve ardından elde etmek için yöntemi çağırın `OutputString` bölmesinde nesnesinin yöntemi.  
  
1.  İçinde *TodoWindowControl.xaml.cs*, `button1_Click` yöntemi almak için kod ekleyin **genel** bölmesinde **çıkış** (varsayılandır) penceresi ve ona yazın. Yöntem şu şekilde görünmelidir:  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Görev listesine öğe eklemek için bir iç içe geçmiş sınıf TodoWindowControl sınıfa eklemek için. İç içe geçmiş sınıf türetmek gerekli <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Sonuna aşağıdaki kodu ekleyin `TodoWindowControl` sınıfı.  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  Özel bir başvuru ekleyin `TodoTaskProvider` ve `CreateProvider()` yönteme `TodoWindowControl` sınıfı. Kod gibi görünmelidir:  
  
    ```csharp  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  Ekleme `ClearError()`, görev listesi temizler ve `ReportError()`, hangi ekler girişi görev listesine çok `TodoWindowControl` sınıfı.  
  
    ```csharp  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  Artık uygulama `CheckForErrors` yöntemini aşağıdaki gibi.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="try-it-out"></a>Deneyin  
  
1.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
2.  Açık **TodoWindow** (**görünümü** > **diğer Windows** > **TodoWindow**).  
  
3.  Bir şey metin kutusuna yazın ve ardından **Ekle**.  
  
     Bugün liste kutusuna eklendikten sonra 2 gün son tarihi. Herhangi bir hata oluşturulur ve **görev listesi** (**görünümü** > **görev listesi**) hiçbir girdilere sahip olmalıdır.  
  
4.  Ayarı artık değiştirmek **Araçları** > **seçenekleri** > **ToDo** gelen sayfasında **2** dön**0**.  
  
5.  İçinde başka bir tür **TodoWindow** ve ardından **Ekle** yeniden. Bu bir hata ve ayrıca bir giriş tetikler **görev listesi**.  
  
     Siz öğeler ekledikçe, başlangıç tarihini şimdi artı 2 gün için ayarlanır.  
  
6.  Üzerinde **görünümü** menüsünde tıklatın **çıkış** açmak için **çıkış** penceresi.  
  
     Her bir öğe eklemek, bir ileti görüntülenir dikkat **görev listesi** bölmesi.  
  
7.  Liste kutusu öğelerden birine tıklayın.  
  
     **Özellikleri** pencere öğesi iki özelliklerini görüntüler.  
  
8.  Bu özelliklerden birini değiştirin ve tuşuna **Enter**.  
  
     Öğeyi liste kutusunda güncelleştirilir.