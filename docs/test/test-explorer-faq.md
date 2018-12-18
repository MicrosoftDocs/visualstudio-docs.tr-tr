---
title: Test Gezgini Hakkında SSS
ms.date: 11/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: douge
ms.openlocfilehash: 59c4cd06ee6c698ceb62803fb43b611daa298512
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055270"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio Test Gezgini hakkında SSS

## <a name="dynamic-test-discovery"></a>Dinamik test bulma

**Test Gezgini dinamik olarak tanımlanan testlerimi bulma değil. (Örneğin, Teoriler, özel bağdaştırıcı, özel özellikleri, #ifdefs, vb.) Bu testleri bulmak ne?**

  Derleme tabanlı bulma içinde açık olduğundan emin olun ve projenizi **Araçları** > **seçenekleri** > **Test**.

  [Gerçek zamanlı test bulma](https://go.microsoft.com/fwlink/?linkid=862824) kaynak tabanlı test bulma. Teoriler, özel bağdaştırıcı, özel özellikleri kullanan testler bulamaz `#ifdef` deyimleri ve çalışma zamanında tanımlanmış için daha fazla. Bir derleme, bu testler doğru bir şekilde bulunması gereklidir. Visual Studio 2017 sürüm 15.6 ve daha sonra derleme tabanlı bulma (Geleneksel Bulucu) yalnızca derlemeler sonra çalışır. Bu yöntem gerçek zamanlı test bulma işleminin, düzenlerken mümkün olduğunca çok testleri ayarlama ve derleme tabanlı bulma, dinamik olarak tanımlanan testleri, derleme sonrası görünmesini sağlar. Gerçek zamanlı test bulma yanıt hızını artırır ancak durağan derleme sonrası tamamlandı ve kesin sonuçlar elde izin verir.

## <a name="test-explorer--plus-symbol"></a>Test Gezgini '+' (sembolü artı)

**Ne yaptığını '+' (artı) Test Gezgini ortalama ilk satırda görünen simge?**

  '+' (Artı) sembolü, derleme tabanlı bulma açık olduğu sürece, daha fazla test derleme sonrası bulunan belirtir. Test projenizde algılanan dinamik olarak tanımlanmışsa bu simge görünür.

  ![Artı özet satırı simgesi](media/testex-plussymbol.png)

## <a name="assembly-based-discovery"></a>Derleme tabanlı bulma

**Derleme tabanlı bulma artık Projem için çalışmaktadır. Nasıl bu kapatırım yeniden?**

  Git **Araçları** > **seçenekleri** > **Test** ve kutusunu işaretlemeniz **testleri yerleşik derlemelerden sonra ayrıca keşfedin oluşturur.**

  ![Derleme tabanlı seçeneği](media/testex-toolsoptions.png)

## <a name="real-time-test-discovery"></a>Gerçek zamanlı test bulma

**Ben Projemi oluşturmak zorunda kalmadan, yazarken testleri şimdi Test Gezgini'nde görünür. Neler değişti?**

  Bu özelliğin adı [gerçek zamanlı test bulma](https://go.microsoft.com/fwlink/?linkid=862824). Testleri bulmak ve Test Gezgini, projenizi oluşturmaya gerek kalmadan gerçek zamanlı olarak doldurmak için Roslyn çözümleyicinizi kullanır. Teoriler veya özel nitelikler gibi dinamik olarak tanımlanan testler için test bulma davranış hakkında daha fazla bilgi için bkz. SSS 1.

## <a name="real-time-test-discovery-compatibility"></a>Gerçek zamanlı test bulma uyumluluğu

**Gerçek zamanlı Test bulma, hangi diller ve test çerçeveleri kullanabilir miyim?**

  [Gerçek zamanlı test bulma](https://go.microsoft.com/fwlink/?linkid=862824) yalnızca yönetilen diller için çalışır (C# ve Visual Basic), bu yana Roslyn derleyicisi kullanılarak oluşturulmuştur. Şimdilik, gerçek zamanlı test bulma yalnızca xUnit, NUnit ve MSTest çerçeveleri çalışır.

## <a name="test-explorer-logs"></a>Test Gezgini günlükleri

**Test Gezgini için nasıl günlüklerini kapatırım?**

  Gidin **Araçları** > **seçenekleri** > **Test** ve günlüğe kaydetme bölümü bulun.

## <a name="uwp-test-discovery"></a>UWP test bulma

**Neden testlerimi uygulamamı dağıtabilirim kadar bulunmayan UWP projelerinde?**

  Uygulama dağıtıldığında UWP testler farklı bir çalışma zamanı hedef. Bu, doğru bir şekilde UWP projeleri için testleri bulmak için yalnızca derleme, ancak ayrıca dağıtmanız gerektiğini anlamına gelir.

## <a name="test-explorer-sorting"></a>Test Gezgini sıralama

**Sıralama test sonuçlarını hiyerarşi Görünümü'nde nasıl çalışır?**

  Hiyerarşi görünümü alfabetik olarak öğesine test sonucuna göre sıralar. Diğer grubun ayarlarını normalde test sonuçlarını sonucuna göre sıralama ve alfabetik olarak. Aşağıdaki görüntüde karşılaştırma için seçenekleri tarafından farklı bir gruba bakın. Tasarım hakkında geri bildirim sağlayabilirsiniz [bu GitHub sorunu içinde](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Test Gezgini hiyerarşi görünümü

**Hiyerarşi Görünümü'nde var. geçirilir, proje ve Namespace sınıfını gruplandırmaları yanındaki başarısız, atlandı ve çalıştırılmadı simgeler. Bu simgeleri ne anlama gelir?**

  Proje ve Namespace sınıfını gruplandırmaları yanındaki simge, o grup içindeki testlerin durumunu gösterir. Aşağıdaki tabloya bakın.

  ![Test Gezgini hiyerarşi simgeleri](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Dosya yoluna göre arama

**Test Gezgini arama kutusuna artık "Dosya yolu" filtresi var.**

Dosya yolu filtrede **Test Gezgini** arama kutusuna, Visual Studio 2017 sürüm 15.7 Önizleme 3 kaldırıldı. Bu özellik kullanımın düşük olduğu ve Test Gezgini, bu özelliği bırakarak test yöntemlerini daha hızlı alabilir. Bu değişiklik, geliştirme akışınızı keser, hakkında geri bildirim göndererek bize [Geliştirici topluluğu](https://developercommunity.visualstudio.com/).

## <a name="remove-undocumented-interfaces"></a>Belgelenmemiş arabirimleri Kaldır

**Bazı test ile ilgili API'ler, artık Visual Studio 2019 içinde mevcut değildir. Neler değişti?**

Visual Studio 2019 ', bazı test penceresi daha önce genel olarak işaretlenmiş, ancak hiçbir zaman resmi olarak belgelenen API'leri kaldırılacak. Bunlar, "Visual Studio uzantısı maintainers erken bir uyarı vermek için 2017'de kullanım dışı"olarak işaretlenmiş. Bizim bilgi için çok az sayıda uzantıları bu API'leri bulundu ve bir bağımlılık bunlar üzerinde gerçekleştirilen. Bunlar `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken`, ve `SearchFilterTokenType`. Bu değişiklik uzantınızı etkiliyorsa, üzerinde bir hatayı dosyalama bize [Geliştirici topluluğu](https://developercommunity.visualstudio.com).

## <a name="test-adapter-nuget-reference"></a>Test bağdaştırıcısı NuGet başvurusu

**Visual Studio 2017 sürüm 15,8 testlerimi bulunan, ancak yürütme yok.**

Tüm test projelerinde, .csproj dosyasında kendi .NET test bağdaştırıcısı NuGet başvuru içermelidir. Hizmet sağlanmıyorsa aşağıdaki test çıkışı projede derleme sonrası bulma bir test bağdaştırıcısı uzantısı tarafından başlatılır veya kullanıcı seçili testleri çalıştırmayı dener görünür:

**Test projesi {} herhangi bir .NET NuGet bağdaştırıcı başvurmuyor. Test bulma veya yürütme bu proje için çalışmayabilir. Her çözüm .NET test projesinde test bağdaştırıcısı, NuGet başvuru önerilir.**

Test bağdaştırıcısı uzantılarından kullanmak yerine, projeleri test bağdaştırıcısı NuGet paketlerini kullanmak için gerekli değildir. Bu gereksinim, büyük ölçüde performansı artırır ve daha az sorunları ile sürekli tümleştirme neden olur. .NET Test bağdaştırıcısı uzantısı kullanımdan kaldırma hakkında daha fazla bilgiyi [sürüm notları](/visualstudio/releasenotes/vs2017-preview-relnotes#testadapterextension).

> [!NOTE]
> NUnit 3 test bağdaştırıcısı'na yükseltemedi olan ve NUnit 2 Test bağdaştırıcısı kullanıyorsanız, bu yeni Visual Studio sürümünde 15,8 bulma davranışı kapatabilirsiniz **Araçları** > **seçenekleri**  >  **Test**.

  ![Araçlar seçeneklerinde Gezgini bağdaştırıcısı davranışını sınama](media/testex-adapterbehavior.png)

## <a name="uwp-testcontainer-was-not-found"></a>UWP TestContainer bulunamadı

**UWP testlerimi artık Visual Studio 2017 sürüm 15.7 ve üzeri yürütülür.**

Son UWP test projeleri, test uygulamaları tanımlamak için daha iyi performans sağlayan bir test platformu yapı özelliğini belirtin. Visual Studio 15.7 Sürüm önce başlatıldı bir UWP test projesi varsa, bu hatayı görebilirsiniz **çıkış** > **testleri**:

**System.AggregateException: Bir veya daha fazla hata oluştu. System.InvalidOperationException--->: şu TestContainer bulunamadı {} Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider adresindeki <GetTestContainerAsync>d__61.MoveNext()**

Bu hatayı düzeltmek için:

- Aşağıdaki kodu kullanarak, test projesi yapı özelliği güncelleştirin:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aşağıdaki kodu kullanarak TestPlatform SDK sürümü güncelleştir:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Özellik bayraklarını kullanarak

**Yeni test özellikleri denemek için özellik bayraklarını üzerinde nasıl kapatabilir miyim?**

Özellik bayrakları, ürün özellikleri resmi olarak sevk etmeden önce geri bildirim sağlamak ister misiniz kullanıcılar avid Deneysel veya tamamlanmamış bölümlerini göndermeye kullanılır. Bunlar, IDE deneyimi kararlılığını. Yalnızca güvenli geliştirme ortamlarında, sanal makineler gibi bunları kullanın. Özellik bayrakları her zaman kullanın--your-kendi-riskli ayarlarıdır. Deneysel özellikler ile etkinleştirebilirsiniz [özellik bayraklarını uzantısı](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), veya Geliştirici komut istemi aracılığıyla.

![Özellik bayrağı uzantısı](media/testex-featureflag.png)

Visual Studio Geliştirici komut istemi üzerinden bir özellik bayrağını etkinleştirmek için aşağıdaki komutu kullanın. Yol, Visual Studio makinenizde yüklü olduğu için ve kayıt defteri anahtarı istediğiniz özellik bayrağını değiştirin.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Dword sonra 1 yerine 0 değerini kullanarak aynı komutla bayrağı kapatabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Oluşturma ve mevcut koda yönelik birim testleri çalıştırma](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Birim testi kod](unit-test-your-code.md)
- [Canlı birim testi ile ilgili SSS](live-unit-testing-faq.md)
