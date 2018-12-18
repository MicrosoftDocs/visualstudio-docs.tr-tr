---
title: Modülleri Listele Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54e975cf886f0bb8392bd3679a28bae6bb6bfe00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944667"
---
# <a name="list-modules-command"></a>Modülleri Listele Komutu
Geçerli işlem için modüllerini listeler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametreler
 / Adresi:`yes|no`

 İsteğe bağlı. Bellek adreslerini modüllerin gösterilip gösterilmeyeceğini belirler. Varsayılan değer `yes`.

 / Adı:`yes|no`

 İsteğe bağlı. Modül adlarını gösterilip gösterilmeyeceğini belirler. Varsayılan değer `yes`.

 / Order:`yes|no`

 İsteğe bağlı. Modülleri sırasını gösterilip gösterilmeyeceğini belirler. Varsayılan değer `no`.

 / Yolu:`yes|no`

 İsteğe bağlı. Modülleri yollarını gösterilip gösterilmeyeceğini belirler. Varsayılan değer `yes`.

 / İşlemi:`yes|no`

 İsteğe bağlı. Modülleri işlemlerinin gösterilip gösterilmeyeceğini belirler. Varsayılan değer `no`.

 / SymbolFile:`yes|no`

 İsteğe bağlı. Simge dosyaları modüllerin gösterilip gösterilmeyeceğini belirler. Varsayılan değer `no`.

 / SymbolStatus:`yes|no`

 İsteğe bağlı. Sembol durumları modüllerin gösterilip gösterilmeyeceğini belirler. Varsayılan değer `yes`.

 / Zaman damgası:`yes|no`

 İsteğe bağlı. Zaman damgaları modüllerin gösterilip gösterilmeyeceğini belirler. Varsayılan değer `no`.

 / Sürümü:`yes|no`

 İsteğe bağlı. Modülleri sürümleri gösterilip gösterilmeyeceğini belirler. Varsayılan değer `no`.

## <a name="example"></a>Örnek
 Bu örnek modül adlarını, adreslerini ve geçerli işlem için zaman damgalarını listeler.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Nasıl yapılır: modüller penceresini kullanma](../../debugger/how-to-use-the-modules-window.md)