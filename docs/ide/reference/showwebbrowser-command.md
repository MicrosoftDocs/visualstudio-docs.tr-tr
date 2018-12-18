---
title: ShowWebBrowser Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87536df138de092948d845cf05d20af8e63ad68a
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672151"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser Komutu

Tümleşik geliştirme ortamı (IDE) veya IDE dışında içindeki bir web tarayıcı penceresinde belirttiğiniz URL'yi görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Arguments
 `URL`

 Gerekli. Web sitesi için URL (Tekdüzen Kaynak Konum Belirleyicisi).

## <a name="switches"></a>Anahtarlar
 / Yeni

 İsteğe bağlı. Sayfayı yeni bir web tarayıcısı örneğini görüntüleneceğini belirtir.

 /ext

 İsteğe bağlı. Sayfa IDE dışında varsayılan web tarayıcısında görüntüleneceğini belirtir.

## <a name="remarks"></a>Açıklamalar
 Diğer **ShowWebBrowser** komutu **gidin** veya **nav**.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, IDE dışında bir web tarayıcısında Microsoft Docs giriş sayfasında gösterilir. Web tarayıcısının bir örneği zaten açıksa kullanılır; Aksi halde yeni bir örneğini başlattınız.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)