---
title: Belge düzeyi özelleştirmelerini programlama
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d9c7fa658c24caa65b3c955002ffeeaff6573c55
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812237"
---
# <a name="program-document-level-customizations"></a>Belge düzeyi özelleştirmelerini programlama
  Microsoft Office Word veya Microsoft Office Excel belge düzeyi özelleştirmesi kullanılarak genişlettiğinizde aşağıdaki görevleri gerçekleştirebilirsiniz:  
  
- Uygulama, nesne modelini kullanarak otomatik hale getirin.  
  
- Belge yüzeyine denetimler ekleyin.  
  
- Visual Basic belgedeki Applications (VBA) kodu için özelleştirme bütünleştirilmiş koddan çağırın.  
  
- Özelleştirme bütünleştirilmiş koddan VBA kodu çağırın.  
  
- Microsoft Office'in yüklü olmayan bir sunucuda olsa bazı yönlerini belge yönetin.  
  
- Uygulamanın kullanıcı arabirimini (UI) özelleştirin.  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
  Belge düzeyinde projelerde kod yazmayı bazı yönleri, Visual Studio'da projelerinin diğer türleri farklıdır. Bu farklılıkların birçoğu şekilde Office nesne modelleri, yönetilen kod için sunulan neden olur. Daha fazla bilgi için [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).  
  
  Visual Studio'da Office geliştirme araçlarını kullanarak oluşturabileceğiniz belge düzeyi özelleştirmeleri ve diğer tür çözümler hakkında genel bilgi için bkz. [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="use-the-generated-classes-in-document-level-projects"></a>Belge düzeyinde projelerde üretilen sınıfları kullanın  
 Bir belge düzeyi projesi oluşturduğunuzda, Visual Studio otomatik olarak kodunuzu yazmaya başlamak için kullanabileceğiniz bir projede bir sınıf oluşturur. Visual Studio, Word ve Excel için farklı sınıflar oluşturur:  
  
- Word için belge düzeyinde projelerde sınıfı olarak adlandırılan `ThisDocument` varsayılan olarak.  
  
- Excel için belge düzeyi projelerine sahip birden çok oluşturulan sınıflar: çalışma kitabının kendisi için ve her çalışma sayfası için bir. Varsayılan olarak, bu sınıfları aşağıdaki adlara sahiptir:  
  
  -   `ThisWorkbook`  
  
  -   `Sheet1`  
  
  -   `Sheet2`  
  
  -   `Sheet3`  
  
  Oluşturulan sınıfın belge açıldığında veya çağrılan olayı işleyicilerini içerir. Belge açıldığında kodu çalıştırmak için kod ekleyin. `Startup` olay işleyicisi. Belge kapatılmadan hemen önce kodu çalıştırmak için kod ekleyin. `Shutdown` olay işleyicisi. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="understand-the-design-of-the-generated-classes"></a>Oluşturulan sınıflar tasarımını anlayın  
 ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], konak öğesi türleri içinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] olduğundan arabirimleri, kendi uygulamasından oluşturulan sınıflar türetilemez. Bunun yerine, üretilen sınıfları birçok üyelerini aşağıdaki temel sınıflarından:  
  
- `ThisDocument`: türetilen <xref:Microsoft.Office.Tools.Word.DocumentBase>.  
  
- `ThisWorkbook`: türetilen <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.  
  
- `Sheet` *n*: türetilen <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.  
  
  Temel sınıfların üyeleri tüm çağrıları karşılık gelen konak öğesi arabirimlerde iç uygulamaları yeniden yönlendirme [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Örneğin, eğer <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> yöntemi `ThisDocument` sınıfı <xref:Microsoft.Office.Tools.Word.DocumentBase> sınıfı iç uygulanması bu çağrıyı yeniden yönlendiren <xref:Microsoft.Office.Tools.Word.Document> arabiriminde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="access-the-object-model-of-the-host-application"></a>Konak uygulamanın nesne modeline erişme  
 Konak uygulamanın nesne modeli erişmek için projenizde oluşturulan sınıfın üyeleri kullanın. Bu sınıfların her birini Excel veya Word nesne modelinde bir nesneye karşılık gelen ve özelliklerini, yöntemlerini ve olaylarını çoğunu içerir. Örneğin, `ThisDocument` Word aynı üyeleri çoğunu sağlar sınıfını bir belge düzeyi projede <xref:Microsoft.Office.Interop.Word.Document> Word nesne modelinde.  
  
 Aşağıdaki kod örneği, Word için belge düzeyi özelleştirmeyi parçası olan bir belgeyi kaydetmek için Word nesne modeli kullanmayı gösterir. Bu örnekte çalışmak üzere tasarlanmıştır `ThisDocument` sınıfı.  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 Dışından aynı şeyi yapmak için `ThisDocument` sınıfı, kullanın `Globals` nesne erişimi `ThisDocument` sınıfı. Dahil etmek istiyorsanız, bu kod Eylemler bölmesi kod dosyasına ekleyebileceğiniz bir **Kaydet** UI Eylemler bölmesinde düğmesi.  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 Çünkü `ThisDocument` sınıf üyelerini çoğunu alır <xref:Microsoft.Office.Tools.Word.Document> konak öğesi `Save` bu kodu, çağrılan yöntem olan gerçekten <xref:Microsoft.Office.Tools.Word.Document.Save%2A> yöntemi <xref:Microsoft.Office.Tools.Word.Document> konak öğesi. Bu yöntem karşılık gelen <xref:Microsoft.Office.Interop.Word._Document.Save%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Document> Word nesne modelinde.  
  
 Word ve Excel nesne modelleri kullanma hakkında daha fazla bilgi için bkz. [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md) ve [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).  
  
 Hakkında daha fazla bilgi için `Globals` nesne, bkz: [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="add-controls-to-documents"></a>Belgelere denetimler ekleme  
 Belgenin kullanıcı arabirimini özelleştirmek için Windows Forms denetimleri ekleyebilirsiniz veya *konak denetimlerini* belge yüzeyine bırakın. Farklı denetim kümelerini birleştirerek ve verilere denetimler bağlayabilirsiniz kod yazarken, kullanıcıdan bilgi toplamak ve kullanıcı eylemlerine yanıt.  
  
 Konak denetimleri bazı nesneler Word ve Excel nesne modelinde genişleten sınıflardır. Örneğin, <xref:Microsoft.Office.Tools.Excel.ListObject> konak kontrolü tüm işlevlerini sağlar <xref:Microsoft.Office.Interop.Excel.ListObject> Excel'de. Ancak, <xref:Microsoft.Office.Tools.Excel.ListObject> konak kontrolü ek olaylar ve veri bağlama özellikleri de vardır.  
  
 Daha fazla bilgi için [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md) ve [Windows forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="combine-vba-and-document-level-customizations"></a>VBA ve belge düzeyi özelleştirmelerini birleştirme  
 Belge düzeyi özelleştirmesi parçası olan bir belgede VBA kodu kullanabilirsiniz. Özelleştirme bütünleştirilmiş koddan belgedeki VBA kodu çağırabilir ve özelleştirme derlemede kod çağırmak için belgedeki VBA kodu etkinleştirmek için projenizi de yapılandırabilirsiniz.  
  
 Daha fazla bilgi için [birleştirmek VBA ve belge düzeyi özelleştirmeleri](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="manage-documents-on-a-server"></a>Bir sunucu üzerinde belgeleri yönetme  
 Microsoft Office Word'ün yüklü olmadığı bir sunucuda belge düzeyi özelleştirmeleri birkaç farklı özelliklerini yönetebilir veya Microsoft Office Excel yüklü. Örneğin, erişim ve belgenin veri önbelleğindeki verileri değiştirme. Ayrıca, belge ile ilişkilendirilen özelleştirme bütünleştirilmiş kodu yönetebilirsiniz. Örneğin, program aracılığıyla derleme belge belge artık kodunuzun çalıştığı ya da belgeye bir derleme program aracılığıyla ekleyebilirsiniz kaldırabilirsiniz.  
  
 Daha fazla bilgi için [ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office uygulamasının kullanıcı arabirimini özelleştirme  
 Belge düzeyi özelleştirmesi kullanılarak Excel ve Word kullanıcı Arabirimi aşağıdaki şekillerde özelleştirebilirsiniz:  
  
- Konak veya Windows Forms denetimleri belge yüzeyine ekleyin.  
  
   Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Word'ü](../vsto/automating-word-by-using-extended-objects.md), [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](../vsto/automating-excel-by-using-extended-objects.md), ve [Windows Forms denetimleri Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
- Belgeye eylemler bölmesi ekleme.  
  
   Daha fazla bilgi için [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).  
  
- Şeride özel sekmeler ekleme  
  
   Daha fazla bilgi için [Şerite Genel Bakış](../vsto/ribbon-overview.md).  
  
- Şeritteki yerleşik bir sekmeyi özel gruplar ekleyin.  
  
   Daha fazla bilgi için [nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md).  
  
  Microsoft Office UI uygulamaları özelleştirme hakkında daha fazla bilgi için bkz. [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Genişletilmiş nesneleri belge düzeyi özelleştirmelerdeki yerel Office nesnelerden alma  
 Office olayları için çok sayıda olay işleyicileri, çalışma kitabı, çalışma veya olayı oluşturan bir belgeyi temsil eden yerel bir Office nesnesi alır. Bazı durumlarda, yalnızca çalışma kitabı veya belge düzeyi özelleştirmenizdeki belge olayı, bazı kodlar çalıştırmak isteyebilirsiniz. Örneğin, Excel için belge düzeyi özelleştirmesinde kullanıcı özelleştirilmiş çalışma kitabının ve çalışma kağıtlarından biri etkinleştirirken, ancak kullanıcı çalışma kitabındaki aynı zamanda açık olmasını gerçekleşen bazı diğer etkinleştirdiğinde değil, bazı kodlar çalıştırmak isteyebilirsiniz.  
  
 Yerel bir Office nesne varsa, bu nesne içine genişletilmiş olup olmadığını sınayabilirsiniz bir *konak öğesi* veya *konak kontrolü* belge düzeyi özelleştirmesinde. Konak denetimlerinin ve konak öğelerinin türleridir tarafından sağlanan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] işlevsellik ekleyen Word veya Excel nesne modellerinde yerel olarak mevcut nesneleri (adlı *yerel Office nesneleri*). Konak denetimlerinin ve konak öğelerinin toplu olarak da adlandırılır *genişletilmiş nesneleri*. Konak denetimlerinin ve konak öğeleri hakkında daha fazla bilgi için bkz: [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>GetVstoObject ve HasVstoObject yöntemleri anlama  
 Yerel bir Office nesne test etmek için `HasVstoObject` ve `GetVstoObject` projenizdeki yöntemleri:  
  
- Kullanım `HasVstoObject` yerel Office nesne özelleştirme sırasında genişletilmiş bir nesneye sahip olup olmadığını belirlemek istiyorsanız yöntemi. Bu yöntem döndürür **true** yerel Office nesne genişletilmiş bir nesne varsa ve **false** Aksi takdirde.  
  
- Kullanım `GetVstoObject` uzatılmış nesne için yerel bir Office nesnesi almak istiyorsanız yöntemi. Bu yöntem döndürür bir <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, veya <xref:Microsoft.Office.Tools.Word.Document> belirtilen yerel Office nesne varsa, nesne. Aksi takdirde, `GetVstoObject` döndürür **null**. Örneğin, `GetVstoObject` yöntemi döndürür bir <xref:Microsoft.Office.Tools.Word.Document> , belirtilen <xref:Microsoft.Office.Interop.Word.Document> Word belgesi projenizdeki belge için temel bir nesnedir.  
  
  Belge düzeyinde projelerde kullanamazsınız `GetVstoObject` yeni bir yöntem <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, veya <xref:Microsoft.Office.Tools.Word.Document> çalışma zamanında konak öğesi. Yalnızca tasarım zamanında projenizde oluşturulan mevcut konak öğelere erişmek için bu yöntemi kullanabilirsiniz. Yeni konak öğeleri çalışma zamanında oluşturmak istiyorsanız, bir VSTO eklenti projesi geliştirmeniz gerekir. Daha fazla bilgi için [konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) ve [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>GetVstoObject ve HasVstoObject yöntemleri kullanın  
 Çağrılacak `HasVstoObject` ve `GetVstoObject` yöntemi, kullanım `Globals.Factory.GetVstoObject` veya `Globals.Factory.HasVstoObject` yöntemi ve yerel Word veya Excel nesnesi geçirin (gibi bir <xref:Microsoft.Office.Interop.Word.Document> veya <xref:Microsoft.Office.Interop.Excel.Worksheet>) test etmek istediğiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)   
 [ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)  
  
  