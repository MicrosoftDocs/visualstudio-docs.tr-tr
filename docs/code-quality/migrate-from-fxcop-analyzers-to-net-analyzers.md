---
title: FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme
ms.custom: SEO-VS-2020
description: FxCop çözümleyicileri ' nden .NET çözümleyicilerine nasıl geçiş yapılacağını öğrenin
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: d6f9c36b1b64abe648c3aa9014c633e4e4949b1a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798264"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme

.NET Compiler Platform ("Roslyn") Çözümleyicileri kaynak analizi, yönetilen kod için [eski analizler](code-analysis-for-managed-code-overview.md) yerini alır. Eski analiz (FxCop) kurallarının birçoğu kaynak Çözümleyicileri olarak zaten yeniden yazıldı.

Visual Studio 2019 16,8 ve .NET 5,0 öncesinde, bu çözümleyiciler `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)olarak gönderilir.

Visual Studio 2019 16,8 ve .NET 5,0 'den başlayarak, bu çözümleyiciler [.NET SDK 'ya dahildir](/dotnet/fundamentals/code-analysis/overview). .NET 5 + SDK ' ya geçmek istemiyorsanız veya bir NuGet paket tabanlı modeli tercih ediyorsanız, çözümleyiciler `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet paketinde](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)de mevcuttur. İsteğe bağlı sürüm güncelleştirmeleri için paket tabanlı bir model tercih edebilirsiniz.

> [!NOTE]
> Birinci taraf .NET Çözümleyicileri, hedef platform belirsiz ' dir. Diğer bir deyişle, projenizin belirli bir .NET platformunu hedeflemesi gerekmez. Çözümleyiciler, `net5.0` ve gibi önceki .NET sürümlerinin yanı sıra hedeflenen projeler için de çalışır `netcoreapp` `netstandard` `net472` .

## <a name="migration-steps"></a>Geçiş adımları

Sürümden itibaren `3.3.2` `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet paketi kullanım dışı bırakılmıştır. Projenizi veya çözümünüzü .NET çözümleyicilerine geçirmek için lütfen aşağıdaki adımları izleyin `Microsoft.CodeAnalysis.FxCopAnalyzers` :

1. `Microsoft.CodeAnalysis.FxCopAnalyzers`NuGet paketini kaldır

2. [.Net Çözümleyicileri etkinleştirebilir veya bunları yükler](install-net-analyzers.md). Projenizin hedef platformunu değiştirmeniz gerekmediğini unutmayın.

3. Ek kuralları etkinleştir: ile `Microsoft.CodeAnalysis.NetAnalyzers` karşılaştırıldığında çok daha fazla koruyucu `Microsoft.CodeAnalysis.FxCopAnalyzers` . Fxcopçözümleyiciler paketinin aksine, yalnızca [derleme uyarıları olarak varsayılan olarak etkinleştirilen](/dotnet/fundamentals/code-analysis/overview#enabled-rules)birkaç doğruluk kuralına sahiptir. [Analysismode](/dotnet/core/project-sdk/msbuild-props#analysismode) MSBuild özelliğini özelleştirerek [ek kurallara izin](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) verebilirsiniz. Örneğin, özelliğinin olarak ayarlanması, `AllEnabledByDefault` geçerli tüm CA kurallarının varsayılan olarak derleme uyarıları olarak etkinleştirecektir.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak kodu analizi ve eski analiz karşılaştırması](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [Eski analizden .NET çözümleyicilerine geçirme](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET çözümleyicilerini etkinleştirme veya yükleme](install-net-analyzers.md)
- [.NET çözümleyicileri hakkında SSS](net-analyzers-faq.yml)
- [.NET çözümleyicilerini yapılandırma](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
