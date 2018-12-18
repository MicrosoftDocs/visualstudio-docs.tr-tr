---
title: Hata ayıklama Visual c++ özelliklerini etkinleştirme (-D_DEBUG) | Microsoft Docs
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
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf560bcde09b9d2e3c2bee689c92c9900c6e2af5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760595"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Visual C++'de Hata Ayıklama Özelliklerini Etkinleştirme (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], programınızı sembolü ile derleme yaparken onaylar etkinleştirilen gibi hata ayıklama özellikleri **_DEBUG** tanımlı. Tanımlayabileceğiniz **_DEBUG** iki yoldan biriyle:  
  
- Belirtin **#define _DEBUG** , kaynak kodunuzdaki veya  
  
- Belirtin **/D_DEBUG** derleyici seçeneği. (Proje sihirbazları kullanarak Visual Studio'da oluşturursanız **/D_DEBUG** hata ayıklama yapılandırmasında otomatik olarak tanımlanır.)  
  
  Zaman **_DEBUG** olan tanımlanan, derleyici tarafından çevrelenen kod bölümlerini derler **#ifdef _DEBUG** ve `#endif`.  
  
  MFC programı hata ayıklama yapılandırmasını MFC Kitaplığı hata ayıklama sürümü ile bağlanması gerekir. MFC üstbilgi dosyalarındaki doğru MFC kitaplığı ile bağlantı için tanımladığınız, gibi semboller üzerinde temel sürümünü **_DEBUG** ve **_UNICODE**. Ayrıntılar için bkz [MFC kitaplık sürümleri](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)



