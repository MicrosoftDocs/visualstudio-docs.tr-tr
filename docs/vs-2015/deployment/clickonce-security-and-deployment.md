---
title: ClickOnce güvenliği ve dağıtımı | Microsoft Docs
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
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 50654574dea18df98f8f4ecef8d606cccec93f14
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898180"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce Güvenliği ve Dağıtımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] yüklü ve minimum kullanıcı müdahalesiyle çalıştırma kendi kendini güncelleştiren ve Windows tabanlı uygulamalar oluşturmanızı sağlayan bir dağıtım teknolojisidir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yayımlama ve projelerinizi Visual Basic ve Visual C# geliştirdiyseniz, ClickOnce teknolojisi ile dağıtılan uygulamaları güncelleştirmek için tam destek sağlar. Visual C++ uygulamalarını dağıtma hakkında daha fazla bilgi için bkz: [Visual C++ uygulamaları için ClickOnce dağıtımı](http://msdn.microsoft.com/library/9988c546-0936-452c-932f-9c76daa42157).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dağıtım üç ana dağıtım sorunları üstesinden gelir:  
  
- **Uygulamaları güncelleştirme sorunlar yaşıyoruz.** Microsoft Windows Installer dağıtımı ile bir uygulama her güncelleştirildiğinde, kullanıcı bir msp dosyası bir güncelleştirmeyi yüklemek ve yüklü ürün için geçerlidir; ile [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtımı, güncelleştirmeleri otomatik olarak sağlayabilirsiniz. Yalnızca değişmiş olan uygulama bölümlerini yüklenir ve ardından tam, güncelleştirilmiş uygulamayı yan yana bir klasörden yeniden yüklenir.  
  
- **Kullanıcının bilgisayarı bir etki.** Windows Installer dağıtımı ile uygulama olası sürüm çakışmaları ile paylaşılan bileşenler genellikle dayanır; ile [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım, her uygulama kendi içinde bağımsızdır ve diğer uygulamalarla müdahale edemez.  
  
- **Güvenlik izinleri.** Windows Installer dağıtımı, yönetim izinleri gerektirir ve yalnızca sınırlı kullanıcı yüklemesine izin verir; [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtımı yüklemek yönetici olmayan kullanıcılara sağlar ve yalnızca uygulama için gerekli kod erişimi güvenliği izinleri verir.  
  
  Geçmişte, bu sorunları bazen ödün Yükleme kolaylığı için zengin kullanıcı arabirimi, Windows tabanlı uygulamalar yerine Web uygulamaları oluşturmaya karar geliştiricilerin neden oldu. Kullanılarak dağıtılan uygulamalar kullanarak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], her iki teknolojinin en iyi olabilir.  
  
## <a name="what-is-a-clickonce-application"></a>ClickOnce uygulaması nedir?  
 A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamasıdır herhangi bir Windows Presentation Foundation (.xbap), Windows Forms (.exe), konsol uygulaması (.exe) veya yayımlanan kullanarak Office çözümü (.dll) [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] teknoloji. Yayımlayabilmek için bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] üç farklı yolla uygulama: bir Web sayfası, bir ağ dosya paylaşımı veya CD-ROM gibi medya. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama son kullanıcının bilgisayarında yüklü ve bile bilgisayarı çevrimdışı olduğunda veya yalnızca çevrimiçi modda, çalıştırılabilir kalıcı olarak herhangi bir şey son kullanıcının bilgisayarında yüklemeden yerel olarak çalıştırın. Daha fazla bilgi için [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaları kendi kendine güncelleştirme; Bunlar, kullanılabilir hale gelir ve güncelleştirilmiş dosyaları otomatik olarak değiştirme gibi yeni sürümlere yönelik kontrol edebilirsiniz. Geliştirici, güncelleştirme davranışını belirtebilirsiniz; bir ağ yöneticisi de denetleyebilirsiniz güncelleştirme stratejileri, örneğin, güncelleştirme zorunlu olarak işaretleniyor. Güncelleştirmeleri de yeniden önceki bir sürüme son kullanıcı veya yönetici tarafından alınabilir. Daha fazla bilgi için [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Çünkü [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalardır, yüklenmesini veya çalıştırılmasını yalıtılmış bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama varolan uygulamaları kesemez. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaları kendi kendine yeterdir; Her [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama yükleneceğini ve bir güvenli kullanıcı, uygulama başına önbellek çalıştırın. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaları, Internet veya Intranet güvenlik bölgeleri'nde çalışır. Gerekirse, uygulama yükseltilmiş güvenlik izinleri isteyebilir. Daha fazla bilgi için [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>ClickOnce güvenliği nasıl çalışır  
 Çekirdek [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] güvenlik sertifikaları, kod erişim güvenliği ilkeleri ve ClickOnce güven istemi dayanır.  
  
### <a name="certificates"></a>Sertifikalar  
 Authenticode sertifikalar uygulama yayımcısının özgünlüğünü doğrulamak için kullanılır. ClickOnce, uygulama dağıtımı için Authenticode kullanılarak oluşturulmuş olan güvenilir bir kaynaktan gelen yasal bir program olarak kendisini tanıtmasını zararlı bir programın önlemeye yardımcı olur. İsteğe bağlı olarak, sertifikalar, uygulamayı imzalamak için de kullanılabilir ve dosyaların üzerinde oynanmadığını değil olduğunu ispatlamak üzere dağıtım bildirimleri. Daha fazla bilgi için [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md). Sertifikaları, güvenilen yayımcılar listesi için istemci bilgisayarların yapılandırmak için de kullanılabilir. Uygulamanın güvenilir bir yayımcıdan geliyorsa, hiçbir kullanıcı etkileşimi olmadan yüklenebilir. Daha fazla bilgi için [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 Kod erişimi güvenliği, kod korumalı kaynaklara sahip olan erişimini sınırlamaya yardımcı olur. Çoğu durumda, izinleri sınırlamak için Internet veya yerel Intranet bölgelerini seçebilirsiniz. Kullanım **güvenlik** sayfasını **ProjectDesigner** uygulama için uygun bölgeyi istemek için. Son kullanıcı deneyimi yaşamak için sınırlı izinler ile uygulamaları hata ayıklaması yapabilirsiniz. Daha fazla bilgi için [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce güven istemi  
 Uygulama bölgenin izin verdiğinden daha fazla izinleri isterse, son kullanıcının bir güven kararı istenecek. Son kullanıcı gibi Windows Forms uygulamaları, Windows Presentation Foundation uygulamaları, konsol uygulamaları, XAML tarayıcı uygulamaları ve Office çözümlerini ClickOnce uygulamaları çalıştırmak için güvenilir olup olmadığına karar verebilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce güven istemi davranışını yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>ClickOnce dağıtımı nasıl çalışır  
 Çekirdek [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım mimarisi, iki XML bildirim dosyaları dayanır: uygulama bildirimi ve bir dağıtım bildirimi. Dosyaları, ClickOnce uygulamalarının gelen yüklendiği, nasıl güncelleştirilir ve ne zaman güncelleştirileceği tanımlamak için kullanılır.  
  
### <a name="publishing-clickonce-applications"></a>ClickOnce Uygulamalarını Yayımlama  
 Uygulama bildirimi uygulamanın kendisinin açıklar. Bu derlemeler, bağımlılıklar ve uygulama, gerekli izinlere ve burada güncelleştirmelerinin kullanılabilir olacağını konumun oluşturan dosyaları içerir. Uygulama geliştiricisi Yayımlama Sihirbazı'nda Visual Studio ya da bildirim oluşturma ve düzenleme aracı (Mage.exe) kullanarak uygulama bildirimini Yazar [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Daha fazla bilgi için [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Dağıtım bildirimi, uygulamanın nasıl dağıtılacağını açıklar. Bu, uygulama bildiriminin konumu ve istemcilerin çalışması gereken uygulama sürümünü içerir.  
  
### <a name="deploying-clickonce-applications"></a>ClickOnce uygulamaları dağıtma  
 Oluşturulduktan sonra dağıtım bildirimini dağıtım konumuna kopyalanır. Bu, bir Web sunucusu, ağ dosya paylaşımı veya CD gibi medya olabilir. Uygulama bildirimini ve uygulama dosyalarını da dağıtım bildiriminde belirtilen bir dağıtım konumuna kopyalanır. Bu dağıtım konumu ile aynı olabilir veya farklı bir konum olabilir. Kullanırken **Yayımlama Sihirbazı** Visual Studio'da kopyalama işlemleri otomatik olarak gerçekleştirilir.  
  
### <a name="installing-clickonce-applications"></a>ClickOnce uygulamalarını yükleme  
 Dağıtım konumuna dağıtıldıktan sonra son kullanıcılar indirin ve bir Web sayfasında veya bir klasördeki dağıtım bildirimi dosyasını temsil eden bir simgeye tıklayarak uygulamayı yükleyin. Çoğu durumda, son kullanıcı, yükleme, hangi yükleme devam eder ve ek müdahalesi olmadan uygulama başlatıldıktan sonra onaylamak için soran bir basit iletişim kutusu ile sunulur. Uygulama yükseltilmiş izinler veya uygulamanın güvenilir bir sertifika ile imzalanmamış varsa burada ihtiyaç duyması iletişim kutusu da yüklemeye devam etmeden önce izin vermek için kullanıcıya sorar. ClickOnce yüklemeleri kullanıcı başına olsa da, yönetici ayrıcalıkları gerektiren bir önkoşul yoksa izin yükseltme gerekli olabilir. Yükseltilmiş izinler hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
 Sertifikaları Güvenilen sertifikalarla imzalanmış ClickOnce uygulamaları sessizce yüklemek makine veya kuruluş düzeyinde güvenilen olabilir. Güvenilen sertifikalar hakkında daha fazla bilgi için bkz. [güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).  
  
 Uygulama kullanıcının eklenebilir **Başlat** menü ve **Program Ekle veya Kaldır** grubu **Denetim Masası**. Diğer dağıtım teknolojileri farklı olarak, hiçbir şey eklenir **Program dosyaları** klasör veya kayıt defteri ve yönetici hakları yok yüklemesi için gerekli  
  
> [!NOTE]
>  Uygulamanın eklenmesini önlemek mümkündür **Başlat** menü ve **Program Ekle veya Kaldır** grup, etkin bir Web uygulaması gibi davranır kolaylaştırır. Daha fazla bilgi için [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>ClickOnce uygulamaları güncelleştirme  
 Uygulama geliştiricileri, uygulamanın güncelleştirilmiş sürümünü oluşturduğunuzda, bunlar yeni bir uygulama bildirimi oluşturmak ve bir dağıtım konuma dosyaları kopyalayın — genellikle bir kardeş klasör özgün uygulamanın dağıtım klasörü. Yönetici, dağıtım bildirimi, uygulamanın yeni sürümü konumunu işaret edecek şekilde güncelleştirir.  
  
> [!NOTE]
>  **Yayımlama Sihirbazı** Visual Studio'da bu adımları gerçekleştirmek için kullanılabilir.  
  
 Dağıtım konumu ek olarak, dağıtım bildirimini ayrıca burada uygulama için güncelleştirilmiş sürümleri denetler bir güncelleştirme konumu (Web sayfası veya ağ dosya paylaşımı) içerir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] **Yayımlama** özellikleri ne zaman ve ne sıklıkta uygulama güncelleştirmeleri denetlesin belirtmek için kullanılır. Güncelleştirme davranışı dağıtım bildiriminde belirtilebilir ve uygulamanın kullanıcı arabirimi yoluyla kullanıcı seçenekleri sunulabilir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] API'leri. Ayrıca, **Yayımla** özellikleri işe güncelleştirmeleri zorunlu kılmak için veya önceki bir sürümüne geri almak için. Daha fazla bilgi için [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Üçüncü taraf yükleyicileri  
 Uygulamanızı yanı sıra üçüncü taraf bileşenleri yüklemek için ClickOnce yükleyicisi özelleştirebilirsiniz. Yeniden dağıtılabilir paketi (.exe veya .msi dosyası) sahip ve dilden Ürün bildirimi ve dile özgü paket bildirimi paketini açıklayan gerekir. Daha fazla bilgi için [önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>ClickOnce Araçları  
 Aşağıdaki tabloda, oluştur, Düzenle, oturum ve uygulama ve dağıtım bildirimlerini yeniden imzalama için kullanabileceğiniz araçları gösterilmektedir.  
  
|Aracı|Açıklama|  
|----------|-----------------|  
|[Güvenlik Sayfası, Proje Tasarımcısı](../ide/reference/security-page-project-designer.md)|Uygulama ve dağıtım bildirimlerini imzalar.|  
|[Yayın Sayfası, Proje Tasarımcısı](../ide/reference/publish-page-project-designer.md)|Oluşturur ve Visual Basic ve Visual C# uygulamaları için uygulama ve dağıtım bildirimlerini düzenler.|  
|[Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)|Visual Basic, Visual C# ve Visual C++ uygulamaları için uygulama ve dağıtım bildirimlerini oluşturur.<br /><br /> İmzalar ve uygulama ve dağıtım bildirimlerini yeniden imzalar.<br /><br /> Toplu betiklerden ve komut isteminden çalıştırabilirsiniz.|  
|[MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)|Oluşturur ve uygulama ve dağıtım bildirimlerini düzenler.<br /><br /> İmzalar ve uygulama ve dağıtım bildirimlerini yeniden imzalar.|  
|[GenerateApplicationManifest Görevi](../msbuild/generateapplicationmanifest-task.md)|Uygulama bildirimi oluşturur.<br /><br /> MSBuild'den çalıştırılabilir. Daha fazla bilgi için [MSBuild başvurusu](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest Görevi](../msbuild/generatedeploymentmanifest-task.md)|Dağıtım bildirimi oluşturur.<br /><br /> MSBuild'den çalıştırılabilir. Daha fazla bilgi için [MSBuild başvurusu](../msbuild/msbuild-reference.md).|  
|[SignFile Görevi](../msbuild/signfile-task.md)|Uygulama ve dağıtım bildirimlerini imzalar.<br /><br /> MSBuild'den çalıştırılabilir. Daha fazla bilgi için [MSBuild başvurusu](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Uygulama ve dağıtım bildirimleri oluşturmak için kendi uygulamanızı geliştirin.|  
  
 Aşağıdaki tabloda bu tarayıcıların içinde ClickOnce uygulamaları desteklemek için gereken .NET Framework sürümünü gösterir.  
  
|Tarayıcı|.NET Framework sürümü|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 4 3.5 SP1|  
|Firefox|2.0 SP1'DE, 3.5 SP1 4|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Vista'da ClickOnce dağıtımı](../deployment/clickonce-deployment-on-windows-vista.md)   
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce ile COM bileşenleri dağıtma](../deployment/deploying-com-components-with-clickonce.md)   
 [Komut satırından ClickOnce uygulamalarını derleme](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [System.Deployment.Application Kullanan ClickOnce Uygulamalarında Hata Ayıklama](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)



