---
title: VSPackage geliştirme için Devenv komut satırı anahtarları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8fd305133f913877f8d4ad4808a8c4efcab52af4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847064"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage geliştirme için Devenv komut satırı anahtarları
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yürütülürken komut satırından görevlerini otomatikleştirmek geliştiricilerinin sağlayan *devenv.exe*, dosyayı Visual Studio tümleşik geliştirme ortamı (IDE) başlatır.  

 Görevler aşağıdakileri içerir:  

-   IDE dışında tasarlanmış yapılandırmalardan uygulamalarda dağıtılıyor.  

-   Otomatik olarak önayarını kullanarak proje oluşturma, derleme ayarları veya hata ayıklama yapılandırması.  

-   IDE dışında tüm gelen belirli yapılandırmalar, IDE'de yükleniyor. Buna ek olarak, IDE başlatma sırasında özelleştirebilirsiniz.  

## <a name="guidelines-for-switches"></a>Anahtarlar için yönergeler  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] belgeler, kullanıcı düzeyi devenv komut satırı anahtarları açıklar. Daha fazla bilgi için [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md). Devenv VSPackage geliştirme, dağıtım ve hata ayıklama için yararlı olan ek komut satırı anahtarları da destekler.  


| Komut satırı anahtarı | Açıklama |
|---------------------| - |
| safemode | Başlatan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] güvenli modda, yalnızca varsayılan IDE ve Hizmetleri Yükleniyor. Ne zaman yüklenmesini safemode anahtarı tüm üçüncü taraf VSPackages engeller [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] böylece kararlı yürütme sağlamaya başlar.<br /><br /> Bu anahtar hiçbir bağımsız değişkeni alır. |
| / resetskippkgs | Ardından Tümünü Atla sorunlu VSPackage yükleme kaçınmak isteyen kullanıcılar tarafından eklenen yükleme seçenekleri temizler başlatır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. SkipLoading etiketinin varlığını VSPackage yüklenmesini devre dışı bırakır. Etiket temizleme VSPackage yükleme yeniden etkinleştirir.<br /><br /> Bu anahtar hiçbir bağımsız değişkeni alır. |
| /rootsuffix | Başlar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] alternatif bir konuma kullanarak. Aşağıdaki komutu tarafından oluşturulan kısayol tarafından çalıştırılan [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] yükleyicisi:<br /><br /> Devenv /RootSuffix üs<br /><br /> Bu durumda, exp, 10.0 yerine örneğin 10.0Exp belirli bir soneki olan bir konum belirtir. Deneysel örneği örneğini listesinden bir VSPackage hatalarını ayıklamanızı sağlar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kod yazmak için kullanmakta olduğunuz.<br /><br /> Bu anahtar VSRegEx.exe kullanarak oluşturduğunuz bir konumu tanımlayan bir dize alabilir. Daha fazla bilgi için [deneysel örneğinde](../extensibility/the-experimental-instance.md). |
| /Splash | Gösterir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zamanki giriş ekranı ve ardından ana IDE göstermeden önce bir ileti kutusu gösterir. İleti kutusu incelemek için bir VSPackage ürün simgesi, örneğin denetlemek için giriş ekranı sağlar.<br /><br /> Bu anahtar hiçbir bağımsız değişkeni alır. |

## <a name="see-also"></a>Ayrıca bkz.  
 [Komut satırı anahtarları ekleme](../extensibility/adding-command-line-switches.md)   
 [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)