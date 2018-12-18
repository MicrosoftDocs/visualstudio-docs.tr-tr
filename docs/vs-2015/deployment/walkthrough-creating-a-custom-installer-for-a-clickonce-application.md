---
title: 'İzlenecek yol: ClickOnce uygulaması için özel bir yükleyici oluşturma | Microsoft Docs'
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
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 16686b0bf53f9e1358d96a7abcfe95f8ed6aac82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222774"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>İzlenecek Yol: ClickOnce Uygulaması için Özel bir Yükleyici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir .exe dosyasını temel alan herhangi bir ClickOnce uygulaması sessizce yüklü ve özel bir yükleyici tarafından güncelleştirildi. Özel bir yükleyici özel iletişim kutuları için güvenlik ve Bakım işlemlerine dahil olmak üzere yüklemesi sırasında özel bir kullanıcı deneyimi uygulayabilirsiniz. Özel yükleyici yükleme işlemlerini gerçekleştirmek için kullandığı <xref:System.Deployment.Application.InPlaceHostingManager> sınıfı. Bu yönerge, sessiz bir ClickOnce uygulamasını yükleyen özel bir yükleyici oluşturma işlemini gösterir.  
  
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
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
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
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bir ClickOnce uygulamasını da güncelleştirme işlemi sırasında gösterilecek bir özel kullanıcı arabirimi de dahil olmak üzere, özel güncelleştirme mantığı ekleyebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Deployment.Application.UpdateCheckInfo>. Bir ClickOnce uygulamasını da standart Başlat menüsü girişi, kısayol ve Program Ekle veya Kaldır giriş kullanarak gizleyebilirsiniz bir `<customUX>` öğesi. Daha fazla bilgi için [ \<entryPoint > öğesi](../deployment/entrypoint-element-clickonce-application.md) ve <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > öğesi](../deployment/entrypoint-element-clickonce-application.md)



