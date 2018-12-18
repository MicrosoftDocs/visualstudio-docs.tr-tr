---
title: 'Nasıl yapılır: iş parçacıkları penceresini kullanma | Microsoft Docs'
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
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 925e5ec609c07fa1ca6d703943cf3437f0f9bf84
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791706"
---
# <a name="how-to-use-the-threads-window"></a>Nasıl Yapılır: İş Parçacıkları Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde **iş parçacıkları** penceresini inceleyin ve uygulamada hata ayıklaması yaptığınız iş parçacıkları ile çalışır.  
  
 **İş parçacıkları** penceresi, her satır bir iş parçacığında uygulamanızı temsil ettiği bir tablo içerir. Varsayılan olarak, uygulamanızı tüm iş parçacıklarının tabloda listelenir, ancak yalnızca sizi ilgilendiren iş parçacıklarını gösterilecek listeyi filtreleyebilirsiniz. Her sütun, farklı türde bilgi içerir. Ayrıca, bazı sütunları gizleyebilirsiniz. Tüm sütunları görüntülemek, aşağıdaki bilgileri, soldan sağa doğru görünür:  
  
-   Burada, özen istediğiniz bir iş parçacığını işaretleyebileyeceğiniz Bayrak sütunu. Bir iş parçacığı bayrak hakkında daha fazla bilgi için bkz: [nasıl yapılır: bayrağı ve iş parçacıklarını bayrakla](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   Sarı okun etkin bir iş parçacığında burada gösterir etkin iş parçacığı sütunu. Burada hata ayıklayıcıya yürütmeyi kesmeden iş parçacığı bir ok bir özetini gösterir.  
  
-   **Kimliği** her iş parçacığı kimlik numarasını içeren sütun.  
  
-   **Yönetilen kimliği** yönetilen iş parçacıkları için yönetilen kimlik sayıları içeren sütun.  
  
-   **Kategori** sütunu kullanıcı arabirimi iş parçacıkları, uzak yordam çağrı işleyicisi veya çalışan iş parçacıkları iş parçacıkları kategorilere ayırır. Uygulamanın ana iş parçacığı bir özel kategori tanımlar.  
  
-   **Adı** varsa veya olarak ada göre her bir iş parçacığı tanımlayan sütun \<No Name >.  
  
-   **Konumu** sütun, iş parçacığı çalıştığı hangi gösterir. Bu konum iş parçacığı için tam çağrı yığınını Göster genişletebilirsiniz.  
  
-   **Öncelik** öncelik ya da sistem her iş parçacığı için atanan öncelik içeren sütun.  
  
-   **Benzeşim maskesi** genellikle gizli bir Gelişmiş sütunu olan sütun. Her iş parçacığı için İşlemci benzeşim maskesi bu sütunda görüntülenir. Çok işlemcili bir sistemde, bir iş parçacığı üzerinde çalışabileceği hangi İşlemci benzeşim maskesi belirler.  
  
-   **Askıya sayısı** askıda sayma içeren sütun. Bu sayaç, bir iş parçacığı çalıştırılıp çalıştırılamayacağını belirler. Askıda sayma açıklaması için "Dondurma ve çözme iş parçacığı sayısı" bölümüne bakın.  
  
-   **İşlem adı** her iş parçacığı ait olduğu için işlem içeren sütun. Bu sütun, birden çok işlemde hata ayıklama, ancak genellikle gizli yararlı olabilir.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>İş parçacıkları penceresini kesme modunda veya çalıştırma modunda görüntülemek için  
  
-   Üzerinde **hata ayıklama** menüsünde **Windows**ve ardından **iş parçacıkları**.  
  
### <a name="to-display-or-hide-a-column"></a>Bir sütunu sakla ya da görüntülemek için  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde tıklayın **sütunları**sonra seçin veya temizleyin, göstermek veya gizlemek istediğiniz sütun adı.  
  
### <a name="to-switch-the-active-thread"></a>Etkin iş parçacığı geçiş yapmak için  
  
-   Aşağıdaki adımlardan birini gerçekleştirin:  
  
    -   Herhangi bir iş parçacığı çift tıklayın.  
  
    -   Bir iş parçacığı sağ tıklatıp **iş parçacığına geçiş**.  
  
         Yeni etkin iş parçacığı yanındaki sarı ok görünür. Bir ok gri özetini burada hata ayıklayıcıya yürütmeyi kesmeden iş parçacığını tanımlar.  
  
## <a name="grouping-and-sorting-threads"></a>İş parçacıkları sıralama ve gruplandırma  
 İş parçacıkları gruplandırdığınızda, tablodaki her grup için bir başlık görünür. Başlığı "Çalışan iş parçacığı" veya "Bayrak yok iş parçacığı sayısı" ve ağaç denetimi gibi bir Grup açıklaması içerir. Her grup üyesi iş parçacıklarının grubunun başlığının altında görünür. Bir grubun üyesi iş parçacıklarının gizlemek istiyorsanız, grubu daraltmak için ağaç denetimi kullanabilirsiniz.  
  
 Gruplandırma sıralama üzerinden öncelikli olduğundan, kategoriye, örneğin, iş parçacığı grubu ve alanlarını her kategoride Kimliğine göre sıralayabilirsiniz.  
  
#### <a name="to-sort-threads"></a>İş parçacıkları sıralamak için  
  
1.  Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde herhangi bir sütun üst kısmındaki düğmeye tıklayın.  
  
     İş parçacıkları, artık bu sütundaki değerlere göre sıralanır.  
  
2.  Sıralama düzenini tersine çevirmek istiyorsanız, aynı düğmesine tekrar tıklayın.  
  
     Artık listesinin üstünde görünen iş parçacıkları ve en altında görünür.  
  
#### <a name="to-group-threads"></a>İş parçacıklarını gruplandırma  
  
-   İçinde **iş parçacıkları** penceresi araç çubuğu, tıklayın **gruplandırma ölçütü** listelemek ve iş parçacıklarını gruplandırma istediğiniz ölçütleri'ı tıklatın.  
  
#### <a name="to-sort-threads-within-groups"></a>Grupları içindeki dizileri sıralama  
  
1.  Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde tıklayın **gruplandırma ölçütü** listelemek ve iş parçacıklarını gruplandırma istediğiniz ölçütleri'ı tıklatın.  
  
2.  İçinde **iş parçacıkları** penceresinde herhangi bir sütun üst kısmındaki düğmeye tıklayın.  
  
     İş parçacıkları, artık bu sütundaki değerlere göre sıralanır.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Tüm grupları genişletin veya daraltın için  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde tıklayın **Grupları Genişlet** veya **grupları Daralt**.  
  
## <a name="searching-for-specific-threads"></a>Belirli iş parçacığı arama  
 İçinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], belirtilen bir dizenin eşleşen iş parçacığı için arama yapabilirsiniz. İş parçacıkları için arama yaptığınızda **iş parçacıkları** penceresinde herhangi bir sütunda arama dizesiyle eşleşen tüm iş parçacıkları pencere görüntüler. Çağrı yığınında üstünde görünen iş parçacığı konumu bilgilerdir **konumu** sütun. Varsayılan olarak, ancak tam çağrı yığınını aranmaz.  
  
#### <a name="to-search-for-specific-threads"></a>Belirli iş parçacığı arama  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde, Git **arama** kutusu ve ya da:  
  
    -   Bir arama dizesi yazın ve ENTER tuşuna basın.  
  
         \- veya -  
  
    -   Aşağı açılan listeye tıklayın **arama** kutusunda ve bir önceki aramaya ait arama dizesini seçin.  
  
-   (İsteğe bağlı) Tam çağrı yığınını aramanızda eklemek için işaretleyin **arama çağrı yığını**.  
  
## <a name="freezing-and-thawing-threads"></a>Dondurma ve iş parçacıklarını çözme  
 Bir iş parçacığını Dondur, sistem kaynakları kullanılabilir olsa bile, iş parçacığının yürütülmesini başlatılmaz.  
  
 Yerel kodda askıya alma veya Windows işlevleri çağırarak iş parçacıklarını sürdürme `SuspendThread` ve `ResumeThread` veya MFC işlevleri [CWinThread::SuspendThread](http://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) ve [CWinThread::ResumeThread](http://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). Çağırırsanız `SuspendThread` veya `ResumeThread`, değiştirdiğiniz *askıya sayısı*, içinde göründüğü **iş parçacıkları** penceresi. Ancak, dondurma veya çözme yerel bir iş parçacığı, askıda sayma değiştirmeyin. Çözülmüş ve askıya alınmış sayısı sıfır olan sürece yerel kodda iş parçacığı yürütülemiyor.  
  
 Yönetilen kodda dondurma veya çözme iş parçacığı askıda sayma değiştirin. Yönetilen kodda dondurulmuş bir iş parçacığı askıda sayısı 1 ' var. Yerel kodda iş parçacığı tarafından askıya alındı sürece askıya alınmış sayısı 0 dondurulmuş bir iş parçacığı sahip bir `SuspendThread` çağırın.  
  
> [!NOTE]
>  Yönetilen koda yerel koddan bir çağrı hata ayıklaması yaparken, yönetilen kod aynı fiziksel iş parçacığında adlı yerel kod olarak çalışır. Yönetilen kod da askıya alma ya da yerel iş parçacığını dondurma donuyor.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Dondurma veya çözme iş parçacığı yürütme için  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde tıklayın **iş parçacıklarını dondurma** veya **çözme iş parçacığı**.  
  
     Bu eylem, seçili iş parçacıklarını etkiler **iş parçacıkları** penceresi.  
  
## <a name="displaying-flagged-threads"></a>Bayraklı iş parçacıklarını görüntüleme  
 Bir simge ile işaretleyerek özel dikkat vermek istediğiniz bir iş parçacığı işaretleyebilirsiniz **iş parçacıkları** penceresi. Daha fazla bilgi için [nasıl yapılır: bayrağı ve iş parçacıklarını bayrakla](../debugger/how-to-flag-and-unflag-threads.md). İş parçacıkları penceresinde tüm iş parçacıkları veya yalnızca bayraklı iş parçacıklarını görüntülemeyi tercih edebilirsiniz.  
  
#### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını görüntülemek için  
  
-   Sol üst köşesinde bayrağı düğmesini **iş parçacıkları** penceresi.  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>İş parçacığı çağrı yığınlarını görüntüleme ve çerçeveler arasında geçiş yapma  
 Bir çoklu iş parçacığı kullanan programda her iş parçacığı kendi çağrı yığınına sahiptir. **İş parçacıkları** penceresi bu yığınlarını görüntülemek için kullanışlı bir yol sağlar.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>İş parçacığı çağrı yığınını görüntülemek için  
  
-   İçinde **konumu** sütun, iş parçacığı konumu yanındaki ters üçgene tıklayın.  
  
     İş parçacığı için çağrı yığınını Göster konumuna genişletir.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Görüntüleme veya tüm iş parçacığı çağrı yığınlarını Daralt  
  
-   Üst kısmındaki araç çubuğunda **iş parçacıkları** penceresinde tıklayın **çağrı yığınlarını genişletme** veya **Daralt çağrı yığınlarını**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [İzlenecek Yol: Çok İş Parçacıklı Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-multithreaded-application.md)



