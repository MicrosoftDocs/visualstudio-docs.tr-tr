---
title: 'İzlenecek yol: ampul önerilerini görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16b9d56daab6eda1ef1cd9c31d8cc4d720f9a08e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875898"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>İzlenecek yol: ampul önerilerini görüntüleme
Ampuller Visual Studio düzenleyicisinde bir dizi eylemi, örneğin, yerleşik kod Çözümleyicileri veya kodu yeniden düzenleme tarafından tanımlanan sorunlar için düzeltmeler gösterecek şekilde genişletmek simgeler ' dir.  
  
 Visual C# ve Visual Basic düzenleyicilerde yazma ve kendi kod Çözümleyicileri otomatik olarak ampuller görüntüleyen eylemlerle paketlemek için .NET derleyici Platformu ("Roslyn") kullanabilirsiniz. Daha fazla bilgi için bkz.:  
  
- [Nasıl yapılır: bir C# tanılama ve kod düzeltmenizi yazın](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
- [Nasıl yapılır: Visual Basic tanılama ve kod düzeltmenizi yazın](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
  Diğer diller C++ gibi ampuller gibi bir öneri, bu işlevin bir saplama uygulaması oluşturmak için bazı hızlı eylemler için de sağlar.  
  
  İşte bir ampul gibi görünüyor. Geçersiz olduğunda bir Visual Basic veya Visual C# projesinde, kırmızı dalgalı bir değişken adı altında görünür. Geçersiz tanımlayıcı fare imleci bir ampul görünür.  
  
  ![Ampul](../extensibility/media/lightbulb.png "ampul")  
  
  Ampul tarafından aşağı oka tıklayın, bir dizi önerilen eylemi, seçili eylem önizlemesi ile birlikte görüntülenir. Bu durumda, eylem çalışırsa, kodunuzda yapılan değişiklikleri gösterir.  
  
  ![Ampul Önizleme](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
  Ampuller kendi önerilen eylemler sağlamak için kullanabilirsiniz. Örneğin, açma küme ayraçları yeni bir satıra Taşı veya bunları önceki satır sonuna taşı eylemleri sağlayabilir. Aşağıdaki örneklerde, geçerli sözcüğü görünür bir ampul oluşturma işlemi gösterilmektedir ve iki sahip önerilen eylemler: **büyük harfe Dönüştür** ve **küçük harfe Dönüştür**.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) proje oluşturma  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `LightBulbTest`.  
  
2.  Ekleme bir **Düzenleyicisi sınıflandırıcı** projeye öğe şablonu. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
4.  Proje şu başvuruyu ekleyin ve ayarlayın **Yereli Kopyala** için `False`:  
  
     *Microsoft.VisualStudio.Language.Intellisense*  
  
5.  Yeni bir sınıf dosyası ekleyin ve adlandırın **LightBulbTest**.  
  
6.  Aşağıdaki using deyimlerini:  
  
    ```csharp  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implement-the-light-bulb-source-provider"></a>Ampul kaynak sağlayıcısını uygulama  
  
1.  İçinde *LightBulbTest.cs* LightBulbTest sınıfını silmek, sınıf dosyası. Adlı bir sınıf ekleyin **TestSuggestedActionsSourceProvider** uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Adlı dışarı **Test Önerilen Eylemler** ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Kaynak sağlayıcısı sınıf içinde alma <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ve bir özellik olarak ekleyin.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> döndürülecek yöntemi bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> nesne. Kaynak, sonraki bölümde ele alınmıştır.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null || textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implement-the-isuggestedactionsource"></a>ISuggestedActionSource uygulayın  
 Önerilen eylem kaynak önerilen eylemleri kümesini toplamak ve doğru bağlamda eklemeden sorumludur. Bu durumda, bağlam geçerli sözcüğü ve önerilen eylemleri **UpperCaseSuggestedAction** ve **LowerCaseSuggestedAction**, aşağıdaki bölümde açıklanan.  
  
1.  Bir sınıf ekleyin **TestSuggestedActionsSource** uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Önerilen eylemi kaynak sağlayıcısı, metin arabelleği ve metin görünümünü özel, salt okunur alanlar ekleyin.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Özel alanları ayarlayan bir oluşturucu ekleyin.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  İmlecin altındaki sözcüğünü döndüren özel bir yöntem ekleyin. Aşağıdaki yöntem, imleci geçerli konumda arar ve metin yapısına Gezgin sözcük kapsamı için sorar. İmleç bir sözcük ise <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> out parametresi olarak döndürülmüştür; Aksi takdirde `out` parametresi `null` ve yöntemi `false`.  
  
    ```csharp  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> yöntemi. Düzenleyici ampul görüntülenecek öğrenmek için bu yöntemi çağırır. Bu çağrı genellikle, örneğin, imleç bir satırından getirdiğinde veya bir hata dalgalı fare geldiğinde yapılır. Bu yöntem çalışırken, gerçekleştirmek diğer UI işlemlerine izin vermek üzere uyumsuzdur. Çoğu durumda bu yöntem işlenmesi biraz zaman alabilir. Bu nedenle, bazı ayrıştırma ve geçerli satırın analizi gerçekleştirmek gerekir.  
  
     Bu uygulama, zaman uyumsuz olarak alır <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> ve bu boşluklar dışında metin içerip içermediğine olduğu gibi önemli ölçüde olup olmadığını belirler.  
  
    ```csharp  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> bir dizi döndüren yöntemi <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> içeren farklı nesneleri <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> nesneleri. Ampul genişletildiğinde bu yöntem çağrılır.  
  
    > [!WARNING]
    >  Emin olmanız gerekir uygulamaları `HasSuggestedActionsAsync()` ve `GetSuggestedActions()` olan tutarlı; are, `HasSuggestedActionsAsync()` döndürür `true`, ardından `GetSuggestedActions()` görüntülemek için bazı eylemler olması gerekir. Çoğu durumda, `HasSuggestedActionsAsync()` hemen önce çağrılır `GetSuggestedActions()`, ancak bu her zaman böyle değildir. Örneğin, kullanıcı tuşlarına basarak ampul eylemleri çağırır (**CTRL +** .) yalnızca `GetSuggestedActions()` çağrılır.  
  
    ```csharp  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Tanımlayan bir `SuggestedActionsChanged` olay.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Uygulama tamamlamak için uygulamaları ekleme `Dispose()` ve `TryGetTelemetryId()` yöntemleri. Telemetri, böylece sadece dönüş yapmak istemediğiniz `false` ve GUID kümesine `Empty`.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implement-light-bulb-actions"></a>Ampul eylemleri uygulayın  
  
1.  Projede bir başvuru ekleyin *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* ayarlayıp **Yereli Kopyala** için `False`.  
  
2.  İki sınıf oluşturma ilk adlı `UpperCaseSuggestedAction` ve ikinci adlı `LowerCaseSuggestedAction`. Her iki sınıfları uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Bir çağrı dışında her iki sınıflar benzer <xref:System.String.ToUpper%2A> ve diğer çağrılar <xref:System.String.ToLower%2A>. Yalnızca büyük harf Eylem sınıfına aşağıdaki adımları kapsar, ancak her iki sınıf uygulamalıdır. Büyük harf eylem olarak küçük eylemi uygulamak için bir desen uygulamak için adımları kullanın.  
  
3.  Aşağıdaki using deyimlerini bu sınıflar için:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Bir özel alan kümesi bildirin.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Alanları ayarlayan bir oluşturucu ekleyin.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> olan eylem Önizleme görünmesi yöntemi.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> boş olan döndürecek şekilde yöntemi <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> sabit listesi.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Özellikleri aşağıdaki gibi uygulayın.  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> aralık içindeki metni kendi büyük harf eşdeğeri ile değiştirerek yöntemi.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Ampul işlemi **Invoke** yöntemi uygulamanın UI göstermesi için beklenmiyor. Eylem (örneğin bir önizleme ya da seçimi iletişim) yeni kullanıcı Arabirimi getirirseniz, doğrudan içinden kullanıcı Arabirimi gösterme **Invoke** yöntemi ancak bunun yerine döndürme sonra kullanıcı arabirimini görüntülemek için zamanlama **Invoke**.  
  
10. Uygulama tamamlamak için ekleme `Dispose()` ve `TryGetTelemetryId()` yöntemleri.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Aynı şeyi yapmak unutmayın `LowerCaseSuggestedAction` görünen metni değiştirme "Dönüştür '{0}' küçük harfe" ve çağrı <xref:System.String.ToUpper%2A> için <xref:System.String.ToLower%2A>.  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup test  
 Bu kodu test etmek için LightBulbTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası oluşturun ve bir metin yazın. Metnin soluna bir ampul de görürsünüz.  
  
     ![Ampul test](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Ampul gelin. Aşağı ok görmeniz gerekir.  
  
5.  Ampule tıkladığınızda, seçili eylem önizlemesiyle birlikte iki önerilen eylemleri görüntülemelidir.  
  
     ![Ampul, genişletilmiş test](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  İlk eylem tıklarsanız, geçerli kelimenin tüm metni büyük harfe dönüştürülmelidir. İkinci eylem tıklarsanız, tüm metni için küçük dönüştürülmelidir.  
  
