---
title: 'Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: cc4e4b9ee24bc7be9126866ae804f1b3c6d6dba6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860818"
---
# <a name="how-to-use-native-run-time-checks"></a>Nasıl Yapılır: Yerel Çalışma Zamanı Denetimlerini Kullanma
Visual C++'da yerel kullanabilirsiniz [runtime_checks](/cpp/preprocessor/runtime-checks) gibi ortak çalışma zamanı hataları yakalamak için:  
  
- İşaretçi Bozulması yığın.  
  
- Yerel diziler taşması.  
  
- Yığın bozulması.  
  
- Başlatılmayan yerel değişkenlerde bağımlılıkları.  
  
- Atama daha kısa bir değişken için veri kaybı.  
  
  Kullanırsanız **/RTC** bir en iyi duruma getirilmiş ile (**/O**) derleme, derleyici hatası sonuçları. Kullanıyorsanız bir `runtime_checks` pragma en iyi duruma getirilmiş bir derlemedeki pragması etkisizdir.  
  
  Etkin çalışma zamanı denetimleri olan bir program hata ayıklaması yaparken, programı durdurup bir çalışma zamanı hatası oluştuğunda ayıklayıcıya olduğunda varsayılan eylem. Herhangi bir çalışma zamanı denetimi için bu varsayılan davranışı değiştirebilirsiniz. Daha fazla bilgi için [yönetme özel durumları hata ayıklayıcısı ile](../debugger/managing-exceptions-with-the-debugger.md).  
  
  Aşağıdaki yordamlar, hata ayıklama derlemesinde yerel çalışma zamanı denetimleri etkinleştirme ve yerel çalışma zamanı denetimi davranışını değiştirmek nasıl açıklar.  
  
  Bu bölümdeki diğer konular hakkında bilgi sağlar:  
  
- [C çalışma zamanı kitaplığı ile çalışma zamanı özelleştirme denetler](../debugger/native-run-time-checks-customization.md)  
  
- [C çalışma zamanı kitaplığını kullanmadan çalışma zamanı kullanarak denetler](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Hata ayıklama derlemesinde yerel çalışma zamanı denetimlerini etkinleştirmek için  
  
-   Kullanım **/RTC** seçeneği ve hata ayıklama sürümü C çalışma zamanı kitaplığı ile bağlantı (/ MDd, örneğin).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Yerel çalışma zamanı denetimi davranışını değiştirmek için  
  
-   Kullanım `runtime_checks` pragması.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’da hata ayıklama](../debugger/index.md)  
 [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [Çalışma Zamanı Hata Denetimi](/cpp/c-runtime-library/run-time-error-checking)