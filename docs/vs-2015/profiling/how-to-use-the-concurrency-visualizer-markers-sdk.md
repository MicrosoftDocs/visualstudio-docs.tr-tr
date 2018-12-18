---
title: "Nasıl yapılır: eşzamanlılık görselleştiricisi işaretçileri SDK'sını kullanma | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e18ada321752c1cde780031524fb45d8bd4997
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761116"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Nasıl Yapılır: Eşzamanlılık Görselleştiricisi İşaretçileri SDK'yı Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, eşzamanlılık görselleştiricisi SDK'si yayılma oluşturup bayrakları, iletileri ve Uyarılar için nasıl kullanılacağını gösterir.  
  
### <a name="to-use-c"></a>C++ kullanmak için  
  
1.  Eşzamanlılık görselleştiricisi SDK desteği uygulamanıza ekleyin. Daha fazla bilgi için [eşzamanlılık görselleştiricisi SDK'si](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Ekleme bir `include` deyimi ve `using` SDK bildirimi.  
  
    ```cpp  
  
    #include <cvmarkersobj.h>  
    using namespace Concurrency::diagnostic;  
  
    ```  
  
3.  Varsayılan işaret dizide üç yayılma oluşturup yazma bayrağı, bir ileti ve bir uyarı, her aralık için kod ekleyin. Bayrakları, iletileri ve uyarılar yazma yöntemleri üyeleri [marker_series](../profiling/marker-series-class.md) sınıfı. Oluşturucusu [span](../profiling/span-class.md) sınıfı gerektirir bir `marker_series` nesne her aralık belirli işaret seri ilişkili olmasını sağlayın. A `span` silindiğinde sona erer.  
  
    ```cpp  
  
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
  
4.  Menü çubuğunda, **Çözümle**, **eşzamanlılık görselleştiricisi**, **Geçerli projeyle Başlat** uygulamayı çalıştırın ve eşzamanlılık görselleştiricisi görüntülemek için. Aşağıdaki çizim üç yayılımları ve üç işaretçileri eşzamanlılık görselleştiricisi içinde gösterir.  
  
     ![Eşzamanlılık görselleştiricisi işaretçileri ve uyarılarla 3](../profiling/media/cvmarkersnative.png "CvMarkersNative")  
  
5.  Ek, özel işaretçisi serisi için oluşturucu çağırarak oluşturmak için kod ekleyin `marker_series` , işaret serisi için bir dize adını alır.  
  
    ```cpp  
  
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
  
6.  Eşzamanlılık görselleştiricisi görüntülemek için geçerli bir proje başlatın. İki işaret serisi kendi kulvarları iş parçacıkları görünümünde görünür. Aşağıdaki çizimde, iki yeni yayılma gösterir.  
  
     ![Eşzamanlılık görselleştiricisi 3 özel işaret serisi ile](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")  
  
### <a name="to-use-visual-basic-or-c"></a>Visual Basic veya C# ' ı kullanmak için  
  
1.  Eşzamanlılık görselleştiricisi SDK desteği uygulamanıza ekleyin. Daha fazla bilgi için [eşzamanlılık görselleştiricisi SDK'si](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Ekleme bir `using` veya `Imports` SDK bildirimi.  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
  
    ```  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
3.  Varsayılan işaret serisinin üç yayılma oluşturup yazma bayrağı, bir ileti ve bir uyarı, her aralık için kod ekleyin. Oluşturduğunuz bir <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Span> [EnterSpan] statik çağırarak (<!-- TODO: review code entity reference <xref:assetId:///EnterSpan?qualifyHint=False&amp;autoUpgrade=True>  -->) yöntemi. Varsayılan serinin yazmak için statik yazma yöntemlerini kullanın. <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> sınıfı.  
  
    ```vb  
  
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
  
4.  Menü çubuğunda, **Çözümle**, **eşzamanlılık görselleştiricisi**, **Geçerli projeyle Başlat** uygulamayı çalıştırın ve eşzamanlılık görselleştiricisi görüntülemek için. Aşağıdaki çizim üç yayılımları ve üç işaretçileri eşzamanlılık görselleştiricisi iş parçacıkları Görünümü'nde gösterir.  
  
     ![Eşzamanlılık görselleştiricisi işaretçileri ve uyarılarla](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")  
  
5.  Statik kullanarak müşteri işaret serisi oluşturmak için kod ekleyin <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.CreateMarkerSeries%2A> yöntemi. <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> Sınıfı yayılma oluşturma ve bayrakları, iletileri ve uyarılar yazma yöntemleri içerir.  
  
    ```vb  
  
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
  
6.  Eşzamanlılık görselleştiricisi görüntülemek için geçerli bir proje başlatın. Üç işaret serisi kendi kulvarları iş parçacıkları görünümünde görünür. Aşağıdaki çizim üç yeni yayılma gösterir.  
  
     ![Eşzamanlılık görselleştiricisi 3 özel işaret serisi ile](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)



