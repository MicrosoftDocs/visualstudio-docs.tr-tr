---
title: Sağlanan hizmetlerin (kaynak denetimi VSPackage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a52ffa7067a91582d8bfe31e09d6b03be54c4ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129608"
---
# <a name="services-provided-source-control-vspackage"></a>Sağlanan hizmetlerin (kaynak denetimi VSPackage)
Hizmetleri üzerinden işlevselliği VSPackages arasında ve Visual Studio tümleşik geliştirme ortamı (IDE) ve yüklü VSPackages arasında paylaşılan birincil sistemdir. Hizmetler ve önemine Visual Studio IDE içinde ayrıntılı açıklaması için bkz:[kullanma ve servisleri](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Kaynak denetimi hizmeti  
 Visual Studio iki katmandan Hizmetleri, IDE düzeyi Hizmetleri ve paket düzeyi hizmetler sağlar. Visual Studio IDE yerel IDE düzeyi hizmetleri sağlar. Kaynak denetimi paketi bu hizmetlerden bazılarını kullanır. Kaynak denetimi paketi bir VSPackage olarak kendi özel kaynak denetimi hizmeti sağlayarak kaynak denetim işlevselliğini paylaşır. Kaynak denetimi paketi, Visual Studio IDE tarafından kullanılan bir sözleşme biçiminde tarafından uygulanan kaynak denetimi ile ilgili arabirimler kümesi yalıtır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tasarım öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)