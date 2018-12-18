---
title: 'Nasıl yapılır: Görselleştirici yazma | Microsoft Docs'
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c7f1fa96bba40e5e56ca7f054b683b3243de65b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724900"
---
# <a name="how-to-write-a-visualizer"></a>Nasıl Yapılır: Görselleştirici Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dışında herhangi bir yönetilen sınıfın bir nesnesi için özel Görselleştirici yazabileceğiniz <xref:System.Object> veya <xref:System.Array>.  
  
> [!NOTE]
>  İçinde **Store** uygulamalar, yalnızca standart metin, HTML, XML ve JSON görselleştiriciler desteklenir. Özel (kullanıcı tarafından oluşturulmuş) görselleştiriciler desteklenmez.  
  
 Hata ayıklama görselleştiricisi mimarisini iki bölümden oluşur:  
  
- *Hata ayıklayıcı, yan* Visual Studio hata ayıklayıcısı içinde çalıştırır. Hata ayıklayıcı tarafı kodunu oluşturup, görselleştiricisi için kullanıcı arabirimini görüntüler.  
  
- *Hata ayıklanan yan* Visual Studio hata ayıklama işlemi içinde çalıştırılan ( *hata ayıklanan*).  
  
  (Bir dize nesnesi, örneğin gibi) görselleştirmek istediğiniz veri nesnesi içinde hata ayıklanan işlem var. Bu nedenle, bu veri nesnesi daha sonra oluşturduğunuz bir kullanıcı arabirimi kullanarak görüntüleyebilirsiniz hata ayıklayıcı tarafa göndermek hata ayıklanan yan vardır.  
  
  Hata ayıklayıcı yan gelen görünür için bu veri nesnesi alan bir *nesne sağlayıcı* uygulayan <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> arabirimi. Hata ayıklanan yan üzerinden veri nesnesine gönderir *nesne kaynağı*, türetilen <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Nesne sağlayıcısı ayrıca veri görüntüler yanı sıra düzenler Görselleştirici yazma sağlar, nesne kaynak için verileri geri gönderebilirsiniz. İfade değerlendirici ve, bu nedenle, nesne kaynağı konuşmak için nesne sağlayıcı geçersiz kılınabilir  
  
  Hata ayıklanan yan ve hata ayıklayıcı yan başka iletişim kurmak <xref:System.IO.Stream>. Yöntemler, bir veri nesnesine serileştirmek için sağlanan bir <xref:System.IO.Stream> ve seri durumdan <xref:System.IO.Stream> yeniden içine bir veri nesnesi.  
  
  Hata ayıklanan tarafı kod DebuggerVisualizer özniteliğini kullanarak belirtilen (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
  Hata ayıklayıcı tarafında görselleştiricisi kullanıcı arabirimi oluşturmak için devralınan bir sınıf oluşturmanız gerekir <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ve geçersiz kılma <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> arabirim görüntülemesi için yöntemi.  
  
  Kullanabileceğiniz <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows forms iletişim kutuları ve, Görselleştirici denetimlerini görüntülemek için.  
  
  Genel türler için destek sınırlıdır. Yalnızca genel tür açık bir tür ise, genel türde bir hedef için Görselleştirici yazabilirsiniz. Bu kısıtlama aynı kısıtlama olarak kullanıldığında `DebuggerTypeProxy` özniteliği. Ayrıntılar için bkz [DebuggerTypeProxy özniteliğini kullanma](../debugger/using-debuggertypeproxy-attribute.md).  
  
  Özel görselleştiriciler, güvenlik konuları olabilir. Bkz: [Görselleştirici güvenlik konuları](../debugger/visualizer-security-considerations.md).  
  
  Aşağıdaki yordamlar Görselleştirici oluşturmak için yapmanız gerekenleri gösteren üst düzey bir görünüm sağlar. Daha ayrıntılı bir açıklaması için bkz. [izlenecek yol: C# ile Görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Hata ayıklayıcı yan oluşturmak için  
  
1.  Kullanım <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> görselleştirilen nesne hata ayıklayıcı tarafta almak için yöntemleri.  
  
2.  Devralınan bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Geçersiz kılma <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> Arabiriminizin görüntülemek için yöntemi. Kullanım <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows forms iletişim kutuları ve denetimleri, arabiriminin bir parçası görüntülenecek yöntemleri.  
  
4.  Uygulama <xref:System.Diagnostics.DebuggerVisualizerAttribute>, Görselleştirici veren (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Hata ayıklanan yan oluşturmak için  
  
1.  Uygulama <xref:System.Diagnostics.DebuggerVisualizerAttribute>, Görselleştirici veren (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) ve bir nesne kaynağı (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Varsayılan nesne kaynak nesne kaynağı atarsanız, kullanılacak  
  
2.  Veri nesneleri düzenleyebilmek için Görselleştirici, isterseniz de bunları olarak geçersiz kılmak ihtiyacınız olacak `TransferData` veya `CreateReplacementObject` yöntemlerinden <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md)   
 [Nasıl yapılır: Görselleştiriciyi hata ayıklama ve Test](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Görselleştirici Güvenlik Konuları](../debugger/visualizer-security-considerations.md)



