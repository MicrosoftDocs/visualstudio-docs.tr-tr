---
title: VSPackage geliştirme için Devenv komut satırı anahtarları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97900d5d23fae8f097ce5f2951f9fb13866f2a1e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749134"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage Geliştirme için Devenv Komut Satırı Anahtarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] geliştiricilerin devenv.exe, Visual Studio tümleşik geliştirme ortamı (IDE) başlatan dosyanın yürütülürken komut satırından görevleri otomatikleştirmenize olanak tanır.  
  
 Görevler aşağıdakileri içerir:  
  
-   IDE dışında tasarlanmış yapılandırmalardan uygulamalarda dağıtılıyor.  
  
-   Otomatik olarak önayarını kullanarak proje oluşturma, derleme ayarları veya hata ayıklama yapılandırması.  
  
-   IDE dışında tüm gelen belirli yapılandırmalar, IDE'de yükleniyor. Buna ek olarak, IDE başlatma sırasında özelleştirebilirsiniz.  
  
## <a name="guidelines-for-switches"></a>Anahtarlar için yönergeler  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belgeler, kullanıcı düzeyi devenv komut satırı anahtarları açıklar. Daha fazla bilgi için [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md). Devenv VSPackage geliştirme, dağıtım ve hata ayıklama için yararlı olan ek komut satırı anahtarları da destekler.  
  
|Komut satırı anahtarı|Açıklama|  
|--------------------------|-----------------|  
|safemode|Başlatan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] güvenli modda, yalnızca varsayılan IDE ve Hizmetleri Yükleniyor. Ne zaman yüklenmesini safemode anahtarı tüm üçüncü taraf VSPackages engeller [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] böylece kararlı yürütme sağlamaya başlar.<br /><br /> Bu anahtar hiçbir bağımsız değişkeni alır.|  
|/ resetskippkgs|Ardından Tümünü Atla sorunlu VSPackage yükleme kaçınmak isteyen kullanıcılar tarafından eklenen yükleme seçenekleri temizler başlatır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. SkipLoading etiketinin varlığını VSPackage yüklenmesini devre dışı bırakır. Etiket temizleme VSPackage yükleme yeniden etkinleştirir.<br /><br /> Bu anahtar hiçbir bağımsız değişkeni alır.|  
|/rootsuffix|Başlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] alternatif bir konuma kullanarak. Aşağıdaki komutu tarafından oluşturulan kısayol tarafından çalıştırılan [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] yükleyicisi:<br /><br /> Devenv /RootSuffix üs<br /><br /> Bu durumda, exp, 10.0 yerine örneğin 10.0Exp belirli bir soneki olan bir konum belirtir. Deneysel örneği örneğini listesinden bir VSPackage hatalarını ayıklamanızı sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kod yazmak için kullanmakta olduğunuz.<br /><br /> Bu anahtar VSRegEx.exe kullanarak oluşturduğunuz bir konumu tanımlayan bir dize alabilir. Daha fazla bilgi için [deneysel örneğinde](../extensibility/the-experimental-instance.md).|  
|/Splash|Gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zamanki giriş ekranı ve ardından ana IDE göstermeden önce bir ileti kutusu gösterir. İleti kutusu incelemek için bir VSPackage ürün simgesi, örneğin denetlemek için giriş ekranı sağlar.<br /><br /> Bu anahtar hiçbir bağımsız değişkeni alır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut satırı anahtarları ekleme](../extensibility/adding-command-line-switches.md)   
 [Devenv Komut Satırı Anahtarları](../ide/reference/devenv-command-line-switches.md)

