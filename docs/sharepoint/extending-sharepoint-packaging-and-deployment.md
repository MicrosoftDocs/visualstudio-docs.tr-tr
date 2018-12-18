---
title: SharePoint paketleme ve dağıtımını genişletme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c6ca4b347cdd733ac166782d8e78dc8e78e0772
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325371"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>SharePoint paketleme ve dağıtımını genişletme
  Paketleme ve dağıtım işlemini SharePoint projeleri için genişletebilirsiniz.
  
## <a name="create-deployment-steps"></a>Dağıtım adımları oluşturma
 Bir SharePoint projesi dağıttığınızda [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] dağıtım adımları, bir dizi yürütür. Visual Studio geri çekilen ve çözümleri ekleme gibi pek çok görev için yerleşik dağıtım adımlarını içerir. Ancak, kendi dağıtım adımları da oluşturabilirsiniz.  
  
 Bir dağıtım adımı oluşturma izlenecek yol için bkz: [izlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="create-deployment-configurations"></a>Dağıtım yapılandırmaları oluşturma
 Dağıtım yapılandırması için belirli bir projenin yürütülür, ancak tüm SharePoint Proje öğeleri etkileyebilecek dağıtım adımları kümesidir. Her dağıtım yapılandırması Proje dağıtıldığında çalıştırılan adımları bir kümesini ve projeyi geri çekilebilir durumda çalıştırılan başka bir kümesini içerir. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] iki yerleşik dağıtım yapılandırmaları içerir, ancak Ayrıca kendi oluşturabilirsiniz. Dağıtım Yapılandırması oluşturduğunuzda, yerleşik dağıtım ve oluşturduğunuz dağıtım adımlar içerebilir.  
  
 Dağıtım yapılandırmasının nasıl oluşturulacağını izlenecek yol için bkz: [izlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Bir SharePoint çözüm dağıtıldığında veya geri çekilebilir kodu çalıştırma
 Bir SharePoint çözüm dağıtıldığında veya geri çekilebilir ek görevleri gerçekleştirmek için olayları işleyebilirsiniz. Visual Studio aşağıdaki senaryolarda işleyebilir olaylar oluşur:  
  
-   Önce ve sonra her bir dağıtım adımı için bir SharePoint proje öğesi yürütülür. Daha fazla bilgi için bkz: [nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   İlk ve son bir SharePoint projesi dağıtıldığında veya geri çekilebilir sonra. Daha fazla bilgi için bkz: [nasıl yapılır: bir SharePoint projesi dağıtıldığında veya geri çekilebilir kodu çalıştırma](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
## <a name="handle-deployment-conflicts"></a>Dağıtım çakışmalarını işleme
 SharePoint Proje öğeleri, modüller, Web bölümleri, liste örnekleri ve içerik türleri gibi bazı türleri yerleşik dağıtım Çakışma çözümlemesi sağlar. Bu proje öğelerinden birini içeren bir çözümü dağıttığınızda, Visual Studio önce bir dosya adı, URL veya kimliği olan SharePoint sitesi üzerinde dağıttığınız öğesi bir dosya olarak zaten olup olmadığını denetler. Bir çakışma varsa, Visual Studio otomatik olarak bir çakışmayı çözebildiğinde veya çakışmayı veya dağıtımı iptal Visual Studio'nun isteyip istemediğinizi belirlemenizi isteyebilir. Daha fazla bilgi için bkz: [sorun giderme SharePoint paketleme ve dağıtım](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Bu özellik olup olmadığını denetler ve dağıtım çakışmaları çözümlenen kendi kodunuzu sağlayarak genişletebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: dağıtım çakışmalarını işleme](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Komut satırı işlemlerini önce veya bir proje dağıtıldıktan sonra Çalıştır
 Bir SharePoint çözüm dağıtıldığında bir komut satırı işlemini çalıştırmak istiyorsanız, ayarlayabileceğiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> özelliklerini bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesnesi. Visual Studio önce ve projeyi dağıtıldıktan sonra bu komutları yürütür.  
  
 Bazı durumlarda, dağıtım çakışmaları görebilirsiniz. Çakışmaları çözümlemek için birkaç farklı yolu vardır. Daha fazla bilgi için bkz: [sorun giderme SharePoint paketleme ve dağıtım](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="customize-validation-rules"></a>Doğrulama kuralları özelleştirme
 Bir çözüm paketi (.wsp) dağıtmadan önce özel özellik ve paket özelliği veya paket geçerli olduğunu doğrulamak için doğrulama kuralları oluşturabilirsiniz. Örneğin, doğrulama sorunları gidermeye yardımcı olmak için geliştiricilere bilgileri, uyarılar veya hatalar bildirebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: özel özellik ve paket doğrulama kuralları için SharePoint çözümleri oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [İzlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Nasıl yapılır: özel özellik ve paket doğrulama kuralları SharePoint çözümleri için oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [SharePoint Proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
