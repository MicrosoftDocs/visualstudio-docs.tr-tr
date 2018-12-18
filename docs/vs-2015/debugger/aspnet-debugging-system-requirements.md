---
title: 'ASP.NET hata ayıklama: Sistem gereksinimleri | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16fcebe8ecb5fff974d5df6e2405acca546ea007
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793808"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Hata Ayıklama: Sistem Gereksinimleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu için yazılım ve güvenlik gereksinimlerini açıklar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] hata ayıklama senaryoları:  
  
-   Yerel, hata ayıklamayı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve Web uygulaması aynı bilgisayarda çalışır. Bu senaryo iki sürümü vardır:  
  
    -   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Kod dosya sisteminde yer alıyor.  
  
    -   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Kod, bir IIS Web sitesinde yer alıyor.  
  
-   Uzaktan, içinde hata ayıklama [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir istemci bilgisayarda çalışan ve bir uzak sunucu bilgisayarda çalışan bir Web uygulaması hata ayıklamasına.  
  
## <a name="security-requirements"></a>Güvenlik Gereksinimleri  
 Uzaktan hata ayıklama için yerel ve uzak bilgisayarlar bir etki alanı kurulumu veya bir çalışma grubu kurulum olması gerekir.  
  
 Hata ayıklamak için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi bu işlemde hata ayıklamak için izninizin olması gerekir. Varsayılan olarak, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamaları çalıştırma olarak **ASPNET** kullanıcı. Çalışan işlem olarak çalışıyorsa **ASPNET**, veya as **ağ hizmeti**, hata ayıklamak için yönetici ayrıcalıklarınız olmalıdır.  
  
 Adını [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi senaryo hata ayıklama ve IIS sürümüne göre farklılık gösterir. Daha fazla bilgi için [nasıl yapılır: ASP.NET işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Kullanıcı değiştirebilir, hesap [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] altında çalışan IIS çalıştıran sunucuda machine.config dosyasının düzenleyerek çalışan işlemi. Bunu yapmanın en iyi yolu kullanmaktır **Internet Information Services (IIS) Yöneticisi'ni**. Daha fazla bilgi için [nasıl yapılır: çalışan işlem altında bir kullanıcı hesabı çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Değiştirirseniz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kendi kullanıcı hesabı altında çalışacak şekilde çalışan işlemi IIS çalıştıran sunucuda yönetici olmanız gerekmez.  
  
> [!CAUTION]
>  Değiştirmeden önce [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi farklı bir hesap altında çalıştırmayı göz önünde bulundurun olası sonuçları, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi ele söz konusu hesap altında çalışırken. ASP.NET ve ağ hizmeti kullanıcı hesaplarını işlemi ele, olası hasarı azaltmak çok az izinleriyle çalıştırın. Değiştirmeniz gerekiyorsa [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] büyük izinleri olan bir hesabı altında çalışacak şekilde çalışan işlemi durumdaki potansiyel hasarı büyüktür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Nasıl Yapılır: Bir Kullanıcı Hesabı Altında Çalışan İşlemini Çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md)



