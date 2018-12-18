---
title: Using the Tasks Window | Microsoft Docs
ms.custom: ''
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d22202e50c973c52bf2b47374b9eda583fb3fe8
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280889"
---
# <a name="using-the-tasks-window"></a>Görevleri Penceresini Kullanma

**Görevleri** pencere benzeyen **iş parçacıkları** BT'nin hakkında bilgileri gösterir ancak pencere <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class), veya [WinJS.Promise ](/previous-versions/windows/apps/br211867(v=win.10)) yerine her bir iş parçacığı nesneleri. İş parçacığı gibi görevleri aynı anda çalışabilecek zaman uyumsuz işlemleri temsil eder; Ancak, birden çok görev aynı iş parçacığı üzerinde çalışabilir.

Yönetilen kodda kullanabileceğiniz **görevleri** ile çalışırken penceresi <xref:System.Threading.Tasks.Task?displayProperty=fullName> nesneleri veya **await** ve **zaman uyumsuz** anahtar sözcükleri (**Await** ve **zaman uyumsuz** VisualBasic içinde). Yönetilen kodda görevleri hakkında daha fazla bilgi için bkz. [paralel programlama](/dotnet/standard/parallel-programming/index).

Yerel kod halinde kullanabileceğiniz **görevleri** ile çalışırken penceresi [görev grupları](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [paralel algoritmalar](/cpp/parallel/concrt/parallel-algorithms), [zaman uyumsuz aracılar](/cpp/parallel/concrt/asynchronous-agents), ve [Basit görevler](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Yerel kodda görevleri hakkında daha fazla bilgi için bkz. [eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime).

JavaScript'te, promise ile çalışırken görevleri penceresini kullanabilirsiniz `.then` kod. Bkz: [JavaScript (UWP uygulamaları) zaman uyumsuz programlamada](/previous-versions/windows/apps/hh700330(v=win.10)) daha fazla bilgi için.

Kullanabileceğiniz **görevleri** hata ayıklayıcıya girdikten zaman penceresi. Şirket erişim **hata ayıklama** tıklayarak menü **Windows** tıklayıp **görevleri**. Aşağıdaki çizimde gösterildiği **görevleri** kendi varsayılan modunda penceresi.

![Görevler penceresi](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> Yönetilen kodda bir <xref:System.Threading.Tasks.Task> durumu olan [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>), veya [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) olmayabilir Görüntülenen **görevleri** yönetilen iş parçacıklarını uyku ya da birleştirme durumda olduğunda penceresi.

## <a name="tasks-column-information"></a>Görevleri sütun bilgileri

Sütunları **görevleri** penceresi, aşağıdaki bilgileri gösterir.

|Sütun adı|Açıklama|
|-----------------|-----------------|
|**bayrakları**|Hangi görevlerin işaretlenmiş gösterir ve bir görevi işaretleme veya işaretini kaldırma olanak tanır.|
|**Simgeler**|Sarı bir ok, geçerli görev gösterir. Geçerli görev, geçerli iş parçacığı üzerinde en üstteki görevdir.<br /><br /> Bölme görevi, diğer bir deyişle, hata ayıklayıcı çağrıldığında geçerli bir beyaz bir ok gösterir.<br /><br /> Duraklatma simgesi, kullanıcı tarafından dondurulmuş bir görevi gösterir. Dondurma ve bir görev listesinde sağ tıklayarak Çöz.|
|**ID**|Görev için sistem tarafından sağlanan bir sayı. Yerel kod halinde, bu görev adresidir.|
|**Status**|Geçerli durumu (zamanlanmış, etkin, engellenmiş, kilitlenen, bekleniyor veya tamamlanmış) görev. Zamanlanmış bir görev henüz çalıştırılmadı ve bu nedenle, henüz bir çağrı yığını, atanan bir iş parçacığı veya ilgili bilgiler yok biridir.<br /><br /> Etkin görev kodu hata ayıklayıcıda kesmeden önce yürütülen biridir.<br /><br /> Bir bekleniyor veya engellenen sinyal bir olay, bir kilidi serbest bırakılması veya başka bir görevi tamamlamak için beklediği, engellenen bir görevdir.<br /><br /> Kilitlenen bir görevi başka bir iş parçacığıyla, iş parçacığı kilitlendiğini bekleyen bir görevdir.<br /><br /> Üzerine **durumu** hücre bloğu hakkında daha fazla bilgi kilitlenen veya bekleniyor bir görev için. **Uyarı:** **görevleri** penceresi bekleyin zinciri geçişi (WCT) tarafından desteklenen eşitleme temel kullanan bir engellenen görev için kilitlenme bildirir. Örneğin, bir kilitlenen <xref:System.Threading.Tasks.Task> WCT, hata ayıklayıcı raporları kullanan nesne **Awaiting kilitlendiğini**. Eşzamanlılık WCT kullanmaz, çalışma zamanı tarafından yönetilen kilitlenen bir görev için hata ayıklayıcı raporları **bekleyen**. WCT hakkında daha fazla bilgi için bkz: [bekleyin zinciri geçişi](/windows/desktop/Debug/wait-chain-traversal).|
|**Başlangıç saati**|Saat, görev etkin hale geldi.|
|**Süresi**|Görev etkin biçimde saniye sayısı.|
|**Tamamlanma Zamanı**|Hangi görev tamamlanma zamanı.|
|**Konum**|Görevin çağrı yığınındaki geçerli konum. Görev için bütün çağrı yığını görmek için bu hücreyi üzerine gelin. Zamanlanmış Görevler, bu sütunda bir değer yoktur.|
|**Görev**|İlk yöntem ve oluşturulduğunda bu göreve geçirilen bağımsız değişkenler.|
|**AsyncState**|Yönetilen kod için görev durumu. Bu sütun varsayılan olarak gizlidir. Bu sütunu görüntülemek için bir sütun başlıkları için bağlam menüsünü açın. Seçin **sütunları**, **AsyncState**.|
|**Üst**|Bu görevi oluşturan görevin kimliği. Boş ise, hiçbir üst görev vardır. Bu yalnızca yönetilen programlar için geçerlidir.|
|**İş parçacığı atama**|Görevin üzerinde çalıştığı iş parçacığının adı ve kimliği.|
|**AppDomain**|Yönetilen kod için görevin yürütüldüğü uygulama etki alanı.|
|**task_group**|Yerel kod, adresini [task_group](/cpp/parallel/concrt/reference/task-group-class) zamanlanmış görev nesnesi. Zaman uyumsuz aracılar ve Basit görevler için bu sütun 0 olarak ayarlanır.|
|**İşlem**|Görevin üzerinde çalıştığı işlem kimliği.|

 Bir sütunun başlığına sağ tıklayıp sonra istediğiniz sütunları seçerek görünüme sütun ekleyebilirsiniz. (Seçim işaretini kaldırarak sütunları kaldırın.) Sütun sağa veya sola sürükleyerek de yeniden sıralayabilirsiniz. Sütun kısayol menüsünü aşağıdaki çizimde gösterilmektedir.

 ![Görevler penceresi kısayol Görünüm menüsünde](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Sıralama görevleri
 Görevleri sütun ölçütlerine göre sıralamak için sütun başlığına tıklayın. Tıklayarak gibi **kimliği** sütun üst bilgisine görevleri görev Kimliğine göre sıralayabilirsiniz: 1,2,3,4,5 ve benzeri. Sıralama düzenini tersine çevirmek için sütun başlığını tekrar tıklatın. Geçerli sıralama sütunu ve sıralama düzenini sütununda bir ok ile belirtilir.

## <a name="grouping-tasks"></a>Görevleri gruplandırma
 Görevleri liste görünümünde herhangi bir sütuna göre gruplandırabilirsiniz. Örneğin, sağ tıklanarak **durumu** sütun başlığını ve ardından **gruplandırma ölçütü** > **[*durumu*]**, şunları yapabilirsiniz aynı durumunda olan tüm görevleri grup. Örneğin, neden, engellenen üzerinde odaklanın böylece görevi bekliyor hızlıca görebilirsiniz. Hata ayıklama oturumu sırasında ilgi değil bir grup da daraltabilirsiniz. Aynı şekilde, diğer sütunlara göre gruplandırabilirsiniz. Bir grubu (BM) olarak yalnızca Grup üstbilgisi yanındaki düğmeye tıklayarak bayrağı. Aşağıdaki çizimde gösterildiği **görevleri** gruplandırılmış modunda penceresi.

 ![Görevler penceresi gruplandırılmış modunda](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Üst alt Görünüm
 (Bu görünüm, yalnızca yönetilen kod için kullanılabilir.) Sağ tıklanarak **durumu** sütun başlığını ve ardından **gruplandırma ölçütü** > **üst**, görevlerin listesi, hiyerarşik bir görünümü değiştirebilirsiniz Her alt görev, görüntülenen veya onun üst öğe altında gizli bir alt düğümü olmalıdır.

## <a name="flagging-tasks"></a>Görevleri işaretleme
 Görevin çalıştığı görev seçerek görev listesi öğesi ve ardından iş parçacığı işaretleyebilirsiniz **atanan iş parçacığını işaretle** bağlam menüsünden veya ilk sütunda bayrak simgesine tıklayarak. Çeşitli görevler bayrağı, böylece yalnızca bunlara odaklanabilirsiniz dön bayrak eklenmiş olan tüm görevleri getirilecek bayrağı sütununda ardından sıralayabilirsiniz. Ayrıca **Paralel Yığınlar** penceresini görüntülemek için görevleri yalnızca bayrak. Bu, hata ayıklama için ilgilenmediğiniz görevlerini filtreleme yapmanızı sağlıyor. Hata ayıklama oturumları arasında bayrakları kalıcı değildir.

## <a name="freezing-and-thawing-tasks"></a>Dondurma ve görevleri çözme
 Görevin çalıştığı görev listesi öğesini sağ tıklatın ve ardından iş parçacığını Dondur **atanan iş parçacığını Dondur**. (Bir görev zaten dondurulmuş olup olmadığını komuttur **çözme atanmış iş parçacığı**.) Bir iş parçacığını Dondur, geçerli kesme noktası sonra kodunuz içinde adım adım olduğunda, iş parçacığı yürütülmez. **Dondurma tüm iş parçacıkları, ancak bu bir** komutu, görev listesi öğesini yürüten dışındaki tüm iş parçacıklarının donuyor.

 Bir menü öğelerini her görev için aşağıda gösterilmiştir.

 ![Görevler penceresi kısayol iş parçacığı menüde](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Etkin Görev veya çerçeve değiştirme

**Göreve geçiş** komut etkin görev geçerli görev yapar. **Çerçeveye geçiş yap** komut etkin yığın çerçevesini çerçeve seçili yığın yapar. Hata ayıklayıcı bağlamı geçerli görev ya da seçili yığın çerçevesini geçer.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı Temel Bilgileri](../debugger/getting-started-with-the-debugger.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Paralel Programlama](/dotnet/standard/parallel-programming/index)
- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)
- [Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)
- [İzlenecek Yol: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)