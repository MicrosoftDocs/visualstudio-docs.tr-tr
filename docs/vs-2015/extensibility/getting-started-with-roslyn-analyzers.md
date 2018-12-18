---
title: Roslyn Çözümleyicileriyle çalışmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 320f35d2a80f120d14f01b471449cd308ab30c8e
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348288"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Roslyn Çözümleyicileriyle Çalışmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da canlı, proje temelli kod çözümleyicileriyle API yazarlar, etki alanına özgü kod analizi NuGet paketlerinin bir parçası olarak gönderebilirsiniz.  Bu Çözümleyicileri .NET derleyici Platformu (eskiden "Roslyn") tarafından desteklenen çünkü (daha fazla sorunları bulmak için kodunuzu derlemek için bekleniyor) satırı bitirdikten sonra bile önce yazdığınız sırada bunlar kodunuzdaki uyarılar oluşturabilir.  Çözümleyicileri de temiz kodunuzu oluşturan hemen izin vermek için Visual Studio ampul istemi üzerinden bir otomatik kod düzeltme ortaya çıkabilir

## <a name="getting-started"></a>Başlarken
[Roslyn Canlı kod Çözümleyicileri giriş ve gözden geçirme](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Kod ekleme, izlenecek giderir: Kullanıcılar düzeltmeleri Çözümleyicisi sorunlarda sağlayabilir.](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Giriş ve gerçek dünya Çözümleyicisi konuşma ilişkin kılavuz](http://channel9.msdn.com/events/Build/2015/3-725)

[Gerçek dünya Roslyn Çözümleyicinizi](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) olarak izleyebileceğiniz bir [konuşun](http://channel9.msdn.com/events/Build/2015/3-725)

[Üç tür Çözümleyicileri gruplandırılmış github'da çeşitli örnekleri](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Giriş ve birkaç Çözümleyicileri turu](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Diğer Kaynaklar
[GitHub OSS sitesinde daha fazla belgeleri](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Roslyn çözümleyicilerini github'da ile uygulanan FxCop kuralı](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)

