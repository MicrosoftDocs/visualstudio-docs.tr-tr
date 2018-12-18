---
title: SharePoint araçlarını Visual Studio'da genişletme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f360982f26cf2eb9ffe26678743bb514d9606ae7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890681"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>SharePoint araçlarını Visual Studio'da genişletme
  Visual Studio'da SharePoint araçları birçok uygulama geliştirme senaryosu gereksinimlerini karşılayın. Ancak, bunlar burada, sizin veya diğer geliştiriciler gerektiren işlevleri sağlamaz çalışmaları fark edebilirsiniz. Bu durumlarda, ihtiyacınız olan işlevleri oluşturmak için SharePoint araçları genişletebilirsiniz.

## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint araçlarını genişletmek nasıl
 SharePoint Proje sistemi genişletebilir ve **SharePoint bağlantıları** düğümünde **Sunucu Gezgini** penceresi.

### <a name="extend-the-sharepoint-project-system"></a>SharePoint Proje sistemini genişletme
 Visual Studio Proje şablonları ve öğe şablonları, SharePoint çözümleri oluşturmak için kullanabileceğiniz bir dizi içerir. Örneğin, Olay alıcıları, liste tanımları, iş akışları ve Web bölümleri için şablonlar vardır. Ancak, kendi alanlar veya özel eylemler gibi SharePoint bileşenleri oluşturmak için SharePoint proje öğelerinin türlerini tanımlayabilirsiniz. SharePoint projeleri için uzantıları oluşturabilirsiniz ve ayrıca Visual Studio'da yüklü SharePoint proje öğesi türleri için uzantıları oluşturabilirsiniz.

 Daha fazla bilgi için [SharePoint Proje sistemini genişletmek](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme
 Visual Studio'da kullanabileceğiniz **SharePoint bağlantıları** düğümünde **Sunucu Gezgini** birçok bileşenlerin bir veya daha fazla yerel SharePoint sitelerine bir hiyerarşik ağaç görünümünde görüntülemek için pencere. Ayrıca genişletebilirsiniz **SharePoint bağlantıları** aşağıdaki yollarla düğüm:

- Kendi düğüm ekleyerek. Bu, varsayılan olarak görüntülenmez SharePoint siteleri bileşenlerinin görüntülemek istiyorsanız kullanışlıdır.

- Var olan düğümleri genişleterek. Örneğin, var olan bir düğüme yeni bir alt düğüm ekleyebilirsiniz veya bir düğüm için bir kısayol menü öğesi ekleme ve bir geliştirici menü öğesini tıkladığında görevleri.

  Daha fazla bilgi için [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Geliştirme bilgisayar gereksinimleri
 SharePoint araçları için uzantıları oluşturmak için geliştirme bilgisayarınıza Visual Studio'da SharePoint çözümleri oluşturmak için aynı gereksinimleri karşılamalıdır.

 Ayrıca, yüklemenizi öneririz [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. SDK'sı, proje şablonları ve Visual Studio genişletmek için kullanabileceğiniz araçları içerir. Özellikle, SDK, Visual Studio Uzantısı (VSIX) paketini bir kolayca oluşturmak için kullanabileceğiniz bir proje şablonu içerir. VSIX paketlerini, Visual Studio uzantıları Visual Studio'da dağıtmak için tercih edilen yoludur. VSIX paketlerini kullanarak tüm SharePoint araç uzantıları dağıtılması gerekir. İzlenecek bu belgedeki tüm sahip olduğunuzu varsaymaktadır [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] yüklü.

 Visual Studio SDK'yı yüklemek için bkz [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md). Visual Studio uzantıları hakkında daha fazla bilgi için bkz: [Visual Studio uzantıları geliştirme başlangıç](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Araç uzantılarının programlama modeline SharePoint genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [SharePoint Proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint araç uzantıları için programlama kavramları ve Özellikler](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Başvuru &#40;SharePoint araçları genişletilebilirliği&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Uzantıları Visual Studio'da SharePoint araçları için hata ayıklama](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)