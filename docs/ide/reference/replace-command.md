---
title: Değiştir Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b712ee88526585d24ffd7b22fadbbf015c3d131
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949951"
---
# <a name="replace-command"></a>Değiştir Komutu
Bir alt kümesi üzerinde kullanılabilir seçenekleri kullanarak dosyaları metinde değiştirir **dosyalarda Değiştir** sekmesinde **bulma ve değiştirme** penceresi.

## <a name="syntax"></a>Sözdizimi

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat`

 Gerekli. Eşleşen metin.

 `replacewith`

 Gerekli. Eşleşen metin için alternatif metin.

## <a name="switches"></a>Anahtarlar
 / all veya /a

 İsteğe bağlı. Arama metni tüm oluşumlarını değiştirme metni ile değiştirir.

 /Case veya /c

 İsteğe bağlı. Eşleşme ortaya yalnızca zaman büyük ve küçük harfleri tam olarak belirtilen eşleşiyorsa `findwhat` bağımsız değişkeni.

 / doc veya /d

 İsteğe bağlı. Yalnızca geçerli belgede arar. Kullanılabilir arama kapsamlar yalnızca birini belirtin `/doc`, `/proc`, `/open`, veya `/sel`.

 / Gizli veya /h

 İsteğe bağlı. Tasarım zamanı denetimi, gizli bir bölge anahatları belirlenmiş bir belge veya bir daraltılmış sınıfı ya da yöntemi meta verileri gibi gizli bilgiler ve daraltılmış metin arar.

 /Open veya /o

 İsteğe bağlı. Bir belge değilmiş gibi tüm açık belgeleri arar. Kullanılabilir arama kapsamlar yalnızca birini belirtin `/doc`, `/proc`, `/open`, veya `/sel`.

 / Options veya /t

 İsteğe bağlı. Geçerli Bul seçeneği ayarlarını listesini görüntüler ve arama gerçekleştirmez.

 /proc veya /p

 İsteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlar yalnızca birini belirtin `/doc`, `/proc`, `/open`, veya `/sel`.

 /Regex veya /r

 İsteğe bağlı. Önceden tanımlanmış özel karakterleri kullanan `findwhat` bağımsız değişken olarak değişmez değer karakterleri yerine metin desenlerini göstermek gösterimler. Normal ifade karakter tam bir listesi için bkz: [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset veya /e

 İsteğe bağlı. Bul seçeneklerini varsayılan ayarlarına geri döndürür ve bir arama gerçekleştirmez.

 /sel veya/s

 İsteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlar yalnızca birini belirtin `/doc`, `/proc`, `/open`, veya `/sel`.

 /UP veya /u

 İsteğe bağlı. Dosyanın en üstüne doğru dosyayı geçerli konumundan arar. Varsayılan olarak, dosya ve dosyanın sonuna doğru İlerle geçerli konumda aramalar başlar.

 /wild veya /l

 İsteğe bağlı. Önceden tanımlanmış özel karakterleri kullanan `findwhat` bağımsız değişkeni olarak bir karakter ya da bir karakter dizisi temsil etmek için gösterimler.

 /Word veya /w

 İsteğe bağlı. Yalnızca tam sözcükleri için arama yapar.

## <a name="example"></a>Örnek
 Bu örnek değiştirir `btnSend` ile `btnSubmit` tüm belgeleri açın.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)