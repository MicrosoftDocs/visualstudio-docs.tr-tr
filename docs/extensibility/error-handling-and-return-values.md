---
title: Hata işleme ve dönüş değerleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97e5fbd68a82a74112f884a8091992c1fd6ba6ae
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370750"
---
# <a name="error-handling-and-return-values"></a>Hata işleme ve dönüş değerleri
VSPackages ve COM aynı mimariye hataları için kullanın. `SetErrorInfo` Ve `GetErrorInfo` işlevleri Win32 uygulama programlama arabirimi (API) bir parçasıdır. Tümleşik geliştirme ortamında (IDE) herhangi bir VSPackage alırken bir hata bildirimi, bu genel Win32 API'ları zengin hata bilgileri kaydetmek için çağırabilirsiniz. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Hata bilgilerini yönetmek için birlikte çalışma derlemelerini sağlar.  
  
## <a name="interop-methods"></a>Birlikte çalışma yöntemi  
 Kolaylık, IDE bir yöntem sağlar. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, Win32 API'larını çağırma yerine kullanılacak. Yönetilen kod kullanılan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Bir hata oluştuğunda `HRESULT` burada hata iletisini görüntülenmelidir düzeyinde ulaşan (Bu genellikle nesnedir uygulama bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komut işleyicisi), IDE başka bir yöntem kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, uygun bir ileti kutusu görüntülemek için. Yönetilen kod kullanılan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> yöntemi.  
  
 VSPackage'ı uygulayan, normal olarak, COM nesneleri uygulamak `ISupportErrorInfo`. `ISupportErrorInfo` Arabirimi sağlar zengin hata bilgileri çağrı zincirini dikey olarak taşıyabilirsiniz. İş parçacıkları arasında veya işlemler arasında kullanılabilir nesneleri desteklemelidir `ISupportErrorInfo` zengin hata bilgisini çağırana geri düzgün bir şekilde sıralanmış olduğundan emin olmak için.  
  
 VSPackage'ları için ilgili ve, düzenleyici fabrikaları, düzenleyiciler, hiyerarşileri, dahil olmak üzere IDE genişletme ile ilgili ve Hizmetleri, sunulan tüm nesneleri zengin hata bilgileri desteklemelidir. IDE uygulamak için bu VSPackage nesneler ihtiyacı olmasa da `ISupportErrorInfo`, her zaman teşvik edilir.  
  
 IDE hata bilgilerini raporlama ve bir kullanıcıya görüntülemek için sorumlu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] her bir `HRESULT` IDE'ye yayılır. Ayrıca oluşturma mekanizması ıde'dir `ErrorInfo` nesneleri.  
  
## <a name="general-guidelines"></a>Genel yönergeler  
 Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> VSPackage uygulamanız için de iç hataları bildirin ve ayarlamak için yöntemleri. Ancak, genel bir kural olarak, VSPackage hata iletileri işlemek için aşağıdaki yönergeleri izleyin:  
  
-   Uygulama `ISupportErrorInfo` VSPackage COM nesnelerinizi.  
  
-   Bir hata raporlama mekanizmasını çağırır oluşturma <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> uygulayan nesneler yönteminde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Kullanıcılara hataları görüntülemek IDE izin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> yöntemi.  
  
## <a name="error-information-in-the-ide"></a>IDE'de hata bilgileri  
 Aşağıdaki kurallar hata bilgisini nasıl ele alınacağını belirtmek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Eski hata bilgisi kullanıcılara bildirilmedi güvence altına almak için bir savunma stratejisi işlevleri gibi çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> yöntemini çağırmanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemi. Geçirin `null` herhangi bir şey çağıran yeni hata bilgilerini ayarlayabilir önce önbelleğe alınan hata iletilerini temizleyin.  
  
-   Hata iletileri doğrudan bildirmeyen işlevleri çağırmak için yalnızca verilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> varsa bunlar bir hatayı döndürmeden yöntemi `HRESULT`. Temizle izin verilse `ErrorInfo` girişteki bir işleve veya döndürülürken <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Bir çağrı, bir hata döndürür. Bu kuralın tek özel durum olduğunda `HRESULT` , alıcı tarafın açıkça kurtarmak veya güvenli bir şekilde yoksay.  
  
-   Açıkça bir hatayı gözardı herhangi bir tarafa `HRESULT` çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemiyle <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Aksi takdirde, `ErrorInfo` nesnesi yanlışlıkla kullanılabilir başka bir taraf kendi sağlamadan bir hata oluşturduğunda `ErrorInfo`.  
  
-   Bir hata kaynaklanan tüm yöntemleri `HRESULT` çağrılacak denetlemeleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> zengin hata bilgileri sağlamak için yöntemi. Varsa döndürülen `HRESULT` olan özel bir `FACILITY_ITF` uygun sağlamak için hata ve ardından yöntemi gereklidir `ErrorInfo`nesne. Döndürülen hata, bir standart sistem hatası ise (örneğin, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>ve benzeri) hata kodu açıkça çağırmadan döndürmek için kabul edilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemi. Kaynaklanan bir hata olduğunda bir savunma kodlama strateji olarak `HRESULT` (sistem hataları), her zaman çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> ile yöntemi `ErrorInfo` daha fazla ayrıntı'nde hatayı açıklayan veya `null`.  
  
-   Başka bir çağrı tarafından kaynaklanan hatayla başarısız alınan bilgilere geçmesi gerekir döndüren tüm işlevleri çağırmak `HRESULT` değiştirmeden `ErrorInfo` nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Seterrorınfo (Bileşen Otomasyonu)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)   
 [Geterrorınfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)   
 [ISupportErrorInfo arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
