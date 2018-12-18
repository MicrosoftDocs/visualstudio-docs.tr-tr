---
title: Performansı iyileştirmeye yönelik ipuçları
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1c4e55fe6275d750d3bc3b03fb8f0ac5eec2751
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672931"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Visual Studio performans ipuçları ve püf noktaları

Visual Studio performans önerisi, nadir durumlarda oluşabilir düşük bellek durumları yöneliktir. Bu gibi durumlarda değil kullanıyor olabileceğiniz bazı Visual Studio özellikleri iyileştirebilirsiniz. Aşağıdaki ipuçları, genel öneriler olarak tasarlanmamıştır.

> [!NOTE]
> Bellek sorunları nedeniyle ürün kullanmakta zorluk yaşıyorsanız aracılığıyla bize [geri bildirim aracı](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="use-a-64-bit-os"></a>Bir 64-bit işletim sistemi kullanın

Sisteminiz Windows 32-bit sürümünden bir 64 bit sürümüne yükseltirseniz, 2 GB ile 4 GB Visual Studio için kullanılabilir sanal bellek miktarını genişletirsiniz. 32 bit işlem olsa bile bu önemli ölçüde daha büyük iş yüklerini işlemek üzere Visual Studio sağlar.

Daha fazla bilgi için [bellek sınırlarını](/windows/desktop/Memory/memory-limits-for-windows-releases#memory_limits) ve [/largeaddressaware 64 bit Windows üzerinde kullanmak](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Otomatik dosya geri yükleme devre dışı bırak

Visual Studio, önceki oturumu açık bırakıldı belgeleri otomatik olarak açılır. Bu % 30 veya daha fazla proje türü ve açılmasını belgeleri bağlı olarak bir çözümü yüklemek için gereken uzatmak. Windows Forms, XAML ve bazı JavaScript ve typescript dosyaları gibi tasarımcıları açılması yavaş olabilir.

Visual Studio bir sarı çubuk, önemli ölçüde daha yavaş yüklemek bir çözüm otomatik belge geri yükleme ne zaman açtığını bildirir. Aşağıdaki adımları izleyerek otomatik dosya yeniden açmayı devre dışı bırakabilirsiniz:

1. Seçin **Araçları** > **seçenekleri** açmak için **seçenekleri** iletişim kutusu.

1. Üzerinde **proje ve çözüm** > **genel** sayfasında, seçimini **çözüm yükü belgelerde yeniden**.

Otomatik dosya geri yükleme devre dışı bırakırsanız, açmak istediğiniz dosyaları bulmak için hızlı bir şekilde birini kullanarak olan [Git](../ide/go-to.md) komutları:

- Genel için **Git** işlevi, select **Düzenle** > **Git** > **tümüne Git**, veya tuşunabasın **CTRL**+**T**.

- Visual Studio 2017 sürüm 15,8 ve daha sonra son bir çözüm kullanarak düzenleme konumu atlayabilirsiniz **Düzenle** > **Git** > **Git son Düzen konumuna**, veya basarak **Ctrl**+**Shift**+**geri**.

- Visual Studio 2017'de 15,8 ve sonraki sürümleri kullanın **son dosya** bir çözümde en son ziyaret edilen dosyaların listesini görmek için. Seçin **Düzenle** > **Git** > **son dosya**, veya basın **Ctrl** + **1**, **Ctrl**+**R**.

## <a name="configure-debugging-options"></a>Hata ayıklama seçeneklerini yapılandırma

Genellikle bellek hata ayıklama oturumları sırasında düşük çalıştırıyorsanız, bir veya daha fazla yapılandırma değişikliklerini yaparak performansı en iyi duruma getirebilirsiniz.

- **Yalnızca kendi kodumu etkinleştir**

    En basit iyileştirme etkinleştirmektir **yalnızca kendi kodum** yalnızca projeniz için sembolleri yükler özelliğine sahiptir. Bu özelliğin etkinleştirilmesi kaydetme (.NET) yönetilen uygulamalarda hata ayıklama için önemli bir bellek neden olabilir. Bu seçenek varsayılan olarak, bazı proje türleri zaten etkin.

    Etkinleştirmek için **yalnızca kendi kodum**, seçin **Araçları** > **seçenekleri** > **hata ayıklama**  >   **Genel**ve ardından **yalnızca benim kodumu etkinleştir**.

- **Yüklenecek semboller belirtin**

    Yerel hata ayıklama sembol dosyalarını yükleme (*.pdb*) bellek kaynaklarının açısından pahalıdır. Hata ayıklayıcı sembol ayarlarınızı bellekten kazanacak şekilde yapılandırabilirsiniz. Genellikle, yalnızca projenizden modülleri yüklemek için çözümü yapılandırın.

    Sembol yükleme belirtmek için **Araçları** > **seçenekleri** > **hata ayıklama** > **sembolleri**.

    Seçenekleri ayarlamak **yalnızca belirtilen modüller** yerine **tüm modüllerin** ve sizin yüklemek için hangi Modülü belirtin. Hata ayıklama sırasında aynı zamanda belirli modüller ne sağ tıklayarak **modülleri** açıkça bir modül sembol yükleme içerecek şekilde penceresi. (Hata ayıklama sırasında penceresini açmak için seçin **hata ayıklama** > **Windows** > **modülleri**.)

    Daha fazla bilgi için [sembol dosyalarını anlamak](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Tanılama araçları devre dışı bırak**

    Kullanımdan sonra CPU profili oluşturma devre dışı bırakmanız önerilir. Bu özellik, büyük miktarda kaynak tüketebilir. CPU profili oluşturma etkinleştirildikten sonra bu durum açıkça işiniz bittiğinde kapatmayı değer, bu nedenle sonraki hata ayıklama oturumları arasında kalıcıdır. Bazı kaynaklar, tanılama araçları sağlanan özelliklere ihtiyacınız yoksa hata ayıklama sırasında devre dışı bırakarak kaydedebilirsiniz.

    Devre dışı bırakmak için **tanılama araçları**, hata ayıklama oturumu başlatma öğesini **Araçları** > **seçenekleri** > **etkinleştirme tanılama Araçlar**ve bu seçeneğin işaretini kaldırın.

    Daha fazla bilgi için [profil oluşturma araçları](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Araçlar ve uzantılar devre dışı bırak

Bazı araçları veya uzantıları performansını artırmak için kapatılabilir.

> [!TIP]
> Performans sorunları genellikle, aynı anda uzantıları devre dışı bir kapatma ve yeniden denetleme performans da ayırabilirsiniz.

### <a name="managed-language-service-roslyn"></a>Yönetilen dil hizmeti (Roslyn)

.NET derleyici Platformu ("Roslyn") performans konuları hakkında daha fazla bilgi için bkz. [büyük çözümler için başarım düşünceleri](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Tam çözüm analizini devre dışı bırak**

    Visual Studio, bir derleme çağırmadan önce hatalar hakkında zengin bir deneyim sağlamak amacıyla tüm çözümünüz çözümleme gerçekleştirir. Bu özellik, olabildiğince çabuk hataları belirlemek yararlıdır. Ancak, büyük çözümler için önemli bellek kaynakları bu özelliği kullanabilir. Bellek baskısı veya benzer sorunlar yaşıyorsanız bu deneyim, bu kaynakları serbest bırakmak için devre dışı bırakabilirsiniz. Bu seçenek varsayılan olarak, Visual Basic için etkinleştirilir ve C# için devre dışı.

    Devre dışı bırakmak için **tam çözüm analizini**, seçin **Araçları** > **seçenekleri** > **metin düzenleyici**seçin Her iki **Visual Basic** veya **C#**. Seçin **Gelişmiş** ve seçimini **tam çözüm analizini etkinleştirme**.

- **CodeLens devre dışı bırak**

    Visual Studio gerçekleştiren bir **tüm başvuruları Bul** görüntülendiği her metodunda görev. CodeLens, satır içi görüntü başvuruları sayısı gibi özellikler sağlar. İş gibi ayrı bir işlemde gerçekleştirilir *ServiceHub.RoslynCodeAnalysisService32*. Büyük çözümler veya kaynak kısıtlı sistemlerde, bu özellik, performansı üzerinde önemli bir etkisi olabilir. Bellek sorunları yaşıyorsanız, örneğin, 4 GB makinede veya bu işlem için yüksek CPU kullanımından büyük bir çözümde yüklenirken, CodeLens kaynakları serbest bırakmak için devre dışı bırakabilirsiniz.

    Devre dışı bırakmak için **CodeLens**, seçin **Araçları** > **seçenekleri** > **metin düzenleyici**  >   **Tüm diller** > **CodeLens**, özellik seçimini kaldırın.

    > [!NOTE]
    > CodeLens, Visual Studio Professional ve Enterprise sürümlerinde kullanılabilir.

### <a name="other-tools-and-extensions"></a>Diğer araçlar ve uzantılar

- **Uzantıları devre dışı bırak**

    Yeni işlevsellik sağlayan veya var olan işlevselliği genişletmek için Visual Studio eklenen ek yazılım bileşenleri uzantılarıdır. Uzantılar genellikle bellek kaynağı sorunları kaynağı olabilir. Bellek kaynak sorun yaşıyorsanız, iş akışı ve senaryoya nasıl etkilediğini görmek için bir defada tek uzantıları devre dışı bırakma deneyin.

    Uzantıları devre dışı bırakmak için Git **Araçları** > **Uzantılar ve güncelleştirmeler**ve belirli bir uzantıyı devre dışı bırakın.

- **XAML Tasarımcısı devre dışı bırak**

    XAML Tasarımcısı'nı varsayılan olarak etkindir, ancak açarsanız, yalnızca kaynak tüketen bir *.xaml* dosya. XAML dosyaları ile çalışma, ancak Tasarımcı işlevselliği kullanmak istemiyorsanız, bazı belleği boşaltmak için bu özelliği devre dışı bırakın.

    Devre dışı bırakmak için **XAML Tasarımcısı**Git **Araçları** > **seçenekleri** > **XAML Tasarımcısı**  >  **XAML tasarımcısını etkinleştirmek**ve bu seçeneğin işaretini kaldırın.

- **İş yüklerini kaldırın**

    Artık kullanılmayan iş yükleri kaldırmak için Visual Studio Yükleyicisi'ni kullanabilirsiniz. Bu eylem, paketler ve artık gerekmeyen derlemeleri atlayarak başlangıç ve çalışma zamanı maliyetini kolaylaştırabilirsiniz.

## <a name="force-a-garbage-collection"></a>Bir Çöp toplamayı zorlamak

CLR çöp toplama bellek yönetimi sistemi kullanır. Bu sistemde, bazen bellek artık gerekmeyen nesneler tarafından kullanılır. Bu durum geçici; Çöp toplayıcı, performans ve kaynak kullanımı buluşsal yöntemlerini temel alarak bu belleği serbest bırakır. Visual Studio'da bir kısayol tuşu kullanarak kullanılmayan belleği toplamak için CLR zorlayabilirsiniz. Önemli miktarda atık koleksiyonu için bekliyor ve bir Çöp toplamayı zorlamak, bellek kullanımını görmelisiniz *devenv.exe* işlem bırak **Görev Yöneticisi'ni**. Bu yöntemi kullanmak nadiren gereklidir. (Tam derleme, hata ayıklama oturumu veya bir çözüm açık olay gibi) pahalı bir işlem tamamlandıktan sonra ancak, ne kadar bellek gerçekten işlem tarafından kullanılıyor belirlemenize yardımcı olur. Visual Studio (yönetilen ve yerel) karışık olduğundan, bazen yerel ayırıcısı ve atık toplayıcı sınırlı bellek kaynaklarının mücadele etmek mümkündür. Yüksek bellek kullanım koşullarında, çöp toplayıcısının çalıştırmak için zorlayın yardımcı olabilir.

Bir Çöp toplamayı zorlamak için kısayol tuşu kullanın: **Ctrl**+**Alt**+**Shift**+**F12**, **Ctrl**+**Alt**+**Shift**+**F12** (Bu iki defa basın).

Çöp toplama güvenilir bir şekilde başlatılmasına gerek olursa çalışma, Visual Studio geri bildirim aracı üzerinden bir rapor dosyası bu hata büyük olasılıkla, davranıştır gibi senaryonuza sağlar.

CLR çöp toplayıcısı ayrıntılı bir açıklaması için bkz. [çöp toplamanın Temelleri](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirme](../ide/optimize-visual-studio-performance.md)
- [Daha Hızlı çözümler (Visual Studio blogu) yükleme](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)