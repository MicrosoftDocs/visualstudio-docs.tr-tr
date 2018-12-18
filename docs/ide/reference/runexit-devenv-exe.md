---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dff2f028c94013df4f69e9aca244f98c307d2782
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948237"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Derler ve belirtilen proje veya çözüm çalıştırır ve ardından tümleşik geliştirme ortamı (IDE) kapatır.

## <a name="syntax"></a>Sözdizimi

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments
 `SolutionName`

 Gerekli. Bir çözüm dosyası adını ve tam yolu.

 `ProjectName`

 Gerekli. Bir proje dosyasının adını ve tam yolu.

## <a name="remarks"></a>Açıklamalar
 Derler ve belirtilen proje veya çözümü etkin çözüm yapılandırması için belirtilen ayarlara göre çalıştırır. IDE projeyi sırasında bu anahtar en aza indirir veya çözümü çalıştırın, sonra projeyi IDE'yi kapatır ve çözüm çalışması tamamlandıktan.

-   Çift tırnak içine boşluk dizeleri alın.

-   Hataları dahil olmak üzere Özet bilgileri görüntülenebilir **komut** penceresinde veya belirtilen herhangi bir günlük dosyasını `/out` geçin.

## <a name="example"></a>Örnek
 Bu örnek çözüm çalıştırılır `MySolution` simge durumuna küçültülmüş IDE'de etkin dağıtım yapılandırması kullanan ve daha sonra IDE'yi kapatır.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/ Çalıştırma (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Derleme (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ (Devenv.exe out)](../../ide/reference/out-devenv-exe.md)