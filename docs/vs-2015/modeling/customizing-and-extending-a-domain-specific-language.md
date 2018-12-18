---
title: Bir etki alanına özgü dili özelleştirme ve genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3d5b55a9b9a55d00cbfb7928295699c254f72639
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180693"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Etki Alanına Özgü Dili Özelleştirme ve Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio modelleme ve görselleştirme SDK'sı (VMSDK) modelleme araçları tanımlamak birden fazla düzeyleri sağlar:  
  
1.  DSL tanım diyagramı kullanarak bir etki alanına özgü dil (DSL) tanımlayın. Bir DSL, bir grafiksel gösterimi, okunabilir XML form ve kodu ve diğer yapıları üretmek için gerekli olan temel araçları ile hızlı bir şekilde oluşturabilirsiniz.  
  
     Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  DSL DSL tanımının daha gelişmiş özelliklerini kullanarak hassas ayarlamalar yapabilirsiniz. Örneğin, ek bağlantılar kullanıcı bir öğe oluşturduğunda görünür yapabilirsiniz. Bu teknikler genellikle DSL tanımındaki elde edilir ve bazı program kodu birkaç satır gerektirir.  
  
3.  Program kodunu kullanarak, modelleme araçları genişletir. VMSDK uzantılarınızı DSL tanımını oluşturan kod ile tümleştirmeyi kolaylaştırmak için tasarlanmıştır.  Daha fazla bilgi için [bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  DSL tanımlarına dosya güncelleştirildiğinde tıklamayı değil **tüm Şablonları Dönüştür** çözümünüzü yeniden oluşturmayı önce Çözüm Gezgini araç çubuğundaki.  
  
##  <a name="customShapes"></a> Bu bölümde  
  
|Bu etkiyi elde etmek için|Bu konuya bakın|  
|----------------------------|-------------------------|  
|Şeklin rengi ve stil özelliklerini ayarlama izin verin.|Şekil veya bağlayıcının sınıfı sağ tıklatın, **ekleme kullanıma sunulan**ve bir öğeye tıklayın.<br /><br /> Bkz: [diyagramda sunuyu özelleştirme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Model öğesinin farklı sınıflar diyagramda ilk yükseklik ve genişlik, renk, araç ipuçları gibi özellikleri paylaşımı benzer.|Şekilleri veya bağlayıcı sınıfları arasındaki devralma kullanın. Türetilmiş şekiller ve türetilmiş alan sınıfları arasındaki eşlemeleri üst eşleme ayrıntılarını alır.<br /><br /> Ya da farklı bir etki alanı sınıfları aynı şekli sınıfa eşleme.|  
|Model öğesinin bir sınıf tarafından bağlamları farklı şekiller görüntülenir.|Birden fazla şekil sınıfı için aynı etki alanı sınıfı eşleyin. Çözüm derlediğinizde, hata raporu izleyin ve kullanmak için nasıl bir şekil karar vermek için istenen kod sağlar.|  
|Şekil rengine veya yazı tipi gibi diğer özellikleri geçerli durumunu gösterir.|Bkz: [modeli yansıtacak şekilleri ve bağlayıcıları güncelleştirme](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Sunulan özellikler güncelleştiren bir kural oluşturun. Bkz: [değişiklikleri modelin içinde yayan kurallar](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Dilerseniz OnAssociatedPropertyChanged() bağlantı oklar veya yazı tipi gibi açık olmayan özellikleri güncelleştirmek için kullanın.|  
|Simge durumu göstermek için şekli değişir.|DSL Ayrıntıları penceresinde dekoratör eşlemesi görünürlüğünü ayarlayabilirsiniz. Aynı konumda birden fazla görüntü dekoratörleri bulun. Bkz: [modeli yansıtacak şekilleri ve bağlayıcıları güncelleştirme](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Veya geçersiz kılma `ImageField.GetDisplayImage()`. Örnekte bakın <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Herhangi bir şekli bir arka plan görüntüsü ayarlama|Bağlantılı bir ImageField eklemek için InitializeInstanceResources() geçersiz kılar. Bkz: [diyagramda sunuyu özelleştirme](../modeling/customizing-presentation-on-the-diagram.md).|  
|İç içe şekillere herhangi derinliği|Özyinelemeli bir ağaç katıştırma ayarlayın. BoundsRules şekil içerecek şekilde tanımlar. Bkz: [diyagramda sunuyu özelleştirme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Bir öğenin sınırında sabit noktalarda bağlayıcıları ekleyin.|Küçük bağlantı noktalarına diyagram tarafından temsil edilen katıştırılmış terminal öğelerini tanımlayın. BoundsRules yerinde bağlantı noktaları düzeltmek için kullanın. Bağlantı hattı diyagramı örneğine bakın [Görselleştirme ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Metin alanı, diğer değerlerden türetilmiş bir değer görüntüler.|Metin dekoratör bir hesaplanmış ya da özel depolama etki alanı özelliğine eşleyin. Daha fazla bilgi için [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).|  
|Şekil veya model öğeleri arasında değişiklikleri yayma|Bkz: [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).|  
|Kaynakları gibi diğer değişiklikleri yaymak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deponun dışında uzantıları.|Bkz: [değişiklikleri modelin dışına yayan olay işleyicileri](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Özellik penceresi ilgili öğenin özelliklerini görüntüler.|İletme özelliği ayarlayın. Bkz: [Özellikler penceresini özelleştirme](../modeling/customizing-the-properties-window.md).|  
|Özellik kategorisi|Özellikler penceresinde kategorileri adlı bölümlere ayrılmıştır. Ayarlama **kategori** , etki alanı özelliklerinin özellikleri. Aynı kategori adlı özellikler aynı bölümde görünecektir. Ayrıca **kategori** ilişki rolü.|  
|Kullanıcı erişimini denetlemek için etki alanı özellikleri|Ayarlama **olan gözatılabilir** bir alan özelliği, Özellikler penceresinde çalışma zamanında görünmesini engellemek için false. Yine de metin dekoratörleri için eşleyebilirsiniz.<br /><br /> **Salt okunur kullanıcı Arabirimi** kullanıcıların bir alan özelliği değiştirmesini engeller.<br /><br /> Etki alanı özelliği program erişimi etkilenmez.|  
|Ad, simge ve DSL'NİZİN model Gezgini'nde düğümler görünürlüğünü değiştirin.|Bkz: [Model Gezginini özelleştirme](../modeling/customizing-the-model-explorer.md).|  
|Kopyala, Kes ve Yapıştır etkinleştir|Ayarlama **etkinleştirme Kopyala Yapıştır** özelliği **Düzenleyicisi** DSL Gezgininde.|  
|Her bir öğe kopyalanır referans bağlantıları ve hedeflerine kopyalayın. Örneğin, bir iş öğesine ekli açıklamalar kopyalayın.|Ayarlama **yayar kopyalama** (DSL tanım diyagramı, etki alanı ilişkinin bir tarafında çizgiyle gösterilir) kaynak rolünün özelliği.<br /><br /> Daha karmaşık efektler elde etmek için ProcessOnCopy geçersiz kılmak için kod yazın.<br /><br /> Bkz: [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|  
|Silme, yeniden üst öğe yap veya bir öğe silindiğinde ilgili öğeleri yeniden bağlayın.|Ayarlama **yayar Sil** ilişki rolü değeri. Daha karmaşık etkileri için geçersiz kılma `ShouldVisitRelationship` ve `ShouldVisitRolePlayer` yöntemleri `MyDslDeleteClosure` sınıfı içinde tanımlanan **DomainModel.cs**<br /><br /> Bkz: [silme davranışını özelleştirme](../modeling/customizing-deletion-behavior.md)|  
|Şekil düzeninin ve görünümünün kopyalama ve sürükle-bırak korur.|Şekilleri ve bağlayıcıları kopyalanan ekleme `ElementGroupPrototype`. Geçersiz kılmak için en uygun yöntemi `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Bkz: [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|  
|Şekiller geçerli imleç konumu gibi seçtiğiniz bir konuma yapıştırın.|Geçersiz kılma `ClipboardCommandSet.ProcessOnCopy()` konuma özgü sürümünü kullanacak şekilde `ElementOperations.Merge().` bkz [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|  
|Yapıştırırken ek bağlantılar oluşturma|Override ClipboardCommandSet.ProcessOnPasteCommand()|  
|Sürükle ve bırak Bu diyagram ile başka bir DSL veya UML etkinleştirmek diyagramları ve Windows öğeleri|Bkz: [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Üst sürüklediğiniz gibi bir şekil veya bir bağlantı noktası gibi bir alt Şekil'üzerine sürüklenerek aracı sağlar.|Öğe birleştirme yönergesinde, bırakılan nesne üst iletmek için hedef nesne sınıfı üzerinde tanımlayın. Bkz: [öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md).|  
|Bir şekil veya ek bağlantılar ve şeklin üzerine sürüklenerek aracını izin verin veya oluşturulan nesneler. Örneğin, bir yorum, bağlı durumda olan bir öğe kesilmesine izin vermek için.|Öğe birleştirme yönergesinde hedef etki alanı sınıfını tanımlamak ve oluşturulacak bağlantılara tanımlayın. Karmaşık durumlarda, özel kod ekleyebilirsiniz. Bkz: [öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md).|  
|Bir aracıyla öğeleri bir grup oluşturun. Örneğin, sabit bir dizi bağlantı noktası ile bir bileşen.|ToolboxHelper.cs araç kutusu başlatma yöntemi yok sayın. Bir öğe grubu prototip (öğeleri ve bunların ilişki bağlantılarını içeren EGP) oluşturun. Bkz: [araçları ve araç kutusunu özelleştirme](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Asıl ve bağlantı noktası şekiller EGP içeriyor ya da bağlantı noktası şekilleri EGP örneği oluşturulduğunda konumlandırmak için BoundsRules tanımlayın. Bkz: [BoundsRules şekil konumunu ve boyutunu Kısıtlamama](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Birden fazla ilişki oluşturmak için bir bağlantı aracını kullanın.|Bağlantı bağlama yönergesi (LCD) araç tarafından çağrılan bağlantı oluşturucuyu ekleyin. LCD'ler iki öğe türleri arasında ilişki türünü belirler. Bu öğelerin durumlarını bağımlı hale getirmek için özel kod ekleyebilirsiniz. Bkz: [araçları ve araç kutusunu özelleştirme](../modeling/customizing-tools-and-the-toolbox.md).|  
|Yapışkan araçları – kullanıcı, çok sayıda şekilleri veya bağlayıcıları art arda oluşturmak için herhangi bir aracı çift tıklayabilirsiniz.|DSL Gezgini içinde seçin `Editor` düğümü. Özellikler penceresinde ayarlayın **kullanan Yapışkan araç kutusu öğeleri**.|  
|Menü komutlarını tanımlama|Bkz: [nasıl yapılır: standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Model doğrulama kuralları ile sınırlama|Bkz: [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md)|  
|Bir DSL kod, yapılandırma dosyaları ve belgeleri oluşturur.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Modelleri nasıl kaydedileceğini özelleştirme dosyası için.|Bkz: [dosya depolamayı ve XML serileştirmeyi özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Modelleri, veritabanları veya diğer ortam kaydedin.|Geçersiz kılma *YourLanguage*DocData<br /><br /> Bkz: [dosya depolamayı ve XML serileştirmeyi özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Bir uygulamanın bir parçası çalışmaları için birden çok DSL tümleştirin.|Bkz: [Visual Studio Modelbus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|DSL'nizi üçüncü taraflarca genişletilmesi izin ve uzantı denetleyin.|[MEF kullanarak DSL'nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md)   
 [Bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)



