---
title: 'Nasıl yapılır: bir Web sitesi için performans verileri toplama | Microsoft Docs'
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
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 646d5a59dee68123e478da074901c9d6f98c2763
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783915"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Nasıl yapılır: bir Web sitesi için performans verileri toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz **performans Sihirbazı** için performans verilerini toplamak için bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması. Açık olan bir Web uygulaması profilini oluşturabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], veya profil bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] yerel bilgisayarınızda bulunan ve açık değil Web sitesi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
>  **Performans Sihirbazı** Katman etkileşimi (TIP) verileri, JScript performans verilerini veya hem toplanan profil oluşturma verilerinin eklemenize olanak tanır. İpucu seçeneği, sunucu tarafı işlemlerden veri toplar. JScript profil oluşturmayı yerel veya uzak bir Web sitesi üzerinde çalıştırılan betikler veri toplar. Çoğu durumda, seçeneklerden yalnızca birini seçmeniz gerekir.  
  
 Yönetici kullanımına kullanıcı erişim izinleri ayarlarına bağlı olarak tek bir kullanıcı olabilir veya ASP.NET işleminin barındıran bilgisayarda bir profil oluşturucu oturumu oluşturmak için güvenlik izni olmayabilir. Aşağıdaki örneklerde kullanıcılar arasındaki olası farklar gösterilmektedir:  
  
- Yöneticisi hizmetinin başlatılmasını ve sürücü ayarladığınızda, bazı kullanıcılar Gelişmiş profil oluşturma özelliklerine erişebilir.  
  
- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişebilir.  
  
- Bazı kullanıcılar, diğer tüm kullanıcılar için profil oluşturma için benim Reddet erişir.  
  
  Daha fazla bilgi için [profil oluşturma ve Windows Vista Güvenliği](../profiling/profiling-and-windows-vista-security.md) ve yönetim seçeneklerini [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Bir Web sitesi projesi profilini çıkarmak için  
  
1.  Açık [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web projesinde [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] veya [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2.  Üzerinde **Çözümle** menüsünü tıklatın **performans Sihirbazını Başlat**.  
  
3.  Sihirbazın ilk sayfasında, profil oluşturma yöntemini seçin ve ardından **sonraki**. Profil oluşturma yöntemlerini hakkında daha fazla bilgi için bkz. [anlama performans koleksiyon metotları](../profiling/understanding-performance-collection-methods.md). Profil oluşturma yöntemi eşzamanlılık görselleştiricisi web uygulamaları için kullanılabilir olmadığını unutmayın.  
  
4.  İçinde **hangi uygulamanın profilini oluşturmak için hedeflemek istiyorsunuz?** aşağı açılan listesinde, geçerli projenin'in seçili olduğundan emin olun ve ardından **sonraki**.  
  
5.  Sihirbazın üçüncü sayfasında Katman etkileşimi profil oluşturma (TIP) verileri, JavaScript Web sayfaları veya her ikisi içinde çalışan verilerini eklemek seçebilirsiniz.  
  
    -   Katman etkileşim toplamak için seçin **Katman etkileşimi profil oluşturmayı etkinleştir** onay kutusu.  
  
    -   JavaScript Web sayfaları'nda çalışan veri toplamak için seçin **JavaScript profili** onay kutusu.  
  
6.  **İleri**'ye tıklayın.  
  
7.  Sihirbazının dördüncü sayfasında tıklayın **son**.  
  
8.  Performans oturumu için oluşturulan [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulaması ve Web sitesi tarayıcıda başlatılır. Profil oluşturmak istediğiniz işlevi çalıştırın ve sonra Tarayıcıyı kapatın.  
  
     Profil Oluşturucu veri dosyasını oluşturur ve veri Özet görünümünü görüntüler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ana penceresi.  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Visual Studio'da bir proje açmadan bir Web sitesinin profilini çıkarmak için  
  
1. Açık [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] veya [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. Üzerinde **Çözümle** menüsünü tıklatın **performans Sihirbazını Başlat**.  
  
3. Sihirbazın ilk sayfasında, profil oluşturma yöntemini seçin ve ardından **sonraki**. Daha fazla bilgi için [anlama performans koleksiyon metotları](../profiling/understanding-performance-collection-methods.md).  
  
4. Sihirbazın ikinci sayfasında seçin **bir ASP.NET veya JavaScript uygulamanın profilini** seçeneğini ve ardından **sonraki**.  
  
5. İçinde **web uygulamanız hangi URL'de çalışacak** kutusunda sihirbazın üçüncü sayfasında, uygulama giriş sayfası URL'sini girin ve ardından **sonraki**.  
  
   - Sunucusu (IIS) tabanlı Web sitesi için bir URL gibi yazın **http://localhost/MySite/default.aspx**. Bu neden [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulama kök profili oluşturulacak MySite ve sayfa default.aspx oturumu başlatmak için Internet Explorer'da başlatılması için bu sitede yerel bilgisayardaki uygulama.  
  
   - Bir dosya tabanlı Web sitesi için dosya / / / gibi bir yol yazın**c:\WebSites\MySite\default.aspx**. Bu neden [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulama profili oluşturulacak c:\webSites\MySite ve sayfa bulunan http://localhost:nnnn/MySite/default.aspx oturumu başlatmak için Internet Explorer'da başlatılacak.  
  
   - Örneğin URL'yi yazın, JavaScript verilerini toplamak istediğiniz dış siteleri için http://www.contoso.com.  
  
     Daha fazla bilgi için özellik sayfaları görüntülemek bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] hedef ikili.  
  
6. Sihirbazın üçüncü sayfasında Katman etkileşimi profil oluşturma (TIP) verileri, JavaScript Web sayfaları veya her ikisi içinde çalışan verilerini eklemek seçebilirsiniz.  
  
   -   Katman etkileşim toplamak için seçin **Katman etkileşimi profil oluşturmayı etkinleştir** onay kutusu.  
  
   -   JavaScript Web sayfaları'nda çalışan veri toplamak için seçin **JavaScript profili** onay kutusu.  
  
7. **İleri**'ye tıklayın.  
  
8. Sihirbazının dördüncü sayfasında tıklayın **son**.  
  
9. Performans oturumu için ASP.NET uygulama oluşturulur ve Web sitesi tarayıcıda başlatılır. Profil oluşturmak istediğiniz işlevi çalıştırın ve sonra Tarayıcıyı kapatın.  
  
     Profil Oluşturucu veri dosyasını oluşturur ve veri Özet görünümünü görüntüler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ana penceresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel bakış](../profiling/overviews-performance-tools.md)   
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [İzleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)   
 [Örnekleme Veri Değerlerini Anlama](../profiling/understanding-sampling-data-values.md)



