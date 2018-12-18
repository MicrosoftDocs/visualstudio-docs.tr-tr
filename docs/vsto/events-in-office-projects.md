---
title: Office Projelerindeki Olaylar
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 85cbee61cde596831d06aa83af326cc0a0534f0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949688"
---
# <a name="events-in-office-projects"></a>Office Projelerindeki Olaylar
  Her Office proje şablonu, çeşitli olay işleyicileri otomatik olarak oluşturur. Belge düzeyi özelleştirmeleri için olay işleyicileri, VSTO eklentileri için olay işleyicileri biraz farklıdır.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="document-level-projects"></a>Belge düzeyi projeleri  
 Visual Studio, yeni veya varolan belgeleri ve belge düzeyi özelleştirmeleri çalışma sayfalarında arkasına oluşturulan kod sağlar. Bu kod, iki farklı olay oluşturur: **başlangıç** ve **kapatma**.  
  
### <a name="startup-event"></a>Startup olayı  
 **Başlangıç** olayı her ana bilgisayar öğesi (belge, çalışma kitabı veya çalışma sayfası) oluşturulur belge çalışıyorken ve derlemedeki tüm başlatma kodları çalıştıktan sonra. Kodunuzun çalıştığı sınıfının oluşturucusu, çalıştırmak için son şeydir. Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
 Bir belge düzeyi projesi oluşturduğunuzda, Visual Studio için olay işleyicileri oluşturur **başlangıç** oluşturulan kodda olay:  
  
-   Microsoft Office Word projeleri için olay işleyicisi adlı `ThisDocument_Startup`.  
  
-   Microsoft Office Excel projelerinde olay işleyicileri aşağıdaki adlara sahiptir:  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### <a name="shutdown-event"></a>Shutdown olayı  
 **Kapatma** olayı her ana bilgisayar öğesi (belge veya çalışma sayfası) için oluşturulur, kodunuzu yüklendiği uygulama etki alanı olduğunda kaldırılmak üzere. Sınıfı, bunu çağırılacak çağrılması son şeydir.  
  
 Bir belge düzeyi projesi oluşturduğunuzda, Visual Studio için olay işleyicileri oluşturur **kapatma** oluşturulan kodda olay:  
  
-   Microsoft Office Word projeleri için olay işleyicisi adlı `ThisDocument_Shutdown`.  
  
-   Microsoft Office Excel projelerinde olay işleyicileri aşağıdaki adlara sahiptir:  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  Program aracılığıyla denetimleri sırasında kaldırmayın **kapatma** belgenin olay işleyicisi. UI öğeleri artık kullanılabilir **kapatma** olayı oluşur. Denetimleri uygulama kapatılmadan önce kaldırmak isterseniz, kodunuzu başka bir olay işleyicisine aşağıdaki gibi ekleyin **BeforeClose** veya **BeforeSave**.  
  
### <a name="event-handler-method-declarations"></a>Olay işleyicisi yöntem bildirimleri  
 Her olay işleyicisi yöntem bildiriminde geçirilen aynı bağımsız değişkenlere sahiptir: *gönderen* ve *e*. Excel'de *gönderen* bağımsız değişken başvuran sayfa gibi `Sheet1` veya `Sheet2`; Word *gönderen* bağımsız değişken belgeye başvuruyor. *e* bağımsız değişkeni, bu durumda kullanılmayan standart için bağımsız değişkenler için olaya başvurur.  
  
 Aşağıdaki kod örneği, Word için belge düzeyi projelerine varsayılan olay işleyicileri gösterilmektedir.  
  
 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]  
  
 Aşağıdaki kod örneği, Excel için belge düzeyi projelerine varsayılan olay işleyicileri gösterilmektedir.  
  
> [!NOTE]  
>  Aşağıdaki kod örneği, olay işleyicileri gösterilmektedir `Sheet1` sınıfı. Diğer ana bilgisayar öğesi sınıflardaki olay işleyicileri adlarını sınıf adına karşılık gelir. Örneğin, `Sheet2` sınıfı **başlangıç** olay işleyicisi adlı `Sheet2_Startup`. İçinde `ThisWorkbook` sınıfı **başlangıç** olay işleyicisi adlı `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]  
  
### <a name="order-of-events-in-document-level-excel-projects"></a>Belge düzeyi Excel projelerinde olayların sırası  
 **Başlangıç** Excel projelerinde olay işleyicileri şu sırayla çağrılır:  
  
1. `ThisWorkbook_Startup`.  
  
2. `Sheet1_Startup`.  
  
3. `Sheet2_Startup`.  
  
4. `Sheet3_Startup`.  
  
5. Sırayla diğer sayfaları.  
  
   **Kapatma** olay işleyicileri bir çalışma kitabı çözümde şu sırayla çağrılır:  
  
6. `ThisWorkbook_Shutdown`.  
  
7. `Sheet1_Shutdown`.  
  
8. `Sheet2_Shutdown`.  
  
9. `Sheet3_Shutdown`.  
  
10. Sırayla diğer sayfaları.  
  
    Sırası, proje derlendiğinde belirlenir. Kullanıcının çalışma zamanında sayfaları düzenlerse, sonraki açışınızda bir çalışma kitabı açılamıyor veya tetiklenen olayları sırasını değiştirmez.  
  
## <a name="vsto-add-in-projects"></a>VSTO eklentisi projeleri  
 Visual Studio, VSTO eklentileri üretilen kodda sağlar. Bu kod, iki farklı olay oluşturur: <xref:Microsoft.Office.Tools.AddInBase.Startup> ve <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### <a name="startup-event"></a>Startup olayı  
 <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentisi yüklenir ve derlemedeki tüm başlatma kodları çalıştıktan sonra olayı oluşturulur. Bu olay tarafından işlenen `ThisAddIn_Startup` üretilen kod dosyasında yöntemi.  
  
 Kod `ThisAddIn_Startup` olay işleyicisi, çalıştırmak için ilk kullanıcı kod VSTO eklenti kılmadıkça <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> yöntemi. Bu durumda, `ThisAddIn_Startup` olay işleyicisi, sonra çağrılır <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 Kod ekleme `ThisAdd-In_Startup` kodu açık bir belge gerektiriyorsa, olay işleyicisi. Bunun yerine, bu kod, bir kullanıcı oluşturur ya da bir belge açılır Office uygulaması oluşturan bir olay ekleyin. Daha fazla bilgi için [Office uygulaması başlatıldığında, bir belgeye erişme](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 VSTO eklentileri başlatma sırası hakkında daha fazla bilgi için bkz. [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="shutdown-event"></a>Shutdown olayı  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Olayı kodunuzun yüklü uygulama etki alanı kaldırılmak üzere olduğunda oluşturulur. Bu olay tarafından işlenen `ThisAddIn_Shutdown` üretilen kod dosyasında yöntemi. Bu olay işleyicisi için VSTO eklentisi kaldırıldığında çalıştırmak için son kullanıcı kodudur.  
  
#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Kapatma olayı Outlook VSTO eklentileri  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Yalnızca kullanıcı VSTO eklentisi Outlook'ta COM eklentileri iletişim kutusunu kullanarak devre dışı bıraktığında olayı oluşturulur. Outlook çıktığında çıkarılır değil. Outlook çıktığında, çalıştırılması gereken bir kodunuz varsa, aşağıdaki olaylardan biri ya da işler:  
  
-   <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> Olayı <xref:Microsoft.Office.Interop.Outlook.Application> nesne.  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> Olayı <xref:Microsoft.Office.Interop.Outlook.Explorer> nesne.  
  
> [!NOTE]  
>  Yükseltmek için Outlook zorlayabilirsiniz <xref:Microsoft.Office.Tools.AddInBase.Shutdown> kayıt defterini değiştirerek çıktığında olay. Yönetici bu ayarı döndürüyorsa, ancak herhangi için ekleme kodu `ThisAddIn_Shutdown` yöntemi artık Outlook çıkar olduğunda çalışır. Daha fazla bilgi için [kapatma Outlook 2010 için değişiklikleri](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)  
  
  