---
title: Windows Forms denetimlerine Office belgeleri genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51c671a583e4e96b51ae6627de1fce738696fe22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892787"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Windows Forms denetimlerine Office belgeleri genel bakış
  Windows Forms denetimlerini, kullanıcıların girin veya verileri işlemek için etkileşim kurabilir nesnelerdir. Microsoft Office Excel ve Microsoft Office Word için belge düzeyi projeleri, Windows Forms denetimleri belge veya çalışma kitabındaki projenizde tasarım zamanında ekleyebileceğiniz veya program aracılığıyla çalışma zamanında bu denetimler ekleyebilirsiniz. Program aracılığıyla bu denetimleri herhangi bir açık belge veya çalışma zamanında VSTO eklenti Excel veya Word için ekleyebilirsiniz.  
  
 Daha fazla bilgi için [nasıl yapılır: denetimleri Office belgelerine Windows Forms ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="use-windows-forms-controls"></a>Windows Forms denetimlerini kullanma  
 Windows Forms denetimleri, belgelere ve Eylemler bölmesi, özel görev bölmeleri ve Windows Forms dahil olmak üzere, özelleştirilebilir kullanıcı arabirimi (UI) öğeleri ekleyebilirsiniz. Windows Forms denetimlerine genel belgelerde bu bir kullanıcı Arabirimi öğelerinde aynı davranışa sahip, ancak bazı farklılıklar mevcuttur. Bilgi için [sınırlamalar, Windows Forms denetimleri Office belgelerini](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Windows Forms denetimleri bir belge veya başka bir kullanıcı Arabirimi öğesi eklemek çeşitli etkenlere bağlıdır karar. Windows Forms denetimleri kullanımlarını UI çözümünüzü tasarlarken, aşağıdaki tabloda açıklandığı gibi göz önünde bulundurun.  
  
 Belge üzerinde.  
 -   %100 zaman denetimlerini görüntülemek istediğinizde.  
  
- Kullanıcıların doğrudan belgedeki verileri, örneğin, form tabanlı belgeleri nerede düzenleme surface kilitli girmesini istediğinizde.  
  
- Belgedeki veriyi ayarlarına uygun olarak görüntülemek için denetimler istediğinizde. Örneğin, her satıra bir liste nesnesinin düğmeleri ekliyorsanız, bunları ayarlarına uygun olarak her bir liste öğesi istersiniz.  
  
  Eylemler bölmesinde veya bir özel görev bölmesi.  
  -   Kullanıcıya bağlamsal bilgi sağlamak istediğinizde.  
  
- Belge ve değil sorgu denetimleri ve verileri yalnızca sonuçların görünmesini istediğinizde.  
  
- Denetim belgeyle yazdırılmaz sağlamak istediğinizde.  
  
- Denetimler belgenin görüntüsüyle karışmadığına müdahale etmez sağlamak istediğinizde.  
  
  Bir Windows formunda.  
  -   Kullanıcı arabirimini boyutunu denetlemek istediğinizde.  
  
- Denetimleri gizleme veya kullanıcıların engellemek istediğinizde.  
  
- Bir kullanıcıdan giriş almak ve kullanıcının giriş alınana kadar her şeyi belge yapmasını önlemek istediğinizde.  
  
## <a name="add-windows-forms-controls-programmatically"></a>Program aracılığıyla Windows Forms denetimleri ekleme  
 Word belgelerini ve Excel çalışma zamanında Windows Forms denetimleri ekleyebilirsiniz. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Ortak Windows Formları denetimleri eklemek için yardımcı yöntemleri sağlar. Bu yardımcı yöntemler Office belge ve birleşik Windows Forms denetimi işlevlerini erişim denetimleri ve işlevselliği Office ile ilgili bu denetimlerin hızla eklemenize imkan tanır.  
  
 Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="use-windows-forms-controls-in-document-level-projects"></a>Belge düzeyinde projelerde Windows Forms denetimlerini kullanma  
 Bazı yönlerini belgelerindeki Windows Forms denetimleri kullanarak Visual Studio tasarımcısı kullanarak, belgenizin kullanıcı Arabirimi tasarlamanıza olanak tanıyan belge düzeyi projelerine özgüdür.  
  
### <a name="create-custom-user-controls"></a>Özel kullanıcı denetimi oluşturma  
 Projenize bir kullanıcı denetimi ekleyin ve ardından ekleyin **araç kutusu**. Ardından, belgenize bir Windows Forms denetimi eklemek tıpkı belgenizi doğrudan kullanıcı denetimi sürükleyebilirsiniz. Kullanıcı denetimleri oluşturduğunuzda göz önünde bulundurmanız gereken bazı hususlar vardır:  
  
-   Oluşturma bir **korumalı** kullanıcı denetimi. Belgenize denetimi sürükleyin, Visual Studio yükseltime ve belge üzerinde kullanımını desteklemek için kullanıcı denetimi türetilen bir sarmalayıcı sınıf oluşturur. Kullanıcı denetimine ise **korumalı**, Visual Studio sarmalayıcı sınıfı oluşturamaz.  
  
-   Kullanıcı denetimleri olmalıdır <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliğini **true**. Bir Office projesi içinde oluşturulan kullanıcı denetiminiz ayarlamak bu öznitelik **true** varsayılan, ancak kullanıcı tarafından dış projelerin bir parçası olan denetimler ayarlamak bu öznitelik olmayabilir **true**.  
  
-   Belgeyi bir kullanıcı denetimi ekledikten sonra yeniden adlandırma silmeyin veya <xref:System.Windows.Forms.UserControl> projesinden sınıfı. Bir kullanıcı denetiminin adını değiştirmeniz gerekirse belgeden silmeden önce ve adı değiştirildikten sonra tekrar eklemeniz gerekir.  
  
### <a name="arrange-controls-at-design-time"></a>Denetimleri tasarım zamanında düzenleme  
 Tasarım zamanında Word ve Excel birden çok denetim eklerseniz, hızlı bir şekilde tüm seçili denetimleri hizalama kullanarak ayarlayabilirsiniz **Microsoft Office Word** ve **Microsoft Office Excel**Visual Studio'da araç çubukları. Bu araç çubukları, yalnızca bir belge veya çalışma sayfasını tasarımcıda açık olduğunda kullanılabilir.  
  
 Birden çok denetim Tasarımcısı'nda seçtiğinizde, bu araç çubuklarında denetimlerini düzenlemek için aşağıdaki düğmelerden kullanabilirsiniz:  
  
-   **Sola Hizala**  
  
-   **Merkeze Hizala**  
  
-   **Sağa Hizala**  
  
-   **Üste hizalama**  
  
-   **Ortaya Hizala**  
  
-   **Alta Hizala**  
  
-   **Yatay Aralığı Eşit Yap**  
  
-   **Dikey aralığı eşit yap**  
  
> [!NOTE]  
>  Yalnızca Seçili denetimleri metinle yüklemiyorsanız bu düğmeler Word projelerinde etkinleştirilir. Varsayılan olarak, tasarım zamanında belgeye eklediğiniz metinle denetimlerdir.  
  
### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Eski veri yükleme sırasında Excel çalışma kitaplarını görünmesini engellemek  
 Windows Forms denetimleri belge veya çalışma sayfaları için tasarım zamanında eklediğiniz zaman, kullanıcının belgeyi kapandığında denetimleri belgede kalır. Tasarım zamanında eklenen denetimler de denir *statik denetim*.  
  
 Statik denetim içeren bir Excel çalışma kitabını açtığınızda, çalışma kitabını özelleştirme kodu çalıştırır ve gerçek denetim yükler kadar denetimin bir bit eşlem ActiveX denetiminde görüntüler. Excel bu bit eşlem oluşturur ve çalışma kitabının kaydedilmiş her çalışma kitabında depolar. Bit eşlem denetim, denetimin gösterdiği tüm veriler dahil olmak üzere çalışma kitabının kaydedilmiş son kez göründükleri gibi gösterir. Windows Forms denetimleri ve bit eşlemler içeren bir ActiveX denetimi hakkında daha fazla bilgi için bkz. [sınırlamalar, Windows Forms denetimleri Office belgelerini](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Bazı durumlarda, kod yüklemez ve sadece bit eşlemi, kullanıcı çalışma kitabı Tasarım modunda açıldığında gibi görüntülenir. Ayrıca, kullanıcının sahip olmayan bir bilgisayarda çalışma kitabını açar, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] denetimleri yüklemek için özelleştirme çalışamaz ve bu nedenle yalnızca bit eşlem denetimin görünür olup yüklü. Her zaman, çalışma kitabını kaydetmeden ve kişisel bilgilerinizi yanlışlıkla olarak çıkmadığından emin olmak için başka bir kullanıcıya göndermeden önce çalışma kitaplarının denetimlerden kişisel bilgileri kaldırmanız gerekir.  
  
### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Excel çalışma sayfasındaki hücreyi boyuta denetim boyutu  
 Denetimin üst hücre boyutu değiştiğinde otomatik olarak yeniden boyutlandırılıp ayarlayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Tüm çalışma sayfalarını tarafından paylaşılan bileşenleri ekleme  
 Tüm çalışma sayfaları arasında gibi paylaşmak istediğiniz bileşenleri ekleyebileceğiniz bir <xref:System.Data.DataSet>, çalışma kitabı tasarımcısına çalışma sayfaları. Bileşen bileşen alanında görünür.  
  
### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Formül bir Excel çalışma sayfasına denetimler ekleme  
 Excel'de bir denetimi seçtiğinizde göreceğiniz **=EMBED("WinForms.Control.Host","")** içinde **formül çubuğu**. Bu metin, gereklidir ve silinmemelidir.  
  
### <a name="layout-style-of-controls-on-a-word-document"></a>Word belgesinde denetimlerin düzen stili  
 Bir denetimi bir belge düzeyi projede Word belgesi için Visual Studio tasarımcısı kullanarak eklediğinizde, denetimin metin ayarlarına uygun olarak eklenir. Denetimin düzenini stilini değiştirmek için denetime sağ tıklayın ve ardından **biçim denetimi**. Bir kaydırma stilini seçin **Düzen** sayfasının **biçimi nesne** iletişim kutusu.  
  
 Çalışma zamanında bir Word belgesi için bir denetim eklediğinizde, farklı kullanarak yeni denetimin düzen stili belirtebilirsiniz `Add` \< *denetim sınıf*> yöntemi aşırı yüklemeleri <xref:Microsoft.Office.Tools.Word.ControlCollection> sınıfı:  
  
- Ayarlarına uygun olarak metin denetimi eklemek için kabul eden bir aşırı yüklemesini kullanın. bir <xref:Microsoft.Office.Interop.Word.Range> denetimin konumunu belirtir.  
  
- Denetimi kayan bir şekil eklemek için denetimin sol ve üst koordinatları kabul eden bir aşırı yüklemesini kullanın.  
  
  Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
  Visual Studio tasarımcıda bir Word şablonu açın, Visual Studio şablonu açar çünkü şablon satır içi denetimleri görünür olmayabilir **Normal** görünümü. Denetimleri görüntülemek için görünüme **düzeni**.  
  
### <a name="controls-outside-the-main-document-body"></a>Ana dosya gövdesinin dışında denetimleri  
 Windows Forms denetimleri üstbilgisindeki veya altbilgisindeki içinde veya bir alt içinde desteklenmez.  
  
### <a name="add-components-at-design-time"></a>Tasarım zamanında bileşenleri ekleme  
 Belirli denetimler ve bileşenler belgede görünmez ve bunun yerine bir bileşen tepsisinde görüntülenir. Visual Studio bileşeni Tepsi her belge penceresi için sağlar. Bileşen Tepsisi bileşenleri belgede yalnızca mevcut ekranda görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)   
 [Windows Forms denetimleri](/dotnet/framework/winforms/controls/index)   
 [Office belgelerindeki Windows Forms denetimleri sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Nasıl yapılır: yazdırırken çalışma sayfası denetimlerini gizleme](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [İzlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [İzlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [İzlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [İzlenecek yol: metin kutusunda düğme kullanarak bir belgede metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Office belgelerindeki Windows Forms denetimleri sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [İzlenecek yol: radyo düğmelerini kullanarak belgede grafik güncelleştir](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [İzlenecek yol: radyo düğmelerini kullanarak çalışma sayfasında grafik güncelleştir](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  