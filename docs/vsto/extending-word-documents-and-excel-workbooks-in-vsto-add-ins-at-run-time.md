---
title: Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 424b2cf8a6461ed0d60a1c16555c49c0ed8a0136
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895788"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-runtime"></a>Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerinde genişletme
  Bir VSTO eklentisi Word belgelerini ve Excel çalışma kitapları aşağıdaki yollarla özelleştirmek için kullanabilirsiniz:  
  
- Yönetilen denetimleri, herhangi bir açık belge veya çalışma sayfası ekleyin.  
  
- Excel çalışma kitabında var olan bir liste nesnesi için genişletilmiş bir dönüştürme <xref:Microsoft.Office.Tools.Excel.ListObject> olayları ortaya koyan ve verilere Windows Forms veri bağlama modelini kullanarak bağlanabilir.  
  
- Belirli belgeler, workbooks ve çalışma sayfaları için Word ve Excel tarafından sunulan erişim uygulama düzeyinde olaylar.  
  
  Bu işlevselliği kullanmak için belge veya çalışma kitabındaki genişleten çalışma zamanında bir nesne oluşturur.  
  
  **İçin geçerlidir:** bu makaledeki bilgiler şu uygulamalar için VSTO eklentisi projeleri için geçerlidir: Excel ve Word. Daha fazla bilgi için [Office uygulaması ve proje türüne göre kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="generate-extended-objects-in-vsto-add-ins"></a>VSTO eklentileri Genişletilmiş nesneler oluştur  
 *Genişletilmiş nesneleri* Word veya Excel nesne modellerinde yerel olarak mevcut nesneleri işlevselliği eklemek için Office çalışma zamanı için Visual Studio Araçları tarafından sağlanan türlerinin örnekleridir (adlı *yerel Office nesneleri*). Word veya Excel nesnesi için genişletilmiş bir nesne oluşturmak için `GetVstoObject` yöntemi. İlk kez çağırmanız `GetVstoObject` yöntemi belirtilen Word veya Excel nesne, belirtilen nesne genişleten yeni bir nesne döndürür. Her zaman yöntemini çağırın ve aynı Word veya Excel nesne aynı Genişletilmiş nesneyi döndürür.  
  
 Genişletilmiş nesne türünü yerel Office nesne türü olarak aynı ada sahip, ancak türü tanımlanan <xref:Microsoft.Office.Tools.Excel> veya <xref:Microsoft.Office.Tools.Word> ad alanı. Örneğin, eğer `GetVstoObject` genişletmek için yöntemi bir <xref:Microsoft.Office.Interop.Word.Document> yöntemi döndürür, nesne bir <xref:Microsoft.Office.Tools.Word.Document> nesne.  
  
 `GetVstoObject` Yöntemleri, öncelikle VSTO eklentisi projelerde kullanılmaya yöneliktir. Belge düzeyinde projelerde bu yöntemleri de kullanabilirsiniz, ancak bunlar farklı davranır ve daha az kullanıma sahip.  
  
 Genişletilmiş bir nesne için belirli bir yerel Office nesnesi zaten oluşturulmuş olup olmadığını belirlemek için `HasVstoObject` yöntemi. Daha fazla bilgi için [Office nesne genişletilmiş olup olmadığını belirlemek](#HasVstoObject).  
  
### <a name="generate-host-items"></a>Ana bilgisayar öğeleri oluşturma  
 Kullanırken `GetVstoObject` belge düzeyinde bir nesne genişletmek için (diğer bir deyişle, bir <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, veya <xref:Microsoft.Office.Interop.Word.Document>), döndürülen nesne adında bir *konak öğesi*. Bir konak öğesi diğer genişletilmiş nesneler ve denetimler gibi diğer nesneleri içerebilir bir türdür. Word veya Excel birincil birlikte çalışma derlemesi karşılık gelen türü benzer, ancak ek özellikleri vardır. Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
 Bir konak öğesi oluşturduktan sonra yönetilen denetimleri belge, çalışma kitabı veya çalışma sayfası eklemek için kullanabilirsiniz. Daha fazla bilgi için [Ekle yönetilen belgeler ve çalışma denetimlerini](#AddControls).  
  
#### <a name="to-generate-a-host-item-for-a-word-document"></a>Bir konak öğesi için bir Word belgesi oluşturmak için  
  
-   Aşağıdaki kod örneği, etkin belge konak öğesi oluşturmak nasıl gösterir.  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Bir Excel çalışma kitabı konak öğesi oluşturmak için  
  
-   Aşağıdaki kod örneği, etkin çalışma kitabı konak öğesi oluşturmak nasıl gösterir.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Bir Excel çalışma sayfası konak öğesi oluşturmak için  
  
-   Aşağıdaki kod örneği, etkin çalışma sayfası konak öğesi bir proje oluşturmak nasıl gösterir.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generate-listobject-host-controls"></a>ListObject konak denetimleri oluştur  
 Kullanırken `GetVstoObject` genişletmek için yöntemi bir <xref:Microsoft.Office.Interop.Excel.ListObject>, yöntem döndürür bir <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Tüm özellikleri özgün sahip <xref:Microsoft.Office.Interop.Excel.ListObject>. Ayrıca, ek işlevlere sahiptir ve verilere Windows Forms veri bağlama modelini kullanarak bağlanabilir. Daha fazla bilgi için [ListObject denetimine](../vsto/listobject-control.md).  
  
#### <a name="to-generate-a-host-control-for-a-listobject"></a>ListObject bir konak denetimi oluşturmak için  
  
-   Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:Microsoft.Office.Tools.Excel.ListObject> ilk <xref:Microsoft.Office.Interop.Excel.ListObject> projesinde etkin çalışma sayfasındaki.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
###  <a name="AddControls"></a> Yönetilen denetimleri belgeler ve çalışma sayfalarına ekleme  
 Oluşturduktan sonra bir <xref:Microsoft.Office.Tools.Word.Document> veya <xref:Microsoft.Office.Tools.Excel.Worksheet>, belgeye denetim eklemek veya bu genişletilmiş çalışma nesnelerini temsil eder. Denetimler eklemek için `Controls` özelliği <xref:Microsoft.Office.Tools.Word.Document> veya <xref:Microsoft.Office.Tools.Excel.Worksheet>. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Windows Forms denetimleri ekleyebilirsiniz veya *konak denetimlerini*. Bir ana bilgisayar denetim tarafından sağlanan bir denetimdir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Word veya Excel birincil birlikte çalışma derlemesi içinde karşılık gelen bir denetim sonuna geldik. Bir konak denetimi tüm temel alınan yerel Office nesnesinin davranışını kullanıma sunar. Ayrıca, olayları başlatır ve verilere Windows Forms veri bağlama modelini kullanarak bağlanabilir. Daha fazla bilgi için [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  Ekleyemezsiniz bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimi bir çalışma sayfasına veya <xref:Microsoft.Office.Tools.Word.XMLNode> veya <xref:Microsoft.Office.Tools.Word.XMLNodes> denetlemek için VSTO eklentisi kullanarak bir belge. Bu konak denetimleri program aracılığıyla eklenemez. Daha fazla bilgi için [konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="persist-and-remove-controls"></a>Kalıcı hale getirmek ve denetimlerini kaldırma  
 Yönetilen denetimleri bir belge veya çalışma sayfasına eklediğinizde, belgenin kaydedilip kapatılan denetimleri kalıcı değildir. Tüm konak denetimleri, böylece yalnızca arka plandaki yerel Office nesneleri geride kaldırılır. Örneğin, bir <xref:Microsoft.Office.Tools.Excel.ListObject> olur bir <xref:Microsoft.Office.Interop.Excel.ListObject>. Tüm Windows Formları denetimleri de kaldırılır, ancak denetimler için ActiveX sarmalayıcısının belgede kalır. Kod, VSTO eklenti denetimleri temizlemek için ya da belgeyi bir sonraki açılışında denetimleri yeniden eklemeniz gerekir. Daha fazla bilgi için [Office belgelerinde Dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## <a name="access-application-level-events-on-documents-and-workbooks"></a>Belgeler ve çalışma kitapları erişim uygulama düzeyinde olaylar  
 Bazı belge, çalışma kitabının ve çalışma olayları yerel Word ve Excel nesne modelleri yalnızca uygulama düzeyinde oluşturulur. Örneğin, <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> Word'de bir belge açıldığında, ancak bu olayın tanımlanan olayı oluşturulur <xref:Microsoft.Office.Interop.Word.Application> sınıfı yerine <xref:Microsoft.Office.Interop.Word.Document> sınıfı.  
  
 VSTO eklenti yalnızca yerel Office nesneleri kullandığınızda, bu uygulama düzeyinde olaylar işlemek ve ardından olayı belge bir özelleştirilmiş olup olmadığını belirlemek için ek kod yazmanız gerekir. Konak öğeleri belirli bir belge için olaylarını işlemek daha kolay bu olaylar belge düzeyinde sağlayın. Konak öğesi oluşturmak ve ardından söz konusu konak öğesi olayını işleyin.  
  
### <a name="example-that-uses-native-word-objects"></a>Yerel Word nesneleri kullanan örnek  
 Aşağıdaki kod örneği, bir Word belgeleri için uygulama düzeyi olayın nasıl işleneceğini gösterir. `CreateDocument` Yöntemi yeni bir belge oluşturur ve ardından tanımlayan bir <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> bu belgeyi kaydedilmesini engelleyen bir olay işleyicisi. Olay için ortaya çıkan bir uygulama düzeyi olaydır <xref:Microsoft.Office.Interop.Word.Application> gerekir, nesne ve olay işleyicisi karşılaştırma `Doc` parametresiyle `document1` belirlemek için nesne `document1` kaydedilen belgeyi temsil eder.  
  
 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>Bir konak öğesi kullanan örnekler  
 Aşağıdaki kod örnekleri, işleme göre bu işlemi basitleştireceksiniz <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> olayı bir <xref:Microsoft.Office.Tools.Word.Document> konak öğesi. `CreateDocument2` Yöntem bu örneklerde oluşturur bir <xref:Microsoft.Office.Tools.Word.Document> genişleten `document2` nesnesi ve ardından onu tanımlayan bir <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> belge kaydedilmesini engelleyen bir olay işleyicisi. Yalnızca olay işleyicisinde çağrılır `document2` kaydedilir ve kaydetme iptal edebilirsiniz hangi belge kaydedildi doğrulamak için ek iş yapmadan olmadan işlem.  
  
 Aşağıdaki kod örneği, bu görevi gösterir.  
  
 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> Bir Office nesne genişletilmiş olup olmadığını belirleme  
 Genişletilmiş bir nesne için belirli bir yerel Office nesnesi zaten oluşturulmuş olup olmadığını belirlemek için `HasVstoObject` yöntemi. Bu yöntem döndürür **true** genişletilmiş bir nesne zaten oluşturulduysa.  
  
 Kullanım `Globals.Factory.HasVstoMethod` yöntemi. Gibi yerel Word veya Excel nesnesi içinde geçirin bir <xref:Microsoft.Office.Interop.Word.Document> veya <xref:Microsoft.Office.Interop.Excel.Worksheet>, genişletilmiş bir nesne için test etmek istediğiniz.  
  
 `HasVstoObject` Yöntemi, yalnızca belirtilen bir Office nesne genişletilmiş bir nesneye sahip kodu çalıştırmak istediğinizde yararlıdır. Örneğin, bir sözcük VSTO işleyen eklentisi varsa <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> kaydedilmeden önce yönetilen denetimleri belgeden kaldırmak için kullanın, olay `HasVstoObject` belge genişletilmiş olup olmadığını belirlemek için yöntemi. Belge genişletilmemiş, denetimleri yönetilen olamaz ve olay işleyicisi belge denetimlere temizlemek çalışmadan döndürebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)  
  
  