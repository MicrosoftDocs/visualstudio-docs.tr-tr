---
title: CRT hata ayıklama tekniklerine | Microsoft Docs
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
- c.runtime.debugging
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6745a31dcb7c37d12551248473b072d440116501
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801036"
---
# <a name="crt-debugging-techniques"></a>CRT Hata Ayıklama Teknikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C çalışma zamanı kitaplığı kullanan bir programı hata ayıklaması yapıyorsanız, bu hata ayıklama teknikleri yararlı olabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CRT Hata Ayıklama Kitaplığı Kullanımı](../debugger/crt-debug-library-use.md)  
 C çalışma zamanı kitaplığı tarafından sağlanan hata ayıklama desteğini açıklar ve araçlara erişmek için yönergeler sağlar.  
  
 [Raporlama Makroları](../debugger/macros-for-reporting.md)  
 Hakkında bilgi sağlar **_RPTn** ve **_RPTFn** makroları (CRTDBG içinde tanımlanır. Kullanımını değiştirin H) `printf` hata ayıklama için deyimleri.  
  
 [Öbek Atama İşlevleri Hata Ayıklama Sürümleri](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Yığın ayırma işlevleri dahil olmak üzere, özel hata ayıklama sürümlerini açıklar: CRT çağrıları, açıkça çağırma avantajları nasıl eşlendiğini nasıl önleneceğini dönüştürme, istemci bloklar ayırmaları ayrı türlerini ve tanımlamayarak _ sonuçlarını izleme HATA AYIKLAMA.  
  
 [CRT Hata Ayıklama Öbeği Ayrıntıları](../debugger/crt-debug-heap-details.md)  
 Bellek yönetimi ve hata ayıklama yığın, blok türlerine bağlantılar kullanarak hata ayıklama öbek, öbek durumu raporlama işlevleri ve yığın ayırma isteklerini izleme hata ayıklama yığınında sağlar.  
  
 [Hata Ayıklama Kanca İşlevi Yazma](../debugger/debug-hook-function-writing.md)  
 İstemci engelleme listeleri bağlantılar, İşlevler, atama kanca işlevleri, atama kancaları ve CRT bellek ayırmaları ve kanca işlevlerini raporlama bağlayın.  
  
 [CRT Kitaplığını Kullanarak Bellek Sızıntılarını Bulma](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Algılama ve hata ayıklayıcı ve C çalışma zamanı kitaplığını kullanarak bellek sızıntılarını ayırma teknikleri kapsar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)  
 Bazı yaygın hata ayıklama sorunları ve C ve C++ uygulamaları için teknikleri açıklar.  
  
 [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)  
 Daha güvenli hata ayıklama için öneriler sağlar.



