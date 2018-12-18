---
title: SharePoint çözümleri için güvenlik | Microsoft Docs
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
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b014c3b4ada42982c41928ca17472e3f585af3ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878771"
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint çözümleri için güvenlik
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint uygulamaları güvenliğini iyileştirmenize yardımcı olacak aşağıdaki özellikleri içerir.

## <a name="safe-control-entries"></a>Güvenli denetim girdileri
 Her SharePoint proje öğesi oluşturulan [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] sahip bir **güvenli denetim girdileri** güvenli temsil eden özellik koleksiyonu denetler. Kendi **güvenli** alt özellik güvenli göz önünde bulundurun denetimleri belirtmenize imkan tanır. Daha fazla bilgi için [proje öğelerinde paketleme ve dağıtım bilgileri sağlayan](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) ve [güvenli Web Bölümleri belirtme](http://go.microsoft.com/fwlink/?LinkId=177521).

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers özniteliği
 Varsayılan olarak, yalnızca uygulamalar çalışma zamanı kod erişim güvenliği (CAS) sistemi tarafından tam güvenilir bir paylaşılan yönetilen kod derleme erişebilirsiniz. AllowPartiallyTrustedCallers özniteliği ile tam olarak güvenilen bir derlemede işaretleme erişmek kısmen güvenilir derlemeler sağlar.

 Sistemin genel derleme önbelleğine dağıtılmaz herhangi bir SharePoint çözümü AllowPartiallyTrustedCallers özniteliği eklenir ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Bu, korumalı alana alınan çözümler ya da SharePoint uygulaması Bin dizinine dağıtılan çözümleri içerir. Daha fazla bilgi için [için Microsoft .NET Framework sürüm 1 güvenlik değişikliklerini](http://go.microsoft.com/fwlink/?LinkId=177515) ve [dağıtma Web Bölümleri SharePoint Foundation'da](http://go.microsoft.com/fwlink/?LinkId=177509).

## <a name="safe-against-script-property"></a>Betik özelliğinde karşı güvenli
 *Betik ekleme* kötü amaçlı olabilecek kod ekleme denetimleri veya Web sayfaları. SharePoint 2010 sitelerine betik ekleme karşı korumaya yardımcı olmak için katkıda bulunanlar görüntüleyemez veya varsayılan olarak Web Bölümleri veya özelliklerini düzenleyin. Bu davranışı SafeAgainstScript adlı SafeControl bir öznitelik tarafından denetlenir. İçinde [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], bu öznitelik bir proje öğesinin ayarlayın **güvenli denetim girdileri** alt özellik **karşı güvenli betik**. Daha fazla bilgi için [proje öğelerinde paketleme ve dağıtım bilgileri sağlayan](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) ve [nasıl yapılır: denetimleri güvenli denetim olarak işaretleme](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Vista ve Windows 7 kullanıcı hesabı denetimi
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] ve [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] kullanıcı hesabı denetimi (UAC) olarak bilinen bir güvenlik özelliği dahil edilip derecelendirilir. SharePoint çözümleri geliştirmek için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] üzerinde [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] ve [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemleri, UAC gerektirir, çalıştırmanızı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir sistem yöneticisi olarak. Gelen **Başlat** menüsünde, kısayol menüsünü açın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ve ardından **yönetici olarak çalıştır**.

 Yapılandırmak için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] her zaman yönetici olarak çalıştırın, kısayol menüsünü açın,'ı seçin, kısayol **özellikleri**, seçin **Gelişmiş** düğmesine **özellikleri**iletişim kutusunu ve ardından **yönetici olarak çalıştır** onay kutusu.

 Daha fazla bilgi için [anlama ve Windows Vista kullanıcı hesabı denetimi yapılandırma](http://go.microsoft.com/fwlink/?LinkID=156476). ve [Windows 7 kullanıcı hesabı denetimi](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>SharePoint izinleri hakkında önemli noktalar
 SharePoint çözümleri geliştirmek için çalıştırın ve SharePoint çözümlerinde hata ayıklama için yeterli izinleri olmalıdır. Bir SharePoint çözümünü test edebilmek için önce gerekli izinlere sahip olmasını sağlamak için aşağıdaki adımları uygulayın:

1.  Sistem Yöneticisi olarak kullanıcı hesabınızı ekleyin.

2.  SharePoint server için Grup yöneticisi olarak kullanıcı hesabınızı ekleyin.

    1.  SharePoint 2010 Merkezi Yönetim'i seçin **Grup Yöneticileri grubunu Yönet** bağlantı.

    2.  Üzerinde **grup yöneticileri** sayfasında **yeni** menü seçeneği

3.  Kullanıcı hesabınızı eklemek için WSS_ADMIN_WPG grubu.

## <a name="additional-security-resources"></a>Ek güvenlik kaynakları
 Güvenlik sorunları hakkında daha fazla bilgi için aşağıdakilere bakın.

### <a name="visual-studio-security"></a>Visual Studio güvenliği

-   [Güvenlik ve kullanıcı izinleri](http://go.microsoft.com/fwlink/?LinkId=177503)

-   [Yerelde ve .NET Framework kodunda güvenlik](http://go.microsoft.com/fwlink/?LinkId=177504)

-   [.NET Framework'te güvenlik](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>SharePoint güvenlik

-   [SharePoint Foundation Yönetim ve güvenlik](http://go.microsoft.com/fwlink/?LinkId=177501)

-   [SharePoint güvenlik kaynağı merkezi](http://go.microsoft.com/fwlink/?LinkId=177498)

-   [Web Bölümleri SharePoint Foundation'da güvenliğini sağlama](http://go.microsoft.com/fwlink/?LinkId=177511)

-   [Web uygulaması güvenliği geliştirmeye: Tehditler ve Önlemler Kılavuzu](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>Genel güvenlik

-   [MSDN güvenlik geliştirme yaşam döngüsü](http://go.microsoft.com/fwlink/?LinkID=147149)

-   [Güvenli bir ASP.NET uygulamaları: Kimlik doğrulaması, yetkilendirme ve güvenli iletişim](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)