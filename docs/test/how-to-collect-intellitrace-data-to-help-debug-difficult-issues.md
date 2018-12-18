---
title: IntelliTrace verisi
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: cad52f39fc45e5561e2a87f12c804cb0d445d96a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064763"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Nasıl yapılır: hata ayıklama zorluklarını çözmeye yardımcı olmak için IntelliTrace verilerini toplama

Tanılama veri bağdaştırıcısı için görsel Stdio, belirli tanı izleme bilgilerini toplamak için IntelliTrace'i yapılandırabilirsiniz. Testler bu bağdaştırıcıyı kullanabilir, test, uygulama için büyük miktarda tanılama olayları toplayabilir ve sonrasında bir geliştirici bu olayları, kodu izleyip bir hatanın nedenini bulmak üzere kullanabilir. IntelliTrace için tanılama veri bağdaştırıcısı el ile veya otomatik testler için kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> IntelliTrace yalnızca yönetilen kod kullanarak yazılmış bir uygulama üzerinde çalışır. Bir tarayıcı istemci olarak kullanan bir web uygulamasını test ediyorsanız, yönetilen kod yok izleme için kullanılabilir olmadığından, IntelliTrace istemci için test ayarlarınızda etkinleştirmemeniz gerekir. Bu durumda, bir ortam kurmak ve web sunucunuz üzerinde uzaktan IntelliTrace veri toplamak isteyebilirsiniz.

IntelliTrace verisi uzantısına sahip bir dosyada depolanır *.iTrace*. Test ve bir test adımı başarısız çalıştırdığınızda, bir hata oluşturabilirsiniz. Tanılama bilgilerini içeren bir IntelliTrace dosyası otomatik olarak bu hataya eklenir.

> [!NOTE]
> Test geçiş başarılı olduğunda, IntelliTrace için tanılama veri bağdaştırıcısını IntelliTrace dosyası oluşturmaz. Yalnızca başarısız bir test çalışması veya bir hatayı bildirme, bir dosya kaydeder.

IntelliTrace dosyasında toplanan veri, kodunuzda hata yeniden oluşturmak için gerekli olan zamanı azaltarak hata ayıklama verimliliğini artırır. Ayrıca, yerel oturumunuza bilgisayarlarında çoğaltabilirsiniz başka bir kişi ile IntelliTrace dosyası paylaşabildiğinden hata tekrarlanabilir olmayan olacağını olasılığını azaltır.

> [!NOTE]
> Test ayarlarınızda IntelliTrace etkinleştirirseniz, kod kapsam verisi toplama çalışmaz.

> [!WARNING]
> IntelliTrace için tanılama veri bağdaştırıcısı, test çalışması için testleri yüklendikten sonra gerçekleştirilmesi gereken yönetilen bir işlem kullanılarak çalışır. İzlemek istediğiniz işlem zaten başladıysanız, işlem zaten çalıştığından hiç IntelliTrace dosyaları toplanacak. Bu aşmak için testler yüklenmeden önce işlem durdurulduğundan emin olun. Ardından test yüklenemedi veya ilk testi başlatıldıktan sonra işlemi başlatın.

Aşağıdaki yordam, toplamak istediğiniz IntelliTrace verilerini yapılandırmak açıklar. Bu adımlar, Microsoft Test Yöneticisi ve Test Ayarları iletişim kutusunda Visual Studio'da her iki yapılandırma düzenleyicisine uygulanır.

> [!NOTE]
> IntelliTrace verilerini toplamak için kullanılan test aracısı için kullanıcı hesabı Yöneticileri grubunun bir üyesi olması gerekir. Daha fazla bilgi için [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace Tanılama veri bağdaştırıcısıyla toplanacak verileri yapılandırma

Bu yordamdaki adımları gerçekleştirmeden önce Microsoft Test Yöneticisi veya Visual Studio'dan test ayarlarınızı açmalı ve seçmeniz gerekir **veri ve tanılama** sayfası.

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace Tanılama veri bağdaştırıcısıyla toplanacak verileri yapılandırmak için

1.  IntelliTrace verilerini toplamak için kullanılacak rolü seçin.

2.  Seçin **IntelliTrace**.

3.  Bir ASP.NET web uygulaması veya web istemci rolü için IntelliTrace ekliyorsanız, da seçmelisiniz **IntelliTrace ve Test etkisi için ASP.NET İstemci Proxy'i**.

     Bu proxy, IntelliTrace ve Test etkisi tanılama veri bağdaştırıcısı için bir web sunucusu istemciden gelen http çağrıları ile ilgili bilgi toplamanıza olanak sağlar.

    > [!WARNING]
    > Burada IntelliTrace verilerini toplamak için istediğinize Internet Information Server (IIS) üzerinde uygulama havuzu için kullanılan kimliği için özel bir hesabı kullanmaya karar verirseniz, yerel kullanıcı profili özel hesap için IIS makinesi üzerinde oluşturmanız gerekir kullanılıyor. Yerel IIS makinesi için bir kez oturum açarak veya özel hesap kimlik bilgilerini kullanarak aşağıdaki komutu çalıştırarak yerel profil için özel bir hesap oluşturabilirsiniz:
    >
    > **runas /user:domain\name /profile cmd.exe**

4.  Seçin **yapılandırma** için **IntelliTrace** varsayılan IntelliTrace ayarlarını değiştirmek için.

     Toplanacak verileri yapılandırmak için iletişim kutusu görüntülenir.

    > [!WARNING]
    > IntelliTrace verisi toplamayı etkinleştirirseniz, kod kapsam verisi toplama çalışmaz.

5.  Seçin **genel** sekmesi. Seçin **yalnızca IntelliTrace olaylarını** test ettiğinizde performansı üzerinde çok az etkisi olan önemli tanılama olaylarını kaydetmek için.

     veya

     Seçin **IntelliTrace olayları ve çağrı bilgileri** tanılama olayları ve yöntemi kaydetmek için çağrı bilgileri, izleme düzeyini gösterir. Testlerinizi çalıştırdığınızda, bu izleme düzeyini performans etkisi olabilir.

6.  Internet Information Services üzerinde çalışan ASP.NET uygulamanızın veri toplamak için seçin **Internet Information Services üzerinde çalışan ASP.NET uygulamalarından veri topla**. Ayarlama ve web sunucusu rolünde test aracınızı yapılandırmak. Bkz: [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

7.  Seçin **modülleri** sekmesi. Şunlardan birini seçin **şunlar hariç tüm modüllerden veri toplamak** ve **Ekle** modül listesine eklemek ve **Kaldır** modülü kaldırmak için. Bu seçenek, belirttiğiniz modüller hariç sistemde çalışan tüm modülleri dahil edildi sağlar.

     veya

     Seçin **yalnızca şu modüllerden veri toplamak** ve **Ekle** modül listesine eklemek ve **Kaldır** modülü kaldırmak için. Bu seçenek tam olarak hangi modüllerin istediğinizi belirtmenize olanak tanır.

    > [!NOTE]
    > Mümkünse, izlemek istediğiniz belirli işlemleri seçin. Bu en iyi performans için önerilir.

8.  Seçin **işlemleri** sekmesi. Seçin **şunlar hariç tüm işlemlerden veri topla** ve **Ekle** işlemler listesine eklemek ve **Kaldır** işlemi kaldırmak için. Bu seçenek, belirttiğiniz işlemleri dışında sistemde çalışan tüm işlemler dahil sağlar.

     veya

     Seçin **yalnızca belirtilen işlemlerden veri topla** ve **Ekle** işlemler listesine eklemek ve **Kaldır** işlemi kaldırmak için. Bu seçenek tam olarak hangi işlemlerin istediğinizi belirtmenize olanak tanır.

9. (İsteğe bağlı) Seçin **IntelliTrace olayları** sekmesi. Seçin veya eklemek veya tanılama olaylarını toplarken hariç tutmak istediğiniz her bir IntelliTrace olay kategorisi temizleyin.

10. (İsteğe bağlı) IntelliTrace olay kategorisini genişletin ve seçin veya eklemek veya IntelliTrace olayları hariç tutmak istediğiniz her özel olay temizleyin.

11. (İsteğe bağlı) Seçin **Gelişmiş** sekmesi. Ardından, yanındaki oku seçin **en fazla kayıt için disk alanı miktarını** ve IntelliTrace dosyası kullanmak etkinleştirmek istediğiniz en büyük boyutu seçin.

    > [!NOTE]
    > Kayıt boyutunu artırmak için bu kayıt, test sonuçları ile birlikte kaydettiğinizde, bir zaman aşımı sorun ortaya çıkabilir.

12. Microsoft Test Yöneticisi kullanıyorsanız seçin **Kaydet**. Visual Studio kullanıyorsanız, seçin **Tamam**. IntelliTrace ayarları artık yapılandırılır ve test ayarlarınız için kaydedildi.

    > [!NOTE]
    > Bu tanılama veri bağdaştırıcısı için yapılandırmayı sıfırlamak için seçin **varsayılan yapılandırmaya Sıfırla** Visual Studio için veya **Varsayılana Sıfırla** Microsoft Test Yöneticisi için.

## <a name="see-also"></a>Ayrıca bkz.

- [(Azure Test planları) test sırasında tanılama verilerini toplayın](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [El ile testlerde (Azure Test planları) tanılama verilerini toplayın](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Test ayarlarını kullanarak tanılama bilgileri Topla](../test/collect-diagnostic-information-using-test-settings.md)
- [IntelliTrace verilerini toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)