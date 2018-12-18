---
title: -LCID (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a97874ae1267677c5055e84650a839068479fc10
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948601"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Metin, para birimi ve diğer değerleri tümleşik geliştirme ortamında (IDE) için kullanılan varsayılan dili ayarlar.

## <a name="syntax"></a>Sözdizimi

```cmd
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Arguments
 `LocaleID` Gerekli. Dilin LCID (yerel ayar kimliği) belirtirsiniz.

## <a name="remarks"></a>Açıklamalar
 IDE yükler ve ortam için varsayılan doğal dili ayarlar. Bu değişiklik oturumları arasında kalıcı ve yansıtılan **uluslararası ayarlar** bölmesinde **ortam** seçeneklerini **seçenekleri** iletişim kutusu IDE'de.

 Belirtilen dil kullanıcının sisteminde kullanılabilir durumda değilse, / LCID anahtarı yok sayıldı.

 Aşağıdaki tabloda LCID'ler tarafından desteklenen dilleri listeler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Dil|LCID|
|--------------|----------|
|ve|2052|
|seçenekleri yerine|1028|
|İngilizce|1033|
|Fransızca|1036|
|Almanca|1031|
|İtalyanca|1040|
|Japonca|1041|
|Korece|1042|
|İspanyolca|3082|

## <a name="example"></a>Örnek
 Bu örnekte, İngilizce kaynak dizelerini IDE'ye yükler.

```cmd
devenv /LCID 1033
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [Uluslararası Ayarlar, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)