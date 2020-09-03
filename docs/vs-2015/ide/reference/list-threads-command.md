---
title: Iş parçacıklarını Listele komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671135"
---
# <a name="list-threads-command"></a>İş Parçacıklarını Listele Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Geçerli programdaki iş parçacıklarının listesini görüntüler.

## <a name="syntax"></a>Söz dizimi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `index` Seçim. Geçerli iş parçacığı olarak dizini tarafından bir iş parçacığı seçer.

## <a name="remarks"></a>Açıklamalar
 Belirtildiğinde `index` bağımsız değişken belirtilen iş parçacığını geçerli iş parçacığı olarak işaretler. Geçerli iş parçacığının yanındaki listede bir yıldız işareti (*) görüntülenir.

## <a name="example"></a>Örnek

```
>Debug.ListThreads
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Çağrı yığınını Listele komut](../../ide/reference/list-call-stack-command.md) [listesi ayrıştırma komutu](../../ide/reference/list-disassembly-command.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
