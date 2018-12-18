---
title: Dağıtma, yayımlama ve SharePoint çözüm paketlerini yükseltme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
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
ms.openlocfilehash: 17578fbfb58d354f06e91c78f067d228b92860fe
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327209"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Dağıtma, yayımlama ve SharePoint çözüm paketlerini yükseltme
  Visual Studio'da SharePoint çözüm geliştirmek sonra kendi paketi (.wsp) dosyasını yerel bir SharePoint sunucusuna dağıtma veya bir uzak veya yerel SharePoint sunucuya yayımlayın. Dosyaları dağıtırsanız, paket dosyalarını (.wsp) nasıl dağıtıldığını özelleştirebilirsiniz.  
  
> [!NOTE]  
>  Şu anda, yalnızca korumalı çözümler uzak SharePoint sunucularına yayımlanabilir. Daha fazla bilgi için bkz: [Korumalı çözüm değerlendirmeleri](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploy-publish-and-upgrade"></a>Dağıtma, yayımlama ve yükseltme
 *Dağıtma* Visual Studio'da SharePoint projeden yerel ana bilgisayara yerleşik bir SharePoint çözüm dosyasını kopyalamak için başvuruyor. Dağıtılan bir çözümde dağıtımdan sonra çözüm etkinleştirilirken Internet Information Services (IIS) havuzu geri dönüştürme gibi dağıtım adımları yapılandırmak ve benzeri. Dağıtmak için kullandığınız **dağıtma** komutunu **yapı** menüsü. Daha fazla bilgi için bkz: [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) ve [nasıl yapılır: dağıtma ve bir SharePoint çözümünü yerel SharePoint sitesine yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Yayımlama* uzak bir SharePoint korumalı bir SharePoint çözüm dosyasını karşıya yükleme için başvuruyor site; diğer bir deyişle, başka bir sistem üzerinde bulunan bir site. Bir SharePoint Korumalı çözüm dosya yerel bir SharePoint sitesine yayımlayabilirsiniz ancak yayımlanan site yerel veya uzak olup olmadığına bakılmaksızın, kendi dağıtım adımları yapılandıramazsınız.  
  
 *Yükseltme* var olan uzaktan veya yerel olarak yayımlanan SharePoint çözüm güncelleştirmeye başvuruyor. Visual Studio'da SharePoint çözüm için herhangi bir değişiklik yapıldıktan sonra çözümü yeniden yayımlamanız çözümün paket dosyası adı değiştirin ve sonra başarıyla yeniden yayımlar çözümünü Yükselt. Yerel olarak yayımlanmış bir çözüm yeniden yayımlarsanız, varolan çözüm dosyasını üzerine yazabilirsiniz.  
  
## <a name="deploy-packages"></a>Paketlerini dağıtma
 Geliştirme bilgisayarınızda test ve hata ayıklama için SharePoint sunucusuna paket dosyalarını dağıtabilirsiniz. Seçerek başka bir bilgisayara yüklemek için bir paket dosyası da oluşturabilirsiniz **dosya sistemi Yayımla** seçenek düğmesini **Yayımla** iletişim kutusu. Paket oluşturulur ve belirtilen yerel dosya yolu kopyalanır. Bir SharePoint çözümünü yerel sunucuya dağıtmak için kullandığınız **dağıtma** komutunu **yapı** menüsü. Daha fazla bilgi için bkz: [nasıl yapılır: dağıtma ve bir SharePoint çözümünü yerel bir SharePoint sitesine yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Bir listesi tanımını dağıtma, olay alıcı eklemek ve özellik Tasarımcısı ve paket tasarımcısını kullanmak öğrenmek için bkz: [izlenecek yol: Proje Görev listesi tanımını dağıtma](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customize-the-deployment-process"></a>Dağıtım işlemi özelleştirme
 Aşağıdaki tabloda, hata ayıklama ve bir SharePoint çözümünü dağıtırken kullanabileceğiniz iki dağıtım yapılandırması gösterilmektedir.  
  
|Dağıtım Yapılandırması|Açıklama|  
|------------------------------|-----------------|  
|Varsayılan|Varsayılan dağıtım yapılandırması. Aşağıdaki dağıtım adımlar gerçekleştirilir:<br /><br /> 1.  Dağıtım öncesi komutunu çalıştırın.<br />2.  IIS uygulama havuzu geri dönüşüm.<br />3.  Çözümünü ayıkla.<br />4.  Çözümü ekleyin.<br />5.  Özellikleri etkinleştirin.<br />6.  Dağıtım sonrası komutunu çalıştırın.<br /><br /> Bir paketi kaldırıldığında, aşağıdaki geri çekilmesi adımlar gerçekleştirilir.<br /><br /> 1.  IIS uygulama havuzu geri dönüşüm.<br />2.  Çözümünü ayıkla.|  
|Etkinleştirme yok|Bu dağıtım yapılandırması aynı adımları varsayılan yapılandırma olarak çalışır, ancak etkinleştirme adımı atlar.|  
  
 Tek bir adım tamamlamak ya da dağıtım işlemindeki adımları sırasını değiştirmek için kendi dağıtım yapılandırmaları oluşturabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  

 Önce ve dağıtımdan sonra çalıştırılacak komut de ekleyebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: ayarlama SharePoint dağıtım komutlarını](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publish-packages-to-a-remote-or-local-server"></a>Paketleri bir uzak veya yerel sunucuya yayımlayın
 Menü çubuğunda, uzak bir sunucuya korumalı bir SharePoint çözüm yayımlamaya seçin **yapı**, **Yayımla**ve ardından **Yayımla** iletişim kutusunda, seçin**SharePoint sitesi için Yayımlama** seçenek düğmesi, uzak sunucunun URL'sini gibi sağlama **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 Bir SharePoint çözümünü yerel bir sunucuya yayımlamak için **Yayımla** iletişim kutusunda, seçin **dosya sistemi Yayımla** seçenek düğmesi, bir yerel sistem yolu sağlar.  
  
 Bir çözüm başarıyla SharePoint'e yayımlar sonra çözüm görünür **çözüm Galerisi** Burada, etkinleştirebilir. Daha fazla bilgi için bkz: [nasıl yapılır: dağıtma, yayımlama ve uzak bir sunucudaki SharePoint çözümlerini yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrade-published-packages"></a>Yükseltme yayımlanan paketleri
 Visual Studio'da SharePoint projesi için herhangi bir değişiklik yaparsanız yayımlandıktan sonra yayımlanan paket değişiklikleri içerecek şekilde yükseltilmesi gerekir. Başarıyla yükseltmek için bir paket benzersiz bir ad olmalıdır. Aynı ada sahip bir paketi bir hata uyarısı - var olan bir uygulama güncelleştirilirken hangi oluşabilir - SharePoint sitesinde bulunursa, dosya adına çakışıyor ve paketi yeniden adlandırın olanak tanır. Yayınlanmasını sonra yeni paketi SharePoint sitesinde görünür ve yükseltilebilir. Yükseltilen paket eski paketi verileri kullanarak çözüm güncelleştirir ve SharePoint çözümde etkinleştirir. Daha fazla bilgi için bkz: [nasıl yapılır: dağıtma, yayımlama ve uzak bir sunucudaki SharePoint çözümlerini yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
