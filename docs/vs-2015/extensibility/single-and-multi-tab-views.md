---
title: Tek ve çoklu sekme görünümleri | Microsoft Docs
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
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8231581761199be4df9c368494fb27bdc7926c51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748990"
---
# <a name="single-and-multi-tab-views"></a>Tek ve Çoklu Sekme Görünümleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı türde bir düzenleyici oluşturabilirsiniz. Bir örnek bir kod düzenleyicisi penceresi, başka bir form tasarımcısı.  
  
 Birden çok sekmeli bir görünüm, birden çok sekme bulunur bir görünümüdür. Örneğin, HTML düzenleyicisinin alt kısmında iki sekme bulunur: **tasarım** ve **kaynak**, her bir mantıksal görünümü. Tasarım görünümü diğer web sayfası oluşturan HTML görüntüler işlenen bir web sayfası görüntülenir.  
  
## <a name="accessing-physical-views"></a>Fiziksel görünümler erişme  
 Fiziksel görünümler her veri arabellekteki kod ya da bir form gibi bir görünümünü temsil eden belge görünümü nesneleri barındırır. Buna göre her belge görünümü nesnesi (fiziksel görünüm dize olarak bilinen bir şey tarafından tanımlanır) fiziksel bir görünümü ve genellikle tek bir mantıksal görünüm vardır.  
  
 Bazı durumlarda, iki veya daha fazla mantıksal görünüm fiziksel bir görünüm yine de sahip olabilir. Yan yana görünümlere sahip bir bölünmüş pencere olan bir düzenleyici veya bir GUI/Tasarım görünümü ve kod-plan--form görünümü bir Form Tasarımcısı bazı örnekler verilmiştir.  
  
 Tüm kullanılabilir fiziksel görünümleri erişmek üzere etkinleştirmek için her Düzenleyicisi Fabrika oluşturabilirsiniz belge görünümü nesne türü için bir benzersiz fiziksel görünüm dize oluşturmanız gerekir. Örneğin, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] görünüm nesneleri için bir kod penceresinde ve forms tasarımcı penceresi Düzenleyici fabrikası belge oluşturabilirsiniz.  
  
## <a name="creating-multi-tabbed-views"></a>Birden çok sekmeli görünümler oluşturma  
 Bir belge view nesnesinin benzersiz fiziksel görüntü dizesi aracılığıyla fiziksel görünümü ile ilişkilendirilmiş olması gerekir ancak farklı şekillerde veri izlenmesini etkinleştirmek için fiziksel görünümü içinde birden fazla sekme yerleştirebilirsiniz. Bu yapılandırmada birden çok sekmeli, tüm sekmeler aynı fiziksel görüntü dizesi ile ilişkilendirilir, ancak her sekme, farklı bir mantıksal görünüm GUID verilir.  
  
 Birden çok sekmeli bir görünüm için bir düzenleyici oluşturmak için uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> arabirim ve farklı bir mantıksal görünüm GUID ilişkilendirin (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) oluşturduğunuz her sekme ile.  
  
 Visual Studio HTML düzenleyici çoklu sekme görünümü bir düzenleyiciyle örneğidir. Sahip **tasarım** ve **kaynak** sekmeler. Bunu etkinleştirmek için farklı bir mantıksal görünüm her sekme ile ilişkilendirilen `LOGICALVIEWID_TextView` için **tasarım** sekmesi ve `LOGICALVIEWID_Code` için **kaynak** sekmesi.  
  
 VSPackage uygun mantıksal görünümü belirterek, bir form tasarlarken, kod düzenleme veya kodda hata ayıklama gibi belirli bir amaç için karşılık gelen görünüm erişebilirsiniz. Ancak, windows birini gerekir tanımlanır boş bir dize ve bunu birincil mantıksal görünümü karşılık gelmelidir (`LOGVIEWID_Primary`).  
  
 Aşağıdaki tabloda kullanılabilir mantıksal görünüm değerler ve kullanımları listeler.  
  
|LOGVIEWID GUID|Önerilen kullanım|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Düzenleyici üreteci varsayılan/ana görünümü.<br /><br /> Bu değer tüm Düzenleyici fabrikaları desteklemesi gerekir. Bu görünüm, fiziksel görünüm dize olarak boş bir dize kullanmanız gerekir. En az bir mantıksal görünüm bu değere ayarlamanız gerekir.|  
|`LOGVIEWID_Debugging`|Hata ayıklama görünümü. Genellikle, `LOGVIEWID_Debugging` eşlemeleri aynı görünüme `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Görünüm başlatılan tarafından **kodu görüntüle** komutu.|  
|`LOGVIEWID_Designer`|Görünüm başlatılan tarafından **formu görüntüle** komutu.|  
|`LOGVIEWID_TextView`|Metin Düzenleyicisi'ni görüntüleyin. Bu döndüren görünümdür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, hangi erişeceği gelen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Hangi kullanılacak görüntülemek seçmenizi ister.|  
|`LOGVIEWID_ProjectSpecificEditor`|Geçirilen **birlikte Aç** iletişim kutusu<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> ne zaman kullanıcı "(projenin varsayılan Düzenleyicisi)" giriş seçer.|  
  
 Mantıksal görünüm GUID'leri Genişletilebilir olsa da, VSPackage içinde tanımlanan mantıksal görünüm GUID'leri kullanabilirsiniz.  
  
 Kapanma durumunda, Visual Studio Düzenleyici fabrikası ve çözüm yeniden açıldığında belge pencereleri yeniden açmak için kullanılabilir, böylece belge penceresi ile ilişkili fiziksel görünüm dizelerinin GUID korur. Çözüm (.suo) dosyasında bir çözüm kapatıldığında, açık olan windows kalıcıdır. Bu değerleri karşılık `VSFPROPID_guidEditorType` ve `VSFPROPID_pszPhysicalView` geçirilen değerler `propid` parametresinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bu kod parçacığı gösterir nasıl <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> uygulayan bir görünüm erişmek için kullanılan nesne `IVsCodeWindow`. Bu durumda, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> hizmeti çağırmak için kullanılan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> ve istek `LOGVIEWID_TextView`, pencere çerçevesi için bir işaretçi alır. Belge Görünümü nesnesine bir işaretçi çağırılarak alınır <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> değerini belirterek `VSFPROPID_DocView`. Belge Görünümü nesnesinden `QueryInterface` için adlı `IVsCodeWindow`. Bu durumda bir metin düzenleyicisi döndürülür ve bu nedenle belge görünümü nesnesi döndürülen içinde beklenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> bir kod penceresinde bir yöntemdir.  
  
```cpp#  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md)   
 [Nasıl yapılır: belge verilerine görünüm ekleme](../extensibility/how-to-attach-views-to-document-data.md)   
 [Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../extensibility/creating-custom-editors-and-designers.md)

