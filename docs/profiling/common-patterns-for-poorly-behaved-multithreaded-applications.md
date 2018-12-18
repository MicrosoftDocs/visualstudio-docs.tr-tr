---
title: Hatalı davranan çok iş parçacıklı uygulamalar için ortak desenler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9929fc5acfe58d51de9142abc7addd539cf2b74e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34549012"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Hatalı davranan çok iş parçacıklı uygulamalar için ortak desenler

Eşzamanlılık görselleştiricisi çok iş parçacıklı uygulamada davranışını görselleştirmek için geliştiricilere yardımcı olur. Bu araç, hatalı davranan çok iş parçacıklı uygulamalar için ortak desenler Galerisi içerir. Galeri araçla bunu çözmek için büyük olasılıkla sonucunu bu davranışı ve en yaygın yaklaşımı her düzeni tarafından temsil edilen davranışının bir açıklaması ile birlikte sunulan tipik ve tanınabilir visual düzenleri içerir.

## <a name="lock-contention-and-serialized-execution"></a>Kilit çakışması ve serileştirilmiş yürütme

![Kilit çakışması serileştirilmiş yürütme kaynaklanan](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Bazen parallelized uygulama stubbornly seri olarak birkaç iş parçacığı vardır ve bilgisayarın mantıksal çekirdekler yeterli sayıda olsa bile yürütmeye devam eder. İlk belirti birden çok iş parçacıklı performansın, hatta belki de seri uygulaması biraz yavaş olmasıdır. İş Parçacıkları görünümü'nde, paralel olarak çalışan birden çok iş parçacığı görmezsiniz; Bunun yerine, yalnızca bir iş parçacığı herhangi bir anda yürütülmekte olduğu bakın. Bu noktada, bir iş parçacığı eşitleme kesimdeki tıklarsanız, engellenmiş iş parçacığı (engelleme çağrı yığını) ve engelleme koşulu (çağrı yığın engellemesini kaldırma) kaldırılmış iş parçacığı için çağrı yığını görebilirsiniz. Ayrıca, arama yığın engellemesini kaldırma, çözümlemesi işleminde ortaya çıkarsa, bir iş parçacığı için hazır bağlayıcı görüntülenir. Bu noktadan serileştirme daha da fazla nedenini araştırmak için engelleme ve engellemesini kaldırma çağrısı yığınlar koda gidebilirsiniz.

Aşağıdaki çizimde gösterildiği gibi eşzamanlılık görselleştiricisi de bu belirti nerede, birden çok iş parçacığı varlığını rağmen uygulamayı yalnızca bir mantıksal çekirdek tüketir CPU Kullanımı görünümü içinde getirebilir.

Daha fazla bilgi için "performans düzeni 1: tanımlayıcı kilit çakışması" Hazim Shafi'nın içinde [Windows için performans araçları paralel](http://go.microsoft.com/fwlink/?LinkID=160569) blog MSDN blog Web sitesinde.

![Kilit çakışması](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Düzensiz iş yükü dağıtım

![Düzensiz iş yükü](../profiling/media/unevenworkload_1.png "UnevenWorkLoad_1")

Bir uygulama birden fazla paralel iş parçacıkları arasında düzensiz bir dağıtım iş ortaya çıktığında, her iş parçacığının kendi iş tamamlandıktan gibi tipik Merdiven adım düzeni önceki örnekte gösterildiği gibi görünür. Eşzamanlılık görselleştiricisi çoğunlukla her eş zamanlı iş parçacığı için çok yakın başlangıç zamanlarını gösterir. Ancak, bu iş parçacıkları, aynı anda bitiş yerine bir düzensiz şekilde genellikle sonlandırın. Bu desen çalışma grubu performansın için yol açabilecek paralel iş parçacıkları arasında düzensiz bir dağıtımı gösterir. En iyi bir sorun için kullandığı iş paralel iş parçacıkları arasında bölünmüş algoritması yeniden değerlendirmeye yaklaşımdır.

Aşağıdaki çizimde gösterildiği gibi eşzamanlılık görselleştiricisi de bu belirti CPU Kullanımı görünümü içinde aşamalı step-down CPU kullanımında olarak hale getirebilir.

![Düzensiz iş yükü](../profiling/media/unevenworkload_2.png "UnevenWorkload_2")

## <a name="oversubscription"></a>Aşırı abonelik

![Aşırı abonelik](../profiling/media/oversubscription.png "aşırı abonelik")

Aşırı abonelik söz konusu olduğunda, bir işlemdeki etkin iş parçacığı sayısı sistem üzerindeki kullanılabilir mantıksal çekirdekler sayısından büyüktür. Önceki çizimde, tüm etkin iş parçacığı önemli önalım gösterilmeyen aşırı abonelik, sonuçlarını gösterir. Ayrıca, gösterge Önalım (Bu örnekte 84 yüzde) olarak harcanan zaman büyük bir yüzdesini gösterir. Bu işlem mantıksal çekirdekler sayısından daha fazla eşzamanlı iş parçacığının sistem isteyen olduğunu gösteriyor olabilir. Ancak, bu sistemdeki diğer işlemler bu işlem için kullanılabilir olmasını kabul edildiği kaynakları kullanıyorsanız da gösterebilir.

Bu sorunu değerlendirirken aşağıdakileri dikkate alın:

- Genel sistem talep. Sistemdeki diğer işlemler, iş parçacıkları preempting olduğunu göz önünde bulundurun. İş Parçacıkları görünümü önalım kesimdeki üzerinden duraklattığınızda, araç ipucu iş parçacığı ve iş parçacığı etkisiz işlem tanımlayın. Bu işlem mutlaka işleminizi boşaltıldı tüm süre boyunca yürütülen bir değildir, ancak ne işleminizi karşı önalım baskısı oluşturulan hakkında bir ipucu sağlar.

- İşleminizi iş parçacıkları yürütme sırasında bu iş aşaması için uygun sayıda nasıl belirlediğini değerlendirin. İşleminizi doğrudan etkin paralel iş parçacığı sayısını hesaplar, bu algoritma sistem üzerindeki kullanılabilir mantıksal çekirdek sayısı için daha iyi hesabına değiştirmeyi düşünebilirsiniz. Eşzamanlılık Çalışma zamanı, görev paralel kitaplığı veya PLINQ kullanıyorsanız, bu kitaplıklar iş parçacığı sayısını hesaplama iş gerçekleştirin.

## <a name="inefficient-io"></a>Verimsiz g/ç

![Verimsiz ı&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

Aşırı kullanımı ya da g/ç kötüye kullanılması verimsiz uygulamalarında yaygın bir nedenidir. Önceki çizimde göz önünde bulundurun. Görünür zaman çizelgesi profili görünür iş parçacığı zaman 44 yüzdesi g/ç tarafından tüketilmesi gösterir. Zaman Çizelgesi profili uygulama sık sık g/ç tarafından engellendiğini gösterir g/ç, büyük miktarlarda gösterir. G/ç ve burada programınızı engellendi türleri hakkındaki ayrıntıları görmek için sorunlu bölgelere yakınlaştırma, görünür zaman çizelgesi profili inceleyin ve geçerli çağrı yığınları görmek için belirli bir g/ç blok'ye tıklayın.

## <a name="lock-convoys"></a>Kilit Konvoyları

![Kilitleme Konvoyları](../profiling/media/lock_convoys.png "Lock_Convoys")

Kilit Konvoyları uygulama, ilk hizmet önce gelen bir order kilitler elde ettiğinde ve kilidi varış hızında edinme hızından daha yüksek olduğunda oluşur. Bu iki koşulun birleşimi yedekleme başlatmak Lock istekleri neden olur. Bu sorunu mücadele etmek için bir yolu "haksız" kilitleri ya da kilidi Devletleri'nde bulmak için ilk iş parçacığı erişmenizi kilitleri kullanmaktır. Önceki çizimde, bu convoy davranış gösterir. Sorunu çözmek için eşitleme nesneleri için Çekişme azaltmayı deneyin ve haksız kilitleri kullanmayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.

[İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)