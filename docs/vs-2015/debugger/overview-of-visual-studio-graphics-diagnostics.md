---
title: Grafik Tanılama'ne genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4ff1b4b74dae005b48f297fa26413fd371fe3f1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051423"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio *grafik tanılama* kaydetme ve ardından Direct3D uygulamalar oluşturma ve performans sorunları çözümleme araçları kümesidir. Grafik Tanılama, Windows PC, bir Windows cihaz öykünücüsü veya bir uzak bilgisayar veya cihaz üzerinde yerel olarak çalışan uygulamalarda kullanılabilir.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>İşleme sorunlarında hata ayıklamak için Grafik Tanılama'yı kullanma
 Grafik açısından zengin bir uygulamada işleme sorunları hatalarının ayıklanması, hata ayıklayıcıyı başlatıp herhangi bir kodda adım adım ilerlemek kadar basit işlem değildir. Her kare içinde, her biri karmaşık bir durum, veri, parametre ve kod kümesine göre olmak üzere yüz binlerce benzersiz piksel üretilirken, tanılamaya çalıştığınız sorunu bunlar arasında belki de yalnızca birkaç piksel sergileyecektir. He bir pikseli üreten kodun, yüzlerce pikseli paralel olarak işlemden geçiren özel amaçlı donanımlarda yürütülmesi meseleyi daha da karmaşık bir hale getirir. Çok fazla veriyle karşı karşıya kalındığında, iş parçacıklarının yoğun olmadığı kodlarda bile yarar sağlanması zor olan geleneksel hata ayıklama araçları ve teknikleri etkisiz kalmaktadır.

 İçindeki grafik tanılama araçları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sorun ve sonra geri sorunun kaynağına yalnızca alakalı gölgelendirici koduna, odaklanarak izleme işlem hattı gösteren görsel yapılarla başlatarak işleme sorunlarını bulmanıza yardımcı olmak için tasarlanmıştır Aşama, çizim çağrıları, kaynaklar ve cihaz durumu — uygulamanın kendi kaynak kodunda.

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu
 Grafik tanılama Direct3D 12, Direct3D 11 ve Direct3D 10 kullanan uygulamaları destekler ve Direct2D kullanan uygulamalar için sınırlı destek sağlar. Direct3D, DirectDraw veya diğer grafik API'lerinin önceki sürümlerini kullanan uygulamaları desteklemez.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 ve Direct3D 12
 Windows 10, Direct3D'ın sonraki sürümü tanıtır *Direct3D 12*, Direct3D 11 ve Direct3D 10 arasında önemli ölçüde farklı olduğu. Bu farklar DirectX geri modern grafik donanımının ve tam potansiyelini unleashing ile aynı doğrultuda içine taşıyın, ancak ayrıca büyük API değişiklikleri getirmek ve kaynak yaşam süreleri ve Çekişme yönetmek için programcı büyük sorumluluk yerleştirin. Sahip olmak harika hata ayıklama araçları, Visual Studio 2015'te grafik tanılama Direct3D12 destekler. böylece bu geçiş baştan doğru yapmak grafik programcılar yardımcı olmak önemlidir. Farklar rağmen grafik tanılama Direct3D 12 çerçeve analizi özelliği geçerli durumun özellik-eşliği ile grafik tanılama Direct3D 11.2 ile tutar. Yakında, Direct3D 12'deki karşılaşabileceğiniz hatalar yeni tür gidermenize yardımcı olacak yeni tanılama araçları ardından Direct3D 12 çerçeve analizi için destek eklenecektir.

 Windows 10, Direct3D oyun ve bunlar üzerinde dayanan uygulamalar, önceki sürümleri için destek de korur. Visual Studio 2015'te grafik tanılama Direct3D 10 ve Direct3D 11 Windows 10 yanı sıra Windows 8.1 desteklemeye devam eder.

### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 ve Direct3D 11.2
 İçinde [!INCLUDE[win81](../includes/win81-md.md)], DirectX 11.2, çalışma zamanı aracılığıyla grafik bilgilerini yakalama için destek içeren yeni özellikleri tanıtır. [!INCLUDE[win81](../includes/win81-md.md)] Yeni çalışma zamanı tabanlı yakalama kullanır; olarak bilinen *sağlam yakalama*— DirectX tüm sürümleri için özel olarak, [!INCLUDE[win81](../includes/win81-md.md)] destekler. Güçlü yakalama Direct3D 11.2'ün yeni özelliklerini de destekler.

### <a name="limited-direct2d-support"></a>Sınırlı Direct2D desteği
 Direct2D, Direct3D üzerine kurulu bir kullanıcı modu API'si olduğundan, Direct2D kullanan uygulamalarda işleme sorunlarındaki hataları ayıklamaya yardımcı olması için Grafik Tanılama'yı kullanabilirsiniz. Bununla birlikte, üst düzey Direct2D olayları yerine yalnızca temeli oluşturan Direct3D olayları kaydedildiğinden, Direct2D olayları Grafik Olay Listesi'nde görünmez. Ayrıca, Direct2D olayları ve sonuç Direct3D olayları arasındaki ilişki her zaman net olmadığından, Direct2D kullanan uygulamalarda işleme sorunları hatalarını ayıklamak için Grafik Tanılama kullanılması her zaman basit değildir. Yine de, Direct2D kullanan uygulamalarda düşük düzeyli işleme sorunları hakkında bilgi almak için Grafik Tanılama'yı kullanabilirsiniz.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Visual Studio grafik tanılama özellikleri
 Grafik Tanılama, adanmış bir arabirimi vardır — grafik Çözümleyicisi penceresi-için işleme sorunları, ancak tanılama ayrıca bazı araçlar Visual Studio ekler.

### <a name="the-graphics-toolbar-visual-studio"></a>Grafik araç çubuğu (Visual Studio)
 Grafik araç çubuğu, grafik tanılama komutlarına hızlı erişim sağlar.

 **Tanılamayı Başlat** düğmesi uygulamayı grafik tanılama altında çalıştırır. Bir uygulama grafik tanılama altında çalışırken **sonraki kareyi Yakala** düğmesi etkinleşir.

### <a name="diagnostics-capture-interface"></a>Tanılama yakalama arabirimi
 Uygulamanızı grafik tanılama altında çalıştırdığınızda, Visual Studio çerçeveleri yakalamak için kullanabilirsiniz ve ayrıca geçerli CPU ve GPU yük görüntüleyen bir tanılama oturumu arabirimini görüntüler. CPU ve GPU yük, kendi performans özellikleri yerine nedeniyle işleme hataları yakalamak isteyebileceğiniz çerçeveler tanımlamanıza yardımcı olması için görüntülenir.

 Bu çerçeve ancak yakalamak için tek yolu değildir. Programlı yakalama arabirimini kullanarak veya komut satırı yakalama programını kullanarak da kare yakalayabilirsiniz dxcap.exe.

 Bkz: [Capturing Graphics Information](../debugger/capturing-graphics-information.md) daha fazla bilgi için.

### <a name="gpu-usage"></a>GPU Kullanımı
 Grafik tanılama Direct3D uygulamanızın performansını da profilini oluşturabilirsiniz. Profil oluşturma verilerini grafik olaylarını tarafından kaydetme ayrıntılarını dengesiz çünkü bu kullanılacak çerçeveleri yakalamasını önler ayrı grafik Çözümleyicisi ile incelenir.

 Bkz: [GPU kullanımı](../debugger/gpu-usage.md) daha fazla bilgi için.

### <a name="directx-control-panel"></a>DirectX denetim masası
 DirectX denetim masası, DirectX'in davranış şeklini değiştirmek için kullanabileceğiniz bir DirectX bileşenidir; örneğin, DirectX çalışma zamanı bileşenlerinin hata ayıklama sürümünü etkinleştirebilir, raporlanan hata ayıklama iletilerinin türünü seçebilir ve daha düşük kapasiteli donanımlara öykünmek için belirli grafik donanımı yeteneklerinin kullanılmasına izin vermeyebilirsiniz. DirectX üzerinde bu düzeyde bir denetim DirectX uygulamanızda hata ayıklamanıza ve uygulamayı test etmenize yardımcı olabilir. DirectX denetim masasına Visual Studio'dan erişebilirsiniz.

##### <a name="to-open-the-directx-control-panel"></a>DirectX denetim masasını açmak için

-   Menü çubuğunda, **hata ayıklama**, **grafik**, **DirectX Denetim Masası'ndaki**.

## <a name="graphics-analyzer"></a>Grafik Çözümleyicisi
 Visual Studio grafik Çözümleyicisi zaten yakalanan çerçeve işleme ve performans sorunları incelemek için adanmış bir arabirimdir. Grafik Çözümleyicisi keşfedin ve uygulamanızı işleme davranışını anlamanıza yardımcı olacak birkaç araç bulabilirsiniz. Her aracı farklı türde bir, denetlenen kare hakkında bilgiler sunar ve Araçlar, sezgisel dar başlayarak bir işleme sorunun kaynağı için birlikte kullanılmak üzere tasarlanmıştır framebuffer görünümüne.

 Bu örnekte, grafik Çözümleyicisi'nde araçlar tipik yerleşimi gösterilmiştir.

 ![Tüm grafik hata ayıklayıcısı pencereleri](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Grafik araç çubuğu (grafik Çözümleyicisi)
 Grafik araç çubuğu, grafik Çözümleyicisi araç pencerelerini hızlı erişim sağlar.

 ![Grafik araç çubuğu grafik tanılama modunda](../debugger/media/vsg-toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Grafik günlük belgesi
 Grafik Çözümleyicisi grafik günlük belgesi en önemli araç penceresidir. Bu pencere tüm uygulamanızı grafik tanılama altında çalışan tarafından yakalanan kareleri temsil eder. Buradan inceleyin veya piksel geçmişi aracıyla incelemek istediğiniz belirli bir pikseli seçmek için farklı bir çerçeve seçebilirsiniz. Bu belge değişiklikleri seçili olan olay framebuffer zaman içinde nasıl etkilendiğini görmenize olanak tanıyan yansıtmak için görüntülenen framebuffer resim.

 [Grafik günlük belgesi](../debugger/graphics-log-document.md) de yardımcı olur çerçeve analizi aracı için giriş noktası anlamak çerçevenin performans yapılandırılmış olan belirli yönlerini işleme biçimini değiştirme ve kıyaslama sonuçları sağlayarak özgün sürümle karşılaştırın.

### <a name="event-list"></a>Olay listesi
 Grafik olaylarını her Direct3D API çağrısı ve kullanıcı tanımlı olay'ı işaretleyin.

 [Olay listesi](../debugger/graphics-event-list.md) tüm incelemekte çerçeve sırasında kaydedilmiş grafik olaylarını gösterir. Önemli olan bulmanıza yardımcı olmak için olay listesi hiyerarşik olarak görüntülenebilir — son durum değişikliği altındaki sonraki çağrı çizmek — veya bir zaman çizelgesi olarak. Ayrıca, ait oldukları sıraya göre olaylar kodludur ve yalnızca ilgilendiğiniz olayları dahil etmek için listeyi filtreleyebilirsiniz.

 Listesinde bir olay seçtiğinizde, grafik analizi araçları geri kalanı, Olay sırasındaki çerçeve durumunu yansıtır. Bu şekilde, GPU üzerinde herhangi bir olay etkisini görebilirsiniz. Örneğin, sonraki çizim çağrıları'na göre engellediği olur bile herhangi bir çizim anlık etkisini framebuffer üzerinde çağrı görebilirsiniz. Bazı olayları, parametre veya ilişkili kaynak nesneleri hakkında daha fazla ayrıntı için izlemeniz gereken bir köprü de var.

### <a name="pipeline-stages"></a>Ardışık Düzen aşamaları
 Direct3D tarafından sağlanan grafik ardışık düzeninden uygulamanızdaki her bir çizim çağrısına gider. İşlem hattındaki her bir aşamada, önceki aşamanın çıktısı küçük bir program tarafından dönüştürülür, gölgelendirici adlı ve ekrana son işlenen kadar sonraki aşamaya ardından geçirilir. Çıkış biçimi sonraki aşamasına beklediğinden ya da tek bir aşamada yalnızca hatalı sonuçlar üreten farklı olduğunda ardışık düzen aşamaları arasında sınırında birçok işleme hataları oluşur. Normalde, yalnızca son sonuçları ekranda görür ve işlem hattı, hatanın oluştuğu kolayca bildiremez sahip olursunuz.

 [Ardışık düzen aşamaları](../debugger/graphics-pipeline-stages.md) penceresi görselleştirir sonucu, her bir aşamaya bağımsız olarak, hangi aşamada daha kolay belirleyebilirsiniz bir işleme sorunun ilk görünür. Diğer bir deyişle, aşama saptadıktan sonra sağa ardışık düzen aşamaları penceresinden, gölgelendirici hata ayıklamaya başlayabilirsiniz.

### <a name="graphics-state"></a>Grafik Durumu
 Oluşturma işlemleri, genellikle birden fazla nesne arasında yayılır durumu çok bağlıdır. Çok çeşitli işleme sorunları, yanlış yapılandırılmış durumuna göre neden olur.

 [Durumu](../debugger/graphics-state.md) penceresini bulmak daha kolaydır ve önceki itibaren gerçekleşen durum değişiklikleri vurgular arama de çizin tek bir yerde birlikte her çizim çağrısı ile ilgili durum bilgilerini toplar.

### <a name="pixel-history"></a>Piksel geçmişi
 Karmaşık sahneler için birden çok kez tek bir çerçevede gölgeli bir piksel seyrek değil. Bazen önceki renk renkleri birleştirilir yalnızca üzerine, ancak diğer katıdır birlikte saydamlık gibi efektler elde etmek için. Bunları birbirine birleştirmek sonucunu doğru görünümü sahip olmadığında bir renge yanlış veya yolu ile ilgili bir sorun varsa birleştirilen olup olmadığını kolayca bildiremez. Diğer durumlarda, bir nesne katkıyı piksel herhangi bir nedenden dolayı reddedildiği için eksik olduğu görünebilir.

 [Piksel geçmişi](../debugger/graphics-pixel-history.md) pencere çerçevesinde, reddedilen Katkıları da dahil olmak üzere her pikselin tam gölgelendirici geçmişi görselleştirir. Reddedilen olmayan katkılar için ham gölgelendirici sonuçlarını ve her yeni renk Öncekine ile nasıl birleştirilmiş görüntüler. Bu bilgilere sahip olarak, gölgelendirici sonuçları blend veya bir işlenen nesnesi katkıyı piksel yanlış reddedildiği için ne zaman eksik piksel cinsinden hataları kaynağı bulmak çok daha kolay olur.

### <a name="event-call-stack"></a>Olay Çağırma yığını
 Gölgelendirici kodunda bir Direct3D uygulaması işleme sorunlarındaki yalnızca kaynağı değilse, bazen uygulamanızın kaynak kodu yanlış parametre geçirir veya Direct3D oldukça doğru yapılandırmaz. Tüm piksel reddettiği için işlenen nesne eksik olduğunda daha önce bahsedildiği özelliğini piksel geçmişi bulmanıza yardımcı olabilecek hata için bir türüdür. Bu tür bir hatayı, genellikle bir ayarı yanlış gerçekleşir, genellikle bir derinlik testinde nasıl gerçekleştirildiğini denetler ve size, yanlış yere eksik nesnenin çağrı yığınında bulabilirsiniz gibi çizim çağrısı çıktılarının.

 [Olay çağrı yığını](../debugger/graphics-event-call-stack.md) penceresi olay listesinde her grafik olayı tam çağrı yığınını görüntüler ve hata ayıklama bilgileri kullanılabiliyorsa kaynak kodu, uygulamanızın bağlantı da sağlar. Öncelikle, uygulamanızın kaynak kodunda geldiği için geri GPU üzerinde göründüğü gelen bir hatadan sonra için güçlü bir araçtır.

### <a name="object-table"></a>Nesne tablosu
 Uygulama oluşturur, yüzlerce veya hatta kaynak nesneleri binlerce büyük olasılıkla yedeklenen her karede. Bu arka arabellek içerir ve işleme hedefleri, dokular, köşe arabellekleri, dizin arabelleklerinin, genel arabellekler — hemen Direct3D hatırlar her şeyi bir nesnedir.

 [Nesne tablosu](../debugger/graphics-object-table.md) tüm seçili grafik olay sırada mevcut nesneleri olay listesi görüntüler. Tipik bir uygulamada bulunan nesnelerin çoğu dokular olduğundan, olay listesi bir bakışta görüntüleri ile ilgili ayrıntıları göstermek için optimize edilmiştir. Tür sütunu, her satırda hangi nesne çeşidi olduğunu bildirir. ve alt türü veya nesnenin daha fazla biçim sütunu gösterir. Diğer ayrıntıları da gösterilir. Bazı nesneler (bir görüntü olarak doku görüntüleyebilirsiniz) doku ya da (arabellek Görüntüleyicisi'ni nasıl ayrıştırır ve ham arabelleği bayt arabelleği tanımlayarak görüntüler seçebilirsiniz arabellekleri gibi daha özel bir Görüntüleyici ile nesneyi görüntülemek için izlemeniz gereken bir köprü de vardır. Biçim için).

### <a name="frame-analysis"></a>Çerçeve analizi
 Uygulamanızın grafik yalnızca doğru olmasına gerek yok: çok daha hızlı olması gerekir. Daha az güçlü cihazlarda tümleşik grafik veya cep telefonları ile dizüstü bilgisayarlar gibi. Ve yine de çok harika görünecek gerekir.

 [Çerçeve analizi](../debugger/graphics-frame-analysis.md) aracı otomatik olarak uygulamanın kullandığı Direct3D biçimini değiştirme ve kıyaslama sonuçları karşılaştırma için sağlayarak olası performans iyileştirmelerini keşfediyor. Örneğin, çerçeve analizi MIP eşleme MIP eşlemesinden yararlı olabilir, ancak şu anda etkin olmayan dokular açığa her doku üzerinde etkinleştirebilirsiniz. Bunu destekleyen donanımlar üzerinde çerçeve analizi aynı zamanda GPU'nun performans sayaçlarından toplanan bilgiler sunar; bu bilgi düzeyi yüksek sayıda doku getirme takılma gibi donanım düzeyinde performans sorunlarını tanımlamak veya İsabetsiz Önbellek.

 Ancak çerçeve analizi hakkında hızlı bozmayacağı – en az miktarda görsel kaliteyi vererek while çoğu performans elde etme hakkında olduğunu. Bazen büyük bir ekranda harika göründüğünden pahalı efekt küçük ekranındaki burada daha basit bir etkisi olmadan pil boşaltma yalnızca kadar iyi görünebilir telefonda görüntülendiğinde aynı etkiyi yapmaz. Grafik analizi sağlayan değerlendirmesi ve otomatik değişiklikleri, bir cihaz yelpazesinde uygulamanız için doğru dengeyi bulmak yardımcı olabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Komut satırı Yakalama aracı](../debugger/command-line-capture-tool.md) [HLSL hata ayıklayıcısı](../debugger/hlsl-shader-debugger.md)
