---
title: Visual Studio 2015'te hata ayıklamaya başlama | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e4366061cc6eba29f630cb51757ddc2ace58970
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066255"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Visual Studio 2015'te Hata Ayıklamaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 proje derleme ve hata ayıklama araçları, güçlü tümleşik sunmaktadır. Bu konu başlığında, en temel hata ayıklama kullanıcı Arabirimi özellikleri kümesi kullanmaya başlamak nasıl öğrenin.

 Not: Bu sayfanın alt kısmında daha gelişmiş özellikleri ve platform veya özelliğe özgü konulara bağlantılar vardır.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Benim kodumu çalışmaz. Me, Visual Studio 2015 yardımcı olun!
 Böylece düzenleyicisini verdi ve bazı kod oluşturdunuz. Artık, kod hata ayıklamayı başlatmak istediğiniz. Visual Studio 2015'te çoğu ıde'lerle gibi hata ayıklama için iki aşama vardır: yakalayın ve proje ve derleme hatalarını; kod oluşturma Bu kodu yakalamak ve çalışma zamanı ve dinamik hatalarını gidermek için ortamında ve çalıştırma.

### <a name="configuring-a-build"></a>Bir derleme yapılandırma
 İki temel tür yapı yapılandırması vardır: **hata ayıklama** ve **yayın**. İlk Yapılandırma bir daha zengin etkileşimli çalışma zamanı hata ayıklama deneyimi sağlar, ancak hiçbir zaman sevk edilmesi gereken bir yavaş, daha büyük çalıştırılabilir dosyası oluşturur. İkinci göndermeye uygun olan daha hızlı, daha en iyi duruma getirilmiş bir çalıştırılabilir derlemeleri (en az derleyici perspektifinden).

 Varsayılan yapı yapılandırma **hata ayıklama**.

 ![Visual Studio hata ayıklama derlemesi düğmesi](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Hedef, bir özel yapı platformunu gibi belirtebilirsiniz **x86** (32-bit Intel CPU'yu) **x64** (64-bit Intel CPU) ve **ARM** (ARM CPU'lar, yalnızca belirli bir uygulama için desteklenir türleri için). Varsayılan değer **x86** yönetilen ve yerel projeleri için. Değiştirmek için yapı platform üzerindeki açılır menüye tıklayın ve farklı bir platform seçin veya **Configuration Manager...**

 ![Visual Studio yapılandırma dosyası Yöneticisi penceresi](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 Hedeflenen derleme yapılandırmayla belirtebilirsiniz **Configuration Manager**. Başlatın, tıklayın **yapılandırma** veya **CPU** açılır listesinde seçip **yeni...** Yeni derleme veya platformu oluşturmak için.

 ![Visual Studio Configuration Manager penceresini](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Kullanmanız yeterlidir, başlangıç **hata ayıklama** ve **x86** derleme yapılandırması ve platformu, sırasıyla. Kodlama ve hata ayıklama işiniz bittiğinde yapılandırmayı değiştirmek **yayın** ve belirli bir platforma hedefleyebilirsiniz. (Sağlanan Visual Studio'nun eski sürümlerini bir **AnyCPU** .Net kod projeleri için varsayılan platform.)

 Not: projenizi yapılandırdığınızda, yapılandırma ve platform değerler da yürütülebilir dosya depolamak için hangi proje dizin yolu oluşturulup belirlemek için kullanılır. Bu genellikle  **\<yolu Proje >\\< proje adı >\\< yapılandırma\>\\< platform\>**. Örneğin, proje yapılandırmasıyla `Debug` ve bir platformda `x86` altında bulunabilir `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. Bu, kendi araçları veya bu yerleşik yürütülebilir dosyaları yönetme betikleriniz varsa yararlı olabilir.

### <a name="building-your-code"></a>Kod oluşturma
 Yapınızı ile yapılandırılmış, aslında derleme zamanı geldi. F7, ancak basmak için bunu yapmanın en kolay yolu da yapı seçerek başlatabilirsiniz **Yapı Çözümü Derle ->** ana menüden.

 ![Visual Studio derleme proje menü seçimini](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Derleme işleminde inceleyebileceğiniz **çıkış** Visual Studio kullanıcı Arabirimi alt kısmındaki durum penceresi. Hataları, uyarıları ve yapı işlemleri burada görüntülenir. Hata (veya yapılandırılan bir düzey bir uyarı olup olmadığını) varsa, yapınız başarısız olur. Hataları ve Uyarıları nerede oluştuğunu satıra gitmek için tıklayabilirsiniz. Projenizi yeniden derleyin ya basarak **F7** yeniden (yalnızca dosyalar hatalarla yeniden derlemek için) veya **Ctrl + Alt + F7** (için bir temiz ve tam yeniden derleme).

 Sekmeli pencerelerin Düzenleyicisi aşağıdaki sonuçları penceresinde iki yapı vardır: **çıkış** içeriyor (hata iletileri de dahil olmak üzere) çıktı; ham derleyici penceresinde ve **hata listesi** penceresinde, tüm hataları ve Uyarıları sıralanabilir ve filtrelenebilir listesini sağlar.

 Başarılı olduğunda, bu benzer bir sonuç göreceksiniz **çıkış** penceresi.

 ![Visual Studio başarılı derleme çıktı](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Hata listesini gözden geçirme
 Daha önce ve başarıyla derlenen kod için herhangi bir değişiklik yapmış olduğunuz sürece, muhtemelen bir hata vardır. Kodlamaya yeniyseniz, muhtemelen bunlardan çok fazla vardır. Hataları bazen belirgin, böyle bir basit söz dizimi hatası veya yanlış bir değişken adı ve bazı durumlarda, size yol göstermesi için yalnızca bir şifreli koduyla anlaşılması zor. Sorunların daha net bir görünüm için derleme alt kısmına gidin **çıkış** pencere seçeneğine tıklayıp **hata listesi** sekmesi. Projeniz için uyarıları ve hataları daha düzenli bir görünümünü götürür ve bazı ek seçenekler de sunar.

 ![Visual Studio 2015 çıktı ve hata listesi](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 Hata satırında tıklayın **hata listesi** penceresi ve atlama hata oluşuyor satırına. (Veya tıklayarak satır numaralarını Aç **hızlı başlatma** "numaraları içine satır" yazın ve Enter tuşuna basarak dokunun, çubuğunda. Bu ulaşmak için en hızlı yoludur **seçenekleri** Burada, kapatabilir satır numaralarını penceresi girişi. Kullanmayı öğrenme **hızlı başlatma** çubuk ve kendiniz çok sayıda UI tıklama Kaydet!)

 ![Satır numaraları ile Visual Studio Düzenleyicisi](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Visual Studio satır numaraları seçeneği](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Hatanın oluştuğu satır numarasına hızla gitmek için CTRL + g'tuşlarını kullanın.

 Hata, kırmızı bir "dalgalı çizgi" alt çizgi ile tanımlanır. Üzerinde ek detaylar için üzerine gelin. Düzeltme yapmak ve yeni bir hata düzeltmesi yükleyebilecek olsa da çalıştırmayı, geçer. (Bu bir "regresyon" olarak adlandırılır.)

 ![Visual Studio hata vurgulu](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Hata listesi izlemek ve kodunuzda tüm hatalarla ilgilenin.

 ![Visual Studio hata ayıklama hataları penceresinde](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Ayrıntılı hataları gözden geçirme
 Birçok hatayı yok, derleyicinin koşullarını oldukları gibi tümcecik oluşturulmuş mantıklı olabilir. Bu gibi durumlarda ek bilgilere ihtiyacınız olacaktır. Gelen **hata listesi** penceresi, hata (veya uyarı) ile ilgili giriş satırına sağ tıklayıp hakkında daha fazla bilgi için otomatik bir Bing arama yapabilir **hata yardımını göster** gelen bağlam menüsü.

 ![Visual Studio hata listesi Bing arama](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Bu, Visual Studio 2015 konakları bir Bing sonuçlarının hata kodu ve metin arama içinde bir sekmesinde çalıştırır. Internet'teki birçok farklı kaynaklardan sonuçları olan ve tüm yararlı olabilir.

 Alternatif olarak, köprülü hata kodu değeri tıklayabilirsiniz **kod** sütununun **hata listesi**. Bu işlem, Bing arama yalnızca hata kodunu başlatılır.

### <a name="performing-static-code-analysis"></a>Statik kod analizini gerçekleştirme
 "Statik kod analizi", "çalışma zamanı hatalarına neden olabilecek yaygın sorunlar veya kod yönetimi sorunları için kendi kodum otomatik olarak denetle" etkisine başvurmaktan bir yoludur. Derleme önleme belirgin hataları temizledikten sonra çalışan alýþkanlýk alın ve bunu üretebilir uyarıları gidermek için biraz zaman alabilir. Kendiniz yol aşağı bazı zorlukların kaydedin, hem de birkaç kod stili teknikleri öğrenin.

 Alt + F11 tuşlarına basarak (veya **analiz çözümü kod çözümlemeyi Çalıştır ->** üstteki menüden) statik kod analizi başlatmak için. Çok fazla kod varsa bu biraz zaman alabilir.

 ![Visual Studio 2015 Kod Analizi menü öğesi](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Tüm yeni veya güncelleştirilmiş uyarı görünür **hata listesi** IDE alt kısmındaki sekme. Uyarıların bunlara atlamak için tıklayın.

 ![Visual Studio 2015 hata Listesi'nde uyarılar](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Uyarıları parlak bir sarı-yeşil dalgalı kırmızı bir tane yerine ile tanımlanır. Daha fazla ayrıntı için üzerine gelin ve bunları düzeltmeleri veya yeniden düzenleme seçeneklerini yardımcı olmak için bir bağlam menüsü almak için sağ tıklayın.

 ![Visual Studio Kod Analizi uyarısı vurgulu](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Ampuller kullanarak düzeltin veya kodu yeniden düzenleyin
 Ampuller olanak tanıyan Visual Studio 2015 için yeni bir özellik olan kod satır içi yeniden düzenleyin. Genel uyarıları gidermek için kolay bir yol oldukları hızla ve etkili bir şekilde. Bunlara erişmek için bir uyarı dalgalı oku üzerinde sağ tıklayın (veya CTRL tuşuna basın. gelindiğinde dalgalı çizgi) ve ardından **hızlı Eylemler**.

 ![Visual Studio 2015 ampul hızlı seçenekleri](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Olası düzeltmeleri veya ilgili kod satırına uygulayabilirsiniz refactors listesini görürsünüz.

 ![Visual Studio 2015 ampul Önizleme](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Ampuller, kod Çözümleyicileri, yeniden düzenleme, düzeltin veya kodunuzu geliştirmek için bir fırsat olup belirlemek her yerde kullanılabilir. Herhangi bir kod satırında, bağlam menüsünü açmak için sağ tıklayın ve seçin **hızlı seçenekleri** (veya verimliliği tercih ederseniz, yeniden CTRL tuşuna basın.). Yeniden düzenleme ve geliştirme seçenekleri kullanılabilir alan ise bunlar görüntülenir; Aksi takdirde, iletinin `No quick options available here` IDE'nin sol alt köşesinde çerçeve içinde görüntülenir.

 ![Visual Studio 2015 ampul 'seçeneği' metin](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Deneyiminiz ok tuşları ve Ctrl + hızlı bir şekilde kullanabilirsiniz. için hızlı fırsatları yeniden düzenleme seçeneği işaretleyin ve kodunuzu oluşturan temizlemek için!

 Ampuller hakkında daha fazla bilgi için okuma [ampullerle hızlı eylemler gerçekleştirme](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Çalışan kodunuzun hatalarını ayıklama
 Sizin başarıyla kodunuzu derleyip biraz temizleme gerçekleştirilen göre çalıştırın F5 tuşuna basarak veya seçerek **hata ayıklama -> hata ayıklamayı Başlat**. Ayrıntılı davranışını görebilirsiniz. Bu nedenle bu bir hata ayıklama ortamında uygulamanızı başlatacak. Visual Studio 2015 IDE değişiklikleri uygulamanız çalışırken: **çıkış** penceresi (varsayılan yapılandırmasında pencere), iki yeni etiketler ile değiştirilir **Otolar/Yereller/modülleri/Watch** sekmeli pencere ve **Çağrı yığını/kesme noktaları/özel durum ayarları/çıkış** sekmeli pencere. Bu windows inceleyin ve çalıştırdığı gibi uygulamanızın değişkenleri, iş parçacıkları, çağrı yığınları ve diğer çeşitli davranışların değerlendirme olanak tanıyan birden fazla sekme vardır.

 ![VS2015 Otolar ve çağrı yığını Windows](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Çeşitli eylemler uygulamanızla çalışın ve değişiklikleri gözlemleyin. Bir şey olağan dışı görünüyorsa, Ctrl + Alt + Break tuşlarına basarak uygulamayı duraklatmak (veya tıkladığınızda **duraklatmak** düğmesi).

 ![Visual Studio tümünü Kes düğmesi](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Uygulamayı çalıştırmaya devam etmek için F5'e basın (veya **devam** düğmesi).

 ![Visual Studio hata ayıklama devam düğmesine](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 Shift + F5 tuşlarına basarak veya tıklayarak uygulamanızı durdurabilirsiniz **Durdur** düğmesi. Veya yalnızca uygulamanın ana pencere (veya komut satırı iletişim) kapatabilirsiniz.

 Kodunuzu mükemmel çalıştırdıysanız ve tam olarak bekleniyordu, Tebrikler! Derleme yapılandırmasını değiştirmek **yayın** ve dağıtım için yeniden! (Uzmanları bite birim testi üzerinde sonunda, yine de gitmek isteyebilirsiniz.) Ancak, askıda kalma, veya kilitlenmiş veya bazı ilginç sonuçlar verdiğiniz, bu sorunların kaynağını bulun ve hataları düzeltmek gerekir.

### <a name="setting-simple-breakpoints"></a>Basit kesme noktaları ayarlama
 Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir. Bir projeyi ayarlama ve kesme noktaları kaldırma sonrasında yeniden gerekmez.

 Gerçekleşirse, kod satırını seçin veya F9 tuşuna basın, kesme istediğiniz kadar kenar boşluğunu satırının tıklayarak bir kesme noktası ayarlayın. Kodunuzu çalıştırmak, bu kod satırı yönergelerini yürütülmeden önce durdurur.

 ![Visual Studio kesme noktası](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Kodu keserse işaretlenmiş kod satırının henüz yürütüldü değil. Bu noktada, kesme noktası işaretlenmiş kod satırının yönergeleri yürütmek ve değiştirilmiş değerleri incelemek isteyebilirsiniz. Bu, "içine kodu Adımlama" olarak adlandırılır. Bir yöntem çağrısının işaretlenmiş kod ise içine F11 tuşuna basarak geçebilirsiniz. Aynı zamanda "üzerinden kod satırının F10 tuşlarına basarak adım". Kesme noktası adım eylemleri hakkında daha fazla ayrıntı için okuma [hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md).

 Kesme noktaları için yaygın kullanımları şunlardır:

1. Bir kilitlenme veya kapanma kaynağını daraltmak için bunları boyunca ve hataya neden olduğunu düşündüğünüz yöntem çağrısının kod etrafında dağılım. Kodunuz içinde adım adım olarak, kaldırmak ve kod geçemediğinde bulana kadar yakın kesme noktaları birlikte sıfırlayın.

2. Yeni kod yapılırsa ve beklendiği gibi davrandığından emin olmak için kodu adımlayın başında bir kesme noktası ayarlayın.

3. Karmaşık bir davranış uygulanırsa, program böldüğünde veri ve değişken değerlerini inceleyebilirsiniz. Bu nedenle algoritmik kodu için kesme noktaları ayarlayın.

4. Bunu C veya C++ koduna kodunu durdurmak için kullanım kesme noktaları yazıyorsanız, bellekle ilgili hataları için hata ayıklama sırasında adres değerlerini (NULL arayın) ve başvuru sayısı inceleyebilirsiniz.

   Kesme noktaları kullanma hakkında daha fazla bilgi için okuma [kesme noktaları kullanma](../debugger/using-breakpoints.md)

### <a name="setting-conditional-breakpoints"></a>Koşullu kesme noktaları ayarlama
 Bir döngüde veya özyinelemede içinde bir kesme noktası varsa veya çok sık adım adım kesme noktaları varsa, koşullu kesme noktası yalnızca belirli koşullar karşılandığında kodunuzu askıya alındığından emin olmak için kullanın. Aksi takdirde, F11 awful bir çok tuşuna basarak.

 Koşullu kesme noktası ayarlayın ve bir değişken, belirli bir değere ayarlayın veya belirli bir eşiği geçirir, kodunuzu askıya alma, bir kesme noktası ayarlamak için kenar boşluğunda tıklayın ve ardından görüntülenen vurgulu menüsünden "dişli" seçin için.

 ![Visual Studio 2015 kesme noktası ayarları](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Şuna benzer bir iletişim kutusu görürsünüz kesmenin belirli koşulları ayarlayabileceğiniz.

 ![Visual Studio 2015 koşullu kesme noktası](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Koşullu kesme noktaları değerlendirmek için kullanılan ifadeler bildirmek nasıl daha fazla ayrıntı için Channel9 videoya göz atın [Visual Studio 2015'te kesme noktası yapılandırması deneyimi](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).

### <a name="inspecting-your-code-at-run-time"></a>Çalışma zamanında kodunuzu inceleniyor
 Çalışan kodunuz bir kesme noktası ve durur ulaştığında, değişkenlerinizi inceleyin ve neler olduğunu belirlemek için yığınları çağırın. Görmeyi beklediğiniz aralıklara değerler? Aramalar doğru sırada yapılır?

 ![Visual Studio 2015'nı Çalıştır&#45;zaman değeri incelemesi](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Şu anda içerdiği başvuruları ve değerleri görmek için bir değişken üzerinde gezdirin. Beklemediğiniz bir değer görürseniz, önceki veya çağıran kod satırıyla muhtemelen hata vardır. Kesme noktaları Yukarı Taşı veya daha fazla aramanızı daraltmak için mevcut kesme noktaları için koşullar ekleyebilirsiniz.

 Ayrıca, Visual Studio 2015 tanılama araçları penceresi, burada, uygulamanızın CPU ve bellek kullanımı zamanla inceleyebileceğiniz görüntüler. Beklenmeyen yoğun CPU kullanımı veya bellek ayırma için aramak için bunları kullanın. İle birlikte kullanmak **Watch** penceresi ve hangi beklenmeyen, yoğun kullanım veya yayımlanmamış kaynak neden olduğunu belirlemek için kesme noktaları.

 ![Visual Studio 2015 tanılama araçları penceresi](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Birim testleri çalıştırma
 Birim testlerini kod yollarında uygulamanızı veya hizmetinizi alıştırma programlardır. Visual Studio 2015 hem yönetilen hem de yerel kod için Microsoft birim testi çerçevelerini yükler. Birim testleri oluşturun, bunları çalıştırmak ve bu testlerin sonuçları rapor için bir birim testi Çerçevesi'ni kullanın. Kodunuzun düzgün çalışıp çalışmadığını test etmek için değişiklik yaptığınız zaman yeniden çalıştır birim testleri. Visual Studio 2015 Enterprise'ı kullandığınızda, her derleme sonrasında testleri otomatik olarak çalıştırabilir.

 Başlamak için okuma [Intellitest ile kodunuz için birim testleri oluşturmak](../test/generate-unit-tests-for-your-code-with-intellitest.md).

 Visual Studio 2015 ve bunların nasıl daha kaliteli kod oluşturmanıza yardımcı olabileceğini birim testleri hakkında daha fazla bilgi edinmek için [birim testi temel bilgileri](../test/unit-test-basics.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da hata ayıklama](../debugger/debugging-in-visual-studio.md) [hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md) [64-Bit uygulamalarında hata ayıklama](../debugger/debug-64-bit-applications.md) [hata ayıklayıcı temel bilgileri](../debugger/debugger-basics.md)
