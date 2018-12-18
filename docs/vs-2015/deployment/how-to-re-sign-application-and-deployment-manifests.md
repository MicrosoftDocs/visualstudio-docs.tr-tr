---
title: 'Nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama | Microsoft Docs'
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
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 734258871e72e6272abcd61c4efa1a00765f8a32
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185724"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Nasıl yapılır: Uygulama ve Dağıtım Bildirimlerini Yeniden İmzalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms uygulamaları, Windows Presentation Foundation uygulamaları (xbap) ya da Office çözümleri için uygulama bildiriminde dağıtım özelliklerini değişiklikleri yaptıktan sonra her iki uygulamayı yeniden imzalamanız gerekir ve dağıtım bildirimleri ile bir Sertifika. Bu işlem, değiştirilen dosyaların son kullanıcı bilgisayarlarında yüklenmediğinden garanti eder.  
  
 Burada bildirimlerini yeniden imzalama başka bir senaryo, kendi sertifika ile dağıtım bildirimleri ve uygulamayı imzalamak Müşterilerinizin istediği andır.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini yeniden imzalama  
 Bu yordam, uygulama bildirim dosyası (.manifest) önceden değişiklikleri yaptığınızı varsayar. Daha fazla bilgi için [nasıl yapılır: dağıtım özelliklerini değiştirme](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Uygulama ve dağıtım yeniden imzalamak için Mage.exe ile bildirimleri  
  
1.  Açık bir **Visual Studio komut istemi** penceresi.  
  
2.  Dizinleri oturum istediğiniz dosyaları içeren klasöre değiştirin.  
  
3.  Uygulama bildirim dosyasını imzalamak için aşağıdaki komutu yazın. ManifestFileName'i yanı sıra uzantı bildirim dosyasının adıyla değiştirin. Sertifika, sertifika dosyasının göreli veya tam yoluyla değiştirin ve parola sertifika parolasını değiştirin.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, bir eklenti, bir Windows Form uygulaması veya bir Windows Presentation Foundation gözatma uygulaması için bir uygulama bildirimi imzalamak için aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikalar üretim ortamlarında dağıtımı için önerilmez.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Güncelleştirmek ve önceki adımla yer tutucu adlarını değiştirme dağıtım bildirimi dosyasını imzalamak için aşağıdaki komutu yazın.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, güncelleştirmek ve Excel eklentisi, bir Windows Forms uygulaması veya bir Windows Presentation Foundation gözatma uygulaması için bir dağıtım bildirimi imzalamak için aşağıdaki komutu çalıştırabilirsiniz.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  İsteğe bağlı olarak, ana dağıtım bildirimini kopyalayın (Yayımlama\\*appname*.application) sürüm dağıtım dizinine (publish\Application dosyaları\\*appname*_ *sürüm*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Güncelleştirme ve uygulama ve dağıtım bildirimlerini yeniden imzalama  
 Bu yordam, zaten uygulamanıza bildirim dosyası (.manifest) değişiklikler yaptınız, ancak güncelleştirildi diğer dosyalar olduğunu varsayar. Dosya güncelleştirildiğinde, dosyayı temsil eden karma da güncelleştirilmesi gerekir.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Güncelleştirme ve uygulama ve dağıtım yeniden imzalamak için Mage.exe ile bildirimleri  
  
1.  Açık bir **Visual Studio komut istemi** penceresi.  
  
2.  Dizinleri oturum istediğiniz dosyaları içeren klasöre değiştirin.  
  
3.  Yayımlama çıktı klasöründe bulunan dosyaları .deploy dosya uzantısını kaldırın.  
  
4.  Güncelleştirilen dosyaların yeni karma uygulama bildirimini güncelleştirin ve uygulama bildirim dosyasını imzalamak için aşağıdaki komutu yazın. ManifestFileName'i yanı sıra uzantı bildirim dosyasının adıyla değiştirin. Sertifika, sertifika dosyasının göreli veya tam yoluyla değiştirin ve parola sertifika parolasını değiştirin.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, bir eklenti, bir Windows Form uygulaması veya bir Windows Presentation Foundation gözatma uygulaması için bir uygulama bildirimi imzalamak için aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikalar üretim ortamlarında dağıtımı için önerilmez.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Güncelleştirmek ve önceki adımla yer tutucu adlarını değiştirme dağıtım bildirimi dosyasını imzalamak için aşağıdaki komutu yazın.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, güncelleştirmek ve Excel eklentisi, bir Windows Forms uygulaması veya bir Windows Presentation Foundation gözatma uygulaması için bir dağıtım bildirimi imzalamak için aşağıdaki komutu çalıştırabilirsiniz.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Uygulama ve dağıtım bildirim dosyaları dışında dosyaları için .deploy dosya uzantısı ekleyin.  
  
7.  İsteğe bağlı olarak, ana dağıtım bildirimini kopyalayın (Yayımlama\\*appname*.application) sürüm dağıtım dizinine (publish\Application dosyaları\\*appname*_ *sürüm*).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Güvenilir Uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Nasıl yapılır: güvenilir bir yayımcı ClickOnce uygulamaları için bir istemci bilgisayara ekleyin](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Nasıl yapılır: ClickOnce Güven İstemi Davranışını Yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)



