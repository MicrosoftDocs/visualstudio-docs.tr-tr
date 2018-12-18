---
title: 'İzlenecek yol: bir çalışma kitabından bir sunucuda önbelleğe alınmış verileri alma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2365fc766ede37d39eccdccc664d5710dc68d586
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673009"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>İzlenecek yol: bir çalışma kitabından bir sunucuda önbelleğe alınmış verileri alma
  Bu kılavuzda bir Microsoft Office Excel çalışma kitabını Excel kullanarak başlatmadan önbelleğe alınan bir veri kümesinden veri almayı gösterir <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Verileri içeren bir veri kümesi tanımlayarak *AdventureWorksLT* veritabanı.  
  
- Veri kümesinin örnekleri, bir Excel çalışma kitabı projesi ve bir konsol uygulama projesi oluşturma.  
  
- Oluşturma bir <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma kitabındaki veri kümesine bağlı ve doldurulurken <xref:Microsoft.Office.Tools.Excel.ListObject> verilerle çalışma kitabı açılır.  
  
- Veri kümesini çalışma kitabında veri önbelleğine ekleniyor.  
  
- Excel başlatmadan konsol uygulamasında, veri kümesine önbelleğe alınan veri kümesindeki verileri okuma.  
  
  Bu izlenecek yol, geliştirme bilgisayarınızda kodun çalıştığını varsayar olsa da, bu izlenecek yol gösterilen kod Excel yüklü olmayan bir sunucu üzerinde kullanılabilir.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Microsoft SQL Server veya Microsoft SQL Server bağlı AdventureWorksLT örnek veritabanı olan Express çalışan örneğine erişim. AdventureWorksLT veritabanı indirebileceğiniz [CodePlex Web sitesinde](http://go.microsoft.com/fwlink/?linkid=87843). Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
    -   SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz: [nasıl yapılır: veritabanı (SQL Server Management Studio) ekleme](/sql/relational-databases/databases/attach-a-database).  
  
    -   Komut satırını kullanarak bir veritabanı eklemek için bkz: [nasıl yapılır: SQL Server Express için bir veritabanı dosyası iliştirmek](/previous-versions/sql/).  
  
## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Bir veri kümesini tanımlayan bir sınıf kitaplığı projesi oluşturun  
 Bir Excel çalışma kitabı projesi ve bir konsol uygulaması aynı veri kümesini kullanmak için ayrı bir derleme hem de bu proje tarafından başvurulan dataset tanımlamanız gerekir. Bu kılavuz için bir sınıf kitaplığı projesinde veri kümesi tanımlarsınız.  
  
### <a name="create-the-class-library-project"></a>Sınıf kitaplığı projesi oluşturun  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Windows**.  
  
4.  Proje şablonları listesinde seçin **sınıf kitaplığı**.  
  
5.  İçinde **adı** kutusuna **AdventureWorksDataSet**.  
  
6.  Tıklayın **Gözat**, gidin, *%UserProfile%\My belgeleri* (Windows XP ve önceki sürümler) veya *%UserProfile%\Documents* (için Windows Vista) klasörünü ve ardından **Klasör Seç**.  
  
7.  İçinde **yeni proje** iletişim kutusunda **çözüm için dizin oluştur** onay kutusu seçilmez.  
  
8.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **AdventureWorksDataSet** için proje **Çözüm Gezgini** ve açılır *Class1.cs* veya *Class1.vb* kod dosyası.  
  
9. İçinde **Çözüm Gezgini**, sağ *Class1.cs* veya *Class1.vb*ve ardından **Sil**. Bu kılavuz için bu dosyayı gerekmez.  
  
## <a name="define-a-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde bir veri kümesi tanımlayın  
 SQL Server 2005'te AdventureWorksLT veritabanında verileri içeren bir türü belirtilmiş veri kümesi tanımlayın. Bu kılavuzda daha sonra bu veri kümesi, bir Excel çalışma kitabı projesi ve bir konsol uygulama projesi başvurur.  
  
 Veri kümesi bir *yazılan veri kümesi* AdventureWorksLT veritabanı ürün tablodaki verileri temsil eden. Türü belirtilmiş veri kümeleri hakkında daha fazla bilgi için bkz. [Visual Studio'daki veri kümesi Araçları](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde bir türü belirtilmiş veri kümesi tanımlayın  
  
1. İçinde **Çözüm Gezgini**, tıklayın **AdventureWorksDataSet** proje.  
  
2. Varsa **veri kaynakları** penceresi görünür değilse, bunu, menü çubuğundan seçme görüntüleyebilir **görünümü** > **diğer Windows**  >   **Veri kaynakları**.  
  
3. Seçin **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
4. Tıklayın **veritabanı**ve ardından **sonraki**.  
  
5. AdventureWorksLT veritabanında var olan bir bağlantınız varsa bu bağlantıyı seçin ve tıklayın **sonraki**.  
  
    ' A tıklayıp **yeni bağlantı**ve **Bağlantı Ekle** yeni bir bağlantı oluşturmak için iletişim kutusu. Daha fazla bilgi için [yeni bağlantı ekleme](../data-tools/add-new-connections.md).  
  
6. İçinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.  
  
7. İçinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** seçip **ürün (SalesLT)**.  
  
8. **Son**'a tıklayın.  
  
    *AdventureWorksLTDataSet.xsd* dosya eklendiğinde **AdventureWorksDataSet** proje. Bu dosya, aşağıdakileri tanımlar:  
  
   - Adlı bir türü belirtilmiş veri kümesi `AdventureWorksLTDataSet`. Bu veri kümesi Product tablosunda AdventureWorksLT veritabanında içeriğini temsil eder.  
  
   - Adlı bir TableAdapter `ProductTableAdapter`. Bu TableAdapter okuyup veri yazmak için kullanılan `AdventureWorksLTDataSet`. Daha fazla bilgi için [TableAdapter genel bakışı](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Bu izlenecek yolda, bu nesnelerin her ikisi de kullanır.  
  
9. İçinde **Çözüm Gezgini**, sağ **AdventureWorksDataSet** tıklatıp **yapı**.  
  
     Projenin hatasız oluşturulduğunu doğrulayın.  
  
## <a name="create-an-excel-workbook-project"></a>Bir Excel çalışma kitabı projesi oluşturma  
 Arabirimi için verileri bir Excel çalışma kitabı projesi oluşturun. Bu kılavuzda daha sonra oluşturacağınız bir <xref:Microsoft.Office.Tools.Excel.ListObject> verileri görüntüleyen ve çalışma kitabının veri önbelleğindeki bir örnek veri kümesi ekleyeceksiniz.  
  
### <a name="create-the-excel-workbook-project"></a>Excel çalışma kitabı projesi oluşturma  
  
1.  İçinde **Çözüm Gezgini**, sağ **AdventureWorksDataSet** çözümü noktasına **Ekle**ve ardından **yeni proje**.  
  
2.  Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Office/SharePoint**.  
  
3.  Genişletilmiş altında **Office/SharePoint** düğümünü **Office eklentilerini** düğümü.  
  
4.  Proje şablonları listesinde seçin **Excel 2010 Çalışma kitabı** veya **Excel 2013'ün çalışma kitabı** proje.  
  
5.  İçinde **adı** kutusuna **AdventureWorksReport**. Konumunu değiştirmeyin.  
  
6.  **Tamam**'ı tıklatın.  
  
     **Office Project Sihirbazı için Visual Studio Araçları** açılır.  
  
7.  Emin **yeni belge oluşturma** seçilir ve tıklayın **Tamam**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açılır **AdventureWorksReport** çalışma kitabını tasarımcıda ve ekler **AdventureWorksReport** için proje **Çözüm Gezgini**.  
  
## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Excel çalışma kitabı projesi raporu veri kaynakları için veri kümesi Ekle  
 Excel çalışma kitabında veri kümesini görüntülemeden önce Excel çalışma kitabı projesi raporu veri kaynakları için ilk veri kümesini eklemeniz gerekir.  
  
1.  İçinde **Çözüm Gezgini**, çift *Sheet1.cs* veya *Sheet1.vb* altında **AdventureWorksReport** proje.  
  
     Çalışma kitabını tasarımcıda açılır.  
  
2.  Üzerinde **veri** menüsünü tıklatın **yeni veri kaynağı Ekle**.  
  
     **Veri kaynağı Yapılandırma Sihirbazı** açılır.  
  
3.  Tıklayın **nesne**ve ardından **sonraki**.  
  
4.  İçinde **bağlamak istediğiniz nesneyi seçin** sayfasında için **Başvuru Ekle**.  
  
5.  Üzerinde **projeleri** sekmesinde **AdventureWorksDataSet** ve ardından **Tamam**.  
  
6.  Altında **AdventureWorksDataSet** ad **AdventureWorksDataSet** derlemesi tıklayın **AdventureWorksLTDataSet** ve ardından **son** .  
  
     **Veri kaynakları** penceresi açılır ve **AdventureWorksLTDataSet** veri kaynaklarının listesine eklenir.  
  
## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Veri kümesi örneğine bağlı ListObject oluşturma  
 Çalışma kitabında veri kümesini görüntülemek için oluşturun bir <xref:Microsoft.Office.Tools.Excel.ListObject> dataset örneğine bağlı. Denetimlere veri bağlama hakkında daha fazla bilgi için bkz: [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
1.  İçinde **veri kaynakları** penceresini genişletin **AdventureWorksLTDataSet** düğümünde **AdventureWorksDataSet**.  
  
2.  Seçin **ürün** düğümünde görünür ve seçin, aşağı açılan oku tıklatın **ListObject** aşağı açılan listesinde.  
  
     Açılan liste okunu görünmüyorsa, çalışma kitabını tasarımcıda açık olduğundan emin olun.  
  
3.  Sürükleme **ürün** A1 hücresine tablo.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> adlı Denetim `productListObject` çalışma A1 hücresine başlayarak oluşturulur. Aynı anda, adlı bir veri kümesi nesnesi `adventureWorksLTDataSet` ve <xref:System.Windows.Forms.BindingSource> adlı `productBindingSource` projeye eklenir. <xref:Microsoft.Office.Tools.Excel.ListObject> Bağlı <xref:System.Windows.Forms.BindingSource>, sırayla bağlı dataset nesnesine.  
  
## <a name="add-the-dataset-to-the-data-cache"></a>Veri önbelleğe veri kümesi Ekle  
 Çalışma kitabındaki veri kümesine erişim Excel çalışma kitabı projesi dışındaki kod etkinleştirmek için veri kümesine veri önbelleğine eklemeniz gerekir. Veri önbelleği hakkında daha fazla bilgi için bkz. [veri belge düzeyi özelleştirmelerdeki önbelleğe alınmış](../vsto/cached-data-in-document-level-customizations.md) ve [veriyi önbelleğe alma](../vsto/caching-data.md).  
  
1.  Tasarımcıda **adventureWorksLTDataSet**.  
  
2.  İçinde **özellikleri** penceresinde **değiştiriciler** özelliğini **genel**.  
  
3.  Ayarlama **CacheInDocument** özelliğini **True**.  
  
## <a name="initialize-the-dataset-in-the-workbook"></a>Çalışma kitabındaki veri kümesini Başlat  
 Konsol uygulaması kullanarak önbelleğe alınmış veri kümesinden veri almadan önce önbelleğe alınmış veri kümesini verilerle doldurmanız gerekir.  
  
1.  İçinde **Çözüm Gezgini**, sağ *Sheet1.cs* veya *Sheet1.vb* tıklayın ve dosya **Kodu Görüntüle**.  
  
2.  Değiştirin `Sheet1_Startup` aşağıdaki kod ile olay işleyicisi. Bu kod örneğini kullanan `ProductTableAdapter` tanımlanan sınıfı **AdventureWorksDataSet** şu anda boş ise, önbellekteki veri kümesini verilerle doldurmak için proje.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Oluşturup derler ve hatasız çalışan emin olmak için Excel çalışma kitabı projesi çalıştırın. Bu işlem ayrıca önbellekteki veri kümesini doldurur ve verileri çalışma kitabında kaydeder.  
  
### <a name="build-and-run-the-project"></a>Derleme ve proje çalıştırma  
  
1.  İçinde **Çözüm Gezgini**, sağ **AdventureWorksReport** projesinin **hata ayıklama**ve ardından **yeni örnek Başlat**.  
  
     Proje oluşturulur ve Excel çalışma kitabı açılır. Aşağıdakileri doğrulayın:  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject> Verilerle doldurur.  
  
    -   Değer **ListPrice** ilk satır için sütun <xref:Microsoft.Office.Tools.Excel.ListObject> 1431.5. Bu kılavuzda daha sonra bir konsol uygulaması değerleri değiştirmek için kullanacağı **ListPrice** sütun.  
  
2.  Çalışma kitabını kaydedin. Dosya adı veya çalışma kitabını konumunu değiştirmeyin.  
  
3.  Excel'i kapatın.  
  
## <a name="create-a-console-application-project"></a>Bir konsol uygulama projesi oluşturma  
 Önbellekteki veri kümesini çalışma kitabındaki verileri değiştirmek için bir konsol uygulama projesi oluşturun.  
  
1.  İçinde **Çözüm Gezgini**, sağ **AdventureWorksDataSet** çözümü noktasına **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **proje türleri** bölmesini genişletin **Visual C#** veya **Visual Basic**ve ardından **Windows**.  
  
3.  İçinde **şablonları** bölmesinde **konsol uygulaması**.  
  
4.  İçinde **adı** kutusuna **DataReader**. Konumunu değiştirmeyin.  
  
5.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **DataReader** için proje **Çözüm Gezgini** ve açılır *Program.cs* veya *Module1.vb* kod dosyası.  
  
## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Konsol uygulaması kullanarak önbelleğe alınmış veri kümesinden veri alın  
 Kullanım <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı yerel verileri okumak için konsol uygulamasındaki `AdventureWorksLTDataSet` nesne. Yerel veri kümesi önbelleğe alınan veri kümesine ilişkin verilerin başlatıldı onaylamak için uygulamayı yerel veri kümesindeki satır sayısını görüntüler.  
  
### <a name="retrieve-data-from-the-cached-dataset"></a>Önbelleğe alınmış veri kümesinden veri alın  
  
1. İçinde **Çözüm Gezgini**, sağ **DataReader** projesine **Başvuru Ekle**.  
  
2. Üzerinde **.NET** sekmesinde **Microsoft.VisualStudio.Tools.Applications.ServerDocument**.  
  
3. **Tamam**'ı tıklatın.  
  
4. İçinde **Çözüm Gezgini**, sağ **DataReader** projesine **Başvuru Ekle**.  
  
5. Üzerinde **projeleri** sekmesinde **AdventureWorksDataSet**, tıklatıp **Tamam**.  
  
6. Açık *Program.cs* veya *Module1.vb* dosyasını Kod düzenleyicisinde.  
  
7. Aşağıdaki **kullanarak** (için C#) veya **içeri aktarmalar** (Visual Basic için) kod dosyasının en üstüne deyimi.  
  
    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8. Aşağıdaki kodu ekleyin `Main` yöntemi. Bu kod, aşağıdaki nesneleri bildirir:  
  
   - Örneği `AdventureWorksLTDataSet` içinde tanımlanan tür **AdventureWorksDataSet** proje.  
  
   - Derleme klasöründe AdventureWorksReport çalışma kitabı yolu **AdventureWorksReport** proje.  
  
   - A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> çalışma kitabındaki verileri önbelleğe erişmek için kullanılacak nesne.  
  
     > [!NOTE]  
     >  Aşağıdaki kodu kullanarak, çalışma kitabını kaydettiğiniz varsayar *.xlsx* uzantısı. Projenizdeki çalışma kitabının farklı bir uzantısı varsa, yol gerekli olarak değiştirin.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]  
  
9. Aşağıdaki kodu ekleyin `Main` yöntemi, önceki adımda eklediğiniz koddan sonra. Bu kod aşağıdaki görevleri gerçekleştirir:  
  
   - Kullandığı <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> özelliği <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> çalışma kitabında önbelleğe alınan veri kümesine erişmesine izin sınıfı.  
  
   - Önbelleğe alınmış veri kümesinden verileri yerel kümesine okur.  
  
   - Satır sayısı, veri olduğunu doğrulamak için yerel veri kümesini görüntüler.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]  
  
10. Üzerinde **derleme** menüsünde tıklatın **Build DataReader**.  
  
## <a name="test-the-project"></a>Test projesi  
 Konsol uygulamasını çalıştırdığınızda, yerel veri kümesindeki satır sayısını görüntüler.  
  
### <a name="test-the-workbook"></a>Çalışma kitabını test  
  
1.  İçinde **Çözüm Gezgini**, sağ **DataReader** proje, işaret **hata ayıklama**ve ardından **yeni örnek Başlat**.  
  
     Uygulama yerel veri kümesi 295 satır olduğunu bildirir doğrulayın.  
  
2.  Tuşuna **Enter** uygulamayı kapatmak için.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu konu başlıkları önbelleğe alınan verilerle çalışma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Önbelleğe alınan bir veri kümesindeki verileri Excel başlatmadan değiştirme. Daha fazla bilgi için [izlenecek yol: sunucudaki çalışma kitabında veri değişikliği önbelleğe](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: sunucudaki çalışma kitabına veri ekleme](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [İzlenecek yol: sunucudaki çalışma kitabında önbelleğe alınmış verileri değiştirme](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
  
  