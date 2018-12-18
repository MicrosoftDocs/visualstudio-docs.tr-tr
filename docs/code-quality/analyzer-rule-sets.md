---
title: Çözümleyicisi için kural kümeleri
ms.date: 07/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7df084a81de2afc522fc3b82141cf8c5c59205ca
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204556"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Roslyn çözümleyicilerini için kural kümeleri

Önceden tanımlanmış kural kümeleri bazı NuGet Çözümleyicisi paketleri dahil edilir. Örneğin, eklenen kural kümesi [Microsoft.CodeAnalysis.FxCopAnalyzers NuGet Çözümleyicisi paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) etkinleştirin veya adlandırma, güvenlik gibi kategorilerine göre kuralları devre dışı bırak (sürüm 2.6.2 başlayarak) veya performans. Kural kümeleri kullanma, kuralın belirli bir kategoriye ait kural ihlalleri hızlıca görmek kolaylaştırır.

Eski "FxCop" statik kod analizi için Roslyn Çözümleyicileri geçiriyorsanız, bu kural kümeleri, daha önce kullandığınız aynı kuralı yapılandırmaları kullanmaya devam etmek etkinleştirin.

## <a name="use-analyzer-rule-sets"></a>Çözümleyicisi için kural kümeleri kullanma

Çalıştırdıktan sonra [NuGet Çözümleyicisi paket yükleme](install-roslyn-analyzers.md), önceden tanımlanmış kural kümesi bulun, *rulesets* örneğin dizinine *% USERPROFILE %\\.nuget\packages\ Microsoft.codequality.analyzers\<sürüm > \rulesets*. Buradan, sürükleyin ve bırakın veya kopyalayıp yapıştırabilirsiniz, bir veya daha fazla Visual Studio projenize rulesets **Çözüm Gezgini**.

Analizi için etkin kural kümesi bir kural oluşturmak için projeye sağ **Çözüm Gezgini** ve **özellikleri**. Proje özellik sayfaları'nda seçin **Kod Analizi** sekmesi. Altında **bu kural kümesini Çalıştır**seçin **Gözat**ve ardından proje dizinine kopyalanır istenen kural kümesi seçin. Artık yalnızca seçili kural kümesinde etkin bu kuralları için kural ihlalleri görürsünüz.

Ayrıca [önceden tanımlanmış kural kümesi özelleştirme](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set) tercihinize. Örneğin, böylece hatalar veya uyarılar olarak ihlalleri görünür bir veya daha fazla kural önem derecesi değiştirebilirsiniz **hata listesi**.

## <a name="available-rule-sets"></a>Kullanılabilir kural kümeleri

Paketteki tüm kuralları etkiler üç rulesets önceden tanımlanmış Çözümleyicisi kural kümelerini Ekle&mdash;tümünü sağlayan, Tümünü devre dışı bırakan bir, diğeri, önem derecesi ve etkinleştirme her kuralın varsayılan ayarlarını kabul eder:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Ayrıca, performans veya güvenlik gibi paket kurallarında her kategorisi için iki kural kümesi vardır. Bir kural kümesi kategorisi için tüm kuralları etkinleştirir ve varsayılan önem derecesi ve etkinleştirme ayarları kategorideki her kural için bir kural kümesi geliştirir.

 [Microsoft.CodeAnalysis.FxCopAnalyzers NuGet Çözümleyicisi paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) için eski "FxCop" statik kod analizi kural kümesi eşleştirmek için gereken şu kategorileri için kural kümeleri içerir:

- tasarlama
- belgeler
- bakım
- adlandırma
- performans
- güvenilirlik
- güvenlik
- kullanım

## <a name="see-also"></a>Ayrıca bkz.

- [.NET derleyici platformu Çözümleyicileri genel bakış](roslyn-analyzers-overview.md)
- [.NET derleyici platformu çözümleyicilerini yükleme](install-roslyn-analyzers.md)
- [Yapılandırma ve Roslyn çözümleyicisi kuralları kullanma](use-roslyn-analyzers.md)
- [Kural Kod Analizi kurallarını gruplandırmak için kümeleri kullanma](using-rule-sets-to-group-code-analysis-rules.md)