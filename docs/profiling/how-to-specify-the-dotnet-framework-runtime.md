---
title: 'Nasıl yapılır: .NET Framework çalışma zamanı belirtin | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e85e1c571ecb900d5ce7ffdecf8e85b8c367de5c
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844140"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Nasıl yapılır: .NET Framework çalışma zamanı belirtin

Sürümü ile [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], uygulamaları, farklı sürümleri kullanılarak oluşturulan modüllerin birleştirilebilen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] çalıştırma. Varsayılan olarak, Visual Studio profil oluşturma araçları uygulama tarafından yüklenen ilk çalışma zamanı profil. Bir uygulamaya Profil Oluşturucu ile başladığınızda ve zaten çalışan bir uygulamaya profil oluşturucu ekleme, profil için çalışma zamanı belirtebilirsiniz.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>.NET Framework çalışma zamanı profili için bir uygulama ile profil oluşturucu başlatılırken belirtmek için

1. İçinde **performans Gezgini**, performans oturumunu sağ tıklayın, **özellikleri**ve ardından **Gelişmiş**.

     **Hedef CLR sürümü** liste kutusunu görüntüler **otomatik** ve sürümleri [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bilgisayarda yüklü olan çalışma zamanı.

2. Aşağıdaki adımlardan birini uygulayın:

    - Profil oluşturmayı istediğiniz CLR sürümü'ı tıklatın.

    - Tıklatın **otomatik** uygulama tarafından yüklenen ilk sürüm profilini.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>.NET Framework çalışma zamanı profili için bir uygulamaya profil oluşturucu eklerken belirtmek için

1. Üzerinde **Çözümle** menüsündeki **profil oluşturucu**, ardından **Attach/Detach**.

2. Üzerinde **profil oluşturucu ekleme işlemi için** iletişim kutusu, profil oluşturmayı istediğiniz işlemi'ı tıklatın.

     **Hedef CLR sürümü** liste kutusu s **otomatik** ve sürümleri [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bilgisayarda yüklü olan çalışma zamanı.

3. Aşağıdaki adımlardan birini uygulayın:

    - Profil oluşturmayı istediğiniz CLR sürümü'ı tıklatın.

    - Tıklatın **otomatik** uygulamaya profil oluşturucu ekler, yüklenen sürüm profilini.