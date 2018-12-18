---
title: 'Nasıl yapılır: GetGlobalService kullanın | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: 5ce0d5657fa65cd727da2b97b3dd24735a81937a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276137"
---
# <a name="how-to-use-getglobalservice"></a>Nasıl yapılır: GetGlobalService kullanın
Bazen bir araç penceresinden bir hizmet almaya veya değil tarihli, aksi takdirde, istediğiniz hizmeti hakkında bilgi sahibi değildir bir hizmet sağlayıcısı ile tarihli kapsayıcı denetimi gerekebilir. Örneğin, etkinlik günlüğünde denetimdeki yazmak isteyebilirsiniz. Bu ve diğer senaryolar hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri sorun giderme](../extensibility/how-to-troubleshoot-services.md).  
  
 Çoğu alabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] statik çağırarak Hizmetleri <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yöntemi.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> herhangi bir VSPackage türetilen ilk kez başlatılan bir önbelleğe alınan hizmet sağlayıcısı dayanan <xref:Microsoft.VisualStudio.Shell.Package> tarihli. Bu koşul karşılandığında, aksi takdirde null bir hizmet için hazırlıklı olmalıdır garanti etmeniz gerekir.  
  
 Neyse ki, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> çoğu zaman düzgün şekilde çalışır.  
  
-   VSPackage yalnızca başka bir Vspackage'e bilinen hizmet sağlıyorsa, hizmet talep eden VSPackage'ı hizmet yüklü sağlama VSPackage'ı önce tarihli.  
  
-   Araç penceresi tarafından VSPackage oluşturduysanız, araç penceresi oluşturulmadan önce VSPackage tarihli.  
  
-   Bir denetim kapsayıcısı VSPackage tarafından oluşturulan bir araç penceresi tarafından barındırılıyorsa, Denetim kapsayıcısı oluşturulmadan önce VSPackage tarihli.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Araç penceresi ya da Denetim kapsayıcısı içinden bir hizmetten alınamıyor  
  
-   Bu kod Oluşturucu, araç penceresi veya denetim kapsayıcısı ekleyin:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Bu kod bir SVsActivityLog hizmeti alır ve kendisine bıraktığı bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> etkinlik günlüğüne yazmak için kullanılan arabirim. Bir örnek için bkz. [nasıl yapılır: etkinlik günlüğü'nün](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: hizmetlerde sorun giderme](../extensibility/how-to-troubleshoot-services.md)   
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)