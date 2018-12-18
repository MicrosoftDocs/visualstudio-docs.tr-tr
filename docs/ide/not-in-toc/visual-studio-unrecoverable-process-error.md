---
title: Bir işlem kurtarılamaz bir hatayla karşılaştı
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b6d69aa899ffea95c8da7c3513c6f7b0fa6002ee
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895164"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio kurtarılamaz işlemi hatası

Visual Studio 2017 birçok işlem dışı işlem live unit testing gibi gerekli arka plan görevleri çalıştırmak, kod Çözümleyicileri ve daha fazlası için kullanır. Bu işlemler, çıkış, kaynak yoğunluklu işler çalışırken daha hızlı yanıt Visual Studio etkinleştirme gibi Visual Studio performans avantajlarını vermek için işlem dışı çalıştırılır. Visual Studio 32 bitlik bir işlem olduğundan, ayrıca, işlemler,-işlem dışı çalışan bellek kullanımı yoğun iş çalışacağı daha büyük bir bellek alanı sağlar.

Varsa *ServiceHub.RoslynCodeAnalysisService.exe* veya *ServiceHub.RoslynCodeAnalysisService32.exe* işlem sona erer herhangi bir nedenle açılır bilgi çubuğu ile aşağıdaki ileti görünür:

**"Ne yazık ki Visual Studio tarafından kullanılan işlem kurtarılamaz bir hatayla karşılaştı. İş ve ardından kapatarak ve Visual Studio'yu yeniden başlatmayı kaydetme öneririz."**

Bu iletiyi görürseniz, çalışmanızı kaydedin ve ardından kapatın ve Visual Studio'yu yeniden başlatın.

## <a name="list-of-processes"></a>İşlemlerin listesi

Visual Studio tarafından kullanılan işlem dışı işlemlerin bir listesi verilmiştir. Bu listenin belirli iş akışları veya senaryo başlatma işlemleri tamamlanmıyorsa olduğunu ve bu nedenle çoğu durumda bunlar tümü aynı anda çalıştırmıyor.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Bu işlemlerden biri sona ererse beklenmedik bir şekilde, Visual Studio içinde bazı işlevler çalışmaz. Bazı işlemler için işlevsellik kaybı Önemsiz olabilir. Diğer kullanıcıların, Visual Studio kararlılığını etkilenir ve bir hata iletisi görüntülenir.