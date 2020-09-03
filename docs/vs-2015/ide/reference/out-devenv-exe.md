---
title: -Out (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 075746353440462a66133cd83ed9158470d8de5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662208"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir çözümü çalıştırdığınızda, yapılandırdığınızda, yeniden oluşturduğunuzda veya dağıtırken hataları depolamak ve göstermek için bir dosya belirtir.

## <a name="syntax"></a>Söz dizimi

```
devenv /out FileName
```

## <a name="arguments"></a>Bağımsız değişkenler
 `FileName` Gerekli. Yürütülebilir dosya oluştururken hata alacak dosyanın yolu ve adı.

## <a name="remarks"></a>Açıklamalar
 Varolmayan bir dosya adı belirtilmişse dosya otomatik olarak oluşturulur. Dosya zaten varsa, sonuçlar dosyanın varolan içeriğine eklenir.

 Komut satırı derleme hataları, **komut** penceresinde ve **Çıkış** penceresinin çözüm Oluşturucu görünümünde görüntülenir. Bu seçenek, katılımsız derlemeler çalıştırıyorsanız ve sonuçları görmeniz gerekiyorsa yararlıdır.

## <a name="example"></a>Örnek
 Bu örnek `MySolution` , dosyasını çalıştırır ve dosyaya hatalar yazar `MyErrorLog.txt` .

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
