---
title: 'İzlenecek yol: Düzenleyici uzantısı ile Kabuk komutu kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 02ff8a2be0d13af193a204ee6711bf7dfa11dee7
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566966"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>İzlenecek yol: Düzenleyici uzantısı ile Kabuk komutu kullanma
VSPackage düzenleyiciye menü komutları gibi özellikleri ekleyebilirsiniz. Bu kılavuzda bir kenarlığı düzenleyici metin görünümünde bir menü komutunu çağırarak nasıl ekleneceğini gösterir.  
  
 Bu izlenecek yol, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen bölümü ile birlikte bir VSPackage kullanımını gösterir. Menü komutu ile Visual Studio Kabuğu kaydetmek için bir VSPackage'ı kullanmanız gerekir. Ve MEF Bileşeni parçası erişmeye komutunu kullanabilirsiniz.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-menu-command"></a>Bir menü komutuyla uzantı oluşturma  
 Adlı bir menü komutu yerleştiren bir VSPackage'ı oluşturma **ekleme kenarlığı** üzerinde **Araçları** menüsü.  
  
1.  Adlı bir C# VSIX projesi oluşturun `MenuCommandTest`ve bir özel komut öğesi şablonunun adı ekleyin **AddAdornment**. Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  MenuCommandTest adlı bir çözümü açar. Menü komutunu oluşturur ve bunu koyar kodu MenuCommandTestPackage dosyayı içeren **Araçları** menüsü. Bu noktada, komut yalnızca bir ileti kutusunda görünmesine neden olur. Sonraki adımlarında bu açıklama kenarlığı görüntülenecek değiştirme gösterir.  
  
3.  Açık *source.extension.vsixmanifest* VSIX bildirim düzenleyicisinde. `Assets` MenuCommandTest bir Microsoft.VisualStudio.VsPackage adlı için sekmesinde bir satır olmalıdır.  
  
4.  Kaydet ve Kapat *source.extension.vsixmanifest* dosya.  
  
## <a name="add-a-mef-extension-to-the-command-extension"></a>MEF uzantısı için komut uzantısı Ekle  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**ve ardından **yeni proje**. İçinde **Yeni Proje Ekle** iletişim kutusu, tıklayın **genişletilebilirlik** altında **Visual C#**, ardından **VSIX projesi**. Projeyi adlandırın `CommentAdornmentTest`.  
  
2.  Bu proje VSPackage tanımlayıcı adlı derleme ile etkileşim kurmak için derleme oturum açmanız gerekir. VSPackage derleme için önceden oluşturulmuş bir anahtar dosyası kullanabilirsiniz.  
  
    1.  Proje özelliklerini açın ve seçin **imzalama** sekmesi.  
  
    2.  Seçin **derlemeyi imzalamayı**.  
  
    3.  Altında **bir tanımlayıcı ad anahtar dosyası seç**seçin *Key.snk* MenuCommandTest derleme için oluşturulan dosya.  
  
## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage proje MEF uzantı bakın  
 VSPackage'ı için bir MEF Bileşeni eklemekte olduğunuz çünkü her iki türde varlıkları bildiriminde belirtmeniz gerekir.  
  
> [!NOTE]
>  MEF hakkında daha fazla bilgi için bkz: [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](/dotnet/framework/mef/index).  
  
### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage projedeki MEF Bileşeni başvurmak için  
  
1.  MenuCommandTest projeyi *source.extension.vsixmanifest* VSIX bildirim düzenleyicisinde.  
  
2.  Üzerinde **varlıklar** sekmesinde **yeni**.  
  
3.  İçinde **türü** listesinde **Microsoft.VisualStudio.MefComponent**.  
  
4.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
5.  İçinde **proje** listesinde **CommentAdornmentTest**.  
  
6.  Kaydet ve Kapat *source.extension.vsixmanifest* dosya.  
  
7.  MenuCommandTest proje CommentAdornmentTest projeye bir başvuru olduğundan emin olun.  
  
8.  CommentAdornmentTest projesinde bir derleme oluşturmak için proje ayarlayın. İçinde **Çözüm Gezgini**, projeyi seçin ve ardından konum **özellikleri** penceresi **OutputDirectory için derleme çıkışı Kopyala** özelliği için ayarlayın**true**.  
  
## <a name="define-a-comment-adornment"></a>Bir yorum kenarlığı tanımlayın  
 Açıklama kenarlığı oluşan bir <xref:Microsoft.VisualStudio.Text.ITrackingSpan> seçili metni ve yazar ve metin açıklamasını temsil eden herhangi bir dize izler.  
  
#### <a name="to-define-a-comment-adornment"></a>Bir yorum kenarlığı tanımlamak için  
  
1.  CommentAdornmentTest projesinde yeni bir sınıf dosyası ekleyin ve adlandırın `CommentAdornment`.  
  
2.  Aşağıdaki başvuruları ekleyin:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  Aşağıdaki `using` deyimi.  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  Dosya adında bir sınıf içermelidir `CommentAdornment`.  
  
    ```csharp  
    internal class CommentAdornment  
    ```  
  
5.  Üç alanlarına Ekle `CommentAdornment` sınıfının <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, yazar ve açıklama.  
  
    ```csharp  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  Alanları başlatan bir oluşturucu ekleyin.  
  
    ```csharp  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="create-a-visual-element-for-the-adornment"></a>Bir görsel öğe kenarlığı için oluşturma  
 Bir görsel öğe, kenarlığı için tanımlayın. Bu kılavuz için Windows Presentation Foundation (WPF) sınıfından devralan bir denetim tanımlamak <xref:System.Windows.Controls.Canvas>.  
  
1.  CommentAdornmentTest projede bir sınıf oluşturun ve adlandırın `CommentBlock`.  
  
2.  Aşağıdaki `using` deyimleri.  
  
    ```csharp  
    using Microsoft.VisualStudio.Text;  
    using System;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Media;  
    using System.Windows.Shapes;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Olun `CommentBlock` sınıf türünden devralınır <xref:System.Windows.Controls.Canvas>.  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  Kenarlığı görsel özelliklerini tanımlamak için bazı özel alanlar ekleyin.  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  Açıklama kenarlığı tanımlar ve ilgili metin ekleyen bir oluşturucu ekleyin.  
  
    ```csharp  
    public CommentBlock(double textRightEdge, double viewRightEdge,   
            Geometry newTextGeometry, string author, string body)  
    {  
        if (brush == null)  
        {  
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));  
            brush.Freeze();  
            Brush penBrush = new SolidColorBrush(Colors.Green);  
            penBrush.Freeze();  
            solidPen = new Pen(penBrush, 0.5);  
            solidPen.Freeze();  
            dashPen = new Pen(penBrush, 0.5);  
            dashPen.DashStyle = DashStyles.Dash;  
            dashPen.Freeze();  
        }  
  
        this.textGeometry = newTextGeometry;  
  
        TextBlock tb1 = new TextBlock();  
        tb1.Text = author;  
        TextBlock tb2 = new TextBlock();  
        tb2.Text = body;  
  
        const int MarginWidth = 8;  
        this.commentGrid = new Grid();  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        ColumnDefinition cEdge = new ColumnDefinition();  
        cEdge.Width = new GridLength(MarginWidth);  
        ColumnDefinition cEdge2 = new ColumnDefinition();  
        cEdge2.Width = new GridLength(MarginWidth);  
        this.commentGrid.ColumnDefinitions.Add(cEdge);  
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());  
        this.commentGrid.ColumnDefinitions.Add(cEdge2);  
  
        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();  
        rect.RadiusX = 6;  
        rect.RadiusY = 3;  
        rect.Fill = brush;  
        rect.Stroke = Brushes.Green;  
  
            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);  
            tb1.Measure(inf);  
            tb2.Measure(inf);  
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);  
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;  
  
        Grid.SetColumn(rect, 0);  
        Grid.SetRow(rect, 0);  
         Grid.SetRowSpan(rect, 2);  
        Grid.SetColumnSpan(rect, 3);  
        Grid.SetRow(tb1, 0);  
        Grid.SetColumn(tb1, 1);  
        Grid.SetRow(tb2, 1);  
        Grid.SetColumn(tb2, 1);  
        this.commentGrid.Children.Add(rect);  
        this.commentGrid.Children.Add(tb1);  
        this.commentGrid.Children.Add(tb2);  
  
        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));  
         Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);  
  
        this.Children.Add(this.commentGrid);  
    }  
    ```  
  
6.  Ayrıca uygulayan bir <xref:System.Windows.Controls.Panel.OnRender%2A> kenarlığı çizen bir olay işleyicisi.  
  
    ```csharp  
    protected override void OnRender(DrawingContext dc)  
    {  
        base.OnRender(dc);  
        if (this.textGeometry != null)  
        {  
            dc.DrawGeometry(brush, solidPen, this.textGeometry);  
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);  
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);  
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);  
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);  
            dc.DrawLine(dashPen, p1, p2);  
            dc.DrawLine(dashPen, p2, p3);  
        }  
    }  
    ```  
  
## <a name="add-an-iwpftextviewcreationlistener"></a>Bir IWpfTextViewCreationListener Ekle  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Oluşturma olayları görüntülemek için dinlemek için kullanabileceğiniz bir MEF Bileşeni parçasıdır.  
  
1.  CommentAdornmentTest projeye bir sınıf dosyası ekleyin ve adlandırın `Connector`.  
  
2.  Aşağıdaki `using` deyimleri.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Uygulayan bir sınıf bildirme <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ve <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> , <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. İçerik türü özniteliğini bileşeni uygulandığı içerik türünü belirtir. Metin türü tüm ikili olmayan dosya türleri için temel türdür. Bu nedenle, oluşturulduktan hemen hemen her metin görünümü, bu tür olacaktır. Metin görünümü role özniteliğini bileşeni uygulandığı metin görünümü türünü belirtir. Belge metin görünümü rolleri genellikle satırlarını oluşur ve bir dosyada depolanır metni gösterir.  
  
     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  Uygulama <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> statik olan çağırır yöntemi `Create()` olayı `CommentAdornmentManager`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  Komutu yürütmek için kullanabileceğiniz bir yöntem ekleyin.  
  
    ```csharp  
    static public void Execute(IWpfTextViewHost host)  
    {  
        IWpfTextView view = host.TextView;  
        //Add a comment on the selected text.   
        if (!view.Selection.IsEmpty)  
        {  
            //Get the provider for the comment adornments in the property bag of the view.  
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));  
  
            //Add some arbitrary author and comment text.   
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;  
            string comment = "Four score....";  
  
            //Add the comment adornment using the provider.  
            provider.Add(view.Selection.SelectedSpans[0], author, comment);  
        }  
    }  
    ```  
  
## <a name="define-an-adornment-layer"></a>Kenarlığı katman tanımlayın  
 Yeni bir kenarlığı eklemek için bir kenarlığı katmanı tanımlamanız gerekir.  
  
### <a name="to-define-an-adornment-layer"></a>Kenarlığı katman tanımlamak için  
  
1.  İçinde `Connector` sınıfı, ortak bir alan türü bildirmek <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> kenarlığı katmanı için benzersiz bir ad belirtir ve bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , bu kenarlığı katmanın Z düzenini ilişki için diğer metni tanımlar Katmanları (metin, giriş işaretini ve seçimi) görüntüleyin.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="provide-comment-adornments"></a>Açıklama Kenarlıklar sağlayın  
 Ayrıca bir kenarlığı tanımladığınızda, bir açıklama kenarlığı sağlayıcısı ve bir açıklama kenarlığı Yöneticisi'ni uygulayın. Açıklama kenarlığı sağlayıcısı açıklama Kenarlıklar listesini tutar, dinleyen <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olayları temel alınan metin arabelleği ve temel alınan metin silindiğinde açıklama Kenarlıklar siler.  
  
1.  CommentAdornmentTest projeye yeni bir sınıf dosyası ekleyin ve adlandırın `CommentAdornmentProvider`.  
  
2.  Aşağıdaki `using` deyimleri.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  Adlı bir sınıf ekleyin `CommentAdornmentProvider`.  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  Metin arabelleği ve arabelleğe ilgili yorum Kenarlıklar listesi için özel alanlar ekleyin.  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  İçin bir oluşturucu ekleyin `CommentAdornmentProvider`. Sağlayıcı tarafından oluşturulur çünkü bu oluşturucu özel erişimi olması gereken `Create()` yöntemi. Oluşturucu ekler `OnBufferChanged` olay işleyicisine <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olay.  
  
    ```csharp  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  Ekleme `Create()` yöntemi.  
  
    ```csharp  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  Ekleme `Detach()` yöntemi.  
  
    ```csharp  
    public void Detach()  
    {  
        if (this.buffer != null)  
        {  
            //remove the Changed listener   
            this.buffer.Changed -= OnBufferChanged;  
            this.buffer = null;  
        }  
    }  
    ```  
  
8.  Ekleme `OnBufferChanged` olay işleyicisi.  
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. Eklemek için bir bildirim bir `CommentsChanged` olay.  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Oluşturma bir `Add()` kenarlığı eklemek için yöntemi.  
  
    ```csharp  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
        //Create a comment adornment given the span, author and text.  
        CommentAdornment comment = new CommentAdornment(span, author, text);  
  
        //Add it to the list of comments.   
        this.comments.Add(comment);  
  
        //Raise the changed event.  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
        if (commentsChanged != null)  
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));  
    }  
  
    ```  
  
11. Ekleme bir `RemoveComments()` yöntemi.  
  
    ```csharp  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith.   
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
            {  
                //Raise the change event to delete this comment.   
                if (commentsChanged != null)  
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));  
            }  
            else  
                keptComments.Add(comment);  
        }  
  
        this.comments = keptComments;  
    }  
    ```  
  
12. Ekleme bir `GetComments()` belirtilen anlık görüntü aralığı içinde tüm yorumları döndüren yöntem.  
  
    ```csharp  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. Adlı bir sınıf ekleyin `CommentsChangedEventArgs`aşağıdaki gibi.  
  
    ```csharp  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="manage-comment-adornments"></a>Açıklama Kenarlıklar yönetme  
 Açıklama kenarlığı manager kenarlığı oluşturur ve onu kenarlığı katmanına ekler. İçin dinler <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> olan geçiş yapabilir veya kenarlığı Sil olayları. Ayrıca için dinler `CommentsChanged` açıklamalar eklendiğinde veya kaldırıldığında, yorum kenarlığı sağlayıcı tarafından harekete geçirilen olay.  
  
1.  CommentAdornmentTest projeye bir sınıf dosyası ekleyin ve adlandırın `CommentAdornmentManager`.  
  
2.  Aşağıdaki `using` deyimleri.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  Adlı bir sınıf ekleyin `CommentAdornmentManager`.  
  
    ```csharp  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  Bazı özel alanlar ekleyin.  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  Yöneticiye abone olan bir oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> olayları ve ayrıca `CommentsChanged` olay. Yönetici tarafından statik örneği oluşturucusu özel olduğundan `Create()` yöntemi.  
  
    ```csharp  
    private CommentAdornmentManager(IWpfTextView view)  
    {  
        this.view = view;  
        this.view.LayoutChanged += OnLayoutChanged;  
        this.view.Closed += OnClosed;  
  
        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");  
  
        this.provider = CommentAdornmentProvider.Create(view);  
        this.provider.CommentsChanged += OnCommentsChanged;  
    }  
    ```  
  
6.  Ekleme `Create()` yönteminin bir sağlayıcıyı alır veya bir gerekirse oluşturur.  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  Ekleme `CommentsChanged` işleyici.  
  
    ```csharp  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
    {  
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag).   
        if (e.CommentRemoved != null)  
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);  
  
        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout).   
        if (e.CommentAdded != null)  
            this.DrawComment(e.CommentAdded);  
    }  
    ```  
  
8.  Ekleme <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> işleyici.  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Ekleme <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> işleyici.  
  
    ```csharp  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        //Get all of the comments that intersect any of the new or reformatted lines of text.  
        List<CommentAdornment> newComments = new List<CommentAdornment>();  
  
        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.    
        //Use the latter to find the comments that intersect the new or reformatted lines of text.   
        foreach (Span span in e.NewOrReformattedSpans)  
        {  
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));  
        }  
  
        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not.   
        //Sort the list and skip duplicates.  
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });  
  
        CommentAdornment lastComment = null;  
        foreach (CommentAdornment comment in newComments)  
        {  
            if (comment != lastComment)  
            {  
                lastComment = comment;  
                this.DrawComment(comment);  
            }  
        }  
    }  
    ```  
  
10. Açıklama çizen özel bir yöntem ekleyin.  
  
     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Açıklama kenarlığı eklemek için menü komutunu kullanın.  
 Menü komutunu uygulayarak bir yorum kenarlığı oluşturmak için kullanabileceğiniz `MenuItemCallback` VSPackage yöntemi.  
  
1.  MenuCommandTest proje aşağıdaki başvuruları ekleyin:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  Açık *AddAdornment.cs* dosyasını açıp aşağıdaki `using` deyimleri.  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  Silme `ShowMessageBox()` yöntemi ve aşağıdaki komut işleyicisi ekleyin.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  Etkin bir görünüm elde edin, kodu ekleyin. Edinmeniz gerekir `SVsTextManager` etkin almak için Visual Studio Shell `IVsTextView`.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  Bu metin görünümünü bir düzenleyici metni görünümü örneği ise, kendisine çevirebilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> arabirim ve ardından <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> ve onun ilişkili <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Kullanım <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> çağrılacak `Connector.Execute()` açıklama kenarlığı sağlayıcısını alır ve kenarlığı ekler yöntemi. Komut işleyici, artık şu kod gibi görünmelidir:  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
        IVsUserData userData = vTextView as IVsUserData;  
         if (userData == null)  
        {  
            Console.WriteLine("No text view is currently open");  
                            return;  
        }  
        IWpfTextViewHost viewHost;  
        object holder;  
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;  
        userData.GetData(ref guidViewHost, out holder);  
        viewHost = (IWpfTextViewHost)holder;  
        Connector.Execute(viewHost);  
    }  
    ```  
  
6.  AddAdornmentHandler yöntemi AddAdornment oluşturucuda AddAdornment komut işleyicisi olarak ayarlayın.  
  
    ```csharp  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup test  
  
1.  Çözümü derleyin ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir.  
  
2.  Bir metin dosyası oluşturun. Bir metin yazın ve ardından bu seçeneği belirleyin.  
  
3.  Üzerinde **Araçları** menüsünde tıklatın **ekleme kenarlığı çağırma**. Balon metin penceresinin sağ tarafında görüntülenmelidir ve aşağıdaki metne benzer bir metin içermelidir.  
  
     Kullanıcıadınız  
  
     Fourscore...  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: bir içerik türü için bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)