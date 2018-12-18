---
title: Çok iş parçacıklı uygulamalarda hata ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/06/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ea1af90ae775ed24f5cceabeca04cdc901f545f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059684"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Visual Studio'da çok iş parçacıklı uygulamalarda hata ayıklama
Bir iş parçacığı, işletim sisteminin işlemci zamanı veren yönergeler sırasıdır. İşletim sisteminde çalışan her işlem en az bir iş parçacığından oluşur. Birden fazla iş parçacığı bulunan işlemler birden çok iş parçacıklı çağrılır.  
  
Bilgisayarlar birden çok işlemci, çok çekirdekli işlemcisi veya hiper iş parçacıklı işlemler birden fazla eşzamanlı iş parçacığı çalıştırabilir. Birçok iş parçacığı kullanarak Paralel işleme büyük ölçüde program performansı artırabilir, ancak birçok iş parçacığı takip ettiğiniz çünkü bunu de hata ayıklamayı zorlaştırır.  
  
Çoklu iş parçacığı kullanımı, yeni türde olası hatalar ortaya çıkarabilir. Örneğin, iki veya daha fazla iş parçacığı aynı kaynağa erişmek gerekebilir, ancak aynı anda yalnızca tek bir iş parçacığı güvenle kaynağa erişmek için. Çeşit karşılıklı dışlama, yalnızca bir iş parçacığı herhangi bir zamanda kaynak eriştiğinden emin olmak gereklidir. Karşılıklı dışlama yanlış uygulanırsa oluşturabilirsiniz bir *kilitlenme* hiçbir iş parçacığı çalıştırılacağı burada koşul. Kilitlenmeler, hata ayıklamak için sabit bir sorun çoğunlukla olur.

## <a name="tools-for-debugging-multithreaded-apps"></a>Hata ayıklama çok iş parçacıklı uygulamalar için Araçlar

Visual Studio hata ayıklama çok iş parçacıklı uygulamalar için farklı araçlar sağlar.

- İş parçacığı için iş parçacıklarında hata ayıklama için kullanılan birincil Araçlar olan **iş parçacıkları** penceresinde, kaynak pencerelerdeki iş parçacığı işaretçileri **Paralel Yığınlar** penceresinde **paralel izleme** penceresinde ve **hata ayıklama konumu** araç çubuğu. Hakkında bilgi edinmek için **iş parçacıkları** penceresi ve **hata ayıklama konumu** araç bkz [izlenecek yol: iş parçacıkları penceresini kullanarak hata ayıklama](../debugger/how-to-use-the-threads-window.md). Nasıl kullanılacağını öğrenmek için **Paralel Yığınlar** ve **paralel izleme** windows bkz [birden çok iş parçacıklı bir uygulamanın hatalarını ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md). Her iki konuları, iş parçacığı işaretçileri kullanmayı göstermektedir.
  
- Kullanan kod için [görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) veya [eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime/), hata ayıklama için kullanılan birincil Araçlar **Paralel Yığınlar** penceresinde, **Paralel izleme** penceresinde ve **görevleri** JavaScript destekleyen penceresi. Başlamak için bkz: [izlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md) ve [izlenecek yol: C++ AMP uygulamasında hata ayıklama](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- GPU iş parçacıklarında hata ayıklama için birincil araçtır **GPU iş parçacıkları** penceresi. Bkz: [nasıl yapılır: GPU iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-gpu-threads-window.md).  

- İşlemler için birincil araçlardır **iliştirme** iletişim kutusu, **işlemleri** penceresinde ve **hata ayıklama konumu** araç çubuğu.  
  
Visual Studio ayrıca güçlü kesme noktaları ve izleme noktaları, çok iş parçacıklı uygulamaların hatalarını ayıklarken yararlı olabilen sağlar. Tek tek iş parçacıkları üzerinde kesme noktaları yerleştirmek için kesme noktası koşulları ve filtreleri kullanın. İzleme noktaları kilitlenmeler gibi sorunları incelemek için bozmadan programınızın yürütülmesini izlemek için etkinleştirin. Daha fazla bilgi için [kesme noktası eylemleri ve izleme noktaları](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Bir kullanıcı arabirimine sahip birden çok iş parçacıklı bir uygulamada hata ayıklama özellikle zor olabilir. Uygulamanın ikinci bir bilgisayar üzerinde çalışan ve uzaktan hata ayıklama kullanmayı düşünebilirsiniz. Daha fazla bilgi için [uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
## <a name="articles-about-debugging-multithreaded-apps"></a>Hata ayıklama çok iş parçacıklı uygulamalar hakkında makaleler

 [Çok iş parçacıklı bir uygulamanın hatalarını ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md)   
 Hata ayıklama özellikleri vurgulayan özellikleri, iş parçacığı Turu **Paralel Yığınlar** penceresi ve **paralel izleme** penceresi.

 [İş parçacıklarında ve işlemlerde hata ayıklama araçları](../debugger/debug-threads-and-processes.md)  
 İş parçacıklarında ve işlemlerde hata ayıklama araçları'nın özellikleri listeler.  
  
 [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)  
 Birden çok işlemde hata ayıklama açıklanmaktadır.

 [İzlenecek yol: iş parçacıkları penceresini kullanarak hata ayıklama](../debugger/how-to-use-the-threads-window.md).  
 Nasıl kullanılacağını gösteren izlenecek yol **iş parçacıkları** penceresi ve **hata ayıklama konumu** araç çubuğu. 

 [İzlenecek yol: Paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Nasıl kullanılacağını gösteren izlenecek yol **Paralel Yığınlar** ve **görevleri** windows.  
  
 [Nasıl yapılır: Hata ayıklarken başka bir iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Hata ayıklama içeriğini başka bir iş parçacığına geçiş yapmak için birçok yol sağlar.  
  
 [Nasıl yapılır: İş parçacıklarını bayrakla işaretleme ve işareti geri alma](../debugger/how-to-flag-and-unflag-threads.md)  
 Hata ayıklarken özel dikkat vermek istediğiniz işaretleyin veya bayrak iş parçacıkları.    
  
 [Nasıl yapılır: yüksek performanslı kümede hata ayıklama](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Yüksek performanslı küme üzerinde çalışan bir uygulamada hata ayıklama teknikleri.  

 [Yerel kod iş parçacıklarında hata ayıklama ipuçları](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Yerel iş parçacığı hata ayıklama için yararlı olabilicek basit yöntemler. 

 [Nasıl yapılır: Yerel kodda iş parçacığı adı ayarlama](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 İş parçacığınıza görüntülediğiniz bir ad verin **iş parçacıkları** penceresi.  
  
 [Nasıl yapılır: Yönetilen kodda iş parçacığı adı ayarlama](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 İş parçacığınıza görüntülediğiniz bir ad verin **iş parçacıkları** penceresi. 
  
## <a name="see-also"></a>Ayrıca bkz.  

[Kesme noktalarınıullanma](../debugger/using-breakpoints.md)  
[İş parçacığı oluşturma](/dotnet/standard/threading/index)  
[Bileşenlerinde çoklu iş parçacığı kullanımı](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[Eski kod (Visual C++) için çoklu iş parçacığı desteği](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [İş parçacıklarında ve işlemlerde hata ayıklama](../debugger/debug-threads-and-processes.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)