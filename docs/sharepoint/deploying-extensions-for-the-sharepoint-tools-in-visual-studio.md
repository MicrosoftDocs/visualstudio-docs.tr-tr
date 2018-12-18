---
title: Visual Studio'da SharePoint araçları için hata ayıklama uzantıları | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3bf20f945c40dd963820b1bf3f4032a2dd517ca
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295975"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio'da SharePoint araçları için uzantıları dağıtma

SharePoint araçları uzantısının dağıtmak için oluşturun bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantı derlemesini ve uzantısıyla dağıtmak istediğiniz diğer tüm dosyaları içeren uzantısı (VSIX) paketini. Bir VSIX paketi açık paketleme kuralları (OPC) standart sıkıştırılmış bir dosyadır. VSIX paketlerini sahip *.vsix* uzantısı.

Bir VSIX paketi oluşturduktan sonra diğer kullanıcıların, uzantıyı yüklemek için .vsix dosyasını çalıştırabilirsiniz. Bir kullanıcı, uzantı yüklendiğinde, tüm dosyaları %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions klasörüne yüklenir. Uzantıyı dağıtmak için VSIX paketi yükleyebilirsiniz [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesi veya dağıtabilirsiniz paketi müşterileriniz için başka bir yöntemle paketini bir ağ paylaşımına veya başka bir Web sitesi barındırma gibi bazı.

VSIX paketlerini oluşturma ve bunları dağıtma hakkında daha fazla bilgi için [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847), bkz: [sevkiyat Visual Studio uzantıları](../extensibility/shipping-visual-studio-extensions.md).

 Bir VSIX paketi kullanarak oluşturabileceğiniz **VSIX projesi** Visual Studio ya da şablon oluşturabilirsiniz bir VSIX paketi el ile.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>VSIX paketlerini oluşturmak için VSIX projeleri kullanın

Kullanabileceğiniz **VSIX projesi** Visual Studio SharePoint araçları uzantıları için VSIX paketleri oluşturmak için SDK'sı tarafından sağlanan şablon. Bir VSIX projesi kullanarak, bir VSIX paketi el ile oluşturma üzerinde çeşitli avantajlar sunar:

-   Proje oluşturduğunuzda visual Studio, VSIX paketini otomatik olarak oluşturur. Paket için dağıtım dosyaları ekleme ve [Content_Types] .xml dosyası için paket oluşturma gibi görevleri sizin yerinize gerçekleştirilir.

-   VSIX projesi, uzantı projesi ve proje şablonları ve öğe şablonları gibi diğer dosyaları yapı çıkışını VSIX paket içerisine dâhil etmek yapılandırabilirsiniz.

Bir VSIX projesi kullanma hakkında daha fazla bilgi için bkz. [VSIX proje şablonu](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Projelerinizi düzenleme

Varsayılan olarak, VSIX projeleri yalnızca VSIX paketlerini değil derlemeleri oluşturun. Bu nedenle, genellikle bir SharePoint araçları uzantısının bir VSIX projesinde kullanılmaz. Genellikle, en az iki projeleriyle de çalışır:

-   VSIX projesi.

-   Uzantınızı uygulayan bir sınıf kitaplığı projesi.

Ek projeleri ile aynı zamanda belirli ve uzantı türlerini çalışabilir:

-   Uzantınız tarafından kullanılan herhangi bir SharePoint komut uygulayan bir sınıf kitaplığı projesi. Bu senaryoyu gösteren bir kılavuz için bkz. [izlenecek yol: Sunucu Gezgini web bölümlerini görüntülemek üzere genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

-   Uzantınızı yeni bir SharePoint proje öğesi türü tanımlıyorsa oluşturan bir öğe şablonu veya proje şablonu, bir öğe şablonu veya proje şablonu projesi. Bu senaryoyu gösteren bir kılavuz için bkz. [izlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

-   Bir öğe şablonu veya proje şablonu, özel bir sihirbazın uzantınızı bir şablon içeriyorsa uygulayan bir sınıf kitaplığı projesi. Bu senaryoyu gösteren bir kılavuz için bkz. [izlenecek yol: bir öğe şablonu, bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Tüm projeleri aynı Visual Studio çözümünde eklerseniz, sınıf kitaplığı projeleri derleme çıktısını dahil etmek için VSIX projesinde source.extension.vsixmanifest dosyasını değiştirebilirsiniz.

### <a name="edit-the-vsix-manifest"></a>VSIX bildirimini Düzenle

Uzantınızı eklemek istediğiniz tüm öğeler için girişlerini dahil etmek için VSIX projesinde source.extension.vsixmanifest dosyasını düzenlemeniz gerekir. Kısayol menüsünden source.extension.vsixmanifest dosyasını açtığınızda, dosya dosyasındaki XML düzenleme için bir kullanıcı Arabirimi sağlayan bir Tasarımcısı'nda görünür. Daha fazla bilgi için [VSIX bildirim Tasarımcısı](../extensibility/vsix-manifest-designer.md).

Aşağıdaki öğeler için source.extension.vsixmanifest dosyası girdileri eklemeniz gerekir:

-   Uzantı derlemesini.

-   Uzantınız tarafından kullanılan herhangi bir SharePoint komut uygulayan derleme.

-   Tüm proje şablonları veya sizin uzantısıyla ilişkili olan öğe şablonları.

-   Uzantınız ile ilişkili olan bir şablon için özel bir sihirbaz.

Aşağıdaki yordamlar, girişleri için .vsixmanifest dosyasının bu öğelerin her biri için ekleme işlemi açıklanmaktadır.

#### <a name="to-include-the-extension-assembly"></a>Uzantı derlemesini eklemek için

1.  VSIX projesinde source.extension.vsixmanifest dosyası için kısayol menüsünü açın ve ardından **açın**.

     Dosyası tasarımcıda açılır

2.  Üzerinde **varlıklar** sekmesini düzenleyicinin seçin **yeni** düğmesi.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3.  İçinde **türü** listesinde **Microsoft.VisualStudio.MefComponent**.

4.  İçinde **kaynak** listesinde, aşağıdaki adımlardan birini gerçekleştirin:

    -   Uzantı derlemesini VSIX projesi aynı çözümde bir Proje oluşturulur, seçim **mevcut çözümde bir proje**. İçinde **proje** listesinde, proje adını seçin.

    -   Uzantı derlemesini, projenizdeki bir dosya olarak dahil ise seçin **FileSystem'daki**. İçinde **yolu** listesinde, uzantı derleme dosyasının tam yolunu girin veya bunları kullanmanızı **Gözat** düğmesine bulun ve derleme dosyasını seçin.

5.  Seçin **Tamam** düğmesi.

#### <a name="to-include-a-sharepoint-command-assembly"></a>Bir SharePoint komutu derlemeyi dahil etmek için

1.  VSIX projesinde source.extension.vsixmanifest dosyası için kısayol menüsünü açın ve ardından **açın** düğmesi.

     Dosyası tasarımcıda açılır.

2.  İçinde **varlıklar** bölümü düzenleyicinin seçin **yeni** düğmesi.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3.  İçinde **türü** kutusuna **SharePoint.Commands.v4**.

4.  İçinde **kaynak** listesinde, aşağıdaki adımlardan birini gerçekleştirin:

    -   Komut derleme VSIX projesi aynı çözümde bir Proje oluşturulur, seçim **mevcut çözümde bir proje**. İçinde **proje** listesinde, proje adını seçin.

    -   Komut derleme projenize bir dosya olarak dahil edilen ise seçin **FileSystem'daki**. İçinde **yolu** listesinde, uzantı derleme dosyasının tam yolunu girin veya bunları kullanmanızı **Gözat** düğmesine bulun ve derleme dosyasını seçin.

5.  Seçin **Tamam** düğmesi.

#### <a name="to-include-a-template-that-you-create"></a>Oluşturduğunuz bir şablonu eklemek için

1.  VSIX projesinde source.extension.vsixmanifest dosyası için kısayol menüsünü açın ve ardından **açın** düğmesi.

     Dosyası tasarımcıda açılır.

2.  İçinde **varlıklar** bölümü düzenleyicinin seçin **yeni** düğmesi.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3.  İçinde **türü** listesinde **Microsoft.VisualStudio.ProjectTemplate** veya **Microsoft.VisualStudio.ItemTemplate**.

4.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.

5.  İçinde **proje** listesinde, proje adını seçin ve ardından **Tamam** düğmesi.

6.  İçinde **Çözüm Gezgini**, proje şablonu veya öğe şablonu projeniz için kısayol menüsünü açın ve ardından **projeyi**.

7.  Yeniden proje düğümü için kısayol menüsünü açın ve ardından **Düzenle**_YourTemplateProjectName_**.csproj** veya **Düzenle**  _YourTemplateProjectName_**.vbproj**.

8.  Aşağıdaki bulun `VSTemplate` proje dosyasındaki öğesi.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Bu öğe aşağıdaki XML ile değiştirin.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` Öğesi altında proje şablonu oluşturulan proje oluşturduğunuzda yolunda ek klasörleri belirtir. Burada belirtilen klasörleri yalnızca müşterilerin açtığınızda öğe şablonu kullanılabilir olmasını sağlamak **Yeni Proje Ekle** iletişim kutusunda **SharePoint** düğümünü seçip **2010**  düğümü.

10. Dosyayı kaydedin ve kapatın.

11. İçinde **Çözüm Gezgini**, öğe Şablonu proje şablonu projesi için kısayol menüsünü açın ve ardından **projeyi**.

#### <a name="to-include-a-template-that-you-create-manually"></a>El ile oluşturduğunuz bir şablonu eklemek için

1.  VSIX projesinde yeni bir klasör, şablonu içeren projeye ekleyin.

2.  Bu yeni klasörü altında aşağıdaki alt klasörlere oluşturun ve ardından şablonu (.zip) dosyasına ekleyin *yerel ayar kimliği* klasör.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *Yerel ayar kimliği*

     *YourTemplateName*.zip

     Örneğin, İngilizce (Amerika Birleşik Devletleri) yerel ayarı destekler ContosoCustomAction.zip adlı bir öğe şablonunu varsa, tam yol olabilir *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3.  İçinde **Çözüm Gezgini**, şablon dosyası seçin (*YourTemplateName*.zip).

4.  İçinde **özellikleri** penceresinde **derleme eylemi** özelliğini **içerik**.

5.  Source.extension.vsixmanifest dosyası için kısayol menüsünü açın ve ardından **açık**.

     Dosyası tasarımcıda açılır.

6.  İçinde **varlıklar** bölümü düzenleyicinin seçin **yeni** düğmesi.

     **Yeni varlık Ekle** iletişim kutusu açılır.

7.  İçinde **türü** listesinde **Microsoft.VisualStudio.ItemTemplate** veya **Microsoft.VisualStudio.ProjectTemplate**.

8.  İçinde **kaynak** listesinde **FileSystem'daki**.

9. İçinde **yolu** derlemeye tam yolunu girin (örneğin, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, veya **Gözat**düğmesini bulun ve derlemeyi seçin ve ardından **Tamam** düğmesi.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Bir proje şablonu veya öğe şablonu sihirbaz eklemek için

1.  VSIX projesinde source.extension.vsixmanifest dosyası için kısayol menüsünü açın ve ardından **açın**.

     Dosyası tasarımcıda açılır.

2.  İçinde **varlıklar** bölümü düzenleyicinin seçin **yeni** düğmesi.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3.  İçinde **türü** listesinde **Microsoft.VisualStudio.Assembly**.

4.  İçinde **kaynak** listesinde, aşağıdaki adımlardan birini gerçekleştirin:

    -   VSIX projesi aynı çözümde bir Proje Sihirbazı derleme oluşturulur, seçin **mevcut çözümde bir proje**. İçinde **proje** listesinde, proje adını seçin.

    -   Sihirbazı derleme dosyası projenize olarak dahil ise, seçin **FileSystem'daki**. İçinde **yolu** alan, derleme dosyasının tam yolunu girin veya bunları kullanmanızı **Gözat** düğmesine bulun ve derlemeyi seçin.

5.  Seçin **Tamam** düğmesi.

### <a name="related-walkthroughs"></a>İlgili izlenecek yollar

Aşağıdaki tablo, bir VSIX projesi SharePoint araç uzantıları farklı türde dağıtmak için nasıl kullanılacağını gösteren izlenecek yollar listeler.

|Uzantı türü|İlgili izlenecek yollar|
|--------------------|--------------------------|
|Uzantı derlemesini içeren bir uzantı|[İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [İzlenecek yol: bir SharePoint proje uzantısı oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [İzlenecek yol: bir sunucu Gezgini uzantısında SharePoint istemcisi nesne modelini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|SharePoint komutları içeren bir uzantı|[İzlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [İzlenecek yol: Sunucu Gezgini, web bölümlerini görüntülemek üzere genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [İzlenecek yol: bir proje şablonu, bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Visual Studio şablonu içeren bir uzantı|[İzlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [İzlenecek yol: bir proje şablonu, bölüm 1 ile bir Site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|İçeren bir şablon Sihirbazı uzantısı|[İzlenecek yol: bir öğe şablonu, bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [İzlenecek yol: bir proje şablonu, bölüm 2 ile bir Site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>VSIX paketlerini el ile oluşturma

El ile için SharePoint araçları uzantınızı VSIX paketi oluşturmak istiyorsanız, aşağıdaki adımları gerçekleştirin:

1.  .Vsixmanifest uzantı dosyası ve [Content_Types] .xml dosyasının içinde yeni bir klasör oluşturun. Daha fazla bilgi için [bir VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md).

2.  Windows Gezgini'nde, iki XML dosyalarını içeren klasörü sağ tıklatın, göndermek için tıklayın ve ardından sıkıştırılmış klasöre tıklayın. Elde edilen .zip dosyasının dosya adı, paket yükleyen yeniden dağıtılabilir dosyasının adı olduğu Filename.vsix için yeniden adlandırın.

3.  VSIX paketi, uzantı derlemesini ekleyin. Uzantınızı bir SharePoint komutu içeriyorsa, ayrıca SharePoint komutu VSIX paketini uygulayan derlemeye ekleyin.

4.  .Vsixmanifest uzantı dosyası değiştirin:

    -   Ekleme bir `Microsoft.VisualStudio.MefComponent` öğesi altında `Assets` öğesine ve sonra uzantınızı VSIX paketinde uygulayan derlemenin göreli yolu yeni öğenin değeri ayarlayın. Daha fazla bilgi için [MEFComponent öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    -   Uzantınız için SharePoint sunucu nesne modeline çağıran bir SharePoint komutu varsa ekleme bir `Microsoft.VisualStudio.Assembly` öğesi altında `Assets` öğesi. Yeni bir öğe VSIX paketinde SharePoint komutunun uygulayan derlemeye göreli yoluna ayarlayın. Daha fazla bilgi için [varlık öğesi (VSX şema)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

    -   Uzantınızı bir proje şablonu veya öğe şablonu içeriyorsa, ekleme bir `ProjectTemplate` veya `ItemTemplate` öğesi altında `Assets` öğesi. Yeni öğenin değeri şablonda bir VSIX paketini içeren klasörün göreli yoluna ayarlayın. Daha fazla bilgi için [ProjectTemplate öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) ve [ItemTemplate öğesi (VSX şema)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    -   Uzantınızı bir proje şablonu veya öğe şablonu için özel bir sihirbazın içeriyorsa, ekleme bir `Assembly` öğesi altında `Assets` öğesi. Yeni öğenin değerini VSIX paketini derlemenin göreli yoluna ayarlayın ve ardından `AssemblyName` özniteliği (sürüm, kültür ve ortak anahtar belirteci dahil olmak üzere) tam derleme adı. Daha fazla bilgi için [Dependency öğesi (VSX şema)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Örnek

Aşağıdaki örnek, bir SharePoint araçları uzantısının bir extension.vsixmanifest dosyasının içeriğini gösterir. Uzantı Contoso.ProjectExtension.dll adlı bir derlemede uygulanır. Uzantı Contoso.ExtensionCommands.dll ve adlı bir klasör altındaki bir öğe şablonunu adlı bir SharePoint komutu derleme içerir **öğe şablonları** VSIX paketinde. Bu örnek de VSIX paketinde.vsixmanifest uzantı dosyası ile aynı klasörde olduğunu varsayar.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint Proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Uzantıları Visual Studio'da SharePoint araçları için hata ayıklama](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
