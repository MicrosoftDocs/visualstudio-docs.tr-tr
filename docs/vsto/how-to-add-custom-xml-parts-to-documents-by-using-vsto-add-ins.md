---
title: 'Nasıl yapılır: VSTO eklentileri kullanarak belgelere özel XML bölümleri ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a559f8c074a7e80ea898f86dc205dec6ad2bb064
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826902"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Nasıl yapılır: VSTO eklentileri kullanarak belgelere özel XML bölümleri ekleme
  VSTO eklentisi içinde özel bir XML parçasına oluşturarak XML verileri aşağıdaki belge türlerini depolayabilirsiniz:  
  
- Bir Microsoft Office Excel çalışma kitabı.  
  
- Microsoft Office Word belgesi.  
  
- Microsoft Office PowerPoint sunusu.  
  
  Daha fazla bilgi için [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).  
  
  **İçin geçerlidir:** Bu konu başlığı altındaki bilgiler Excel, PowerPoint ve Word için uygulama düzeyi projelerine yöneliktir. Daha fazla bilgi için [Office uygulaması ve proje türüne göre kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Bir Excel çalışma kitabına özel XML bölümleri ekleme  
  
1.  Yeni bir <xref:Microsoft.Office.Core.CustomXMLPart> nesnesini <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> çalışma kitabında koleksiyonu. <xref:Microsoft.Office.Core.CustomXMLPart> Çalışma kitabında depolamak istediğiniz XML dizesi içerir.  
  
     Aşağıdaki kod örneği, belirli bir çalışma kitabına özel bir XML parçasına ekler.  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  Ekle `AddCustomXmlPartToWorkbook` yönteme `ThisAddIn` Excel için VSTO eklenti projesinde sınıfı.  
  
3.  Projenizdeki başka bir koddan yöntemi çağırın. Örneğin, bir çalışma kitabı kullanıcı oturum açtığında özel XML parçaları oluşturmak için yöntem için bir olay işleyicisi çağırmanıza <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> olay.  
  
## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Bir Word belgesi için özel XML bölümleri ekleme  
  
1.  Yeni bir <xref:Microsoft.Office.Core.CustomXMLPart> nesnesini <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> belgedeki koleksiyonu. <xref:Microsoft.Office.Core.CustomXMLPart> Belge içinde depolamak istediğiniz XML dizesi içerir.  
  
     Aşağıdaki kod örneği, belirtilen bir belge için özel bir XML parçasına ekler.  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  Ekle `AddCustomXmlPartToDocument` yönteme `ThisAddIn` Word için VSTO eklenti projesinde sınıfı.  
  
3.  Projenizdeki başka bir koddan yöntemi çağırın. Örneğin, kullanıcı bir belge açıldığında özel XML parçaları oluşturmak için yöntem için bir olay işleyicisi çağırmanıza <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> olay.  
  
## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Bir PowerPoint sunumu özel XML bölümleri ekleme  
  
1.  Yeni bir <xref:Microsoft.Office.Core.CustomXMLPart> nesnesini [Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) sunuda koleksiyonu. <xref:Microsoft.Office.Core.CustomXMLPart> Sunuda depolamak istediğiniz XML dizesi içerir.  
  
     Aşağıdaki kod örneği belirli bir sunuya özel bir XML parçasına ekler.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  Ekle `AddCustomXmlPartToPresentation` yönteme `ThisAddIn` PowerPoint için VSTO eklenti projesinde sınıfı.  
  
3.  Projenizdeki başka bir koddan yöntemi çağırın. Örneğin, kullanıcı bir sunu açıldığında özel XML parçaları oluşturmak için yöntem için bir olay işleyicisi çağırmanıza [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) olay.  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Kolaylık olması için bu örnek, bir yerel değişken yöntemi olarak tanımlanan bir XML dizesi kullanır. Genellikle, bir dosya veya veritabanı gibi bir dış kaynaktan XML edinmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)   
 [Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  