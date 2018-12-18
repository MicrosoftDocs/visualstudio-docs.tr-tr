---
title: "İzlenecek yol: bir Visual C# projesinde VBA'dan kod çağırmak"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e2803ef31ec1009215d4490ac527c42cbdc90571
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781695"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>İzlenecek yol: bir Visual C# projesinde VBA'dan kod çağırmak
  Bu yönerge, bir yöntem belge düzeyi özelleştirmesinde Microsoft Office Excel için Visual Basic for Applications (VBA) kodu çalışma kitabı nasıl çağrılacağını gösterir. Yordamı üç temel adımdan oluşur: bir yöntem ekleyin `Sheet1` konak öğesi sınıfına, çalışma kitabını VBA koduna yöntemi kullanıma sunar ve sonra çalışma kitabının VBA kodu yöntemini çağırın.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Bu izlenecek yolda Excel özellikle kullansa da, izlenecek yol gösterilen kavramları da Word için belge düzeyi projelere geçerlidir.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   VBA kodu içeren bir çalışma kitabı oluşturma.  
  
-   Çalışma kitabı konumunu, Excel'deki Güven Merkezi'ni kullanarak güvenen.  
  
-   Bir yöntem ekleme `Sheet1` ana öğe sınıfı.  
  
-   Bir arabirim için ayıklama `Sheet1` ana öğe sınıfı.  
  
-   VBA kodu yöntemi açığa çıkarma.  
  
-   VBA koddan yöntemini çağırma.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-a-workbook-that-contains-vba-code"></a>VBA kodu içeren bir çalışma kitabı oluşturun  
 İlk adım, basit bir VBA makro içeren bir makro özellikli bir çalışma kitabını oluşturmaktır. VBA özelleştirmelerinde kodu oluşturmadan önce çalışma kitabı zaten VBA kodu içermesi gerekir. Aksi takdirde, Visual Studio VBA kodunu özelleştirme bütünleştirilmiş kod içine çağırmak için etkinleştirmek için bir VBA projesi değiştiremezsiniz.  
  
 Kullanmak istediğiniz VBA kodu içeren bir çalışma kitabı zaten varsa bu adımı atlayabilirsiniz.  
  
### <a name="to-create-a-workbook-that-contains-vba-code"></a>VBA kodu içeren bir çalışma kitabı oluşturun  
  
1.  Excel'i başlatın.  
  
2.  Etkin belge olarak kaydedebilir bir **etkin çalışma kitabı (\*.xlsm)** adıyla **WorkbookWithVBA**. Masaüstü gibi uygun bir konuma kaydedin.  
  
3.  Şerit üzerinde tıklayın **Geliştirici** sekmesi.  
  
    > [!NOTE]  
    >  Varsa **Geliştirici** sekme görünür değilse, önce görünür olmalıdır. Daha fazla bilgi için [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  İçinde **kod** grubunda **Visual Basic**.  
  
     Visual Basic Düzenleyicisi açılır.  
  
5.  İçinde **proje** penceresinde çift **ThisWorkbook**.  
  
     Kod dosyası `ThisWorkbook` nesnesini açar.  
  
6.  Aşağıdaki VBA kodu için kod dosyasını ekleyin. Bu kod, hiçbir şey yapmaz basit bir işlevi tanımlar. Tek amacı, bu işlev bir VBA projesi çalışma kitabında var olduğundan emin olmaktır. Bu, sonraki adımlarda bu izlenecek yol için gereklidir.  
  
    ```vb  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Belgeyi kaydedin ve Excel'den çıkın.  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 Artık, daha önce oluşturduğunuz makro özellikli çalışma kitabı kullanılmıştır Excel için belge düzeyi projesi oluşturabilirsiniz.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Şablonlar bölmesinde, **Visual C#** ve ardından **Office/SharePoint**.  
  
4.  Seçin **Office eklentilerini** düğümü.  
  
5.  Proje şablonları listesinde seçin **Excel 2010 Çalışma kitabı** veya **Excel 2013'ün çalışma kitabı** proje.  
  
6.  İçinde **adı** kutusuna **CallingCodeFromVBA**.  
  
7.  **Tamam**'ı tıklatın.  
  
     **Office Project Sihirbazı için Visual Studio Araçları** açılır.  
  
8.  Seçin **mevcut belgeyi kopyalamak**hem de **mevcut belgenin tam yolu** kutusunda, konumu belirtin **WorkbookWithVBA** daha önce oluşturduğunuz çalışma kitabı . Makro özellikli kendi çalışma kitabınızı kullanıyorsanız, bu çalışma kitabı konumunu belirleyin.  
  
9. **Son**'a tıklayın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açılır **WorkbookWithVBA** çalışma kitabını tasarımcıda ve ekler **CallingCodeFromVBA** için proje **Çözüm Gezgini**.  
  
## <a name="trust-the-location-of-the-workbook"></a>Çalışma kitabı konumunu güven  
 VBA kodu çalışma kitabında, çözümünüzdeki kod oluşturmadan önce çalıştırılacak çalışma kitabında VBA güvenmesi gerekir. Bunu yapmanın birkaç yolu vardır. Bu izlenecek yolda, bu çalışma kitabında konumunu güvenerek görevi **Güven Merkezi** Excel'de.  
  
### <a name="to-trust-the-location-of-the-workbook"></a>Çalışma kitabı konumunu güvenmek için  
  
1.  Excel'i başlatın.  
  
2.  Tıklayın **dosya** sekmesi.  
  
3.  Tıklayın **Excel Seçenekleri** düğmesi.  
  
4.  Kategorileri bölmesinden **Güven Merkezi**.  
  
5.  Ayrıntılar bölmesinden **Güven Merkezi Ayarları**.  
  
6.  Kategorileri bölmesinden **Güvenilen Konumlar**.  
  
7.  Ayrıntılar bölmesinden **yeni konum Ekle**.  
  
8.  İçinde **Microsoft Office güvenilir konum** iletişim kutusunda, içeren klasöre gidin **CallingCodeFromVBA** proje.  
  
9. Seçin **bu konumdaki alt klasörler güvenilen ayrıca**.  
  
10. İçinde **Microsoft Office güvenilir konum** iletişim kutusu, tıklayın **Tamam**.  
  
11. İçinde **Güven Merkezi** iletişim kutusu, tıklayın **Tamam**.  
  
12. İçinde **Excel Seçenekleri** iletişim kutusu, tıklayın **Tamam**.  
  
13. Çıkış **Excel**.  
  
## <a name="add-a-method-to-the-sheet1-class"></a>Sheet1 sınıfı için bir yöntem ekleyin  
 VBA projesi ayarlamak, ortak bir yöntem ekleyin `Sheet1` konak VBA kodu çağırabilir Item sınıfı.  
  
### <a name="to-add-a-method-to-the-sheet1-class"></a>Sheet1 sınıfı için bir yöntem eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **Sheet1.cs**ve ardından **kodu görüntüle**.  
  
     **Sheet1.cs** dosyası Kod Düzenleyicisi'nde açılır.  
  
2.  Aşağıdaki kodu ekleyin `Sheet1` sınıfı. `CreateVstoNamedRange` Yöntemi yeni bir oluşturur <xref:Microsoft.Office.Tools.Excel.NamedRange> belirtilen aralıkta nesne. Bu yöntem ayrıca için bir olay işleyicisi oluşturur <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> olayı <xref:Microsoft.Office.Tools.Excel.NamedRange>. Bu kılavuzda daha sonra çağıracaksınız `CreateVstoNamedRange` belgedeki VBA kodu yöntemi.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]  
  
3.  Aşağıdaki yöntemi ekleyin `Sheet1` sınıfı. Bu metot geçersiz kılmaları <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> geçerli örneğini döndürülecek yöntemi `Sheet1` sınıfı.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]  
  
4.  İlk satırından önce aşağıdaki öznitelikleri uygulanır `Sheet1` sınıfının bildirimi. Bu öznitelikler sınıfı görebilmesi com ancak bir sınıf arabirimi oluşturuluyor.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]  
  
## <a name="extract-an-interface-for-the-sheet1-class"></a>Sheet1 sınıfı için bir arabirimi Ayıkla  
 Oluşturmadan önce `CreateVstoNamedRange` yöntemi VBA kodu bu yöntemi tanımlayan bir ortak arabirim oluşturmanız gerekir ve bu arabirimi vystavit kullanıma sunması gerekir  
  
### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Sheet1 sınıfı için bir arabirimi ayıklamak için  
  
1.  İçinde **Sheet1.cs** kod dosyası, herhangi bir yeri tıklatın `Sheet1` sınıfı.  
  
2.  Üzerinde **yeniden düzenleme** menüsünde tıklatın **Arabirimi Ayıkla**.  
  
3.  İçinde **Arabirimi Ayıkla** iletişim kutusundaki **arayüz genel üyeleri seçin** için giriş kutusunda, `CreateVstoNamedRange` yöntemi.  
  
4.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adlı yeni bir arabirim oluşturur `ISheet1`, ve tanımını değiştirir `Sheet1` uygular sınıfının `ISheet1` arabirimi. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca açılır **Isheet1.cs** dosyası Kod Düzenleyicisi'nde.  
  
5.  İçinde **Isheet1.cs** dosyası, değiştirin `ISheet1` arabirimi aşağıdaki kodla bildirimi. Bu kod yapar `ISheet1` genel arabirim ve geçerli <xref:System.Runtime.InteropServices.ComVisibleAttribute> arabirimi COM görünür yapmak için özniteliği  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]  
  
6.  Projeyi oluşturun.  
  
## <a name="expose-the-method-to-vba-code"></a>VBA kodu yöntemi oluşturma  
 Kullanıma sunmak için `CreateVstoNamedRange` VBA kodu çalışma kitabında, yöntem kümesi **ReferenceAssemblyFromVbaProject** özelliği `Sheet1` konak öğesi **True**.  
  
### <a name="to-expose-the-method-to-vba-code"></a>VBA kodu yöntemi ortaya çıkarmak için  
  
1.  İçinde **Çözüm Gezgini**, çift **Sheet1.cs**.  
  
     **WorkbookWithVBA** görünür Sheet1 Tasarımcısı'nda dosyasını açar.  
  
2.  İçinde **özellikleri** penceresinde **ReferenceAssemblyFromVbaProject** özellik ve değere değiştirin **True**.  
  
3.  Tıklayın **Tamam** iletisinde görüntülenir.  
  
4.  Projeyi oluşturun.  
  
## <a name="call-the-method-from-vba-code"></a>VBA kodu yöntemini çağırın  
 Artık çağırabilirsiniz `CreateVstoNamedRange` VBA kodu çalışma kitabında yöntemi.  
  
> [!NOTE]  
>  Bu izlenecek yolda, proje hata ayıklama sırasında çalışma kitabına VBA kodu ekleyeceksiniz. Visual Studio ana proje klasöründen belgenin bir kopyasını ile belge derleme çıktısı klasörü içinde değiştirdiğinden projeyi sonraki açışınızda bu belgeye eklediğiniz VBA kodu üzerine yazılır. VBA kodu kaydetmek istiyorsanız, proje klasöründeki belgesine kopyalayabilirsiniz. Daha fazla bilgi için [birleştirmek VBA ve belge düzeyi özelleştirmeleri](../vsto/combining-vba-and-document-level-customizations.md).  
  
### <a name="to-call-the-method-from-vba-code"></a>VBA kodu yöntemini çağırmak için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Üzerinde **Geliştirici** sekmesinde **kod** grubunda **Visual Basic**.  
  
     Visual Basic Düzenleyicisi açılır.  
  
3.  Üzerinde **Ekle** menüsünde tıklatın **Modülü**.  
  
4.  Yeni modül için aşağıdaki kodu ekleyin.  
  
     Bu kod `CreateTable` özelleştirme derlemesindeki yöntemi. Makro bu yöntem genel kullanarak erişir `GetManagedClass` erişmeye yöntemi `Sheet1` konak VBA koduna kullanıma sunulan Item sınıfı. `GetManagedClass` Yöntemi ayarladığınızda otomatik olarak oluşturulan **ReferenceAssemblyFromVbaProject** bu kılavuzda daha önce açıklanan özelliği.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1  
        Set VSTOSheet1 = GetManagedClass(Sheet1)  
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")  
    End Sub  
    ```  
  
5.  Tuşuna **F5**.  
  
6.  Açık çalışma kitabında, hücreyi tıklatın **A1** üzerinde **Sayfa1**. İleti kutusunda göründüğünü doğrulayın.  
  
7.  Excel, değişikliklerinizi kaydetmeden çıkmak.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu konu başlıklarında VBA'dan Office çözümlerinde kod çağırma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Konak öğesi VBA'dan Visual Basic özelleştirmelerinde kodu çağırın. Bu işlem Visual C# işleminden farklıdır. Daha fazla bilgi için [izlenecek yol: çağrı kodu VBA içinden bir Visual Basic projesinde](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   VBA içinden VSTO eklentisi kodu çağırın. Daha fazla bilgi için [izlenecek yol: çağrı kodu bir VSTO eklenti VBA'dan](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [Nasıl yapılır: Visual Basic projesinde kodu sunmaya](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Nasıl yapılır: Visual c kodu sunmaya&#35; proje](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [İzlenecek yol: kod Visual Basic projesinde VBA'dan çağırın](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  