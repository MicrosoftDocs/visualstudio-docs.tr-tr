---
title: 'İzlenecek yol: bir uygulama sayfasını bir iş akışına ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4bdb01e5cbb45b9986e61a99e18b5984e92d37dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866902"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>İzlenecek yol: bir uygulama sayfasını bir iş akışına ekleme
  Bu izlenecek yol, bir iş akışı projesine bir iş akışından türetilen veriyi görüntüleyen bir uygulama sayfasını nasıl ekleneceğini gösterir. Bu konu başlığı altında açıklanan projede derlemeler [izlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- ASPX uygulama sayfası, bir SharePoint iş akışı projesine ekleniyor.

- İş akışı projeden veri edinme ve bu işleme.

- Uygulama sayfasında bir tablodaki verileri görüntüleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   Desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] ve SharePoint.

-   Visual Studio.

-   Konu başlığı projeyi tamamlamak de [izlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="ammend-the-workflow-code"></a>Ammend iş akışı kodu
 İlk olarak, harcama raporlarını miktarını sonucu sütununun değerini ayarlamak için iş akışına bir kod satırı ekleyin. Bu değer daha sonra harcama raporu Özet hesaplamaya kullanılır.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>İş akışında sonucu sütununun değerini ayarlamak için

1.  Tamamlanmış projeyi konu başlığından yük [izlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) içine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Kodu açık *Workflow1.cs* veya *Workflow1.vb* (bağlı olarak, programlama dili).

3.  Alt kısmına `createTask1_MethodInvoking` yöntemine aşağıdaki kodu ekleyin:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Uygulama sayfası oluşturma
 Ardından, ASPX form projeye ekleyin. Bu formu harcama raporu iş akışı projeden alınan veriler görüntüler. Bunu yapmak için bir uygulama sayfası ekleyeceksiniz. Bir uygulama sayfasını SharePoint sitesindeki diğer sayfalara benzer anlamına gelir, diğer SharePoint sayfaları aynı sayfayı kullanır.

#### <a name="to-add-an-application-page-to-the-project"></a>Bir uygulama sayfasını projeye eklemek için

1.  ExpenseReport projeyi seçin ve ardından, menü çubuğunda, **proje** > **Yeni Öğe Ekle**.

2.  İçinde **şablonları** bölmesinde seçin **uygulama sayfası** Şablonu proje öğesi için varsayılan adı kullanın (**ApplicationPage1.aspx**) ve **Ekle** düğmesi.

3.  İçinde [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1.aspx değiştirin `PlaceHolderMain` aşağıdaki bölümü:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Bu kod sayfası başlığı ile birlikte bir tablo ekler.

4.  Uygulama sayfası başlık değiştirerek ekleme `PlaceHolderPageTitleInTitleArea` aşağıdaki bölümü:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Uygulama sayfası kod
 Ardından, kod harcama raporu Özet uygulama sayfasına ekleyin. Sayfasını açtığınızda, kod ayrılmış harcama limitini aşan expenses SharePoint görev listesinde tarar. Rapor masrafları toplamını birlikte her bir öğe listeler.

#### <a name="to-code-the-application-page"></a>Uygulama sayfası kod

1.  Seçin **ApplicationPage1.aspx** düğümünü ve ardından, menü çubuğunda, **görünümü** > **kod** uygulama sayfası arka plan kod görüntülenecek.

2.  Değiştirin **kullanarak** veya **alma** üst sınıf aşağıdaki deyimleri (bağlı olarak, programlama dili):

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3.  Aşağıdaki kodu ekleyin `Page_Load` yöntemi:

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    >  "TestServer" kodda SharePoint çalıştıran geçerli bir sunucu adı ile değiştirdiğinizden emin olun.

## <a name="test-the-application-page"></a>Uygulama sayfasını sınama
 Ardından, uygulama sayfasına gider verileri doğru şekilde görüntülenip görüntülenmeyeceğini belirler.

#### <a name="to-test-the-application-page"></a>Uygulama sayfasını sınamak için

1. Seçin **F5** çalıştırmak ve SharePoint için projeyi dağıtmak için anahtar.

2. Seçin **giriş** düğmesine ve ardından **paylaşılan belgeler** SharePoint sitesinde paylaşılan belgelerin listesini görüntülemek için Hızlı Başlat çubuğunda bağlantı.

3. Bu örneğin gider raporlarını temsil etmek için bazı yeni belgeler belgelerin listesine seçerek karşıya **belgeleri** bağlantısını **LibraryTools** sayfası ve seçereküstkısmındakisekme **Belgeyi Karşıya Yükle** araç şeridinde düğmesi.

4. Bazı belgeler karşıya yüklenmesinin ardından, seçerek iş akışı örneği **Kitaplığı** bağlantısını **LibraryTools** sayfasını seçerek ve ardından üst kısmındaki sekme **kitaplık ayarları**araç şeridinde düğmesi.

5. İçinde **belge kitaplığı ayarlarını** sayfasında **iş akışı ayarları** bağlantısını **izinler ve Yönetim** bölümü.

6. İçinde **iş akışı ayarları** sayfasında **bir iş akışı Ekle** bağlantı.

7. İçinde **bir iş akışı Ekle** sayfasında **ExpenseReport - Workflow1** iş akışı, iş akışı için bir ad girin **ExpenseTest**, seçin**Sonraki** düğmesi.

    İş akışı ilişkilendirme formu görüntülenir. Harcama sınırı miktarını bildirmek için kullanın.

8. İlişkilendirme biçiminde girin **1000** içine **otomatik onay sınırı** kutusuna ve ardından **iş akışı ilişkilendirme** düğmesi.

9. Seçin **giriş** düğmesini SharePoint giriş sayfasına dönün.

10. Seçin **paylaşılan belgeler** Hızlı Başlat çubuğunda bağlantı.

11. Aşağı açılan okunu görüntülemek için bunu seçin ve ardından karşıya yüklenen belgelerin birini **iş akışları** öğesi.

12. İş akışı başlatma formu görüntülemek için ExpenseTest yanında bir görüntü seçin.

13. İçinde **gider toplam** metin kutusunda, 1000'den büyük bir değer girin ve ardından **başlangıç iş akışı** düğmesi.

     Bildirilen gider ayrılmış harcama miktarı aşarsa, bir görev görev listesine eklenir. Adlı bir sütun **ExpenseTest** değerle **tamamlandı** gider rapor öğesinin paylaşılan belgeler listesinde de eklenir.

14. Diğer belgelerle paylaşılan belgeler listesinde 11-13 adımları yineleyin. (Belgelerin tam sayı önemli değildir.)

15. Aşağıdaki URL'ye bir Web tarayıcısında açarak harcama raporu Özet uygulama sayfası görüntüleme: **http://**<em>SystemName</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Harcama raporu Özet sayfası, tüm ayrılan miktarı aşan gider raporlarını, tarafından aşıldı miktarını ve toplam tutarı tüm raporların listeler.

## <a name="next-steps"></a>Sonraki adımlar
 SharePoint uygulama sayfaları hakkında daha fazla bilgi için bkz: [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

 Visual Studio'da Visual Web Designer aşağıdaki konulardan kullanarak SharePoint sayfası içeriği tasarlama hakkında daha fazla bilgi:

-   [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md).

-   [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Nasıl yapılır: uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)