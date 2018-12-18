---
title: Kod eşleme çözümleyicilerini kullanarak olası sorunları bulma
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: afc2915a5d1bfb6cf361a4b84a0235db296bac67
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856762"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Kod haritası çözümleyicilerini kullanarak olası sorunları bulma

Fazla karmaşık olabilecek kod tanımlamanıza yardımcı olması için kod haritalarını Çözümleyicileri çalıştırın veya geliştirme ihtiyaç duyabilirsiniz. Örneğin, bu Çözümleyicileri kullanabilirsiniz:

|**Sahip kodu bulmak için**|**Bu alanları görmek için inceleyin olmadığını**|
|-|-|
|Döngüler veya döngüsel bağımlılıklar|Bunları basitleştirin ve bu döngüleri kesme olup olmadığını göz önünde bulundurun.|
|Çok fazla bağımlılıkları|Çok fazla işlevleri gerçekleştirdiği veya bu alanları değiştirmenin etkilerini belirlemek için. İyi biçimlendirilmiş bir kod haritası, en az bir bağımlılık sayısı gösterilir. Kod korumak, Değiştir, test edin ve yeniden, olup olmadığını ve böylece daha net bir şekilde tanımlanan bu alanları yeniden düzenleyebilirsiniz ya da benzer işlevler gerçekleştiren kod birleştirmek için göz önünde bulundurun daha kolay hale getirmek için.|
|Hiçbir bağımlılık|Gerekli veya bu kodu kaldırmanız gerekir.|

## <a name="analyze-code-maps"></a>Kod haritaları analiz edin

Harita araç çubuğunda **Düzen** > **Çözümleyicileri**ve sonra çalıştırmak istediğiniz Çözümleyicisi:

|**Çözümleyici**|**Düğümleri tanımlamak için**|
|-|-|
|**Döngüsel başvuru Çözümleyicisi**|Döngüsel bağımlılıklar birbirleri üzerinde sahip. **Not:** bulunan döngüsel bağımlılıklar **genel türler** grubu grubu genişlettiğinizde haritada gösterilmez.|
|**Merkez çözümleyicisini Bul**|Yüksek oranda bağlı düğümlerin üst %25 olan<br /><br /> **Harita üzerinde tüm düğümleri gizlemek için**<br /><br /> -Map için kısayol menüsünü açın, **Gelişmiş**, **seçin**, **gizlemek için seçilmeyen**.<br />     Seçili olmayan düğümleri eşlemesi gizler ve hub'ları olarak yeni düğümler Çözümleyicisi belirler.|
|**Başvurulmamış düğümler Çözümleyicisi**|Diğer düğümlerden başvuruları yok. **Dikkat:** varsayarak kod kullanılmayan her durumda önce doğrulayın. XAML ve çalışma zamanı iç bağımlılıkları gibi belirli bağımlılıkları kod statik olarak bulunamıyor.|

Kod Haritası çözümleyicilerini uygulamadan sonra çalışmaya devam eder. Harita değiştirirseniz, uygulanan çözümleyiciler güncelleştirilmiş haritanın otomatik olarak işleyecektir. Harita araç çubuğunda bir çözümleyici durmaya tercih **Düzen** > **Çözümleyicileri**. Seçili Çözümleyicisi devre dışı bırakın.

> [!TIP]
> Çok büyük bir eşlemesi varsa, çalışan bir çözümleyiciyi bir yetersiz bellek özel durumu neden olabilir. Bu meydana gelirse, kapsamını azaltın veya daha küçük bir tane oluşturmak için harita düzenleyin ve ardından Çözümleyicisi çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
