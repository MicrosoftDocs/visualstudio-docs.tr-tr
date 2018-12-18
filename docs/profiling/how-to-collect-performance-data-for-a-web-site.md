---
title: 'Nasıl yapılır: bir Web sitesi için performans verileri toplama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2d9cb832d8797eb4ebf16482f4bef02aa6644a3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064303"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Nasıl yapılır: bir web sitesi performans verileri toplama

Kullanabileceğiniz **performans Sihirbazı** için performans verilerini toplamak için bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması. Visual Studio'da açık olan bir web uygulaması profilini oluşturabilirsiniz veya profil bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web sitesi, yerel bilgisayarınızda bulunan ve Visual Studio IDE'de açık değil.

> [!NOTE]
> **Performans Sihirbazı** Katman etkileşimi (TIP) verileri, JScript performans verilerini veya hem toplanan profil oluşturma verilerinin eklemenize olanak tanır. İpucu seçeneği, sunucu tarafı işlemlerden veri toplar. JScript profil oluşturmayı yerel veya uzak bir Web sitesi üzerinde çalıştırılan betikler veri toplar. Çoğu durumda, seçeneklerden yalnızca birini seçmeniz gerekir.

 Yönetici kullanımına kullanıcı erişim izinleri ayarlarına bağlı olarak tek bir kullanıcı olabilir veya ASP.NET işleminin barındıran bilgisayarda bir profil oluşturucu oturumu oluşturmak için güvenlik izni olmayabilir. Aşağıdaki örneklerde kullanıcılar arasındaki olası farklar gösterilmektedir:

- Bazı kullanıcılar, sürücü ve hizmeti başlatmak için yöneticiniz tarafından belirlenen zaman Gelişmiş profil oluşturma özelliklerine erişimi.

- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişebilir.

- Bazı kullanıcılar, diğer tüm kullanıcılar için profil oluşturma için erişimi kısıtla.

  Daha fazla bilgi için [profil oluşturma ve Windows Vista Güvenliği](../profiling/profiling-and-windows-vista-security.md) ve yönetim seçeneklerini [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Bir web sitesi projesi profilini çıkarmak için

1. Açık [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Visual Studio'da Web projesi.

2. Üzerinde **Çözümle** menüsünde **performans Profiler**seçin **performans Gezgini**ve ardından **Başlat**.

3. Sihirbazın ilk sayfasında, profil oluşturma yöntemini seçin ve ardından **sonraki**. Profil oluşturma yöntemlerini hakkında daha fazla bilgi için bkz. [performans bilgilerini toplama metotlarını anlama](../profiling/understanding-performance-collection-methods.md). Profil oluşturma yöntemi eşzamanlılık görselleştiricisi web uygulamaları için kullanılabilir olmadığını unutmayın.

4. İçinde **hangi uygulamanın profilini oluşturmak için hedeflemek istiyorsunuz?** aşağı açılan listesinde, geçerli projenin'in seçili olduğundan emin olun ve ardından **sonraki**.

5. Sihirbazın üçüncü sayfasında Katman etkileşimi profil oluşturma (TIP) verileri, JavaScript web sayfaları veya her ikisi içinde çalışan verilerini eklemek seçebilirsiniz.

    - Katman etkileşim toplamak için seçin **Katman etkileşimi profil oluşturmayı etkinleştir** onay kutusu.

    - JavaScript Web sayfaları'nda çalışan veri toplamak için seçin **JavaScript profili** onay kutusu.

6. **İleri**'ye tıklayın.

7. Sihirbazının dördüncü sayfasında tıklayın **son**.

8. Performans oturumu için oluşturulan [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulaması ve web sitesi tarayıcıda başlatılır. Profil oluşturmak istediğiniz işlevi çalıştırın ve sonra Tarayıcıyı kapatın.

     Profil Oluşturucu veri dosyasını oluşturur ve veri Özet görünümünü görüntüler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ana penceresi.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Visual Studio'da bir proje açmadan bir web sitesinin profilini çıkarmak için

1. Visual Studio'yu açın.

2. Üzerinde **Çözümle** menüsünde **performans Profiler**seçin **performans Gezgini**ve ardından **Başlat**.

3. Sihirbazın ilk sayfasında, profil oluşturma yöntemini seçin ve ardından **sonraki**. Daha fazla bilgi için [anlama performans koleksiyon metotları](../profiling/understanding-performance-collection-methods.md).

4. Sihirbazın ikinci sayfasında seçin **bir ASP.NET veya JavaScript uygulamanın profilini** seçeneğini ve ardından **sonraki**.

5. İçinde **web uygulamanız hangi URL'de çalışacak** kutusunda sihirbazın üçüncü sayfasında, uygulama giriş sayfası URL'sini girin ve ardından **sonraki**.

   - Sunucusu (IIS) tabanlı Web sitesi için bir URL gibi yazın **< `http://localhost/MySite/default.aspx` >**. Bu neden [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulama kök profili oluşturulacak MySite ve sayfa default.aspx oturumu başlatmak için Internet Explorer'da başlatılması için bu sitede yerel bilgisayardaki uygulama.

   - Bir dosya tabanlı Web sitesi için dosya / / / gibi bir yol yazın**c:\WebSites\MySite\default.aspx**. Bu neden [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulama profili oluşturulacak c:\webSites\MySite ve sayfa bulunan `http://localhost:nnnn/MySite/default.aspx` oturumu başlatmak için Internet Explorer'da başlatılacak.

   - Örneğin URL'yi yazın, JavaScript verilerini toplamak istediğiniz dış siteleri için `http://www.contoso.com`.

     Daha fazla bilgi için özellik sayfaları görüntülemek bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hedef ikili.

6. Sihirbazın üçüncü sayfasında Katman etkileşimi profil oluşturma (TIP) verileri, JavaScript web sayfaları veya her ikisi içinde çalışan verilerini eklemek seçebilirsiniz.

    - Katman etkileşim toplamak için seçin **Katman etkileşimi profil oluşturmayı etkinleştir** onay kutusu.

    - JavaScript web sayfaları'nda çalışan veri toplamak için seçin **JavaScript profili** onay kutusu.

7. **İleri**'ye tıklayın.

8. Sihirbazının dördüncü sayfasında tıklayın **son**.

9. Performans oturumu için ASP.NET uygulama oluşturulur ve web sitesi tarayıcıda başlatılır. Profil oluşturmak istediğiniz işlevi çalıştırın ve sonra Tarayıcıyı kapatın.

     Profil Oluşturucu veri dosyasını oluşturur ve veri Özet görünümünü görüntüler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ana penceresi.

## <a name="see-also"></a>Ayrıca bkz.

[Genel Bakışlar](../profiling/overviews-performance-tools.md)  
[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)  
[İzleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)  
[Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
