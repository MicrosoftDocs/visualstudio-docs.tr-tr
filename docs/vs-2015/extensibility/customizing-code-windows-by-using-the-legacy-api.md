---
title: Eski API'sini kullanarak kod Windows özelleştirme | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45788e3fdfff2898a0d2d2ed36c81425c225b54c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809772"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Eski API'sini kullanarak kod Windows özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kod penceresinde bir veya daha fazla metin görünümlerini destekleyen bir belge penceresi nesnesidir. Tam bir kod penceresi özelliklerini ilişkili dil hizmetine bağlıdır. Çok Belgeli Arabirim (MDI) modunda kod penceresinde MDI alt çerçeve ' dir.  
  
 Kodu windows dil Hizmetleri tarafından denetlenir ve her dil hizmeti, kendi kod penceresinde yöneticisini sağlayabilir. Bu, kod penceresi dalgalı çizgiler, renklendirme ve daha fazlası gibi kendi kenarlıklar eklemek dil hizmeti sağlar. Core pencereyi oluşturma hakkında daha fazla bilgi için bkz. [çekirdek düzenleyici kullanarak eski API örnekleme](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Bir kod penceresi bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> metni görünümü ve nesne tarihli herhangi Kenarlıklar nesnesi. Düzenleyici, çekirdek Örnekleme sırasında kod penceresinde oluşturduğunuzda, dil hizmetinizi ekleyebilirsiniz bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> kod penceresine olarak aşağıdaki çizimde gösterilmiştir.  
  
 ![CodeWindow grafiği](../extensibility/media/vscodewindow.gif "vscodewindow")  
Kod penceresi  
  
 Dil hizmeti, kod penceresi Yöneticisi uygular ve açılan çubuğu gibi Kenarlıklar yönetmekten sorumludur. Kod penceresi çağrıları <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> kod penceresinde başlatma sırasında yöntemi. Bu çağrı yapıldığında, dil hizmeti açılan çubuğu veya düğme çubuğu ekleyebilirsiniz (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) için kod penceresi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 `Customizing Code Windows by Using the Legacy API`  
 Kodu windows eski API'yi kullanarak özelleştirmek nasıl açıklar.  
  
 [Nasıl Yapılır: Bir Düzenleyiciyi Başka Bir Düzenleyicide Barındırma](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Bir düzenleyici penceresi içine ikinci bir düzenleyici barındırmak nasıl açıklar.  
  
 [Nasıl Yapılır: Düzenleyici Odağı Kaybettiğinde Olayları Başlatma](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Bir belge veri nesnesine bir belge görünümü ekleme açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Eski API'yi kullanarak çekirdek Düzenleyici örnekleme](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Eski API'yi Kullanarak Metin Görünümüne Erişme](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

