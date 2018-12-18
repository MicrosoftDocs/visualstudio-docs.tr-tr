---
title: Modelleme çözümünüzün yapısını oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2c279da9aed4a11799004a38004f8b82dca65174
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966719"
---
# <a name="structure-your-modeling-solution"></a>Modelleme çözümünüzün yapısını oluşturma

Modelleri geliştirme projesindeki etkili bir şekilde kullanmak için ekip üyelerinin aynı anda farklı bölümlerini proje modelleri çalışabilmek için olmalıdır. Bu konuda öneren bir düzen uygulama katmanları genel bir karşılık gelen farklı parçalara bölmek için katman diyagramı.

Bir projeye başlayın ya da hızlı bir şekilde alt proje için seçtiğiniz Proje yapısı aşağıdaki proje şablonuna sahip kullanışlıdır. Bu konu, oluşturmak ve bu tür bir şablon kullanmak açıklar.

Bu konuda, birkaç ekip üyeleri gerektirecek kadar büyük olduğunu ve belki de Takımlarınız bir proje üzerinde çalışmakta olduğunuz varsayılır. Proje modelleri ve kod üzerinde kaynak denetim sistemi gibi depolanan [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. En azından bazı ekip üyeleri, modelleri geliştirmek için Visual Studio'yu kullanın ve diğer takım üyelerinin diğer Visual Studio sürümlerini kullanarak modelleri görüntüleyebilirsiniz.

Visual Studio'nun hangi sürümlerinin her aracı ve modelleme özelliğini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Çözüm yapısı

Orta veya büyük bir projede takım yapısı, yapıya uygulamanın temel alır. Her takım bir Visual Studio çözümünü kullanır.

### <a name="to-divide-an-application-into-layers"></a>Bir uygulamayı katmanlara ayırmak için

1. Web uygulaması, hizmet uygulama veya masaüstü uygulaması gibi uygulamanızın yapısını çözümlerinizi yapısını temel. Yaygın mimarileri çeşitli içinde ele alınmıştır [Microsoft Uygulama Mimarisi Kılavuzu'ndaki uygulama mimarisi türleri](http://go.microsoft.com/fwlink/?LinkId=196681).

2. Mimari çözüm sizi ararız bir Visual Studio çözümü oluşturun. Bu çözüm, genel sistem tasarımı oluşturmak için kullanılır. Modelleri, ancak hiçbir kodu içerecek.

   Bir bağımlılık diyagramı, bu çözüme ekleyin. Uygulamanız için seçtiğiniz mimari bağımlılık diyagram üzerinde çizin. Örneğin, diyagramda bu katmanlar ve aralarındaki bağımlılıkları gösterebilir: sunu; İş mantığı; ve verileri.

4. Mimari bağımlılık diyagramda her katman için ayrı bir Visual Studio çözümü oluşturun.

   Bu çözümler, katmanları kodunu geliştirmek için kullanılır.

5. Katmanlar ve tüm katmanlarda yaygın kavramları tasarımları temsil eden modeller oluşturun. Modelleri, böylece tüm modelleri Mimari çözümünden görülebilir ve ilgili modellerin her katmandan görülebilir düzenleyin.

   Aşağıdaki yordamlardan birini kullanarak bunu gerçekleştirebilirsiniz. İlk seçenek, her katman için ayrı bir modelleme projesi oluşturur ve ikinci katmanlar arasında paylaşılan tek bir modelleme projesi oluşturur.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Her bir katman için ayrı bir modelleme projesi kullanın

1. Her katman çözümde bir modelleme projesi oluşturun.

   Bu model gereksinimleri ve katman tasarımını açıklayan diyagramları içerir. Bağımlılık diyagramları, iç içe katmanlar Göster de içerebilir.

   Artık her katman için bir model yanı sıra, uygulama mimarisi için bir modeli vardır. Her model, kendi çözümde yer alır. Bu katmanlardaki aynı anda çalışmak takım üyeleri sağlar.

2. Her katman çözüm modelleme projesini Mimarisi çözüme ekleyin. Bunu yapmak için mimarisi çözümü açın. İçinde **Çözüm Gezgini**çözüm düğümüne sağ tıklayın, eklenecek gelin ve ardından **mevcut proje**. Çözümdeki bir katman modelleme projesi (.modelproj) gidin.

   Her model iki çözümlerinde görülebilir: "home", çözüm ve çözüm mimarisi.

3. Her katman modelleme projesine bir bağımlılık diyagramı ekleyin. Mimari bağımlılık diyagram bir kopyasını başlatın. Bağımlılık diyagramın bağımlılıkları olmayan parçaları silebilirsiniz.

   Bu katman ayrıntılı yapısını temsil eden bağımlılık diyagramları da ekleyebilirsiniz.

   Bu diyagramları bu katmanda geliştirilen kodu doğrulamak için kullanılır.

4. Visual Studio kullanarak tüm katmanlara yönelik tasarım modelleri ve gereksinimleri mimarisi çözümde düzenleyin.

   Her katman çözümde modele başvuran, söz konusu katman için kod geliştirin. Modeli güncelleştirmek için aynı bilgisayara kullanmadan geliştirme yapmak içerik modeli okumak ve modelleri oluşturulamıyor Visual Studio sürümlerini kullanarak kod geliştirin. Kod modelinden bu sürümleri de oluşturabilirsiniz.

   Bu yöntem, aynı anda katman modellerini düzenleme geliştiriciler tarafından hiçbir kesintiye neden garanti eder.

   Ancak, modelleri ayrı olduğundan, ortak kavramlara başvurmak zor olabilir. Her model, diğer katmanları ve mimariye bağımlı olduğu öğeleri kendine ait kopyasını olmalıdır. Her katman bağımlılık diyagramda mimari bağımlılık diyagram ile eşitlenmiş durumda tutulmalıdır. Bu öğeleri değiştirdiğinizde, bunu gerçekleştirmek için Araçlar geliştirmeniz ancak eşitleme elde etmek zordur.

#### <a name="use-a-separate-package-for-each-layer"></a>Her bir katman için ayrı bir paket kullanma

1. Her katmanın çözümde mimari modelleme projesine ekleyin. İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, fareyle **Ekle**ve ardından **mevcut proje**. Tek bir modelleme projesi artık her bir çözümden erişilebilir: Mimari proje ve her katman için geliştirme projesi.

2. Paylaşılan modeldeki her bir katman için paket oluşturma: içinde **Çözüm Gezgini**, modelleme projesini seçin. İçinde **UML Model Gezgini**, model kök düğümüne sağ tıklayın, fareyle **Ekle**ve ardından **paket**.

   Her paket gereksinimleri ve ilgili katmanı tasarımını açıklayan diyagramları içerir.

3. Gerekirse, her katmanın iç yapısı için yerel bağımlılık diyagramları ekleyin.

   Bu yöntem, her katmanın doğrudan bu bağımlı olduğu bir yaygın mimari ve katman başvurmak için tasarım öğeleri sağlar.

   Eşzamanlı işler farklı paketleri bazı çakışmalara neden olabilir, ancak paketleri ayrı dosyalarda depolandığından Yönetimi oldukça kolaydır.

## <a name="create-architecture-templates"></a>Mimari şablonları oluşturma

Uygulamada, aynı anda tüm Visual Studio çözümleri oluşturma ancak bunları Proje ilerledikçe ekleyin. Büyük olasılıkla da aynı çözüm yapısını gelecekteki projeleri kullanın. Yeni çözümleri hızlı bir şekilde oluşturmanıza yardımcı olmak için bir çözüm veya proje şablonu oluşturabilirsiniz. Böylece bir kolayca dağıtmak ve diğer bilgisayarlara yüklemek için bir Visual Studio Tümleştirme Uzantısı (VSIX) içinde şablon yakalayabilirsiniz.

Örneğin, sık sık sunu, iş ve veri katmanlarına sahip bir çözüm kullanıyorsanız, bu yapıya sahip yeni çözümler oluşturan şablondan yapılandırabilirsiniz.

### <a name="to-create-a-solution-template"></a>Bir çözüm şablonu oluşturmak için

1. [Şablonu Dışarı Aktarma Sihirbazı'nı indirip](http://go.microsoft.com/fwlink/?LinkId=196686).

2. İleride gerçekleştirilecek projeler için bir başlangıç noktası olarak kullanmak istediğiniz çözüm yapısını oluşturun.

3. Üzerinde **dosya** menüsünde tıklatın **VSIX olarak şablonu dışarı aktar**.

   **VSIX Sihirbazı olarak dışarı aktarma şablonu** açılır.

4. Sihirbazdaki yönergeleri, şablona dahil, bir ad ve şablon için bir açıklama girin ve bir çıkış konumunu belirtme istediğiniz projeleri seçin.

## <a name="watch-a-video"></a>Bir video izleyin

[Düzenleme ve Modellerinizi yönetme](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Ayrıca Bkz.

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Visual Studio Mimari Araç Kullanımı Kılavuzu](../modeling/visual-studio-architecture-tooling-guidance.md)
