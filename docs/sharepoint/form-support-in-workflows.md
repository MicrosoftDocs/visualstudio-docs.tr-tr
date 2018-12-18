---
title: İş akışlarında form desteği | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 27e8ab6651c6838de92b8a3d83311ebd47fabcbb
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296196"
---
# <a name="form-support-in-workflows"></a>İş akışlarında form desteği
  Bir iş akışında formlarının dört türleri kullanılabilir: İlişkilendirme ve başlatma, görev ve değiştirme. Bu form türleri ASPX form ya da bir InfoPath formunu temel alabilir. Destek düzeyini [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belirli bir form aşağıdaki tablolarda açıklanan çeşitli etkenlere bağlıdır sağlar. İş akışı form türleri hakkında daha fazla bilgi için bkz. [iş akışı Forms'a genel bakış](http://go.microsoft.com/fwlink/?LinkId=185228).  
  
## <a name="xml-refactoring"></a>XML yeniden düzenleme
 Bir ASPX ilişkilendirme veya başlatma formu eklediğinizde bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı projesine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışının XML otomatik olarak yeniden düzenler *Elements.xml* ilişkilendirmesine başvuran öznitelik korumak için dosya veya başlatma formu form adı veya dağıtım yolu güncelleştirildiğinde eşitlenmiş veya formun silinir. Ancak, diğer form türlerini kullandığınızda, bir görev veya değişiklik formu gibi bir iş akışında *Elements.xml* dosya yeniden değil.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Yeni Visual Studio iş akışlarında form desteği
 Aşağıdaki tabloda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ASPX veya InfoPath form, oluşturulan iş akışlarındaki farklı form türleri için destek [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Form türü|Visual Studio'da ASPX Form ile oluşturulan iş akışı|Visual Studio'da bir InfoPath formunu kullanarak oluşturulan bir iş akışı|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|İlişkilendirme|-Bir ASPX ilişkilendirme formu kullanarak iş akışını eklenebilir **iş akışı ilişkilendirme formu** öğe şablonu.<br />- *Elements.xml* form eklendiğinde, yeniden adlandırılmış veya silinmiş veya onun dağıtım yolu değiştiğinde iş akışının dosya yeniden.<br />-Daha fazla bilgi için [izlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Yok hiçbir InfoPath ilişkilendirme formu şablonunda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Yok arasında hiçbir tümleştirme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve InfoPath Designer.<br />- *Elements.xml* iş akışının dosya yeniden değil.|  
|Başlatma|-Bir ASPX başlatma formu kullanarak iş akışını eklenebilir **iş akışı başlatma formu** öğe şablonu.<br />- *Elements.xml* form eklendiğinde, yeniden adlandırılmış veya silinmiş veya onun dağıtım yolu değiştiğinde iş akışının dosya yeniden.<br />-Daha fazla bilgi için [izlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Yok hiçbir InfoPath ilişkilendirme formu şablonunda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Yok arasında hiçbir tümleştirme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve InfoPath Designer.<br />- *Elements.xml* iş akışının dosya yeniden değil.|  
|Görev|-Herhangi bir ASPX görev form şablonu kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Uygulama sayfası oluşturma ve kod eklemeniz gerekir.<br />- *Elements.xml* iş akışının dosya yeniden değil.<br />-Daha fazla bilgi için [iş akışı görev formları (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Yok hiçbir InfoPath görev formda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Yok arasında hiçbir tümleştirme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve InfoPath Designer.<br />- *Elements.xml* iş akışının dosya yeniden değil.|  
|Değişiklik|-Herhangi bir ASPX değiştirme form şablonu kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Bir değişiklik formu eklemek, bir uygulama sayfası oluşturmak ve kodu ekleyin.<br />- *Elements.xml* iş akışının dosya yeniden değil. El ile uygun şekilde düzenlemeniz gerekir.<br />-Daha fazla bilgi için [iş akışı değişiklik formları (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Yok hiçbir InfoPath değişikliği formda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Yok arasında hiçbir tümleştirme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve InfoPath Designer.<br />- *Elements.xml* iş akışının dosya yeniden değil.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>İçeri aktarılan SharePoint yeniden kullanılabilir iş akışlarında form desteği
 Aşağıdaki tabloda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] içine alınan SharePoint yeniden kullanılabilir iş akışlarını ASPX veya InfoPath formlarda farklı form türleri için destek [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Form türü|SharePoint Tasarımcısı'ndan alınan bir ASPX biçimde yeniden kullanılabilir iş akışı|SharePoint Tasarımcısı'ndan alınan bir InfoPath formunu sahip yeniden kullanılabilir iş akışı|  
|---------------|-------------------------------------------------------------------------------| - |  
|İlişkilendirme|-Formun başvurulduğundan *Elements.xml* iş akışı dosyası.<br />- *Elements.xml* formu yeniden adlandırılmış veya silinmiş veya onun dağıtım yolu değiştiğinde iş akışının dosya yeniden.|-Formun alındı, ancak başvurulan değil *Elements.xml* iş akışı.<br />- *Elements.xml* iş akışının dosya yeniden değil.|  
|Başlatma|-İş akışı tarafından başvurulan formu *Elements.xml* iş akışı dosyası.<br />- *Elements.xml* formu yeniden adlandırılmış veya silinmiş veya onun dağıtım yolu değiştiğinde iş akışının dosya yeniden.|-Formun alındı, ancak başvurulan değil *Elements.xml* iş akışı.<br />- *Elements.xml* iş akışının dosya yeniden değil. **Not:** kurallarıyla ve özellikleriyle gerekir eklenebilir ve bu senaryo için çalışacak şekilde değiştirildi.|  
|Görev|-Formun başvurulduğundan *Elements.xml* iş akışı dosyası.<br />- *Elements.xml* iş akışının dosya yeniden değil.|-Formun alındı, ancak başvurulan değil *Elements.xml* iş akışı.<br />- *Elements.xml* iş akışının dosya yeniden değil. **Not:** kurallarıyla ve özellikleriyle gerekir eklenebilir ve bu senaryo için çalışacak şekilde değiştirildi.|  
|Değişiklik|Yok. ASPX değişiklik formları SharePoint Tasarımcısı'nda oluşturulamıyor.|Yok. InfoPath değişiklik formları, iş akışı dışarı aktardığınızda, .wsp dosyasında yer almayan yerleşik SharePoint Server iş akışı hariç, SharePoint Tasarımcısı'nda oluşturulamıyor.|  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İzlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [SharePoint iş akışı çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
