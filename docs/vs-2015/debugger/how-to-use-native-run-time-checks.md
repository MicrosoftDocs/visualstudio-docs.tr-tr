---
title: 'Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma | Microsoft Docs'
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
- c.runtime.errorchecks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4efbb4e151ea47f655f0b28e19d2811d5541e944
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798761"
---
# <a name="how-to-use-native-run-time-checks"></a>Nasıl Yapılır: Yerel Çalışma Zamanı Denetimlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C++'da yerel kullanabilirsiniz [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) gibi ortak çalışma zamanı hataları yakalamak için:  
  
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
 [Visual Studio'da hata ayıklama](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Çalışma Zamanı Hata Denetimi](http://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)





