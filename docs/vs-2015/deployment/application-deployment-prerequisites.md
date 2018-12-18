---
title: Uygulama dağıtımının önkoşulları | Microsoft Docs
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
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: 53
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: e382c5d312a2de69281bdeda92e9c275e2877932
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891004"
---
# <a name="application-deployment-prerequisites"></a>Uygulama Dağıtımının Önkoşulları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızı yüklemek ve başarılı bir şekilde çalıştırılması sağlamak için önce uygulamanızın bağımlı olduğu tüm bileşenleri hedef bilgisayarda zaten yüklü olduğundan emin olun gerekir. Örneğin, çoğu uygulama kullanılarak oluşturulan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] üzerinde bir bağımlılığa sahip [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]; uygulama yüklenmeden önce doğru ortak dil çalışma zamanı sürümünü hedef bilgisayarda mevcut olması gerekir.  
  
 Önkoşullar seçebileceğiniz **Önkoşullar iletişim kutusu** ve .NET Framework ve diğer yeniden dağıtılabilir dosyaları yüklemenizin bir parçası yükleyin. Bu yöntem olarak da bilinen *önyükleme*. Ardından, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] olarak da bilinir, Setup.exe adlı bir Windows yürütülebilir bir program oluşturur bir *önyükleyici*. Önyükleyici, uygulama çalışmadan önce bu önkoşulları yüklemek için sorumludur. Bu Önkoşullar seçme hakkında daha fazla bilgi için bkz. [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).  
  
 Her bir önyükleyici paketi önkoşuldur. Bir önyükleyici paketi, dizinler ve önkoşul nasıl yükleneceğini açıklayan bildirim dosyalarını içeren dosyaları grubudur. İçinde uygulama önkoşulları listelenmiyorsa **önkoşul iletişim kutusu**, özel önyükleyici paketleri oluşturma ve bunları Visual Studio'ya ekleyin. Önkoşullarda seçip **Önkoşullar iletişim kutusu**. Daha fazla bilgi için [önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md).  
  
 Varsayılan olarak, ClickOnce dağıtım için önyükleniyor etkinleştirilir. ClickOnce dağıtımı için oluşturulan önyükleyici imzalanır. Bir bileşen için önyüklemeyi devre dışı bırakabilirsiniz, ancak bileşen doğru sürümü, tüm hedef bilgisayarlarda zaten yüklü olduğundan emin olması durumunda bunu yapmanız gerekir.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Önyükleme ve ClickOnce dağıtımı  
 Bir istemci bilgisayarda, bir uygulamayı yüklemeden önce [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildiriminde belirtilen belirli gereksinimleri olduğundan emin olmak için istemci inceleyeceksiniz. Bunlar aşağıdakileri içerir:  
  
- Bir derleme bağımlılığı uygulama bildiriminde belirtilen ortak dil çalışma zamanı sürümü gerekli en düşük.  
  
- Gerekli en düşük sürümü Windows işletim sistemi, uygulamanın gerektirdiği belirtilen uygulama bildirimi kullanarak `<osVersionInfo>` öğesi. (Bkz [ \<bağımlılık > öğesi](../deployment/dependency-element-clickonce-application.md))  
  
- Derleme bildiriminde derleme bağımlılık bildirimi tarafından belirtilen genel derleme önbelleğinde (GAC), önceden yüklenmiş tüm derlemeleri en düşük sürümü.  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] eksik Önkoşullar algılayabilir ve bir önyükleyici kullanarak önkoşulları yükleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamasıyla Önkoşulları Yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  Bildirimleri gibi araçları tarafından oluşturulan değerleri değiştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] MageUI.exe ihtiyacınız ve uygulama bildirimi bir metin düzenleyicisinde düzenleyin ve ardından uygulama ve dağıtım bildirimlerini yeniden imzalama. Daha fazla bilgi için [nasıl yapılır: yeniden imzalama uygulama ve dağıtım bildirimlerini](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Uygulamanızı dağıtmak için Visual Studio ve ClickOnce kullanırsanız, varsayılan olarak seçili önyükleyici paketleri çözümdeki .NET Framework sürümü bağlıdır. Ancak, hedef .NET Framework sürümünü değiştirirseniz seçeneklerinde güncelleştirmeniz gerekir **Önkoşullar iletişim kutusu** el ile.  
  
|Hedef .NET Framework'ü|Seçilen önyükleyici paketleri|  
|---------------------------|------------------------------------|  
|.NET Framework 4 İstemci Profili|.NET Framework 4 İstemci Profili<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 İle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım, tarafından oluşturulan Publish.htm sayfa [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Yayımlama Sihirbazı ya da yalnızca uygulama yükleyen bir bağlantı noktaları veya bağlantı, hem uygulamayı hem de zamanlama bileşenleri yükler.  
  
 Önyükleyici Visual Studio'da ClickOnce Yayımlama Sihirbazı'nı veya Yayımlama Sayfası'ı kullanarak oluşturursanız, Setup.exe otomatik olarak imzalanır. Ancak, müşterinizin sertifika önyükleyici imzalamak için kullanmak istiyorsanız, dosya daha sonra oturum açabilirsiniz.  
  
## <a name="bootstrapping-and-msbuild"></a>Önyükleme ve MSBuild  
 Kullanmıyorsanız, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ancak komut satırında, uygulamalarınızın derleme, oluşturabileceğiniz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Microsoft Build Engine (MSBuild) görevini kullanarak uygulama önyükleniyor. Daha fazla bilgi için [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md).  
  
 Önyükleme alternatif olarak, önceden bir elektronik yazılım dağıtım sistemi Microsoft Systems Management Server (SMS) gibi kullanarak bileşenleri dağıtabilirsiniz.  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Önyükleyici (Setup.exe) komut satırı bağımsız değişkenleri  
 Tarafından oluşturulan Setup.exe [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve MSBuild görevleri komut satırı bağımsız değişkenleri aşağıdaki küçük kümesini destekler. Bunların dışında önyükleme uygulaması için sağlanan tüm bağımsız değişkenleri uygulama yükleyicisine iletilir.  
  
 Önyükleyici seçenekleri değiştirirseniz, işaretsiz önyükleyici değiştirin ve ardından önyükleyici dosya daha sonra oturum gerekir.  
  
|Komut satırı bağımsız değişkeni|Açıklama|  
|---------------------------|-----------------|  
|**-?, -h, - Yardım**|Yardım iletişim kutusunu görüntüler.|  
|**-url, - componentsurl**|Saklı URL'yi ve bu kurulum bileşenleri URL'sini gösterir.|  
|**-url =** `location`|Burada Setup.exe/sfw URL'sini ayarlar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama.|  
|**-componentsurl =** `location`|Burada Setup.exe bağımlılıklar için aşağıdaki gibi görünür URL'sini ayarlar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|  
|**-homesite =** `true`**&#124;** `false`|Zaman `true`, satıcının sitesinden tercih edilen konum bağımlılıkları indirir. Bu geçersiz kılmaları **- componentsurl** ayarı. Zaman `false`, tarafından belirtilen URL'den bağımlılıkları indirir **- componentsurl**.|  
  
## <a name="operating-system-support"></a>İşletim sistemi desteği  
 Windows Server 2008 Sunucu Çekirdeği veya Windows Server 2008 R2 Server sınırlı işlevsellikle düşük bakım sunucusu ortamı sağlayan Core, Visual Studio önyükleyicisi desteklenmiyor. Örneğin, Sunucu Çekirdeği yükleme seçeneği, yalnızca .NET Framework üzerinde tam bağlı olan Visual Studio özellikleri çalıştırılamıyor .NET Framework 3.5 Sunucu Çekirdeği profilini destekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce Güvenliği ve Dağıtımı](../deployment/clickonce-security-and-deployment.md)



