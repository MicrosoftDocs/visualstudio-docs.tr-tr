---
title: Outlook nesne modeline genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6885968385725f4aa7d991309902ca712849c8a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941197"
---
# <a name="outlook-object-model-overview"></a>Outlook nesne modeline genel bakış
  Microsoft Office Outlook için VSTO eklentileri geliştirmek için Outlook nesne modeli tarafından sağlanan nesneler ile etkileşim kurabilir. Outlook nesne modeline sınıflar ve kullanıcı arabirimi öğelerini temsil eden arabirim sağlar. Örneğin, <xref:Microsoft.Office.Interop.Outlook.Application> nesnesini temsil eder tüm uygulama <xref:Microsoft.Office.Interop.Outlook.Folder> nesne e-posta veya diğer öğeleri içeren bir klasörü temsil eder ve <xref:Microsoft.Office.Interop.Outlook.MailItem> nesnesi, bir e-posta iletisini temsil eder.  
  
 Bu konu Outlook nesne modelindeki ana nesnelerin bazıları kısa bir genel bakış sağlar. Kaynaklar nerede edinebilirsiniz tüm Outlook nesne modeli hakkında daha fazla bilgi için bkz [Outlook nesne modeli belgeleri kullanın](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [ı: Outlook'u kullanma bir özel görev rapor oluşturmak için bunu nasıl?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="access-objects-in-an-outlook-project"></a>Outlook projesinde nesnelere erişme  
 Outlook birçok nesne ile etkileşim sağlar. Nesne modeline etkili bir şekilde kullanmak için aşağıdaki üst düzey nesneleri ile ilgili bilgi sahibi olması gerekir:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Folder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Uygulama nesnesi  
 <xref:Microsoft.Office.Interop.Outlook.Application> Nesnesini temsil eden Outlook uygulaması ve Outlook nesne modelinde en üst düzey nesnedir. Bu nesnenin en önemli üyeleri bazıları şunlardır:  
  
- [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) bir e-posta iletisi, görev veya randevu gibi yeni bir öğe oluşturmak için kullanabileceğiniz yöntemi.  
  
- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> Özelliği Outlook kullanıcı arabiriminde (UI) görüntüleyen bir klasörün içeriğini windows erişmek için kullanabilirsiniz.  
  
- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> Özelliği gibi bir e-posta iletisi veya toplantı isteği tek bir öğenin içeriğini görüntüleyen pencerelerin erişmek için kullanabilirsiniz.  
  
  Bir kopyasını almak için <xref:Microsoft.Office.Interop.Outlook.Application> nesne, uygulama alanın kullanın `ThisAddIn` projenizdeki sınıfı. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Outlook nesne özelliklerini ve Outlook nesne modeli Koruması tarafından engellenen yöntemlerini kullandığınızda güvenlik uyarılarını önlemek için uygulama alanından Al `ThisAddIn` sınıfı. Daha fazla bilgi için [Office çözümleriyle ilgili belirli güvenlik konuları](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Nesne Gezgini  
 <xref:Microsoft.Office.Interop.Outlook.Explorer> Nesnesi e-posta iletileri, görevler veya randevu gibi öğeler içeren bir klasörün içeriğini görüntüleyen bir pencereyi temsil eder. <xref:Microsoft.Office.Interop.Outlook.Explorer> Yöntemleri ve penceresini değiştirmek için kullanabileceğiniz özellikler ve pencere değiştiğinde başlatılan olaylara nesne içerir.  
  
 Alınacak bir <xref:Microsoft.Office.Interop.Outlook.Explorer> nesne, aşağıdakilerden birini yapın:  
  
-   Kullanım <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> özelliği <xref:Microsoft.Office.Interop.Outlook.Application> tüm erişmek için nesne <xref:Microsoft.Office.Interop.Outlook.Explorer> Outlook'ta nesneleri.  
  
-   Kullanım <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> yöntemi <xref:Microsoft.Office.Interop.Outlook.Application> alınacak nesne <xref:Microsoft.Office.Interop.Outlook.Explorer> geçerli odağa sahip.  
  
-   Kullanım `GetExplorer` yöntemi <xref:Microsoft.Office.Interop.Outlook.Folder> alınacak nesne <xref:Microsoft.Office.Interop.Outlook.Explorer> geçerli klasör.  
  
### <a name="inspector-object"></a>Inspector nesnesi  
 <xref:Microsoft.Office.Interop.Outlook.Inspector> Nesnesi gibi bir e-posta iletisi, görev veya randevu tek bir öğeyi görüntüleyen bir pencereyi temsil eder. <xref:Microsoft.Office.Interop.Outlook.Inspector> Yöntemleri ve penceresini değiştirmek için kullanabileceğiniz özellikler ve pencere değiştiğinde başlatılan olaylara nesne içerir.  
  
 Alınacak bir <xref:Microsoft.Office.Interop.Outlook.Inspector> nesne, aşağıdakilerden birini yapın:  
  
-   Kullanım <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> özelliği <xref:Microsoft.Office.Interop.Outlook.Application> tüm erişmek için nesne <xref:Microsoft.Office.Interop.Outlook.Inspector> Outlook'ta nesneleri.  
  
-   Kullanım <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> yöntemi <xref:Microsoft.Office.Interop.Outlook.Application> alınacak nesne <xref:Microsoft.Office.Interop.Outlook.Inspector> geçerli odağa sahip.  
  
-   Kullanım `GetInspector` gibi belirli bir yöntemi öğesi bir <xref:Microsoft.Office.Interop.Outlook.MailItem> veya <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, onunla ilişkilendirilen Inspector'ı almak için.  
  
### <a name="folder-object"></a>Nesnesinin klasörünü  
 <xref:Microsoft.Office.Interop.Outlook.Folder> Nesne e-posta iletileri, kişiler, görevler ve diğer öğeleri içeren bir klasörü temsil eder. Outlook 16 varsayılan sağlar <xref:Microsoft.Office.Interop.Outlook.Folder> nesneleri.  
  
 Varsayılan <xref:Microsoft.Office.Interop.Outlook.Folder> nesneleri tarafından tanımlanmış <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> sabit listesi değerleri. Örneğin,  
  
 Karşılık gelen Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox **gelen** Outlook'taki.  
  
 Varsayılan erişim gösteren bir örnek <xref:Microsoft.Office.Interop.Outlook.Folder> ve yeni bir <xref:Microsoft.Office.Interop.Outlook.Folder>, bkz: [nasıl yapılır: program aracılığıyla özel klasör öğeleri oluşturma](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>MailItem Nesnesi  
 <xref:Microsoft.Office.Interop.Outlook.MailItem> Nesnesi, bir e-posta iletisini temsil eder. <xref:Microsoft.Office.Interop.Outlook.MailItem> nesneleri, genellikle klasörler gibi **gelen**, **Gönderilmiş öğeler**, ve **giden**. <xref:Microsoft.Office.Interop.Outlook.MailItem> Özellikler ve oluşturmak ve e-posta iletileri göndermek için kullanılan yöntemler sunar.  
  
 Bir e-posta iletisi oluşturmak nasıl gösteren bir örnek için bkz: [nasıl yapılır: program aracılığıyla bir e-posta öğesi oluşturma](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>AppointmentItem nesnesi  
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> Nesnesini gösteren bir toplantı, tek seferlik bir randevu veya yinelenen bir randevu veya toplantıya **Takvim** klasör. <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> Nesne yanıtlama veya toplantı istekleri ve toplantı ayrıntılarını zaman ve konum gibi belirten özellikleri iletme gibi eylemler gerçekleştiren yöntemler içerir.  
  
 Randevu oluşturma işlemini gösteren bir örnek için bkz: [nasıl yapılır: program aracılığıyla toplantı isteği oluşturma](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>TaskItem nesnesi  
 <xref:Microsoft.Office.Interop.Outlook.TaskItem> Nesnesi belirtilen bir zaman çerçevesi içinde gerçekleştirilecek bir görevi temsil eder. <xref:Microsoft.Office.Interop.Outlook.TaskItem> nesneleri yerleştirilir **görevleri** klasör.  
  
 Bir görev oluşturmak için kullanın [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) yöntemi <xref:Microsoft.Office.Interop.Outlook.Application> nesne ve değer geçirmek <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> parametresi için.  
  
### <a name="contactitem-object"></a>ContactItem nesnesi  
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>Nesnesini temsil eden bir kişi **kişiler** klasör. <xref:Microsoft.Office.Interop.Outlook.ContactItem> iletişim bilgileri, adres, e-posta adresi ve telefon numaraları gibi temsil ettikleri kişiler için çeşitli nesneleri içerir.  
  
 Yeni bir kişi oluşturulacağını gösteren bir örnek için bkz: [nasıl yapılır: program aracılığıyla Outlook Kişilerine bir giriş ekleyin](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Var olan bir kişi arama gösteren bir örnek için bkz [nasıl yapılır: program aracılığıyla belirli bir kişi arama](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Outlook nesne modeli belgeleri kullanın  
 Outlook nesne modeli hakkında tam bilgi için Outlook birincil birlikte çalışma derlemesi (PIA) başvuru ve VBA nesne modeli başvurusu başvurabilir.  
  
### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma bütünleştirilmiş kod başvurusu  
 Outlook 2010 için birincil birlikte çalışma bütünleştirilmiş kodlarında türler Outlook PIA başvuru belgeleri. Daha fazla bilgi için [Outlook 2010 birincil birlikte çalışma bütünleştirilmiş kod başvurusu](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Bütün PIA'ların türlerini bilgi sağlamaya ek olarak, bu belgeleri de PIA'ların ve kod örnekleri için ortak Outlook otomasyon görevleri yapısı hakkında ek bilgi sağlar.  
  
### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu  
 Visual Basic for Applications (VBA) kodundaki sunulur şekilde VBA nesne modeli başvurusu Outlook nesne modeline listelenmiştir. Daha fazla bilgi için [Outlook 2010 nesne modeli başvurusu](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Tüm nesnelerin ve üyelerin VBA nesne modeli başvurusu türlerine ve üyelerine Outlook PIA karşılık gelir. VBA nesne modeli başvurusu denetçisi nesnesinde, karşılık gelen <xref:Microsoft.Office.Interop.Outlook.Inspector> Outlook PIA nesne. VBA nesne modeli başvurusu çoğu özellikleri, yöntemleri ve olayları için kod örnekleri sağlasa da, bunları kullanarak oluşturduğunuz bir Outlook VSTO eklenti projesinde kullanmak istiyorsanız, Visual Basic veya Visual C# bu başvuruyu VBA kodu Çevir gerekir Visual Studio.  
  
### <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Kişi öğeleriyle çalışma](../vsto/working-with-contact-items.md)|Kişilerle görevleri nasıl gerçekleştireceğinizi gösteren konuları sağlar.|  
|[Posta öğeleriyle çalışma](../vsto/working-with-mail-items.md)|Posta öğeleriyle görevleri nasıl gerçekleştireceğinizi gösteren konuları sağlar.|  
|[Klasörlerle çalışma](../vsto/working-with-folders.md)|Klasörlerle görevleri nasıl gerçekleştireceğinizi gösteren konuları sağlar.|  
|[Takvim öğeleriyle çalışma](../vsto/working-with-calendar-items.md)|Takvim öğeleriyle görevleri nasıl gerçekleştireceğinizi gösteren konuları sağlar.|  
|[Nasıl yapılır: program aracılığıyla geçerli Outlook öğesini belirleme](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Geçerli klasör ve seçtiğiniz öğe hakkındaki bazı bilgileri adının nasıl görüntüleneceğini gösterir.|  
  