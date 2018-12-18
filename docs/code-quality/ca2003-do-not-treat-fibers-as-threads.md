---
title: 'CA2003: Lifleri iş parçacığı olarak görmeyin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3322b968266ad6fdfe1be2e5bdaac73aad32b9c7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551918"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Lifleri iş parçacığı olarak görmeyin

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Kategori|Microsoft.Reliability|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Yönetilen iş parçacığı bir Win32 iş parçacığı kabul edilir.

## <a name="rule-description"></a>Kural açıklaması

Yönetilen iş parçacığı bir Win32 iş parçacığı olan varsaymayın; Bu, bir fiber olur. Ortak dil çalışma zamanı (CLR) yönetilen iş parçacıklarını iyileştirmesini SQL tarafından sahip olunan gerçek iş parçacıkları bağlamında çalışır. Bu iş parçacıkları SQL Server işlemde uygulama etki alanları ve hatta veritabanları arasında paylaşılabilir. Kullanılarak yönetilen iş parçacığı yerel depolama çalışır, ancak değil yönetilmeyen iş parçacığı yerel depolama kullanan veya kodunuzu geçerli işletim sistemi iş parçacığı üzerinde yeniden çalışacağını varsayalım. İş parçacığı yerel ayarı gibi ayarları değiştirmeyin. Kilit girer iş parçacığı kilit çıkmalı gerektirdiğinden CreateCriticalSection veya P/Invoke aracılığıyla CreateMutex çağırmayın. Win32 kritik bölümler mutex'leri iyileştirmesini kullandığınızda kilit girdiği iş parçacığının bir kilidi çıkmak değil çünkü gereksiz SQL. Güvenli bir şekilde çoğu durumu üzerinde bir yönetilen kullanabilirsiniz <xref:System.Threading.Thread> yönetilen iş parçacığı yerel depolama ve iş parçacığının geçerli kullanıcı arabirimi (UI) kültürü dahil olmak üzere bir nesne. Ancak, model nedeniyle programlama için SQL kullanırken bir iş parçacığının geçerli kültürü değiştirmek mümkün olmayacaktır. Bu sınırlama ile yeni bir izin zorlanır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

İş parçacıkları kullanımınızı inceleyin ve kodunuzu buna göre değişir.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Bu kural bastırmayın.