---
title: Tek ve birden çok sekme görünümleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23feeaee14e6a149ad385c9f5e4a0c4b41be1e86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142990"
---
# <a name="single-and-multi-tab-views"></a>Tek ve birden çok sekme görünümleri
Bir düzenleyici farklı türlerde görünümler oluşturabilirsiniz. Bir örnek kod düzenleyicisini, başka bir form tasarımcısı.  
  
 Bir çoklu sekmeli birden çok sekme bulunur bir görünüm görünümüdür. Örneğin, HTML düzenleyicisi altındaki iki sekme bulunur: **tasarım** ve **kaynak**, her bir mantıksal görünümü. Diğer web sayfası oluşur HTML'yi görüntülerken Tasarım görünümüne işlenmiş bir web sayfası görüntülenir.  
  
## <a name="accessing-physical-views"></a>Fiziksel görünümleri erişme  
 Fiziksel görünümler her bir görünümünü kodu veya bir form gibi arabelleği temsil eden belge görünümü nesneleri barındırır. Buna göre her belge görünüm nesnesi (fiziksel görünüm dize olarak bilinen bir şey tarafından tanımlanan) fiziksel bir görünüm ve genellikle tek bir mantıksal görünüm vardır.  
  
 Bazı durumlarda, iki veya daha fazla mantıksal görünüm fiziksel bir görünüm yine de sahip olabilir. Bazı örnekler şunlardır: yan yana görünümlerle bölünmüş penceresine sahip bir düzenleyici ya da bir GUI/Tasarım görünümü ve bir kod arka plan--biçimli görünümü bir form tasarımcısı.  
  
 Tüm kullanılabilir fiziksel görünümlerinin erişmek düzenleyicinizi etkinleştirmek için her Düzenleyici üreteci oluşturabilirsiniz belge görünümü nesne türü için bir benzersiz fiziksel görünüm dize oluşturmanız gerekir. Örneğin, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Düzenleyici üreteci görünümü nesneleri için bir kod ve forms Tasarımcısı penceresinde belge oluşturabilir.  
  
## <a name="creating-multi-tabbed-views"></a>Çoklu sekmeli görünümler oluşturma  
 Bir belge görünüm nesnesi dizesini benzersiz fiziksel görüntüle aracılığıyla fiziksel bir görünümle ilişkili olsa, farklı şekillerde verilerinin görüntülenmesi etkinleştirmek için fiziksel görünümü içinde birden fazla sekme yerleştirebilirsiniz. Bu yapılandırmada çoklu sekmeli, tüm sekmeler aynı fiziksel görünüm dizesiyle ilişkilendirilir, ancak her sekme farklı bir mantıksal görünüm GUID verilir.  
  
 Bir düzenleyici için çoklu sekmeli bir görünüm oluşturmak için uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> arabirim ve farklı bir mantıksal görünüm GUID ilişkilendirmek (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) her sekme ile oluşturduğunuz.  
  
 Visual Studio HTML Düzenleyicisi'ni çok sekmesi görünümü bir düzenleyiciyle örneğidir. Bunun **tasarım** ve **kaynak** sekmeleri. Bunu etkinleştirmek için farklı bir mantıksal görünüm her sekme ile ilişkilendirilen `LOGICALVIEWID_TextView` için **tasarım** sekmesi ve `LOGICALVIEWID_Code` için **kaynak** sekmesi.  
  
 Uygun mantıksal görünümü belirterek, bir VSPackage bir form tasarlarken, kod düzenleme veya kodda hata ayıklama gibi belirli bir amaç için karşılık gelen görünümü erişebilir. Ancak, windows birini gerekir tanımlanır tarafından NULL dize ve bu birincil mantıksal görünümüne karşılık gelmelidir (`LOGVIEWID_Primary`).  
  
 Kullanılabilir mantıksal görünümü değerler ve bunların kullanılması aşağıdaki tabloda listelenmektedir.  
  
|LOGVIEWID GUID|Önerilen kullanın|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Düzenleyici üreteci varsayılan/birincil görünümü.<br /><br /> Bu değer tüm Düzenleyicisi oluşturucuları desteklemesi gerekir. Bu görünüm, fiziksel görünüm dize olarak boş bir dize kullanmanız gerekir. En az bir mantıksal görünümü bu değerine ayarlamanız gerekir.|  
|`LOGVIEWID_Debugging`|Hata ayıklama görünümü. Genellikle, `LOGVIEWID_Debugging` aynı görünüm olarak eşlendiğini `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Görünüm başlatılan tarafından **görünümü kodu** komutu.|  
|`LOGVIEWID_Designer`|Görünüm başlatılan tarafından **formu görüntüle** komutu.|  
|`LOGVIEWID_TextView`|Metin Düzenleyicisi'ni görüntüleyin. Bu döndüren görünümdür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, hangi erişebilirsiniz gelen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Kullanıcının hangi kullanılacak görüntülemek seçmesini ister.|  
|`LOGVIEWID_ProjectSpecificEditor`|Geçirilen **birlikte Aç** iletişim kutusu<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> ne zaman kullanıcı "(Proje varsayılan düzenleyici)" giriş seçer.|  
  
 Mantıksal görünüm GUID'ler olsa da Genişletilebilir, yalnızca sizin VSPackage tanımlanan mantıksal görünümü GUID'leri kullanabilirsiniz.  
  
 Kapatma işlemi, Visual Studio Düzenleyici üreteci ve böylece bu çözümü yeniden açıldığında belge pencereleri yeniden açmak için kullanılabilir belge penceresi ile ilişkili fiziksel görünüm dizelerinin GUID korur. Bir çözüm kapatıldığında açık olan windows çözüm (.suo) dosyasında kalıcıdır. Bu değerler karşılık `VSFPROPID_guidEditorType` ve `VSFPROPID_pszPhysicalView` geçirilen değerleri `propid` parametresinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bu kod parçacığında gösterilmektedir nasıl <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> uygulayan bir görünüm erişmek için kullanılan nesne `IVsCodeWindow`. Bu durumda, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> çağırmak için kullanılan hizmet <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> ve istek `LOGVIEWID_TextView`, pencere çerçevesi için bir işaretçi alır. Belge görünüm nesnesi için bir işaretçi çağırılarak alınır <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> ve değerini belirterek `VSFPROPID_DocView`. Belge Görünümü nesnesinden `QueryInterface` için adlı `IVsCodeWindow`. Bu durumda bir metin düzenleyicisi döndürülür ve bu nedenle belge görünüm nesnesi döndürülen içinde beklenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> kod penceresi bir yöntemdir.  
  
```cpp  
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
 [Birden çok belge görünümleri destekleme](../extensibility/supporting-multiple-document-views.md)   
 [Nasıl yapılır: veri belgelemek için görünümler ekleme](../extensibility/how-to-attach-views-to-document-data.md)   
 [Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../extensibility/creating-custom-editors-and-designers.md)