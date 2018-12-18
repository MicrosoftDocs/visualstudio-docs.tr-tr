---
title: CPU kullanım verilerini (ASP.NET) çözümleme
description: CPU kullanımı Tanılama Aracı'nı kullanarak ASP.NET uygulamalarında uygulama performansını ölçmeye
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
- aspnet
ms.openlocfilehash: 4d4f2382814cabbd26f93db27301ffa9b8d1c658
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42624159"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Hızlı Başlangıç: CPU kullanım verileri, Visual Studio (ASP.NET) çözümleme

Visual Studio, uygulamanızdaki performans sorunlarını analiz etmenize yardımcı olmak için çok sayıda güçlü özellikler sağlar. Bu konuda bazı temel özellikleri öğrenmek için hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımından kaynaklanan performans sorunlarını tanımlamak için bir aracı atacağız. Tanılama araçları, yerel/C++ geliştirme ve ASP.NET dahil olmak üzere Visual Studio .NET geliştirme için desteklenir.

Tanılama hub'ı, çok sayıda çalıştırın ve tanılama oturumunuzu yönetmek için diğer bir seçenek sunar. Varsa **CPU kullanımı** burada açıklanan aracı değil size gereksinim duyduğunuz verileri [diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) farklı türde size yardımcı olabilecek bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorunu, CPU, bellek, işleme kullanıcı Arabirimi veya ağ isteği süresi gibi dışında bir şey tarafından kaynaklanabilir.

Windows 8 ve üzeri, hata ayıklayıcısı ile profil oluşturma araçları çalıştırmak için gereklidir (**tanılama araçları** pencere). Windows 7 ve daha sonra son İnceleme aracını kullanabilirsiniz [performans Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio'da **dosya** > **yeni proje**.

1. Altında **Visual C#**, seçin **Web**seçip Ortadaki bölmeden **ASP.NET Web uygulaması (.NET Framework)**.

    Görmüyorsanız **ASP.NET Web uygulaması** proje şablonu, tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu. Visual Studio Yükleyicisi'ni başlatır. Seçin **ASP.NET ve web geliştirme** iş yükü, ardından **Değiştir**.

1. Gibi bir ad yazın **MyProfilingApp_MVC** tıklatıp **Tamam**.

1. Görünen iletişim kutusunda **MVC** orta bölmesinde ve ardından **Tamam**.

    Visual Studio projesi oluşturur. Çözüm Gezgini (sağ bölme), proje dosyaları gösterir.

1. Çözüm Gezgini'nde, modeller klasörü sağ tıklatın ve seçin **Ekle** > **sınıfı**.

1. Yeni bir sınıf adı `Data.cs` ve **Ekle**.

1. Çözüm Gezgini'nde açın `Models/Data.cs` ve aşağıdakileri ekleyin `using` deyimini dosyanın en üstüne:

    ```csharp
    using System.Threading;
    ```

1. Aşağıdaki kod Data.cs değiştirin:

    ```csharp
    public class Data
    {
    }
    ```

    Bu kod ile:

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
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
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. Çözüm Gezgini'nde açın *Controller/HomeControllers.cs*, aşağıdaki kodu değiştirin:

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    Bu kod ile:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

##  <a name="step-1-collect-profiling-data"></a>1. adım: profil oluşturma verilerini topla 
  
1.  İlk olarak, bu kod satırı üzerinde uygulamanızda bir kesme noktası ayarlamak `Simple` Oluşturucusu:

    `for (int i = 0; i < 200; i++)`

    Bir kesme noktası cilt payını sola kod satırının tıklayarak ayarlayın.

1.  Ardından, sonunda kapanış ayracı ikinci bir kesme noktası ayarlamak `Simple` Oluşturucusu:

     ![Profil oluşturma için kesme noktaları belirleyin](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > İki kesme noktaları ayarlayarak veri toplamayı çözümlemek istediğiniz kod parçalarını sınırlayabilirsiniz.
  
1.  **Tanılama araçları** pencere zaten görünür değilse, bunu devre dışı bırakmış. Pencereyi ayarlayıp yeniden getirmek için tıklayın **hata ayıklama** > **Windows** > **tanılama araçlarını Göster**.

1.  Tıklayın **hata ayıklama** > **hata ayıklamayı Başlat** (veya **Başlat** araç çubuğunda veya **F5**).

1.  Uygulama yükleme bittiğinde, bilgisayarınızı **hakkında** yeni kod çalıştırmaya başlamak için web sayfasının üstündeki bağlantısı.

1.  Bakmak **özeti** Tanılama Araçları'nın görünümü görüntülenir.

1.  Seçerek hata ayıklayıcıyı duraklatılmış durumdayken, CPU kullanım verileri toplamayı etkinleştir **kayıt CPU profili**ve ardından açın **CPU kullanımı** sekmesi.

     ![Tanılama araçları, CPU profili oluşturmayı etkinleştir](../profiling/media/quickstart-cpu-usage-summary.png)

     Veri toplama etkinleştirilirse, Kaydet düğmesinin kırmızı bir daire görüntüler.

     Seçeneğini belirlediğinizde **kayıt CPU profili**, Visual Studio, işlevlerinizin kaydı başlayacak ve aldıkları yürütmek için ne kadar süre ve örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Uygulamanız bir kesme noktasında durdurulur, yalnızca bu toplanan verileri görüntüleyebilirsiniz.

6.  Uygulamayı, ikinci bir kesme noktasına kadar çalıştırmak için F5'e basın.

     Şimdi, artık performans verileri bölge için özellikle uygulamanız iki kesme noktaları arasında çalışan kod için var.

     Profil Oluşturucu, iş parçacığı veri hazırlama başlar. Bitmesini bekleyin.
  
     CPU kullanımı aracı raporda görüntüler **CPU kullanımı** sekmesi.

     Bu noktada, verileri çözümlemek başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. adım: CPU kullanım verilerini çözümleme

CPU kullanımı altında işlevler listesini inceleyerek, en fazla çalışmayı yapan işlevleri tanımlama ve ardından her birine daha yakından bakalım alma verilerinizi analiz etmeye başlamanızı öneririz.

1. İşlev listesinde, en fazla çalışmayı yapan işlevler inceleyin.

     ![Tanılama araçları CPU kullanımı sekmesi](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > İşlevler, en fazla çalışmayı yapan olanlar başlayarak sırayla listelenir (çağrı sırayla olmadıklarını). Bu, uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde çift `MyProfilingApp_MVC.Models.ServerClass::GetNumber` işlevi.

    İşlev çift tıkladığınızda **çağıran/çağrılan** görünümü sol bölmede açılır. 

    ![Arayan/Aranan görünümü tanılama araçları](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    Bu görünümünde seçili işlev hem de başlığında gösterilir **geçerli işlevin** kutusunu (`ServerClass::GetNumber`, bu örnekte). Geçerli işlevi çağıran işleve sol altında gösterilen **işlevi çağırma**, ve geçerli işlev tarafından çağrılan tüm işlevleri gösterilir **çağrılan işlevlerin** sağdaki kutuya. (Geçerli işlevin değiştirmek için ya da kutusunu seçebilirsiniz.)

    Bu görünüm, toplam süre (ms) ve genel uygulamayı işlevi tamamlamak için gerçekleştirdiği zaman yüzdesini gösterir.

    **İşlev gövdesi** ayrıca süresi (ve zamanı yüzdesi) işlev gövdesinde harcanan süre hariç toplam miktarı harcanan içinde arama ve işlevlerin çağrılma gösterilmektedir. (Bu örnekte, 2220 2235 ms dışında işlev gövdesi ve kalan zaman harcanan (< 20 ms) Bu işlev tarafından çağırılan dış kod harcandığını). Gerçek değerleri ortamınıza bağlı olarak farklı olacaktır.

    > [!TIP]
    > Yüksek değerleri **işlev gövdesi** işlevin kendisi içinde bir performans engelini işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- [Bellek kullanımını analiz etme](../profiling/memory-usage.md)performans sorunlarını tanımlamak için.
- [CPU kullanımını analiz etme](../profiling/cpu-usage.md) CPU kullanım aracı hakkında daha ayrıntılı bilgiler.
- -Daha fazla bilgi için çalışan bir uygulamanın hedefleyerek veya eklenmiş bir hata ayıklayıcı olmadan CPU kullanımını analiz etme [hata ayıklama olmadan profil oluşturma verisi toplama](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) içinde [profil oluşturma araçları ile veya hata ayıklayıcı olmadan çalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Ayrıca bkz.  

 [Visual Studio profil oluşturma](../profiling/index.md)  
 [Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)
