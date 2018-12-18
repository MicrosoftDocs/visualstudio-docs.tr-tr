---
title: Office çözümlerine güven verme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfce58ca765e7e3710ecb55a1c84c09f0ee14f52
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447251"
---
# <a name="grant-trust-to-office-solutions"></a>Office çözümlerine güven verme
  GRANT güven çözümü derleme, uygulama bildirimi, dağıtım bildirimi ve belge güvenmeyi her hedef bilgisayarın güvenlik ilkesini değiştirme Office çözümleri anlamına gelir. Güven Office çözümü için ya da son kullanıcı tarafından verilebilir.  
  
 Uygulama ve dağıtım bildirimlerini imzalama tarafından Office çözümü için tam güven verebilirsiniz.  
  
 Son kullanıcılar vermek Office çözümlerine güven bir güven kararı yaparak [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] güven istemi.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Uygulama ve dağıtım bildirimlerini imzalama tarafından çözümü güven  
 Tüm uygulama ve dağıtım bildirimlerini Office çözümleri yayımcıyı tanımlayan bir sertifika ile imzalanmalıdır. Sertifikalar, güven kararları almak için bir temel sağlar.  
  
 Geçici bir sertifika sizin için oluşturulur ve siz hata ayıklarken çözümü çalıştıracak şekilde güven derleme zamanında verilir. Geçici bir sertifikayla imzalanmış bir çözüm yayımlarsanız, son kullanıcı bir güven kararı vermeniz istenir.  
  
 Çözüm bilinen ve güvenilen bir sertifika ile oturum açarsanız, çözüm bir güven kararı için son kullanıcıya sormadan otomatik olarak yüklenir. İmzalama için bir sertifika edinme hakkında daha fazla bilgi için bkz: [ClickOnce ve Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Bir sertifika alındıktan sonra sertifikayı güvenilen yayımcılar listesine ekleyerek açıkça güvenilmelidir. Daha fazla bilgi için bkz: [nasıl yapılır: ClickOnce uygulamaları için bir istemci bilgisayar güvenilen bir yayımcı eklemek](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Bir geliştirici çözüm geçici bir sertifika ile oturum açtığında, yönetici özelleştirme bilinen ve güvenilen bir sertifika ile bildirim oluşturma ve düzenleme aracı kullanarak yeniden oturum (*mage.exe*), aşağıdakilerden birini olduğu Microsoft .NET Framework Araçları. Çözümleri imzalama hakkında daha fazla bilgi için bkz: [nasıl yapılır: oturum Office çözümleri](../vsto/how-to-sign-office-solutions.md) ve [nasıl yapılır: uygulama ve dağıtım bildirimlerini imzalama](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>ClickOnce güven istemi kullanarak çözüm güven  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] çözümün sertifikasına güvenen kuruluş genelinde ilke yok ise güven kararı için son kullanıcıya sorar. Son kullanıcı çözüme güven verirse, bu güven kararı depolamak için bir URL ve ortak anahtar içeren bir ekleme listesi girdisi oluşturulur. Güvenilir özelleştirme daha sonra çalıştırdığınızda, son kullanıcı yeniden istenmez.  
  
 Yöneticiler devre dışı bırakabilir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] güven istemi veya Authenticode sertifikası ile imzalanmış çözümleri için isteme gerek duyabilir. Bilgisayarım, LocalIntranet, Internet, TrustedSites ve UntrustedSites bölgeler için bu ayarları değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: ClickOnce güven istemi davranışını yapılandırma](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri güvenli](../vsto/securing-office-solutions.md)   
 [Belgelere güven verme](../vsto/granting-trust-to-documents.md)   
 [Office çözüm güvenlik sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)   
 [Office çözümleri için belirli güvenlik konuları](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  