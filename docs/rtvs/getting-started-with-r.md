---
title: R öğreticiyle çalışmaya başlama
description: Kod düzenleme ve hata ayıklama projesi oluşturma, etkileşimli pencerenin dahil olmak üzere Visual Studio'da R kullanmaya yönelik bir kılavuz.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 88387485b952bf201a222741a6b3d02861df186c
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238452"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Visual Studio için R araçları kullanmaya başlayın

R araçları Visual Studio (yüklü için RTVS'yi) aldıktan sonra (bkz [yükleme](installing-r-tools-for-visual-studio.md)), bu araçları sağlayan deneyimi denemek hızlıca elde edebilirsiniz. 

## <a name="create-an-r-project"></a>Bir R projesi oluşturma

1. Visual Studio'yu başlatın.
1. Seçin **dosya** > **yeni** > **proje** (**Ctrl**+**Shift** + **N**)
1. "R" altındaki projenizi **şablonları** > **R**, projeye bir ad ve konum verin ve seçin **Tamam**:

   ![R (vs2017 RTVS) Visual Studio'da yeni proje iletişim kutusu](media/getting-started-01-new-project.png)

1. Proje oluşturulduktan sonra aşağıdaki windows bakın:

    - Visual Studio Çözüm Gezgini'nde projenizi içeren bir iç gördüğünüz, sağ tarafta olduğunu *çözüm*. (Çözümleri, projeleri farklı türde herhangi bir sayıda içerebilir; bkz [projeleri](r-projects-in-visual-studio.md) Ayrıntılar için.
    - Sol Üstten yeni bir R dosyadır (`script.R`), Visual Studio'nun tüm kaynak kodu düzenleyebileceğiniz düzenleme özellikleri.
    - Sol altta bulunan **R etkileşimli** , etkileşimli geliştirme ve test kod penceresi.

> [!Note]
> Kullanabileceğiniz **R etkileşimli** farklı proje türü yüklendiğinde herhangi bir projeyi açın ve şunu bile kalmadan penceresi. Yalnızca select **R Araçları** > **Windows** > **R etkileşimli** dilediğiniz zaman.

## <a name="explore-the-interactive-window-and-intellisense"></a>IntelliSense ve etkileşimli pencere keşfedin

1. Yazarak etkileşimli pencereye çalışma test `3 + 4` ardından **Enter** sonuçları görmek için:

    ![Visual Studio 2017'den (VS2017) R etkileşimli penceresi](media/getting-started-02-interactive1.png)

1. Biraz daha karmaşık, giriş `ds <- c(1.5, 6.7, 8.9) * 1:12`yazıp enter `ds` sonuçları görmek için:

    ![Visual Studio'da R için ek etkileşimli örneği](media/getting-started-03-interactive2.png)

1. Yazın `mean(ds)` ancak yazdığınız hemen sonra dikkat `m` veya `me`, Visual Studio IntelliSense otomatik tamamlama seçenekleri sağlar. İstediğiniz tamamlama listesinde seçildiğinde basın **sekmesini** ; eklemek için ok tuşlarını veya fare seçimi değiştirebilirsiniz.

    ![Kod girerken görünen IntelliSense](media/getting-started-04-intellisense1.png)

1. Tamamladıktan sonra `mean`, açılış parantezi `(` ve nasıl IntelliSense, satır içi Yardım işlevi verir dikkat edin:

    ![Bir işlev için Yardım'ı gösteren IntelliSense](media/getting-started-05-intellisense2.png)

1. Satır tamamlamak `mean(ds)` ve sonuçları görmek için Enter tuşuna basın (`[1] 39.51667`).

1. Etkileşimli pencere şekilde girme konusunda yardıma ile tümleşiktir `?mean` görüntüler bu işlev için Yardım **R yardımcı** Visual Studio'daki. Ayrıntılar için bkz [Visual Studio için R Araçları'nda Yardım](getting-started-help.md).

    ![Visual Studio'da R Yardım penceresi](media/getting-started-06-help.png)

1. Gibi bazı komutlar `plot(1:100)`, çıkış doğrudan etkileşimli pencerede görüntülendiğinde, Visual Studio'da yeni bir pencere aç:

    ![Visual Studio'da bir çizim görüntüsü](media/getting-started-07-plot-window.png)

Etkileşimli pencere geçmişini gözden geçirin, yükleme ve çalışma alanlarını kaydetme, bir hata ayıklayıcıyı iliştirmek ve kopyala-yapıştır kullanmak yerine, kaynak kodu dosyaları ile etkileşim sağlar. Bkz: [R etkileşimli pencere ile çalışma](interactive-repl-for-r-in-visual-studio.md) Ayrıntılar için.

## <a name="experience-code-editing-features"></a>Deneyimi kod düzenleme özellikleri

Ayrıca Kod Düzenleyicisi'nde çalışan temel düzenleme özelliklerine IntelliSense gibi etkileşimli penceresiyle kısaca gösterir. Önce aynı kodu girerseniz, aynı otomatik tamamlama ve IntelliSense istemleri, ancak çıkış görürsünüz.

Kod yazmada bir *. R* dosyasını tek seferde tüm kodunuzu görmenizi sağlar ve küçük değişiklikler yapmak ve etkileşimli pencerede kodu çalıştırarak sonucu hızlı bir şekilde görmek kolaylaştırır. Bir projede istediğiniz sayıda dosyayı da olabilir. Kod bir dosya olduğunda da bu (Bu makalenin sonraki bölümlerinde açıklanmıştır) hata ayıklayıcı adım adım çalıştırabilirsiniz. Hesaplama algoritmaları geliştirirken ve özellikle tüm ara sonuçlar incelemek istediğinizde bir veya daha fazla veri kümeleri, işlemek için kod yazma sırada bu özellikler yararlı olur.

Örneğin, aşağıdaki adımları keşfetmek için biraz kod oluşturma [merkezi sınırı Teoremi](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). (Bu örnekte gelen uyarlanmış *R Kılavuzu* Paul Teetor tarafından.)

1. İçinde `script.R` Düzenleyicisi, aşağıdaki kodu girin:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Hızlı bir şekilde sonuçları görmek için tüm kod seçin (**Ctrl**+**A**), tuşuna **Ctrl**+**Enter** veya sağ tıklayıp **etkileşimli içinde Yürüt**. Doğrudan sonucu gösteren bir çizim pencerede yazdığınız gibi tüm seçili kodu etkileşimli pencerede çalıştırılır:

    ![Visual Studio'da bir çizim görüntüsü](media/getting-started-08-plot1.png)

1. Tek bir satır için tuşuna basarak **Ctrl**+**Enter** dilediğiniz zaman bu satırı etkileşimli pencerede çalıştırın.

> [!Tip]
> Düzenlemeleri ve basıldığında düzeni öğrenin **Ctrl**+**Enter** (veya olan her şeyi seçerek **Ctrl**+**bir** ve tuşuna basarak **Ctrl**+**Enter**) hızlı bir şekilde kod çalıştırabilir. Bunun yapılması, aynı işlemleri için fare kullanmaktan çok daha verimlidir.
> 
> Ayrıca, sürükleyin ve çizim penceresi Visual Studio çerçevenin dışında bırakın ve başka ekranınızda istediğinizde yerleştirin. Ardından istediğiniz ve bir resim veya PDF dosyasını kaydedin boyutlarına çizim pencereyi yeniden boyutlandırabilirsiniz.

1. Birkaç daha fazla satır içeren ikinci bir çizim kodu ekleyin:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Tuşuna **Ctrl**+**A** ve **Ctrl**+**Enter** aşağıdaki sonuç oluşturmayı kodu yeniden çalıştırmak için:

    ![Visual Studio'da güncelleştirilmiş çift çizimi](media/getting-started-09-plot2.png)

1. İkinci çizim için ilk çizim dikey ölçeklendirme belirler sorunudur (ile `lines`) sığmıyor. Bu sorunu düzeltmek için ayarlanacak ihtiyacımız `ylim` parametresi `plot` diyebilirsiniz, ama düzgün bir şekilde en fazla dikey değeri hesaplamak için kod eklemek ihtiyacımız olacak şekilde yapın. Bu satır satır etkileşimli pencerede yapılması olduğundan kullanışsız kullanmak için kodu yeniden düzenlemek ihtiyacımız `samp.means` çağırmadan önce `plot`. Bir kod dosyasında, ancak biz kolayca uygun düzenlemeleri yapabilirsiniz:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. **CTRL**+**A** ve **Ctrl**+**Enter** yeniden sonuçları görmek için:

    ![Visual Studio'da düzgün şekilde ölçeklendirilir, güncelleştirilmiş çift çizimi](media/getting-started-10-plot3.png)

Daha fazla Düzenleyicisi'nde yapabileceğiniz yoktur. Ayrıntılar için bkz [Düzenle R kodunu](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md), ve [kod parçacıkları](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Kodunuzdaki hataları ayıklamanıza

Anahtar güçleriyle Visual Studio hata ayıklama kullanıcı arabirimini biridir. RTVS bu güçlü bir temel üzerine oluşturur ve yenilikçi UI eklemeler [değişken Gezgini](variable-explorer.md). Burada, yalnızca hata ayıklama bir ilk bakalım.

1. Şu ana kadar kullanarak yaptığınız her şeyi temizlemek için geçerli çalışma sıfırlamasına başlamak için **R Araçları** > **oturumu** > **sıfırlama** menü komutu. Varsayılan olarak, her şeyi etkileşimli pencerede bunu daha sonra hata ayıklayıcı tarafından da kullanılır geçerli oturum tabidir. Oturum sıfırlayarak, hata ayıklama oturumu önceden var olan veri ile başladığından emin olmak. **Sıfırlama** komutu, ancak etkilemez, *betiği. R* dışında çalışma kaydedilen ve yönetilen olduğundan kaynak dosyası.

1. İle *betiği. R* ile başlayan satırında bir kesme noktası ayarlayın, önceki bölümde oluşturulan dosya `pop <-` giriş işaretini satırdaki yerleştirerek ve sonra tuşlarına basarak **F9**, veya seçerek **hata ayıklama**  >  **İki durumlu kesme noktası** menü komutu. Alternatif olarak, sol kenar boşluğu (veya cilt payını) kırmızı kesme noktası nokta göründüğü için bu satıra tıklamanız yeterlidir:

    ![Düzenleyicide bir kesme noktası ayarlama](media/getting-started-11-debug1.png)

1. Hata ayıklayıcısı ile kodda başlatma *betiği. R* seçerek ya da **kaynak başlangıç dosyası** araç çubuğu düğmesini seçerek **hata ayıklama** > **kaynak başlangıç dosyası** menü öğeleri veya tuşuna basarak **F5**. Visual Studio hata ayıklama moduna girer ve kod çalışmaya başlar. Bu, ancak Kesme noktasının ayarlandığı satırında durdurur:

    ![Visual Studio hata ayıklayıcı bir kesme noktasında durduruluyor](media/getting-started-12-debug2.png)

1. Visual Studio hata ayıklama sırasında satır kodunuzda adım adım ilerleyin olanağı sağlar. Ayrıca, İşlevler, bunları üzerinden adımla Adımlama veya bunların dışında arama bağlamı için adım. Bu özellikler, diğerlerinin yanı sıra bulunabilir **hata ayıklama** menüsü, düzenleyici ve hata ayıklama araç çubuğu sağ bağlam menüsü:

    ![Hata ayıklama Visual Studio'da araç çubuğu](media/getting-started-13-debug3.png)

1. Bir kesme noktasında durduğunda, değişkenlerin değerlerini inceleyebilirsiniz. Bulun **Otolar** penceresi Visual Studio ve adlı alt kısmında bulunan sekmesini seçin **Yereller**. **Yereller** penceresi program içinde geçerli noktadaki yerel değişkenleri gösterir. Daha önce ayarladığınız kesme noktasına durmuşsa, gördüğünüz `pop` değişken henüz tanımlı değil. Artık **hata ayıklama** > **Step Over** komut (**F10**), ve değeri görmek `pop` görünür:

    ![Visual Studio'da yerel öğeler penceresi](media/getting-started-14-debug4.png)

1. Küresel kapsam ve paket kapsamları dahil olmak üzere farklı kapsamlardaki değişkenleri incelemek için [değişken Gezgini](variable-explorer.md). Değişken Gezgini ayrıca sıralanabilir sütunları içeren bir tablo görünümüne geçiş yapmak ve verileri bir CSV dosyasına dışarı aktarma olanağı sağlar.

    ![Değişken Gezgini genişletilmiş görünümünü](media/variable-explorer-expanded-results.png)

1. Satır veya select adımlarken devam **devam** (**F5**) için tamamlama (veya sonraki kesme noktasına).

Derinliklerine için bkz: [hata ayıklama](debugging-r-in-visual-studio.md) ve [değişken Gezgini](variable-explorer.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda etkileşimli penceresini kullanarak R projeleri hakkındaki temel bilgileri öğrendiniz, kod düzenleme ve Visual Studio'da hata ayıklama. Daha fazla özellik keşfetmeye devam etmek için aşağıdaki makaleleri hem de makaleler içindekiler tablosunda gösterilen bakın:

- [Örnek Proje](getting-started-samples.md)
- [Kodu düzenleme](editing-r-code-in-visual-studio.md)
- [Hata Ayıklama](debugging-r-in-visual-studio.md)
- [Çalışma Alanları](r-workspaces-in-visual-studio.md)
- [Verileri görselleştirme](visualizing-data-with-r-in-visual-studio.md)
