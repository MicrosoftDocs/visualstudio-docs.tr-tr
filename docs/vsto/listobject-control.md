---
title: ListObject denetimi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2fe8191acc2bab7fbcfa2f21ef203f6057535a75
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677183"
---
# <a name="listobject-control"></a>ListObject denetimi
  <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim olayları ortaya koyan ve verilere bağlı bir listedir. Bir çalışma sayfasına bir liste eklediğinizde, Visual Studio oluşturur bir <xref:Microsoft.Office.Tools.Excel.ListObject> Microsoft Office Excel nesne modeline geçiş yapmak zorunda kalmadan doğrudan programlayabileceğiniz denetimi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Denetim oluşturma  
 Belge düzeyinde projelerde eklediğiniz <xref:Microsoft.Office.Tools.Excel.ListObject> tasarım zamanında veya çalışma zamanında çalışma. Projelerinde, VSTO eklentisi, eklediğiniz <xref:Microsoft.Office.Tools.Excel.ListObject> yalnızca çalışma zamanında çalışma sayfalarına denetimleri. Daha fazla bilgi için [nasıl yapılır: çalışma sayfalarına ListObject ekleme denetimlerini](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Varsayılan olarak, çalışma sayfasında dinamik olarak oluşturulan listenin nesneleri sürdürülmeyen çalışma kapatıldığında denetimleri gibi. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="bind-data-to-the-control"></a>Veriyi denetime bağlama  
 A <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi, basit ve karmaşık veri bağlamayı destekler. <xref:Microsoft.Office.Tools.Excel.ListObject> Denetimi kullanarak bir veri kaynağına bağlanabilir <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> ve <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> tasarım zamanında özellikleri veya <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> zamanında yöntemi.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.ListObject> Gibi bir veri kaynağına bağlı olduğu zaman otomatik olarak güncelleştirilen bir <xref:System.Data.DataTable>, veriler değiştiğinde bir olay başlatır. Bağlarsanız <xref:Microsoft.Office.Tools.Excel.ListObject> veriler değiştiğinde olayları geçirmemesi için bir veri kaynağı, çağırmalısınız <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> veya <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> güncelleştirilecek yöntemi <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
 Eklediğinizde bir <xref:Microsoft.Office.Tools.Excel.ListObject> bir çalışma sayfası hücresi yinelenen bir şema öğesine bu hücreye eşleyerek, Visual Studio otomatik olarak eşlenir <xref:Microsoft.Office.Tools.Excel.ListObject> üretilen veri kümesi için. Ancak, <xref:Microsoft.Office.Tools.Excel.ListObject> otomatik olarak verilere bağlı değil. Bağlamak üzere adım atabilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject> tasarım zamanında veya çalışma zamanında bir belge düzeyi projede veri kümesi için. Program aracılığıyla bağlayabilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject> veri kümesiyle çalışma zamanında VSTO eklenti.  
  
 Veriler ayrı olduğundan <xref:Microsoft.Office.Tools.Excel.ListObject>, eklemek ve kaldırmak, ilişkili veri kümesini ve doğrudan aracılığıyla veri <xref:Microsoft.Office.Tools.Excel.ListObject>. Herhangi bir mekanizma aracılığıyla ilişkili veri kümesindeki veriler güncelleştirilirse <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi otomatik olarak değişiklikleri yansıtır. Daha fazla bilgi için [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Hızlı bir şekilde doldurmak için bir <xref:Microsoft.Office.Tools.Excel.ListObject> bağlayarak denetimi <xref:Microsoft.Office.Tools.Excel.ListObject> bir veri kaynağı. Verilere bağlı verileri düzenlerseniz <xref:Microsoft.Office.Tools.Excel.ListObject>, değişiklikler veri kaynağında da otomatik olarak yapılır. Doldurmak istiyorsanız bir <xref:Microsoft.Office.Tools.Excel.ListObject> ve sonra verileri değiştirmek kullanıcı etkinleştirme <xref:Microsoft.Office.Tools.Excel.ListObject> kullanabileceğiniz veri kaynağını değiştirmeden <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> yöntemini <xref:Microsoft.Office.Tools.Excel.ListObject> veri kaynağından. Daha fazla bilgi için bkz [nasıl yapılır: ListObject dolgu denetimleri ile verileri](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
> [!NOTE]  
>  Veri bağlama çakışan üzerinde desteklenmiyor <xref:Microsoft.Office.Tools.Excel.ListObject> kontrol eder.  
  
### <a name="improve-performance-in-listobject-controls"></a>ListObject denetiminde performansı  
 Verilere bağlı bir XML dosyası okunurken <xref:Microsoft.Office.Tools.Excel.ListObject> denetim eğilimlidir denetimi ilk bağlamak ve ardından arama yavaş olacak şekilde <xref:System.Data.DataSet.ReadXml%2A> DataSet'i doldurmak için. Performansı artırmak için çağrı <xref:System.Data.DataSet.ReadXml%2A> denetimi bağlamadan önce.  
  
### <a name="disconnect-listobject-controls-from-the-data-source"></a>ListObject denetimlerini veri kaynağından bağlantısını kes  
 Doldurduktan sonra bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetim liste nesnesi verilerde yapılan değişiklikleri veri kaynağına etkilemez, böylece bir veri kaynağına bağlayarak veri ile kesebilirsiniz. Daha fazla bilgi için bkz [nasıl yapılır: ListObject dolgu denetimleri ile verileri](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
### <a name="restore-column-and-row-order"></a>Sütun ve satır sırası geri yükleme  
 Veri bağladığınızda bir <xref:Microsoft.Office.Tools.Excel.ListObject> Visual Studio çalışma kitabının kaydedilmiş her sütun ve satır sırasını izler tasarım zamanında, bir belgeye eklendikten sonra Denetim. Bir kullanıcı taşınırsa <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma zamanı sırasında satırları veya sütunları yeni sipariş çalışma kitabı sonraki açılışında korunur ve <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi veri kaynağına yeniden bağlar.  
  
 Geri yüklemek istiyorsanız <xref:Microsoft.Office.Tools.Excel.ListObject> özgün sütun ve satır sırası için çağırabilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> yöntemi. Bu yöntem sütunuyla ilişkili özel belge özellikleri kaldırır ve belirtilen satır sırası <xref:Microsoft.Office.Tools.Excel.ListObject>. Bu yöntemi çağırın <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> olay sütun ve satır sıralamasını korumak istemiyorsanız çalışma kitabının <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## <a name="format"></a>Biçimi  
 Uygulanabilir biçimlendirme bir <xref:Microsoft.Office.Interop.Excel.ListObject> uygulanabilir bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi. Bu, kenarlık, yazı tipleri, sayı biçimini ve stilleri içerir. Son kullanıcılar, verilere bağlı sütunlar düzenleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject>, ve bu değişiklikleri sağlanan belge ile kalıcı <xref:Microsoft.Office.Tools.Excel.ListObject> belgenin tasarım zamanında eklendi. Belgeyi bir sonraki açılışında liste nesnesi aynı veri kaynağına bağlı, ancak sütun sırasını kullanıcıların değişiklikleri yansıtır.  
  
## <a name="add-and-remove-columns-at-runtime"></a>Ekleme ve çalışma zamanında sütunları kaldırma  
 El ile ekleyemez veya verilere bağlı sütunları kaldırma <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma zamanında denetim. Son kullanıcı, bir sütunu silmek çalışırsa, hemen geri yüklenecektir ve eklenen sütunlar kaldırılır. Bu nedenle, neden olamaz gerçekleştirdikleri bu eylemler hakkında kullanıcılara açıklamak üzere kod yazmak önemli bir <xref:Microsoft.Office.Tools.Excel.ListObject> verilere bağlı. Visual Studio üzerinde çeşitli etkinliklerde sağlar bir <xref:Microsoft.Office.Tools.Excel.ListObject> veri bağlama ile ilgili. Örneğin, kullanabileceğiniz <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> bunlar silmeye çalıştı veri silinemez ve geri yüklendi kullanıcıları uyarmak için olay.  
  
## <a name="add-and-remove-rows-at-runtime"></a>Ekleme ve çalışma zamanında satırları Kaldır  
 El ile eklemek ve veri bağlama satırları Kaldır <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi veri kaynağı yeni satırların eklenmesini sağlar ve salt okunur olmaması koşuluyla. Olaylara karşı kodu gibi yazabileceğiniz <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> verileri doğrulamak için. Daha fazla bilgi için [nasıl yapılır: ListObject denetimine yeni bir satır eklendiğinde veri doğrulama](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).  
  
 Bazen veri kaynağı için liste nesne arasındaki ilişkiyi rutin hatalarına neden olur. Örneğin, görüntülenmesini istediğiniz sütunları eşleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject>, null değerler alamaz gibi bir alan kısıtlamaları olan sütunları atlarsanız, bir satır oluşturulduğunda hatalar ortaya çıkar. Eksik değerleri için bir olay işleyicisi eklemek için kod yazabilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> olay.  
  
## <a name="rename-listobject-controls-in-excel"></a>Excel ListObject denetimleri yeniden adlandırma  
 Excel kullanarak çalışma zamanında Excel tabloları adını değiştirmek kullanıcıların sağlar **tasarım** sekmesi. Ancak, <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi, bu özelliği desteklemez. Bir kullanıcı için karşılık gelen bir Excel tabloyu yeniden adlandırma çalışırsa bir <xref:Microsoft.Office.Tools.Excel.ListObject>, çalışma kitabını kaydedildiğinde Excel tablosu adını otomatik olarak özgün adına geri döner.  
  
## <a name="events"></a>Olaylar  
 Aşağıdakiler için kullanılabilir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi:  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Nasıl yapılır: ListObject denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-listobject-controls.md)   
 [Nasıl yapılır: ListObject denetimine yeni bir satır eklendiğinde verileri doğrulama](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Nasıl yapılır: eşleme ListObject sütunlarıyla verileri](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Nasıl yapılır: dolgu ListObject denetimlerini veri ile](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Nasıl yapılır: çalışma sayfalarını veritabanı verileriyle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  