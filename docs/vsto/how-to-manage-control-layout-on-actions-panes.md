---
title: 'Nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme'
description: Kullanıcı denetimlerini düzgün bir şekilde yığmak için kod yazarak eylem bölmelerinde denetim yerleşimini nasıl yönetebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 182dee248f161f3dde721c50ee996d6f621dd9af
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827457"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme
  Bir eylemler bölmesi, varsayılan olarak bir belge veya çalışma sayfasının sağına yerleştirilir; Ancak, sol, üst veya alt kısma yerleştirilebilir. Birden çok kullanıcı denetimi kullanıyorsanız, Eylemler bölmesinde kullanıcı denetimlerini doğru bir şekilde yığmak için kod yazabilirsiniz. Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Denetimlerin yığın sıralaması, Eylemler bölmesinin dikey veya yatay olarak yerleştirilmiş olmasına bağlıdır.

> [!NOTE]
> Kullanıcı, çalışma zamanında eylemler bölmesini yeniden boyutlandırırsa, denetimleri Eylemler bölmesiyle yeniden boyutlandırmak için ayarlayabilirsiniz. <xref:System.Windows.Forms.Control.Anchor%2A>Denetimleri eylemler bölmesine bağlamak için bir Windows Forms denetiminin özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimleri bağlama](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Eylemler bölmesi denetimlerinin yığın sırasını ayarlamak için

1. Birden çok kullanıcı denetimi veya iç içe geçmiş eylemler bölmesi denetimleri içeren bir eylemler bölmesi içeren Microsoft Office sözcük için belge düzeyi projesi açın. Daha fazla bilgi için bkz. [nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

2. **Çözüm Gezgini** içinde **ThisDocument. cs** veya **ThisDocument. vb** öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

3. <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>Eylemler bölmesinin olay işleyicisinde, Eylemler bölmesinin yönünün yatay olup olmadığını kontrol edin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet30":::

4. Hizalama yataysa, eylem bölmesi denetimlerini soldan yığın. Aksi takdirde, bunları üstten yığın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet31":::

5. C# ' de, olay işleyicisine için bir olay işleyicisi eklemeniz gerekir `ActionsPane` <xref:Microsoft.Office.Tools.Word.Document.Startup> . Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet32":::

6. Projeyi çalıştırın ve eylemler bölmesi belgenin en üstüne yerleştirildiğinde eylemler bölmesi denetimlerinin sol tarafa doğru şekilde yığıldiğini ve eylemler bölmesi belgenin sağ tarafına yerleştirildiğinde denetimlerin üstten alta yığıldıktan emin olun.

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet29":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet29":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek şunları gerektirir:

- Birden çok kullanıcı denetimi veya iç içe geçmiş eylemler bölmesi denetimleri içeren bir eylemler bölmesi olan Word belge düzeyi projesi.

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
