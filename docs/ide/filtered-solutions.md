---
title: Projelerin bir alt kümesini yükleme
ms.date: 12/04/2018
ms.topic: conceptual
ms.prod: visual-studio-dev16
ms.technology: vs-ide-general
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: douge
ms.openlocfilehash: 655644e936bdfb1382e70d746f589b8fcfabf488
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896988"
---
# <a name="filtered-solutions-in-visual-studio"></a>Visual Studio'da filtrelenmiş çözümleri

**Yeni Visual Studio 2019 Önizleme 1**

Genellikle büyük geliştirme takımları ile çok sayıda proje tek büyük bir çözümde kullanarak işbirliği yapın. Ancak, bireysel geliştiriciler genellikle bu projeler küçük bir kısmı üzerinde çalışır. Büyük çözümlerde açılırken performansını geliştirmek için Visual Studio 2019 Önizleme 1 tanıtır *çözüm filtreleme*. Çözüm filtreleme yalnızca yüklenen seçmeli projeleriyle bir çözüm açın sağlar. Bir alt kümesini bir çözümde proje yüklemeyi çözüm yükü, yapı ve test çalışma zamanı azaltır ve etkinleştirir gözden geçirme daha odaklı.

Aşağıdaki özellikler mevcuttur:

- Daha hızlı bir çözüm açarak projeleri yüklemeden kodu alabilirsiniz. Çözüm açıldıktan sonra yükleme için hangi projelerin seçerek belirleyebilirsiniz.

- Bir çözümü yeniden açın, Visual Studio önceki oturumunuzda hangi projelerin yüklenmiş hatırlar ve yalnızca bu projeleri yükler.

- Bir veya daha fazla proje yükü yapılandırmaları kaydetme veya yapılandırma arkadaşlarıyla paylaşmak için bir çözüm filtre dosyası oluşturabilirsiniz.

## <a name="open-a-filtered-solution"></a>Filtrelenmiş bir çözüm açın

Yalnızca bazı yüklenen projeleri ile bir çözümü açmak için şu adımları izleyin:

1. Seçin **dosya** > **açık** > **proje/çözüm** menü çubuğundan.

2. İçinde **yeni proje** iletişim çözümünü seçin ve ardından **proje yüklenmemesine**.

   ![Visual Studio Proje Aç iletişim kutusunda seçili projeler yüklenmez](media/filtered-solutions/do-not-load-projects.png)

3. Seçin **açık**.

   Çözüm tüm yüklenmemiş projeleri ile açılır.

4. İçinde **Çözüm Gezgini**, yüklemek istediğiniz projeleri seçin (basın **Ctrl** birden fazla proje seçmek için tıklatırken) ve ardından proje üzerinde sağ tıklatın ve seçin **projeyi yeniden yükle** .

   ![Visual Studio Çözüm Gezgini'nde birden çok projeleri yeniden yükle](media/filtered-solutions/reload-project.png)

   Visual Studio çözümünü yerel olarak bir sonraki açışınızda hangi projelerin yüklenen hatırlanır.

## <a name="toggle-unloaded-project-visibility"></a>Yüklenmemiş proje görünürlüğünü Değiştir

Çözümdeki tüm projeleri veya yalnızca aşağıdaki seçeneklerden birini kullanarak yüklü olanları görmek seçebileceğiniz **Çözüm Gezgini**:

- Çözümü sağ tıklatın **yüklenmemiş projeleri göster** veya **yüklenmemiş projeleri Gizle**.

- Seçin **tüm dosyaları göster** yüklenmemiş projeleri görünürlüğünü açıp kapatmak için düğme.

   ![Visual Studio Çözüm Gezgini'nde tüm dosyaları düğmesini göster](media/filtered-solutions/show-all-files.PNG)

## <a name="solution-filter-files"></a>Çözüm filtresi dosyaları

Proje yükü yapılandırmanızı paylaşabilir veya kaynak denetimine uygulamak istiyorsanız, bir çözüm filtre dosyası oluşturabilirsiniz (uzantısına sahip *.slnf*). Bir çözüm filtre dosyasını açtığınızda, çözüm yüklenen belirtilen projeleri ile gizli yüklenmemiş projeleri Visual Studio'da açılır. Yapabilecekleriniz [geçiş](#toggle-unloaded-project-visibility) yüklenmemiş projeleri görüntülemek için.

Çözüm filtresi dosyaları görsel olarak ayırt normal çözüm dosyaları ek Huni glifine çözümde yanındaki simge tarafından **Çözüm Gezgini**. Filtre ve yüklenen projelerin sayısını adını da çözüm adının yanında gösterilir.

![Çözüm filtre dosyası Visual Studio Çözüm Gezgini'nde Aç](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Çözüm filtresi dosyasını oluşturduktan sonra özgün çözüme yeni proje eklenirse, kaldırılan projelerinde olarak görünürler **Çözüm Gezgini**.

### <a name="create-a-solution-filter-file"></a>Bir çözüm filtre dosyası oluşturma

1. İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve seçin **çözüm filtre olarak Kaydet**.

   ![Visual Studio Çözüm Gezgini'nde çözüm filtre olarak Kaydet menüsü](media/filtered-solutions/save-as-solution-filter.png)

2. Bir ad ve çözüm filtre dosyası için konum seçin.

Bir çözüm filtre dosyasını oluşturduktan sonra eklenir, **son projeler ve çözümler** kolay erişim için liste:

![Visual Studio'da en son öğeyi aç](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözüm Gezgini'nde dosya iç içe yerleştime özelleştirme](file-nesting-solution-explorer.md)
- [Visual Studio performansını iyileştirme](optimize-visual-studio-performance.md)