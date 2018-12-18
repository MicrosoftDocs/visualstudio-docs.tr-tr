---
title: Eski API'yi kullanarak metin arabelleğini erişme | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c52e4beb1397e9919c3bf670e009d7ca1060ce1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722194"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Eski API'yi kullanarak metin arabelleğini erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin, metin akışları ve dosya kalıcılığına yönetmekten sorumludur. Arabellek okuma veya yazma diğer biçimlere rağmen arabellek ile tüm sıradan iletişim Unicode kullanılarak gerçekleştirilir. Eski API'leri, metin arabelleğini bir - veya iki boyutlu bir koordinat sistemini arabellekteki karakterin konumlarını belirlemek için kullanabilirsiniz.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Tek ve iki boyutu koordinat sistemleri  
 Tek boyutlu bir koordinat konumu ilk karakter bir karakterin konumu arabellekteki 147 gibi temel alır. Kullandığınız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> tek boyutlu bir arabellek konuma erişmek için arabirim. İki boyutlu bir koordinat sistemini satır ve dizin çiftlerine dayanarak temel alır. Örneğin, bir karakter 43 arabellekte 5 satırında 43, o satırdaki ilk karakterin sağındaki beş karakter olabilir. Arabellek kullanarak iki boyutlu bir konuma erişim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> arabirimi. Hem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> arabirimleri metin arabelleği nesne tarafından uygulanan (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) ve birbirinden kullanarak erişilebilir `QueryInterface`. Aşağıdaki diyagramda bu ve diğer temel arabirimleri gösteren <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Metin arabelleği nesnesi](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Metin arabelleği nesnesi  
  
 Metin arabelleğinde ya da koordinat sistemini çalışır, ancak iki boyutlu koordinatlarını kullanmak için optimize edilmiştir. Tek boyutlu bir koordinat sistemi performans yükü oluşturabilirsiniz. Bu nedenle, mümkün olduğunda iki boyutlu koordinat sistemini kullanın.  
  
 Arabellek ikinci sorumluluk dosya kalıcılığına metindir. Bunu yapmak için metin arabelleği nesnesi uygulayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ve proje öğeleri için belge veri nesnesi bileşeni ve kalıcı ilgili diğer ortam bileşenleri olarak görev yapar. Daha fazla bilgi için [açma ve kaydetme proje öğeleri](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski API'yi Kullanarak Görünüm Ayarlarını Değiştirme](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Eski API'yi kullanarak görünüm ayarlarını değiştirme açıklanmaktadır.  
  
 [Genel Ayarları İzlemek İçin Metin Yöneticisini Kullanma](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Genel ayarlar izlemek için metin Yöneticisi'ni kullanmayı açıklar...  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Düzenleyicinin İçinde](../extensibility/inside-the-core-editor.md)

