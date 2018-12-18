---
title: Otomatik özelliği askıya alma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: b97a58a7f5ba3808c658b838de942e94c12b9b79
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049100"
---
# <a name="automatic-feature-suspension"></a>Otomatik özelliği askıya alma

200 MB veya daha az, kullanılabilir sistem belleğini denk gelirse, Visual Studio Kod Düzenleyicisi'nde aşağıdaki iletiyi görüntüler:

![Tam çözüm analizini askıya uyarı metni](../code-quality/media/fsa_alert.png)

Otomatik olarak Visual Studio bir yetersiz bellek koşulunu algıladığında, tutarlı kalmasını yardımcı olmak için bazı gelişmiş özellikleri askıya alır. Visual Studio'nun önceki gibi çalışmaya devam eder, ancak bunun performansı düşer.

Bir düşük bellek durumu aşağıdaki eylemler gerçekleşir:

- Visual C# ve Visual Basic için tam çözüm analizini devre dışı bırakıldı.

- [Çöp toplama](/dotnet/standard/garbage-collection/index) görsel için düşük gecikmeli modu (GC) C# ve Visual Basic devre dışı bırakıldı.

- Visual Studio önbellekler temizlenir.

## <a name="improve-visual-studio-performance"></a>Visual Studio performansını

İpuçları ve püf noktaları ile büyük çözümlerin veya düşük bellek koşullarını ilgilenirken Visual Studio performansını geliştirmeye yönelik bkz [büyük çözümler için başarım düşünceleri](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Tam çözüm analizini askıya alındı

Varsayılan olarak, tam çözüm analizini Visual Basic için etkinleştirilir ve Visual C# için devre dışı. Ancak, bir düşük bellek koşulunda tam çözüm analizini otomatik olarak hem Visual Basic ve Visual C# için Seçenekler iletişim kutusu ayarlarına bakılmaksızın devre dışıdır. Ancak, tam çözüm analizini seçerek yeniden etkinleştirebilirsiniz **yeniden etkinleştirmeniz** düğmesi olduğunda, seçerek göründüğü çubuğu bilgileri **tam çözüm analizini etkinleştirme** onay kutusundan veya Seçenekler iletişim kutusunda Visual Studio yeniden başlatılıyor. Seçenekler iletişim kutusu, her zaman geçerli tam çözüm analizi ayarları gösterir. Daha fazla bilgi için [nasıl yapılır: etkinleştirme ve devre dışı tam çözüm analizini](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC devre dışı gecikme süresi düşük

GC düşük gecikme süreli modunda yeniden etkinleştirmek için Visual Studio'yu yeniden başlatın. Herhangi bir GC işlemi yazdıklarınızı engellemediğinden emin olmak için yazdığınız zaman varsayılan olarak, Visual Studio GC düşük gecikme süreli modunu etkinleştirir. Ancak, bir düşük bellek durumu otomatik askıya alma uyarısı görüntülemek Visual Studio neden olursa, GC düşük gecikme süreli modu bu oturum için devre dışı bırakıldı. Visual Studio'yu yeniden başlatmayı varsayılan GC davranışı yeniden etkinleştirir. Daha fazla bilgi için bkz. <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio önbellekler temizlendi

Tüm Visual Studio önbellekleri, hemen geçerli geliştirme oturumunuzu devam veya Visual Studio'yu yeniden başlatın, boşaltılıp ancak derlenmeye başlar. Temizlenen önbellekleri önbellekler için aşağıdaki özellikleri içerir:

- Tüm başvuruları Bul

- Gidin

- Using ekleme

Ayrıca, iç Visual Studio işlemleri için kullanılan önbellekler de temizlenir.

> [!NOTE]
> Çözüm başına temelinde, bir oturum başına temelinde otomatik özelliği askıya alma uyarısı yalnızca bir kez gerçekleşir. Bu, Visual Basic, Visual C# (veya tersi) geçin ve başka bir düşük bellekli bir duruma çalıştırın, başka bir otomatik özelliği askıya alma uyarısı büyük olasılıkla edinebileceğiniz anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Tam Çözüm Analizini Etkinleştirme ve Devre Dışı Bırakma](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Atık Toplamanın Temelleri](/dotnet/standard/garbage-collection/fundamentals)
- [Büyük çözümler için performans konuları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)