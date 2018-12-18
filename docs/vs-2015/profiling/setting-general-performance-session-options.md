---
title: Genel Performans oturumunu ayarlama seçenekleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d63c4a255d972b16bd7d9fda3d6c5a0d27978595
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808433"
---
# <a name="setting-general-performance-session-options"></a>Genel Performans Oturumunu Ayarlama Seçenekleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toplama yöntemi ve profil oluşturma veri adlandırma kuralları için ayarlayabileceğiniz bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profil Araçları performans oturum **genel** için performans oturumu Özellikleri iletişim kutusu sayfası. Bu iletişim kutusu açmak için **performans Gezgini**performans oturumu sağ tıklayın ve ardından **özellikleri**.  
  
 **Gereksinimler**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="choosing-data-collection-methods"></a>Veri toplama metotlarını seçme  
 Altında seçeneklerden birini seçerek temel koleksiyonu yöntemi ayarlamak **profil oluşturma koleksiyonu**. Aşağıdaki tabloda aşağıdaki seçenekleri açıklanmıştır:  
  
|||  
|-|-|  
|**Örnekleme**. Örnekleme yöntemi düzenli aralıklarla profil bilgilerini toplar. Bu yöntem çoğu performans araştırmalar başlangıç için önerilen yöntem ve işlemci kullanım sorunları bulmak için kullanışlıdır.|-   [Örnekleme kullanarak performans istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**İzleme**. Araçlar yöntemini bir profil oluşturma sırasında modüldeki her giriş, çıkış ve işlevlerin işlev çağrısı kaydeden kod profil oluşturma modülü bir kopyasını içine yerleştirir. Bu yöntem, kodunuzu bir bölümünü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemleri uygulama performansı üzerindeki etkisini anlamak için kullanışlıdır.|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Eşzamanlılık**. Eşzamanlılık yöntemi gibi bir iş parçacığı zaman bekler, kodunuzun yürütülmesini engeller serbest bırakılacak Uygulama kaynağı için erişim kilitli her olay için veri toplar. Bu yöntem, çok iş parçacıklı uygulamalar çözümlemek için kullanışlıdır.|-   [İş parçacığı ve işlem eşzamanlılık verileri toplama](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 Örnekleme ve araç yöntemleri kullanarak, .NET bellek verileri toplayabilirsiniz. Altında veri türünü seçin **.NET bellek profili oluşturma**.  
  
|||  
|-|-|  
|**.NET nesnesi ayırma bilgilerini topla**. Varsayılan olarak, veri sayısını ve ayrılan nesnelerin boyutunu içerir. Seçin veya etkinleştirin veya .NET bellek verileri toplama devre dışı bırakmak için bu onay kutusunu temizleyin.<br /><br /> **Ayrıca .NET nesnesi ömür bilgilerini toplayın**. Bellek nesneleri geri kazanmak için kullanılan çöp toplama kuşakları hakkında veri eklemek için bu onay kutusunu seçin.|-   [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Burada, duraklatma, sürdürme ve profil oluşturmayı durdurmak bir uygulamanın profilini başladığınızda bir profil oluşturma oturumu sayfasında görünür.  
  
 ![Profil oluşturma oturumu sayfasında](../profiling/media/prof-profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-datra-file-options"></a>Profil oluşturma Datra dosya seçeneklerini ayarlama  
  
|||  
|-|-|  
|**Rapor**. Varsayılan olarak, profil oluşturma veri (.vsp) dosyasının profillenen uygulamanın adı verilir ve çözüm veya proje klasöründe bulunur. Bir tarih dizesini de adının sonuna eklenir ve artan bir sayı, aksi halde yinelenen adlara sahip olabileceği veri dosyalarına eklenir. Bu seçenekleri değiştirebilirsiniz.|-   [Nasıl yapılır: performans veri dosyası adlandırma seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|



