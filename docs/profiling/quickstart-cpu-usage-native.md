---
title: Analiz CPU kullanım verileri (C++)
description: CPU kullanımı Tanılama Aracı'nı kullanarak C++ dilinde uygulama performansını ölçmeye
ms.custom: ''
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c4cf51a4961d6b9139d4f8fdbfd6c5df2ab0052c
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42624190"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Hızlı Başlangıç: Analiz CPU kullanım verileri, Visual Studio (C++)

Visual Studio, uygulamanızdaki performans sorunlarını analiz etmenize yardımcı olmak için çok sayıda güçlü özellikler sağlar. Bu konuda bazı temel özellikleri öğrenmek için hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımından kaynaklanan performans sorunlarını tanımlamak için aracı atacağız. Tanılama araçları, yerel/C++ geliştirme ve ASP.NET dahil olmak üzere Visual Studio .NET geliştirme için desteklenir.

Tanılama hub'ı, çok sayıda çalıştırın ve tanılama oturumunuzu yönetmek için diğer bir seçenek sunar. Varsa **CPU kullanımı** burada açıklanan aracı değil size gereksinim duyduğunuz verileri [diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) farklı türde size yardımcı olabilecek bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorunu, CPU, bellek, işleme kullanıcı Arabirimi veya ağ isteği süresi gibi dışında bir şey tarafından kaynaklanabilir. Tanılama hub'ı, çok sayıda kaydedin ve bu tür verilerin analiz etmek için diğer bir seçenek sunar.

Windows 8 ve üzeri, hata ayıklayıcısı ile profil oluşturma araçları çalıştırmak için gereklidir (**tanılama araçları** pencere). Windows 7 ve daha sonra son İnceleme aracını kullanabilirsiniz [performans Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio'da **dosya** > **yeni proje**.

2. Altında **Visual C++**, seçin **Windows Masaüstü**seçip Ortadaki bölmeden **Windows konsol uygulaması**.

    Görmüyorsanız **Windows konsol uygulaması** proje şablonu, tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu. Visual Studio Yükleyicisi'ni başlatır. Seçin **C++ ile masaüstü geliştirme** iş yükü, ardından **Değiştir**.

3. Gibi bir ad yazın **Diagnostics_Get_Started_Native** tıklatıp **Tamam**.

    Visual Studio projesi oluşturur.

4. İçinde *MyDbgApp.cpp*, aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    Bu kod (kaldırmayın `#include "stdafx.h"`):

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>
    
    //.cpp file code:
    
    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;
    
    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;
    
    int getNumber()
    {
    
        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();
    
        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here  
        // to increase CPU usage 
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }
    
    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;
    
        auto x = getNumber();    
    }
    
    int main()
    {
        std::vector<std::thread> threads;
    
        for (int i = 0; i < 10; ++i) {
    
            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }
    
        for (auto& thread : threads) {
            thread.join();
        }
    
        return 0;
    }
    ```
  
## <a name="step-1-collect-profiling-data"></a>1. adım: profil oluşturma verilerini topla 
  
1.  İlk olarak, bu kod satırı üzerinde uygulamanızda bir kesme noktası ayarlamak `main` işlevi:

    `for (int i = 0; i < 10; ++i) {`

    Bir kesme noktası cilt payını sola kod satırının tıklayarak ayarlayın.

2.  Ardından, sonunda kapanış ayracı ikinci bir kesme noktası ayarlamak `main` işlevi:

     ![Profil oluşturma için kesme noktaları ayarlayın](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "profil oluşturma kesme noktası ayarlama")

    > [!TIP]
    > İki kesme noktaları ayarlayarak veri toplamayı çözümlemek istediğiniz kod parçalarını sınırlayabilirsiniz.
  
3.  **Tanılama araçları** pencere zaten görünür değilse, bunu devre dışı bırakmış. Pencereyi ayarlayıp yeniden getirmek için tıklayın **hata ayıklama** > **Windows** > **tanılama araçlarını Göster**.

4.  Tıklayın **hata ayıklama** > **hata ayıklamayı Başlat** (veya **Başlat** araç çubuğunda veya **F5**).

     Uygulama yüklemesi tamamlandığında **özeti** Tanılama Araçları'nın görünümü görüntülenir.

5.  Seçerek hata ayıklayıcıyı duraklatılmış durumdayken, CPU kullanım verileri toplamayı etkinleştir **kayıt CPU profili**ve ardından açın **CPU kullanımı** sekmesi.

     ![Tanılama araçları, CPU profili oluşturmayı etkinleştir](../profiling/media/quickstart-cpu-usage-summary.png "tanılama araçları, CPU profili oluşturmayı etkinleştir")

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

     ![Tanılama araçları CPU kullanımı sekmesinde](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en fazla çalışmayı yapan olanlar başlayarak sırayla listelenir (çağrı sırayla olmadıklarını). Bu, uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde çift `getNumber` işlevi.

    İşlev çift tıkladığınızda **çağıran/çağrılan** görünümü sol bölmede açılır. 

    ![Tanılama araçları arayan-Aranan görünümü](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    Bu görünümünde seçili işlev hem de başlığında gösterilir **geçerli işlevin** kutusunu (`getNumber`, bu örnekte). Geçerli işlevi çağıran işleve sol altında gösterilen **işlevi çağırma**, ve geçerli işlev tarafından çağrılan tüm işlevleri gösterilir **çağrılan işlevlerin** sağdaki kutuya. (Geçerli işlevin değiştirmek için ya da kutusunu seçebilirsiniz.)

    Bu görünüm, toplam süre (ms) ve genel uygulamayı işlevi tamamlamak için gerçekleştirdiği zaman yüzdesini gösterir.

    **İşlev gövdesi** ayrıca süresi (ve zamanı yüzdesi) işlev gövdesinde harcanan süre hariç toplam miktarı harcanan içinde arama ve işlevlerin çağrılma gösterilmektedir. (Bu çizim 119 tanesi 43602 ms işlev gövdesinde harcanan ve bu işlev tarafından çağrılan diğer kod içinde kalan süreyi harcandığını). Gerçek değerler, ortamınıza bağlı olarak çok farklı olacaktır.

    > [!TIP]
    > Yüksek değerleri **işlev gövdesi** işlevin kendisi içinde bir performans engelini işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- [Bellek kullanımını analiz etme](../profiling/memory-usage.md)performans sorunlarını tanımlamak için.
- [CPU kullanımını analiz etme](../profiling/cpu-usage.md) CPU kullanım aracı hakkında daha ayrıntılı bilgiler.
- -Daha fazla bilgi için çalışan bir uygulamanın hedefleyerek veya eklenmiş bir hata ayıklayıcı olmadan CPU kullanımını analiz etme [hata ayıklama olmadan profil oluşturma verisi toplama](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) içinde [profil oluşturma araçları ile veya hata ayıklayıcı olmadan çalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Ayrıca bkz.  

 [Visual Studio profil oluşturma](../profiling/index.md)  
 [Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)
