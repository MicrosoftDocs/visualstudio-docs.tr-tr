---
title: WPF'ye giriş | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b29e4e241589134c8dfa5b94e997d6603b075ee3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826362"
---
# <a name="introduction-to-wpf"></a>WPF'ye Giriş
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF) masaüstü istemcisi, görsel olarak etkileyici kullanıcı deneyimleri ile Windows için uygulamalar oluşturmanıza olanak sağlar.  
  
 ![Contoso sağlık UI örnek](../designers/media/wpfintrofigure24.png "WPFIntroFigure24")  
  
 WPF setinin modern grafik donanımının yararlanmak için yerleşik bir çözüm bağımsız ve vektör tabanlı işleme altyapısıdır. WPF Extensible Application Markup Language (XAML), denetimleri, veri bağlama, düzen, 2B ve 3B grafikler, animasyon, stiller, şablonlar, belgeleri, medya, metin içeren bir uygulama geliştirme özellikleri kapsamlı bir dizi çekirdek genişletir ve Tipografi. WPF, .NET Framework, .NET Framework Sınıf Kitaplığı'nın diğer öğeleri bir araya getiren uygulamalar oluşturmanıza yardımcı olacak dahil edilir.  
  
 Bu genel bakışta yeni gelenlere yöneliktir ve temel işlevleri ve WPF kavramlarını ele alınmaktadır.  
  
##  <a name="Programming_with_WPF"></a> WPF ile programlama  
 WPF mevcut bir alt kümesini çoğunlukla bulunan .NET Framework türleri olarak <xref:System.Windows> ad alanı. ASP.NET ve Windows Forms gibi yönetilen teknolojilerini kullanarak uygulamaları .NET Framework ile daha önce geliştirdim, programlama deneyimi temel WPF tanımanız gerekir; sınıf örneği, özellikleri, yöntemleri çağırabilir ve tüm programlama dili, C# veya Visual Basic gibi en sevdiğiniz .NET kullanarak olayları işleyebilirsiniz.  
  
 WPF özellikleri ve olayları geliştiren ek programlama yapıları içerir: [bağımlılık özellikleri](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx) ve [yönlendirilmiş olaylar](https://msdn.microsoft.com/library/ms742806\(v=vs.100\).aspx).  
  
##  <a name="Markup_And_Codebehind"></a> Biçimlendirme ve arka plan kod  
 WPF, her ikisini de kullanarak bir uygulama geliştirmenize olanak tanır *biçimlendirme* ve *arka plan kod*, ASP.NET geliştiricilerinin aşina olmanız gereken bir deneyim. Genel olarak yönetilen bir programlama dili (arka plan kod) davranışını uygulamak için kullanırken uygulama görünümünü uygulamak için XAML biçimlendirme kullanın. Görünümünü ve davranışını ayrımı aşağıdaki faydaları sağlar:  
  
- Görünüm özgü biçimlendirme davranışını özgü kodla sıkı bir şekilde eşleşmediğinden dolayı geliştirme ve bakım maliyetlerinin azaltılır.  
  
- Tasarımcılar ile aynı anda uygulamanın davranışını uygulama geliştiriciler bir uygulamanın görünümünü uygulayabilirsiniz çünkü geliştirme daha verimli olur.  
  
- [Genelleştirme ve Yerelleştirme](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx) WPF uygulamaları basitleştirilir.  
  
  WPF biçimlendirmesi ve arka plan kod hakkında temel bilgiler verilmiştir.  
  
### <a name="markup"></a>Biçimlendirme  
 XAML bir uygulamanın görünümünü bildirimli olarak uygulamak için kullanılan XML-tabanlı işaretleme dilidir. Genellikle, windows, iletişim kutuları, sayfalar ve kullanıcı denetimleri oluşturma ve denetimleri, şekiller ve grafikler ile doldurmak için kullanılır.  
  
 Aşağıdaki örnek, tek bir düğme içeren bir pencere görünümünü uygulamak için XAML kullanır.  
  
```xaml  
<Window  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    Title="Window with Button"  
    Width="250" Height="100">  
  
  <!-- Add button to window -->  
  <Button Name="button">Click Me!</Button>  
  
</Window>  
```  
  
 Özellikle, bu XAML bir pencere ve bir düğmeyi kullanarak tanımlar `Window` ve `Button` öğeleri, sırasıyla. Her öğe gibi özniteliklerle yapılandırılmış `Window` öğenin `Title` pencerenin başlık çubuğu metni belirtmek için özniteliği. Çalışma zamanında WPF biçimlendirmesi WPF sınıfların örnekleri için tanımlanan öznitelikleri ve öğeleri dönüştürür. Örneğin, `Window` öğesi örneğine dönüştürülür <xref:System.Windows.Window> sınıfının <xref:System.Windows.Window.Title%2A> özelliği değerini `Title` özniteliği.  
  
 Aşağıdaki şekilde, önceki örnekte XAML tarafından tanımlanan kullanıcı arabirimi (UI) gösterilmektedir.  
  
 ![Bir düğme içeren bir pencere](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")  
  
 XAML XML tabanlı olduğundan, onu ile oluşturan kullanıcı Arabirimi olarak bilinen iç içe öğelerin bir hiyerarşideki derlendiğinden bir [öğe ağacı](https://msdn.microsoft.com/library/ms753391\(v=vs.100\).aspx). Öğe ağacı oluşturmak ve kullanıcı arabirimleri yönetmek için mantıksal ve kullanımı kolay bir yol sağlar.  
  
### <a name="code-behind"></a>Arka plan kod  
 Ana uygulamanın kullanıcı etkileşimlerine (örneğin, menü, araç çubuğunun veya düğmeyi tıklayarak) olaylarını işleme dahil olmak üzere, yanıt veren işlevselliği uygulamak için bir davranıştır ve iş mantığı ve veri erişim mantığı yanıtta çağırma. WPF içinde bu davranış, biçimlendirme ile ilişkili olan kod genellikle uygulanır. Bu tür kod arka plan kod bilinir. Aşağıdaki örnek önceki örneğe ve arka plan kod güncelleştirilmiş biçimlendirmeyi gösterir.  
  
```xaml  
<Window  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Class="SDKSample.AWindow"  
    Title="Window with Button"  
    Width="250" Height="100">  
  
  <!-- Add button to window -->  
  <Button Name="button" Click="button_Click">Click Me!</Button>  
  
</Window>  
```  
  
```csharp  
using System.Windows; // Window, RoutedEventArgs, MessageBox   
  
namespace SDKSample  
{  
    public partial class AWindow : Window  
    {  
        public AWindow()  
        {  
            // InitializeComponent call is required to merge the UI   
            // that is defined in markup with this class, including    
            // setting properties and registering event handlers  
            InitializeComponent();  
        }  
  
        void button_Click(object sender, RoutedEventArgs e)  
        {  
            // Show message box when button is clicked  
            MessageBox.Show("Hello, Windows Presentation Foundation!");  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
  
    Partial Public Class AWindow  
        Inherits System.Windows.Window  
  
        Public Sub New()  
  
            ' InitializeComponent call is required to merge the UI   
            ' that is defined in markup with this class, including    
            ' setting properties and registering event handlers  
            InitializeComponent()  
  
        End Sub   
  
        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
  
            ' Show message box when button is clicked  
            MessageBox.Show("Hello, Windows Presentation Foundation!")  
  
        End Sub   
  
    End Class   
  
End Namespace  
  
```  
  
 Bu örnekte, arka plan kod türetildiği bir sınıf uygulayan <xref:System.Windows.Window> sınıfı. `x:Class` Özniteliği işaretleme arka plan kod sınıfı ile ilişkilendirmek için kullanılır. `InitializeComponent` biçimlendirme ile arka plan kod sınıfı içinde tanımlanan kullanıcı Arabirimi birleştirmek için arka plan kod sınıfın oluşturucusundan çağrılır. (`InitializeComponent` uygulamanız, uygulamanız gerekmez neden olan yapılandırıldığında sizin için oluşturulur.) Birleşimi `x:Class` ve `InitializeComponent` , oluşturulduğunda, uygulamanızın doğru şekilde başlatıldığından emin olun. Arka plan kod sınıfı ayrıca bir olay işleyicisi düğmenin uygulayan <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay. Düğme tıklandığında, olay işleyicisi bir ileti kutusu çağırarak gösterir <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> yöntemi.  
  
 Düğme tıklandığında sonucu aşağıdaki şekilde gösterilmektedir.  
  
 ![Bir MessageBox](../designers/media/wpfintrofigure25.png "WPFIntroFigure25")  
  
##  <a name="Controls"></a> Denetimleri  
 Uygulama modeli tarafından sunulan kullanıcı deneyimleri oluşturulmuş denetimlerdir. WPF, "control" bir kategoriye bir pencere veya sayfa barındırılan WPF sınıfların geçerli bir genel bir terimdir ve bir kullanıcı arabirimine sahip bazı davranış uygulayın.  
  
 Daha fazla bilgi için [denetimleri](http://msdn.microsoft.com/library/3f255a8a-35a8-4712-9065-472ff7d75599).  
  
### <a name="wpf-controls-by-function"></a>İşleve göre WPF denetimleri  
 Yerleşik WPF denetimleri burada listelenir.  
  
-   **Düğmeler**: <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Primitives.RepeatButton>.  
  
-   **Veri görüntüsüne**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, ve <xref:System.Windows.Controls.TreeView>.  
  
-   **Tarih görüntüleme ve seçim**: <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker>.  
  
-   **İletişim kutuları**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, ve <xref:Microsoft.Win32.SaveFileDialog>.  
  
-   **Dijital Mürekkep**: <xref:System.Windows.Controls.InkCanvas> ve <xref:System.Windows.Controls.InkPresenter>.  
  
-   **Belgeler**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, ve <xref:System.Windows.Controls.StickyNoteControl>.  
  
-   **Giriş**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Controls.PasswordBox>.  
  
-   **Düzen**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, ve <xref:System.Windows.Controls.WrapPanel>.  
  
-   **Medya**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, ve <xref:System.Windows.Controls.SoundPlayerAction>.  
  
-   **Menüler**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, ve <xref:System.Windows.Controls.ToolBar>.  
  
-   **Gezinti**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, ve <xref:System.Windows.Controls.TabControl>.  
  
-   **Seçimi**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, ve <xref:System.Windows.Controls.Slider>.  
  
-   **Kullanıcı bilgilerini**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, ve <xref:System.Windows.Controls.ToolTip>.  
  
##  <a name="Input_And_Commanding"></a> Giriş ve komut vermeye genel  
 Denetimleri çoğunlukla algılar ve kullanıcı girişine yanıt verir. [WPF giriş sistem](https://msdn.microsoft.com/library/ms754010\(v=vs.100\).aspx) doğrudan ve yönlendirilmiş olaylar metin girişi, odağı yönetim ve fare konumlandırma desteklemek için kullanır.  
  
 Uygulamalar genellikle karmaşık giriş gereksinimlerine sahiptir. WPF sağlar bir [komut sistemi](https://msdn.microsoft.com/library/ms752308\(v=vs.100\).aspx) giriş kullanıcı eylemlerini söz konusu eylemlere yanıt veren kodundan ayırır.  
  
##  <a name="Layout"></a> Düzen  
 Bir kullanıcı arabirimi oluşturduğunuzda, konum ve boyut bir düzen oluşturmak için denetimlerinizin düzenleyin. Pencere boyutu değiştiğinde bunlara uyum sağlayabilir ve ayarlarını görüntülemek için herhangi bir düzen anahtarı gereksinimi var. Şu durumlarda bir düzende uyarlamak üzere kod yazmak için zorlama yerine WPF birinci sınıf, Genişletilebilir düzen sistemi için sunar.  
  
 Düzen sistemi göreli konumlandırma, hangi penceresi değişen benimsemesine ve koşullar görüntüleme olanağı artırır taşıdır. Ayrıca, düzen sistemi belirleme düzenini belirlemek için denetimler arasındaki yönetir. Anlaşma iki adımlı bir işlemdir: ilk olarak, bir denetimin hangi konum ve boyut gerektiriyor; üst bildirir İkinci olarak, üst denetimin sağlayabilirsiniz hangi alanı bildirir.  
  
 Temel WPF sınıflarıyla alt denetimler için Düzen sistemi kullanıma sunulur. Kılavuz, yığın ve takma gibi ortak düzenleri için çeşitli düzen denetimleri WPF içerir:  
  
- <xref:System.Windows.Controls.Canvas>: Kendi düzen alt denetimleri sağlar.  
  
- <xref:System.Windows.Controls.DockPanel>: Alt denetimler bölmesinin kenarlarını hizalanır.  
  
- <xref:System.Windows.Controls.Grid>: Alt denetimler, satırlar ve sütunlarla yerleştirilir.  
  
- <xref:System.Windows.Controls.StackPanel>: Dikey veya yatay alt denetimler yığılır.  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>: Alt denetimler sanallaştırılmış ve yatay veya dikey yönlendirilmiş olan tek bir satıra düzenlenir.  
  
- <xref:System.Windows.Controls.WrapPanel>: Alt denetimler soldan sağa doğru sırayla konumlandırılmış ve geçerli satırdaki boşluk izin verdiğinden daha fazla denetim olduğunda sonraki satıra kaydırılmış.  
  
  Aşağıdaki örnekte bir <xref:System.Windows.Controls.DockPanel> birkaç düzenlemek için <xref:System.Windows.Controls.TextBox> kontrol eder.  
  
  [!code-xml[IntroToWPFSnippets#LayoutMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/LayoutWindow.xaml#layoutmarkup)]  
  
  <xref:System.Windows.Controls.DockPanel> Alt sağlayan <xref:System.Windows.Controls.TextBox> bunları düzenlemek nasıl bildirmek için kontrol eder. Bunu yapmak için <xref:System.Windows.Controls.DockPanel> uygulayan bir <xref:System.Windows.Controls.DockPanel.Dock%2A> dock stilini belirtmek için bunların her biri izin vermek için alt denetimler için kullanıma sunulan özelliği.  
  
> [!NOTE]
>  Alt denetimler tarafından kullanılacak bir WPF yapısı için bir üst denetimi tarafından uygulanan bir özellik olarak adlandırılan bir [ekli özellik](https://msdn.microsoft.com/library/ms749011\(v=vs.100\).aspx).  
  
 Aşağıdaki şekilde, önceki örnekte XAML biçimlendirme sonucu gösterir.  
  
 ![DockPanel sayfa](../designers/media/wpfintrofigure11.png "WPFIntroFigure11")  
  
##  <a name="Data_Binding"></a> Veri bağlama  
 Çoğu uygulama, kullanıcılara görüntülemek ve veri düzenleme bulunmasını sağlamak için oluşturulur. WPF uygulamaları için depolama ve veri erişim iş zaten için SQL Server ve ADO .NET gibi teknolojileri tarafından sağlanır. Verilere nasıl erişildiği ve yönetilen nesnelere bir uygulamanın yüklü WPF uygulamaları için sabit çalışmaya başladıktan sonra. Esas olarak, bu iki şey içerir:  
  
1. Verileri veri burada görüntülenir ve düzenlenebildiği denetimlere yönetilen nesneleri kopyalama.  
  
2. Denetimleri kullanarak verilerde yapılan değişiklikler yönetilen nesnelere kopyalandığından emin olma.  
  
   Uygulama geliştirmeyi kolaylaştırmak için WPF otomatik olarak bu adımları gerçekleştirmek için veri bağlama altyapısı sağlar. Veri bağlama altyapısı temel birimidir <xref:System.Windows.Data.Binding> sınıfı, işi olduğu bir denetimi (bağlama hedefi) bağlamak için bir veri nesnesine (bağlama kaynağı). Bu ilişki, aşağıdaki şekilde gösterilmiştir.  
  
   ![Temel veri bağlama diyagramı](../designers/media/databindingmostbasic.png "DataBindingMostBasic")  
  
   Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.Windows.Controls.TextBox> özel bir örneğine `Person` nesne. `Person` Uygulaması, aşağıdaki kodda gösterilmiştir.  
  
   [!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/Person.cs#personclasscode)]
   [!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/Person.vb#personclasscode)]  
  
   Aşağıdaki biçimlendirmede bağlar <xref:System.Windows.Controls.TextBox> özel bir örneğine `Person` nesne.  
  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP1](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup1)]  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP2](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup2)]  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP3](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup3)]  
  
   [!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml.cs#databindingcodebehind)]
   [!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/DataBindingWindow.xaml.vb#databindingcodebehind)]  
  
   Bu örnekte, `Person` sınıfı gerideki kod örneği ve veri bağlamı olarak ayarlanmış olan `DataBindingWindow`. Biçimlendirme içinde <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox> bağlı `Person.Name` özelliği (kullanarak "`{Binding ... }`" XAML sözdizimi). WPF bağlama için bu XAML söyler <xref:System.Windows.Controls.TextBox> denetimini `Person` depolanan nesne <xref:System.Windows.FrameworkElement.DataContext%2A> penceresinin özelliği.  
  
   WPF veri bağlama altyapısı, sıralama, filtreleme ve gruplandırma doğrulama içeren ek destek sağlar. Ayrıca, veri bağlama standart WPF denetimi tarafından görüntülenen kullanıcı arabirimi uygun değilse, bağlı veri için özel kullanıcı arabirimi oluşturmak üzere veri şablonları destekler.  
  
   Daha fazla bilgi için [Data Binding Overview](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx).  
  
##  <a name="Graphics"></a> Grafik  
 WPF kapsamlı, ölçeklenebilir ve esnek bir aşağıdaki avantajlara sahip grafik özellikler kümesi sağlar:  
  
-   **Çözüm bağımsız ve CİHAZDAN bağımsız grafik**. WPF Grafik sistemdeki temel ölçü olan 1 cihaz bağımsız piksel/96 inç gerçek bağımsız olarak, ekran çözünürlüğü ve çözümleme bağımsız ve CİHAZDAN bağımsız işleme için bir temel sunar. Her CİHAZDAN bağımsız piksel üzerinde işlediği sistemin nokta / inç (dpi) ayarını eşleşecek şekilde otomatik olarak ölçeklendirir.  
  
-   **Gelişmiş duyarlılık**. WPF koordinat sistemini tek duyarlıklı yerine çift duyarlıklı kayan noktalı sayıların ile ölçülür. Dönüşümler ve saydamlık değerleri de çift duyarlık ifade edilir. WPF ayrıca geniş renk skalası (scRGB) destekler ve farklı bir renk boşlukları girişleri yönetmek için tümleşik destek sağlar.  
  
-   **Grafikler ve animasyon Gelişmiş**. WPF grafik programlama animasyon sahneler yöneterek basitleştirir; Sahne işleme, işleme döngüler ve çift doğrusal enterpolasyon hakkında endişelenmenize gerek yoktur. Ayrıca, WPF, isabet sınaması ve tam alfa birleştirme desteği sağlar.  
  
-   **Donanım hızlandırma**. WPF Grafik sistem CPU kullanımını en aza indirmek için grafik donanımının yararlanır.  
  
### <a name="2-d-shapes"></a>2B şekiller  
 WPF genel vektör çizimli 2B şekiller, dikdörtgenler ve üç nokta simgesini aşağıdaki çizimde gösterildiği gibi bir kitaplık sağlar.  
  
 ![Elips ve dikdörtgen](../designers/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Bir ilgi çekici şekillerinin değil yalnızca görüntü için oldukları bir özelliktir; şekiller, klavye ve fare girişi gibi denetimleri, beklediğiniz özelliklerin çoğunu uygulayın. Aşağıdaki örnekte gösterildiği <xref:System.Windows.UIElement.MouseUp> olayı bir <xref:System.Windows.Shapes.Ellipse> işlenen.  
  
 [!code-xml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml#handleellipsemouseupeventmarkup)]  
  
 [!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml.cs#handleellipsemouseupeventcodebehind)]
 [!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/EllipseEventHandlingWindow.xaml.vb#handleellipsemouseupeventcodebehind)]  
  
 Aşağıdaki şekilde önceki kod tarafından üretilen gösterilmektedir.  
  
 ![Metin içeren bir pencere "elips tıkladığınız&#33;"](../designers/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Daha fazla bilgi için [şekiller ve temel çizimlere WPF genel bakışında](https://msdn.microsoft.com/library/ms747393\(v=vs.100\).aspx).  
  
### <a name="2-d-geometries"></a>2B geometri  
 WPF tarafından sağlanan 2B şekiller temel şekilleri standart kümesini içerir. Ancak, özelleştirilmiş kullanıcı arabirimi tasarımı kolaylaştırmak için özel şekiller oluşturmanız gerekebilir. Bu amaçla WPF geometriler sağlar. Aşağıdaki şekil, geometri doğrudan çizilmiş, fırça olarak kullanılan veya küçük diğer şekiller ve denetimler için kullanılan özel bir şekil oluşturmak için kullanımını gösterir.  
  
 <xref:System.Windows.Shapes.Path> nesneler, kapalı veya açık şekiller, birden çok şekil ve hatta eğri şekiller çizmek için kullanılabilir.  
  
 <xref:System.Windows.Media.Geometry> nesneleri kırpması, isabet sınaması ve 2B grafik verilerini işleme için kullanılabilir.  
  
 ![Bir yol çeşitli kullanımları](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Daha fazla bilgi için [geometriye genel bakış](https://msdn.microsoft.com/library/ms751808\(v=vs.100\).aspx)  
  
### <a name="2-d-effects"></a>2B efektler  
 Gradyan, bit eşlemler, çizimleri, videolar, döndürme, ölçeklendirme ve eğriltme boyama gibi görsel efektler WPF 2B yeteneklerinin bir alt kümesini içerir. Bu tüm fırçalar ile elde edilir; Aşağıdaki şekilde, bazı örnekler gösterilmektedir.  
  
 ![Farklı fırçalar gösterimi](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Daha fazla bilgi için [WPF fırçalarına genel bakış](https://msdn.microsoft.com/library/aa970904\(v=vs.100\).aspx).  
  
### <a name="3-d-rendering"></a>3B işleme  
 WPF ile 2B grafikler daha etkileyici ve ilgi çekici kullanıcı arabirimleri oluşturmaya izin vermek için tümleştirme 3B işleme özelliklerini de içerir. Örneğin, aşağıdaki şekilde 3B şekilleri üzerinde işlenen 2B görüntüleri gösterilmektedir.  
  
 ![Visual3D örnek ekran görüntüsünde](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Daha fazla bilgi için [3B Grafiklere Genel Bakış](https://msdn.microsoft.com/library/ms747437\(v=vs.100\).aspx).  
  
##  <a name="Animation"></a> Animasyon  
 WPF animasyonu destek sağlar, arttıkça, sallayın denetimleri yaptığınız döndürme ve ilgi çekici oluşturmak için fade geçişleri ve daha fazla sayfa. Çoğu WPF sınıf animasyon, hatta özel sınıflar. Aşağıdaki şekilde basit animasyon gösterilmiştir.  
  
 ![Animasyonlu bir küp görüntülerini](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Daha fazla bilgi için [animasyona genel bakış](https://msdn.microsoft.com/library/ms752312\(v=vs.100\).aspx).  
  
##  <a name="Media"></a> Medya  
 Zengin içerik iletmek için bir görsel ve işitsel ortam genelindeki yoludur. WPF, görüntü, video ve ses için özel desteği sağlar.  
  
### <a name="images"></a>Görüntüler  
 Görüntüleri çoğu uygulama için ortak olan ve WPF kullanabilmesi için birçok yol sağlar. Aşağıdaki şekilde, bir kullanıcı arabirimi ile küçük resimlerini içeren bir liste kutusu gösterilmektedir. Bir küçük resim seçildiğinde, tam boyutlu görüntü de gösterilir.  
  
 ![Küçük resimler ve tam&#45;resim boyutu](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")  
  
 Daha fazla bilgi için [Imaging genel bakış](https://msdn.microsoft.com/library/ms748873\(v=vs.100\).aspx).  
  
### <a name="video-and-audio"></a>Video ve ses  
 <xref:System.Windows.Controls.MediaElement> Denetimidir video ve ses çalabilir ve özel media Player temel olması için yeterince esnektir. Bir medya yürütücüsü aşağıdaki XAML biçimlendirme uygular.  
  
 [!code-xml[IntroToWPFSnippets#MediaElementMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/MediaElementWindow.xaml#mediaelementmarkup)]  
  
 Aşağıdaki şekilde gösterildiği penceresinde <xref:System.Windows.Controls.MediaElement> denetimi sürüyor.  
  
 ![Ses ve video MediaElement denetimi](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")  
  
 Daha fazla bilgi için [WPF Grafik, animasyon ve medya genel bakış](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx).  
  
##  <a name="Text_and_Typography"></a> Metin ve tipografi  
 Yüksek kaliteli metin işleme kolaylaştırmak için WPF aşağıdaki özellikleri sunmaktadır:  
  
- OpenType yazı tipi desteği.  
  
- ClearType geliştirmeleri.  
  
- Donanım hızlandırma yararlanır, yüksek performans.  
  
- Tümleştirme ortamı, grafikler ve animasyon metin.  
  
- Destek ve geri dönüş mekanizması uluslararası yazı tipi.  
  
  Grafik metin tümleştirmesiyle bir örnek, aşağıdaki şekilde metin düzenlemelerinin uygulaması gösterilmektedir.  
  
  ![Çeşitli metin süslemeleri metin](../designers/media/wpfintrofigure23.png "WPFIntroFigure23")  
  
  Daha fazla bilgi için [tipografi Windows Presentation Foundation'da](https://msdn.microsoft.com/library/ms742190\(v=vs.100\).aspx).  
  
##  <a name="WPF_Customization"></a> WPF uygulamaları özelleştirme  
 Bu noktaya kadar uygulamaları geliştirmek için çekirdek WPF yapı taşlarını öğrendiniz. Uygulama modeli, barındırmak ve çoğunlukla denetimlerden oluşan uygulama içerik teslim etmek için kullanın. Bir kullanıcı arabirimi denetimleri düzenlemesini basitleştirmek ve pencere boyutunu değişiklikleri karşılaşıldığında düzenlemeyi korunduğundan emin olmak ve ayarlarını görüntülemek için WPF düzen sistemi kullanın. Uygulamaların çoğu verilerle etkileşimde bulunmak kullanıcıların olduğundan, kullanıcı arabirimi ile veri tümleştirme iş miktarını azaltmaya yönelik veri bağlama kullanın. Uygulamanızın görünümünü geliştirmek için WPF tarafından sağlanan kapsamlı grafikler, animasyon ve medya kullanın.  
  
 Genellikle, yine de temellerini oluşturma ve kullanıcı deneyimi görsel olarak etkileyici tamamen ayrı yönetmek için yeterli değildir. Standart WPF denetimleri kullanarak, uygulamanızın istediğiniz görünümü ile tümleştirmemek. Veri en etkili şekilde görüntülenmeyebilir. Varsayılan Görünüm ve yapısını için Windows temaları, uygulamanızın genel kullanıcı deneyimini uygun olmayabilir. Birçok yolla sunu teknolojisi olarak herhangi bir genişletilebilirlik türden görsel genişletilebilirlik gerekir.  
  
 Bu nedenle, WPF çeşitli denetimleri, Tetikleyiciler, Denetim ve veri şablonları, stilleri, kullanıcı arabirimi kaynaklarını ve temalar ve kaplamaları için zengin bir içerik modeli de dahil olmak üzere, benzersiz kullanıcı deneyimleri oluşturmak için bir mekanizma sağlar.  
  
### <a name="content-model"></a>İçerik modeli  
 WPF denetimleri çoğunu ana amacı, içerik görüntülemektir. WPF içinde denetiminin içeriğini oluşturan öğelerin sayısı ve türü başvurduğu denetimin *içerik modeli*. Bazı denetimler, tek öğe ve içerik türünü içerebilir; Örneğin, içeriği bir <xref:System.Windows.Controls.TextBox> atanan bir dize değeridir <xref:System.Windows.Controls.TextBox.Text%2A> özelliği. Aşağıdaki örnek, içeriği ayarlar bir <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup1)]  
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup2)]  
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup3)]  
  
 Aşağıdaki şekilde sonucu gösterir.  
  
 ![Metin içeren bir metin kutusu denetimi](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")  
  
 Diğer denetimleri, ancak içerik farklı türlerde birden çok öğe içerebilir; içeriği bir <xref:System.Windows.Controls.Button>tarafından belirtilen <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği öğeleri düzen denetimleri, metin, resimler ve şekiller de dahil olmak üzere çeşitli içerebilir. Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.Button> içeren içeriğe sahip bir <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>ve <xref:System.Windows.Controls.MediaElement>.  
  
 [!code-xml[IntroToWPFSnippets#ButtonContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup1)]  
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup2)]  
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup3)]  
  
 Aşağıdaki şekil bu düğme içeriğini gösterir.  
  
 ![Birden çok içerik türlerini içeren bir düğmesi](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")  
  
 Çeşitli denetimler tarafından desteklenen içerik türleri hakkında daha fazla bilgi için bkz. [WPF içerik modeli](https://msdn.microsoft.com/library/bb613548\(v=vs.100\).aspx).  
  
### <a name="triggers"></a>Tetikleyiciler  
 XAML biçimlendirme ana amacı, bir uygulamanın görünümünü uygulamak için olsa da, XAML bazı yönlerini uygulamanın davranışı uygulamak için kullanabilirsiniz. Kullanıcı denetimine göre bir uygulamanın görünümünü değiştirmek için Tetikleyiciler kullanımı bir örnektir. Daha fazla bilgi için [stil ve şablon oluşturma](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx).  
  
### <a name="control-templates"></a>Denetim şablonları  
 WPF denetimleri için varsayılan kullanıcı arabirimleri genellikle, diğer denetimler ve şekillerden şekiller oluşturulur. Örneğin, bir <xref:System.Windows.Controls.Button> her ikisi de oluşur <xref:Microsoft.Windows.Themes.ButtonChrome> ve <xref:System.Windows.Controls.ContentPresenter> kontrol eder. <xref:Microsoft.Windows.Themes.ButtonChrome> Standart düğme görünümünü sağlar ancak <xref:System.Windows.Controls.ContentPresenter> düğmenin içeriği tarafından belirtilen görüntüler <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği.  
  
 Bazen bir denetimin varsayılan görünümünü uygulamanın genel görünümünü incongruent olabilir. Bu durumda, kullanabileceğiniz bir <xref:System.Windows.Controls.ControlTemplate> içeriği ve davranışını değiştirmeden kullanıcı arabirimi denetimin görünümünü değiştirmek için.  
  
 Örneğin, aşağıdaki örnek görünümünü değiştirmek nasıl gösterir bir <xref:System.Windows.Controls.Button> kullanarak bir <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml#buttoncontroltemplatewindowmarkup)]  
  
 [!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml.cs#buttoncontroltemplatewindowcodebehind)]
 [!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/ControlTemplateButtonWindow.xaml.vb#buttoncontroltemplatewindowcodebehind)]  
  
 Bu örnekte, varsayılan düğme kullanıcı arabirimi ile değiştirilmiştir bir <xref:System.Windows.Shapes.Ellipse> , koyu mavi bir kenarlık varsa ve kullanılarak doldurulan bir <xref:System.Windows.Media.RadialGradientBrush>. <xref:System.Windows.Controls.ContentPresenter> Denetimi içeriğini görüntüler <xref:System.Windows.Controls.Button>, "Me tıklayın!" Zaman <xref:System.Windows.Controls.Button> tıklandığında <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı bir parçası olarak hala oluşturulur <xref:System.Windows.Controls.Button> denetimin varsayılan davranışını. Sonuç, aşağıdaki şekilde gösterilir.  
  
 ![Bir elips düğmesine ve ikinci bir pencere](../designers/media/wpfintrofigure2.png "WPFIntroFigure2")  
  
### <a name="data-templates"></a>Veri şablonları  
 Bir denetim şablonu bir denetimin görünümünü belirtmenize olanak tanır ancak bir veri şablonu bir denetimin içeriğinin görünümünü belirtmenize olanak sağlar. Veri şablonları nasıl bağlı veri geliştirmek için kullanılan sık görüntülenir. Aşağıdaki şekil, varsayılan görünümünü gösterir. bir <xref:System.Windows.Controls.ListBox> koleksiyonuna bağlı `Task` nesneleri, her görev sahip olduğu bir ad, açıklama ve öncelik.  
  
 ![Varsayılan görünüm içeren bir liste kutusu](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")  
  
 Gelen beklediğiniz gibi varsayılan görünümü, bir <xref:System.Windows.Controls.ListBox>. Ancak, her görevin varsayılan görünümünü yalnızca görev adını içerir. Görev adı, açıklama ve öncelik, varsayılan görünümünü göstermek için <xref:System.Windows.Controls.ListBox> denetimin ilişkili liste öğelerini kullanarak değiştirilmeli bir <xref:System.Windows.DataTemplate>. Aşağıdaki XAML gibi tanımlayan bir <xref:System.Windows.DataTemplate>, uygulandığı her görev için kullanarak <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özniteliği.  
  
 [!code-xml[IntroToWPFSnippets#DataTemplateMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup1)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup2)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup3)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup4)]  
  
 Aşağıdaki şekil, bu kod etkisini gösterir.  
  
 ![Veri şablonu kullanan simgesiz liste kutusu](../designers/media/wpfintrofigure19.png "WPFIntroFigure19")  
  
 Unutmayın <xref:System.Windows.Controls.ListBox> ; genel görünümünü ve davranışını korudu yalnızca liste kutusu tarafından görüntülenen içerik görünümünü değişti.  
  
 Daha fazla bilgi için [veri şablonu oluşturmaya genel bakış](https://msdn.microsoft.com/library/ms742521\(v=vs.100\).aspx).  
  
### <a name="styles"></a>Stilleri  
 Stilleri, geliştiricilerin ve tasarımcıların ürün için belirli bir görünümünü standart hale getirmek etkinleştirin. WPF sağlar temeli olan güçlü bir stil modeli, <xref:System.Windows.Style> öğesi. Aşağıdaki örnek, arka plan rengini ayarlar bir stil oluşturur. her <xref:System.Windows.Controls.Button> pencere üzerindeki `Orange`.  
  
 [!code-xml[IntroToWPFSnippets#StyleMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup1)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup2)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup3)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup4)]  
  
 Bu stil tüm hedeflediğinden <xref:System.Windows.Controls.Button> aşağıdaki şekilde gösterildiği gibi penceresindeki tüm düğmeler stili denetimleri otomatik olarak uygulanır.  
  
 ![Turuncu iki düğme](../designers/media/wpfintrofigure20.png "WPFIntroFigure20")  
  
 Daha fazla bilgi için [stil ve şablon oluşturma](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx).  
  
### <a name="resources"></a>Kaynaklar  
 Uygulamaya denetimler şablonları, veri şablonları ve stilleri denetlemek için yazı tipi ve arka plan renkleri her şeyi içeren aynı görünümünü paylaşmalıdır. WPF'nin desteği için kullanıcı arabirimi kaynaklarını tek bir konumda yeniden kullanım için bu kaynakları kapsamak için kullanabilirsiniz.  
  
 Aşağıdaki örnek, tarafından paylaşılan ortak bir arka plan rengi tanımlar. bir <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Label>.  
  
 [!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup1)]  
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup2)]  
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup3)]  
  
 Bu örnekte kullanarak arka plan rengi kaynağı uygulayan `Window.Resources` özellik öğesi. Bu kaynak için tüm alt kullanılabilir <xref:System.Windows.Window>. Birçok kaynak kapsamlar, aşağıdakiler de dahil oldukları çözümlenen sırayla listelenir:  
  
1. Tek bir denetim (devralınan kullanarak <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> özelliği).  
  
2. A <xref:System.Windows.Window> veya <xref:System.Windows.Controls.Page> (Ayrıca devralınan kullanarak <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> özelliği).  
  
3. Bir <xref:System.Windows.Application> (kullanarak <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> özelliği).  
  
   Çeşitli kapsamlar, tanımlamak ve kaynaklarınızı paylaşım yolu esneklik sağlar.  
  
   Kaynaklarınızı doğrudan belirli bir kapsamla ilişkilendirmeye alternatif olarak, ayrı bir kullanarak bir veya daha fazla kaynak paketleyebilirsiniz <xref:System.Windows.ResourceDictionary> bir uygulamanın diğer bölümlerini başvurulabilir. Örneğin, aşağıdaki örnek, bir kaynak sözlüğünde varsayılan arka plan rengi tanımlar.  
  
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup1)]  
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup2)]  
  
   Aşağıdaki örnek, önceki örnekte, bir uygulama arasında paylaşılacak şekilde tanımlanmış kaynak sözlüğü başvurur.  
  
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup1)]  
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup2)]  
  
   Kaynak ve kaynak sözlükleri temalar ve dış görünümleri için destek WPF temelidir.  
  
   Daha fazla bilgi için [kaynaklarına genel bakış](https://msdn.microsoft.com/library/ms750613\(v=vs.100\).aspx).  
  
### <a name="custom-controls"></a>Özel denetimler  
 WPF özelleştirme desteği çok sayıda sağlasa da, burada varolan WPF denetimlerinin uygulamanız ya da kullanıcılarının gereksinimlerini karşılamayan durumlarla karşılaşabilirsiniz. Bu durum ortaya çıkabilir olduğunda:  
  
- Varolan WPF uygulamaları Görünüm ve yapısını özelleştirerek gerektiren kullanıcı arabirimi oluşturulamıyor.  
  
- İhtiyaç duyduğunuz davranışı desteklenmiyor (veya kolayca desteklenmez) varolan WPF uygulamaları tarafından.  
  
  Bu noktada, ancak yeni bir denetim oluşturmak için üç WPF model birinin yararlanabilirsiniz. Her model, belirli bir senaryoyu hedefler ve belirli WPF temel sınıftan türetilen özel denetim gerektirir. Üç model aşağıda listelenmiştir:  
  
- **Kullanıcı denetimi modeli**. Özel denetim türetildiği <xref:System.Windows.Controls.UserControl> ve bir veya daha fazla diğer denetimlerden oluşur.  
  
- **Denetim modeli**. Özel denetim türetildiği <xref:System.Windows.Controls.Control> ve WPF denetimleri çoğunu gibi şablonları kullanarak görünümlerini davranışlarını ayırmak uygulamaları oluşturmak için kullanılır. Öğesinden türetme <xref:System.Windows.Controls.Control> kullanıcı denetimleri, ancak daha fazla çaba gerektirebilir, özel bir kullanıcı arabirimi oluşturmak için daha fazla özgürlük tanır.  
  
- **Framework öğesi modeli**. Özel denetim türetildiği <xref:System.Windows.FrameworkElement> görünümünü (şablonları değil) özel işleme mantığı tarafından tanımlanan zaman.  
  
  Aşağıdaki örnek bir özel sayısal gösterir yukarı/aşağı öğesinden türetilen denetim <xref:System.Windows.Controls.UserControl>.  
  
  [!code-xml[IntroToWPFSnippets#UserControlMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml#usercontrolmarkup)]  
  
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind1)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind1)]  
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind2)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind2)]  
  
  
 Kullanıcı denetimine eklemek için gerekli olan XAML sonraki örnekte bir <xref:System.Windows.Window>.  
  
 [!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup1)]  
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup2)]  
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup3)]  
  
 Aşağıdaki şekil gösterir `NumericUpDown` denetiminde barındırılan bir <xref:System.Windows.Window>.  
  
 ![Özel bir UserControl](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")  
  
 Özel denetimler hakkında daha fazla bilgi için bkz. [denetim yazmaya genel bakış](https://msdn.microsoft.com/library/ms745025\(v=vs.100\).aspx).  
  
##  <a name="WPF_Best_Practices"></a> WPF en iyi uygulamalar  
 Bir geliştirme platformu olduğu gibi WPF istenen sonucu elde etmek için yol çeşitli içinde kullanılabilir. WPF emin olmanın bir yolu olarak uygulamalar gerekli bir kullanıcı deneyimi sağlar ve İzleyici genel karşılayacak, erişilebilirlik, Genelleştirme ve yerelleştirme ve performans için en iyi var. önerilir. Daha fazla bilgi için aşağıdakilere bakın:  
  
-   [En iyi erişilebilirlik uygulamaları](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)en iyi erişilebilirlik uygulamaları  
  
-   [WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)  
  
-   [WPF Uygulama Performansını İyileştirme](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)  
  
-   [Windows Presentation Foundation güvenliği](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)  
  
##  <a name="Summary"></a> Özeti  
 WPF, istemci uygulamalarını görsel olarak etkileyici çeşitli oluşturmaya yönelik bir kapsamlı sunu teknolojisidir. Bu giriş, WPF anahtar özelliklerini göz sağlamıştır.  
  
 Sonraki adım, WPF uygulamaları oluşturmaktır!  
  
 Bunları derleme sırasında geri Yenileyici bu giriş için temel özellikler ve bu bölümde ele alınan özelliklerin daha ayrıntılı kapsamını başvurularını bulmak için dönebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF ile çalışmaya başlama](../designers/getting-started-with-wpf.md)   
 [Windows Presentation Foundation ile modern masaüstü uygulamaları oluşturun](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)   
 [Windows Presentation Foundation](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)



