---
title: Dosya Aç Komutu
description: Dosya Aç komutu ve var olan bir dosyayı nasıl açtığı hakkında bilgi edinin ve bir düzenleyici belirtmenize izin verir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96376c352d3019ba2efefc1f82e75e89a4ac2370
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935631"
---
# <a name="open-file-command"></a>Dosya Aç komutu

Var olan bir dosyayı açar ve bir düzenleyici belirtmenize olanak tanır.

## <a name="syntax"></a>Söz dizimi

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler

`filename`

Gereklidir. Açılacak dosyanın tam veya kısmi yolu ve dosya adı. Boşluk içeren yollar tırnak işaretleri içine alınmalıdır.

## <a name="switches"></a>Anahtarlar

/e`editorname`

İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E: `editorname` Argument sözdizimi, birlikte Aç Iletişim kutusunda göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

Örneğin, kaynak kodu düzenleyicisinde bir dosya açmak için,/e: Argument için aşağıdakini girersiniz `editorname` .

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar

Bir yol girerken, otomatik tamamlama doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek

Bu örnek, kaynak kodu düzenleyicisinde "test1. css" stil dosyasını açar.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Komut penceresi](../../ide/reference/immediate-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
