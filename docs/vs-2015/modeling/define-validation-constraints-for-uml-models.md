---
title: UML modelleri için doğrulama kısıtlamaları tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6647d37636ed0e79d817113e388ae5df23a88a29
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782420"
---
# <a name="define-validation-constraints-for-uml-models"></a>UML modelleri için doğrulama kısıtlamaları tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modelin belirttiğiniz koşulu karşılayıp karşılamadığını test eden doğrulama kısıtlamalarını tanımlayabilirsiniz. Örneğin, kullanıcının kalıtım ilişkileri döngüsünü oluşturmadığından emin olmak için bir kısıtlama tanımlayabilirsiniz. Kullanıcı açmanız veya kaydetmeniz model dener ve ayrıca el ile çağrılabilir kısıtlaması çağrılır. Eğer kısıtlama başarısız olursa, tanımladığınız bir hata iletisi hata penceresine eklenir. Bu kısıtlamalar bir Visual Studio Tümleştirme Uzantısı'na paketini ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.  
  
 Ayrıca, modeli veritabanları gibi dış kaynaklara karşı doğrulama kısıtlamalarını tanımlayabilirsiniz. Program kodunu katman diyagramına karşı doğrulamak istiyorsanız, bkz. [katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 Visual Studio'nun hangi sürümlerinin UML modellerini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="requirements"></a>Gereksinimler  
 Bkz: [gereksinimleri](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="applying-validation-constraints"></a>Doğrulama kısıtlamalarını uygulama  
 Doğrulama kısıtlamaları üç durumda uygulanır: bir modeli kaydettiğinizde bir modeli açtığınızda; ve tıkladığınızda **UML modeli doğrula** üzerinde **mimarisi** menüsü. Genellikle her kısıtlamayı birden çok duruma uygulamak için tanımlamanıza rağmen her durumda, o durum için tanımlanmış kısıtlamalar uygulanacaktır.  
  
 Doğrulama hataları bildirilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hatalar penceresinde ve hatalı model öğelerini seçmek için hataya çift tıklayabilirsiniz.  
  
 Doğrulamayı uygulama hakkında daha fazla bilgi için bkz. [UML modelinizi doğrulama](../modeling/validate-your-uml-model.md).  
  
## <a name="defining-a-validation-extension"></a>Geçerlilik uzatma tanımlama  
 Bir UML tasarımcısı için bir doğrulama uzantısı oluşturmak üzere doğrulama sınırlamalarının davranışını belirleyen bir sınıf oluşturmanız ve sınıfı bir Visual Studio Tümleştirme Uzantısı'na (VSIX) katıştırmanız gerekir. VSIX kısıtlamayı yükleyebilecek bir kapsayıcı gibi davranır. Bir doğrulama uzantısı tanımlamanın iki farklı yöntemi vardır:  
  
-   **Bir proje şablonunu kullanarak kendi VSIX'inde bir doğrulama uzantısı oluşturun.** Bu daha hızlı bir yöntemdir. Doğrulama sınırlamalarınızı menü komutları, özel araç kutusu öğeleri gibi uzantısı diğer tür birleştirmek veya hareket işleyicileri istemiyorsanız bunu kullanın. Bir sınıfta çeşitli kısıtlamalar tanımlayabilirsiniz.  
  
-   **Ayrı doğrulama sınıfı ve VSIX projeleri oluşturun.** Aynı VSIX içinde kaç tür uzantıyı birleştirmek istiyorsanız bu yöntemi kullanın. Örneğin, menü komutunuz modelin belirli kısıtlamalar ortaya koyacağını ön görüyorsa bunu bir doğrulama yöntemi olarak aynı VSIX içine katıştırabilirsiniz.  
  
#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Kendi VSIX'inde bir doğrulama uzantısı oluşturmak için  
  
1. İçinde **yeni proje** iletişim kutusunun **modelleme projeleri**seçin **doğrulama uzantısı**.  
  
2. Açık **.cs** yeni projeye dosya ve doğrulama kısıtlamanızı uygulamak için sınıfı değiştirin.  
  
    Daha fazla bilgi için [doğrulama kısıtlamayı değerlendirme](#Implementing).  
  
   > [!IMPORTANT]
   >  Emin olun, **.cs** dosyalarınızda aşağıdaki `using` deyimi:  
   >   
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
3. Yeni yöntemler tanımlayarak ek sınırlamalar ekleyebilirsiniz. Bir yöntemi doğrulama yöntemi olarak tanımlamak için bu özniteliklerle ilk doğrulama yöntemi olarak aynı şekilde etiketlenmelidir.  
  
4. F5 tuşuna basarak kısıtlamaları test edin. Daha fazla bilgi için [doğrulama kısıtlaması yürütme](#Executing).  
  
5. Menü komut dosyasını kopyalayarak başka bir bilgisayara yükleyin. **bin\\\*\\\*.vsix** projeniz tarafından oluşturulmuş. Daha fazla bilgi için [yükleme ve kaldırma uzantı](#Installing).  
  
   Eklediğinizde, diğer **.cs** dosyaları, genellikle aşağıdaki gerektirecek `using` ifadeleri:  
  
```csharp  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Uml.Classes;  
  
```  
  
 Alternatif yordam şöyledir:  
  
#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Bir sınıf kitaplığı projesinde ayrı bir doğrulama kısıtlaması oluşturmak için  
  
1.  Varolan bir VSIX çözümüne ekleyerek veya yeni bir çözüm oluşturarak bir sınıf kitaplığı projesi oluşturun.  
  
    1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  
  
    2.  Altında **yüklü şablonlar**, genişletme **Visual C#** veya **Visual Basic**ve ardından Orta sütundaki **sınıf kitaplığı**.  
  
2.  Çözümünüz bir tane içermiyorsa, bir VSIX projesi oluşturun:  
  
    1.  İçinde **Çözüm Gezgini**, çözümün kısayol menüsünde **Ekle**, **yeni proje**.  
  
    2.  Altında **yüklü şablonlar**, genişletme **Visual C#** veya **Visual Basic**, ardından **genişletilebilirlik**. Orta sütundaki tıklayın **VSIX projesi**.  
  
3.  VSIX projesinin çözümün başlangıç projesi olarak ayarlayın.  
  
    -   Çözüm Gezgini'nde VSIX projesinin kısayol menüsünden seçin **başlangıç projesi olarak ayarla**.  
  
4.  İçinde **source.extension.vsixmanifest**altında **içerik**, sınıf kitaplığı projesini MEF Bileşeni olarak ekleyin:  
  
    1.  Üzerinde **meta verileri** sekmesinde, VSIX için bir ad belirleyin.  
  
    2.  Üzerinde **hedefleri Yükle** sekmesinde, hedefler olarak Visual Studio sürümleri ayarlayın.  
  
    3.  Üzerinde **varlıklar** sekmesini, bir **yeni**ve iletişim kutusunda şunu ayarlayın:  
  
         **Tür** = **MEF Bileşeni**  
  
         **Kaynak** = **mevcut çözümde bir proje**  
  
         **Proje** = *, sınıf kitaplığı projesi*  
  
#### <a name="to-define-the-validation-class"></a>Doğrulama sınıfını tanımlamak için  
  
1.  Kendi VSIX doğrulama proje şablonu ile bir doğrulama sınıfı oluşturduysanız, bu yordama ihtiyacınız yoktur.  
  
2.  Doğrulama sınıfı projesinde aşağıdaki başvuruları ekleyin [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] derlemeler:  
  
     `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
     `Microsoft.VisualStudio.Uml.Interfaces`  
  
     `System.ComponentModel.Composition`  
  
3.  Aşağıdaki örneğe benzer bir kod içeren sınıf kitaplığı projesine bir dosya ekleyin.  
  
    -   Her doğrulama kısıtlaması belirli bir özniteliği ile işaretlenmiş bir yöntem içinde yer alır. Yöntemi, bir model öğesi türünde bir parametre kabul eder. Doğrulama çağrıldığında doğrulama Framework'ü her doğrulama yöntemi, parametre türüne uyan her model öğe uygulanır.  
  
    -   Bu yöntemleri tüm sınıflara ve ad alanlarına yerleştirebilirsiniz. Bunları tercihinize uygun olarak değiştirin.  
  
    ```  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using Microsoft.VisualStudio.Modeling.Validation;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
    using Microsoft.VisualStudio.Uml.Classes;  
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.  
  
    namespace Validation  
    {  
      public class MyValidationExtensions  
      {  
        // SAMPLE VALIDATION METHOD.  
        // All validation methods have the following attributes.  
        [Export(typeof(System.Action<ValidationContext, object>))]  
        [ValidationMethod(  
           ValidationCategories.Save  
         | ValidationCategories.Open  
         | ValidationCategories.Menu)]  
        public void ValidateClassNames  
          (ValidationContext context,   
           // This type determines what elements   
           // will be validated by this method:  
           IClass elementToValidate)  
        {  
          // A validation method should not change the model.  
  
          List<string> attributeNames = new List<string>();  
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)  
          {  
            string name = attribute.Name;  
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))  
            {  
              context.LogError(  
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),  
                "001", elementToValidate);  
            }  
            attributeNames.Add(name);  
          }  
  
        }  
        // Add more validation methods for different element types.  
      }  
    }  
    ```  
  
##  <a name="Executing"></a> Doğrulama kısıtlaması yürütme  
 Test amaçları için doğrulama yöntemlerinizi hata ayıklama modunda yürütün.  
  
#### <a name="to-test-the-validation-constraint"></a>Doğrulama sınırlamasını test etmek için  
  
1.  Tuşuna **F5**, veya **hata ayıklama** menüsünde seçin **hata ayıklamayı Başlat**.  
  
     Deneysel örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlatır.  
  
     **Sorun giderme**: yeni [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlamıyor:  
  
    -   Birden fazla projeniz varsa, VSIX projesinin çözümün başlangıç projesi olarak ayarlandığından emin olun.  
  
    -   Çözüm Gezgini'nde başlatmanın veya yalnızca projenin kısayol menüsünde seçin **özellikleri**. Proje özellik Düzenleyicisi'ndeki **hata ayıklama** sekmesi. Emin olun dizesinde **harici program Başlat** alandır tam yol adını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], genellikle:  
  
         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2.  Deneysel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], açın veya bir modelleme projesi oluşturmak ve açmak veya bir modelleme diyagramı oluşturun.  
  
3.  Önceki bölümde verilen örnek kısıtlama için bir test ayarlamak için:  
  
    1.  Bir sınıf diyagramı açın.  
  
    2.  Bir sınıf oluşturun ve aynı ada sahip iki öznitelik ekleyin.  
  
4.  Diyagram üzerindeki herhangi bir yerde kısayol menüsünde **doğrulama**.  
  
5.  Modeldeki herhangi bir hata hata penceresinde bildirilecektir.  
  
6.  Hata raporuna çift tıklayın. Raporda belirtilen öğeler ekranda görünür durumdaysa vurgulanacaklardır.  
  
     **Sorun giderme**: varsa **doğrulama** komut görünmez menüde emin olun:  
  
    -   Doğrulama projesi, bir MEF Bileşeni olarak listelenir **varlıklar** sekmesinde **source.extensions.manifest** VSIX projesinde.  
  
    -   Doğru `Export` ve `ValidationMethod` öznitelikleri doğrulama yöntemlerine eklenir.  
  
    -   `ValidationCategories.Menu` bağımsız değişken için yer aldığı `ValidationMethod` özniteliği ve mantıksal OR kullanan diğer değerlerle oluşturulmuştur (&#124;).  
  
    -   Tüm parametreleri `Import` ve `Export` öznitelikleri geçerlidir.  
  
##  <a name="Implementing"></a> Kısıtlamayı değerlendirme  
 Doğrulama yöntemi, uygulamak istediğiniz doğrulama kısıtlamasının doğru veya yanlış olup olmadığını belirlemeniz gerekir. TRUE ise, hiçbir şey yapmamalıdır. False, bunu tarafından sağlanan yöntemleri kullanarak hatayı bildirmelidir varsa `ValidationContext` parametresi.  
  
> [!NOTE]
>  Doğrulama yöntemlerinin modeli değiştirmemesi gerekir. Garantisi yoktur ne zaman veya ne sırada kısıtlamaları yürütüleceğinin. Doğrulama çalışması içinde doğrulama yönteminin birbirini izleyen yürütmeleri arasında bilgi geçirmek varsa, altında açıklanan bağlam önbelleğini kullanabilirsiniz [koordine birden çok doğrulamayı düzenleme](#ContextCache).  
  
 Örneğin, her türün (sınıf, arabirim veya numaralandırıcı) en az üç karakter uzunluğunda bir ad olduğundan emin olmak istiyorsanız, bu yöntemi kullanabilirsiniz:  
  
```  
public void ValidateTypeName(ValidationContext context, IType type)  
{  
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)  
  {  
    context.LogError(  
      string.Format("Type name {0} is too short", type.Name),  
               "001", type);  
   }  
 }  
```  
  
 Bkz: [UML API ile programlama](../modeling/programming-with-the-uml-api.md) gezinmek ve modeli okumak için kullanabileceğiniz yöntemler ve türleri hakkında bilgi için.  
  
### <a name="about-validation-constraint-methods"></a>Kısıtlama yöntemlerini doğrulama hakkında  
 Her doğrulama kısıtlaması aşağıdaki formdaki bir yöntem tarafından tanımlanır:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
 [ValidationMethod(ValidationCategories.Save   
  | ValidationCategories.Menu   
  | ValidationCategories.Open)]  
public void ValidateSomething  
  (ValidationContext context, IClassifier elementToValidate)  
{...}  
```  
  
 Öznitelikler ve her doğrulama yönteminin parametreleri aşağıdaki gibidir:  
  
|||  
|-|-|  
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Yöntemi Yönetilen Genişletilebilirlik Çerçevesi (MEF) kullanarak doğrulama kısıtlaması tanımlar.|  
|`[ValidationMethod (ValidationCategories.Menu)]`|Doğrulama ne zaman gerçekleştirileceğini belirtir. Bit düzeyinde OR kullanın (&#124;) birden fazla seçeneği birleştirmek istiyorsanız.<br /><br /> `Menu` = Doğrulama menüsü tarafından çağrılır.<br /><br /> `Save` = modeli kaydederken çağrılır.<br /><br /> `Open` = modeli açarken çağrılır. `Load` = modeli kaydederken çağrılır, ancak için olamayabileceği hakkında kullanıcıyı bu modeli tekrar açmanın mümkün olmayabilir, uyarır. Ayrıca, model ayrıştırılmadan önce yüklemede de çağrılır.|  
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|İkinci parametre değiştirme `IElement` kısıtlamanın uygulamasını istediğiniz öğe türüne göre. Kısıtlama yöntemi belirtilen türdeki tüm öğelere çağrılacaktır.<br /><br /> Yöntemin adı önemli değildir.|  
  
 İkinci parametrede farklı türler ile istediğiniz sayıda doğrulama yöntemi tanımlayabilirsiniz. Doğrulama çağrıldığında her doğrulama yöntemi parametre türüne uyan her model öğe üzerinde çağrılır.  
  
### <a name="reporting-validation-errors"></a>Doğrulama hatalarını raporlama  
 Bir hata raporu oluşturmak için tarafından sağlanan yöntemleri kullanın. `ValidationContext`:  
  
 `context.LogError("error string", errorCode, elementsWithError);`  
  
- `"error string"` görünür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata listesi  
  
- `errorCode` hatanın benzersiz tanımlayıcısı olması dizedir  
  
- `elementsWithError` modeldeki öğeleri tanımlar. Kullanıcı hata raporuna çift tıkladığında, bu öğeyi gösteren şekil seçilecektir.  
  
  `LogError(),` `LogWarning()` ve `LogMessage()` iletileri hata listesinin farklı bölümlerine yerleştirin.  
  
## <a name="how-validation-methods-are-applied"></a>Doğrulama yöntemleri nasıl uygulanır  
 Doğrulama modelindeki ilişkileri ve sınıf öznitelikleri ve işlem parametreleri gibi büyük öğelerin parçaları dahil olmak üzere her öğeye uygulanır.  
  
 Her doğrulama yöntemi ikinci parametresindeki türe uyan her öğeye uygulanır. Bir doğrulama yöntemi ikinci parametresi ile tanımlarsanız, örneğin, yani `IUseCase` supertype ile diğerini `IElement`, bu yöntemlerin ikisi de modeldeki her kullanım örneğine uygulanacaktır.  
  
 Türlerin hiyerarşisi özetlenir [UML model öğe türleri](../modeling/uml-model-element-types.md).  
  
 Ayrıca öğelere ilişkileri takip ederek da erişebilirsiniz. Örneğin, bir doğrulama yöntemi tanımlamak için oluşturduysanız `IClass`, kendi özellikleri boyunca döngüye girebilirsiniz:  
  
```  
public void ValidateTypeName(ValidationContext context, IClass c)  
{  
   foreach (IProperty property in c.OwnedAttributes)  
   {  
       if (property.Name.Length < 3)  
       {  
            context.LogError(  
                 string.Format(  
                        "Property name {0} is too short",   
                        property.Name),   
                 "001", property);  
        }  
   }  
}  
```  
  
### <a name="creating-a-validation-method-on-the-model"></a>Model üzerinde doğrulama yöntemi oluşturma  
 Doğrulama yönteminin her doğrulama çalışması esnasında, tam olarak doğrulamak için bir kez çağrıldığından emin olmak istiyorsanız `IModel`:  
  
```  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  foreach (IElement element in model.OwnedElements)  
   { ...  
```  
  
### <a name="validating-shapes-and-diagrams"></a>Şekilleri ve diyagramları doğrulama  
 Doğrulama yöntemlerinin birincil amacı modeli doğrulamaktır olduğundan doğrulama yöntemleri diyagramlar ve şekiller gibi görüntüleme öğeleri üzerinde çağrılmaz. Ancak diyagram bağlamını kullanarak geçerli diyagrama erişebilirsiniz.  
  
 Doğrulama sınıfında, bildirmek `DiagramContext` içeri aktarılan özellik olarak:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
...  
[Import]  
public IDiagramContext DiagramContext { get; set; }  
```  
  
 Kullanabileceğiniz bir doğrulama yönteminde `DiagramContext` varsa geçerli odak diyagramına erişmek için:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;  
  if (focusDiagram != null)  
  {  
    foreach (IShape<IUseCase> useCaseShape in  
              focusDiagram.GetChildShapes<IUseCase>())  
    { ...  
```  
  
 Bir şekle geçirilemez bir hatayı kaydetmek için şeklin gösterdiği model öğeyi edinmeniz gerekir çünkü `LogError`:  
  
```  
IUseCase useCase = useCaseShape.Element;  
context.LogError(... , usecase);  
```  
  
###  <a name="ContextCache"></a> Birden çok doğrulamayı düzenleme  
 Doğrulama çağrıldığında, örneğin bir diyagram menüsünden, kullanıcı tarafından her doğrulama yöntemi her model öğesine uygulanır. Bu doğrulama çerçevesinin tek bir çağrısı içinde aynı yöntemi birden çok kez farklı öğelere uygulanabilir, anlamına gelir.  
  
 Bu öğeleri arasındaki ilişkileri uğraşmanız doğrulamaları bir sorunu gösterir. Örneğin, başlayan bir doğrulama, bir kullanım örneği ve ilişkilerinden geçen yazabilirsiniz **dahil** ilişkileri döngü olmadığını doğrulayın. Ancak zaman yöntemi uygulanan birçok olan modelde her kullanım örneğine **dahil** bağlantıları, büyük olasılıkla sürekli olarak modelin aynı alanlarını işleyecektir.  
  
 Bu durumu önlemek için bilgi doğrulama çalışması esnasında korunduğu bağlam önbelleği yoktur. Doğrulama yöntemlerinin yürütmeleri arasında bilgi geçirmek için kullanabilirsiniz. Örneğin, zaten ile bu doğrulama çalışmasında ilgili olan öğelerin listesini saklayabilirsiniz. Önbellek her doğrulama çalışmasının başlangıcında oluşturulur ve farklı doğrulama çalışmaları arasında bilgi geçirmek için kullanılamaz.  
  
|||  
|-|-|  
|`context.SetCacheValue<T> (name, value)`|Bir değer Store|  
|`context.TryGetCacheValue<T> (name, out value)`|Bir değer alır. Başarılıysa true döndürür.|  
|`context.GetValue<T>(name)`|Bir değer alır.|  
|`Context.GetValue<T>()`|Belirtilen türde bir değer alır.|  
  
##  <a name="Installing"></a> Yükleme ve bir uzantıyı kaldırma  
 Yükleyebileceğiniz bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] hem kendi bilgisayarınıza hem de diğer bilgisayarlara uzantısı.  
  
#### <a name="to-install-an-extension"></a>Bir uzantı yüklemek için  
  
1.  Bilgisayarınızda, bulma **.vsix** VSIX projeniz tarafından oluşturulan dosya.  
  
    1.  İçinde **Çözüm Gezgini**, VSIX projesinin kısayol menüsünde **klasörü Windows Gezgini'nde Aç**.  
  
    2.  Dosyayı bulmak **bin\\\*\\**_projeniz_**.vsix**  
  
2.  Kopyalama **.vsix** uzantıyı yüklemek istediğiniz hedef bilgisayarın bir dosyaya. Bu sizin kendi bilgisayarınız veya başka bir tane olabilir.  
  
    -   Hedef bilgisayarda sürümlerinden biri olmalıdır [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] belirttiğiniz **source.extension.vsixmanifest**.  
  
3.  Hedef bilgisayarda açın **.vsix** dosya.  
  
     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yükler.  
  
4.  Başlatın veya yeniden [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Bir uzantıyı kaldırmak için  
  
1. Üzerinde **Araçları** menüsünde seçin **Uzantılar ve güncelleştirmeler**.  
  
2. Genişletin **yüklü uzantıları**.  
  
3. Uzantıyı seçin ve ardından **kaldırma**.  
  
   Nadiren, hatalı bir uzantı yüklemede başarısız olur ve hata penceresinde bir rapor oluşturur ancak Uzantı Yöneticisi'nde görünmez. Bu durumda, dosya şu konumdan silerek uzantıyı kaldırabilirsiniz burada *% LocalAppData %* genellikle *DriveName*: \Users\\*kullanıcıadı*\AppData\Local:  
  
   *% LocalAppData %* **\Microsoft\VisualStudio\\[sürüm] \Extensions**  
  
##  <a name="Example"></a> Örnek  
 Bu örnekte, öğeler arasındaki bağımlılık ilişkisindeki döngüleri bulur.  
  
 Hem kaydetme hem üzerinde doğrulama menü komutunu doğrulayacaktır.  
  
```  
/// <summary>  
/// Verify that there are no loops in the dependency relationsips.  
/// In our project, no element should be a dependent of itself.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">Element to start validation from.</param>  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu   
     | ValidationCategories.Save | ValidationCategories.Open)]  
public void NoDependencyLoops(ValidationContext context, INamedElement element)  
{  
    // The validation framework will call this method  
    // for every element in the model. But when we follow  
    // the dependencies from one element, we will validate others.  
    // So we keep a list of the elements that we don't need to validate again.   
    // The list is kept in the context cache so that it is passed  
    // from one execution of this method to another.  
    List<INamedElement> alreadySeen = null;  
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))  
    {  
       alreadySeen = new List<INamedElement>();  
       context.SetCacheValue("No dependency loops", alreadySeen);  
    }  
  
    NoDependencyLoops(context, element,   
                new INamedElement[0], alreadySeen);      
}  
  
/// <summary>  
/// Log an error if there is any loop in the dependency relationship.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">The element to be validated.</param>  
/// <param name="dependants">Elements we've followed in this recursion.</param>  
/// <param name="alreadySeen">Elements that have already been validated.</param>  
/// <returns>true if no error was detected</returns>  
private bool NoDependencyLoops(ValidationContext context,   
    INamedElement element, INamedElement[] dependants,   
    List<INamedElement> alreadySeen)  
{  
    if (dependants.Contains(element))  
    {  
        context.LogError(string.Format("{0} should not depend on itself", element.Name),   
        "Fabrikam.UML.NoGenLoops", // unique code for this error  
        dependants.SkipWhile(e => e != element).ToArray());   
            // highlight elements that are in the loop  
        return false;  
    }  
    INamedElement[] dependantsPlusElement =   
        new INamedElement[dependants.Length + 1];  
    dependants.CopyTo(dependantsPlusElement, 0);  
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;  
  
    if (alreadySeen.Contains(element))  
    {  
        // We have already validated this when we started   
        // from another element during this validation run.  
        return true;  
    }  
    alreadySeen.Add(element);  
  
    foreach (INamedElement supplier in element.GetDependencySuppliers())  
    {  
        if (!NoDependencyLoops(context, supplier,  
             dependantsPlusElement, alreadySeen))  
        return false;  
    }  
    return true;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modelleme Uzantısı Tanımlama ve yükleme](../modeling/define-and-install-a-modeling-extension.md)   
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)



