---
title: Kaynağı Listele Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03a5d0699fced4d01d439942081b359454bcf476
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943624"
---
# <a name="list-source-command"></a>Kaynağı Listele Komutu
Kaynak kodu belirtilen satır görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
 / Sayısı:`number`

 İsteğe bağlı. Görüntülenecek satır sayısını belirtir.

 / Geçerli

 İsteğe bağlı. Geçerli satır gösterir.

 / Dosyası:`filename`

 İsteğe bağlı. Gösterilecek dosyasının yolu. Bir dosya adı belirtilmezse, komut satırı geçerli deyimin için kaynak kodunu gösterir.

 / Satır:`number`

 İsteğe bağlı. Bir satır numarasında gösterir.

 / ShowLineNumbers:`yes|no`

 İsteğe bağlı. Satır numaraları görüntülenip görüntülenmeyeceğini belirtir.

## <a name="example"></a>Örnek
 Bu örnekte, kaynak kodu satır numaralarını görünür dosyanın Form1.vb, 4 satırından listelenmiştir.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)