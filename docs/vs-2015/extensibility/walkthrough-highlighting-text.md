---
title: 'İzlenecek yol: Metni vurgulama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4fad243b109cb8522f15e30d628d5eb27c09c07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790727"
---
# <a name="walkthrough-highlighting-text"></a>İzlenecek Yol: Metni Vurgulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçalarına oluşturarak farklı görsel efektler Düzenleyicisi'ne ekleyebilirsiniz. Bu izlenecek yol, bir metin dosyasındaki geçerli kelimenin her geçtiği vurgulamak gösterilmektedir. Bir sözcük, bir metin dosyasına birden fazla kez gerçekleşir ve giriş işaretini bir yineleme getirin, her oluşumu vurgulanır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF proje oluşturma  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `HighlightWordTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="defining-a-textmarkertag"></a>Bir TextMarkerTag tanımlama  
 Metin vurgulama ilk adımı için sınıfıdır <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ve onun görünümünü tanımlayın.  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Bir TextMarkerTag ve bir MarkerFormatDefinition tanımlamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın **HighlightWordTag**.  
  
2.  Aşağıdaki başvuruları ekleyin:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  Aşağıdaki ad alanlarını içeri aktarın.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using System.Threading;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Text.Tagging;  
    using Microsoft.VisualStudio.Utilities;  
    using System.Windows.Media;  
    ```  
  
4.  Devralınan bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ve adlandırın `HighlightWordTag`.  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  Devralınan bir ikinci sınıfı oluşturma <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, HighlightWordFormatDefinition adlandırın. Bu biçim tanımını, etiket için kullanmak için aşağıdaki özniteliklere sahip dışarı aktarmanız gerekir:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: etiketler bu biçim başvurmak için bunu kullanın  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Bu biçim kullanıcı Arabiriminde görüntülenecek neden olur  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  Görünen adına ve görünümüne HighlightWordFormatDefinition Oluşturucusu tanımlayın. Ön plan özelliği kenarlık rengi açıklarken dolgu rengi arka plan özelliği tanımlar.  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  HighlightWordTag oluşturucusunun içinde yeni oluşturduğunuz biçimlendirme tanımında adını geçirin.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Bir ITagger uygulama  
 Sonraki adım uygulamaktır <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> arabirimi. Bu arabirim, verilen metin arabelleği, metni vurgulama sağlayan etiketler ve diğer görsel efektler atar.  
  
#### <a name="to-implement-a-tagger"></a>Bir etiketlerde uygulamak için  
  
1.  Uygulayan bir sınıf oluşturma <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> türü `HighlightWordTag`ve adlandırın `HighlightWordTagger`.  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  Aşağıdaki özel alanlar ve Özellikler sınıfa ekleyin:  
  
    -   Bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, geçerli metin görünüme karşılık gelir.  
  
    -   Bir <xref:Microsoft.VisualStudio.Text.ITextBuffer>, metin görünümünü altını metin arabelleğine karşılık gelir.  
  
    -   Bir <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, metni bulmak için kullanılır.  
  
    -   Bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, metin alanı içinde gezinmek için yöntemleri vardır.  
  
    -   A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, vurgulamak için sözcükler kümesini içerir.  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, geçerli kelimenin karşılık gelir.  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, geçerli giriş işareti konumuna karşılık gelir.  
  
    -   Bir kilit nesnesi.  
  
    ```csharp  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  Daha önce listelenen özelliklerini başlatır ve ekleyen bir oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> olay işleyicileri.  
  
    ```csharp  
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,  
    ITextStructureNavigator textStructureNavigator)  
    {  
        this.View = view;  
        this.SourceBuffer = sourceBuffer;  
        this.TextSearchService = textSearchService;  
        this.TextStructureNavigator = textStructureNavigator;  
        this.WordSpans = new NormalizedSnapshotSpanCollection();  
        this.CurrentWord = null;  
        this.View.Caret.PositionChanged += CaretPositionChanged;  
        this.View.LayoutChanged += ViewLayoutChanged;  
    }  
  
    ```  
  
4.  Her ikisi de arama olay işleyicileri `UpdateAtCaretPosition` yöntemi.  
  
    ```csharp  
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        // If a new snapshot wasn't generated, then skip this layout   
        if (e.NewSnapshot != e.OldSnapshot)  
        {  
            UpdateAtCaretPosition(View.Caret.Position);  
        }  
    }  
  
    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)  
    {  
        UpdateAtCaretPosition(e.NewPosition);  
    }  
    ```  
  
5.  Ayrıca eklemelisiniz bir `TagsChanged` güncelleştirme yöntemi tarafından çağrılacak olay.  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs#10)]
     [!code-vb[VSSDKHighlightWordTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb#10)]  
  
6.  `UpdateAtCaretPosition()` Yöntemi imleç nereye yerleştirilir ve bir listesini oluşturur sözcüğüne aynı olan metin arabelleğinde her sözcük bulur <xref:Microsoft.VisualStudio.Text.SnapshotSpan> sözcüğün geçtiği için karşılık gelen nesneleri. Ardından `SynchronousUpdate`, oluşturursa `TagsChanged` olay.  
  
    ```csharp  
    void UpdateAtCaretPosition(CaretPosition caretPosition)  
    {  
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);  
  
        if (!point.HasValue)  
            return;  
  
        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it   
        if (CurrentWord.HasValue  
            && CurrentWord.Value.Snapshot == View.TextSnapshot  
            && point.Value >= CurrentWord.Value.Start  
            && point.Value <= CurrentWord.Value.End)  
        {  
            return;  
        }  
  
        RequestedPoint = point.Value;  
        UpdateWordAdornments();  
    }  
  
    void UpdateWordAdornments()  
    {  
        SnapshotPoint currentRequest = RequestedPoint;  
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();  
        //Find all words in the buffer like the one the caret is on  
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);  
        bool foundWord = true;  
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
        if (!WordExtentIsValid(currentRequest, word))  
        {  
            //Before we retry, make sure it is worthwhile   
            if (word.Span.Start != currentRequest  
                 || currentRequest == currentRequest.GetContainingLine().Start  
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))  
            {  
                foundWord = false;  
            }  
            else  
            {  
                // Try again, one character previous.    
                //If the caret is at the end of a word, pick up the word.  
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);  
  
                //If the word still isn't valid, we're done   
                if (!WordExtentIsValid(currentRequest, word))  
                    foundWord = false;  
            }  
        }  
  
        if (!foundWord)  
        {  
            //If we couldn't find a word, clear out the existing markers  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);  
            return;  
        }  
  
        SnapshotSpan currentWord = word.Span;  
        //If this is the current word, and the caret moved within a word, we're done.   
        if (CurrentWord.HasValue && currentWord == CurrentWord)  
            return;  
  
        //Find the new spans  
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);  
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;  
  
        wordSpans.AddRange(TextSearchService.FindAll(findData));  
  
        //If another change hasn't happened, do a real update   
        if (currentRequest == RequestedPoint)  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);  
    }  
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7.  `SynchronousUpdate` Zaman uyumlu bir güncelleştirme gerçekleştirir `WordSpans` ve `CurrentWord` özellikleri ve harekete geçirirse `TagsChanged` olay.  
  
    ```vb  
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)  
    {  
        lock (updateLock)  
        {  
            if (currentRequest != RequestedPoint)  
                return;  
  
            WordSpans = newSpans;  
            CurrentWord = newCurrentWord;  
  
            var tempEvent = TagsChanged;  
            if (tempEvent != null)  
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));  
        }  
    }  
    ```  
  
8.  Uygulamanız gereken <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> yöntemi. Bu yöntem bir koleksiyonunu alır <xref:Microsoft.VisualStudio.Text.SnapshotSpan> nesneleri ve etiket yayılma numaralandırmasını döndürür.  
  
     C# içinde bu yöntem geç değerlendirme (diğer bir deyişle, değerlendirme için yalnızca tek tek öğeleri erişildiğinde kümesi) sağlar ve yield yineleyici etiketleri uygulayın. Visual Basic'te bir listesine etiketler ekleyin ve bir liste döndürür.  
  
     Burada yöntem döndürür bir <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> "mavi" nesnesi <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, mavi bir arka plan sağlar.  
  
    ```csharp  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot   
        if (spans[0].Snapshot != wordSpans[0].Snapshot)  
        {  
            wordSpans = new NormalizedSnapshotSpanCollection(  
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));  
  
            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);  
        }  
  
        // First, yield back the word the cursor is under (if it overlaps)   
        // Note that we'll yield back the same word again in the wordspans collection;   
        // the duplication here is expected.   
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))  
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>Etiketlerde sağlayıcı oluşturma  
 Etiketlerde oluşturmak için uygulamanız gereken bir <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Bu sınıf bir MEF Bileşeni parçası olduğundan bu uzantı tanınan böylece doğru öznitelikleri ayarlamanız gerekir.  
  
> [!NOTE]
>  MEF hakkında daha fazla bilgi için bkz: [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-create-a-tagger-provider"></a>Etiketlerde sağlayıcısı oluşturmak için  
  
1.  Adlı bir sınıf oluşturun `HighlightWordTaggerProvider` uygulayan <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> , <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  İki Düzenleyici hizmet aktarmalısınız <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> ve <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, etiketlerde örneklemek için.  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> örneği döndürülecek yöntemi `HighlightWordTagger`.  
  
    ```csharp  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
 Bu kodu test etmek için HighlightWordTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Derleme ve HighlightWordTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası oluşturun ve içine sözcükleri yinelenir, bazı Örneğin, "hello hello hello" metni yazın.  
  
4.  "Hello" oluşumlarını birinde imleci getirin. Her oluşumu mavi renkle vurgulanmış olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

