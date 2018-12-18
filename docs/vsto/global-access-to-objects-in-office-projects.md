---
title: Office projelerindeki nesnelere genel erişim
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 018ffc5c165c8cea7df66911c71f636712df4229
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932047"
---
# <a name="global-access-to-objects-in-office-projects"></a>Office projelerindeki nesnelere genel erişim
  Bir Office projesi oluşturduğunuzda, Visual Studio otomatik olarak adlı bir sınıf oluşturur `Globals` projedeki. Kullanabileceğiniz `Globals` projesinde herhangi bir koddan çalışma zamanında birçok farklı proje öğesine erişmek için sınıf.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="how-to-use-the-globals-class"></a>Globals sınıfı kullanma  
 `Globals` projenizde belirli öğelere başvuru tutan statik bir sınıftır. Kullanarak `Globals` sınıfı, çalışma zamanında proje herhangi bir koddan aşağıdaki öğelere erişebilirsiniz:  
  
- `ThisWorkbook` Ve `Sheet` *n* projesinde Excel çalışma kitabı veya şablon sınıfları. Bu nesneleri kullanarak erişebileceğiniz `Globals.ThisWorkbook` ve `Sheet` *n* özellikleri.  
  
- `ThisDocument` Bir Word belgesi veya şablonu projesinde sınıfı. Bu nesneyi kullanarak erişebileceğiniz `Globals.ThisDocument` özelliği.  
  
- `ThisAddIn` VSTO eklenti projesinde sınıfı. Bu nesneyi kullanarak erişebileceğiniz `Globals.ThisAddIn` özelliği.  
  
- Şerit Tasarımcısını kullanarak özelleştirilmiş, projenizdeki tüm Şerit. Şerit kullanarak erişebileceğiniz `Globals.Ribbons` özelliği. Daha fazla bilgi için [çalışma zamanında Şerit erişmek](../vsto/accessing-the-ribbon-at-run-time.md).  
  
- Outlook VSTO eklenti projesindeki tüm Outlook form bölgeleri. Form bölgeleri kullanarak erişebileceğiniz `Globals.FormRegions` özelliği. Daha fazla bilgi için [form bölgesine çalışma zamanında erişme](../vsto/accessing-a-form-region-at-run-time.md).  
  
- Hedefleyen projeleri çalışma zamanında, Şerit denetimlerini oluşturmanıza ve barındırmanıza olanak tanıyan bir Fabrika nesnesine öğeler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Bu nesneyi kullanarak erişebileceğiniz `Globals.Factory` özelliği. Bu nesne, aşağıdaki arabirimlerinden birini uygulayan bir sınıf örneği verilmiştir:  
  
  -   <xref:Microsoft.Office.Tools.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
  Örneğin, kullanabileceğiniz `Globals.Sheet1` metnine eklemek için özellik bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi `Sheet1` bir kullanıcı Excel için belge düzeyi projesi eylemler bölmesinde bir düğmeyi tıkladığında.  
  
  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]  
  
## <a name="initialize-the-globals-class"></a>Globals sınıfı Başlat  
 Kullanmayı denerse kod `Globals` belge veya VSTO eklentisi başlatılmadan önce sınıfı, bir çalışma zamanı özel durum throw. Örneğin, kullanarak `Globals` ne zaman bir sınıf düzeyi değişkenleri bildirme başarısız olabilir, çünkü `Globals` sınıfı atanamaz tüm ana bilgisayar öğesi başvuruları ile bildirilen nesnenin örneği oluşturulmadan önce.  
  
> [!NOTE]  
>  `Globals` Sınıfı tasarım zamanında hiçbir zaman başlatılmaz, ancak denetim örnekleri tasarımcı tarafından oluşturuldu. Bir özelliği kullanan bir kullanıcı denetimi oluşturmak istiyorsanız buna `Globals` sınıf özelliği döndürüp döndürmediğini gelen bir kullanıcı denetimi sınıf içinde gerekir **null** döndürülen nesneyi kullanmayı denemeden önce.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Form bölgesine çalışma zamanında erişme](../vsto/accessing-a-form-region-at-run-time.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Belge konak öğesi](../vsto/document-host-item.md)   
 [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)   
 [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)  
  
  