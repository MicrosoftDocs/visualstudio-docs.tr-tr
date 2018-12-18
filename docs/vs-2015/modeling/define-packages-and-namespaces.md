---
title: Paketleri ve ad alanlarını tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b9295b5af83270069df11e6460ee85dfe0fd9c73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741903"
---
# <a name="define-packages-and-namespaces"></a>Paketleri ve ad alanlarını tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da bir *paket* UML öğelerini sınıfları, kullanım örnekleri ve bileşenleri gibi tanımları için bir kapsayıcıdır. Bir paket diğer paketleri de içerebilir.  
  
 UML Model Gezgini'nde bir paket içindeki tüm tanımları paketin altında iç içe geçirilmiştir. UML modeli paket türüdür ve ağacının kökü oluşturur.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>Bu Konu kapsamında  
 [Ad Alanları](#Namespaces)  
  
 [Paketleri oluşturma ve görüntüleme](#Packages)  
  
 [Model öğelerini paketleri içinde oluşturma](#Elements)  
  
 [İçine veya dışına bir paket öğeleri taşıma](#Moving)  
  
 [Öğe pakete yapıştırma](#Pasting)  
  
 [Paketleri arasındaki ilişkileri içeri aktarma](#Import)  
  
 [Bir Namespace gelen başvuruları](#References)  
  
 [Paket Özellikleri](#Properties)  
  
##  <a name="Namespaces"></a> Ad alanları  
 Paketler halinde farklı alanları ayırmak için kullanışlıdır. Her paket farklı paketlerde tanımlanan adları birbiriyle çakışmadığından bir ad alanı tanımlar.  
  
 Her öğenin tam adı, öğenin kendi adından önce gelen ait olduğu paket tam adı özelliğidir. Örneğin, paketinizin çağrılırsa `MyPackage`, bir sınıf içinde paket tam adı gibi olacaktır `MyPackage::MyClass`. Her öğe bir model içinde bulunduğundan, her tam adı modelin adı ile başlar.  
  
 Modeldeki her bir öğenin tam adı modelin adını başlayabilmesi için bir model, ayrıca bir ad alanı tanımlar.  
  
 Diğer model öğeleri de ad alanlarını tanımlar. Tam adı gibi böylece Örneğin, bir işlem kendi üst sınıfı tarafından tanımlanan ad alanı ait `MyModel ::MyPackage ::MyClass ::MyOperation`. Aynı şekilde, kendi üst etkinliği tarafından tanımlanan ad alanı için bir eylem aittir.  
  
 Paketleri kapsayıcılardır. Taşıma veya bir paketi silmek, sınıflar, paketleri ve içinde tanımlanan başka şeyler de taşınmış veya. Aynı ad alanlarını tanımlayan diğer öğeleri de geçerlidir.  
  
##  <a name="Packages"></a> Paketleri oluşturma ve görüntüleme  
 Bir UML sınıf diyagramında veya UML Model Gezgini'nde bir paket oluşturabilirsiniz.  
  
#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Bir UML sınıf diyagramında bir paketi oluşturmak için  
  
1.  Bir UML sınıf diyagramı açın veya yeni bir tane oluşturun.  
  
2.  Tıklayın **paket** aracı.  
  
3.  Diyagram üzerinde herhangi bir yere tıklayın. Yeni bir paket şekli görünür.  
  
     Başka bir paket içine yerleştirmek için var olan bir paket içinde tıklayabilirsiniz.  
  
4.  Paket için yeni bir ad yazın.  
  
#### <a name="to-create-a-package-in-uml-model-explorer"></a>UML Model Gezgini'nde bir paketi oluşturmak için  
  
1. Açık **UML Model Gezgini**. Üzerinde **mimarisi** menüsünde **Windows**ve ardından **UML Model Gezgini**.  
  
2. Yeni bir paket eklemek istediğiniz bir modeli veya bir pakete sağ tıklayın.  
  
   > [!NOTE]
   >  Bir paketi başka bir paket içinde iç içe yerleştirebilirsiniz.  
  
3. İşaret **Ekle** ve ardından **paket**.  
  
    Modelde yeni bir paket görünür.  
  
4. Paket için yeni bir ad yazın.  
  
   UML Model Gezgini'nde bir paketi oluşturduysanız, bir UML sınıf diyagramında görüntüleyebilirsiniz. Ayrıca, bir paket birden fazla UML sınıf diyagramında görüntüleyebilirsiniz.  
  
#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Bir UML sınıf diyagramı üzerinde varolan paketi göstermek için  
  
-   Paket, UML Model Gezgini'nden sınıf diyagramına sürükleyebilir sürükleyin.  
  
    > [!NOTE]
    >  Bu, bu diyagramda paket bir görünümünü oluşturur. Bu mutlaka tüm öğeleri paketin içerdiği göstermez. Bir paketin içeriğinin tamamını gördüğünüzden emin olmak için UML Model Gezgini'nde görüntüleyin.  
  
##  <a name="Elements"></a> Model öğelerini paketleri içinde oluşturma  
 Bir paket içinde model öğeleri yerleştirmek dört yolu vardır:  
  
- UML Model Gezgini'nde bir pakete yeni bir öğe ekleyin.  
  
- Sınıfları ve diğer türleri UML sınıf diyagramında paketleri ekleyin.  
  
- Ayarlama **LinkedPackage** diyagramın özelliğini yeni öğeler diyagram üzerinde oluşturulan yerleştirilir belirttiğiniz paketin. Sınıf diyagramları, Bileşen diyagramları ve kullanım örneği diyagramları bu şekilde bir pakete bağlanabilir.  
  
- İçine veya dışına UML Model Gezgini'nde bir paket öğeleri Taşı.  
  
  UML Model Gezgini'nde paket altında bir paket içindeki bir öğenin görünür ve tam adı, paket tam adı ile başlar. Herhangi bir öğenin tam adı görmek için öğeye sağ tıklayın ve ardından **özellikleri**. **Tam adı** özellik görünür **özellikleri** penceresi.  
  
#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>UML Model Gezgini'nde bir paket içinde bir öğe oluşturmak için  
  
1.  Açık **UML Model Gezgini**. Üzerinde **görünümü** menüsünde **diğer Windows**ve ardından **UML Model Gezgini**.  
  
2.  Yeni bir öğe eklemek istediğiniz bir modeli veya bir pakete sağ tıklayın.  
  
3.  İşaret **Ekle**ve ardından eklemek istediğiniz öğe türünü tıklayın.  
  
     Yeni öğe paketin altında görünür.  
  
4.  Yeni öğe için bir ad yazın.  
  
    > [!NOTE]
    >  Yeni öğe herhangi bir diyagram üzerinde görünmez. Yeni öğe görünümü oluşturmak için bunu UML Model Gezgini'nden bir diyagram üzerine sürükleyebilirsiniz. Diyagram, bu tür bir öğe görüntüleyen bir türü olmalıdır.  
  
#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Bir UML sınıf diyagramında bir paket içinde bir öğe oluşturmak için  
  
1.  Paket görünen bir sınıf diyagramı açın.  
  
    -   Zaten bunu yapmadıysanız, yeni bir paket oluşturun.  
  
    -   Var olan paketi bir sınıf diyagramı üzerinde görünmesini sağlamak için paket sürükleyebilirsiniz **UML Model Gezgini** sınıf diyagramına sürükleyebilirsiniz.  
  
2.  Sınıf, arabirim veya numaralandırma veya paket için Aracı'nı tıklatın.  
  
3.  Yeni öğe koymak istediğiniz pakete tıklayınız.  
  
     Paketin içinde yeni bir öğe görünür.  
  
#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Belirtilen bir paketteki tüm öğelerinin bir diyagram oluşturmak için  
  
1.  Zaten bu yapmadıysanız paketi oluşturun.  
  
2.  Bir bileşen diyagramı, kullanım durumu diyagramı veya UML sınıf diyagramı açın.  
  
3.  Diyagram özelliklerini açın. Diyagramın boş bir bölümüne sağ tıklayın ve ardından **özellikleri**.  
  
4.  İçinde **bağlantılı paket** özelliği, diyagramın içeriğini içermesini istediğiniz paketi seçin.  
  
5.  Yeni öğeler diyagramda oluşturun. Bu pakete yerleştirilecek.  
  
    -   **Tam adı** her öğeye paketin tam adı ile başlar.  
  
    -   İçinde **UML Model Gezgini**, her öğe paketinin altında görünür.  
  
##  <a name="Moving"></a> İçine ve dışına paketleri öğeleri taşıma  
 Bir veya daha fazla öğe içinde veya dışında bir paket taşıyabilirsiniz.  
  
 Bir paket taşırsanız, içindeki her şeyi birlikte taşınır.  
  
#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Bir öğenin içine veya dışına bir paket taşımak için  
  
-   UML Model Gezgini'nde öğenin içine veya dışına, kök paketi ağacına sürükleyin.  
  
     Öğenin tam adı, sahip olan yeni bir paket veya model gösterecek şekilde değişir.  
  
     \- veya -  
  
-   Bir sınıf diyagramında paket şekle öğeyi sürükleyin.  
  
     Öğenin tam adı, yeni bir sahip olan paket göstermek için değiştirir.  
  
    > [!NOTE]
    >  Diyagramın boş bir kısmına bir paket dışında bir öğeyi sürüklediğinizde, onun sahibi olan paket değiştirmez. Bu paketleri göstermek zorunda kalmadan birkaç paketten öğeleri gösteren bir diyagram yapmanıza olanak sağlar.  
  
##  <a name="Pasting"></a> Öğe pakete yapıştırma  
 Öğe pakete yapıştırabilirsiniz. İlgili öğeleri bir grup pakete yapıştırabilirsiniz, onlar arasındaki ilişkileri de yapıştırılır.  
  
#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Bir UML sınıf diyagramında bir paket öğeleri yapıştırmak için  
  
1.  Bir UML sınıf diyagramı üzerinde kopyalamak istediğiniz tüm öğeleri seçin. Bunlardan birini sağ tıklayın ve ardından **kopyalama**.  
  
2.  Pakete sağ tıklayın ve ardından **Yapıştır**.  
  
    > [!NOTE]
    >  Paketi farklı bir diyagram üzerinde olabilir.  
  
##  <a name="Import"></a> Paketleri arasındaki ilişkileri içeri aktarma  
 Bir içeri aktarma ilişki kullanarak paketler arasında tanımlayabilirsiniz **alma** aracı.  
  
 İçeri aktarma, ilişkinin ok ucu öğeler olan içeri aktarılan pakette tanımlanmış öğeleri etkili bir şekilde de içeri aktarma pakette tanımlandığından emin anlamına gelir. Görünürlüğü olarak tanımlanmış olan herhangi bir öğe **paket** alma pakette de görünür.  
  
 İçeri aktarma ilişkilerinde döngüler oluşturmaktan kaçının.  
  
##  <a name="References"></a> Bir Namespace gelen başvuruları  
 Başka bir paketin bir öğeye başvurmak istiyorsanız, öğenin tam adı kullanmanız gerekir.  
  
 Örneğin, bu paket varsayalım `SalesCommon` türünü tanımlayan `CustomerAddress`. Başka bir paketteki `RestaurantSales`, bir tür tanımlamak istediğiniz `MealOrder`, müşteri adresi bir türün özniteliği vardır. İki seçeneğiniz vardır:  
  
-   Tam adı kullanılarak öznitelik türü belirtin `SalesCommon::CustomerAddress`. Bu can yalnızca, yapmanız gerekenler `CustomerAddress` sahip kendi **görünürlük** özelliğini **genel**.  
  
-   Bir içeri aktarma ilişkiden oluşturma `RestaurantSales` paketini `SalesCommon` paket. Kullanabileceğiniz sonra `CustomerAddress` tam adı kullanmadan.  
  
##  <a name="Properties"></a> Paket Özellikleri  
 Her paket, aşağıdaki özelliklere sahiptir. Özelliklerini görmek için bir diyagramda veya UML Model Gezgini'nde, pakete sağ tıklayın ve ardından **özellikleri**.  
  
|Özellik|Varsayılan değer|Açıklama|  
|--------------|-------------------|-----------------|  
|**Ad**|(yeni ad)|Paket adı. Diyagram üzerinde ya da Özellikler penceresinde değiştirebilirsiniz.|  
|**Tam adı**|*Kapsayıcı* :: *paket adı*|Bu paket içeren model veya paketin adıyla önek tam adı. Daha fazla bilgi için [ad alanları](#Namespaces).|  
|**Profilleri**|(boş)|Bu paketin bağlı profilleri listesi. Bu profiller, paket içindeki öğeler uygulanabilir stereotipler sağlar. Daha fazla bilgi için [modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
|**Görünürlük**|**Public**|Paket üst paketiyle dışında görünürlüğünü.|  
|**İş öğeleri**|(boş)|Bağlantılı iş öğeleri listesi. Daha fazla bilgi için [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|  
|**Tanım konumu**|(ad)|Paket ayrıntılarını depolandığı dosya adı. Dosyalar içinde **ModelDefinition** proje klasörü. Bu bilgiler, kaynak denetimi işlemleri için yararlı olabilir.|  
|**Açıklama**|(boş)|Paket açıklaması.|  
|**Stereotipler**|(boş)|Bu pakete uygulanan stereotip. Kullanılabilir stereotiplerin listesi, bu paket ve onu içeren paketleri için seçtiğiniz profilleri tarafından belirlenir. Daha fazla bilgi için [modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
  
## <a name="how-packages-are-stored"></a>Paketler nasıl depolanır  
 Yeni bir paket oluşturduğunuzda, yeni bir **.uml** dosyasının oluşturulduğunu **ModelDefinition** proje klasörü. Ayrıca bir pakettir, kök modeli de depolanan bir **.uml** dosya.  
  
 Ayrıca, her diyagram iki dosyada, diyagramın şeklini temsil eden bir depolanır ve bir **.layout** şekilleri konumlarını kayıtları dosya.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)   
 [Sürüm denetimi altındaki modelleri ve diyagramları yönetme](../modeling/manage-models-and-diagrams-under-version-control.md)



