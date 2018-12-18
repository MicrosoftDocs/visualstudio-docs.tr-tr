---
title: 'İzlenecek yol: Oluşturma ve bir SharePoint iş akışı çözümü hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c254f6f3e044f938ed2749567d66ee7a313081e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42626494"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>İzlenecek yol: Oluşturma ve bir SharePoint iş akışı çözümü hata ayıklama
  Bu izlenecek yol, temel sıralı iş akışı şablonunun nasıl oluşturulacağını gösterir. İş akışı, bir belgeyi gözden olup olmadığını belirlemek için paylaşılan belge kitaplığı özelliğini denetler. Belgeyi gözden, iş akışı tamamlanır.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Bir SharePoint liste tanımını sıralı iş akışı projesi oluşturma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   İş akışı etkinlikleri oluşturuluyor.  
  
-   İşleme iş akışı etkinlik olayları.  
  
> [!NOTE]  
>  Bu kılavuzda bir sıralı iş akışı projesi kullansa da, bir Durum makinesi iş akışı projesi için işlem aynıdır.  
>   
>  Ayrıca, bilgisayarınız Visual Studio kullanıcı bazıları için farklı adlar veya konumlar arabirimi öğeleri aşağıdaki yönergelerde yer gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Microsoft Windows ve SharePoint sürümleri desteklenir.  
  
-   Visual Studio.  
  
## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint paylaşılan belge kitaplığı'na özellikleri ekleyin
 Belgelerde durumunu izlemek için **paylaşılan belgeler** kitaplığı, biz oluşturacaktır paylaşılan belgeler için üç yeni özellik SharePoint sitemize: `Status`, `Assignee`, ve `Review Comments`. Bu özellikleri tanımlarız **paylaşılan belgeler** kitaplığı.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Paylaşılan SharePoint özelliklerini eklemek için kitaplığı belgeleri  
  
1.  Http:// gibi bir SharePoint sitesine açın\<sistem adı > / bir Web tarayıcısında SitePages/Home.aspx.  
  
2.  Hızlı Başlat çubuğunda **SharedDocuments**.  
  
3.  Seçin **Kitaplığı** üzerinde **Kütüphane Araçları** Şerit ve ardından **sütun oluşturma** yeni bir sütun oluşturmak için Şeritteki düğme.  
  
4.  Sütun adı **belge durumu**, kendi tür kümesine **seçenek (arasından menü)**, aşağıdaki üç seçenek belirtin ve ardından **Tamam** düğmesi:  
  
    -   **Gözden geçirme gerekli**  
  
    -   **Gözden geçirme tamamlandı**  
  
    -   **İstenen değişiklikler**  
  
5.  İki sütun daha oluşturun ve bunları **atanan** ve **gözden geçirme**. Tek metin satırı olarak atanan sütun türü ve gözden geçirme sütun türü birden çok metin satırı ayarlayın.  
  
## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Bir kullanıma gerek kalmadan düzenlenecek belgelere etkinleştir
 İş akışı şablonu belgeleri gözden geçirin gerek kalmadan düzenleyebileceğiniz, test etmek daha kolaydır. Sonraki yordamda, etkinleştirmek için SharePoint sitesi yapılandırın.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Kullanıma almadan düzenlenecek belgeleri etkinleştirmek için  
  
1.  Hızlı Başlat çubuğunda **paylaşılan belgeler** bağlantı.  
  
2.  Üzerinde **Kütüphane Araçları** şeridinden **Kitaplığı** sekmesine ve ardından **kitaplık ayarları** görüntülemek için düğmeyi **belge kitaplığı ayarlarını** sayfası.  
  
3.  İçinde **genel ayarlar** bölümünde, seçin **sürüm oluşturma ayarları** görüntülemek için bağlantıyı **sürüm oluşturma ayarları** sayfası.  
  
4.  Doğrulayın ayarı **düzenlenmeden önce kullanıma alınması belgelerin gerektir** olduğu **Hayır**. Yüklü değilse, değiştirmek **Hayır** seçip **Tamam** düğmesi.  
  
5.  Tarayıcıyı kapatın.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Bir SharePoint sıralı iş akışı projesi oluşturma
 Bir sıralı iş akışı son etkinlik tamamlanana kadar sırayla yürüten adımları kümesidir. Bu yordamda, paylaşılan belgeler listemize uygulanacak bir sıralı iş akışı oluşturacağız. İş akışı Sihirbazı iş akışı site tanımını veya liste tanımı ile ilişkilendirmenizi sağlar ve iş akışını başlatacak belirlerken olanak tanır.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Bir SharePoint sıralı iş akışı projesi oluşturma  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Menü çubuğunda, **dosya** > **yeni** > **proje** görüntülenecek **yeni proje** iletişim kutusu.  
  
3.  Genişletin **SharePoint** ya da düğümünde **Visual C#** veya **Visual Basic**ve ardından **2010** düğümü.  
  
4.  İçinde **şablonları** bölmesinde seçin **SharePoint 2010 projesi** şablonu.  
  
5.  İçinde **adı** kutusuna **MySharePointWorkflow** seçip **Tamam** düğmesi.  
  
     **SharePoint Özelleştirme Sihirbazı** görünür.  
  
6.  İçinde **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında **Grup çözümü olarak Dağıt** seçenek düğmesini ve ardından **son** kabul etmek için düğme güven düzeyi ve varsayılan site.  
  
     Bu adım çözümünün güven düzeyi Grup çözümü iş akışı projeleri için kullanılabilir tek seçenek olarak ayarlar. Daha fazla bilgi için [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  İçinde **Çözüm Gezgini**, proje düğümünü seçin ve ardından, menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
8.  Ya da altında **Visual C#** veya **Visual Basic**, genişletme **SharePoint** düğümünü seçip **2010** düğümü.  
  
9. İçinde **şablonları** bölmesinde seçin **sıralı iş akışı (yalnızca Grup çözümü)** şablonu seçip **Ekle** düğmesi.  
  
     **SharePoint Özelleştirme Sihirbazı** görünür.  
  
10. İçinde **hata ayıklama için iş akışı adını** sayfasında, varsayılan adı kabul edin (**MySharePointWorkflow - Workflow1**). Varsayılan iş akışı şablonu türü değeri tutun **liste iş akışı**ve ardından **sonraki** düğmesi.  
  
11. İçinde **otomatik olarak hata ayıklama oturumunda iş akışını ilişkilendirmek için Visual Studio ister misiniz?** sayfasında **sonraki** tüm varsayılan ayarları kabul etmek için düğme.  
  
     Bu adım, otomatik olarak iş akışı paylaşılan belgeler kitaplığı ile ilişkilendirir.  
  
12. İçinde **iş akışınızın başlama koşullarını belirtin** sayfasında, varsayılan seçenekleri seçili bırakın **nasıl iş akışı başlatmak için istediğinize?** seçin ve bölüm **Son** düğmesi.  
  
     Bu sayfa, iş akışı başladığında belirtmenize olanak sağlar. Bir kullanıcı el ile SharePoint veya iş akışının ilişkili olduğu bir öğe oluşturulduğunda başladığında varsayılan olarak, iş akışı otomatik olarak ya da başlar.  
  
## <a name="create-workflow-activities"></a>İş akışı etkinlikleri oluşturun
 İş akışı içeren bir veya daha fazla *etkinlikleri* gerçekleştirilecek eylemler temsil eder. Bir iş akışı etkinlikleri düzenlemek için iş akışı Tasarımcısı'nı kullanın. Bu yordamda, iki etkinlikleri iş akışına ekleyeceğiz: HandleExternalEventActivity ve OnWorkFlowItemChanged. Bu etkinlikler belgeleri gözden geçirme durumu izleme **paylaşılan belgeler** listesi  
  
#### <a name="to-create-workflow-activities"></a>İş akışı etkinlikleri oluşturmak için  
  
1.  İş akışı iş akışı Tasarımcısı'nda görüntülenmesi gerekir. Yüklü değilse, ya da açık **Workflow1.cs** veya **Workflow1.vb** içinde **Çözüm Gezgini**.  
  
2.  Tasarımcısı'nda **OnWorkflowActivated1** etkinlik.  
  
3.  İçinde **özellikleri** penceresinde girin **onWorkflowActivated** yanındaki **çağrılan** özelliği ve ardından Enter tuşuna basın.  
  
     Kod Düzenleyicisi açılır ve onWorkflowActivated adlı bir olay işleyicisi yöntemi Workflow1 kod dosyasına eklenir.  
  
4.  Geçiş iş akışı tasarımcıya geri dönün, araç kutusunu açın ve ardından **Windows iş akışı v3.0** düğümü.  
  
5.  İçinde **Windows iş akışı v3.0** düğümünün **araç kutusu**, aşağıdaki adımlardan birini gerçekleştirin:  
  
    1.  Kısayol menüsünü açın **sırada** etkinliğini seçip **kopyalama**. İş Akışı Tasarımcısı'nda altındaki kısayol menüsünü açın **onWorkflowActivated1** etkinliğini seçip **Yapıştır**.  
  
    2.  Sürükle **sırada** etkinliğinden **araç kutusu** iş akışı Tasarımcısı için etkinlik altındaki bağlanın **onWorkflowActivated1** etkinlik.  
  
6.  Seçin **WhileActivity1** etkinlik.  
  
7.  İçinde **özellikleri** penceresinde **koşul** kod koşulu.  
  
8.  Genişletin **koşul** özelliği girin **isWorkflowPending** alt yanındaki **koşul** özelliği ve ardından Enter tuşuna basın.  
  
     Kod Düzenleyicisi açılır ve isWorkflowPending adlı bir yöntem Workflow1 kod dosyasına eklenir.  
  
9. Geçiş iş akışı tasarımcıya geri dönün, araç kutusunu açın ve ardından **SharePoint iş akışı** düğümü.  
  
10. İçinde **SharePoint iş akışı** düğümünün **araç kutusu**, aşağıdaki adımlardan birini gerçekleştirin:  
  
    -   Kısayol menüsünü açın **OnWorkflowItemChanged** etkinliğini seçip **kopyalama**. İş Akışı Tasarımcısı'nda içinde satır için kısayol menüsünü açın **whileActivity1** etkinliğini seçip **Yapıştır**.  
  
    -   Sürükleme **OnWorkflowItemChanged** etkinliğinden **araç kutusu** iş akışı Tasarımcısı için satır içinde etkinlik bağlanın **whileActivity1** etkinlik.  
  
11. Seçin **onWorkflowItemChanged1** etkinlik.  
  
12. İçinde **özellikleri** penceresinde, aşağıdaki tabloda gösterildiği gibi özellikleri ayarlayın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Çağrılır**|**onWorkflowItemChanged**|  
  
## <a name="handle-activity-events"></a>Etkinlik olayları işleme
 Son olarak, belge her etkinlik durumunu denetleyin. Belgeyi gözden, iş akışı sona erer.  
  
#### <a name="to-handle-activity-events"></a>Etkinlik olayları işlemek için  
  
1.  İçinde *Workflow1.cs* veya *Workflow1.vb*, aşağıdaki alan üst kısmına ekleyin `Workflow1` sınıfı. Bu alan, bir etkinlik iş akışı tamamlanıp tamamlanmadığını belirlemek için kullanılır.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Aşağıdaki yöntemi ekleyin `Workflow1` sınıfı. Bu yöntem değeri kontrol `Document Status` belgeyi gözden olup olmadığını belirlemek için belgeler listesi özelliği. Varsa `Document Status` özelliği `Review Complete`, ardından `checkStatus` yöntemi kümeleri `workflowPending` alanı **false** iş akışını tamamlamak hazır olduğunu göstermek için.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Aşağıdaki kodu ekleyin `onWorkflowActivated` ve `onWorkflowItemChanged` yöntemleri çağırmak için `checkStatus` yöntemi. İş akışı başladığında, `onWorkflowActivated` yöntem çağrılarını `checkStatus` belge zaten gözden olup olmadığını belirlemek için yöntemi. Bu gözden geçirilmemiştir varsa, iş akışı devam eder. Belge kaydedildiğinde `onWorkflowItemChanged` yöntem çağrılarını `checkStatus` yeniden belgeyi gözden olup olmadığını belirlemek için yöntemi. Sırada `workflowPending` ayarlanmış **true**, iş akışı çalışmaya devam eder.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Aşağıdaki kodu ekleyin `isWorkflowPending` durumunu denetlemek için yöntem `workflowPending` özelliği. Belge kaydedildiğinde, her zaman **whileActivity1** etkinlik çağrıları `isWorkflowPending` yöntemi. Bu yöntem inceler <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> özelliği <xref:System.Workflow.Activities.ConditionalEventArgs> belirlemek için nesne olup olmadığını **WhileActivity1** etkinliği devam veya son. Özellik ayarlanmışsa **true**, etkinlik devam eder. Aksi takdirde, etkinlik tamamlanır ve iş akışı tamamlanır.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Projeyi kaydedin.  
  
## <a name="test-the-sharepoint-workflow-template"></a>SharePoint iş akışı şablonu test
 Hata ayıklayıcıyı başlattığınızda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı şablonu SharePoint sunucusuna dağıtır ve iş akışı ile ilişkilendirir **paylaşılan belgeler** listesi. İş akışı test etmek için bir belgedeki bir iş akışı örneği başlatın **paylaşılan belgeler** listesi.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>SharePoint iş akışı şablonu test etmek için  
  
1.  İçinde *Workflow1.cs* veya *Workflow1.vb*, yanında bir kesme noktası ayarlamak **onWorkflowActivated** yöntemi.  
  
2.  Seçin **F5** anahtarı oluşturun ve çözümü çalıştırın.  
  
     SharePoint sitesi görüntülenir.  
  
3.  SharePoint'te Gezinti bölmesinde **paylaşılan belgeler** bağlantı.  
  
4.  İçinde **paylaşılan belgeler** sayfasında **belgeleri** bağlantısını **Kütüphane Araçları** sekmesine ve ardından **belge Yükle** düğmesi .  
  
5.  İçinde **belge Yükle** iletişim kutusunda **Gözat** düğmesi, herhangi bir belge dosya seçin, **açık** düğmesine ve ardından **Tamam** düğmesi.  
  
     Bu seçili belgeye yükler **paylaşılan belgeler** listelemek ve iş akışı başlatır.  
  
6.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], hata ayıklayıcı yanındaki kesme noktasında durduğunu doğrulayın `onWorkflowActivated` yöntemi.  
  
7.  Seçin **F5** yürütme devam etmek için anahtarı.  
  
8.  Belge burada ayarlarını değiştirebilirsiniz, ancak bunları varsayılan değerlerinde seçerek şimdilik bırakın **Kaydet** düğmesi.  
  
     Bu size döndürür **paylaşılan belgeler** varsayılan SharePoint Web sitesi sayfası.  
  
9. İçinde **paylaşılan belgeler** sayfasında, değerin altında **MySharePointWorkflow - Workflow1** sütun ayarlanmış **sürüyor**. Bu iş akışı devam ediyor ve belgenin gözden geçirme bekliyor gösterir.  
  
10. İçinde **paylaşılan belgeler** sayfasında, bir belge seçin, görünür ve sonra oka **özelliklerini Düzenle** menü öğesi.  
  
11. Ayarlama **belge durumu** için **gözden geçirme tamamlandı**ve ardından **Kaydet** düğmesi.  
  
     Bu size döndürür **paylaşılan belgeler** varsayılan SharePoint Web sitesi sayfası.  
  
12. İçinde **paylaşılan belgeler** sayfasında, değerin altında **belge durumu** sütun ayarlanmış **gözden geçirme tamamlandı**. Yenileme **paylaşılan belgeler** doğrulayın ve sayfa değerin altında **MySharePointWorkflow - Workflow1** sütun ayarlanmış **tamamlandı**. Gösterir iş akışı tamamlandığında ve belgenin gözden geçirildi.  
  
## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan iş akışı şablonları oluşturma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   SharePoint iş akışı etkinlikleri hakkında daha fazla bilgi için bkz: [iş akışı etkinlikleri, SharePoint Foundation için](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Windows Workflow Foundation etkinlikleri hakkında daha fazla bilgi için bkz: [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint iş akışı çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Derleme ve SharePoint çözümlerinde hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
