---
title: Bir bulut hizmetinin performansını test etme | Microsoft Docs
description: Visual Studio profil oluşturucu kullanılarak bir bulut hizmetinin performansını test etme
author: mikejo5000
manager: douge
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 25b60e5e4072a0523d17082a5c5646e5bb1ade6a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003449"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Bulut hizmetinin performansını test etme
## <a name="overview"></a>Genel Bakış
Aşağıdaki yollarla bir bulut hizmetinin performansını test edebilirsiniz:

* Azure Tanılama, istekler ve bağlantılar hakkında bilgi toplamak ve hizmeti bir müşteri açısından nasıl çalıştığını gösteren site istatistiklerini gözden geçirmek için kullanın. Kullanmaya başlamak için bkz. [Azure bulut Hizmetleri ve sanal makineler için tanılamayı yapılandırma](http://go.microsoft.com/fwlink/p/?LinkId=623009).
* Visual Studio profil oluşturucu hizmeti nasıl çalışır hesaplama yönlerini derinlemesine analizini almak için kullanın. Bu konuda açıklandığı gibi bir hizmet, Azure'da çalışan performansını ölçmek için profil oluşturucu kullanabilirsiniz. Bir hizmet yerel olarak bir işlem öykünücüsünde çalışır gibi performansını ölçmek için profil oluşturucu kullanma hakkında daha fazla bilgi için bkz: [Visual Studio ProfilerişlemöykünücüsükullanarakbirAzurebuluthizmetiyerelolarakperformansınıtest](http://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>Performans sınama yöntemi seçme
### <a name="use-azure-diagnostics-to-collect"></a>Azure Tanılama verileri toplamak için kullanın:
* Web sayfaları veya istekler ve bağlantılar gibi Hizmetleri istatistikleri.
* Rolleri, rol ne sıklıkta yeniden gibi istatistikleri.
* Genel bir çalışan rolü gibi çöp toplayıcı geçen süreyi veya bellek yüzdesini, bellek kullanımı hakkında bilgi ayarlayın.

### <a name="use-the-visual-studio-profiler-to"></a>Visual Studio profil oluşturucu için kullanın:
* Hangi işlevlerin en uzun süre yürütülen belirleyin.
* Her bir işlem bakımından yoğun programın parçası süresini ölçün.
* Bir hizmeti iki sürümü için ayrıntılı porovnat sestavy výkonu
* Bellek ayırma bireysel bellek ayırmaları düzeyi daha ayrıntılı analiz edin.
* Eşzamanlılık sorunları çok iş parçacıklı kod analiz edin.

Profil oluşturucuyu kullandığınızda, bir bulut hizmeti yerel olarak veya azure'da çalıştırıldığında veri toplayabilir.

### <a name="collect-profiling-data-locally-to"></a>İçin profil oluşturma verilerini yerel olarak toplamak:
* Bir bölümü bir bulut hizmetinin performansını test etme, gerçekçi bir benzetim yapılmış yükleme gerektirmez belirli bir çalışan rolü yürütme gibi.
* Yalıtım, denetlenen koşullarda bir bulut hizmetinin performansını test.
* Azure'a dağıtmadan önce bir bulut hizmetinin performansını test edin.
* Özel bir bulut hizmetinin performansını var olan dağıtımları etkilemeden test edin.
* Azure'da çalıştırmak için ücret ödemeden hizmetinin performansını test edin.

### <a name="collect-profiling-data-in-azure-to"></a>Azure için profil oluşturma verilerini toplama:
* Sanal ya da gerçek bir yük altında bir bulut hizmetinin performansını test edin.
* Bu konuda daha sonra açıklandığı gibi profil oluşturma verileri toplama araçları yöntemini kullanın.
* Hizmet üretim ortamında çalıştığında olarak aynı ortamda hizmetinin performansını test.

Genellikle bir yük testi normal altındaki bulut Hizmetleri veya stres koşullarında benzetimini yapın.

## <a name="profiling-a-cloud-service-in-azure"></a>Azure'daki bir bulut hizmeti profili oluşturma
Bulut hizmetinizi Visual Studio'dan yayımladığınızda, hizmetin profilini ve istediğiniz bilgileri sağlamak için profil oluşturma ayarları belirtin. Her bir rol örneği için bir profil oluşturma oturumu başlatıldı. Hizmetinizi Visual Studio'dan yayımlama hakkında daha fazla bilgi için bkz. [Visual Studio'dan bir Azure bulut Hizmeti'nde yayımlanıyor](https://msdn.microsoft.com/library/azure/ee460772.aspx).

Visual Studio'da performans profili oluşturma hakkında daha fazla bilgi için bkz: [performans profili oluşturma Başlangıç Kılavuzu](https://msdn.microsoft.com/library/azure/ms182372.aspx) ve [profil oluşturma araçları kullanarak uygulama performansını analiz etme](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> IntelliTrace veya Bulut hizmetinizi yayımlayın, profil oluşturma etkinleştirebilirsiniz. Her ikisi de etkinleştirilemiyor.
> 
> 

### <a name="profiler-collection-methods"></a>Profiler koleksiyon metotları
Farklı bir koleksiyon metotları, performans sorunlarına temel profil oluşturma için kullanabilirsiniz:

* **CPU örnekleme** -bu yöntem ilk analizini CPU kullanımı sorunları için faydalı olan uygulama istatistiklerini toplar. CPU örnekleme, çoğu performans araştırmalar'ı başlatmak için önerilen yöntemdir. CPU örnekleme verileri topladığınızda, profil uygulama üzerinde düşük bir etkisi yoktur.
* **İzleme** -bu yöntem, odaklı analiz için ve giriş/çıkış performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verileri toplar. Araçlar yöntemini her giriş, çıkış ve işlevlerin işlev çağrısı bir modüldeki bir profil oluşturma sırasında kaydeder. Bu yöntem, kodunuzu bir bölümünü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemleri uygulama performansı üzerindeki etkisini anlamak için kullanışlıdır. Bu yöntem, 32-bit işletim sistemi çalıştıran bir bilgisayar için devre dışı bırakıldı. Bu seçenek, yalnızca bulut hizmeti, Azure'da yerel olarak işlem öykünücüsünde çalıştırdığınızda kullanılabilir.
* **.NET bellek ayırma** -örnekleme profili oluşturma yöntemi kullanarak, bu yöntem .NET Framework bellek ayırma verileri toplar. Toplanan veriler, sayısını ve ayrılan nesnelerin boyutunu içerir.
* **Eşzamanlılık** -bu yöntem, kaynak Çekişme verisi ve çok iş parçacıklı ve birden çok işlem uygulamaları çözümlenmesinde yararlı olan işlem ve iş parçacığı yürütme verileri toplar. Eşzamanlılık yöntemi gibi bir iş parçacığı zaman bekler, kodunuzun yürütülmesini engeller serbest bırakılacak Uygulama kaynağı için erişim kilitli her olay için veri toplar. Bu yöntem, çok iş parçacıklı uygulamalar çözümlemek için kullanışlıdır.
* Ayrıca etkinleştirebilirsiniz **katman etkileşim profili oluşturma**, ADO.NET zaman uyumlu yürütme sürelerini hakkında ek bilgi sağlayan bir veya daha fazla veritabanı ile iletişim kuran çok katmanlı uygulamaların işlevlerini de çağırır. Profil oluşturma yöntemlerinden birini ile Katman etkileşim verileri toplayabilir. Katman etkileşim profili oluşturma hakkında daha fazla bilgi için bkz. [katman etkileşimleri görünümü](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırma
Aşağıdaki resimde, Azure uygulamasını Yayımla iletişim kutusu, profil oluşturma ayarlarını yapılandırma işlemi gösterilmektedir.

![Profil oluşturma ayarlarını yapılandır](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Etkinleştirmek için **profil oluşturmayı etkinleştir** onay kutusu, profil oluşturucu bulut hizmetinizi yayımlayın için kullandığınız yerel bilgisayarda yüklü olması gerekir. Varsayılan olarak, profil oluşturucu, Visual Studio'yu yüklediğinizde yüklenir.
> 
> 

### <a name="to-configure-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırmak için
1. Çözüm Gezgini'nde, Azure projeniz için kısayol menüsünü açın ve ardından **Yayımla**. Bir bulut hizmeti yayımlama hakkında ayrıntılı adımlar için bkz: [Azure araçlarını kullanarak bir bulut hizmeti yayımlama](http://go.microsoft.com/fwlink/p?LinkId=623012).
2. İçinde **Azure uygulamasını Yayımla** iletişim kutusunda, seçtiğiniz **Gelişmiş ayarlar** sekmesi.
3. Oluşturmayı etkinleştirmek için işaretleyin **profil oluşturmayı etkinleştir** onay kutusu.
4. Profil oluşturma ayarlarınızı yapılandırmak için **ayarları** köprü. Profil ayarları iletişim kutusu görüntülenir.
5. Gelen **hangi profil oluşturma yöntemini kullanmak istediğiniz** seçenek düğmelerini, gereksinim, profil oluşturma türünü seçin.
6. Katman etkileşimi profil oluşturma verilerini toplamak için seçin **Katman etkileşimi profil oluşturmayı etkinleştir** onay kutusu.
7. Ayarları kaydetmek için seçin **Tamam** düğmesi.
   
    Bu uygulama yayımladığınızda, bu ayarlar, her rol için profil oluşturma oturumu oluşturmak için kullanılır.

## <a name="viewing-profiling-reports"></a>Profil oluşturma raporları görüntüleme
Bulut hizmetinizde bir rolünün her örneği için profil oluşturma oturumunu oluşturulur. Visual Studio'dan her oturum, profil oluşturma raporları görüntülemek için Sunucu Gezgini penceresini görüntüleyin ve ardından bir rol örneği seçmek için Azure işlem düğümünü seçin. Ardından aşağıdaki çizimde gösterildiği gibi profil oluşturma raporu da görüntüleyebilirsiniz.

![Azure'dan profil oluşturma raporunu görüntüleyin](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Profil oluşturma raporları görüntülemek için
1. Visual Studio'da Sunucu Gezgini penceresini görüntülemek için menü çubuğundaki Sunucu Gezgini görünümü seçin.
2. Azure bilgi işlem düğümünü seçin ve ardından Visual Studio'dan yayımlandığında, profil için seçili bulut hizmetini Azure dağıtım düğümünü seçin.
3. Bir örneği için profil oluşturma raporları görüntülemek için rol hizmeti seçin, belirli bir örneği için kısayol menüsünü açın ve ardından **profili oluşturma raporu görüntüle**.
   
    Rapor, bir .vsp dosya artık Azure'dan indirilir ve yükleme durumu, Azure etkinlik günlüğü'nde görünür. Yükleme tamamlandığında, profil oluşturma raporunun bir düzenleyici adlı Visual Studio için sekmesinde görünür <Role name> *<Instance Number>* <identifier>.vsp. Rapor için Özet veriler görüntülenir.
4. Geçerli Görünüm listesinde, raporun farklı görünümleri görüntülemek için istediğiniz görünümü türünü seçin. Daha fazla bilgi için [profil oluşturma araçları rapor görünümlerini](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Sonraki adımlar
[Bulut hizmetlerinde hata ayıklama](https://msdn.microsoft.com/library/azure/ee405479.aspx)

[Bir Azure bulut hizmetinde Visual Studio'dan yayımlama](https://msdn.microsoft.com/library/azure/ee460772.aspx)

