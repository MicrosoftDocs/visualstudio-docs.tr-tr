---
title: -UseEnv (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a11d8eceec682e37f9bf34c79980c37880bdbe6
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948497"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Visual Studio başlatılır ve ortam değişkenlerini uygulamasına yükler **VC ++ dizinleri** iletişim kutusu.

> [!NOTE]
> Bu anahtar ile birlikte yüklenir **C++ ile masaüstü geliştirme** iş yükü.

## <a name="syntax"></a>Sözdizimi

```shell
Devenv /useenv
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Studio başlatılır ve ortam değişkenlerini uygulamasına yükler **VC ++ dizinleri** iletişim kutusu.

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>Ayrıca bkz.

* [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)