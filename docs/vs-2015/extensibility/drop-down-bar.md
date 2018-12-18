---
title: Aşağı açılan çubuğu | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da48806d6be6b19dc3681b19e95ac7664656eeb0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791154"
---
# <a name="drop-down-bar"></a>Aşağı açılan çubuğu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağı açılan çubuğu kod penceresinin en üstünde sağlanır ve iki açılan listeleri içerir.  
  
## <a name="drop-down-bar-interfaces"></a>Aşağı açılan çubuğu arabirimleri  
 İçinde [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], örneğin, aşağı açılan çubuğu listelerini içerir [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] öğeleri ve [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] öğeleri üye işlevleri aşağıdaki resimde gösterildiği gibi.  
  
 ![DROP&#45;aşağı çubukları](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Aşağı açılan çubuğu  
  
 Bir açılan çubuğu uygularken birincil önem dört arabirimi vardır:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Aşağı açılan çubuğunun içeriğini eklemek için bu arabirimi uygulayın. Her bir açılan birleşimini düz metin veya başvurmaktan metin içerebilir (kalın, italik veya alt çizgi), pencere metin yazı tipi renkleri veya çıkış gri yazı tipi renklendirme sahip olabilir ve isteğe bağlı olarak açılan öğesinin yanındaki küçük bir bit eşlem sağlayabilir. Benzer şekilde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> arabirimi, bit eşlem resimleri görüntü listeleri sağlanır. Farklı bir görüntü listesini her bir açılan bileşimi olabilir; Ancak, her bir görüntü listesi görüntüler aynı yükseklikte içermelidir. Ayrıca, kullanarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> yöntemi, her bir birleşimi için bir araç ipucu sağlayabilir.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Bu arabirim oluşturmak veya bir kod penceresinde açılan çubuğunu yok etmek için çağırın. Bu arabirim, aşağı açılan çubuğu zaten bir kod penceresine çağırarak ekli olup olmadığını belirlemek için de kullanılabilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> yöntemi. Çağrı <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> gelen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Doğrudan aşağı açılan çubuğu ile iletişim kurmak için bu arabirimi çağırın. Bu arabirim, açılan listeyi yenilemeye zorlamak için kullanabileceğiniz içeriği çubuk veya Seçimi liste kutuları biriyle değiştirin.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Kayıtlı `ShowDropdownBarOption` dil hizmeti kayıt defteri anahtarında, kod penceresi yöneticinize açılan çubuğu görüntülenip görüntülenmeyeceğini ilgili kullanıcı tercihlerini ile eşitlemek için bu olay izlemelidir. Bu seçenek Dil hizmeti anahtarınızı kaydetmeyin sonra açılan çubuğunu gösterme veya gizleme seçeneğini devre dışı **seçenekleri** menüsü.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Bir kod penceresi için bir açılan çubuğu ekleme  
 Oluşturulduğunda bir açılan çubuğu koda eklemek için bir dil hizmeti için açılan iliştirin ne zaman çubuk <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> yöntemi çağrılır. Bir çağrı, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> yöntemi gösteren bir açılan çubuğu zaten mevcut çağırma ve emin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Erişim için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> arabirim, çağrı <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> gelen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> işaretçi döndürdü, ne zaman, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> uygulama bağlı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API'sini kullanarak kod Windows özelleştirme](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

