---
title: İş parçacığı hata ayıklayıcıda görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 764eb46fb387e1a007362b02a0f62cf478c771fe
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066229"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window"></a>İş parçacıkları penceresini kullanarak Visual Studio hata ayıklayıcı iş parçacıkları görünümü
İçinde **iş parçacıkları** penceresini inceleyin ve ayıkladığınız uygulama iş parçacıkları ile çalışır. Nasıl kullanılacağını adım adım yönergeler için **iş parçacıkları** penceresinde görmek [izlenecek yol: iş parçacıkları penceresini kullanarak hata ayıklama](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>İş Parçacıkları penceresini kullanma 
 **İş parçacıkları** penceresi içeren bir tablo, her satır ayrı bir iş parçacığı, uygulamanızda nerede açıklar. Varsayılan olarak, uygulamanızı tüm iş parçacıklarının tabloda listelenir, ancak yalnızca sizi ilgilendiren iş parçacıklarını gösterilecek listeyi filtreleyebilirsiniz. Her sütun, farklı türden bilgileri açıklar. Ayrıca, bazı sütunları gizleyebilirsiniz. Tüm sütunları görüntülemek, aşağıdaki sütunlar, soldan sağa doğru görünür:  
  
- **Bayrağı**: etiketlenmemiş bu sütunda adlandırdığınızdan istediğiniz bir iş parçacığı işaretleyebilirsiniz. Bir iş parçacığı bayrak hakkında daha fazla bilgi için bkz: [nasıl yapılır: bayrağı iş parçacıklarını bayrakla işaretleme ve](../debugger/how-to-flag-and-unflag-threads.md).  
  
- **Geçerli iş parçacığı**: etiketlenmemiş bu sütunda bir sarı ok geçerli iş parçacığı gösterir. Ok anahat geçerli olmayan bir iş parçacığı için geçerli hata ayıklayıcı bağlamını gösterir.
  
- **Kimliği**: her iş parçacığı kimlik numarasını görüntüler.  
  
- **Kimliği yönetilen**: yönetilen kimlik numaraları için yönetilen iş parçacıklarını görüntüler.  
  
- **Kategori**: kullanıcı arabirimi iş parçacıkları, uzak yordam çağrı işleyicisi veya çalışan iş parçacığı iş parçacığı kategorisini görüntüler. Uygulamanın ana iş parçacığı bir özel kategori tanımlar.  
  
- **Adı**: her iş parçacığı varsa veya olarak ada göre tanımlayan \<No Name >.  
  
- **Konum**: iş parçacığı nerede çalıştığını gösterir. Bu konum iş parçacığı için tam çağrı yığınını Göster genişletebilirsiniz.  
  
- **Öncelik**: öncelik ya da sistem her iş parçacığı için atanan öncelik görüntüler (varsayılan olarak gizlidir) bir Gelişmiş sütunu.  
  
- **Benzeşim maskesi**: her iş parçacığı için İşlemci benzeşim maskesi gösterir (varsayılan olarak gizlidir) bir Gelişmiş sütunu. Çok işlemcili bir sistemde, bir iş parçacığı üzerinde çalışabileceği hangi İşlemci benzeşim maskesi belirler.  
  
- **Sayısı askıya**: askıya alınma sayısını görüntüler (varsayılan olarak gizlidir) bir Gelişmiş sütunu. Bu sayaç, bir iş parçacığı çalıştırılıp çalıştırılamayacağını belirler. Askıya alınmış sayıları hakkında daha fazla bilgi için bkz: [dondurma ve iş parçacıklarını çözme](#freeze-and-thaw-threads).  
  
- **İşlem adı**: her iş parçacığı ait olduğu için işlem gösterir (varsayılan olarak gizlidir) bir Gelişmiş sütunu. Bu sütundaki veriler, birçok işlemi hata ayıklama işlemi yaparken yararlı olabilir.  

- **İşlem Kimliği**: işlem gösterir (varsayılan olarak gizlidir) bir Gelişmiş sütun kimliği her iş parçacığı ait olduğu. 

- **Aktarım niteleyicisi**: hata ayıklayıcı bağlı makineyi benzersiz olarak tanımlayan (varsayılan olarak gizlidir) bir Gelişmiş sütunu. 
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>İş parçacıkları penceresini kesme modunda veya çalıştırma modunda görüntülemek için  
  
-   Visual Studio hata ayıklama modunda olsa da, seçin **hata ayıklama** menüsünde **Windows**ve ardından **iş parçacıkları**.  
  
### <a name="to-display-or-hide-a-column"></a>Bir sütunu sakla ya da görüntülemek için  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde **sütunları**. Daha sonra seçin veya göstermek veya gizlemek istediğiniz sütunun adını temizleyin.  

## <a name="display-flagged-threads"></a>Bayraklı iş parçacıklarını görüntüleme  
 Bir simge ile işaretleyerek özel dikkat vermek istediğiniz bir iş parçacığı işaretleyebilirsiniz **iş parçacıkları** penceresi. Daha fazla bilgi için [nasıl yapılır: iş parçacıklarını bayrakla işaretleme ve bayrak](../debugger/how-to-flag-and-unflag-threads.md). İçinde **iş parçacıkları** penceresinde tercih edebilirsiniz tüm iş parçacıkları veya yalnızca bayraklı iş parçacıklarını görüntüler.  
  
### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını görüntülemek için  
  
-   Seçin **sadece iş parçacığı bayrak eklenmiş Göster** en üstündeki araç çubuğunda **iş parçacıkları** penceresi. (Bunu soluksa, bazı iş parçacıkları ilk bayrak gerekir.) 

## <a name="freeze-and-thaw-threads"></a>Dondurma ve iş parçacıklarını çözme  
 Bir iş parçacığını Dondur, sistem kaynakları kullanılabilir olsa bile, iş parçacığının yürütülmesini başlatılamıyor.  
  
 Yerel kodda askıya alma veya Windows işlevleri çağırarak iş parçacıklarını sürdürme `SuspendThread` ve `ResumeThread`. Ya da MFC işlevlerini [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) ve [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Çağırırsanız `SuspendThread` veya `ResumeThread`, *askıya sayısı* gösterilen **iş parçacıkları** penceresi değiştirilebilir. Dondurma veya çözme yerel bir iş parçacığı askıda sayma değiştirmez. Çözülmüş ve askıya alınmış sayısı sıfır sahip sürece bir iş parçacığı yerel kodda yürütülemiyor.  
  
 Yönetilen kodda dondurma veya çözme iş parçacığı askıda sayma değiştirir. Yönetilen kodda bir iş parçacığını Dondur ise, askıya alınmış sayısı 1'dir. Yerel kodda bir iş parçacığını Dondur, kullandığınız sürece, askıya alınmış sayısı 0 ' dır `SuspendThread` çağırın.  
  
> [!NOTE]
>  Yönetilen koda yerel koddan bir çağrı hata ayıklaması yaparken, yönetilen kod aynı fiziksel iş parçacığında adlı yerel kod olarak çalışır. Yönetilen kod da askıya alma ya da yerel iş parçacığını dondurma donuyor.  
  
### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Dondurma veya çözme iş parçacığı yürütme için  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde **iş parçacıklarını dondurma** veya **çözme iş parçacığı**.  
  
     Bu eylem, seçili iş parçacıklarını etkiler **iş parçacıkları** penceresi. 

### <a name="switch-to-another-thread"></a>Başka bir iş parçacığına geçiş 

Sarı bir ok, geçerli iş parçacığı (ve yürütme işaretçisi konumunu) gösterir. Kıvrık kuyruklu yeşil bir ok, geçerli hata ayıklayıcı bağlamı geçerli olmayan bir iş parçacığı olduğunu gösterir.

#### <a name="to-switch-to-another-thread"></a>Başka bir iş parçacığına geçiş yapmak için  
  
-   Aşağıdaki adımlardan birini izleyin:  
  
    -   Herhangi bir iş parçacığı çift tıklayın.  
  
    -   Bir iş parçacığı sağ tıklayıp **iş parçacığı anahtarı**.

## <a name="group-and-sort-threads"></a>Grup ve sıralama iş parçacıkları  
 İş parçacıkları gruplandırdığınızda, tablodaki her grup için bir başlık görünür. Bir Grup açıklaması gibi başlık içeren **çalışan iş parçacığı** veya **bayrak yok iş parçacıkları**ve bir ağaç denetimi. Her grup üyesi iş parçacıklarının grubunun başlığının altında görünür. Bir grubun üyesi iş parçacıklarının gizlemek istiyorsanız, grubu daraltmak için ağaç denetimi kullanın.  
  
 Gruplandırma sıralama üzerinden öncelikli olduğundan, kategoriye, örneğin, iş parçacığı grubu ve alanlarını her kategoride Kimliğine göre sıralayabilirsiniz.  
  
### <a name="to-sort-threads"></a>İş parçacıkları sıralamak için  
  
1.  Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde herhangi bir sütunun üst düğmeyi seçin.  
  
     İş parçacıkları, artık bu sütundaki değerlere göre sıralanır.  
  
2.  Sıralama düzenini tersine çevirmek istiyorsanız, aynı düğmesini tekrar seçin.  
  
     Artık listesinin üstünde görünen iş parçacıkları ve en altında görünür.  
  
### <a name="to-group-threads"></a>İş parçacıklarını gruplandırma  
  
-   İçinde **iş parçacıkları** penceresi araç çubuğu, select **gruplandırma ölçütü** listelemek ve iş parçacıklarını gruplandırma istediğiniz ölçütleri seçin.  
  
### <a name="to-sort-threads-within-groups"></a>Grupları içindeki dizileri sıralama  
  
1.  Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde **gruplandırma ölçütü** listelemek ve iş parçacıklarını gruplandırma istediğiniz ölçütleri seçin.  
  
2.  İçinde **iş parçacıkları** penceresinde herhangi bir sütunun üst düğmeyi seçin.  
  
     İş parçacıkları, artık bu sütundaki değerlere göre sıralanır.  
  
### <a name="to-expand-or-collapse-all-groups"></a>Tüm grupları genişletin veya daraltın için  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde **genişletin grupları** veya **grupları Daralt**.  
  
## <a name="search-for-specific-threads"></a>Belirli bir iş parçacığı arama  
 Belirtilen bir dize içinde eşleşen iş parçacığı arayabilirsiniz **iş parçacıkları** penceresi. İş parçacıkları için arama yaparken, herhangi bir sütun arama dizesinde eşleşen tüm iş parçacıkları penceresini görüntüler. Bu bilgiler çağrı yığınında üstünde görünen iş parçacığı konum içeren **konumu** sütun. Varsayılan olarak, tam çağrı yığınını Aranan değil.  
  
### <a name="to-search-for-specific-threads"></a>Belirli iş parçacığı arama  
  
1. Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde, Git **arama** kutusu ve ya da:  

     - Bir arama dizesi girin ve sonra basın **Enter**.  
  
     \- veya -  
  
     - Aşağı açılan listesinde seçin **arama** kutusunda ve bir önceki aramaya ait arama dizesini seçin.  
  
2. (İsteğe bağlı) Tam çağrı yığınını aramanızda eklemek için işaretleyin **arama çağrı yığını**.   
  
## <a name="display-thread-call-stacks-and-switch-between-frames"></a>İş parçacığı çağrı yığınlarını görüntüleyebilir ve arasında çerçeveleri Değiştir  
Bir çoklu iş parçacığı kullanan programda her iş parçacığı kendi çağrı yığınına sahiptir. **İş parçacıkları** penceresi bu yığınlarını görüntülemek için kullanışlı bir yol sağlar.

> [!TIP]
> Her iş parçacığı için çağrı yığınını görsel bir temsilini için kullanmak [Paralel Yığınlar](../debugger/get-started-debugging-multithreaded-apps.md) penceresi.
  
### <a name="to-view-the-call-stack-of-a-thread"></a>İş parçacığı çağrı yığınını görüntülemek için  
  
-   İçinde **konumu** sütun, iş parçacığı konumu yanındaki ters üçgeni seçin.  
  
     İş parçacığı için çağrı yığınını Göster konumuna genişletir.  
  
### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Görüntüleme veya tüm iş parçacığı çağrı yığınlarını Daralt  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde **çağrı yığınlarını genişletme** veya **Daralt çağrı yığınlarını**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Çok iş parçacıklı uygulamalarda hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md)