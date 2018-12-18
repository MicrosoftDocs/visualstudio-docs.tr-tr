---
title: Kullanarak ve hizmetleri sağlayan | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 351b5b5c0ab32ab7e8267864eddaae10459a23bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138346"
---
# <a name="using-and-providing-services"></a>Kullanarak ve hizmetleri sağlar
İki VSPackages arasında bir sözleşme hizmetidir. Bir VSPackage arabirimleri kullanmak üzere başka bir VSPackage için belirli bir dizi sunar. Örneğin, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sunar <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> isteğe bağlı olarak tüm VSPackage yükleri hizmet. Bu hizmet sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> etkinlik günlüğü yazmak için kullanılan arabirim. Daha fazla bilgi için bkz: [nasıl yapılır: etkinlik günlüğü kullanın](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages tarafından kendi kullanmanın Hizmetleri sunabilir <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> arabirimi...  
  
 Visual Studio aşağıdaki gibi önemli hizmetler sunar:  
  
|IDE hizmeti|Açıklama|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Temel işlevleri, VSPackages ve kayıt defteri ile ilgilenen IDE erişim hizmetleri sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Temel Pencereleme ve araçları ve belge pencereleri oluşturma yeteneği gibi IDE UI ilgili işlevleri sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Projeleri listeleme, yeni projeler oluşturun ve proje değişiklikleri izleme yeteneğini gibi temel çözüm ilgili işlevleri sağlar.|  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)  
 Visual Studio hizmet önemli öğelerini gösterir.  
  
 [Nasıl Yapılır: Hizmet Alma](../extensibility/how-to-get-a-service.md)  
 İstek açıklanmaktadır (kullanabilir) bir hizmet.  
  
 [Nasıl Yapılır: Hizmet Sağlama](../extensibility/how-to-provide-a-service.md)  
 Bir hizmet sağlamak nasıl ele alınmaktadır.  
  
 [Nasıl Yapılır: Zaman Uyumsuz Visual Studio Hizmeti Sağlama](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Zaman uyumsuz bir hizmet sağlamak üzere nasıl ele alınmaktadır.  
  
 [Nasıl Yapılır: Hizmetlerde Sorun Giderme](../extensibility/how-to-troubleshoot-services.md)  
 Sık karşılaşılan sorunlar anlatılmaktadır ve bunların çözümleri sunar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)