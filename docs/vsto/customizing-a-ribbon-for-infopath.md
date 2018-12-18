---
title: InfoPath için Şerit özelleştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0a6a50ca1e84d9b1f5508cccbad24607f36b3f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942068"
---
# <a name="customize-a-ribbon-for-infopath"></a>InfoPath için Şerit özelleştirme
  Microsoft Office InfoPath Şeritte'nı özelleştirdiğinizde, Şerit uygulamada nerede görüneceğini dikkate almanız gerekir. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] Şerit InfoPath windows uygulaması aşağıdaki üç tür görüntüleyebilirsiniz:  
  
- Tasarım modunda açılan bir form şablon görünen Windows.  
  
- Görüntüleme formu şablonu temel alan bir formu Windows.  
  
- Baskı önizleme penceresi.  
  
  **İçin geçerlidir:** Bu konu başlığı altındaki bilgiler InfoPath 2010 VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi için [Office uygulaması ve proje türüne göre kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).  
  
  Kullanıcılar ve tasarımcılar form şablonu şablonu düzen ve görünümü değiştirmek için Tasarım modunda açın. Kullanıcıların içeriği eklemek için bir form şablonu temel alan form açın.  
  
  Baskı önizleme penceresi tasarımcıları ve kullanıcıların bir form veya form şablonu sayfaları yazdırmadan önce önizleme sağlar.  
  
> [!NOTE]  
>  **Eklentileri** sekmesini Baskı Önizleme penceresinde görünmez. Özel sekme Baskı Önizleme penceresinde görünmesini istiyorsanız, emin **OfficeId** sekmesinde özelliği ayarlanmadı **TabAddIns**.  
  
 İçinde Şerit görünmesini istediğiniz her bir pencere Şerit türünü belirtmeniz gerekir.  
  
## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Şerit Tasarımcısı'nda Şerit türünü belirtin  
 Kullanıyorsanız **Şerit (Görsel Tasarımcı)** öğesi,'ı tıklatın **RibbonType** Şeritte özelliği **özellikleri** penceresinde ve Şerit kimliklerinden herhangi biriyle seçin Aşağıdaki tabloda açıklanan.  
  
|Şerit Kimliği|Projeyi çalıştırdığınızda, Şerit görünür penceresi|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Tasarım modunda açılan bir form şablon görünen Windows.|  
|**Microsoft.InfoPath.Editor**|Görüntüleme formu şablonu temel alan bir formu Windows.|  
|**Microsoft.InfoPath.PrintPreview**|Baskı önizleme penceresi.|  
  
 Birden fazla Şerit projeye ekleyebilirsiniz. Birden fazla şeridi bir Şerit Kimliğini paylaşıyorsanız, geçersiz kılma `CreateRibbonExtensibilityObject` yönteminde `ThisAddin` çalışma zamanında görüntülemek üzere hangi Şerit belirtmek için projenizin sınıfı. Daha fazla bilgi için [Şerite Genel Bakış](../vsto/ribbon-overview.md).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Şerit XML kullanarak Şerit türünü belirtin  
 Kullanıyorsanız **Ribbon (XML)** öğesi, değerini kontrol edin *ribbonID* parametresinde <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> yöntemi ve dönüş uygun Şerit.  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Yöntemi Şerit kod dosyasını Visual Studio tarafından otomatik olarak oluşturulur. *RibbonID* parametredir açıyor InfoPath pencere türünü tanımlayan bir dize.  
  
 Aşağıdaki kod örneği, Tasarım modunda bir form şablonu görüntüleyen bir pencere bir Şerit görüntülenecek gösterilmiştir. Görüntülenecek Şerit belirtilen `GetResourceText()` oluşturulan Şerit sınıfında yöntemi. Şerit sınıfı hakkında daha fazla bilgi için bkz: [Ribbon XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Şerit Tasarımcısı](../vsto/ribbon-designer.md)   
 [Şerit XML](../vsto/ribbon-xml.md)  
  
  