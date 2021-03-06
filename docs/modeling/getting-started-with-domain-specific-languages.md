---
title: Etki Alanına Özgü Dillerle Çalışmaya Başlama
description: Visual Studio için Modelleme SDK'sı ile oluşturulan etki alanına özgü dil (DSL) tanımlama ve kullanmayla ilgili temel Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ae488056986afbe35763be1eebb500ff0eab9a8
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602263"
---
# <a name="get-started-with-domain-specific-languages"></a>Alana Özgü Dilleri Kullanmaya Başlama

Bu konuda, Visual Studio için Modelleme SDK'sı ile oluşturulan etki alanına özgü dil (DSL) tanımlama ve kullanma ile ilgili temel Visual Studio.

> [!NOTE]
> Metin Şablonu Dönüştürme SDK'sı ve Visual Studio Modelleme SDK'sı, uygulamanın belirli özelliklerini Visual Studio. Diğer ayrıntılar için bu [blog gönderisi'ne bakın.](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

DSL'leri yeni başladıysanız DSL **Araçları** Laboratuvarı'nın üzerinden çalışmanız önerilir. Bu sitede bulabilirsiniz: [Görselleştirme ve Modelleme SDK'sı](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Domain-Specific Language ile ne Domain-Specific?

Etki alanına özgü dil, genellikle grafiksel olan ve belirli bir amaç için kullanılacak şekilde tasarlanmış bir gösterimidir. Buna karşılık UML gibi diller genel amaçlıdır. DSL'de model öğesinin türlerini ve ilişkilerini ve ekranda nasıl sun olduklarını tanımlayabilirsiniz.

DSL tasarlasanız, bunu bir Visual Studio Integration Extension (VSIX) paketinin parçası olarak dağıtabilirsiniz. Kullanıcılar dsl ile Visual Studio:

![Aile ağacı diyagramı, araç kutusu ve gezgin](../modeling/media/familyt_instance.png)

Bu not, DSL'nin yalnızca bir bölümü. VSIX paketiniz, bu nota ek olarak kullanıcıların modellerini düzenlemelerine ve modellerinden malzeme oluşturmalarına yardımcı olmak için uygulayabilecekleri araçlar içerir.

DSL'lerin temel uygulamalarından biri program kodu, yapılandırma dosyaları ve diğer yapıtlar oluşturmaktır. Özellikle bir ürünün çeşitli çeşitlemelerinin oluşturulacak olduğu büyük projelerde ve ürün hatlarında, DSL'lerden birçok değişken yönü oluşturularak güvenilirlikte büyük bir artış ve gereksinimlere çok hızlı bir yanıt oluşturulabilir.

Bu genel bakışın geri kalanları, etki alanına özgü bir dil oluşturma ve kullanma ile ilgili temel işlemleri Visual Studio.

## <a name="prerequisites"></a>Önkoşullar

DSL tanımlamak için aşağıdaki bileşenleri yüklemiş olması gerekir:

| Bileşen | Bağlantı |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [https://go.microsoft.com/fwlink/?linkid=2166172](../extensibility/visual-studio-sdk.md) |
| Visual Studio için Modelleme SDK'sı | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>DSL Çözümü Oluşturma

Etki alanına özgü yeni bir dil oluşturmak için, Domain-Specific Dil proje şablonunu kullanarak yeni bir Visual Studio çözüm oluştururuz.

1. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Proje'ye **tıklayın.**

2. Proje **türleri altında** Diğer Proje Türleri **düğümünü** genişletin ve Genişletilebilirlik'e **tıklayın.**

3. Öğesini Alana Özgü Dil Tasarımcısı.

     ![DSL Oluştur iletişim kutusu](../modeling/media/create_dsldialog.png)

4. Ad **kutusuna** **FamilyTree yazın.** **Tamam**'a tıklayın.

     Etki **Alanına Özgü Dil Sihirbazı** açılır ve ŞABLON DSL çözümlerinin listesini görüntüler.

     Açıklamayı görmek için her şablona tıklayın,

     Şablonlar yararlı başlangıç noktalarıdır. Bunların her biri, tam bir çalışan DSL sağlar ve bunları, ihtiyaçlarınıza uyacak şekilde düzenleyebilirsiniz. Normalde, oluşturmak istediğinize en yakın şablonu seçersiniz.

5. Bu kılavuz için En Az Dil **şablonunu** seçin.

6. DSL'niz için uygun sihirbaz sayfasına bir dosya adı uzantısı girin. Bu, DSL'nizin örneklerini içeren dosyaların kullanabileceği uzantıdır.

    - Bilgisayarınızda veya DSL'yi yüklemek istediğiniz herhangi bir bilgisayarda herhangi bir uygulamayla ilişkilendirilen bir uzantı seçin. Örneğin, **docx** ve **html dosyaları** kabul edilemez dosya adı uzantıları olabilir.

    - Girdiğiniz uzantı DSL olarak kullanılıyorsa sihirbaz sizi uyaracak. Farklı bir dosya adı uzantısı kullanmayı göz önünde bulundurabilirsiniz. Eski deneysel tasarımcıları temizlemek Visual Studio SDK Deneysel örneğini de sıfırlayabilirsiniz. **Başlat'a** tıklayın, Tüm **Programlar'a** tıklayın, Microsoft Visual Studio  **2010 SDK,** Araçlar'a tıklayın ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın.**

7. Diğer sayfaları incele ve ardından Son'a **tıklayın.**

     İki proje içeren bir çözüm oluşturulur. Dsl ve DslPackage olarak adlandırılmıştır. DslDefinition.dsl adlı bir diyagram dosyası açılır.

    > [!NOTE]
    > İki projedeki klasörlerde gördüğünüz kodun çoğu DslDefinition.dsl'den oluşturulur. Bu nedenle DSL'niz üzerinde yapılan değişikliklerin çoğu bu dosyada yapılır.

Kullanıcı arabirimi artık aşağıdaki resme benzer.

![dsl tasarımcısı](../modeling/media/dsl_designer.png)

Bu çözüm, etki alanına özgü bir dil tanımlar. Daha fazla bilgi için [bkz. Domain-Specific Dil Araçları'Kullanıcı Arabirimi.](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)

## <a name="the-important-parts-of-the-dsl-solution"></a>DSL çözümünün önemli bölümleri

Yeni çözümün aşağıdaki yönlerine dikkat:

- **Dsl\DslDefinition.dsl** Bu, DSL çözümü oluşturmada gördüğünüz dosyadır. Çözümde yer alan kodun neredeyse hepsi bu dosyadan oluşturulur ve DSL tanımında yaptığınız değişikliklerin çoğu burada yapılır. Daha fazla bilgi için, bkz. [Working with the DSL Definition Diagram](../modeling/working-with-the-dsl-definition-diagram.md).

- **Dsl projesi** Bu proje, etki alanına özgü dili tanımlayan kodu içerir.

- **DslPackage projesi** Bu proje, DSL örneklerinin Visual Studio'de açılmasına ve düzenlen Visual Studio.

## <a name="running-the-dsl"></a><a name="Debugging"></a> DSL'i çalıştırma

DSL çözümünü oluşturduktan hemen sonra çalıştırılabilir. Daha sonra DSL tanımını kademeli olarak değiştirebilir ve her değişiklik sonrasında çözümü yeniden çalıştırabilirsiniz.

### <a name="to-experiment-with-the-dsl"></a>DSL ile deneme yapmak için

1. Araç **çubuğunda Tüm Şablonları Dönüştür'e** **Çözüm Gezgini** tıklayın. Bu, DslDefinition.dsl kaynak kodunun çoğunu yeniden oluşturulur.

    > [!NOTE]
    > *DslDefinition.dsl'yi her değiştirişinde,* çözümü **yeniden** oluşturmadan önce Tüm Şablonları Dönüştür'e tıklamalısınız. Bu adımı otomatikleştirin. Daha fazla bilgi için [bkz. How to Automate Transform All Templates](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. **F5 tuşuna** basın veya Hata **Ayıklama menüsünde** Hata Ayıklamayı **Başlat'a tıklayın.**

     DSL, Visual Studio'nin deneysel örneğinde derleme Visual Studio.

     Deneysel bir Visual Studio başlar. Deneysel örnek, ayarlarını kayıt defterinin ayrı bir alt ağacından alır ve burada Visual Studio hata ayıklama amacıyla kaydedilir. Normal örnek Visual Studio kayıtlı uzantılara erişimi yok.

3. deneysel Visual Studio test adlı model dosyasını **Çözüm Gezgini.** 

     \- veya -

     Hata ayıklama projesine sağ tıklayın, Ekle'nin **üzerine gelin ve** ardından Öğe'ye **tıklayın.** Öğe **Ekle iletişim** kutusunda DSL'nizin dosya türünü seçin.

     Model dosyası boş bir diyagram olarak açılır.

     Araç kutusu açılır ve diyagram türüne uygun araçlar görüntülenir.

4. Diyagramda şekiller ve bağlayıcılar oluşturmak için araçları kullanın.

    1. Şekil oluşturmak için Örnek veri Şekil aracı diyagrama sürükleyin.

    2. İki şekli bağlamak için Örnek Bağlayıcı aracına tıklayın, ilk şekle tıklayın ve ardından ikinci şekle tıklayın.

5. Şekilleri değiştirmek için şekillerin etiketlerine tıklayın.

Deneysel Visual Studio aşağıdaki örnekteki gibi olacak:

![Visual Studio'de etki alanına özgü dil örnek Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Modelin İçeriği

DSL örneği olan bir dosyanın içeriğine model adı *ve denir.* Model, model *öğelerini* <em>ve</em> öğeler *arasındaki* bağlantıları içerir. DSL tanımı modelde hangi tür model öğelerinin ve bağlantıların mevcut olduğunu belirtir. Örneğin, Minimum Dil şablonundan oluşturulan bir DSL'de bir model öğesi türü ve bir bağlantı türü vardır.

DSL tanımı, modelin diyagramda nasıl görüntülendiğinden bunu belirtebilirsiniz. Çeşitli şekil ve bağlayıcı stilleri arasında seçim yapabilirsiniz. Bazı şekillerin diğer şekillerin içinde görünmesini belirtebilirsiniz.

Modeli düzenlerken Gezgin görünümünde bir **ağaç** olarak görüntüebilirsiniz. Diyagrama şekiller eklerken model öğeleri de gezginde görünür. Diyagram olmasa bile gezgin kullanılabilir.

Visual Studio 'nun hata ayıklama örneğinde gezgin 'i göremiyorsanız, **Görünüm** menüsünde **diğer pencereler**' in üzerine gelin ve ardından gezgin ' e tıklayın *\<Your Language>* .

### <a name="the-api-of-your-dsl"></a>DSL API 'SI

DSL 'niz, DSL örnekleri olan modelleri okumanızı ve güncelleştirmenizi sağlayan bir API oluşturur. API 'nin bir uygulaması, bir modelden metin dosyaları üretmesidir. Daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Hata ayıklama çözümünde ". tt" uzantılı şablon dosyalarını açın. Bu örneklerde modellerden nasıl metin oluşturabileceğiniz ve DSL 'nizin API 'sini test etmeniz için nasıl izin oluşturabileceğiniz gösterilmektedir. Örneklerden biri, içinde diğeri içinde yazılmıştır [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

Her şablon dosyası altında oluşturduğu dosyadır. Çözüm Gezgini şablon dosyasını genişletin ve oluşturulan dosyayı açın.

Şablon dosyası, modeldeki tüm öğeleri listeleyen kısa bir kod segmenti içerir.

Oluşturulan dosya sonucu içerir.

Bir model dosyasını değiştirdiğinizde, dosyaları yeniden oluşturduktan sonra oluşturulan dosyalarda ilgili değişiklikleri görürsünüz.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Model dosyasını değiştirdikten sonra metin dosyalarını yeniden oluşturmak için

1. Visual Studio 'nun deneysel örneğinde model dosyasını kaydedin.

2. Her. tt dosyasındaki dosya adı parametresinin, denemeleri için kullandığınız model dosyasına başvurduğundan emin olun. . Tt dosyasını kaydedin.

3. **Çözüm Gezgini** araç çubuğundan **Tüm Şablonları Dönüştür** ' e tıklayın.

     \- veya

     Yeniden oluşturmak istediğiniz şablonlara sağ tıklayın ve ardından **özel araç Çalıştır**' a tıklayın.

Bir projeye istediğiniz sayıda metin şablonu dosyası ekleyebilirsiniz. Her şablon bir sonuç dosyası üretir.

> [!NOTE]
> DSL tanımını değiştirdiğinizde örnek metin şablonu kodu, güncelleştirmediğiniz takdirde çalışmaz.

Daha fazla bilgi için bkz. [Domain-Specific dilden kod üretme](../modeling/generating-code-from-a-domain-specific-language.md) ve [bir Domain-Specific dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>DSL 'yi özelleştirme

DSL tanımını değiştirmek istediğinizde, deneysel örneği kapatın ve ana Visual Studio örneğindeki tanımı güncelleştirin.

> [!NOTE]
> DSL tanımını değiştirdikten sonra, önceki sürümleri kullanarak oluşturduğunuz test modellerinde bilgileri kaybedebilirsiniz.  Örneğin, hata ayıklama çözümü, bazı şekiller ve bağlayıcılar içeren örnek adlı bir dosya içerir. DSL tanımınızı geliştirmeye başladıktan sonra, bunlar görünür olmayacaktır ve dosyayı kaydettiğinizde kaybedilir.

DSL 'niz için çok çeşitli uzantılar yapabilirsiniz. Aşağıdaki örnekler size olasılıklardan oluşan bir izlenim verecektir.

Her değişiklikten sonra DSL tanımını kaydedin, **Çözüm Gezgini** **Tüm Şablonları Dönüştür** ' e tıklayın ve ardından değiştirilen DSL 'yi denemek için **F5** tuşuna basın.

### <a name="rename-the-types-and-tools"></a>Türleri ve araçları yeniden adlandırma

Var olan etki alanı sınıflarını ve ilişkileri yeniden adlandırın. Örneğin, minimum dil şablonundan oluşturulan bir DSL tanımından başlayarak, DSL 'nin aile ağaçlarını göstermesini sağlamak için aşağıdaki yeniden adlandırma işlemlerini gerçekleştirebilirsiniz.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Etki alanı sınıflarını, ilişkileri ve araçları yeniden adlandırmak için

1. DslDefinition diyagramında, **ExampleModel** ' i **FamilyTreeModel**, **ExampleElement** öğesini **kişiye**, **Ebeveynler** için **hedefler** ve **alt öğeleri** olan **kaynaklara** yeniden adlandırın. Her etikete tıklayarak bunu değiştirebilirsiniz.

     ![DSL tanımı diyagramı &#45; aile ağacı modeli](../modeling/media/familyt_person.png)

2. Öğe ve bağlayıcı araçlarını yeniden adlandırın.

    1. Çözüm Gezgini altındaki sekmeye tıklayarak DSL Gezgini penceresini açın. Bunu göremiyorsanız, **Görünüm** menüsünde **diğer pencereler** ' i Işaret edin ve ardından **DSL Gezgini**' ne tıklayın. DSL Gezgini yalnızca DSL tanımı diyagramı etkin pencere olduğunda görülebilir.

    2. Özellikler penceresi açın ve aynı anda DSL Gezginini ve özelliklerini görebilmek için konumlandırın.

    3. DSL Gezgini ' nde **Düzenleyici**, **araç kutusu sekmeleri**, *\<your DSL>* ve ardından **Araçlar**' ı genişletin.

    4. **ExampleElement öğesine** tıklayın. Bu, öğeleri oluşturmak için kullanılan araç kutusu öğesidir.

    5. Özellikler penceresi, **ad** özelliğini **Person** olarak değiştirin.

         **Caption** özelliğinin de değişdiğine dikkat edin.

    6. Aynı şekilde, **ExampleConnector** aracının adını **parentlınk** olarak değiştirin. **Caption** özelliğini, Name özelliğinin bir kopyası olmaması için değiştirin. Örneğin, **üst bağlantıyı** girin.

3. DSL 'yi yeniden derleyin.

    1. DSL tanım dosyasını kaydedin.

    2. Çözüm Gezgini araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın

    3. F5 tuşuna basın. Visual Studio 'nun deneysel örneği görünene kadar bekleyin.

4. Visual Studio 'nun Deneysel örneğindeki hata ayıklama çözümünde bir test modeli dosyası açın. Öğeleri araç kutusu 'ndan üzerine sürükleyin. DSL Gezgini 'ndeki araç başlıklarının ve tür adlarının değiştiğini unutmayın.

5. Model dosyasını kaydedin.

6. Bir. tt dosyası açın ve eski tür ve özellik adlarının oluşumlarını yeni adlarla değiştirin.

7. . Tt dosyasında belirtilen dosya adının test modelinizi belirttiğinden emin olun.

8. . Tt dosyasını kaydedin. Kodu. tt dosyasında çalıştırmanın sonucunu görmek için oluşturulan dosyayı açın. Doğru olduğunu doğrulayın.

### <a name="add-domain-properties-to-classes"></a>Sınıflara etki alanı özellikleri ekleyin
 Bir etki alanı sınıfına özellikler ekleyin, örneğin, bir kişinin Doğum ve ölül yılını temsil edin.

 Yeni özellikleri diyagramda görünür hale getirmek için model öğesini görüntüleyen şekle *dekoratörler* eklemeniz gerekir. Ayrıca özellikleri dekoratörler ile de eşlemeniz gerekir.

##### <a name="to-add-properties-and-display-them"></a>Özellikleri eklemek ve bunları göstermek için

1. Özellikleri ekleyin.

   1. DSL tanımı diyagramında **kişi** etki alanı sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **etki alanı özelliği**' ne tıklayın.

   2. **Doğum** ve **ölüm** gibi yeni özellik adlarının bir listesini yazın. Her birinin ardından **ENTER** tuşuna basın.

2. Şekildeki özellikleri görüntüleyecek dekoratörler ekleyin.

   1. Kişi etki alanı sınıfından diyagramın diğer tarafına genişleyen gri çizgiyi izleyin. Bu bir diyagram öğe eşlemedir. Alan sınıfını bir şekil sınıfına bağlar.

   2. Bu şekil sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **metin dekoratörü**' ne tıklayın.

   3. **Ikdekoratör** ve **DeathDecorator** gibi adlara sahip iki dekoratörü ekleyin.

   4. Her yeni dekoratör ' ı seçin ve Özellikler penceresi **konum** alanını ayarlayın. Bu, şekil üzerinde etki alanı özelliği değerinin nerede gösterileceğini belirler. Örneğin, **InnerBottomLeft** ve **InnerBottomRight**'yi ayarlayın.

        ![Bölme şekli tanımı](../modeling/media/familyt_compartment.png)

3. Dekoratlarını özelliklerle eşleyin.

   1. DSL ayrıntıları penceresini açın. Genellikle çıkış penceresinin yanındaki bir sekmeden oluşur. Bunu göremiyorsanız, **Görünüm** menüsünde **diğer pencereler**' ın üzerine gelin ve **DSL ayrıntıları**' na tıklayın.

   2. DSL tanımı diyagramında, **kişi** etki alanı sınıfını şekil sınıfına bağlayan satıra tıklayın.

   3. **DSL ayrıntıları** **dekoratör haritaları** sekmesinde, eşlenmemiş dekoratörün onay kutusuna tıklayın. **Görüntü özelliği**' nde, eşleştirilmesini istediğiniz etki alanı özelliğini seçin. Örneğin, **Doğıcı dolabı** **Doğum** olarak eşleyin.

4. DSL 'yi kaydedin, tüm Şablonları Dönüştür ' e tıklayın ve F5 tuşuna basın.

5. Örnek model diyagramında, artık seçtiğiniz konumlara tıklabildiğinizi ve bunlara değer yazdığınıza emin olun. Ayrıca, bir **kişi** şekli seçtiğinizde Özellikler penceresi, yeni özellikleri Doğum ve ölüm olarak görüntüler.

6. Bir. tt dosyasında, her birinin özelliklerini elde eden kodu ekleyebilirsiniz.

   ![Aile ağacı diyagramı, araç kutusu ve gezgin](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Yeni sınıfları tanımlama
 Bir modele etki alanı sınıfları ve ilişkiler ekleme. Örneğin, şehirleri temsil etmek için yeni bir sınıf ve bir kişinin bir şehirde yaşadığı ilişkiyi temsil edecek yeni bir ilişki oluşturabilirsiniz.

 Bir model diyagramında farklı türleri ayrı yapmak için etki alanı sınıflarını farklı şekil türlerine veya farklı geometri ve renklere sahip şekillere eşebilirsiniz.

##### <a name="to-add-and-display-a-new-domain-class"></a>Yeni bir etki alanı sınıfı eklemek ve görüntülemek için

1. Bir etki alanı sınıfı ekleyin ve bunu model kökünün alt sınıfına ekleyin.

    1. DSL Tanımı diyagramında Katıştırma İlişkisi aracına tıklayın, **FamilyTreeModel** kök sınıfına tıklayın ve ardından diyagramın boş bir parçasına tıklayın. 

         FamilyTreeModel'e ekleme ilişkisiyle bağlı yeni bir etki alanı sınıfı görüntülenir.

         Adını ayarlayın, örneğin **Şehir**.

        > [!NOTE]
        > Modelin kökü dışındaki her etki alanı sınıfının en az bir ekleme ilişkisinin hedefi olması veya eklemenin hedefi olan bir sınıftan devralması gerekir. Bu nedenle, Katıştırma İlişkisi aracını kullanarak bir etki alanı sınıfı oluşturmak sık sık kullanışlıdır.

    2. Yeni sınıfa ad gibi bir etki alanı özelliği **ekleyin.**

2. Kişi ve Şehir arasında bir başvuru ilişkisi ekleyin.

    1. Başvuru **İlişkisi aracına,** Kişi'ye ve ardından Şehir'e tıklayın.

         ![DSL tanım parçası: aile ağacı kökü](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Başvuru ilişkileri, model ağacının bir parçasından diğerine çapraz başvuruları temsil ediyor.

3. Model diyagramlarında şehirleri temsil etmek için bir şekil ekleyin.

    1. Araç **kutusundan bir** Geometri Şeklini diyagrama sürükleyip yeniden adlandırabilirsiniz, örneğin **TownShape**.

    2. Yeni Özellikler penceresi Dolgu Rengi ve Geometri gibi Görünüm alanlarını ayarlayın.

    3. Şehrin adını görüntülemek için bir Dekoratör ekleyin ve nameDecorator olarak yeniden adlandıryın. Konum özelliğini ayarlayın.

4. Town etki alanı sınıfını TownShape ile eşler.

    1. Diyagram Öğesi **Haritası aracına** tıklayın, ardından Şehir etki alanı sınıfına ve ardından TownShape şekil sınıfına tıklayın.

    2. Harita **bağlayıcısı seçiliyken** DSL Ayrıntıları penceresinin **Dekoratör** Haritaları sekmesinde, AdDecorator'ı kontrol edin ve Görünen Özellik'i **Ad olarak** ayarlayın.

5. Person ve İlişkiler arasındaki ilişkiyi görüntülemek için bir bağlayıcı oluşturun.

    1. Bağlayıcıyı araç kutusundan diyagrama sürükleyin. Yeniden adlandırarak görünüm özelliklerini ayarlayın.

    2. Yeni **bağlayıcıyı Kişi** ve Şehir arasındaki ilişkiye bağlantı için Diyagram Öğesi Eşleme aracını kullanın.

         ![Şekil haritası eklenmiş Aile Ağacı tanımı](../modeling/media/familyt_shapemap.png)

6. Yeni bir Şehir oluşturmak için bir öğe aracı oluşturun.

    1. **DSL Gezgini'nde** Düzenleyici'ye **ve ardından** Araç **Kutusu Sekmeleri'ni genişletin.**

    2. Sağ tıklayın ve *\<your DSL>* ardından Yeni Öğe Aracı **Ekle'ye tıklayın.**

    3. Yeni **aracın Name** özelliğini ve Class özelliğini **Town** olarak ayarlayın.

    4. Araç Kutusu **Simgesi özelliğini** ayarlayın. **Öğesini tıklatın ve** Dosya adı **alanında** bir simge dosyası seçin.

7. Ilçeler ve insanlar arasında bağlantı oluşturmak için bir bağlayıcı aracı oluşturun.

    1. Sağ tıklayın ve *\<your DSL>* ardından Yeni Bağlayıcı Aracı **Ekle'ye tıklayın.**

    2. Yeni aracın Name özelliğini ayarlayın.

    3. **ConnectionBuilder özelliğinde,** ilişki oluşturma ilişkisinin adını içeren Person-Town seçin.

    4. Araç Kutusu **Simgesini ayarlayın.**

8. DSL Tanımını kaydedin, Tüm Şablonları **Dönüştür'e tıklayın** ve **F5 tuşuna basın.**

9. Deneysel Visual Studio test modeli dosyasını açın. Şehirleri ve şehirleri ve kişiler arasındaki bağlantıları oluşturmak için yeni araçları kullanın. Yalnızca doğru öğe türleri arasında bağlantı oluşturabilirsiniz.

10. Her bir kişinin yaşadığı şehri listeleye kod oluşturun. Metin şablonları, bu tür kodu çalıştırabilirsiniz. Örneğin, Hata Ayıklama çözümünde mevcut Sample.tt dosyasını aşağıdaki kodu içeren şekilde değiştirebilirsiniz:

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     *.tt dosyasını kaydedecek, kişilerin ve onların evlerinin listesini içeren bir yan kuruluş dosyası oluşturacak. Daha fazla bilgi için [bkz. Domain-Specific Dilinden Kod Oluşturma.](../modeling/generating-code-from-a-domain-specific-language.md)

## <a name="validation-and-commands"></a>Doğrulama ve Komutlar
 Doğrulama kısıtlamaları ekleyerek bu DSL'i daha da geliştirin. Bu kısıtlamalar, modelin doğru durumda olduğundan emin olmak için tanımladığınız yöntemlerdir. Örneğin, bir çocuğun doğum tarihini ebeveynlerinin doğum tarihine göre daha geç olduğundan emin olmak için bir kısıtlama tanımlayabilirsiniz. DSL kullanıcısı kısıtlamaların herhangi birini bozan bir modeli kaydetmeye çalışırsa doğrulama özelliği bir uyarı görüntüler. Daha fazla bilgi için, [bkz. Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

 Ayrıca, kullanıcının çağıranı menü komutlarını da tanımlayabilirsiniz. Komutlar modeli değiştirebilir. Ayrıca, kaynaklarda ve dış kaynaklarda Visual Studio modellerle de etkileşime olabilir. Daha fazla bilgi için, [bkz. How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>DSL'yi dağıtma
 Diğer kullanıcıların etki alanına özgü dili kullanmasına izin vermek için bir Visual Studio Uzantısı (VSIX) dosyası dağıtırsanız. Bu, DSL çözümünü oluşturulduğunda oluşturulur.

 Çözümdürmenizin bin klasöründe .vsix dosyasını bulun. Yüklemek istediğiniz bilgisayara kopyalayın. Bu bilgisayarda VSIX dosyasına çift tıklayın. DSL, bu bilgisayarın tüm Visual Studio kullanılabilir.

 DSL'i kendi bilgisayarınıza yüklemek için aynı yordamı kullanabilirsiniz, böylece Visual Studio.'nin deneysel örneğini kullanmak zorunda Visual Studio.

 Daha fazla bilgi için, [bkz. Deploying Domain-Specific Language Solutions](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Eski Deneysel DSL'leri kaldırma
 Artık istemeyebilirsiniz deneysel DSL'ler oluşturduysanız, Deneysel örneği sıfırlayarak bunları Visual Studio kaldırabilirsiniz.

 Bu, bilgisayarınızdan tüm deneysel DSL'leri ve diğer deneysel Visual Studio kaldırır. Bunlar hata ayıklama modunda yürütülen uzantılardır.

 Bu yordam, VSIX dosyasını yürüterek Visual Studio yüklü olan DIĞER UZANTıLAR'ı veya diğer uzantılarını kaldırmaz.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Deneysel Visual Studio sıfırlamak için

1. **Başlat'a** tıklayın, Tüm **Programlar'a** tıklayın, Microsoft Visual Studio  **2010 SDK,** Araçlar'a tıklayın ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın.**

2. Tüm deneysel DSL'leri veya Visual Studio hala kullanmak istediğiniz diğer deneysel uzantılarını yeniden oluşturma.

## <a name="see-also"></a>Ayrıca bkz.

- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
