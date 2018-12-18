---
title: CRT hata ayıklama kitaplığı kullanımı | Microsoft Docs
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
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6bba5b9c1b9d65c867176ac72c0641fac4cd286
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817652"
---
# <a name="crt-debug-library-use"></a>CRT Hata Ayıklama Kitaplığı Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C çalışma zamanı kitaplığı hata ayıklama kapsamlı destek sağlar. CRT hata ayıklama kitaplıklarını birini kullanmak için ile bağlamalısınız [/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) ve derleme **/MDd**, **/mtd**, veya **/LDd**.  
  
## <a name="remarks"></a>Açıklamalar  
 Ana tanımları ve makroları CRT hata ayıklama için CRTDBG.h üstbilgi dosyasında bulunabilir.  
  
 CRT hata ayıklama kitaplıklarını işlevlerinde hata ayıklama bilgileri ile derlenen ([/z7, / ZD, / zi, /zı (hata ayıklama bilgileri biçimi)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) ve en iyi duruma getirme olmadan. Onaylamalar kendisine geçirilen parametreleri doğrulamak için bazı işlevleri içerir ve kaynak kodu sağlanır. Bu kaynak koduyla bekler ve hatalı parametre veya bellek durumları denetlemek gibi işlevleri çalıştığını onaylamak için CRT işlevlerinin geçebilirsiniz. (Bazı CRT teknoloji özel ve kaynak kodu, özel durum işleme, kayan nokta ve diğer birkaç rutinleri için sağlamaz.)  
  
 Visual C++'ı yüklediğinizde, C çalışma zamanı kitaplığı kaynak kodunu sabit diskinize yükleme seçeneğiniz vardır. Kaynak kodu yüklemezseniz, CRT işlevlerinin adımlamak için CD-ROM'dan gerekir.  
  
 Kullanabileceğiniz çeşitli çalışma zamanı kitaplıkları hakkında daha fazla bilgi için bkz. [C çalışma zamanı kitaplıkları](http://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (Çalışma Zamanı Kitaplığını Kullan)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)



