---
title: 'ASP.NET hata ayıklama: Sistem gereksinimleri | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 71b6cbc3f523b8f21b21b0e69b1d6e45e23acb0c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915353"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Hata Ayıklama: Sistem Gereksinimleri
Bu konu için yazılım ve güvenlik gereksinimlerini açıklar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hata ayıklama senaryoları:  
  
- Yerel, hata ayıklamayı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve Web uygulaması aynı bilgisayarda çalışır. Bu senaryo iki sürümü vardır:  
  
  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Kod dosya sisteminde yer alıyor.  
  
  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Kod, bir IIS Web sitesinde yer alıyor.  
  
- Uzaktan, içinde hata ayıklama [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir istemci bilgisayarda çalışan ve bir uzak sunucu bilgisayarda çalışan bir Web uygulaması hata ayıklamasına.  
  
## <a name="security-requirements"></a>Güvenlik Gereksinimleri  
 Uzaktan hata ayıklama için yerel ve uzak bilgisayarlar bir etki alanı kurulumu veya bir çalışma grubu kurulum olması gerekir.  
  
 Hata ayıklamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi (bir uygulama havuzu tarafından barındırılan), bu işlemde hata ayıklamak için izni olmalıdır. Varsayılan olarak, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] IIS 6.0 öncesinde uygulamaları çalıştırma olarak **ASPNET** kullanıcı. IIS 6.0 ve IIS 7. 0'da, **ağ hizmeti** varsayılan hesaptır. Çalışan işlem olarak çalışıyorsa **ASPNET**, veya as **ağ hizmeti**, hata ayıklamak için yönetici ayrıcalıklarınız olmalıdır.

 > [!IMPORTANT]
 > Windows Server 2008 R2 ile başlayarak, kullanılmasını öneririz [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) her uygulama havuzunun kimliği olarak.
  
 Adını [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi senaryo hata ayıklama ve IIS sürümüne göre farklılık gösterir. Daha fazla bilgi için [nasıl yapılır: ASP.NET işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Kullanıcı değiştirebilir, hesap [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] altında çalışan IIS çalıştıran sunucuda machine.config dosyasının düzenleyerek çalışan işlemi. Bunu yapmanın en iyi yolu kullanmaktır **Internet Information Services (IIS) Yöneticisi'ni**. Daha fazla bilgi için [nasıl yapılır: çalışan işlem altında bir kullanıcı hesabı çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Değiştirirseniz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kendi kullanıcı hesabı altında çalışacak şekilde çalışan işlemi IIS çalıştıran sunucuda yönetici olmanız gerekmez.  
  
> [!CAUTION]
>  Değiştirmeden önce [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi farklı bir hesap altında çalıştırmayı göz önünde bulundurun olası sonuçları, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi ele söz konusu hesap altında çalışırken. ASP.NET ve ağ hizmeti kullanıcı hesaplarını işlemi ele, olası hasarı azaltmak çok az izinleriyle çalıştırın. Değiştirmeniz gerekiyorsa [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] büyük izinleri olan bir hesabı altında çalışacak şekilde çalışan işlemi durumdaki potansiyel hasarı büyüktür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Nasıl Yapılır: Bir Kullanıcı Hesabı Altında Çalışan İşlemini Çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md)