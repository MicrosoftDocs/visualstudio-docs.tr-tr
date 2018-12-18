---
title: Outlook için Şerit özelleştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 035a38abc2285f744841b1d095387f61a21335a7
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671540"
---
# <a name="customize-a-ribbon-for-outlook"></a>Outlook için Şerit özelleştirme
  Microsoft Office Outlook'ta Şeritteki'nı özelleştirdiğinizde, Şerit uygulamada nerede görüneceğini dikkate almanız gerekir. Outlook, ana uygulama kullanıcı arabiriminde (UI) ve Windows'da, kullanıcılar e-posta iletilerini oluşturmak gibi belirli görevleri gerçekleştirirken açın Şerit görüntüler. Bu uygulamayı windows, denetçi olarak adlandırılır.  
  
 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [şeridi Outlook'ta özelleştirmek için Şerit Tasarımcısını bunu nasıl yaparım kullanın?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Bir Şerit ana uygulama kullanıcı Arabirimi ekleme  
 Ana uygulama Outlook kullanıcı Arabiriminde Gezgin olarak adlandırılır. Kullanıyorsanız **Şerit (Görsel Tasarımcı)** Gezgini tıklayarak bir Şerit öğesi, ekleyebilirsiniz **RibbonType** Şeritte özelliği **özellikleri** penceresinde seçip **Microsoft.Outlook.Explorer**.  
  
## <a name="assign-a-ribbon-to-an-inspector"></a>Şerit için bir denetçi atayın  
 Denetleyici için ileti sınıfı için karşılık gelen Şerit türünü belirterek özelleştirmek istediğiniz denetçisi tanımla  
  
 Kullanıyorsanız **Şerit (Görsel Tasarımcı)** öğesi, tıklayın **RibbonType** Şeritte özelliği **özellikleri** penceresini ve ardından bir veya daha fazla Şerit kimlikleri değerler listesi.  
  
 Birden fazla Şerit projeye ekleyebilirsiniz. Birden fazla şeridi şeridi kimliği paylaşırsa, geçersiz kılma `CreateRibbonExtensibilityObject` yönteminde `ThisAddin` , çalışma zamanında görüntülemek için Şerit belirtmek için projenizin sınıfı. Daha fazla bilgi için [Şerite Genel Bakış](../vsto/ribbon-overview.md). Her Şerit türü hakkında daha fazla bilgi için teknik makaleye bakın [Outlook 2007 Şeritte özelleştirme](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Şerit XML kullanarak Şerit türünü belirtin  
 Kullanıyorsanız **Ribbon (XML)** öğesi, değerini kontrol edin *ribbonID* parametresinde <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> yöntemi ve dönüş uygun Şerit.  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Yöntemi Şerit kod dosyasını Visual Studio tarafından otomatik olarak oluşturulur. *RibbonID* parametredir Gezgini veya belirli bir denetleyici türünü tanımlayan bir dize. Olası değerler tam bir listesi için *ribbonID* parametresi, teknik makaleye bakın [Outlook 2007 Şeritte özelleştirme](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).  
  
 Aşağıdaki kod örneği, özel bir görüntülenecek gösterilmiştir yalnızca Şerit `Microsoft.Outlook.Mail.Compose` denetçisi. Yeni bir e-posta iletisini bir kullanıcı oluşturduğu zaman açılır Inspector budur. Görüntülenecek Şerit belirtilen `GetResourceText()` içinde oluşturulan yöntemi **Şerit** sınıfı. Hakkında daha fazla bilgi için **Şerit** sınıfı [Ribbon XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Şerit Tasarımcısı](../vsto/ribbon-designer.md)   
 [Şerit XML](../vsto/ribbon-xml.md)  
  
  