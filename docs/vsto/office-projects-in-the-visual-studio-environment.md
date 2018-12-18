---
title: Visual Studio ortamında Office projeleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8149e8029dbe39d37ab3979df9af38386af84d6b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867422"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Visual Studio ortamında Office projeleri
  Microsoft Office projeleri, Visual Studio'daki diğer proje türlerine (Windows Forms projeleri gibi) benzer bir geliştirme deneyimine sahiptir. Proje öğeleri oluşturduğunuzda veya bir Office projesi görünür **Çözüm Gezgini**. Belge düzeyinde projeler için, belge (yani, Word belgesi veya Excel çalışma kitabı) Visual Studio'da açılır ve belge bir görsel tasarımcı gibi davranır.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="project-items-in-solution-explorer"></a>Çözüm Gezgini'nde proje öğeleri  
 Bir belge düzeyi projede **Çözüm Gezgini** aşağıdaki varsayılan öğeleri görüntüler:  
  
- Projenin özelleştirdiği belge, çalışma kitabı ve sayfa düğümleri. Bu düğümler; belge, çalışma kitabı ve sayfalar ile ilişkili kod dosyaları için kapsayıcı işlevi görür.  
  
- Projenin özelleştirdiği belge, çalışma kitabı ve sayfalar ile ilişkili kod dosyaları. Word projelerinde, kod dosyaları Word belgesi veya şablonu ile ilişkilidir. Excel projelerinde, kod dosyaları Excel çalışma kitabı veya şablonuyla ve çalışma kitabı veya şablondaki her bir çalışma sayfası ve grafik sayfası ile ilişkilidir.  
  
- Doğrudan düzenlemeniz için tasarlanmamış gizli proje dosyaları. Daha fazla bilgi için [gizli proje dosyaları](#hiddenfiles).  
  
  Bir VSTO eklenti projesinde **Çözüm Gezgini** aşağıdaki varsayılan öğeleri görüntüler:  
  
- Uygulama düğümü. Bu düğüm gibi konak uygulama ile aynı ada sahip **Word**, **Excel**, veya **Outlook**. Bu uygulama düğümü ThisAddIn kod dosyasını içerir. Ayrıca sağlar **Namespace for Host Item** özelliği. Bu özellik hakkında daha fazla bilgi için bkz. [Office projelerinde Özellikler](../vsto/properties-in-office-projects.md).  
  
- ThisAddIn kod dosyası. Bu dosyada oluşturulan `ThisAddIn` VSTO eklenti için sınıf. Bu sınıf hakkında daha fazla bilgi için bkz: [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
- Doğrudan düzenlemeniz için tasarlanmamış gizli proje dosyaları. Daha fazla bilgi için [gizli proje dosyaları](#hiddenfiles).  
  
### <a name="temporary-certificates"></a>Geçici Sertifikalar  
 Office projeleri ayrıca adlı geçici bir sertifika içerir *proje adı*_TemporaryKey.pfx. Bu sertifika, geliştirme sırasında projenin uygulama ve dağıtım bildirimlerini imzalamak için kullanılır. Daha fazla bilgi için [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md) ve [güvenli Office çözümleri](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> Gizli proje dosyaları  
 Bazı proje dosyaları varsayılan olarak gizlidir. Bu dosyalar Visual Studio tarafından oluşturulur ve proje türüne göre farklılık gösterir. Gizli dosyaları görüntülemek için tıklatın **tüm dosyaları göster** içinde **Çözüm Gezgini**.  
  
 Gizli proje dosyalarında değişiklik yapmayın. Bu dosyaların doğrudan değiştirilmesi desteklenmez ve projenizin bozulmasına neden olabilir. Gizli proje dosyaları, belgede belirli değişiklikler olduğu durumlarda yeniden oluşturulur. Gizli bir proje dosyasında el ile değişiklikler yaparsanız, dosya yeniden oluşturulduğunda bu değişiklikler kaybolur.  
  
## <a name="document-designer-in-document-level-projects"></a>Belge düzeyinde projelerde belge Tasarımcısı  
 Excel ve Word için belge düzeyinde projeler, Visual Studio'da projenizle ilişkili belgeyi barındıran bir tasarımcı sunar. Tasarımcı, Visual Studio ortamının dışına çıkmadan belgede değişiklik yapmanızı sağlar.  
  
 Bir belgeyi tasarımcıda açmak için kod dosyasına çift tıklayın **Çözüm Gezgini** belgeyle ilişkili. Örneğin, çalışma sayfasını açmak için **Sayfa1** Excel projesinde tasarımcıda çift **Sayfa1** kod dosyası.  
  
 Belgeyi tasarımcıda değiştirirken, Office uygulamasının yerel işlevselliğinden yararlanabilirsiniz. Örneğin, belgeye veya bir çalışma sayfasına metin girebilir veya tablo ya da grafik ekleme gibi görevleri gerçekleştirmek için Şerit'i kullanabilirsiniz. Varsayılan olarak, klavye kısayolu eşlemeleri Visual Studio eşlemelerine varsayılan olur. Office kullanılacak klavye kısayolu eşlemeleri bunun yerine, ayarları değiştirmek **Microsoft Office Klavyesi ayarları** düğümünde **seçenekleri** iletişim kutusunda **Araçları** menüsü .  
  
### <a name="controls-on-documents"></a>Belgeler Üzerindeki Denetimler  
 Sürükleyebilirsiniz *konak denetimlerini* ve Visual Studio'dan Windows Forms denetimleri **araç kutusu** belge tasarım yüzeyine. Konak denetimleri Office nesnelerinin özelleşmiş sürümleri olup (Word içerik denetimleri ve Excel aralıkları gibi), Visual Studio ile oluşturulmuş Office projelerinde kullanılabilirler. Konak denetimlerinin karşılık gelen Office nesnelerinde bulunmayan, veri bağlama ve ek olaylar gibi ilave özellikleri vardır.  
  
 Daha fazla bilgi için [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md) ve [Windows forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Excel çalışma kitabı ve tasarımcıda çalışma  
 Bir çalışma sayfasını tasarımcıda açtığınızda, çalışma sayfasını doğrudan Excel'de açtığınızda yaptığınız gibi değiştirebilirsiniz. Bir çalışma sayfası hücresine çift tıklarsanız hücre düzenleme moduna geçer. Bir konak denetimi içeren bir hücreye çift tıklarsanız Kod Düzenleyicisi açılır ve Visual Studio denetim için varsayılan olay işleyicisini oluşturur. Diğer çalışma sayfalarına gitmek için tasarımcının en altında çalışma sayfası sekmelerine tıklayabilirsiniz.  
  
 Çalışma kitabını tasarımcıda açtığınızda tasarım yüzeyi bulunmaz. Çalışma kitabına ilişkin tasarım görünümü tasarımcıyı dolduran büyük bir bileşen alanıdır.  
  
 Çalışma kitabının ve çalışma kitabındaki tüm sayfaların ilişkili birer kod dosyası vardır. Her kod dosyası oluşturulan bir içerir *konak öğesi* çalışma kitabını veya sayfasını temsil eden sınıf. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](../vsto/automating-excel-by-using-extended-objects.md).  
  
### <a name="word-documents-in-the-designer"></a>Tasarımcıda Word belgeleri  
 Belgeyi tasarımcıda açtığınızda, doğrudan Word'de açtığınızda yaptığınız gibi değiştirebilirsiniz. Belgedeki bir sözcüğe çift tıklarsanız, sözcük seçili hale gelir. Ancak sözcük bir konak denetiminin içindeyse, kod düzenleyicisi açılır ve Visual Studio denetim için varsayılan olay işleyicisini oluşturur.  
  
 Belgenin ilişkili bir kod dosyası vardır. Oluşturulan bir kod dosyası içeren *konak öğesi* belgeyi temsil eden sınıf. Daha fazla bilgi için [belge konak öğesi](../vsto/document-host-item.md).  
  
### <a name="design-mode-vs-runtime-mode"></a>Tasarım modu ve çalışma zamanı modu karşılaştırması  
 Bir belge Visual Studio ortamında açık durumdayken, her zaman içinde *tasarım modu*. Bazı görevler (örneğin, belge yüzeyine bir konak denetimi sürüklemek gibi) sadece tasarım modunda gerçekleştirebilir.  
  
 Belgeyi görüntülemek için *çalışma zamanı modu*, uygulamayı ve belgeyi Visual Studio'nun dışında açmalısınız. Ayrıca, projeyi derleyip çalıştırabilirsiniz ve böylece, belge ve uygulama otomatik olarak Visual Studio'nun dışında açılır.  
  
## <a name="code-editor"></a>Kod Düzenleyicisi  
 Kod Düzenleyicisi çözümünüzdeki görünür kod dosyalarını görüntüleyip değiştirebilmenizi sağlar. Bu dosyalar çözümünüzün davranışını tanımlayan kodu içerir.  
  
 Kod Düzenleyicisi hakkında daha fazla bilgi için bkz. [kod ve metin düzenleyicide kod yazma](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Office projelerinde kod yazma hakkında daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="properties-window"></a>Özellik penceresi  
 **Özellikleri** penceresi seçili proje öğeleri için özellikleri görüntüler **Çözüm Gezgini**ve belge veya denetimler gibi Tasarımcısı'nda seçtiğiniz kullanıcı Arabirimi öğeleri için bir Belge düzeyi projesi. Bazı özellikler uygulamaya ve belgeye özgü olurken, bazı özellikler tüm projeler genelinde aynıdır.  
  
## <a name="data-sources-window"></a>Veri Kaynakları penceresi  
 Kullanabileceğiniz **veri kaynakları** penceresi veri kaynağını belgenizin üzerine sürükleyebilir ve oluşturan bir denetimi için belge düzeyinde Office projelerinde veri kaynağına bağlı. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office projelerinde Özellikler](../vsto/properties-in-office-projects.md)  
  
  