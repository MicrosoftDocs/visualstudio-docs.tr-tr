---
title: ClickOnce uygulamalarının güvenliğini sağlama | Microsoft Docs
ms.custom: ''
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56a49bf9cbf2c43cd7692592b53b9aca2b256313
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080346"
---
# <a name="secure-clickonce-applications"></a>ClickOnce uygulamalarının güvenliğini sağlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar, kod korumalı kaynaklara ve işlemlere sahip olan erişimini sınırlamaya yardımcı olması için .NET Framework kod erişim güvenliği sınırlamalarına tabidir. Bu nedenle, yazma için kod erişim güvenliği etkilerini anlamanız önemli olduğu, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaların uygun şekilde. Uygulamalarınız erişim için Internet ve Intranet gibi tam güven veya kısmi bölgeler kullanabilir.  
  
 Ayrıca ClickOnce, uygulama yayımcısının özgünlüğünü doğrulamak ve dosyaların karışmadığını ispatlamak üzere dağıtım bildirimleri ve uygulamayı imzalamak için sertifikalar kullanır. İmzalama isteğe bağlı bir adımdır; bu, bildirimler üretildikten sonra uygulama dosyalarını değiştirmeyi kolaylaştırır. Ancak, imzalı bildirimler olmadan, uygulama yükleyicisinin ortadaki adam güvenlik saldırılarında müdahaleye uğramadığından olmak zordur. Bu nedenle, uygulamalarınızı güvenlik altına almak için uygulama ve dağıtım bildirimlerinizi imzalamanızı öneririz.  
  
## <a name="zones"></a>Bölgeler  
 Kullanılarak dağıtılan uygulamalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] teknoloji izinleri ve güvenlik bölgesi tarafından tanımlanan bir eylemler kümesi sınırlı. Güvenlik bölgeleri, Internet Explorer'da tanımlanmış ve uygulamanın konumunu temel alır. Aşağıdaki tablo dağıtım konumunu temel alan varsayılan izinleri listeler:  
  
|Dağıtım Konumu|Güvenlik Bölgesi|  
|-------------------------|-------------------|  
|Web'den çalıştırın|Internet Bölgesi|  
|Web'den yükleyin|Internet Bölgesi|  
|Ağ dosya paylaşımından yükleyin|Yerel Intranet bölgesi|  
|CD-ROM'dan yükleyin|Tam Güven|  
  
 Varsayılan izinler uygulamanın özgün sürümüyle dağıtılan konumu temel alır; uygulama güncelleştirmeleri de bu izinleri devralır. Uygulama Web veya ağ konumundan güncelleştirmeleri denetlemek için yapılandırılmış ve daha yeni bir sürüm varsa, özgün yükleme tam güven izinleri yerine Internet ve Intranet bölgesi için izinleri alabilir. Kullanıcıların uyarılmasını önlemek için, Sistem Yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar için, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır. Daha fazla bilgi için [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Güvenilir uygulama dağıtımını yapılandırmak için, sertifika makine veya kuruluş düzeyinde yüklenebilir. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamaları için bir istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Kod erişim güvenliği ilkeleri  
 Uygulama izinlerini ayarlar tarafından belirlenir [ \<trustInfo > öğesi](../deployment/trustinfo-element-clickonce-application.md) uygulama bildiriminin öğesi. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projenin ayarlarına dayanarak bu bilgiyi otomatik olarak oluşturduğu **güvenlik** özellik sayfası. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama, sadece istediği özel izinler verilir. Örneğin, dosya erişiminin tam güven izinlerini gerektirdiği yerde uygulama tam güven izinleri isterse, uygulamaya tam güven izinleri değil de sadece dosya erişim izni verilir. Geliştirirken, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulaması emin olmanız uygulamanız için gereken belirli izinleri istemek. Çoğu durumda, uygulamanızı kısmi güvenle sınırlamak için Internet veya yerel Intranet bölgelerini kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Uygulamanız özel izinleri gerektiriyorsa, özel bir bölge oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Uygulamanın dağıtıldığı bölge için varsayılan izin kümesinin parçası olmayan bir izni dahil etme, son kullanıcının güncelleme ve yükleme zamanında iznin verilmesi için uyarılmasına sebep olur. Kullanıcıların uyarılmasını önlemek için, sistem yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar üzerinde, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır.  
  
 Geliştirici olarak, uygulamanızın uygun izinlerle çalıştığından emin olmak sizin sorumluluğunuzdur. Uygulama çalışma zamanı sırasında bir bölge dışında izinler isterse, güvenlik özel durumu ortaya çıkabilir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hedef güvenlik bölgesinde uygulamanızda hata ayıklamak sağlar. ve güvenli uygulamalar geliştirme üzerine Yardım sağlar. Daha fazla bilgi için [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Kod erişimi güvenliği ve ClickOnce hakkında daha fazla bilgi için bkz: [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Kod İmzalama sertifikaları  
 Kullanarak bir uygulamayı yayımlamak üzere [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım, bir ortak/özel anahtar çifti kullanarak uygulama için uygulama ve dağıtım bildirimlerini imzalayabilirsiniz. Bildirim imzalamak için kullanılan araçlar kullanılabilir **imzalama** sayfasının **Proje Tasarımcısı**. Daha fazla bilgi için [imzalama sayfası, Proje Tasarımcısı](../ide/reference/signing-page-project-designer.md). Alternatif olarak, bildirimlerin bir anahtar dosyasıyla yayımlama işlemi sırasında Yayımlama Sihirbazı'nı kullanarak oturum.  
  
 Bildirimler imzalandıktan sonra, Authenticode imzasına bağlı yayımcı bilgisi uygulamanın güvenilir bir kaynaktan olduğunu kullanıcıya göstermek için izinler iletişim kutusunda gösterilir.  
  
 Sertifikalar ve ClickOnce hakkında daha fazla bilgi için bkz. [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>ASP.NET form tabanlı kimlik doğrulaması  
 Hangi dağıtımlara her kullanıcı erişebileceğini denetlemek istiyorsanız, anonim erişim etkinleştirmemelisiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir Web sunucusu üzerinde dağıtılan uygulamalar. Alternatif olarak, kullanıcı erişimini bir kullanıcı kimliği üzerinde yüklenmiş dağıtımlar için, Windows kimlik doğrulaması kullanarak etkinleştirebilirsiniz.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ASP.NET form tabanlı kimlik doğrulamasını desteklemez, çünkü kalıcı tanımlama bilgileri kullanır; Internet Explorer önbelleğinde bulunduğu ve korsan saldırıya uğrayabileceği için bu bir güvenlik riski ortaya çıkarır. Bu nedenle, dağıtıyorsanız [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaları doğrulaması Windows kimlik doğrulaması dışındaki senaryolar desteklenmez.  
  
## <a name="pass-arguments"></a>Bağımsız değişkenleri geçirme  
 Bir ek güvenlik önlemleri bağımsız değişkenler geçirmek zorunda olduğunuzda oluşur bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir sorgu dizesi Web üzerinden dağıtılan uygulamalara sağlamak üzere etkinleştirir. Sorgu dizesi, uygulamayı başlatmak için kullanılan URL'nin sonunda bir dizi ad-değer çiftleri şeklini alır:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Varsayılan olarak, sorgu dizesi bağımsız değişkenleri devre dışıdır. Öznitelik etkinleştirmek için `trustUrlParameters` uygulamanın dağıtım bildiriminde ayarlanmalıdır. Bu değer arasında ayarlanabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] MageUI.exe gelen ve giden. Etkinleştirme geçirme hakkında ayrıntılı adımlar için sorgu dizeleri, bkz: [nasıl yapılır: çevrimiçi bir ClickOnce uygulamasında sorgu dize bilgilerini alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Bir komut satırı veya veritabanı için olan sorgu dizesi aracılığıyla elde edilen bağımsız değişkenleri güvenli oldukları konusunda emin olmadan geçirmeyin. Güvenli olmayan bağımsız değişkenler rasgele komutları çalıştırarak uygulamanızı yönetmek için kötü amaçlı kullanıcılara izin verebilecek veritabanı ve komut satırı kaçış karakterlerini içeren dizelerdir.  
  
> [!NOTE]
>  Sorgu dizesi bağımsız değişkenler bağımsız değişkenler tek yolu bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamasına başlangıçta. Bağımsız değişken geçiremezsiniz bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] komut satırından uygulama.  
  
## <a name="deploying-obfuscated-assemblies"></a>Gizlenmiş (Obfuscated) derlemeleri dağıtma  
 Visual Studio ücretsiz içerir [PreEmptive koruma - Dotfuscator Community Edition](../ide/dotfuscator/index.md), hangi kod karartma ve active koruma önlemleri aracılığıyla ClickOnce uygulamaları korumak için kullanabilirsiniz.  Ayrıntılar için lütfen bkz [Dotfuscator Community Edition Kullanıcı Kılavuzu'nun ClickOnce bölüm](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce dağıtım stratejisini seçin](../deployment/choosing-a-clickonce-deployment-strategy.md)