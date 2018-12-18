---
title: 'Nasıl yapılır: program aracılığıyla arama seçeneklerini ayarlama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e4e6b5471f1d36eab677d8a1d0b65ab39b7dba4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853954"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Nasıl yapılır: program aracılığıyla arama seçeneklerini ayarlama
  Microsoft Office Word belgelerinde seçimleri için arama seçeneklerini ayarlamak için iki yolu vardır:  
  
- Özelliklerini ayarlamak bir <xref:Microsoft.Office.Interop.Word.Find> nesne.  
  
- Bağımsız değişkenlerini kullanmak <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> yöntemi bir <xref:Microsoft.Office.Interop.Word.Find> nesne.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="use-properties-of-a-find-object"></a>Bir bulma nesnesinin özelliklerini kullanma  
 Aşağıdaki kod özelliklerini ayarlar bir <xref:Microsoft.Office.Interop.Word.Find> Geçerli seçimdeki metni aramak için nesne. İleri, sarmalama ve metin, aramak için arama gibi arama ölçütleri özelliklerini olduğunu fark <xref:Microsoft.Office.Interop.Word.Find> nesne.  
  
 Her özelliklerini ayarlama <xref:Microsoft.Office.Interop.Word.Find> nesne değil yararlı parametreler olarak aynı özelliklerini belirtmeniz gerekir çünkü C# kodu yazarken <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> yöntemi. Bu nedenle bu örnekte, yalnızca Visual Basic kodunu içerir.  
  
### <a name="to-set-search-options-using-a-find-object"></a>Bir bulma nesnesi ile arama seçeneklerini ayarlama  
  
1.  Özelliklerini ayarlama bir <xref:Microsoft.Office.Interop.Word.Find> seçim metin için ileriye doğru arama nesnesine **bana Bul**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="use-execute-method-arguments"></a>Execute yöntemi bağımsız değişkenleri kullanma  
 Aşağıdaki kod <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> yöntemi bir <xref:Microsoft.Office.Interop.Word.Find> Geçerli seçimdeki metni aramak için nesne. İleri, sarmalama ve metin, aramak için arama gibi arama ölçütleri bir parametre olarak geçirilen bildirimi <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> yöntemi.  
  
### <a name="to-set-search-options-using-execute-method-arguments"></a>Execute yöntemi bağımsız değişken ile arama seçeneklerini ayarlama  
  
1.  Arama ölçütleri bir parametre olarak geçirmeniz <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> seçim metin için ileriye doğru arama yapmanız gereken yöntemini **bana Bul**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla arama ve belgelerdeki metni değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla bulunan öğeler arasında döngü](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla aramalardan sonra seçimleri geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  