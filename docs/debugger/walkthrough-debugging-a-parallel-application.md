---
title: Paralel uygulamada hata ayıklama | Microsoft Docs
description: Paralel Görevler ve Paralel Yığınlar pencerelerinin Visual Studio kullanarak hata ayıklama
ms.custom: ''
ms.date: 03/22/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48bcfe8ca54236fc2134d431f5f6dd16d4b82a48
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060193"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio"></a>İzlenecek yol: paralel uygulamada Visual Studio'da hata ayıklama
Bu izlenecek yolda nasıl kullanılacağını gösterir **Paralel Görevler** ve **Paralel Yığınlar** paralel uygulamada hata ayıklamak için windows. Bu windows anlamanıza ve çalışma zamanı davranışı kullanan kod doğrulama Yardım [görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) veya [eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime). Bu izlenecek yol, yerleşik kesme noktaları olan örnek kodu sağlıyor. Kodları keser sonra izlenecek yolu nasıl kullanılacağını gösterir. **Paralel Görevler** ve **Paralel Yığınlar** bunu incelemek için windows.  
  
 Bu izlenecek yol bu görevleri öğretir:  
  
-   Nasıl tüm iş parçacığı çağrı yığınlarını tek bir görünümde görüntülenir.  
  
-   Listesini görüntülemek nasıl `System.Threading.Tasks.Task` uygulamanızda oluşturduğu örneklerin.  
  
-   Görev iş parçacıkları yerine gerçek çağrı yığınlarını görüntülemek nasıl.  
  
-   Koda gitmek nasıl **Paralel Görevler** ve **Paralel Yığınlar** windows.  
  
-   Nasıl windows gruplandırma, yakınlaştırma ve diğer ilgili özellikler Ölçekle başa.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda olduğunu varsayar **yalnızca kendi kodum** etkin (Bu, Visual Studio'nun daha yeni sürümlerinde varsayılan olarak etkindir). Üzerinde **Araçları** menüsünde tıklatın **seçenekleri**, genişletin **hata ayıklama** düğümünü **genel**ve ardından **etkinleştir Yalnızca benim kodum (sadece yönetilen)**. Bu özelliği ayarlamazsanız, bu izlenecek yolda kullanmaya devam edebilirsiniz, ancak sonuçlarınızı gösterilenlerden farklı olabilir.  
  
## <a name="c-sample"></a>C# örneği  
 C# örneği kullanıyorsanız, bu kılavuzda Ayrıca Dış kod gizlidir varsayılır. Dış kod görüntülenip görüntülenmeyeceğini geçiş yapmak için sağ **adı** tablo üstbilgisinin **çağrı yığını** penceresinde ve sonra seçin veya temizleyin **harici kodu Göster**. Bu özelliği ayarlamazsanız, bu izlenecek yolda kullanmaya devam edebilirsiniz, ancak sonuçlarınızı gösterilenlerden farklı olabilir.  
  
## <a name="c-sample"></a>C++ örnek  
 C++ örnek kullanırsanız, bu konudaki dış kod başvurularını yoksayabilirsiniz. Dış kod yalnızca C# örneği için geçerlidir.  
  
## <a name="illustrations"></a>Çizimler  
 Bu konudaki resimler, C# örneği çalıştıran bir dört çekirdekli bilgisayarda kaydedilmiş. Bu izlenecek yolu tamamlamak için diğer yapılandırmalar kullanabilirsiniz, ancak çizimler bilgisayarınızda görüntülenen öğesinden farklı olabilir.  
  
## <a name="creating-the-sample-project"></a>Örnek Proje oluşturma  
 Bu kılavuzda örnek kod, hiçbir şey yapmaz bir uygulamadır. Yalnızca araç pencereleri paralel uygulamada hata ayıklamak için nasıl kullanılacağını anlamak için hedeftir.  
  
#### <a name="to-create-the-sample-project"></a>Örnek proje oluşturmak için  
  
1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.  
  
2. Şunlardan birini seçin **Visual C#**, **Visual Basic**, veya **Visual C++**. Yönetilen diller için emin [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] framework kutusunda görüntülenir.  
  
3. Altında **Windows Masaüstü**, seçin **konsol uygulaması** ve ardından **Tamam**. Varsayılan hata ayıklama yapılandırmasında kalır.  
  
4. Projede .cpp, .cs veya .vb kod dosyasını açın. Boş bir kod dosyası oluşturmak için içeriğini silin.  
  
5. Aşağıdaki kod, seçtiğiniz dilde için boş bir kod dosyasına yapıştırın.  
  
   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]  
  
6. Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet**.  
  
7. Üzerinde **derleme** menüsünde tıklatın **çözümü yeniden derle**.  
  
    Dört çağrıları olduğunu fark `Debugger.Break` (`DebugBreak` C++ örneğinde) bu nedenle, kesme noktaları eklemek gerekmez; yalnızca uygulamayı çalıştıran neden olur, en fazla dört kez hata ayıklayıcıda ayırmak.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Kullanarak Paralel Yığınlar penceresi: iş parçacıkları görünümü  
 Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**. İlk kesme noktasına isabet tamamlanmasını bekleyin.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Tek bir iş parçacığı çağrı yığınını görüntülemek için  
  
1.  Üzerinde **hata ayıklama** menüsünde **Windows** ve ardından **iş parçacıkları**. Dock **iş parçacıkları** penceresinin Visual Studio'nun altındaki.  
  
2.  Üzerinde **hata ayıklama** menüsünde **Windows** ve ardından **çağrı yığını**. Dock **çağrı yığını** penceresinin altındaki Visual Studio.  
  
3.  Bir iş parçacığında çift **iş parçacıkları** geçerli hale penceresi. Sarı bir ok geçerli iş parçacığı vardır. Geçerli iş parçacığı değiştirdiğinizde, çağrı yığını görüntülenen **çağrı yığını** penceresi.  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>Paralel Yığınlar penceresini incelemek için  
  
1.  Üzerinde **hata ayıklama** menüsünde **Windows** ve ardından **Paralel Yığınlar**. Emin olun **iş parçacıkları** sol üst köşesinde kutusunda seçilir.  
  
     Kullanarak **Paralel Yığınlar** penceresinde aynı anda tek bir görünümde birden çok çağrı yığınlarını görüntüleyebilir. Aşağıdaki çizimde gösterildiği **Paralel Yığınlar** penceresi yukarıdaki **çağrı yığını** penceresi.  
  
     ![İş parçacıkları, Paralel Yığınlar penceresini görünümünde](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")  
  
     Ana iş parçacığı çağrı yığınına bir kutuda görünür ve diğer dört iş parçacığı için çağrı yığınlarını başka bir kutuya gruplandırılır. Yığın çerçevelerinin aynı yöntemi bağlamları paylaştığından dört iş parçacığı birlikte gruplandırılır; diğer bir deyişle, bunlar içinde aynı yöntemler şunlardır: `A`, `B`, ve `C`. İş parçacığı kimlikleri ve adları aynı kutu paylaşan iş parçacıklarının gelin kutunun üst bilgisiyle üzerinden görünümüne (**4 iş parçacıkları**). Geçerli iş parçacığı kalın olarak gösterilir.  
  
     ![İş parçacığı kimlikleri ve adları gösteren araç ipucu](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")  
  
     Sarı ok, geçerli iş parçacığının etkin yığın çerçevesini belirtir.
  
     Yığın çerçevelerini göstermek için ne kadar ayrıntı ayarlayabilirsiniz (**modül adlarını**, **parametre türleri**, **parametre adları**, **parametre değerlerini**, **Satır numaralarını** ve **bayt kaydırır**) içinde sağ tıklanarak **çağrı yığını** penceresi.  
  
     Bir kutu etrafındaki mavi Vurgu, geçerli iş parçacığı kutunun bir parçası olduğunu gösterir. Geçerli iş parçacığı, ayrıca araç ipucunda kalın yığın çerçevesi tarafından belirtilir. Ana iş parçacığı iş parçacıkları penceresinde çift tıklarsanız, inceleyebileceğiniz içinde mavi Vurgu **Paralel Yığınlar** penceresi buna göre hareket eder.  
  
     ![Paralel Yığınlar penceresini ana iş parçacığında vurgulanmış](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütme devam etmek için  
  
1.  İkinci kesme noktasına, üzerinde isabet kadar yürütme devam etmek için **hata ayıklama** menüsünü tıklatın **devam**. Aşağıdaki resimde ikinci bir kesme noktasında iş parçacığı ağacını gösterir.  
  
     ![Birçok dalları gösteren Paralel Yığınlar penceresini](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")  
  
     İlk kesme noktasında dört iş parçacığı tüm S.A S.C yöntemlere S.B için oluştu. Bilgilerin hala görünür olduğunu **Paralel Yığınlar** penceresi, ancak dört iş parçacığı progressed daha fazla. S.D ve ardından G.D. bunlardan birinin devamı Başka bir S.F, S.G ve S.H. devamı Diğer iki S.I ve S.J ve orada birinin devamı S.K için gittiği ve diğer dış kullanıcı dışı kod için devam.  
  
     Örneğin, kutusunun üst bilgisinin üzerinde gezdirin **1 iş parçacığı** veya **2 iş parçacığı**iş parçacığının iş parçacığı kimlikleri görmek için. İş parçacığı kimlikleri yanı sıra diğer çerçeve ayrıntılarını görmek için yığın çerçevesi gelebilirsiniz. Geçerli iş parçacığı mavi Vurgu gösterir ve geçerli iş parçacığının etkin yığın çerçevesini sarı ok gösterir.  
  
     (Satır interweaved) bez iş parçacığı simgesini çerçevesidir iş parçacığı etkin yığın çerçeveleri gösterir. İçinde **çağrı yığını** penceresinde S.B çerçeve geçiş yapmak için çift tıklayın. **Paralel Yığınlar** pencere eğri yeşil ok simgesini kullanarak geçerli iş parçacığının geçerli yığın çerçevesi gösterir.  
  
     İçinde **iş parçacıkları** penceresinde, iş parçacıkları arasında geçiş yapın ve mesajının görüntülendiğini görün Görünümü'nde **Paralel Yığınlar** penceresi güncelleştirilir.  
  
     Kısayol menüsünü kullanarak başka bir iş parçacığına veya başka bir iş parçacığının çerçeveye geçebilirsiniz **Paralel Yığınlar** penceresi. Örneğin, S.J sağ tıklayın, fareyle **için anahtar kare**ve bir komut'ye tıklayın.  
  
     ![Paralel Yığınlar yürütme yolunu](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")  
  
     S.C sağ tıklayın ve fareyle **için anahtar kare**. Komutlardan birini geçerli iş parçacığı yığın çerçevesinde belirten bir onay işareti bulunur. (Yalnızca yeşil ok taşınır) aynı iş parçacığının bu çerçeveye geçiş yapabilir veya (Mavi Vurgu, ayrıca taşınır) diğer iş parçacığına geçiş yapabilirsiniz. Aşağıdaki çizim, alt gösterir.  
  
     ![Yığınlar menüsü J geçerliyken c 2 seçeneklerle](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")  
  
     Bir yöntem bağlamı tek bir yığın çerçevesi ile ilişkili olduğunda kutusunun üst bilgiyi görüntüler **1 iş parçacığı** ve ona çift tıklayarak geçin. 1'den fazla çerçeve ile ilişkili olan bir yöntemi bağlamı çift tıklayın, ardından menüsü otomatik olarak açılır. Yöntemi bağlamları geldiğinizde sağ siyah üçgeni dikkat edin. Bu üçgen tıklayarak, kısayol menüsünü görüntüler.  
  
     Birçok iş parçacığı olan büyük uygulamalar için yalnızca bir alt kümesi iş parçacıkları üzerinde odaklanmak isteyebilirsiniz. **Paralel Yığınlar** penceresi yalnızca bayraklı iş parçacıklarını için çağrı yığınlarını görüntüleyebilir. İş parçacıklarını için kısayol menüsü veya bir iş parçacığının ilk hücrenin kullanın. 

     Araç çubuğunda **Göster bayrağı yalnızca** liste kutusunun yanındaki düğmeyi.  

     ![Paralel Yığınlar penceresini ve araç ipucu](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")  

     Şimdi, yalnızca bayraklı iş parçacığı görünür **Paralel Yığınlar** penceresi.
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Üçüncü kesme noktasına kadar yürütme devam etmek için  
  
1.  Üçüncü kesme noktasına, üzerinde isabet kadar yürütme devam etmek için **hata ayıklama** menüsünü tıklatın **devam**.  
  
     Yöntemi, birden çok iş parçacığı aynı yöntemi olan ancak yöntem çağrı yığınının başında değil, farklı kutusunda görünür. Üç iş parçacığı vardır ve üç kutularında görünen S.L geçerli kesme noktasında örnektir. R. çift tıklayın  
  
     ![Paralel Yığınlar penceresini yürütme yolu](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")  
  
     Else göründüğü görebilmeniz için S.L diğer iki kutulara kalın olduğuna dikkat edin. Görmek istiyorsanız S.L çağrısına çerçeveler ve hangi çerçeveleri, çağrıları **yöntemi görünüme Değiştir** araç çubuğunda. Yöntem görünümü aşağıdaki çizimde **Paralel Yığınlar** penceresi.  
  
     ![Paralel Yığınlar penceresini yöntemi görünümünde](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")  
  
     Nasıl diyagramda seçilen metodunda özetlenmiş ve kendi kutusunda görünümün ortasında yerleştirilmiş dikkat edin. Çağıranlar ve çağrılanlar üst ve alt görünür. Tıklayın **yöntemi görünüme Değiştir** düğmesine tekrar bu modda bırakın.  
  
     Kısayol menüsünde, **Paralel Yığınlar** penceresine ayrıca aşağıdaki sahip diğer öğeleri.  
  
    -   **Onaltılık gösterim** araç ipuçları arasında ondalık ve onaltılık sayıları değiştirir.  
  
    -   **Sembol ayarları** ilgili iletişim kutusunu açın.  
  
    -   **Kaynakta iş parçacıklarını Göster** iş parçacığı işaretçileri iş parçacıkları konumunu, kaynak kodunuzda gösterir, kaynak kodunuzdaki görünümünü değiştirir.
  
    -   **Dış Kodu Göster** kullanıcı kodunda olmasa bile tüm çerçeveleri görüntüler. Genişletme (simgeler için erişiminiz yok olduğu için soluk) ek çerçeveler uyum sağlamak için bir diyagram görmeniz için deneyin.  

2.  İçinde **Paralel Yığınlar** penceresinde emin **geçerli yığın çerçevesine otomatik Kaydır** araç çubuğunda açıktır.  

     Sahip olduğunuz büyük diyagramları ve sonraki kesme noktasına adım, geçerli iş parçacığının etkin yığın çerçevesine otomatik Kaydır görünümüne isteyebilirsiniz; diğer bir deyişle, ilk kesme noktasına isabet iş parçacığı.
  
3.  Buna devam etmeden önce **Paralel Yığınlar** penceresinde, tüm yol sola ve tüm aşağı kaydırın.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Dördüncü kesme noktasına kadar yürütme devam etmek için  
  
1.  Dördüncü kesme noktasına, üzerinde isabet kadar yürütme devam etmek için **hata ayıklama** menüsünü tıklatın **devam**.  
  
     Bildirim nasıl görünümü autoscrolled içine yerleştir. İş parçacıkları geçiş **iş parçacıkları** penceresi veya anahtar yığın çerçevelerini **çağrı yığını** penceresini açın ve bildirim nasıl görünümü her zaman doğru çerçevesine autoscrolls. Devre dışı **geçerli aracı çerçevesine otomatik Kaydır** seçenek ve farkı görüntüleyin.  
  
     **Kuşbakışı Görünüm** büyük diyagramlarda da yardımcı olur **Paralel Yığınlar** penceresi. Varsayılan olarak, **Kuşbakışı Görünüm** açıktır. Ancak, bunu arasında kaydırma çubuklarını penceresinin sağ alt köşesindeki düğmeye tıklayarak aşağıdaki çizimde gösterildiği gibi geçiş yapabilirsiniz.  
  
     ![Kuşbakışı&#45;göz Paralel Yığınlar penceresini görünümünde](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")  
  
     Kuşbakışı göz görünümü'nde, diyagram hızla kaydırmak için dikdörtgen taşıyabilirsiniz.  
  
     Diyagramın herhangi bir yönde taşımak için başka bir yolu, diyagramın boş bir alana tıklayın ve istediğiniz yere sürükleyin oluşturmaktır.  
  
     Diyagramını yakınlaştırma ve uzaklaştırma için basın ve CTRL basılı tutarak fare tekerleğini taşıyın. Alternatif olarak, araç çubuğundaki Yakınlaştır düğmesinin tıklayın ve Yakınlaştırma aracını kullanın.  
  
     Ayrıca yığını aşağıdan yukarıya yerine yukarıdan aşağı yönde tıklayarak görüntüleyebilirsiniz **Araçları** tıklayarak menüsünde **seçenekleri**ve sonra seçin veya altında seçeneğinin işaretini **hataayıklama** düğümü.  
  
2.  Üzerinde devam etmeden önce **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Durdur** son yürütme için.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Paralel Görevler penceresi ve Görevler görünümü Paralel Yığınlar penceresini kullanma  
 Devam etmeden önce önceki yordamlarını tamamlamanız önerilir.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>İlk kesme noktasına kadar uygulamayı yeniden başlatmasını isabet  
  
1.  Üzerinde **hata ayıklama** menüsünde tıklatın **hata ayıklamayı Başlat** ulaşılmasına ilk kesme noktasına için bekleyin.  
  
2.  Üzerinde **hata ayıklama** menüsünde **Windows** ve ardından **iş parçacıkları**. Dock **iş parçacıkları** penceresinin Visual Studio'nun altındaki.  
  
3.  Üzerinde **hata ayıklama** menüsünde **Windows** tıklatıp **çağrı yığını**. Dock **çağrı yığını** penceresinin altındaki Visual Studio.  
  
4.  Bir iş parçacığında çift **iş parçacıkları** penceresine yapar, geçerli. Geçerli iş parçacığı, sarı ok vardır. Geçerli iş parçacığı değiştirdiğinizde, diğer windows güncelleştirilir. Ardından, görevleri inceleyeceğiz.  
  
5.  Üzerinde **hata ayıklama** menüsünde **Windows**ve ardından **görevleri**. Aşağıdaki çizimde gösterildiği **görevleri** penceresi.  
  
     ![Dört çalışan görevler Görevler penceresinde](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")  
  
     Çalışan her görev için aynı adlı özelliği, kimliği ve konumunu (tüm çağrı yığınına sahip bir araç ipucu görüntüleyen geldiğinizde), çalışan iş parçacığının adı tarafından döndürülen Kimliğini okuyabilir. Ayrıca, altında **görev** sütun göreve geçirilen yöntemi görebilirsiniz; diğer bir deyişle, başlangıç noktası.  
  
     Herhangi bir sütunu sıralayabilirsiniz. Karakter Sırala yönünü ve sıralama sütunu gösteren dikkat edin. Sütunları sağa veya sola sürükleyerek de yeniden sıralayabilirsiniz.  
  
     Sarı ok geçerli görev gösterir. Görevler, görev çift tıklayarak veya kısayol menüsünü kullanarak geçiş yapabilirsiniz. Görevler arasında geçiş yaptığınızda, temel alınan iş parçacığı geçerli olur ve diğer windows güncelleştirilir.  
  
     El ile bir görevden diğerine geçiş yaptığınızda, sarı ok taşır, ancak beyaz bir ok yine de hata ayıklayıcının neden görev gösterir.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütme devam etmek için  
  
1.  İkinci kesme noktasına, üzerinde isabet kadar yürütme devam etmek için **hata ayıklama** menüsünü tıklatın **devam**.  
  
     Daha önce **durumu** sütun etkin olarak tüm görevler gösterilmiştir, ancak artık iki görevleri engellenir. Görevler, birçok nedenden dolayı engellenebilir. İçinde **durumu** sütun, neden engellenir öğrenmek için bekleyen görev üzerine gelin. Örneğin, aşağıdaki çizimde, 3. görev 4. görevde bekliyor.  
  
     ![Görevler penceresinde iki Bekleyen Görevler](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")  
  
     Görev 4, sırasıyla 2 göreve atanmış iş parçacığı tarafından sahip olunan bir monitörde bekliyor. (Üst bilgi satırı sağ tıklatın ve seçin **sütunları** > **iş parçacığı atama** 2. Görev iş parçacığı atama değerini görüntülemek için).
  
     ![Görev ve araç ipucu Görevler penceresinde bekleme](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")
  
     Bir görev ilk sütununda bayrağını tıklayarak çevrilmemesi **görevleri** penceresi.  
  
     Aynı hata ayıklama oturumunda farklı kesme noktaları arasındaki görevleri izlemek için veya görevleri olan çağrı yığınlarını gösterilir filtrelemek için bayrak kullanabileceğiniz **Paralel Yığınlar** penceresi.  
  
     Kullanıldığında, **Paralel Yığınlar** penceresi daha önce uygulama iş parçacığı görüntülenebilir. Görünüm **Paralel Yığınlar** penceresini tekrar ancak bu sefer uygulama görevleri görüntüleyin. Bunu seçerek **görevleri** kutusunun sol üstte. Görevler görünümü aşağıda gösterilmiştir.  
  
     ![Görevler Paralel Yığınlar penceresini görünümünde](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")  
  
     Şu anda, görev yürütemiyor olmayan iş parçacıkları Görevler görünümünde gösterilmez **Paralel Yığınlar** penceresi. Ayrıca, görevleri yürütme iş parçacığı için bazı görevler ilgili olmayan yığın çerçevelerini yığınının alt ve üst filtre uygulanır.  
  
     Görünüm **görevleri** yeniden penceresi. Sütunu için kısayol menüsünü görmek için herhangi bir sütun başlığına sağ tıklayın.  
  
     Sütun ekleme veya kaldırma için kısayol menüsünü kullanabilirsiniz. Örneğin, AppDomain sütun seçilmedi; Bu nedenle, listesinde görüntülenmez. Tıklayın **üst**. **Üst** dört görevlerden herhangi biri için değer içermeyen sütunu görünür.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Üçüncü kesme noktasına kadar yürütme devam etmek için  
  
1.  Üçüncü kesme noktasına, üzerinde isabet kadar yürütme devam etmek için **hata ayıklama** menüsünü tıklatın **devam**.  
  
     Yeni bir görev, görev 5, şu anda çalışıyor ve 4. Görev artık bekliyor. Bekleyen görev üzerine neden geldiği tarafından gördüğünüz **durumu** penceresi. İçinde **üst** sütun, bu görev 4, 5. görev üst olduğuna dikkat edin.  
  
     Üst-alt ilişkisi daha iyi görselleştirme için sütun üst bilgi satırı sağ tıklayın ve ardından **üst-alt Görünüm**. Aşağıdaki çizim görmeniz gerekir.  
  
     ![Üst&#45;Görevler penceresinde alt Görünüm](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")  
  
     Görev 4 ve 5. görev aynı iş parçacığı üzerinde çalıştığını fark (Göster **iş parçacığı atama** gizli ise sütunu). Bu bilgiler görüntülenmiyorsa **iş parçacıkları** penceresi; burada olduğu başka bir faydası görmesini **görevleri** penceresi. Bunu doğrulamak için görüntüleme **Paralel Yığınlar** penceresi. Görüntülediğiniz emin **görevleri**. Görev 4 ve 5 bunları çift tıklayarak bulun **görevleri** penceresi. Bunu yaptığınızda, mavi Vurgu **Paralel Yığınlar** penceresi güncelleştirilir. Araç ipuçları tarama tarafından 4 ve 5 görevleri bulabilir **Paralel Yığınlar** penceresi.  
  
     ![Görev Paralel Yığınlar penceresini görünümünde](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")  
  
     İçinde **Paralel Yığınlar** penceresinde S.P sağ tıklayın ve ardından **gitmek için iş parçacığı**. İş Parçacıkları görünümü penceresi geçer ve karşılık gelen bir çerçeve görünür. Her iki görevi aynı iş parçacığında görebilirsiniz.  
  
     ![Vurgulanan iş parçacıkları görünümünde iş parçacığı](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")  
  
     Bu görevler Görünümü'nde başka bir avantajdır **Paralel Yığınlar** karşılaştırıldığında penceresinde **iş parçacıkları** penceresi.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Dördüncü kesme noktasına kadar yürütme devam etmek için  
  
1.  Üçüncü kesme noktasına, üzerinde isabet kadar yürütme devam etmek için **hata ayıklama** menüsünü tıklatın **devam**. Tıklayın **kimliği** kimliğe göre sıralamak için sütun başlığını Aşağıdaki çizim görmeniz gerekir.  
  
     ![Paralel Yığınlar penceresini durumlarda dört görev](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")  
  
     Görev 5 tamamlandığından artık görüntülenmez. Bu durum, bilgisayarınızda değil ve kilitlenme gösterilmez, bir kez basarak adım **F11**.  
  
     Görev 3 ve 4. Görev artık birbirleri üzerinde bekleyen ve engellenir. 2. görev alt ve artık zamanlanmış 5 yeni görevleri de vardır. Zamanlanmış Görevler, kodda başlatıldı ancak henüz çalıştırmadıysanız görevlerdir. Bu nedenle, bunların **konumu** ve **iş parçacığı atama** sütunları boş.  
  
     Görünüm **Paralel Yığınlar** yeniden penceresi. Her kutusunun üst bilgisi, iş parçacığı kimlikleri ve adları gösteren bir araç ipucu yok. Görevler görünümüne geçiş **Paralel Yığınlar** penceresi. Aşağıdaki çizimde gösterildiği gibi görev kimliği, adı ve görevin durumunu görmek için bir üst bilgisinin üzerinde gelin.  
  
     ![Paralel Yığınlar penceresini üstbilgi ipucunda](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")  
  
     Görevleri sütunu örneğe göre gruplandırabilirsiniz. İçinde **görevleri** penceresinde sağ **durumu** sütun üst bilgisine tıklayın ve sonra **durumuna göre grup**. Aşağıdaki çizimde gösterildiği **görevleri** penceresi duruma göre gruplandırılır.  
  
     ![Gruplanan Görevler penceresinde görevleri](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")  
  
     Ayrıca, herhangi bir sütuna göre de gruplayabilirsiniz. Gruplandırma görevler tarafından görevlerin bir alt kümesi üzerinde odaklanabilirsiniz. Daraltılabilir her grubu, birlikte gruplanır öğelerinin sayısını sahiptir.
  
     Son özelliği **görevleri** penceresi incelemek için bir görev sağ tıkladığınızda görüntülenen kısayol menüsü.  
  
     Kısayol menüsünü görev durumuna bağlı olarak farklı komutları görüntüler. Komutlar içerebilir **kopyalama**, **Tümünü Seç**, **onaltılık gösterim**, **göreve geçiş**, **dondurma atanan İş parçacığı**, **ancak bu tüm iş parçacıklarını dondurma**, ve **atanan iş parçacığını çözme**, ve **bayrağı**.  
  
     Bir görev veya görevleri temel alınan iş parçacığını Dondur ya da atanan dışındaki tüm iş parçacıklarını dondurma. Dondurulmuş bir iş parçacığı temsil edilir **görevleri** penceresi olarak konusu **iş parçacıkları** penceresi, mavi bir *duraklatmak* simgesi.  
  
## <a name="summary"></a>Özet  
 Bu izlenecek yolda gösterilen **Paralel Görevler** ve **Paralel Yığınlar** hata ayıklayıcı, windows. Bu windows birden çok iş parçacıklı kod kullanan gerçek projelerde kullanın. C++, C# veya Visual Basic içinde yazılan paralel kod inceleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Hata ayıklayıcı temel bilgileri](../debugger/getting-started-with-the-debugger.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Paralel Programlama](/dotnet/standard/parallel-programming/index)   
 [Eşzamanlılık Çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime)   
 [Paralel Yığınlar penceresini kullanma](../debugger/using-the-parallel-stacks-window.md)   
 [Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)