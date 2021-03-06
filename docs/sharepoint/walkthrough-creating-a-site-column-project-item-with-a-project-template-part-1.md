---
title: Proje şablonu, Bölüm 1 ile site sütunu proje öğesi oluştur
titleSuffix: ''
description: Bir site sütunu oluşturmak için bir proje öğesi türü tanımlayın ve ardından Proje öğesini içeren bir SharePoint projesi oluşturmak için kullanılacak bir proje şablonu oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 07f3b90df070eca4e17e5bba9fa6a9e3582bd238
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217807"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>İzlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma
  SharePoint projeleri bir veya daha fazla SharePoint proje öğesi için kapsayıcılardır. Visual Studio 'da, kendi SharePoint proje öğesi türlerinizi oluşturup bunları bir proje şablonuyla ilişkilendirerek SharePoint proje sistemini genişletebilirsiniz. Bu kılavuzda, bir site sütunu oluşturmak için bir proje öğesi türü tanımlayacaksınız ve sonra bir site sütunu proje öğesi içeren yeni bir proje oluşturmak için kullanılabilecek bir proje şablonu oluşturacaksınız.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir site sütunu için yeni bir SharePoint proje öğesi türünü tanımlayan bir Visual Studio uzantısı oluşturma. Proje öğesi türü, **Özellikler** penceresinde görünen basit özel bir özelliği içerir.

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Proje öğesi için proje şablonu oluşturuluyor.

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Proje şablonunu ve uzantı derlemesini dağıtmak için bir uzantı (VSIX) paketi oluşturma.

- Proje öğesini hata ayıklama ve test etme.

  Bu tek başına bir yönergedir. Bu yönergeyi tamamladıktan sonra proje şablonuna bir sihirbaz ekleyerek Proje öğesini geliştirebilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: proje şablonu, Bölüm 2 ile site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Bir dizi örnek iş akışı için bkz. [SharePoint Workflow örnekleri](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Microsoft Windows, SharePoint ve sürümleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu izlenecek yol, Proje öğesini dağıtmak üzere bir VSıX paketi oluşturmak için SDK 'daki **VSIX proje** şablonunu kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavram hakkında bilgi yararlı olur, ancak gerekli değildir:

- SharePoint 'te site sütunları. Daha fazla bilgi için bkz. [sütunlar](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

- Visual Studio 'da proje şablonları. Daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için üç proje oluşturmanız gerekir:

- Bir VSıX projesi. Bu proje, site sütunu proje öğesini ve proje şablonunu dağıtmak için VSıX paketini oluşturur.

- Proje şablonu projesi. Bu proje, site sütunu proje öğesini içeren yeni bir SharePoint projesi oluşturmak için kullanılabilecek bir proje şablonu oluşturur.

- Bir sınıf kitaplığı projesi. Bu proje, site sütunu proje öğesinin davranışını tanımlayan bir Visual Studio uzantısı uygular.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

3. **Yeni proje** iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **4,5 .NET Framework** seçildiğinden emin olun.

4. **Visual Basic** veya **Visual C#** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > **Genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'sını yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

5. Proje şablonları listesinde **VSIX projesi**' ni seçin.

6. **Ad** kutusuna **SiteColumnProjectItem** girin ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**SiteColumnProjectItem** projesini **Çözüm Gezgini** ekler.

#### <a name="to-create-the-project-template-project"></a>Proje şablonu projesi oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **4,5 .NET Framework** seçildiğinden emin olun.

3. **Visual C#** veya **Visual Basic** düğümünü genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

4. Proje şablonları listesinde **C# proje** şablonunu veya **Visual Basic projesi** şablonu şablonunu seçin.

5. **Ad** kutusuna **SiteColumnProjectTemplate** girin ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**SiteColumnProjectTemplate** projesini çözüme ekler.

6. Class1 kod dosyasını projeden silin.

7. Bir Visual Basic projesi oluşturduysanız, projeden aşağıdaki dosyaları da silin:

    - *MyApplication. Designer. vb*

    - MyApplication. MyApp

    - *Resources. Designer. vb*

    - *Resources. resx*

    - *Settings. Designer. vb*

    - Settings. Settings

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **4,5 .NET Framework** seçildiğinden emin olun.

3. **Visual C#** veya **Visual Basic** düğümlerini genişletin, **Windows** düğümünü seçin ve ardından **sınıf kitaplığı** şablonunu seçin.

4. **Ad** kutusuna **projectItemTypeDefinition** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**projectItemTypeDefinition** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Uzantı projesini yapılandırmak için kod dosyalarını ve derleme başvurularını ekleyin.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. ProjectItemTypeDefinition projesinde, **SiteColumnProjectItemTypeProvider** adlı bir kod dosyası ekleyin.

2. Menü çubuğunda **Proje**  >  **Başvuru Ekle**' yi seçin.

3. **Reference Manager-projectItemTypeDefinition** iletişim kutusunda, **derlemeler** düğümünü genişletin, **Framework** düğümünü seçin ve ardından System. ComponentModel. Composition onay kutusunu seçin.

4. **Uzantılar** düğümünü seçin, Microsoft. VisualStudio. SharePoint derlemesinin yanındaki onay kutusunu Işaretleyin ve **Tamam** düğmesini seçin.

## <a name="define-the-new-sharepoint-project-item-type"></a>Yeni SharePoint proje öğesi türünü tanımlayın
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>Yeni proje öğesi türünün davranışını tanımlamak için arabirimini uygulayan bir sınıf oluşturun. Yeni proje öğesi türünü tanımlamak istediğinizde bu arabirimi uygulayın.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Yeni SharePoint proje öğesi türünü tanımlamak için

1. **SiteColumnProjectItemTypeProvider** kod dosyasında, varsayılan kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb" id="Snippet1":::

## <a name="create-a-visual-studio-project-template"></a>Visual Studio proje şablonu oluşturma
 Bir proje şablonu oluşturarak, diğer geliştiricilerin site sütunu proje öğelerini içeren SharePoint projeleri oluşturmalarına olanak tanır. SharePoint proje şablonu, Visual Studio 'daki *. csproj* veya *. vbproj* ve *. vstemplate* dosyaları gibi tüm projeler için gerekli dosyaları ve SharePoint projelerine özgü dosyaları içerir. Daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Bu yordamda, SharePoint projelerine özgü dosyaları oluşturmak için boş bir SharePoint projesi oluşturacaksınız. Daha sonra bu dosyaları, bu projeden oluşturulan şablona dahil olmaları için SiteColumnProjectTemplate projesine eklersiniz. Ayrıca, SiteColumnProjectTemplate proje dosyasını, proje şablonunun **Yeni proje** iletişim kutusunda nerede göründüğünü belirtecek şekilde yapılandırırsınız.

#### <a name="to-create-the-files-for-the-project-template"></a>Proje şablonu dosyalarını oluşturmak için

1. Yönetici kimlik bilgileriyle ikinci bir örneğini başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **BaseSharePointProject** adında bir SharePoint 2010 projesi oluşturun.

   > [!IMPORTANT]
   > **SharePoint Özelleştirme sihirbazında**, **Grup çözümü olarak dağıt** seçenek düğmesini seçmeyin.

3. Projeye boş bir öğe öğesi ekleyin ve ardından öğeyi **alan1** olarak adlandırın.

4. Projeyi kaydedin ve ikinci örneğini kapatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

5. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SiteColumnProjectItem çözümü açık olan örneğinde, **Çözüm Gezgini**' de **SiteColumnProjectTemplate** proje düğümünün kısayol menüsünü açın, **Ekle**' yi seçin ve ardından **Varolan öğe**' yi seçin.

6. **Varolan öğe Ekle** iletişim kutusunda, dosya uzantılarının listesini açın ve **tüm dosyalar ( \* . \* )** öğesini seçin.

7. BaseSharePointProject projesini içeren dizinde Key. snk dosyasını seçin ve sonra **Ekle** düğmesini seçin.

   > [!NOTE]
   > Bu kılavuzda, oluşturduğunuz proje şablonu, şablonu kullanılarak oluşturulan her bir projeyi imzalamak için aynı Key. snk dosyasını kullanır. Her proje örneği için farklı bir Key. snk dosyası oluşturmak üzere bu örneği genişletmeyi öğrenmek için bkz. [Izlenecek yol: proje şablonu, Bölüm 2 ile site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. BaseSharePointProject dizinindeki belirtilen alt klasörlerden aşağıdaki dosyaları eklemek için 5-8 adımlarını yineleyin:

   - *\Field1\Elements.xml*

   - *\Field1\sharepointprojectıtem.exe*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\ Package\package.exe paketi*

   - *\Package\Package.Template.xml*

     Bu dosyaları doğrudan SiteColumnProjectTemplate projesine ekleyin; Projedeki alan1, özellikler veya paket alt klasörlerini yeniden oluşturmayın. Bu dosyalar hakkında daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Geliştiricilerin proje şablonunu yeni proje iletişim kutusunda nasıl bulyacağını yapılandırmak için

1. **Çözüm Gezgini**, **SiteColumnProjectTemplate** proje düğümünün kısayol menüsünü açın ve ardından **Projeyi Kaldır**' ı seçin. Değişiklikleri herhangi bir dosyaya kaydetmeniz istenirse, **Evet** düğmesini seçin.

2. **SiteColumnProjectTemplate** düğümünün kısayol menüsünü yeniden açın ve ardından **SiteColumnProjectTemplate. csproj öğesini Düzenle** ' yi seçin veya **SiteColumnProjectTemplate. vbproj**' i düzenleyin.

3. Proje dosyasında, aşağıdaki `VSTemplate` öğeyi bulun.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Bu öğeyi aşağıdaki XML ile değiştirin.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Öğesi, proje oluşturduğunuzda proje şablonunun oluşturulduğu yolda ek klasörleri belirtir. Burada belirtilen klasörler, proje şablonunun yalnızca müşteriler **Yeni proje** iletişim kutusunu açtıklarında kullanılabilir olacağını, **SharePoint** düğümünü genişlettikten sonra da **2010** düğümünü seçemeyeceğini güvence altına aldığından emin olur.

5. Dosyayı kaydedin ve kapatın.

6. **Çözüm Gezgini**, **SiteColumnProjectTemplate** projesinin kısayol menüsünü açın ve ardından **projeyi yeniden yükle**' yi seçin.

## <a name="edit-the-project-template-files"></a>Proje şablonu dosyalarını düzenleme
 SiteColumnProjectTemplate projesinde, proje şablonunun davranışını tanımlamak için aşağıdaki dosyaları düzenleyin:

- *AssemblyInfo. cs* veya *AssemblyInfo. vb*

- *Elements.xml*

- *SharePointProjectItem. spdata*

- *Özellik1. Feature*

- *Package. Package*

- *SiteColumnProjectTemplate. vstemplate*

- *ProjectTemplate. csproj* veya *ProjectTemplate. vbproj*

  Aşağıdaki yordamlarda, bu dosyalardan bazılarına değiştirilebilen parametreler ekleyeceksiniz. Değiştirilebilir bir parametre, dolar işareti ($) karakteriyle başlayan ve biten bir belirteçtir. Bir Kullanıcı bir proje oluşturmak için bu proje şablonunu kullandığında, Visual Studio yeni projedeki bu parametreleri belirli değerlerle otomatik olarak değiştirir. Daha fazla bilgi için bkz. [değiştirilebilen parametreler](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>AssemblyInfo. cs veya AssemblyInfo. vb dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde *AssemblyInfo. cs* veya *AssemblyInfo. vb* dosyasını açın ve ardından aşağıdaki ifadeyi onun üstüne ekleyin:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Bir SharePoint projesinin **Korumalı çözüm** özelliği **true** olarak ayarlandığında, Visual Studio öğesini <xref:System.Security.AllowPartiallyTrustedCallersAttribute> AssemblyInfo kod dosyasına ekler. Ancak Proje şablonundaki AssemblyInfo kod dosyası, <xref:System.Security> Varsayılan olarak ad alanını içeri aktarmaz. Derleme hatalarını engellemek için bu **using** veya **Imports** ifadesini eklemeniz gerekir.

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-elementsxml-file"></a>Elements.xml dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde *Elements.xml* dosyasının IÇERIĞINI aşağıdaki XML ile değiştirin.

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

     Yeni XML, `Field` site sütununun adını, temel türünü ve galerisindeki site sütununun listekaydedileceği grubu tanımlayan bir öğe ekler. Bu dosyanın içeriği hakkında daha fazla bilgi için bkz. [alan tanımı şeması](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14)).

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>SharePointProjectItem. spdata dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde, *SharePointProjectItem. spdata* dosyasının IÇERIĞINI aşağıdaki XML ile değiştirin.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Yeni XML, dosyasında aşağıdaki değişiklikleri yapar:

   - `Type`Öğesi özniteliğini, `ProjectItem` <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> Proje öğesi tanımında ( `SiteColumnProjectItemTypeProvider` Bu kılavuzda daha önce oluşturduğunuz sınıf) kendisine geçirilen aynı dizeye dönüştürür.

   - `SupportedTrustLevels`Ve `SupportedDeploymentScopes` özniteliklerini `ProjectItem` öğesinden kaldırır. Bu öznitelik değerleri, `SiteColumnProjectItemTypeProvider` projectItemTypeDefinition projesindeki sınıfında güven düzeyleri ve dağıtım kapsamları belirtildiğinden gereksizdir.

     *. Spdata* dosyalarının içerikleri hakkında daha fazla bilgi için bkz. [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-feature1feature-file"></a>Özellik1. feature dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde, *özellik1. feature* dosyasının IÇERIĞINI aşağıdaki XML ile değiştirin.

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

    Yeni XML, dosyasında aşağıdaki değişiklikleri yapar:

   - `Id`Öğesi ve özniteliklerinin değerlerini olarak değiştirir `featureId` `feature` `$guid4$` .

   - `itemId`Öğesi özniteliğinin değerlerini `projectItemReference` olarak değiştirir `$guid2$` .

     *. Feature* dosyaları hakkında daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-packagepackage-file"></a>Package. Package dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde, *Package. Package* dosyasının IÇERIĞINI aşağıdaki XML ile değiştirin.

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

    Yeni XML, dosyasında aşağıdaki değişiklikleri yapar:

   - `Id`Öğesi ve özniteliklerinin değerlerini olarak değiştirir `solutionId` `package` `$guid3$` .

   - `itemId`Öğesi özniteliğinin değerlerini `featureReference` olarak değiştirir `$guid4$` .

     *. Package* dosyaları hakkında daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>SiteColumnProjectTemplate. vstemplate dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde, SiteColumnProjectTemplate. vstemplate dosyasının içeriğini XML 'nin aşağıdaki bölümlerinden biriyle değiştirin.

   - Visual C# proje şablonu oluşturuyorsanız, aşağıdaki XML 'i kullanın.

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

   - Visual Basic proje şablonu oluşturuyorsanız, aşağıdaki XML 'i kullanın.

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

    Yeni XML, dosyasında aşağıdaki değişiklikleri yapar:

   - `Name`Öğesini değer **site sütununa** ayarlar. (Bu ad **Yeni proje** iletişim kutusunda görünür).

   - `ProjectItem`Her bir proje örneğine dahil edilen her bir dosya için öğe ekler.

   - Ad alanını kullanır `http://schemas.microsoft.com/developer/vstemplate/2005` . Bu çözümdeki diğer proje dosyaları `http://schemas.microsoft.com/developer/msbuild/2003` ad alanını kullanır. Bu nedenle, XML şeması uyarı iletileri oluşturulacaktır, ancak bu kılavuzda yoksayabilirsiniz.

     *. Vstemplate* dosyalarının içerikleri hakkında daha fazla bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md).

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>ProjectTemplate. csproj veya ProjectTemplate. vbproj dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde, *ProjectTemplate. csproj* dosyasının veya *ProjectTemplate. vbproj* dosyasının içeriğini XML 'nin aşağıdaki bölümlerinden biriyle değiştirin.

    - Visual C# proje şablonu oluşturuyorsanız, aşağıdaki XML 'i kullanın.

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

    1. Visual Basic proje şablonu oluşturuyorsanız, aşağıdaki XML 'i kullanın.

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

     Yeni XML, dosyasında aşağıdaki değişiklikleri yapar:

    - , `TargetFrameworkVersion` 4,5 değil 3,5 .NET Framework belirtmek için öğesini kullanır.

    - `SignAssembly` `AssemblyOriginatorKeyFile` Proje çıkışını imzalamak için ve öğeleri ekler.

    - `Reference`SharePoint projelerinin kullandığı derleme başvuruları için öğeler ekler.

    - Projedeki her bir varsayılan dosya için öğeler ekler; örneğin, *Elements.xml* ve *SharePointProjectItem. spdata*.

2. Dosyayı kaydedin ve kapatın.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Proje şablonunu dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, **SiteColumnProjectItem** çözümünde VSIX projesi ' ni kullanarak bir VSIX paketi oluşturun. İlk olarak, VSIX projesinde bulunan kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSıX paketini yapılandırmak ve oluşturmak için

1. **Çözüm Gezgini**, **SiteColumnProjectItem** projesinde, bildirim düzenleyicisinde source. Extension. valtmanifest dosyasını açın.

     Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)).

2. **Ürün adı** kutusuna **site sütununu** girin.

3. **Yazar** kutusuna **contoso** girin.

4. **Açıklama** kutusunda, **site sütunları oluşturmak için bir SharePoint projesi** girin.

5. **Varlıklar** sekmesini seçin ve ardından **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

6. **Tür** listesinde, **Microsoft. VisualStudio. ProjectTemplate**' i seçin.

    > [!NOTE]
    > Bu değer, `ProjectTemplate` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe, proje şablonunu içeren VSıX paketindeki alt klasörü tanımlar. Daha fazla bilgi için bkz. [ProjectTemplate öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

8. **Proje** listesinde, **SiteColumnProjectTemplate**' i ve sonra **Tamam** düğmesini seçin.

9. **Yeni** düğmesini yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

10. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

12. **Proje** listesinde **projectItemTypeDefinition**' ı seçin ve ardından **Tamam** düğmesini seçin.

13. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından projenin hatasız derlendiğinden emin olun.

## <a name="test-the-project-template"></a>Proje şablonunu test etme
 Artık proje şablonunu test etmeye hazırsınız. İlk olarak, Visual Studio 'nun deneysel örneğinde SiteColumnProjectItem çözümünde hata ayıklamaya başlayın. Daha sonra, **site sütunu** projesini Visual Studio 'nun deneysel örneğinde test edin. Son olarak, site sütununun beklendiği gibi çalıştığını doğrulamak için SharePoint projesini derleyin ve çalıştırın.

#### <a name="to-start-debugging-the-solution"></a>Çözümdeki hata ayıklamayı başlatmak için

1. Visual Studio 'Yu yönetici kimlik bilgileriyle yeniden başlatın ve ardından SiteColumnProjectItem çözümünü açın.

2. SiteColumnProjectItemTypeProvider kod dosyasında, yöntemdeki kodun ilk satırına bir kesme noktası ekleyin `InitializeType` ve ardından hata ayıklamayı başlatmak Için **F5** tuşunu seçin.

     Visual Studio, uzantıyı%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 konumuna yükleyerek Visual Studio 'nun deneysel bir örneğini başlatır. Bu Visual Studio örneğinde Proje öğesini test edersiniz.

#### <a name="to-test-the-project-in-visual-studio"></a>Projeyi Visual Studio 'da test etmek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

2. **Visual C#** veya **Visual Basic** düğümünü (proje şablonunuzun desteklediği dile bağlı olarak) genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. Proje şablonları listesinde, **site sütunu** şablonunu seçin.

4. **Ad** kutusuna **SiteColumnTest** girin ve **Tamam** düğmesini seçin.

     **Çözüm Gezgini** Içinde, **alan1** adlı bir proje öğesiyle yeni bir proje görüntülenir.

5. Visual Studio 'nun diğer örneğindeki kodun, yönteminde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `InitializeType` ve sonra projede hata ayıklamaya devam etmek Için **F5** tuşunu seçin.

6. **Çözüm Gezgini**, **alan1** düğümünü seçin ve sonra **F4** tuşunu seçin.

     **Özellikler** penceresi açılır.

7. Özellikler listesinde, Property **example özelliğinin** göründüğünü doğrulayın.

#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint 'te site sütununu test etmek için

1. **Çözüm Gezgini**, **SiteColumnTest** düğümünü seçin.

2. **Özellikler** penceresinde, **site URL** özelliğinin yanındaki metin kutusunda, girin **http://localhost** .

     Bu adım, geliştirme bilgisayarında hata ayıklama için kullanmak istediğiniz yerel SharePoint sitesini belirtir.

    > [!NOTE]
    > Site sütunu proje şablonu proje oluşturulduğunda bu değerin toplanması için bir sihirbaz sağlamadığından, **site URL 'si** özelliği varsayılan olarak boştur. Geliştiriciyi bu değere soran bir sihirbaz ekleme ve sonra bu özelliği yeni projede yapılandırma hakkında bilgi edinmek için bkz. [Izlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. **F5** tuşunu seçin.

     Site sütunu paketlenir ve projenin **site URL 'si** özelliğinde belirtilen SharePoint sitesine dağıtılır. Web tarayıcısı, bu sitenin varsayılan sayfasına açılır.

    > [!NOTE]
    > **Betik hata ayıklaması devre dışı** iletişim kutusu görüntülenirse, projede hata ayıklamaya devam etmek için **Evet** düğmesini seçin.

4. **Site eylemleri** menüsünde, **site ayarları**' nı seçin.

5. **Site ayarları** sayfasında, **galeriler** listesinde, **site sütunları** bağlantısını seçin.

6. Site sütunları listesinde, **özel bir sütun** grubunun **SiteColumnTest** adlı bir sütun içerdiğini doğrulayın.

7. Web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Projeyi test etmeyi tamamladıktan sonra, Visual Studio 'nun deneysel örneğinden proje şablonunu kaldırın.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizlemek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde, **site sütunu** uzantısını seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin.

4. Kaldırma işlemini gerçekleştirmek için **Kapat** düğmesini seçin.

5. Visual Studio 'nun her iki örneğini (deneysel örnek ve SiteColumnProjectItem çözümünün açık olduğu Visual Studio örneği) kapatın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu yönergeyi tamamladıktan sonra, proje şablonuna bir sihirbaz ekleyebilirsiniz. Bir Kullanıcı bir site sütun projesi oluşturduğunda, sihirbaz kullanıcıdan hata ayıklama için kullanacağı site URL 'sini ve yeni çözümün korumalı olup olmadığını sorar ve sihirbaz yeni projeyi bu bilgilerle yapılandırır. Sihirbaz ayrıca sütun hakkındaki bilgileri (temel tür ve sütunun site sütunu galerisinde listekaydedileceği grup gibi) toplar ve bu bilgileri yeni projedeki *Elements.xml* dosyasına ekler. Daha fazla bilgi için bkz. [Izlenecek yol: proje şablonu, Bölüm 2 ile site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint Araç Uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)