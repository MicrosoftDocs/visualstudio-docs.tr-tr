---
title: Çalıştırma, yapı ve Test Gezgini ile birim testlerinin hatalarını ayıklama
description: Visual Studio'da Test Exlorer ile testleri çalıştırmayı öğrenin. Bu konu, otomatik test çalıştırmaları derlemeden sonra etkinleştirmek, test sonuçlarını görüntülemek, Grup ve test listesini filtrelemek, çalma listeleri oluşturmak, Testlerde Hata Ayıkla ve test kısayolları kullanma kapsar.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: dc918adb6a66f64cdcda46ea535cd0ab017c0676
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939525"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma

Kullanım **Test Gezgini** birim testlerini Visual Studio ya da üçüncü taraf birim testi projelerini çalıştırmak için. Ayrıca **Test Gezgini** testleri kategoriler halinde gruplandırmak, test listesini filtrelemek ve oluşturma, kaydedin ve test çalma listeleri çalıştırın. Testlerde hata ayıklama yaparak test performansı ve kod kapsamını analiz etme.

Visual Studio, hem yönetilen hem de yerel kod için Microsoft birim testi çerçevelerini içerir. Ancak, **Test Gezgini** herhangi bir birim Test Gezgini bağdaştırıcısı uygulayan test çerçevesi de çalıştırabilirsiniz. Üçüncü taraf birim test çerçeveleri yükleme hakkında daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)

**Test Gezgini** bir çözümde birden çok test projesini ve üretim kodu projelerin bir parçası olan test sınıflarından testler çalıştırabilirsiniz. Test projeleri farklı birim test çerçeveleri kullanabilir. Test altındaki kod .NET Framework için yazıldığında, test projesi, ayrıca hedef kodun dili ne olursa olsun .NET Framework hedefleyen herhangi bir dilde yazılabilir. Yerel C/C++ kod projeleri, bir C++ birim test çerçevesi kullanılarak test edilmelidir. Daha fazla bilgi için [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Testleri Test Gezgini'nde çalıştırma

Test projesi oluşturduğunuzda, testler Test Gezgini'nde görünür. Test Gezgini görünür değilse seçin **Test** Visual Studio menüsünde **Windows**ve ardından **Test Gezgini**.

![Birim Test Gezgini](../test/media/ute_failedpassednotrunsummary.png)

Çalıştırma, yazma ve testlerinizi yeniden çalıştırın, Test Gezgini sonuçları varsayılan gruplarında görüntüler **başarısız testler**, **başarılı testler**, **Atlanan testler** ve  **Testleri Çalıştır**. Test Gezgini'nin testlerinizi gruplandırma şeklini değiştirebilirsiniz.

Bulma, düzenleme ve testleri çalıştıran işin çoğunu gerçekleştirebilirsiniz **Test Gezgini** araç çubuğu.

![Test Gezgini araç çubuğundan Testleri Çalıştır](../test/media/ute_toolbar.png)

### <a name="run-tests"></a>Testleri çalıştırma

Tüm testler, Çözümdeki tüm testleri bir grup veya seçtiğiniz test kümesini çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Bir çözümdeki tüm testleri çalıştırmak için tercih **tümünü Çalıştır**.

- Varsayılan bir grupta tüm testleri çalıştırmak için tercih **çalıştırma** ve sonra menüde grubu seçin.

- Seçilmiş test için bağlam menüsünü açın ve ardından çalıştırmak istediğiniz testleri tek tek seçin **seçili Testleri Çalıştır**.

- Bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, paralel test yürütme ile Aç ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.

**Geçer/başarısız çubuğu** en üstündeki **Test Gezgini** penceresi Testler çalışırken animasyonlu. Test çalıştırması, sonunda **geçer/başarısız çubuğu** tüm testler geçildi, yeşile döner veya herhangi bir test başarısız olursa kırmızıya döner.

### <a name="run-tests-after-every-build"></a>Her derleme sonrasında Testleri Çalıştır

|Düğme|Açıklama|
|-|-|
|![Yapıdan sonra çalıştırmak](../test/media/ute_runafterbuild_btn.png)|Her bir yerel oluşturmadan sonra birim testlerinizi çalıştırmak için tercih **Test** standart menüde seçip **oluşturmadan sonra Testleri Çalıştır** üzerinde **Test Gezgini** araç çubuğu.|

## <a name="view-test-results"></a>Test sonuçlarını görüntüle

Test Gezgini çalıştırma, yazma ve testlerinizi yeniden çalıştırın gibi sonuçları gruplarında görüntüler. **başarısız testler**, **başarılı testler**, **Atlanan testler** ve **çalıştırma Testleri**. Test Gezgini görüntüler altındaki ayrıntılar bölmesi test özeti çalıştırın.

### <a name="view-test-details"></a>Test ayrıntılarını görüntüleme

Tek bir testin ayrıntılarını görüntülemek için testi seçin.

![Test yürütme ayrıntıları](../test/media/ute_testdetails.png)

Test ayrıntıları bölmesinde aşağıdaki bilgileri görüntüler:

- Kaynak dosya adı ve test yönteminin satır sayısı.

- Testin durumu.

- Test yöntemini çalıştırmak için geçen geçen süre.

Test başarısız olursa, Ayrıntılar bölmesinde de görüntüler:

- Test için birim test çerçevesi tarafından döndürülen ileti.

- Yığın izleme zaman test başarısız oldu.

### <a name="view-the-source-code-of-a-test-method"></a>Test yönteminin kaynak kodunu görüntüleme

 Visual Studio düzenleyicisinde bir test yöntemi için kaynak kodunu görüntülemek için testi seçin ve ardından **testi Aç** bağlam menüsünde (klavye: **F12**).

## <a name="group-and-filter-the-test-list"></a>Grup ve test listesini Filtrele

Test Gezgini, testlerinizi önceden tanımlanmış kategoriler halinde gruplamanızı sağlar. Test Gezgini izin verir, çalışan çoğu test çerçeveleri, kendi kategorileri ve testlerinizi gruplamak için kategori/değer çiftlerini tanımlayın. Ayrıca test özelliklerine karşı dizeleri eşleştirerek test listesine filtre uygulayabilirsiniz.

### <a name="group-tests-in-the-test-list"></a>Grup testleri test listesi

 Testlerin düzenlenme şeklini değiştirmek için aşağı yanındaki oku seçin **Group By** düğmesi ![Test Gezgini Grup düğmesi](../test/media/ute_groupby_btn.png) ve bir gruplandırma ölçütü.

 ![Grup testler Test Gezgini'nde kategoriye göre](../test/media/ute_groupbycategory.png)

### <a name="test-explorer-groups"></a>Test Gezgini grupları

|Grup|Açıklama|
|-|-----------------|
|**Süresi**|Yürütme süresine göre testi gruplandırır: **hızlı**, **orta**, ve **yavaş**.|
|**Sonucu**|Yürütme sonuçlarına göre testleri gruplandırır: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
|**Nitelikler**|Tanımladığınız kategori/değer çiftlerine göre testi gruplandırır. Nitelik kategorileri ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.|
|**Project**|Projelerin adına göre testi gruplandırır.|

### <a name="group-by-traits"></a>Niteliklere göre gruplandırma

 Ayırt edici nitelik genellikle bir kategori ad/değer çifti olan, ancak tek bir kategori de olabilir. Nitelikler, birim test çerçevesi tarafından bir test yöntemi olarak tanımlanan yöntemlere atanabilir. Bir birim test çerçevesi, ayırt edici nitelik kategorilerini tanımlayabilir. Kendi kategori ad/değer çiftlerinizi tanımlamak için ayırdedici nitelik kategorilerine değerler ekleyebilirsiniz. Nitelik kategorileri ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.

 **Microsoft birim testi için yönetilen kod çerçevesi içindeki nitelikler**

 Yönetilen uygulamalar için Microsoft birim test çerçevesi, ayırt edici nitelik adını tanımlamak / değer çiftinin bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> özniteliği. Test çerçevesi, önceden tanımlanmış bu nitelikleri de içerir:

|Nitelik|Açıklama|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Sahip kategorisi birim test çerçevesi tarafından tanımlanır ve sahibin bir dize değerini vermenizi gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Öncelik kategorisi birim test çerçevesi tarafından tanımlanır ve bir tamsayı öncelik değeri vermenizi gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory özniteliği bir değer olmadan bir kategori girmenize olanak tanır. TestCategory özniteliği tarafından tanımlanan bir kategori, TestProperty özniteliği kategorisi de olabilir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty özniteliği ayırdedici nitelik kategorisi/değer çifti tanımlamanızı sağlar.|

 **C++ için Microsoft birim testi çerçevesi içindeki nitelikler** bkz [C++ için Microsoft birim testi çerçevesi kullanmayı](how-to-use-microsoft-test-framework-for-cpp.md).

### <a name="search-and-filter-the-test-list"></a>Arama ve test listesini Filtrele

Projelerinizde görüntüleyip çalıştırabileceğiniz, test yöntemlerini sınırlamak için Test Gezgini filtreleri kullanabilirsiniz.

Bir dizede yazdığınızda **Test Gezgini** seçin ve arama kutusuna **Enter**, test listesi yalnızca tam adları dizeyi içeren testleri görüntüleyecek şekilde filtrelenmiştir.

Farklı ölçütlere göre filtrelemek için:

1. Arama kutusunun sağındaki açılan listeyi açın.

2. Yeni bir ölçüt seçin.

3. Filtre değeri tırnak işaretleri arasında girin.

![Testleri Test Gezgini'nde Filtrele](../test/media/ute_filtertestlist.png)

> [!NOTE]
> Arama büyük/küçük harfe duyarsızdır ve belirtilen dizeyi ölçüt değeri herhangi bir bölümü eşleştir.

|Niteleyicisi|Açıklama|
|-|-----------------|
|**Nitelik**|Hem ayırdedici nitelik kategorisini hem de değer eşleşmelerini arar. Nitelik kategorileri ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.|
|**Project**|Test proje adı eşleşmeleri arar.|
|**Hata iletisi**|Arama tarafından döndürülen başarısız kullanıcı tanımlı hata iletileri için eşleşme onaylar.|
|**Dosya yolu**|Test kaynak dosyaları tam olarak nitelenmiş dosya adını eşleşmelerini arar.|
|**Tam adı**|Test ad alanları, sınıflar ve yöntemler tam olarak nitelenmiş dosya adını eşleşmelerini arar.|
|**Output**|Standart çıkış (stdout) veya standart hata (stderr) yazılmış kullanıcı tanımlı hata iletileri arar. Çıktı iletilerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanmıştır.|
|**Sonucu**|Eşleşmeleri için Test Gezgini kategori adlarını arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|

Bir alt kümesini bir filtre sonuçlarını tutmak için aşağıdaki sözdizimini kullanın:

```cpp
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Örneğin, `FullName:"MyClass" - FullName:"PerfTest"` adında "adında PerfTest" de testler dışındaki, adında "Sınıfım" içeren tüm testleri döndürür.

## <a name="create-custom-playlists"></a>Özel çalma listeleri oluşturma

 Oluşturun ve çalıştırın veya bir grup olarak görüntülemek istediğiniz testlerin listesini kaydedin. Çalma listesi seçtiğinizde listedeki testler Test Gezgini'nde görüntülenir. Bir testi birden fazla çalma listesine ekleyebilirsiniz ve varsayılan seçtiğinizde projenizdeki tüm testler kullanılabilir **tüm testleri** çalma listesi.

 ![Bir çalma listesini seçin](../test/media/ute_playlist.png)

 **Bir çalma listesi oluşturmak için**, Test Gezgini'nde bir veya birden çok test seçin. Bağlam menüsünde **çalma listesine Ekle** > **NewPlaylist**. Dosya adı ve belirttiğiniz konuma kaydetmek **yeni çalma listesi oluştur** iletişim kutusu.

 **Bir çalma listesine testler eklemek için**, Test Gezgini'nde bir veya birden çok test seçin. Bağlam menüsünde **çalma listesine Ekle**, testleri eklemek istediğiniz çalma listesini seçin.

 **Bir çalma listesini açmak için**, seçin **Test** > **çalma listesi** Visual Studio menüsünde ve ya da son kullanılan çalma listesinden seçin veya seçin **açın Çalma listesi** çalma konumunu ve adını belirtmek için.

 Bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, paralel test yürütme ile Aç ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.

## <a name="debug-and-analyze-unit-tests"></a>Hata ayıklama ve birim testlerini çözümleme

### <a name="debug-unit-tests"></a>Birim testlerinin hatalarını ayıklama

Test Gezgini, testleriniz için hata ayıklama oturumu başlatmak için kullanabilirsiniz. Kodunuzu Visual Studio hata ayıklayıcısı ile sorunsuz bir şekilde Adımlama, İleri ve geri birim testleri ve test altındaki projeye arasında sürer. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hatalarını ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde kesme noktası ayarlayın.

    > [!NOTE]
    > Test yöntemleri herhangi bir sırada çalışabileceğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktalarını ayarlayın.

2. Test Gezgini'nde test yöntemlerini seçin ve ardından **seçilen Testlerde Hata Ayıkla** bağlam menüsünde.

   Hata ayıklayıcısı hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](../debugger/debugging-in-visual-studio.md).

### <a name="diagnose-test-method-performance-issues"></a>Test yöntemi performans sorunlarını tanılama

 Neden bir test yöntemi, çok fazla zaman aldığını tanılamak için yöntemi Test Gezgini'nde seçin ve ardından **profili** bağlam menüsünde. Bkz: [performans Gezgini](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Birim testi kod kapsamını analiz etme

Visual Studio kod kapsamı Aracı'nı kullanarak birim testleriniz tarafından gerçekten edildiğini, ürün kodu miktarını belirleyebilirsiniz. Kod kapsamı Seçili testler ya da bir çözümdeki tüm testleri çalıştırabilirsiniz.

Bir çözümde test yöntemleri için kod kapsamını çalıştırmak için:

1. Seçin **testleri** Visual Studio menüsünde seçip **kod kapsamını analiz etme**.

2. Alt menüden olarak aşağıdaki komutlardan birini seçin:

    - **Seçili testler** Test Gezgini'nde seçtiğiniz test yöntemlerini çalıştırır.

    - **Tüm testler** Çözümdeki tüm test yöntemlerini çalıştırır.

**Kod kapsamı sonuçlarını** penceresi satır, işlevi, sınıf, ad alanı ve modül tarafından uygulanan ürünün kodu bloklarının yüzdesini görüntüler.

Daha fazla bilgi için [ne kadar kodun test edildiğini belirlemek için kod kapsamı kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Test kısayolları

Test çalıştırılabilir **Test Gezgini**, Kod düzenleyicisinde bir test üzerinde sağ tıklatıp seçerek **test çalıştırması**, veya varsayılan kullanarak [Test Gezgini kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) içinde Visual Studio. Bazı kısayolları, içerik tabanlı. Bu, çalıştırmak veya imleci Kod Düzenleyicisi'nde olduğu temel Testlerde Hata Ayıkla anlamına gelir. İmleci test yönteminin içinde ise, ardından, yöntemi test çalıştırmaları. İmlecinizi sınıf düzeyinde ise, ardından o sınıfta tüm testleri çalıştırın. Bu ad alanı düzeyinde de aynıdır.

|Sık kullanılan komutları| Klavye Kısayolları|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**CTRL**+**R**, **Ctrl**+**T**|
|TestExplorer.RunAllTestsInContext|**CTRL**+**R**, **T**|

> [!NOTE]
> Testleri yalnızca soyut sınıflar tanımlanır ve değil örneği için soyut bir sınıf, bir test çalıştırılamıyor. Soyut sınıflar testleri çalıştırmak için soyut sınıftan türeyen bir sınıf oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Birim testi kod](../test/unit-test-your-code.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
