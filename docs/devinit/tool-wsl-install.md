---
title: wsl-install
description: devinit aracı WSL-Install.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 4dff121d7866918d5c30986dc9bd4c3cab039ac5
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672427"
---
# <a name="wsl-install"></a>wsl-install

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`wsl-install`Araç, [Linux için Windows alt sistemi](/windows/wsl/) (WSL) için Linux Distro 'lara yüklemek üzere kullanılır.

> [!IMPORTANT]
> `wsl-install`Araç, Windows üzerinde WSL 2 ' nin zaten etkinleştirilmesini gerektirir. Bazı nedenlerle WSL 2 etkinleştirilmemişse, [WSL yüklemesi belgelerini](https://docs.microsoft.com/windows/wsl/install-win10)takip edebilirsiniz. Gerekli Windows özelliklerini etkinleştirmek için [WindowsFeature-Enable](tool-windowsfeature-enable.md) aracını da kullanabilirsiniz.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                             |
| [**girişinin**](#input)                              | string | Yes      | Yüklemeyi geri çevirme. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.     |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.  |

### <a name="input"></a>Giriş

Dağıtımı yapılan kapsayıcıyı içeren AppX uygulama dağıtım paketi ( `.appx` ) IÇIN URI. URI, arşiv kökünde ya da `.appx` `install.tar.gz` bir iç arşiv içinde tek bir içeren bir arşivi işaret etmelidir `.appx` . Desteklenen destekler arasında şunlar yer alır:

| Distro                          | Kullanılmamışsa                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Borçlu GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE artık 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> ARM Linux Distro 'lara, GitHub codespaces 'de Şu anda desteklenmiyor.

### <a name="additional-options"></a>Ek seçenekler

Birden çok ek seçenek desteklenir:

| Ad                      | Tür      | Gerekli | Değer                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-sürümü             | dize    | No       | Kullanılacak WSL sürümü. Varsayılan değer 2 ' dir.                                                                                                                                  |
| --oluşturma sonrası-komutu     | dize    | No       | Yükleme tamamlandıktan sonra Linux 'un içinde yürütülecek komut. Komut tek bir sözcük olarak biçimlendirilmelidir veya tırnak işaretleri içine alınmalıdır. Varsayılan, komut değildir.  |

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `wsl-install` `input` , ' nin yükleneceğine ilişkin özelliği olarak hata olur.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `wsl-install` `.devinit.json` .

#### <a name="devinitjson-that-will-install-ubuntu-2004"></a>Ubuntu 20,04 ' i yükleyecek .devinit.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command"></a>Ubuntu 20,04 yükleyecek ve oluşturma sonrası bir komut gerçekleştirecek .devinit.js.
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command-that-configures-the-packages-listed"></a>Bu, Ubuntu 20,04 yükleyecek ve listelenen paketleri yapılandıran bir Create a komutu gerçekleştirecek .devinit.js.
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```
