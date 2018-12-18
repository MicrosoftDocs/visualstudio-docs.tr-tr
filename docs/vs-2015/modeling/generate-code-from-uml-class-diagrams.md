---
title: UML sınıf diyagramlarından kod oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a8108a552f21504714fea84bcb29194db4d947cf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764787"
---
# <a name="generate-code-from-uml-class-diagrams"></a>UML sınıf diyagramları aracılığıyla kod oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da UML sınıf diyagramlarından Visual C# .NET kodunu oluşturmak için **kod üret** komutu. Varsayılan olarak, komut seçtiğiniz her UML türü için bir C# türü oluşturur. Kod oluşturan metin şablonlarını değiştirerek veya kopyalayarak bu davranışı değiştirebilir ve genişletebilirsiniz. Modelinizdeki farklı paketlerde bulunan türler için farklı davranış belirtebilirsiniz.  

 **Kod üret** kullanıcının öğe seçiminden kod oluşturmak ve her UML sınıfı veya diğer öğe için bir dosya oluşturmak için komut özellikle uygun. Örneğin, ekran görüntüsü iki UML sınıfından oluşturulmuş iki C# dosyası gösterir.  

 Kod içinde oluşturulan dosyalar yok UML öğeleriyle 1:1 ilişki oluşturmak istiyorsanız alternatif olarak, koduyla çağrılan metin şablonları yazmayı düşünebilirsiniz **tüm Şablonları Dönüştür** komutu. Bu yöntem hakkında daha fazla bilgi için bkz. [bir UML modelinden dosyalar oluşturma](../modeling/generate-files-from-a-uml-model.md).  

 ![UML sınıf diyagramı ve oluşturulan C&#35; sınıf dosyaları. ](../modeling/media/oob-gencode1.png "oob_GenCode1")  

 Visual Studio'da UML sınıf diyagramları hakkında daha fazla bilgi için aşağıdaki konulara bakın:  

- [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)  

- [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)  

  UML sınıf diyagramları Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="using-the-generate-code-command"></a>Kod Oluştur Komutunu Kullanma  
 Aşağıdaki yordam varsayılan davranışını açıklar **kod üret** komutu:  

#### <a name="to-generate-a-separate-file-for-each-element"></a>Her öğe için ayrı bir dosya oluşturmak üzere  

1. Sınıflar içeren bir UML modeli oluşturun. Model öğelerine stereotipler uygulayabilirsiniz.  

    Daha fazla bilgi için [varsayılan kod oluşturma dönüşümleri](#default).  

2. Bir sınıf diyagramında veya **UML Model Gezgini**, kodu oluşturmak istediğiniz öğeleri seçin. Aşağıdakilerden birini seçebilirsiniz:  

   -   Belirli bir öğe kümesi.  

   -   İçeriğinden kod oluşturmak için bir paket veya model.  

   -   Diyagramdaki tüm öğeleri seçmek için diyagram.  

3. Seçili öğe için kısayol menüsünü açın ve ardından **kod üret**.  

    Kullandığınız ilk kez **kod üret** belirli bir modeldeki bir iletişim kutusu görüntülenir. Bu iletişim kutusu, modelin kod oluşturma parametrelerini düzenlemenizi sağlar.  

    Seçin **Tamam** , bu parametreleri değiştirmek istediğinizi bilmiyorsanız.  

    Daha sonra bu iletişim kutusuna dönmek için açın **UML Model Gezgini**. Modelleme projesinin kısayol menüsünü ve ardından açık **kod oluşturma ayarlamak**. Daha fazla bilgi için [Kod Oluştur komutunu özelleştirme](#custom).  

   C# kodu içeren dosyalar oluşturulur. Varsayılan durumda, her tür için bir dosya oluşturulur ve dosyalar bir C# sınıf kitaplığı projesinde oluşturulur. Ancak, bu davranışı özelleştirebilirsiniz. Daha fazla bilgi için [Kod Oluştur komutunu özelleştirme](#custom).  

   Bazı doğrulama testleri, C#'ye çevrilebilmesini sağlamak için modele uygulanır. Bu testler başarısız olursa, bir hata iletisi görüntülenir ve kod oluşturma gerçekleştirilemez. Doğrulama menü komutu oluşturduysanız, doğrulama komutunuzun başarısız olduğu herhangi bir öğe için kod oluşturulmaz. Daha fazla bilgi için [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md).  

##  <a name="default"></a> Varsayılan kod oluşturma dönüşümleri  
 Bu bölümde tarafından oluşturulan sonuçlar özetlenmektedir **kod üret** komutu özelleştirmediğiniz sürece. Daha fazla bilgi için [Kod Oluştur komutunu özelleştirme](#custom).  

- UML modelinde seçtiğiniz her tür için bir C# türü oluşturulur. Her türü altında ayrı kod dosyasına yerleştirilir **GeneratedCode** klasör.  

- UML türü bir paket içinde yer alıyorsa, oluşturulan C# türü bir ad alanı içine yerleştirilir ve dosya ad alanıyla aynı ada sahip bir klasörde oluşturulur.  

- Her biri için bir C# özelliği oluşturulur `Attribute` bir UML sınıf.  

- Her biri için bir C# yöntemi oluşturulur `Operation` UML türü.  

- Sınıfın katıldığı her gezilebilir ilişkilendirme için bir C# alanı oluşturulur.  

  Her UML türüne bir stereotip ekleyerek, oluşturulan C# türünün daha fazla özelliğini denetleyebilirsiniz.  

|**Bu C# türünü oluşturmak için**|**Şu UML türünü çizin**|**Bu stereotipi uygulayın**|  
|---------------------------------|----------------------------|-------------------------------|  
|örneği|örneği|\<yok > veya<br /><br /> C# sınıfı|  
|Arabirim|Arabirim|\<yok > veya<br /><br /> C# arabirimi|  
|Sabit Listesi|Sabit Listesi|\<yok > veya<br /><br /> C# sabit listesi|  
|Temsilci|örneği|C# temsilcisi|  
|Yapı|örneği|C# yapısı|  

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Bir türde veya başka bir öğede bir stereotip ayarlamak için  

1. Diyagram üzerinde veya öğe için kısayol menüsünü açın **UML Model Gezgini**ve ardından **özellikleri**.  

2. İçinde **özellikleri** penceresinde, aşağı açılan oku seçin **stereotipler** özelliği ve ardından uygulamak istediğiniz stereotip için onay kutusunu seçin.  

   > [!TIP]
   >  C# stereotipleri görünmezse, ilgilendiğiniz model öğelerini içeren model veya paket için C# Profilini etkinleştirin. Paket veya model içinde kök seçin **UML Model Gezgini**. Ardından **özellikleri** penceresinde seçin **profili**ve C# profilini etkinleştirin.  

3. Genişletin **stereotipler** ayarlayabileceğiniz ek özellikleri görmek için özellik.  

   **Açıklama** türleri, öznitelikleri, işlemleri ve ilişkileri özelliklerini yazılır `<summary>` oluşturulan kod açıklamaları. Türlere bağlı açıklama öğeleri yazılır `<remarks>` yorumlar.  

## <a name="varying-the-generated-code"></a>Oluşturulan kodu değiştirme  
 Oluşturulan kod her türün, özniteliğin veya işlemin özelliklerine göre değişir. Örneğin, ayarlarsanız **soyut** özelliği true olarak bir sınıfın sonra `abstract` anahtar sözcüğü oluşturulan sınıfta görünür. Ayarlarsanız **Çoğulluk** bir özniteliğin ** 0..\\ , oluşturulan özellik olacaktır bir `IEnumerable<>` türü.  

 Ayrıca, her stereotip ayarlayabileceğiniz çeşitli ek özellikler sağlar. Bu değerler için C# kodunda uygun anahtar sözcüklere çevrilir. Örneğin, özelliğini ayarlarsanız `Is Static` sınıfta, ardından C# sınıfı olacaktır `static`.  

 Bu ek özellikleri ayarlamak için diyagramda sınıfı veya diğer öğeyi seçin. Özellikler penceresinde genişletin **stereotipler**ve ardından gibi C# stereotipini genişletin **C# sınıfı**.  Sınıflar için bu ek özellikler şunlardır:  

- CLR Öznitelikleri  

- Is Partial  

- Is Static  

- Is Unsafe  

- Paket Görünürlüğü  

  Her öznitelik ve işlemde ayarlayabileceğiniz stereotip özellikleri de vardır. Yeni bir öznitelikte özellikleri göremiyorsanız çalıştırma **kod üret**.  

##  <a name="custom"></a> Kod Oluştur komutunu özelleştirme  
 **Kod üret** metin şablonları kümesi kullanılarak model öğelerinizin dönüştürülmesiyle çalışır komutu. Metin şablonları hakkında daha fazla bilgi için bkz. [kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md).  

 Şablonlar kümesi içinde belirtilen *metin şablon bağlamaları*. Metin şablon bağlaması, hangi şablon, oluşturulan çıkışın nereye yerleştirileceğini, uygulanması gereken ve diğer parametreleri belirtir **kod üret** komutu.  

 İlk kez çalıştırdığınızda **kod üret** belirli bir modelde, modelin köküne bunu ekler varsayılan şablon bağlamaları kümesini komutu. Bu bağlamalar, modeldeki tüm öğelere uygulanır.  

 Ancak, kendi bağlamalarınızı paketlere, sınıflara veya diğer öğelere ekleyerek bu varsayılan bağlamaları geçersiz kılabilir ve bunlara ekleme yapabilirsiniz. Bağlama, bağlı olduğu öğe içinde bulunan tüm öğelere uygulanır. Örneğin, belirli bir paket içindeki tüm türlerin farklı şablonlar kümesi tarafından dönüştürülmesini veya farklı bir klasöre çıkarılmasını istiyorsanız, pakete şablon bağlamaları ekleyebilirsiniz.  

 Bir model öğesine eklenen şablon bağlamalarını denetlemek için üç noktayı seçin **[...]**  içinde **metin şablon bağlamaları** Özellikler penceresindeki özellik.  

 **Kod üret** komutu, şablonları seçtiğiniz her model öğesine uygular. Her öğe için uygulanan şablonlar kümesi, modelin kökü de dahil olmak üzere kapsayıcılarına eklenen birleştirilmiş şablon kümesidir.  

 Bu kümedeki iki şablon bağlaması aynı ada sahipse, daha küçük kapsayıcıdaki bağlama daha büyük kapsayıcıdaki bağlamayı geçersiz kılar. Örneğin, model kökünün ada sahip bir bağlama sahip **sınıf şablonu**. Belirli bir paket içeriğini uygulanan kendi şablonunuzu sağlamak için adında kendi şablon bağlamanızı tanımlayın **sınıf şablonu**.  

 Model öğesine birden fazla şablon uygulanabilir. Her model öğesinden birden fazla dosya oluşturabilirsiniz.  

> [!NOTE]
>  Modelin köküne eklenen bağlamalar, modeldeki tüm öğeler için varsayılanlar olarak görev görür. Bu varsayılan bağlamaları görmek için **UML Model Gezgini**. Modelleme projesinin kısayol menüsünü açın ve sonra seçin **kod oluşturma ayarlamak**. Alternatif olarak, UML Model Gezgini'nde modelin kökünü seçebilirsiniz. Özellikler penceresinde **[...]**  içinde **metin şablon bağlamaları** özelliği. Bağlamaları kullanılana dek görünmeyecektir **kod üret** en az bir kez komutu. Şablon bağlamaları bir diyagrama eklenemez.  

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Metin şablon bağlamalarını bir pakete veya başka bir model öğesine eklemek için  

1. İçinde **UML Model Gezgini**, model öğesinin kısayol menüsünü açın ve ardından **özellikleri**. Genellikle, metin şablon bağlamalarını bir pakete veya modelin köküne eklersiniz.  

2. İçinde **özellikleri** penceresinde üç nokta düğmesini (**[...]** ) içinde **metin şablon bağlamaları** özelliği.  

    **Metin şablon bağlamaları** iletişim kutusu görüntülenir.  

3. Seçin **Ekle** yeni metin şablon bağlaması oluşturmak için.  

    \- veya -  

    Düzenlemek için varolan bir bağlamayı seçin.  

    Her şablon bağlaması, belirtilen bir şablonun seçtiğiniz model öğesine ve içerdiği diğer model öğelerine nasıl uygulanması gerektiğini tanımlar.  

4. İletişim kutusunda, metin şablon bağlamasının özelliklerini ayarlayın.  


   |    **Özelliği**    |                                                                                                                                                                                                                                                                                                                    **Açıklama**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Ad        |                                                                                                                                                                                                                                                  Bu bağlama için bir ad. Kapsayan bir paketten veya modelden devralınan bir bağlamayı geçersiz kılmak için geçersiz kılmak istediğiniz bağlamayla aynı adı kullanın.                                                                                                                                                                                                                                                  |
   |     Üzerine yaz      |                                                                                                                                                                                                                                                                                                      True ise, varolan tüm kodların üzerine yazılır.                                                                                                                                                                                                                                                                                                       |
   |    Hedef Adı     | Oluşturulan dosyanın adı.<br /><br /> Bu dizeye gibi ifadeler ekleyebilirsiniz `{Name}` veya `{Owner.Name}`. Örneğin, şunu yazabilirsiniz: `{Owner.Name}_{Name}`. İfade, model öğesi üzerinde değerlendirilir. Yöntemlerin değil, öğelerin özelliklerini kullanabilir. Hangi özelliklerin kullanılabileceğini öğrenmek için öğesinde türlerin özelliklerine bakın **Microsoft.VisualStudio.Uml.\\ ***. \*\*Önemli:* \* `{Name}` veya `{Owner.Name}` yalnızca kullanılabilir **hedef adı** özelliği. Oluşturulan sınıfın adını değiştirmek için şablonu değiştirmeniz gerekir. Daha fazla bilgi için [Writing a Text Template](#writing). |
   |    Proje Yolu    |                                                                      Yolunu belirtir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dönüştürme içeren bir proje Çıkış dosyalarını. Yeni bir proje oluşturmak için yazılan değerleri kullanın. Üç nokta düğmesini (**[...]** ) varolan bir projeyi seçin.<br /><br /> Yoksa yeni bir proje oluşturulacaktır. Bu bir C# sınıf kitaplığı projesi olacaktır.<br /><br /> Bunu yapmak için projeyi doğrudan yazmanız gerekir. %ProgramFiles% veya %LocalAppData% gibi ortam değişkeni makrolarını dahil edebilirsiniz.                                                                       |
   |  Hedef Dizin  |                                                                                          Hedef dosyanın oluşturulduğu klasör. Yol, proje klasörüyle ilişkilidir.<br /><br /> Kullanabileceğiniz `{PackageStructure}` kapsayan paketlerin adlarına karşılık gelen bir yol eklemek için ifade. Varsayılan değer `\GeneratedCode\{PackageStructure}` şeklindedir. %TEMP% veya %HomePath% gibi ortam değişkenlerini de ekleyebilirsiniz. **Önemli:** `{PackageStructure}` yalnızca kullanılabilir **hedef dizin** özelliği.                                                                                          |
   | Şablon Dosya Yolu |                                                                                                                                                           Dönüşümü gerçekleştirecek şablon.<br /><br /> Sağlanan şablonları kullanabilir veya kendi şablonunuzu oluşturabilirsiniz. Sağlanan şablonları aşağıdaki konumda bulabilirsiniz:<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |


5. Bir öğeye istediğiniz kadar bağlama ekleyebilirsiniz.  

##  <a name="writing"></a> Metin şablonu yazma  
 Kendi metin şablonlarınızı yazabilirsiniz. Metin şablonları, program kodu veya başka tür bir metin dosyası oluşturabilirsiniz.  

 Standart şablonların kopyalarını değiştirerek başlamanızı öneririz. Şablonları aşağıdaki konumlardan kopyalayabilirsiniz:  

 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  

 Metin şablonlarını anlamak için aşağıdaki konulara bakın.  

- Metin şablonu ortaya çıkan dosyanın prototipidir ve hem ortaya çıkan metni hem de modeli okuyan program kodunu içerir. Daha fazla bilgi için [kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md).  

- Program kodundaki UML modeline gitmek için UML API'sini kullanmanız gerekir. Daha fazla bilgi için [UML modelini gezme](../modeling/navigate-the-uml-model.md) ve [UML modelleme genişletilebilirliği için API Başvurusu](../modeling/api-reference-for-uml-modeling-extensibility.md).  

  Şablonlar ile kullanmak için **kod üret** komutunu modelleme yönergesini dahil etmelisiniz. Örneğin:  

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  

  `ElementType` Özniteliği, bu şablonun uygulandığı UML öğesinin türünü tanımlar.  

  Şablon içinde `this` aşağıdaki özelliklere sahip geçici bir sınıfa aittir:  

- `Element` UML = <xref:Microsoft.VisualStudio.Uml.Classes.IElement> için şablon uygulanıyor.  

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  

- `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  

- `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>. Daha fazla bilgi için [tümleştirme UML modellerini diğer modeller ve araçlarla birlikte](../modeling/integrate-uml-models-with-other-models-and-tools.md).  

- `ProfileName` "C #Profile" =  

- `ServiceProvider`: <xref:System.IServiceProvider>  

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.  

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Bu, UML ModelStore'un uygulandığı Görselleştirme ve Modelleme SDK Deposudur. UML edinme <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, kullanın `this.Element.GetModelStore()`.  

  Metin şablonu yazarken aşağıdaki noktaları yararlı bulabilirsiniz. Bu bilgiler, ayrıntılı olarak açıklanan [kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md).  

- Sonucun dosya adı uzantısı ayarlayabilirsiniz `Output` yönergesi. Bir `Output` yönergesi, her metin şablonunda gereklidir.  

- Bazı derlemelere şablon tarafından otomatik olarak başvurulur. Bu derlemeler, örneğin System.dll ve Microsoft.VisualStudio.Uml.Interfaces.dll'yi içerir.  

   İçinde program kodu oluştururken diğer derlemeleri kullanmak için kullanmalısınız bir `Assembly` yönergesi. Örneğin:  

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  

- Gibi bazı ad alanları `System` otomatik olarak program kodunuza aktarılır. Diğer ad alanları için kullanabileceğiniz `Import` kullanacağınız aynı şekilde yönerge bir `using` deyimi. Örneğin:  

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  

- Kullanım `Include` başka bir dosyanın metnine başvurmak için yönergesi.  

- Ayraç içine şablonunun bölümlerine `<# ... #>` tarafından yürütülen **kod üret** komutu. Şablonun bu parantezlerin dışında kalan bölümleri sonuç dosyasına kopyalanır. Oluşturulan kod ile oluşturulan metni ayırt etmek çok önemlidir. Oluşturulan metin herhangi bir dilde olabilir.  

- `<#= Expressions #>` değerlendirilir ve dizelere dönüştürülür.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)   
 [UML modeli aracılığıyla dosya oluşturma](../modeling/generate-files-from-a-uml-model.md)



