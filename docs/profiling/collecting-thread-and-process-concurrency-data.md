---
title: İş parçacığı ve işlem eşzamanlılık verileri toplama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8ce2c1d7a28eff441cbf3a95e8f9df644789e70
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775564"
---
# <a name="collect-thread-and-process-concurrency-data"></a>İş parçacığı ve işlem eşzamanlılık verileri toplama

Visual Studio profil oluşturma araçları eşzamanlılık profili oluşturma yöntemi, bir işlev bir kaynağa erişim için beklenecek profillenen uygulamanın neden olan her eşitleme olay hakkında bilgiler içeren kaynak Çekişme verisi toplamanıza olanak tanır.

Aşağıdaki yordamlardan birini kullanarak profili oluşturma yöntemi eşzamanlılık belirtebilirsiniz:

- Profil Oluşturma Sihirbazı'nın ilk sayfasında, tıklayın **eşzamanlılık**
- Üzerinde **genel** sayfası için performans oturumu Özellikleri iletişim kutusu tıklayın **eşzamanlılık**.
- Üzerinde **performans Gezgini** araç penceresindeki **yöntemi** listesinde **eşzamanlılık**.

## <a name="common-tasks"></a>Ortak görevler

Ek seçenekler belirtebilirsiniz _performans oturumu_**özellik sayfaları** performans oturumunun iletişim kutusu. Bu iletişim kutusunu açmak için:

- İçinde **performans Gezgini**performans oturumu adına sağ tıklayın ve ardından **özellikleri**.

Aşağıdaki tabloda görevler belirleyebilirsiniz seçenekleri açıklanmıştır _performans oturumu_**özellik sayfaları** eşzamanlılık metodu kullanarak profil olduğunda iletişim kutusu.

|Görev|İlgili içerik|
|----------|---------------------|
|Üzerinde **genel** sayfasında, oluşturulan profil oluşturma veri (.vsp) dosyasının adlandırma ayrıntıları belirtin.|- [Nasıl yapılır: performans veri dosyası adlandırma seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|Üzerinde **başlatma** sayfasında, kod çözümünüz içinde birden çok .exe projeniz varsa başlatmak için bir uygulama belirtin.|- [Nasıl yapılır: başlatmak için ikili dosya belirtme](../profiling/how-to-specify-the-binary-to-start.md)|
|Üzerinde **katman etkileşim** sayfasında, profil oluşturma çalışması için ADO.NET çağrı veri ekleyin.|- [Katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)|
|Üzerinde **Windows sayaçları** sayfasında işaretleri olarak profil oluşturma verilerini eklemek için bir veya daha fazla işletim sistemi performans sayaçları belirtin.|- [Nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)|
|Üzerinde **Gelişmiş** sayfasında, uygulama modüllerinizi birden çok sürümü kullanıyorsanız, .NET Framework çalışma zamanı profili sürümünü belirtin. Varsayılan olarak yüklenen ilk sürüm profil oluşturulan.|- [Nasıl yapılır: .NET Framework çalışma zamanını belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|