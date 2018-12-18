---
title: Etki alanına özgü bir dilde doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
ms.assetid: 65b93df8-af3c-462b-904c-60292f8ed381
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 30a29c9b8921d72f717aea21ed202766f0874389
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950810"
---
# <a name="validation-in-a-domain-specific-language"></a>Etki Alanına Özgü bir Dilde Doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir etki alanına özgü dil (DSL) yazarı, kullanıcı tarafından oluşturulan model anlamlı olduğunu doğrulamak için doğrulama kısıtlamalarını tanımlayabilirsiniz. Örneğin, kullanıcılar, kişiler ve kendi üst öğelerinden ailesi ağacının çizmek DSL'nizi izin veriyorsa, alt kendi üst öğeleri sonraki Doğum tarihleri sahip olmasını sağlar bir kısıtlama yazabilirsiniz.  
  
 Model kaydedildiğinde açıldığında ve kullanıcı açıkça çalıştırdığında yürütmek doğrulama kısıtlamaları olabilir **doğrulama** menü komutu. Program denetiminin altında doğrulama da çalıştırabilirsiniz. Örneğin, bir özellik değeri ya da ilişki bir değişikliğe yanıt doğrulama yürütebilir.  
  
 Metin şablonları ya da kullanıcılarınızın modelleri işleyen diğer araçları yazıyorsanız doğrulama özellikle önemlidir. Modelleri tarafından bu Araçları'nı varsayıldı önkoşulları karşılayan doğrulama sağlar.  
  
> [!WARNING]
>  Ayrıca yanı sıra uzantısı menü komutları ve hareket işleyicileri DSL'nizi uzantıları ayrı tanımlanması için doğrulama kısıtlamaları izin verebilirsiniz. Kullanıcılar DSL'nizi yanı sıra bu uzantıları yüklemeyi tercih edebilirsiniz. Daha fazla bilgi için [MEF kullanarak DSL'nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md).  
  
## <a name="running-validation"></a>Doğrulama çalışıyor  
 Diğer bir deyişle, bir kullanıcı bir model düzenlerken, aşağıdaki eylemleri doğrulama, etki alanına özgü dil örneğini çalıştırabilirsiniz:  
  
- Diyagrama sağ tıklayıp **doğrulama tüm**.  
  
- DSL ve select Gezgini'nde üst düğümünü sağ tıklatın **tüm doğrulama**  
  
- Modeli kaydedin.  
  
- Model açın.  
  
- Buna ek olarak, doğrulama, örneğin, bir menü komutu ya da bir değişikliğe yanıt olarak bir parçası olarak çalışan program kodu yazabilirsiniz.  
  
  Tüm doğrulama hatalarını görünür **hata listesi** penceresi. Kullanıcı, bir hata iletisi, hatanın nedenini model öğelerini seçmek için çift tıklayabilirsiniz.  
  
## <a name="defining-validation-constraints"></a>Doğrulama kısıtlamaları tanımlama  
 Doğrulama yöntemlerinin alan sınıfları veya ilişkileri, DSL'nin ekleyerek, doğrulama kısıtlamaları tanımlama. Doğrulama kullanıcı tarafından veya program denetiminin altında çalıştırıldığında bazılarını veya tümünü doğrulama yöntemlerinin yürütülür. Her yöntem sınıfının her örneği için uygulanır ve her sınıfta çeşitli doğrulama yöntemleri olabilir.  
  
 Her doğrulama yöntemi, bulduğu hataları bildirir.  
  
> [!NOTE]
>  Doğrulama yöntemlerinin hataları bildirin, ancak modelin değiştirmeyin. İsterseniz ayarlamak veya bazı değişiklikleri önlemek için bkz: [doğrulama alternatifleri](#alternatives).  
  
#### <a name="to-define-a-validation-constraint"></a>Doğrulama kısıtlaması tanımlamak için  
  
1. Doğrulamayı etkinleştirmek **Editor\Validation** düğüm:  
  
   1.  Açık **Dsl\DslDefinition.dsl**.  
  
   2.  DSL Gezgini'nde **Düzenleyicisi** düğümünü seçip alt **doğrulama**.  
  
   3.  Özellikler penceresinde ayarlayın **kullanan** özelliklerine `true`. Tüm bu özellikleri ayarlamak oldukça kullanışlıdır.  
  
   4.  Tıklayın **tüm Şablonları Dönüştür** Çözüm Gezgini araç.  
  
2. Bir veya daha fazla alan sınıfları veya etki alanı ilişkileri için kısmi sınıf tanımları yazma. Yeni bir kod dosyasında bu tanımları yazma **Dsl** proje.  
  
3. Bu öznitelik her sınıfıyla ön ek:  
  
   ```csharp  
   [ValidationState(ValidationState.Enabled)]  
   ```  
  
   -   Varsayılan olarak, bu öznitelik de türetilmiş sınıflar için doğrulama sağlayacaktır. Belirli bir türetilmiş sınıf için doğrulama devre dışı bırakmak isterseniz, kullanabileceğiniz `ValidationState.Disabled`.  
  
4. Doğrulama yöntemlerinin sınıfları ekleyin. Her doğrulama yöntemi herhangi bir ada sahip ancak türünde bir parametreye sahip <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>.  
  
    Bir veya daha fazla eklenmelidir `ValidationMethod` öznitelikleri:  
  
   ```csharp  
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]  
   ```  
  
    Yöntemi zaman yürütülür ValidationCategories belirtin.  
  
   Örneğin:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
  
// Allow validation methods in this class:  
[ValidationState(ValidationState.Enabled)]  
// In this DSL, ParentsHaveChildren is a domain relationship  
// from Person to Person:  
public partial class ParentsHaveChildren  
{  
  // Identify the method as a validation method:  
  [ValidationMethod  
  ( // Specify which events cause the method to be invoked:  
    ValidationCategories.Open // On file load.  
  | ValidationCategories.Save // On save to file.  
  | ValidationCategories.Menu // On user menu command.  
  )]  
  // This method is applied to each instance of the   
  // type (and its subtypes) in a model:   
  private void ValidateParentBirth(ValidationContext context)     
  {  
    // In this DSL, the role names of this relationship  
    // are "Child" and "Parent":   
     if (this.Child.BirthYear < this.Parent.BirthYear   
        // Allow user to leave the year unset:  
        && this.Child.BirthYear != 0)  
      {  
        context.LogError(  
             // Description:  
                       "Child must be born after Parent",  
             // Unique code for this error:  
                       "FAB001ParentBirthError",   
              // Objects to select when user double-clicks error:  
                       this.Child,   
                       this.Parent);  
    }  
  }  
```  
  
 Bu kod hakkında aşağıdaki noktalara dikkat edin:  
  
- Doğrulama yöntemlerinin alan sınıfları veya etki alanı ilişkileri ekleyebilirsiniz. Bu tür için kodu **Dsl\Generated Code\Domain\*.cs**.  
  
- Her doğrulama yöntemi, sınıf ve alt sınıflarından her örneği için uygulanır. Bir etki alanı ilişkisi söz konusu olduğunda, her iki model öğeleri arasında bir bağlantı örneğidir.  
  
- Doğrulama yöntemlerinin belirtilen herhangi bir sırada uygulanmaz ve her bir yöntemin herhangi bir sırada öngörülebilir kendi sınıfının örneklerine uygulanmaz.  
  
- Bu tutarsız sonuçlara neden deposu içeriği güncelleştirmek bir doğrulama yöntemi için genellikle hatalı bir uygulama olmasıdır. Yöntem herhangi bir hata çağırarak bunun yerine, bildirmelisiniz `context.LogError`, `LogWarning` veya `LogInfo`.  
  
- LogError çağrısında, model öğeleri veya kullanıcı hata iletisini çift tıkladığında seçilir ilişki bağlantılar listesini sağlayabilirsiniz.  
  
- Program kodundaki modeli okuma hakkında daha fazla bilgi için bkz: [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
  Örneğin, aşağıdaki etki alanı modeli için geçerlidir. ParentsHaveChildren ilişkisi, alt ve üst adlı rol yok.  
  
  ![DSL tanım diyagramı &#45; ailesi ağaç modeli](../modeling/media/familyt-person.png "FamilyT_Person")  
  
## <a name="validation-categories"></a>Doğrulama kategorileri  
 İçinde <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> özniteliği, belirttiğiniz doğrulama yöntemi yeniden çalıştırıldığında.  
  
|Kategori|Yürütme|  
|--------------|---------------|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Ne zaman kullanıcı doğrulama menü komutunu çağırır.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Model dosyası açıldığında.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Ne zaman dosya kaydedilmiş kalır. Doğrulama hataları varsa, kullanıcı kaydetme iptal etme seçeneği sunulur işlemi.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Ne zaman dosya kaydedilmiş kalır. Bu kategorideki yöntemlerinden hatalar varsa kullanıcı bu dosyayı tekrar açmanın mümkün olmayabileceğini uyarılır.<br /><br /> Bu kategori, test yinelenen adlara veya kimlik doğrulama yöntemlerinin veya yükleme hatalara neden olabilecek diğer koşullar için kullanın.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|ValidateCustom yöntem olduğunda çağrılır. Bu kategorideki doğrulamaları yalnızca program koddan çağrılabilir.<br /><br /> Daha fazla bilgi için [özel doğrulama kategoriler](#custom).|  
  
## <a name="where-to-place-validation-methods"></a>Doğrulama yöntemlerinin yerleştirileceği yeri  
 Farklı bir türde bir doğrulama yöntemi yerleştirerek genellikle aynı etkiyi elde edebilirsiniz. Örneğin, kişi sınıfı ParentsHaveChildren ilişki yerine bir yöntem ekleyin ve sahip bağlantılar aracılığıyla yineleme:  
  
```  
[ValidationState(ValidationState.Enabled)]  
public partial class Person  
{[ValidationMethod  
 ( ValidationCategories.Open   
 | ValidationCategories.Save  
 | ValidationCategories.Menu  
 )  
]  
  private void ValidateParentBirth(ValidationContext context)     
  {  
    // Iterate through ParentHasChildren links:  
    foreach (Person parent in this.Parents)  
    {  
        if (this.BirthYear <= parent.BirthYear)  
        { ...  
  
```  
  
 **Doğrulama kısıtlamaları toplama.** Tahmin edilebilir bir sırada doğrulama uygulamak için böyle bir kök öğe modelinizin bir sahip sınıf bir tek doğrulama yöntemi tanımlayın. Bu teknik, tek bir iletiye birden çok hata raporlarını toplamak da sağlar.  
  
 Dezavantajları: Birleşik yöntemi yönetmek kolaydır ve kısıtlamaların tümü aynı olması gerektiğini `ValidationCategories`. Bu nedenle, her kısıtlama ayrı yöntemlerde mümkünse tutmanızı öneririz.  
  
 **Bağlam önbelleğini değerlerde geçirerek.** Bağlam parametresi rastgele değerler yerleştirebilirsiniz bir sözlük var. Sözlük, doğrulama çalışması süresince devam ettirir. Belirli bir doğrulama yöntemi, örneğin, hata sayısı bağlamında korumak ve yinelenen iletileri ile hata penceresinde taşmasını önlemek için kullanın. Örneğin:  
  
```csharp  
List<ParentsHaveChildren> erroneousLinks;  
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))  
erroneousLinks = new List<ParentsHaveChildren>();  
erroneousLinks.Add(this);  
context.SetCacheValue("erroneousLinks", erroneousLinks);  
if (erroneousLinks.Count < 5) { context.LogError( ... ); }  
  
```  
  
## <a name="validation-of-multiplicities"></a>Çeşitlilikler doğrulama  
 En küçük çokluğu denetlemek için doğrulama yöntemlerinin DSL'nizi için otomatik olarak oluşturulur. Kod yazılır **Dsl\Generated Code\MultiplicityValidation.cs**. Doğrulama etkinleştirdiğinizde, bu yöntemleri etkili **Editor\Validation** DSL Gezgininde.  
  
 1 alan ilişkisine ait bir rolün çokluğu ayarlarsanız.. * veya 1..1, ancak kullanıcı oluşturmaz, bu ilişkinin bir bağlantı bir doğrulama hata iletisi görüntülenir.  
  
 DSL'nizi varsa, örneğin, kişi ve şehir ve ilişkisi olan bir ilişki PersonLivesInTown sınıfları **1..\\** * belediye rolde hiçbir belediye sahip her kişi için bir hata iletisi görünür.  
  
## <a name="running-validation-from-program-code"></a>Program kodundan çalışan doğrulama  
 Doğrulama erişme veya bir ValidationController oluşturarak çalıştırabilirsiniz. Kullanıcıya hata penceresinde görüntülenecek hataları için diyagramın DocData bağlı ValidationController kullanın. Örneğin, bir menü komutu yazıyorsanız `CurrentDocData.ValidationController` komut kümesi sınıfta kullanılabilir:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
partial class MyLanguageCommandSet   
{  
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)   
  {   
   ValidationController controller = this.CurrentDocData.ValidationController;   
...  
  
```  
  
 Daha fazla bilgi için [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
 Ayrı doğrulama denetleyicisi oluşturmak ve hataları kendiniz yönetirsiniz. Örneğin:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
Store store = ...;  
VsValidationController validator = new VsValidationController(s);  
// Validate all elements in the Store:  
if (!validator.Validate(store, ValidationCategories.Save))  
{  
  // Deal with errors:  
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }  
}  
  
```  
  
## <a name="running-validation-when-a-change-occurs"></a>Bir değişiklik meydana geldiğinde çalışan doğrulama  
 Model geçersiz olur, kullanıcıya hemen uyarılır emin olmak istiyorsanız, doğrulama çalıştıran bir depolama olayı tanımlayabilir. Depolama olaylar hakkında daha fazla bilgi için bkz. [olay işleyicileri yaymak değişiklikleri dışında modeli](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Doğrulama kodu yanı sıra, bir özel kod dosyasına ekleyin, **DslPackage** aşağıdaki örneğe benzer içeriğe sahip bir proje. Bu kod `ValidationController` belgeye eklenir. Bu denetleyici doğrulama hataları görüntüler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata listesi.  
  
```csharp  
using System;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
namespace Company.FamilyTree  
{  
  partial class FamilyTreeDocData // Change name to your DocData.  
  {  
    // Register the store event handler:   
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded();  
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory  
         .FindDomainClass(typeof(ParentsHaveChildren));  
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory  
         .FindDomainClass(typeof(Person));  
      EventManagerDirectory events = this.Store.EventManagerDirectory;  
      events.ElementAdded  
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));  
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));  
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));  
    }  
    // Handler will be called after transaction that creates a link:  
    private void ParentLinkAddedHandler(object sender,  
                                ElementAddedEventArgs e)  
    {  
      this.ValidationController.Validate(e.ModelElement,  
           ValidationCategories.Save);  
    }  
    // Called when a link is deleted:  
    private void ParentLinkDeletedHandler(object sender,   
                                ElementDeletedEventArgs e)  
    {  
      // Don't apply validation to a deleted item!   
      // - Validate store to refresh the error list.  
      this.ValidationController.Validate(this.Store,  
           ValidationCategories.Save);  
    }  
    // Called when any property of a Person element changes:  
    private void BirthDateChangedHandler(object sender,  
                      ElementPropertyChangedEventArgs e)  
    {  
      Person person = e.ModelElement as Person;  
      // Not interested in changes in other properties:  
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)  
          return;  
  
      // Validate all parent links to and from the person:  
      this.ValidationController.Validate(  
        ParentsHaveChildren.GetLinksToParents(person)  
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))  
        , ValidationCategories.Save);  
    }  
  }  
}  
  
```  
  
 İşleyiciler, bağlantıları veya öğeleri etkileyen geri alma veya yineleme işlemleri sonra olarak da adlandırılır.  
  
##  <a name="custom"></a> Özel doğrulama kategorileri  
 Standart doğrulama kategoriler, menü ve açık gibi ek olarak, kendi kategorilerinizi tanımlayabilirsiniz. Bu kategorilerden bir program kodunu çağırabilirsiniz. Kullanıcı bunları doğrudan çağrılamaz.  
  
 Özel kategoriler için genel kullanım modeli belirli bir Aracı'nın önkoşulları karşılayıp karşılamadığını test eden bir kategori tanımlamaktır.  
  
 Bir doğrulama yöntemi için belirli bir kategori eklemek için böyle bir öznitelik ile öneki:  
  
```csharp  
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]  
[ValidationMethod(ValidationCategory.Menu)]   
private void TestForCircularLinks(ValidationContext context)   
{...}  
  
```  
  
> [!NOTE]
>  Bir yöntemle kadar ön ek `[ValidationMethod()]` istediğiniz öznitelikler. Bir yöntem hem özel hem de standart kategorisine ekleyebilirsiniz.  
  
 Özel doğrulama çağırmak için:  
  
```csharp  
  
// Invoke all validation methods in a custom category:   
validationController.ValidateCustom  
  (store, // or a list of model elements  
   "PreconditionsForGeneratePartsList");  
```  
  
##  <a name="alternatives"></a> Doğrulama alternatifleri  
 Doğrulama kısıtlamaları hataları bildirin, ancak modelin değiştirmeyin. Bunun yerine, geçersiz olma modeli engellemek istiyorsanız, diğer teknikleri kullanabilirsiniz.  
  
 Ancak, bu teknikler önerilmez. Geçersiz bir model nasıl karar izin vermek daha iyi.  
  
 **Model için geçerlilik geri yüklemek için değişiklik yapın.** Örneğin, kullanıcı, izin verilen en üstünde bir özellik ayarlar, özelliği için maksimum değer sıfırlanamadı. Bunu yapmak için bir kural tanımlar. Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).  
  
 **Geçersiz bir değişiklik yapılmaya çalışılırsa, işlem geri alma.** Ayrıca bu amaç için bir kural tanımlayabilirsiniz, ancak bazı durumlarda bir özellik işleyicisi geçersiz kılmak olası **OnValueChanging()**, veya gibi bir yöntemi geçersiz kılmak için `OnDeleted().` bir işlem geri almak için kullanmak `this.Store.TransactionManager.CurrentTransaction.Rollback().` daha fazla bilgi için bilgi edinmek bkz [etki alanı özellik değeri değişiklik işleyicileri](../modeling/domain-property-value-change-handlers.md).  
  
> [!WARNING]
>  Kullanıcının değişiklik ayarlanır veya bırakıldığı geri olduğunu bilir emin olun. Örneğin, kullanın `System.Windows.Forms.MessageBox.Show("message").`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gezinme ve Program kodundaki modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri](../modeling/event-handlers-propagate-changes-outside-the-model.md)



