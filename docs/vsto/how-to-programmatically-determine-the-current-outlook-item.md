---
title: 'Nasıl yapılır: program aracılığıyla geçerli Outlook öğesini belirleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 94d7e16b011b153a43e3d1666451a90b0e44c8b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547166"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Nasıl yapılır: program aracılığıyla geçerli Outlook öğesini belirleme
  Bu örnek, `Explorer.SelectionChange` geçerli klasörün adını ve seçili öğe hakkında bazı bilgileri göstermek için olayını kullanır. Kod daha sonra seçili öğeyi görüntüler.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek şunları gerektirir:

- Outlook Microsoft Office randevu, iletişim ve e-posta öğeleri.

## <a name="see-also"></a>Ayrıca bkz.
- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılır: program aracılığıyla belirli bir kişi arama](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
