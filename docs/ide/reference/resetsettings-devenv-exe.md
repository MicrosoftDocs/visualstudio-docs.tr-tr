---
title: -ResetSettings (devenv.exe)
ms.date: 11/16/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c8f826db0c619e1dfb5811aaf9d0c5ef40093c97
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388679"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Visual Studio varsayılan ayarlarına geri yükler ve Visual Studio IDE otomatik olarak başlatır. İsteğe bağlı olarak belirtilen bir ayarları sıfırlar *vssettings* dosya.

Varsayılan ayarlar, Visual Studio ilk başlatıldığında seçilen profili tarafından belirlenir.

> [!TIP]
> Tümleşik geliştirme ortamı (IDE) kullanarak ayarlarını sıfırlama hakkında bilgi edinmek için [ayarlarına](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Sözdizimi

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Arguments

`SettingsFile`

Dosyanın tam yolunu ve adını *vssettings* Visual Studio'ya uygulamak için dosya.

Genel Geliştirme Ayarları profilini geri yüklemek için kullanın `General`.

## <a name="remarks"></a>Açıklamalar

Hayır ise `SettingsFile` belirtilirse, ayar varsayılan koleksiyonunu seçmek için istenirse sonraki Visual Studio'yu başlatın.

## <a name="example"></a>Örnek

Aşağıdaki komut satırını dosyasında depolanan ayarları uygular `MySettings.vssettings`.

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../environment-settings.md)
- [Visual Studio IDE'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)