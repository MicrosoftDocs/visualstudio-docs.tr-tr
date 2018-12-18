---
title: Düzenleyici içeri aktarımları | Microsoft Docs
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
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f82815871f59dfcf4d384157a9461388e96d05e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759022"
---
# <a name="editor-imports"></a>Düzenleyici İçeri Aktarımları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir dizi Düzenleyicisi Hizmetleri, fabrikaları ve erişim farklı türde çekirdek Düzenleyici uzantınızı sağlayan aracıları içeri aktarabilirsiniz. Örneğin, aktarabilirsiniz <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> sunmak için bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> için belirli bir içerik türü. (Bu Gezgin, bir metin arabelleği farklı türde aramaları gerçekleştirme sağlar.)  
  
 Bir düzenleyici içeri aktarma kullanılacak bir alan veya özellik bir Yönetilen Genişletilebilirlik Çerçevesi bileşen bölümü dışarı aktaran bir sınıfın aktarmadan.  
  
> [!NOTE]
>  Yönetilen Genişletilebilirlik Çerçevesi hakkında daha fazla bilgi için bkz: [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Söz dizimi içeri aktarma  
 Aşağıdaki örnek, düzenleyici içeri aktarma seçenekleri factory hizmeti gösterir.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Hizmetinden bir alan ve bir özelliği içe aktarmak istiyorsanız, onu ayarlamanız gerekir `null` bildiriminde bir değişkene atama değil hakkında Derleyici uyarılarını önlemek için:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 İçeri aktarmalar kullanarak daha fazla örnek için aşağıdaki izlenecek yollara bakın:  
  
 [İzlenecek Yol: Dış Boşluk Karakteri Oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [İzlenecek Yol: Metin Görünümünü Özelleştirme](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [İzlenecek Yol: Metni Vurgulama](../extensibility/walkthrough-highlighting-text.md)  
  
 [İzlenecek Yol: HızlıBilgi Araç İpuçlarını Görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [İzlenecek Yol: İmza Yardımını Görüntüleme](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [İzlenecek Yol: Deyim Tamamlamayı Görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [İzlenecek yol: Akıllı etiketler görüntüleme](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Hizmet sağlayıcısı içeri aktarma  
 Ayrıca Al bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (Microsoft.VisualStudio.Shell.Immutable.10.0 derlemede bulunan) Visual Studio hizmetlerine erişim elde etmek için aynı şekilde:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Bkz: [izlenecek yol: Düzenleyici uzantısından DTE nesnesine erişme](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) daha fazla bilgi için.  
  
## <a name="services"></a>Hizmetler  
 Düzenleyici, bir hizmet sağlayan ve birden çok bileşen arasında paylaşılan genellikle tek varlıklar hizmetleridir.  
  
|{1&gt;İçeri Aktar&lt;1}|Sağlar|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Dosya uzantıları arasındaki ilişki ve <xref:Microsoft.VisualStudio.Utilities.IContentType> nesneleri.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Koleksiyonu <xref:Microsoft.VisualStudio.Utilities.IContentType> nesneleri.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> Nesneleri|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Birçok Düzenleyicisi bağdaştırıcısı nesneler:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> verilen metni görünümü için nesne.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Bir <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> farklılıklar.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Bir <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> farklılıklar.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> veya <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> kümesinin <xref:Microsoft.VisualStudio.Text.ITextBuffer> nesneleri.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> için bir <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Bir <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Koleksiyonunu tutar <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> nesneleri.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> için bir metin arabelleği.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> metni görünümü.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> Belirtilen kapsam için.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> metni görünümü.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Bir <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Otomatik girintili yazma alır <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> nesneleri.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Yöneten <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> için bir <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Anlık görüntü yayılma kümesinden RTF biçimlendirilmiş metin üretir.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> görünümde metin satırlarını biçimlendirme.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> nesnesi bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Bir metin anlık görüntüyü arar.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> için bir <xref:Microsoft.VisualStudio.Text.ITextBuffer> tarafından <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Bir <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> metni görünümü.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standart bir karakter kümesi.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Klavye ile işleme izler.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standart <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> nesneleri.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Metin arabelleği arasındaki ilişkiyi tutar ve <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> nesneleri.|  
  
## <a name="other-imports"></a>Diğer içeri aktarmalar  
 Sağlayıcı üreteçlerinin ve aracıya genellikle birden çok bileşeni birden çok örneği olan varlıklardır.  
  
|{1&gt;İçeri Aktar&lt;1}|Sağlar|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Bir <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> türü <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) belirtilen arabellek için.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Bir metin işaretçisi etiketlerde (bir <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> türü <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Bir <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> için bir verilen <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)

