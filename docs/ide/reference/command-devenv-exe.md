---
title: -Command (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2ee6f1166a543cc3dc85dfb62d19d1c5b194a16
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948172"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Başlatıldıktan sonra belirtilen komutu yürütür [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE).

## <a name="syntax"></a>Sözdizimi

```cmd
devenv /command CommandName
```

## <a name="arguments"></a>Arguments
 `CommandName` Gerekli. Tam adı bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut ya da çift tırnak işareti içine alınmış, diğer ad. Komut ve diğer ad sözdizimi hakkında daha fazla bilgi için bkz: [Visual Studio komutları](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Açıklamalar
 Başlangıç tamamlandıktan sonra IDE adlandırılmış komutu yürütür. Bu anahtarı kullanırsanız, IDE aşağıdaki dotnetclıtools'u görüntülemiyor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başlangıcında başlangıç sayfası.

 Bir eklenti bir komut sunarsa, komut satırından eklentiyi başlatmak için bu anahtarı kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: denetim eklentileri kullanarak Eklenti Yöneticisi](https://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Örnek
 Bu örnek başlatır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve makro açık sık kullanılan dosyaları otomatik olarak çalıştırır.

```cmd
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)