---
title: Ayrıştırılmış Kodu Listele Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64951810020d99239a47b9c6bdba751b2c0a3dfd
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704739"
---
# <a name="list-disassembly-command"></a>Ayrıştırılmış Kodu Listele Komutu
Hata ayıklama işlemi başlar ve hataların nasıl işleneceğini belirtmenizi sağlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
 Her anahtar, formun tamamını veya bir kısa süreli kullanılarak çağrılabilir.

 / count: `number` [veya] / c: `number` [veya] /length: `number` [veya] / l: `number`

 İsteğe bağlı. Görüntülenecek yönergeleri sayısı. Varsayılan değer 8'dir.

 /endaddress: `expression` [veya] / e: `expression`

 İsteğe bağlı. Ayrıştırılmış durdurmak hangi adresi.

 /codebytes:`yes` &#124; `no` [veya] /bytes:`yes` &#124; `no` [veya] / b:`yes`&#124;`no`

 İsteğe bağlı. Kod bayt sayısının görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `no`.

 / source:`yes` &#124; `no` [veya] / s:`yes`&#124;`no`

 İsteğe bağlı. Kaynak kodu görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `no`.

 /symbolnames:`yes` &#124; `no` [veya] /names:`yes` &#124; `no` [veya] / n:`yes`&#124;`no`

 İsteğe bağlı. Simgeler adları görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `yes`.

 [/ lınenumbers:`yes`&#124;`no`]

 İsteğe bağlı. Kaynak koduyla ilişkili satır numaralarını görüntülemesini sağlar. / Source anahtar değeri olmalıdır `yes` /linenumbers anahtarı kullanacak.

## <a name="example"></a>Örnek

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Çağrı Yığınını Listele Komutu](../../ide/reference/list-call-stack-command.md)
- [İş Parçacıklarını Listele Komutu](../../ide/reference/list-threads-command.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)