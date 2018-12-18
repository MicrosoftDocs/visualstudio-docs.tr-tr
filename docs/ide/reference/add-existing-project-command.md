---
title: Varolan Projeyi Ekle Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c030358eb071613e98d473845708b01235683ded
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704791"
---
# <a name="add-existing-project-command"></a>Varolan Projeyi Ekle Komutu
Varolan projeyi geçerli çözüme ekler.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
 `filename` İsteğe bağlı. Tam yol ve proje adı, çözüme eklemek için projenin uzantısına sahip.

 Varsa `filename` bağımsız değişkeni alanları içerir, tırnak işaretleri içine alınmalıdır.

 Bir dosya adı belirtilirse, bu kullanıcının bir proje seçebileceği şekilde komutu dosya iletişim kutusu açılır.

## <a name="remarks"></a>Açıklamalar
 Otomatik Tamamlama doğru yolun ve dosya adı, türü bulmaya çalışır.

## <a name="example"></a>Örnek
 Bu örnek, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proje olan geçerli çözüme TestProject1,.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)