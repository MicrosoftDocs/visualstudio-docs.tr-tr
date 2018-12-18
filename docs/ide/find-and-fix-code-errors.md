---
title: Program hataları düzeltin ve kod geliştirin
description: Bu makalede, Visual Studio hata ayıklama araçları ve birim testleri bulmak ve derleme hataları dahil olmak üzere, kodunuzda, kod çözümleme sorunları gidermenize yardımcı olabilir bazı temel yolları açıklanmaktadır.
ms.date: 05/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 320615daa95ba9fad69fe48490f83c19ccf8e1ce
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34065123"
---
# <a name="make-code-work-in-visual-studio"></a>Visual Studio'da iş kodu olun

Visual Studio Proje derleme ve hata ayıklama araçları güçlü tümleşik kümesi sağlar. Bu makalede, nasıl Visual Studio yardımcı olabileceğini öğrenmek için hata ayıklama araçları çıkışı, yapı kullanarak kodunuzda Kod Analizi sorunlarını bulmak ve birim testleri bulun.

Düzenleyicisi dahil edilir ve biraz kod oluşturulan. Şimdi, kod düzgün çalıştığından emin olmak istersiniz. Visual Studio'da çoğu IDE gibi ile kod iş yapmak için iki aşama vardır: yakalamak ve proje ve derleyici hataları gidermek için kod oluşturma ve çalıştırma ve dinamik hatalarını bulmak için kodu çalıştırma.

## <a name="build-your-code"></a>Kodunuzu oluşturma

Yapı yapılandırması iki temel tür vardır: **hata ayıklama** ve **sürüm**. **Hata ayıklama** yapılandırma daha zengin etkileşimli çalışma zamanı hata ayıklama için bir deneyim sağlayan daha yavaş ve daha büyük bir yürütülebilir üretir. **Hata ayıklama** yürütülebilir hiçbir zaman sevk. **Sürüm** yapılandırma sevk etmek uygun olan bir daha hızlı ve en iyi duruma getirilmiş yürütülebilir dosyası oluşturur (en az derleyici perspektifinden). Varsayılan derleme yapılandırma **hata ayıklama**.

Projenizi derleme için en kolay yolu basmaktır **F7**, ancak derleme seçerek de başlatabilirsiniz **yapı** > **yapı çözümü** ana menüden.

![Visual Studio derleme proje menüsü seçimi](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Yapı işleminde gözleyebilirsiniz **çıkış** Visual Studio kullanıcı arabirimini ekranın alt kısmındaki penceresi. Hataları, uyarıları ve yapı işlemleri burada görüntülenir. Hataları (veya yapılandırılan düzeyi uyarılar varsa) varsa, derleme başarısız oluyor. Hataları ve Uyarıları nerede oluştuğunu satıra gitme tıklatabilirsiniz. Her iki basarak projeniz yeniden **F7** yeniden (yalnızca hatalar dosyalarıyla yeniden derleyin için) veya **Ctrl**+**Alt**+**F7**  (için temiz ve eksiksiz rebuild).

Düzenleyici aşağıda Sonuçları penceresinde iki sekmeli windows vardır: **çıkış** (hata iletileri de dahil olmak üzere) çıkış; ham derleyici içeren pencere ve **hata listesi** sağlayan penceresini bir listesi tüm hataların ve uyarıların sıralanabilir ve filtrelenebilir.

Yapı başarılı olduğunda bu şekilde sonuçları görmek **çıkış** penceresi:

![Visual Studio başarılı yapı çıktısı](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Hata listesini gözden geçirin

Daha önce ve başarılı bir şekilde derledik kod değişiklik yapmış olduğunuz sürece, muhtemelen bir hata vardır. Kodlama için yeniyseniz, bunları çok sayıda'de vardır. Bazen hatalar basit söz dizimi hatası veya hatalı değişken adı gibi belirgin ve bazı durumlarda, size yol göstermesi için yalnızca bir şifreli koduyla anlaşılması güç. Sorunları temizleyici görünümü için derleme alt kısmına gidin **çıkış** penceresi ve tıklatın **hata listesi** sekmesi. Bu hataları ve Uyarıları projeniz için daha düzenli bir görünümünü sürer ve bazı ek seçenekler de sunar.

![Visual Studio çıkış ve hata listesi](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

' I tıklatın hata satırında **hata listesi** hata satırına atlamak için pencere oluşuyor. (Veya satır numaralarını tıklayarak açmak **hızlı başlatma** "satır numaralarını" içine yazarak ve basarak sağ üst, çubuğunda **Enter**. Bu almak için en hızlı yoludur **seçenekleri** Burada, açmanız satır numaralarını iletişim. Kullanmayı öğrenin **hızlı başlatma** çubuğunu ve kendiniz birçok UI tıklama kaydedin!)

![Satır numaraları ile Visual Studio Düzenleyicisi](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio satır numaralarını seçeneği](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Tuşuna **Ctrl**+**G** hatanın oluştuğu satır numarası hızla atlamak için.

Hata bir kırmızı "dalgalı çizgi" alt çizgi tarafından tanımlanır. Daha fazla ayrıntı için üzerine gelin. Düzeltme yapın ve düzeltmeler ile yeni bir hata neden olabilir ancak bu, kaybolur. (Bu bir "gerileme" olarak adlandırılır.)

![Visual Studio hata vurgulu](../ide/media/vs_ide_gs_debug_error_hover1.png)

Hata listesi yol ve kodunuzdaki tüm hataları çözün.

![Visual Studio hata ayıklama hataları penceresi](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Ayrıntılı hataları gözden geçirin

Birçok hata hiçbir derleyici şartlarında oldukları gibi tümcecik oluşturulmuş sizin için anlamlı olabilir. Bu durumda, ek bilgi gerekir. Gelen **hata listesi** penceresi, hata veya uyarı hakkında daha fazla bilgi için otomatik bir Bing arama yapabilirsiniz. Karşılık gelen giriş satırına sağ tıklatıp **hata yardımını göster** bağlam menüsünden veya köprülü hata kodu değeri tıklatın **kod** sütunu **hata listesi**.

![Visual Studio hata listesi Bing arama](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

Ayarlarına bağlı olarak, web tarayıcınızın hata kodu ve metin için arama sonuçlarını görüntüler ya da bir sekme Visual Studio içinde açılır ve Bing arama sonuçlarını gösterir. Internet üzerindeki birçok farklı kaynaktan sonuçlar olur ve tüm yararlı olabilir.

## <a name="use-code-analysis"></a>Kod çözümleme kullanın

Kod çözümleyicilerini çalışma zamanı hataları için yol açabilecek ortak kod veya sorunlarına kodu Yönetimi'nde arayın.

### <a name="c-and-visual-basic-code-analysis"></a>C# ve Visual Basic kod çözümleme

Visual Studio 2017 içeren yerleşik bir dizi [.NET derleyici platformu çözümleyiciler](../code-quality/roslyn-analyzers-overview.md) , inceleyin C# ve Visual Basic kodu yazarken. Visual Studio uzantısı olarak veya bir NuGet paketi olarak ek çözümleyiciler yükleyebilirsiniz. Kural ihlallerinin bulunursa, hem bir dalgalı soruna neden olan kod altında ve içinde olarak kod düzenleyicisinde bildirilirken **hata listesi**.

### <a name="c-code-analysis"></a>C++ kod çözümleme

C++ kodunu analiz etmek için Çalıştır [statik kod analizi](../code-quality/quick-start-code-analysis-for-c-cpp.md). Başarılı bir derlemede önlemek ve onu üretebilir uyarıları gidermek için biraz zaman belirgin hataları temizledikten sonra onu çalıştıran biri alýþkanlýk alın. Kendiniz bazı zorlukların yol aşağı kurtulmuş olursunuz ve birkaç kod stili teknikleri öğrenin.

Tuşuna **Alt**+**F11** (veya seçin **Çözümle** > **çalıştırmak Kod Analizi çözüm üzerinde** üstteki menüden) için statik kod analizi başlatın.

![Visual Studio Kod Analizi menü öğesi](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Tüm yeni veya güncelleştirilmiş uyarılar görüntülenir **hata listesi** IDE ekranın alt kısmındaki sekme. Bunları kodda atlamak için Uyarılar'ı tıklatın.

![Visual Studio hata listesi uyarılarla](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-light-bulbs-to-fix-or-refactor-code"></a>Kodu yeniden düzenleyin veya için ampuller kullanın

[Hızlı Eylemler](../ide/quick-actions.md), ampul veya tornavida simgesi kullanılabilir let kodu satır içi yeniden düzenleyin. Sık kullanılan uyarılar düzeltmek için kolay bir yol oldukları hızlı ve etkili şekilde C#, C++ ve Visual Basic kodu. Bunları erişmek için bir uyarı dalgalı sağ tıklatın ve seçin **hızlı Eylemler ve yapan yeniden düzenlemeler**. Veya imlecinizi renkli dalgalı satırıyla açık olduğunda, basın **Ctrl**+**.** Ampul veya veya tornavida simgesi kenar boşluğunda seçin. Olası düzeltmeler veya bu kod satırına uygulayabilirsiniz yapan yeniden düzenlemeler listesini görürsünüz.

![Visual Studio ampul Önizleme](../ide/media/quick-actions-options.png)

Hızlı Eylemler, düzenleme, düzeltmek veya kodunuzu iyileştirmek için bir fırsat kodu çözümleyiciler belirlemek her yerde kullanılabilir. Herhangi bir kod satırında, bağlam menüsünü açmak için sağ tıklayıp **hızlı Eylemler ve yapan yeniden düzenlemeler**. Yeniden düzenleme veya geliştirme seçenekleri varsa, bunlar görüntülenir. Aksi takdirde, ileti **hiçbir hızlı Eylemler kullanılabilir burada** IDE sol alt köşesinde görüntülenir.

![Hızlı Eylemler kullanılabilir metin yok](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Deneyim, hızlı bir şekilde ok tuşlarını kullanabilirsiniz ve **Ctrl**+**.** Denetlenecek kodunuzu kolay fırsatları yeniden düzenleme ve temiz yukarı!

## <a name="debug-your-running-code"></a>Çalışan kodda hata ayıklama

Başarıyla kodunuzu yerleşik artık ve biraz temizleme gerçekleştirilen göre çalıştırın tuşlarına basarak **F5** veya seçerek **hata ayıklama** > **hata ayıklamayı Başlat**. Ayrıntılı kendi davranış gözlenir şekilde bu bir hata ayıklama ortamında uygulamanızı başlatır. Visual Studio IDE değişiklikleri uygulamanızı çalışırken: **çıkış** penceresi (varsayılan yapılandırmasında penceresi), iki yenilerini almıştır **Yereller/otomobiller/izleme** sekmeli pencere ve **Çağrı yığını/kesme noktaları/özel durum ayarları/çıkış** sekmeli penceresi. Bu windows inceleyin ve çalışırken, uygulamanızın değişkenleri, iş parçacıkları, çağrı yığınları ve çeşitli diğer davranışlarını değerlendirmek olanak tanıyan birden fazla sekme sahip.

![Visual Studio otomobiller ve çağrı yığını Windows](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Tuşlarına basarak uygulamanızı durdurma **Shift**+**F5** veya tıklatarak **durdurmak** düğmesi. Veya, yalnızca uygulamanın ana penceresinde (veya komut satırı iletişim) kapatabilirsiniz.

Kodunuzu mükemmel çalıştırdıysanız ve tam olarak beklenen, Tebrikler! Ancak, askıda, veya kilitlendi veya bazı garip sonuçları vermiş, bu sorunların kaynağı bulmak ve hataları düzeltmek gerekir.

### <a name="set-simple-breakpoints"></a>Set basit kesme noktaları

[Kesme noktaları](../debugger/using-breakpoints.md) en temel ve temel güvenilir hata ayıklama özelliği. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız veya kod dalı çalıştırmak destekleyip desteklemediğini belirtir. Ayarlama ve kesme noktaları kaldırma sonrasında bir projeyi yeniden gerek yoktur.

Tuşuna basın veya oluşabilir sonu istediğiniz kadar boşlukta satırının tıklatarak bir kesme noktası ayarlayın **F9** geçerli kod satırında bir kesme noktası ayarlamak için. Kodunuzu çalıştırdığınızda, duraklatmak (veya *sonu*) Bu kod satırı yönergelerini yürütülmeden önce.

![Visual Studio kesme noktası](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Kesme noktaları için yaygın kullanımları şunlardır:

- Kilitlenme veya askı kaynağı daraltmak için kesme noktaları boyunca ve hataya neden olduğunu düşündüğünüz yöntem çağrısı kodunu çözmek dağılım. Hata ayıklayıcıda kod çalıştırmadan olarak kaldırın ve soruna neden olan kod satırı ile bulana kadar yakın kesme noktaları birlikte sıfırlayın. Hata ayıklayıcıda kod çalıştırmayı öğrenmek için sonraki bölüme bakın.

- Yeni kod katılırsa, bunu başında bir kesme noktası ayarlayın ve beklendiği şekilde davrandığından emin olmak için kodu çalıştırın.

- Karmaşık bir davranış uyguladık istiyorsanız, program böldüğünde değişkenleri ve veri değerlerini inceleyebilirsiniz şekilde algoritmik kodu için kesme noktaları ayarlayın.

- C veya C++ kodu, kod durdurmak için kullanım kesme noktaları bunu yazıyorsanız, bellekle ilgili hataları için hata ayıklama sırasında adres değerleri (NULL bakın) ve başvuru sayıları inceleyebilirsiniz.

Kesme noktaları kullanma hakkında daha fazla bilgi için okuma [kesme noktalarını kullanma](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Çalışma zamanında kodunuzu inceleyin.

Çalışan kodunuzu bir kesme noktası ve duraklatır geldiğinde, sarı (geçerli deyimi) olarak işaretlenmiş kod satırı henüz yürüttü değil. Bu noktada, geçerli deyimini yürütün ve sonra değiştirilmiş değerleri incelemek isteyebilirsiniz. Birkaç kullanabilirsiniz *adım* Hata Ayıklayıcısı'ndaki kod yürütmek için komutları. İşaretli kodu yöntem çağrısı ise, içine tuşlarına basarak adım **F11**. Ayrıca *üzerinden adım* basarak kod satırı **F10**. Ek komutlar ve aracılığıyla koda adım hakkında ayrıntılar için okuma [kod hata ayıklayıcısını kullanmaya gidin](../debugger/navigating-through-code-with-the-debugger.md).

![Visual Studio çalışma zamanı değeri denetleme](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Önceki çizimde, hata ayıklayıcı bir deyim ya basarak ilerletebilirsiniz **F10** veya **F11** (hiçbir yöntem çağrısı olduğundan, her iki komut aynı sonucu vardır).

Hata ayıklayıcı duraklatıldığında değişkenlerinizi inceleyebilir ve çağrı yığınları neler olduğunu belirlemek için. Değerleri görmeyi beklediğiniz aralıklardaki misiniz? Çağrılar doğru sırayla yapılır?

![Visual Studio çalışma zamanı değeri denetleme](../ide/media/vs_ide_gs_debug_inspect_value.png)

Geçerli değer ve başvuru görmek için bir değişken gelin. Beklemediğiniz bir değer görürseniz, muhtemelen önceki veya arama kodda bir hata vardır. Daha fazla hata ayıklama hakkında ayrıntılı bilgi için [daha fazla bilgi edinin](../debugger/getting-started-with-the-debugger.md) hata ayıklayıcıyı kullanma hakkında.

Ayrıca, Visual Studio görüntüler **tanılama araçları** penceresinde, burada, gözlemlemek uygulamanızın CPU ve bellek kullanımı Zamanla. Daha sonra uygulama geliştirme, beklenmeyen yoğun CPU kullanımı veya bellek ayırma için aramak için bu araçları kullanabilirsiniz. İle birlikte kullanmak **izleme** penceresini açın ve ne beklenmeyen ağır kullanımı veya yayımlanmamış kaynakları neden olduğunu belirlemek için kesme noktaları. Daha fazla bilgi için bkz: [özelliği turu profil](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Birim testleri çalıştırma

Doğru yapıldığında, bunlar tek bir kod, tek bir işlev genellikle, "Birim" test ve hata ayıklama tam programınızı kolaydır, birim testleri, ilk karşı savunma hattı kod hataları olduklarından. Visual Studio hem yönetilen hem de yerel kod için Microsoft birim test çerçevelerini yükler. Birim testleri oluşturmak, bunları çalıştırmak ve sonuçları bu testler, rapor için bir birim testi çerçevesi kullanın. Kodunuzun doğru şekilde çalışıp çalışmadığını sınamak için değişiklik yaptığınızda yeniden çalıştır birim testleri. Visual Studio Enterprise edition ile testleri otomatik olarak her derleme sonrası çalıştırabilirsiniz.

Başlamak için okuma [Intellitest ile kodunuz için birim testleri oluşturmak](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Visual Studio ve nasıl bunlar daha iyi kalite kod oluşturmanıza yardımcı olabilir birim testleri hakkında daha fazla bilgi için okuma [birim testi Temelleri](../test/unit-test-basics.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcıyı kullanma hakkında daha fazla bilgi edinin](../debugger/getting-started-with-the-debugger.md)
- [Oluşturma ve kod Düzelt](../ide/code-generation-in-visual-studio.md)