---
title: Otomatik özelliği askıya alma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c8aee8f4ef46d3621bf569b260d943180abd7ad5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178184"
---
# <a name="automatic-feature-suspension"></a>Otomatik özelliği askıya alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
200 MB veya daha az, kullanılabilir sistem belleğini denk gelirse, Visual Studio Kod Düzenleyicisi'nde aşağıdaki iletiyi görüntüler.

 ![Uyarı metni tam çözüm analizini askıya](../code-quality/media/fsa-alert.png "FSA_Alert")

 Otomatik olarak Visual Studio bir yetersiz bellek koşulunu algıladığında, tutarlı kalmasını yardımcı olmak için bazı gelişmiş özellikleri askıya alır. Bu gelişmiş özellik askıya alma uyarısı görünür, Visual Studio'nun önceki gibi çalışmaya devam eder, ancak performansını biraz daha düşük olacağını.

 Bir düşük bellek koşulunda aşağıdakiler gerçekleşir:

-   Visual C# ve Visual Basic için tam çözüm analizini devre dışı bırakıldı.

-   [Çöp toplama](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) Visual C# ve Visual Basic için düşük gecikmeli modu devre dışı bırakıldı.

-   Visual Studio önbellekler temizlenir.

## <a name="improve-visual-studio-performance"></a>Visual Studio performansını
 İpuçları ve püf noktaları ile büyük çözümlerin veya düşük bellek koşullarını ilgilenirken Visual Studio performansını geliştirmeye yönelik bkz [büyük çözümler için başarım düşünceleri](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Tam çözüm analizini askıya alındı
 Varsayılan olarak, tam çözüm analizini Visual Basic için etkinleştirilir ve Visual C# için devre dışı. Ancak, bir düşük bellek koşulunda tam çözüm analizini otomatik olarak hem Visual Basic ve Visual C# için Seçenekler iletişim kutusu ayarlarına bakılmaksızın devre dışıdır. Ancak, tam çözüm analizini seçerek yeniden etkinleştirebilirsiniz **yeniden etkinleştirmeniz** düğmesi olduğunda, seçerek göründüğü çubuğu bilgileri **tam çözüm analizini etkinleştirme** onay kutusundan veya Seçenekler iletişim kutusunda Visual Studio yeniden başlatılıyor. Seçenekler iletişim kutusu, her zaman geçerli tam çözüm analizi ayarları gösterir. Daha fazla bilgi için [nasıl yapılır: etkinleştirme ve devre dışı tam çözüm analizini](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC devre dışı gecikme süresi düşük
 GC düşük gecikme süreli modunda yeniden etkinleştirmek için Visual Studio'yu yeniden başlatın.  Herhangi bir GC işlemi yazdıklarınızı engellemediğinden emin olmak için yazdığınız zaman varsayılan olarak, Visual Studio GC düşük gecikme süreli modunu etkinleştirir. Ancak, bir düşük bellek durumu otomatik askıya alma uyarısı görüntülemek Visual Studio neden olursa, GC düşük gecikme süreli modu bu oturum için devre dışı bırakıldı. Visual Studio'yu yeniden başlatmayı varsayılan GC davranışı yeniden etkinleştirilir. Daha fazla bilgi için bkz. <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio önbellekler temizlendi

Tüm Visual Studio önbellekleri hemen boşaltılması, ancak geçerli geliştirme oturumunuzu devam ya da Visual Studio'yu yeniden derlenmeye başlar. Temizlenen önbellekleri önbellekler için aşağıdaki özellikleri içerir.

-   Tüm başvuruları Bul

-   Gidin

-   Using ekleme

Ayrıca, iç Visual Studio işlemleri için kullanılan önbellekler de temizlenir.

> [!NOTE]
> Çözüm başına temelinde, bir oturum başına temelinde otomatik özelliği askıya alma uyarısı yalnızca bir kez gerçekleşir. Bu, Visual Basic, Visual C# (veya tersi) geçin ve başka bir düşük bellekli bir duruma çalıştırın, başka bir otomatik özelliği askıya alma uyarısı büyük olasılıkla edinebileceğiniz anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Tam Çözüm Analizini Etkinleştirme ve Devre Dışı Bırakma](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Atık Toplamanın Temelleri](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Büyük çözümler için performans konuları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)