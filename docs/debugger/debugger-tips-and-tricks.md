---
title: İpuçları ve püf noktaları hata ayıklayıcısı
description: Visual Studio hata ayıklayıcı tarafından desteklenen daha az bilinen özelliklerinden bazıları hakkında bilgi edinin
ms.custom: seodec18
ms.date: 06/15/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 238236df48adab491cd8a1f9282a8f6a440c5321
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055231"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Hata Ayıklayıcı'Visual Studio için üretkenlik ipuçları ve püf noktaları öğrenin

Visual Studio hata ayıklayıcı için birkaç üretkenlik ipuçları ve püf noktaları öğrenmek için bu konuyu okuyun. Hata ayıklayıcı temel özelliklerine bir bakış için bkz. [hata ayıklayıcısı özellik Turu](../debugger/debugger-feature-tour.md). Bu konu başlığında özellik turu dahil edilmeyen bazı alanlar biz karşılarız.

## <a name="pin-data-tips"></a>PIN veri ipuçları

Sık hata ayıklama sırasında veri ipuçları gelin, değişken kendiniz hızlı erişim vermek için veri ipucu sabitlemek isteyebilirsiniz. Değişkeni yeniden başlatıldıktan sonra bile sabitlenmiş kalır. Veri ipucu sabitlemek için üzerine gelindiğinde Raptiye simgesine tıklayın. Birden fazla değişken sabitleyebilirsiniz.

![Bir veri ipucunda sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Kodunuzu düzenleyin ve (C#, VB, C++) hata ayıklamaya devam et

Visual Studio tarafından desteklenen çoğu dillerde hata ayıklama oturumu ortasında kodunuzu düzenleyin ve hata ayıklamaya devam et. Bu özelliği kullanmak için imlecinizi hata ayıklayıcı, düzenlemeleri yapma ve ENTER tuşuna duraklatıldığı sırada kodunuzu tıklayın **F5**, **F10**, veya **F11** hata ayıklamaya devam etmek için.

![Düzenle ve devam et hata ayıklama](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Özelliğini kullanarak ve özellik kısıtlamaları hakkında daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Yeniden oluşturulması zor olan sorunlarında hata ayıklama

Zor veya uygulamanızda belirli bir durumu yeniden oluşturmak harcanan zamanı ortadan kaldırır, koşullu kesme noktası kullanımı yardımcı olup olmadığını düşünün. Kullanabileceğiniz [koşullu kesme noktaları](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) ve filtre uygulamayı (örneğin, bir durum içinde bir değişkeni depolamak bozuk veri) istenen duruma girene kadar uygulama kodunuza bozmayı önlemek için kesme noktaları. İfadeler, filtreler, isabet sayılarını vb. kullanarak koşulları ayarlayabilirsiniz.

#### <a name="to-create-a-conditional-breakpoint"></a>Koşullu kesme noktası oluşturmak için

1. Bir kesme noktası simgesi (kırmızı Top) sağ tıklatın ve seçin **koşullar**.

2. İçinde **kesme noktası ayarları** penceresinde, bir ifade türü.

    ![Koşullu kesme noktası](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Koşul başka bir türünü ilgileniyorsanız seçin **filtre** yerine **koşullu ifade** içinde **kesme noktası ayarları** iletişim kutusunu ve sonra Filtre ipuçları.

## <a name="change-the-execution-flow"></a>Yürütme akışı değiştirme

Hata ayıklayıcısı ile duraklatılmış bir kod satırının sol taraftaki sarı ok işaretçi almak için fareyi kullanın. Başka bir noktada kod yürütme yolunda sarı ok işaretçiyi taşıyın. Ardından uygulamayı çalıştırmaya devam etmek için F5'e ya da bir adımı komutunu kullanın.

![Yürütme işaretçiyi](../debugger/media/dbg-tour-move-the-execution-pointer.gif "yürütme işaretçiyi taşıyın")

Yürütme akışı değiştirerek farklı kod yürütme yolları test veya hata ayıklayıcı yeniden başlatmadan kodu yeniden gibi işlemler yapabilirsiniz.

> [!WARNING]
> Genelde bu özellikle dikkat etmek gerekir ve araç ipucunda bir uyarı görürsünüz. Çok diğer uyarılar görebilirsiniz. İşaretçiyi taşıma uygulamanızı daha önceki bir uygulama durumuna geri alınamaz.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>İzleme kapsamını nesneyi (C#, Visual Basic)

Hata ayıklayıcı pencereleri gibi kullanarak değişkenleri görmek daha kolaydır **Watch** penceresi. Ancak, bir değişken gittiğinde kapsam dışına **Watch** penceresinde gri renkte görüntülenir gözleyebilirsiniz. Bazı uygulama senaryolarında bir değişkenin değerini değiştirebilir, bile zaman kapsam dışına değişkendir ve yakından izlemek isteyebilirsiniz (örneğin, bir değişkenin atık alabilirsiniz). Değişkeni içinde onun için bir nesne kimliği oluşturarak izleyebilirsiniz **Watch** penceresi.

#### <a name="to-create-an-object-id"></a>Bir nesne kimliği oluşturmak için

1.  İzlemek istediğiniz değişken yakın bir kesme noktası ayarlayın.

2.  Hata ayıklayıcıyı başlatın (**F5**) ve kesme noktasındaki durdur.

3. Değişkeninde Bul **Yereller** penceresi (**hata ayıklama > Windows > Yereller**), değişkeni sağ tıklatın ve seçin **nesne kimliği yap**.

    ![Bir nesne kimliği oluşturma](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Görmelisiniz bir **$** bir sayıyı artı **Yereller** penceresi. Bu değişken nesne kimliğidir.
  
5.  Nesne Kimliği değişkeni sağ tıklatın ve seçin **Gözcü Ekle**.

Daha fazla bilgi için [bir nesne kimliği oluşturma](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>İşlevlerine yönelik dönüş değerlerini görüntüleme

İşlevleriniz için dönüş değerleri görüntülemek için görünen işlevleri bakın **Otolar** , kod içerisinde ilerlemeye sırada penceresi. Bir işlevin dönüş değeri görmek için ilgilendiğiniz işlevi zaten yürütüldü emin olun (basın **F10** üzerinde işlev çağrısı şu anda durdurulmuş durumda olmadığını bir kez). Pencereyi kapattıysanız kullanın **hata ayıklama > Windows > Otolar** açmak için **Otolar** penceresi.

![Otolar penceresinde](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

İşlevler Ayrıca, girdiğiniz **hemen** dönüş değerleri görüntülemek için pencere. (Kullanarak açmadan **hata ayıklama > Windows > hemen**.)

![Komut penceresi](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Ayrıca [sözde değişken](../debugger/pseudovariables.md) içinde **Watch** ve **hemen** penceresinde gibi `$ReturnValue`.

## <a name="string_visualizer"></a>Görselleştiricide dize inceleyin

Dizeleri ile çalışırken, biçimlendirilmiş dizenin tamamını görüntülemek yararlı olabilir. Düz metin, XML, HTML veya JSON dizesini görüntülemek için büyüteç simgesini tıklayın ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") bir dize değeri içeren bir değişken gelindiğinde.

![Dize Görselleştirici açın](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Dize Görselleştirici bir dize dize türüne bağlı olarak biçimlendirilmiş olup bulmanıza yardımcı olabilir. Örneğin, bir boş **değer** alanının dize Görselleştirici türü tarafından tanınmıyor. Daha fazla bilgi için [dize Görselleştirici iletişim kutusu](../debugger/string-visualizer-dialog-box.md).

![JSON dizesi Görselleştirici](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Birkaç diğer türleri için hata ayıklayıcı pencerelerinde görüntülenen WPF nesneleri gibi görselleştiriciler da açabilirsiniz.

## <a name="break-into-code-on-handled-exceptions"></a>Koda işlenen özel durumlar üzerinde kesme

İşlenmeyen özel durumları hakkında kodunuza hata ayıklayıcı keser. Ancak, özel durumları ele (içinde oluşan özel durumlar gibi bir `try/catch` blok) hataları kaynağı da olabilir ve bunlar ortaya çıktığında araştırmak isteyebilirsiniz. Koda de işlenen özel durumlar için seçenekleri yapılandırarak hata ayıklayıcının yapılandırabileceğiniz **özel durum ayarları** iletişim kutusu. Bu iletişim kutusunu seçerek açın **hata ayıklama > Windows > özel durum ayarları**.

**Özel durum ayarları** iletişim kutusu içinde özel durum kodu hata ayıklayıcının bildirmenize olanak tanır. Aşağıdaki çizimde hata ayıklayıcı kodunuza keser. her bir `System.NullReferenceException` gerçekleşir. Daha fazla bilgi için [özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md).

![Özel durum Ayarları iletişim kutusu](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Hata ayıklama Kilitlenmeler ve yarış durumları

Tür birden çok iş parçacıklı uygulamalar için ortak olan sorunları hata ayıklamak ihtiyacınız varsa, bunu genellikle hata ayıklama sırasında iş parçacığı konumunu görüntülemek için yardımcı olur. Bunu kullanarak kolayca yapmak **kaynak iş parçacıklarını Göster** düğmesi.

#### <a name="to-show-threads-in-your-source-code"></a>İş parçacığı kaynak kodunuzu göstermek için

1.  Hata ayıklama sırasında tıklayın **kaynak iş parçacıklarını Göster** düğmesi ![kaynak iş parçacıklarını Göster](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") içinde **hata ayıklama** araç çubuğu.
  
2.  Pencerenin sol tarafındaki cilt payını bakın. Bu satırda gördüğünüz bir *iş parçacığı işaret* simgesi ![iş parçacığı işaret](../debugger/media/dbg-thread-marker.png "ThreadMarker") , iki bez iş parçacığı benzer. İş parçacığı işaretçisi, bir iş parçacığı bu konuma durdurulduğunu gösterir.

    Bir iş parçacığı işaret kısmen bir kesme noktası tarafından altına gizlenmiş, dikkat edin.
  
3.  İşaretçi iş parçacığı işaret gelin. Bir DataTip görünür. DataTip durdurulmuş her iş parçacığı için adı ve iş parçacığı kimlik numarasını belirtir.

    İş parçacıklarında konumunu da görüntüleyebilirsiniz [Paralel Yığınlar penceresini](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Web hizmetleri ve ağ kaynaklarına (UWP) için yüklerini inceleyin

UWP uygulamalarında kullanılarak yapılan ağ işlemlerini çözümleyebilirsiniz `Windows.Web.Http` API. Web hizmetleri ve ağ kaynaklarını hata ayıklama yardımcı olmak için bu aracı kullanabilirsiniz. Aracı'nı kullanmayı tercih **hata ayıklama > performans Profiler**. Seçin **ağ**ve ardından **Başlat**. Uygulamanızda kullandığı senaryosuyla Git `Windows.Web.Http`ve ardından **koleksiyonu Durdur** raporu oluşturmak için.

![Ağ kullanımı aracı profil oluşturma](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Bir işlem içinde Özet görünümünü için daha fazla ayrıntı'ı seçin.

![Ayrıntılı bilgi ağ kullanımı aracında](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Daha fazla bilgi için [ağ kullanımını](../profiling/network-usage.md).

## <a name="modules_window"></a> Hata Ayıklayıcı'nın uygulamanıza nasıl ekleyen daha iyi tanımak (C#, C++, Visual Basic F#)

Çalışan uygulamanıza eklemek için hata ayıklayıcının hata ayıklamaya çalıştığınız uygulama aynı tam derleme için oluşturulan sembol (.pdb) dosyalarını yükler. Sembol dosyalarının biraz bilgi bazı senaryolarda yararlı olabilir. Visual Studio sembol dosyalarını kullanarak nasıl yükler inceleyebilirsiniz **modülleri** penceresi.

Açık **modülleri** penceresini seçerek hata ayıklama sırasında **hata ayıklama > Windows > modülleri**. **Modülleri** penceresi, hata ayıklayıcının kullanıcı kodu davranılması hangi modüllerin öğrenebilirsiniz veya [ *kodum*](../debugger/just-my-code.md)ve sembol durumu modülü için yükleme. Çoğu senaryoda, hata ayıklayıcı kullanıcı kodu için Sembol dosyalarını otomatik olarak bulur, ancak adımla (veya hata ayıklama) .NET framework kodu, sistem kodunu veya üçüncü taraf kitaplık kodu isterseniz, doğru sembol dosyalarını edinmek için ek adımlar gereklidir.

![Modüller penceresini içinde Sembol bilgilerini görüntüleyin](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Sembol bilgilerini doğrudan yükleyebilirsiniz **modülleri** sağ tıklayıp seçme penceresi **yük sembolleri**.

Bazı durumlarda, uygulama geliştiricilerinin (ayak izini azaltmak için) eşleşen sembol dosyaları, yayımlanmış bir sürüm'e daha sonra debug derleme için bir kopyasını eşleşen sembol dosyalar tut ancak olmadan uygulamalar gönderin.

Hata ayıklayıcı kod kullanıcı kodu olarak sınıflandırır nasıl kullanıma bulmak için bkz: [yalnızca kendi kodum](../debugger/just-my-code.md). Sembol dosyaları hakkında daha fazla bilgi için bkz: [Visual Studio hata ayıklayıcısında simge (.pdb) ve kaynak dosyaları belirtme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Daha fazla bilgi edinin

Ek ipuçları ve püf noktaları ve daha ayrıntılı bilgi için şu blog postalarına bakın:

- [Visual Studio'da hata ayıklama için 7 daha az bilinen atölyelere](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio 7 gizli toprağa değerli taşlar](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Ayrıca Bkz.
[Klavye Kısayolları](../ide/tips-and-tricks-for-visual-studio.md)
