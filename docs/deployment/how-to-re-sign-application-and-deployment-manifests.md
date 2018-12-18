---
title: 'Nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cce175f487d24e528d7527c424a1f76fa2a82824
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280681"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Nasıl yapılır: yeniden, uygulama ve dağıtım bildirimlerini imzalama
Windows Forms uygulamaları, Windows Presentation Foundation uygulamaları (xbap) ya da Office çözümleri için uygulama bildiriminde dağıtım özelliklerini değişiklikleri yaptıktan sonra her iki uygulamayı yeniden imzalamanız gerekir ve dağıtım bildirimleri ile bir Sertifika. Bu işlem, değiştirilen dosyaların son kullanıcı bilgisayarlarında yüklenmediğinden garanti eder.  
  
 Burada bildirimlerini yeniden imzalama başka bir senaryo, kendi sertifika ile dağıtım bildirimleri ve uygulamayı imzalamak Müşterilerinizin istediği andır.  
  
## <a name="re-sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini yeniden imzalama  
 Bu yordam, uygulama bildirim dosyasına değişiklikler zaten yaptınız varsayar (*.manifest*). Daha fazla bilgi için [nasıl yapılır: dağıtım özelliklerini değiştirme](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Uygulama ve dağıtım yeniden imzalamak için Mage.exe ile bildirimleri  
  
1.  Açık bir **Visual Studio komut istemi** penceresi.  
  
2.  Dizinleri oturum istediğiniz dosyaları içeren klasöre değiştirin.  
  
3.  Uygulama bildirim dosyasını imzalamak için aşağıdaki komutu yazın. Değiştirin *ManifestFileName'i* yanı sıra uzantı bildirim dosyasının adı. Değiştirin *sertifika* değiştirin ve sertifika dosyası için göreli veya tam yoluyla *parola* sertifika için parola ile.  
  
    ```cmd  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, bir eklenti, bir Windows Form uygulaması veya bir Windows Presentation Foundation gözatma uygulaması için bir uygulama bildirimi imzalamak için aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikalar üretim ortamlarında dağıtımı için önerilmez.  
  
    ```cmd  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Güncelleştirmek ve önceki adımla yer tutucu adlarını değiştirme dağıtım bildirimi dosyasını imzalamak için aşağıdaki komutu yazın.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, güncelleştirmek ve Excel eklentisi, bir Windows Forms uygulaması veya bir Windows Presentation Foundation gözatma uygulaması için bir dağıtım bildirimi imzalamak için aşağıdaki komutu çalıştırabilirsiniz.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  İsteğe bağlı olarak, ana dağıtım bildirimini kopyalayın (*yayımlama\\\<uygulamaadı > .application*) sürüm dağıtım dizinine (*publish\Application dosyaları\\ \<uygulamaadı > _\<sürüm >*).  
  
## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Güncelleştirme ve uygulama ve dağıtım bildirimlerini yeniden imzalama  
 Bu yordam, uygulama bildirim dosyasına değişiklikler zaten yaptınız varsayar (*.manifest*), ancak bu güncelleştirildi diğer dosyalar da mevcuttur. Dosya güncelleştirildiğinde, dosyayı temsil eden karma da güncelleştirilmesi gerekir.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Güncelleştirme ve uygulama ve dağıtım yeniden imzalamak için Mage.exe ile bildirimleri  
  
1.  Açık bir **Visual Studio komut istemi** penceresi.  
  
2.  Dizinleri oturum istediğiniz dosyaları içeren klasöre değiştirin.  
  
3.  Kaldırma *.deploy* dosya uzantısı yayımlama dosyalarından çıktı klasörü.  
  
4.  Güncelleştirilen dosyaların yeni karma uygulama bildirimini güncelleştirin ve uygulama bildirim dosyasını imzalamak için aşağıdaki komutu yazın. Değiştirin *ManifestFileName'i* yanı sıra uzantı bildirim dosyasının adı. Değiştirin *sertifika* değiştirin ve sertifika dosyası için göreli veya tam yoluyla *parola* sertifika için parola ile.  
  
    ```cmd  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, bir eklenti, bir Windows Form uygulaması veya bir Windows Presentation Foundation gözatma uygulaması için bir uygulama bildirimi imzalamak için aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikalar üretim ortamlarında dağıtımı için önerilmez.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Güncelleştirmek ve önceki adımla yer tutucu adlarını değiştirme dağıtım bildirimi dosyasını imzalamak için aşağıdaki komutu yazın.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, güncelleştirmek ve Excel eklentisi, bir Windows Forms uygulaması veya bir Windows Presentation Foundation gözatma uygulaması için bir dağıtım bildirimi imzalamak için aşağıdaki komutu çalıştırabilirsiniz.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Ekleme *.deploy* uygulama ve dağıtım bildirim dosyaları dışında dosyaları yedekleme dosya uzantısı.  
  
7.  İsteğe bağlı olarak, ana dağıtım bildirimini kopyalayın (*yayımlama\\\<uygulamaadı > .application*) sürüm dağıtım dizinine (*publish\Application dosyaları\\ \<uygulamaadı > _\<sürüm >*).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Güvenilir Uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Nasıl yapılır: ClickOnce uygulamaları için bir istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Nasıl yapılır: ClickOnce güven istemi davranışını yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)