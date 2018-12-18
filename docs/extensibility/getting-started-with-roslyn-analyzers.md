---
title: Roslyn Çözümleyicileriyle çalışmaya başlama | Microsoft Docs
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6077fb8a9f0db360389953ef6a7ed25c6d242247
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821298"
---
# <a name="get-started-with-roslyn-analyzers"></a>Roslyn çözümleyicileriyle çalışmaya başlama

Visual Studio'da canlı, proje temelli kod çözümleyicileriyle API yazarlar, etki alanına özgü kod analizi NuGet paketlerinin bir parçası olarak gönderebilirsiniz. Bu Çözümleyicileri .NET derleyici Platformu (eskiden "Roslyn") tarafından desteklenen çünkü (daha fazla sorunları bulmak için kodunuzu derlemek için bekleniyor) satırı bitirdikten sonra bile önce yazdığınız sırada bunlar kodunuzdaki uyarılar oluşturabilir. Çözümleyiciler, ayrıca bir otomatik kod düzeltme temiz kodunuzu oluşturan hemen izin vermek için Visual Studio ampul istemi üzerinden ortaya çıkabilir.

## <a name="get-started"></a>Kullanmaya başlayın

[Roslyn Canlı kod Çözümleyicileri giriş ve gözden geçirme](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Ekleme kodu düzeltir izlenecek yol: Çözümleyicisi sorunları için kullanıcıların düzeltmeleri sağlayabilir](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Giriş ve gerçek dünya Çözümleyicisi Kılavuzu](https://channel9.msdn.com/events/Build/2015/3-725)

[Gerçek dünya Roslyn çözümleyicinizi](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) olarak izleyebileceğiniz bir [konuşun](https://channel9.msdn.com/events/Build/2015/3-725)

[Üç tür Çözümleyicileri gruplandırılmış github'da çeşitli örnekleri](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Giriş ve birkaç Çözümleyicileri turu](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>Ayrıca bkz.

- [Roslyn Çözümleyicileri genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Öğretici: ilk Çözümleyicisi ve kod düzeltmenizi yazın](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)
- [.NET derleyici platformu Paket sürümü başvurusu](roslyn-version-support.md)
- [GitHub OSS sitesinde daha fazla belgeleri](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Roslyn çözümleyicilerini github'da ile uygulanan FxCop kuralı](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)