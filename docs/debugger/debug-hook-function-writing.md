---
title: Hata ayıklama kanca işlevi yazma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 365196a01ba9e62ef0b26eb3a99278d4d77a4dd4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457348"
---
# <a name="debug-hook-function-writing"></a>Hata Ayıklama Kanca İşlevi Yazma
Bu bölümde, hata ayıklayıcı'nın normal işlem içindeki önceden tanımlanmış bazı noktaları kodunuzu eklemeye izin veren, yazabilirsiniz özel hata ayıklama kanca işlevleri açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İstemci blok kanca işlevleri](../debugger/client-block-hook-functions.md)  
 Kılavuz ve prototip doğrulamak veya _clıent_block bloklarında depolanan verileri içeriğini raporun işlevler yazma için sağlar.  
  
 [Atama kanca işlevleri](../debugger/allocation-hook-functions.md)  
 Bir ayırma kanca işlevini tanımlar, farklı kullanımları, kısıtlamalar, çıkış noktaları inceler ve prototip sağlar.  
  
 [Ayırma kancaları ve CRT bellek ayırma](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Kısıtlama açıkça yoksayılıyor, atama kanca işlevleri açıklanır `_CRT_BLOCK` iç bellek C çalışma zamanı kitaplığı işlevleri yapılan her çağrı yaparsanız engeller. Atama kanca değil yoksayarsanız Bu konu ayrıca sonuçları listeler `_CRT_BLOCK` bloklarla (örnekler) ve varsayılan yerleşimi değiştirmek nasıl kanca işlevini **CrtDefaultAllocHook**.  
  
 [Kanca işlevlerini raporlama](../debugger/report-hook-functions.md)  
 Ele `_CrtSetReportHook`, filtre uygulamak için kullanabileceğiniz raporları ayırmaları belirli türlerdeki odaklanmak için. Bu konu aynı zamanda bir prototip sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md)  
 CRT hata ayıklama kitaplığı, raporlama, makroları kullanma dahil olmak üzere C çalışma zamanı kitaplığı için ayıklama teknikleri bağlantılar arasındaki farklılıklar `malloc` ve `_malloc_dbg`, hata ayıklama kanca işlevleri ve CRT hata ayıklama yığınını yazma.