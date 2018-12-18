---
title: Araçları ve Araç Kutusunu Özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3b0acab24dbb7ff1313e62e91b17bf87190dbb99
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967447"
---
# <a name="customizing-tools-and-the-toolbox"></a>Araçları ve Araç Kutusunu Özelleştirme

Kullanıcıların kendi modellere eklemek istediğiniz öğeleri için araç kutusu öğelerini tanımlamanız gerekir. Araçlar iki tür vardır: öğe araçları ve bağlantı araçları. Oluşturulan tasarımcıda bir kullanıcı şekil diyagrama sürüklemek öğe aracına seçebilirsiniz ve şekiller arasında bağlantılar çizmek için bir bağlantı aracını seçebilirsiniz. Genel olarak, öğe araçlarını modellerini için etki alanı sınıfların örneklerini eklemelerine olanak ve bunları etki alanı ilişki örneklerini eklemek bağlantı araçları sağlar.

## <a name="ToolboxDef"></a> Araç kutusu nasıl tanımlanır
 DSL Gezgini içinde Düzenleyici düğüm ve bunun altındaki düğümleri genişletin. Genellikle bu benzer bir hiyerarşi görürsünüz:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

DSL Gezgini bu kısmında, şunları yapabilirsiniz:

-   Yeni sekmeler oluşturun. Sekmeleri bölüm başlıkları araç kutusunda tanımlayın.

-   Yeni Araçları oluşturun.

-   Araçlar kopyalayıp yeniden açın.

-   Listede araçları yukarı veya aşağı taşıyın.

-   Sekmeler ve Araçları'nı silin.

> [!IMPORTANT]
> Eklemek veya DSL Gezgini içinde öğeleri yapıştırmak için Yeni düğümün dizinleriyle sağ tıklayın. Örneğin, bir aracı eklemek için sekmesinde sağ tıklayın ve **Araçları** düğümü. Sekme eklemek için sağ **Düzenleyicisi** düğümü.

**Araç kutusu simgesi** özelliği her aracı bir 16 x 16 bit eşlem dosyası başvurur. Bu dosyalar genellikle tutulan **Dsl\Resources** klasör.

**Sınıfı** öğesi aracı özelliği somut bir etki alanı sınıfına başvuruyor. Varsayılan olarak, bu sınıfın örneklerinin aracı oluşturur. Ancak, aracın öğeleri ya da farklı türdeki öğeleri grupları oluşturmak için kod yazabilirsiniz.

**Bağlantı Oluşturucu** ne tür öğelerin aracı bağlanabilir ve ilişkiler oluşturur aralarında tanımlayan bir bağlantı Oluşturucu başvurduğu bağlantısı aracı özelliği. Bağlantı oluşturucular DSL Gezgini'ndeki düğümler olarak tanımlanır. Bağlantı Oluşturucular, etki alanı ilişkileri tanımlamak, ancak bunları özelleştirmek için kod yazabilirsiniz otomatik olarak oluşturulur.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Araç kutusuna bir aracı eklemek için

1.  Bir şeklin sınıfını oluşturup bir etki alanı sınıfı için eşlenmiş sonra genellikle bir öğe aracı oluşturun.

     Bağlayıcı sınıfı oluşturup bir başvuru ilişkisi için eşlenmiş sonra genellikle bir bağlayıcı aracını oluşturun.

2.  DSL Gezgini'nde **Düzenleyicisi** düğüm ve **araç kutusu sekmeleri** düğümü.

     Araç kutusu sekmesi düğümüne sağ tıklayın ve ardından **yeni öğe aracı ekleme** veya **ekleme yeni bağlantı aracını**.

3.  Ayarlama **araç kutusu simgesi** 16 x 16 bit eşleme başvurmak için özellik.

     Rapordaki yeni simge tanımlamak istiyorsanız, Çözüm Gezgini içindeki bir bit eşlem dosyası oluştur **Dsl\Resources** klasör. Dosyada, aşağıdaki özellik değerlerini olmalıdır: **derleme eylemi** = **içerik**; **Çıkış dizinine Kopyala** = **kopyalamayın**.

4.  **Bir öğe aracı:** ayarlayın **sınıfı** bir şekli için eşlenmiş bir somut bir alan sınıfına başvurmak için aracı özelliği.

     **Bağlayıcı aracı:** ayarlamak **bağlantı Oluşturucu** aşağı açılan listede sunulur öğelerinden biri için aracının özelliği. Bir bağlayıcı için bir etki alanı ilişkisi eşlediğinizde bağlantı oluşturucular otomatik olarak oluşturulur. Yakın zamanda bağlayıcıyı oluşturduysanız, normalde ilişkili bağlantı oluşturucunun seçersiniz.

5.  DSL test etmek için F5'e ya da CTRL + F5 tuşuna basın ve bir örnek model dosyasını Visual Studio'nun deneysel örneğinde açın. Yeni aracı araç kutusunda görünmesi gerekir. Yeni bir öğe oluşturur doğrulamak için diyagram üzerine sürükleyin.

     Aracı görünmüyorsa, Deneysel bir Visual Studio durdurun. Windows içinde **Başlat** menüsü çalıştırma **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlama**. Üzerinde **derleme** menüsünde tıklatın **çözümü yeniden derle**. DSL yeniden sınayın.

## <a name="customizing"></a> Öğe araçlarını özelleştirme
 Varsayılan olarak, aracı belirtilen sınıf tek bir örneğini oluşturur, ancak bu iki yolla değişebilir:

-   Öğe birleştirme yönergeleri Bu sınıfın yeni örneklerini kabul etmelerine izin etkinleştirme ve bunları yeni bir öğe oluşturulduğunda ek bağlantılar oluşturmak etkinleştirmek diğer sınıflarında tanımlayın. Örneğin, kullanıcının başka bir öğenin üzerine yorum bırakın izin verin ve böylece ikisi arasında bir referans bağlantı oluşturun.

     Kullanıcı yapıştırabilir veya sürüklediğinde ve bir öğeyi aşağı doğru ne olur, bu özelleştirmeler de etkiler.

     Daha fazla bilgi için [özelleştirme öğe oluşturma ve hareketini](../modeling/customizing-element-creation-and-movement.md).

-   Öğelerin gruplar oluşturabilmesi aracı özelleştirmek için kod yazın. Araç, geçersiz kılabilirsiniz ToolboxHelper.cs yöntemleri tarafından başlatılır. Daha fazla bilgi için [oluşturma grupları öğeleri aracından](#groups).

## <a name="groups"></a> Bir aracından öğelerin grupları oluşturma
 Her öğe araç oluşturması gereken öğelerin bir prototip içeriyor. Varsayılan olarak, her öğe aracı, tek bir öğe oluşturur, ancak bir aracı ile ilgili nesneler bir grup oluşturmak mümkündür. Bunu yapmak için aracı ile başlatılamıyor. bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> , ilgili öğeleri içerir.

 Aşağıdaki örnek, bir tür transistör olduğu DSL'de alınır. Her transistör üç adlandırılmış terminaller sahiptir. Öğe araç transistörler için dört model öğelerini ve üç ilişki bağlantılarını içeren bir prototip depolar. Kullanıcı araç diyagram üzerine sürüklediğinde, prototip örneği ve model köküne bağlanır.

 Bu kod içinde tanımlanan yöntem geçersiz **Dsl\GeneratedCode\ToolboxHelper.cs**.

 Program kodu kullanarak model özelleştirme hakkında daha fazla bilgi için bkz. [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }
```

## <a name="connections"></a> Bağlantı araçlarını özelleştirme
 Genellikle, yeni bir bağlayıcı sınıfı oluşturduğunuzda, bir öğe aracı oluşturun. Alternatif olarak, bir aracı ilişki türünü belirlemek için iki ucu türleri sağlayarak aşırı yüklenebilir. Örneğin, kişi yüze ilişkileri hem kişi belediye ilişkileri oluşturabilir bir bağlantı aracını tanımlayabilirsiniz.

 Bağlantı Araçları bağlantı oluşturucular çağırın. Bağlantı oluşturucular kullanıcılar oluşturulan tasarımcıda öğeleri nasıl bağlayabilirsiniz belirtmek için kullanın. Bağlantı oluşturucular bağlanabilir öğelerin ve bunlar arasında oluşturulan bağlantı türünü belirtin.

 Bir alan sınıfları arasındaki başvuru ilişkisi oluşturduğunuzda, bir bağlantı Oluşturucu otomatik olarak oluşturulur. Bağlantı aracını eşleştirdiğinizde, bu bağlantı Oluşturucu kullanabilirsiniz. Bağlantı Araçlar oluşturma hakkında daha fazla bilgi için bkz. [araç kutusunu yapılandırma](../modeling/customizing-tools-and-the-toolbox.md).

 Farklı bir kaynak ve hedef türleri aralığı ile Dağıt ve farklı türde ilişki oluşturmak için varsayılan bağlantı Oluşturucusu değiştirebilirsiniz.

 Bağlantı için kaynak ve hedef sınıflarını belirtin, duruma bir bağlantı türü tanımlama ve bağlantısının oluşturulması ile ilgili diğer eylemleri bağlantı oluşturucular için özel kod da yazabilirsiniz.

### <a name="the-structure-of-connection-builders"></a>Bağlantı oluşturucular yapısı
 Bir bağlantı oluşturucular içeren veya daha fazla bağlantı bağlama, etki alanı ilişkisi ve kaynak ve hedef öğeleri belirten yönergeleri. Örneğin, Görev akışı çözüm şablonunda, gördüğünüz **CommentReferencesSubjectsBuilder** içinde **DSL Gezgini**. Bu bağlantı Oluşturucu bir bağlantı içeren bağlanma yönergesi adlı **CommentReferencesSubjects**, etki alanı ilişkisine eşlenen **CommentReferencesSubjects**. Bu bağlantı bağlama yönergesi içeren işaret eden kaynak rolü yönergesi `Comment` etki alanı sınıfı ve işaret eden hedef rol yönergesi `FlowElement` etki alanı sınıfı.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Kaynak kısıtlamak için bağlantı oluşturucular kullanarak ve hedef rolleri
 Bağlantı Oluşturucular, belirli sınıfların Kaynak rolü veya belirtilen etki alanı ilişkinin hedef rolü örneğini kısıtlamak için kullanabilirsiniz. Örneğin, bir etki alanı ilişkisine başka bir alan sınıfına temel alan sınıfı olabilir, ancak bu ilişkide aynı rollerini sağlamak için temel sınıfın tüm türetilmiş sınıfları istemeyebilir. Görev akışı çözümde dört somut bir etki alanı sınıfı vardır (**StartPoint**, **uç nokta**, **MergeBranch**, ve **eşitleme**) doğrudan soyut alan sınıfından devralan **FlowElement**, ve iki etki alanı sınıflar somut (**görev** ve **ObjectInState**), dolaylı olarak bu türden devralmalıdır. Ayrıca bir **akış** başvuru alan ilişkisi **FlowElement** alan sınıfları, Kaynak rolü ve hedef rolü. Ancak, örneği bir **uç nokta** etki alanı sınıfı, örneği kaynağını olmamalıdır bir **akış** ilişki, ya da örneği gerekir bir **StartPoint** sınıfı hedef örneği bir **akış** ilişki. **FlowBuilder** bağlantı Oluşturucu adlı yönergesi bağlanın bağlantısı vardır **akış** hangi etki alanı sınıfları kaynak rol oynayabilir belirtir (**görev**,  **MergeBranch**, **StartPoint**, ve **eşitleme**) ve hedef rolü çalabilir (**MergeBranch**,  **Uç nokta**, ve **eşitleme**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Bağlantı oluşturucular ile birden çok bağlantı bağlama yönergeleri
 Birden fazla bağlantı ekleyebileceğiniz bir bağlantı oluşturucuya bağlanma yönergesi. Bu, bazı kullanıcıların etki alanı modeli karmaşıklığını gizler ve tutun yardımcı olabilir **araç kutusu** çok dolmasını öğesinden. Bağlantı ekleyebilirsiniz bağlama için tek bir bağlantı Oluşturucu birkaç farklı bir etki alanı ilişkileri yönergeleri. Ancak, bunlar yaklaşık aynı işlevi gerçekleştirir, etki alanı ilişkileri birleştirmemelisiniz.

 Görev akışı çözümünde **akış** hem örneklerini çizmek için kullanılan bağlantı aracını **akış** ve **NesneAkış** etki alanı ilişkileri. **FlowBuilder** bağlantı Oluşturucusu vardır, ayrıca için **akış** bağlantı bağlama yönergesi daha önce açıklanan, iki bağlantı bağlama yönergeleri adlı **NesneAkış**. Bu yönergeler, belirten bir örneğini bir **NesneAkış** ilişki örnekleri arasında çizilmiş **ObjectInState** etki alanı sınıfı, veya örneğinden bir **ObjectInState**  örneğine bir **görev**, iki örneği arasında değil bir **görev**, veya örneğinden bir **görev** bir örneğine**ObjectInState**. Ancak, örneği bir **akış** ilişki iki örnekleri arasında çizilmiş bir **görev**. Derleme ve Görev akışı çözümü çalıştırın, bu çizim gördüğünüz bir **akış** örneğinden bir **ObjectInState** örneğine bir **görev** örneği oluşturur bir **NesneAkış**, ancak çizim bir **akış** iki örnekleri arasında bir **görev** örneği oluşturur bir **akış**.

### <a name="custom-code-for-connection-builders"></a>Bağlantı oluşturucular için özel kod
 Bağlantı oluşturucular özelleştirmesini farklı türlerini tanımlamak dört onay kutuları kullanıcı arabiriminde bulunur:

- **özel kabul** bir kaynak veya hedef rol yönergesi onay kutusu

- **özel bağlanma** bir kaynak veya hedef rol yönergesi onay kutusu

- **özel bağlantı kullanan** onay kutusunu bağlanma yönergesi

- **olan özel** bağlantı oluşturucunun özelliği

  Bu özelleştirmeler için bazı program kodu sağlamanıza gerek. Hangi kod sağlamanız gerekir bulmak için bu kutularından birini işaretleyin, tüm Şablonları Dönüştür'e tıklayın ve ardından çözümünüzü oluşturun. Bir hata raporu neden olur. Eklemeniz gerekir, hangi kod anlatan bir açıklama görmek için hata raporuna çift tıklayın.

> [!NOTE]
>  Özel kod eklemek için bir parçalı sınıf tanımı bir kod dosyasında GeneratedCode klasörlerdeki kod dosyalarından ayrı oluşturun. İş kaybını önlemek için oluşturulan kod dosyaları düzenleme yapmamanız gerekir. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Özel bağlantı kod oluşturma
 Her bir bağlantısını bağlanma yönergesi, **Kaynak rolü yönergeleri** sekmesini tanımlayan gelen ne türleri sürükleyebilirsiniz. Benzer şekilde, **hedef rolü yönergeleri** için sekmesinde tanımlar, türleri sürükleyebilirsiniz. Her türü için daha fazla ayarlayarak bağlantı için (Bu bağlantı bağlama yönergesi) izin verip vermeyeceğinizi belirtebilirsiniz **özel kabul** bayrak ve ardından ek bir kod sağlama.

 Bağlantı kurulduğunda ne olacağını özelleştirebilirsiniz. Sürükleme nerede oluştuğunu için veya belirli bir sınıfın durum, özelleştirebileceğiniz tüm durumlarda, bir bağlantı bağlama yönergesi yönetir, ya da tüm FlowBuilder bağlantı Oluşturucu. Bu seçeneklerin her biri için uygun düzeyde özel bayraklar ayarlayabilirsiniz. Tüm Şablonları Dönüştür ve çözüm oluşturmayı denerseniz, hata iletileri, üretilen kodda olan açıklamaları yönlendirin. Bu açıklamalar sağlamanız gerekir belirleyin.

 Bileşenleri diyagramı Bu örnekte, bağlantı noktaları arasında yapılan bağlantıları kısıtlamak için bağlantı alan ilişkisine yönelik bağlantı oluşturucunun özelleştirilir. Yalnızca gelen bağlantıları yapabileceğiniz aşağıda gösterilmiştir `OutPort` öğelerine `InPort` öğeleri, ancak bileşenler arasındaki ilişki içinde içe kullanabilirsiniz.

 **İç içe geçmiş bileşen bir OutPort için gelen bağlantı**

 ![Bağlantı oluşturucu](../modeling/media/connectionbuilder_3.png)

 Bu nedenle, bir bağlantı için bir OutPort iç içe geçmiş bileşen gelebilir belirlemenizi isteyebilirsiniz. Bu tür bir bağlantı belirtmek için ayarladığınız **kullanan özel kabul** üzerinde **InPort** kaynağı rol türü ve **OutPort** türü hedef rolü olarak **DSL ayrıntıları**  aşağıdaki resimlerde gösterildiği penceresi:

 **Bağlantı bağlama yönergesi, DSL Gezgini**

 ![Bağlantı oluşturucu resmi](../modeling/media/connectionbuilder_4a.png)

 **Bağlantı bağlama yönergesi DSL Ayrıntıları penceresinde**

 ![](../modeling/media/connectionbuilder_4b.png)

 Ardından ConnectionBuilder sınıftaki yöntemlerin sağlamanız gerekir:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Program kodu kullanarak model özelleştirme hakkında daha fazla bilgi için bkz. [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Örneğin, kullanıcılar üst-alt bağlantıları döngüler oluşturmasını önlemek için benzer bir kod kullanabilirsiniz. Kullanıcılar herhangi bir zamanda bunları ihlal olamaz çünkü bu kısıtlamalar 'sabit' kısıtlamaları olarak kabul edilir. Ayrıca kullanıcılar, geçici olarak kaydedilemiyor geçersiz yapılandırmaları oluşturarak atlayabilirsiniz 'soft' doğrulama denetimleri oluşturabilirsiniz.

### <a name="good-practice-in-defining-connection-builders"></a>İyi bir uygulama bağlantı oluşturucular tanımlama
 Yalnızca kavramsal olarak ilişkili oldukları, farklı türlerde ilişkiler oluşturmak için bir bağlantı Oluşturucu tanımlamanız gerekir. Görev akışı örnek görevler arasında ve ayrıca görev nesneler arasında bir akış oluşturmak için aynı Oluşturucusu'nu kullanın. Ancak, açıklamalar ve görevler arasında ilişkiler oluşturmak için aynı Oluşturucusu'nu kullanmak kafa karıştırıcı olacaktır.

 Birden çok türde ilişki için bir bağlantı Oluşturucu tanımlarsanız, birden fazla kaynak ve hedef nesnelerin aynı çifti türünden eşleşemez emin olmalısınız. Aksi takdirde, sonuçlar tahmin edilemez olacaktır.

 'Hard' kısıtlamaları uygulamak için özel kod kullanın, ancak kullanıcıların geçici olarak geçersiz bağlantılar oluşturmak mümkün olup olmayacağını göz önünde bulundurmanız gerekir. Bunlar gerekir, böylece kullanıcılar değişiklikleri kaydetmeyi deneyin kadar bağlantıları doğrulanmaz kısıtlamaları değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.

- [Öğe Oluşturma ve Hareketini Özelleştirme](../modeling/customizing-element-creation-and-movement.md)
- [Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Bağlantı hattı diyagramları örneği DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)