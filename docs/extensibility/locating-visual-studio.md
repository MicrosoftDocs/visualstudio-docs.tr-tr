---
title: Visual Studio'yu bulma | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65b0b8dfcc42cfcf80fc24f0c844469b77734e9c
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495394"
---
# <a name="locate-visual-studio"></a>Visual Studio bulun

Visual Studio 2017'den itibaren aynı sürümü veya hatta sürümü birden çok örneğini yükleyebilirsiniz. Bu, önceki yüklemede korurken yeni işlevleri birincil geliştirme makinenizde izlemek istediğinizde yararlıdır. Bu değişiklikler nedeniyle örneği bulmak için kullanabileceğiniz tek bir ortam değişkeninin veya kayıt defteri değeri yoktur. Bunun yerine kullanabileceğiniz bir [COM sorgu API'si](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) Uzantınız için ilgili ölçütlere göre örnekleri bulunamadı.

NuGet paketlerini yerel ve yönetilen kod için kullanılabilir olan hızlı, salt okunur bir API budur.

| Kod | Paket |
| ---- | --- |
| Yerel | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Yönetilen | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Bir yolu veya geçerli işlem verilen tek bir örneği bulun veya tüm örnekleri numaralandırır. Bkz: [örneklerimizi](https://github.com/Microsoft/vs-setup-samples) tam örnekler nasıl Visual Studio bulun.

## <a name="tools"></a>Araçlar

Visual Studio ve diğer araçları, derleme ortamları, PowerShell betikleri, yükleyiciler ve daha fazla senaryo bulmak için doğrudan kullanabilir veya kendi komut dosyalarınızı birlikte yeniden açık kaynak araçlar vardır.

| Proje | Açıklama |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Yayın veya yayın öncesi sürüm, hangi ürünü yüklü olduğundan ve hangi iş yüklerini yüklü gibi ölçütlerine uyan örneklerini bulmak için yerel yürütülebilir tek dosya. Ayrıca, daha az bilgi, Visual Studio 2017 için ve döndürülmesine rağmen Visual Studio 2010 ve sonraki sürümleri, bulma destekler. Bkz: [wiki](https://github.com/Microsoft/vswhere/wiki) örnekler. |
| [VSSetup cmdlet'leri](https://github.com/Microsoft/vssetup.powershell) | Desteklenen PowerShell cmdlet'leri 2.0 ve üzeri sürümlerde, aynı ölçütüne göre örneklerini bulmak için kullanabileceğiniz Zengin bilgiler nesneler olarak iade _vswhere_ ve örnekleri hakkında daha fazla özellikleri bulur. Bkz: [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) örnekler. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Otomatik olarak bulur _Vsıxınstaller_ ve yüklemek için komut satırı aracılığıyla başarılı bir **.vsix* dosya. Bu özellik doğrudan sorgu API desteği olmayan yükleyicileri yararlı olabilir. Bkz: [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) örnekler. |

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 Kurulum değişiklikler](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup/)
