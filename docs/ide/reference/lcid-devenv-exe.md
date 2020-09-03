---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cabbf36adb5019543b3cfb72b0b0e56976517d2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557940"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Metin, para birimi ve IDE içindeki diğer değerler için kullanılan varsayılan dili ayarlar.

## <a name="syntax"></a>Söz dizimi

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Bağımsız değişkenler

- *LocaleID*

  Gereklidir. Belirttiğiniz dilin Yerel ayar tanıtıcısı (LCıD).

## <a name="remarks"></a>Açıklamalar

IDE 'yi yükler ve ortam için varsayılan doğal dili ayarlar. Bu değişiklik oturumlar arasında kalıcıdır ve IDE, bu değişikliği **Araçlar**  >  **Seçenekler**  >  **ortamı**  >  **Uluslararası ayarlar**  >  **dil** kutusunda gösterir.

Belirtilen dil sisteminizde yoksa, `/LCID` anahtar yok sayılır.

Aşağıdaki tabloda, Visual Studio tarafından desteklenen dillerin LCID 'Ler listelenmiştir.

|Dil|LCID|
|--------------|----------|
|Basitleştirilmiş Çince|2052|
|Geleneksel Çince|1028|
|Çekçe|1029|
|İngilizce|1033|
|Fransızca|1036|
|Almanca|1031|
|İtalyanca|1040|
|Japonca|1041|
|Korece|1042|
|Lehçe|1045|
|Portekizce (Brezilya)|1046|
|Rusça|1049|
|İspanyolca|3082|
|Türkçe|1055

## <a name="example"></a>Örnek

Bu örnek, IDE 'yi Ingilizce kaynak dizeleri ile yükler.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [Uluslararası Ayarlar, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)
