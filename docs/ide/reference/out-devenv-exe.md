---
title: -Out (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5778cb281ca6edcf8045620aee049b0f115a50a
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948250"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Depolama ve çalıştırma, derleme, yeniden oluşturun veya bir çözüm dağıtma hataları görüntülemek için dosyayı belirtir.

## <a name="syntax"></a>Sözdizimi

```cmd
devenv /out FileName
```

## <a name="arguments"></a>Arguments
 `FileName`

 Gerekli. Bir yürütülebilir dosya oluştururken hatalar almak için dosyanın adı ve yolu.

## <a name="remarks"></a>Açıklamalar
 Dosya, var olmayan bir dosya adı belirtilirse, otomatik olarak oluşturulur. Dosya zaten varsa, dosyanın mevcut içeriğini için sonuçları eklenir.

 Komut satırı derleme hataları görüntülenir **komut** penceresi ve çözüm Oluşturucusu'nu görüntülemek **çıkış** penceresi. Bu seçenek, katılımsız yapılar çalıştırıyorsanız ve sonuçları görmek gereken yararlıdır.

## <a name="example"></a>Örnek
 Bu örnek çalıştırılır `MySolution` ve hataları Yazar `MyErrorLog.txt`.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/ Çalıştırma (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Derleme (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ (Devenv.exe) dağıtma](../../ide/reference/deploy-devenv-exe.md)