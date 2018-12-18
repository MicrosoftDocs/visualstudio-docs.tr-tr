---
title: Eşzamanlılık görselleştiricisi SDK'sı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d98a5383a330242110bef860b9dc19a2fb6bef87
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754825"
---
# <a name="concurrency-visualizer-sdk"></a>Eşzamanlılık Görselleştiricisi SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşzamanlılık Görselleştiricisindeki ek bilgileri görüntülemek için eşzamanlılık görselleştiricisi SDK'sını kullanarak kaynak kodunuz izleyebilirsiniz. Ek veri kodunuzda aşamaları ve olaylarla ilişkilendirebilirsiniz. Bu ek görselleştirmeler olarak bilinen *işaretçileri*.  Tanıtım amaçlı bir kılavuz için bkz. [eşzamanlılık görselleştiricisi SDK'sı ile tanışın](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Özellikler  
 Bayrakları, yayılımları ve her iki özelliğe sahip iletileri: kategori ve önem derecesi. İçinde [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda görüntülenen işaretçileri kümesini filtrelemek için bu özellikleri kullanabilirsiniz. Ayrıca, bu özellikleri işaretçileri görsel temsilini etkiler. Örneğin, bayrakları boyutunu önem göstermek için kullanılır. Ayrıca, renk kategorisi belirtmek için kullanılır.  
  
## <a name="basic-usage"></a>Temel kullanım  
 Eşzamanlılık görselleştiricisi işaretleyicileri oluşturmak için kullanabileceğiniz bir varsayılan sağlayıcıyı gösterir. Eşzamanlılık görselleştiricisi ile birlikte bir sağlayıcı zaten kayıtlı ve işaretçileri kullanıcı Arabiriminde görünür yapmak için başka bir şey yapmanız gerekmez.  
  
### <a name="c-and-visual-basic"></a>C# ve Visual Basic  
 C#, Visual basic ve diğer yönetilen kod, çağrı yaparak ve varsayılan sağlayıcıyı kullanmak <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. İşaretçileri oluşturmak için dört işlev sunar: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>, ve <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Varsayılan özelliklerini kullanmak istediğinize bağlı olarak, bu işlevler için birden fazla aşırı yüklemeleri vardır.  En basit aşırı olayın açıklamasını belirten bir dize parametresi alır. Açıklama, Concurrency Visualizer raporlarında görüntülenir.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesi için SDK desteği eklemek için  
  
1.  Menü çubuğunda, **Çözümle**, **eşzamanlılık görselleştiricisi**, **SDK proje ekleme**.  
  
2.  Erişim SDK'yı ve ardından istediğiniz projeyi seçin **Seçili projeye Ekle SDK** düğmesi.  
  
3.  Bir Imports veya using deyimini kodunuza ekleyin.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 C++'ta, oluşturun bir [marker_series sınıfı](../profiling/marker-series-class.md) nesne ve işlevlerini çağırmak için kullanın.  `marker_series` Sınıfı gösterir, işaretçiler oluşturmak için üç işlev [marker_series::write_flag yöntemi](../profiling/marker-series-write-flag-method.md), [marker_series::write_message yöntemi](../profiling/marker-series-write-message-method.md)ve [işaretçi_ Series::write_alert yöntemi](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Bir C ya da C++ projesine SDK desteği eklemek için  
  
1.  Menü çubuğunda, **Çözümle**, **eşzamanlılık görselleştiricisi**, **SDK proje ekleme**.  
  
2.  Erişim SDK'yı ve ardından istediğiniz projeyi seçin **Seçili projeye Ekle SDK** düğmesi.  
  
3.  C++ için ekleme `cvmarkersobj.h`. C için dahil `cvmarkers.h`.  
  
4.  Kullanarak bir ekleme kodunuzu deyimi.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Oluşturma bir `marker_series` nesne ve geçirin `span` Oluşturucusu.  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Özel kullanım  
 Gelişmiş senaryolar için daha fazla denetim eşzamanlılık görselleştiricisi SDK'sı sunar.  İki ana kavram daha gelişmiş senaryoları ile ilişkili: işaretleyicisi sağlayıcılarını ve işaret serisi. İşaretçisi, farklı ETW sağlayıcılarını (her farklı bir GUID vardır) sağlayıcılarıdır. Bir sağlayıcı tarafından oluşturulan olayları seri kanalları işaret oluşur. İşaretleyici sağlayıcı tarafından oluşturulan olayları düzenlemek için bunları kullanabilirsiniz.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesinde yeni bir işaretleyici sağlayıcısını kullanmak için  
  
1.  Oluşturma bir <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> nesne.  Oluşturucusu bir GUID alır.  
  
2.  Sağlayıcıyı kaydetmek için eşzamanlılık görselleştiricisi'ni açın [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusu.  Seçin **işaretçileri** sekmesine ve ardından **Yeni Sağlayıcı Ekle** düğmesi. İçinde [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda, sağlayıcısı ve sağlayıcı açıklamasını oluşturmak için kullanılan GUID girin.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Bir C ya da C++ projesinde yeni bir işaretleyici sağlayıcısını kullanmak için  
  
1.  Kullanım `CvInitProvider` işlevi bir PCV_PROVIDER başlatılamadı.  Bir GUID * ve PCV_PROVIDER Oluşturucusu alır\*.  
  
2.  Sağlayıcıyı kaydetmek için açık [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusu.  Seçin **işaretçileri** sekmesine ve ardından **Yeni Sağlayıcı Ekle** düğmesi. Bu iletişim kutusunda sağlayıcısı ve sağlayıcı açıklamasını oluşturmak için kullanılan GUID girin.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesinde bir işaret serisi kullanmak için  
  
1.  Yeni bir kullanılacak <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, kullanarak ilk oluşturmak bir <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> nesne ve işaret olayları doğrudan yeni dizisinden sonra oluşturmak.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Bir C++ projesinde bir işaret serisi kullanmak için  
  
1.  Oluşturma bir `marker_series` nesne.  Bu yeni serisinden olaylar oluşturabilir.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Bir C projesi içinde bir işaret serisi kullanmak için  
  
1.  Kullanım `CvCreateMarkerSeries` bir PCV_MARKERSERIES oluşturmak için işlevi.  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[C++ Kitaplık Başvurusu](../profiling/cpp-library-reference.md)|Eşzamanlılık görselleştiricisi API'si için C++ açıklar.|  
|[C Kitaplığı Başvurusu](../profiling/c-library-reference.md)|Eşzamanlılık görselleştiricisi API C. açıklar.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Yönetilen kod için eşzamanlılık görselleştiricisi API açıklar.|  
|[Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)|Görünümleri ve raporları, eşzamanlılık yöntemi kullanılarak oluşturulur ve iş parçacığı yürütme verileri içeren veri dosyalarını profil oluşturma için başvuru bilgileri.|



