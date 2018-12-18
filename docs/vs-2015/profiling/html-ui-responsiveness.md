---
title: HTML kullanıcı Arabirimi yanıt hızı | Microsoft Docs
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
- performance, JavaScript [Windows Store apps]
- performance tools, JavaScript [Windows Store apps]
- UI Responsiveness Profiler [JavaScript]
- profiler, UI responsiveness [JavaScript]
- profiler, JavaScript [Windows Store apps]
ms.assetid: da13070a-ba40-47dd-a846-ad72eed70d0b
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63027ccfffde0aa3b62bae6c1529826fd9b26c71
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760713"
---
# <a name="html-ui-responsiveness"></a>HTML kullanıcı Arabirimi yanıt hızı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, uygulamalarınızı Windows Evrensel uygulamaları için bir performans aracı kullanıcı Arabirimi yanıtlama hızı Profiler'ı kullanarak performans sorunlarını yalıtmak açıklar.  
  
 UI yanıtlama hızı Profiler gibi kullanıcı Arabirimi yanıt hızı sorunlarını veya platform yan etkiler, genellikle aşağıdaki belirtilerle oluşan sorunları ayırmanıza yardımcı olabilir:  
  
-   UI yanıtlama hızını eksiği. Uygulama kullanıcı Arabirimi iş parçacığı engellenir yanıt yavaş olabilir. UI iş parçacığı engelleyebilecek bazı şeyleri aşırı zaman uyumlu bir JavaScript kod, aşırı CSS düzen veya CSS hesaplama iş, zaman uyumlu XHR istekleri, çöp toplama, aşırı Boya kez veya yoğun işlemci JavaScript kodu içerir.  
  
-   Yavaş sayfa veya uygulama için yükleme süresi. Bunun nedeni genellikle kaynakları tarafından harcanan aşırı zaman yükleme.  
  
-   Beklenenden daha az sıklıkta görsel güncelleştirmeleri. UI iş parçacığı kesintisiz kare hızını korumak için çok meşgul olduğunda gerçekleşir. Örneğin, çerçeve, UI iş parçacığı meşgulse bırakılabilir. Bazı kullanıcı Arabirimi olmayan iş parçacığı görüntü kodu çözme, ağ istekleri ve paints visual güncelleştirmelerin sıklığını da sınırlayabilirsiniz gibi çalışır. (Tüm boyama UI iş parçacığı üzerinde gerçekleştirilir.)  
  
##  <a name="RunningProfiler"></a> HTML kullanıcı Arabirimi yanıt hızı Aracı'nı çalıştırın  
 Çalışan bir evrensel Windows veya Windows Store app Visual Studio'da Aç veya sonraki veya Windows 8 çalıştıran bir bilgisayarda yüklü olduğunda, HTML kullanıcı Arabirimi yanıt hızı Aracı'nı kullanabilirsiniz.  
  
1.  Visual Studio'da uygulama üzerinde çalıştırıyorsanız, **standart** araç penceresindeki **hata ayıklamayı Başlat** listesinde, bir Windows Phone öykünücüleri gibi bir dağıtım hedefini seçin **yerel makine** , **Simülatör**, veya **uzak makine**.  
  
2.  Üzerinde **hata ayıklama** menüsünde seçin **performans Profiler...** .  
  
     Analiz hedefi için profil oluşturucuyu değiştirmek istiyorsanız, seçin**değiştirme hedefi**.  
  
     ![Çözümleme hedefi Değiştir](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Çözümleme hedefi için aşağıdaki seçenekler kullanılabilir:  
  
    -   **Başlangıç projesi**. Geçerli başlangıç projesini analiz etmek için bu seçeneği belirleyin. Uygulama, bir uzak makine veya cihaz üzerinde çalıştırıyorsanız, bu ayar varsayılan değer olan kullanmanız gerekir.  
  
    -   **Uygulamayı çalıştıran**. Windows Store app çalışan uygulamalar, bir listeden seçmek için bu seçeneği belirleyin. Bir uzak makine veya cihaz üzerinde uygulama çalıştırırken bu seçeneği kullanamazsınız.  
  
         Kaynak koduna erişim iznine sahip değilseniz, bilgisayarınızda çalışan uygulamaların performansını çözümlemek için bu seçeneği kullanabilirsiniz.  
  
    -   **Uygulama yüklü**. Analiz etmek istediğiniz yüklü bir uygulama seçmek için bu seçeneği belirleyin. Bir uzak makine veya cihaz üzerinde uygulama çalıştırırken bu seçeneği kullanamazsınız.  
  
         Kaynak koduna erişiminiz yoksa, bilgisayarınızda yüklü uygulamaların performansını analiz etmek için bu seçeneği kullanabilirsiniz. Yalnızca kendi uygulama geliştirme dışında herhangi bir uygulama performansını analiz etmek istediğinizde bu seçeneği de yararlı olabilir.  
  
3.  Gelen **kullanılabilir Araçları**seçin **HTML UI yanıtlama hızı**ve ardından **Başlat**.  
  
4.  Bir kullanıcı hesabı denetimi penceresinde, kullanıcı Arabirimi yanıtlama hızı Profiler'ı başlattığınızda, Visual Studio ETW Collector.exe çalıştırmak için izninizi isteyebilir. Seçin **Evet**.  
  
     İlgili performans senaryoyu test etmek için uygulamayla etkileşim kurun. Ayrıntılı iş akışı için bkz: [bir kullanıcı Arabirimi yanıt hızı sorununu gidermek](#Workflow) ve [görsel üretilen iş yalıtmak](#IsolateVisualThroughput).  
  
5.  Visual Studio için Alt + Sekme tuşuna basarak geçin.  
  
6.  Profil Oluşturucu toplanan uygulama ve verileri profil oluşturmayı durdurmak için seçin **koleksiyonu Durdur**.  
  
##  <a name="IsolateAnIssue"></a> Bir sorunu  
 Aşağıdaki bölümde, performans sorunlarını yalıtmak yardımcı olacak öneriler sunar. Uygulamasının performansını test etme bir örnek kullanarak performans sorunlarını belirleyin ve nasıl hakkında adım adım açıklama için bkz: [izlenecek yol: iyileştirme UI yanıtlama hızı (HTML)](../profiling/walkthrough-improving-ui-responsiveness-html.md).  
  
###  <a name="Workflow"></a> Bir kullanıcı Arabirimi yanıt hızı sorununu gidermek  
 UI yanıtlama hızı Profiler daha etkili bir şekilde kullanmanıza yardımcı olabilecek bir önerilen iş akışı adımları sağlayın:  
  
1.  Uygulamanızı Visual Studio'da açın.  
  
2.  Kullanıcı Arabirimi yanıt hızı sorunlarını için uygulamanızı test edin. (Hata ayıklama olmadan uygulamanızı başlatmak için Ctrl + F5 tuşlarına basın.)  
  
     Bir sorun bulursanız, sorunun gerçekleştiği zaman çerçevesi daraltmak deneyin ya da devre dışı davranışlara neden Tetikleyicileri belirlemeye çalışın test devam edin.  
  
3.  Visual Studio (Alt + Sekme tuşuna basın) geçin ve uygulamanızı (Shift + F5) durdurun.  
  
4.  İsteğe bağlı olarak, kullanıcı işaretlerini kullanarak kod ekleme [kod analizi için işaretleyin](#ProfileMark).  
  
    > [!TIP]
    >  Kullanıcı işaretleri profil oluşturucu verileri görüntülerken yanıt verme hızını sorunu belirlemenize yardımcı olabilir. Örneğin, bir yanıt verdiğini soruna neden olan kod bölümünün başında ve sonunda bir kullanıcı işareti ekleyebilirsiniz.  
  
5.  Önceki bölümdeki yönergeleri takip ederek kullanıcı Arabirimi yanıtlama hızı Profiler çalıştırın.  
  
6.  Uygulama içinde bir kullanıcı Arabirimi yanıt hızı sorununu sonuçlarını durum yerleştirin.  
  
7.  Visual Studio'ya (Alt + Sekme tuşuna basın) ve seçin **koleksiyonu Durdur** kullanıcı Arabirimi yanıtlama hızı Profiler profil oluşturucu sekmesindeki.  
  
8.  Kullanıcı işaretleri eklediyseniz, bunlar görünür [Tanılama oturumu zaman çizelgesini görüntüleyin](#Ruler) profil oluşturucunun. Kodunuzda belirli bir işlem belirtmek için kullanılan tek bir kullanıcı işareti aşağıda gösterilmiştir.  
  
     ![Bir kullanıcı işareti gösteren tanılama cetvel](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
9. Zaman Çizelgesi ve profil oluşturucu grafikleri gösterdiğiniz ilgi alanı, kullanıcı işaretlerini, uygulama yaşam döngüsü olayları ya da veri grafiklerde görünür kullanarak tanımlayın. Analiz ve veri grafiklerde kullanmanıza yardımcı olması için bazı yönergeler aşağıda verilmiştir:  
  
    -   Kullanım [Tanılama oturumu zaman çizelgesini görüntüleyin](#Ruler) görüntülemek için [kod analizi için işaretleyin](#ProfileMark), uygulama yaşam döngüsü olaylarını ve bu olaylar için ilişkili zaman çizelgesi ve diğer grafiklerin verilerin zaman çizelgesi.  
  
    -   Kullanım [CPU kullanım grafiği](#CPUutilization) CPU etkinliği ve bu belirli bir süre boyunca işleme iş türü hakkındaki genel bilgileri görüntülemek için. Aşırı CPU etkinliği dönemlerini yanıt hızını sorunlarına yol olasılığı daha yüksektir ve çerçeveleri bırakılan.  
  
    -   Bir oyun ya da zengin medya uygulaması geliştiriyorsanız, kullanın [görünümü görsel üretilen iş (FPS)](#VisualThroughput) süreler içinde kare hızı bırakılan tanımlamak için.  
  
10. Grafikler biriyle ilgi alanı, grafiğin parçası tıklayarak ve seçim yapmak için işaretçiyi sürükleyerek (veya SEKME tuşunu ve ok tuşlarını kullanarak) seçin. Bir seçim yaparak bir zaman aralığı seçin, profil oluşturucunun alt bölmesinde zaman çizelgesi ayrıntıları grafikte yalnızca seçilen zaman aralığı göstermek için değiştirir.  
  
     Aşağıdaki çizimde vurgulanan ilgi alanı ile CPU kullanım grafiği gösterir.  
  
     ![CPU kullanım grafiği](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
11. Kullanım [zaman çizelgesi ayrıntıları görüntüle](#TimelineDetails) çok sık çalışması veya tamamlamak için çok fazla zaman aldığını olaylar hakkında ayrıntılı bilgi almak için. Örneğin, aşağıdakileri kontrol edin:  
  
    -   Olay dinleyicilerini, zamanlayıcılar ve animasyonlu çerçeve geri çağırmalarını. Belirli olay bağlı olarak, değiştirilen DOM öğeleri, değiştirilen CSS özellik adı, kaynak konumu için bir bağlantı kimliği ve ilişkili olay veya geri arama işlevinin adını sağlanan verileri içerebilir.  
  
    -   Düzeni veya betik gibi işleme öğeler, sonuçlanan olayları çağrılar `window.getComputedStyles`. İlişkili DOM öğesi olayı için sağlanır.  
  
    -   Sayfalarını veya HTML olayları ayrıştırmak için betik değerlendirmeleri gibi uygulama tarafından yüklenen URL kaynakları. Dosya adı veya kaynak sağlanır.  
  
    -   Belirtilen diğer olayları [Profiler olay başvurusunu](#ProfilerEvents).  
  
    > [!TIP]
    >  Profil Oluşturucu kullanılabilir bilgilerin çoğu zaman çizelgesi ayrıntıları grafikte görünür.  
  
12. CPU kullanımı veya görsel üretilen iş (FPS) grafik seçili ile bir alanı seçin **yakınlaştırmak** (daha ayrıntılı bilgi almak için düğme ya da bağlam menüsü). Zaman Çizelgesi grafiği değişerek yalnızca seçilen zaman aralığı için.  
  
13. Seçeneğinde, CPU kullanımı veya görsel üretilen iş grafiklerini bir bölümünü seçin. Yalnızca seçilen zaman aralığı profil oluşturucunun alt bölmesinde değişerek zaman çizelgesi ayrıntıları grafikte bir seçim yaptığınızda.  
  
###  <a name="IsolateVisualThroughput"></a> Görsel üretilen iş ile ilgili bir sorun Ayır  
 Aşırı CPU kullanımını süreler içinde düşük veya tutarsız kare hızları neden olabilir. Zengin medya uygulamaları ve oyunları geliştirmek, görsel üretilen iş grafiklerini CPU kullanım grafiği daha önemli veri sağlayabilir.  
  
 Bir görsel üretilen iş sorununu gidermek için önceki bölümde açıklanan adımları izleyin, ancak anahtar veri noktalarını biri olarak görsel üretilen iş grafiklerini kullanın.  
  
###  <a name="ProfileMark"></a> Kod Analizi için işaretleyin  
 Grafiklerde Görüntülenen verilerle ilişkili uygulama kodun bir bölümünü yalıtmaya yardımcı olmak için uygulamanızda yönlendiren kullanıcı işareti eklemek için profil oluşturucu bir işlev çağrısı ekleyebilirsiniz. — ters bir üçgen — anda Zaman Çizelgesi'nde işlevin yürütüldüğü. CPU kullanım grafiği, görsel üretilen iş grafiklerini ve zaman çizelgesi ayrıntıları grafik zaman çizelgesinde eklediğiniz tüm kullanıcı işareti görünür.  
  
 Bir kullanıcı işareti eklemek için uygulamanız için aşağıdaki kodu ekleyin. Bu örnek, "veri" Olay açıklaması kullanır.  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("getting data");  
}  
  
```  
  
 Kullanıcı işareti fare işaretçisini getirdiğinizde olayın açıklamasını bir araç ipucu olarak görüntülenir. Gereksinim duyduğunuz kadar çok kullanıcı işaretlerini ekleyebilirsiniz.  
  
> [!NOTE]
>  `console.timeStamp`, bir Chrome komutu, bir kullanıcı işareti da görünür.  
  
 Tek kullanıcı işareti ve araç ipucu ile tanılama cetvel aşağıda gösterilmiştir.  
  
 ![Bir kullanıcı işareti gösteren tanılama cetvel](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
 İki kullanıcı işaretleri arasında geçen süreyi göstermek için zaman çizelgesi Ayrıntıları görünümünde, araç tarafından oluşturulan olayları da oluşturabilirsiniz. Aşağıdaki kod, ikinci bir kullanıcı işareti ve bir (Yukarıdaki kod ilk kullanıcı işareti gösterir) iki kullanıcı işaretlerini yürütülmesi arasında geçen süre ölçümü ekler.  
  
```javascript  
if (performance.mark && performance.measure) {  
    performance.mark("data retrieved");  
    performance.measure("data measure", "getting data", "data retrieved");  
}  
```  
  
 İkinci kullanıcı işareti belirtilmezse, `performance.measure` bir zaman damgası, ikinci kullanıcı işareti kullanır. İlk kullanıcı işareti gereklidir.  
  
 Süre ölçümü olarak görünür bir **kullanıcı ölçü** zaman çizelgesinde Olay Ayrıntıları görünümünde ve seçildiğinde ayrıntılı bilgileri gösterir.  
  
 ![Zaman Çizelgesi'nde kullanıcı ölçü Olay Ayrıntıları görünümünde](../profiling/media/js-htmlvizprofiler-user-measure.png "JS_HTMLVizProfiler_User_Measure")  
  
##  <a name="AnalyzeData"></a> Verileri analiz etme  
 Aşağıdaki bölümler, Profil Oluşturucusu'nda görüntülenen verileri yorumlama yardımcı olacak bilgiler sağlar.  
  
###  <a name="Ruler"></a> Tanılama oturumu zaman çizelgesini görüntüleyin  
 Profil oluşturucunun cetvel profili oluşturulan bilgiler için zaman çizelgesini gösterir. Bu zaman çizelgesi hem CPU kullanım grafiği hem de görsel üretilen iş grafiği için geçerlidir.  
  
 Tanılama oturumu zaman çizelgesi birkaç uygulama yaşam döngüsü olayları için görüntülenen araç ipucu ile nasıl göründüğünü aşağıda verilmiştir:  
  
 ![Tanılama oturumu cetvel](../profiling/media/js-htmlvizprof-ruler.png "JS_HTMLVizProf_Ruler")  
  
 Etkinleştirme olayı gibi uygulama yaşam döngüsü olaylarını ortaya çıktığında ve kullanıcı işaretlerini (kullanıcı işareti üçgenler) olduğunu gösterir ve zaman çizelgesi gösterildiği kodunuza ekleyebilirsiniz. Daha fazla bilgi içeren araç ipuçlarını göster olayları seçebilirsiniz. Kullanıcı işaretleri hakkında daha fazla bilgi için bkz. [kod analizi için işaretleyin](#ProfileMark) bu konuda.  
  
 Uygulama yaşam döngüsü olaylarını elmas simgeler olarak görünür. Aşağıdakileri içeren DOM olayları şunlardır:  
  
-   `DOMContentLoaded` ve `Load` genellikle etkinleştirilmiş olay işleyicisinde kodunuzda ortaya çıkan olaylar. Olay için bir araç ipucu, belirli olay ve URL'sini gösterir.  
  
-   Farklı bir sayfasına gittiğinizde oluşan bir gezinti olayı. Olay için bir araç ipucu hedef sayfası URL'si gösterilir.  
  
###  <a name="CPUUtilization"></a> Görünüm CPU kullanımı  
 CPU kullanım grafiği aşırı CPU etkinliği olduğu süre tanımlamanızı sağlar. Uygulamanın bir süre boyunca ortalama CPU kullanımı hakkında bilgi sağlar. Bilgi aşağıdaki kategorileri göstermek için renk kodlu: **Yükleniyor**, **komut dosyası**, çöp toplama (**GC**), **stil**, **İşleme**, ve **görüntü kodu çözme**. Bu kategorileri hakkında daha fazla bilgi için bkz. [Profiler olay başvuru](#ProfilerEvents) bu konuda.  
  
 CPU kullanım grafiği, CPU kullanımı değerleri tek bir yüzde değeri bir veya daha fazla CPU için birleştirme tüm uygulama iş parçacığı üzerinde harcanan süreyi gösterir. Birden fazla CPU kullanımda olduğunda değerin CPU kullanımı yüzde 100 aşabilir.  
  
> [!NOTE]
>  GPU kullanımı grafiğinde görünmüyor.  
  
 Bu örnek, CPU kullanım grafiği nasıl göründüğünü gösterir:  
  
 ![CPU kullanım grafiği](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
 Bu grafiğe kullanın:  
  
- Genel sorunlu alanları tanımlayın.  
  
- Zaman Çizelgesi ayrıntıları grafikte görüntülemek için belirli bir süre seçin. Bir zaman dilimi seçmek için grafiğin parçası seçin ve seçim yapmak için işaretçiyi sürükleyin.  
  
- Seçerek seçili bir döneme ait daha ayrıntılı bir görünüm elde **yakınlaştırmak** düğmesi.  
  
  Grafik kullanma hakkında daha fazla bilgi için bkz. [bir kullanıcı Arabirimi yanıt hızı sorununu gidermek](#Workflow) bu konuda.  
  
###  <a name="VisualThroughput"></a> Görünüm görsel üretilen iş (FPS)  
 Görsel üretilen iş grafiklerini süreler içinde kare hızı bırakılan tanımlamanızı sağlar. Bu, saniyedeki kare (FPS) uygulama sayısını gösterir. Bu grafik oyunları ve zengin medya uygulamaları geliştirme için en kullanışlıdır.  
  
 Görüntülenen FPS değerini gerçek kare hızı farklı olabilir. Bu graf verileri incelerken, bu bilgileri göz önünde bulundurun:  
  
- Grafik FPS uygulama herhangi bir belirli zamanda elde etmek kapasitesine sahip olduğunu gösterir. Uygulama boşta olduğunda FPS İzleyici yenileme hızı ile aynıdır.  
  
- Grafik uygulaması görsel güncelleştirmeleri gerektiren iş yapıyor, gerçek FPS gösterir.  
  
- Çerçeve bırakılma durumunda grafik sıfır değeri gösterir.  
  
  Bu örnek, görsel üretilen iş grafiklerini nasıl göründüğünü gösterir:  
  
  ![Görsel üretilen iş grafiklerini](../profiling/media/js-htmlvizprof-vizthru.png "JS_HTMLVizProf_VizThru")  
  
  Görsel üretilen iş grafiğe kullanın:  
  
- Genel sorunlu alanları tanımlayın.  
  
- Zaman Çizelgesi ayrıntıları grafikte görüntülemek için belirli bir süre seçin. Bir zaman dilimi seçmek için grafiğin parçası seçin ve seçim yapmak için işaretçiyi sürükleyin.  
  
- Seçerek seçili bir döneme ait daha ayrıntılı bir görünüm elde **yakınlaştırmak** düğmesi.  
  
###  <a name="TimelineDetails"></a> Zaman Çizelgesi ayrıntıları görüntüle  
 Zaman Çizelgesi ayrıntıları grafik kullanıcı Arabirimi yanıtlama hızı Profiler alt bölmede görünür. En yüksek CPU zamanının Seçilen süreler sırasında tüketilen olaylar hakkında sıralı ve hiyerarşik bilgilere yer verilmiştir. Bu grafiği, belirli bir olay neyin tetiklediği belirlemenize yardımcı olur ve bazı olaylar için kaynak koda geri olay nasıl eşlendiğini. Bu grafik, ayrıca ekranında visual güncelleştirmeleri boyamak için gereken süreyi belirlemenize yardımcı olur.  
  
 Grafik kullanıcı Arabirimi iş parçacığı iş ve iş görsel güncelleştirmeleri yavaş katkıda bulunmak arka plan iş parçacıklarında gösterir. Graf JavaScript JIT iş, zaman uyumsuz GPU işi, (örneğin, iş RuntimeBroker.exe ve dwm.exe) ana bilgisayar işlemi dışında gerçekleştirilen iş veya iş için Windows çalışma zamanı henüz (disk g/ç gibi) için izleme eklenmiş profil oluşturma henüz alanlarını göstermez.  
  
> [!TIP]
>  Arka plan iş parçacığında bir olay meydana geldiğinde, iş parçacığı kimliği olay adının yanındaki köşeli ayraç içinde görünür.  
  
 Bu örnek, olay için bir DOM olay dinleyicisi tıkladığınızda seçili ayrıntılarını graph görülüyor ne zaman çizelgesini gösterir:  
  
 ![Zaman Çizelgesi ayrıntıları grafiği](../profiling/media/js-htmlvizprof-timelinedet.png "JS_HTMLVizProf_TimelineDet")  
  
 Bu çizimde, **spinAction** olay işleyicisinde **olay adı** sütundur bir bağlantı, seçili olduğunda, kaynak kodundaki olay işleyicisi yönlendirilirsiniz. Sağ bölmede, **geri çağırma işlevi** özelliği, kaynak kodu aynı bağlantı sağlar. Diğer özellikleri de ilişkili DOM öğesi gibi bir olay hakkında bilgiler sağlar.  
  
 CPU kullanımı ve görsel üretilen iş (FPS) graph zaman çizelgesinin bir bölümü seçerseniz, zaman çizelgesi ayrıntıları grafik, seçilen zaman aralığı için ayrıntılı bilgileri gösterir.  
  
 İş CPU kullanımı grafiğinde gösterilen aynı kategorilerini göstermek için renk kodlu zaman çizelgesi ayrıntıları graftaki olaylardır. Olay kategorisi ve belirli olayları hakkında daha fazla bilgi için bkz. [Profiler olay başvuru](#ProfilerEvents) bu konuda.  
  
 Zaman Çizelgesi ayrıntıları grafiğe kullanın:  
  
-   Yaklaşık başlangıç zamanlarını, süresini ve bitiş zamanlarını bir olay için bir zaman çizelgesi ve ızgara görünümünde görüntüleyin. Zaman Çizelgesi ayrıntıları grafiği 30 milisaniye kılavuz görünümü yakınlaştırma durumuna bağlı olarak 30 saniyeye kadar uzanan dönemlerde gösterebilirsiniz. Duration değerleri için:  
  
    -   Kapsamlı bir kez olay alt öğeleri dahil olmak üzere Olay süresini temsil eder. Izgara görünümünde bu değer ilk olarak görünür.  
  
    -   Özel süreleri, olay alt öğeleri dahil değil, olay süresi temsil eder. Izgara görünümünde bu değeri parantez içinde görüntülenir.  
  
-   Olay alt öğelerini görüntülemek için hiyerarşideki bir olay'ı genişletin. Olay alt öğeler tarafından üst olayı oluşturan diğer olaylardır. Örneğin, bir DOM olayı alt öğe olarak görüntülenen olay dinleyicileri olabilir. Olay dinleyicisi, kendisinden gibi bir düzen olay sonuçlanan diğer olayları olabilir.  
  
-   Başlangıç sıralama olayların süresi (varsayılan) ya da süresi. Kullanım **sıralama ölçütü** sıralama metodunu seçin.  
  
-   Ayrıntılar bölmesinde (sağ bölme) her olay için ayrıntıları görüntüleyin. Aşağıdaki örneklerde gösterildiği gibi özellikler, belirli bir olaya bağlı olarak farklılık gösterir:  
  
    -   Zamanlayıcılar, olay dinleyicileri (DOM olayları) ve animasyonlu çerçeve geri çağırmalarını **geri çağırma işlevi** özellik adı ile birlikte kaynak kodu konumu olay işleyicisi veya geri çağırma işlevinin bir bağlantı sağlar.  
  
    -   Seçilen olay ve tüm alt öğelerini renk kodlu özetini zamanlayıcıları, olay dinleyicileri (DOM olayları), Düzen olayları ve animasyonlu çerçeve geri çağırmalarını için görünür **sınırları içeren zaman özeti** bölümü (renk kodlu halka). Her renk kodlu dilimi görüntünün bir olay türünü temsil eder. Araç ipuçları, olay türü adını sağlayın.  
  
    > [!TIP]
    >  Zaman Çizelgesi ayrıntıları grafiği ve **sınırları içeren zaman özeti** iyileştirme için alanları tanımlamanıza yardımcı olabilir. Bu görünüm ya da çok sayıda küçük görevlere gösteriyorsa, olay iyileştirme için bir aday olabilir. Örneğin, bir uygulama düzenini ve HTML olayları ayrıştırma çok sayıda içinde elde edilen yenileme DOM öğeleri sık de olabilir. Bu iş'toplu işlem performansına mümkün olabilir.  
  
###  <a name="FilterTimelineDetails"></a> Filtre zaman çizelgesi ayrıntıları  
 Belirli bir olay için zaman çizelgesi Ayrıntıları görünümünde seçerek filtreleyebilirsiniz **olaya filtre** belirli bir olaya ilişkin bağlam menüsünden. Bu seçeneği belirlediğinizde, zaman çizelgesi ve ızgara görünümü seçilen olaya kapsanır. CPU kullanım grafiği seçiminde de belirli bir olay için kapsamları.  
  
 ![Bir olay için zaman çizelgesi filtreleme](../profiling/media/js-htmlvizprofiler-filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")  
  
###  <a name="FilterEvents"></a> Olayları Filtrele  
 Bazı olaylar zaman çizelgesi ayrıntıları Graph verilerindeki Gürültüyü azaltma veya performans senaryonuz için ilgi çekici olmayan verileri ortadan kaldırmak için filtre uygulayabilirsiniz. Burada açıklanan belirli filtreler veya olay adı ya da olay süresi filtre uygulayabilirsiniz.  
  
 Görüntü kodu çözme olmadığını, bunun kurgusal indirme ve GC olayları filtrelemek için Temizle **arka plan etkinliği** alt kısmında bulunan filtre simgesinin seçeneği. Bu olaylar eyleme dönüştürülebilir olmadığından, bunlar varsayılan olarak gizlidir.  
  
 ![Zaman Çizelgesi'nde olayları filtreleme](../profiling/media/js-htmlvizprofiler-event-filter.png "JS_HTMLVizProfiler_Event_Filter")  
  
 HTTP isteği olaylarını filtrelemek için Temizle **ağ trafiği** alt kısmında bulunan filtre simgesinin seçeneği. Varsayılan olarak, bu olayları zaman çizelgesi ayrıntıları grafikte gösterilir.  
  
 UI iş parçacığı faaliyeti filtrelemek için Temizle **UI etkinliği** seçeneği.  
  
> [!TIP]
>  Bu seçeneği temizleyin ve ağ gecikmesi sorunları araştırmak için ağ trafiği seçeneğini belirleyin.  
  
 Kullanıcı ölçümleri filtrelemek için Temizle **kullanıcı ölçümleri** seçeneği. Kullanıcı ölçümleri, alt ile üst düzey olaylardır.  
  
###  <a name="GroupFrames"></a> Çerçeve tarafından grubu olayları  
 Tek tek çerçeveler için zaman çizelgesi Ayrıntıları görünümünde görüntülenen olayları gruplandırabilirsiniz. Bu çerçeve olayları aracı tarafından oluşturulan olayları ve Boya olaylar arasında gerçekleşen tüm kullanıcı Arabirimi iş parçacığı işi için üst düzey olay kapsayıcılar temsil eder. Bu görünümü etkinleştirmek için seçin **üst düzey olayları karelere göre grup**.  
  
 ![Çerçeve tarafından üst düzey olayları grup](../profiling/media/js-htmlvizprofiler-frame-grouping-button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")  
  
 Çerçeve tarafından olayları gruplandırmak, üst düzey olayları zaman çizelgesi ayrıntıları her temsil eder bir çerçeve görüntüleyin.  
  
 ![Çerçeve tarafından gruplandırılmış zaman çizelgesi olay](../profiling/media/js-htmlvizprofiler-frame-grouping.png "JS_HTMLVizProfiler_Frame_Grouping")  
  
##  <a name="SaveSession"></a> Tanılama oturumu kaydedin  
 Visual Studio'da oturum ile ilişkili sekme kapattığınızda bir tanılama oturumu kaydedebilirsiniz. Daha sonra kaydedilmiş oturumları açılabilir.  
  
##  <a name="ProfilerEvents"></a> Profiler etkinliği başvurusu  
 Profiler olaylar kategorilere ve renk kodlu kullanıcı Arabirimi yanıtlama hızı Profiler içinde. Olay kategorileri şunlardır:  
  
- **Yükleniyor.** Uygulamayı ilk kez yüklediğinde alınırken uygulama kaynakları ve ayrıştırma HTML ve CSS harcanan zamanı belirtir. Bu işlem, ağ isteklerini içerebilir.  
  
- **Komut dosyası.** Harcanan süre ayrıştırma ve JavaScript çalıştırma gösterir. Bu, DOM olaylarını, zamanlayıcıları, betik yorumlamalarını ve animasyon çerçeve iş içerir. Bu, kullanıcı kodu hem kitaplık kodu içerir.  
  
- **GC.** Çöp toplama üzerinde harcanan zamanı gösterir.  
  
- **Stil.** CSS ayrıştırma ve hesaplama öğe sunumunu ve yerleşimini harcanan zamanı belirtir.  
  
- **İşleme.** Saati gösteren ekran boyama harcanan.  
  
- **Görüntü kodu çözme.** Resimlerin genişletilmesine ve kod harcanan zamanı belirtir.  
  
  Betik ve stil kategorileri için kullanıcı Arabirimi yanıtlama hızı Profiler zaman çizelgesi ayrıntıları grafikte üzerinde işlem yapabileceğiniz veri sağlayabilir. Bir sorun kodlama sorunları tanımlamak, CPU örnekleme Profil Oluşturucu ile kullanıcı Arabirimi yanıtlama hızı Profiler çalıştırabilirsiniz. Alternatif olarak, ayrıntılı verileri almak için Visual Studio işlevi Profiler'ı kullanabilirsiniz. Daha fazla bilgi için bkz. [JavaScript işlev zamanlaması analiz verileri](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b).  
  
  Diğer olay kategorileri için Özellikler'ı uygulamanıza eklemek neden platform yan etkileri belirlemek mümkün olabilir, ancak bu durumda, kullanıcı Arabirimi yanıtlama hızı Profiler'ı kullanarak belirli performans sorunlarını çözmek mümkün olmayabilir.  
  
  Bu tablo, olayları ve açıklamalarının gösterir:  
  
|Olay|Olay kategorisi|Gerçekleşir,|  
|-----------|--------------------|-----------------|  
|CSS ayrıştırma|Yükleniyor|Yeni CSS içeriği karşılaşıldı ve CSS içeriği ayrıştırmak için bir girişimde bulunuldu.|  
|HTML Ayrıştırma|Yükleniyor|Yeni HTML içeriğiyle karşılaşıldı ve düğümlere içerik ayrıştırmayı ve DOM ağacına içerik eklemek için bir girişimde bulunuldu.|  
|HTTP isteği|Yükleniyor|DOM'da uzak bir kaynak bulunamadı veya HTTP isteğinden sonuçlanan bir XMLHttpRequest oluşturuldu.|  
|Kurgusal indirme|Yükleniyor|Sayfanın HTML içeriğinde için gerekli kaynakları Aranan böylece sonraki HTTP istekleri kaynaklar için hızlı bir şekilde zamanlanabilir.|  
|Animasyon çerçevesi geri çağırma işlevi|Betik Oluşturma|Tarayıcıda başka bir çerçeveyi işlemeye devam ve bu, Tetiklenmiş bir uygulama tarafından sağlanan geri çağırma işlevi.|  
|DOM olayı|Betik Oluşturma|DOM olayı oluştu ve yürütülmesi.<br /><br /> `context` DOM olay özelliği gibi `DOMContentLoaded` veya `click`, parantez içinde gösterilir.|  
|Olay dinleyicisi|Betik Oluşturma|Olay dinleyicisi olarak adlandırılan ve yürütüldü.|  
|Medya sorgusu dinleyicisi|Betik Oluşturma|Kayıtlı bir medya sorgusu, sorgunun dinleyenleri yürütme sonuçlandı geçersiz kılındı.|  
|Mutasyon gözlemcisi|Betik Oluşturma|Bir veya daha fazla DOM öğeleri değiştirildi, hangi MutationObserver'ın ilişkili geri çağırması yürütme sonuçlandı gözlemledik.|  
|Betik yorumlama|Betik Oluşturma|DOM'da yeni bir BETİK öğesi bulundu ve ayrıştıracak ve komut dosyası için bir girişimde bulunuldu.|  
|Zamanlayıcı|Betik Oluşturma|Zamanlanmış bir Zamanlayıcının geçen ve bu, ilişkili geri çağırma işlevinin yürütme sonuçlandı.|  
|Windows çalışma zamanı zaman uyumsuz geri çağırma işlevi|Betik Oluşturma|Tetiklenen zaman uyumsuz bir işlemi bir `Promise` geri çağırma işlevi, bir Windows çalışma zamanı nesnesi tarafından tamamlandı.|  
|Windows çalışma zamanı olayı|Betik Oluşturma|Bir Windows çalışma zamanı nesnesi üzerinde oluşan olaya kayıtlı bir dinleyiciyi tetikleyen.|  
|Atık toplama|GC|Artık kullanımda olan nesneler için bellek toplamaya harcanan süre.|  
|CSS hesaplama|Stil oluşturma|Hesaplanacak etkilenen tüm öğelerin stil özelliklerinin gerekli DOM'da değişiklikler yapıldı.|  
|Düzen|Stil oluşturma|Boyutunun ve/veya konumunun hesaplanmasını etkilenen tüm öğelerin DOM'da değişiklikler yapıldı.|  
|Boyama|işleme|DOM'da görsel değişiklikler yapıldı ve sayfasının bölümlerini yeniden oluşturmak için bir girişimde bulunuldu.|  
|İşleme katmanı|işleme|DOM (katman olarak bilinir) bağımsız olarak işlenen bir parçasında görsel değişiklikler yapıldı ve işlenecek sayfasının bir bölümü değişiklik gerekli.|  
|Görüntü kodu çözme|Görüntü kodu çözme|Görüntü DOM eklenmiştir ve sıkıştırmasını açın ve özgün biçiminde görüntüden bir bit eşleme kodunu çözmek için bir girişimde bulunuldu.|  
|Çerçeve|Yok|DOM'da etkilenen tüm bölümleri sayfasının yeniden çizilmesini gerektiren görsel değişiklikler yapıldı. Gruplandırma için kullanılan bir araç tarafından oluşturulan olay budur.|  
|Kullanıcı ölçümü|Yok|Uygulamaya özel bir senaryo kullanma ölçülmüştür `performance.measure` yöntemi. Kod çözümlemesi için kullanılan bir araç tarafından oluşturulan olay budur.|  
  
##  <a name="Tips"></a> Ek bilgi  
  
-   İzleme [bu videoyu](http://channel9.msdn.com/Events/Build/2013/3-316) kullanıcı Arabirimi yanıtlama hızı Profiler hakkında derleme 2013 konferansına ait.  
  
-   JavaScript kullanarak Windows için oluşturulan Windows Store uygulamaları için performans ipuçları okuyun. Daha fazla bilgi için bkz. [JavaScript kullanan Windows Store uygulamaları için en iyi performans](http://msdn.microsoft.com/library/windows/apps/hh465194.aspx).  
  
-   Tek iş parçacıklı kod yürütme modeli ve performans ile ilgili daha fazla bilgi için bkz. [kodu yürüten](http://msdn.microsoft.com/library/windows/apps/hh781217.aspx).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama performansını analiz edin](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)



