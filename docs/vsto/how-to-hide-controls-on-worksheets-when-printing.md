---
title: 'Nasıl yapılır: yazdırırken çalışma sayfalarında denetimleri gizleme'
description: Windows Forms denetimleri içeren Microsoft Office bir Excel çalışma sayfası yazdırırken denetimleri gizleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d87da5c22969fc355fe473e9505c61429b8023f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934812"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Nasıl yapılır: yazdırırken çalışma sayfalarında denetimleri gizleme
  Windows Forms denetimleri içeren bir Microsoft Office Excel belgesi yazdırdığınızda, denetimler yazdırılmış çalışma sayfasında görünür. Çalışma sayfası yazdırılırken denetimleri gizleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Gibi verileri görüntüleyen denetimleri gizlerseniz <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> , denetimdeki veriler, yazdırılan çalışma sayfasında görünür olmayacaktır.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Bir çalışma sayfası yazdırıldığında denetimleri gizlemek için

1. Visual Studio 'da bir Excel projesi oluşturun veya açın ve **Sheet1** ' in tasarımcıda görünür olduğunu doğrulayın. Proje oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Araç kutusunun** **ortak denetimler** sekmesinden, bir <xref:Microsoft.Office.Tools.Excel.Controls.Button> denetimi üzerindeki bir hücreye sürükleyin `Sheet1` .

3. **Özellikler** penceresinde, <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> özelliğini **false** olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)
