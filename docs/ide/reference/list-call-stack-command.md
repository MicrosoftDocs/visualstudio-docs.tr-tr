---
title: Çağrı Yığınını Listele Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e809af75f0a4a47da6af30a3d93748401ca4609d
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512011"
---
# <a name="list-call-stack-command"></a>Çağrı Yığınını Listele Komutu
Geçerli çağrı yığınını görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Arguments
 `index` İsteğe bağlı. Geçerli yığın çerçevesini ayarlar ve hiçbir çıktı görüntüler.

## <a name="switches"></a>Anahtarlar
 Her anahtar, formun tamamını veya bir kısa biçim kullanılarak çağrılabilir.

 / Sayısı:`number` [veya] / c:`number`

 İsteğe bağlı. Çağrı yığınlarını görüntülemek için en fazla sayısı. Varsayılan değer büyük/küçük harf sınırsızdır.

 / ShowTypes:`yes` &#124; `no` [veya] / t:`yes`&#124;`no`

 İsteğe bağlı. Parametre türleri görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `yes`.

 / ShowNames:`yes` &#124; `no` [veya] / n:`yes`&#124;`no`

 İsteğe bağlı. Parametre adları görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `yes`.

 / ShowValues:`yes` &#124; `no` [veya] / v:`yes`&#124;`no`

 İsteğe bağlı. Parametre değerlerini görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `yes`.

 / ShowModule:`yes` &#124; `no` [veya] / m:`yes`&#124;`no`

 İsteğe bağlı. Modül adı görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `yes`.

 / ShowLineOffset:`yes` &#124; `no` [veya] / #:`yes`&#124;`no`

 İsteğe bağlı. Satır sapması görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `no`.

 / ShowByteOffset:`yes` &#124; `no` [veya] / b:`yes`&#124;`no`

 İsteğe bağlı. Bayt uzaklığı görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `no`.

 / ShowLanguage:`yes` &#124; `no` [veya] / l:`yes`&#124;`no`

 İsteğe bağlı. Dil görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `no`.

 / IncludeCallsAcrossThreads:`yes` &#124; `no` [veya] / i:`yes`&#124;`no`

 İsteğe bağlı. Çağrıları için veya diğer iş parçacıklarından eklenip eklenmeyeceğini belirtir. Varsayılan değer `no`.

 / ShowExternalCode:`yes`&#124;`no`

 İsteğe bağlı. Çağrı yığını için yalnızca kendi kodum görüntülenip görüntülenmeyeceğini belirtir. Tüm kullanıcı olmayan kod, yalnızca kendi kodum kapalı olduğunda görüntülenir. Yalnızca kendi kodum etkin olduğunda, kullanıcı dışı kod olarak görüntülenen `[external]` çağrı yığını çıktı.

 İş parçacığı:`n`

 İsteğe bağlı. İş parçacığı için çağrı yığınını görüntüler `n`. İş parçacığı belirtilmemişse, geçerli iş parçacığı için çağrı yığınını görüntüler.

## <a name="remarks"></a>Açıklamalar
 Bu komutun gelecekteki çağrılarına bağımsız değişkenler veya anahtarlarının yapılan değişiklikler uygulanır. Debug.ListCallStackby kendisini dağıttığınız bütün çağrı yığını görüntülenir. Örneğin bir dizin belirtmeniz durumunda

```cmd
Debug.ListCallStack 2
```

 Geçerli yığın çerçevesi (Bu durumda, ikinci çerçevesi) bu çerçevesine ayarlayın daha sonra.

 Ayrıca, önceden tanımlanmış diğer adının, bu komutu yazabilirsiniz kb. Örneğin, girin

```cmd
kb 2
```

 Geçerli yığın çerçevesi ikinci çerçeveye ayarlamak için.

## <a name="example"></a>Örnek

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Ayrıştırılmış Kodu Listele Komutu](../../ide/reference/list-disassembly-command.md)
- [İş Parçacıklarını Listele Komutu](../../ide/reference/list-threads-command.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)