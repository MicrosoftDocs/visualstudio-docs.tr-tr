---
title: Test ayarlarını kullanarak tanılama bilgileri Topla
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 288d1ce5511d33a48006c97030d2b9c2f12ec88c
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895216"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Test ayarlarını kullanarak tanılama bilgileri Topla

Kullanabileceğiniz *Test ayarları* testlerinizi çalıştırdığınızda fazladan veri toplamak için Visual Studio'da. Örneğin, bir video testinizi çalıştırırken kaydı yapmak isteyebilirsiniz. Tanılama veri bağdaştırıcıları vardır:

-   Metin biçiminde her UI eylemi adımını toplayın

-   Kayıttan yürütme için her UI eylemini kaydedin

-   Sistem bilgilerini toplayın

-   Olay günlüğü verisini toplayın

-   Tekrarlanabilir olmayan hataları yalıtmaya yardımcı IntelliTrace verilerini toplama

Tanılama veri bağdaştırıcıları test makinesinin davranışını değiştirmek için de kullanılabilir. Örneğin, Visual Studio'da bir test ayarı ile takımınızın uygulamasının performansını değerlendirmek için çeşitli ağ topolojisi engellerini taklit edebilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Visual Studio ile test ayarlarını kullan

Birim çalıştırmak için kodlanmış UI, web performansı ve yük testlerini Visual Studio kullanarak, ekleme, yapılandırabilir ve testlerinizi çalıştırdığınızda kullanılacak test ayarlarını seçin. Testlerinizi çalıştırmak, veri toplamak veya test makinesini uzaktan etkilemek için test ayarlarınızda kullanmak üzere bir test denetleyicisi belirtmelisiniz. Test denetleyicisi test ayarlarınızda her rol için kullanılabilecek aracıları sahiptir.

## <a name="diagnostic-data-adapter-details"></a>Tanılama veri bağdaştırıcısı ayrıntıları

Aşağıdaki tabloda, tanılama veri bağdaştırıcılarını yerel veya uzaktan makine rolleriyle kullanılmak üzere yapılandırılabilir çeşitli yollarına genel bakış sağlar.

|Test ayarlarında kullanılan tanılama veri bağdaştırıcısı|Yerel makinede el ile testler|Otomatik testler|El ile testler: roller ve bir ortam kümesi kullanarak veri toplama|Notlar|
|-|-|-|-|-|
|**ASP.NET İstemci Proxy for IntelliTrace and Test Impact:** bu proxy, IntelliTrace ve Test etkisi tanılama veri bağdaştırıcısı için bir web sunucusuna istemciden gelen http çağrıları ile ilgili bilgi toplamanıza olanak tanır.|Evet|Evet|Evet|-Bunu yalnızca bir istemci rolü için IntelliTrace veya Test etkisi tanılama veri bağdaştırıcıları seçili olduğunda kullanın.|
|**ASP.NET profiler:** ASP.NET web uygulamalarına performans verileri toplayan ASP.NET Profil içeren bir test ayarı oluşturabilirsiniz.|Hayır|Evet (bkz. Notlar)|Hayır|-Bu tanılama veri bağdaştırıcısı yalnızca Visual Studio'dan yük testleri çalıştırdığınızda desteklenir.|
|**Kod kapsamı:** testlerin, kodunuzun ne kadarını kapsadığını araştırmak için kullanılan kod kapsam bilgilerini içeren bir test ayarı oluşturabilirsiniz.|Hayır|Evet (bkz. Notlar)|Hayır|Visual Studio'da otomatikleştirilmiş bir testi çalıştırdığınızda kod kapsamı-kullanabilirsiniz veya *mstest.exe*ve yalnızca testi çalıştıran makineden. Uzak koleksiyon desteklenmez.<br />-IntelliTrace bilgisi toplamak için yapılandırılmış test ayarına sahipseniz kod kapsam verisi toplama çalışmaz. **Not:** Bu tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Yöneticisi'nde test ayarları için kullanılmaz. Ayrıca, bu bağdaştırıcı Visual Studio 2010 test projeleriyle uyumluluk içindir. **Not:** otomatik testler Microsoft Test Yöneticisi'nden veya uzak bir Test aracısından Visual Studio'dan eski MSTest Çalıştırıcısı kullanılarak çalıştırıldığında kod kapsamı uyumluluk için geçerlidir.|
|**Olay günlüğü:** test sonuçlarında yer toplanan olay günlüğünü içerecek bir test ayarı yapılandırabilirsiniz.|Evet|Evet|Evet||
|**IntelliTrace:** tanılama veri bağdaştırıcısını yapılandırabilirsiniz *IntelliTrace* yeniden oluşturulması zor olan hataları ayırmaya yardımcı olmak için belirli tanı izleme bilgilerini toplamak için. Bu, bu bilgileri içeren bir IntelliTrace dosyası oluşturur. Bir IntelliTrace dosya uzantısına sahip *.iTrace*. Bir test başarısız olduğunda bir hata oluşturabilirsiniz. Test sonuçları ile birlikte kaydedilen IntelliTrace dosyası otomatik olarak bu hataya bağlanır. IntelliTrace dosyasında toplanan veri, kodda bir hata yeniden oluşturmak için gerekli olan zamanı azaltarak hata ayıklama verimliliğini artırır. Bu IntelliTrace dosyasından dosya yerel oturumun başka bir bilgisayarda benzetimi yapılabilir. Bu hatanın oluşturulamama riskini azaltır.|Evet|Evet|Evet|-IntelliTrace verisi toplamayı etkinleştirirseniz, kod kapsamı veri koleksiyonu çalışmıyor.<br />-Web istemci rolü için IntelliTrace kullanırsanız, IntelliTrace ve Test etkisi tanılama veri bağdaştırıcısı için ASP.NET İstemci Proxy'i de seçmelisiniz.<br />-IIS yalnızca şu sürümleri desteklenir: IIS 7.0, IIS 7.5 and IIS 8.0.|
|**Ağ öykünmesi:** yapay bir ağ yükü, bir test ayarı kullanarak testinize yerleştirmek istediğiniz belirtebilirsiniz. Ağ öykünmesi öykünmesi, çevirmeli gibi belirli ağ bağlantı hızı tarafından makine gelen ve giden iletişimi etkiler. |Hayır|Evet (bkz. Notlar)|Hayır|Bir istemci veya sunucu rolü için ağ öykünmesi tanılama veri bağdaştırıcısı kullanabilirsiniz. Birbirleri ile iletişim kuran bu rollerin ikisinde de bağdaştırıcı kullanın gerekmez. **Not:** Bu tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Yöneticisi'nde test ayarları için kullanılmaz. **Not:** ağ öykünmesi, ağ bağlantı hızını artırmak için kullanılamaz. **Uyarı:** test ayarlarına ağ öykünmesi tanılama veri bağdaştırıcısı içerir ve yerel makinenizde kullanmayı planladığınıza durumunda, ayrıca ağ öykünmesi sürücüsünü makinenizin ağ bağdaştırıcılarından birine bağlamanız gerekir. Ağ öykünmesi sürücüsü işlevi için ağ öykünmesi tanılama veri bağdaştırıcısı için gereklidir. Ağ öykünmesi sürücüsü yüklü ve bağdaştırıcınıza iki şekilde bağlanır: <ul><li>**Microsoft Visual Studio Test Aracısı ile yüklenmiş ağ öykünme sürücüsü:** Visual Studio Test Aracısı hem uzak makinelerde hem de yerel makinenizde kullanılabilir. Visual Studio Test aracısı yüklediğinizde, yükleme işlemi ağ öykünmesi sürücüsünü ağ kartınıza bağlayan bir yapılandırma adımı içerir. Daha fazla bilgi için [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).</li><li>**Microsoft Visual Studio Test Professional ile yüklenmiş ağ öykünme sürücüsü:** ağ öykünmesini ilk kez kullanırken, ağ öykünme sürücüsünü bir ağ kartına bağlamanız istenir.</li></ul> Ayrıca ağ öykünmesi sürücüsü komut satırından yerel makinenizde aşağıdaki komutu kullanarak Visual Studio test aracısı yüklemeden yükleyebilirsiniz: **VSTestConfig NETWORKEMULATION/Install**  **Uyarı:** ağ öykünmesi bağdaştırıcısı yük testleri tarafından yok sayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanın.|
|**Sistem bilgisi:** test üzerinde çalıştırıldığı makine hakkında sistem bilgisi içermek için bir test ayarı ayarlanabilir.|Evet|Evet|Evet||
|**Test etkisi:** hakkında uygulama kodunuzun yöntemleri kullanılmakta olan bir test durumu çalıştırdığınızda bilgi toplayabilirsiniz. Bu, uygulama kodu değişiklikleri ile hangi testlerin etkilendiğini belirlemek için geliştiriciler tarafından yapılan değişiklikler ile birlikte kullanılabilir.|Evet|Evet|Evet|-Web istemci rolü için test etkisi verisi topluyorsanız, IntelliTrace ve Test etkisi tanılama veri bağdaştırıcısı için ASP.NET İstemci Proxy'i de seçmelisiniz.<br />-IIS yalnızca şu sürümleri desteklenir: IIS 7.0, IIS 7.5 and IIS 8.0.|
|**Video Kaydedicisi:** bir testi çalıştırdığınızda masaüstü oturumunuzun bir video kaydını oluşturabilirsiniz. Videoyu diğer takım üyelerinin yeniden oluşturulması zor olan uygulama sorunlarını yalıtmalarına yardımcı olabilir.|Evet|Evet (bkz. Notlar)|Evet|-Test aracısı yazılımını hizmet yerine işlem olarak çalıştırmayı etkinleştirirseniz, bir video otomatik testler çalıştırdığınızda kaydı oluşturabilirsiniz.|