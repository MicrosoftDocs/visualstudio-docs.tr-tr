---
title: Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ededaae56e9d09072e236036c15a2ccd662a952e
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326471"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri
  SharePoint Tasarımcısı'nda oluşturulan yeniden kullanılabilir iş akışlarını almak için yeniden kullanılabilir SharePoint 2010 iş akışı içe proje şablonunda kullanmak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Bu şablonu içeri aktarır bir *bildirim temelli* *iş akışı* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-yalnızca) dosyasına dönüştüren bir *iş akışı kodu*, ile ya da geliştirebilirsiniz bir iş akışı olduğu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] kodu. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [İzlenecek yol: bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio'ya içeri aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Ancak, SharePoint 2010 iş akışı yeniden kullanılabilir alma şablonu yalnızca küme çözümleri içeri aktarabilirsiniz. Korumalı bir çözüm olarak, iş akışınızı dağıtmak istiyorsanız, SharePoint 2010 çözüm paket Aktar şablonu içeri aktarın. Ancak, bunu yaparak, iş akışı kodu kendisine dönüştürülemiyor ve bu şekilde değiştirmek mümkün olmaz.  
  
## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Yeniden kullanılabilir iş akışlarını içeri aktarma yeniden kullanılabilir iş akışı şablonu kullanarak içeri aktarma
 Yeniden kullanılabilir iş akışı alma yeniden kullanılabilir SharePoint 2010 iş akışı şablonu kullanarak içe aktarıyorsanız, çalıştırmak veya çözüm gibi diğer değiştirmek [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint çözüm, ancak bazı öğeler el ile düzeltmeniz olabilir.  
  
### <a name="import-task-forms"></a>Görev formları alma
 İçeri aktarma yeniden kullanılabilir SharePoint 2010 iş akışı Proje şablonu tüm başlatma ve ilişkilendirme formları alır, ancak kodu iş akışı şema yalnızca bir görev formu izin verdiği için yalnızca bir görev formu alır. Tüm ek görev forms özgün iş akışı çözümden içine konur **diğer içe aktarılan dosyaları** klasöründe **Çözüm Gezgini**.  
  
## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>İçeri aktarma SharePoint 2010 çözüm paketi şablonunu kullanarak yeniden kullanılabilir iş akışlarını içeri aktarma
 Yeniden kullanılabilir iş akışı SharePoint 2010 çözüm paket Aktar şablonunu kullanarak içe aktarıyorsanız, aşağıdaki sorunları dikkate almanız gerekir:  
  
-   İş akışını içeri aktardıktan sonra hemen dağıtabilir ve bunu çalıştırabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] seçerek **F5** anahtarı. Ancak, içeri aktarılan çözümde iş akışındaki herhangi bir şey değiştirirseniz, dağıtmak ve iş akışını çalıştırmak için önce öğeleri projede el ile düzeltmeniz gerekebilir.  
  
-   İş akışı bildirim temelli olduğundan, kod eklenemez. İş akışı kodu akışına dönüştürmek için içine almanız gerekir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yeniden kullanılabilir SharePoint 2010 iş akışı alma şablonunu kullanarak.  
  
-   Tasarım görünümünde iş akışı Tasarımcısı (.xoml) dosyasını düzenleyebilir, ancak iş akışı Tasarımcısı'nı false hataları görüntüler için kaynak görünümünde Düzenle önerilir.  
  
-   İş akışında hata ayıklama için bildirim temelli içerik çalışmaz. Kesme noktaları kümesinde [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] değil ulaştı.  
  
## <a name="import-globally-reusable-workflow-solutions"></a>Genel olarak yeniden kullanılabilir iş akışı çözümleri alın
 Genel olarak yeniden kullanılabilir iş akışlarını içeri aktarma yeniden kullanılabilir SharePoint 2010 iş akışı şablonu kullanarak aktarılamaz. Genel olarak yeniden kullanılabilir iş akışı almak için bir genel olmayan yeniden kullanılabilir iş akışı ile dönüştürmeniz gerekir veya SharePoint 2010 çözüm paket Aktar şablonu kullanmak zorunda.  
  
 İş akışı dönüştürmek için SharePoint Tasarımcısı'nda genel yeniden kullanılabilir iş akışı bir kopyasını oluşturun (iş akışı için kısayol menüsünü açarak ve ardından seçme **kopya olarak Kaydet**). Yeni yeniden kullanılabilir iş akışını alma yeniden kullanılabilir SharePoint 2010 iş akışı şablon ile içeri aktarma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Değişiklik yapmadan genel yeniden kullanılabilir iş akışını içeri aktarmak için SharePoint 2010 çözüm paket Aktar şablonunu kullanın. Bu yöntemi kullanırsanız, iş akışı kodu iş akışına dönüştürülmedi ve bildirim temelli bir iş akışı kalır.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [İzlenecek yol: bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio'ya içeri aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  
