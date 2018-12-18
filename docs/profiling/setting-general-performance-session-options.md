---
title: Genel Performans oturumunu ayarlama seçenekleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6c44435f69b5a94433081a518be14f8ffd1756e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834234"
---
# <a name="set-general-performance-session-options"></a>Genel performans oturumunu ayarlama seçenekleri

Toplama yöntemi ve Visual Studio Profil Araçları performans oturumu için profil oluşturma veri adlandırma kuralları ayarlayabilirsiniz **genel** için performans oturumu Özellikleri iletişim kutusu sayfası. Bu iletişim kutusu açmak için **performans Gezgini**performans oturumu sağ tıklayın ve ardından **özellikleri**.

## <a name="choosing-data-collection-methods"></a>Veri toplama metotlarını seçme

Altında seçeneklerden birini seçerek temel koleksiyonu yöntemi ayarlamak **profil oluşturma koleksiyonu**. Aşağıdaki tabloda aşağıdaki seçenekleri açıklanmıştır:

|||
|-|-|
|**Örnekleme**. Örnekleme yöntemi düzenli aralıklarla profil bilgilerini toplar. Bu yöntem çoğu performans araştırmalar başlangıç için önerilen yöntem ve işlemci kullanım sorunları bulmak için kullanışlıdır.|- [Örnekleme kullanarak performans istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**İzleme**. Araçlar yöntemini bir profil oluşturma sırasında modüldeki her giriş, çıkış ve işlevlerin işlev çağrısı kaydeden kod profil oluşturma modülü bir kopyasını içine yerleştirir. Bu yöntem, kodunuzu bir bölümünü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemleri uygulama performansı üzerindeki etkisini anlamak için kullanışlıdır.|- [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Eşzamanlılık**. Eşzamanlılık yöntemi gibi bir iş parçacığı zaman bekler, kodunuzun yürütülmesini engeller serbest bırakılacak Uygulama kaynağı için erişim kilitli her olay için veri toplar. Bu yöntem, çok iş parçacıklı uygulamalar çözümlemek için kullanışlıdır.|- [İş parçacığı ve işlem eşzamanlılık verileri toplama](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Örnekleme ve araç yöntemleri kullanarak, .NET bellek verileri toplayabilirsiniz. Altında veri türünü seçin **.NET bellek profili oluşturma**.

|||
|-|-|
|**.NET nesnesi ayırma bilgilerini topla**. Varsayılan olarak, veri sayısını ve ayrılan nesnelerin boyutunu içerir. Seçin veya etkinleştirin veya .NET bellek verileri toplama devre dışı bırakmak için bu onay kutusunu temizleyin. |- [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Ayrıca .NET nesnesi ömür bilgilerini toplayın**. Bellek nesneleri geri kazanmak için kullanılan çöp toplama kuşakları hakkında veri eklemek için bu onay kutusunu seçin.|- [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Burada, duraklatma, sürdürme ve profil oluşturmayı durdurmak bir uygulamanın profilini başladığınızda bir profil oluşturma oturumu sayfasında görünür.

 ![Profil oluşturma oturumu sayfasında](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Profil oluşturma veri dosyası seçeneklerini ayarlama

|||
|-|-|
|**Rapor**. Varsayılan olarak, profil oluşturma veri (.vsp) dosyasının profillenen uygulamanın adı verilir ve çözüm veya proje klasöründe bulunur. Bir tarih dizesini de adının sonuna eklenir ve artan bir sayı, aksi halde yinelenen adlara sahip olabileceği veri dosyalarına eklenir. Bu seçenekleri değiştirebilirsiniz.|- [Nasıl yapılır: performans veri dosyası adlandırma seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|