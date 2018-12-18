---
title: 'Nasıl yapılır: Test ve hata ayıklama Görselleştirici | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b41a65fb92615bf8b8e38cc13260187a6abc946f
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058418"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Test Etme ve Hata Ayıklama
Bir kez hata ayıklama ve test etmeniz, Görselleştirici yazmıştır.  
  
 Görselleştirici test etmek için bir Visual Studio yükleyerek ve bir hata ayıklayıcı penceresinden çağırma yoldur. (Bkz [nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md).) Bunu yaparsanız, ekleme ve hata ayıklayıcısı ilk örneğinde çalışan Görselleştirici hata ayıklamak için Visual Studio ikinci bir örneğini kullanmanız gerekir.  
  
 Görselleştirici hata ayıklamak için daha kolay bir yolu, bir test sürücüsünden Görselleştirici çalıştırmaktır. Görselleştirici API'leri olarak adlandırılan bu tür bir sürücü oluşturmak kolaylaştırır *Görselleştirici geliştirme konak*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Görselleştirici geliştirme konak oluşturmak için  
  
1.  Hata ayıklayıcı tarafı sınıfınızda oluşturan bir statik yöntem dahil bir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> nesne ve onun show yöntemi çağırır:  
  
    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Ana bilgisayar oluşturmak için kullanılan Görselleştirici gösterilen veri nesnesi parametreleridir (`objectToVisualize`) ve hata ayıklayıcı yan sınıf türü.  
  
2.  Çağırmak için aşağıdaki ifadeyi ekleyin `TestShowVisualizer`. Bir sınıf kitaplığı'nda, Görselleştirici oluşturduysanız, sınıf kitaplığı çağırın ve bu deyimi, yürütülebilir dosya yerleştirmek için yürütülebilir bir dosya oluşturmanız gerekir:  
  
    ```csharp
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Daha eksiksiz bir örnek için bkz: [izlenecek yol: C# ile Görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Görselleştirici C# ile yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md)   
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)
