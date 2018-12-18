---
title: Özel Özellikler penceresinde sağlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 8b3aeae11e087b6a6bd662ed32564d93062426df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186283"
---
# <a name="providing-a-custom-properties-window"></a>Özel Özellikler penceresinde sağlama
Kendi sağlamak mümkündür **özellikleri** genişletmek yerine ek olarak, belirtilen proje sistemi penceresinde **özellikleri** penceresi tarafından sağlanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE). Sizin pencere çerçevesinde tarihli nesne uygularken en sık karşılaşılan bir senaryodur.  
  
 Pencere çerçevesinde tarihli nesnesi kullanılmaz, ancak başka bir şekilde ona erişimi devam ediyor durumunda erişmek için çeşitli yollarla vardır <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> son yordamda bu sayfada listelenen arabirim.  
  
### <a name="to-provide-your-properties-window"></a>Özellikler penceresinde sağlamak için  
  
1.  Temsil eden bir GUID tanımlayın, **özellikleri** penceresi uygulama.  
  
2.  İçinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> uygulama, kullanım <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> proffer hizmetinin, **özellikleri** penceresi Visual Studio ortamına bir hizmet olarak.  
  
### <a name="to-call-your-properties-window"></a>Özellikler penceresinde çağırmak için  
  
1.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> yöntemi.  
  
2.  `QueryService` için <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> gelen <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> yöntemlere geçirilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> yöntemi.  
  
3.  Elde <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> gelen <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> hizmeti.  
  
4.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> ilk parametre kümesine sahip `SEID_PropertyBrowserSID` (alınan <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> numaralandırma) ve üçüncü parametre `varValue`, GUID'nin temsil eden bir dize biçiminde temsil eden, **özellikleri** pencere. Bu çağrı yalnızca bir kez olun ilk oluşturma sırasında **özellikleri** penceresi belge penceresi. Çağırdıktan sonra bu **özellikleri** penceresi, pencere çerçevesi ile ilişkili.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Pencere çerçevesi nesne uygulayan olmadığında edinme  
  
-   Yapabilecekleriniz `QueryService` için <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> hizmetinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> parametresiyle `propid` kümesine <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  
  
-   Etkin belge penceresini çağırarak elde edebileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> SVsMonitorSelection hizmeti aracılığıyla. Parametre kümesi `elementid` için `SEID_WindowFrame`, öğesinden alınan <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> sabit listesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri genişletme](../extensibility/internals/extending-properties.md)   
 [Özellikler Penceresi Alanları ve Arabirimleri](../extensibility/internals/properties-window-fields-and-interfaces.md)