---
title: 'Nasıl yapılır: uzantı performansını tanılama | Microsoft Docs'
ms.custom: ''
ms.date: 11/08/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: douge
ms.workload:
- bertaygu
ms.openlocfilehash: d1f2942c9f5987a686226c94e9764b8ab6300050
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934931"
---
# <a name="measuring-extension-impact-in-startup"></a>Başlangıç uzantısı etkileri ölçme

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Visual Studio 2017 uzantı performansını odaklanın

Müşteri geri bildirimi doğrultusunda, Visual Studio 2017 sürüm için odak alanlarından başlangıç ve çözüm yükleme performansını olmuştur. Visual Studio platformu ekibi, başlangıç ve çözüm yükleme performansını geliştirme konusunda durmaksızın çalışıyoruz. Genel olarak, bu senaryolara yüklü uzantılar da önemli bir etkisi olabilir bizim ölçümleri önerin.

Bu etkiyi anlayıp anlamadığını yardımcı olmak için yeni bir özellik yavaş uzantılarının kullanıcılara bildirmek için Visual Studio'da ekledik. Bazı durumlarda, Visual Studio çözüm yükünü veya başlangıç aşağı yavaşlatır yeni bir uzantı algılar. Yavaşlama tespit edildiğinde, kullanıcılar bunları işaret eden yeni "Visual Studio performansını Yönet" iletişim kutusu IDE'de bir bildirim görür. Bu iletişim kutusunu de her zaman daha önce algılanan uzantılara Gözat Yardım menüsü tarafından erişilebilir.

![Visual Studio performansını Yönet](media/manage-performance.png)

Uzantı geliştiricileri, uzantı etkisi nasıl hesaplandığını açıklayarak yardımcı olmak için bu belgede amaçlar. Bu belge, ayrıca nasıl uzantısı etkisi yerel olarak çözümlenebilir açıklar. Yerel olarak uzantısı etkisini çözümleme uzantısı etkileyen bir performans gösterilebilir uzantı belirler.

> [!NOTE]
> Bu belge, başlangıç ve çözüm yükleme uzantıları etkisini odaklanır. Bunlar UI yanıt veremez duruma gelmesine neden olduğunda uzantıları ayrıca Visual Studio performansını etkiler. Bu konu hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzantılardan kaynaklanan kullanıcı Arabirimi tanılama gecikmeleri](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Uzantıları başlangıç nasıl etkileyebileceğini

Başlangıç performansı etkileyen uzantıları için en yaygın yollarından otomatik yük NoSolutionExists veya ShellInitialized gibi bilinen Başlangıç UI bağlamları birini seçerek biridir. Bu UI bağlamı başlatma sırasında devreye. Dahil herhangi bir paket `ProvideAutoLoad` özniteliği bu bağlamı ile kendi tanımındaki yüklendi ve o anda başlatılır.

Şu uzantı etkisini ölçmek, öncelikli olarak yukarıdaki bağlamlarda otomatik yük tercih bu uzantıları tarafından harcanan süre odaklanıyoruz. Ölçülen süreleri dahil ancak bunlarla sınırlı değildir:

* Uzantı derleme zaman uyumlu paketleri yükleniyor
* Zaman uyumlu paketleri paket sınıfı oluşturucusunda harcanan süre
* Paket başlatma (veya SetSite) yönteminde zaman uyumlu paketler için harcanan süre
* Zaman uyumsuz paketler için yukarıdaki işlemleri arka plan iş parçacığında çalışır.  Bu nedenle, işlemler, izlemeden hariç tutulur.
* Paket başlatma sırasında ana iş parçacığı üzerinde çalışmak üzere zamanlanmıştır. herhangi bir zaman uyumsuz iş harcanan süre
* Olay işleyicileri, özellikle başlatılmamış Kabuk bağlam etkinleştirme veya kabuk zombi durum değişikliği için harcanan süre
* Visual Studio 2017 güncelleştirme 3 ' başlayarak, ayrıca Kabuk başlatılmadan önce boşta çağrılarında harcanan süre izleme başlayacağız. Boşta işleyicilerde uzun işlemler ayrıca yanıt vermeyen IDE neden ve kullanıcı tarafından algılanan başlangıç zamanını katkıda bulunun.

Visual Studio 2015'ten itibaren birçok özelliği ekledik. Bu özellikler, otomatik yük paketler için gereken kaldırma ile yardımcı olur. Özellikleri, ayrıca daha belirli çalışmalarına yüklenecek paketler için gereken erteleyin. Bu gibi durumlarda ise kullanıcılar uzantıyı kullanabilir veya otomatik olarak yüklenirken bir uzantı etkisini azaltmak belirli daha olacağı örnek olarak verilebilir.

Aşağıdaki belgelerde bu özellikler hakkında daha fazla ayrıntı bulabilirsiniz:

[Kural tabanlı UI bağlamı](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): oluşturulan kullanıcı Arabirimi bağlamları daha zengin bir kural tabanlı altyapısı, özellikleri, proje türlerine göre özel bağlamları oluşturmanıza olanak sağlar ve öznitelikleri. Özel bağlamları daha özel senaryoları sırasında bir paket yüklemek için kullanılabilir. Bu belirli senaryolar başlangıç yerine belirli bir özelliğine sahip bir proje varlığını içerir. Ayrıca özel bağlamları izin [komutu için özel bir bağlam bağlanması için görünürlük](visibilityconstraints-element.md) proje bileşenleri veya kullanılabilir başka koşullar göre. Bu özellik bir komut durumu Sorgu işleyici kaydetmek için bir paket yükleme gereğini ortadan kaldırır.

[Zaman uyumsuz paket desteği](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Visual Studio paketleri paket yükleme, otomatik yük özniteliği veya bir zaman uyumsuz hizmet sorgu tarafından istendi, zaman uyumsuz olarak arka planda yüklenecek Visual Studio 2015'te yeni AsyncPackage temel sınıf sağlar . Bu arka plan IDE yanıt vermeye devam edebilir yüklenmesine izin verir. Uzantı arka planda başlatılır ve başlangıç ve çözüm yükleme gibi kritik senaryolar etkilenen mıydı bile olsa, IDE yanıt veriyor.

[Zaman uyumsuz Hizmetleri](how-to-provide-an-asynchronous-visual-studio-service.md): zaman uyumsuz paket desteği sayesinde, hizmetleri zaman uyumsuz olarak sorgulamak ve zaman uyumsuz Hizmetleri kaydettirebilir için destek ekledik. Çoğu zaman uyumsuz sorgu iş arka plan iş parçacıklarında gerçekleşmesi zaman uyumsuz sorgu desteklemek için temel Visual Studio Hizmetleri dönüştürmeyle ilgili daha da önemlisi çalışıyoruz. SComponentModel (Visual Studio MEF ana bilgisayarı) artık tamamen zaman uyumsuz yüklemeyi destekleyecek kadar uzantılarına izin vermek için zaman uyumsuz sorgu desteklediği önemli hizmetler biridir.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Otomatik etkisini azaltma uzantılar yüklendi

Bir paket hala başlangıçta yüklenen otomatik olarak yapması gerekiyorsa, paket başlatma sırasında çalışmanın en aza indirmek önemlidir. Paket başlatma çalışmayı en aza başlangıç etkileyen uzantı olasılığını azaltır.

Paket başlatma pahalı neden olabilecek bazı örnekler şunlardır:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Zaman uyumsuz paket yükleme yerine zaman uyumlu paket yük kullanımı

Zaman uyumlu paketleri ana iş parçacığı üzerinde varsayılan olarak yüklenir çünkü zaman uyumsuz paket taban sınıfı yerine daha önce bahsedildiği gibi kullanmak için otomatik yüklenen paketler sahip uzantı sahipleri öneririz. Zaman uyumsuz yükleme desteklemek için bir otomatik yüklenen paket değiştirme ayrıca aşağıdaki diğer sorunları gidermek kolaylaştırır.

### <a name="synchronous-filenetwork-io-requests"></a>Zaman uyumlu bir dosya/ağ g/ç isteği

İdeal olarak ana iş parçacığında eşzamanlı dosya veya ağ g/ç istek kaçınılmalıdır. Etkilerine makine durumuna bağlı olacaktır ve bazı durumlarda uzun süreler için engelleyebilirsiniz.

Zaman uyumsuz paketi yükleme ve zaman uyumsuz g/ç API'leri kullanarak ana iş parçacığı bu gibi durumlarda, paket başlatma engellemediğinden emin olmanız gerekir. Ayrıca, kullanıcılar g/ç istekleri arka planda gerçekleşir, ancak Visual Studio ile etkileşim kurmak devam edebilirsiniz.

### <a name="early-initialization-of-services-components"></a>Hizmet bileşenleri erken başlatma

Paket başlatma ortak yaklaşımlar biri tarafından kullanılan veya bu pakette bir paket tarafından sağlanan hizmetleri başlatmak için `constructor` veya `initialize` yöntemi. Bu hizmetleri kullanılmaya hazır olmasını sağlar, ancak bu hizmetlere hemen kullanılmıyorsa yükleme paketini gereksiz maliyeti de ekleyebilirsiniz. Bunun yerine paket başlatmanın çalışmayı en aza indirmek için isteğe bağlı tür hizmetlerin başlatılması gerekir.

Bir paketi tarafından sağlanan küresel hizmetler için kullandığınız `AddService` yöntemleri yalnızca bir bileşen tarafından istendiğinde gevşek hizmeti başlatmak için bir işlevi alır. Lazy kullanabileceğiniz paket içinde kullanılan hizmetler için<T> veya AsyncLazy<T> Hizmetleri başlatılmış/sorgulanan ilk kullanımda olduğundan emin olmak için.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Etkinlik günlüğü kullanarak uzantılara otomatik etkisini ölçmek yüklendi

Visual Studio 2017 güncelleştirme 3'te başlayarak, Visual Studio etkinlik günlüğü artık girişleri performans etkisini paketleri için başlangıç ve çözüm yükleme sırasında içerir. Bu ölçümler görmek için Visual Studio'yu/log anahtarı ile başlatın ve açmak sahip *ActivityLog.xml* dosya.

Etkinlik günlüğü'ndeki girişleri altında "Visual Studio performansını Yönet" kaynağı olur ve aşağıdaki örnekteki gibi görünecektir:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Bu örnek, bir paket GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" ile Visual Studio 2008 ms başlangıç harcadığı gösterir. Visual Studio, bu paket uzantısı devre dışı bıraktığınızda tasarruf kullanıcıları görmek olduğu gibi bir paket etkisini hesaplarken birincil sayı olarak en üst düzey maliyet dikkate unutmayın.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Otomatik etkisini ölçülmesine PerfView kullanma uzantılar yüklendi

Kod Analizi paketi başlatma yavaşlatabilir kod yollarını belirlemeye yardımcı olabilecek olsa da Visual Studio başlangıç paketi yük etkisini anlamak için PerfView gibi uygulamaları kullanarak izlemeyi de kullanabilir.

PerfView sistem genelinde izleme aracıdır. Bu araç, CPU kullanımı veya sistem çağrıları engelleyici nedeniyle, bir uygulamada etkin yolları anlamak yardımcı olur. PerfView adresinde kullanarak bir örnek uzantısı çözümleme hakkında hızlı bir örnek aşağıdadır [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Örnek kod:**

Bu örnekte, örneği temel göstermek için tasarlanmış olan aşağıdaki kod, bazı yaygın gecikme nedenleri durumda:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Bir izleme PerfView ile kaydetme:**

Yüklü uzantınız ile Visual Studio ortamınızı ayarladıktan sonra PerfView açma ve açma başlangıç izlemesi kaydedebilirsiniz **toplamak** iletişim kutusundan **toplamak** menüsü.

![perfview toplama menüsü](media/perfview-collect-menu.png)

CPU tüketimi için varsayılan seçenekleri çağrı yığınları sağlar ancak biz de engelleme sürede ilgi olduğundan, ayrıca etkinleştirmelisiniz **iş parçacığı zaman** yığınları. Ayarları hazır olduğunuzda tıklayabilirsiniz **toplamaya Başla** ve kayıt başlatıldıktan sonra Visual Studio'yu başlatın.

Koleksiyon durdurmadan önce Visual Studio tamamen başlatılır, otomatik olarak gösteren bir UI parçalarını uzantınız varsa bunlar da görülebilir ve, ana pencereyi tamamen görünür olduğundan emin olmanız gerekir. Visual Studio tamamen yüklendikten sonra uzantınızı başlatılır, izlemeyi analiz etmek için kaydı durdurabilirsiniz.

**Bir izleme PerfView ile analiz ediliyor:**

Kayıt tamamlandıktan sonra PerfView otomatik olarak izlemeyi açmak ve Seçenekleri'ni genişletin.

Bu örneğin amacı doğrultusunda, biz ağırlıklı olarak ilgilendiğiniz **iş parçacığı zamanı yığınları** altında bulabileceğiniz görünümü **Gelişmiş Grup**. Bu görünüm, hem CPU süresi ve disk g/ç veya tutamaçları bekleyen gibi engellenme süresi dahil olmak üzere bir yöntem tarafından bir iş parçacığı üzerinde harcanan toplam zamanı gösterir.

 ![iş parçacığı zamanı yığınları](media/perfview-thread-time-stacks.png)

 Açma sırasında **iş parçacığı zamanı yığınları** görünümünde, seçmeniz gereken **devenv** analiz başlatmak için işlem.

PerfView zamanı yığınları daha ayrıntılı analiz için kendi Yardım menüsü altında iş parçacığı okuma hakkında yönergeler ayrıntılı içerir. Bu örneğin amacı doğrultusunda, bu görünümü yalnızca bizim paketleri modül adı ve başlangıç iş parçacığı yığınlarıyla dahil ederek filtre istiyoruz.

1. Ayarlama **GroupPats** varsayılan olarak eklenen herhangi bir gruplama kaldırmak için boş metin.
2. Ayarlama **IncPats** derleme adı ve başlangıç iş parçacığı mevcut filtresi ek dahil edilecek. Bu durumda, olmalıdır **devenv; Başlangıç iş parçacığı; MakeVsSlowExtension**.

Görünümü artık yalnızca uzantısı ilgili derlemeleri ile ilişkili olan maliyet gösteriyor. Bu görünümde, istediğiniz zaman, altında listelenen **dahil edilen (kapsamlı maliyeti)** başlangıç etkileyen ve filtrelenmiş uzantımızı ilgili başlangıç iş parçacığı sütunu.

Örneğin yukarıdaki bazı ilginç çağrı yığınlarını olacaktır:

1. GÇ kullanarak `System.IO` sınıfı: Bu kareler kapsamlı maliyetini izlemede çok pahalı olmayabilir ancak dosya g/ç hızı makineden makineye farklılık gösterir, soruna neden olabilir olduğundan.

   ![Sistem g/ç çerçeveler](media/perfview-system-io-frames.png)

2. Diğer zaman uyumsuz işler, bekleyen çağrılar engelleme: kapsamlı süre bu durumda, ana iş parçacığı, zaman uyumsuz iş tamamlanma engellendi süreyi temsil eder.

   ![engelleme çağrı çerçeveler](media/perfview-blocking-call-frames.png)

Diğer görünümlerde etkisini belirlemek yararlı olacak izleme biri olacak **görüntü yük yığınları**. Aynı Filtreler uygulanmış olarak uygulayabilirsiniz **iş parçacığı zamanı yığınları** görüntülemek ve otomatik yüklenen paketi tarafından çalıştırılan koda nedeniyle yüklenmiş tüm derlemeleri bulabilirsiniz.

Her ek derleme, başlangıç daha yavaş makinelerde önemli ölçüde yavaşlatabilir ek disk GÇ içerecektir gibi bir paket başlatma yordamı içine yüklenen derlemeler sayısını en aza indirmek önemlidir.

## <a name="summary"></a>Özet

Visual Studio Başlangıç sürekli geri bildirim aldığımız üzerinde alanlarından olmuştur. Hedefimiz daha önce belirtildiği gibi tüm kullanıcıların deneyimi bileşenleri ve uzantıları yüklü olduğu bağımsız olarak tutarlı bir başlangıç içindir. Bu hedefe ulaşmak yardımcı yardımcı olmak için uzantı sahipleriyle birlikte çalışmak istiyoruz. Yukarıdaki yönergeleri uzantıları etkilenmesinden başlangıç anlaşılması ve ya da otomatik olarak yük veya zaman uyumsuz olarak kullanıcının üretkenliği üzerindeki etkiyi en aza indirmek için yüklemek için gereken önleme yardımcı olabilir.
