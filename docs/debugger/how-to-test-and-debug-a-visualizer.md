---
title: Görselleştiriciyi test etme ve hata ayıklama | Microsoft Docs
description: bir test sürücüsünden (görselleştirici geliştirme ana bilgisayarı) çalıştırarak veya Visual Studio yükleyip hata ayıklayıcı penceresinden çağırarak bir görselleştirici test edin ve hatalarını ayıklayın.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa97453d08650b78a02eda873a01afe9e376caec
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298250"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Test Etme ve Hata Ayıklama
Görselleştirici yazdıktan sonra hata ayıklaması yapmanız ve test etmeniz gerekir.

görselleştirici test etmenin bir yolu, Visual Studio bir hata ayıklayıcı penceresinden yüklenerek bu uygulamayı test etmenin bir yoludur. (Bkz. [nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md).) bunu yaparsanız, hata ayıklayıcının ilk örneğinde çalışan görselleştiricisi eklemek ve hatalarını ayıklamak için Visual Studio ikinci bir örneğini kullanmanız gerekir.

Görselleştirici hata ayıklamanın daha kolay bir yolu, Görselleştirici bir test sürücüsünden çalıştırılmaktır. Görselleştiricisi API 'Leri, *görselleştiricisi geliştirme Konağı* olarak adlandırılan böyle bir sürücü oluşturmayı kolaylaştırır.

>[!NOTE]
> şu anda, test sürücüsü yalnızca görselleştiricisi bir .NET Framework uygulamasından çağrılırken desteklenir.

### <a name="to-create-a-visualizer-development-host"></a>Görselleştiricisi geliştirme konağı oluşturmak için

1. Hata ayıklayıcı tarafı sınıfınıza, bir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> nesnesi oluşturan ve Show yöntemini çağıran statik bir yöntem ekleyin:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Konağı oluşturmak için kullanılan parametreler, Görselleştirici ( `objectToVisualize` ) ve hata ayıklayıcı tarafı sınıfının türü içinde gösterilecek veri nesnesidir.

2. Çağırmak için aşağıdaki ifadeyi ekleyin `TestShowVisualizer` . Görselleştiriciyi bir sınıf kitaplığında oluşturduysanız, sınıf kitaplığını çağırmak için bir yürütülebilir dosya oluşturmanız ve bu ifadeyi çalıştırılabilirinize yerleştirmeniz gerekir:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Daha kapsamlı bir örnek için bkz. [Izlenecek yol: C# dilinde Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek Yol: C# ile Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
