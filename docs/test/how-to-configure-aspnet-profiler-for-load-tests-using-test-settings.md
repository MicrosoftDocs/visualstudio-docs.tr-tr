---
title: Yük testleri için ASP.NET Profiler'ı yapılandırma
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 197a6c4a743f5f30e060950413b7e2214fb91b36
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068428"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Nasıl yapılır: Visual Studio'da test ayarlarını kullanarak yük testleri için ASP.NET profil oluşturucuyu yapılandırma

ASP.NET Profil Oluşturucu bilgi toplamak için ASP.NET profiler tanılama veri bağdaştırıcısı'nı kullanabilirsiniz. Bu tanılama veri bağdaştırıcısı, ASP.NET uygulamaları için performans verilerini toplar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Bu tanılama veri bağdaştırıcısı Microsoft Test Yöneticisi'ni kullanarak çalıştırılan testler için kullanılamaz. ASP.NET Profiler tanılama bağdaştırıcısı, Visual Studio Enterprise gerektiren bir yalnızca, Web siteleri kullanan yük testleriyle kullanabilirsiniz.

ASP.NET profiler tanılama veri bağdaştırıcısı, bir yük testi çalıştırdığınızda, uygulama katmanından ASP.NET Profil Oluşturucu verileri toplamanıza olanak tanır. Uzun yük testleri, örneğin, bir saatten daha uzun yük testleri için profil oluşturucu çalıştırmamanız gerekir. Profil oluşturucu dosyası büyüyebilir olmasıdır belki de yüz megabayt. Bunun yerine, ayrıntılı performans sorunlarını tanılama avantajı hala erişmenizi sağlayan ASP.NET profil oluşturucuyu kullanarak kısa yük testleri çalıştırın.

> [!NOTE]
> ASP.NET profiler tanılama veri bağdaştırıcısı Internet Information Services (IIS) işleminin profilini. Bu nedenle, bir geliştirme web sunucusuna karşı çalışmaz. Yük testinizde Web sitesinin profilini çıkarmak için IIS'in çalıştığı makineye bir test aracısı yüklemek zorunda. Test aracısı yük oluşturmayacak ancak yalnızca koleksiyon için bir aracı olacak. Daha fazla bilgi için [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

Daha fazla bilgi için [nasıl yapılır: Dağıtılmış yük testi için bir test ayarı oluşturmanız](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Test ayarlarınız için ASP.NET Profiler'ı yapılandırma

Bu yordamdaki adımları gerçekleştirmeden önce Visual Studio'dan test ayarlarınızı açmalı ve seçmeniz gerekir **veri ve tanılama** sayfası.

1.  ASP.NET Profil Oluşturucu verileri toplamak için kullanılacak rolü seçin.

    > [!WARNING]
    > Bu rol, bir web sunucusu olmalıdır.

2.  Seçin **ASP.NET Profiler** ASP.NET profil oluşturma verisi toplamayı etkinleştirmek ve ardından **yapılandırma**.

     ASP.NET profil oluşturma veri koleksiyonu yapılandırmak için iletişim kutusu görüntülenir.

3.  İçinde **Profiler örnekleme aralığı**, ASP.NET profil oluşturma örnekleri alma arasında beklenecek döngüleri saat kaç durdurulmamış CPU gösteren bir değer girin.

4.  Katman etkileşim profili oluşturma'yı etkinleştirmek için seçin **Katman etkileşimi profil oluşturmayı etkinleştir**.

     Katman etkileşim profili oluşturma, her bir yapıt için web sunucusuna gönderilen istek sayısını sayar (örneğin, *MyPage.aspx* veya *CompanyLogo.gif*) ve her isteğe hizmet vermek için geçen süre. Ayrıca, katman etkileşim profili oluşturma ve hangi ADO.NET bağlantı sayfası isteğin bir parçası olarak kullanılan kaç sorguları ve saklı yordam çağrılarını bu isteği hizmet parçası olarak dahil edilen toplar.

     İki farklı ayarlar, zamanlama bilgilerinin toplanır:

    -   Her web isteğini bakım için zamanlama bilgileri (Min, Max, ortalama ve toplam).

    -   Her sorguyu yürütmek için zamanlama bilgileri (Min, Max, ortalama ve toplam).

Bir test ayarında yapılandırılan ASP.NET profiler tanılama veri bağdaştırıcısı ile ASP.NET profil oluşturma ASP.NET web uygulamanızı şirket verilerini toplayabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgileri Topla](../test/collect-diagnostic-information-using-test-settings.md)
- [Nasıl yapılır: Dağıtılmış yük testi için bir test ayarı oluşturun](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)