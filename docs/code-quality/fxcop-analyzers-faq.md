---
title: FxCop Kod Analizi ve FxCop Çözümleyicileri
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136384"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop ve FxCop hakkında sık sorulan sorular çözümleyiciler

Eski FxCop FxCop arasındaki farkları anlamak biraz kafanızı karıştırabilir çözümleyici. Bu makalede sahip olabileceğiniz soruların adres amaçlar.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Eski FxCop ve FxCop arasındaki fark nedir Çözümleyicileri?

Eski FxCop derleme sonrası analiz derlenmiş bir derleme üzerinde çalışır. Adlı ayrı bir yürütülebilir olarak çalıştığı **FxCopCmd.exe**. FxCopCmd.exe derlenmiş bütünleştirilmiş kodunu yükler, Kod Analizi çalıştırır ve sonuçları daha sonra raporlar (veya *tanılama*).

FxCop Çözümleyicileri .NET derleyici Platformu ("Roslyn") temel alır. [Bir NuGet paketi olarak yükleneceği](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) proje veya çözüm tarafından başvuruluyor. Derleyicinin yürütme sırasında dayalı analizi FxCop Çözümleyicileri kaynak kodu çalıştırın. FxCop Çözümleyicileri barındırılır derleyici işlemin içinde ya da **csc.exe** veya **vbc.exe**, ve proje derlenirken analizini Çalıştır. Çözümleyici sonuçları birlikte derleyici sonuçları raporlanır.

> [!NOTE]
> Ayrıca [FxCop Çözümleyicileri Visual Studio uzantısı yükleme](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). Bu durumda, Çözümleyicileri, Kod Düzenleyicisi'nde yazın, ancak yapı zamanında yürütme yok olarak yürütün. FxCop Çözümleyicileri sürekli tümleştirme (CI) bir parçası olarak çalıştırmak istiyorsanız, bunları bir NuGet paketi olarak bunun yerine yükleyin.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Kod çözümlemeyi Çalıştır komutu FxCop Çözümleyicileri çalışıyor mu?

Hayır. Seçtiğinizde, **Çözümle** > **kod çözümlemeyi Çalıştır** Visual Studio 2017'de statik kod analizi veya eski FxCop yürütür. **Kod analizini Çalıştır** Roslyn tabanlı FxCop Çözümleyicileri dahil olmak üzere, Roslyn tabanlı Çözümleyicileri üzerinde hiçbir etkisi olmaz.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild proje özelliği Çözümleyicileri çalışıyor mu?

Hayır. **RunCodeAnalysis** özelliği proje dosyasında (örneğin, *.csproj*) yalnızca eski FxCop yürütmek için kullanılır. Çağıran bir derleme sonrası msbuild görevi çalıştığı **FxCopCmd.exe**. Bu seçmeye eşdeğerdir **Çözümle** > **kod çözümlemeyi Çalıştır** Visual Studio'da.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>FxCop Çözümleyicileri sonra nasıl çalıştırırım?

FxCop Çözümleyicileri, ilk olarak çalışmasını [NuGet paketini yüklemek](install-fxcop-analyzers.md) bunlar için. Ardından Proje veya çözüm Visual Studio veya msbuild'ı kullanarak oluşturun. FxCop Çözümleyicileri oluşturma hataları ve Uyarıları görünür **hata listesi** veya komut penceresinden.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET derleyici platformu Çözümleyicileri genel bakış](roslyn-analyzers-overview.md)
- [Çözümleyicileriyle çalışmaya başlama](fxcop-analyzers.yml)
- [FxCop Çözümleyicileri yükleyin](install-fxcop-analyzers.md)
