---
title: 'Nasıl yapılır: dağıtma ve bir SharePoint çözümünü yerel bir SharePoint sitesine yayımlama | Microsoft Docs'
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
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e288b5a284ca4155cf70f4458b5b490ca4289cbe
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120569"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Nasıl yapılır: dağıtma ve bir SharePoint çözümünü yerel bir SharePoint sitesine yayımlama
  Dağıtabilir veya SharePoint çözümleri geliştirme bilgisayarınızda yerel bir SharePoint server yayımlama. Dağıtım işlemi kopyaları *.wsp* dosyasını SharePoint sunucusuna çözümü yükler ve özellikleri etkinleştirir. Yayımlama işlemi yalnızca kopyaları *.wsp* dosyasını SharePoint sunucusuna ve yükler. SharePoint'te etkinleştirmek için el ile etkinleştirmeniz gerekir.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Bir SharePoint çözümünü yerel SharePoint sunucusuna dağıtmak için  
  
1.  İçinde **Çözüm Gezgini**, dağıtmak istediğiniz projesini seçin.  
  
2.  Menü çubuğunda seçin **yapı**, **çözümü Dağıt**.  
  
     *.Wsp* dosya oluşturulur ve yerel SharePoint sunucu üzerinde yüklü. Ayrıca, özellikleri etkinleştirilir.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Bir SharePoint çözümünü yerel SharePoint sunucusuna yayımlamak için  
  
1.  İçinde **Çözüm Gezgini**, yayımlama ve ardından istediğiniz SharePoint proje için kısayol menüsünü açın **Yayımla**.  
  
2.  İçinde **Yayımla** iletişim kutusunda, seçin **dosya sistemi Yayımla** seçenek düğmesi.  
  
3.  İçinde **hedef konumu** metin kutusunda, yerel bir yol girin ve ardından **Yayımla** düğmesi.  
  
     Visual Studio'da yayımlama ilerleme görünür **çıkış** penceresi. İşlem tamamlandığında, çözüm (*.wsp*) dosyası yerel SharePoint sunucusuna yüklenir. Ancak, bunu hala SharePoint'te kullanılacak etkinleştirilmesi gerekir. Çözüm dosyası zaten varsa, bir hata oluşur ve mevcut dosyanın üzerine yazmak isteyip istemediğinizi sorar. Paket yükseltme hakkında daha fazla bilgi için Uzak paketlerinde yükseltme bölümüne bakın [nasıl yapılır: dağıtma, yayımlama ve uzak bir sunucudaki SharePoint çözümlerini yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: dağıtma, yayımlama ve uzak bir sunucudaki SharePoint çözümlerini yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Nasıl yapılır: ekleme ve özellikler ve öğeler bir paket için paket Tasarımcısını kullanarak kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
