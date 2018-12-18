---
title: Kullanarak Paralel Yığınlar penceresini | Microsoft Docs
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
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 602fdd683ecb1b3244289c305e4fc850d337b03e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792040"
---
# <a name="using-the-parallel-stacks-window"></a>Paralel Yığınlar Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Paralel Yığınlar** penceresi, çok iş parçacıklı uygulamalarda hata ayıklama işlemi yaparken yararlıdır. Kendi **iş parçacıkları görünümü** gösterir, uygulamanızdaki tüm iş parçacıkları için yığın bilgileri çağırın. İş parçacıkları ve bu iş parçacıkları üzerinde yığın çerçevelerini arasında gezinmenize olanak tanır. Yönetilen kodda **Görevler görünümü** gösterir çağrı yığını <xref:System.Threading.Tasks.Task?displayProperty=fullName> nesneleri. Yerel kodda **Görevler görünümü** gösterir çağrı yığını [görev grupları](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [paralel algoritmalar](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [zaman uyumsuz aracılar](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)ve [Basit görevler](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>İş Parçacıkları Görünümü  
 A B ve dış kod ana gittiğiniz tek bir iş parçacığı aşağıda gösterilmiştir. Diğer iki iş parçacığı bazı dış koddan çalışmaya ve B ve dış kod devam iş parçacıkları ve C ve ardından bazı AnonymousMethod devam diğer iş parçacığı biri, bir sorun oluştu.  
  
 ![İş parçacıkları, Paralel Yığınlar penceresini görünümünde](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 Çizimde, geçerli iş parçacığı arama yolunu mavi renkle vurgulanır ve etkin yığın çerçevesini sarı bir ok ile belirtilir. Geçerli yığın çerçevesi, farklı bir yöntemde seçerek değiştirebilirsiniz **Paralel Yığınlar** penceresi. Ayrıca seçtiğiniz yönteme geçerli iş parçacığı zaten başka bir iş parçacığı veya bir parçası olup olmamasına bağlı olarak geçerli iş parçacığı, geçiş de neden olabilir. Aşağıdaki tabloda ana özelliklerini açıklayan **Paralel Yığınlar** çizimde gösterildiği gibi penceresi.  
  
|Belirtme çizgisi harf|Öğe adı|Açıklama|  
|--------------------|------------------|-----------------|  
|BİR|Çağrı yığını Segment veya düğüm|Bir dizi bir veya daha fazla iş parçacığı için bağlamı yöntemi içerir. Ardından ona bağlı ok satır düğüm yok, iş parçacıkları için tüm arama yolunu temsil eder.|  
|B|Mavi Vurgu|Geçerli iş parçacığı arama yolunu belirtir.|  
|C|Satırları oku|İş parçacıkları için tüm arama yolu oluşturan düğümlerin bağlanın.|  
|D|Düğüm üst araç ipucu|Bu düğüm, arama yolu paylaşan her bir iş parçacığı kullanıcı tanımlı adını ve Kimliğini gösterir.|  
|E|Bağlam yöntemi|Aynı yöntem bir veya daha fazla yığın çerçevelerini temsil eder.|  
|F|Araç İpucu bağlamında yöntemi|İş Parçacıkları görünümü'nde, tüm iş parçacıkları tabloda benzer gösterir **iş parçacıkları** penceresi. Görev Görünümü'nde, tüm görevleri bir tablodaki benzer gösterir **Paralel Görevler** penceresi.|  
  
 Ayrıca, Paralel Yığınlar penceresini gösteren bir **Kuşbakışı Görünüm** graf pencereye sığdırmak için çok büyük olduğunda ana bölmede simgesi. Grafın tamamında penceresinde görmek için simgesine tıklayabilirsiniz.  
  
## <a name="method-context-icons"></a>Bağlam simgeler yöntemi  
 Aşağıdaki tabloda, etkin ve geçerli yığın çerçevesi hakkında bilgi sağlayan simgeleri açıklanmaktadır:  
  
|||  
|-|-|  
|Simge|Açıklama|  
|![Paralel Yığınlar sarı ok](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Yöntem bağlamı geçerli iş parçacığının etkin yığın çerçevesini içerdiğini gösterir.|  
|![Paralel Yığınlar İş parçacıkları simgesi](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Yöntem bağlamı geçerli olmayan bir iş parçacığının etkin yığın çerçevesini içerdiğini gösterir.|  
|![Paralel Yığınlar yeşil ok](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Yöntem bağlamı geçerli yığın çerçevesi içerdiğini gösterir. Bu yöntem adı göründüğü tüm düğümlerin bold olarak belirlenmiştir.|  
  
## <a name="toolbar-controls"></a>Araç çubuğu denetimleri  
 Aşağıdaki şekil ve tabloda Paralel Yığınlar araç çubuğundaki denetimleri açıklanmaktadır.  
  
 ![Paralel Yığınlar penceresi araç çubuğu](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Belirtme çizgisi harf|Denetim|Açıklama|  
|--------------------|-------------|-----------------|  
|BİR|İş parçacıklarının/görevlerin birleşik giriş kutusu|Görünüm arasında iş parçacığı yığınları çağırın ve çağrı yığınları görevlerin geçiş yapar. Görevler görünümü ve iş parçacıkları görünümü daha fazla bilgi için bkz.|  
|B|Yalnızca bayrak eklenmiş olanları göster|Gösterir gibi diğer hata ayıklama pencerelerinde bayrağı yalnızca iş parçacığı için yığınları çağırın **GPU iş parçacıkları** penceresi ve **paralel izleme** penceresi.|  
|C|Metot görünümünü Aç/Kapat|Yığın görünümü ve yöntem görünümü arasında geçiş yapar. Daha fazla bilgi için yöntemi görmek.|  
|D|Geçerli yığın çerçevesine otomatik Kaydır|Geçerli yığın çerçevesi Autoscrolls diyagram görünümünde olduğunu. Geçerli yığın çerçevesi başka windows değiştirirken veya büyük diyagramlarında yeni kesme noktasına ulaşma bu özellik yararlıdır.|  
|E|Yakınlaştırma denetimini Aç/Kapat|Yakınlaştırma denetimini gizler veya gösterir. Kullanarak veya CTRL tuşuna basarak ve fare tekerleğini yakınlaştırma denetimi görünürlüğünü bakılmaksızın kapatma yakınlaştırma yapabilirsiniz **CTRL + SHIFT + '+'** yakınlaştırmak için ve **CTRL + SHIFT +'-'** uzaklaştırmak için. Tuşuna basarak **CTRL + F8** ekrana sığacak şekilde Yakınlaştır.|  
  
### <a name="context-menu-items"></a>Bağlam menüsü öğeleri  
 Aşağıdaki şekil ve tabloda, iş parçacıkları görünümü veya Görevler görünümü yöntemi bağlamda sağ tıklattığınızda, kullanılabilen kısayol menüsü öğelerini açıklar. Son altı öğe, doğrudan çağrı yığını penceresinden ödünç ve yeni bir davranış sunar.  
  
 ![Paralel Yığınlar penceresi kısayol menüsü](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Menü Öğesi|Açıklama|  
|---------------|-----------------|  
|Bayrağı|Seçili öğeyi işaretler.|  
|İşaretini kaldır|Seçili öğeyi unflags.|  
|Dondurma|Seçili öğeyi donuyor.|  
|Çözme|Seçili öğeyi thaws.|  
|Görev (iş parçacığı) geçin|Araç çubuğunda birleşik giriş kutusu aynı işlevi gerçekleştirir, ancak aynı yığın çerçevesini vurgulanmış halde tutar.|  
|Kaynak koduna Git|Kullanıcı sağ yığın çerçevesi için karşılık gelen kaynak kodu konumuna gider.|  
|Çerçeveye geçiş yap|Çağrı yığını penceresinde karşılık gelen menü komutu ile aynıdır. Ancak, Paralel Yığınlar ile birden çok çerçeve için bir yöntem bağlamı karşılık gelebilir. Bu nedenle, her biri belirli bir yığın çerçevesini temsil eden alt menüler, menü öğesi vardır. Yığın çerçevelerini biri geçerli iş parçacığı üzerinde olduğunda, ardından bu yığın çerçevesi için karşılık gelen menü seçilir.|  
|Ayrıştırma için Git|Kullanıcı sağ yığın çerçevesi için karşılık gelen ayrıştırma penceresinde konumuna gider.|  
|Dış Kodu Göster|Dış kodu gizler veya gösterir.|  
|Onaltılık gösterim|Ondalık ve onaltılık görünen arasında geçiş yapar.|  
|Sembol Yükleme Bilgisi|Karşılık gelen iletişim kutusunu görüntüler.|  
|Sembol ayarları|Karşılık gelen iletişim kutusunu görüntüler.|  
  
## <a name="tasks-view"></a>Görevler görünümü  
 Uygulamanızı kullanıyorsa <xref:System.Threading.Tasks.Task?displayProperty=fullName> nesneleri (yönetilen kod için) veya `task_handle` paralellik ifade etmek için (yerel kod için) nesneleri, geçiş yapmak Paralel Yığınlar penceresi araç çubuğu birleşik giriş kutusunda kullanabilirsiniz *Görevler görünümü*. Görev Görünümü görevleri yerine iş parçacığı çağrı yığınlarını gösterir. Görevler görünümü iş parçacıkları Görünümü'ndeki aşağıdaki şekilde farklıdır:  
  
- Görevler ile çalışan iş parçacığı çağrı yığınlarını gösterilmez.  
  
- Görevleri çalıştıran iş parçacığı çağrı yığınlarını görsel olarak göster görevlere ait ilgilendiren çerçeveleri için altındaki ve üstündeki atılır.  
  
- Birden çok görev bir iş parçacığı üzerinde olduğunda, bu görevlerin çağrı yığınları farklı düğümlere bölünür.  
  
  Paralel Yığınlar Görevler görünümü sağ ve sol taraftaki karşılık gelen iş parçacıkları görünümü aşağıda gösterilmiştir.  
  
  ![Görevler Paralel Yığınlar penceresini görünümünde](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Tüm çağrı yığınını görmek için yalnızca iş parçacığı yığın çerçevesi sağ tıklatıp ardından görünümüne dönebilirsiniz **iş parçacığına Git**.  
  
  Bir yöntem bağlamı gelerek önceki tabloda açıklandığı gibi ek bilgileri görebilirsiniz. Aşağıdaki görüntüde iş parçacıkları görünümü ve Görevler görünümü için araç ipucunda bilgileri gösterir.  
  
  ![Paralel Yığınlar penceresini araç ipuçlarında](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Metot görüntüle  
 İş Parçacıkları görünümü veya Görevler görünümünde, araç çubuğundaki yöntemi görünümü simgesine tıklayarak geçerli yöntemi grafikte Özet. Yöntemi bir bakışta tüm yöntemleri çağırmak ya da geçerli yöntemi tarafından çağrılır tüm iş parçacıkları üzerinde görüntüler. Aşağıdaki çizimde, iş parçacıkları görünümü ve de aynı bilgileri yöntemi Görünümü'nde nasıl göründüğünü gösterir.  
  
 ![Paralel Yığınlar penceresini yöntemi görünümünde](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Yeni bir yığın çerçevesine geçiş, bu yöntem geçerli yöntemi olun ve tüm çağıranlar ve çağrılanlar yeni yöntem için gösterilecek yol. Bu, bazı iş parçacıklarının görünmesini veya kaybolmasını bu yöntem çağrı yığınlarıyla görüntülenip bağlı olarak bu görünümden neden olabilir. Yığın görünümüne dönmek için görünümü araç çubuğu düğmesini tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Hata ayıklayıcı temel bilgileri](../debugger/debugger-basics.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Paralel Programlama](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Görevleri penceresini kullanma](../debugger/using-the-tasks-window.md)   
 [İzlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Task Sınıfı](../extensibility/debugger/task-class-internal-members.md)



