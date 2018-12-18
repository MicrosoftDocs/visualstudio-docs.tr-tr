---
title: Korumalı arasındaki farklar ve Grup çözümleri | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 282fe23a9a586d79b745efec99bc014e88777fd6
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326338"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Korumalı arasındaki farklar ve Grup çözümleri
  Bir SharePoint çözüm derlediğinizde, SharePoint sunucusuna dağıtır ve hata ayıklamak için bir hata ayıklayıcı ekler. Çözüm hata ayıklamak için kullanılan işlem Korumalı çözüm özelliğinin ayarına bağlıdır: Korumalı çözüm ya da Grup çözümü.  
  
 Daha fazla bilgi için bkz: [Korumalı çözüm değerlendirmeleri](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Küme çözümleri
 IIS çalışan işlemi (W3WP.exe) barındırılan, küme çözümleri tüm grubu etkileyebilir kodu çalıştırın. SharePoint geri çeker veya IIS çalışan işlem tarafından kilitlenmiş dosyaları bırakılamıyor amacıyla özellik dağıtır önce korumalı Çözümle özelliği "grubu çözüm için" olarak ayarlanmış bir SharePoint projenin hata ayıklamasını yaparken, sistemin IIS uygulama havuzu geri dönüştürüldüğünde. SharePoint Proje site URL'si hizmet veren yalnızca IIS uygulama havuzu geri dönüştürülmeden.  
  
## <a name="sandboxed-solutions"></a>Korumalı alana alınan çözümler
 SharePoint kullanıcı kodu çözüm çalışan işlem (SPUCWorkerProcess.exe) barındırılan, korumalı çözümler yalnızca çözüm site koleksiyonunu etkileyebilir kodu çalıştırın. Korumalı çözümler IIS çalışan işlemindeki çalıştırmayın çünkü IIS uygulama havuzu ne IIS sunucusunu yeniden başlatmanız gerekir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcı SharePoint SPUserCodeV4 hizmetinde otomatik olarak tetikler SPUCWorkerProcess işlemi ve denetimleri ekler. Çözüm en son sürümünü yüklemek için Geri Dönüşüm SPUCWorkerProcess işlemi için gerekli değildir.  
  
## <a name="either-type-of-solution"></a>Her iki tür bir çözüm
 Her iki çözüm türüyle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayrıca istemci tarafı komut dosyası hata ayıklamayı etkinleştirmek için tarayıcıya hata ayıklayıcı ekler. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Bu amaçla altyapısı ayıklamasını kullanır. Komut dosyası hata ayıklamayı etkinleştirmek için istendiğinde varsayılan tarayıcı ayarlarını değiştirmeniz gerekir.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcı geçerli site çalıştıran yalnızca W3WP veya SPUCWorkerProcess işlemleri için ekler. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca yönetilen COM Plus ve iş akışı motorları hata ayıklama ekler.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md)   
 [Derleme ve SharePoint çözümlerini hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md)  
  
