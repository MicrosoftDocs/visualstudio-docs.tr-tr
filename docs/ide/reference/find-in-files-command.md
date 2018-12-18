---
title: Dosyalarda Bul Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4cf5078bb16d90744b83dfd99cf0c1da663149a
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705027"
---
# <a name="find-in-files-command"></a>Dosyalarda Bul Komutu
Arama bir alt kümesi üzerinde kullanılabilir seçenekleri kullanarak dosyaları **dosyalarda Bul** sekmesinde **bulma ve değiştirme** penceresi.

## <a name="syntax"></a>Sözdizimi

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` Gerekli. Eşleşen metin.

## <a name="switches"></a>Anahtarlar
 /Case veya /c isteğe bağlı. Eşleşme ortaya yalnızca büyük ve küçük harfleri tam olarak belirtilen eşleşiyorsa `findwhat` bağımsız değişkeni.

 /ext: `extensions` isteğe bağlı. Aranacak dosyaların dosya uzantıları belirtir. Bir daha önce girilmiş olması durumunda belirtilmezse, önceki uzantıyı kullanılır.

 /lookin: `searchpath` isteğe bağlı. Arama dizini. Yol boşluk içeriyorsa, yolun tamamını tırnak işaretleri içine alın.

 /Names veya /n isteğe bağlı. Eşleşmeleri dosya adlarının bir listesini görüntüler.

 / Options veya /t isteğe bağlı. Geçerli Bul seçeneği ayarlarını listesini görüntüler ve arama gerçekleştirmez.

 /Regex veya /r isteğe bağlı. Önceden tanımlanmış özel karakterleri kullanan `findwhat` bağımsız değişken olarak değişmez değer karakterleri yerine metin desenlerini göstermek gösterimler. Normal ifade karakter tam bir listesi için bkz: [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset veya /e isteğe bağlı. Bul seçeneklerini varsayılan ayarlarına geri döndürür ve bir arama gerçekleştirmez.

 / İsteğe bağlı durdurun. Devam eden ise geçerli arama işlemini durdurur. Arama, diğer tüm bağımsız değişkenleri göz ardı eder zaman `/stop` belirtilmedi. Örneğin, geçerli aramayı durdurmak için aşağıdaki girmeniz gerekir:

```cmd
>Edit.FindinFiles /stop
```

 /Sub veya /s isteğe bağlı. Alt klasörleri /lookin belirtilen dizin içinde arar:`searchpath` bağımsız değişkeni.

 /text2 veya /2 isteğe bağlı. Arama sonuçlarını Bul sonuçları 2 penceresinde görüntüler.

 /wild veya /l isteğe bağlı. Önceden tanımlanmış özel karakterleri kullanan `findwhat` bağımsız değişkeni olarak bir karakter ya da bir karakter dizisi temsil etmek için gösterimler.

 /Word veya /w isteğe bağlı. Yalnızca tam sözcükleri için arama yapar.

## <a name="example"></a>Örnek
 Bu örnekte "My Visual Studio projeleri" klasöründe bulunan tüm .cls dosyalarında btnCancel arar ve Bul sonuçları 2 penceresinde eşleştirme bilgileri görüntüler.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Dosyalarda Bul](../../ide/find-in-files.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)