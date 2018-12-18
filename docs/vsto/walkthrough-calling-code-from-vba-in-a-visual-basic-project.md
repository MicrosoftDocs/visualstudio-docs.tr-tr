---
title: "İzlenecek yol: kod Visual Basic projesinde VBA'dan çağırın"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bd766e8ce1896c0b53d32cbe3f4174da5bc934d7
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808943"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>İzlenecek yol: kod Visual Basic projesinde VBA'dan çağırın
  Bu kılavuzda bir yöntem belge düzeyi özelleştirmesinde için Microsoft Office Word Visual Basic'ten belgedeki Applications (VBA) kodu için nasıl çağrılacağını gösterir. Yordamı üç temel adımdan oluşur: bir yöntem ekleyin `ThisDocument` konak öğesi sınıfına, VBA kodu yöntemi kullanıma sunar ve belgedeki VBA kodu, ardından yöntemi çağırın.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Bu izlenecek yolda Word özellikle kullansa da, izlenecek yol gösterilen kavramları Excel için belge düzeyi projelere de geçerlidir.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   VBA kodu içeren bir belge oluşturma.  
  
-   Belge konumunu Word'de Güven Merkezi'ndeki kullanarak güvenen.  
  
-   Bir yöntem ekleme `ThisDocument` ana öğe sınıfı.  
  
-   VBA kodu yöntemi açığa çıkarma.  
  
-   VBA koddan yöntemini çağırma.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-a-document-that-contains-vba-code"></a>VBA kodu içeren bir belge oluşturma  
 İlk adım, basit bir VBA makrosu içeren makro özellikli bir belge oluşturmaktır. Bu belgeye dayalı bir Visual Studio projesi oluşturmadan önce belge bir VBA projesi içermelidir. Aksi takdirde, Visual Studio VBA kodunu özelleştirme bütünleştirilmiş kod içine çağırmak için etkinleştirmek için bir VBA projesi değiştiremezsiniz.  
  
 Kullanmak istediğiniz VBA kodu içeren bir belge zaten varsa bu adımı atlayabilirsiniz.  
  
### <a name="to-create-a-document-that-contains-vba-code"></a>VBA kodu içeren bir belge oluşturmak için  
  
1.  Word'ü başlatın.  
  
2.  Bir sözcük etkin belgeyi Kaydet **Enabled Document (\*.docm)** adıyla **DocumentWithVBA**. Masaüstü gibi uygun bir konuma kaydedin.  
  
3.  Şerit üzerinde tıklayın **Geliştirici** sekmesi.  
  
    > [!NOTE]  
    >  Varsa **Geliştirici** sekme görünür değilse, önce görünür olmalıdır. Daha fazla bilgi için [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  İçinde **kod** grubunda **Visual Basic**.  
  
     Visual Basic Düzenleyicisi açılır.  
  
5.  İçinde **proje** penceresinde çift **ThisDocument**.  
  
     Kod dosyası `ThisDocument` nesnesini açar.  
  
6.  Aşağıdaki VBA kodu için kod dosyasını ekleyin. Bu kod, hiçbir şey yapmaz basit bir işlevi tanımlar. Tek amacı, bu işlev, belgede bir VBA projesi bulunduğunu sağlamaktır. Bu, sonraki adımlarda bu izlenecek yol için gereklidir.  
  
    ```vb  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Belgeyi kaydedin ve sözcük çıkın.  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 Artık, daha önce oluşturduğunuz makro özellikli belge kullanan Word için belge düzeyi projesi oluşturabilirsiniz.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**. IDE'nizi Visual Basic geliştirme ayarlarını kullanmaya ayarlanmışsa **dosya** menüsünü tıklatın **yeni proje**.  
  
3.  Şablonlar bölmesinde, **Visual Basic**ve ardından **Office/SharePoint**.  
  
4.  Seçin **Office eklentilerini** düğümü.  
  
5.  Proje şablonları listesinde seçin **Word 2010 Belgesi** veya **Word 2013 belge** proje.  
  
6.  İçinde **adı** kutusuna **CallingCodeFromVBA**.  
  
7.  **Tamam**'ı tıklatın.  
  
     **Office Project Sihirbazı için Visual Studio Araçları** açılır.  
  
8.  Seçin **mevcut belgeyi kopyalamak**hem de **mevcut belgenin tam yolu** kutusunda, konumu belirtin **DocumentWithVBA** daha önce oluşturduğunuz belge . Bu belgenin konumunu, kendi makro özellikli bir belgeyi kullanıyorsanız, bunun yerine belirtin.  
  
9. **Son**'a tıklayın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açılır **DocumentWithVBA** ekler ve belgeyi tasarımcıda **CallingCodeFromVBA** için proje **Çözüm Gezgini**.  
  
## <a name="trust-the-location-of-the-document"></a>Belgenin konumunu güven  
 Çözümünüzdeki belgedeki VBA kodu için kod oluşturmadan önce çalıştırılacak belgedeki VBA güvenmesi gerekir. Bunu yapmanın birkaç yolu vardır. Bu kılavuz için belge konumunu güvenilir **Güven Merkezi** Word.  
  
### <a name="to-trust-the-location-of-the-document"></a>Belgenin konumunu güvenmek için  
  
1.  Word'ü başlatın.  
  
2.  Tıklayın **dosya** sekmesi.  
  
3.  Tıklayın **Word Seçenekleri** düğmesi.  
  
4.  Kategorileri bölmesinden **Güven Merkezi**.  
  
5.  Ayrıntılar bölmesinden **Güven Merkezi Ayarları**.  
  
6.  Kategorileri bölmesinden **Güvenilen Konumlar**.  
  
7.  Ayrıntılar bölmesinden **yeni konum Ekle**.  
  
8.  İçinde **Microsoft Office güvenilir konum** iletişim kutusunda, içeren klasöre gidin **CallingCodeFromVBA** proje.  
  
9. Seçin **bu konumdaki alt klasörler güvenilen ayrıca**.  
  
10. İçinde **Microsoft Office güvenilir konum** iletişim kutusu, tıklayın **Tamam**.  
  
11. İçinde **Güven Merkezi** iletişim kutusu, tıklayın **Tamam**.  
  
12. İçinde **Word Seçenekleri** iletişim kutusu, tıklayın **Tamam**.  
  
13. Word çıkın.  
  
## <a name="add-a-method-to-the-thisdocument-class"></a>Bir yöntem ThisDocument sınıfına ekleyin.  
 VBA projesi ayarlamak, bir yöntem ekleyin `ThisDocument` konak VBA kodu çağırabilir Item sınıfı.  
  
### <a name="to-add-a-method-to-the-thisdocument-class"></a>ThisDocument sınıfına bir yöntem eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **ThisDocument.vb**ve ardından **kodu görüntüle**.  
  
     **ThisDocument.vb** dosyası Kod Düzenleyicisi'nde açılır.  
  
2.  Aşağıdaki yöntemi ekleyin `ThisDocument` sınıfı. Bu yöntem, iki satır ve belgenin başına iki sütunlu bir tablo oluşturur. Parametreleri ilk satırında görüntülenen metni belirtin. Bu kılavuzda daha sonra bu yöntem belgedeki VBA kodu çağıracaksınız.  
  
     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]  
  
3.  Projeyi oluşturun.  
  
## <a name="expose-the-method-to-vba-code"></a>VBA kodu yöntemi oluşturma  
 Kullanıma sunmak için `CreateTable` belgedeki VBA kodunu yöntem kümesi **EnableVbaCallers** özelliği `ThisDocument` konak öğesi **True**.  
  
### <a name="to-expose-the-method-to-vba-code"></a>VBA kodu yöntemi ortaya çıkarmak için  
  
1.  İçinde **Çözüm Gezgini**, çift **ThisDocument.vb**.  
  
     **DocumentWithVBA** dosyası tasarımcıda açılır.  
  
2.  İçinde **özellikleri** penceresinde **EnableVbaCallers** özellik ve değere değiştirin **True**.  
  
3.  Tıklayın **Tamam** iletisinde görüntülenir.  
  
4.  Projeyi oluşturun.  
  
## <a name="call-the-method-from-vba-code"></a>VBA kodu yöntemini çağırın  
 Artık çağırabilirsiniz `CreateTable` belgedeki VBA kodu yöntemi.  
  
> [!NOTE]  
>  Bu izlenecek yolda, proje hata ayıklama sırasında VBA kodunu belgeye ekleyeceksiniz. Visual Studio ana proje klasöründen belgenin bir kopyasını ile belge derleme çıktısı klasörü içinde değiştirdiğinden projeyi sonraki açışınızda bu belgeye eklediğiniz VBA kodu üzerine yazılır. VBA kodu kaydetmek istiyorsanız, proje klasöründeki belgesine kopyalayabilirsiniz. Daha fazla bilgi için [birleştirmek VBA ve belge düzeyi özelleştirmeleri](../vsto/combining-vba-and-document-level-customizations.md).  
  
### <a name="to-call-the-method-from-vba-code"></a>VBA kodu yöntemini çağırmak için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Üzerinde **Geliştirici** sekmesinde **kod** grubunda **Visual Basic**.  
  
     Visual Basic Düzenleyicisi açılır.  
  
3.  Üzerinde **Ekle** menüsünde tıklatın **Modülü**.  
  
4.  Yeni modül için aşağıdaki kodu ekleyin.  
  
     Bu kod `CreateTable` özelleştirme derlemesindeki yöntemi. Makro bu yöntemi kullanarak erişir `CallVSTOAssembly` özelliği `ThisDocument` nesne. Ayarladığınızda bu özellik otomatik olarak oluşturulmuş **EnableVbaCallers** bu kılavuzda daha önce açıklanan özelliği.  
  
    ```vb  
    Sub CreateTable()  
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")  
    End Sub  
    ```  
  
5.  Tuşuna **F5**.  
  
6.  Belgeye yeni bir tablo eklendiğini doğrulayın.  
  
7.  Word, değişikliklerinizi kaydetmeden çıkmak.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu konu başlıklarında VBA'dan Office çözümlerinde kod çağırma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Bir Visual C# özelleştirme VBA'dan Kod çağırın. Bu işlem, Visual Basic işleminden farklıdır. Daha fazla bilgi için [izlenecek yol: Visual c VBA'dan Kod Çağırma&#35; proje](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
-   VBA içinden VSTO eklentisi kodu çağırın. Daha fazla bilgi için [izlenecek yol: çağrı kodu bir VSTO eklenti VBA'dan](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [Nasıl yapılır: Visual Basic projesinde kodu VBA kullanımına sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Nasıl yapılır: kodu Visual c VBA kullanımına sunma&#35; proje](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [İzlenecek yol: Visual c VBA'dan Kod Çağırma&#35; proje](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)  
  
  