---
title: 'İzlenecek yol: ClickOnce uygulaması için özel bir yükleyici oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 939fd64873a2aab9d5652768ad4ecfa4a93b5122
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152249"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>İzlenecek yol: ClickOnce uygulaması için özel bir yükleyici oluşturma
Herhangi bir ClickOnce uygulaması temel bir *.exe* dosya sessizce yüklenebilir ve özel bir yükleyici tarafından güncelleştirildi. Özel bir yükleyici özel iletişim kutuları için güvenlik ve Bakım işlemlerine dahil olmak üzere yüklemesi sırasında özel bir kullanıcı deneyimi uygulayabilirsiniz. Özel yükleyici yükleme işlemlerini gerçekleştirmek için kullandığı <xref:System.Deployment.Application.InPlaceHostingManager> sınıfı. Bu yönerge, sessiz bir ClickOnce uygulamasını yükleyen özel bir yükleyici oluşturma işlemini gösterir.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Özel bir ClickOnce Uygulama yükleyici oluşturmak için  
  
1.  ClickOnce uygulamanızı System.Deployment ve System.Windows.Forms öğelerini başvurular ekleyin.  
  
2.  Uygulamanız için yeni bir sınıf ekleyin ve herhangi bir ad belirtin. Bu izlenecek yol adı kullanan `MyInstaller`.  
  
3.  Aşağıdaki `Imports` veya `using` en yeni sınıfınızın.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Sınıfınıza aşağıdaki yöntemi ekleyin.  
  
     Bu yöntemleri çağırmak <xref:System.Deployment.Application.InPlaceHostingManager> dağıtım bildirimini yükleme yöntemleri assert uygun izinleri yükleyin, sonra da indirin ve uygulamayı ClickOnce önbelleğine yüklemek için kullanıcı izni isteyin. ClickOnce uygulaması önceden güvenilen veya güven kararını ertelemek özel bir yükleyici belirtebilirsiniz <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> yöntem çağrısı. Bu kod, uygulamanın önceden güvenir.  
  
    > [!NOTE]
    >  Özel yükleyici kod izinlerini önceden güvenerek atanan izinler aşamaz.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Kodunuzu yükleme girişiminde çağrı `InstallApplication` yöntemi. Örneğin, sınıf adlı, `MyInstaller`, çağırabilirsiniz `InstallApplication` şu şekilde.  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bir ClickOnce uygulamasını da güncelleştirme işlemi sırasında gösterilecek bir özel kullanıcı arabirimi de dahil olmak üzere, özel güncelleştirme mantığı ekleyebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Deployment.Application.UpdateCheckInfo>. Bir ClickOnce uygulamasını da standart Başlat menüsü girişi, kısayol ve Program Ekle veya Kaldır giriş kullanarak gizleyebilirsiniz bir `<customUX>` öğesi. Daha fazla bilgi için [ \<entryPoint > öğesi](../deployment/entrypoint-element-clickonce-application.md) ve <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > öğesi](../deployment/entrypoint-element-clickonce-application.md)