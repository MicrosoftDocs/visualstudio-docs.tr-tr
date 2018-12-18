---
title: 'İzlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma | Microsoft Docs'
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
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6aafde6fed0a1f1722c2d355499523114aaaa00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873883"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>İzlenecek yol: İlişkilendirme ve başlatma formları ile iş akışı oluşturma
  Bu yönerge, ilişki ve başlatma formlarını kullanımını içeren bir temel sıralı iş akışının nasıl oluşturulacağını gösterir. Öncelikle SharePoint Yöneticisi tarafından (İlişkilendirme formu) ilişkili ve iş akışı (başlatma formu) kullanıcı tarafından yeniden başlatıldığında, bir iş akışına eklenecek parametrelerini etkinleştirme ASPX forms şunlardır.  
  
 Bu izlenecek yolda, burada aşağıdaki gereksinimleri olan bir onay iş akışı gider raporlarını oluşturmak için bir kullanıcının istediği bir senaryosu açıklanmaktadır:  
  
- İş akışı bir listesi ile ilişkili olduğunda yönetici ile bir ilişkilendirme formu dolar sınırı masraf raporları nereye girmeleri istenir.  
  
- Çalışanlar paylaşılan belgeler listesine, Gider raporlarını karşıya yükleme, iş akışını başlatmak ve sonra iş akışı başlatma formu içinde Toplam gider girin.  
  
- Toplam çalışan gider raporu yöneticinin önceden tanımlanmış sınırını aşarsa çalışanın yöneticisine harcama raporlarını onaylamak bir görev oluşturulur. Ancak, bir çalışanın harcama raporu toplam harcama sınırına eşit veya daha az ise, iş akışı Geçmiş listesine bir otomatik onaylı ileti yazılır.  
  
  Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Bir SharePoint liste tanımını sıralı iş akışı projesi oluşturma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- Bir iş akışı zamanlama oluşturuluyor.  
  
- İşleme iş akışı etkinlik olayları.  
  
- İş akışı ilişkilendirme ve başlatma formlarını oluşturuluyor.  
  
- İş akışı ilişkilendirme.  
  
- İş akışı el ile başlatma.  
  
> [!NOTE]  
>  Bu kılavuzda bir sıralı iş akışı projesi kullansa da, durum makine iş akışları için aynı işlemidir.  
>   
>  Ayrıca, bilgisayarınız bazıları için farklı adlar veya konumlar gösterebilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanıcı arabirimi öğeleri aşağıdaki yönergeleri izleyin. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sizdeki sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] ve SharePoint.  
  
-   Visual Studio.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Bir SharePoint sıralı iş akışı projesi oluşturma
 İlk olarak, bir sıralı iş akışı projesinde oluşturmak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Bir sıralı iş akışı son etkinlik tamamlanana kadar sırayla yürütülen bir dizi adımı ' dir. Bu yordamda, paylaşılan belgeler SharePoint listesine uygulayan bir sıralı iş akışı oluşturacaksınız. İş akışının Sihirbazı iş akışı sitesi veya liste tanımı ile ilişkilendirmenizi sağlar ve iş akışını başlatacak belirlerken olanak tanır.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Bir SharePoint sıralı iş akışı projesi oluşturma  
  
1.  Menü çubuğunda, **dosya** > **yeni** > **proje** görüntülenecek **yeni proje** iletişim kutusu.  
  
2.  Genişletin **SharePoint** ya da düğümünde **Visual C#** veya **Visual Basic**ve ardından **2010** düğümü.  
  
3.  İçinde **şablonları** bölmesinde seçin **SharePoint 2010 projesi** proje şablonu.  
  
4.  İçinde **adı** kutusuna **ExpenseReport** seçip **Tamam** düğmesi.  
  
     **SharePoint Özelleştirme Sihirbazı** görünür.  
  
5.  İçinde **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında **Grup çözümü olarak Dağıt** seçenek düğmesini ve ardından **son** kabul etmek için düğme güven düzeyi ve varsayılan site.  
  
     Bu adım, çözümünün güven düzeyi de iş akışı projeleri için kullanılabilir tek seçenek olan Grup çözümü olarak ayarlar.  
  
6.  İçinde **Çözüm Gezgini**, proje düğümünü seçin.  
  
7.  Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
8.  Ya da altında **Visual C#** veya **Visual Basic**, genişletme **SharePoint** düğümünü seçip **2010** düğümü.  
  
9. İçinde **şablonları** bölmesinde seçin **sıralı iş akışı (yalnızca Grup çözümü)** şablonu seçip **Ekle** düğmesi.  
  
     **SharePoint Özelleştirme Sihirbazı** görünür.  
  
10. İçinde **hata ayıklama için iş akışı adını** sayfasında, varsayılan adı kabul edin (**ExpenseReport - Workflow1**). Varsayılan iş akışı şablonu türü değeri tutun (**liste iş akışı)**. Seçin **sonraki** düğmesi.  
  
11. İçinde **otomatik olarak hata ayıklama oturumunda iş akışını ilişkilendirmek için Visual Studio ister misiniz?** sayfasında, bu işaretlenirse, iş akışı şablonu otomatik olarak ilişkilendirir kutuyu temizleyin.  
  
     Bu adım, el ile ilişkilendirme formu görüntüleyen bir iş akışı daha sonra paylaşılan belgeler listesiyle ilişkilendirmenizi sağlar.  
  
12. Seçin **son** düğmesi.  
  
## <a name="add-an-association-form-to-the-workflow"></a>İş akışı ilişkilendirme formu Ekle
 Ardından, oluşturun bir. SharePoint Yöneticisi, iş akışını önce bir harcama rapor belgesi ilişkilendirir. görüntülenen ASPX ilişkilendirme formu.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>İş akışı ilişkilendirme formu eklemek için  
  
1.  Seçin **Workflow1** düğümünde **Çözüm Gezgini**.  
  
2.  Menü çubuğunda, **proje** > **Yeni Öğe Ekle** görüntülenecek **Yeni Öğe Ekle** iletişim kutusu.  
  
3.  İletişim kutusu ağaç görünümünde genişletin **Visual C#** veya **Visual Basic** genişletin (Proje dilinizi bağlı olarak), **SharePoint** düğümünün seçin**2010** düğümü.  
  
4.  Şablonlar listesinde seçin **iş akışı ilişkilendirme formu** şablonu.  
  
5.  İçinde **adı** metin kutusuna **ExpenseReportAssocForm.aspx**.  
  
6.  Seçin **Ekle** projeye form ekleme düğmesi.  
  
## <a name="designing-and-coding-the-association-form"></a>Tasarlama ve ilişkilendirme formu kodlama
 Bu yordamda, denetimleri ile kod ekleyerek ilişkilendirme formu için işlevsellik sunar.  
  
#### <a name="to-design-and-code-the-association-form"></a>Tasarım ve kod ilişkilendirme formu  
  
1.  İlişkilendirme formu (ExpenseReportAssocForm.aspx), bulun `asp:Content` sahip öğe `ID="Main"`.  
  
2.  Doğrudan ilk satırının sonra içerik bu öğesinde bir etiket ve harcama onay sınırını ister metin oluşturmak için aşağıdaki kodu ekleyin (*AutoApproveLimit*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Genişletin **ExpenseReportAssocForm.aspx** dosyası **Çözüm Gezgini** bağımlı dosyalarından görüntülenecek.  
  
    > [!NOTE]  
    >  Projenizi ise [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], seçmeniz gerekir **görünümü tüm dosyaları** bu adımı gerçekleştirmek için düğme.  
  
4.  ExpenseReportAssocForm.aspx dosyası için kısayol menüsünü açın ve seçin **kodu görüntüle**.  
  
5.  Değiştirin `GetAssociationData` yöntemiyle:  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## <a name="add-an-initiation-form-to-the-workflow"></a>İş akışı başlatma formu Ekle
 Ardından, kullanıcılar, Gider raporlarını karşı iş akışını çalıştırdığınızda görüntülenen başlatma formu oluşturun.  
  
#### <a name="to-create-an-initiation-form"></a>Başlatma formu oluşturma  
  
1.  Seçin **Workflow1** düğümünde **Çözüm Gezgini**.  
  
2.  Menü çubuğunda, **proje** > **Yeni Öğe Ekle** görüntüleme **Yeni Öğe Ekle** iletişim kutusu.  
  
3.  İletişim kutusu ağaç görünümünde genişletin **Visual C#** veya **Visual Basic** genişletin (Proje dilinizi bağlı olarak), **SharePoint** düğümünün seçin**2010** düğümü.  
  
4.  Şablonlar listesinde seçin **iş akışı başlatma formu** şablonu.  
  
5.  İçinde **adı** metin kutusuna **ExpenseReportInitForm.aspx**.  
  
6.  Seçin **Ekle** projeye form ekleme düğmesi.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Tasarlama ve başlatma formu kodlama
 Ardından, denetimleri ile kod ekleyerek başlatma formu için işlevsellik sunar.  
  
#### <a name="to-code-the-initiation-form"></a>Kodu başlatma formu  
  
1.  Başlatma formu (ExpenseReportInitForm.aspx), bulun `asp:Content` öğesini içeren `ID="Main"`.  
  
2.  Doğrudan içerik bu öğesinde ilk satırından sonra bir etiket ve onay harcama sınırını görüntüler metin oluşturmak için aşağıdaki kodu ekleyin (*AutoApproveLimit*) ilişkilendirme formu ve başka bir etiket girilen ve Harcama toplamı istemek için metin (*ExpenseTotal*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Genişletin **ExpenseReportInitForm.aspx** dosyası **Çözüm Gezgini** bağımlı dosyalarından görüntülenecek.  
  
4.  ExpenseReportInitForm.aspx dosyası için kısayol menüsünü açın ve seçin **kodu görüntüle**.  
  
5.  Değiştirin `Page_Load` aşağıdaki örnekle yöntemi:  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  Değiştirin `GetInitiationData` aşağıdaki örnekle yöntemi:  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## <a name="cutomize-the-workflow"></a>Özeleştirme iş akışı
 Ardından, iş akışını özelleştirin. Daha sonra iki tür iş akışına ilişkilendireceksiniz.  
  
#### <a name="to-customize-the-workflow"></a>İş akışını özelleştirme  
  
1.  İş akışı projesinde Workflow1 açarak iş akışı Tasarımcısı'nda görüntülenir.  
  
2.  İçinde **araç kutusu**, genişletme **Windows iş akışı v3.0** düğümünü bulun **Ifelse** etkinlik.  
  
3.  Bu etkinlik, iş akışı için aşağıdaki adımlardan birini uygulayarak ekleyin:  
  
    -   Kısayol menüsünü açın **Ifelse** etkinliği seçin **kopyalama**, altındaki kısayol menüsünü açın **onWorkflowActivated1** iş akışı tasarımcısında etkinlik ve ardından **Yapıştır**.  
  
    -   Sürükleme **Ifelse** etkinliğinden **araç kutusu**ve altındaki satıra bağlayın **onWorkflowActiviated1** iş akışı tasarımcısında etkinlik.  
  
4.  Araç kutusunda genişletin **SharePoint iş akışı** düğümünü bulun **CreateTask** etkinlik.  
  
5.  Bu etkinlik, iş akışı için aşağıdaki adımlardan birini uygulayarak ekleyin:  
  
    -   Kısayol menüsünü açın **CreateTask** etkinliği seçin **kopyalama**, iki biri için kısayol menüsünü açın **etkinlikleri Buraya Bırak** içindeki alanları  **IfElseActivity1** iş akışı Tasarımcısı'nda seçip **Yapıştır**.  
  
    -   Sürükleme **CreateTask** etkinliğinden **araç kutusu** iki birini üzerine **etkinlikleri Buraya Bırak** içindeki alanları **IfElseActivity1**.  
  
6.  İçinde **özellikleri** penceresi, özellik değeri girin *taskToken* için **CorrelationToken** özelliği.  
  
7.  Genişletin **CorrelationToken** artı işaretini seçerek özelliği (![TreeView artı](../sharepoint/media/plus.gif "TreeView artı")) yanında.  
  
8.  Aşağı açılan oku seçin **OwnerActivityName** alt özellik ve ayarlama *Workflow1* değeri.  
  
9. Seçin **Taskıd** özelliği ve ardından üç noktayı seçin (![ASP.NET Mobil Tasarımcısı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcısı elips")) görüntülemekiçindüğmeyi**Bağlama özelliği** iletişim kutusu.  
  
10. Seçin **bağlamak için yeni bir üye** sekmesini, **alanı oluştur** seçenek düğmesini ve ardından **Tamam** düğmesi.  
  
11. seçin **TaskProperties** özelliği ve ardından üç noktayı seçin (![ASP.NET Mobil Tasarımcısı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcısı elips")) düğmesini görüntülemekiçin **Özelliği bağlamak** iletişim kutusu.  
  
12. Seçin **bağlamak için yeni bir üye** sekmesini, **alanı oluştur** seçenek düğmesini ve ardından **Tamam** düğmesi.  
  
13. İçinde **araç kutusu**, genişletme **SharePoint iş akışı** düğümünü bulun **LogToHistoryListActivity** etkinlik.  
  
14. Bu etkinlik, iş akışı için aşağıdaki adımlardan birini uygulayarak ekleyin:  
  
    -   Kısayol menüsünü açın **LogToHistoryListActivity** etkinliği seçin **kopyalama**, diğeri için kısayol menüsünü açın **etkinlikleri Buraya Bırak** ucunuzu**IfElseActivity1** iş akışı Tasarımcısı'nda seçip **Yapıştır**.  
  
    -   Sürükleme **LogToHistoryListActivity** etkinliğinden **araç kutusu**, diğer bırakın **etkinlikleri Buraya Bırak** ucunuzu **IfElseActivity1** .  
  
## <a name="add-code-to-the-workflow"></a>İş akışı için kod ekleyin
 Ardından, işlevsellik sağlamak için iş akışı için kod ekleyin.  
  
#### <a name="to-add-code-to-the-workflow"></a>İş akışı kodu eklemek için  
  
1.  Kısayol menüsünü açın **createTask1** iş akışı tasarımcısında etkinlik seçip **kodu görüntüle**.  
  
2.  Aşağıdaki yöntemi ekleyin:  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  Kod içinde `somedomain\\someuser` kendisi için bir görev oluşturulur, gibi bir etki alanı ve kullanıcı adı ile "`Office\\JoeSch`". Test etmek için ile geliştirdiğiniz hesabı kullanmak en kolay yoldur.  
  
3.  Aşağıda `MethodInvoking` yöntemi, aşağıdaki örnekte ekleyin:  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  İş Akışı Tasarımcısı'nda **ifElseBranchActivity1** etkinlik.  
  
5.  İçinde **özellikleri** penceresinde, aşağı açılan oku seçin **koşul** özelliği ve ardından *kod koşulu* değeri.  
  
6.  Genişletin **koşul** artı işaretini seçerek özelliği (![TreeView artı](../sharepoint/media/plus.gif "TreeView artı")) yanında ve ardından değerini ayarlamak *checkApprovalNeeded* .  
  
7.  İş akışı tasarımcısında kısayol menüsünü açın **logToHistoryListActivity1** etkinlik ve ardından **oluşturmak işleyicileri** için boş bir metodun üretileceği `MethodInvoking` olay.  
  
8.  Değiştirin `MethodInvoking` kodu şu kodla:  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. Seçin **F5** programda hata ayıklamak için anahtar.  
  
     Bu uygulamayı derler, bu paketler, bunu dağıtan, özelliklerini etkinleştirir, geri dönüştüren [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] uygulama havuzu ve tarayıcı konumda belirtilen sonra başlar **Site URL'si** özelliği.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Belge listesi için iş akışını ilişkilendirme
 Ardından, iş akışı ilişkilendirme formu ile iş akışı ilişkilendirme görüntülemek **SharedDocuments** SharePoint sitesinde listesi.  
  
#### <a name="to-associate-the-workflow"></a>İş akışını ilişkilendirmek için  
  
1.  Seçin **paylaşılan belgeler** Hızlı Başlat çubuğunda bağlantı.  
  
2.  Seçin **Kitaplığı** bağlantısını **Kütüphane Araçları** sekmesine ve ardından **kitaplık ayarları** Şerit düğmesi.  
  
3.  İçinde **izinler ve Yönetim** bölümünde, seçin **iş akışı ayarları** bağlamak ve ardından **bir iş akışı Ekle** bağlantısını **işakışları** sayfası.  
  
4.  İş Akışı Ayarları sayfasında üst listeden seçin **ExpenseReport - Workflow1** şablonu.  
  
5.  Sonraki alanına **ExpenseReportWorkflow** seçip **sonraki** düğmesi.  
  
     Bu iş akışı ile ilişkilendirir **paylaşılan belgeler** listelemek ve iş akışı ilişkilendirme formu görüntüler.  
  
6.  İçinde **otomatik onay sınırı** metin kutusuna **1200** seçip **iş akışı ilişkilendirme** düğmesi.  
  
## <a name="start-the-workflow"></a>İş akışını Başlat
 Ardından, belgelerde birine iş akışını ilişkilendirmek **paylaşılan belgeler** iş akışı başlatma formu görüntülemek için liste.  
  
#### <a name="to-start-the-workflow"></a>İş akışını başlatmak için  
  
1.  SharePoint sayfasında **giriş** düğmesi.  
  
2.  Seçin **paylaşılan belgeler** Hızlı Başlat çubuğunda görüntülenecek bağlantı **paylaşılan belgeler** listesi.  
  
3.  Seçin **belgeleri** bağlantısını **Kütüphane Araçları** sekmesinde sayfanın en üstündeki ve ardından **belge Yükle** içine yeni bir belge yüklemek için Şeritteki düğme **Paylaşılan belgeler** listesi.  
  
4.  İçinde **belge Yükle** iletişim kutusunda **Gözat** düğmesi, herhangi bir belge dosya seçin, **açık** düğmesine ve ardından **Tamam** düğmesi.  
  
     Bu iletişim kutusunda belge için ayarları değiştirmek, ancak bunları seçerek varsayılan değerlerinde bırakın **Kaydet** düğmesi.  
  
5.  Karşıya yüklenen belge seçin, görünür ve ardından açılan liste okunu **iş akışları** öğesi.  
  
6.  ExpenseReportWorkflow yanında bir görüntü seçin.  
  
     Bu iş akışı başlatma formu görüntüler. (Değer görüntülenen Not **otomatik onay sınırı** kutusu, salt okunur ilişkilendirme biçiminde girildiğinden.)  
  
7.  İçinde **gider toplam** metin kutusuna **1600**ve ardından **başlangıç iş akışı** düğmesi.  
  
     Bu görüntüler **paylaşılan belgeler** yeniden listeleyin. Adlı yeni bir sütun **ExpenseReportWorkflow** değerle **tamamlandı** iş akışını kullanmaya yeni öğesine eklenir.  
  
8.  Karşıya yüklenen belge yanındaki aşağı açılan oku seçin ve ardından **iş akışları** iş akışı durumu sayfasını görüntülemek için öğesi. Seçin **tamamlandı** altındaki **tamamlanan iş akışı**. Görevi altında listelenen **görevleri** bölümü.  
  
9. Görev ayrıntılarını görüntülemek için görevin başlığını seçin.  
  
10. Geri Git **SharedDocuments** listelemek ve aynı belgede ya da farklı bir kullanarak iş akışını yeniden başlatın.  
  
11. Başlatma sayfasında ilişkilendirme sayfada girilen tutar küçük veya ona eşit bir miktar girin (**1200**).  
  
     Böyle bir durumda geçmişi listesindeki bir girdinin yerine bir görev oluşturulur. Giriş görüntüler **iş akışı geçmişi** bölümü iş akışı durumu sayfası. İletide Not **sonucu** geçmişi olay sütunu. Girilen metni içeren `logToHistoryListActivity1.MethodInvoking` otomatik olarak onaylandı miktar içeren olay.  
  
## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan iş akışı şablonları oluşturma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   SharePoint iş akışı hakkında daha fazla bilgi için bkz: [Windows SharePoint Services iş akışlarında](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint iş akışı çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [İzlenecek yol: bir uygulama sayfasını bir iş akışına ekleme](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
