---
title: 'İzlenecek yol: çok iş parçacıklı uygulamada hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5dd742411710698cb2dd626e211cb0e73b8379e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798650"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>İzlenecek Yol: Çok İş Parçacıklı Uygulamada Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Gelişmiş sağlar **iş parçacıkları** penceresi ve diğer kullanıcı arabirimi hata ayıklama çok iş parçacıklı uygulamalarda daha kolay hale getirmek için iyileştirmeler. Bu izlenecek yol yalnızca birkaç dakika sürer, ancak bunu tamamlamaya, çok iş parçacıklı uygulamalarda hata ayıklama için yeni arabirimi özellikleri ile alışmanızı.  
  
 Bu izlenecek yolda başlamak için bir çok iş parçacıklı uygulaması projesi gerekir. Bu projeyi oluşturmak için burada listelenen adımları izleyin.  
  
#### <a name="to-create-the-walkthrough-project"></a>İzlenecek yol projeyi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde seçin **yeni** ve ardından **proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  İçinde **proje türü**s kutusunda, tercih ettiğiniz dili: **Visual Basic**, **Visual C#**, veya **Visual C++**.  
  
3.  İçinde **şablonları** kutusunda **konsol uygulaması** veya **CLR konsol uygulaması**.  
  
4.  İçinde **adı** kutusuna MyThreadWalkthroughApp adı yazın.  
  
5.  **Tamam**'ı tıklatın.  
  
     Yeni bir konsol projesi görünür. Bir kaynak dosyası projeyi oluşturduğunuzda görünür. Seçtiğiniz dile bağlı olarak, kaynak dosya Module1.vb, Program.cs veya MyThreadWalkthroughApp.cpp çağrılabilir  
  
6.  Kaynak dosyada kod silin ve konunun bölümünde "Bir iş parçacığı oluşturulurken" görünen örnek kod ile değiştirin [iş parçacığı oluşturma ve geçirme verilerini başlangıç zamanında](http://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7.  Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet**.  
  
#### <a name="to-begin-the-walkthrough"></a>İzlenecek yol başlamak için  
  
-   Kaynak penceresinde, aşağıdaki kodu bulun:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Hata ayıklamayı başlatmak için  
  
1.  Sağ `Console.WriteLine` deyimi, noktasına **kesme noktası** ve ardından **kesme noktası Ekle**.  
  
     Kaynak pencerenin sol tarafındaki kanalda, kırmızı bir TOP görünür. Bu, bir kesme noktası bu konumda şimdi ayarlandığını gösterir.  
  
2.  Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.  
  
     Hata ayıklama başladığında, çalıştırmak için konsol uygulaması başlar ve kesme noktası sonra durur.  
  
3.  Konsol uygulama penceresine odak bu noktada varsa, tıklayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Pencere odağı döndürülecek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Kaynak penceresinde, aşağıdaki kodu içeren satırı bulun:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1.  
  
#### <a name="to-discover-the-thread-marker"></a>İş parçacığı işaret bulmak için  
  
1. Sağ **iş parçacıkları** penceresinde ardından **kaynak iş parçacıklarını Göster**.  
  
2. Pencerenin sol tarafındaki cilt payını bakın. Bu satırda iki bez iş parçacığı benzer bir simge görürsünüz. Bir iş parçacığı kırmızı ve diğer mavi şeklindedir. İş parçacığı işaretçisi, bir iş parçacığı bu konuma durdurulduğunu gösterir. Bu konumda büyük olasılıkla, iş parçacığı durduruldu.  
  
3. İşaretçi iş parçacığı işaret gelin. Bir DataTip görünür. DataTip durdurulmuş her iş parçacığı için adı ve iş parçacığı kimlik numarasını belirtir. Bu durumda, yalnızca bir iş parçacığı adı büyük olasılıkla yoktur `<noname>`.  
  
4. İş parçacığı işaret sağ tıklayın. Kısayol menüsündeki seçenekleri unutmayın.  
  
   Bu simge bir *iş parçacığı işaret*:  
  
   ![İş parçacığı işaret](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Bayrak ekleme ve Unflagging iş parçacıkları  
 İçinde [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)], özel dikkat vermek istediğiniz iş parçacıklarının bayrağını. İş parçacıklarını işaretleme, önemli iş parçacığı izlemek ve iş parçacıkları hakkında önemli yoksaymak için iyi bir yoludur.  
  
#### <a name="to-flag-threads"></a>İş parçacıklarını için  
  
1.  Üzerinde **görünümü** menüsünde **araç çubukları**.  
  
     Emin olun **hata ayıklama konumu** araç seçili.  
  
2.  Git **hata ayıklama konumu** araç çubuğu ve tıklatın **iş parçacığı** listesi.  
  
    > [!NOTE]
    >  Bu araç tarafından üç tanınmış listeleri tanıyabilmesi: **işlem**, **iş parçacığı**, ve **yığın çerçevesi**.  
  
3.  Ne kadar iş parçacığı listede göründüğüne dikkat edin.  
  
4.  Geri Git sağ tıklayın ve kaynak penceresinde **iş parçacığı** yeniden işaretçisi.  
  
5.  Kısayol menüsünde, işaret **bayrağı**, iş parçacığı adı ve kimlik numarası'ı tıklatın.  
  
6.  Geri Git **hata ayıklama konumu** araç çubuğu ve tıklayın **iş parçacığı** yeniden listeleyin.  
  
     Yalnızca bayraklı iş parçacığı listesinde görünür. Yalnızca sağında bayrağı düğmesi **iş parçacığı** listesi. Bayrak simgesine düğmesine, önce soluk. Şimdi, bir düz, parlak kırmızı geldi.  
  
7.  İşaretçiyi, bayrak simgesinin üzerine gelin.  
  
     Bir açılır pencere görüntülenir. Bu açılır pencere modu söyler **iş parçacığı** listesi konusu: **yalnızca bayraklı iş parçacıklarını Göster**.  
  
8.  Geri geçiş yapmak için bayrağı düğmesine **tüm iş parçacıklarını Göster** modu.  
  
9. Tıklayın **iş parçacığı** yeniden listeleme ve, artık tüm iş parçacıklarını yeniden görebildiğinizi doğrulayın.  
  
10. Geri geçiş yapmak için bayrağı düğmesine **yalnızca bayraklı iş parçacıklarını Göster**.  
  
11. Üzerinde **hata ayıklama** menüsünde **Windows** ve ardından **iş parçacıkları**.  
  
     **İş parçacıkları** penceresi görüntülenir. Bir iş parçacığı bağlı bir belirgin bayrak simgesine sahip.  
  
12. Kaynak penceresinde, iş parçacığı işaret tekrar sağ tıklayın.  
  
     Hangi seçenek kısayol menüsünde kullanılabilir dikkat edin. Yerine **bayrağı**, şimdi **Unflag**. Tıklamayın **Unflag**.  
  
13. İş parçacıklarını bayrakla konusunda sonraki yordama gidin.  
  
#### <a name="to-unflag-threads"></a>İş parçacıklarını bayrakla için  
  
1.  Üzerinde **iş parçacıkları** penceresinde bayraklı iş parçacığına karşılık gelen satıra sağ tıklayın.  
  
     Bir kısayol menüsü görüntülenir. Seçeneklerine sahip **Unflag** ve **işaretsiz tüm**.  
  
2.  İş parçacığının işaretini Kaldır için tıklatın **Unflag**.  
  
3.  Kırmızı bayrak simgesine tıklayın.  
  
4.  Bakmak **hata ayıklama konumu** yeniden araç çubuğu. Bayrak düğmesini tekrar soluklaşır. Yalnızca bayraklı iş parçacığının işaretini kaldıran. Hiçbir işaretli iş parçacığı olduğundan, araç için geri geçti **tüm iş parçacıklarını Göster** modu. Tıklayın **iş parçacığı** listelemek ve tüm iş parçacıklarının görebildiğinizi doğrulayın.  
  
5.  Geri Git **iş parçacıkları** penceresi ve bilgi sütunu inceleyin.  
  
     Her bir sütunun üstünde, düğmelerin çoğu sütun tanımlayan başlıklar sahiptir. Ancak, sol taraftaki ilk sütun başlığı yok. Bunun yerine, bir bayrak anahat bir simge vardır. Dizi listesinin her satırında aynı ana hat fark edeceksiniz. Ana hat iş parçacığı bayrak yok anlamına gelir.  
  
6.  İki iş parçacığı, ikinci ve üçüncü listenin en üstündeki bayrağı anahatları tıklayın.  
  
     Bayrak simgeleri boş anahatları yerine düz kırmızı olur.  
  
7.  Bayrak sütunu üst kısmındaki düğmeye tıklayın.  
  
     Düğme tıklandığında değiştirilen iş parçacığı listesi sırası. Dizi listesini üstte bayraklı iş parçacıklarını artık sıralanır.  
  
8.  Yeniden, bayrak sütunu üst kısmındaki düğmeye tıklayın.  
  
     Sıralama düzenini yeniden değiştirildi.  
  
## <a name="more-about-the-threads-window"></a>İş parçacıkları penceresi hakkında daha fazla bilgi  
  
#### <a name="to-learn-more-about-the-threads-window"></a>İş parçacıkları penceresi hakkında daha fazla bilgi edinmek için  
  
1.  İçinde **iş parçacıkları** penceresinde üçüncü sütunda soldan inceleyin. Bu sütunun üstünde düğme diyor **kimliği**.  
  
2.  Tıklayın **kimliği**.  
  
     Dizi listesini artık iş parçacığı kimliği numarasına göre sıralanır.  
  
3.  Listedeki herhangi bir iş parçacığı sağ tıklayın. Kısayol menüsünde **onaltılık gösterim**.  
  
     İş parçacığı kimliği sayılarının biçimini değiştirilir.  
  
4.  Fare işaretçisi listedeki herhangi bir iş parçacığı üzerine gelin.  
  
     İçeriklerinin anlık bir gecikmeden sonra bir DataTip görünür. Bu iş parçacığı için bir kısmi çağrı yığınını gösterir.  
  
5.  Etiketli üstten dördüncü sütununda Ara **kategori**. İş parçacıkları kategoride sınıflandırılır.  
  
     Bir işlemde oluşturulan ilk iş parçacığında ana iş parçacığı adlandırılır. İş parçacığı listesinde bulun.  
  
6.  Ana iş parçacığı sağ tıklayın ve ardından **iş parçacığına geçiş**.  
  
     Bir uyarı iletişim kutusu görünür. Bu başarısız olduğunu anlatan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ana iş parçacığı için kaynak kodu görüntülenemiyor.  
  
     **Tamam**'ı tıklatın.  
  
7.  Bakmak **çağrı yığını** penceresi ve **hata ayıklama konumu** araç çubuğu.  
  
     İçeriğini **çağrı yığını** penceresi değişti.  
  
## <a name="switching-the-active-thread"></a>Etkin iş parçacığı değiştirme  
  
#### <a name="to-switch-threads"></a>Geçiş yapmak için iş parçacıkları  
  
1.  İçinde **iş parçacıkları** penceresinde soldan ikinci sütunda inceleyin. Bu sütunun üstünde düğme, metin veya simge vardır. Bu sütun **etkin iş parçacığı** sütun.  
  
2.  Bakmak **etkin iş parçacığı** sütunu ve tek bir iş parçacığı bir sarı ok olduğunu göreceksiniz. Bu *etkin iş parçacığı göstergesi*.  
  
3.  Etkin iş parçacığı göstergesi bulunduğu iş parçacığı kimlik numarasını not edin. Başka bir iş parçacığı için etkin iş parçacığı göstergesi taşınır, ancak geri bitirdiğinizde koymak istediğiniz gerekir.  
  
4.  Başka bir iş parçacığı sağ tıklayın ve ardından **iş parçacığına geçiş**.  
  
5.  Bakmak **çağrı yığını** penceresi kaynak penceresinde. İçeriği değişmiş.  
  
6.  Bakmak **hata ayıklama konumu** araç çubuğu. Etkin iş parçacığı, çok değişti.  
  
7.  Git **hata ayıklama konumu** araç çubuğu. Tıklayın **iş parçacığı** kutusu ve aşağı açılan listeden farklı bir iş parçacığı seçin.  
  
8.  Bakmak **iş parçacıkları** penceresi. Etkin iş parçacığı göstergesi değişti.  
  
9. Kaynak penceresinde, bir iş parçacığı işaret sağ tıklayın. Kısayol menüsünde, işaret **geçin** ve bir iş parçacığı adı/kimlik numarasını'ı tıklatın.  
  
     Etkin iş parçacığı değiştirme üç yolu artık gördünüz: kullanarak **iş parçacıkları** penceresinde **iş parçacığı** kutusunda **hata ayıklama konumu** araç çubuğu ve iş parçacığı göstergesi Kaynak penceresi.  
  
     İş parçacığı göstergesi ile belirli bir konumda durdurulan iş parçacığı geçiş yapabilirsiniz. Kullanarak **iş parçacıkları** penceresi ve **hata ayıklama konumu** araç için herhangi bir iş parçacığı geçirebilirsiniz.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Dondurma ve iş parçacığı yürütmeyi çözme  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Freeze ve iş parçacığı Çöz  
  
1.  İçinde **iş parçacıkları** penceresinde herhangi bir iş parçacığı sağ tıklayın ve ardından **dondurma**.  
  
2.  Etkin iş parçacığı sütununa bakın. Dikey çubuk çifti artık var. görüntülenir. Bu iki mavi çubukları, iş parçacığı'nın dondurulmuş olup olmadığını gösterir.  
  
3.  Bakmak **askıya alma** sütun. İş parçacığı için askıya alma sayımı artık 1'dir.  
  
4.  Dondurulmuş bir iş parçacığı sağ tıklayın ve ardından **çözme**.  
  
     Etkin iş parçacığı sütunu ve **askıya alma** sütun değişikliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Nasıl Yapılır: Hata Ayıklarken Başka Bir İş Parçacığına Geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)



