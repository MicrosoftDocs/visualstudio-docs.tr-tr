---
title: 'Nasıl yapılır: uygulamaya özel görev bölmesi ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b8608fcc263be4750c38b6fe3f84967f40dd34ab
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548820"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Nasıl yapılır: uygulamaya özel görev bölmesi ekleme
  VSTO eklentisini kullanarak bir özel görev bölmesi uygulamaları için yukarıda listelenen ekleyebilirsiniz. Daha fazla bilgi için bkz: [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz: [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="add-a-custom-task-pane-to-an-application"></a>Uygulamaya özel görev bölmesi ekleme  
  
### <a name="to-add-a-custom-task-pane-to-an-application"></a>Uygulamaya özel görev bölmesi ekleme  
  
1.  Bir VSTO eklenti projesi yukarıda listelenen uygulamalardan birinin oluşturun veya açın. Daha fazla bilgi için bkz: [nasıl yapılır: Visual Studio oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Üzerinde **proje** menüsünde tıklatın **kullanıcı denetimi Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, yeni kullanıcı denetimi adını değiştirmek **MyUserControl**ve ardından **Ekle**.  
  
     Kullanıcı denetimi Tasarımcısı'nda açılır.  
  
4.  Bir veya daha fazla Windows Forms denetimleri ekleme **araç** kullanıcı denetimi için.  
  
5.  Açık **ThisAddIn.cs** veya **ThisAddIn.vb** kod dosyası.  
  
6.  Aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Bu kod örneklerini bildirir `MyUserControl` ve <xref:Microsoft.Office.Tools.CustomTaskPane> üyeleri olarak `ThisAddIn` sınıfı.  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  Aşağıdaki kodu ekleyin `ThisAddIn_Startup` olay işleyicisi. Bu kod yeni bir oluşturur <xref:Microsoft.Office.Tools.CustomTaskPane> ekleyerek `MyUserControl` nesnesine `CustomTaskPanes` koleksiyonu. Kod ayrıca görev bölmesini görüntüler.  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  Bu kod, özel görev bölmesini uygulamadaki etkin pencereyi ilişkilendirir. Bazı uygulamalar, görev bölmesinde diğer belgelerin veya öğelerin uygulamadaki ile görünmesini sağlamak için bu kodu değiştirmek isteyebilirsiniz. Daha fazla bilgi için bkz: [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Özel görev bölmeleri](../vsto/custom-task-panes.md)   
 [İzlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  