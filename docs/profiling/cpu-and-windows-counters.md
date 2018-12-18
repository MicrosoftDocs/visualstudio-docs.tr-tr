---
title: CPU ve Windows sayaçları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 585fb2fa8d2662d1a2bec7915bf1f08a4dc771e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865927"
---
# <a name="cpu-and-windows-counters"></a>CPU ve Windows sayaçları

Visual Studio Profiler, işletim sistemi tarafından (Windows sayaçları) oluşturulan performans verilerini ve işlemci birimi (CPU sayaçları) tarafından oluşturulan performans verilerini toplamanıza olanak sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Windows sayaçları

Windows sayaçları performansı işletim sistemi veya uygulamanın, bir hizmet veya sürücü ile ilgili bilgi sağlayan Windows Tanılama Altyapısı bir parçasıdır. Windows sayaçları geçerli bilgisayar yapılandırmasına bağlıdır ve diğer bilgisayarlarda kullanılamayabilir. Windows performans sayaçları, profil oluşturma veri dosyaları görünümleri ve raporları filtrelemek için kullanılabilir işaretleri, profil oluşturma olarak toplanır.

## <a name="cpu-counters"></a>CPU sayaçları

CPU sayaçları, donanım ile ilgili olayların sayısını depolayan bilgisayarın CPU özelliğidir. Yöntemi profil oluşturma Araçları'nı kullanarak CPU sayaç verileri toplama, İşlevler ve modüller için veri veri eklenir. Araçlar yöntemini kullanarak birden çok CPU sayaçları toplayabilirsiniz. Örnekleme yöntemini kullandığınızda, örneklenen için olay olarak kullanılacak bir sayaç seçin.

Performans sayaçları, CPU özgü olur. Farklı modelleri ve bir CPU sürümleri aynı performans sayacını etkinleştirmek için önemli ölçüde farklı yapılandırma ayarları olabilir. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] Profiler taşınabilir olayları, belirli bir işlemci bazı ortak performans sayaçlarını ayırmanıza ve toplamak veya genel performans olaylarını örnek olanak sağlar.

Örneğin, L2 önbellek isabetsizliği, profil oluşturucuyu kullandığınızda belirli bir olay saymak istiyorsanız, bu olay gönderen etrafında bir performans oturumu oluşturabilirsiniz. L2 önbellek ile herhangi bir CPU üzerinde bunu yapabilirsiniz. Performans oturumu platformdan platforma değiştirilmeden taşınabilir.

Visual Studio profil oluşturucu, belirli olaylar için belirli bir platforma desteklemeye devam eder. Örneğin, bir geliştirici Pentium 4 platformunda birlikte NetBurst mimariye özgü olaylar saymak isteyebilirsiniz. Bu olay belirli bir platformda belirli bir performans oturumu için taşınabilir, ancak geliştirici için hala kullanılabilir değil.

## <a name="portable-and-platform-events"></a>Taşınabilir ve platform olaylarını

Taşınabilir olayları, özel bir işlemciye özgü olmayan CPU sayaçları grubudur. Diğer tüm CPU sayaçları platform olayı olarak adlandırılır ve çeşitli platformlarda desteklenmiyor olabilir.

 Hem taşınabilir ve platform olaylarını sayaçları tanımlanır. *xml* dosyaları burada sayaçlarıyla ilgili belirli değerler sağlanır. Intel ve AMD işlemciler, verileri gibi farklı olduğundan farklı CPU'lar, birden çok dosya vardır. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Profiler taşınabilir hem platform uygun sayaçları için performans ölçümlerini kullanıcıya sunmak için bu bilgileri kullanır.

### <a name="portable-events"></a>Taşınabilir olayları

Taşınabilir olayları aşağıdaki olaylar içerir:

**Genel olaylar**

|Olay adı|Olay açıklaması|
|----------------|-----------------------|
|Yönergeleri Çekildi|Olay tamamlanana kadar yürütülen yönergeleri sayısını gösterir.|
|Durdurulmayan döngüler|Hangi işlemci, örneğin, g/ç için bekleyen durdurulmaz döngüleri belirtir.|

**Ön uç etkinlikleri**

|Olay adı|Olay açıklaması|
|----------------|-----------------------|
|ITLB isabetsiz|İçinde bir isabetsizliği sonuçlanan yönerge çeviri görünüm edilgen arabellek aramaları sayısını gösterir.|

**Dal etkinlikleri**

|Olay adı|Olay açıklaması|
|----------------|-----------------------|
|Dallar Çekildi|Olay tamamlanana kadar yürütülen dal yönergeleri sayısını gösterir.|
|Yanlış tahmin edilen dallar|Yanlış bir yol işlemci tahmin nedeniyle oluşabilecek yanlış tahmin edilen dallar gösterir. İşlemci tüm çalışmanın iptal ve doğru yola yeniden başlatmak için yanlış tahmin edilen dallar performansını etkiler.|

**Bellek olayları:**

|Olay adı|Olay açıklaması|
|----------------|-----------------------|
|L2 Önbellek Okuma isabetsiz|İkinci düzey önbellek sayısını okuma isabetsiz gösterir.|
|L2 Önbellek Okuma referansları|İkinci düzey önbellek sayısını başvuruları okuma gösterir. Bu yükleme isabetsiz içerir ve sahiplik (RFO) isabetsiz ve isabet sayısı için okuyun.|

## <a name="view-available-counters"></a>Kullanılabilir sayaçları görüntüleyin

Bir komut istemi penceresinde üzerinde Visual Studio IDE'de kullanılabilir CPU sayaçları listeleyebilirsiniz.

### <a name="visual-studio-ui"></a>Visual Studio UI

Visual Studio IDE'de bir bilgisayarda kullanılabilir sayaçları listelemek için performans Gezgini profil oluşturucu performans oturumu olması gerekir.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen tüm CPU sayaçları listesini bir listesini görüntülemek için

1. Performans Gezgini performans oturumu sağ tıklayın ve ardından **özellikleri**.

2. Aşağıdakilerden birini yapın:

   - Tıklayın **örnekleme**ve ardından **performans sayacı** gelen **örnek** olay listesi. CPU sayaçları listelenen **ulaşılabilir performans sayaçları**.

      **Not** tıklayın **iptal** önceki örnekleme yapılandırmaya dönmek için.

     veya

   - Seçin **CPU sayaçları**ve ardından **CPU sayaçlarını Topla**. CPU sayaçları listelenen **kullanılabilir sayaçları**.

      **Not** tıklayın **iptal** önceki sayaç koleksiyonu yapılandırmaya dönmek için.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen penceresi sayaçları listesini bir listesini görüntülemek için

1. Performans Gezgini performans oturumu sağ tıklayın ve ardından **özellikleri**.

2. Tıklayın **Windows sayaçları**.

3. Seçin **Windows sayaçları toplamak**.

4. Gelen **sayaç kategorisi** listesinde, bir sayaç grubunu seçin. Liste kutusunda grup için Windows sayaç görüntülenir.

     **Not:** tıklayın **iptal** önceki sayaç koleksiyonu yapılandırmaya dönmek için.

### <a name="command-line"></a>Komut satırı

Kullanarak [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracını komut satırından bir bilgisayarda kullanılabilir CPU sayaçları yeniden sıralayabilir.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen CPU sayaçları bir listesi için

1. Bir komut istemi penceresi açın.

2. Tür

     **\<Visual Studio performans araçları dizinine > \VSPerfCmd/querycounters**

     Burada  *\<Visual Studio performans araçları dizinine >* Visual Studio yüklemenizin performans araçları dizinini genellikle yoludur

     *C:\Program Files\Microsoft Visual Studio 10.0\Team Araçlar\Performans araçları*

## <a name="see-also"></a>Ayrıca bkz.

[Genel Bakışlar](../profiling/overviews-performance-tools.md)  
[Nasıl yapılır: Örnekleme olayları seçme](../profiling/how-to-choose-sampling-events.md)  
[Nasıl yapılır: CPU sayaç verileri toplama](../profiling/how-to-collect-cpu-counter-data.md)  
[Nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)