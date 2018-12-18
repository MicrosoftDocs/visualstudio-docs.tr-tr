---
title: Using the Tasks Window | Microsoft Docs
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
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa59e1e57750c9c2075c10c76ab5c518ed0e8686
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793912"
---
# <a name="using-the-tasks-window"></a>Görevleri Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Görevleri** pencere benzeyen **iş parçacıkları** BT'nin hakkında bilgileri gösterir ancak pencere <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7), veya [WinJS.Promise ](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) yerine her bir iş parçacığı nesneleri. İş parçacığı gibi görevleri aynı anda çalışabilecek zaman uyumsuz işlemleri temsil eder; Ancak, birden çok görev aynı iş parçacığı üzerinde çalışabilir. Bkz: [zaman uyumsuz programlama (Windows Store apps) javascript'teki](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) daha fazla bilgi için.  
  
 Yönetilen kodda kullanabileceğiniz **görevleri** ile çalışırken penceresi <xref:System.Threading.Tasks.Task?displayProperty=fullName> nesneleri veya **await** ve **zaman uyumsuz** anahtar sözcükleri (**Await** ve **zaman uyumsuz** VisualBasic içinde). Yönetilen kodda görevleri hakkında daha fazla bilgi için bkz. [paralel programlama](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 Yerel kod halinde kullanabileceğiniz **görevleri** ile çalışırken penceresi [görev grupları](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [paralel algoritmalar](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [zaman uyumsuz aracılar](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a), ve [Basit görevler](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90). Yerel kodda görevleri hakkında daha fazla bilgi için bkz. [eşzamanlılık çalışma zamanı](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 JavaScript'te, promise .then kodla çalışırken görevler penceresini kullanabilirsiniz.  
  
 Kullanabileceğiniz **görevleri** hata ayıklayıcıya girdikten zaman penceresi. Şirket erişim **hata ayıklama** tıklayarak menü **Windows** tıklayıp **görevleri**. Aşağıdaki çizimde gösterildiği **görevleri** kendi varsayılan modunda penceresi.  
  
 ![Paralel Görevler penceresi](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  Yönetilen kodda bir <xref:System.Threading.Tasks.Task> durumu olan <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus>, veya <xref:System.Threading.Tasks.TaskStatus> yönetilen iş parçacıklarını bir uyku ya da birleştirme durumdayken Görevler penceresinde görüntülenmeyebilir.  
  
## <a name="tasks-column-information"></a>Görevleri sütun bilgileri  
 Sütunları **görevleri** penceresi, aşağıdaki bilgileri gösterir.  
  
|Sütun adı|Açıklama|  
|-----------------|-----------------|  
|**bayrakları**|Hangi görevlerin işaretlenmiş gösterir ve bir görevi işaretleme veya işaretini kaldırma olanak tanır.|  
|**Simgeler**|Sarı bir ok, geçerli görev gösterir. Geçerli görev, geçerli iş parçacığı üzerinde en üstteki görevdir.<br /><br /> Bölme görevi, diğer bir deyişle, hata ayıklayıcı çağrıldığında geçerli bir beyaz bir ok gösterir.<br /><br /> Duraklatma simgesi, kullanıcı tarafından dondurulmuş bir görevi gösterir. Dondurma ve bir görev listesinde sağ tıklayarak Çöz.|  
|**ID**|Görev için sistem tarafından sağlanan bir sayı. Yerel kod halinde, bu görev adresidir.|  
|**Status**|Geçerli durumu (zamanlanmış, etkin, kilitlenen, bekleyen veya tamamlanmış) görev. Zamanlanmış bir görev henüz çalıştırılmadı ve bu nedenle, henüz bir çağrı yığını, atanan bir iş parçacığı veya ilgili bilgiler yok biridir.<br /><br /> Etkin görev kodu hata ayıklayıcıda kesmeden önce yürütülen biridir.<br /><br /> Bekleyen görev sinyal bir olay, bir kilidi serbest bırakılması veya başka bir görevi tamamlamak için beklediği, engellenen biridir.<br /><br /> Kilitlenen bir görevi başka bir iş parçacığıyla, iş parçacığı kilitlendiğini bekleyen bir görevdir.<br /><br /> Üzerine **durumu** hücre bloğu hakkında daha fazla bilgi kilitlenen veya bekleyen bir görev için. **Uyarı:** **görevleri** penceresi bekleyin zinciri geçişi (WCT) tarafından desteklenen eşitleme temel kullanan bir engellenen görev için kilitlenme bildirir. Örneğin, bir kilitlenen <xref:System.Threading.Tasks.Task> WCT, hata ayıklayıcı raporları kullanan nesne **bekleme kilitlendiğini**. Eşzamanlılık WCT kullanmaz, çalışma zamanı tarafından yönetilen kilitlenen bir görev için hata ayıklayıcı raporları **bekleyen**. WCT hakkında daha fazla bilgi için bkz: [bekleyin zinciri geçişi](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Başlangıç saati**|Saat, görev etkin hale geldi.|  
|**Süresi**|Görev etkin biçimde saniye sayısı.|  
|**Tamamlanma Zamanı**|Hangi görev tamamlanma zamanı.|  
|**Konum**|Görevin çağrı yığınındaki geçerli konum. Görev için bütün çağrı yığını görmek için bu hücreyi üzerine gelin. Zamanlanmış Görevler, bu sütunda bir değer yoktur.|  
|**Görev**|İlk yöntem ve oluşturulduğunda bu göreve geçirilen bağımsız değişkenler.|  
|**Üst**|Bu görevi oluşturan görevin kimliği. Boş ise, hiçbir üst görev vardır. Bu yalnızca yönetilen programlar için geçerlidir.|  
|**İş parçacığı atama**|Görevin üzerinde çalıştığı iş parçacığının adı ve kimliği.|  
|**Dönüş durumu**|Tamamlandığında, görev durumu. Dönüş durumu değerler **başarı**, **iptal edildi**, ve **hata**.|  
|**AppDomain**|Yönetilen kod için görevin yürütüldüğü uygulama etki alanı.|  
|**task_group**|Yerel kod, adresini [task_group](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) zamanlanmış görev nesnesi. Zaman uyumsuz aracılar ve Basit görevler için bu sütun 0 olarak ayarlanır.|  
|İşlem|Görevin üzerinde çalıştığı işlem kimliği.|  
|Zaman uyumsuz durumu|Yönetilen kod için görev durumu. Bu sütun varsayılan olarak gizlidir. Bu sütunu görüntülemek için bir sütun başlıkları için bağlam menüsünü açın. Seçin **sütunları**, **AsyncState**.|  
  
 Bir sütunun başlığına sağ tıklayıp sonra istediğiniz sütunları seçerek görünüme sütun ekleyebilirsiniz. (Seçim işaretini kaldırarak sütunları kaldırın.) Sütun sağa veya sola sürükleyerek de yeniden sıralayabilirsiniz. Sütun kısayol menüsünü aşağıdaki çizimde gösterilmektedir.  
  
 ![Paralel Görevler penceresi kısayol Görünüm menüsünde](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Sıralama görevleri  
 Görevleri sütun ölçütlerine göre sıralamak için sütun başlığına tıklayın. Tıklayarak gibi **kimliği** sütun üst bilgisine görevleri görev Kimliğine göre sıralayabilirsiniz: 1,2,3,4,5 ve benzeri. Sıralama düzenini tersine çevirmek için sütun başlığını tekrar tıklatın. Geçerli sıralama sütunu ve sıralama düzenini sütununda bir ok ile belirtilir.  
  
## <a name="grouping-tasks"></a>Görevleri gruplandırma  
 Görevleri liste görünümünde herhangi bir sütuna göre gruplandırabilirsiniz. Tıklanarak gibi **durumu** sütun başlığını ve ardından **durumuna göre grup**, aynı durumunda olan tüm görevleri gruplayabilirsiniz. Örneğin, neden, engellenen üzerinde odaklanın böylece bekleme görevleri hızlı bir şekilde görebilir. Hata ayıklama oturumu sırasında ilgi değil bir grup da daraltabilirsiniz. Aynı şekilde, diğer sütunlara göre gruplandırabilirsiniz. Bir grubu (BM) olarak yalnızca Grup üstbilgisi yanındaki düğmeye tıklayarak bayrağı. Aşağıdaki çizimde gösterildiği **görevleri** gruplandırılmış modunda penceresi.  
  
 ![Paralel Görevler penceresi gruplandırılmış modunda](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Üst alt Görünüm  
 (Bu görünüm, yalnızca yönetilen kod için kullanılabilir.) Bir sütun başlığına sağ tıklayıp ardından **üst-alt Görünüm**, görevlerin listesi her hangi bir alt görevi olan görüntülenen veya onun üst öğe altında gizli bir alt düğümü, hiyerarşik bir görünümü değiştirebilirsiniz. Aşağıdaki çizimde, üst-alt Görünümü'nde Görevler gösterilmektedir.  
  
 ![Üst&#45;Paralel Görevler penceresi alt görünümünde](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Görevleri işaretleme  
 Görevin çalıştığı görev seçerek görev listesi öğesi ve ardından iş parçacığı işaretleyebilirsiniz **bayrağı** bağlam menüsünden veya ilk sütunda bayrak simgesine tıklayarak. Çeşitli görevler bayrağı, böylece yalnızca bunlara odaklanabilirsiniz dön bayrak eklenmiş olan tüm görevleri getirilecek bayrağı sütununda ardından sıralayabilirsiniz. Ayrıca **Paralel Yığınlar** penceresini görüntülemek için görevleri yalnızca bayrak. Bu, hata ayıklama için ilgilenmediğiniz görevlerini filtreleme yapmanızı sağlıyor. Hata ayıklama oturumları arasında bayrakları kalıcı değildir.  
  
## <a name="freezing-and-thawing-tasks"></a>Dondurma ve görevleri çözme  
 Görevin çalıştığı görev listesi öğesini sağ tıklatın ve ardından iş parçacığını Dondur **atanan iş parçacığını Dondur**. (Bir görev zaten dondurulmuş olup olmadığını komuttur **çözme atanmış iş parçacığı**.) Bir iş parçacığını Dondur, geçerli kesme noktası sonra kodunuz içinde adım adım olduğunda, iş parçacığı yürütülmez. **Dondurma tüm iş parçacıkları, ancak bu** komutu, görev listesi öğesini yürüten dışındaki tüm iş parçacıklarının donuyor.  
  
 Bir menü öğelerini her görev için aşağıda gösterilmiştir.  
  
 ![Paralel Görevler penceresi kısayol iş parçacığı menüde](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı temel bilgileri](../debugger/debugger-basics.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Paralel Programlama](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Eşzamanlılık Çalışma zamanı](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Paralel Yığınlar penceresini kullanma](../debugger/using-the-parallel-stacks-window.md)   
 [İzlenecek Yol: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)



