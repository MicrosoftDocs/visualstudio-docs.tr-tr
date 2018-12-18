---
title: Yeni başlayanlar için performans profili oluşturma Kılavuzu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a1b8fbc31bb05f69a1f9e30960106c08df5eb6f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731485"
---
# <a name="beginners-guide-to-performance-profiling"></a>Performans Profili Oluşturma Başlangıç Kılavuzu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio profil oluşturma araçları, uygulamanızdaki performans sorunlarını analiz etmek için kullanabilirsiniz. Bu yordam, nasıl kullanılacağını gösterir **örnekleme** veri.  
  
 **Örnekleme** uygulamada çoğu kullanıcı modu yapmakta olduğunuz işlevler çalışma gösteren bir istatistik profil oluşturma yöntemidir. Örnekleme, uygulamanızı hızlandırmak alanlar aramaya başlamak için iyi bir yerdir.  
  
 Belirli aralıklarla **örnekleme** yöntemi uygulamanızda yürütülen işlevler hakkında bilgi toplar. Bir profil oluşturma çalıştırmasını tamamladıktan sonra **özeti** verileri en etkin işlev çağrısı ağacını gösterir, profil oluşturma görünümü adlı **etkin yolu**, burada uygulamadaki işin çoğu yapılmıştır. Görünüm ayrıca en bireysel işleri yapan işlevleri listeler ve örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.  
  
 Varsa **örnekleme** duyduğunuz verileri sağlamazsa diğer profil oluşturma araçları koleksiyonu yöntemleri size yardımcı olabilecek bilgiler farklı türde sağlayın. Bu diğer yöntemler hakkında daha fazla bilgi için bkz. [nasıl yapılır: Koleksiyon metotları seçin](../profiling/how-to-choose-collection-methods.md).  
  
> [!TIP]
>  Windows işlevlerini çağıran kodu yazıyorsanız, en güncel .pdb dosyalarına sahip olduğunuzdan emin olun. Bu dosyalar olmadan rapor görünümleriniz karmaşık ve anlaşılması zor olan Windows işlev adlarını listeler. Gereksinim duyduğunuz dosyaların bilgisayarınızda yüklü olduğundan emin olma hakkında daha fazla bilgi için bkz. [nasıl yapılır: başvuru Windows sembol bilgilerini](../profiling/how-to-reference-windows-symbol-information.md).  
  
##  <a name="Step1"></a> Oluşturma ve performans oturumu çalıştırma  
 Analiz etmek için gereken verileri almak için öncelikle bir performans oturumu oluşturmanız ve ardından çalıştırmanız gerekir. **Performans Sihirbazı** her ikisini de yapmanızı sağlar.  
  
 Windows masaüstü uygulaması veya ASP.NET uygulamasını profil değil, bir profil oluşturma araçlarından birini kullanmanız gerekir. Bkz: [profil oluşturma araçları](../profiling/profiling-tools.md).  
  
#### <a name="to-create-and-run-a-performance-session"></a>Oluşturma ve performans oturumu çalıştırma  
  
1.  Visual Studio içinde çözümü açın. Yapılandırması yayın olarak ayarlanmış. (Bul **çözüm yapılandırmaları** ayarlamak için araç çubuğundaki **hata ayıklama** varsayılan olarak. Değiştirin **yayın**.)  
  
    > [!IMPORTANT]
    >  Kullanmakta olduğunuz bilgisayarda yönetici değilseniz, profil oluşturucuyu kullanırken, Visual Studio Yönetici olarak çalıştırmalısınız. (Visual Studio uygulama simgesini sağ tıklatın ve ardından **yönetici olarak çalıştır**.  
  
2.  Üzerinde **hata ayıklama** menüsünü tıklatın **performans Profiler**.  
  
3.  Denetleme **performans Sihirbazı** seçeneğini ve tıklayın **Başlat**.  
  
4.  Denetleme **CPU örnekleme (önerilir)** seçeneğini ve tıklayın **son**.  
  
5.  Uygulamanız başlatılır ve Profil Oluşturucu veri toplamaya başlar.  
  
6.  Performans sorunları içerebilecek işlevi çalıştırın.  
  
7.  Her zaman yaptığınız gibi uygulamayı kapatın.  
  
     Uygulamayı yürütmeyi bitirdikten sonra **özeti** profil oluşturma verilerinin görünümü ana Visual Studio penceresinde görüntülenir ve yeni bir oturum için bir simge görünür **performans Gezgini** penceresi.  
  
##  <a name="Step2"></a> 2. adım: Örnekleme verileri analiz edin  
 Bir performans oturumunu çalıştırmayı bitirdiğinizde **özeti** Visual Studio ana penceresinde profil oluşturma rapor görünümünde görünür.  
  
 İnceleyerek verilerinizi analiz etmeye başlamanızı öneririz **sık kullanılan yol** ardından fazla çalışmayı yapan ve son olarak diğer işlevlere odaklanarak üzerinde kullanarak işlevlerin listesi **Özet zaman çizelgesi** . Profil oluşturma önerilerini ve Uyarıları da görüntüleyebilirsiniz **hata listesi** penceresi.  
  
 Örnekleme yöntemi, size gereken bilgileri sağlamayabilir olduğunu unutmayın. Örneğin, yalnızca uygulama kullanıcı modu kodunu yürüttüğünde örnekleri toplanır. Bu nedenle, giriş ve çıkış işlemleri gibi bazı işlevler örnekleme tarafından yakalanmaz. Profil oluşturma araçları, önemli verilere odaklanmanıza olanak veren çeşitli toplama yöntemleri sağlar. Diğer yöntemler hakkında daha fazla bilgi için bkz. [nasıl yapılır: Koleksiyon metotları seçin](../profiling/how-to-choose-collection-methods.md).  
  
 Şekildeki her numaralı alan yordamdaki bir adımda ilgilidir.  
  
 ![Örnekleme için Özet rapor görünümü](../profiling/media/summary-sampling.png "Summary_Sampling")  
  
#### <a name="to-analyze-sampling-data"></a>Örnekleme verileri analiz etmek için  
  
1.  İçinde **özeti** görünümü **etkin yolu** en kapsamlı örneklerle uygulamanızın çağrı ağacının dalını gösterir. Bu, veriler toplandığında en aktif olan yürütme yoludur. Çağrı ağacını üreten algoritmayı iyileştirilebilir yüksek içeren değerler belirtebilirsiniz. Kodunuzda yoldaki en düşük işlevi bulun. Bir yolu da sistem işlevlerini veya İşlevler harici modüllerdeki içerebileceğine dikkat edin.  
  
     ![Profiler etkin yolu](../profiling/media/profiler-hotpath.png "Profiler_HotPath")  
  
    1.  **Kapsamlı örnekler** işlevi ve olarak adlandırılan her türlü işlev ne kadar iş yapıldığı gösterir. Yüksek içeren sayılar işlevin, genel olarak en pahalı olduğunu işaret eder.  
  
    2.  **Dışlamalı örnekler** tarafından çağrılan işlevler tarafından yapılan iş hariç işlev gövdesindeki kod tarafından ne kadar iş yapıldığı gösterir. Yüksek dışlamalı sayımlar işlevin kendisi içinde bir performans engelini işaret edebilir.  
  
2.  Görüntülemek için işlevin adını tıklayarak **işlev ayrıntıları** profil oluşturma verilerinin görünümü. **İşlev ayrıntıları** görünümü, o işlevi çağıran tüm işlevlere ve seçili işlev tarafından çağrılan tüm işlevleri gösteren seçili işlev için profil verilerinin grafik bir görünümünü sunar.  
  
    -   Çağıran ve çağrılan işlevlerin blok boyutu, işlevlerin yaptığını veya çağrıldığını sıklıkta temsil eder.  
  
    -   Bir arama adını tıklayabilirsiniz ya da çağrılan işlev Ayrıntıları görünümünde seçili işlev yapmak için işlev.  
  
    -   Alt bölmesinde **işlev ayrıntıları** windows işlev kodunu görüntüler. Kodu inceleyerek performansını iyileştirme fırsatı bulursanız, Visual Studio Düzenleyicisi'nde dosyayı açmak için kaynak dosya adına tıklayın.  
  
3.  Çözümlemenize devam etmek için iade **özeti** görünümü seçerek **özeti** görünüm açılır listesinden. Ardından deki işlevleri inceleyin **en bireysel işleri yapan işlevler**. Bu liste, en yüksek dışlamalı örnek işlevleri görüntüler. Bu işlevlerin işlev gövdesindeki kod önemli işler yapar ve bunu en iyi duruma olabilir. Daha fazla belirli bir işlev analiz edin, içinde görüntülemek için işlevin adını tıklayarak için **işlev ayrıntıları** görünümü.  
  
     ![En fazla çalışmayı yapan işlevler listesini](../profiling/media/functions-mostwork.png "Functions_MostWork")  
  
     Profil oluşturma, araştırmanızı devam etmek için profil oluşturma verilerinin bir segmentini zaman çizelgesini kullanarak yeniden Çözümle **özeti** görünüm, gösterilecek **etkin yolu** ve **işlevleri En bireysel işleri yapan** seçilen bir segmentten. Örneğin, Zaman Çizelgesi'nde küçük bir tepe üzerinde odaklanmak pahalı çağrı ağaçları ve tüm profil oluşturma analizinde gösterilmeyen işlevleri açığa çıkarabilir.  
  
     Bir segmenti yeniden Çözümle için Özet zaman çizelgesi kutusunda bir segment seçin ve ardından **seçime göre filtre**.  
  
     ![Performans Özet görünümü zaman çizelgesi](../profiling/media/performancesummary.png "PerformanceSummary")  
  
4.  Profil Oluşturucu ayrıca profil oluşturma çalıştırılmasına ilişkin iyileştirme yollarını önermek ve olası performans sorunlarını tanımlamak için bir kural kümesi kullanır. Bir sorun bulunursa, bir uyarı görüntülenen **hata listesi** penceresi. Açmak için **hata listesi** penceresi, **görünümü** menüsünü tıklatın **hata listesi**.  
  
    -   Uyarı çalıştıran işlevi görmek için **işlev ayrıntıları** görüntülemek için uyarıyı çift tıklatın.  
  
    -   Uyarı hakkında ayrıntılı bilgi görüntülemek için hatayı sağ tıklayın ve ardından **hata yardımını göster**  
  
##  <a name="Step3"></a> 3. adım: kodu gözden geçirin ve bir oturumu yeniden çalıştırın  
 Bulmak ve bir veya daha fazla işlev en iyi duruma getirme sonra profil oluşturma çalıştırmasını yineleyebilirsiniz ve uygulamanızın performansını için Değişikliklerinizi yaptıktan farkı görmek için verileri karşılaştırabilirsiniz.  
  
#### <a name="to-revise-code-and-rerun-the-profiler"></a>Kodu gözden geçirin ve profil oluşturucuyu yeniden çalıştırmak için  
  
1.  Kodunuzu değiştirin.  
  
2.  Açmak için **performans Gezgini**, **hata ayıklama** menüsünü tıklatın **Profiler**, ardından **performans Gezgini** ve ardından**Göster performans Gezgini**.  
  
3.  İçinde **performans Gezgini**, yeniden çalıştırın ve ardından istediğiniz oturumu sağ **profil ile Başlat.**  
  
4.  Oturumu yeniden çalıştırdıktan sonra başka bir veri dosyası eklenir **raporları** klasörü oturumda **performans Gezgini**. Hem özgün seçin ve yeni profil oluşturma verisini, seçime sağ tıklayın ve ardından **Performans raporlarını Karşılaştır**.  
  
     Karşılaştırma sonuçlarını görüntüleyen yeni bir rapor penceresi açılır. Karşılaştırma görünümünün nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: performans veri dosyalarını karşılaştırma](../profiling/how-to-compare-performance-data-files.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)   
 [Çalışmaya başlama](../profiling/getting-started-with-performance-tools.md)   
 [Genel Bakışlar](../profiling/overviews-performance-tools.md)



