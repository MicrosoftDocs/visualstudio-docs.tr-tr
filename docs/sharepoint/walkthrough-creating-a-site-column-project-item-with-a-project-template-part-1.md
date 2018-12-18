---
title: 'İzlenecek yol: Proje şablonu ile bir Site sütunu proje öğesi oluşturma, bölüm 1 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56f50a3c50156cbd932fc7a7247fd96c4c6c2834
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296261"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>İzlenecek yol: bir proje şablonu, bölüm 1 ile bir site sütunu proje öğesi oluşturma
  SharePoint projeleri, bir veya daha fazla SharePoint Proje öğeleri için kapsayıcılardır. Visual Studio'da SharePoint Proje sisteminin, kendi SharePoint proje öğesi türleri oluşturarak ve ardından bunları bir proje şablonu ile ilişkilendirerek genişletebilirsiniz. Bu kılavuzda, bir site sütunu oluşturmak için bir proje öğesi türü tanımlayacağınızı ve bir site sütunu proje öğesi içeren yeni bir proje oluşturmak için kullanılan bir proje şablonu oluşturup.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Visual Studio uzantısı oluşturma, yeni bir SharePoint için site sütunu proje öğesi türünü tanımlar. Proje öğesi türü görünür basit bir özel özellik içeren **özellikleri** penceresi.  
  
- Oluşturma bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proje öğesi için proje şablonu.  
  
- Oluşturma bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proje şablonu ve uzantı derlemesini dağıtmak için paket uzantısı (VSIX).  
  
- Hata ayıklama ve proje öğesi test etme.  
  
  Tek başına bir gidiş yolu budur. Bu kılavuzu tamamladıktan sonra proje öğesi için Proje Şablonu Sihirbazı ekleyerek geliştirebilirsiniz. Daha fazla bilgi için [izlenecek yol: bir proje şablonu, bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
> Bir dizi örnek iş akışları için [SharePoint iş akışı örnekleri](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenler ihtiyacınız vardır:  
  
- Desteklenen Microsoft Windows, SharePoint sürümleri ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu izlenecek yolda **VSIX projesi** proje öğesini dağıtmak üzere bir VSIX paketi oluşturmak için SDK'sı şablonunda. Daha fazla bilgi için [Visual Studio'da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Aşağıdaki prototip bilgi yardımcı, ancak gerekli değildir, bu izlenecek yolu tamamlamak için:  
  
- SharePoint için site sütunları. Daha fazla bilgi için [sütunları](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
- Visual Studio Proje şablonları. Daha fazla bilgi için [oluşturma proje ve öğe şablonları](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için üç projeleri oluşturmanız gerekir:  
  
- VSIX projesi. Bu projenin site sütunu proje öğesi ve proje şablonu dağıtmak için VSIX paketi oluşturur.  
  
- Bir proje şablonu projesi. Bu projenin site sütunu proje öğesi içeren yeni bir SharePoint projesi oluşturmak için kullanılan bir proje şablonu oluşturur.  
  
- Bir sınıf kitaplığı projesi. Site sütunu proje öğesi davranışını tanımlayan bir Visual Studio uzantısını uygulayan bu proje.  
  
  İzlenecek yol, proje oluşturmaya başlayın.  
  
#### <a name="to-create-the-vsix-project"></a>VSIX projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
3.  Üst kısmındaki **yeni proje** iletişim kutusunda, emin **.NET Framework 4.5** .NET Framework sürümleri listesinde seçilir.  
  
4.  Genişletin **Visual Basic** veya **Visual C#** düğümler ve ardından **genişletilebilirlik** düğümü.  
  
    > [!NOTE]  
    >  **Genişletilebilirlik** düğümüdür yalnızca, Visual Studio SDK yüklenmiş ise kullanılabilir. Daha fazla bilgi için bu konudaki Önkoşullar bölümüne bakın.  
  
5.  Proje şablonları listesinde seçin **VSIX projesi**.  
  
6.  İçinde **adı** kutusuna **SiteColumnProjectItem**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **SiteColumnProjectItem** için proje **Çözüm Gezgini**.  
  
#### <a name="to-create-the-project-template-project"></a>Proje şablonu projesi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  Üst kısmındaki **yeni proje** iletişim kutusunda, emin **.NET Framework 4.5** .NET Framework sürümleri listesinde seçilir.  
  
3.  Genişletin **Visual C#** veya **Visual Basic** düğümünü seçip **genişletilebilirlik** düğümü.  
  
4.  Proje şablonları listesinde seçin **C# proje şablonu** veya **Visual Basic proje şablonu** şablonu.  
  
5.  İçinde **adı** kutusuna **SiteColumnProjectTemplate**ve ardından **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **SiteColumnProjectTemplate** çözüme bir proje.  
  
6.  Projeden Class1 kod dosyasını silin.  
  
7.  Ayrıca bir Visual Basic projesi oluşturduysanız, projeden aşağıdaki dosyaları silin:  
  
    -   *MyApplication.Designer.vb*  
  
    -   MyApplication.myapp  
  
    -   *Resources.Designer.vb*  
  
    -   *Resources.resx*  
  
    -   *Settings.Designer.vb*  
  
    -   Settings.Settings  
  
#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.  
  
2.  Üst kısmındaki **yeni proje** iletişim kutusunda, emin **.NET Framework 4.5** .NET Framework sürümleri listesinde seçilir.  
  
3.  Genişletin **Visual C#** veya **Visual Basic** düğümlerini **Windows** düğümünü seçip **sınıf kitaplığı** şablonu.  
  
4.  İçinde **adı** kutusuna **ProjectItemTypeDefinition** seçip **Tamam** düğmesi.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ekler **ProjectItemTypeDefinition** çözüme ve varsayılan Class1 kod dosyasını açar.  
  
5.  Projeden Class1 kod dosyasını silin.  
  
## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Uzantı projesini yapılandırmak için bütünleştirilmiş kod başvuruları ve kod dosyaları ekleyin.  
  
#### <a name="to-configure-the-project"></a>Proje yapılandırma  
  
1.  Adlı bir kod dosyası ProjectItemTypeDefinition projesinde ekleyin **SiteColumnProjectItemTypeProvider**.  
  
2.  Menü çubuğunda, **proje** > **Başvuru Ekle**.  
  
3.  İçinde **başvuru Yöneticisi - ProjectItemTypeDefinition** iletişim kutusunda **derlemeleri** düğümünü seçin **Framework** düğümüne tıklayın ve ardından System.ComponentModel.Composition onay kutusunu seçin.  
  
4.  Seçin **uzantıları** düğümünün Microsoft.VisualStudio.SharePoint derlemenin yanındaki onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>Yeni bir SharePoint proje öğesi türü tanımlama
 Uygulayan bir sınıf oluşturma <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> yeni proje öğesi türüyle davranışını tanımlamak için arabirim. Yeni bir proje öğesi türünü tanımlamak istediğinizde bu arabirimi uygulayın.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Yeni bir SharePoint proje öğesi türü tanımlama  
  
1.  İçinde **SiteColumnProjectItemTypeProvider** kod dosyası, varsayılan kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="create-a-visual-studio-project-template"></a>Visual Studio Proje şablonu oluşturma
 Bir proje şablonu oluşturarak, site sütunu proje öğeleri içeren SharePoint projeleri oluşturmak diğer geliştiriciler etkinleştirin. Bir SharePoint Proje şablonu Visual Studio'daki tüm projeler için gibi gerekli dosyaları içeren *.csproj* veya *.vbproj* ve *.vstemplate* dosyaları ve dosyalar SharePoint projelerine özgüdür. Daha fazla bilgi için [öğe şablonları ve proje şablonları SharePoint Proje öğeleri için oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Bu yordamda, SharePoint projelerine özgü dosyaları oluşturmak için boş bir SharePoint projesi oluşturun. Böylece bu projeden oluşturulan şablonu dahil SiteColumnProjectTemplate projeye bu dosyaları ekleyin. Proje şablonu olarak görüneceği yeri belirtmek için SiteColumnProjectTemplate proje dosyası da yapılandırmanız **yeni proje** iletişim kutusu.  
  
#### <a name="to-create-the-files-for-the-project-template"></a>Proje şablonu dosyalarını oluşturmak için  
  
1. İkinci bir örneğini Başlat [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yönetici kimlik bilgilerine sahip.  
  
2. Adlı bir SharePoint 2010 projesi oluşturma **BaseSharePointProject**.  
  
   > [!IMPORTANT]  
   >  İçinde **SharePoint Özelleştirme Sihirbazı**, seçmeyin **Grup çözümü olarak Dağıt** seçenek düğmesini.  
  
3. Projeye bir boş öğe öğe ekleyin ve ardından öğe adı **alan1**.  
  
4. Projeyi kaydedin ve ikinci örneğini kapatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5. Örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SiteColumnProjectItem çözüm açık, buna sahip **Çözüm Gezgini**, kısayol menüsünü açın **SiteColumnProjectTemplate** proje düğümünü, seçin **Ekleme**ve ardından **var olan öğe**.  
  
6. İçinde **varolan öğeyi Ekle** iletişim kutusunda, dosya uzantıları listesini açın ve ardından **tüm dosyalar (\*.\*)** .  
  
7. BaseSharePointProject projesini içeren dizin key.snk dosyasını seçin ve ardından **Ekle** düğmesi.  
  
   > [!NOTE]  
   >  Bu kılavuzda, oluşturduğunuz proje şablonu, şablonu kullanılarak oluşturulan her proje oturum açmak için aynı key.snk dosyasını kullanır. Her bir proje örneği için bir başka key.snk dosyası oluşturmak için bu örnek genişletme öğrenmek için bkz. [izlenecek yol: bir proje şablonu, bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8. Aşağıdaki dosyalar BaseSharePointProject dizinde belirtilen klasörlerdeki eklemek için 5-8 adımları yineleyin:  
  
   - *\Field1\Elements.XML*  
  
   - *\Field1\SharePointProjectItem.spdata*  
  
   - *\Features\Feature1\Feature1.Feature*  
  
   - *\Features\Feature1\Feature1.Template.XML*  
  
   - *\Package\Package.Package*  
  
   - *\Package\Package.Template.XML*  
  
     Bu dosyalar doğrudan SiteColumnProjectTemplate projeye ekleyin; Proje alan1, özellikleri veya paket klasörlerinde yeniden yok. Bu dosyalar hakkında daha fazla bilgi için bkz. [öğe şablonları ve proje şablonları SharePoint Proje öğeleri için oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Geliştiriciler yeni proje iletişim kutusunda proje şablonu nasıl keşfetmek yapılandırmak için
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SiteColumnProjectTemplate** proje düğümünü ve ardından **projeyi**. Değişiklikleri olan dosyaları kaydetmek için istenirse, seçin **Evet** düğmesi.  
  
2.  Kısayol menüsünü açın **SiteColumnProjectTemplate** düğümü yeniden seçip **Düzenle SiteColumnProjectTemplate.csproj** veya **SiteColumnProjectTemplate.vbprojDüzenle**.  
  
3.  Proje dosyasında aşağıdaki bulun `VSTemplate` öğesi.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Bu öğe aşağıdaki XML ile değiştirin.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Öğesi altında proje şablonu oluşturulan proje oluşturduğunuzda yolunda ek klasörleri belirtir. Burada belirtilen klasörleri yalnızca müşterilerin açtığınızda, proje şablonu kullanılabilir olmasını sağlamak **yeni proje** iletişim kutusunda **SharePoint** düğümünü seçip **2010**  düğümü.  
  
5.  Dosyayı kaydedin ve kapatın.  
  
6.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SiteColumnProjectTemplate** proje ve ardından **projeyi**.  
  
## <a name="edit-the-project-template-files"></a>Proje şablonu dosyalarını Düzenle
 SiteColumnProjectTemplate projenin proje şablonu davranışını tanımlamak için aşağıdaki dosyayı düzenleyin:  
  
- *AssemblyInfo.cs* veya *AssemblyInfo.vb*  
  
- *Elements.XML*  
  
- *SharePointProjectItem.spdata*  
  
- *Feature1.Feature*  
  
- *Package.Package*  
  
- *SiteColumnProjectTemplate.vstemplate*  
  
- *ProjectTemplate.csproj* veya *ProjectTemplate.vbproj*  
  
  Aşağıdaki yordamlarda, bu dosyaların bazıları değiştirilebilir parametreler ekleyeceksiniz. Bir parametredir başlar ve dolar işareti ($) karakteri ile biten bir belirteçtir. Bir kullanıcı, bir proje oluşturmak için bu proje şablonu kullandığında, Visual Studio bu parametreleri yeni projede belirli değerlerle otomatik olarak değiştirir. Daha fazla bilgi için [değiştirilebilir parametreler](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>AssemblyInfo.cs veya AssemblyInfo.vb dosyayı düzenlemek için
  
1.  SiteColumnProjectTemplate projeyi *AssemblyInfo.cs* veya *AssemblyInfo.vb* dosya ve sonra da üstüne aşağıdaki ifadeyi ekleyin:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Zaman **Korumalı çözüm** özelliği bir SharePoint projesinin **True**, Visual Studio ekler <xref:System.Security.AllowPartiallyTrustedCallersAttribute> AssemblyInfo kod dosyası. Ancak, proje şablonu AssemblyInfo kod dosyasını içe aktarmaz <xref:System.Security> varsayılan ad alanı. Bu eklemelisiniz **kullanarak** veya **içeri aktarmalar** derleme hataları önlemek için deyimi.  
  
2.  Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-edit-the-elementsxml-file"></a>Elements.xml dosyası düzenlemek için
  
1.  SiteColumnProjectTemplate projenin içeriğini değiştirin *Elements.xml* aşağıdaki XML dosyasıyla.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Yeni XML ekler bir `Field` site sütunu, kendi temel türü ve site sütunu galerisinde listelemek grubu adını tanımlayan bir öğe. Bu dosyanın içeriği hakkında daha fazla bilgi için bkz. [alan tanımı şema](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>SharePointProjectItem.spdata dosyayı düzenlemek için
  
1. SiteColumnProjectTemplate projenin içeriğini değiştirin *SharePointProjectItem.spdata* aşağıdaki XML dosyasıyla.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
     <Files>  
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
     </Files>   
   </ProjectItem>  
   ```  
  
    Yeni XML dosyasında aşağıdaki değişiklikleri yapar:  
  
   - Değişiklikleri `Type` özniteliği `ProjectItem` öğesine geçirilen aynı dize <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> proje öğesi tanımı ( `SiteColumnProjectItemTypeProvider` bu kılavuzda daha önce oluşturduğunuz sınıfı).  
  
   - Kaldırır `SupportedTrustLevels` ve `SupportedDeploymentScopes` özniteliklerini `ProjectItem` öğesi. Güven düzeyleri hem de dağıtım kapsamları belirtilmiş olduğundan bu öznitelik değerleri gereksiz `SiteColumnProjectItemTypeProvider` ProjectItemTypeDefinition projedeki sınıf.  
  
     İçeriği hakkında daha fazla bilgi için *.spdata* dosyaları görmek [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-edit-the-feature1feature-file"></a>Feature1.feature dosyayı düzenlemek için
  
1. SiteColumnProjectTemplate projenin içeriğini değiştirin *Feature1.feature* aşağıdaki XML dosyasıyla.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
     <projectItems>  
       <projectItemReference itemId="$guid2$" />  
     </projectItems>  
   </feature>  
   ```  
  
    Yeni XML dosyasında aşağıdaki değişiklikleri yapar:  
  
   - Değerlerini değiştirir `Id` ve `featureId` özniteliklerini `feature` öğesine `$guid4$`.  
  
   - Değerlerini değiştirir `itemId` özniteliği `projectItemReference` öğesine `$guid2$`.  
  
     Hakkında daha fazla bilgi için *.feature* dosyaları görmek [öğe şablonları ve proje şablonları SharePoint Proje öğeleri için oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-edit-the-packagepackage-file"></a>Package.package dosyayı düzenlemek için
  
1. SiteColumnProjectTemplate projenin içeriğini değiştirin *Package.package* aşağıdaki XML dosyasıyla.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
     <features>  
       <featureReference itemId="$guid4$" />  
     </features>  
   </package>  
   ```  
  
    Yeni XML dosyasında aşağıdaki değişiklikleri yapar:  
  
   - Değerlerini değiştirir `Id` ve `solutionId` özniteliklerini `package` öğesine `$guid3$`.  
  
   - Değerlerini değiştirir `itemId` özniteliği `featureReference` öğesine `$guid4$`.  
  
     Hakkında daha fazla bilgi için *.package* dosyaları görmek [öğe şablonları ve proje şablonları SharePoint Proje öğeleri için oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Sitecolumnprojecttemplate.vstemplate dosyayı düzenlemek için
  
1. SiteColumnProjectTemplate projesinde SiteColumnProjectTemplate.vstemplate dosyasının içeriğini XML aşağıdaki bölümlerden biri ile değiştirin.  
  
   -   Visual C# proje şablonu oluşturuyorsanız, aşağıdaki XML kullanın.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>CSharp</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
   -   Visual Basic proje şablonu oluşturuyorsanız, aşağıdaki XML kullanın.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>VisualBasic</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
    Yeni XML dosyasında aşağıdaki değişiklikleri yapar:  
  
   - Kümeleri `Name` değeri öğesine **Site sütunu**. (Bu ad görünür **yeni proje** iletişim kutusunda).  
  
   - Ekler `ProjectItem` dahil her proje örneğinde her filethat için öğeleri.  
  
   - Ad alanını kullanır "<http://schemas.microsoft.com/developer/vstemplate/2005>". Bu çözüm kullanımı diğer proje dosyalarının "<http://schemas.microsoft.com/developer/msbuild/2003>" ad alanı. Bu nedenle, XML şema uyarı iletilerini oluşturulur, ancak bu izlenecek yolda yoksayabilirsiniz.  
  
     İçeriği hakkında daha fazla bilgi için *.vstemplate* dosyaları görmek [Visual Studio şablon şeması başvurusu](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
2. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Projecttemplate.csproj veya projecttemplate.vbproj dosyayı düzenlemek için
  
1.  SiteColumnProjectTemplate projenin içeriğini değiştirin *ProjectTemplate.csproj* dosya veya *ProjectTemplate.vbproj* aşağıdaki bölümlerden XML dosyasıyla.  
  
    -   Visual C# proje şablonu oluşturuyorsanız, aşağıdaki XML kullanın.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Visual Basic proje şablonu oluşturuyorsanız, aşağıdaki XML kullanın.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Yeni XML dosyasında aşağıdaki değişiklikleri yapar:  
  
    -   Kullanan `TargetFrameworkVersion` 4.5 değil .NET Framework 3.5 belirtmek için öğesi.  
  
    -   Ekler `SignAssembly` ve `AssemblyOriginatorKeyFile` proje çıkışını imzalamakta öğe.  
  
    -   Ekler `Reference` SharePoint projeleri kullanan derleme için öğeleri başvuruyor.  
  
    -   Her bir varsayılan dosya için öğeleri gibi proje ekler *Elements.xml* ve *SharePointProjectItem.spdata*.  
  
2.  Dosyayı kaydedin ve kapatın.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Proje şablonu dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için VSIX projesi kullanın **SiteColumnProjectItem** bir VSIX paketi oluşturmak için çözüm. İlk olarak, VSIX projesine dahil olan source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırın. Ardından çözümü oluşturarak VSIX paketini oluşturun.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Yapılandırma ve VSIX paketini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, **SiteColumnProjectItem** proje, bildirim Düzenleyicisi'nde source.extension.vsixmanifest dosyasını açın.  
  
     Source.extension.vsixmanifest dosyası, tüm VSIX paketleri gerektiren extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  İçinde **ürün adı** kutusuna **Site sütunu**.  
  
3.  İçinde **Yazar** kutusuna **Contoso**.  
  
4.  İçinde **açıklama** kutusuna **site sütunları oluşturmak için bir SharePoint proje**.  
  
5.  Seçin **varlıklar** sekmesine ve ardından **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu açılır.  
  
6.  İçinde **türü** listesinde **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `ProjectTemplate` extension.vsixmanifest dosyasındaki öğesi. Bu öğe, alt proje şablonu içeren VSIX paketi tanımlar. Daha fazla bilgi için [ProjectTemplate öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).  
  
7.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
8.  İçinde **proje** listelemek ve seçin **SiteColumnProjectTemplate**ve ardından **Tamam** düğmesi.  
  
9. Seçin **yeni** düğmesini tekrar.  
  
     **Yeni varlık Ekle** iletişim kutusu açılır.  
  
10. İçinde **türü** listesinde **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Bu değer karşılık gelen `MefComponent` extension.vsixmanifest dosyasındaki öğesi. Bu öğe VSIX paketinde bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için [MEFComponent öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
11. İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
12. İçinde **proje** listesinde **ProjectItemTypeDefinition**ve ardından **Tamam** düğmesi.  
  
13. Menü çubuğunda, **derleme** > **Çözümü Derle**ve ardından projenin hata olmadan derlediğinden emin olun.  
  
## <a name="test-the-project-template"></a>Test projesi şablonu
 Artık proje şablonu test etmek hazırsınız. İlk olarak, Visual Studio'nun deneysel örneğinde SiteColumnProjectItem çözüm hatalarını ayıklamaya başlayın. Ardından, test **Site sütunu** projesi Visual Studio'nun deneysel örneğinde. Son olarak, oluşturun ve site sütunu beklendiği gibi çalıştığını doğrulamak için SharePoint Proje çalıştırın.  
  
#### <a name="to-start-debugging-the-solution"></a>Çözüm hata ayıklamayı başlatmak için  
  
1.  Yönetici kimlik bilgileriyle Visual Studio'yu yeniden başlatın ve ardından SiteColumnProjectItem çözümü açın.  
  
2.  
  
3.  SiteColumnProjectItemTypeProvider kod dosyasında, ilk kod satırına bir kesme noktası ekleyin. `InitializeType` yöntemini seçip **F5** hata ayıklamayı başlatmak için anahtar.  
  
     Visual Studio için %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 uzantıyı yükleyen ve Visual Studio'nun deneysel örneği başlar. Proje öğesi bu Visual Studio örneğinde test edeceksiniz.  
  
#### <a name="to-test-the-project-in-visual-studio"></a>Visual Studio'da projeyi test etmek için  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **dosya** > **yeni** > **proje**.  
  
2.  Genişletin **Visual C#** veya **Visual Basic** (dile bağlı olarak, proje şablonu destekleyen), düğümünü **SharePoint** düğümünün seçin**2010** düğümü.  
  
3.  Proje şablonları listesinde seçin **Site sütunu** şablonu.  
  
4.  İçinde **adı** kutusuna **SiteColumnTest** seçip **Tamam** düğmesi.  
  
     İçinde **Çözüm Gezgini**, yeni bir proje ile adlı bir proje öğesi görünür **alan1**.  
  
5.  Visual Studio'nun diğer örneğindeki kodun daha önce ayarladığınız kesme noktasına durduğunu doğrulayın `InitializeType` yöntemini seçip **F5** proje hatalarını ayıklamaya devam etmek için anahtarı.  
  
6.  İçinde **Çözüm Gezgini**, seçin **alan1** düğümünü seçip **F4** anahtarı.  
  
     **Özellikleri** penceresi açılır.  
  
7.  Özellikler listesinde bulunan doğrulayın özelliği **örnek özellik** görünür.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint site sütunu test etmek için  
  
1.  İçinde **Çözüm Gezgini**, seçin **SiteColumnTest** düğümü.  
  
2.  İçinde **özellikleri** yanındaki metin kutusuna penceresinde **Site URL'si** özelliği girin **http://localhost**.  
  
     Bu adım, hata ayıklama için kullanmak istediğiniz geliştirme bilgisayarında yerel SharePoint sitesini belirtir.  
  
    > [!NOTE]  
    >  **Site URL'si** Site sütunu proje şablonu proje oluşturulduğunda, bu değer toplanması için bir sihirbazını sağlamadığından özelliği varsayılan olarak boştur. Bu değer için bir geliştirici ister ve ardından bu özelliği yeni projede yapılandıran bir sihirbaz ekleme konusunda bilgi edinmek için [izlenecek yol: bir proje şablonu, bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Seçin **F5** anahtarı.  
  
     Site sütunu paketlenir ve belirtilen SharePoint sitesine dağıtılan **Site URL'si** projenin özelliği. Web tarayıcısı bu sitenin varsayılan sayfasına açılır.  
  
    > [!NOTE]  
    >  Varsa **betik hata ayıklamasını devre dışı bırakılmış** iletişim kutusu görüntülenirse, seçin **Evet** proje hatalarını ayıklamaya devam etmek için düğme.  
  
4.  Üzerinde **Site eylemleri** menüsünde seçin **Site Ayarları**.  
  
5.  Üzerinde **Site Ayarları** sayfasındaki **galeriler** listesinde **Site sütunları** bağlantı.  
  
6.  Doğrulayın site sütunlar listesinde bir **özel sütunları** adlı bir sütun içeren grubu **SiteColumnTest**.  
  
7.  Web tarayıcısını kapatın.  
  
## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme
 Proje testi tamamladıktan sonra proje şablonu Visual Studio'nun deneysel örneği kaldırın.  
  
#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizleme  
  
1.  Visual Studio'nun Deneysel örneğinin menü çubuğunda seçin **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Uzantılar listesinde seçin **Site sütunu** uzantısı seçip **kaldırma** düğmesi.  
  
3.  Görünen iletişim kutusunda **Evet** uzantının yüklemesini kaldırmak istediğinizi onaylamak için düğme.  
  
4.  Seçin **Kapat** kaldırma işlemini tamamlamak için düğme.  
  
5.  (Deneysel örneği ve Visual Studio'nun SiteColumnProjectItem çözüm açık olduğu örneği) Visual Studio'nun her iki örneklerini kapatın.  
  
## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuzu tamamladıktan sonra sihirbaz proje şablonuna ekleyebilirsiniz. Bir kullanıcı bir Site sütunu proje oluşturduğu zaman, sihirbazın yeni çözümü korumalı olup ve hata ayıklama için kullanılacak site URL'si için kullanıcıdan ve sihirbaz yeni projeyi bu bilgilerle yapılandırır. Sihirbaz aynı zamanda sütun (örneğin, taban türü ve sütun site sütunu galerisinde listelemek grubu) hakkında bilgi toplar ve bu bilgileri ekler *Elements.xml* yeni proje dosyasında. Daha fazla bilgi için [izlenecek yol: bir proje şablonu, bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İzlenecek yol: bir proje şablonu, bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Öğe şablonları ve SharePoint Proje öğeleri için proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [SharePoint Proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint araç uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
