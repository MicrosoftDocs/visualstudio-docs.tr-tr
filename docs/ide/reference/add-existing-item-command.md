---
title: Varolan Öğeyi Ekle Komutu
description: Var olan öğe Ekle komutu ve var olan bir dosyayı geçerli bir çözüme ekleme ve bunu açma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43c9e7d5947796bb1598bf9dc02420b31e43d167
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933836"
---
# <a name="add-existing-item-command"></a>Varolan Öğeyi Ekle Komutu
Geçerli çözüme var olan bir dosyayı ekler ve açar.

## <a name="syntax"></a>Söz dizimi

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler
`filename`\
Gereklidir. Geçerli çözüme eklenecek öğenin Uzantısı ile tam yol ve dosya adı. Dosya yolu veya dosya adı boşluk içeriyorsa, tüm yolu tırnak işaretleri içine alın.

## <a name="switches"></a>Anahtarlar
/e `editorname`\
İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E: `editorname` Argument sözdizimi, **birlikte Aç iletişim kutusunda** göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır. Örneğin, kaynak kodu düzenleyicisinde bir stil sayfası açmak için/e: Argument için aşağıdakini girersiniz `editorname` .

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek, Form1. frm dosyasını geçerli çözüme ekler.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
