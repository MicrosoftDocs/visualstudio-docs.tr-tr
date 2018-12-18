---
title: Genişletilebilirlik arabirimlerini kullanarak kullanıcı Arabirimi özelliklerini özelleştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec1f538515c8765629e812b8d7f4070476dd95ba
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670851"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini kullanarak kullanıcı Arabirimi özelliklerini özelleştirme
  Visual Studio'da Office geliştirme araçları, sınıflar ve VSTO eklentisi içinde özel görev bölmeleri, Şerit özelleştirmeleri ve Outlook form bölgeleri oluşturma kullanıldıklarında birçok uygulama ayrıntıları işleyen tasarımcılar sağlar. Ancak, aynı zamanda uygulayabileceğiniz *genişletilebilirlik arabirimi* her özel gereksinimleriniz varsa, kendiniz özelliği.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="overview-of-extensibility-interfaces"></a>Genişletilebilirlik arabirimleri genel bakış  
 Microsoft Office, COM, VSTO eklentileri şeridinde gibi belirli özellikleri özelleştirmek için uygulayabileceğiniz genişletilebilirlik arabirimleri kümesi tanımlar. Bu arabirimler, erişim sağladıkları özellikler üzerinde tam denetim sağlar. Ancak, bu arabirimleri uygulayan yönetilen kodda COM birlikte çalışabilirlik biraz bilgi gerektirir. Bazı durumlarda, bu arabirimlerin programlama modeli ayrıca .NET Framework için alışkın oldukları geliştiriciler için kullanımı kolay değildir.  
  
 Bir VSTO eklentisi Visual Studio'da Office proje şablonları kullanarak oluşturduğunuzda, Şerit gibi özellikleri özelleştirmek için genişletilebilirlik arabirimleri uygulayan gerekmez. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Sizin için bu arabirimlerini uygular. Bunun yerine, daha sezgisel sınıflar ve Visual Studio tarafından sağlanan tasarımcılar kullanabilirsiniz. Ancak, isterseniz genişletilebilirlik arabirimleri doğrudan, VSTO eklenti yine de uygulayabilirsiniz.  
  
 Sınıflar ve Visual Studio bu özellikler için sağladığı tasarımcılar hakkında daha fazla bilgi için bkz: [özel görev bölmeleri](../vsto/custom-task-panes.md), [Şerit Tasarımcısı](../vsto/ribbon-designer.md), ve [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Bir VSTO eklenti uygulayabileceğiniz genişletilebilirlik arabirimleri  
 Aşağıdaki tabloda, uygulayabileceğiniz genişletilebilirlik arabirimleri ve bunları destekleyen uygulamaları listeler.  
  
|Arabirim|Açıklama|Uygulamalar|  
|---------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Şerit kullanıcı arabirimini özelleştirmek için bu arabirimi uygulayın. **Not:** ekleyebileceğiniz bir **Ribbon (XML)** varsayılan oluşturmak için bir proje öğesine <xref:Microsoft.Office.Core.IRibbonExtensibility> VSTO eklenti uygulamasında. Daha fazla bilgi için [Ribbon XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proje<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Özel görev bölmesi oluşturmak için bu arabirimi uygulayın.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Outlook form bölgesi oluşturmak için bu arabirimi uygulayın.|Outlook|  
  
 Microsoft Office tarafından gibi tanımlanan diğer genişletilebilirlik arabirimleri vardır <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>, ve <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio içinde bir VSTO Office proje şablonları kullanılarak oluşturulmuş eklentisi bu arabirimleri uygulayan desteklemez.  
  
## <a name="use-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini kullanın  
 Genişletilebilirlik arabirimini kullanarak bir kullanıcı Arabirimi özelliğinin özelleştirmek için VSTO eklentisi projeleri uygun arabirim uygular. Ardından, geçersiz kılma <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> arabirimi uygulayan sınıf örneği döndürmek için yöntemi.  
  
 Nasıl uygulayacağınızı gösteren bir örnek uygulama için <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, ve <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> VSTO eklentisi, Outlook için genel arabirimlerde UI Manager örnekte bkz [Office geliştirme örnekleri](../vsto/office-development-samples.md).  
  
### <a name="example-of-implementing-an-extensibility-interface"></a>Genişletilebilirlik arabirimi uygulama örneği  
 Aşağıdaki kod örneği basit bir uygulamasını gösterir <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> özel görev bölmesi oluşturmak için arabirim. Bu örnek, iki sınıf tanımlar:  
  
- `TaskPaneHelper` Sınıfının Implements <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> oluşturmak ve bir özel görev bölmesini görüntülemek için.  
  
- `TaskPaneUI` Sınıfı görev bölmesinin kullanıcı Arabirimi sağlar. Özniteliklerini `TaskPaneUI` sınıfı sınıfı sınıfı bulmak Microsoft Office uygulamaları sağlayan COM görünür hale. Bu örnekte, boş bir kullanıcı Arabirimi olan <xref:System.Windows.Forms.UserControl>, ancak kodu değiştirerek denetimler ekleyebilirsiniz.  
  
  > [!NOTE]  
  >  Kullanıma sunmak için `TaskPaneUI` sınıfı, COM de ayarlamanız gerekir **kaydetme COM birlikte çalışması için** proje özelliği.  
  
  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]  
  
  Uygulama hakkında daha fazla bilgi için <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, bkz: [2007 Office sistemi içinde özel görev bölmeleri oluşturma](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) Microsoft Office belgelerinde.  
  
### <a name="example-of-overriding-the-requestservice-method"></a>Örnek RequestService yöntemini geçersiz kılma  
 Aşağıdaki kod örneğinde nasıl geçersiz kılınacağını gösterir <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> örneği döndürülecek yöntemi `TaskPaneHelper` önceki kod örneğinde bir sınıftan. Değerini denetler *serviceGuid* hangi arabirim istenen ve ardından bu arabirimi uygulayan bir nesne döndürür belirlemek için parametre.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [VSTO eklentilerinde diğer Office Çözümlerinden kod arama](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)  
  
  