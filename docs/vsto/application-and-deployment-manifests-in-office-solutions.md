---
title: Office çözümlerinde uygulama ve dağıtım bildirimleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb4386469e02934045d9f1da45fe515dc9af5da2
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53247965"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Office çözümlerinde uygulama ve dağıtım bildirimleri
  Bir uygulama bildirimi bulun ve kendi derlemeleri güncelleştirmek için bir Office çözümü tarafından kullanılan bilgileri sağlayan bir XML dosyasıdır. Bir uygulama bildirimi, derlemeler ve uygulama bildirimi en güncel sürümünü bulmak için gereken bilgileri sağlar sunucuda depolanan bir XML dosyası olan bir dağıtım bildirimi ile kullanılabilir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Office çözümleri için bildirim yapısı  
 Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan Microsoft Office çözümleri için tüm bildirimleri standart ClickOnce şemasını temel alır. Office çözümleri dağıttığınızda, hem belge düzeyi ve VSTO eklentisi projeleri için uygulama bildirimleri ClickOnce önbellekte yer alır. Dağıtım bildirimleri, istemci bilgisayara kopyalanmaz.  
  
 Uygulama ve dağıtım bildirimlerinin Office projeleri için içeriği hakkında bilgi için [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md) ve [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).  
  
## <a name="create-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini oluşturma  
 Uygulama bildirimleri oluşturma işleminin bir parçası otomatik olarak oluşturulur. Belge düzeyi projeyi her derlediğinizde, dağıtım bildiriminin konumunu belgeye bir özel belge özelliği olarak eklenir. VSTO eklentileri için dağıtım bildiriminin konumunu kayıt defterinde depolanır.  
  
 Hakkında daha fazla bilgi için **Yayımlama Sihirbazı**, bkz: [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Office çözümleri ile çalışma hakkında daha fazla bilgi bildirimleri için bkz: [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)   
 [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Uygulama bildirimi](/visualstudio/deployment/clickonce-application-manifest)   
 [ClickOnce dağıtım bildirimi](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  