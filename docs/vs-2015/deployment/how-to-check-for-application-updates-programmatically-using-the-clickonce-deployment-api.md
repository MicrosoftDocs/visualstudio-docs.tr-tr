---
title: "Nasıl yapılır: ClickOnce dağıtım API'sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme | Microsoft Docs"
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
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 1a380d549fa10c3229601a1a9541679c7e3ac1e7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282197"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Nasıl yapılır: ClickOnce Dağıtım API'sini Kullanarak Program Aracılığıyla Uygulama Güncelleştirmelerini Denetleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce dağıtıldıktan sonra bir uygulamayı güncelleştirmek için iki yol sunar. İlk yöntemde, güncelleştirmeleri belirli aralıklarla otomatik olarak denetlemek için ClickOnce dağıtımı yapılandırabilirsiniz. İkinci yöntemde kullanan kod yazabileceğiniz <xref:System.Deployment.Application.ApplicationDeployment> güncelleştirmeleri denetlemek için sınıf tabanlı bir kullanıcı isteği gibi bir olay.  
  
 Aşağıdaki yordamları programlı bir güncelleştirme gerçekleştirmek için gereken kodu gösterir ve ayrıca programlı güncelleştirme denetimlerini etkinleştirmek için ClickOnce dağıtımını yapılandırmak nasıl açıklar.  
  
 ClickOnce uygulaması programlı bir şekilde güncelleştirmek için güncelleştirmeler için bir konum belirtmeniz gerekir. Bu bazen bir dağıtım sağlayıcısı olarak adlandırılır. Bu özellik hakkında daha fazla bilgi için bkz. [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Ayrıca, uygulamanızı bir konumdan dağıtmak, ancak başka bir güncelleştirme için aşağıda açıklanan tekniği kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Güncelleştirmeleri programlı olarak denetlemek için  
  
1.  Tercih edilen görsel veya komut satırı araçlarını kullanarak yeni bir Windows Forms uygulaması oluşturun.  
  
2.  Düğme, menü öğesi oluşturmak veya diğer kullanıcı arabirimi öğesi, kullanıcılarınıza güncelleştirmeleri denetlemek için istediğiniz. Bu öğenin olay işleyicisinden denetlemek ve güncelleştirmeleri yüklemek için aşağıdaki yöntemi çağırın.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3.  Uygulamanızı derleyin.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Program aracılığıyla güncelleştirme kontrolü yapana bir uygulamayı dağıtmak için Mage.exe kullanma  
  
-   Mage.exe içinde açıklandığı gibi kullanarak uygulamanızı dağıtmak için yönergeleri izleyin [izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Dağıtım bildirimi oluşturmak için Mage.exe çağrılırken komut satırı anahtarı kullandığınızdan emin olun `providerUrl`ve burada ClickOnce güncelleştirmeleri denetle URL'sini belirtin. Gelen uygulamanızı güncelleştirme yapacaksanız [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), örneğin, dağıtım bildirimi oluşturmak için çağrı şuna benzeyebilir:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Program aracılığıyla güncelleştirme kontrolü yapana bir uygulamayı dağıtmak için MageUI.exe kullanma  
  
-   Mage.exe içinde açıklandığı gibi kullanarak uygulamanızı dağıtmak için yönergeleri izleyin [izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Üzerinde **dağıtım seçenekleri** sekmesinde, belirleyin **Başlat konumu** alan uygulama bildiriminin ClickOnce güncelleştirmeleri kontrol etmelidir. Üzerinde **Güncelleştirme Seçenekleri** sekmesi, NET **bu uygulama güncelleştirmeleri denetlesin** onay kutusu.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulamanızı programlı güncelleştirmeyi kullanmak için tam güven izinleri olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce Uygulamalarını Yayımlama](../deployment/publishing-clickonce-applications.md)



