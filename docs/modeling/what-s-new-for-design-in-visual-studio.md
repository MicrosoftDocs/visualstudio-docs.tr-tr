---
title: Tasarım için yenilikler nelerdir?
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebe304cafa5e8ed4eae287750aeb8e2db02fbc31
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062289"
---
# <a name="whats-new-for-design-in-visual-studio"></a>Visual Studio tasarımındaki yenilikler

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulama

İstenmeyen bağımlılık kaldırma, teknik borcun yönetimi, önemli bir parçasıdır. Canlı doğrulama bağımlılıklarının içerdiği artık sorunları hakkında kesin bilgi sağlama ve hata listesi ve düzenleyici yeni özelliklerinden tam olarak yararlanıyor.

![Eylem Canlı bağımlılık doğrulama](media/dep-validation-whatsnew-01.png)

Yazma deneyiminde daha bulunabilir ve daha erişilebilir değiştirme "Katman diyagramından" terminoloji "Bağımlılık diyagrama" bağımlılık doğrulaması yapmak için değişti.

**Mimarisi** menüsü artık, doğrudan bir bağımlılık diyagramı oluşturmak için bir komut içerir:

![Canlı bağımlılık öğede mimari menüsü](media/dep-validation-whatsnew-02.png)

… ve daha anlamlı olacak şekilde bir katmana bağımlılık diyagramı ve onların açıklamalarını özellik adları değiştirildi:

![Canlı bağımlılık özelliği adları güncelleştirildi](media/dep-validation-whatsnew-03.png)

Değişikliklerinizi hemen geçerli çözümün kodunu analiz sonuçları etkisini diyagramda her kaydettiğinizde göreceksiniz. Artık "Bağımlılıkları doğrulamak" komutunun tamamlanmasını beklemek zorunda değilsiniz.

Daha fazla ayrıntı için [bu blog gönderisini](https://blogs.msdn.microsoft.com/devops/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>UML tasarımcılarına kaldırıldı

UML tasarımcılarına Visual Studio Enterprise'nın bu sürümünden kaldırılmıştır.

* UML diyagramları artık XML dosyaları olarak sunulur
* UML Model Gezgini artık yok
* Modelleme projesi başvuruları artık bağımlılık doğrulaması için kullanılır
* Çözüm Gezgini "Katman başvuruları" düğümünde artık görüntülenmez
* Bağımlılık (katman) diyagram üzerinde "Doğrula" derleme eylemi artık kullanılmamaktadır - derleme görevi kaldırıldı
* Proje yapısını sürümleri arasında gidiş dönüşü korunur
* Yine de açın, oluşturabilir, düzenleyebilir ve bir bağımlılık (katman) diyagramı XML olarak kaydetme
* TFS iş öğeleri için bir bağımlılık (katman) diyagramı tasarım yüzeyinde erişilebilir değil
* Geri gelen DSL veya katmanına bağlama artık desteklenmiyor
* UML Genişletilebilirlik modelleme SDK'sı, artık desteklenmiyor

Ancak, .NET ve C++ kodu mimarisini görselleştirmek aracılığıyla kullanılabilir desteğinin [kod haritaları](map-dependencies-across-your-solutions.md)ve bağımlılık doğrulaması yukarıda açıklanan önemli geliştirmeler.

UML tasarımcılarına önemli bir kullanıcı varsa, UML ihtiyaçlarınız için alternatif bir aracı üzerinde karar sırada Visual Studio 2015 veya önceki sürümlerini kullanmaya devam edebilirsiniz.

Daha fazla ayrıntı için [bu blog gönderisini](https://blogs.msdn.microsoft.com/devops/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Mimari ve Modelleme Araçları sürüm desteği

Visual Studio 2017 birçok sürümlerinde kullanılabilir. Bunların tümü, mimari ve Modelleme Araçları için destek sağlar. Aşağıdaki tabloda her bir aracı kullanılabilirliğini gösterir.

|**Özelliği**|**Enterprise edition**|**Professional sürümü**|**Community sürümü**|
|-|-|-|-|
|**Kod haritaları**|Evet|Yalnızca okuma kod haritalarını destekler, kod filtreleme, yeni genel düğüm ekleme ve seçimden yeni yönlendirilmiş grafik oluşturma eşler.|-|
|**Bağımlılık diyagramları**|Evet|Yalnızca bağımlılık diyagramlarını okuma destekler.|Yalnızca bağımlılık diyagramlarını okuma destekler.|
|**Yönlendirilmiş grafikleri** (DGML diyagramları)|Evet|Evet|Evet|
|**Kod kopyası**|Evet|-|-|