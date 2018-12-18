---
title: CRT hata ayıklama kitaplığı kullanımı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e550a5fa705f3c85b3464046cd3c92d96bc47ca
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467962"
---
# <a name="crt-debug-library-use"></a>CRT Hata Ayıklama Kitaplığı Kullanımı
C çalışma zamanı kitaplığı kapsamlı hata ayıklama desteği sağlar. CRT hata ayıklama kitaplıklarından birini kullanmak için ile bağlamanız gerekir [/DEBUG](/cpp/build/reference/debug-generate-debug-info) ve ile derleme **/MDd**, **/MTd**, veya **/LDd**.  
  
## <a name="remarks"></a>Açıklamalar  
 CRT hata ayıklama için makrolar ve ana tanımları CRTDBG.h üstbilgi dosyasında bulunabilir.  
  
 CRT hata ayıklama kitaplıkları işlevlerinde hata ayıklama bilgileri ile derlenen ([/Z7, /Zd, / zi, /zı (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format)) ve en iyi duruma getirme olmadan. Bazı işlevler kendisine geçirilen parametreleri doğrulamak için onayları içerir ve kaynak kodu sağlanır. Bu kaynak koduyla işlevleri, beklediğiniz ve hatalı parametre veya bellek durumlarını denetleyin şekilde çalıştığını doğrulamak için CRT işlevlerinin geçebilirsiniz. (Bazı CRT teknolojisi özel ve kaynak kodu özel durum işleme, kayan nokta ve birkaç diğer yordamlar için sağlamaz.)  
  
 Visual C++ yüklediğinizde, sabit diskinizdeki C çalışma zamanı kitaplığı kaynak kodu yükleme seçeneğiniz vardır. Kaynak kodu yüklemezseniz CD-ROM CRT işlevlerinin adım gerekir.  
  
 Kullanabileceğiniz çeşitli çalışma zamanı kitaplıkları hakkında daha fazla bilgi için bkz: [C çalışma zamanı kitaplıkları](/cpp/c-runtime-library/crt-library-features).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (Çalışma Zamanı Kitaplığını Kullan)](/cpp/build/reference/md-mt-ld-use-run-time-library)