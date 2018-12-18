---
title: Live Unit Testing
ms.date: 2017-03-07
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 7be078044454ebf5d6b3a6d99a60fff66ab1f69b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066216"
---
# <a name="live-unit-testing-with-visual-studio-2017"></a>Visual Studio 2017 ile Live Unit Testing

Bir uygulama geliştiriyorsunuz gibi Live Unit Testing otomatik olarak tüm etkilenen birim testlerini arka planda çalıştırır ve sonuçları ve kod kapsamını Canlı gerçek zamanlı olarak Visual Studio IDE'de sunar. Kodunuzu değiştirmeniz gibi Live Unit Testing değişikliklerinizi mevcut testleri nasıl etkilenen geri bildirim sağlar ve bir veya daha fazla var olan testlerin kapsadığını olup yeni kod ekledik. Bu yavaşça, hata düzeltmeleri yapmak veya yeni özellikler eklenmesi gibi birim testleri yazma hatırlatır.

> [!NOTE]
> Live Unit Testing, .NET Core veya Enterprise Edition, Visual Studio 2017'de .NET Framework hedefleyen C# ve Visual Basic projeleri için kullanılabilir.

Testleriniz için Live Unit Testing kullandığınızda, Live Unit Testing testlerinizi durumu hakkında veriler devam ettirir. Live Unit Testing, sınamaları çalışırken dinamik olarak kod değişikliklere yanıt olarak üstün performans sunmak kalıcı verileri kullanma olanağı sağlar.

## <a name="supported-test-frameworks"></a>Desteklenen test çerçeveleri
Live Unit Testing aşağıdaki tabloda listelenen üç popüler birim test çerçeveleri ile çalışır. Desteklenen en düşük sürüm bağdaştırıcılarının ve çerçeveleri de tabloda listelenir. Birim testi çerçevelerini NuGet.org adresinden tüm kullanılabilir.

<table>
<tr>
   <th>Test çerçevesi</th>
   <th>Visual Studio bağdaştırıcısı en düşük sürüm</th>
   <th>Framework en düşük sürüm</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.Runner.VisualStudio sürüm 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>3.5.1 NUnit3TestAdapter sürümü</td>
   <td>NUnit 3.5.0 sürümü</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Eski varsa, MSTest başvuruyor test projeleri dayalı `Microsoft.VisualStudio.QualityTools.UnitTestFramework` ve yeni MSTest NuGet paketleri, Visual Studio 2017 sürüm 15.4 yükseltme için taşımak istediğiniz yok.

Bazı durumlarda, açıkça için Live Unit Testing çalışmaya sırayla çözümde proje tarafından başvurulan NuGet paketlerini geri yüklemek gerekebilir. Çözümün belirtik bir derleme yaparak ya da bunu yapabilirsiniz (seçin **derleme** > **çözümü yeniden derle** en üst düzey Visual Studio menüsünde) ya da çözüm (paketleri geri yükleniyor sağ tıklatın ve çözüm **NuGet paketlerini geri yükle**) Living birim testi etkinleştirmeden önce.

## <a name="configure-live-unit-testing"></a>Live Unit Testing yapılandırın

Live Unit Testing seçerek yapılandırabileceğiniz **Araçları** > **seçenekleri** en üst düzey Visual Studio menü çubuğunda, ve ardından seçerek **Live Unit Testing** sol bölmesinde **seçenekleri** iletişim.

> [!TIP]
> Live Unit Testing etkinleştirildikten sonra (sonraki bölüme bakın [başlatmak, duraklatmak ve Live Unit Testing durdurmak](#start-pause-and-stop-live-unit-testing)), da açabilirsiniz **seçenekleri** seçerek iletişim **Test**  >  **Live Unit Testing** > **seçenekleri**.

Live Unit Testing yapılandırma seçenekleri iletişim kutusunda aşağıdaki şekilde gösterilmiştir:

  ![Görüntü](./media/lut-options.png)

Yapılandırılabilir seçeneklerin şunlardır:

- Bir çözüm oluşturulan ve hata ayıklama mı Live Unit Testing duraklatır.

- Sistemin pili belirtilen eşiğin altına düştüğünde olup Live Unit Testing duraklatır.

- Bir çözümü açtığınızda olup Live Unit Testing otomatik olarak çalıştırılır.

- Etkinleştirilip etkinleştirilmeyeceğini sembol ve XML belgesi açıklama oluşturma hatalarını ayıklayın.

- Kalıcı veri depolanacağı dizin.

- Tüm kalıcı veri silme yeteneği. Live Unit Testing, kalıcı verileri bozulmuş önerir öngörülemeyen ya da beklenmeyen şekilde davrandığından istediğinizde yararlıdır.

- Bir test çalışması sonra zaman aşımına Interval; Varsayılan değer 30 saniyedir.

- Live Unit Testing oluşturan test işlemlerinin maksimum sayısı.

- Live Unit Testing işler maksimum belleğin kullanabilir.

- Live Unit Testing için yazılan bilgi düzeyini **çıkış** penceresi.

   Seçenekleriniz günlüğünü (**hiçbiri**), yalnızca hata iletileri (**hata**), hata ve bilgilendirici iletileri (**bilgileri**, varsayılan), ya da tüm ayrıntıları (**ayrıntılı** ).

   Live Unit Testing içinde ayrıntılı çıkış görüntüleyebilirsiniz **çıkış** değerini "1" adlı bir kullanıcı düzeyinde ortam değişkenine atayarak penceresi `VS_UTE_DIAGNOSTICS`ve ardından Visual Studio'yu yeniden başlatmayı.

   Live Unit Testing dosyasındaki öğesinden ayrıntılı MSBuild günlük iletilerini yakalamak için `LiveUnitTesting_BuildLog` kullanıcı düzeyinde ortam değişkenine günlük içerecek dosyanın adı.

## <a name="start-pause-and-stop-live-unit-testing"></a>Başlatma, duraklatma ve Live Unit Testing Durdur

Live Unit Testing seçerek etkinleştirmeniz **Test** > **Live Unit Testing** > **Başlat** en üst düzey Visual Studio menüsünde. Live Unit Testing etkinleştirildiğinde, bulunan Seçenekler **Live Unit Testing** tek bir öğe menüsü değişiklik **Başlat**, **duraklatma**, **Durdur**, ve **temiz sıfırlama**.

> [!NOTE]
> Bir birim test projesi içermeyen bir çözümde Live Unit Testing başlatırsanız **duraklatma**, **Durdur**, ve **temiz sıfırlama** seçenekleri görünmez **Canlı Birim test** menü ancak Live Unit Testing başlamıyor. **Çıkış** penceresi "desteklenen test bağdaştırıcısı yok... Bu çözüm tarafından başvurulan" başlayan bir ileti görüntüler

Herhangi bir zamanda geçici olarak duraklatabilir veya tamamen Live Unit Testing durdurun. Bunu, örneğin, bir yeniden düzenleme ortasında olan ve testlerinizi bir süredir kesik sunulacağını bildiğiniz yapmak isteyebilirsiniz. Üç menü seçenekleri şunlardır:

- **Duraklatma**, hangi geçici olarak askıya Live Unit Testing.

    Live Unit Testing duraklatıldığında kapsamı görselleştirmeniz Düzenleyicisi'nde görünmez, ancak toplanan tüm veriler korunur. Live Unit Testing sürdürmek için seçin **devam** Live Unit Testing menüsünde. Live Unit Testing ile duraklatıldı ve karakterleri gerekli şekilde güncelleştirecek yapılmış tüm düzenlemeleri Kaçırdığınız gerekli çalışır.

- **Durdur**, Live Unit Testing tamamen durdurmak için. Live Unit Testing, toplanan tüm verileri atar.

- **Temiz sıfırlama**, Live Unit Testing durdurur, siler, verilerin kalıcı ve Live Unit Testing yeniden başlatır.

- **Seçenekleri**, açan **seçenekleri** iletişim açıklanan [yapılandırma Live Unit Testing](#configure-live-unit-testing) bölümü.

## <a name="view-coverage-visualization-in-the-editor-as-you-type"></a>Siz yazarken kapsamı görselleştirme Düzenleyicisi'nde görüntüleyemezsiniz.

Etkinleştirildikten sonra Live Unit Testing güncelleştirmeler her kod yazdığınız olmadığını göstermek için Visual Studio düzenleyicisinde bir kod satırının, birim testleri ve yoksa onu kapsayan testleri geçiliyor mu tarafından ele alınmıştır.  Aşağıdaki şekilde, geçirme ve testleri gibi testler tarafından kapsanmaz kod satırlarını başarısız kod satırlarını gösterilmektedir. Yeşil "✓" ile düzenlenmiş satırları yalnızca testleri geçirerek ele alınmaktadır satırları "x" kırmızı ile donatılmış bir veya birden çok başarısız olan testler tarafından ele alınmaktadır ve mavi "➖" tarafından düzenlenmiş satırları tarafından herhangi bir test kapsamında değildir.

  ![Görüntü](./media/lut-codewindow.png)

Live Unit Testing Kod düzenleyicisinde kod değiştirirken kapsamı görselleştirme hemen güncelleştirilir. Düzenlemeleri işlenirken verileri yuvarlak bir zamanlayıcı ekleyerek güncel olmadığını göstermek için görselleştirme değişiklikler başarısız, geçirme Aşağıda, görüntü ve semboller, aşağıdaki şekilde gösterildiği gibi ele alınmamaktadır.

  ![Görüntü](./media/lut-codeupdating.png)

## <a name="get-information-on-successful-or-failed-tests"></a>Başarılı ve başarısız testleri hakkında bilgi edinin

Kod penceresinde başarılı veya başarısız simgenin üzerine gelerek, kaç tane test satırdaki karşılaştınız demektir görebilirsiniz. Simgesine tıklayın, tek tek testlerin durumunu aşağıdaki şekilde gösterildiği gibi görebilirsiniz:

  ![Görüntü](./media/lut-failedinfo.png)

Sağlama adları ve test sonucu, araç ipucu sağlar ek olarak, yeniden test kümesini çalıştırın yanı hata ayıklayıcıyı kullanarak test kümesini çalıştırın. Araç çubuğuna bir veya daha fazla testin seçerseniz, çalıştırmak veya yalnızca bu Testlerde Hata Ayıkla. Bu kod penceresinde ayrılmak zorunda kalmadan testlerinizi ayıklamanızı sağlar. Hata ayıklayıcı yürütüldüğünde zaten ayarladığınız, herhangi bir kesme noktası gözleme yanı sıra hata ayıklama sırasında program yürütme duraklatır bir [ `Assert` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) beklenmeyen bir sonuç döndüren yöntem.

Başarısız bir test araç ipucunda üzerine geldiğinizde, bu hata hakkında ek bilgi sağlamak için aşağıdaki görüntüde gösterildiği gibi genişletir. Başarısız test araç ipucunda çift tıklarsanız, doğrudan gidebilirsiniz.

  ![Görüntü](./media/lut-failedmsg.png)

Başarısız test için gittiğinizde, Live Unit Testing da görsel olarak (yeşil "✓" ile birlikte bir Yarım tam beaker tarafından gösterilen), geçen testler başarısız oldu Yöntem imzasında belirtir (kırmızı ile birlikte bir Yarım tam beaker "🞩"), veya değil Live Unit Testing (mavi bir "➖" birlikte yarı tam beaker) katılan. Olmayan test yöntemleri bir simge ile donatılmış değil. Aşağıdaki şekilde, tüm dört tür yöntemleri gösterilmektedir.

  ![Görüntü](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Tanılama ve test hataları düzeltin

Başarısız test çalıştırmasından kolayca ürün kodu için hata ayıklama, düzenlemeler ve uygulamanızı geliştirmeye devam edebilirsiniz. Live Unit Testing arka planda çalıştığından, durdurma ve yeniden başlatma sırasında hata ayıklama, Live Unit Testing gerekmez Düzenle ve devam etme döngüsüne devam.

Örneğin, önceki şekilde gösterildiği test-alfabetik olmayan karakterler döndüren test yönteminde yanlış bir varsayım tarafından nedeniyle başarısız oldu `true` için geçirildiğinde <xref:System.Char.IsLower%2A?displayProperty=fullName> yöntemi. Şu test yönteminin düzeltin, sonra tüm testlerden geçtiğini bulun. Biz bunu yaparken, biz duraklatmak veya Live Unit Testing durdurmak zorunda değildir.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing ve Test Gezgini

Normalde, **Test Gezgini** çalıştırma, hata ayıklama ve test sonuçlarını çözümleme olanak sağlayan bir arabirim sağlar. Live Unit Testing ile tümleştirilir **Test Gezgini**. Live Unit Testing etkin değil ya da durdurulmuş, **Test Gezgini** birim testleri bir test çalıştırma son kez durumunu görüntüler. Testleri yeniden çalıştırın, kaynak kodu değişiklikleri gerektirir. Live Unit Testing etkin olduğunda, buna karşılık, birim durumu içinde testleri **Test Gezgini** hemen güncelleştirilir. Artık açıkça birim testlerinizi çalıştırmak gerekir.

> [!NOTE]
> Açabileceğiniz **Test Gezgini** seçerek **Test** > **Windows** > **Test Gezgini** gelen üst düzey Visual Studio menü.

Fark edebilirsiniz **Test Gezgini** bazı testler soluk penceresi. Örneğin, etkinleştirdiğinizde Live Unit Testing önceden kaydedilmiş bir projeyi açtıktan sonra **Test Gezgini** penceresi soluk tüm başarısız test, aşağıdaki şekilde gösterildiği gibi. Bu durumda, Live Unit Testing başarısız testi yeniden ancak başarılı testlerin yeniden değil, Live Unit Testing 's kalıcı yaptığınızdan veri test son başarıyla çalıştırılamadı bu yana herhangi bir değişiklik olduğunu gösterir.

  ![Görüntü](media/lut-test-explorer.png)

Seçerek soluk görünür tüm testleri yeniden **tümünü Çalıştır** veya **çalıştırın** gelen seçenekleri **Test Gezgini** menüsünden veya bir veya daha fazla test içinde seçerek**Test Gezgini** menüsünde sağ tıklatıp seçerek **seçili Testleri Çalıştır** veya **seçilen Testlerde Hata Ayıkla** açılan menüsünde. Testler çalışırken, Yukarı üst Kabarcık.

Live Unit Testing otomatik olarak çalıştırarak test sonuçları güncelleştiriliyor ve açıkça çalışan test eder. arasında bazı farklar vardır **Test Gezgini**. Bu farklar şunlardır:

- Live Unit Testing izleme eklenmiş ikili dosyalar çalıştırılır çalıştırma veya testleri Test Gezgini penceresinden hata ayıklama normal ikili dosyaları, çalışır.
- Live Unit Testing testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, ancak bunun yerine varsayılan etki alanından testleri çalıştırır. Testleri çalıştırın **Test Gezgini** penceresi, yeni bir uygulama etki alanı oluşturun.
- Live Unit Testing testler sırayla her bir test derlemesindeki çalıştırır. Birden çok testleri çalıştırırsanız **Test Gezgini** penceresi ve **çalıştırmak testlerini paralel** düğmesi seçildiğinde, testler paralel olarak.

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing ve büyük çözümler

Çözümünüzü 10 veya daha fazla proje, Live Unit Testing Başlat ve kalıcı veri sahip veya seçtiğinizde **Test** > **Live Unit Testing**  >  **Temiz sıfırlama** en üst düzey bir Visual Studio menüsünde, Visual Studio seçeneği büyük projeler testlerinde çok sayıda dinamik yürütme performansı ciddi bir şekilde etkileyebilir uyarmak için aşağıdaki iletişim kutusunu görüntüler. Seçerseniz **Tamam**, Live Unit Testing, Çözümdeki tüm testleri yürütür. Seçerseniz **iptal**, yürütülecek testleri seçebilirsiniz. Aşağıdaki bölümde, bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [dahil etme ve dışlama projelerin test ve test yöntemleri](#include-and-exclude-test-projects-and-test-methods).

 ![Büyük projeleri için Live Unit Testing iletişim](media/lut-large-project.png)

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Test projeleri hariç içerir ve test yöntemleri

Birçok test projeleri içeren çözümler için hangi projelerin ve bir projedeki her hangi bir yöntem içinde Live Unit Testing katılmak denetleyebilirsiniz. Örneğin, test projeleri yüzlerce bir çözümünüz varsa, test projeleri Live Unit Testing katılmak için hedeflenen bir dizi seçebilirsiniz. Dahil edilecek veya hariç çoğu testleri isteyip istemediğinizi proje veya çözüm, tüm testler hariç tutmak isteyip istemediğinizi bağlı olarak bunu yapmak için çeşitli yollarla vardır veya hariç tutmak istediğiniz ayrı ayrı test eder. Live Unit Testing içerme/dışlama durumunu bir kullanıcı ayarı olarak kaydeder ve bir çözüm kapatılıp yeniden olduğunda bunu hatırlar.

**Bir proje veya çözüm tüm testleri hariç**

Tek tek projeler birim testleri seçmek için Live Unit Testing başlatıldıktan sonra aşağıdakileri yapın:

1.  Çözüme sağ **Çözüm Gezgini** ve **Canlı testleri** > **hariç** çözümün tamamını dışlanacak.
1.  Sağ tıklayın ve testler eklemek istediğiniz her bir test projesi **Canlı testleri** > **Ekle**.

**Bireysel testler kod düzenleyici penceresinde hariç**

Kod Düzenleyicisi penceresi, dahil etmek veya bireysel test yöntemleri hariç tutmak için kullanabilirsiniz. Kod Düzenleyicisi penceresinde test metodunun İmzasındaki sağ tıklatın ve seçin **Canlı testleri** > **dahil [seçili yöntemi]**, **Canlı testleri**  >  **[Seçili yöntemi] hariç**, veya **Canlı testleri** > **hariç tüm ancak [seçili yöntemi]**, burada "Seçili yöntemi" adıdır Kod penceresinde seçtiğiniz yöntem.

**Testleri programlı olarak hariç**

Uygulayabileceğiniz <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> programlı olarak yöntemler, sınıflar veya yapılar kendi kapsamı içinde Live Unit Testing bildirimden hariç tutulacak özniteliği.

Live Unit Testing her bir yöntem hariç tutmak için de aşağıdaki öznitelikleri kullanabilirsiniz:

- XUnit için: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- NUnit için: `[Category("SkipWhenLiveUnitTesting")]`
- MSTest için: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Ayrıca bkz.

- [Kod test araçları](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing blogu](https://go.microsoft.com/fwlink/?linkid=842514)
- [Live Unit Testing SSS](live-unit-testing-faq.md)
- [Kanal 9 videosu: Visual Studio 2017'de Live Unit Testing](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
