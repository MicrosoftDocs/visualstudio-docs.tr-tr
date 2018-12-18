---
title: Hata ayıklama Visual c++ özelliklerini etkinleştirme (-D_DEBUG) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 772467caf74a381fc2ef5cc74e8e31bf2ff0503c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949623"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Visual C++'de Hata Ayıklama Özelliklerini Etkinleştirme (/D_DEBUG)
İçinde [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], programınızı sembolü ile derleme yaparken onaylar etkinleştirilen gibi hata ayıklama özellikleri **_DEBUG** tanımlı. Tanımlayabileceğiniz **_DEBUG** iki yoldan biriyle:  
  
- Belirtin **#define _DEBUG** , kaynak kodunuzdaki veya  
  
- Belirtin **/D_DEBUG** derleyici seçeneği. (Proje sihirbazları kullanarak Visual Studio'da oluşturursanız **/D_DEBUG** hata ayıklama yapılandırmasında otomatik olarak tanımlanır.)  
  
  Zaman **_DEBUG** olan tanımlanan, derleyici tarafından çevrelenen kod bölümlerini derler **#ifdef _DEBUG** ve `#endif`.  
  
  MFC programı hata ayıklama yapılandırmasını MFC Kitaplığı hata ayıklama sürümü ile bağlanması gerekir. MFC üstbilgi dosyalarındaki doğru MFC kitaplığı ile bağlantı için tanımladığınız, gibi semboller üzerinde temel sürümünü **_DEBUG** ve **_UNICODE**. Ayrıntılar için bkz [MFC kitaplık sürümleri](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)