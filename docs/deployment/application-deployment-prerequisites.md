---
title: Uygulama dağıtımının önkoşulları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 421092218cdeb889fe195917e46b123c73e7e1f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851809"
---
# <a name="application-deployment-prerequisites"></a>Uygulama dağıtımının önkoşulları

Uygulamanızı yüklemek ve başarılı bir şekilde çalıştırılması için sağlamak için ilk uygulamanızı hedef bilgisayara bağımlı olduğu tüm bileşenleri yükleyin. Örneğin, çoğu uygulama kullanılarak oluşturulan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] üzerinde bir bağımlılığa sahip [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Bu durumda, uygulama yüklenmeden önce doğru ortak dil çalışma zamanı sürümünü hedef bilgisayarda mevcut olması gerekir.  

 Önkoşullar seçebileceğiniz **Önkoşullar iletişim kutusu** ve .NET Framework ve herhangi diğer redistributable yüklemenizin bir parçası yükleyin. Bu yöntem olarak da bilinen *önyükleme*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adlı bir Windows yürütülebilir bir program oluşturur *Setup.exe*olarak da bilinen bir *önyükleyici*. Önyükleyici, uygulama çalışmadan önce bu önkoşulları yüklemek için sorumludur. Bu Önkoşullar seçme hakkında daha fazla bilgi için bkz. [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).  

 Her bir önyükleyici paketi önkoşuldur. Bir önyükleyici paketi, dizin ve dosyaların önkoşulları nasıl yüklendiğini açıklayan bildirim dosyalarını içeren bir gruptur. İçinde uygulama önkoşulları listelenmiyorsa **önkoşul iletişim kutusu**, özel önyükleyici paketleri oluşturma ve bunları Visual Studio'ya ekleyin. Önkoşullarda seçip **Önkoşullar iletişim kutusu**. Daha fazla bilgi için [önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md).  

 Varsayılan olarak, ClickOnce dağıtım için önyükleniyor etkinleştirilir. ClickOnce dağıtımı için oluşturulan önyükleyici imzalanır. Bir bileşen için önyüklemeyi devre dışı bırakabilirsiniz, ancak yalnızca, eminseniz bileşeni doğru sürümü zaten tüm hedef bilgisayarlarda yüklü.  

## <a name="bootstrapping-and-clickonce-deployment"></a>Önyükleme ve ClickOnce dağıtımı  
 Bir istemci bilgisayarda, bir uygulamayı yüklemeden önce [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] inceler istemciye, uygulama bildiriminde belirtilen gereksinimlere sahip olduğundan emin olun. Bu, aşağıdaki gereksinimleri şunlardır:  

- Bir derleme bağımlılığı uygulama bildiriminde belirtilen ortak dil çalışma zamanı sürümü gerekli en düşük.  

- Gerekli en düşük sürümü Windows işletim sistemi, uygulamanın gerektirdiği belirtilen uygulama bildirimi kullanarak `<osVersionInfo>` öğesi. (Bkz [ \<bağımlılık > öğesi](../deployment/dependency-element-clickonce-application.md).)  

- Derleme bildiriminde derleme bağımlılık bildirimi tarafından belirtilen genel derleme önbelleğinde (GAC), önceden yüklenmiş tüm derlemeleri en düşük sürümü.  

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eksik Önkoşullar algılayabilir ve bir önyükleyici kullanarak önkoşulları yükleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamasıyla Önkoşulları Yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  

> [!NOTE]
>  Bildirimleri gibi araçları tarafından oluşturulan değerleri değiştirmek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve *MageUI.exe*, uygulama bildirimi bir metin düzenleyicisinde düzenleyin ve ardından uygulama ve dağıtım bildirimlerini yeniden imzalama gerekiyor. Daha fazla bilgi için [nasıl yapılır: yeniden, uygulama ve dağıtım bildirimlerini imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  

 Uygulamanızı dağıtmak için Visual Studio ve ClickOnce kullanırsanız, varsayılan olarak seçili önyükleyici paketleri çözümdeki .NET Framework sürümü bağlıdır. Ancak, hedef .NET Framework sürümünü değiştirirseniz seçeneklerinde güncelleştirmeniz gerekir **Önkoşullar iletişim kutusu** el ile.  

|Hedef .NET Framework'ü|Seçilen önyükleyici paketleri|  
|---------------------------|------------------------------------|  
|.NET Framework 4 İstemci Profili|.NET Framework 4 İstemci Profili<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  

 İle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım *Publish.htm* sayfası tarafından oluşturulan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Yayımlama Sihirbazı ya da yalnızca uygulama yükleyen bir bağlantı noktaları veya hem uygulama hem de zamanlama yükler Bağla bileşenleri.  

 Visual Studio'da ClickOnce Yayımlama Sihirbazı'nı veya yayımlama sayfasını kullanarak önyükleyici oluşturursanız *Setup.exe* otomatik olarak imzalanır. Ancak, müşterinizin sertifika önyükleyici imzalamak için kullanmak istiyorsanız, dosya daha sonra oturum açabilirsiniz.  

## <a name="bootstrapping-and-msbuild"></a>Önyükleme ve MSBuild  
 Kullanmıyorsanız, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ancak bunun yerine uygulamalarınızın komut satırında derleyin, oluşturabileceğiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Microsoft Build Engine (MSBuild) görevini kullanarak uygulama önyükleniyor. Daha fazla bilgi için [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md).  

 Önyükleme alternatif olarak, önceden bir elektronik yazılım dağıtım sistemi Microsoft Systems Management Server (SMS) gibi kullanarak bileşenleri dağıtabilirsiniz.  

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Önyükleyici (Setup.exe) komut satırı bağımsız değişkenleri  
 *Setup.exe* tarafından oluşturulan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve MSBuild görevleri, aşağıdaki komut satırı bağımsız değişkenleri kümesini destekler. Diğer bağımsız değişkenleri uygulama yükleyicisine iletilir.  

 Önyükleyici seçenekleri değiştirirseniz, işaretsiz önyükleyici değiştirmek ve önyükleyici dosya daha sonra oturum açın.  


| komut satırı bağımsız değişkeni | Açıklama |
| - | - |
| **-?, -h, - Yardım** | Yardım iletişim kutusunu görüntüler. |
| **-url, - componentsurl** | Saklı URL'yi ve bu kurulum bileşenleri URL'sini gösterir. |
| **-url =** `location` | URL'sini ayarlar burada *Setup.exe* arar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama. |
| **-componentsurl =** `location` | URL'sini ayarlar burada *Setup.exe* bağımlılıklar için aşağıdaki gibi görünür [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. |
| **-homesite =** `true`**&#124;** `false` | Zaman `true`, satıcının sitesinden tercih edilen konum bağımlılıkları indirir. Bu ayar geçersiz kılar **- componentsurl** ayarı. Zaman `false`, tarafından belirtilen URL'den bağımlılıkları indirir **- componentsurl**. |

## <a name="operating-system-support"></a>İşletim sistemi desteği  
 Sınırlı işlevsellikle sağladıkları düşük bakım sunucu ortamı olarak Visual Studio önyükleyicisi Windows Server 2008 Sunucu Çekirdeği veya Windows Server 2008 R2 Server Core üzerinde desteklenmiyor. Örneğin, Sunucu Çekirdeği yükleme seçeneği, yalnızca tam .NET Framework'e bağlı Visual Studio özellikleri çalıştırılamaz .NET Framework 3.5 Sunucu Çekirdeği profilin destekler.  

## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce dağıtım stratejisini seçin](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)