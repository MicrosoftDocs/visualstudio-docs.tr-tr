---
title: VSPackages 'ta güvenlik için en iyi uygulamalar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e73be2af3d24a6a719f353fbd0ab25dbdf86fe09
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012145"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackages içindeki güvenlik için en iyi uygulamalar
Bilgisayarınıza yüklemek için [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] yönetici kimlik bilgilerine sahip bir bağlamda çalıştırıyor olmanız gerekir. Temel güvenlik ve uygulamanın dağıtım birimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [VSPackage](../../extensibility/internals/vspackages.md)' dır. Bir VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , yönetim kimlik bilgileri gerektiren kullanılarak kaydedilmelidir.

 Yöneticiler kayıt defteri ve dosya sistemine yazmak ve herhangi bir kodu çalıştırmak için tam izinlere sahiptir. VSPackage geliştirmek, dağıtmak veya yüklemek için bu izinlere sahip olmanız gerekir.

 Yüklendikten hemen sonra VSPackage tamamen güvenilirdir. VSPackage ile ilişkili bu üst düzey izin nedeniyle, kötü amaçlı bir amaç içeren bir VSPackage 'ı yanlışlıkla yüklemek mümkündür.

 Kullanıcılar, VSPackages 'ı yalnızca güvenilir kaynaklardan yüklediklerinden emin olmalıdır. VSPackages geliştiren şirketlerin, kullanıcının izinsiz değişiklik yapmasını güvence altına almak için, onları kesin olarak adı ve imzalayabilmelidir. VSPackages geliştiren şirketler, herhangi bir güvenlik sorununu değerlendirmek ve düzeltmek üzere Web Hizmetleri ve uzaktan yükleme gibi dış bağımlılıklarını incelemelidir.

 Daha fazla bilgi için bkz. [.NET Framework Için güvenli kodlama yönergeleri](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Ayrıca bkz.
- [Eklenti Güvenliği](/previous-versions/1326zbk3(v=vs.140))
- [DDEX güvenliği](/previous-versions/bb163703(v=vs.140))