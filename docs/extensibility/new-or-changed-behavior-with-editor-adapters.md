---
title: Yeni veya değiştirilen davranışı Düzenleyicisi bağdaştırıcısıyla | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2b32eeb110240cabfec5d81cc862611a0d32fe2
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639240"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Düzenleyici bağdaştırıcıları ile yeni veya değiştirilen davranışı
Visual Studio çekirdek Düzenleyicisi önceki sürümlerini karşı yazılmış kodu güncelleştirmekte olduğunuz ve yeni API kullanmak yerine Düzenleyicisi bağdaştırıcıları (veya dolgular) kullanmayı planlıyorsanız, düzenleyici bağdaştırıcılarının davranışta aşağıdaki farklar farkında olmalıdır önceki çekirdek Düzenleyici göre.  
  
## <a name="features"></a>Özellikler  
  
### <a name="use-setsite"></a>SetSite() kullanın  
 Çağırmalısınız <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> zaman işlemi metin arabelleğini metin görünümleri ve bunlar üzerinde herhangi bir işlem gerçekleştirmeden önce windows kod. Ancak, bu kullanırsanız, gerekli değildir <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> çünkü onları oluşturmak için bu hizmetin `Create()` kendilerini yöntemleri çağırmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
### <a name="host-ivscodewindow-and-ivstextview-in-your-own-content"></a>Konak IVsCodeWindow ve kendi içerik Ivstextview  
 Her ikisi de barındırabilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 modu ya da WPF modu kullanarak kendi içerik. Ancak, bazı farklar iki modda olduğunu aklınızda tutmanız gerekir.  
  
#### <a name="use-win32-and-wpf-versions-of-ivscodewindow"></a>Win32 ve WPF IVsCodeWindow sürümlerini kullanma  
 Kod Düzenleyicisi penceresi türetilir <xref:Microsoft.VisualStudio.Shell.WindowPane>, eski Win32 uygulayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirim yanı sıra yeni WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> arabirimi. Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> HWND tabanlı barındırma ortamı, yöntemini veya <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> WPF barındırma ortamı oluşturmak için yöntemi. Temel Düzenleyici her zaman WPF kullanır ancak bu bölme doğrudan kendi içeriğinize ekliyorsanız barındırma gereksinimlerinize uyan pencere bölmesi türünü oluşturabilirsiniz.  
  
#### <a name="use-win32-and-wpf-versions-of-ivstextview"></a>Win32 ve WPF Ivstextview sürümlerini kullanma  
 Ayarlayabileceğiniz bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 modu ya da WPF modu.  
  
 Bir düzenleyici fabrikası barındırıldığı bir HWND içinde varsayılan olarak bir metin görünümünü oluşturduğunda ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> bir HWND döndürür. Düzenleyicinin içinde WPF denetimi eklemek için bu modu kullanmamanız gerekir.  
  
 Metin görünümünü WPF moda ayarlanacak çağırmalısınız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> ve geçirin <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> başlatma biri olarak işaretler gibi `InitView` parametresi. Alabileceğiniz <xref:System.Windows.FrameworkElement> çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 WPF modu iki yolla Win32 modundan farklıdır. İlk olarak, metin görünümünü bir WPF bağlamında barındırılabilir. WPF bölmesinde atayarak erişebileceğiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> ve çağırma <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. İkinci olarak, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> hala yalnızca konumunu denetleyin ve odak üzerinde ayarlamak için bir HWND, ancak bu HWND kullanılabilir döndürür. Düzenleyici penceresinde nasıl boyar etkilemez çünkü bir WM_PAINT iletiye yanıt vermek için bu HWND kullanmamalıdır. Bu HWND yalnızca bağdaştırıcıları yoluyla yeni Düzenleyicisi kod geçişi kolaylaştırmak için mevcuttur. Kullanmamalısınız önerilen `VIF_NO_HWND_SUPPORT` bileşeniniz döndürüldüğü HWND sınırlamaları nedeniyle çalışmak bir HWND gerektiriyorsa `GetWindowHandle` bu modda çalışırken.  
  
#### <a name="pass-arrays-as-parameters-in-native-code"></a>Yerel kodda parametreler olarak diziler geçirin  
 API eski düzenleyicide bir dizi ve sayımına dahil parametrelere sahip birçok yöntem vardır. Örnekler şunlardır:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Yerel kodda bu yöntemleri çağırıyorsanız, aynı anda yalnızca bir öğe geçmesi gerekir. Birden fazla öğe geçirirseniz, arama, birincil birlikte çalışma uygulamasını sorunlar nedeniyle reddedilir.  
  
 Sorun gibi yöntemlerle daha karmaşık <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Bu yöntem her çağrıldığında yalnızca bu yöntem üç farklı işaretçi türleri ile üç kez çağırmak mümkün olmadığından yoksayılan işaretçi türleri, önceki listesini temizler. Yalnızca remedy, bu yöntem yalnızca yönetilen kodda çağırmaktır.  
  
#### <a name="threading"></a>İş Parçacığı Oluşturma  
 Her zaman arabellek bağdaştırıcısı UI iş parçacığından çağırmalısınız. Yönetilen kod içine arama COM hazırlama atlamak ve aramanız için UI iş parçacığı otomatik olarak sıralanmış değil bir yönetilen nesne arabellek bağdaştırıcısıdır.  Arka plan iş parçacığından arabellek bağdaştırıcısı çağırıyorsanız kullanmalısınız <xref:System.Windows.Threading.Dispatcher.Invoke%2A> veya benzer bir yöntem.  
  
#### <a name="lockbuffer-methods"></a>LockBuffer yöntemleri  
 Tüm LockBuffer() yöntemleri kullanım dışı bırakılmıştır. Örnekler şunlardır:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Olayları işleme  
 İşleme olayları desteklenmez. Bu olayları öneren bir yöntem çağrılırken bir hata kodu döndürmek yöntemin neden olur.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Artık, Commit() üzerinde harekete. Bunun yerine her metin değişikliğe kov.  
  
#### <a name="text-markers"></a>Metin işaretçileri  
 Çağırmalısınız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> üzerinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> nesneleri bunları kaldırdığınızda. Önceki sürümlerde, yalnızca işaretlerinin sürüm gerekli.  
  
#### <a name="line-numbers"></a>Satır numaraları  
 Çeşitli yöntemlerin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>satır numaralarını karşılık gelen temel alınan arabellek satır numaraları, olmayan satır numaraları anahat oluşturma ve sözcük kaydırma, Visual Studio 2008 olduğu gibi yalıtılması.  
  
 Etkilenen yöntemleri (listesi değil kapsamlı) şunları içerir:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Anahat Oluşturma  
 İstemcileri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> kullanılarak eklenen bu anahat bölgeleri görürsünüz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>veya <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Düzenleyici bağdaştırıcıları aracılığıyla ekli değil çünkü geçici bölgeleri görmezsiniz. Benzer şekilde, bu istemciler Düzenleyicisi bağdaştırıcıları yerine yeni Kod Düzenleyicisi'ni kullanma (C# ve C++ dahil) dilleri tarafından eklenen bölgeleri anahat oluşturma görmezsiniz.  
  
#### <a name="line-heights"></a>Satır yüksekliklerini  
 Yeni düzenleyicide metin satırlarını yazı tipi boyutunu ve diğer satırlara göre satır taşıyabilir olası satır dönüşümler bağlı olarak farklı yüksekliklerini olabilir. Satır yüksekliği gibi yöntemler tarafından döndürülen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> hiçbir satırı dönüşümler uygulanan varsayılan yazı tipi boyutunu kullanarak bir satırın yüksekliği. Bu yüksekliği olabilir veya bir çizgi görünümünde gerçek yüksekliğini yansıtmayabilir.  
  
#### <a name="eventing-and-undo"></a>Olay ve geri alma  
 Yeni Düzenleyici'de görünümü oluşturma ve olayları sürekli oluşturma gibi işlemler gerçekleştirmeye devam eder. İşlem geri alma küme açık olduğunda bile devam edin. Bu davranış, kadar Kapanıştan sonra bu işlemleri geri kümesinin gerçekleştirmedi eski görünümleri farklıdır.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Yöntemi başarısız olur ya da uygulamayan bir sınıfta geçirirseniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> veya <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Özel bir Win32 sahip tarafından çizilmiş açılan pencereler artık desteklenmemektedir.  
  
#### <a name="smarttags"></a>Akıllı etiketler  
 Akıllı etiketler, oluşturulan için bağdaştırıcı desteği yoktur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> arabirimleri.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> Uygulanmadı.  
  
## <a name="unimplemented-methods"></a>Uygulanmayan yöntemleri  
 Bazı yöntemler metin arabelleği bağdaştırıcısı, metin view bağdaştırıcısı ve metin katmanı bağdaştırıcısı uygulanmış henüz.  
  
|Arabirim|Uygulanmadı|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` Uygulanmadı.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> Anahat oluşturma kullanıcı Arabirimi tarafından yok sayıldı ancak bağdaştırıcılarında uygulanır.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> Anahat oluşturma kullanıcı Arabirimi tarafından yok sayıldı ancak bağdaştırıcılarında uygulanır.|