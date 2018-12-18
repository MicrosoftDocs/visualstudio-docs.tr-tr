---
title: Görselleştirici mimarisi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7a3255b8e8b91f074308a0238719f26af6cf665
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736155"
---
# <a name="visualizer-architecture"></a>Görselleştirici Mimarisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklama görselleştiricisi mimarisini iki bölümden oluşur:  
  
- *Hata ayıklayıcı, yan* Visual Studio hata ayıklayıcısı içinde çalıştırır. Hata ayıklayıcı tarafı kodunu oluşturup, görselleştiricisi için kullanıcı arabirimini görüntüler.  
  
- *Hata ayıklanan yan* Visual Studio hata ayıklama işlemi içinde çalıştırılan ( *hata ayıklanan*).  
  
  Görselleştirici görüntülenecek hata ayıklayıcıyı etkinleştiren bir hata ayıklayıcı bileşendir (*görselleştirme*) anlamlı, anlaşılır bir form veri nesnesinde içeriği. Veri nesnesinin de düzenleme bazı görselleştiriciler destekler. Özel görselleştiriciler yazarak, kendi özel veri türlerini işlemek için hata ayıklayıcı genişletebilirsiniz.  
  
  Veri nesnesi görünür için hata ayıklama işlemi içinde bulunduğu ( *hata ayıklanan* işlem). İçinde Visual Studio hata ayıklayıcı işlemi verileri görüntüleyecek kullanıcı arabirimi oluşturulur:  
  
|Hata ayıklayıcı işleme|Hata ayıklanan işlem|  
|----------------------|----------------------|  
|Kullanıcı Arabirimi (DataTips, İzleme penceresinde QuickWatch) hata ayıklayıcı|Görselleştirilmiş için veri nesnesi|  
  
 Veri nesnesi içinde hata ayıklayıcı arabirim görselleştirmek için iki işlem arasında iletişim kurmak için kod gerekir. Sonuç olarak, Görselleştirici mimarisi iki bölümden oluşur: *hata ayıklayıcı, yan* kod ve *hata ayıklanan yan* kod.  
  
 Hata ayıklayıcı tarafı kod, hata ayıklayıcı arabiriminden bir DataTip İzle penceresine veya QuickWatch gibi çağrılabilir, kendi kullanıcı arabirimi oluşturur. Görselleştirici arabirimi kullanılarak oluşturulan <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> sınıfı ve <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> arabirimi. Tüm Görselleştirici API'leri, DialogDebuggerVisualizer ve IDialogVisualizerService bulunan gibi <xref:Microsoft.VisualStudio.DebuggerVisualizers> ad alanı.  
  
|Hata ayıklayıcı yan|Hata ayıklanan yan|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer sınıfı<br /><br /> IDialogVisualizerService arabirimi|Veri nesnesi|  
  
 Kullanıcı arabirimi hata ayıklayıcı tarafta var olan bir nesne sağlayıcısı, görselleştirilmiş verileri alır:  
  
|Hata ayıklayıcı yan|Hata ayıklanan yan|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer sınıfı<br /><br /> IDialogVisualizerService arabirimi|Veri nesnesi|  
|Sağlayıcı nesnesi (uygulayan <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||  
  
 Nesne kaynağı olarak adlandırılan hata ayıklanan taraftaki karşılık gelen nesne vardır:  
  
|Hata ayıklayıcı yan|Hata ayıklanan yan|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer sınıfı<br /><br /> IDialogVisualizerService arabirimi|Veri nesnesi|  
|Sağlayıcı nesnesi (uygulayan <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Kaynak nesne (türetilen <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|  
  
 Nesne sağlayıcı görselleştiricisi UI görselleştirilmiş nesne verileri sağlar. Nesne sağlayıcı nesne kaynak nesne verilerini alır. Nesne sağlayıcısı ve nesne kaynak nesne verilerini hata ayıklayıcı yan debugee tarafı arasındaki iletişim kurmak için API'leri sağlar.  
  
 Her Görselleştirici görünür için veri nesnesi almanız gerekir. Aşağıdaki tabloda, nesne kaynağı ve nesne sağlayıcısı bu amaçla kullanabileceğiniz ilgili API'leri gösterir:  
  
|Nesne sağlayıcısı|Nesne kaynağı|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 Bildirim ya da nesne sağlayıcıyı kullanabilirsiniz <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> veya <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Her iki API çağrısı sonuçlanıyor <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> nesne kaynak. Bir çağrı <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> [System.IO.Stream] içinde doldurur (<!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->), görselleştirilmekte olan nesnedeki bir seri hala getirilmiş biçimini temsil eder.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> Forma ardından, oluşturduğunuz kullanıcı arabiriminde görüntüleyebilen geri nesne, verileri seri durumdan çıkarır <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> bir ham verileri doldurur <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, hangi kendiniz seri durumdan gerekir. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> çalışan çağırarak <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> serileştirilmiş almak için <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, verileri seri durumdan çıkarılırken sonra. Kullanım <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> zaman nesnesi tarafından .NET seri hale getirilebilir değil ve özel serileştirme gerektirir. Bu durumda, geçersiz kılmalısınız <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> yöntemi.  
  
 Oluşturmakta olduğunuz, salt okunur Görselleştirici, tek yönlü iletişimi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> veya <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> yeterlidir. Veri nesnelerini düzenleme destekleyen Görselleştirici oluşturuyorsanız, bunu daha yapmanız gerekir. Nesne kaynak nesne sağlayıcısından bir veri nesnesi de gönderebilmesi için olması gerekir. Aşağıdaki tabloda, bu amaç için kullanılan nesne kaynak API'leri ve nesne sağlayıcı gösterilmektedir:  
  
|Nesne sağlayıcısı|Nesne kaynağı|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 Yeniden nesne sağlayıcı kullanabileceğiniz iki API olduğuna dikkat edin. Veriler her zaman gönderilir nesne sağlayıcısından nesnesi kaynağı olarak bir <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, ancak <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> nesnede seri hale getirme gerektiren bir <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> kendiniz.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> sağlarsanız, nesne bir içine serileştiren bir <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, sonra çağıran <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> göndermek için <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> için <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.  
  
 Replace yöntemlerden birini kullanarak yeni bir veri nesnesi, görselleştirilmekte olan nesnedeki yerini alan hatası ayıklanana oluşturur. Orijinal nesnenin içeriğini değiştirme olmadan değiştirmek istiyorsanız, aşağıdaki tabloda gösterilen aktarımı yöntemlerden birini kullanın. Bu API'ler, görselleştirilmekte olan nesnedeki değiştirmeden, aynı zamanda, her iki yönde veri aktarımı:  
  
|Nesne sağlayıcısı|Nesne kaynağı|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Görselleştirici yazma](../debugger/how-to-write-a-visualizer.md)   
 [İzlenecek yol: Görselleştiriciyi C# ' de yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [İzlenecek yol: Visual Basic'de Görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [İzlenecek yol: Visual Basic'de Görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Görselleştirici Güvenlik Konuları](../debugger/visualizer-security-considerations.md)



