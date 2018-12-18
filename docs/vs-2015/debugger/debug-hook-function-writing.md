---
title: Hata ayıklama kanca işlevi yazma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47cd3d42639785290f26d7acbbad15cd948b4f51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735520"
---
# <a name="debug-hook-function-writing"></a>Hata Ayıklama Kanca İşlevi Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, bir dizi önceden tanımlanmış bazı noktalar normal işleme hata ayıklayıcı'nın içinde kod eklemeye izin veren yazabileceğiniz özel hata ayıklama kanca işlevleri açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İstemci Blok Kanca İşlevleri](../debugger/client-block-hook-functions.md)  
 Yönergeler ve bir prototip doğrulamak veya _clıent_block bloklarında depolanan verilerin içeriklerini rapor işlevleri yazmak için sağlar.  
  
 [Atama Kanca İşlevleri](../debugger/allocation-hook-functions.md)  
 Bir ayırma kanca işlevini tanımlayan, farklı kullanımları, kısıtlamalar, noktaları inceler ve bir prototip sağlar.  
  
 [Atama kancaları ve CRT bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Kısıtlama açıkça yoksayılıyor, atama kanca işlevleri açıklar `_CRT_BLOCK` iç bellek C çalışma zamanı kitaplık işlevleri çağrıları yaptıkları engeller. Bu konuda, atama kanca değil yoksayarsanız, ayrıca sonuçları listeler `_CRT_BLOCK` bloklarla (örnekler) ve varsayılan ayırma değiştirme kanca işlevini, **CrtDefaultAllocHook**.  
  
 [Kanca İşlevlerini Raporlama](../debugger/report-hook-functions.md)  
 Anlatılmaktadır `_CrtSetReportHook`, ayırmaları belirli türlerde odaklanmak için filtre uygulamak için kullanabileceğiniz raporlar. Bu konu, bir prototip de sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)  
 CRT hata ayıklama kitaplığı, raporlama için makroları kullanma dahil olmak üzere C çalışma zamanı kitaplığı hata ayıklama tekniklerine bağlantılarını farkları arasında `malloc` ve `_malloc_dbg`, hata ayıklama kanca işlevlerini ve CRT hata ayıklama yığın yazma.



