---
title: İş parçacıkları Paralel Yığınlar penceresini görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0bf1ca8fabf70f2d4fbe5920803773af07db0a99
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389234"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window"></a>İş parçacıkları ve görevler Paralel Yığınlar penceresinde görüntüleme

**Paralel Yığınlar** penceresi, çok iş parçacıklı uygulamalarda hata ayıklama için kullanışlıdır. Bu, birkaç görünüm vardır:

- [İş Parçacıkları görünümü](#threads-view) gösterir, uygulamadaki tüm iş parçacıkları için yığın bilgileri çağırın. İş parçacıkları ve bu iş parçacıkları üzerinde yığın çerçevelerini arasında gezinebilirsiniz. 

- [Görevler görünümü](#tasks-view) görev merkezli çağrı yığını bilgileri gösterir. 
  - Yönetilen kodda **görevleri** görüntüler, çağrı yığınlarını <xref:System.Threading.Tasks.Task?displayProperty=fullName> nesneleri. 
  - Yerel kodda **görevleri** görüntüler, çağrı yığınlarını [görev grupları](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [paralel algoritmalar](/cpp/parallel/concrt/parallel-algorithms), [zaman uyumsuz aracılar](/cpp/parallel/concrt/asynchronous-agents)ve [Basit görevler](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).  
  
- [Yöntem görünümü](#method-view) seçili bir yöntem çağrı yığınında döner. 

## <a name="use-the-parallel-stacks-window"></a>Paralel Yığınlar penceresini kullanma 

Açmak için **Paralel Yığınlar** penceresi, hata ayıklama oturumunda olması gerekir. Seçin **hata ayıklama** > **Windows** > **Paralel Yığınlar**. 

### <a name="toolbar-controls"></a>Araç çubuğu denetimleri

**Paralel Yığınlar** penceresinde aşağıdaki araç çubuğu denetimleri vardır: 

![Paralel Yığınlar penceresi araç çubuğu](../debugger/media/parallel_stackstoolbar.png "Paralel Yığınlar araç çubuğu")  
  
|Simge|Denetim|Açıklama|  
|-|-|-|  
|![İş parçacıklarının/görevlerin birleşik giriş kutusu](media/parallel_toolbar1.png "iş parçacıklarının/görevlerin birleşik giriş kutusu")|**İş parçacığı**/**görevleri** birleşik giriş kutusu|Görünüm arasında iş parçacığı yığınları çağırın ve çağrı yığınları görevlerin geçiş yapar. Daha fazla bilgi için [Görevler görünümü](#tasks-view) ve [iş parçacıkları görünümü](#threads-view).|  
|![Yalnızca bayraklı simgesini göster](media/parallel_toolbar2.png "Göster bayrağı yalnızca simgesi")|Yalnızca bayrak eklenmiş olanları göster|Gösterir gibi diğer hata ayıklayıcı pencerelerinde bayrağı yalnızca iş parçacığı için yığınları çağırın **GPU iş parçacıkları** penceresi ve **paralel izleme** penceresi.|  
|![Geçiş yöntemi görünümü simgesi](media/parallel_toolbar3.png "geçiş yöntemi görünümü simgesi")|İki durumlu **yöntemi görünümü**|Çağrı yığını görünümler arasında geçiş yapar ve **yöntemi görünümü**. Daha fazla bilgi için [yöntemi görünümü](#method-view).|  
|![Kaydırma için geçerli simge otomatik](media/parallel_toolbar4.png "geçerli simge otomatik Kaydır")|Geçerli yığın çerçevesine otomatik Kaydır|Geçerli yığın çerçevesi Autoscrolls graf görünümünde olduğunu. Bu özellik, geçerli yığın çerçevesi başka windows değiştirdiğinizde veya büyük grafikleri yeni bir kesme noktasına ulaştığınızda yararlı olur.|  
|![İki durumlu Yakınlaştır simgesi](media/parallel_toolbar5.png "geçiş Yakınlaştır simgesi")|Yakınlaştırma denetimini Aç/Kapat|Yakınlaştırma Denetimi pencerenin sol gizler veya gösterir. <br /><br />Yakınlaştırma denetimini görünürlüğünü bağımsız olarak, ayrıca tuşlarına basarak yakınlaştırabilirsiniz **Ctrl** ve fare tekerleğini kapatma veya göre tuşuna basarak **Ctrl**+**Shift** + **+** yakınlaştırmak için ve **Ctrl**+**Shift** + **-** uzaklaştırmak için. |  
  
### <a name="stack-frame-icons"></a>Yığın çerçeve simgeleri
Aşağıdaki simgeler, tüm görünümlerde etkin ve geçerli yığın çerçevesi hakkında bilgi sağlar:

|Simge|Açıklama|  
|-|-|  
|![Sarı ok](media/icon_parallelyellowarrow.gif)|Geçerli iş parçacığının geçerli konumu (etkin yığın çerçevesini) gösterir.|
|![İş parçacıkları simgesi](media/icon_parallelthreads.gif)|Geçerli olmayan bir iş parçacığı geçerli konumunu (etkin yığın çerçevesini) gösterir.|
|![Yeşil ok](media/icon_parallelgreenarrow.gif)|Geçerli yığın çerçevesi (geçerli hata ayıklayıcı bağlamı) gösterir. Yöntem adı göründüğü yerlerde bold olarak belirlenmiştir.|  

### <a name="context-menu-items"></a>Bağlam menüsü öğeleri  
Bir yönteme sağ tıkladığınızda aşağıdaki kısayol menüsü öğelerini kullanılabilir **iş parçacıkları** görünümü veya **görevleri** görünümü. Son altı öğe aynıdır [çağrı yığını penceresini](how-to-use-the-call-stack-window.md).  

![Paralel Yığınlar penceresi kısayol menüsü](../debugger/media/parallel_contmenu.png "Paralel Yığınlar penceresi kısayol menüsü")  

|Menü öğesi|Açıklama|  
|-|-|  
|**Bayrağı**|Seçili öğeyi işaretler.|  
|**İşaretini kaldır**|Seçili öğeyi unflags.|  
|**Dondurma**|Seçili öğeyi donuyor.|  
|**Çözme**|Seçili öğeyi thaws.|  
|**Çerçeveye geçiş yap**|Karşılık gelen menüsünden aynı komutu **çağrı yığını** penceresi. Bununla birlikte, **Paralel Yığınlar** penceresinde bir yöntem birkaç çerçevelerde olabilir. Bu öğe için alt menüde istediğiniz çerçeveyi seçebilirsiniz. Yığın çerçevelerini biri geçerli iş parçacığı üzerinde olduğunda, bu çerçeve menüde varsayılan olarak seçilidir.|  
|**Görev Git** veya **iş parçacığına Git**|Ağınızdan **görev** veya **iş parçacıkları** görünümü ve aynı yığın çerçeve vurgulanmış tutar.|  
|**Kaynak koduna Git**|Kaynak kod penceresi içinde ilgili konuma gider. |  
|**Ayrıştırma için Git**|İçinde ilgili konuma gider **ayrıştırılmış kodu** penceresi.|  
|**Dış Kodu Göster**|Dış kodu gizler veya gösterir.|  
|**Onaltılık gösterim**|Ondalık ve onaltılık görünen arasında geçiş yapar.|  
|**Kaynakta iş parçacıklarını Göster**|İş parçacığı kaynak kod penceresinde konumu işaretler. |  
|**Sembol yükleme bilgisi**|Açılır **sembol yükleme bilgisi** iletişim kutusu.|  
|**Sembol ayarları**|Açılır **sembol ayarları** iletişim kutusu. |  
  
## <a name="threads-view"></a>İş parçacıkları görünümü  

İçinde **iş parçacıkları** görüntülemek, yığın çerçevesi ve geçerli iş parçacığı arama yolunu mavi renkle vurgulanır. İş parçacığı geçerli konumunu sarı bir ok ile gösterilir. 

Geçerli yığın çerçevesini değiştirmek için farklı bir yöntemi çift tıklayın. Bu ayrıca seçtiğiniz yöntem geçerli iş parçacığı veya başka bir iş parçacığı bir parçası olup olmamasına bağlı olarak geçerli iş parçacığı, geçiş. 

Zaman **iş parçacıkları** grafı görüntüle penceresine sığmayacak kadar büyük bir **Kuşbakışı Görünüm** denetim penceresinde görünür. Grafiği farklı bölümlerine gitmek için denetiminde çerçeve taşıyabilirsiniz.  
  
Ana yönetilen yerel kod geçiş gider tek bir iş parçacığı aşağıda gösterilmiştir. Geçerli yöntemde altı akışlardır. Bir net_thread_sleep için devam eder ve başka Console.WriteLine ve ardından SyncTextWriter.WriteLine devam eder.  

 ![İş parçacıkları, Paralel Yığınlar penceresini görünümünde](../debugger/media/parallel_stack1.png "iş parçacıkları Görünümü'nde Paralel Yığınlar penceresi")  

Aşağıdaki tabloda ana özelliklerini açıklayan **iş parçacıkları** görüntüle:  
  
|Belirtme çizgisi|Öğe adı|Açıklama|  
|-|-|-|  
|1.|Çağrı yığını segment veya düğüm|Bir dizi yöntem için bir veya daha fazla iş parçacıklarını içerir. Çerçeve bağlı ok satır varsa, çerçeve iş parçacıkları için tüm arama yolunu gösterir.|  
|2|Mavi Vurgu|Geçerli iş parçacığı arama yolunu belirtir.|  
|3|Satırları oku|İş parçacıkları için tüm arama yolu oluşturan düğümlerin bağlanın.|  
|4|Düğümü üstbilgisi|İşlemler ve iş parçacıkları için düğüm sayısını gösterir.|  
|5|Yöntem|Aynı yöntem bir veya daha fazla yığın çerçevelerini temsil eder.|  
|6|Araç İpucu yöntemi|Bir yöntem geldiğinizde görünür. İçinde **iş parçacıkları** görünümünde, araç ipucunu gösteren tüm iş parçacıkları, benzer bir tablodaki **iş parçacıkları** penceresi. |  

## <a name="tasks-view"></a>Görevler görünümü  
Uygulamanız kullanıyorsa <xref:System.Threading.Tasks.Task?displayProperty=fullName> nesneleri (yönetilen kod için) veya `task_handle` kullanabileceğiniz paralellik ifade etmek için (yerel kod için) nesneleri, **görevleri** görünümü. **Görevleri** görünümü görevleri yerine iş parçacığı çağrı yığınlarını gösterir. 

İçinde **görevleri** görüntüle:  
  
- Görevleri çalıştırmadığınız iş parçacığı çağrı yığınlarını gösterilmez.  
- Görevleri çalıştıran iş parçacığı çağrı yığınlarını, üst ve alt görevler için en uygun çerçeve göstermek için görsel olarak atılır.  
- Çeşitli görevleri bir iş parçacığı üzerinde olduğunda, bu görevlerin çağrı yığınlarını ayrı düğüm gösterilir.  

Bütün çağrı yığını görmek için dönmek **iş parçacıkları** tarafından bir yığın çerçevesine sağ tıklayıp, Görünüm **iş parçacığına Git**.  

Aşağıdaki çizimde gösterildiği **iş parçacıkları** en üst sırada ve karşılık gelen Görünüm **görevleri** altındaki görünümü.  

![İş parçacıkları ve görevler görünümleri](../debugger/media/parallel_threads-tasks.png "iş parçacıkları ve görevler görünümleri")  

Ek bilgi içeren bir araç ipucunu göstermek için bir yöntem üzerine gelin. İçinde **görevleri** görünümünde, araç ipucunu gösteren tüm görevleri bir tablodaki benzer şekilde **görevleri** penceresi. 

Aşağıdaki resimde araç ipucu için bir yöntem gösterilmektedir **iş parçacıkları** görünümü üst ve karşılık gelen için **görevleri** altındaki görünümü.  

![İş parçacıkları ve Görevler araç ipuçları](../debugger/media/parallel_threads-tasks-tooltips.png "iş parçacıkları ve Görevler araç ipuçları")  

## <a name="method-view"></a>Metot görüntüle  
Da **iş parçacıkları** görünümü veya **görevleri** görünümü seçerek geçerli yöntemi grafikte Özet **yöntemi görünüme Değiştir** araç çubuğundaki simgeye. **Yöntem görünümü** bir bakışta tüm yöntemleri çağırın ya da geçerli yöntemi tarafından çağrılır tüm iş parçacıklarını gösterir. Aşağıdaki çizimde aynı bilgileri nasıl göründüğünü gösterir **iş parçacıkları** soldaki ve görüntüleme **yöntemi görünümü** sağ.  

![İş Parçacıkları görünümü ve yöntem görünümü](../debugger/media/parallel_methodview.png "iş parçacıkları görünümü ve görünüm yöntemi")  
  
Yeni bir yığın çerçevesine geçiş yapıyorsanız, bu yöntem geçerli yöntemi yapın ve **yöntemi görünümü** tüm çağıranlar ve çağrılanlar yeni yöntemi gösterir. Bu, bazı iş parçacıklarının görünmesini veya kaybolmasını bu yöntem çağrı yığınlarıyla görüntülenip bağlı olarak bu görünümden neden olabilir. Çağrı yığını görünümüne dönmek için seçin **yöntemi görünümü** yeniden araç çubuğu simgesi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çok iş parçacıklı bir uygulamanın hatalarını ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md)   
 [İzlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Hata ayıklayıcı temel bilgileri](../debugger/getting-started-with-the-debugger.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Paralel Programlama](/dotnet/standard/parallel-programming/index)   
 [Görevler penceresini kullanma](../debugger/using-the-tasks-window.md)   
 [Görev sınıfı](../extensibility/debugger/task-class-internal-members.md)
