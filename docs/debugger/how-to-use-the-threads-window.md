---
title: Çok iş parçacıklı uygulamaların hatalarını ayıklama
description: Visual Studio'da iş parçacıkları penceresi ve hata ayıklama konumu araç çubuğu kullanarak hata ayıklama
ms.custom: ''
ms.date: 11/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd66d7f9d8f214e8e7166a77162553b694e20cc5
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389409"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window"></a>İzlenecek yol: iş parçacıkları penceresini kullanarak birden çok iş parçacıklı bir uygulamanın hatalarını ayıklama

Birçok Visual Studio kullanıcı arabirimi öğeleri birden çok iş parçacıklı uygulamaların hatalarını ayıklamanıza yardımcı olur. Bu makale Kod Düzenleyicisi penceresinde birden çok iş parçacıklı hata ayıklama özellikleri tanıtır **hata ayıklama konumu** araç ve **iş parçacıkları** penceresi. Hata ayıklama çok iş parçacıklı uygulamalar için diğer araçları hakkında daha fazla bilgi için bkz: [birden çok iş parçacıklı uygulamalarında hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md). 
  
Bu öğreticiyi tamamlamak, yalnızca birkaç dakika sürer ve hata ayıklama çok iş parçacıklı uygulamalar ile ilgili temel familiarizes.

## <a name="create-a-multithreaded-app-project"></a>Çok iş parçacıklı uygulaması projesi oluşturma  

Bu öğreticide kullanmak üzere aşağıdaki birden çok iş parçacıklı uygulaması projesi oluşturun: 
  
1. Visual Studio'da **dosya** > **yeni** > **proje**.  
   
1. İçinde **yeni proje** iletişim kutusunda:
   - İçin bir C# uygulama, select **Visual C#**    >  **konsol uygulaması (.NET Framework)**.  
   - Bir C++ uygulama için seçin **Visual C++** > **Windows konsol uygulaması**.
   
1. Uygulama MyThreadWalkthroughApp adlandırın ve ardından **Tamam**.  
   
   Yeni Proje görünür **Çözüm Gezgini**, ve bir kaynak dosyası adlı *Program.cs* veya *MyThreadWalkthroughApp.cpp* kaynak kod penceresinde açılır.  
   
1. Kaynak dosyasıyla değiştirin C# veya C++ Örnek koddan [birden çok iş parçacıklı uygulamalarında hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md).  
   
1. Seçin **dosya** > **Tümünü Kaydet**.  
  
## <a name="start-debugging"></a>Hata Ayıklamayı Başlat 

1. Kaynak kodunda aşağıdaki satırları bulun:  
   
   ```csharp  
   Thread.Sleep(3000); 
   Console.WriteLine();
   ```  
   
   ```C++ 
   Thread::Sleep(3000); 
   Console.WriteLine(); 
   ```
   
1. Bir kesme noktası ayarlamak `Console.WriteLine();` sol cilt payını tıklayarak veya çizgiyi seçerek ve tuşuna basarak satır **F9**.  
   
   Kesme noktası sol kanaldaki kod satırının yanında kırmızı bir daire olarak görünür.  
   
1. Seçin **hata ayıklama** > **hata ayıklamayı Başlat**, veya basın **F5**.  
   
   Uygulama, hata ayıklama modunda başlar ve kesme noktasında duraklatır.  
   
1. Kesme modundayken, açma **iş parçacıkları** penceresini seçerek **hata ayıklama** > **Windows** > **iş parçacıkları**. Açın veya hata ayıklama oturumunda olmalıdır **iş parçacıkları** ve diğer hata ayıklama windows. 
   
## <a name="examine-thread-markers"></a>İş parçacığı işaretçileri inceleyin

1. Kaynak kodunda bulun `Console.WriteLine();` satır. 
   
   1. Sağ **iş parçacıkları** penceresi ve Seç **kaynak iş parçacıklarını Göster** ![kaynak iş parçacıklarını Göster](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") menüsünde.
   
   Cilt payını yanındaki kaynak kodu satır görüntüler artık bir *iş parçacığı işaret* simgesi ![iş parçacığı işaret](../debugger/media/dbg-thread-marker.png "iş parçacığı işaret"). İş parçacığı işaretçisi, bir iş parçacığı bu konuma durdurulduğunu gösterir. Konumunda, birden fazla durdurulan iş parçacığı ise ![birden çok iş parçacığı](../debugger/media/dbg-multithreaded-show-threads.png "birden çok iş parçacığı") simgesi görünür.
   
1. İşaretçi iş parçacığı işaret gelin. Durdurulan iş parçacığı veya iş parçacığı adı ve iş parçacığı kimlik numarasını gösteren bir DataTip görünür. İş parçacığı adları olabilir `<No Name>`.  

   >[!TIP]
   >Adsız iş parçacığı belirlemenize yardımcı olması için bunları yeniden adlandırabilirsiniz **iş parçacıkları** penceresi. İş parçacığı sağ tıklayıp **Yeniden Adlandır**.
  
1. Kısayol menüsünde kullanılabilir seçenekleri görmek için kaynak kodda iş parçacığı işaret sağ tıklayın. 

## <a name="flag-and-unflag-threads"></a>İş parçacıklarını bayrakla işaretleme ve işareti geri alma 

Özel dikkat edilmesi gereken istediğiniz iş parçacığı izlemek için iş parçacığı işaretleyebilirsiniz. 

Kaynak Kod Düzenleyicisi'ni ya da iş parçacıklarını bayrakla işaretleme ve bayrak **iş parçacıkları** penceresi. Yalnızca gelen iş parçacıkları veya tüm iş parçacıklarını bayrakla görüntülemek isteyip istemediğinizi seçin **hata ayıklama konumu** veya **iş parçacıkları** penceresi araç çubukları. Tüm Konumlar herhangi bir konumdan yapılan seçimleri etkiler. 

### <a name="flag-and-unflag-threads-in-source-code"></a>Kaynak kodunda iş parçacıklarını bayrakla işaretleme ve bayrak 

1. Açık **hata ayıklama konumu** seçerek araç **görünümü** > **araç çubukları** > **hata ayıklama konumu**. Ayrıca araç çubuğu alanına sağ tıklatıp seçin **hata ayıklama konumu**. 
   
1. **Hata ayıklama konumu** araç üç alan vardır: **işlem**, **iş parçacığı**, ve **yığın çerçevesi**. Açılan menü **iş parçacığı** listesinde ve ne kadar iş parçacığı yok olduğuna dikkat edin. İçinde **iş parçacığı** liste, şu anda çalışan bir iş parçacığı olarak işaretlenmiş bir **>** simgesi. 
   
1. Kaynak kod penceresinde, bir iş parçacığı işaret simgesi cilt payını üzerine gelin ve DataTip içinde bayrak simgesine (veya boş bayrağını simge) seçin. Bayrak simgesine kırmızıya döner. 
   
   Ayrıca bir iş parçacığı işaret simgesi sağ işaret **bayrağı**ve ardından kısayol menüsünden işaretlemek için bir iş parçacığı seçin.  
   
1. Üzerinde **hata ayıklama konumu** araç, select **yalnızca bayraklı iş parçacıklarını Göster** simgesi ![bayraklı iş parçacıklarını Göster](../debugger/media/dbg-threads-show-flagged.png "bayraklı iş parçacıklarını Göster"), sağ **iş parçacığı** alan. Bir veya daha fazla iş parçacıklarını bayrakla sürece simgesi gri renkte gösterilir.  
   
   Yalnızca bayraklı iş parçacığı görüntülenir **iş parçacığı** araç çubuğundaki açılır. Tüm iş parçacıklarını yeniden göstermek için seçin **yalnızca bayraklı iş parçacıklarını Göster** yeniden simgesi.
   
   >[!TIP]
   >Bazı iş parçacıkları işaretlediğiniz sonra Kod Düzenleyicisi, sağ tıklatın ve seçin, imleci yerleştirebilirsiniz **çalıştırma bayraklı iş parçacıklarını imlece kadar**. Bayraklı iş parçacıklarını tüm kod ulaşacak seçtiğinizden emin olun. **İmlece Git bayraklı iş parçacıklarını** kod yürütme sırasını denetlemek kolaylaştıran, seçilen satırdaki iş parçacıkları duraklatılır [dondurma ve iş parçacıklarını çözme](#bkmk_freeze).
   
1. Şu anda yürütülen iş parçacığının bayrak eklenmiş veya bayrak yok durumu geçiş yapmak için tek bayrakla seçin **geçiş geçerli iş parçacığı bayraklı durumu** solundaki araç çubuğu düğmesi **yalnızca bayraklı iş parçacıklarını Göster** düğmesi. Geçerli iş parçacığını işaretleme yalnızca bayraklı iş parçacıklarını gösterilirken, geçerli iş parçacığı konumunu belirlemek için yararlıdır. 
   
1. Bir iş parçacığının işaretini Kaldır için kaynak kodda iş parçacığı işaret üzerine gelin ve, temizlemek veya iş parçacığı işaret sağ tıklayıp kırmızı bayrak simgesini seçerek **Unflag**.  

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>İş parçacıkları penceresinde iş parçacıklarını bayrakla işaretleme ve bayrak 

İçinde **iş parçacıkları** penceresinde bayraklı iş parçacıklarını kırmızı bayrak simgeleri yanında, iş parçacığı bayrak yok, hata yoksa, boş simgelere sahip olması.

![İş parçacıkları penceresi](../debugger/media/dbg-threads-window.png "iş parçacıkları penceresi")  
  
Bayrak eklenmiş veya bayrak yok, geçerli durumuna bağlı olarak iş parçacığı durumu değiştirmek için bir bayrağı simgesini seçin. 

Ayrıca bir satıra sağ tıklayın ve seçin **bayrağı**, **Unflag**, veya **tüm iş parçacıklarını bayrakla** kısayol menüsünden. 

**İş parçacıkları** penceresi araç çubuğu de sahip bir **sadece iş parçacığı bayrak eklenmiş Göster** righthand iki bayrağı simgelerden birini düğmesi. Düğme aynı üzerinde çalıştığı **hata ayıklama konumu** araç çubuğu ve herhangi bir düğmeyi görünen konumlarının her ikisinde de denetler. 

### <a name="other-threads-window-features"></a>Diğer iş parçacıkları penceresi özellikleri

İçinde **iş parçacıkları** penceresinde iş parçacıkları bu sütuna göre sıralamak için herhangi bir sütun başlığını seçin. Sıralama düzenini tersine çevirmek için bir kez daha seçin. Tüm iş parçacıkları yoksa, bayrak simgesinin sütunu seçme iş parçacığı işaretli veya bayrak yok duruma göre sıralar. 

İkinci sütun **iş parçacıkları** penceresi (üst bilgi ile) **geçerli iş parçacığı** sütun. Bu sütundaki sarı bir ok geçerli yürütme noktasını işaretler. 

**Konumu** sütunda her bir iş parçacığı kaynak kodunda göründüğü görüntülenir. Genişletme oku seçin **konumu** girişi veya iş parçacığı için bir kısmi çağrı yığınını Göster girişi,'ın üzerine gelin. 

>[!TIP]
>İş parçacığı için çağrı yığınlarını için bir grafik görünümü kullanmak [Paralel Yığınlar](../debugger/using-the-parallel-stacks-window.md) penceresi. Hata ayıklama sırasında penceresini açmak için seçmeniz **hata ayıklama**> **Windows** > **Paralel Yığınlar**.  

Ek olarak **bayrağı**, **Unflag**, ve **tüm iş parçacıklarını bayrakla**, sağ tıklama bağlam menüsünü **iş parçacığı** pencere öğeleri vardır:

- **Kaynak iş parçacıklarını Göster** düğmesi.
- **Onaltılık gösterim**, hangi değişikliklerin **iş parçacığı kimliği**s'te **iş parçacıkları** ondalık penceresine on altılık biçimde. 
- [İş parçacığı anahtarı](#switch-to-another-thread), hangi hemen yürütme iş parçacığı için geçer. 
- **Yeniden adlandırma**, olanak sağlayan iş parçacığı adı değiştirin. 
- [Dondurma ve çözme](#bkmk_freeze) komutları.

## <a name="bkmk_freeze"></a> Dondurma ve iş parçacığı yürütmeyi çözme 

Dondurma ve çözme, veya askıya alma ve sürdürme, iş parçacıkları iş gerçekleştiren sırasını denetlemek için iş parçacığı. Dondurma ve iş parçacıklarını çözme eşzamanlılık kilitlenmeler gibi sorunları çözmek ve yarış durumlarına yardımcı olabilir.

> [!TIP]
> Diğer iş parçacıkları, aynı zamanda genel bir hata ayıklama senaryosuna olan dondurma olmadan tek bir iş parçacığı izlemek için bkz: [birden çok iş parçacıklı uygulamalarda hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
**Dondurma iş parçacığı Çöz için:**  
  
1. İçinde **iş parçacıkları** penceresinde herhangi bir iş parçacığı sağ tıklayın ve ardından **dondurma**. A **duraklatma** simgesini **geçerli iş parçacığı** sütunu, iş parçacığı'nın dondurulmuş olup olmadığını gösterir.  
   
1. Seçin **sütunları** içinde **iş parçacıkları** penceresi araç çubuğu ve ardından **askıya sayısı** görüntülenecek **askıya sayısı** sütun. Dondurulmuş bir iş parçacığı askıda sayma değeri **1**.  
   
1. Dondurulmuş bir iş parçacığı sağ tıklayıp **çözme**.  
  
   **Duraklatma** logo kaybolur ve **askıya sayısı** değeri **0**. 
  
## <a name="switch-to-another-thread"></a>Başka bir iş parçacığına geçiş 

Görebileceğiniz bir **uygulama kesme modundayken** başka bir iş parçacığına geçiş çalıştığınızda penceresi. Bu pencere, iş parçacığının geçerli hata ayıklayıcı görüntüleyebilen herhangi bir kod yok bildirir. Örneğin, yönetilen kodda hata ayıklama, ancak yerel kod parçacığıdır. Pencere, sorunu çözmek için öneriler sunar. 
  
**Başka bir iş parçacığına geçiş yapmak için:**

1. İçinde **iş parçacıkları** penceresinde, geçerli iş parçacığı kimliğini not sarı bir ok ile iş parçacığı olduğu **geçerli iş parçacığı** sütun. Uygulamanızı devam etmek için bu iş parçacığına geri geçmek istersiniz. 
   
1. Farklı bir iş parçacığına sağ tıklayıp **iş parçacığı anahtarı** bağlam menüsünden.  
   
1. Sarı ok konumu olarak değiştiğini gözlemleyin **iş parçacıkları** penceresi. Özgün geçerli iş parçacığı işaretçi de, anahat olarak kalır. 
   
   Kaynak Kod düzenleyicisinde iş parçacığı işaret ve listede ipucuna bakın **iş parçacığı** üzerindeki açılır menüye **hata ayıklama konumu** araç çubuğu. Geçerli iş parçacığı da var. değiştiğini gözlemleyin. 
   
1. Üzerinde **hata ayıklama konumu** araç, farklı bir iş parçacığından seçin **iş parçacığı** listesi. Geçerli iş parçacığı diğer iki konumda da değiştiğine dikkat edin. 
   
1. Bir iş parçacığı işaretçisi Kaynak Kod Düzenleyicisi'nde sağ tıklatın, **iş parçacığı anahtarı**, listeden başka bir iş parçacığı seçin. Geçerli iş parçacığının tüm üç konumda değiştiğini gözlemleyin.  
   
Kaynak kodda iş parçacığı işaretleyiciyle o konumda durdurulan iş parçacığı geçiş yapabilirsiniz. Kullanarak **iş parçacıkları** penceresi ve **hata ayıklama konumu** araç için herhangi bir iş parçacığı geçirebilirsiniz.   

Artık, hata ayıklama çok iş parçacıklı uygulamalar hakkındaki temel bilgileri öğrendiniz. İnceleyin, bayrak ve işaretleme, dondurma ve kullanarak çözme iş parçacığı **iş parçacıkları** penceresinde **iş parçacığı** listesinde **hata ayıklama konumu** araç çubuğunu veya içinde iş parçacığı işaretçileri Kaynak Kod Düzenleyicisi.
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Nasıl yapılır: Hata ayıklarken başka bir iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)
