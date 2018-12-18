---
title: Modelbus kullanarak modelleri tümleştirme
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e72814b34790dd133f09e0fb16c594e12ea8147c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064603"
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme

Visual Studio Modelbus'ı modellerini diğer araçlar ve modelleri arasında bağlantılar oluşturmak için bir yöntem sağlar. Örneğin, etki alanına özgü dil (DSL) modelleri ve UML modellerini bağlayabilirsiniz. DSL tümleşik bir dizi oluşturabilirsiniz.

ModelBus benzersiz bir Modeli'ne veya bir model içinde belirli bir öğeye başvuru oluşturmanıza olanak sağlar. Bu başvuru modeli dışında Örneğin, başka bir modelinde bir öğedeki depolanabilir. Bir sonraki fırsatta, bir aracı öğeye erişmek istediğinde, Model veri yolu altyapı uygun model yüklenemiyor ve öğesini döndürür. İsterseniz, model kullanıcıya görüntüleyebilirsiniz. Dosyayı önceki konumuna erişilemiyor, ModelBus bulmak için kullanıcı sorar. Kullanıcı dosyasını bulursa, bu dosyaya yapılan tüm başvurular ModelBus düzeltir.

> [!NOTE]
> Geçerli Visual Studio uygulamasında ModelBus, bağlantılı model öğeleri aynı Visual Studio çözümü içinde olması gerekir.

Ek bilgi ve örnek kod için bkz:

-   [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)

-   [Visual Studio için modelleme SDK'sı](http://www.microsoft.com/download/details.aspx?id=40754)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="provide"></a> Bir DSL için erişim sağlama
 Bir model veya öğelerini ModelBus başvuruları oluşturabilmek için DSL ModelBusAdapter tanımlamanız gerekir. Bunu yapmanın en kolay yolu, Visual Studio Model veri yolu için DSL Tasarımcısı komutları ekleyen uzantısı, kullanmaktır.

### <a name="expose"></a> Model veri yolu için bir DSL tanımını ortaya çıkarmak için

1. İndirin ve zaten yüklemiş olduğunuz sürece, Visual Studio Model veri yolu uzantıyı yükleyin. Daha fazla bilgi için [Görselleştirme ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkID=185579).

2. DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve ardından **etkinleştirme Modelbus**.

3. İletişim kutusunda **bu DSL için ModelBus kullanıma sunmak istediğiniz**. Bu DSL modellerinin kullanıma sunmak ve diğer DSL'ler başvurular kullanmak istiyorsanız, iki seçenek de seçebilirsiniz.

4. **Tamam**'ı tıklatın. Yeni bir proje "ModelBusAdapter" DSL çözüme eklenir.

5. DSL bir metin şablonundan erişmek istiyorsanız, yeni projede AdapterManager.tt değiştirmeniz gerekir. Komutlar ve olay işleyicileri gibi diğer koddan DSL erişmek istiyorsanız bu adımı atlayın. Daha fazla bilgi için [metin şablonunda Visual Studio ModelBus kullanarak](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. AdapterManagerBase için temel sınıfını değiştirmek <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.

   2. Dosyanın sonuna, bu ek öznitelik sınıfı AdapterManager önüne ekleyin:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. Başvurular, ModelBusAdapter projesinde ekleyin **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.

      Metin şablonları ve diğer kod DSL erişmek istiyorsanız, iki bağdaştırıcı, biri değiştirilmiş ve biri üzerinde değişiklik yapılmadan gerekir.

6. Tıklayın **tüm şablonları dönüştürme**.

7. Çözümü yeniden derleyin.

   Artık bu DSL örneklerini açmak için ModelBus mümkündür.

   Klasör `ModelBusAdapters\bin\*` tarafından oluşturulmuş derlemeler içeren `Dsl` proje ve `ModelBusAdapters` proje. Bu DSL başka bir DSL başvurmak için bu bütünleştirilmiş kodları almanız gerekir.

### <a name="ensure-that-elements-can-be-referenced"></a>Öğeleri başvurulan emin olun

Visual Studio Modelbus'ı bağdaştırıcıları öğenin guid'si, varsayılan olarak tanımlamak için kullanın. Bu tanımlayıcılar, bu nedenle model dosyasında kalıcı olmasını.

Bu öğe kimlikleri kalıcı emin olmak için:

1. DslDefinition.dsl açın.

2. DSL Gezgini'nde **Xml serileştirme davranışı**, ardından **sınıfı verilerinin**.

3. Model veri yolu oluşturmak istediğiniz her bir sınıf için başvuruyor:

    Sınıf düğümü tıklayın ve Özellikler penceresinde emin **serileştirmek kimliği** ayarlanır `true`.

   Alternatif olarak, öğe adları yerine GUID öğeleri tanımlamak için kullanmak istiyorsanız, oluşturulan bağdaştırıcıların bölümlerini geçersiz kılabilirsiniz. Bağdaştırıcı sınıfı aşağıdaki yöntemleri geçersiz kıl:

-   Geçersiz kılma `GetElementId` kullanmak istediğiniz kimlik döndürmek için. Bu yöntem, başvuruları oluştururken çağrılır.

-   Geçersiz kılma `ResolveElementReference` Model veri yolu başvurudan doğru öğesi bulunamıyor.

## <a name="editRef"></a> Bir DSL başka bir DSL erişme

Bir etki alanı özelliği DSL model veri yolu başvuruları depolayabilirsiniz ve bunları kullanan özel kod yazabilirsiniz. Ayrıca kullanıcının bir model dosyası ve bir öğesiyle seçerek bir modeli bus başvurusu oluşturmasını sağlayabilirsiniz.

Başka bir DSL başvurular kullanmak bir DSL etkinleştirmek için öncelikle bunu olmalısınız bir *tüketici* model veri yolu başvuruları.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Bir DSL oluşturulan bir DSL başvurular kullanmak üzere etkinleştirmek için

1.  DSL tanım diyagramı, diyagram ana bölümü sağ tıklayın ve ardından **etkinleştirme Modelbus**.

2.  İletişim kutusunda **modeli yol başvuruları kullanmak bu modeli etkinleştirmek istiyorum**.

3.  Alıcı DSL Dsl projesinde aşağıdaki derlemeler projenin başvurular ekleyin. Bu derlemeleri (.dll dosyaları) içinde ModelBusAdapter\bin bulabilirsiniz\\* sunulan DSL dizin.

    -   Örneğin sunulan DSL derleme **Fabrikam.FamilyTree.Dsl.dll**

    -   İfşa edilen modeli bağdaştırıcısı derlemesini, örneğin veri yolu **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4.  Aşağıdaki .NET derlemelerini alıcı DSL proje proje başvurular ekleyin.

    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Bir etki alanı özelliği bir Model veri yolu başvuru depolamak için

1. Alıcı DSL DSL tanımındaki alan sınıfı için bir alan özelliği ekleyin ve adını ayarlayın.

2. Özellikler penceresinde, seçili etki alanı özelliği ile ayarlayın **türü** için `ModelBusReference`.

   Bu aşamada, program kodu özellik değeri ayarlayabilirsiniz ancak Özellikler penceresinde salt okunur.

   Özelleştirilmiş bir ModelBus başvuru düzenleyici ile özelliğini ayarlamak kullanıcılar izin verebilirsiniz. Bu düzenleyicinin iki sürümü vardır veya *Seçici:* bir model dosyası seçmek kullanıcıların bir sağlar ve başka bir model dosyası ve bir öğe model içindeki seçmelerini sağlar.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Model veri yolu başvuru bir etki alanı özelliği ayarlamak izin vermek için

1.  Etki alanı özelliği sağ tıklayın ve ardından **Düzenle ModelBusReference belirli özellikleri**. Bir iletişim kutusu açılır. Bu *Model veri yolu Seçici*.

2.  Uygun seçin **tür ModelBusReference**: bir Modeli'ne veya bir model içinde bir öğe.

3.  Dosya iletişim filtre dizesi içinde bir dize gibi girin `Family Tree files |*.ftree`. DEVICEHIGH sunulan DSL'nizi dosya uzantısı.

4.  Bir modeldeki bir öğeye başvuru seçerseniz, kullanıcı seçebilirsiniz, örneğin Company.FamilyTree.Person türlerinin bir listesini ekleyebilirsiniz.

5.  Tıklayın **Tamam**ve ardından **tüm Şablonları Dönüştür** içinde **Çözüm Gezgini** araç çubuğu.

    > [!WARNING]
    > Geçerli model veya varlık seçmediyseniz, Tamam düğmesine etkin görünebilir olsa bile hiçbir etkisi gerekir.

6.  Company.FamilyTree.Person gibi hedef türlerinin bir listesi belirtilmişse, ardından bir bütünleştirilmiş kod başvurusu DSL projenize DLL hedef DSL, örneğin Company.FamilyTree.Dsl.dll başvuru eklemeniz gerekir

### <a name="to-test-a-model-bus-reference"></a>Model veri yolu başvuru test etmek için

1.  Kullanıma sunulan ve alıcı DSL'ler oluşturun.

2.  Bir DSL, Deneysel modda F5 veya CTRL + F5 tuşlarına basarak çalıştırın.

3.  Visual Studio'nun deneysel örneğinde hata ayıklama projesinde her DSL örneklerini dosyaları ekleyin.

    > [!NOTE]
    > Visual Studio Modelbus'ı yalnızca öğeler aynı Visual Studio çözümünde modellere başvurular çözebilirsiniz. Örneğin, dosya sisteminizi başka bir kısmında bir model dosyasına bir başvuru oluşturulamıyor.

4.  Bazı öğeleri ve bağlantılarına sunulan DSL örneğini oluşturun ve kaydedin.

5.  Alıcı DSL örneği açın ve model veri yolu başvuru özelliğine sahip bir model öğesini seçin.

6.  Özellikler penceresinde model veri yolu başvuru özelliği çift tıklayın. Seçici iletişim kutusunu açar.

7.  Tıklayın **Gözat** ve sunulan DSL örneğini seçin.

     Model veri yolu başvurusu özel öğe türü belirtilirse Seçici Ayrıca, modeldeki bir öğe seçin olanak tanır.

## <a name="creating-references-in-program-code"></a>Program kodunda başvuruları oluşturma

Bir model veya bir model içinde bir öğe için bir başvuru depolamak istediğinizde, oluşturduğunuz bir `ModelBusReference`. İki tür vardır, `ModelBusReference`: model başvuruları ve öğesi başvuruları.

Bir model başvuru oluşturmak için model bir örneği ve dosya adı veya Visual Studio Proje öğesi modelinin olduğu DSL AdapterManager gerekir.

Bir öğe başvurusu oluşturmak için model dosyası ve başvurmak istediğiniz öğeyi için bir bağdaştırıcı gerekir.

> [!NOTE]
> Visual Studio ModelBus ile aynı Visual Studio çözümünde başvuruları yalnızca öğeleri oluşturabilirsiniz.

### <a name="import-the-exposed-dsl-assemblies"></a>İfşa edilen DSL derlemeler Al

Kullanan projenin proje başvurularına sunulan DSL DSL ve ModelBusAdapter derlemeleri ekleyin.

Örneğin, öğeleri MusicLibrary DSL'nin ModelBus başvuruları depolamak istediğinizi varsayalım. ModelBus başvuruları FamilyTree DSL öğelerine başvuracaktır. İçinde `Dsl` MusicLibrary çözümde başvurular düğümü, projenin aşağıdaki derlemelere başvurular ekleyin:

- Fabrikam.FamilyTree.Dsl.dll - sunulan DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll - sunulan DSL ModelBus Bağdaştırıcısı'nı tıklatın.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Bu derlemeleri bulabilirsiniz `ModelBusAdapters` sunulan DSL projesi altında `bin\*`.

  Başvuruları oluşturacağı kod dosyasında, genellikle aşağıdaki ad alanlarını içeri aktarın gerekecektir:

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Bir Modeli'ne başvuru oluşturmak için

Model başvuru oluşturmak için AdapterManager erişmek için kullanıma sunulan DSL ve model için bir başvuru oluşturmak için bunu kullanın. Ya da bir dosya yolu belirtebilirsiniz veya `EnvDTE.ProjectItem`.

AdapterManager modelinde öğelere erişim sağlayan bir bağdaştırıcı elde edebilirsiniz.

> [!NOTE]
> İşiniz bittiğinde ile bir bağdaştırıcı dispose gerekir. Bunu yapmanın en kolay yolu olan bir `using` deyimi. Aşağıdaki örnek bunu göstermektedir.

```csharp
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter
```

Kullanabilmelerini istiyorsanız `modelReference` daha sonra dış türüne sahip bir etki alanı özelliğinde depolayabilirsiniz `ModelBusReference`:

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Bu etki alanı özelliği düzenlemek kullanıcılara izin vermek üzere `ModelReferenceEditor` Düzenleyicisi özniteliğinde parametre olarak. Daha fazla bilgi için [kullanıcının bir başvuru düzenlemesine izin](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Öğeye bir başvuru oluşturmak için

Model için oluşturduğunuz bağdaştırıcısı oluşturmak ve başvuruları çözümlemek için kullanılabilir.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

Kullanabilmelerini istiyorsanız `elementReference` daha sonra dış türüne sahip bir etki alanı özelliğinde depolayabilirsiniz `ModelBusReference`. Düzenlenecek kullanıcılar izin vermek üzere `ModelElementReferenceEditor` Düzenleyicisi özniteliğinde parametre olarak. Daha fazla bilgi için [kullanıcının bir başvuru düzenlemesine izin](#editRef).

### <a name="resolving-references"></a>Başvurular çözümleniyor

Varsa bir `ModelBusReference` (MBR) modeli veya başvurduğu model öğesi edinebilirsiniz. Öğe bir diyagram veya diğer görünüm sunulmazsa, görünümü açın ve öğeyi seçin.

Bir bağdaştırıcı bir MBR'yi oluşturabilirsiniz. Bağdaştırıcısından modelin kökü elde edebilirsiniz. Ayrıca, model içindeki belirli öğelere başvuran MBRs çözebilirsiniz.

```csharp
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Metin şablonunda ModelBus başvurularını çözümlemek için

1. Erişmek istediğiniz DSL erişimi için metin şablonları tarafından yapılandırılan bir ModelBus bağdaştırıcısı olmalıdır. Daha fazla bilgi için [DSL erişim sağlayarak](#provide).

2. Genellikle, DSL Model veri yolu başvurusu (MBR) kullanarak bir DSL kaynakta depolanan bir hedef erişim sağlarlar. Şablonunuz, bu nedenle MBR çözümlenecek yönergesi kaynak DSL ek olarak kodu içerir. Metin şablonları hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>
   ```

   Daha fazla bilgi ve bir kılavuz için bkz: [metin şablonunda Visual Studio ModelBus kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>Bir ModelBusReference seri hale getirme

Depolamak istiyorsanız bir `ModelBusReference` (MBR), seri dize biçiminde:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

Bu şekilde serileştirilmiş bir MBR bağlamında bağımsızdır. Basit dosya tabanlı Model veri yolu bağdaştırıcısı kullanıyorsanız, MBR bir mutlak dosya yolunu içerir. Bu örnek model dosyaları hiçbir zaman geçmeniz durumunda yeterlidir. Ancak, model dosyaları genellikle Visual Studio projesi öğeleri olacaktır. Kullanıcılarınızın, dosya sisteminin farklı bölümlerine tüm projeye taşımak ister. Ayrıca projenin kaynak denetimi altında tutun ve farklı bilgisayarlarda açmak beklediği. Dosyaları içeren proje konumu göreli yol adları bu nedenle seri hale.

### <a name="serializing-relative-to-a-specified-file-path"></a>Belirtilen dosya yolu göreli seri hale getirme

A `ModelBusReference` içeren bir `ReferenceContext`, hangi depolayabileceğiniz göre bunu seri hale getirilemiyor dosya yolu gibi bilgileri bir sözlük olduğu.

Göreli bir yol serileştirmek için:

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

Dizeden başvuru almak için:

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>Diğer bağdaştırıcıları tarafından oluşturulan ModelBusReferences
 Aşağıdaki bilgiler, kendi bağdaştırıcısı oluşturmak istiyorsanız yararlıdır.

 A `ModelBusReference` (MBR) iki bölümden oluşur: model veri yolu tarafından seri durumdan, MBR üst bilgi ve belirli bir bağdaştırıcı Yöneticisi tarafından işlenen bir bağdaştırıcı özgü. Bu, kendi bağdaştırıcısı serileştirme biçimi sağlamanıza olanak sağlar. Örneğin, bir dosya yerine bir veritabanına başvurabilir veya ek bilgileri bağdaştırıcısı başvurusunda depolayabilir. Ek bilgileri kendi bağdaştırıcısı yerleştirebilirsiniz `ReferenceContext`.

 Bir MBR serisini olduğunda, ardından MBR nesnesinde depolanan bir ReferenceContext sağlamanız gerekir. Bir MBR seri olduğunda, depolanan ReferenceContext dizesi oluşturmak amacıyla bağdaştırıcı tarafından kullanılır. Seri durumdan çıkarılmış dize ReferenceContext tüm bilgileri içermiyor. Örneğin, basit dosya tabanlı bağdaştırıcısında ReferenceContext serileştirilmiş MBR dizesinde depolanmaz kök dosya yolu içerir.

 MBR iki aşamada seri durumda:

-   `ModelBusReferencePropertySerializer` MBR üstbilgiyle ilgilenen standart seri hale getirici ' dir. Standart DSL kullanan `SerializationContext` depolanan özellik paketi `ReferenceContext` anahtar kullanılarak `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. Özellikle, `SerializationContext` örneğini içermelidir `ModelBus`.

-   ModelBus bağdaştırıcınızı MBR bağdaştırıcısı özel bölümü ile ilgilidir. Bunu yapmak için MBR ' ReferenceContext içinde depolanan ek bilgileri kullanabilirsiniz. Kök dosya yolları anahtarlar kullanılarak basit dosya tabanlı bağdaştırıcısı tutar `FilePathLoadContextKey` ve `FilePathSaveContextKey`.

     Yalnızca kullanıldığında bir bağdaştırıcı başvuru bir model dosyası seri durumdan.

## <a name="to-create-a-model"></a>Bir Model oluşturmak için

### <a name="creating-opening-and-editing-a-model"></a>Oluşturma, açma ve bir modeli düzenleme
 Durum makinesi örnek VMSDK Web sitesinde aşağıdaki parçası alınır. Bunu ModelBusReferences oluşturmak ve bir modeli açmak için ve modelle ilişkili diyagram elde etmek için kullanımını gösterir.

 Bu örnekte, Durum makinesi ' % s'hedef DSL adıdır. Birden fazla ad kendisinden model sınıfı adını ve ModelBusAdapter adı gibi türetilir.

```csharp
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>Başvuruları doğrulanıyor
 BrokenReferenceDetector ModelBusReferences tutabilen bir Store içinde yer alan tüm etki alanı özellikleri test eder. Eylemi çağırır, herhangi bir eylemde bulunduğu sağlayın. Bu doğrulama yöntemleri için özellikle yararlıdır. Aşağıdaki doğrulama yöntemi modeli kaydedin girişimi mağaza test eder ve bozuk başvurularda ise hatalar penceresinde raporları:

```csharp
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>ModelBus uzantısı tarafından gerçekleştirilen eylemler

Aşağıdaki bilgileri gerekli değildir, ancak kapsamlı kullanımını ModelBus yaparsanız yararlı olabilir.

ModelBus uzantısı DSL çözümünüzde aşağıdaki değişiklikleri yapar.

DSL tanım diyagramı tıkladığında, tıklayın **Modelbus'ı etkinleştirme**ve ardından **Modelbus'ı kullanmak bu DSL etkinleştirme**:

- Bir başvuru eklenir DSL projesinde **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- DSL tanımındaki bir dış tür başvurusu eklenir: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.

   Başvuru gördüğünüz **DSL Gezgini**altında **etki alanı türleri**. Dış tür başvurularını el ile eklemek için kök düğümüne sağ tıklayın.

- Yeni şablon dosya eklendiğinde, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

Ne zaman, ModelBusReference için bir alan özelliği türünü ayarlayın ve sonra özellik sağ tıklatıp **belirli özellikleri etkinleştirin ModelBusReference**:

- Birden çok CLR öznitelikleri etki alanı özelliğine eklenir. Özellikler penceresindeki özel öznitelikler alanında görebilirsiniz. İçinde **Dsl\GeneratedCode\DomainClasses.cs**, özellik bildiriminde öznitelikleri görebilirsiniz:

  ```csharp
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

DSL tanım Diyagramı sağ tıkladığınızda, tıklayın **Modelbus'ı etkinleştirme**seçip **bu DSL için ModelBus kullanıma**:

- Yeni bir proje `ModelBusAdapter` çözüme eklenir.

- Bir başvuru `ModelBusAdapter` eklenir `DslPackage` proje. `ModelBusAdapter` bir başvuru içeriyor `Dsl` proje.

- İçinde **DslPackage\source.extention.tt**, `|ModelBusAdapter|` MEF Bileşeni olarak eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Metin Şablonunda Visual Studio ModelBus'ı Kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md)