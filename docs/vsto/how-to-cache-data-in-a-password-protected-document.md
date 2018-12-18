---
title: 'Nasıl yapılır: bir parola korumalı belgede veriyi önbelleğe alma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c15d3fee1728118df2701cc940dc288ae500942d
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255349"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Nasıl yapılır: bir parola korumalı belgede veriyi önbelleğe alma
  Bir belge veya bir parolayla korunduğu çalışma kitabının veri önbelleğindeki veri eklerseniz, önbelleğe alınmış verilerde yapılan değişiklikleri otomatik olarak kaydedilmez. Projenizdeki iki yöntemi geçersiz kılarak önbelleğe alınmış veri değişikliklerini kaydedebilir.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Word belgelerinde önbelleğe alma  
  
### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Bir parola ile korunan bir Word belgesinde veriyi önbelleğe almak için  
  
1.  İçinde `ThisDocument` sınıfı, bir ortak alan veya önbelleğe alınacak özelliği işaretleyin. Daha fazla bilgi için bkz: [veriyi önbelleğe](../vsto/caching-data.md).  
  
2.  Geçersiz kılma <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> yönteminde `ThisDocument` sınıfı ve belgeden korumayı kaldırın.  
  
     Belge kaydedildiğinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Belge korumasını olanağı vermek için bu yöntemi çağırır. Kaydedilecek önbelleğe alınmış verilerde yapılan değişiklikleri sağlar.  
  
3.  Geçersiz kılma <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> yönteminde `ThisDocument` sınıfı ve belgeye korumayı yeniden uygulayın.  
  
     Belge kaydedildikten sonra [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] belgeye korumayı yeniden uygulamanız için bir fırsat vermek için bu yöntemi çağırır.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir parola ile korunan bir Word belgesinde veriyi önbelleğe gösterilmiştir. Kod koruma kaldırılmadan önce <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> yöntemi, geçerli kaydeder <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> değer böylece aynı tür korumanın içinde uygulanabilir <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> yöntemi.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compile-the-code"></a>Kod derleme  
 Bu kodu ekleyin `ThisDocument` projenizdeki sınıfı. Bu kod parola adlı bir alana saklandığı varsayılır `securelyStoredPassword`.  
  
## <a name="cache-in-excel-workbooks"></a>Excel çalışma kitaplarını önbelleğe alma  
 Excel projelerinde kullanarak tüm çalışma kitabını korumaya aldığınızda bu yordam gereklidir <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> yöntemi. Bu yordamı kullanarak yalnızca belirli bir çalışma bir parolayla koruyun durumunda gerekli değildir <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> yöntemi.  
  
### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Parola korumalı Excel çalışma kitabında veriyi önbelleğe almak için  
  
1.  İçinde `ThisWorkbook` sınıf veya biri `Sheet` *n* sınıfları, işaretlemek ortak alan veya önbelleğe alınacak özelliği. Daha fazla bilgi için bkz: [veriyi önbelleğe](../vsto/caching-data.md).  
  
2.  Geçersiz kılma <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> yönteminde `ThisWorkbook` sınıfı ve koruma çalışma kitabından kaldırın.  
  
     Çalışma kitabı kaydedildiğinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çalışma kitabının korumasını kaldırmak için bir fırsat vermek için bu yöntemi çağırır. Kaydedilecek önbelleğe alınmış verilerde yapılan değişiklikleri sağlar.  
  
3.  Geçersiz kılma <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> yönteminde `ThisWorkbook` sınıfı ve belgeye korumayı yeniden uygulayın.  
  
     Çalışma kitabı kaydedildikten sonra [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çalışma kitabının korumasını yeniden olanağı vermek için bu yöntemi çağırır.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir parolayla korunduğu Excel çalışma kitabında veriyi önbelleğe gösterilmiştir. Kod koruma kaldırılmadan önce <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> yöntemi, geçerli kaydeder <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> ve <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> değerleri aynı tür korumanın içinde uygulanabilir böylece <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> yöntemi.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compile-the-code"></a>Kod derleme  
 Bu kodu ekleyin `ThisWorkbook` projenizdeki sınıfı. Bu kod parola adlı bir alana saklandığı varsayılır `securelyStoredPassword`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Verileri önbelleğe](../vsto/caching-data.md)   
 [Nasıl yapılır: çevrimdışı veya sunucuda kullanmak için verileri önbelleğe alma](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Nasıl yapılır: program aracılığıyla bir veri kaynağı Office belgesinden önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  