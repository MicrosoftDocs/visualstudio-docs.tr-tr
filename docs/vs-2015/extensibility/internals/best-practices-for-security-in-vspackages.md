---
title: Vspackage'larda güvenlik için en iyi uygulamalar | Microsoft Docs
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
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 49285b29c00f9f8a50232c2eaa2eb82a65cb71e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756237"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackage’larda Güvenlik için En İyi Yöntemler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yüklenecek [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] bilgisayarınızda yönetici kimlik bilgilerine sahip bir bağlamda çalıştırıyor olmalısınız. Güvenliği ve dağıtımı temel birimini bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uygulama [VSPackages](../../extensibility/internals/vspackages.md). Bir VSPackage'ı kullanarak kaydedilmelidir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], gerektiren yönetici kimlik bilgileri.  
  
 Yöneticiler, kayıt defteri ve dosya sistemine yazma ve herhangi bir kodu çalıştırmak için tam izinleri vardır. Geliştirme, dağıtma veya bir VSPackage'ı yüklemek için bu izinlere sahip olmalıdır.  
  
 VSPackage yüklendikten hemen sonra tam olarak güvenilirdir. VSPackage'ı ile ilişkili izin nedeniyle bu yüksek düzeyde farkında olmadan kötü amaçlı olan bir VSPackage'ı yüklemek mümkündür.  
  
 Kullanıcılar VSPackages yalnızca güvenilir kaynaklardan gelen yükleme emin olmanız gerekir. VSPackage geliştirme şirketler kesin ad ve oturumunu, kullanıcı söz konusu oynama güvence altına almak için engellenir. VSPackage geliştirme şirketler, web hizmetleri ve değerlendirmek ve güvenlik sorunları düzeltmek için uzaktan yükleme gibi dış bağımlılıklarını incelemeniz gerekir.  
  
 Daha fazla bilgi için .NET Framework için güvenli kodlama kılavuzları bakın ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eklenti güvenliği](http://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX güvenlik](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)

