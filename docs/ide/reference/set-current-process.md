---
title: Geçerli Süreci Ayarla
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64561db59cc089d9539ab396cf4e869e92fe1117
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705092"
---
# <a name="set-current-process"></a>Geçerli Süreci Ayarla
Belirtilen işlem etkin işlem hata ayıklayıcı olarak ayarlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Arguments
 `index`

 Gerekli. İşlem dizini.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama yaptığınız ancak herhangi bir anda yalnızca bir işlem dubber etkin olduğu durumlarda, birden çok işlem ekleyebilirsiniz. Kullanabileceğiniz `SetCurrentProcess` etkin işlem ayarlamak için komutu.

## <a name="example"></a>Örnek

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)