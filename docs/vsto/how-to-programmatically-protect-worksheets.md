---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma'
description: Kullanıcıların ve kodun bir çalışma sayfasındaki nesneleri değiştirmesini engellemek için Microsoft Excel 'de koruma özelliğini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31c0184cbf8f29db6d33d135cf295f8277b55f2e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827109"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma
  Microsoft Office Excel 'deki koruma özelliği, kullanıcıların ve kodun bir çalışma sayfasındaki nesneleri değiştirmelerini önlemeye yardımcı olur. Varsayılan olarak, korumayı etkinleştirdikten sonra tüm hücreler kilitlenir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Belge düzeyi özelleştirmelerinde Excel tasarımcısını kullanarak çalışma sayfalarını koruyabilirsiniz. Ayrıca, bir çalışma sayfasını herhangi bir proje türünde çalışma zamanında programlı bir şekilde koruyabilirsiniz.

> [!NOTE]
> Korunan çalışma sayfasının bölümlerine Windows Forms denetimleri ekleyemezsiniz.

## <a name="use-the-designer"></a>Tasarımcıyı kullanma

### <a name="to-protect-a-worksheet-in-the-designer"></a>Tasarımcıda çalışma sayfasını korumak için

1. **İnceleme** sekmesinin **değişiklikler** grubunda, **sayfayı koru ' ya** tıklayın.

    **Sayfayı koru** iletişim kutusu görüntülenir. Bir parola ayarlayabilir ve isteğe bağlı olarak, çalışma sayfası ile izin verilen belirli eylemleri (hücreleri biçimlendirme veya satır ekleme gibi) belirtebilirsiniz.

   Ayrıca, kullanıcıların korumalı çalışma sayfalarındaki belirli aralıkları düzenlemesine de izin verebilirsiniz.

### <a name="to-allow-editing-in-specific-ranges"></a>Belirli aralıklarda düzenlenmesine izin vermek için

1. **İnceleme** sekmesinin **değişiklikler** grubunda, **Kullanıcıların aralıkları düzenlemesine izin ver ' e** tıklayın.

     **Kullanıcıların aralıkları düzenlemesine Izin ver** iletişim kutusu görüntülenir. Parola ile kilitsiz olan aralıkları ve parola olmadan aralıkları düzenleyebilen kullanıcıları belirtebilirsiniz.

## <a name="use-code-at-run-time"></a>Çalışma zamanında kodu kullan
 Aşağıdaki kod, parolayı (kullanıcıdan elde edilen bir parola içeren getPasswordFromUser değişkenini kullanarak) ayarlar ve yalnızca sıralamaya izin verir.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki kodu kullanarak çalışma sayfasını korumak için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>Çalışma sayfasının yöntemini çağırın. Bu örnek, adlı bir çalışma sayfasıyla çalıştığınızı varsayar `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet27":::

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>VSTO eklentideki kodu kullanarak çalışma sayfasını korumak için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A>Etkin çalışma sayfasının yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet17":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: çalışma sayfalarından program aracılığıyla korumayı kaldırma](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını koruma](../vsto/how-to-programmatically-protect-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
