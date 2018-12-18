---
title: VSTO eklentilerini programlama
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 522a3cbac565e217f0b6525fb6288f5b79908a78
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676926"
---
# <a name="program-vsto-add-ins"></a>VSTO eklentilerini programlama
  Bir VSTO eklentisi oluşturma tarafından bir Microsoft Office uygulamasının genişlettiğinizde, karşı doğrudan kod yazma `ThisAddIn` projenizdeki sınıfı. Bu sınıf, Microsoft Office konak uygulamanın nesne modeline erişme, uygulamanın kullanıcı arabirimini (UI) özelleştirmek ve diğer Office çözümleri için VSTO eklenti içinde nesnelerini kullanıma sunma gibi görevleri gerçekleştirmek için kullanabilirsiniz.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Bazı yönlerini VSTO eklentisi projelerinde kod yazma, Visual Studio'da projelerinin diğer türleri farklıdır. Bu farklılıkların birçoğu şekilde Office nesne modelleri, yönetilen kod için sunulan neden olur. Daha fazla bilgi için [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).  
  
 Visual Studio'da Office geliştirme araçlarını kullanarak oluşturabileceğiniz VSTO eklentileri ve diğer tür çözümler hakkında genel bilgi için bkz. [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="use-the-thisaddin-class"></a>ThisAddIn sınıfı kullanın  
 VSTO eklentisi kod yazmaya başlayabilirsiniz `ThisAddIn` sınıfı. Visual Studio otomatik olarak oluşturduğu bu sınıfta *ThisAddIn.vb* (içinde [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) veya *ThisAddIn.cs* (C# ') kod VSTO eklenti projesinde dosyası. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Microsoft Office uygulamasının VSTO Eklenti yüklendiğinde otomatik olarak bu sınıfın örneğini sizin için oluşturur.  
  
 İki varsayılan olay işleyicileri vardır `ThisAddIn` sınıfı. VSTO Eklenti yüklendiğinde kodu çalıştırmak için kod ekleyin. `ThisAddIn_Startup` olay işleyicisi. VSTO eklentisi kaldırılmadan hemen önce kodu çalıştırmak için kod ekleyin. `ThisAddIn_Shutdown` olay işleyicisi. Bu olay işleyicileri hakkında daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  Outlook'ta, varsayılan olarak `ThisAddIn_Shutdown` olay işleyicisi için VSTO eklentisi kaldırıldığında her zaman çağrılmaz. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="access-the-object-model-of-the-host-application"></a>Konak uygulamanın nesne modeline erişme  
 Konak uygulamanın nesne modeli erişmek için `Application` alanını `ThisAddIn` sınıfı. Bu alan, ana uygulamanın geçerli örneğini temsil eden bir nesne döndürür. Aşağıdaki tablo, dönüş değeri türünü listeler `Application` her VSTO eklenti projesinde alan.  
  
|Ana bilgisayar uygulaması|Dönüş değeri türü|  
|----------------------|-----------------------|  
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Microsoft Office projesini|Microsoft.Office.Interop.MSProject.Application|  
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 Aşağıdaki kod örneği kullanma işlemini gösterir `Application` alan Microsoft Office Excel için VSTO eklentisi içinde yeni bir çalışma kitabı oluşturun. Bu örnekte çalışmak üzere tasarlanmıştır `ThisAddIn` sınıfı.  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Dışından aynı şeyi yapmak için `ThisAddIn` sınıfı, kullanın `Globals` nesne erişimi `ThisAddIn` sınıfı. Hakkında daha fazla bilgi için `Globals` nesne, bkz: [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Belirli Microsoft Office uygulamasının nesne modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)  
  
-   [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)  
  
-   [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath çözümleri](../vsto/infopath-solutions.md)  
  
-   [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)  
  
-   [Proje çözümleri](../vsto/project-solutions.md)  
  
-   [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> Office uygulaması başlatıldığında, bir belgeye erişme  
 Tüm [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamaları ve hiçbiri başlattığınızda bir belge otomatik olarak açmak [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] uygulamaları, başlattığınızda bir belgeyi açın. Bu nedenle, kod ekleme `ThisAdd-In_Startup` kodu açık bir belge gerektiriyorsa, olay işleyicisi. Bunun yerine, bu kod, bir kullanıcı oluşturur ya da bir belge açılır Office uygulaması oluşturan bir olay ekleyin. Böylece, kodunuzu bir işlem gerçekleştirmeden önce bir belge açık olduğunu garanti edebilir.  
  
 Kullanıcı bir belgeyi oluşturur veya var olan bir belgeyi açar aşağıdaki kod örneği bir Word belgesini ile çalışır.  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>Diğer görevler için kullanılacak ThisAddIn üyeleri  
 Aşağıdaki tablo diğer ortak görevleri açıklar ve hangi üyelerinin gösterir `ThisAddIn` sınıfı görevleri gerçekleştirmek için kullanabilirsiniz.  
  
|Görev|Üye kullanmak için|  
|----------|-------------------|  
|VSTO eklentisi için VSTO eklentisi yüklendiğinde başlatmak için kodu çalıştırın.|Kodu `ThisAddIn_Startup` yöntemi. İçin varsayılan olay işleyicisini budur <xref:Microsoft.Office.Tools.AddInBase.Startup> olay. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).|  
|VSTO eklentisi kaldırılmadan önce VSTO eklentisi tarafından kullanılan kaynakları temizlemek için kodu çalıştırın.|Kodu `ThisAddIn_Shutdown` yöntemi. İçin varsayılan olay işleyicisini budur <xref:Microsoft.Office.Tools.AddInBase.Shutdown> olay. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md). **Not:** Outlook'ta, varsayılan olarak `ThisAddIn_Startup` olay işleyicisi için VSTO eklentisi kaldırıldığında her zaman çağrılmaz. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).|  
|Bir özel görev bölmesini görüntüler.|Kullanım `CustomTaskPanes` alan. Daha fazla bilgi için [özel görev bölmeleri](../vsto/custom-task-panes.md).|  
|Diğer Microsoft Office çözümleri için VSTO eklenti nesneleri kullanıma sunma.|Geçersiz kılma <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> yöntemi. Daha fazla bilgi için [çağrı kod VSTO eklentileri diğer Office Çözümlerinden](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|  
|Bir özellik genişletilebilirlik arabirimi uygulama tarafından Microsoft Office sistemindeki özelleştirin.|Geçersiz kılma <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> arabirimi uygulayan bir sınıf örneği döndürmek için yöntemi. Daha fazla bilgi için [genişletilebilirlik arabirimlerini kullanarak kullanıcı Arabirimi özelleştirme özellikleri](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Not:** Şerit kullanıcı arabirimini özelleştirmek için ayrıca kılabilirsiniz <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> yöntemi.|  
  
### <a name="understand-the-design-of-the-thisaddin-class"></a>ThisAddIn sınıfı tasarımı anlama  
 ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> bir arabirimdir. `ThisAddIn` Sınıf türetilir <xref:Microsoft.Office.Tools.AddInBase> sınıfı. Bu temel sınıf üyelerine tüm çağrıları için iç uygulaması yönlendirir <xref:Microsoft.Office.Tools.AddIn> arabiriminde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 Outlook için VSTO eklentisi projeleri içinde `ThisAddIn` sınıf türetilir `Microsoft.Office.Tools.Outlook.OutlookAddIn` sınıfı .NET Framework 3. 5'i hedefleyen projelerde ve gelen <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Temel sınıfların form bölgesini desteklemek için bazı ek işlevsellik sağlar. Form bölgeleri hakkında daha fazla bilgi için bkz. [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office uygulamasının kullanıcı arabirimini özelleştirme  
 Bir VSTO eklentisi kullanarak, Microsoft Office UI uygulamalarının programlı bir şekilde özelleştirebilirsiniz. Örneğin, Şerit özelleştirme, bir özel görev bölmesini görüntülemek veya özel form bölgesinin Outlook'ta oluşturun. Daha fazla bilgi için [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
 Visual Studio, tasarımcılar ve özel görev bölmeleri, Şerit özelleştirmeleri ve Outlook form bölgeleri oluşturma için kullanabileceğiniz sınıflar sağlar. Bu tasarımcılar ve sınıflar bu özelliklerini özelleştirme işlemi basitleştirmeye yardım eder. Daha fazla bilgi için [özel görev bölmeleri](../vsto/custom-task-panes.md), [Şerit Tasarımcısı](../vsto/ribbon-designer.md), ve [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
 Sınıflar ve tasarımcılar tarafından desteklenmeyen bir yolla bu özelliklerden birini özelleştirmek istiyorsanız, bu özelliklerin uygulayarak özelleştirebilirsiniz bir *genişletilebilirlik arabirimi* VSTO eklenti içinde. Daha fazla bilgi için [genişletilebilirlik arabirimlerini kullanarak kullanıcı Arabirimi özelleştirme özellikleri](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
 Ayrıca, belgeler ve çalışma kitapları davranışını genişleten ana bilgisayar öğeleri oluşturma tarafından kullanıcı Arabirimi, Word belgelerini ve Excel çalışma kitaplarını değiştirebilirsiniz. Bu belgeler ve çalışma sayfalarına yönetilen denetimleri eklemenize olanak sağlar. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>VSTO eklentilerinde diğer çözümlerden kod arama  
 Diğer Office çözümleri gibi diğer çözümlerle için VSTO eklenti içinde nesneler üzerinden kullanıma sunabilirsiniz. VSTO eklenti diğer çözümleri kullanmayı etkinleştirmek istediğiniz bir hizmet sağlar, bu yöntem kullanışlıdır. Bir web hizmetinden Finansal veriler üzerinde hesaplamalar yapan Microsoft Office Excel için VSTO eklentisi varsa, örneğin, diğer çözümleri bu hesaplamalar çalışma zamanında Excel VSTO eklentisi içinde çağırarak gerçekleştirebilirsiniz.  
  
 Daha fazla bilgi için [çağrı kod VSTO eklentileri diğer Office Çözümlerinden](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [VSTO eklentilerinde diğer Office Çözümlerinden kod arama](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [İzlenecek yol: çağrı VBA'dan kod bir VSTO eklenti](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Genişletilebilirlik arabirimlerini kullanarak kullanıcı Arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)  
  
  