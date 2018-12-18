---
title: Çok iş parçacıklı uygulamalarda hata ayıklamayı öğrenin
description: Paralel Yığınlar ve paralel izleme Visual Studio kullanarak hata ayıklama
ms.custom: H1HackMay2017
ms.date: 11/16/2018
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
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a6ded522a917dd7207da7731850303535e19fdb
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948991"
---
# <a name="get-started-debugging-multithreaded-applications"></a>Çok iş parçacıklı uygulamalarda hata ayıklamaya başlama
Visual Studio, çeşitli araçları ve çok iş parçacıklı uygulamalarda hata ayıklamanıza yardımcı olmak için kullanıcı arabirimi öğeleri sağlar. Bu öğreticide, iş parçacığı işaretçileri kullanmak gösterilir **Paralel Yığınlar** penceresinde **paralel izleme** pencere, koşullu kesme noktaları ve filtre kesme noktaları. Bu öğreticiyi tamamlamak, hata ayıklama çok iş parçacıklı uygulamalar için Visual Studio özellikleriyle alışmanızı.

| | |
|---------|---------|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [Bir video izleyin](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) benzer adımları gösteren çok iş parçacıklı hata ayıklama. |

Bu 2 konu diğer birden çok iş parçacıklı hata ayıklama araçları kullanma hakkında ek bilgiler sağlar:

- Kullanılacak **hata ayıklama konumu** araç ve **iş parçacıkları** penceresinde görmek [izlenecek yol: birden çok iş parçacıklı bir uygulamada hata ayıklama](../debugger/how-to-use-the-threads-window.md).

- Kullanan bir örnek için <xref:System.Threading.Tasks.Task> (yönetilen kod) ve Eşzamanlılık Çalışma zamanı (C++) [izlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md). En çok iş parçacıklı uygulama türleri için geçerli olan genel hata ayıklama ipuçları için bu konuda hem de bunu okuyun.
  
Öncelikle, bir çok iş parçacıklı bir uygulama projesi de gerekir. Bir örnek aşağıda verilmiştir.  
  
## <a name="create-a-multithreaded-app-project"></a>Çok iş parçacıklı uygulaması projesi oluşturma  
  
1.  Üzerinde **dosya** menüsünde **yeni** > **proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Bir dil seçin: **Visual C#** , **Visual C++**, veya **Visual Basic**.  
  
3.  Altında **Windows Masaüstü**, seçin **konsol uygulaması**.  
  
4.  İçinde **adı** MyThreadWalkthroughApp girin.  
  
5.  Seçin **Tamam**.  
  
     Yeni bir konsol projesi görünür. Proje oluşturulduktan sonra bir kaynak dosyası görüntülenir. Seçtiğiniz dile bağlı olarak, kaynak dosyası olarak adlandırılabilir *Program.cs*, *MyThreadWalkthroughApp.cpp*, veya *Module1.vb*.  
  
6.  Kaynak dosyada kod silin ve aşağıda listelendiği uygun örnek kod ile değiştirin.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  Üzerinde **dosya** menüsünde **Tümünü Kaydet**.  
  
## <a name="debug-the-multithreaded-app"></a>Çok iş parçacıklı uygulamaların hatalarını ayıklama  
  
1. Kaynak Kod Düzenleyicisi'nde, aşağıdaki kod parçacıkları birini arayın: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Sol tıklatma sol cilt payını `Thread.Sleep` veya `this_thread::sleep_for` deyimini yeni bir kesme noktası ekleyin.  
  
    Kanalda, kırmızı bir daire bu konumda bir kesme noktasının ayarlandığını gösterir. 
  
2. Üzerinde **hata ayıklama** menüsünde **hata ayıklamayı Başlat** (**F5**).  
  
    Visual Studio çözümü oluşturur, uygulamayı hata ayıklayıcısı ekli çalıştırmaya başladığında ve uygulama kesme noktasında durur.  
  
3. Kaynak Kod Düzenleyicisi'nde kesme noktasını içeren satırı bulun.
  
### <a name="ShowThreadsInSource"></a>İş parçacığı işaret keşfedin  

1.  Hata ayıklama araç seçin **kaynak iş parçacıklarını Göster** düğmesi ![kaynak iş parçacıklarını Göster](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Tuşuna **F11** hata ayıklayıcı tek satırlık bir kod ilerlemek için bir kez.
  
3.  Pencerenin sol tarafındaki cilt payını bakın. Bu satırda göreceğiniz bir *iş parçacığı işaret* simgesi ![iş parçacığı işaret](../debugger/media/dbg-thread-marker.png "ThreadMarker") bükümlü iki iş parçacığı benzer şekilde görünür. İş parçacığı işaretçisi, bir iş parçacığı bu konuma durdurulduğunu gösterir.

    Bir iş parçacığı işaret kısmen bir kesme noktası tarafından altına gizlenmiş. 
  
4.  İşaretçi iş parçacığı işaret gelin. Durdurulan her iş parçacığı için adı ve iş parçacığı kimlik numarasını belirten bir DataTip görünür. Bu durumda, muhtemelen adıdır `<noname>`. 
  
5.  Kısayol menüsünde kullanılabilir seçenekleri görmek için iş parçacığı işaret seçin.
    
### <a name="ParallelStacks"></a>İş parçacığı konumları görüntüleyin

İçinde **Paralel Yığınlar** penceresinde geçirebilirsiniz (için görev-tabanlı programlama) ve iş parçacıkları görünümü arasında Görevler görünümü ve her bir iş parçacığı için çağrı yığını bilgilerini görüntüleyebilirsiniz. Bu uygulamada iş parçacıkları görünümü kullanabiliriz.

1. Açık **Paralel Yığınlar** penceresini seçerek **hata ayıklama** > **Windows** > **Paralel Yığınlar**. Aşağıdakine benzer bir şey görmeniz gerekir. Gördüğü bilgiler, her iş parçacığı, donanım ve programlama dilini geçerli konumuna bağlı olarak farklılık gösterir.

    ![Paralel Yığınlar penceresini](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    Bu örnekte, soldan sağa doğru yönetilen kod için bu bilgiler görüyoruz:
    
    - Ana iş parçacığı (sol taraf) üzerinde durduruldu `Thread.Start`, burada bir durma noktası iş parçacığı işaret simgesiyle gösterilir ![iş parçacığı işaret](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - İki iş parçacığı girmiş `ServerClass.InstanceMethod`, biri olan geçerli iş parçacığı (sarı ok), içinde başka bir iş parçacığı tarafından durdurulduğu sırada `Thread.Sleep`.
    - Yeni bir iş parçacığı (sağdaki) de başlangıç ancak üzerinde durduruldu `ThreadHelper.ThreadStart`.

2.  Girişlere sağ **Paralel Yığınlar** penceresi kısayol menüsünde kullanılabilir seçenekleri görmek için.

    Bu sağ tıklama menülerinde çeşitli eylemleri gerçekleştirebilirsiniz, ancak bu öğretici için size bu ayrıntıları birkaçını göstereceğiz **paralel izleme** penceresi (sonraki bölümlerde).

    > [!NOTE]
    > Her iş parçacığı bilgileri görünümüyle listesini görmek için **iş parçacıkları** penceresi yerine. Bkz: [izlenecek yol: birden çok iş parçacıklı bir uygulamada hata ayıklama](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Bir değişken üzerinde bir izleme ayarlayın

1. Açık **paralel izleme** penceresini seçerek **hata ayıklama** > **Windows** > **paralel izleme**  >  **Paralel izleme 1**.

2. Gördüğünüz hücreyi `<Add Watch>` metin (veya 4 sütundaki boş üst bilgi hücresini) ve girin `data`.

    Her iş parçacığı için veri değişkeni için değerleri penceresinde görünür.

3. Gördüğünüz hücreyi `<Add Watch>` metin (veya 5 sütun üstbilgisi boş hücreye) ve girin `count`.

    Değerleri `count` her iş parçacığı için değişken penceresinde görünür. Henüz bu kadar bilgi görmüyorsanız tuşlarına basarak deneyin **F11** birkaç kez hata ayıklayıcı iş parçacıklarının yürütülmesini ilerlemek için.

    ![Paralel İzleme penceresi](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Mevcut seçenekleri görmek için penceresinde satırlardan birinin üzerinde sağ tıklayın.

### <a name="flag-and-unflag-threads"></a>İş parçacıklarını bayrakla işaretleme ve işareti geri alma  
Önemli iş parçacığı izlemek ve diğer iş parçacıklarını yok saymak için iş parçacığı işaretleyebilirsiniz.  
  
1. İçinde **paralel izleme** penceresinde basılı **Shift** anahtar ve birden çok satır seçin.

2. Sağ tıklayıp **bayrağı**.

    Tüm Seçili iş parçacıklarını işaretlenir. Artık, yalnızca bayraklı iş parçacıklarını gösterecek şekilde filtreleyebilirsiniz.
  
3.  İçinde **paralel izleme** penceresinde **yalnızca bayraklı iş parçacıklarını Göster** düğmesi ![bayraklı iş parçacıklarını Göster](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
    Yalnızca bayraklı iş parçacıklarını listesinde görünür.

    > [!TIP]
    > Bazı iş parçacıkları işaretlediğiniz sonra bir satır kod düzenleyicisinde kod sağ tıklatın ve seçin **çalıştırma bayraklı iş parçacıklarını imlece kadar**. Bayraklı iş parçacıklarını tüm kod ulaşacak seçtiğinizden emin olun. Visual Studio tarafından yürütme sırasını denetlemek kolaylaştırarak seçili bir satır kod iş parçacıklarında duraklatacaktır [dondurma ve iş parçacıklarını çözme](#bkmk_freeze).

4.  Seçin **yalnızca bayraklı iş parçacıklarını Göster** tekrar tekrar açıp kapatmak için düğme **tüm iş parçacıklarını Göster** modu.
    
5. İş parçacıklarının bayraklarını Kaldır için bir veya daha fazla bayraklı iş parçacıklarını, sağ **paralel izleme** penceresi ve select **Unflag**.

### <a name="bkmk_freeze"></a> Dondurma ve iş parçacığı yürütmeyi çözme 

> [!TIP]
> Dondurma ve çözme (askıya alma ve sürdürme) iş parçacıkları iş gerçekleştirmek sırasını denetlemek için iş parçacığı. Bu, kilitlenmeler gibi eşzamanlılık sorunları çözün ve yarış durumlarına yardımcı olabilir.
   
1.  İçinde **paralel izleme** penceresinde, seçili tüm sütunları içeren sütuna sağ tıklayıp **dondurma**.

    İkinci sütunda, her satır için bir duraklatma simgesi görünür. Duraklatma simgesi, iş parçacığı'nın dondurulmuş olup olmadığını gösterir.

2.  Diğer tüm satırlar yalnızca bir satır seçerek işaretini kaldırın.

3.  Bir satırın sağ tıklayıp **çözme**.

    Duraklatma simgesi iş parçacığı artık dondurulmuş olup olmadığını gösteren bu satırda kaybolduktan.

4.  Geçiş tuşuna basın ve Kod Düzenleyicisi **F11**. Çözülmüş iş parçacığı çalıştırır.

    Uygulama, bazı yeni iş parçacıkları de örneği. Herhangi bir yeni iş parçacığı bayrak yok ve donuk değil.

### <a name="bkmk_follow_a_thread"></a> Koşullu kesme noktaları ile tek bir iş parçacığı izleyin

Hata ayıklayıcı tek bir iş parçacığının yürütülmesini izlemek yararlı olabilir. Bunu yapmanın bir yolu, ilginizi olmayan iş parçacıklarını dondurma tarafından ' dir. Bazı senaryolarda, örneğin belirli bir hatayı yeniden oluşturmak diğer iş parçacıklarını dondurma olmadan tek bir iş parçacığı uygulamanız gerekebilir. Diğer iş parçacıklarını dondurma olmadan bir diziyi takip etmeye, ilgilendiğiniz iş parçacığı üzerinde kod parçalamak kaçınmalısınız. Bunu ayarlayarak yapabilirsiniz bir [koşullu kesme noktası](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

İş parçacığı adı veya iş parçacığı kimliği gibi farklı koşullar üzerinde kesme noktaları ayarlayın Hale gelmesi için her bir iş parçacığı benzersiz bildiğiniz verileri koşul ayarlamaya yardımcı olur. Bazı belirli veri değeri belirli herhangi bir iş parçacığı daha ilgi olduğu bir yaygın hata ayıklama senaryosuna budur.

1. Daha önce oluşturduğunuz kesme noktasına sağ tıklayıp **koşullar**.

2. İçinde **kesme noktası ayarları** penceresinde girin `data == 5` koşullu ifade.

    ![Koşullu kesme noktası](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Ardından belirli bir iş parçacığında fazla ilgileniyorsanız, bir iş parçacığı adı veya iş parçacığı kimliği koşul için kullanın. Bunu yapmak için **kesme noktası ayarları** penceresinde **filtre** yerine **koşullu ifade**ve filtre ipuçlarını izleyin. İş parçacığı kimlikleri değiştikçe hata ayıklayıcıyı başlattığınızda, uygulama kodunuz, iş parçacığı adı isteyebilirsiniz.

3. Kapat **kesme noktası ayarları** penceresi.

4. Yeniden başlatma seçin ![yeniden uygulama](../debugger/media/dbg-tour-restart.png "RestartApp") hata ayıklama oturumunuzu yeniden başlatmak için.

    Koda veri değişken değerini 5 olduğu iş parçacığında Kes. İçinde **paralel izleme** penceresi, geçerli hata ayıklayıcı bağlam gösteren sarı ok arayın.

5. Kod üzerinde Adım şimdi (**F10**) ve kod içine Adımlama (**F11**) ve çoklu iş parçacığının yürütülmesini izleyin.

    Kesme noktası koşulu iş parçacığına benzersizdir ve hata ayıklayıcı (bunları devre dışı bırakmanız gerekebilir) diğer iş parçacıkları üzerinde diğer herhangi bir kesme noktası isabet etmez sürece, kod üzerinde adım ve diğer iş parçacıkları için geçmeden kodda ilerleyebilmeniz.

    > [!NOTE]
    > Hata ayıklayıcı geçildiğinde, tüm iş parçacıklarının çalışacağı. Ancak, diğer iş parçacıklarından biri bir kesme noktasına denk gelir sürece diğer iş parçacıkları üzerinde koda hata ayıklayıcı kesme olmaz. 
  
## <a name="see-also"></a>Ayrıca bkz.  
[Çok iş parçacıklı uygulamaların hatalarını ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)  
[Nasıl yapılır: Hata ayıklarken başka bir iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
[Nasıl yapılır: paralel yığını penceresini kullanma](../debugger/using-the-parallel-stacks-window.md)  
[Nasıl yapılır: Paralel İzleme penceresini kullanma](../debugger/how-to-use-the-parallel-watch-window.md)  
