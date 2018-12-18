---
title: 'CA2003: lifleri iş parçacığı olarak yok | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3d72e052decc5a26dd134aafcaac8aba6af699f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49810924"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Lifleri iş parçacığı olarak görmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Kategori|Microsoft.Reliability|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Yönetilen iş parçacığı bir Win32 iş parçacığı kabul edilir.

## <a name="rule-description"></a>Kural Tanımı
 Yönetilen iş parçacığı bir Win32 iş parçacığı olan varsaymayın. Bu, bir fiber olur. Ortak dil çalışma zamanı (CLR) yönetilen iş parçacıkları, SQL tarafından sahip olunan gerçek iş parçacıkları bağlamında iyileştirmesini olarak çalıştırılır. Bu iş parçacıkları SQL Server işlemde uygulama etki alanları ve hatta veritabanları arasında paylaşılabilir. Kullanılarak yönetilen iş parçacığı yerel depolama çalışır, ancak değil yönetilmeyen iş parçacığı yerel depolama kullanan veya kodunuzu geçerli işletim sistemi iş parçacığı üzerinde yeniden çalışacağını varsayalım. İş parçacığı yerel ayarı gibi ayarları değiştirmeyin. Kilit girer iş parçacığı kilit çıkmalı gerektirdiğinden CreateCriticalSection veya P/Invoke aracılığıyla CreateMutex çağırmayın. İyileştirmesini kullandığınızda bu durum olmayacağı için Win32 kritik bölümler ve mutex'leri SQL'de gereksiz olacaktır. Bu gibi durumlarda, durumun en güvenli bir şekilde bir yönetilen System.Thread nesnesinde kullanabilirsiniz. Bu, yönetilen iş parçacığı yerel depolama ve iş parçacığının geçerli kullanıcı arabirimi (UI) kültürü içerir. Ancak, model nedeniyle programlama için SQL kullanırken bir iş parçacığının geçerli kültürü değiştirmek mümkün olmayacaktır; Bu, yeni bir izin zorlanır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İş parçacıkları kullanımınızı inceleyin ve kodunuzu buna göre değişir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural göndermeme değil.



