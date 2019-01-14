---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794934ab0bddcc90a36accf639b26e5ecc6bab30
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54228068"
---
# <a name="nosplash-devenvexe"></a>/ NoSplash (devenv.exe)

Karşılama ekranında gösterilen engeller.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Arguments

- *Fıle1'de*

  İsteğe bağlı. Mevcut bir Visual Studio örneğini dosyayı açın. Visual Studio örneği varsa, yeni bir örneği bir Basitleştirilmiş pencere düzeni ile oluşturulur ve aracı açılır *dosya1* yeni örneğinde.

- *Dosyan*

  İsteğe bağlı. Visual Studio'nun var olan örnekte açmak için bir veya daha fazla ek dosyalar.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, giriş ekranı gizler. Bu anahtar bırakarak gösterilecek giriş ekranı neden olur. Giriş ekranı (örneğin, onay VSPackage ürün simgesi) daha ayrıntılı incelemek istediğiniz kullanırsanız [/tanıtım](../../extensibility/devenv-command-line-switches-for-vspackage-development.md) geçin.

`/NoSplash` Anahtar birleştirilebilir diğer anahtarlardan bazılarıyla gibi [/Run](run-devenv-exe.md) veya [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Örnek

Örnek üç ekranı görüntülemeden IDE açın. İkinci örnek, ayrıca belirtilen çözümü derler ve derlenen yürütülebilir dosyayı çalıştırır. Üçüncü örnek IDE içinde hata ayıklama için belirtilen çalıştırılabilir dosya açılır.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [VSPackage geliştirme için Devenv komut satırı anahtarları](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)