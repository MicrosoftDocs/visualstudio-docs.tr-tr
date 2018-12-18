---
title: -Edit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5588d5dbf86039273854ddc372d1bbe096dad70b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948146"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Mevcut bir örneğini belirtilen dosyayı açar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sözdizimi

```cmd
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Arguments
 `file1`

 İsteğe bağlı. Mevcut bir örneğini açmak için dosyaya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Hiç bir örneği ise [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yoksa, yeni bir örneği bir Basitleştirilmiş pencere düzeni ile oluşturulur ve `file1` yeni bir örneğinde açılmış.

 `file2`

 İsteğe bağlı. Var olan örnekte açmak için bir veya daha fazla ek dosyalar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="remarks"></a>Açıklamalar
 Hiçbir dosya belirtilir ve var olan bir örneği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], var olan örneğinin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odağı alır. Hiçbir dosya belirtilir ve mevcut hiçbir örneği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], yeni bir örneğini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir Basitleştirilmiş pencere düzeni ile oluşturulur.

 Varsa mevcut örneğini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] örneğin kalıcı bir durumda olduğundan, [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md) açık dosya olacak mevcut açık örnek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kalıcı durumdan çıkar.

## <a name="example"></a>Örnek
 Bu örnek dosyayı açar `MyFile.cs` var olan bir örneğini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] veya dosyayı yeni bir örneğini açar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] biri zaten mevcut değilse.

```cmd
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)