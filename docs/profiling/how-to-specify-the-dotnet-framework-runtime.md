---
title: .NET Framework çalışma zamanını belirtin | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 27846b448f7e0667004bd25d24bd447fe43f8e51
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851131"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Nasıl yapılır: .NET Framework çalışma zamanını belirtin

.NET Framework 4 sürümünde, uygulamalar .NET Framework çalışma zamanının farklı sürümleri kullanılarak oluşturulmuş modüllerden oluşabilir. Varsayılan olarak, Visual Studio Profil Oluşturma Araçları uygulama tarafından yüklenen ilk çalışma zamanını profili. Profil Oluşturucu ile bir uygulama başlattığınızda ve zaten çalışan bir uygulamaya profil oluşturucu iliştirçalıştığınızda, profil oluşturma zamanını belirtebilirsiniz.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Profil Oluşturucu ile bir uygulama başlatılırken .NET Framework çalışma zamanını belirlemek için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın, **Özellikler**' e ve ardından **Gelişmiş**' e tıklayın.

     **Hedef CLR sürümü** liste kutusu, bilgisayarda yüklü olan .NET Framework çalışma zamanının **Otomatik** ve sürümlerini görüntüler.

2. Aşağıdaki adımlardan birini uygulayın:

    - Profil eklemek istediğiniz CLR sürümüne tıklayın.

    - Uygulama tarafından yüklenen ilk sürümü profil için **Otomatik** ' e tıklayın.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Profil oluşturucuyu bir uygulamaya eklerken kullanılacak .NET Framework çalışma zamanını belirtmek için

1. **Çözümle** menüsünde **Profil Oluşturucu**' nın üzerine gelin ve **Ekle/ayır**' a tıklayın.

2. **Işleme profil oluşturucu Ekle** iletişim kutusunda, profil eklemek istediğiniz işleme tıklayın.

     **Hedef CLR sürümü** liste kutusu **Otomatik** ve bilgisayarda yüklü olan .NET Framework çalışma zamanının sürümleri.

3. Aşağıdaki adımlardan birini uygulayın:

    - Profil eklemek istediğiniz CLR sürümüne tıklayın.

    - Profil Oluşturucu uygulamaya iliştirayarlandığında yüklenen sürümü profil için **Otomatik** ' e tıklayın.
