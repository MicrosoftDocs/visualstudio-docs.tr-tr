---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f797b6228124da8d8a998a6647dcfd9195ea92c
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948081"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Yükleme sorunu VSPackages yüklenmesini önlemek amacıyla isteyen kullanıcılar tarafından Vspackages'a eklenmiş atlamak için tüm seçenekleri temizler ve ardından başlatır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sözdizimi

```cmd
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Açıklamalar
 SkipLoading etiketinin varlığını VSPackage yüklenmesini devre dışı bırakır; Etiket temizleme VSPackage yükleme yeniden etkinleştirir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, tüm SkipLoading etiketlerini temizler.

```cmd
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)