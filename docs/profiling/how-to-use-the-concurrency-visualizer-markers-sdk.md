---
title: "Nasıl yapılır: eşzamanlılık görselleştiricisi işaretçileri SDK'yı kullanma | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a608c5539e905ba7836f4dcfb5e785dc9630c28a
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844546"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Nasıl yapılır: eşzamanlılık görselleştiricisi işaretçileri SDK'yı kullanma
Bu konu eşzamanlılık görselleştiricisi SDK'sı yayılma oluşturun ve bayrakları, iletileri ve uyarılar yazmak için nasıl kullanılacağını gösterir.  
  
### <a name="to-use-c"></a>C++ kullanmak için  
  
1.  Eşzamanlılık görselleştiricisi SDK'sı desteği uygulamanıza ekleyin. Daha fazla bilgi için bkz: [eşzamanlılık görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Ekleme bir `include` deyimi ve `using` SDK'sı deyimi.  
  
    ```C++  
  
    #include <cvmarkersobj.h>  
    using namespace Concurrency::diagnostic;  
  
    ```  
  
3.  Varsayılan işaret serisinde üç yayılma oluşturmak ve bir bayrak, bir ileti ve bir uyarı, her aralık için yazma için kodu ekleyin. Bayrakları, iletileri ve uyarılar yazmak için yöntemleri üyesi [marker_series](../profiling/marker-series-class.md) sınıfı. Oluşturucusu [span](../profiling/span-class.md) sınıfı gerektiren bir `marker_series` nesne her aralık belirli işaret serisiyle ilişkili olmasını sağlayın. A `span` silindiğinde sona erer.  
  
    ```C++  
  
    marker_series series;  
    span *flagSpan = new span(series, 1, _T("flag span"));  
    series.write_flag(_T("Here is the flag."));  
    delete flagSpan;  
  
    span *messageSpan = new span(series, 2, _T("message span"));  
    series.write_flag(_T("Here is the message."));  
    delete messageSpan;  
  
    span *alertSpan = new span(series, 3, _T("alert span"));  
    series.write_flag(_T("Here is the alert."));  
    delete alertSpan;  
  
    ```  
  
4.  Menü çubuğunda seçin **Çözümle**, **eşzamanlılık görselleştiricisi**, **Başlat Geçerli projeyle** uygulamayı çalıştırın ve eşzamanlılık görselleştiricisi görüntülemek için. Aşağıdaki çizim üç yayılımları ve üç işaretçileri eşzamanlılık görselleştiricisi gösterir.  
  
     ![Eşzamanlılık görselleştiricisi 3 işaretçileri ve uyarılarla](../profiling/media/cvmarkersnative.png "CvMarkersNative")  
  
5.  Ek, özel işaret serisi Oluşturucusu çağırarak oluşturmak için kodu ekleyin `marker_series` işaret serisi için dize adını alır.  
  
    ```C++  
  
    marker_series flagSeries(_T("flag series"));  
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));  
    flagSeries.write_flag(1, _T("flag"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete flagSeriesSpan;  
  
    marker_series messageSeries(_T("message series"));  
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));  
    messageSeries.write_message(1, _T("message"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete messageSeriesSpan;  
  
    ```  
  
6.  Eşzamanlılık görselleştiricisi görüntülenecek geçerli proje başlatın. İki işaret serisi kendi kulvarları iş parçacıkları görünümünde görünür. Aşağıdaki çizimde, iki yeni yayılma gösterir.  
  
     ![3 özel işaret seriler eşzamanlılık görselleştiricisi](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")  
  
### <a name="to-use-visual-basic-or-c"></a>Visual Basic veya C# kullanmak için #
  
1.  Eşzamanlılık görselleştiricisi SDK'sı desteği uygulamanıza ekleyin. Daha fazla bilgi için bkz: [eşzamanlılık görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Ekleme bir `using` veya `Imports` SDK'sı deyimi.  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
  
    ```  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
3.  Varsayılan işaret seriyi üç yayılma oluşturmak ve bir bayrak, bir ileti ve bir uyarı, her aralık için yazma için kodu ekleyin. Oluşturduğunuz bir <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Span> statik çağırarak nesne `EnterSpan` yöntemi. Varsayılan dizisi yazmak için statik yazma yöntemlerini kullanın. <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> sınıfı.  
  
    ```VB  
  
    Dim flagSpan As Span = Markers.EnterSpan("flag span")  
    Markers.WriteFlag("Here is the flag.")  
    flagSpan.Leave()  
  
    Dim messageSpan As Span = Markers.EnterSpan("message span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteMessage("Here is a message")  
    messageSpan.Leave()  
  
    Dim alertSpan As Span = Markers.EnterSpan("alert span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteAlert("Here is an alert")  
    alertSpan.Leave()  
  
    ```  
  
    ```csharp  
  
    Span flagSpan = Markers.EnterSpan("flag span");  
    Markers.WriteFlag("Here is the flag.");  
    flagSpan.Leave();  
  
    Span messageSpan = Markers.EnterSpan("message span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteMessage("Here is a message");  
    messageSpan.Leave();  
  
    Span alertSpan = Markers.EnterSpan("alert span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteAlert("Here is an alert");  
    alertSpan.Leave();  
    ```  
  
4.  Menü çubuğunda seçin **Çözümle**, **eşzamanlılık görselleştiricisi**, **Başlat Geçerli projeyle** uygulamayı çalıştırın ve eşzamanlılık görselleştiricisi görüntülemek için. Aşağıdaki çizim üç yayılımları ve üç işaretçileri eşzamanlılık görselleştiricisi iş parçacıkları görünümünde gösterir.  
  
     ![Eşzamanlılık görselleştiricisi işaretçileri ve uyarılarla](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")  
  
5.  Statik kullanarak müşteri işaret serisi oluşturmak için kodu ekleyin <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.CreateMarkerSeries%2A> yöntemi. <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> Sınıfı yayılma oluşturma ve yazma bayrakları, iletileri ve Uyarılar için yöntemler içerir.  
  
    ```VB  
  
    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")  
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")  
    System.Threading.Thread.Sleep(1)  
    flagSeries.WriteFlag(1, "flag")  
    System.Threading.Thread.Sleep(1)  
    flagSeriesSpan.Leave()  
  
    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")  
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")  
    messageSeries.WriteMessage("message")  
    System.Threading.Thread.Sleep(1)  
    messageSeriesSpan.Leave()  
    ```  
  
    ```csharp  
  
    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");  
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");  
    System.Threading.Thread.Sleep(1);  
    flagSeries.WriteFlag(1, "flag");  
    System.Threading.Thread.Sleep(1);  
    flagSeriesSpan.Leave();  
  
    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");  
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");  
    messageSeries.WriteMessage("message");  
    System.Threading.Thread.Sleep(1);  
    messageSeriesSpan.Leave();  
    ```  
  
6.  Eşzamanlılık görselleştiricisi görüntülenecek geçerli proje başlatın. Üç işaret serisi kendi kulvarları iş parçacıkları görünümünde görünür. Aşağıdaki çizim üç yeni yayılma göstermektedir.  
  
     ![3 özel işaret seriler eşzamanlılık görselleştiricisi](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)
