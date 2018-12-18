---
title: 'İzlenecek yol: VSTO eklenti projesinde bir hizmetten verilere bağlama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4ebf998dc7c278fda1e605d18198945958a7fed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933189"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>İzlenecek yol: VSTO eklenti projesinde bir hizmetten verilere bağlama
  Verileri, VSTO eklentisi projelerine konak denetimlere bağlayabilirsiniz. Bu izlenecek yol, bir Microsoft Office Word belgesi için denetimler ekleme, MSDN içerik hizmetinden alınan verilere denetimler bağlama ve çalışma zamanında olaylara yanıt gösterilmektedir.  
  
 **İçin geçerlidir:** Bu konu başlığı altındaki bilgiler Word 2010 için uygulama düzeyi projelere yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Ekleme bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgeye çalışma zamanında denetim.  
  
- Bağlama <xref:Microsoft.Office.Tools.Word.RichTextContentControl> bir web hizmetinden veri denetimi.  
  
- Yanıtlama <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> olayı bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> denetimi.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
 İlk adım, bir sözcük VSTO eklentisi projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir sözcük VSTO eklentisi projesi oluşturun **MTPS içerik hizmeti**, Visual Basic veya C# kullanarak.  
  
     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio açılır `ThisAddIn.vb` veya `ThisAddIn.cs` dosya ve projeye ekler **Çözüm Gezgini**.  
  
## <a name="add-a-web-service"></a>Bir web hizmeti Ekle  
 Bu kılavuz için MTPS içerik hizmeti olarak adlandırılan bir web hizmetini kullanın. Bu web hizmetini belirtilen bir MSDN makalesi XML dizesi veya düz metin biçiminde bilgi verir. Bir sonraki adımda, bir içerik denetimi döndürülen bilgileri görüntüleme işlemi gösterilmektedir.  
  
### <a name="to-add-the-mtps-content-service-to-the-project"></a>MTPS içerik hizmeti projeye eklemek için  
  
1.  Üzerinde **veri** menüsünü tıklatın **yeni veri kaynağı Ekle**.  
  
2.  İçinde **veri kaynağı Yapılandırma Sihirbazı**, tıklayın **hizmet**ve ardından **sonraki**.  
  
3.  İçinde **adresi** alan, şu URL'yi yazın:  
  
     **http://services.msdn.microsoft.com/ContentServices/ContentService.asmx**  
  
4.  Tıklayın **Git**.  
  
5.  İçinde **Namespace** alanına **ContentService**, tıklatıp **Tamam**.  
  
6.  İçinde **başvuru Ekleme Sihirbazı'nı** iletişim kutusu, tıklayın **son**.  
  
## <a name="add-a-content-control-and-bind-to-data-at-runtime"></a>Bir içerik denetimi ekleyin ve çalışma zamanında verilere bağlayın  
 VSTO eklentisi projeleri ekleyin ve çalışma zamanında denetim bağlama. Bu kılavuz için bir kullanıcı denetimi içinde tıkladığında web hizmetinden veri almak için içerik denetimi yapılandırın.  
  
### <a name="to-add-a-content-control-and-bind-to-data"></a>Bir içerik denetimi ekleyin ve verilere bağlama  
  
1.  İçinde `ThisAddIn` sınıfı, MTPS içerik hizmetini, içerik denetimi ve veri bağlama için değişkenleri bildirin.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]  
  
2.  Aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Bu yöntem, etkin belgenin başlangıcında bir içerik denetimi oluşturur.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]  
  
3.  Aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Bu yöntem, oluşturmak ve web hizmetine bir istek göndermek için gerekli olan nesneler başlatır.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]  
  
4.  Bir kullanıcı içeriği içinde tıkladığında denetimleri denetlemek ve içerik denetimine veri bağlama içeriği hakkında MSDN Kitaplığı belge almak için bir olay işleyicisi oluşturun.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]  
  
5.  Çağrı `AddRichTextControlAtRange` ve `InitializeServiceObjects` yöntemlerinden `ThisAddIn_Startup` yöntemi. C# programcıları için bir olay işleyicisi ekleyin.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]  
  
## <a name="test-the-add-in"></a>Eklenti test  
 Word ' ü açtığınızda <xref:Microsoft.Office.Tools.Word.RichTextContentControl> denetimi görünür. Metin denetimi değişiklikleri içini tıkladığınızda.  
  
### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisi test etmek için  
  
1.  Tuşuna **F5**.  
  
2.  İçerik denetimi içinde tıklayın.  
  
     Bilgi MTPS içerik hizmetinden indirilir ve içerik denetiminin içinde görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  