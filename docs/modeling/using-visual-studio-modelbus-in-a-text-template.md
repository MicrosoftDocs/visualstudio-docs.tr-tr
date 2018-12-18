---
title: Metin şablonunda ModelBus kullanma
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8aed2920e7be177fdbccc9b71796e58cf103e846
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057600"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Metin Şablonunda Visual Studio ModelBus'ı Kullanma
Visual Studio Modelbus'ı başvurular içeren bir modeli okumak metin şablonlar yazarsanız, hedef modelleri erişmek için başvuruları çözümlemek isteyebilirsiniz. Bu durumda, metin şablonlarını ve başvurulan etki alanına özgü diller (DSL) uyarlamak için gerekenler:

-   Hedefi olan başvuruları DSL erişim metin şablonları için yapılandırılmış bir ModelBus bağdaştırıcısı olmalıdır. DSL de başka bir koddan erişirseniz, yeniden yapılandırılmış bağdaştırıcısı ek olarak standart ModelBus bağdaştırıcısı gereklidir.

     Bağdaştırıcı Yöneticisi devralmalıdır <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> ve özniteliği olmalıdır `[HostSpecific(HostName)]`.

-   Şablon devralmalıdır <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.

> [!NOTE]
>  ModelBus başvuruları içermez DSL modeli okumak istiyorsanız, DSL projelerinizde oluşturulan yönerge işlemcileri kullanabilirsiniz. Daha fazla bilgi için [metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md).

 Metin şablonları hakkında daha fazla bilgi için bkz. [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Metin şablonlarından erişim için bir Model veri yolu bağdaştırıcısı oluşturma
 Metin şablonunda ModelBus başvuru çözmek için ' % s'hedefi DSL uyumlu bir bağdaştırıcı olmalıdır. Metin şablonları, Visual Studio belge Düzenleyicisi'nden ayrı bir AppDomain içinde yürütün ve bu nedenle bağdaştırıcı DTE erişmek yerine modeli yük gerekir.

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Metin şablonları ile uyumlu bir ModelBus bağdaştırıcısı oluşturmak için

1.  ' % S'hedef DSL çözümü yoksa bir **ModelBusAdapter** proje, Modelbus uzantısı Sihirbazı'nı kullanarak bir tane oluşturun:

    1.  İndirip, zaten bunu yapmadıysanız, Visual Studio ModelBus uzantısı yükleyin. Daha fazla bilgi için [Görselleştirme ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkID=185579).

    2.  DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve ardından **etkinleştirme Modelbus**.

    3.  İletişim kutusunda **bu DSL için ModelBus kullanıma sunmak istediğiniz**. Bu DSL modellerinin kullanıma sunmak ve diğer DSL'ler başvurular kullanmak istiyorsanız, iki seçenek de seçebilirsiniz.

    4.  **Tamam**'ı tıklatın. Yeni bir proje "ModelBusAdapter" DSL çözüme eklenir.

    5.  Tıklayın **tüm şablonları dönüştürme**.

    6.  Çözümü yeniden derleyin.

2.  Bir metin şablonu ve komutu gibi başka kodları DSL erişmek istiyorsanız yinelenen **ModelBusAdapter** proje:

    1.  Windows Gezgini'nde kopyalayıp içeren klasöre **ModelBusAdapter.csproj**.

    2.  Proje dosyasını yeniden adlandırın (örneğin, **T4ModelBusAdapter.csproj**).

    3.  İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, fareyle **Ekle**ve ardından **mevcut proje**. Yeni bağdaştırıcı projesi bulun **T4ModelBusAdapter.csproj**.

    4.  Her `*.tt` dosya yeni projeyi, ad alanını değiştirme.

    5.  Yeni Çözüm Gezgini'nde projeye sağ tıklayın ve ardından Özellikler seçeneğine tıklayın. Özellik Düzenleyicisi'nde oluşturulan derleme ve varsayılan ad alanı adını değiştirin.

    6.  Her iki bağdaştırıcı başvuruları sahip olacak şekilde DslPackage projede yeni bağdaştırıcı projeye bir başvuru ekleyin.

    7.  DslPackage\source.extension.tt içinde yeni bağdaştırıcı projeniz başvuran bir satır ekleyin.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8.  **Tüm Şablonları dönüştürme** ve çözümü yeniden oluşturun. Derleme hataları gerçekleşmelidir.

3.  Yeni bağdaştırıcı projesinde aşağıdaki derlemelere başvurular ekleyin:

    -   Microsoft.VisualStudio.TextTemplating.11.0

         Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4.  AdapterManager.tt içinde:

    -   AdapterManagerBase bildirimini değiştirin, böylece devraldığı <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    -   Dosyanın sonuna AdapterManager sınıfı önce HostSpecific özniteliği değiştirin. Şu satırı kaldırın:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Aşağıdaki satırı ekleyin:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Bu öznitelik modelbus tüketici için bir bağdaştırıcı aradığında, kullanılabilen bağdaştırıcıları kümesini filtreler.

5.  **Tüm Şablonları dönüştürme** ve çözümü yeniden oluşturun. Derleme hataları gerçekleşmelidir.

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>ModelBus başvuruları çözümlemek için metin şablonu yazma
 Genellikle, okuyan ve bir "kaynak" DSL dosyaları oluşturan bir şablon ile başlayın. İçinde açıklanan şekilde kaynak model dosyaları okumak için kaynak DSL projesi oluşturulur yönergesi bu şablonu kullanan [metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md). Ancak, kaynak DSL bir "hedef" DSL ModelBus başvurular içerir. Bu nedenle başvurularını çözümlemek ve hedef DSL erişmek şablon kodunu etkinleştirmek istiyorsunuz. Bu nedenle aşağıdaki adımları izleyerek şablonu uyarlamanız gerekir:

-   Şablona temel sınıfını değiştirmek <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.

-   Dahil `hostspecific="true"` şablon yönergesinde.

-   ' % S'hedef DSL ve onun bağdaştırıcısı ve Modelbus'ı etkinleştirmek için derleme başvuruları ekleyin.

-   DSL hedef bir parçası olarak oluşturulan yönergesi gerekli değildir.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 Bu metin şablonu yürütüldüğünde, `SourceDsl` yönergesi, bir dosya yükler `Sample.source`. Şablon başlayarak, bu model öğelerine erişebilirsiniz `this.ModelRoot`. Kod etki alanı sınıfları ve bu DSL özelliklerini kullanabilirsiniz.

 Ayrıca, şablonu ModelBus başvuruları çözebilirsiniz. Hedef model için başvuru noktası olduğunda, etki alanı sınıfları ve bu modelin DSL özelliklerini kullanmak kod derleme yönergeleri sağlar.

-   DSL projesi tarafından üretilen bir yönerge kullanmazsanız, aynı zamanda içermelidir.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

-   Kullanım `this.ModelBus` ModelBus erişimi elde edilir.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>İzlenecek yol: Modelbus'ı kullanan bir metin şablonu test etme
 Bu kılavuzda, aşağıdaki adımları izleyin:

1.  İki DSL'ler oluşturun. Bir DSL *tüketici*, sahip bir `ModelBusReference` diğer DSL başvurabilir özelliği *sağlayıcısı*.

2.  Sağlayıcı iki ModelBus bağdaştırıcısı oluşturma: erişim metin şablonları, sıradan bir kod için.

3.  DSL örneği modelleri tek bir Deneysel projesi oluşturun.

4.  Bir alan özelliği bir modeldeki diğer modele işaret edecek şekilde ayarlayın.

5.  İşaret edilen modeli açılan bir çift tıklama işleyicisi yazma.

6.  Birinci modelin yük, diğer bir Modeli'ne başvuru izleyin ve diğer modeli okumak bir metin şablonu yazarsınız.

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>ModelBus için erişilebilir olan bir DSL oluşturun

1. Yeni bir DSL çözümü oluşturun. Bu örnekte, Görev akışı çözüm şablonu seçin. Dil adı kümesine `MBProvider` ve ".provide" için dosya adı uzantısı.

2. DSL tanım diyagramı üst kısımda yer almayan diyagramın boş bir bölümüne sağ tıklayın ve ardından **etkinleştirme Modelbus**.

   -   Görmüyorsanız, **etkinleştirme Modelbus**, indirip VMSDK ModelBus uzantısını yüklemeniz gerekir. VMSDK sitesinde bulabilirsiniz: [Görselleştirme ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkID=185579).

3. İçinde **Modelbus'ı etkinleştirme** iletişim kutusunda **bu DSL için ModelBus kullanıma**ve ardından **Tamam**.

    Yeni bir proje `ModelBusAdapter`, çözüme eklenir.

   Artık ModelBus metin şablonlarını tarafından erişilebilecek bir DSL var. Komutlar, olay işleyicileri veya model dosya Düzenleyicisi AppDomain içinde çalışan tüm kuralları, kod başvuruları çözümlenebilir. Bununla birlikte, metin şablonları ayrı bir AppDomain içinde çalıştırın ve onu düzenlenirken bir model erişemez. Bu DSL ModelBus başvurular bir metin şablonundan erişmek istiyorsanız, ayrı bir ModelBusAdapter olması gerekir.

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Metin şablonları için yapılandırılmış bir ModelBus bağdaştırıcısı oluşturmak için

1. Windows Gezgini'nde, kopyalayın ve ModelBusAdapter.csproj içeren klasöre yapıştırın.

    T4ModelBusAdapter klasörün adı.

    Proje dosyası T4ModelBusAdapter.csproj yeniden adlandırın.

2. Çözüm Gezgini'nde T4ModelBusAdapter MBProvider çözüme ekleyin. Çözüm düğümüne sağ tıklayın, fareyle **Ekle**ve ardından **mevcut proje**.

3. T4ModelBusAdapter proje düğümüne sağ tıklayın ve ardından Özellikler seçeneğine tıklayın. Proje Özellikleri penceresinde **derleme adı** ve **varsayılan Namespace** için `Company.MBProvider.T4ModelBusAdapters`.

4. Satır aşağıdakine benzer olacak şekilde T4ModelBusAdapter her *.tt dosyasında "T4" son kısmını, ad alanı yerleştirin.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. İçinde `DslPackage` projesi, bir proje başvurusu Ekle `T4ModelBusAdapter`.

6. DslPackage\source.extension.tt içinde altında aşağıdaki satırı ekleyin `<Content>`.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. İçinde `T4ModelBusAdapter` projesi, bir başvuru ekleyin: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Open T4ModelBusAdapter\AdapterManager.tt:

   1.  AdapterManagerBase için temel sınıfını değiştirmek <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Bu bölümü dosyasının aşağıdakine benzer.

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {

       ```

   2.  Dosyanın sonuna, aşağıdaki ek öznitelik sınıfı AdapterManager önüne ekleyin.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Sonuç aşağıdakine benzer.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }

       ```

9. Tıklayın **tüm Şablonları Dönüştür** başlık çubuğu, Çözüm Gezgini'nde.

10. Çözümü yeniden derleyin. F5'e tıklayın.

11. F5 tuşuna basarak DSL çalışır durumda olduğunu doğrulayın. Deneysel projeyi `Sample.provider`. Visual Studio'nun deneysel örneği kapatın.

    Bu DSL ModelBus başvuruları artık metin şablonlarında ve ayrıca sıradan bir kod çözülebilir.

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Bir DSL ModelBus başvuru etki alanı özelliği ile oluşturun

1. En az bir dil çözümü şablonu kullanarak yeni bir DSL oluşturun. MBConsumer dil adı ve dosya adı uzantısı için ".consume" olarak ayarlayın.

2. DSL projesinde MBProvider DSL derlemesine bir başvuru ekleyin. Sağ `MBConsumer\Dsl\References` ve ardından **Başvuru Ekle**. İçinde **Gözat** sekmesinde, bulun `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Bu, diğer DSL kullanan kodu oluşturmanıza olanak sağlar. Birden çok DSL başvuruları oluşturmak istiyorsanız, bunları da ekleyin.

3. DSL tanım diyagramı, diyagram sağ tıklayın ve ardından **etkinleştirme ModelBus**. İletişim kutusunda **Modelbus'ı kullanmak bu DSL etkinleştirme**.

4. Sınıfında `ExampleElement`, yeni bir etki alanı özelliği Ekle `MBR`ve türünü Özellikler penceresinde ayarlayın `ModelBusReference`.

5. Etki alanı özelliği diyagram üzerinde sağ tıklayın ve ardından **Düzenle ModelBusReference belirli özellikleri**. İletişim kutusunda **bir model öğesini**.

    Dosya iletişim filtresi için aşağıdaki ayarlayın.

    `Provider File|*.provide`

    Alt dizeden sonra "&#124;" dosya seçimi iletişim kutusu için bir filtredir. Kullanarak dosyaları izin verecek şekilde ayarlayabilirsiniz *.\*

    İçinde **Model öğe türü** listesinde, bir veya daha fazla etki alanı sınıfları DSL (örneğin, Company.MBProvider.Task) sağlayıcı adını girin. Soyut sınıflar olabilirler. Liste boş bırakırsanız, kullanıcı herhangi bir öğeye başvuru ayarlayabilirsiniz.

6. İletişim kutusunu kapatın ve **tüm Şablonları Dönüştür**.

   Başka bir DSL öğelerine başvurular içeren bir DSL oluşturdunuz.

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Çözümdeki başka bir dosyaya ModelBus başvuru oluşturun

1. MBConsumer çözümde, CTRL + F5 tuşlarına basın. Visual Studio deneysel örneği açılır **MBConsumer\Debugging** proje.

2. Bir kopyasını Sample.provide için ekleme **MBConsumer\Debugging** proje. Bunun gerekli olmasının nedeni ModelBus başvuru aynı çözüm içindeki bir dosyaya başvurmalıdır.

   1.  Hata ayıklama projeye sağ tıklayın, fareyle **Ekle**ve ardından **var olan öğe**.

   2.  İçinde **Öğe Ekle** iletişim kutusunda, filtrenin kümesine **tüm dosyalar (\*.\*)** .

   3.  Gidin `MBProvider\Debugging\Sample.provide` ve ardından **Ekle**.

3. Açık `Sample.consume`.

4. Bir örnek şekle tıklayın ve Özellikler penceresinde tıklayın **[...]**  MBR özelliğinde. İletişim kutusunda **Gözat** seçip `Sample.provide`. Öğeleri penceresinde görev türü genişletin ve öğelerden birini seçin.

5. Dosyayı kaydedin.

    (Henüz Visual Studio'nun deneysel örneğinde kapatmayın.)

   Başka bir modelinde bir öğedeki ModelBus başvuru içeren bir model oluşturdunuz.

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Metin şablonunda ModelBus başvuru çözümleyin

1.  Visual Studio'nun deneysel örneğinde, bir örnek metin şablonu dosyasını açın. İçeriği aşağıdaki gibi ayarlayın.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     Aşağıdaki noktalara dikkat edin:

    1.  `hostSpecific` Ve `inherits` özniteliklerini `template` yönergesi ayarlanmalıdır.

    2.  Tüketici modeli, her zamanki şekilde bu DSL içinde oluşturulan bir yönerge işlemcisi aracılığıyla erişilir.

    3.  Derleme ve içeri aktarma yönergeleri ModelBus ve sağlayıcı DSL türlerine erişebilir olması gerekir.

    4.  Birçok MBRs aynı modele bağlı olduğunu biliyorsanız, yalnızca bir kez CreateAdapter çağırmak daha iyidir.

2.  Şablonu kaydedin. Elde edilen metin dosyası aşağıdakine benzer olduğunu doğrulayın.

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Bir hareket işleyicisi ModelBus başvuru çözümleyin

1.  Visual Studio'nun deneysel örneğinde çalışıyorsa kapatın.

2.  MBConsumer\Dsl\Custom.cs adlı ve içeriğini aşağıdaki ayarlı bir dosya ekleyin.

    ```

    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }

    ```

3.  CTRL + F5 tuşlarına basın.

4.  Visual Studio'nun deneysel örneğinde açın `Debugging\Sample.consume`.

5.  Bir şekil çift tıklayın.

     Bu öğe üzerindeki MBR ayarladıysanız, başvurulan model açar ve başvurulan öğe seçilir.

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Kod Oluşturma ve T4 Metin Şablonları](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
