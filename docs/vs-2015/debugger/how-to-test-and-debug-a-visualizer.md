---
title: 'Nasıl yapılır: Görselleştiriciyi hata ayıklama ve Test | Microsoft Docs'
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
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00fb749505f8bfe16c353552aa3afcb9eaaefc2d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723289"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Test Etme ve Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirici, hata ayıklama ve test için ihtiyaç duyduğunuz bir kez yazdığınız.  
  
 Görselleştiriciyi sınamak için bir Visual Studio yükleyerek ve bir hata ayıklayıcı penceresinde çağırma yoludur. (Bkz [nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md).) Bunu yaparsanız, ekleyin ve hata ayıklayıcı ilk örneğinde çalışan görselleştiricisi hata ayıklamak için Visual Studio'nun ikinci bir örneğini kullanmanız gerekir.  
  
 Görselleştiriciyi hata ayıklamak için daha kolay bir yolu, bir test sürücüsünden görselleştiricisi çalıştırmaktır. Görselleştirici API'leri adı verilen bu tür bir sürücüsü oluşturmak kolaylaştırır *Görselleştirici geliştirme konak*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Görselleştirici geliştirme ana bilgisayar oluşturmak için  
  
1.  Hata ayıklayıcı tarafı sınıfınızda oluşturan bir statik yöntem dahil bir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> nesne ve onun show yöntemi çağırır:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Ana bilgisayar oluşturmak için kullanılan görselleştiricisi içinde gösterilecek veri nesnesi parametreleridir (`objectToVisualize`) ve hata ayıklayıcı tarafı sınıf türü.  
  
2.  Çağırmak için aşağıdaki deyimi ekleyin `TestShowVisualizer`. Bir sınıf kitaplığında, görselleştiricisi oluşturduysanız, sınıf kitaplığı çağırın ve bu bildirimi, yürütülebilir dosya yerleştirmek için yürütülebilir bir dosya oluşturmak gerekir:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Daha eksiksiz bir örnek için bkz: [izlenecek yol: C# ile Görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Görselleştiriciyi C# ' de yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md)   
 [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)



