---
title: 'Nasıl yapılır: dağıtma, yayımlama ve yükseltme uzak bir sunucudaki SharePoint çözümlerini | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fbd21016d00bdfecfcb606e9fe2b720ab97bf3d0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120438"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Nasıl yapılır: dağıtma, yayımlama ve uzak bir sunucudaki SharePoint çözümlerini yükseltme
  SharePoint çözümleri için yerel sistem dağıtımına ek olarak, korumalı SharePoint çözümlerini uzak siteleri veya yerel SharePoint siteleri için yayımlayabilirsiniz. Uzak yayımlama işlemi kopyaları *.wsp* dosyasını SharePoint sunucusuna çözümü yükler ve ardından çözümü etkinleştirin olanak tanır. Kendisine değişiklikler yapıldıktan sonra uzak bir SharePoint çözüm yüklemesi yükseltme yapabilirsiniz.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Korumalı bir SharePoint çözüm uzak SharePoint sunucusuna yayımlamak için  
  
1.  İçinde **Çözüm Gezgini**, yayımlama ve ardından istediğiniz korumalı SharePoint proje için kısayol menüsünü açın **Yayımla**.  
  
2.  İçinde **Yayımla** iletişim kutusunda, seçin **SharePoint sitesi için Yayımlama** seçenek düğmesi ve bir URL çevrimiçi yayımlama bir site için gibi girin: `https://mytestsite.sharepoint.microsoftonline.com`.  
  
3.  Seçin **Çözüm Galerisi'ne yayımladıktan sonra tarayıcıda açın** çözümlerinde listesini görüntülemek için seçenek düğmesi **çözüm Galerisi** yayımlama sonra sayfa.  
  
4.  Seçin **Yayımla** düğmesi.  
  
5.  Kullanıcı kimlik doğrulaması gerekli olduğunda uzak sunucuya oturum açın.  
  
     Visual Studio'da yayımlama ilerleme görünür **çıkış** penceresi. İşlem tamamlandığında, çözüm (*.wsp*) dosyası uzak SharePoint sunucusuna yüklenir. SharePoint'te kullanılabilmesi için önce ancak bunu hala etkinleştirilmesi gerekir.  
  
6.  Üzerinde **çözüm Galerisi** sayfasında, SharePoint uygulama seçin ve ardından Şeritteki belirtin **etkinleştirme** düğmesi.  
  
7.  İçinde **etkinleştirme çözüm** Seç iletişim kutusu, Şerit üzerindeki **etkinleştirme** yeniden düğmesi.  
  
     **Durum** sütunu **çözüm Galerisi** sayfa uygulama etkin olduğunu gösterir.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Korumalı bir SharePoint çözüm uzak bir SharePoint sunucusuna yükseltmek için  
 Korumalı bir SharePoint çözüm zaten uzak bir sunucuda yayımladıysanız, şu işlem uygulaması'na değişiklikleri yaptıktan sonra yükseltme sağlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  SharePoint paketinde yeniden adlandırma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Bunu yapmak için **Çözüm Gezgini** paketini açın. Görünür **paket Explorer**.  
  
2.  İçinde **paket Explorer**, **adı** kutusunda, paket adı benzersiz bir adla değiştirin.  
  
3.  Projeyi kaydedin.  
  
4.  İçinde **Çözüm Gezgini**projesi için kısayol menüsünü açın ve ardından **Yayımla**.  
  
5.  İçinde **Yayımla** iletişim kutusunda, seçin **SharePoint sitesi için Yayımlama** seçenek düğmesi ve çözüm kaydettiğiniz yere uzak sunucusu için URL'yi eksikse, daha sonra girin.  
  
6.  Seçin **Çözüm Galerisi'ne yayımladıktan sonra tarayıcıda açın** çözümlerinde listesini görüntülemek için seçenek düğmesi **çözüm Galerisi** yayımlama sonra sayfa.  
  
7.  Seçin **Yayımla** düğmesi.  
  
8.  Kullanıcı kimlik doğrulaması gerekli olduğunda uzak sunucuya oturum açın.  
  
     Uzak sunucuya yakın zamanda oturum, kimlik doğrulaması gerekli olabilir değil.  
  
     Aynı ada sahip uygulamanın daha eski sürümü hala SharePoint sunucusu üzerine varsa, SharePoint sunucusunda aynı ada sahip bir paket zaten bir hata alırsınız. Yayımlamadan önce benzersiz bir ad için paketi yeniden adlandırmanız gerekir.  
  
9. Yeni uygulama SharePoint'te seçin ve ardından Şeritteki **yükseltme** düğmesi.  
  
10. İçinde **yükseltme çözüm** Seç iletişim kutusu, Şerit üzerindeki **yükseltme** yeniden düğmesine tıklayın. **Durum** sütunu **çözüm Galerisi** sayfa şimdi belirtmek uygulama etkin olduğunu.  
  
     Çözümü eski sürümü devre dışı bırakıldı, çözümü yeni sürümü, eski çözümden tutulan verilerle yükseltilir ve yeni bir çözüm SharePoint'te etkinleştirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: dağıtma ve bir SharePoint çözümünü yerel bir SharePoint sitesine yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Nasıl yapılır: ekleme ve özellikler ve öğeler bir paket için paket Tasarımcısını kullanarak kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
