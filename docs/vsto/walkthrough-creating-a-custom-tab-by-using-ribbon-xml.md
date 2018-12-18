---
title: 'İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 45e35b7cf97a6b9a1f310149817f8e79956a47aa
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808930"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma
  Bu izlenecek yol kullanarak özel bir Şerit sekmesi oluşturma işlemini gösterir **Ribbon (XML)** öğesi.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Düğmeleri ekleme **eklentileri** sekmesi. **Eklentileri** sekmedir Şerit XML dosyasında tanımlanan varsayılan bir sekme.  
  
-   Düğmeleri kullanarak Microsoft Office Word'ü Otomatikleştirme **eklentileri** sekmesi.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 İlk adım, bir sözcük VSTO eklentisi projesi oluşturmaktır. Daha sonra özelleştireceğim **eklentileri** bu belgenin sekmesi.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Oluşturma bir **Word eklentisi** adlı proje **MyRibbonAddIn**.  
  
     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açılır **ThisAddIn.cs** veya **ThisAddIn.vb** ekler ve kod dosyası **MyRibbonAddIn** için proje **Çözüm Gezgini**.  
  
## <a name="create-the-vsto-add-ins-tab"></a>VSTO eklentileri sekmesi oluştur  
 Oluşturmak için **eklentileri** sekmesinde, ekleme bir **Ribbon (XML)** projenize öğesi. Bu kılavuzda daha sonra bu sekmeye bazı düğmeler ekleyeceksiniz.  
  
### <a name="to-create-the-add-ins-tab"></a>Eklentiler sekmesi oluşturma  
  
1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Ribbon (XML)**.  
  
3.  Yeni Şeridin adını değiştirmek **MyRibbon**, tıklatıp **Ekle**.  
  
     **MyRibbon.cs** veya **MyRibbon.vb** dosyası tasarımcıda açılır. Adlı bir XML dosyası **MyRibbon.xml** de projenize eklenir.  
  
4.  İçinde **Çözüm Gezgini**, sağ **ThisAddIn.cs** veya **ThisAddIn.vb**ve ardından **Kodu Görüntüle**.  
  
5.  Aşağıdaki kodu ekleyin **ThisAddIn** sınıfı. Bu kodu geçersiz kılmalar `CreateRibbonExtensibilityObject` Office uygulamasına sınıf yöntemi ve Şerit XML döndürür.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  İçinde **Çözüm Gezgini**, sağ **MyRibbonAddIn** proje ve ardından **yapı**. Projenin hatasız oluşturulduğunu doğrulayın.  
  
## <a name="add-buttons-to-the-add-ins-tab"></a>Add-Ins sekmesine düğme ekleme  
 Bu VSTO eklentisi için kullanıcıların etkin belgeye Demirbaş metni ve belirli bir tablo eklemek için bir yol sağlamak olmaktır. Kullanıcı arabirimini sağlamak için iki düğme ekleyin **eklentileri** Ribbon XML dosyasını değiştirerek sekmesi. Bu kılavuzda daha sonra geri çağırma yöntemleri düğmelerinin tanımlayacaksınız. Ribbon XML dosyasındaki hakkında daha fazla bilgi için bkz: [Ribbon XML](../vsto/ribbon-xml.md).  
  
### <a name="to-add-buttons-to-the-add-ins-tab"></a>Add-Ins sekmesine düğme eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **MyRibbon.xml** ve ardından **açık**.  
  
2.  Öğesinin içeriğini değiştirin **sekmesini** şu XML ile öğesi. Bu XML etiketi varsayılan denetim grubunun değişiklikleri **içerik**, ve etiketleri ile iki yeni düğmeler ekler **metni Ekle** ve **Tablo Ekle**.  
  
    ```xml  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automate-the-document-by-using-the-buttons"></a>Belge düğmeleri kullanarak otomatik hale getirin.  
 Eklemelisiniz `onAction` için geri çağırma yöntemleri **metni Ekle** ve **Tablo Ekle** kullanıcı bunları tıkladığında eylemleri gerçekleştirmek için düğmeler. Şerit denetimleri için geri çağırma yöntemleri hakkında daha fazla bilgi için bkz. [Ribbon XML](../vsto/ribbon-xml.md).  
  
### <a name="to-add-callback-methods-for-the-buttons"></a>Düğme için geri çağırma yöntemleri eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **MyRibbon.cs** veya **MyRibbon.vb**ve ardından **açık**.  
  
2.  Üstüne aşağıdaki kodu ekleyin **MyRibbon.cs** veya **MyRibbon.vb** dosya. Bu kod için bir diğer ad oluşturur <xref:Microsoft.Office.Interop.Word> ad alanı.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Aşağıdaki yöntemi ekleyin `MyRibbon` sınıfı. Bunun için bir geri çağırma yöntemi olan **metni Ekle** geçerli imleç konumu etkin belge dizesi düğme.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Aşağıdaki yöntemi ekleyin `MyRibbon` sınıfı. Bunun için bir geri çağırma yöntemi olan **Tablo Ekle** etkin belge geçerli imleç konumu için bir tablo ekler düğmesi.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>VSTO eklentisi test etme  
 Proje, Word açar ve adlı sekmede çalıştırdığınızda **eklentileri** Şerit üzerinde görünür. Tıklayın **metni Ekle** ve **Tablo Ekle** düğmelerini **eklentileri** kodu test etmek için sekmesinde.  
  
### <a name="to-test-your-vsto-add-in"></a>VSTO eklenti test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Onaylayın **eklentileri** sekmedir Şerit üzerinde görünür.  
  
3.  Tıklayın **eklentileri** sekmesi.  
  
4.  Onaylayın **içerik** grubudur Şerit üzerinde görünür.  
  
5.  Tıklayın **metni Ekle** düğmesine **içerik** grubu.  
  
     Bir dize, geçerli imleç konumu konumundaki belgeye eklenir.  
  
6.  Tıklayın **Tablo Ekle** düğmesine **içerik** grubu.  
  
     Tablo, geçerli imleç konumu konumundaki belgeye eklenir.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Aşağıdaki konulardan Office UI özelleştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Farklı bir Office uygulamasının Şerit özelleştirin. Şeridi özelleştirme destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [Şerite Genel Bakış](../vsto/ribbon-overview.md).  
  
-   Şerit Tasarımcısını kullanarak bir Office uygulamasının Şerit özelleştirin. Daha fazla bilgi için [Şerit Tasarımcısı](../vsto/ribbon-designer.md).  
  
-   Özel Eylemler bölmesi oluşturun. Daha fazla bilgi için [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).  
  
-   Outlook Form bölgeleri kullanarak Microsoft Office Outlook kullanıcı arabirimini özelleştirme. Daha fazla bilgi için [izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Şerit XML](../vsto/ribbon-xml.md)   
 [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  