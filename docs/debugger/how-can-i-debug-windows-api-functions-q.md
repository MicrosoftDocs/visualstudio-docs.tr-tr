---
title: Windows API işlevlerinde hata ayıkla | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fab5627f3d467c0df289969e4fee010dd3ea78b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350400"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Windows API İşlevlerinde Nasıl Hata Ayıklayabilirim?
Yüklü NT sembolleri olan bir Windows API işlevinde hata ayıklamak istiyorsanız, aşağıdakileri yapmanız gerekir.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>NT sembolleri yüklenmiş bir Windows API işlevi üzerinde bir kesme noktası ayarlamak için

- [İşlev kesme noktasında](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file), işlev adını IŞLEVIN bulunduğu dll adı ile birlikte girin ( [bağlam işlecine](../debugger/context-operator-cpp.md)bakın). 32 bitlik kodda, işlev adının düzenlenmiş formunu kullanın. Örneğin, **Messagebip**üzerinde bir kesme noktası ayarlamak için, şunu girmeniz gerekir.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Düzenlenmiş adı almak için bkz. [düzenlenmiş adları görüntüleme](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

     Düzenlenmiş adı test edebilir ve kodu ayrıştırılmış kodda görüntüleyebilirsiniz. Visual Studio hata ayıklayıcı işlevinde duraklatıldığında, kod düzenleyici veya çağrı yığını penceresinde işleve sağ tıklayın ve **ayrıştırılmış koda git**' i seçin.

- 64 bitlik kodda, açıklanedilmemiş adı kullanabilirsiniz.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kod Hata Ayıklaması SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
