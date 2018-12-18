---
title: .NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Excel ve Word projelerini güncelleştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aeb36f92533992161e2c7fa4f7bbcd3537fd0ebc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919409"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Excel ve Word projelerini güncelleştirme
  Aşağıdaki özelliklerden herhangi birini kullanan bir Excel veya Word'den projeniz varsa, hedef Framework'ü değiştirilirse kodunuzu değiştirmelisiniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra:  
  
- [GetVstoObject ve HasVstoObject yöntemi](#GetVstoObject)  
  
- [Belge düzeyinde projelerde oluşturulan sınıflar](#generatedclasses)  
  
- [Belgelerindeki Windows Forms denetimleri](#winforms)  
  
- [Word içerik denetimi olayları](#ccevents)  
  
- [OLEObject ve OLEControl sınıfları](#ole)  
  
- [Controls.Item(Object) özelliği](#itemproperty)  
  
- [CollectionBase'den türetilen koleksiyonları](#collections)  
  
  Ayrıca kaldırmanız gerekir `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` ve başvurular `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` için yeniden hedeflendi Excel projeleri sınıftan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Visual Studio bu öznitelik veya sınıf başvurusu, kaldırmaz.  
  
## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Excel projeleri ExcelLocale1033 özniteliğini kaldırın  
 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` Hedefleyen çözümler için kullanılan Office çalışma zamanı için Visual Studio 2010 Araçları kısmından kaldırılan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Ortak dil çalışma zamanı (CLR) [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve daha sonra her zaman geçiş yerel kimliği1033 Excel nesne modeline ve artık bu öznitelik bu davranışı devre dışı bırakabilirsiniz. Daha fazla bilgi için [Genelleştirme ve yerelleştirme Excel çözümlerini](../vsto/globalization-and-localization-of-excel-solutions.md).  
  
### <a name="to-remove-the-excellocale1033attribute"></a>ExcelLocale1033Attribute kaldırmak için  
  
1.  Projeyi Visual Studio'da Aç açın **Çözüm Gezgini**.  
  
2.  Altında **özellikleri** düğümü (C#) veya **Projem** (Visual Basic) düğümünü AssemblyInfo kod dosyası Kod Düzenleyicisi'nde açmak için çift tıklayın.  
  
    > [!NOTE]  
    >  Visual Basic projelerinde tıklamanız **tüm dosyaları göster** düğmesine **Çözüm Gezgini** AssemblyInfo kod dosyasını görmek için.  
  
3.  Bulun `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` ve dosyanın kaldırmak veya yorum çıkarın.  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Bir başvuru ExcelLocal1033Proxy sınıfı Kaldır  
 Microsoft Office sistemi için Microsoft Visual Studio 2005 araçları kullanılarak oluşturulmuş projeler örneği Excel <xref:Microsoft.Office.Interop.Excel.Application> kullanarak nesne `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` sınıfı. Bu sınıf hedefleyen çözümler için kullandığı Office çalışma zamanı için Visual Studio 2010 Araçları bölümünden kaldırıldı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Bu nedenle, kaldırın veya bu sınıf başvuran kod satırı açıklama satırı yapın.  
  
### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy sınıfı başvuruyu kaldırmak için  
  
1.  Projeyi Visual Studio'da açın ve ardından açın **Çözüm Gezgini**.  
  
2.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın *ThisAddIn.cs* (için C#) veya *ThisAddIn.vb* (için Visual Basic için) ve ardından **kodu görüntüle** .  
  
3.  Kod Düzenleyicisi'nde, içinde `VSTO generated code` bölgesi, kaldırmak veya kodunun aşağıdaki satırı açıklama satırı yapın.  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> GetVstoObject ve HasVstoObject yöntemlerini kullanan kodu güncelleştirme  
 .NET Framework 3. 5'i hedefleyen projelerde `GetVstoObject` veya `HasVstoObject` projenize aşağıdaki yerel nesne genişletme yöntemi olarak yöntemleri kullanılabilir: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, veya <xref:Microsoft.Office.Interop.Excel.ListObject>. Bu yöntemi çağırdığınızda, bir parametre gerekmez. Aşağıdaki kod örneği, bir sözcük VSTO .NET Framework 3. 5'i hedefleyen eklentinin GetVstoObject yöntemini kullanmayı gösterir.  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bu yöntemler aşağıdaki yollardan biriyle erişmek için kodunuzu değiştirmeniz gerekir:  
  
- Bu yöntemler genişletme yöntemlerini üzerinde erişmeye devam edebilirsiniz <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, veya <xref:Microsoft.Office.Interop.Excel.ListObject> nesneleri. Bununla birlikte, artık tarafından döndürülen nesne geçmelidir `Globals.Factory` bu yöntemlere yapılan özelliği.  
  
  ```vb  
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
  ```  
  
  ```csharp  
  Microsoft.Office.Tools.Word.Document vstoDocument =   
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
  ```  
  
- Alternatif olarak, bu yöntem tarafından döndürülen nesne üzerinde erişebilirsiniz `Globals.Factory` özelliği. Bu yöntemler bu şekilde eriştiğinizde, yönteme genişletmek istediğiniz yerel nesne geçmesi gerekir.  
  
  ```vb  
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
  ```  
  
  ```csharp  
  Microsoft.Office.Tools.Word.Document vstoDocument =   
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
  ```  
  
  Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
##  <a name="generatedclasses"></a> Belge düzeyinde projelerde oluşturulan sınıfların örneklerini kullanan kodu güncelleştirme  
 .NET Framework 3.5 hedefleyen belge düzeyinde projelerde aşağıdaki sınıflarda projelerde oluşturulan sınıflar türetilen [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
  ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya da sonraki içindeki türleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yukarıda listelenen, sınıf yerine arayüzleridir. Oluşturulan projelerde hedefleyen sınıfları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra aşağıdaki yeni sınıflar türetilen [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
  Kodu, projenizdeki türetildiği temel sınıf olarak oluşturulan sınıflardan birini örneğine başvuruyorsa, kodu değiştirmeniz gerekir.  
  
  Örneğin, .NET Framework 3. 5'i hedefleyen bir Excel çalışma kitabı projesinde, oluşturulan örneklerinde bazı işini gerçekleştiren bir yardımcı yöntem olabilir `Sheet` *n* projeniz içerisindeki sınıflar.  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)  
    ' Do something to the worksheet object.  
End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)  
{  
    // Do something to the worksheet object.  
}  
```  
  
 Proje için hedefi yeniden belirlerseniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra aşağıdaki değişikliklerden birini kodunuza yapmanız gerekir:  
  
-   Çağıran herhangi bir kod değiştirme `DoSomethingToSheet` geçirilecek yöntemi <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> özelliği bir <xref:Microsoft.Office.Tools.Excel.WorksheetBase> projenizdeki nesne. Bu özellik döndürür bir <xref:Microsoft.Office.Tools.Excel.Worksheet> nesne.  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   Değiştirme `DoSomethingToSheet` beklenir yöntem parametresi bir <xref:Microsoft.Office.Tools.Excel.WorksheetBase> bunun yerine nesne.  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)  
        ' Do something to the worksheet object.  
    End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)  
    {  
        // Do something to the worksheet object.  
    }  
    ```  
  
##  <a name="winforms"></a> Belgelerindeki Windows Forms denetimleri kullanan kodu güncelleştirme  
 Eklemelisiniz bir **kullanarak** (C#) veya **içeri aktarmalar** for deyimi (Visual Basic) <xref:Microsoft.Office.Tools.Excel> veya <xref:Microsoft.Office.Tools.Word> Windows eklemek için denetimleri özelliğini kullanan hiçbir kod dosyasının en üstüne ad alanı Belge veya çalışma sayfası denetimlerini programlı olarak oluşturur.  
  
 .NET Framework 3.5, Windows Forms denetimleri ekleme yöntemleri hedefleyen projelerde (gibi `AddButton` yöntemi) tanımlanan <xref:Microsoft.Office.Tools.Excel.ControlCollection> ve <xref:Microsoft.Office.Tools.Word.ControlCollection> sınıfları.  
  
 ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya da daha sonra bu yöntemleri denetimleri özelliği kullanılabilir genişletme yöntemleri. Bu uzantı yöntemleri kullanmak için yöntemleri kullanmak kod dosyası olmalıdır bir **kullanarak** veya **içeri aktarmalar** bildirimi <xref:Microsoft.Office.Tools.Excel> veya <xref:Microsoft.Office.Tools.Word> ad alanı. Bu bildirimi hedefleyen yeni projelerde otomatik olarak oluşturulan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri. Projeyi yeniden hedeflediğinizde eklemelisiniz ancak, bu deyimi otomatik olarak projelerinde hedefleyen .NET Framework 3.5 eklenmez.  
  
 Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="ccevents"></a> Word içerik denetim olaylarını işleme kodunu güncelleştirme  
 .NET Framework 3. 5'i hedefleyen projelerde, Word içerik denetimleri olayları genel tarafından işlenen <xref:System.EventHandler%601> temsilci. ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bu olaylar diğer temsilcileri tarafından işlenir.  
  
 Word içerik denetimi olayları ve hedefleyen projelerde bunlarla ilişkili temsilciler aşağıdaki tabloda listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri.  
  
|Olay|Kullanılacak temsilci [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve sonraki projeleri|  
|-----------| - |  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> OLEObject ve OLEControl sınıfları kullanan kodu güncelleştirme  
 .NET Framework 3. 5'i hedefleyen projelerde, özel denetimler (örneğin, Windows Forms kullanıcı denetimleri) bir belge veya çalışma sayfasına ekleyebilirsiniz `Microsoft.Office.Tools.Excel.OLEObject` ve `Microsoft.Office.Tools.Word.OLEControl` sınıfları.  
  
 ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bu sınıflar tarafından değiştirilmiştir <xref:Microsoft.Office.Tools.Excel.ControlSite> ve <xref:Microsoft.Office.Tools.Word.ControlSite> arabirimleri. Başvuran bir kodu değiştirmeniz gerekir `Microsoft.Office.Tools.Excel.OLEObject` ve `Microsoft.Office.Tools.Word.OLEControl` başvuracak şekilde <xref:Microsoft.Office.Tools.Excel.ControlSite> ve <xref:Microsoft.Office.Tools.Word.ControlSite>. Yeni adlar dışında bu denetimler, .NET Framework 3. 5'i hedefleyen projelerde aynı şekilde davranır.  
  
 Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="itemproperty"></a> Controls.Item(Object) özelliği kullanan kodu güncelleştirme  
 .NET Framework 3. 5'i hedefleyen projelerde Microsoft.Office.Tools.Excel.Worksheet.Controls Item(Object) özelliğini kullanabilirsiniz veya `Microsoft.Office.Tools.Excel.Worksheet.Controls` belge veya çalışma belirtilen bir denetim olup olmadığını belirlemek için koleksiyon.  
  
 ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bu koleksiyonlara Item(Object) özelliği kaldırıldı. Belge veya çalışma belirli bir denetimi içerip içermediğini belirlemek için Contains(System.Object) yöntemi kullanın. <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> veya <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> koleksiyonu yerine.  
  
 Belgeler ve çalışma denetimlerini toplama hakkında daha fazla bilgi için bkz. [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="collections"></a> CollectionBase'den türetilen koleksiyonları kullanan kodu güncelleştirme  
 .NET Framework 3. 5'i hedefleyen projelerde'nın çeşitli koleksiyon türlerini [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] öğesinden türetilen <xref:System.Collections.CollectionBase> gibi sınıf `Microsoft.Office.Tools.SmartTagCollection`, `Microsoft.Office.Tools.Excel.ControlCollection`, ve `Microsoft.Office.Tools.Word.ControlCollection`.  
  
 ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya da daha sonra bu koleksiyon türleri artık öğesinden türetilen olmayan arabirimleri <xref:System.Collections.CollectionBase>. Bazı üyeleri artık gibi bu koleksiyon türleri üzerinde kullanılabilir <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>, ve <xref:System.Collections.CollectionBase.InnerList%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [İçerik denetimleri](../vsto/content-controls.md)   
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)  
  
  