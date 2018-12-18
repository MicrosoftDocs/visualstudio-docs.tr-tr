---
title: Özel veri görselleştiriciler oluştur | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5f505bfa8032b0f7d59f348835e1e4969b2648
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607828"
---
# <a name="create-custom-data-visualizers"></a>Özel veri görselleştiriciler oluşturma 
 A *Görselleştirici* parçasıdır [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] bir değişkeni veya nesneyi, veri türüne uygun şekilde görüntüler hata ayıklayıcı kullanıcı arabirimi. Örneğin, bir HTML Görselleştirici bir HTML dizesi olarak yorumlar ve sonucu bir tarayıcı penceresinde görüneceği şekilde görüntüler. Bit eşlem Görselleştirici bir bit eşlem yapısı yorumlar ve onu gösteren grafiği görüntüler. Bazı görselleştiriciler, yanı sıra veri değiştirmenizi sağlar.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Hata ayıklayıcı altı standart görselleştiriciler içerir. Metin, HTML, XML ve JSON görselleştiriciler dize nesneler üzerinde çalışır. WPF ağacı görselleştiricisini WPF nesne görsel ağacı özelliklerini görüntüler. Veri kümesi görselleştiricisi veri kümesi, DataView ve DataTable nesneleri için çalışır. 

Daha fazla görselleştiriciler, Microsoft, üçüncü taraflar ve topluluktan indirme için kullanılabilir. Ayrıca kendi görselleştiriciler yazabilir ve bunları yüklemek [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] hata ayıklayıcı.

Hata Ayıklayıcı'Görselleştirici Büyüteç simgesi tarafından temsil edilen ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi"). Simge seçebilirsiniz bir **DataTip**, hata ayıklayıcı **izleme** penceresinde veya **QuickWatch** iletişim kutusu ve karşılık gelen nesne için uygun Görselleştirici seçin.

## <a name="write-custom-visualizers"></a>Özel görselleştiriciler yazma

 > [!NOTE]
 > Yerel kod için özel Görselleştirici oluşturmak için bkz [SQLite yerel hata ayıklama görselleştiricisi](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) örnek. Özel görselleştiriciler, UWP ve Windows 8.x uygulamaları için desteklenmez.

Dışında herhangi bir yönetilen sınıfın bir nesnesi için özel Görselleştirici yazabileceğiniz <xref:System.Object> ve <xref:System.Array>.  
  
Hata ayıklama görselleştiricisi mimarisini iki bölümden oluşur:  
  
- *Hata ayıklayıcı, yan* Visual Studio hata ayıklayıcısı içinde çalıştırır ve oluşturur ve Görselleştirici kullanıcı arabirimini görüntüler.  
  
- *Hata ayıklanan yan* Visual Studio hata ayıklama işlemi içinde çalıştırılan ( *hata ayıklanan*). Hata ayıklanan işlemin (örneğin, bir dize nesnesi) görselleştirmek için veri nesnesi yok. Hata ayıklanan tarafı, oluşturduğunuz kullanıcı arabiriminde görüntüler hata ayıklayıcı tarafına nesneyi gönderir.  

Hata ayıklayıcı yan veri nesneden alır bir *nesne sağlayıcı* uygulayan <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> arabirimi. Hata ayıklanan tarafı nesnesi üzerinden gönderir *nesne kaynağı*, türetilen <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. 

Nesne sağlayıcısı Ayrıca verileri düzenleyebileceğiniz Görselleştirici yazmanıza olanak veren nesne kaynak için verileri geri gönderebilirsiniz. İfade değerlendirici ve nesne kaynağı konuşmak için nesne sağlayıcı geçersiz kılmanız.  
  
Hata ayıklanan yan ve hata ayıklayıcı yan aracılığıyla birbiriyle iletişim <xref:System.IO.Stream> bir verileri seri hale getirme yöntemleri nesnesi içine bir <xref:System.IO.Stream> ve seri durumdan <xref:System.IO.Stream> yeniden içine bir veri nesnesi.  

Tür açık bir tür ise genel bir tür için Görselleştirici yazabilirsiniz. Bu kısıtlama aynı kısıtlama olarak kullanıldığında `DebuggerTypeProxy` özniteliği. Ayrıntılar için bkz [DebuggerTypeProxy özniteliğini kullanma](../debugger/using-debuggertypeproxy-attribute.md).  
  
Özel görselleştiriciler, güvenlik konuları olabilir. Bkz: [Görselleştirici güvenlik konuları](../debugger/visualizer-security-considerations.md).  
  
Aşağıdaki adımları görselleştiricisi oluşturma üst düzey bir genel bakış sağlar. Ayrıntılı yönergeler için bkz. [izlenecek yol: Görselleştirici yazma C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) veya [izlenecek yol: Visual Basic'te Görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).  
  
### <a name="to-create-the-debugger-side"></a>Hata ayıklayıcı yan oluşturmak için  
  
Hata ayıklayıcı tarafında görselleştiricisi kullanıcı arabirimi oluşturmak için devralınan bir sınıf oluşturun. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>ve geçersiz kılma <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> arabirim görüntülemesi için yöntemi. Kullanabileceğiniz <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows forms iletişim kutuları ve denetimleri, görselleştiricisi içinde görüntülenecek.  
  
1.  Kullanım <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> görselleştirilen nesne hata ayıklayıcı tarafta almak için yöntemleri.  
  
1.  Devralınan bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
1.  Geçersiz kılma <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> Arabiriminizin görüntülemek için yöntemi. Kullanım <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows forms iletişim kutuları ve denetimleri, arabirimde görüntülemek için yöntemleri.  
  
4.  Uygulama <xref:System.Diagnostics.DebuggerVisualizerAttribute>, görüntülenecek görselleştiricisi veren (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Hata ayıklanan yan oluşturmak için  
  
Hata ayıklanan tarafın kod kullanarak belirttiğiniz <xref:System.Diagnostics.DebuggerVisualizerAttribute>.  
  
1.  Uygulama <xref:System.Diagnostics.DebuggerVisualizerAttribute>, Görselleştirici veren (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) ve bir nesne kaynağı (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Nesne kaynağı atlarsanız, varsayılan nesne kaynak görselleştiricisi kullanır.  
  
1.  Yanı sıra veri nesneleri görüntüleme düzenleme Görselleştirici izin vermek için geçersiz kılma `TransferData` veya `CreateReplacementObject` yöntemlerinden <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="see-also"></a>Ayrıca bkz.
  
 [İzlenecek yol: C# ile görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [İzlenecek yol: Visual Basic'te görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Nasıl yapılır: Görselleştirici yükleme](../debugger/how-to-install-a-visualizer.md)  
  
 [Nasıl yapılır: Görselleştiriciyi test etme ve hata ayıklama](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Görselleştirici API başvurusu](../debugger/visualizer-api-reference.md)  
  
 [Hata ayıklayıcı görünümü verileri](../debugger/viewing-data-in-the-debugger.md)