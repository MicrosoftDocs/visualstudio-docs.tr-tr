---
title: 'Nasıl yapılır: .NET Framework çalışma zamanını belirtin. | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c62b70816ac17789a4aa236e5abcca6832f7359
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749307"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Nasıl yapılır: .NET Framework çalışma zamanını belirtin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sürümüyle [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], uygulamalar oluşan farklı sürümleri kullanılarak derlenmiş modüllerin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] çalışma zamanı. Varsayılan olarak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] profil oluşturma araçları, uygulama tarafından yüklenen ilk çalışma zamanı profili. Bir uygulamaya Profil Oluşturucu ile başladığınızda ve profil oluşturucu zaten çalışan bir uygulamaya ekleme yaptığınızda profil için çalışma zamanı belirtebilirsiniz.  
  
 **Gereksinimler**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Profil Oluşturucu ile bir uygulama başlatma sırasında .NET Framework çalışma zamanı profili belirtmek için  
  
1.  İçinde **performans Gezgini**, performans oturumu sağ tıklayın, **özellikleri**ve ardından **Gelişmiş**.  
  
     **Hedef CLR sürümü** liste kutusu görüntüler **otomatik** sürümleri [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bilgisayarda yüklü çalışma zamanı.  
  
2.  Aşağıdaki adımlardan birini uygulayın:  
  
    -   Profil oluşturmak istediğiniz CLR sürümünü tıklayın.  
  
    -   Tıklayın **otomatik** profilini uygulama tarafından yüklenen ilk sürümü.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Bir uygulamaya profil oluşturucu iliştirme ne zaman .NET Framework çalışma zamanı profili belirtmek için  
  
1.  Analiz menüsünde için Profiler gelin ve iliştir/Ayır'ı tıklatın.  
  
2.  İşlem iletişim kutusu için ekleme Profiler hakkında profil oluşturmak istediğiniz işleme tıklayın.  
  
     **Hedef CLR sürümü** liste kutusu s **otomatik** sürümleri [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bilgisayarda yüklü çalışma zamanı.  
  
3.  Aşağıdaki adımlardan birini uygulayın:  
  
    -   Profil oluşturmak istediğiniz CLR sürümünü tıklayın.  
  
    -   Tıklayın **otomatik** uygulamaya profil oluşturucu ekler, yüklü sürümle profil için.



