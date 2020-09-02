---
title: WPF 'ye giriş | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b33c558187fd32ef7cbd420dce8d627ddc944d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664343"
---
# <a name="introduction-to-wpf"></a>WPF'ye Giriş
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF), görsel açıdan etkileyici kullanıcı deneyimleri sayesinde Windows için masaüstü istemci uygulamaları oluşturmanıza olanak tanır.

 ![Contoso sağlık Kullanıcı arabirimi örneği](../designers/media/wpfintrofigure24.png "WPFIntroFigure24")

 WPF 'nin çekirdeği, modern grafik donanımının avantajlarından yararlanmak için oluşturulmuş, çözünürlükten bağımsız ve vektör tabanlı bir işleme altyapısıdır. WPF, Extensible Application Markup Language (XAML), denetimler, veri bağlama, düzen, 2-D ve 3-b grafikler, animasyon, stiller, şablonlar, belgeler, medya, metin ve tipografi içeren kapsamlı bir uygulama geliştirme özellikleri kümesiyle Core 'u genişletir. WPF .NET Framework eklenmiştir, böylece .NET Framework sınıf kitaplığının diğer öğelerini içeren uygulamalar oluşturabilirsiniz.

 Bu genel bakış, Newcomers 'e yöneliktir ve WPF 'in temel yeteneklerini ve kavramlarını ele alır.

## <a name="programming-with-wpf"></a><a name="Programming_with_WPF"></a> WPF ile programlama
 WPF, ad alanında bulunan en çok bölüm için .NET Framework türlerin bir alt kümesi olarak mevcuttur <xref:System.Windows> . Daha önce ASP.NET ve Windows Forms gibi yönetilen teknolojileri kullanarak .NET Framework uygulamalar oluşturduysanız, temel WPF programlama deneyimi tanıdık gelmelidir; C# veya Visual Basic gibi en sevdiğiniz .NET programlama dilini kullanarak sınıfları örnekleyin, özellikleri ayarlar, yöntemleri çağırır ve olayları işleyebilirsiniz.

 WPF, özellikleri ve olayları geliştiren ek programlama yapılarını içerir: [bağımlılık özellikleri](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx) ve [yönlendirilmiş olaylar](https://msdn.microsoft.com/library/ms742806\(v=vs.100\).aspx).

## <a name="markup-and-code-behind"></a><a name="Markup_And_Codebehind"></a> Biçimlendirme ve arka plan kodu
 WPF, ASP.NET geliştiricilerin tanıdık olması gereken bir deneyim olan hem *biçimlendirme* hem de *arka plan kodu*kullanarak bir uygulama geliştirmenize olanak tanır. Genellikle XAML işaretlemesini kullanarak, davranışını uygulamak için yönetilen programlama dillerini (arka plan kod) kullanırken bir uygulamanın görünümünü uygulayın. Bu görünüm ve davranışın ayrımı aşağıdaki avantajlara sahiptir:

- Görünüme özgü biçimlendirme davranışa özgü kodla sıkı bir şekilde bağlı olmadığından geliştirme ve bakım maliyetleri azaltılır.

- Geliştiriciler uygulamanın davranışını uygulayan geliştiricilerle aynı anda bir uygulamanın görünümünü uygulayabildiğinden geliştirme daha etkilidir.

- WPF uygulamaları için [Genelleştirme ve yerelleştirme](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx) basitleştirilmiştir.

  WPF biçimlendirme ve arka plan kodu için kısa bir giriş aşağıda verilmiştir.

### <a name="markup"></a>İşaretleme
 XAML, uygulamanın görünümünü bildirimli olarak uygulamak için kullanılan XML tabanlı bir biçimlendirme dilidir. Genellikle Windows, iletişim kutuları, sayfalar ve Kullanıcı denetimleri oluşturmak ve bunları denetimler, şekiller ve grafiklerle doldurmaları için kullanılır.

 Aşağıdaki örnek, tek bir düğme içeren bir pencerenin görünümünü uygulamak için XAML kullanır.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

 Özellikle, bu XAML `Window` sırasıyla ve öğelerini kullanarak bir pencere ve bir düğme tanımlar `Button` . Her öğe, `Window` `Title` pencerenin başlık çubuğu metnini belirtmek için öğenin özniteliği gibi özniteliklerle yapılandırılır. Çalışma zamanında WPF, biçimlendirme içinde tanımlanan öğeleri ve öznitelikleri WPF sınıflarının örneklerine dönüştürür. Örneğin, `Window` öğesi <xref:System.Windows.Window> <xref:System.Windows.Window.Title%2A> özelliği özniteliğin değeri olan bir sınıfının örneğine dönüştürülür `Title` .

 Aşağıdaki şekilde, önceki örnekte XAML tarafından tanımlanan Kullanıcı arabirimi (UI) gösterilmektedir.

 ![Düğme içeren pencere](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")

 XAML, XML tabanlı olduğundan, onunla oluşturduğunuz Kullanıcı arabirimi bir [öğe ağacı](https://msdn.microsoft.com/library/ms753391\(v=vs.100\).aspx)olarak bilinen iç içe geçmiş öğelerin hiyerarşisinde toplanır. Öğe ağacı, Usıs oluşturmak ve yönetmek için mantıksal ve sezgisel bir yol sağlar.

### <a name="code-behind"></a>Arka plan kodu
 Bir uygulamanın ana davranışı, olayları işleme (örneğin, bir menü, araç çubuğu veya düğme) ve yanıt olarak iş mantığı ve veri erişim mantığını çağırma dahil olmak üzere kullanıcı etkileşimlerine yanıt veren işlevselliği uygulamaktır. WPF 'de, bu davranış genellikle biçimlendirme ile ilişkili kodda uygulanır. Bu tür bir kod, arka plan kodu olarak bilinir. Aşağıdaki örnek, önceki örnekteki ve arka plan kodundaki güncelleştirilmiş biçimlendirmeyi gösterir.

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
    public partial class AWindow : Window
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

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace

```

 Bu örnekte, arka plan kodu sınıfından türetilen bir sınıf uygular <xref:System.Windows.Window> . `x:Class`Özniteliği, biçimlendirmeyi arka plan kod sınıfıyla ilişkilendirmek için kullanılır. `InitializeComponent` arka plan kod sınıfı ile biçimlendirme içinde tanımlanan Kullanıcı arabirimini birleştirmek için, kod arkasındaki sınıfın oluşturucusundan çağrılır. ( `InitializeComponent` uygulamanızın oluşturulduğu zaman sizin için oluşturulur, bu nedenle el ile uygulamanız gerekmez.) Birleşimi ve uygulamanızın `x:Class` `InitializeComponent` oluşturulduğu her seferinde doğru başlatıldığından emin olun. Arka plan kod sınıfı, düğmenin olayı için bir olay işleyicisi de uygular <xref:System.Windows.Controls.Primitives.ButtonBase.Click> . Düğmeye tıklandığında, olay işleyicisi yöntemini çağırarak bir ileti kutusu gösterir <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> .

 Aşağıdaki şekilde, düğme tıklandığında sonuç gösterilmektedir.

 ![Bir MessageBox](../designers/media/wpfintrofigure25.png "WPFIntroFigure25")

## <a name="controls"></a><a name="Controls"></a> Kontrollerini
 Uygulama modeli tarafından sunulan kullanıcı deneyimleri, oluşturulan denetimlerdir. WPF 'de, "Control" bir pencere veya sayfada barındırılan bir WPF sınıfları kategorisi için geçerli olan ve bir kullanıcı arabirimine sahip olan ve bazı davranışları uygulayan bir şemsiye terimidir.

 Daha fazla bilgi için bkz. [denetimler](https://msdn.microsoft.com/library/3f255a8a-35a8-4712-9065-472ff7d75599).

### <a name="wpf-controls-by-function"></a>Işleve göre WPF denetimleri
 Yerleşik WPF denetimleri burada listelenmiştir.

- **Düğmeler**: <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Primitives.RepeatButton> .

- **Veri görüntüleme**: <xref:System.Windows.Controls.DataGrid> , <xref:System.Windows.Controls.ListView> , ve <xref:System.Windows.Controls.TreeView> .

- **Tarih görüntüleme ve seçim**: <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker> .

- **İletişim kutuları**: <xref:Microsoft.Win32.OpenFileDialog> , <xref:System.Windows.Controls.PrintDialog> , ve <xref:Microsoft.Win32.SaveFileDialog> .

- **Dijital mürekkep**: <xref:System.Windows.Controls.InkCanvas> ve <xref:System.Windows.Controls.InkPresenter> .

- **Belgeler**: <xref:System.Windows.Controls.DocumentViewer> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentScrollViewer> ve <xref:System.Windows.Controls.StickyNoteControl> .

- **Giriş**: <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.RichTextBox> , ve <xref:System.Windows.Controls.PasswordBox> .

- **Düzen**: <xref:System.Windows.Controls.Border> , <xref:System.Windows.Controls.Primitives.BulletDecorator> ,,, <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander> , <xref:System.Windows.Controls.Grid> , <xref:System.Windows.Controls.GridView> , <xref:System.Windows.Controls.GridSplitter> , <xref:System.Windows.Controls.GroupBox> , <xref:System.Windows.Controls.Panel> , <xref:System.Windows.Controls.Primitives.ResizeGrip> , <xref:System.Windows.Controls.Separator> , <xref:System.Windows.Controls.Primitives.ScrollBar> , <xref:System.Windows.Controls.ScrollViewer> , <xref:System.Windows.Controls.StackPanel> , <xref:System.Windows.Controls.Primitives.Thumb> , <xref:System.Windows.Controls.Viewbox> , <xref:System.Windows.Controls.VirtualizingStackPanel> ,, <xref:System.Windows.Window> ve <xref:System.Windows.Controls.WrapPanel> .

- **Medya**: <xref:System.Windows.Controls.Image> , <xref:System.Windows.Controls.MediaElement> , ve <xref:System.Windows.Controls.SoundPlayerAction> .

- **Menüler**: <xref:System.Windows.Controls.ContextMenu> , <xref:System.Windows.Controls.Menu> , ve <xref:System.Windows.Controls.ToolBar> .

- **Gezinti**: <xref:System.Windows.Controls.Frame> ,,, <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow> ve <xref:System.Windows.Controls.TabControl> .

- **Seçim**: <xref:System.Windows.Controls.CheckBox> , <xref:System.Windows.Controls.ComboBox> , <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.RadioButton> , ve <xref:System.Windows.Controls.Slider> .

- **Kullanıcı bilgileri**: <xref:System.Windows.Controls.AccessText> , <xref:System.Windows.Controls.Label> , <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.ProgressBar> , <xref:System.Windows.Controls.Primitives.StatusBar> , <xref:System.Windows.Controls.TextBlock> , ve <xref:System.Windows.Controls.ToolTip> .

## <a name="input-and-commanding"></a><a name="Input_And_Commanding"></a> Giriş ve verme
 Denetimler çoğu zaman Kullanıcı girişini algılar ve yanıtlar. [WPF giriş sistemi](https://msdn.microsoft.com/library/ms754010\(v=vs.100\).aspx) metin girişi, odak yönetimi ve fare konumlandırmayı desteklemek için hem doğrudan hem de yönlendirilmiş olayları kullanır.

 Uygulamalar genellikle karmaşık giriş gereksinimlerine sahiptir. WPF, Kullanıcı giriş eylemlerini bu eylemlere yanıt veren koddan ayıran bir [komut sistemi](https://msdn.microsoft.com/library/ms752308\(v=vs.100\).aspx) sağlar.

## <a name="layout"></a><a name="Layout"></a> Düzenle
 Bir kullanıcı arabirimi oluşturduğunuzda, bir düzen oluşturmak için denetimlerinizi konuma ve boyuta göre düzenleyin. Herhangi bir düzenin önemli bir gereksinimi, pencere boyutu ve görüntüleme ayarlarındaki değişikliklere uyum sağlar. Bu koşullarda bir düzeni uyarlamak için kodu yazmanızı zorlamak yerine WPF, sizin için birinci sınıf bir Genişletilebilir düzen sistemi sağlar.

 Düzen sisteminin temel taşı, değişen pencere ve görüntüleme koşullarına uyum sağlayan göreli konumlardır. Ayrıca, Düzen sistemi, düzeni belirleme denetimleri arasındaki anlaşmayı yönetir. Anlaşma iki adımlı bir işlemdir: ilk olarak, bir denetim üst öğeye gereken konumu ve boyutu söyler; İkincisi, üst öğe denetime ne kadar boşluk yapabileceğini söyler.

 Düzen sistemi, temel WPF sınıfları aracılığıyla alt denetimlere açıktır. WPF, yığınlama ve yerleştirme gibi ortak düzenler için çeşitli düzen denetimleri içerir:

- <xref:System.Windows.Controls.Canvas>: Alt denetimler kendi düzenlerini sağlar.

- <xref:System.Windows.Controls.DockPanel>: Alt denetimler panelin kenarlarına hizalanır.

- <xref:System.Windows.Controls.Grid>: Alt denetimler satırlara ve sütunlara göre konumlandırılır.

- <xref:System.Windows.Controls.StackPanel>: Alt denetimler dikey ya da yatay olarak yığılır.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Alt denetimler sanallaştırılır ve yatay veya dikey olarak yönelimli tek bir satırda düzenlenir.

- <xref:System.Windows.Controls.WrapPanel>: Alt denetimler soldan sağa düzende konumlandırılır ve geçerli satırda alanın izin verdiğinden daha fazla denetim olduğunda sonraki satıra kaydırılır.

  Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel> çeşitli denetimleri düzenlemek için bir kullanır <xref:System.Windows.Controls.TextBox> .

  [!code-xml[IntroToWPFSnippets#LayoutMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/LayoutWindow.xaml#layoutmarkup)]

  , <xref:System.Windows.Controls.DockPanel> Alt <xref:System.Windows.Controls.TextBox> denetimlerin nasıl düzenlendiğini anlatmasını sağlar. Bunu yapmak için, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel.Dock%2A> her birinin bir dock stili belirtmesini sağlamak üzere alt denetimlere sunulan bir özelliği uygular.

> [!NOTE]
> Alt denetimler tarafından kullanılmak üzere bir üst denetim tarafından uygulanan bir özellik, [iliştirilmiş özelliği](https://msdn.microsoft.com/library/ms749011\(v=vs.100\).aspx)olarak ADLANDıRıLAN bir WPF yapısıdır.

 Aşağıdaki şekilde, önceki örnekteki XAML biçimlendirmesinin sonucu gösterilmektedir.

 ![DockPanel sayfası](../designers/media/wpfintrofigure11.png "WPFIntroFigure11")

## <a name="data-binding"></a><a name="Data_Binding"></a> Veri bağlama
 Birçok uygulama, kullanıcılara verileri görüntüleme ve düzenleme araçlarını sağlamak için oluşturulur. WPF uygulamaları için, veri depolama ve erişme işi SQL Server ve ADO .NET gibi teknolojiler tarafından zaten sunulmaktadır. Verilere erişildikten ve uygulamanın yönetilen nesnelerine yüklendikten sonra, WPF uygulamalarına yönelik sabit çalışma başlar. Temelde, bu iki şeyi içerir:

1. Yönetilen nesnelerden verileri, verilerin görüntülenebildiği ve düzenlenebileceği denetimlere kopyalama.

2. Denetimler kullanılarak verilerde yapılan değişikliklerin, yönetilen nesnelere geri kopyalanmasını sağlamak.

   WPF, uygulama geliştirmeyi basitleştirmek için, bu adımları otomatik olarak gerçekleştirmek üzere bir veri bağlama altyapısı sağlar. Veri bağlama altyapısının çekirdek birimi, <xref:System.Windows.Data.Binding> işi bir denetimi (bağlama hedefi) bir veri nesnesine (bağlama kaynağı) bağlamak olan sınıftır. Bu ilişki aşağıdaki şekilde gösterilmiştir.

   ![Temel veri bağlama diyagramı](../designers/media/databindingmostbasic.png "DataBindingMostBasic")

   Aşağıdaki örnek, bir <xref:System.Windows.Controls.TextBox> özel nesne örneğine nasıl bağlanacağını göstermektedir `Person` . `Person`Uygulama aşağıdaki kodda gösterilmiştir.

   [!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/Person.cs#personclasscode)]
   [!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/Person.vb#personclasscode)]

   Aşağıdaki biçimlendirme, öğesini bir <xref:System.Windows.Controls.TextBox> özel nesne örneğine bağlar `Person` .

   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP1](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup1)]
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP2](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup2)]
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP3](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup3)]

   [!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml.cs#databindingcodebehind)]
   [!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/DataBindingWindow.xaml.vb#databindingcodebehind)]

   Bu örnekte, `Person` sınıfı arka plan kodunda oluşturulur ve için veri bağlamı olarak ayarlanır `DataBindingWindow` . Biçimlendirme bölümünde <xref:System.Windows.Controls.TextBox.Text%2A> öğesinin özelliği <xref:System.Windows.Controls.TextBox> `Person.Name` özelliğine bağlanır (" `{Binding ... }` " xaml sözdizimi kullanılarak). Bu XAML, WPF <xref:System.Windows.Controls.TextBox> `Person` 'in denetimi pencerenin özelliğinde depolanan nesneye bağlamasını söyler <xref:System.Windows.FrameworkElement.DataContext%2A> .

   WPF veri bağlama altyapısı, doğrulama, sıralama, filtreleme ve gruplamayı içeren ek destek sağlar. Ayrıca, veri bağlama, standart WPF denetimleri tarafından görüntülenecek kullanıcı arabirimi uygun olmadığında, bağlantılı veriler için özel kullanıcı arabirimi oluşturmak üzere veri şablonlarının kullanımını destekler.

   Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx).

## <a name="graphics"></a><a name="Graphics"></a> Grafik
 WPF, aşağıdaki avantajları içeren kapsamlı, ölçeklenebilir ve esnek bir grafik özellikleri kümesi sunar:

- **Çözünürlükten bağımsız ve cihazdan bağımsız grafikler**. WPF Grafik sistemindeki temel ölçü birimi, gerçek ekran çözünürlüğünden bağımsız olarak bir inç 1/96th olan cihazdan bağımsız pikseldir ve çözünürlükten bağımsız ve cihazdan bağımsız işleme için temel sağlar. Her cihazdan bağımsız piksel, üzerinde oluşturduğu sistemin inç başına nokta (DPI) ayarıyla eşleşecek şekilde otomatik olarak ölçeklendirilir.

- **İyileştirilmiş duyarlık**. WPF koordinat sistemi, tek duyarlık yerine çift duyarlıklı kayan noktalı sayılar ile ölçülür. Dönüşümler ve opaklık değerleri de çift duyarlıklı olarak ifade edilir. WPF ayrıca geniş bir renk gamutu (scRGB) destekler ve farklı renk uzaylarından girişleri yönetmek için tümleşik destek sağlar.

- **Gelişmiş grafikler ve animasyon desteği**. WPF, sizin için animasyon sahneleri yöneterek grafik programlamayı basitleştirir; sahne işleme, işleme döngüleri ve Bilinear ilişkilendirme konusunda endişelenmenize gerek yoktur. Ayrıca WPF, isabet testi desteği ve tam alfa birleştirme desteği sağlar.

- **Donanım hızlandırma**. WPF Grafik sistemi, CPU kullanımını en aza indirmek için grafik donanımından yararlanır.

### <a name="2-d-shapes"></a>2-b şekiller
 WPF, aşağıdaki çizimde gösterilen dikdörtgenler ve üç nokta gibi yaygın vektör çizimli 2-b şekillerinin bir kitaplığını sağlar.

 ![Üç nokta ve dikdörtgen](../designers/media/wpfintrofigure4.PNG "WPFIntroFigure4")

 Şekillerin ilginç bir özelliği yalnızca görüntüleme için değildir; şekiller, klavye ve fare girişi dahil olmak üzere denetimlerden beklediğinizi birçok özelliği uygular. Aşağıdaki örnek, <xref:System.Windows.UIElement.MouseUp> işlenmekte olan olayını gösterir <xref:System.Windows.Shapes.Ellipse> .

 [!code-xml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml#handleellipsemouseupeventmarkup)]

 [!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml.cs#handleellipsemouseupeventcodebehind)]
 [!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/EllipseEventHandlingWindow.xaml.vb#handleellipsemouseupeventcodebehind)]

 Aşağıdaki şekilde, önceki kod tarafından üretilen değer gösterilmektedir.

 !["Elips tıkladınız&#33;" metnini içeren pencere](../designers/media/wpfintrofigure12.png "WPFIntroFigure12")

 Daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](https://msdn.microsoft.com/library/ms747393\(v=vs.100\).aspx).

### <a name="2-d-geometries"></a>2-b geometrileri
 WPF tarafından sunulan 2-b şekiller, temel şekillerin standart kümesini kapsar. Ancak, özelleştirilmiş bir kullanıcı arabiriminin tasarımını kolaylaştırmak için özel şekiller oluşturmanız gerekebilir. Bu amaçla WPF, geometriler sağlar. Aşağıdaki şekilde, doğrudan çizilemeyen, fırça olarak kullanılan veya diğer şekilleri ve denetimleri kırpmak için kullanılan özel bir şekil oluşturmak için geometriler kullanımı gösterilmektedir.

 <xref:System.Windows.Shapes.Path> nesneler, kapalı veya açık şekiller, birden çok şekil ve hatta eğri şekiller çizmek için kullanılabilir.

 <xref:System.Windows.Media.Geometry> nesneler kırpma, isabet sınama ve 2-b grafik verileri işleme için kullanılabilir.

 ![Yolun çeşitli kullanımları](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")

 Daha fazla bilgi için bkz. [geometriye genel bakış](https://msdn.microsoft.com/library/ms751808\(v=vs.100\).aspx)

### <a name="2-d-effects"></a>2-b efekt
 WPF 2-D özellikleri alt kümesi; degradeler, bit eşlemler, çizimler, videolar, döndürme, ölçekleme ve eğriltme gibi görsel etkileri içerir. Bunlar fırçalar ile elde edilir; Aşağıdaki şekilde bazı örnekler gösterilmektedir.

 ![Farklı fırçaların çizimi](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")

 Daha fazla bilgi için bkz. [WPF Fırçalarına Genel Bakış](https://msdn.microsoft.com/library/aa970904\(v=vs.100\).aspx).

### <a name="3-d-rendering"></a>3-b Işleme
 WPF ayrıca, daha heyecan verici ve ilginç Kullanıcı arabirimleri oluşturulmasına olanak tanımak için 2-b grafiklerle tümleştirilen 3-b işleme özelliklerini de içerir. Örneğin, aşağıdaki şekilde 3-b şekiller üzerinde işlenen 2-b görüntü gösterilmektedir.

 ![Visual3d değil örnek ekran görüntüsü](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")

 Daha fazla bilgi için bkz. [3-b grafik genel bakış](https://msdn.microsoft.com/library/ms747437\(v=vs.100\).aspx).

## <a name="animation"></a><a name="Animation"></a> Unda
 WPF animasyon desteği, denetimlerin büyümesi, sallanması, dönmesi ve belirmesini, ilginç sayfa geçişleri oluşturmak ve daha fazlasını yapmanızı sağlar. Birçok WPF sınıfının, hatta özel sınıfların animasyonunu yapabilirsiniz. Aşağıdaki şekilde, eylem içinde basit bir animasyon gösterilmektedir.

 ![Animasyonlu küpün görüntüleri](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")

 Daha fazla bilgi için bkz. [animasyon genel bakış](https://msdn.microsoft.com/library/ms752312\(v=vs.100\).aspx).

## <a name="media"></a><a name="Media"></a> Medyasını
 Zengin içerik iletmenin bir yolu, Audiovisual medyası kullanmaktır. WPF, görüntüler, videolar ve ses için özel destek sağlar.

### <a name="images"></a>Görüntüler
 Görüntüler çoğu uygulama için ortaktır ve WPF bunları kullanmak için çeşitli yollar sağlar. Aşağıdaki şekilde, küçük resim görüntüleri içeren bir liste kutusuyla bir kullanıcı arabirimi gösterilmektedir. Küçük resim seçildiğinde görüntü tam boyut olarak gösterilir.

 ![Küçük resim görüntüleri ve tam&#45;boyutu görüntüsü](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")

 Daha fazla bilgi için bkz. [Imaging 'e genel bakış](https://msdn.microsoft.com/library/ms748873\(v=vs.100\).aspx).

### <a name="video-and-audio"></a>Video ve ses
 <xref:System.Windows.Controls.MediaElement>Denetim hem videoyu hem de sesi oynatabilen ve özel bir medya yürütücüsünün temeli olması yeterince esnektir. Aşağıdaki XAML biçimlendirmesi bir medya oynatıcı uygular.

 [!code-xml[IntroToWPFSnippets#MediaElementMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/MediaElementWindow.xaml#mediaelementmarkup)]

 Aşağıdaki şekilde gösterilen pencere, <xref:System.Windows.Controls.MediaElement> denetimin eylemde bulunduğu bir işlemdir.

 ![Ses ve video ile MediaElement denetimi](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")

 Daha fazla bilgi için bkz. [WPF grafikleri, animasyon ve medyaya genel bakış](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx).

## <a name="text-and-typography"></a><a name="Text_and_Typography"></a> Metin ve tipografi
 WPF, yüksek kaliteli metin işlemesini kolaylaştırmak için aşağıdaki özellikleri sunar:

- OpenType yazı tipi desteği.

- ClearType geliştirmeleri.

- Donanım hızlandırmasının avantajlarından yararlanan yüksek performans.

- Medya, grafik ve animasyonla metin tümleştirmesi.

- Uluslararası yazı tipi desteği ve geri dönüş mekanizmaları.

  Grafiklerle metin tümleştirmesinin bir sunumu olarak, aşağıdaki şekilde metin düzenlemelerinin uygulaması gösterilmektedir.

  ![Çeşitli metin süslemeleri içeren metin](../designers/media/wpfintrofigure23.png "WPFIntroFigure23")

  Daha fazla bilgi için bkz. [tipografi Windows Presentation Foundation](https://msdn.microsoft.com/library/ms742190\(v=vs.100\).aspx).

## <a name="customizing-wpf-applications"></a><a name="WPF_Customization"></a> WPF uygulamalarını özelleştirme
 Bu noktaya kadar, uygulama geliştirmeye yönelik temel WPF yapı taşlarını gördünüz. Genellikle denetimlerden oluşan uygulama içeriğini barındırmak ve sunmak için uygulama modelini kullanırsınız. Bir kullanıcı arabirimindeki denetimlerin düzenlemesini basitleştirmek ve düzenlemenin pencere boyutu ve görüntüleme ayarlarında yapılan değişiklikler üzerinde tutulmasını sağlamak için WPF düzen sistemini kullanırsınız. Çoğu uygulama kullanıcıların verilerle etkileşime girmesine izin vertiğinden, Kullanıcı arabiriminizi verilerle tümleştirme işini azaltmak için veri bağlamayı kullanırsınız. Uygulamanızın görsel görünümünü geliştirmek için WPF tarafından sunulan kapsamlı grafik, animasyon ve medya desteği aralığını kullanırsınız.

 Genellikle, temel bilgiler, gerçekten ayrı ve görsel açıdan etkileyici bir kullanıcı deneyimi oluşturmak ve yönetmek için yeterli değildir. Standart WPF denetimleri uygulamanızın istenen görünümüyle tümleştirilemeyebilir. Veriler en etkili şekilde görüntülenmeyebilir. Uygulamanızın genel kullanıcı deneyimi, Windows temalarının varsayılan görünümü ve hislerine uygun olmayabilir. Birçok şekilde, bir sunum teknolojisinin diğer genişletilebilirlik türleri kadar görsel genişletilebilirliği olması gerekir.

 Bu nedenle WPF, denetimler, Tetikleyiciler, denetim ve veri şablonları, stiller, Kullanıcı arabirimi kaynakları ve Temalar ve kaplamalar için zengin bir içerik modeli de dahil olmak üzere benzersiz kullanıcı deneyimleri oluşturmak için çeşitli mekanizmalar sunar.

### <a name="content-model"></a>İçerik modeli
 WPF denetimlerinin çoğunluğunun ana amacı içeriği görüntülemektir. WPF içinde, bir denetimin içeriğini oluşturan öğelerin türü ve sayısı denetimin *içerik modeli*olarak adlandırılır. Bazı denetimler, tek bir öğe ve içerik türü içerebilir; Örneğin, öğesinin içeriği <xref:System.Windows.Controls.TextBox> özelliğine atanan bir dize değeridir <xref:System.Windows.Controls.TextBox.Text%2A> . Aşağıdaki örnek bir öğesinin içeriğini ayarlar <xref:System.Windows.Controls.TextBox> .

 [!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup1)]
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup2)]
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup3)]

 Aşağıdaki şekilde sonuç gösterilmektedir.

 ![Metin içeren TextBox denetimi](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")

 Bununla birlikte, diğer denetimler farklı türde içeriklerde birden çok öğe içerebilir; özelliği tarafından belirtilen bir öğesinin içeriği, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ContentControl.Content%2A> düzen denetimleri, metin, Resimler ve şekiller gibi çeşitli öğeleri içerebilir. Aşağıdaki örnek, bir,, <xref:System.Windows.Controls.Button> , ve içeren içeriği içeren bir gösterir <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.MediaElement> .

 [!code-xml[IntroToWPFSnippets#ButtonContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup1)]
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup2)]
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup3)]

 Aşağıdaki şekilde bu düğmenin içeriği gösterilmektedir.

 ![Birden çok türde içerik içeren bir düğme](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")

 Çeşitli denetimler tarafından desteklenen içerik türleri hakkında daha fazla bilgi için bkz. [WPF Içerik modeli](https://msdn.microsoft.com/library/bb613548\(v=vs.100\).aspx).

### <a name="triggers"></a>Tetikleyiciler
 XAML biçimlendirmesinin ana amacı uygulamanın görünümünü uygulamak olsa da, bir uygulamanın davranışının bazı yönlerini uygulamak için XAML de kullanabilirsiniz. Bir örnek, bir uygulamanın görünümünü kullanıcı etkileşimlerine göre değiştirmek için tetikleyicilerin kullanılması. Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx)oluşturma.

### <a name="control-templates"></a>Denetim Şablonları
 WPF denetimleri için varsayılan kullanıcı arabirimleri genellikle diğer denetimlerden ve şekillerden oluşturulur. Örneğin, bir, <xref:System.Windows.Controls.Button> <xref:Microsoft.Windows.Themes.ButtonChrome> ve <xref:System.Windows.Controls.ContentPresenter> denetimlerinden oluşur. , <xref:Microsoft.Windows.Themes.ButtonChrome> Standart düğme görünümünü sağlar, ancak <xref:System.Windows.Controls.ContentPresenter> düğme içeriğini özelliği tarafından belirtilen şekilde görüntüler <xref:System.Windows.Controls.ContentControl.Content%2A> .

 Bazen bir denetimin varsayılan görünümü bir uygulamanın genel görünümüyle birlikte kullanılamaz. Bu durumda, <xref:System.Windows.Controls.ControlTemplate> içeriğini ve davranışını değiştirmeden denetimin kullanıcı arabiriminin görünümünü değiştirmek için bir kullanabilirsiniz.

 Örneğin, aşağıdaki örnek, öğesinin görünümünü ' a kullanarak nasıl değiştirileceğini gösterir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> .

 [!code-xml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml#buttoncontroltemplatewindowmarkup)]

 [!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml.cs#buttoncontroltemplatewindowcodebehind)]
 [!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/ControlTemplateButtonWindow.xaml.vb#buttoncontroltemplatewindowcodebehind)]

 Bu örnekte, varsayılan düğme Kullanıcı arabirimi <xref:System.Windows.Shapes.Ellipse> koyu mavi kenarlığa sahip olan ve kullanılarak doldurulmuş bir ile değiştirilmiştir <xref:System.Windows.Media.RadialGradientBrush> . <xref:System.Windows.Controls.ContentPresenter>Denetimde içeriğini görüntüleyen denetim <xref:System.Windows.Controls.Button> , "bana tıklama!" <xref:System.Windows.Controls.Button>Tıklandığında <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay, denetimin varsayılan davranışının bir parçası olarak yine de oluşturulur <xref:System.Windows.Controls.Button> . Sonuç aşağıdaki şekilde gösterilmiştir.

 ![Elips düğme ve ikinci bir pencere](../designers/media/wpfintrofigure2.png "WPFIntroFigure2")

### <a name="data-templates"></a>Veri Şablonları
 Bir denetim şablonu bir denetimin görünümünü belirtmenize izin verirken, bir veri şablonu bir denetimin içeriğinin görünümünü belirtmenize olanak tanır. Veri şablonları genellikle, bağlantılı verilerin nasıl görüntülendiğini iyileştirmek için kullanılır. Aşağıdaki şekilde, <xref:System.Windows.Controls.ListBox> `Task` her görevin bir ad, açıklama ve önceliğe sahip olduğu bir nesne koleksiyonuna bağlanan bir için varsayılan görünüm gösterilmektedir.

 ![Varsayılan görünümü içeren bir liste kutusu](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")

 Varsayılan görünüm, bir ' dan beklediğiniz şeydir <xref:System.Windows.Controls.ListBox> . Ancak, her görevin varsayılan görünümü yalnızca görev adını içerir. Görev adını, açıklamasını ve önceliğini göstermek için, <xref:System.Windows.Controls.ListBox> denetimin bağlantılı liste öğelerinin varsayılan görünümünün bir kullanılarak değiştirilmesi gerekir <xref:System.Windows.DataTemplate> . Aşağıdaki XAML, <xref:System.Windows.DataTemplate> özniteliği kullanılarak her bir göreve uygulanan böyle bir tanımlar <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> .

 [!code-xml[IntroToWPFSnippets#DataTemplateMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup1)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup2)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup3)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup4)]

 Aşağıdaki şekilde bu kodun etkisi gösterilmektedir.

 ![Veri şablonu kullanan llist kutusu](../designers/media/wpfintrofigure19.png "WPFIntroFigure19")

 Öğesinin <xref:System.Windows.Controls.ListBox> davranışını ve genel görünümünü beklediğine ve yalnızca liste kutusu tarafından görüntülenen içeriğin görünümü değiştiği unutulmamalıdır.

 Daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](https://msdn.microsoft.com/library/ms742521\(v=vs.100\).aspx).

### <a name="styles"></a>Stiller
 Stiller, geliştiricilerin ve tasarımcıların ürünlerinin belirli bir görünümünü standartlaştırmasını sağlar. WPF, öğesi olan bir güçlü stil modeli sunar <xref:System.Windows.Style> . Aşağıdaki örnek, her bir pencerede için arka plan rengini ayarlayan bir stil oluşturur <xref:System.Windows.Controls.Button> `Orange` .

 [!code-xml[IntroToWPFSnippets#StyleMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup1)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup2)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup3)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup4)]

 Bu stil tüm denetimleri hedeflediğinden <xref:System.Windows.Controls.Button> , stil, aşağıdaki şekilde gösterildiği gibi penceredeki tüm düğmelere otomatik olarak uygulanır.

 ![İki turuncu düğme](../designers/media/wpfintrofigure20.png "WPFIntroFigure20")

 Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx)oluşturma.

### <a name="resources"></a>Kaynaklar
 Bir uygulamadaki denetimler aynı görünümü paylaşmalıdır. Bu, yazı tiplerinden ve arka plan renklerinden şablonları, veri şablonlarını ve stilleri denetleyebilen herhangi bir şeyi içerebilir. Bu kaynakları yeniden kullanım için tek bir konumda kapsüllemek üzere, WPF 'nin Kullanıcı arabirimi kaynakları desteğini kullanabilirsiniz.

 Aşağıdaki örnek, ve tarafından paylaşılan ortak bir arka plan rengi tanımlar <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label> .

 [!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup1)]
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup2)]
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup3)]

 Bu örnek, özellik öğesini kullanarak bir arka plan rengi kaynağı uygular `Window.Resources` . Bu kaynak, öğesinin tüm alt öğeleri için kullanılabilir <xref:System.Windows.Window> . Aşağıdakiler de dahil olmak üzere çeşitli kaynak kapsamları çözümlendikleri sırayla listelenmiştir:

1. Tek bir denetim (devralınan özelliği kullanarak <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> ).

2. A <xref:System.Windows.Window> veya a <xref:System.Windows.Controls.Page> (devralınan özelliği de kullanılarak <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> ).

3. Bir <xref:System.Windows.Application> (özelliğini kullanarak <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> ).

   Çeşitli kapsamlar, kaynaklarınızı tanımladığınız ve paylaştığınız yönteme göre esneklik sağlar.

   Kaynaklarınızın belirli bir kapsamla doğrudan ilişkilendirilmesi için alternatif olarak, bir veya daha fazla kaynağı, <xref:System.Windows.ResourceDictionary> uygulamanın diğer bölümlerinde başvurulabilen ayrı bir kullanarak paketleyebilir. Örneğin, aşağıdaki örnekte kaynak sözlüğünde varsayılan bir arka plan rengi tanımlanmaktadır.

   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup1)]
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup2)]

   Aşağıdaki örnek, bir uygulama genelinde paylaşılabilmesi için önceki örnekte tanımlanan kaynak sözlüğüne başvurur.

   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup1)]
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup2)]

   Kaynaklar ve kaynak sözlükleri, Temalar ve kaplamalar için WPF desteğinin temelini içerir.

   Daha fazla bilgi için bkz. [kaynaklara genel bakış](https://msdn.microsoft.com/library/ms750613\(v=vs.100\).aspx).

### <a name="custom-controls"></a>Özel denetimler
 WPF, özelleştirme desteği sunan bir konak sağlasa da, mevcut WPF denetimlerinin uygulamanızın veya kullanıcılarınızın ihtiyaçlarını karşılamadığında karşılaşabileceğiniz durumlarla karşılaşabilirsiniz. Bu durum şu durumlarda oluşabilir:

- İhtiyaç duyduğunuz Kullanıcı arabirimi, mevcut WPF uygulamalarının görünümü özelleştirilerek oluşturulamaz.

- Gerekli olan davranış, mevcut WPF uygulamaları tarafından desteklenmez (veya kolayca desteklenmez).

  Ancak, bu noktada, yeni bir denetim oluşturmak için üç WPF modelinden birini kullanabilirsiniz. Her model belirli bir senaryoyu hedefler ve özel denetiminizin belirli bir WPF Taban sınıfından türemesini gerektirir. Üç model burada listelenmiştir:

- **Kullanıcı denetimi modeli**. Özel denetim, öğesinden türetilir <xref:System.Windows.Controls.UserControl> ve bir veya daha fazla denetimden oluşur.

- **Denetim modeli**. Özel bir denetim, ' dan türetilir <xref:System.Windows.Controls.Control> ve, WPF denetimlerinin çoğunluğunda olduğu gibi, davranışlarını, şablonlarının görünümlerini kullanarak ayıran uygulamalar oluşturmak için kullanılır. Öğesinden türetme <xref:System.Windows.Controls.Control> , Kullanıcı denetimlerinden özel bir kullanıcı arabirimi oluşturmak için daha fazla özgürlük sağlar, ancak daha fazla çaba gerektirebilir.

- **Framework öğe modeli**. Özel denetim, <xref:System.Windows.FrameworkElement> görünümü özel işleme mantığı (şablon değil) tarafından tanımlandığında öğesinden türetilir.

  Aşağıdaki örnek, öğesinden türetilen özel bir sayısal yukarı/aşağı denetimi gösterir <xref:System.Windows.Controls.UserControl> .

  [!code-xml[IntroToWPFSnippets#UserControlMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml#usercontrolmarkup)]

  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind1)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind1)]
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind2)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind2)]

 Sonraki örnekte, Kullanıcı denetimini bir öğesine eklemek için gereken XAML gösterilmektedir <xref:System.Windows.Window> .

 [!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup1)]
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup2)]
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup3)]

 Aşağıdaki şekilde, `NumericUpDown` içinde barındırılan denetim gösterilmektedir <xref:System.Windows.Window> .

 ![Özel bir UserControl](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")

 Özel denetimler hakkında daha fazla bilgi için bkz. [Denetim yazma genel bakış](https://msdn.microsoft.com/library/ms745025\(v=vs.100\).aspx).

## <a name="wpf-best-practices"></a><a name="WPF_Best_Practices"></a> WPF En Iyi uygulamaları
 Her türlü geliştirme platformunda olduğu gibi, WPF istenen sonuca ulaşmak için çeşitli yollarla kullanılabilir. WPF uygulamalarınızın gerekli Kullanıcı deneyimini sağlayıp, genel olarak hedef kitle taleplerini karşıladığından emin olmanın bir yolu olarak erişilebilirlik, Genelleştirme ve yerelleştirme ve performans için önerilen en iyi uygulamalar vardır. Daha fazla bilgi için aşağıdakilere bakın:

- [En Iyi erişilebilirlik uygulamaları](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx) En Iyi erişilebilirlik uygulamaları

- [WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- [WPF Uygulama Performansını İyileştirme](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

- [Windows Presentation Foundation güvenliği](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

## <a name="summary"></a><a name="Summary"></a> Özetleme
 WPF, çok çeşitli görsel açıdan şaşırtıcı istemci uygulamaları oluşturmaya yönelik kapsamlı bir sunum teknolojisidir. Bu giriş, WPF 'nin temel özelliklerine bir görünüm sağlamıştır.

 Sonraki adım WPF uygulamaları derlemek!

 Bunları oluştururken, önemli özellikler üzerindeki bir Yenileyici için bu girişe geri dönüp bu giriş kapsamında ele alınan özelliklerin daha ayrıntılı kapsamına yönelik başvuruları bulabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [WPF kullanmaya başlarken](../designers/getting-started-with-wpf.md) [Windows Presentation Foundation Windows Presentation Foundation modern masaüstü uygulamaları oluşturun](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md) [Windows Presentation Foundation](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)
