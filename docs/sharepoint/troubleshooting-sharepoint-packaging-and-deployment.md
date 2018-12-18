---
title: SharePoint paketleme ve dağıtım sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba6f0a1aff0c263534c17256b7f5cf49ff9c9533
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898063"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>SharePoint paketleme ve dağıtım sorunlarını giderme
  Bu konuda, paketleyebilir ve SharePoint çözümlerini dağıtma karşılaşabileceğiniz çeşitli sorunları kapsar.

## <a name="enable-enhanced-debugging"></a>Gelişmiş hata ayıklamayı etkinleştir
 Visual Studio, SharePoint ve diğer katmanlar arasında tanılamak için yığın izlemesini görüntülemek üzere EnableDiagnostics kayıt defteri anahtarını kullanabilirsiniz. Daha fazla bilgi için [hata ayıklama SharePoint çözümleri](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Çözüm paketine proje çıktısı ekleme
 Proje çıktısını paket Tasarımcısı aracılığıyla bir pakete ekleyebilirsiniz. Ancak, proje çıktısını eklerken, Proje platformunun SharePoint çözüm platformu eşleştiğinden emin olun. Kullanmanızı öneririz **herhangi bir CPU** SharePoint sunucusuna dağıtmak istediğiniz derlemeler için platform hedefi. Daha fazla bilgi için [derleme sayfası, Proje Tasarımcısı &#40;Visual Basic&#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) ve [Gelişmiş derleyici Ayarları iletişim kutusu &#40;Visual Basic&#41;](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).

## <a name="validation-warnings-and-errors"></a>Doğrulama uyarıları ve hataları
 Visual Studio'da SharePoint geliştirme araçları, Çözüm paketinin düzgün biçimlendirildiğini doğrulamak için doğrulama adımlarını gerçekleştirin. Ayrıca özellikleriniz ve paketleriniz için özel doğrulama adımları da oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: özel özellik ve paket doğrulama kuralları için SharePoint çözümleri oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Dağıtım çakışması çözümü
 Bir SharePoint çözümünü dağıttığınızda, sunucu üzerindeki bir öğe adı, URL'si veya kimliği çözüm paketinizdeki bir öğe sahip olduğunda, çakışmaları bulabilirsiniz. Değiştirebileceğiniz **dağıtım çakışması çözümü** özelliği çözümlemek, bildirmek veya modüller, Web bölümleri, liste örnekleri ve içerik türleri için çakışmaları yoksay.

 Aşağıdaki tabloda ayarlarını göstermektedir **dağıtım çakışması çözümü** özelliği.

|Değer|Açıklama|
|-----------|-----------------|
|Otomatik|Çarpışmaları algılar ve çakışmaları otomatik olarak çözer.|
|istemi|Çarpışmaları algılar ve çakışmaları çözmeden önce bunları geliştiriciye bildirir.|
|Yok.|Çarpışmaları algılamaz.|

## <a name="differences-between-f5-deployment"></a>F5 dağıtımı arasındaki farklar
 Kullanırken [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projenizi test ve hata ayıklama için yerel SharePoint sunucusuna dağıtmak için tarafından gerçekleştirilen bazı ek adımlar vardır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

1. Internet Information Service (IIS) uygulamasını dağıtım adımı sırasında sıfırlayın.

2. İş akışlarını otomatik olarak ilişkilendirin.

3. Paket Tasarımcısı'ndaki hiyerarşiye göre özellik etkinleştirme düzenini ayarlayın.

   Daha fazla değişiklik özel dağıtım adımları ekleyebilirsiniz **F5** davranışı. Daha fazla bilgi için [izlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturmak](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>SharePoint sayfasının görüntülenmesini geciktirme görsel web bölümü dağıtırken
 SharePoint sayfası üzerinde bir görsel Web Bölümü Bin klasörüne dağıtılırken görünmesini zaman alıyor [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], veya [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Üst düzey bir klasördeki tüm dosyaları değiştirirseniz [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Bin dizini gibi dizini Web uygulamasının tamamı yeniden derlenir. Bu, 25 işlenecek saniyeye kadar SharePoint sayfasının bir gecikmeye neden olabilir.

### <a name="error-message"></a>hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bu sorunu çözmek için aşağıdaki adımları gerçekleştirin:

1.  KB967535 güncelleştirmesini Microsoft Support makalesini açıklandığı biçimde yükleyin [DÜZELTİN: bir düzeltme iki sorunu Windows Vista ve Windows Server 2008 için IIS 7.0 üzerinde ASP.NET düzeltmek kullanılabilir](http://go.microsoft.com/fwlink/?LinkId=179055).

2.  Aşağıdaki satırı Web.config dosyasına ekleyin:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>SharePoint proje dağıtımı, "çözümdeki cab dosyası ayıklanamadı" hatasıyla başarısız oluyor
 Herhangi bir SharePoint proje öğesi adı parantez varsa, çözümü dağıtımda bir hata ile başarısız olur.

### <a name="error-message"></a>hata iletisi
 'Add Solution' dağıtım adımda hata oluştu: çözümdeki cab dosyası ayıklanamadı.

### <a name="resolution"></a>Çözüm
 Bu sorunu gidermek için SharePoint proje öğelerinin adlarındaki parantezleri kaldırın.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Bir görsel web bölümü farklı bir web uygulamasında bir siteye dağıtırken hata görüntülenir.
 İlk kez bir Web uygulamasında, şirket dışındaki bir siteye bir görsel Web bölümünü dağıtmak şu anda (görsel Web bölümünün SiteUrl özelliğini değiştirerek) dağıtıldığı, hata alırsınız.

### <a name="error-message"></a>hata iletisi
 'Add Solution' dağıtım adımda hata oluştu: [#] kimliği olan bir özellik bu grupta zaten yüklenmiş. Açıkça özelliği yeniden yüklemek için zorlama özniteliğini kullanın.

### <a name="resolution"></a>Çözüm
 Görsel Web Bölümü özelliklerinin SharePoint'teki geri Çekilme nedeniyle bu hata oluşur. Visual Web bölümünü başarıyla dağıtmak için çözümü yeniden seçerek dağıtmak **F5** anahtarı.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>İç içe geçmiş kullanıcı denetimleri dağıtılırken uyarı görünür.
 Bu uyarı, bir kullanıcı denetimi içeren bir görsel Web Bölümü, bir görsel Web bölümü içeren bir kullanıcı denetimi veya başka bir kullanıcı denetimi gibi iç içe geçmiş kullanıcı denetimleri olan bir SharePoint çözümünü dağıttığınızda oluşur. Bu uyarı, Toolbox'tan sürükleyerek ya da kullanarak bir tasarımcıya denetim eklemek isteyip oluşur @Register kaynağı görünümündeki yönergesi.

### <a name="error-message"></a>hata iletisi
 Uyarı 1 öğesi ' [*denetim adı*]' bilinen bir öğe değil. Bu Web sitesinde derleme hatası yok veya web.config dosyası eksikse oluşabilir.

### <a name="resolution"></a>Çözüm
 Varsa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proje sistemi bir iç içe geçmiş kullanıcı denetiminin farkında değil, IntelliSense sağlayamaz ve uyarı gösterir. Proje sistemi bir iç içe geçmiş kullanıcı denetiminin farkında proje oluşturulmaz ve tasarımcı kapatılıp yeniden açılana değil ya da durumunda otomatik geri çekme seçeneği etkinleştirilirse neden olan kullanıcı denetiminin SharePoint kovanından hata ayıklama sonrasında çekilmesini.

 Bu uyarıyı kaldırmak için projeyi oluşturun ve ardından kapatın ve tasarımcıyı yeniden ya da devre dışı bırakma seçeneği proje için otomatik geri çekme. Bunu yapmak için temizlemek **otomatik hata ayıklamadan sonra** onay kutusunu **SharePoint** Proje Özellikleri iletişim kutusu sekmesi.

## <a name="see-also"></a>Ayrıca bkz.
 [Paketleme ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

