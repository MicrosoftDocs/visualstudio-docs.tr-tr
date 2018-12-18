---
title: 'İzlenecek yol: öğe şablonu ile özel bir eylem proje öğesi oluşturma, bölüm 1 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8144723f68b9343c1c7d74f7a940aec569dd7969
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296131"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>İzlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma
  Visual Studio'da SharePoint Proje sistemi kendi proje öğesi türleri oluşturarak genişletebilirsiniz. Bu kılavuzda, bir SharePoint sitesinde özel eylem oluşturmak için bir SharePoint projesine eklenen bir proje öğesi oluşturur. Bir menü öğesi özel eylemi ekler **Site eylemleri** SharePoint sitesinin menüsü.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Visual Studio uzantısı oluşturma, yeni bir SharePoint proje öğesi için özel bir eylem türünü tanımlar. Yeni proje öğesi türüyle birden fazla özel özellikler uygular:  
  
  -   Visual Studio'da özel bir eylem için bir tasarımcı görüntüleme gibi proje öğesi ile ilgili ek görevler için bir başlangıç noktası olarak hizmet veren bir kısayol menüsü.  
  
  -   Bir geliştirici proje öğesi ve onu içeren projeyi belirli özellikleri değiştiğinde çalışan kod.  
  
  -   Proje öğesinde yanında özel bir simge **Çözüm Gezgini**.  
  
- Visual Studio öğe Şablonu proje öğesi için oluşturuluyor.  
  
- Proje öğesi şablon ve uzantı derlemesini dağıtmak için Visual Studio Uzantısı (VSIX) paketini derleme.  
  
- Hata ayıklama ve proje öğesi test etme.  
  
  Tek başına bir gidiş yolu budur. Bu kılavuzu tamamladıktan sonra proje öğesi için öğe şablonu sihirbaz ekleyerek geliştirebilirsiniz. Daha fazla bilgi için [izlenecek yol: bir öğe şablonu, bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Bir örnekten indirebileceğiniz [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , özel etkinlikler için iş akışı oluşturma işlemi gösterilmektedir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler ihtiyacınız vardır:  
  
- Microsoft Windows, SharePoint ve Visual Studio'nun desteklenen sürümleri.
  
- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu izlenecek yolda **VSIX projesi** proje öğesini dağıtmak üzere bir VSIX paketi oluşturmak için SDK'sı şablonunda. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Aşağıdaki kavramları bilgisi yardımcı, ancak gerekli değildir, bu izlenecek yolu tamamlamak için:  
  
- SharePoint özel eylemler. Daha fazla bilgi için [özel eylem](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
- Visual Studio öğe şablonları. Daha fazla bilgi için [oluşturma proje ve öğe şablonları](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için üç projeleri oluşturmanız gerekir:  
  
- VSIX projesi. Bu proje SharePoint Proje öğesini dağıtmak için VSIX paketi oluşturur.  
  
- Bir öğe şablonu projesi. Bu proje bir SharePoint projesine SharePoint proje öğesi eklemek için kullanılan bir öğe şablonu oluşturur.  
  
- Bir sınıf kitaplığı projesi. Bu proje, SharePoint Proje öğesinin davranışını tanımlayan bir Visual Studio uzantısı uygular.  
  
  İzlenecek yol, proje oluşturmaya başlayın.  
  
#### <a name="to-create-the-vsix-project"></a>VSIX projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
3.  Üst kısmındaki listede **yeni proje** iletişim kutusunda, emin **.NET Framework 4.5** seçilir.  
  
4.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **genişletilebilirlik** düğümü.  
  
    > [!NOTE]  
    >  **Genişletilebilirlik** düğümüdür yalnızca, Visual Studio SDK yüklenmiş ise kullanılabilir. Daha fazla bilgi için bu konudaki Önkoşullar bölümüne bakın.  
  
5.  Seçin **VSIX projesi** şablonu.  
  
6.  İçinde **adı** kutusuna **CustomActionProjectItem**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **CustomActionProjectItem** için proje **Çözüm Gezgini**.  
  
#### <a name="to-create-the-item-template-project"></a>Öğe şablonu projesi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  Üst kısmındaki listede **yeni proje** iletişim kutusunda, emin **.NET Framework 4.5** seçilir.  
  
3.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümler ve ardından **genişletilebilirlik** düğümü.  
  
4.  Proje şablonları listesinde seçin **C# öğe şablonu** veya **Visual Basic öğe şablonu** şablonu.  
  
5.  İçinde **adı** kutusuna **ItemTemplate**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **ItemTemplate** çözüme bir proje.  
  
#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  Üst kısmındaki listede **yeni proje** iletişim kutusunda, emin **.NET Framework 4.5** seçilir.  
  
3.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** düğümlerini **Windows** düğümünün seçin **Sınıf Kitaplığı** proje şablonu.  
  
4.  İçinde **adı** kutusuna **ProjectItemDefinition**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **ProjectItemDefinition** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
5.  Projeden Class1 kod dosyasını silin.  
  
## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 SharePoint proje öğesi türü tanımlamak için kod yazmadan önce kod dosyalarını ve derleme referanslarını uzantı projesine eklemeniz gerekir.  
  
#### <a name="to-configure-the-project"></a>Proje yapılandırma  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProjectItemDefinition** projesinin **Ekle**, ardından **yeni öğe**.  
  
2.  Proje öğeleri listesinde seçin **kod dosyası**.  
  
3.  İçinde **adı** kutusunda, bir ad girin **özel** uygun dosya adı uzantısı ve ardından **Ekle** düğmesi.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProjectItemDefinition** proje ve ardından **Başvuru Ekle**.  
  
5.  İçinde **başvuru Yöneticisi - ProjectItemDefinition** iletişim kutusunda **derlemeleri** düğümünü seçip **Framework** düğümü.  
  
6.  Aşağıdaki derlemelerin her yanındaki onay kutusunu seçin:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Seçin **uzantıları** düğümünün Microsoft.VisualStudio.Sharepoint derlemenin yanındaki onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>Yeni bir SharePoint proje öğesi türü tanımlama
 Uygulayan bir sınıf oluşturma <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> yeni proje öğesi türüyle davranışını tanımlamak için arabirim. Yeni bir proje öğesi türünü tanımlamak istediğinizde bu arabirimi uygulayın.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Yeni bir SharePoint proje öğesi türü tanımlama  
  
1.  ProjectItemDefinition projesinde özel kod dosyasını açın.  
  
2.  Bu dosyadaki kodu aşağıdaki kodla değiştirin.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Çözüm Gezgini'nde proje öğesi için bir simge oluşturma
 Özel bir SharePoint proje öğesi oluşturduğunuzda, proje öğesi ile bir görüntü (simge veya bit eşlem) ilişkilendirebilirsiniz. Bu görüntü proje öğesinde yanında **Çözüm Gezgini**.  
  
 Aşağıdaki yordamda, proje öğesi için bir simge oluşturur ve simge uzantısı derlemede katıştırmak. Bu simge tarafından başvurulan <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> , `CustomActionProjectItemTypeProvider` daha önce oluşturduğunuz sınıfı.  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Proje öğesi için özel bir simge oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProjectItemDefinition** projesinin **Ekle**ve ardından **yeni öğe...** .  
  
2.  Proje öğeleri listesinde seçin **simge dosyası** öğesi.  
  
    > [!NOTE]  
    >  Visual Basic projelerinde, seçmelisiniz **genel** görüntülemek için **simge dosyası** öğesi.  
  
3.  İçinde **adı** kutusuna **CustomAction_SolutionExplorer.ico**ve ardından **Ekle** düğmesi.  
  
     İçinde yeni simge açıldıktan **Resim Düzenleyicisi**.  
  
4.  Simge dosyası 16 x 16 sürümünü tanıması ve simge dosyası kaydedin bir tasarıma sahip olacak şekilde düzenleyin.  
  
5.  İçinde **Çözüm Gezgini**, seçin **CustomAction_SolutionExplorer.ico**.  
  
6.  İçinde **özellikleri** penceresinde yanındaki oku seçin **derleme eylemi** özelliği.  
  
7.  Açılan listeden seçin **gömülü kaynak**.  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu aşamada izlenecek yolda, proje öğesi için kodun tümü artık projedir. Hata olmadan derlediğinden doğrulamak için projeyi derleyin.  
  
#### <a name="to-build-your-project"></a>Projenizi yapılandırmak için  
  
1.  Kısayol menüsünü açın **ProjectItemDefinition** projesini ve ardından **yapı**.  
  
## <a name="create-a-visual-studio-item-template"></a>Visual Studio öğe şablonu oluşturma
 Diğer geliştiricilerin, proje öğesini kullanmak için bir proje şablonu veya öğe şablonu oluşturmalısınız. Geliştiriciler, Visual Studio'da yeni bir proje oluşturarak veya mevcut bir projeye bir öğe ekleyerek, proje öğesinin bir örneğini oluşturmak için bu şablonları kullanın. Bu kılavuz için ItemTemplate projenin proje öğenizin yapılandırmak için kullanın.  
  
#### <a name="to-create-the-item-template"></a>Öğe şablonu oluşturmak için  
  
1.  ItemTemplate projeden Class1 kod dosyasını silin.  
  
2.  ItemTemplate projeyi *ItemTemplate.vstemplate* dosya.  
  
3.  Dosyanın içeriğini aşağıdaki XML ile değiştirin ve ardından dosyasını kaydedin ve kapatın.  
  
    > [!NOTE]  
    >  Aşağıdaki XML Visual C# öğesi yönelik bir şablondur. Visual Basic öğe şablonu oluşturuyorsanız değiştirin `ProjectType` öğeyle `VisualBasic`.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Bu dosya içeriğini ve öğe şablonu davranışını tanımlar. Bu dosyanın içeriği hakkında daha fazla bilgi için bkz. [Visual Studio şablon şeması başvurusu](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ItemTemplate** projesinin **Ekle**ve ardından **yeni öğe**.  
  
5.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **metin dosyası** şablonu.  
  
6.  İçinde **adı** kutusuna **CustomAction.spdata**ve ardından **Ekle** düğmesi.  
  
7.  Eklemek için aşağıdaki XML *CustomAction.spdata* dosyasını kaydedin ve dosyayı kapatın.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Bu dosya proje öğesi tarafından bulunan dosyalar hakkında bilgi içerir. `Type` Özniteliği `ProjectItem` öğesi, geçirilen aynı dizeye ayarlanmalıdır <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> proje öğesi tanımı ( `CustomActionProjectItemTypeProvider` bu kılavuzda daha önce oluşturduğunuz sınıfı). İçeriği hakkında daha fazla bilgi için *.spdata* dosyaları görmek [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ItemTemplate** projesinin **Ekle**ve ardından **yeni öğe**.  
  
9. İçinde **Yeni Öğe Ekle** iletişim kutusunda **XML dosyası** şablonu.  
  
10. İçinde **adı** kutusuna **Elements.xml**ve ardından **Ekle** düğmesi.  
  
11. Öğesinin içeriğini değiştirin *Elements.xml* dosya aşağıdaki XML ve ardından dosyayı kaydedip kapatın.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Bu dosya çubuğunda bir menü öğesini oluşturan bir varsayılan özel eylemi tanımlayan **Site eylemleri** SharePoint sitesinin menüsü. URL kullanıcı menü öğesi seçtiğinde, belirtilen `UrlAction` öğesi web tarayıcısında açar. Özel bir eylem tanımlamak için kullanabileceğiniz XML öğeleri hakkında daha fazla bilgi için bkz. [özel eylem tanımları](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. İsteğe bağlı olarak, açık *ItemTemplate.ico* dosya ve tanıyabilirsiniz bir tasarıma sahip olacak şekilde değiştirin. Bu simge proje öğesinin yanındaki görüntüler **Yeni Öğe Ekle** iletişim kutusu.  
  
13. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ItemTemplate** proje ve ardından **projeyi**.  
  
14. Kısayol menüsünü açın **ItemTemplate** yeniden proje ve ardından **Düzenle ItemTemplate.csproj** veya **Düzenle ItemTemplate.vbproj**.  
  
15. Aşağıdaki bulun `VSTemplate` proje dosyasındaki öğesi.  
  
    ```xml  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Bunun yerine `VSTemplate` aşağıdaki XML ve ardından Kaydet ve Kapat dosya olan öğe.  
  
    ```xml  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Öğesi altında öğe Şablonu oluşturulan proje oluşturduğunuzda yolunda ek klasörleri belirtir. Burada belirtilen klasörleri yalnızca müşterilerin açtığınızda öğe şablonu kullanılabilir olmasını sağlamak **Yeni Öğe Ekle** iletişim kutusunda **SharePoint** düğümünü seçip **2010**  düğümü.  
  
17. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ItemTemplate** proje ve ardından **projeyi**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Proje öğesini dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için VSIX paketi oluşturmak için çözümünüzdeki VSIX projesi kullanın. İlk olarak, VSIX projesine dahil olan source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırın. Ardından çözümü oluşturarak VSIX paketini oluşturun.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Yapılandırma ve VSIX paketini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **source.extension.vsixmanifest** CustomActionProjectItem projeye dosya ve ardından **açın**.  
  
     Visual Studio, dosyayı bildirim düzenleyicisinde açar. Source.extension.vsixmanifest dosyası, tüm VSIX paketleri gerektiren extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  İçinde **ürün adı** kutusuna **özel eylem proje öğesi**.  
  
3.  İçinde **Yazar** kutusuna **Contoso**.  
  
4.  İçinde **açıklama** kutusuna **özel bir eylemi temsil eden bir SharePoint proje öğesi**.  
  
5.  Üzerinde **varlıklar** sekmesini, **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
6.  İçinde **türü** listesinde **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `ItemTemplate` extension.vsixmanifest dosyasındaki öğesi. Bu öğe, alt proje öğesi şablon içeren VSIX paketi tanımlar. Daha fazla bilgi için [ItemTemplate öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).  
  
7.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
8.  İçinde **proje** listesinde **ItemTemplate**ve ardından **Tamam** düğmesi.  
  
9. İçinde **varlıklar** sekmesini, **yeni** düğmesini tekrar.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
10. İçinde **türü** listesinde **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `MefComponent` extension.vsixmanifest dosyasındaki öğesi. Bu öğe VSIX paketinde bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için [MEFComponent öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
11. İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
12. İçinde **proje** listesinde **ProjectItemDefinition**.  
  
13. Seçin **Tamam** düğmesi.  
  
14. Menü çubuğunda, **derleme** > **Çözümü Derle**ve ardından projenin hata olmadan derlediğinden emin olun.  
  
15. CustomActionProjectItem projesi yapı çıkış klasöründe CustomActionProjectItem.vsix dosyası içerdiğinden emin olun.  
  
     Varsayılan olarak, derleme çıktısı klasörü olduğu... \bin\Debug klasörüne CustomActionProjectItem projeyi içeren klasörü altında.  
  
## <a name="test-the-project-item"></a>Proje öğesi test etme
 Proje öğesi test etmek artık hazırsınız. İlk olarak, Visual Studio'nun deneysel örneğinde CustomActionProjectItem çözüm hatalarını ayıklamaya başlayın. Ardından, test **özel eylem** Visual Studio'nun deneysel örneğinde bir SharePoint projesi içinde proje öğesi. Son olarak, derleme ve özel eylemin beklendiği gibi çalıştığını doğrulamak için SharePoint Proje çalıştırın.  
  
#### <a name="to-start-debugging-the-solution"></a>Çözüm hata ayıklamayı başlatmak için  
  
1.  Yönetici kimlik bilgileriyle Visual Studio'yu yeniden başlatın ve ardından CustomActionProjectItem çözümü açın.  
  
2.  Özel kod dosyasını açın ve ardından ilk kod satırına bir kesme noktası ekleyin `InitializeType` yöntemi.  
  
3.  Seçin **F5** hata ayıklamayı başlatmak için anahtar.  
  
     Visual Studio, eylem proje Item\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom için uzantıyı yükleyen ve Visual Studio'nun deneysel örneği başlar. Proje öğesi bu Visual Studio örneğinde test edeceğiz.  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>Proje öğesi Visual Studio'da Test etmek için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **dosya** > **yeni** > **proje**.  
  
2.  Genişletin **Visual C#** veya **Visual Basic** genişletin (öğe şablonunuzu destekleyen dile bağlı olarak), **SharePoint**ve ardından **2010**  düğümü.  
  
3.  Proje şablonları listesinde seçin **SharePoint 2010 projesi**.  
  
4.  İçinde **adı** kutusuna **CustomActionTest**ve ardından **Tamam** düğmesi.  
  
5.  İçinde **SharePoint Özelleştirme Sihirbazı**, hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin ve ardından **son** düğmesi.  
  
6.  İçinde **Çözüm Gezgini**, proje düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni öğe**.  
  
7.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **2010** düğümünde **SharePoint** düğümü.  
  
     Doğrulayın **özel eylem** öğesi proje öğeleri listesinde görünür.  
  
8.  Seçin **özel eylem** öğesi ekleyin ve ardından **Ekle** düğmesi.  
  
     Visual Studio adlı bir öğe ekler **CustomAction1** açar ve proje için *Elements.xml* düzenleyicideki dosyada.  
  
9. Visual Studio'nun diğer örneğindeki kodun daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `InitializeType` yöntemi.  
  
10. Seçin **F5** proje hatalarını ayıklamaya devam etmek için anahtarı.  
  
11. Visual Studio'nun Deneysel örneğinin içinde **Çözüm Gezgini**, kısayol menüsünü açın **CustomAction1** düğümünü seçip **görünüm özel eylem Tasarımcısı**.  
  
12. Bir ileti kutusu görünür ve ardından doğrulamak **Tamam** düğmesi.  
  
     Geliştiriciler, özel bir eylem için bir tasarımcı görüntüleme gibi ek seçenekleri veya komutları sağlamak için bu kısayol menüsünü kullanabilirsiniz.  
  
13. Menü çubuğunda, **görünümü** > **çıkış**.  
  
     **Çıkış** penceresi açılır.  
  
14. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CustomAction1** öğesi ekleyin ve sonra adını değiştirmek **MyCustomAction**.  
  
     İçinde **çıkış** penceresi, bir onay iletisi görüntülenir. Bu ileti tarafından yazılan <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> tanımlanan olay işleyicisi `CustomActionProjectItemTypeProvider` sınıfı. Bu olay ve proje öğesi Geliştirici değiştirdiğinde özel davranışı uygulamak diğer proje öğesi olayları işleyebilir.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Özel eylem, SharePoint'te test etmek için  
  
1.  Visual Studio'nun deneysel örneğinde açın *Elements.xml* alt öğesi olan dosya **MyCustomAction** proje öğesi.  
  
2.  İçinde *Elements.xml* dosya, aşağıdaki değişiklikleri yapın ve ardından dosyayı kaydedin:  
  
    -   İçinde `CustomAction` öğe, ayarladığınız `Id` aşağıdaki örnekte gösterildiği gibi bir GUID veya diğer bir benzersiz dize özniteliği:  
  
        ```xml  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   İçinde `CustomAction` öğe, ayarladığınız `Title` özniteliği aşağıdaki örnekte gösterildiği gibi:  
  
        ```xml  
        Title="SharePoint Developer Center"  
        ```  
  
    -   İçinde `CustomAction` öğe, ayarladığınız `Description` özniteliği aşağıdaki örnekte gösterildiği gibi:  
  
        ```xml  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   İçinde `UrlAction` öğe, ayarladığınız `Url` özniteliği aşağıdaki örnekte gösterildiği gibi:  
  
        ```xml  
        Url="https://docs.microsoft.com/sharepoint/dev/"  
        ```  
  
3.  Seçin **F5** anahtarı.  
  
     Özel eylem paketlenir ve belirtilen SharePoint sitesine dağıtılan **Site URL'si** projenin özelliği. Web tarayıcısı bu sitenin varsayılan sayfasına açılır.  
  
    > [!NOTE]  
    >  Varsa **betik hata ayıklamasını devre dışı bırakılmış** iletişim kutusu görüntülenirse, seçin **Evet** proje hatalarını ayıklamaya devam etmek için düğme.  
  
4.  Üzerinde **Site eylemleri** menüsünde seçin **SharePoint Geliştirici Merkezi**, tarayıcının Web sitesi açılır doğrulayın https://docs.microsoft.com/sharepoint/dev/ve ardından web tarayıcısını kapatın.  
  
## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme
 Proje öğesi testi tamamladıktan sonra proje öğesi şablonu Visual Studio'nun deneysel örneği kaldırın.  
  
#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Uzantılar listesinde seçin **özel eylem proje öğesi**ve ardından **kaldırma** düğmesi.  
  
3.  Görünen iletişim kutusunda **Evet** uzantının yüklemesini kaldırmak istediğinizi onaylamak için düğme.  
  
4.  Seçin **şimdi yeniden Başlat** kaldırma işlemini tamamlamak için düğme.  
  
5.  Visual Studio'nun deneysel örneğinde hem CustomActionProjectItem çözüm açık olduğu örneği kapatın.  
  
## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuzu tamamladıktan sonra sihirbaz öğe şablonuna ekleyebilirsiniz. Bir kullanıcı bir SharePoint projesine bir özel eylem proje öğesi eklediğinde, sihirbaz eylem (örneğin, konumunu ve eylem seçildiğinde gidilecek URL'yi) hakkında bilgi toplar ve bu bilgileri ekler *Elements.xml*dosyasında yeni proje öğesi. Daha fazla bilgi için [izlenecek yol: bir öğe şablonu, bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İzlenecek yol: bir öğe şablonu, bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Öğe şablonları ve SharePoint Proje öğeleri için proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [SharePoint Proje hizmetini kullanın](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio Şablon Şeması Başvurusu](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)   
 [Simge veya başka görüntü oluşturma &#40;simgeler için görüntü Düzenleyicisi&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
