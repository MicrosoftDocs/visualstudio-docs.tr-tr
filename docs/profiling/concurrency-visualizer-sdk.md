---
title: Eşzamanlılık görselleştiricisi SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c02959f30f89b8f7c79527026404099a4452a827
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691192"
---
# <a name="concurrency-visualizer-sdk"></a>Eşzamanlılık Görselleştiricisi SDK
Eşzamanlılık görselleştiricisi ek bilgileri görüntülemek için eşzamanlılık görselleştiricisi SDK'sını kullanarak kaynak kodunuzu işaretleyebilir. Ek verileri kodunuzda aşamaları ve olaylarla ilişkilendirebilirsiniz. Bu ek görsel olarak da bilinir *işaretçileri*.  Bir giriş için bkz [eşzamanlılık görselleştiricisi SDK'sı giriş](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Özellikler  
 Bayrakları, yayılma ve her iki özellik iletiniz: kategori ve önem derecesi. İçinde [Gelişmiş ayarları](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda görüntülenen işaretçileri kümesini filtrelemek için bu özellikleri kullanabilirsiniz. Ayrıca, bu özellikler işaretçileri görsel gösterimi etkiler. Örneğin, bayrakları boyutunu önem temsil etmek için kullanılır. Ayrıca, renk kategori göstermek için kullanılır.  
  
## <a name="basic-usage"></a>Temel kullanım  
 Eşzamanlılık görselleştiricisi işaretleyicileri oluşturmak için kullanabileceğiniz varsayılan bir sağlayıcı gösterir. Sağlayıcı ile birlikte eşzamanlılık görselleştiricisi zaten kayıtlı ve kullanıcı Arabiriminde görünen işaretçileri yapmak için başka bir şey yapmanıza gerek yoktur.  
  
### <a name="c-and-visual-basic"></a>C# ve Visual Basic  
 C#, Visual basic ve diğer yönetilen kod, varsayılan sağlayıcı çağırarak kullanmak <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. İşaretçileri oluşturmak için dört işlevleri sunar: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>, ve <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Varsayılan özelliklerini kullanmak istediğinize bağlı olarak bu işlevler için birden çok aşırı vardır.  En basit aşırı olayın açıklamasını belirten bir dize parametresi alan. Açıklama eşzamanlılık görselleştiricisi raporlarında görüntülenir.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesine SDK desteği eklemek için  
  
1.  Menü çubuğunda seçin **Çözümle**, **eşzamanlılık görselleştiricisi**, **ekleme SDK projesine**.  
  
2.  İstediğiniz SDK erişmeye ve sonra projeyi seçin **Seçili proje SDK ekleme** düğmesi.  
  
3.  Bir Imports veya kodunuzu deyimiyle ekleyin.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 C++'da, oluşturma bir [marker_series sınıfı](../profiling/marker-series-class.md) nesne ve işlevleri çağırmak için kullanın.  `marker_series` Sınıfı işaretleyicileri oluşturmak için üç işlevleri sunar [marker_series::write_flag yöntemi](../profiling/marker-series-write-flag-method.md), [marker_series::write_message yöntemi](../profiling/marker-series-write-message-method.md)ve [işaretçi_ Series::write_alert yöntemi](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Bir C++ veya C projeye SDK desteği eklemek için  
  
1.  Menü çubuğunda seçin **Çözümle**, **eşzamanlılık görselleştiricisi**, **ekleme SDK projesine**.  
  
2.  İstediğiniz SDK erişmeye ve sonra projeyi seçin **Seçili proje SDK ekleme** düğmesi.  
  
3.  C++ için dahil `cvmarkersobj.h`. C için dahil `cvmarkers.h`.  
  
4.  Kullanarak bir ekleme deyimi, kodunuzun.  
  
    ```cpp  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Oluşturma bir `marker_series` nesne ve ona geçirin `span` Oluşturucusu.  
  
    ```C++  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Özel kullanım  
 Gelişmiş senaryolar için eşzamanlılık görselleştiricisi SDK'sı daha fazla denetim sunar.  İki ana kavramlar daha Gelişmiş senaryolar ile ilişkilidir: işaret sağlayıcıları ve işaret serisi. İşaretçi, farklı ETW sağlayıcılar (her sahip farklı bir GUID) sağlayıcılarıdır. İşaretçi bir sağlayıcı tarafından oluşturulan olaylar seri kanalları oluşur. Bir işaretçi sağlayıcısı tarafından oluşturulan olaylar düzenlemek için bunları kullanabilirsiniz.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Yeni bir işaret sağlayıcı bir C# veya Visual Basic projesinde kullanmak için  
  
1.  Oluşturma bir <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> nesnesi.  Oluşturucu bir GUID alır.  
  
2.  Sağlayıcıyı kaydetmek için eşzamanlılık görselleştiricisi açmak [Gelişmiş ayarları](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusu.  Seçin **işaretçileri** sekmesini ve ardından **Yeni Sağlayıcı Ekle** düğmesi. İçinde [Gelişmiş ayarları](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda, sağlayıcı ve sağlayıcının açıklamasını oluşturmak için kullanılan GUID girin.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>C++ veya C projede yeni bir işaret sağlayıcısı kullanmak için  
  
1.  Kullanım `CvInitProvider` işlevi bir PCV_PROVIDER başlatılamadı.  Bir GUID * ve PCV_PROVIDER Oluşturucusu alır\*.  
  
2.  Sağlayıcıyı kaydetmek için açık [Gelişmiş ayarları](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusu.  Seçin **işaretçileri** sekmesini ve ardından **Yeni Sağlayıcı Ekle** düğmesi. Bu iletişim kutusunda sağlayıcısı ve sağlayıcı açıklamasını oluşturmak için kullanılan GUID girin.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesinde işaret serisi kullanmak için  
  
1.  Yeni bir kullanmak için <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, ilk kullanarak oluşturma bir <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> nesne ve ardından işaret olayları doğrudan yeni serisinden oluşturun.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");  
    series1.WriteFlag("My flag");  
    ```  
  
    ```VB  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")  
    series1.WriteFlag("My flag")  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>C++ projesinde işaret serisi kullanma  
  
1.  Oluşturma bir `marker_series` nesnesi.  Bu yeni serisinden olaylar oluşturabilir.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Bir işaretçi serisi C projesinde kullanmak için  
  
1.  Kullanım `CvCreateMarkerSeries` bir PCV_MARKERSERIES oluşturmak için işlevi.  
  
    ```C++  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[C++ Kitaplık Başvurusu](../profiling/cpp-library-reference.md)|Eşzamanlılık görselleştiricisi API için C++ açıklar.|  
|[C Kitaplık Başvurusu](../profiling/c-library-reference.md)|Eşzamanlılık görselleştiricisi API C. açıklar|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Yönetilen kod için eşzamanlılık görselleştiricisi API açıklar.|  
|[Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)|Eşzamanlılık yöntemi kullanılarak oluşturulur ve iş parçacığı yürütme verileri içeren veri dosyalarını profil oluşturma raporları ve görünümleri için başvuru bilgileri.|