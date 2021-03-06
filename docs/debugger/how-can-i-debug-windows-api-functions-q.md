---
title: Windows API işlevlerinde hata ayıkla | Microsoft Docs
description: Yüklü NT sembolleri olan bir Windows API işlevini nasıl ayıklayacağınızı öğrenin. 32 bitlik kodda, kesme noktasını ayarlamak için işlev adının düzenlenmiş biçimini kullanırsınız.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89fdbcf9d18a7794e1fb2520384db0f9bcec3147
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386949"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Windows API İşlevlerinde Nasıl Hata Ayıklayabilirim?
Yüklü NT sembolleri olan bir Windows API işlevinde hata ayıklamak istiyorsanız, aşağıdakileri yapmanız gerekir.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>NT sembolleri yüklenmiş bir Windows API işlevi üzerinde bir kesme noktası ayarlamak için

- [İşlev kesme noktasında](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file), işlev adını IŞLEVIN bulunduğu dll adı ile birlikte girin ( [bağlam işlecine](../debugger/context-operator-cpp.md)bakın). 32 bitlik kodda, işlev adının düzenlenmiş formunu kullanın. Örneğin, **Messagebip** üzerinde bir kesme noktası ayarlamak için, şunu girmeniz gerekir.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Düzenlenmiş adı almak için bkz. [düzenlenmiş adları görüntüleme](/previous-versions/5x49w699(v=vs.140)).

     Düzenlenmiş adı test edebilir ve kodu ayrıştırılmış kodda görüntüleyebilirsiniz. Visual Studio hata ayıklayıcı işlevinde duraklatıldığında, kod düzenleyici veya çağrı yığını penceresinde işleve sağ tıklayın ve **ayrıştırılmış koda git**' i seçin.

- 64 bitlik kodda, açıklanedilmemiş adı kullanabilirsiniz.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
