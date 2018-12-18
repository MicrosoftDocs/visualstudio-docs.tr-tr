---
title: 'İzlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1bc8aee0a1294aeda4c57a3416de4a0cc98129f3
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673048"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>İzlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama
  Bu yönerge, içerik denetimleri belge içinde depolanan XML verilerini Word için belge düzeyi özelleştirmesinde bağlamak nasıl gösterir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word XML verileri, adlı depolamanızı sağlar *özel XML bölümleri*, bir belgedeki. İçerik denetimlerini özel bir XML parçasına öğeleri bağlama tarafından bu verilerin görünümünü denetleyebilirsiniz. Bu kılavuzda örnek belge içinde özel bir XML parçasına depolanan çalışan bilgilerini görüntüler. Belgeyi açtığında içerik denetimleri XML öğe değerlerini görüntüler. Özel XML bölümünde içerik denetimlerini metinde yaptığınız tüm değişiklikler kaydedilir.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Tasarım zamanında, Word belgesine bir belge düzeyi projede içerik denetimleri ekleme.  
  
- XML veri dosyası ve içerik denetimlerine bağlama öğeleri tanımlayan bir XML şeması oluşturma.  
  
- XML Şeması belge tasarım zamanında iliştiriliyor.  
  
- Özel bir XML parçasına zamanında belgedeki XML dosyasının içeriğini ekleme.  
  
- İçerik denetimlerini özel XML parçasına öğeleri bağlama.  
  
- Bağlama bir <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> XML şemasında tanımlanan değerleri bir dizi.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-a-new-word-document-project"></a>Yeni bir Word belgesi projesi oluşturma  
 İzlenecek yolda kullanacağınız bir Word belgesi oluşturun.  
  
### <a name="to-create-a-new-word-document-project"></a>Yeni bir Word belgesi projesi oluşturmak için  
  
1.  Adlı bir Word belgesi projesi oluşturun **ÇalışanDenetimleri**. Çözüm için yeni bir belge oluşturun. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tasarımcıda yeni Word belgesi açar ve ekler **ÇalışanDenetimleri** için proje **Çözüm Gezgini**.  
  
## <a name="add-content-controls-to-the-document"></a>Belge içerik denetimleri ekleme  
 Üç farklı türde burada kullanıcı görüntüleyebilir veya bir çalışan ilişkin bilgileri düzenlemek içerik denetimlerini içeren bir tablo oluşturun.  
  
### <a name="to-add-content-controls-to-the-document"></a>İçerik denetimleri belgeye eklemek için  
  
1. Barındırılan Word belgesinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı Şerit üzerindeki **Ekle** sekmesi.  
  
2. İçinde **tabloları** Grup öğesini **tablo**ve 2 sütun ve 3 satır içeren bir tablo ekleyin.  
  
3. Aşağıdaki sütun benzeyecek şekilde ilk sütunundaki metni yazın:  
  
   ||  
   |-|  
   |**Çalışan adı**|  
   |**İşe Alınma Tarihi**|  
   |**Başlık**|  
  
4. İlk satırı tablo ikinci sütunda seçin (yanındaki **çalışan adı**).  
  
5. Şerit üzerinde **Geliştirici** sekmesi.  
  
   > [!NOTE]  
   >  Varsa **Geliştirici** sekme görünür değilse, önce görünür olmalıdır. Daha fazla bilgi için [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. İçinde **denetimleri** Grup öğesini **metin** düğmesi ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") bir eklemekiçin<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>ilk hücreye.  
  
7. İkinci satır tablonun ikinci sütunda seçin (yanındaki **işe giriş tarihi**).  
  
8. İçinde **denetimleri** Grup öğesini **tarih seçici** düğmesi ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") bir eklemekiçin<xref:Microsoft.Office.Tools.Word.DatePickerContentControl> ikinci hücreye.  
  
9. Üçüncü satır tablonun ikinci sütunda seçin (yanındaki **başlık**).  
  
10. İçinde **denetimleri** Grup öğesini **açılır listede** düğmesi ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") eklemek için bir <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> son hücreye.  
  
    Bu proje için tüm kullanıcı arabirimi olmasıdır. Projeyi çalıştırmak, artık ilk satırında bir metin yazın ve ikinci satırında bir tarih seçin. Sonraki adım, belgenin bir XML dosyasında görüntülemek istediğiniz veri eklemektir.  
  
## <a name="create-the-xml-data-file"></a>XML veri dosyası oluşturma  
 Genellikle, bir dosya veya veritabanı gibi bir dış kaynaktan özel bir XML parçasına depolamak için XML verileri elde edersiniz. Bu kılavuzda, belgede içerik denetimlerine bağlama öğeleri tarafından işaretlenen çalışan verilerini içeren bir XML dosyası oluşturun. Verileri çalışma zamanında kullanılabilir hale getirmek için XML dosyasını özelleştirme derlemede bir kaynak olarak ekleyin.  
  
#### <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için  
  
1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
2.  İçinde **şablonları** bölmesinde **XML dosyası**.  
  
3.  Dosya adı **employees.xml**ve ardından **Ekle** düğmesi.  
  
     **Employees.xml** dosyası Kod Düzenleyicisi'nde açılır.  
  
4.  Öğesinin içeriğini değiştirin **employees.xml** aşağıdaki metni içeren dosya.  
  
    ```xml 
    <?xml version="1.0" encoding="utf-8" ?>  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  İçinde **Çözüm Gezgini**, seçin **employees.xml** dosya.  
  
6.  İçinde **özellikleri** penceresinde **derleme eylemi** özellik ve değere değiştirin **gömülü kaynak**.  
  
     Proje oluşturduğunuzda, bu adımı XML dosyasını bir kaynak olarak derlemeye gömer. Bu, çalışma zamanında XML dosyasının içeriğini erişmenize olanak sağlar.  
  
## <a name="create-an-xml-schema"></a>XML şeması oluşturma  
 Özel XML bölümleri tek bir öğede bir içerik denetimi bağlamak istiyorsanız, bir XML şeması kullanmak zorunda değil. Ancak, bağlamak için <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> değerleri kümesi için daha önce oluşturduğunuz XML veri dosyası doğrulayan bir XML Şeması oluşturmalısınız. XML şeması için olası değerler tanımlar `title` öğesi. Bağlı olacağı <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> bu kılavuzda daha sonra bu öğe için.  
  
#### <a name="to-create-an-xml-schema"></a>Bir XML şeması oluşturmak için  
  
1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
2.  İçinde **şablonları** bölmesinde **XML Şeması**.  
  
3.  Şema adı **employees.xsd** ve **Ekle** düğmesi.  
  
     Şema Tasarımcısı açılır.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **employees.xsd**ve ardından **kodu görüntüle**.  
  
5.  Öğesinin içeriğini değiştirin **employees.xsd** aşağıdaki şema dosyası.  
  
    ```xml
    <?xml version="1.0" encoding="utf-8" ?>  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** yaptığınız değişiklikleri kaydetmek için **employees.xml** ve **employees.xsd** dosyaları.  
  
## <a name="attach-the-xml-schema-to-the-document"></a>XML Şeması belge ekleme  
 Belgenin bağlamak için XML şeması ekleme <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> geçerli değerlerine `title` öğesi.  
  
### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>XML Şeması belgeye ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Etkinleştirme **ÇalışanDenetimleri.docx'i** Tasarımcısı'nda.  
  
2.  Şerit üzerinde **Geliştirici** sekmesine ve ardından **eklentileri** düğmesi.  
  
3.  İçinde **şablonları ve eklentileri** iletişim kutusunda **XML Şeması** sekmesine ve ardından **Şema Ekle** düğmesi.  
  
4.  Gözat **employees.xsd** şema daha önce oluşturduğunuz, hangi proje dizininde yer alan ve ardından **açık** düğmesi.  
  
5.  Seçin **Tamam** düğmesine **şema ayarları** iletişim kutusu.  
  
6.  Seçin **Tamam** kapatmak için düğme **şablonları ve eklentileri** iletişim kutusu.  
  
### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>XML Şeması belge (Word 2010) eklemek için  
  
1.  Etkinleştirme **ÇalışanDenetimleri.docx'i** Tasarımcısı'nda.  
  
2.  Şerit üzerinde **Geliştirici** sekmesi.  
  
3.  İçinde **XML** Grup öğesini **şema** düğmesi.  
  
4.  İçinde **şablonları ve eklentileri** iletişim kutusunda **XML Şeması** sekmesine ve ardından **Şema Ekle** düğmesi.  
  
5.  Gözat **employees.xsd** proje dizininde bulunur ve seçin, daha önce oluşturduğunuz şema **açık** düğmesi.  
  
6.  Seçin **Tamam** düğmesine **şema ayarları** iletişim kutusu.  
  
7.  Seçin **Tamam** kapatmak için düğme **şablonları ve eklentileri** iletişim kutusu.  
  
     **XML yapısı** görev bölmesi açılır.  
  
8.  Kapat **XML yapısı** görev bölmesi.  
  
## <a name="add-a-custom-xml-part-to-the-document"></a>Belgenin özel XML bölümleri ekleme  
 İçerik denetimleri, XML dosyasındaki öğelerine bağlamadan önce yeni bir özel XML parçasına XML dosyasının içeriğini eklemeniz gerekir.  
  
### <a name="to-add-a-custom-xml-part-to-the-document"></a>Belgenin özel XML bölümleri ekleme  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ThisDocument.vb** veya **ThisDocument.vb**ve ardından **Kodu Görüntüle**.  
  
2.  Aşağıdaki bildirimi ekleyin `ThisDocument` sınıfı. Bu kod, özel bir XML parçasına belgeye eklemek için kullanacağınız birçok nesne bildirir.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Aşağıdaki yöntemi ekleyin `ThisDocument` sınıfı. Bu yöntem, bir kaynak olarak derlemesinde katıştırılır ve içeriği bir XML dizesi olarak döndürür. XML veri dosyasının içeriği alır.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Aşağıdaki yöntemi ekleyin `ThisDocument` sınıfı. `AddCustomXmlPart` Yöntemi yönteme geçirilen bir XML dizesini içeren yeni bir özel XML bölümü oluşturur.  
  
     Emin olmak için özel XML bölümü yalnızca bir kez oluşturulur, özel XML yöntemi oluşturur bölümü eşleşen bir GUID sahip özel bir XML parçasına, belgede zaten yok. İsteğe bağlı olarak bu yöntem çağrıldığında, ilk kez değerini kaydeder <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> özelliğini `employeeXMLPartID` dize. Değerini `employeeXMLPartID` dize kullanarak bildirilen çünkü belgede kalıcı <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliği.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>İçerik denetimlerini özel XML parçasına öğeleri bağlama  
 Kullanarak her içerik denetimi bir öğedeki özel XML parçasına bağlama **XMLMapping** içerik her denetimin özellik.  
  
### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>İçerik denetimlerini özel XML parçasına öğeleri bağlamak için  
  
1.  Aşağıdaki yöntemi ekleyin `ThisDocument` sınıfı. Bu yöntem her içerik denetimi özel XML bölümü içindeki bir öğeye bağlar ve tarih görüntüleme biçimini ayarlar <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="run-your-code-when-the-document-is-opened"></a>Belge açıldığında, kodunuzu çalıştırmak  
 Özel XML parçaları oluşturmak ve belge açıldığında özel denetimleri verilere bağlayın.  
  
### <a name="to-run-your-code-when-the-document-is-opened"></a>Belge açıldığında, kodunuzu çalıştırmak için  
  
1.  Aşağıdaki kodu ekleyin `ThisDocument_Startup` yöntemi `ThisDocument` sınıfı. Bu kodu XML dizesi alır **employees.xml** dosya, yeni bir özel XML parçasına XML dizesi ekler ve içerik denetimlerini özel XML parçasına öğeleri bağlar.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="test-the-project"></a>Test projesi  
 Belgeyi açtığında, içerik denetimlerini özel XML bölümünde öğeleri verileri görüntüler. Tıklayabilirsiniz <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> geçerli üç değerden birini seçmek için `title` tanımlanan öğesini **employees.xsd** dosya. İçerik denetimleri verileri düzenlerseniz, yeni değerleri özel bir XML parçasına belgedeki kaydedilir.  
  
### <a name="to-test-the-content-controls"></a>İçerik denetimlerini test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Aşağıdaki tabloda tabloda bir belge benzediğini doğrulayın. Dize ikinci sütundaki her bir öğeden belgesindeki özel XML bölümünde elde edilir.  
  
    |||  
    |-|-|  
    |**Çalışan adı**|**Karina Leal**|  
    |**İşe Alınma Tarihi**|**1 Nisan 1999**|  
    |**Başlık**|**Yöneticisi**|  
  
3.  Sağındaki hücreyi seçin **çalışan adı** hücre ve farklı bir ad yazın.  
  
4.  Sağındaki hücreyi seçin **işe giriş tarihi** hücre ve farklı bir tarih tarih seçiciden seçin.  
  
5.  Sağındaki hücreyi seçin **başlık** hücre ve aşağı açılan listeden yeni bir öğe seçin.  
  
6.  Kaydedin ve kapatın.  
  
7.  Dosya Gezgini'nde Aç *\bin\Debug* projenizin konumunu klasöründedir.  
  
8.  Kısayol menüsünü açın **ÇalışanDenetimleri.docx'i** seçip **Yeniden Adlandır**.  
  
9. Dosya adı **ÇalışanDenetimleri.docx.zip**.  
  
     **ÇalışanDenetimleri.docx'i** belge Open XML biçiminde kaydedilir. Bu belge ile yeniden adlandırarak *.zip* dosya adı uzantısı belgesinin içeriğini inceleyebilirsiniz. Open XML hakkında daha fazla bilgi için teknik makaleye bakın [(2007) Office Open XML giriş dosyası biçimleri](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).  
  
10. Açık **ÇalışanDenetimleri.docx.zip** dosya.  
  
11. Açık **customXml** klasör.  
  
12. Kısayol menüsünü açın **item2.xml** seçip **açık**.  
  
     Bu dosya, belgeye eklediğiniz özel XML bölümü içerir.  
  
13. Doğrulayın `name`, `hireDate`, ve `title` öğeleri içeren bir belgede içerik denetimlerine girdiğiniz yeni değerleri.  
  
14. Kapat **item2.xml** dosya.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 İçerik denetimleri aşağıdaki konulardan kullanma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Bir şablon oluşturmak için kullanılabilir tüm içerik denetimlerini kullanın. Daha fazla bilgi için [izlenecek yol: içerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Belge kapalıyken özel XML bölümleri verileri değiştirin. Kullanıcı, belgeyi bir sonraki açışında XML öğelerine bağlanan içerik denetimleri yeni veriler görüntüler.  
  
-   Bir belge bölümlerini koruma için içerik denetimleri kullanın. Daha fazla bilgi için [nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [İçerik denetimleri](../vsto/content-controls.md)   
 [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  