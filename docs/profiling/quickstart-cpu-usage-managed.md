---
title: CPU kullanım verilerini (yönetilen kod için) çözümleme
description: C# ve Visual Basic CPU kullanımı Tanılama aracını kullanarak uygulama performansını ölçmeye
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 35c6fd1ea079dd95367bcb7763787f0b06839ecb
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42624221"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-managed-code"></a>Hızlı Başlangıç: Visual Studio'da (yönetilen kod için) CPU kullanım verilerini çözümleme

Visual Studio, uygulamanızdaki performans sorunlarını analiz etmenize yardımcı olmak için çok sayıda güçlü özellikler sağlar. Bu konuda bazı temel özellikleri öğrenmek için hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımından kaynaklanan performans sorunlarını tanımlamak için aracı atacağız. Tanılama araçları, yerel/C++ geliştirme ve ASP.NET dahil olmak üzere Visual Studio .NET geliştirme için desteklenir.

Tanılama hub'ı, çok sayıda çalıştırın ve tanılama oturumunuzu yönetmek için diğer bir seçenek sunar. Varsa **CPU kullanımı** burada açıklanan aracı değil size gereksinim duyduğunuz verileri [diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) farklı türde size yardımcı olabilecek bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorunu, CPU, bellek, işleme kullanıcı Arabirimi veya ağ isteği süresi gibi dışında bir şey tarafından kaynaklanabilir. Tanılama hub'ı, çok sayıda kaydedin ve bu tür verilerin analiz etmek için diğer bir seçenek sunar.

Windows 8 ve üzeri, hata ayıklayıcısı ile profil oluşturma araçları çalıştırmak için gereklidir (**tanılama araçları** pencere). Windows 7 ve daha sonra son İnceleme aracını kullanabilirsiniz [performans Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio'da **dosya** > **yeni proje**.

2. Altında **Visual C#** veya **Visual Basic**, seçin **Windows Masaüstü**seçip Ortadaki bölmeden **konsol uygulaması (.NET Framework)**.

    Görmüyorsanız **konsol uygulaması** proje şablonu, tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu. Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET masaüstü geliştirme** iş yükü, ardından **Değiştir**.

3. Gibi bir ad yazın **MyProfilerApp** tıklatıp **Tamam**.

    Visual Studio projesi oluşturur.

2. Açık *Program.cs* tüm kodu aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Visual Basic'te, Başlangıç nesnesi ayarlandığından emin olun `Sub Main` (**özellikleri** > **uygulama** > **Başlangıç nesnesi**).

##  <a name="step-1-collect-profiling-data"></a>1. adım: profil oluşturma verilerini topla

1.  İlk olarak, bu kod satırı üzerinde uygulamanızda bir kesme noktası ayarlamak `Main` işlevi:

    `for (int i = 0; i < 200; i++)`

    veya Visual Basic için:

    `For i As Integer = 0 To 199`

    Bir kesme noktası cilt payını sola kod satırının tıklayarak ayarlayın.

2.  Ardından, sonunda kapanış ayracı ikinci bir kesme noktası ayarlamak `Main` işlevi:

     ![Profil oluşturma için kesme noktaları ayarlayın](../profiling/media/quickstart-cpu-usage-breakpoints.png "profil oluşturma kesme noktası ayarlama")

    > [!TIP]
    > İki kesme noktaları ayarlayarak veri toplamayı çözümlemek istediğiniz kod parçalarını sınırlayabilirsiniz.

3.  **Tanılama araçları** pencere zaten görünür değilse, bunu devre dışı bırakmış. Pencereyi ayarlayıp yeniden getirmek için tıklayın **hata ayıklama** > **Windows** > **tanılama araçlarını Göster**.

4.  Tıklayın **hata ayıklama** > **hata ayıklamayı Başlat** (veya **Başlat** araç çubuğunda veya **F5**).

     Uygulama yüklemesi tamamlandığında **özeti** Tanılama Araçları'nın görünümü görüntülenir.

5.  Seçerek hata ayıklayıcıyı duraklatılmış durumdayken, CPU kullanım verileri toplamayı etkinleştir **kayıt CPU profili**ve ardından açın **CPU kullanımı** sekmesi.

     ![Tanılama araçları, CPU profili oluşturmayı etkinleştir](../profiling/media/quickstart-cpu-usage-summary.png "tanılama araçları, CPU profili oluşturmayı etkinleştir")

     Veri toplama etkinleştirilirse, Kaydet düğmesinin kırmızı bir daire görüntüler.

     Seçeneğini belirlediğinizde **kayıt CPU profili**, Visual Studio, işlevlerinizin kaydı başlayacak ve aldıkları yürütmek için ne kadar süre ve örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Uygulamanız bir kesme noktasında durdurulur, yalnızca bu toplanan verileri görüntüleyebilirsiniz.

6.  Tuşuna **F5** , ikinci bir kesme noktasına uygulamayı çalıştırmak için.

     Şimdi, artık performans verileri bölge için özellikle uygulamanız iki kesme noktaları arasında çalışan kod için var.

     Profil Oluşturucu, iş parçacığı veri hazırlama başlar. Bitmesini bekleyin.

     CPU kullanımı aracı raporda görüntüler **CPU kullanımı** sekmesi.

     Bu noktada, verileri çözümlemek başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. adım: CPU kullanım verilerini çözümleme

CPU kullanımı altında işlevler listesini inceleyerek, en fazla çalışmayı yapan işlevleri tanımlama ve ardından her birine daha yakından bakalım alma verilerinizi analiz etmeye başlamanızı öneririz.

1. İşlev listesinde, en fazla çalışmayı yapan işlevler inceleyin.

     ![Tanılama araçları CPU kullanımı sekmesinde](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en fazla çalışmayı yapan olanlar başlayarak sırayla listelenir (çağrı sırayla olmadıklarını). Bu, uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde çift `ServerClass::GetNumber` işlevi.

    İşlev çift tıkladığınızda **çağıran/çağrılan** görünümü sol bölmede açılır.

    ![Tanılama araçları arayan-Aranan görünümü](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    Bu görünümünde seçili işlev hem de başlığında gösterilir **geçerli işlevin** kutusunu (`GetNumber`, bu örnekte). Geçerli işlevi çağıran işleve sol altında gösterilen **işlevi çağırma**, ve geçerli işlev tarafından çağrılan tüm işlevleri gösterilir **çağrılan işlevlerin** sağdaki kutuya. (Geçerli işlevin değiştirmek için ya da kutusunu seçebilirsiniz.)

    Bu görünüm, toplam süre (ms) ve genel uygulamayı işlevi tamamlamak için gerçekleştirdiği zaman yüzdesini gösterir.

    **İşlev gövdesi** ayrıca süresi (ve zamanı yüzdesi) işlev gövdesinde harcanan süre hariç toplam miktarı harcanan içinde arama ve işlevlerin çağrılma gösterilmektedir. (Bu örnekte, 2856 2863 ms dışında işlev gövdesi ve kalan zaman harcanan (< 20 ms) Bu işlev tarafından çağırılan dış kod harcandığını). Gerçek değerleri ortamınıza bağlı olarak farklı olacaktır.

    > [!TIP]
    > Yüksek değerleri **işlev gövdesi** işlevin kendisi içinde bir performans engelini işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- [Bellek kullanımını analiz etme](../profiling/memory-usage.md)performans sorunlarını tanımlamak için.
- [CPU kullanımını analiz etme](../profiling/cpu-usage.md) CPU kullanım aracı hakkında daha ayrıntılı bilgiler.
- -Daha fazla bilgi için çalışan bir uygulamanın hedefleyerek veya eklenmiş bir hata ayıklayıcı olmadan CPU kullanımını analiz etme [hata ayıklama olmadan profil oluşturma verisi toplama](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) içinde [profil oluşturma araçları ile veya hata ayıklayıcı olmadan çalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio profil oluşturma](../profiling/index.md)
- [Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)