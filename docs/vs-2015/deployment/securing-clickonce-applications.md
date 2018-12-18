---
title: ClickOnce uygulamalarının güvenliğini sağlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ae5bd70a675798d971cb184038a7e036d04fc95a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247227"
---
# <a name="securing-clickonce-applications"></a>ClickOnce Uygulamalarının Güvenliğini Sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar, kod korumalı kaynaklara ve işlemlere sahip olan erişimini sınırlamaya yardımcı olması için .NET Framework kod erişim güvenliği sınırlamalarına tabidir. Bu nedenle, yazma için kod erişim güvenliği etkilerini anlamanız önemli olduğu, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaların uygun şekilde. Uygulamalarınız erişim için Internet ve Intranet gibi tam güven veya kısmi bölgeler kullanabilir.  
  
 Ayrıca ClickOnce, uygulama yayımcısının özgünlüğünü doğrulamak ve dosyaların karışmadığını ispatlamak üzere dağıtım bildirimleri ve uygulamayı imzalamak için sertifikalar kullanır. İmzalama isteğe bağlı bir adımdır; bu, bildirimler üretildikten sonra uygulama dosyalarını değiştirmeyi kolaylaştırır. Ancak, imzalı bildirimler olmadan, uygulama yükleyicisinin ortadaki adam güvenlik saldırılarında müdahaleye uğramadığından olmak zordur. Bu nedenle, uygulamalarınızı güvenlik altına almak için uygulama ve dağıtım bildirimlerinizi imzalamanızı öneririz.  
  
## <a name="zones"></a>Bölgeler  
 Kullanılarak dağıtılan uygulamalar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] teknoloji izinleri ve güvenlik bölgesi tarafından tanımlanan bir eylemler kümesi sınırlı. Güvenlik bölgeleri, Internet Explorer'da tanımlanmış ve uygulamanın konumunu temel alır. Aşağıdaki tablo dağıtım konumunu temel alan varsayılan izinleri listeler:  
  
|Dağıtım Konumu|Güvenlik Bölgesi|  
|-------------------------|-------------------|  
|Web'den çalıştırın|Internet Bölgesi|  
|Web'den yükleyin|Internet Bölgesi|  
|Ağ dosya paylaşımından yükleyin|Yerel Intranet bölgesi|  
|CD-ROM'dan yükleyin|Tam Güven|  
  
 Varsayılan izinler uygulamanın özgün sürümüyle dağıtılan konumu temel alır; uygulama güncelleştirmeleri de bu izinleri devralır. Uygulama Web veya ağ konumundan güncelleştirmeleri denetlemek için yapılandırılmış ve daha yeni bir sürüm varsa, özgün yükleme tam güven izinleri yerine Internet ve Intranet bölgesi için izinleri alabilir. Kullanıcıların uyarılmasını önlemek için, Sistem Yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar için, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır. Daha fazla bilgi için [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Güvenilir uygulama dağıtımını yapılandırmak için, sertifika makine veya kuruluş düzeyinde yüklenebilir. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamaları için bir istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Kod Erişim Güvenliği İlkeleri  
 Uygulama izinlerini ayarlar tarafından belirlenir [ \<trustInfo > öğesi](../deployment/trustinfo-element-clickonce-application.md) uygulama bildiriminin öğesi. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projenin ayarlarına dayanarak bu bilgiyi otomatik olarak oluşturduğu **güvenlik** özellik sayfası. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama, sadece istediği özel izinler verilir. Örneğin, dosya erişiminin tam güven izinlerini gerektirdiği yerde uygulama tam güven izinleri isterse, uygulamaya tam güven izinleri değil de sadece dosya erişim izni verilir. Geliştirirken, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması emin olmanız uygulamanız için gereken belirli izinleri istemek. Çoğu durumda, uygulamanızı kısmi güvenle sınırlamak için Internet veya yerel Intranet bölgelerini kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Uygulamanız özel izinleri gerektiriyorsa, özel bir bölge oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulaması için özel izinler ayarlayın](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Uygulamanın dağıtıldığı bölge için varsayılan izin kümesinin parçası olmayan bir izni dahil etme, son kullanıcının güncelleme ve yükleme zamanında iznin verilmesi için uyarılmasına sebep olur. Kullanıcıların uyarılmasını önlemek için, sistem yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar üzerinde, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır.  
  
 Geliştirici olarak, uygulamanızın uygun izinlerle çalıştığından emin olmak sizin sorumluluğunuzdur. Uygulama çalışma zamanı sırasında bir bölge dışında izinler isterse, güvenlik özel durumu ortaya çıkabilir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hedef güvenlik bölgesinde uygulamanızda hata ayıklamak sağlar. ve güvenli uygulamalar geliştirme üzerine Yardım sağlar. Daha fazla bilgi için [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Kod erişimi güvenliği ve ClickOnce hakkında daha fazla bilgi için bkz: [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Kod İmzalama Sertifikaları  
 Kullanarak bir uygulamayı yayımlamak üzere [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım, bir ortak/özel anahtar çifti kullanarak uygulama için uygulama ve dağıtım bildirimlerini imzalayabilirsiniz. Bildirim imzalamak için kullanılan araçlar kullanılabilir **imzalama** sayfasının **Proje Tasarımcısı**. Daha fazla bilgi için [imzalama sayfası, Proje Tasarımcısı](../ide/reference/signing-page-project-designer.md). Alternatif olarak, bildirimlerin bir anahtar dosyasıyla yayımlama işlemi sırasında Yayımlama Sihirbazı'nı kullanarak oturum.  
  
 Bildirimler imzalandıktan sonra, Authenticode imzasına bağlı yayımcı bilgisi uygulamanın güvenilir bir kaynaktan olduğunu kullanıcıya göstermek için izinler iletişim kutusunda gösterilir.  
  
 Sertifikalar ve ClickOnce hakkında daha fazla bilgi için bkz. [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>ASP.NET Form Tabanlı Kimlik Doğrulaması  
 Hangi dağıtımlara her kullanıcı erişebileceğini denetlemek istiyorsanız, anonim erişim etkinleştirmemelisiniz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir Web sunucusu üzerinde dağıtılan uygulamalar. Alternatif olarak, kullanıcı erişimini bir kullanıcı kimliği üzerinde yüklenmiş dağıtımlar için, Windows kimlik doğrulaması kullanarak etkinleştirebilirsiniz.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ASP.NET form tabanlı kimlik doğrulamasını desteklemez, çünkü kalıcı tanımlama bilgileri kullanır; Internet Explorer önbelleğinde bulunduğu ve korsan saldırıya uğrayabileceği için bu bir güvenlik riski ortaya çıkarır. Bu nedenle, dağıtıyorsanız [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaları doğrulaması Windows kimlik doğrulaması dışındaki senaryolar desteklenmez.  
  
## <a name="passing-arguments"></a>Bağımsız Değişkenleri Geçirme  
 Bir ek güvenlik önlemleri bağımsız değişkenler geçirmek zorunda olduğunuzda oluşur bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir sorgu dizesi Web üzerinden dağıtılan uygulamalara sağlamak üzere etkinleştirir. Sorgu dizesi, uygulamayı başlatmak için kullanılan URL'nin sonunda bir dizi ad-değer çiftleri şeklini alır:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Varsayılan olarak, sorgu dizesi bağımsız değişkenleri devre dışıdır. Öznitelik etkinleştirmek için `trustUrlParameters` uygulamanın dağıtım bildiriminde ayarlanmalıdır. Bu değer arasında ayarlanabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] MageUI.exe gelen ve giden. Etkinleştirme geçirme hakkında ayrıntılı adımlar için sorgu dizeleri, bkz: [nasıl yapılır: çevrimiçi bir ClickOnce uygulamasında sorgu dize bilgilerini alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Bir komut satırı veya veritabanı için olan sorgu dizesi aracılığıyla elde edilen bağımsız değişkenleri güvenli oldukları konusunda emin olmadan geçirmeyin. Güvenli olmayan bağımsız değişkenler rasgele komutları çalıştırarak uygulamanızı yönetmek için kötü amaçlı kullanıcılara izin verebilecek veritabanı ve komut satırı kaçış karakterlerini içeren dizelerdir.  
  
> [!NOTE]
>  Sorgu dizesi bağımsız değişkenler bağımsız değişkenler tek yolu bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamasına başlangıçta. Bağımsız değişken geçiremezsiniz bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] komut satırından uygulama.  
  
## <a name="deploying-obfuscated-assemblies"></a>Gizlenmiş (Obfuscated) Derlemeleri Dağıtma  
 Başkaları tarafından kod üzerine tersine mühendislik yapılmasını engellemek için Dotfuscator kullanarak uygulamanızı gizleyebilirsiniz. Bunun yanında, derleme gizleme Visual Studio IDE veya ClickOnce dağıtım sürecine tümleşikleştirilmemiştir. Bu nedenle, gizleme işlemini dağıtım sürecinin dışında belki bir bağlama sonrası adımı kullanarak gerçekleştirebilirsiniz. Projeyi derledikten sonra, aşağıdaki adımları Visual Studio'nun dışında el ile gerçekleştirmelisiniz.  
  
1.  Dotfuscator kullanarak gizlemeyi yapın.  
  
2.  ClickOnce bildirimleri oluşturmak ve bunları imzalamak için Mage.exe veya MagUI.exe kullanın. Daha fazla bilgi için [Mage.exe (bildirim üretme ve düzenleme aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) ve [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
3.  El ile dosyaları dağıtım kaynağı konumuna (Web sunucusu, UNC paylaşımı veya CD-ROM) yayımlayın. (Kopyalayın.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce Dağıtım Stratejisini Seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)



