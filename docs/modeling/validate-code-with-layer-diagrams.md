---
title: Bağımlılık diyagramları ile kod doğrulama
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71eebd95db1a616d4f86866ef60fb32251634cc0
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967291"
---
# <a name="validate-code-with-dependency-diagrams"></a>Bağımlılık diyagramları ile kod doğrulama

## <a name="why-use-dependency-diagrams"></a>Bağımlılık diyagramları neden kullanmalısınız?

Kodun tasarımıyla çakışmamasını sağlamak için kodunuzu Visual Studio'da bağımlılık diyagramları ile doğrulayın. Bu, şu konularda size yardımcı olabilir:

- Bağımlılık diyagram üzerinde kodunuzdaki bağımlılıkları ve bağımlılıklar arasında çakışmaları bulun.

- Önerilen değişiklikler tarafından etkilenebilecek bağımlılıkları bulun.

   Örneğin, olası mimari değişiklikleri göstermek ve ardından etkilenen bağımlılıkları görmek için kodu doğrulamak için bağımlılık diyagramı düzenleyebilirsiniz.

- Kodu yeniden düzenleyin veya kodu farklı bir tasarıma geçirin.

   Kodu farklı bir mimariye taşıdığınız zaman iş gerektiren kodu veya bağımlılıkları bulun.

**Gereksinimler**

- Visual Studio

- Bir bağımlılık diyagram ile bir modelleme projesi olan çözüm. Bu bağımlılık diyagramı, doğrulamak istediğiniz C# veya Visual Basic projelerinde yapılara bağlı olmalıdır. Bkz: [kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).

> [!NOTE]
> Bağımlılık diyagramları Visual Studio 2017'de .NET Core projeleri için desteklenmiyor.

Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Kodu Visual Studio'da açık bir bağımlılık diyagramından el ile veya komut isteminde doğrulayabilirsiniz. Yerel yapıları veya Azure işlem hatları çalıştıran oluşturduğunda otomatik olarak kod da doğrulayabilirsiniz. Bkz: [kanal 9 videosu: tasarım ve bağımlılık diyagramlarını kullanarak Mimarinizi doğrulama](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Team Foundation Server (TFS) kullanarak katman doğrulaması çalıştırmak istiyorsanız, yapı sunucunuzda ayrıca Visual Studio'nun aynı sürümünü yüklemeniz gerekir.

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulama

Bağımlılık doğrulama, gerçek zamanlı olarak gerçekleşir ve hataları gösterilir hemen **hata listesi**.

* Canlı doğrulama, C# ve Visual Basic için desteklenir.

* Canlı bağımlılık doğrulama kullanırken tam çözüm analizini etkinleştirmek için görüntülenen sarı renkli çubuk seçeneklerini açık **hata listesi**.

   - Çözümünüzdeki tüm mimari sorunları görmeniz değil ilgileniyorsanız, kalıcı olarak sarı renkli çubuk yok sayabilirsiniz.
   - Tam çözüm analizini etkinleştirme, analiz düzenlenmekte olan dosyalar için gerçekleştirilir.

* Canlı doğrulamasını etkinleştirmek için projeleri yükseltme yaparken, bir iletişim kutusu dönüştürme işleminin ilerleme durumunu gösterir.

* Canlı bağımlılık doğrulama projesi güncelleştirilirken NuGet paketinin sürümünü tüm projelerde aynı olacak şekilde yükseltilir ve en yüksek sürümü.

* Yeni bir bağımlılık doğrulama projesi tetikleyiciler, bir proje güncelleştirmesi ekleniyor.

## <a name="see-if-an-item-supports-validation"></a>Bir öğenin doğrulamayı destekleyip desteklemediğini görme

Katmanları Web sitelerine, Office belgeleri, düz metin dosyaları ve birden çok uygulama arasında paylaşılan projelerdeki dosyaları bağlayabilirsiniz, ancak doğrulama işlemi bunları içermeyecektir. Doğrulama hataları, aralarında hiçbir bağımlılığın görünmediği ayrı katmanlara bağlanmış projelere veya derlemelere olan başvurular için görünmez. Kod bu başvuruları kullanmazsa böyle başvurular bağımlılık olarak düşünülmez.

1.  Bağımlılık diyagram üzerinde bir veya daha fazla katmanları seçin, seçiminize sağ tıklayın ve ardından **bağlantıları görüntüle**.

2.  İçinde **Katman Gezgini**, bakmak **doğrulamayı destekler** sütun. Değer false ise, öğe doğrulamayı desteklemez.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Diğer .NET derlemelerini ve projelerini doğrulama için dahil etme

Öğeleri bağımlılık diyagramına sürüklediğinizde, karşılık gelen .NET derlemeleri veya projelerine başvurular otomatik olarak eklenir **katman başvuruları** modelleme projesindeki klasör. Bu klasör, doğrulama sırasında analiz edilen derlemeler ve projeler için başvurular içerir. Diğer .NET derlemelerini ve projelerini doğrulama için bağımlılık diyagramına sürükleyerek olmadan el ile ekleyebilirsiniz.

1.  İçinde **Çözüm Gezgini**, modelleme projesine sağ tıklayın veya **katman başvuruları** klasörünü ve ardından **Başvuru Ekle**.

2.  İçinde **Başvuru Ekle** iletişim kutusunda, derlemeleri veya projeleri seçin ve ardından **Tamam**.

## <a name="validate-code-manually"></a>Kodu el ile doğrulama

Çözüm öğelerine bağlı bir açık bağımlılık diyagramı varsa, çalıştırabileceğiniz **doğrulama** diyagramı kısayol komutu. Çalıştırmak için komut istemini kullanabilirsiniz **msbuild** komutunu **ValidateArchitecture** özel özellik kümesine **True**. Örneğin, kodda değişiklik yaparken bağımlılık çakışmalarını önceden yakalayabilmek için düzenli olarak katman doğrulama gerçekleştirin.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Açık bir bağımlılık diyagramından kodu doğrulama

1.  Diyagram yüzeyine sağ tıklayın ve ardından **Mimariyi Doğrula**.

    > [!NOTE]
    > Varsayılan olarak, **derleme eylemi** bağımlılık diyagramı (.layerdiagram) dosyasındaki özelliği **doğrulama** böylece doğrulama işleminde diyagramın dahildir.

     **Hata listesi** penceresi oluşan hataları bildirir. Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).

2.  Her hatanın kaynağını görüntülemek için hataya çift **hata listesi** penceresi.

    > [!NOTE]
    > Visual Studio, hatanın kaynağı yerine bir kod Haritası gösterebilir. Bu kod, bağımlılık diyagram tarafından belirtilmemiş bir derleme üzerinde bağımlılık vardır veya kodu, bağımlılık diyagramı tarafından belirlenen bağımlılığı eksikse ortaya çıkar. Kod haritası veya bağımlılık var olup olmadığını belirlemek için kodu gözden geçirin. Kod haritaları hakkında daha fazla bilgi için bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).

3.  Hataları yönetmek için bkz: [doğrulama hatalarını Yönet](#ManageErrors).

### <a name="validate-code-at-the-command-prompt"></a>Komut isteminde kodu doğrulama

1. Visual Studio komut istemi açın.

2. Aşağıdakilerden birini seçin:

   - Çözümde belirli modelleme projesine karşı kodu doğrulamak için aşağıdaki özel özelliğiyle MSBuild'ı çalıştırın.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - veya -

       Gözat modelleme projesi (.modelproj) içeren klasörü için dosya ve bağımlılık Diyagram ve aşağıdaki özel özelliğiyle MSBuild çalıştırın:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Kodu Çözümdeki tüm modelleme projelerine karşı doğrulamak için aşağıdaki özel özelliğiyle MSBuild çalıştır:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - veya -

       Bağımlılık diyagramı içeren modelleme projesini içermesi gerekir ve ardından aşağıdaki özel özelliğiyle MSBuild Çalıştır çözüm klasörüne göz atın:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Oluşan hatalar listelenecektir. MSBuild hakkında daha fazla bilgi için bkz. [MSBuild](../msbuild/msbuild.md) ve [MSBuild görevi](../msbuild/msbuild-task.md).

   Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).

### <a name="manage-validation-errors"></a>Doğrulama hatalarını yönetme

Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Hatayı gizlediğinizde, Team Foundation iş öğesini kaydetmek iyi bir uygulamadır.

> [!WARNING]
> Zaten için TFS kaynak kod denetimi (oluşturmak veya bir çalışma öğesiyle bağlantılandırmak için SCC) bağlı olmanız gerekir. Farklı bir TFS SCC bağlantı açmayı denerseniz, Visual Studio otomatik olarak geçerli çözümü kapatır. Zaten için uygun SCC oluşturmak veya bir çalışma öğesiyle bağlantılandırmak denemeden önce bağlı olduğunuzdan emin olun. Visual Studio daha sonraki sürümleri için bir SCC bağlı değilseniz, menü komutlarını kullanılamaz.

#### <a name="create-a-work-item-for-a-validation-error"></a>Doğrulama hatası için iş öğesi oluşturma

- İçinde **hata listesi** penceresinde hataya sağ tıklayın, fareyle **iş öğesi oluştur**ve ardından oluşturmak istediğiniz iş öğesinin türüne tıklayın.

Doğrulama hatalarını yönetmek için bu görevleri kullanın **hata listesi** penceresi:

|**Hedef**|**Aşağıdaki adımları izleyin**|
|-|-|
|Doğrulama sırasında seçili hataları gizleme|Bir veya birden çok seçili hataya sağ tıklayın, fareyle **doğrulama hatalarını Yönet**ve ardından **Hataları Gizle**.<br /><br /> Gizlenen hatalar üstü çizili biçimde görünür. Doğrulamayı daha sonra çalıştırdığınızda bu hatalar görünmez.<br /><br /> Gizlenen hatalar bir karşılık gelen bağımlılık diyagramı dosyası için .gizlenenler dosyasında izlenir.|
|Seçili hataların gizlenmesini durdurma|Seçili gizlenen hata veya hatalara sağ tıklayın, fareyle **doğrulama hatalarını Yönet**ve ardından **hataları gizlemeyi Durdur**.<br /><br /> Doğrulamayı daha sonra çalıştırdığınızda seçili gizlenen hatalar görünecektir.|
|Tüm gizlenmiş hataları geri yükleme **hata listesi** penceresi|Herhangi bir yere sağ **hata listesi** penceresi **doğrulama hatalarını Yönet**ve ardından **tüm gizlenmiş hataları göster**.|
|Tüm gizlenmiş Hataları Gizle **hata listesi** penceresi|Herhangi bir yere sağ **hata listesi** penceresi **doğrulama hatalarını Yönet**ve ardından **tüm gizlenmiş Hataları Gizle**.|

## <a name="validate-code-automatically"></a>Kodu otomatik olarak doğrulama

Her yerel bir yapı çalıştırışınızda katman doğrulama gerçekleştirebilirsiniz. Azure DevOps takımınızın kullandığı ile Geçitli iade etme doğrulama hatalarını toplamak için yapı raporları kullanabilirsiniz ve özel bir MSBuild görevi oluşturarak belirtebileceğiniz işlemleri, katman doğrulama gerçekleştirebilirsiniz. Geçitli iade yapıları oluşturmak için bkz [TFVC geçişli iade](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Kodu yerel yapı sırasında otomatik olarak doğrulamak için

Modelleme projesi (.modelproj) dosyası açmak için metin düzenleyicisi kullanın ve ardından aşağıdaki özelliği ekleyin:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- veya -

1.  İçinde **Çözüm Gezgini**bağımlılık diyagramı veya diyagramları içeren modelleme projesine sağ tıklayın ve ardından **özellikleri**.

2.  İçinde **özellikleri** penceresinde modelleme projesinin ayarlayın **Mimariyi Doğrula** özelliğini **True**.

    Bu, doğrulama işlemi içinde modelleme projesini içerir.

3.  İçinde **Çözüm Gezgini**, doğrulama için kullanmak istediğiniz bağımlılık diyagramı (.layerdiagram) dosyasına tıklayın.

4.  İçinde **özellikleri** penceresinde emin olun diyagramın **derleme eylemi** özelliği **doğrulama**.

    Bu bağımlılık diyagramı doğrulama işlemindeki içerir.

Hata Listesi penceresindeki hataları yönetmek için bkz: [doğrulama hatalarını Yönet](#ManageErrors).

## <a name="troubleshoot-layer-validation-issues"></a>Katman doğrulama sorunlarını giderme

Aşağıdaki tabloda katman doğrulama sorunları ve bunların çözümü açıklanmaktadır. Bu sorunlar, kod ve tasarım arasındaki çakışmalarla sonuçlanan hatalardan ayrılır. Bu hatalar hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).

|**Sorunu**|**Olası nedeni**|**Çözümleme**|
|-|-|-|
|Doğrulama hataları beklendiği gibi gerçekleşmez.|Doğrulama, Çözüm Gezgini'ndeki diğer bağımlılık diyagramlarından kopyalanmış ve aynı modelleme projesinde olan bağımlılık diyagramları üzerinde çalışmaz. Bu şekilde kopyalanan bağımlılık diyagramları, orijinal bağımlılık diyagram aynı başvuruları içerir.|Yeni bir bağımlılık diyagramı modelleme projesine ekleyin.<br /><br /> Öğeleri kaynak bağımlılık diyagramından yeni diyagrama kopyalayın.|

## <a name="resolve-layer-validation-errors"></a>Katman doğrulama hatalarını çözme

Kod bir bağımlılık diyagramına karşı doğruladığınız zaman, kod tasarımla çakıştığında doğrulama hataları oluşur. Örneğin, aşağıdaki durumlar doğrulama hatalarının oluşmasına neden olabilir:

- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.

- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.

Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu görevi yinelemeli bir şekilde gerçekleştirebilirsiniz.

Aşağıdaki bölümde, bu hatalarda kullanılan sözdizimi belirtilmekte, bu hataların anlamı açıklanmakta ve bunları çözmek veya yönetmek için yapabilecekleriniz önerilmektedir.

|**Söz dizimi**|**Açıklama**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* bağımlılık diyagramında bir katman ile ilişkilendirilmiş bir yapıdır.<br /><br /> *ArtifactTypeN* türü *ArtifactN*, gibi bir **sınıfı** veya **yöntemi**, örneğin:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Bir ad alanının adı.|
|*LayerNameN*|Bağımlılık diyagramındaki katmanın adı.|
|*DependencyType*|Arasındaki bağımlılık ilişkisinin türü *Artifact1* ve *Artifact2*. Örneğin, *Artifact1* sahip bir **çağrıları** ilişkisine sahip *Artifact2*.|

| **Hata sözdizimi** | **Hata açıklaması** |
|-|-|
| DV0001: **Geçersiz bağımlılık** | Bu sorun, bir kod öğesi (ad alanı, tür, üye) başka bir katmana eşlenmiş bir kod öğesi için bir katman başvuruları eşlenmiş, ancak bu bu katmanları içeren bağımlılık doğrulama diyagramı Katmanlar arasındaki bağımlılık ok yok bildirilir. Bir bağımlılık kısıtlama ihlali budur. |
| DV1001: **geçersiz ad alanı adı** | Bu sorun, "Namespace adlarına izin" özelliği bu kod öğe tanımlandığı ad alanı içermeyen bir katman ile ilişkili bir kod öğesinin bildirilir. Bir adlandırma kısıtlaması ihlali budur. "Namespace adlarına izin" söz dizimi ad alanları hangi kod öğeleri ile ilişkili katmandır noktalı virgülle ayrılmış listesi olacak Not tanımlanacak verilir. |
| DV1002: **başvurulamayan ad alanında bağımlılık** | Bu sorun, bir katman ile ilişkili ve Katmanı "Başvurulamayan Namespace" özelliğinde tanımlanan bir ad alanında tanımlanan başka bir kod öğe başvuran bir kod öğesinin bildirilir. Bir adlandırma kısıtlaması ihlali budur. "Başvurulamayan ad alanları" özelliği bir noktalı virgülle ayrılmış liste içinde bu katman ile ilişkili kod öğelerine başvurulmaması gereken ad alanları olarak tanımlandığını aklınızda bulundurun. |
| DV1003: **izin verilmeyen ad alanı adı** | Bu sorun, bu kod öğe tanımlandığı ad alanı "Namespace ad izin verilmeyen" özelliği içeren bir katman ile ilişkili bir kod öğesinin bildirilir. Bir adlandırma kısıtlaması ihlali budur. "Ad alanı adı izin verilmeyen" özelliği ad alanları hangi kod öğeleri bu katman ile ilişkili değil tanımlanmalıdır noktalı virgülle ayrılmış listesi olarak tanımlandığını aklınızda bulundurun. |
| DV3001: **Missing LINK** | Katman '*LayerName*'bağlantı'*Yapıt*' bulunamıyor. Eksik bir derleme başvurunuz mu var? |
| DV9001: **mimari çözümleme iç hatalar buldu** | Sonuçlar tamamlanmamış olabilir. Daha fazla bilgi için ayrıntılı yapı olay günlüğü veya çıkış penceresine bakın. |

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017'de canlı bağımlılık doğrulama](https://blogs.msdn.microsoft.com/devops/2016/11/30/live-dependency-validation-in-visual-studio-2017/)
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)
- [Video: Gerçek zamanlı mimari bağımlılıklarınızı doğrula](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)