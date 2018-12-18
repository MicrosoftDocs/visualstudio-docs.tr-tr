---
title: Öğe oluşturma ve hareketini özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
ms.assetid: cbd28f15-dfd7-46bd-ab79-5430e3ed83c8
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 470ff89dfd864443206c1d9131fb126d58280859
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853837"
---
# <a name="customizing-element-creation-and-movement"></a>Öğe Oluşturma ve Hareketini Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir öğeyi başka sürüklenerek araç kutusundan veya bir yapıştırma veya taşıma işlemi izin verebilirsiniz. Belirttiğiniz ilişkileri kullanarak, taşınan öğeleri hedef öğelere bağlı olabilir.  
  
 Öğe birleştirme yönergesi (EMD) bir model öğesi olduğunda ne olacağını belirtir *birleştirilmiş* başka bir model öğesi olarak. Böyle olduğunda:  
  
- Diyagramda veya bir şekil araç kutusundan kullanıcı sürükler.  
  
- Kullanıcı, bir Ekle menü Gezgini veya bir bölme şekli kullanarak bir öğe oluşturur.  
  
- Kullanıcı bir öğeyi bir Kulvar diğerine taşır.  
  
- Kullanıcı bir öğeyi yapıştırır.  
  
- Öğe birleştirme yönergesi, program kodu çağırır.  
  
  Oluşturma işlemleri kopyalama işlemlerini farklı görünse de, bunlar aslında aynı şekilde çalışır. Örneğin bir öğe eklendiğinde, araç kutusundan bir prototipi çoğaltılır. Prototip, modelin başka bir bölümünden kopyalanan öğeleri aynı şekilde modele birleştirilir.  
  
  Bir EMD nasıl bir nesne veya grup nesne modelinde belirli bir konuma birleştirilip karar sorumluluğundadır. Özellikle, birleştirilmiş Grup modele bağlanmak için hangi ilişkileri örneği karar verir. Bu özellikleri ayarlamak ve ek nesneler oluşturmak için özelleştirebilirsiniz.  
  
  ![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd-merge.png "DSL-EMD_Merge")  
  Öğe birleştirme yönergesinde rolü  
  
  Gömme ilişkisi tanımlarken bir EMD otomatik olarak oluşturulur. Kullanıcılar üst öğeye yeni alt örnekleri eklediğinizde bu varsayılan EMD bir ilişkinin örneğini oluşturur. Özel kod ekleyerek bu varsayılan EMDs örneğin değiştirebilirsiniz.  
  
  Ayrıca, kendi EMDs sürükleyin veya birleştirilmiş ve alan sınıfları farklı birleşimlerini yapıştırın kullanıcıların DSL tanımındaki ekleyebilirsiniz.  
  
## <a name="defining-an-element-merge-directive"></a>Bir öğe birleştirme yönergesinde tanımlama  
 Etki alanı sınıfları, etki alanı ilişkileri, şekiller, bağlayıcılar ve diyagramları için öğe birleştirme yönergeleri ekleyebilirsiniz. Ekleyebilir veya bunları DSL Gezgini'nde alıcı etki alanı sınıfı altında bulun. Alıcı sınıfın modelinde ve yeni ya da kopyalanmış öğesi birleştirilmesi gerektiğini zaten olan öğenin etki alanı sınıftır.  
  
 ![DSL&#45;EMD&#95;ayrıntıları](../modeling/media/dsl-emd-details.png "DSL EMD_Details")  
  
 **Dizin oluşturma sınıfı** alıcı sınıfın üyeleri birleştirilebilir öğelerin etki alanı sınıftır. Dizin oluşturma sınıfının alt sınıfların örneklerini de birleştirilip birleştirilmeyeceğini bu EMD ayarlamadığınız sürece **alt sınıflar için geçerli** false.  
  
 Birleştirme yönergesi iki tür vardır:  
  
- A **birleştirme işlemi** yönergesi tarafından yeni bir öğe bağlı olmaları ağacına ilişkileri belirtir.  
  
- A **İleri birleştirme** yönergesi, başka bir alıcı öğe genellikle bir üst öğeye yeni öğe yönlendirir.  
  
  Yönergeleri birleştirmek için özel kod ekleyebilirsiniz:  
  
- Ayarlama **kullanan özel kabul** dizinleme öğe belirli bir örneğini hedef öğeye birleştirilmiş olup olmadığını belirlemek için kendi kodunuzu eklemek için. Kullanıcı araç kutusundan sürüklediğinde, kodunuzu birleştirme izin vermiyor, "geçersiz" işaretçi gösterir.  
  
   Örneğin, yalnızca alıcı öğe belirli bir durumda olduğunda birleştirme izin verebilir.  
  
- Ayarlama **kullanan özel birleştirme** eklemek için birleştirme işlemi gerçekleştirildiğinde modelinde yapılan değişiklikleri tanımlamak için kendi kodunu sağlayın.  
  
   Örneğin, veri modelinde yeni konumuna kullanarak birleştirilmiş öğesinde özellikleri ayarlayabilirsiniz.  
  
> [!NOTE]
>  Özel birleştirme kodu yazarsanız, bu EMD kullanılarak gerçekleştirilen yalnızca birleştirmeler etkiler. Aynı nesne türünü birleştirme diğer EMDs varsa veya EMD kullanmadan bu nesneleri oluşturan diğer özel kodu varsa, ardından bunların özel birleştirme kodunuz tarafından etkilenmez.  
>   
>  Yeni bir öğe veya yeni ilişki her zaman özel kodunuz tarafından işlendiğinden emin olmak istiyorsanız, tanımlama göz önünde bir `AddRule` gömme ilişkisinde ve `DeleteRule` öğenin etki alanı sınıfı üzerinde. Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Örnek: bir EMD özel kod olmadan tanımlama  
 Aşağıdaki örnek, bir öğe ve bir bağlayıcı aynı anda var olan bir şekil araç kutusundan sürükleyip oluşturmasına olanak verir. Örneğin DSL tanımı için bir EMD ekler. Bu değişiklikten önce kullanıcıların araçları mevcut şekiller üzerine değil ancak diyagram üzerine sürükleyebilirsiniz.  
  
 Kullanıcılar ayrıca öğeleri diğer öğeler üzerine yapıştırabilirsiniz.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Kullanıcıların aynı zamanda bir öğe ve bir bağlayıcı oluşturun  
  
1. Kullanarak yeni bir DSL oluşturma **Minimal dil** çözüm şablonu.  
  
    Bu DSL çalıştırdığınızda, şekilleri ve bağlayıcıları şekiller arasında oluşturmanızı sağlar. Yeni bir sürükleyemezsiniz **ExampleElement** varolan bir şekli araç kutusundan şekli.  
  
2. Öğeleri Birleştir kullanıcıların `ExampleElement` şekilleri oluşturmak, yeni bir EMD `ExampleElement` etki alanı sınıfı:  
  
   1.  İçinde **DSL Gezgini**, genişletme **alan sınıfları**. Sağ `ExampleElement` ve ardından **yeni öğe birleştirme yönergesinde ekleme**.  
  
   2.  Emin olun **DSL ayrıntıları** penceresi açıkken, böylece yeni EMD ayrıntılarını görebilirsiniz. (Menü: **görünümü**, **diğer Windows**, **DSL ayrıntıları**.)  
  
3. Ayarlama **dizin oluşturma sınıfı** hangi sınıfın öğelerin üzerine birleştirilebilir tanımlamak için DSL Ayrıntıları penceresinde `ExampleElement` nesneleri.  
  
    Bu örnekte, seçin `ExampleElements`, böylece kullanıcı, yeni öğeler var olan öğeleri sürükleyebilirsiniz.  
  
    Dizin oluşturma sınıfı DSL Gezgini'nde EMD adını duruma dikkat edin.  
  
4. Altında **bağlantılar oluşturarak birleştirmeyi işle**, iki yolu ekleyin:  
  
   1. Bir yolu, yeni bir öğe üst modeline bağlar. Girmenize gerek yol ifadesi mevcut öğesinden ayarlama gömme ilişkisi üst modele gider. Son olarak, yeni bir öğe atanacak yeni bağlantıya rol belirtir. Yol aşağıdaki gibidir:  
  
       `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
   2. Başka bir yol var olan öğeye yeni öğe bağlar. Başvuru ilişkisi ve yeni bir öğe atanacak rol yol ifadesi belirtir. Bu yolu aşağıdaki gibidir:  
  
       `ExampleElementReferencesTargets.Sources`  
  
      Yolun gezinme aracı her bir yol oluşturmak için kullanabilirsiniz:  
  
   3. Altında **yollarda bağlantılar oluşturarak birleştirmeyi işle**, tıklayın  **\<yolu Ekle >**.  
  
   4. Liste öğesi sağındaki açılan oku tıklatın. Ağaç görünümünde görünür.  
  
   5. Belirlemek istediğiniz yolu oluşturmak için ağaç düğümleri genişletin.  
  
5. DSL test edin:  
  
   1.  Yeniden oluşturun ve çözümü çalıştırmak için F5 tuşuna basın.  
  
        Metin şablonlarından yeni DSL tanımı için uygun olması için oluşturulan kodu güncelleştirilecek olduğundan yeniden normalden daha uzun sürer.  
  
   2.  Deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sahip başlatıldı, DSL'nin bir model dosyasını açın. Bazı örnek öğeleri oluşturun.  
  
   3.  Sürükleyin **örnek öğesi** varolan bir şekli üzerine aracı.  
  
        Yeni bir şekli görünür ve varolan bir şekli bir bağlayıcı ile bağlantılıdır.  
  
   4.  Varolan bir şekli kopyalayın. Başka bir şekil seçmeniz ve yapıştırın.  
  
        İlk şekli bir kopyası oluşturulur.  Yeni bir ada sahip ve ikinci şekli bir bağlayıcı ile bağlantılıdır.  
  
   Bu yordamdan aşağıdaki noktalara dikkat edin:  
  
-   Öğe birleştirme yönergeleri oluşturarak, öğenin diğer kabul etmek için herhangi bir sınıf izin verebilirsiniz. Alıcı etki alanı sınıfında EMD oluşturulur ve kabul edilen etki alanı sınıfı belirtilen **dizin sınıfı** alan.  
  
-   Yolları tanımlayarak, ne tür bağlantıların gerektiğini belirtebilirsiniz yeni öğenin varolan modele bağlanmak için kullanılır.  
  
     Belirttiğiniz bağlantı bir gömme ilişkisi içermelidir.  
  
-   Araç kutusu ve ayrıca yapıştırma işlemlerine oluşturmaya EMD etkiler.  
  
     Yeni öğeleri oluşturan özel kodu yazarsanız, açıkça EMD kullanarak çağırabilirsiniz `ElementOperations.Merge` yöntemi. Bu, kodunuzu yeni öğeler modele diğer işlemler aynı şekilde bağlantı emin olur. Daha fazla bilgi için [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Örnek: Bir EMD için özel kabul kod ekleme  
 Bir EMD için özel kod ekleyerek daha karmaşık birleştirme davranışı tanımlayabilirsiniz. Bu basit örnekte, kullanıcı diyagrama öğe sayısından daha eklemesini önler. Örneğin, varsayılan gömme ilişkisi eşlik eden EMD değiştirir.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Hangi kullanıcı ekleyebilir kısıtlamak için özel kabul kod yazma  
  
1.  Bir DSL kullanarak oluşturma **Minimal dil** çözüm şablonu. DSL tanım diyagramı açın.  
  
2.  DSL Gezgini'nde **alan sınıfları**, `ExampleModel`, **öğe birleştirme yönergeleri**. Adlı öğe birleştirme yönergesinde seçin `ExampleElement`.  
  
     Kullanıcı yeni nasıl oluşturacağınızı bu EMD denetimleri `ExampleElement` Toolbox'tan sürükleyerek Örneğin bu modeldeki nesneleri.  
  
3.  İçinde **DSL ayrıntıları** penceresinde **kullanan özel kabul**.  
  
4.  Çözümü yeniden derleyin. Oluşturulan kod modelinden güncelleştirilecek çünkü bu normalden daha uzun sürer.  
  
     Bir yapı hatası bildirilen, benzer olacaktır: "Company.ElementMergeSample.ExampleElement içermiyor bir tanımı için CanMergeExampleElement..."  
  
     Yöntemini uygulamalıdır `CanMergeExampleElement`.  
  
5.  Yeni bir kod dosyasında oluşturma **Dsl** proje. İçeriğini aşağıdaki kodla değiştirin ve projenizin ad alanına ad alanını değiştirme.  
  
    ```csharp  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace Company.ElementMergeSample // EDIT.  
    {  
      partial class ExampleModel  
      {  
        /// <summary>  
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.  
        /// This happens when the user pastes an ExampleElement  
        /// or drags from the toolbox.  
        /// Determines whether the merge is allowed.  
        /// </summary>  
        /// <param name="rootElement">The root element in the merging EGP.</param>  
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>  
        /// <returns>True if the merge is allowed</returns>  
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)  
        {  
          // Allow no more than 4 elements to be added:  
          return this.Elements.Count < 4;  
        }  
      }  
    }  
  
    ```  
  
     Bu basit örnekte üst modele birleştirilebilir öğelerin sayısını kısıtlar. Daha çok ilginizi çeken koşullara için yöntem özelliklerinden herhangi birini ve alıcı nesnenin bağlantıları inceleyebilirsiniz. İçinde gerçekleştirilen birleştirme öğelerin özelliklerini inceleyebilirsiniz bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Hakkında daha fazla bilgi için `ElementGroupPrototypes`, bkz: [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md). Bir modeli okuyan kod yazma hakkında daha fazla bilgi için bkz. [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6.  DSL test edin:  
  
    1.  Çözümü yeniden derlemek için F5 tuşuna basın. Deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] açıldığında DSL'nizi örneği açın.  
  
    2.  Yeni öğeler, çeşitli yollarla oluşturun:  
  
        1.  Sürükleyin **örnek öğesi** diyagram üzerine aracı.  
  
        2.  İçinde **örnek Model Gezgini**, kök düğümüne sağ tıklayın ve ardından **yeni örnek öğesi ekleme**.  
  
        3.  Kopyalayın ve bir öğeyi diyagram üzerine yapıştırın.  
  
    3.  Modele dörtten fazla öğeleri eklemek için şu adımlardan herhangi birini kullanamazsınız doğrulayın. Tüm öğe birleştirme yönergesinde kullandıkları olmasıdır.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Örnek: Özel birleştirme kodu için bir EMD ekleme  
 Özel birleştirme kodu, kullanıcı bir araç sürüklediğinde veya bir öğenin üstüne yapıştırır ne tanımlayabilirsiniz. Özel bir birleştirme tanımlamak için iki yolu vardır:  
  
1. Ayarlama **kullanan özel birleştirme** ve gerekli kodu sağlayın. Kodunuzu oluşturulan birleştirme kodu değiştirir. Birleştirme yaptığı tamamen tanımlanacak istiyorsanız bu seçeneği kullanın.  
  
2. Geçersiz kılma `MergeRelate` yöntemi ve isteğe bağlı olarak `MergeDisconnect` yöntemi. Bunu yapmak için ayarlamalısınız **Generates Double Derived** alan sınıfının özelliği. Kodunuz, temel sınıfta oluşturulan birleştirme kodu çağırabilir. Birleştirmeyi gerçekleştirdikten sonra ek işlemleri gerçekleştirmek istiyorsanız bu seçeneği kullanın.  
  
   Bu yaklaşım, yalnızca bu EMD kullanılarak gerçekleştirilen birleştirme etkiler. Tüm yollar, birleştirilmiş öğesi oluşturulabilir değiştirmek istediğiniz alternatif tanımlamak için varsa, bir `AddRule` gömme ilişkisinde ve `DeleteRule` birleştirilmiş bir etki alanı sınıfı üzerinde. Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>MergeRelate geçersiz kılmak için  
  
1.  DSL tanımındaki kod eklemek istediğiniz EMD tanımladığınız emin olun. İsterseniz, yollarını ekleyin ve tanımlayın önceki bölümlerde açıklandığı gibi özel kabul kod.  
  
2.  DslDefinition diyagramda, birleştirme alıcı sınıfını seçin. Genellikle bu gömme ilişkisi kaynak sonunda sınıftır.  
  
     Örneğin, en az bir dil çözümü oluşturulan bir DSL içinde seçin `ExampleModel`.  
  
3.  İçinde **özellikleri** penceresinde **Generates Double Derived** için **true**.  
  
4.  Çözümü yeniden derleyin.  
  
5.  İçeriği İnceleme **Dsl\Generated Files\DomainClasses.cs**. Arama adlı yöntemleri için `MergeRelate` ve bunların içeriğini inceleyin. Bu, kendi sürümleri yazmanıza yardımcı olur.  
  
6.  Yeni bir kod dosyasında, alıcı sınıfı için bir parçalı sınıf yazma ve geçersiz kılma `MergeRelate` yöntemi. Taban yöntemini çağırmayı unutmayın. Örneğin:  
  
    ```csharp  
    partial class ExampleModel  
    {  
      /// <summary>  
      /// Called when the user drags or pastes an ExampleElement onto the diagram.  
      /// Sets the time of day as the name.  
      /// </summary>  
      /// <param name="sourceElement">Element to be added</param>  
      /// <param name="elementGroup">Elements to be merged</param>  
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)  
      {  
        // Connect the element according to the EMD:  
        base.MergeRelate(sourceElement, elementGroup);  
  
        // Custom actions:   
        ExampleElement mergingElement = sourceElement as ExampleElement;  
        if (mergingElement != null)  
        {  
          mergingElement.Name = DateTime.Now.ToLongTimeString();  
        }  
      }  
    }  
  
    ```  
  
#### <a name="to-write-custom-merge-code"></a>Özel birleştirme kodu yazmak için  
  
1. İçinde **Dsl\Generated Code\DomainClasses.cs**, adlı yöntemleri inceleyin `MergeRelate`. Bu yöntemler varolan modeli ile yeni bir öğe arasındaki bağlantılar oluşturun.  
  
    Ayrıca, adlı yöntemleri inceleyin `MergeDisconnect`. Silinecek olduğunda bu yöntemler bir öğeyi model bağlantısını.  
  
2. İçinde **DSL Gezgini**seçin veya özelleştirmek istediğiniz öğe birleştirme yönergesinde oluşturun. İçinde **DSL ayrıntıları** penceresinde **kullanan özel birleştirme**.  
  
    Bu seçeneği ayarladığınızda **birleştirme işlemi** ve **İleri birleştirme** seçenekler yok sayılır. Kodunuzu bunun yerine kullanılır.  
  
3. Çözümü yeniden derleyin. Oluşturulan kod dosyaları modelden güncelleştirilecek nedeniyle normalden daha uzun sürer.  
  
    Hata iletileri görüntülenir. Oluşturulan kodun yönergeleri görmek için hata iletileri çift tıklayın. Bu yönergeler, iki yöntem sağlamayı isteyin `MergeRelate` *YourDomainClass* ve `MergeDisconnect` *YourDomainClass*  
  
4. Ayrı bir kod dosyasında bir parçalı sınıf tanımında yöntemleri yazın. Daha önce inceledi örnekler gerekenler Öner.  
  
   Özel birleştirme kodu, nesneleri ve ilişkileri doğrudan oluşturan kodu etkilemez ve diğer EMDs etkilemez. Öğe nasıl oluşturulduğuna bakılmaksızın, ek değişiklikler uygulandığından emin olmak için yazma göz önünde bulundurun. bir `AddRule` ve `DeleteRule` yerine. Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Bir birleştirme işlemi yeniden yönlendirme  
 Bir iletme birleştirme yönergesi, bir birleştirme işlemi hedefi yönlendirir. Genellikle yeni ilk hedef katıştırma üst hedefidir.  
  
 Örneğin, bileşen diyagramı şablonuyla oluşturulan bir DSL içinde bağlantı noktaları bileşenlerde katıştırılır. Bağlantı noktaları, bir bileşen şekli kenarında küçük şekiller olarak görüntülenir. Kullanıcı, bağlantı noktası aracını bileşenin şeklin üzerine sürükleyerek, bağlantı noktaları oluşturur. Ancak bazı durumlarda, kullanıcı Port aracı yanlışlıkla bileşen yerine var olan bir bağlantı noktası üzerine sürüklediğinde ve işlem başarısız olur. Var olan çeşitli bağlantı noktaları olduğunda bir kolayca hata budur. Bu rahatsızlığı kullanıcıya yardımcı olmak için varolan bir bağlantı noktasını sürüklenerek, ancak ana bileşen için yeniden yönlendirilen eyleme sahip bağlantı noktalarına izin verebilirsiniz. İşlem, hedef öğenin bileşeni değilmiş gibi çalışır.  
  
 Bileşen modeli çözümde iletme birleştirme yönergesi oluşturabilirsiniz. Derleme ve özgün çözümü çalıştırın, kullanıcıların herhangi bir sayıda sürükleyebilirsiniz görmelisiniz **giriş bağlantı noktası** veya **çıkış bağlantı noktasına** öğelerden **araç kutusu** bir için**Bileşen** öğesi. Ancak, bunlar mevcut bir bağlantı noktasına bir bağlantı noktası sürükleyemezsiniz. Bu taşıma etkin olmadığını uyaran işaretçiyi kullanılamaz. Yanlışlıkla bir bağlantı noktasıdır, ancak iletme birleştirme yönergesi oluşturabilirsiniz var olan bir bırakılan **giriş bağlantı noktası** iletilir **bileşen** öğesi.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Bir iletme birleştirme yönergesi oluşturmak için  
  
1.  Oluşturma bir [!INCLUDE[dsl](../includes/dsl-md.md)] bileşen modeli şablonunu kullanarak çözüm.  
  
2.  Görüntü **DSL Gezgini** DslDefinition.dsl açarak.  
  
3.  İçinde **DSL Gezgini**, genişletme **alan sınıfları**.  
  
4.  **ComponentPort** soyut etki alanı sınıfı, hem temel sınıfını **InPort** ve **OutPort**. Sağ **ComponentPort** ve ardından **yeni öğe birleştirme yönergesinde ekleme**.  
  
     Yeni bir **öğe birleştirme yönergesinde** düğümü altında görünür **öğe birleştirme yönergeleri** düğümü.  
  
5.  Seçin **öğe birleştirme yönergesinde** düğüm ve açık **DSL ayrıntıları** penceresi.  
  
6.  Dizin oluşturma sınıfı listesinde **ComponentPort**.  
  
7.  Seçin **birleştirmeyi farklı bir alan sınıfına ilet**.  
  
8.  Yol seçim listesinde genişletin **ComponentPort**, genişletme **ComponentHasPorts**ve ardından **bileşeni**.  
  
     Yeni yol buna benzemelidir:  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Çözüm kaydedin ve ardından sağdaki düğmesine tıklayarak şablonlarını Dönüştür **Çözüm Gezgini** araç çubuğu.  
  
10. Derleme ve çözümü çalıştırın. Yeni bir örneğini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] görünür.  
  
11. İçinde **Çözüm Gezgini**, Sample.mydsl açın. Diyagram ve **ComponentLanguage araç kutusu** görünür.  
  
12. Sürükleme bir **giriş bağlantı noktası** gelen **araç kutusu** diğerine **giriş bağlantı noktası.** Sonraki adımda bir **OutputPort** için bir **InputPort** ve için başka bir **OutputPort**.  
  
     Kullanılamayan işaretçi görmemeniz gerekir ve yeni bırak olmalıdır **giriş bağlantı noktası** mevcut bir. Yeni **giriş bağlantı noktası** ve onu başka bir noktaya sürükleyin **bileşeni**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gezinme ve Program kodundaki modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Araçları ve araç kutusunu özelleştirme](../modeling/customizing-tools-and-the-toolbox.md)   
 [Bağlantı hattı diyagramları örneği DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



