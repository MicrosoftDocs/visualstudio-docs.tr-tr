---
title: Dosyalarda Değiştir Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8bf54892d17a877cd8e2c3ffd21ebd513e303d6c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946669"
---
# <a name="replace-in-files-command"></a>Dosyalarda Değiştir Komutu
Bir alt kümesi üzerinde kullanılabilir seçenekleri kullanarak dosyaları metinde değiştirir **dosyalarda Değiştir** sekmesinde **bulma ve değiştirme** penceresi.

## <a name="syntax"></a>Sözdizimi

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
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

 /ext: `extensions`

 İsteğe bağlı. Aranacak dosyaların dosya uzantıları belirtir.

 /Keep veya/k

 İsteğe bağlı. Tüm değiştirilen dosyalar açık bırakılır belirtir.

 /lookin: `searchpath`

 İsteğe bağlı. Arama dizini. Yol boşluk içeriyorsa, yolun tamamını tırnak işaretleri içine alın.

 / Options veya /t

 İsteğe bağlı. Geçerli Bul seçeneği ayarlarını listesini görüntüler ve arama gerçekleştirmez.

 /Regex veya /r

 İsteğe bağlı. Önceden tanımlanmış özel karakterleri kullanan `findwhat` bağımsız değişken olarak değişmez değer karakterleri yerine metin desenlerini göstermek gösterimler. Normal ifade karakter tam bir listesi için bkz: [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset veya /e

 İsteğe bağlı. Bul seçeneklerini varsayılan ayarlarına geri döndürür ve bir arama gerçekleştirmez.

 / Stop

 İsteğe bağlı. Devam eden ise geçerli arama işlemini durdurur. Değiştir, diğer tüm bağımsız değişkenleri göz ardı eder zaman `/stop` belirtilmedi. Örneğin, geçerli değişiklik durdurmak için aşağıdaki girmeniz gerekir:

```
>Edit.ReplaceinFiles /stop
```

 /Sub veya/s

 İsteğe bağlı. Alt klasörleri /lookin belirtilen dizin içinde arar:`searchpath` bağımsız değişkeni.

 /text2 veya /2

 İsteğe bağlı. Değiştirme sonuçlarını görüntüler **Bul sonuçları 2** penceresi.

 /wild veya /l

 İsteğe bağlı. Önceden tanımlanmış özel karakterleri kullanan `findwhat` bağımsız değişkeni olarak bir karakter ya da bir karakter dizisi temsil etmek için gösterimler.

 /Word veya /w

 İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
 Bu örnek arar `btnCancel` ve ile değiştirir `btnReset` tüm .cls dosyaları, "visual studio projeleri my" klasöründe ve değiştirme bilgilerini görüntüler **Bul sonuçları 2** penceresi.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
- [Dosyalarda Değiştir](../../ide/replace-in-files.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)