---
title: Özellik ve paket bildirimleriyle XML birleştirme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3101245d720e9fdd1c4923ea03acd5b2d4db816
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120564"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>XML özellik ve paket bildirimleri birleştirme
  Özellikleri ve paketleri tarafından tanımlanır [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bildirim dosyaları. Bu paket bildirimleri tasarımcıları ve özel üretilen veri birleşimidir [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bildirim şablonunda kullanıcı tarafından girilen. Paketleme zamanında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] özel birleştirmeler [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tasarımcısı tarafından sağlanan ifadelerle [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] paket oluşturmak için [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bildirim dosyası. Benzer öğeleri, daha sonra birleştirme özel durumları, belirtilen özel durum ile birleştirilir önlemek için [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] SharePoint'e dosyaları dağıtmak ve bildirim yapmak için daha küçük ve daha verimli dosyaları sonra doğrulama hataları.  
  
## <a name="modify-the-manifests"></a>Bildirimleri değiştirme
 Özellik veya paket tasarımcıları devre dışı kadar paketlenmiş bildirim dosyaları doğrudan değiştiremezsiniz. Ancak, özel elle ekleyebileceğiniz [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bildirim şablonu öğelerine özellik ve paket tasarımcıları yoluyla veya [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Düzenleyicisi. Daha fazla bilgi için bkz: [nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md) ve [nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Birleştirme işlemi özellik ve paket bildirimi
 Özel öğeleri tasarımcısı tarafından sağlanan öğelerini birlikte birleştirilirken [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aşağıdaki işlemi kullanır. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] her öğe benzersiz bir anahtar değer olup olmadığını denetler. Bir öğenin benzersiz anahtar değeri yoksa, paket bildirim dosyası eklenir. Benzer şekilde, birden çok anahtar olan öğeler birleştirilemiyor. Bu nedenle, bunlar bildirim dosyasının sonuna eklenir.  
  
 Bir öğenin benzersiz bir anahtar varsa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı ve özel anahtarları değerlerini karşılaştırır. Değerleri eşleşirse, bunlar tek bir değer olarak birleştirin. Değerler farklıysa, Tasarımcı anahtar değeri göz ardı edilir ve özel anahtar değeri kullanılır. Koleksiyonlar ayrıca birleştirilir. Örneğin, varsa tasarımcısı tarafından oluşturulan [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ve özel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] hem derlemeleri koleksiyon içerir, paketlenmiş bildirimi yalnızca bir derlemeleri koleksiyonu içerir.  
  
## <a name="merge-exceptions"></a>Özel durumlar birleştirme
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Çoğu Tasarımcısı birleştirir [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] benzer özel birlikte öğeleri [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] öğeleri tek ve benzersiz tanımlayıcı özniteliği sahip oldukları sürece. Ancak, bazı öğeler için gerekli benzersiz tanımlayıcısı eksik [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] birleştirme. Bu öğeleri olarak da bilinir *birleştirme özel durumları*. Bu durumda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] özel birleştirmez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tasarımcısı tarafından sağlanan birlikte öğeleri [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] öğeleri, ancak bunun yerine paket bildirim dosyasının sonuna ekler.  
  
 Özellik ve paket için birleştirme özel durumlar listesine aşağıdadır [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bildirim dosyaları.  
  
|Tasarımcı|XML öğesi|  
|--------------|-----------------|  
|Özellik Tasarımcısı|ActivationDependency|  
|Özellik Tasarımcısı|UpgradeAction|  
|Paket Tasarımcısı|SafeControl|  
|Paket Tasarımcısı|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Özellik bildirimi öğeleri
 Aşağıdaki tabloda, birleştirilebilir tüm özellik bildirim öğeleri ve eşleştirmek için kullanılan kendi benzersiz anahtar listesidir.  
  
|Öğe adı|Benzersiz anahtar|  
|------------------|----------------|  
|Özellik (tüm öznitelikleri)|*Öznitelik adı* (her özniteliği özellik öğesi benzersiz bir anahtar adıdır.)|  
|ElementFile|Konum|  
|ElementManifests/ElementManifest|Konum|  
|Özellikler/özelliği|Anahtar|  
|CustomUpgradeAction|Ad|  
|CustomUpgradeActionParameter|Ad|  
  
> [!NOTE]  
>  Özel CustomUpgradeAction öğesi değiştirmek için tek yolu olduğundan [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Düzenleyicisi değil birleştirme etkisini düşük.  
  
## <a name="package-manifest-elements"></a>Paket bildirim öğeleri
 Aşağıdaki tabloda, birleştirilebilir tüm paket bildirim öğeleri ve eşleştirmek için kullanılan kendi benzersiz anahtar listesidir.  
  
|Öğe adı|Benzersiz anahtar|  
|------------------|----------------|  
|Çözüm (tüm öznitelikleri)|*Öznitelik adı* (her özniteliği çözüm öğesi benzersiz bir anahtar adıdır.)|  
|ApplicationResourceFiles/ApplicationResourceFile|Konum|  
|Derlemeleri/derleme|Konum|  
|ClassResources/ClassResource|Konum|  
|DwpFiles/DwpFile|Konum|  
|FeatureManifests/FeatureManifest|Konum|  
|Kaynakları/kaynak|Konum|  
|RootFiles/RootFile|Konum|  
|SiteDefinitionManifests/SiteDefinitionManifest|Konum|  
|WebTempFile|Konum|  
|TemplateFiles/TemplateFile|Konum|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Dağıtılan dosyaları el ile Ekle
 ApplicationResourceFile ve DwpFiles, gibi bazı bildirim öğeleri, bir dosya adı içeren bir konum belirtin. Ancak, bildirim şablonu için bir dosya adı girişi ekleme temel alınan dosya paketi eklemez. Pakete dahil ve buna göre dağıtım türü özelliği ayarlamak için proje dosyası eklemeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Derleme ve SharePoint çözümlerini hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
