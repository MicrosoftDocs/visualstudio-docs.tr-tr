---
title: Etki Alanına Özgü Dillerle Çalışmaya Başlama
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 89723d09fdd6362cdc301f1fa551b7c062639df0
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967330"
---
# <a name="get-started-with-domain-specific-languages"></a>Alana Özgü Dilleri Kullanmaya Başlama

Bu konu tanımlama ve Visual Studio için modelleme SDK'sı ile oluşturulan bir etki alanına özgü dil (DSL) kullanarak temel kavramları açıklar.

> [!NOTE]
> Visual Studio 2017'de metin şablonu dönüştürme SDK'sını ve Visual Studio modelleme SDK'sı, Visual Studio'nun belirli özelliklerini yüklediğinizde otomatik olarak yüklenir. Daha fazla ayrıntı için [bu blog gönderisini](https://blogs.msdn.microsoft.com/devops/2016/12/12/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

DSL için yeni başladıysanız, aracılığıyla çalışmanızı öneririz **DSL araçları Laboratuvar**, bu sitede bulabileceğiniz: [Visualizaton ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Bir etki alanına özgü dil ile ne yapabilirsiniz?

Belirli bir amaç için kullanılmak üzere tasarlanmış bir gösterim, genellikle grafik etki alanına özgü dilidir. Bunun aksine, UML gibi dilleri genel amaçlı. Bir DSL model öğesi ve ilişkilerini ve ekranda nasıl sunulan türlerini tanımlayabilirsiniz.

Bir DSL tasarlarken, bir Visual Studio Tümleştirme Uzantısı (VSIX) paketini bir parçası olarak dağıtabilirsiniz. Kullanıcılar, Visual Studio DSL çalışmak:

![Aile ağaç görünümünü, araç ve Gezgini](../modeling/media/familyt_instance.png)

Bir DSL yalnızca bir kısmını gösterimidir. Gösterimi ile birlikte, VSIX paketini, kullanıcılar bunları düzenleyebilir ve bunların modellerinden malzemesi oluşturmak amacıyla uygulayabilir araçları içerir.

DSL asıl uygulamaların program kodu, yapılandırma dosyalarını ve diğer yapıları üretmek için biridir. Özellikle büyük projeler ve ürün satırlarını, bir ürün birkaç çeşidini oluşturulacağı, birden çok değişken DSL'ler oluşturma büyük bir artış güvenilirlik ve gereksinim değişikliklerine çok hızlı bir yanıt sağlar.

Bu genel bakışta geri kalanı, oluşturma ve bir etki alanına özgü dil Visual Studio kullanarak sunucunun temel işlemlerini tanıtan bir kılavuz olur.

## <a name="prerequisites"></a>Önkoşullar

Bir DSL tanımlamak için aşağıdaki bileşenler yüklemiş olmanız gerekir:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| Visual Studio için modelleme SDK'sı | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Bir DSL çözümü oluşturun

Yeni bir etki alanına özgü dil oluşturma için etki alanına özgü dil proje şablonunu kullanarak yeni bir Visual Studio çözümü oluşturun.

1.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.

2.  Altında **proje türleri**, genişletme **diğer proje türleri** düğüm seçeneğine tıklayıp **genişletilebilirlik**.

3.  Tıklayın **etki alanına özgü dil tasarımcısını**.

     ![DSL iletişim kutusu oluşturma](../modeling/media/create_dsldialog.png)

4.  İçinde **adı** kutusuna **FamilyTree**. **Tamam**'ı tıklatın.

     **Etki alanına özgü dil Sihirbazı** açılır ve şablon DSL çözümlerinin bir listesini görüntüler.

     Her şablon açıklamasını görmek için tıklatın

     Şablonları yararlıdır başlangıç noktaları. Bunların her biri, tam bir çalışma, gereksinimlerinize uyacak şekilde düzenleyebileceğiniz DSL sağlar. Normalde, en yakın oluşturmak istediğiniz şablonu seçin.

5.  Bu kılavuz için seçin **Minimal dil** şablonu.

6.  Uygun Sihirbazı sayfasında DSL'nizi için bir dosya adı uzantısını girin. Bu örnekleri DSL'nizi içeren dosyalar kullanacağınız uzantısıdır.

    -   Bilgisayarınızda veya DSL yüklemek istediğiniz herhangi bir bilgisayarda herhangi bir uygulama ile ilişkili olmayan bir uzantı seçin. Örneğin, **docx** ve **htm** kabul edilemez bir dosya adı uzantıları olacaktır.

    -   Girdiğiniz uzantısı DSL kullanılıp kullanılmadığını, sihirbaz sizi uyarır. Farklı dosya adı uzantısını kullanmayı düşünün. Eski Deneysel tasarımcıları temizlemek için Visual Studio SDK deneysel örneği de sıfırlayabilirsiniz. Tıklayın **Başlat**, tıklayın **tüm programlar**, **Microsoft Visual Studio 2010 SDK**, **Araçları**, ardından **Microsoft sıfırlama Visual Studio 2010 deneysel örneği**.

7.  Diğer sayfalarını inceleyin ve ardından **son**.

     İki proje içeren bir çözümü oluşturulur. Bunlar, Dsl ve DslPackage adlandırılır. Bir diyagram dosyası başka bir deyişle, adlandırılmış DslDefinition.dsl açılır.

    > [!NOTE]
    > İki proje klasörlerdeki gördüğünüz kodu çoğunu DslDefinition.dsl oluşturulur. Bu nedenle, bu dosyada DSL'nizi çoğu değişiklikler yapılır.

Kullanıcı arabirimi artık aşağıdaki resme benzer.

![DSL Tasarımcısı](../modeling/media/dsl_designer.png)

Bu çözüm, bir etki alanına özgü dil tanımlar. Daha fazla bilgi için [etki alanına özgü dil araçları kullanıcı arabirimine genel bakış](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>DSL çözümünün önemli bölümleri

Yeni çözüm şu yönlerini dikkat edin:

-   **Dsl\DslDefinition.DSL** bu DSL bir çözüm oluşturduğunuzda, gördüğünüz dosyasıdır. Çözümdeki neredeyse tüm kod bu dosyadan oluşturulur ve bir DSL tanımını için yaptığınız değişikliklerin çoğu burada sunulur. Daha fazla bilgi için bkz. Working with [DSL tanım diyagramı ile çalışma](../modeling/working-with-the-dsl-definition-diagram.md).

-   **DSL projesi** bu proje etki alanına özgü dil tanımlayan kodu içerir.

-   **DslPackage proje** bu proje açılamaz ve Visual Studio'da düzenlenemez için DSL örneklerini veren kod içerir.

##  <a name="Debugging"></a> DSL çalıştırma

Oluşturduktan hemen sonra DSL çözüm çalıştırabilirsiniz. Daha sonra çözümü yeniden her değişiklikten sonra çalıştırırken DSL tanımını yavaş yavaş değiştirebilirsiniz.

### <a name="to-experiment-with-the-dsl"></a>DSL ile denemek için

1.  Tıklayın **tüm Şablonları Dönüştür** içinde **Çözüm Gezgini** araç çubuğu. Bu, çoğu DslDefinition.dsl kaynak kodundan yeniden oluşturur.

    > [!NOTE]
    > Değiştirdiğiniz zaman *DslDefinition.dsl*, tıklamanız **tüm Şablonları Dönüştür** önce çözümü yeniden oluşturun. Bu adım otomatik hale getirebilirsiniz. Daha fazla bilgi için [otomatikleştirmek tüm Şablonları Dönüştür nasıl](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2.  Tuşuna **F5**, veya **hata ayıklama** menüsünde tıklatın **hata ayıklamayı Başlat**.

     DSL oluşturur ve ise Visual Studio'nun deneysel örneğinde yüklü.

     Visual Studio deneysel örneği başlar. Deneysel örneğinde, ayrı bir alt ağacı hata ayıklama amacıyla Visual Studio uzantıları burada kaydedilir, kayıt defteri ayarlarını alır. Visual Studio'nun normal örneği burada kayıtlı uzantılara erişiminiz yok.

3.  Visual Studio'nun deneysel örneğinde adlı model dosyasını açma **Test** gelen **Çözüm Gezgini**.

     \- veya -

     Hata ayıklama projeye sağ tıklayın, fareyle **Ekle**ve ardından **öğesi**. İçinde **Öğe Ekle** dosya DSL'nizi iletişim kutusunda, türünü seçin.

     Model dosyası boş bir diyagramı açılır.

     Araç kutusu açılır ve diyagram türü için uygun araçları görüntüler.

4.  Diyagramdaki şekilleri ve bağlayıcıları oluşturma araçlarını kullanın.

    1.  Şekil oluşturmak için örnek şekil aracı diyagram üzerine sürükleyin.

    2.  İki şekil bağlanmak için örnek bağlayıcı Aracı'nı tıklatın, ilk şekle tıklayın ve ardından ikinci şekle tıklayın.

5.  Etiketleri şekillerin bunları değiştirmek için tıklayın.

Deneysel Visual Studio, aşağıdaki örneğe benzer:

![](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Modelin içeriğine

Bir DSL örneği olan bir dosyanın içeriğini adlı bir *model*. Modeli içeren *modeli*<em>öğeleri</em> ve *bağlantıları* olan öğeler arasında. Ne tür bir model öğelerini DSL tanımını belirtir ve modelde bağlantılar bulunabilir. Örneğin, en az bir dil şablondan oluşturulan bir DSL içinde var. bir model öğesi türünü ve bir bağlantı türü

DSL tanımını modelin diyagram üzerinde nasıl görüneceğini belirleyebilirsiniz. Stilleri şekillerin ve bağlayıcıların çeşitli arasından seçim yapabilirsiniz. Bazı şekiller içindeki diğer şekiller görünür belirtebilirsiniz.

Bir modeli içinde bir ağaç olarak görüntüleyebileceğiniz **Gezgini** model düzenlerken görüntüleyin. Şekil diyagrama eklemek gibi model öğelerini de Gezgini'nde görünür. Gezgin hiçbir diyagramı olsa bile kullanılabilir.

Visual Studio hata ayıklama örneğindeki Gezgini'nde göremiyorsanız **görünümü** menüsünde **diğer Windows**ve ardından  *\<bilgisayarınızı dil >* **Gezgini**.

### <a name="the-api-of-your-dsl"></a>DSL'nizi API'si

DSL'nizi okumasına ve güncelleştirmesine DSL örnekleridir modelleri olanak tanıyan bir API oluşturur. Bir API uygulaması, metin dosyaları modelden oluşturmaktır. Daha fazla bilgi için [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Hata ayıklama çözümde ".tt" uzantısı ile şablon dosyalarını açın. Bu örnekler nasıl metin modelleri oluşturabilir ve, DSL'nin API'yi test etme izin gösterir. Örneklerden birini yazılmış [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], içinde diğer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

Her şablon altında dosyası, oluşturduğu dosyasıdır. Çözüm Gezgini'nde şablon dosyası'nı genişletin ve oluşturulan dosyasını açın.

Şablon dosyası modelindeki tüm öğeleri listeler kod kısa bir parçasını içerir.

Oluşturulan dosyanın sonucu içerir.

Bir model dosyasını değiştirdiğinizde, dosya yeniden oluşturduktan sonra oluşturulan dosyalarındaki ilgili değişiklikleri görürsünüz.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Model dosyasını değiştirdikten sonra metin dosyaları yeniden oluşturmak için

1.  Visual Studio'nun deneysel örneğinde model dosyasını kaydedin.

2.  Dosya adı parametresi her .tt dosyasındaki denemeleri için kullanmakta olduğunuz modeli dosyaya başvurduğundan emin olun. .Tt dosyayı kaydedin.

3.  Tıklayın **tüm Şablonları Dönüştür** araç **Çözüm Gezgini**.

     \- veya -

     Sağ tıklayın, yeniden oluşturun ve ardından istediğiniz şablonları **özel aracı Çalıştır**.

Metin şablonu dosyaları herhangi bir sayıda projeye ekleyebilirsiniz. Her şablon bir sonuç dosyası oluşturur.

> [!NOTE]
> DSL tanımı değiştirdiğinizde, güncelleştirmeniz sürece örnek metin şablonunun kod çalışmaz.

Daha fazla bilgi için [bir etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md) ve [bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>DSL özelleştirme

DSL tanımının değiştirmek istediğiniz deneysel örneği kapatın ve ana Visual Studio örneğinde tanımını güncelleştirin.

> [!NOTE]
> DSL tanımını değiştirdikten sonra önceki sürümlerini kullanarak oluşturulan test modelleri bilgileri kaybedilebilir.  Örneğin, hata ayıklama çözüm bazı şekilleri ve bağlayıcıları içeren örnek adlı bir dosya içeriyor. DSL tanımınızı geliştirmek başlattıktan sonra bunların görünür olmaz ve dosyayı kaydettiğinizde, bunlar kaybolacak.

DSL'nizi için çok çeşitli uzantıları yapabilirsiniz. Aşağıdaki örnekler size bir izlenimi olanakları sunar.

DSL tanımını kaydet her değişiklikten sonra tıklayın **tüm Şablonları Dönüştür** içinde **Çözüm Gezgini**ve tuşuna **F5** ile değiştirilen DSL denemek için.

### <a name="rename-the-types-and-tools"></a>Araçları ve türleri yeniden adlandır

Mevcut etki alanı sınıfları ve ilişkileri yeniden adlandırın. Örneğin, en az bir dil şablondan oluşturulan bir Dsl tanımını başlayarak, aile ağaçlarını temsil DSL yapmak için aşağıdaki yeniden adlandırma işlemleri gerçekleştirebilir.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Etki alanı sınıfları, ilişkilerini ve araçları yeniden adlandırmak için

1.  DslDefinition diyagramda, yeniden adlandırma **ExampleModel** için **FamilyTreeModel**, **ExampleElement** için **kişi**,  **Hedefleri** için **üst**, ve **kaynakları** için **alt**. Her bir etiketi değiştirmek için tıklayabilirsiniz.

     ![DSL tanım diyagramı &#45; ailesi ağaç modeli](../modeling/media/familyt_person.png)

2.  Öğe ve bağlayıcı Araçlar yeniden adlandırın.

    1.  DSL Gezgini penceresi, Çözüm Gezgini altında sekmesine tıklayarak açın. Üzerinde göremiyorsanız, **görünümü** menüsünde **diğer Windows** ve ardından **DSL Gezgini**. DSL tanım diyagramı etkin pencere olduğunda DSL Gezgini görünür olur.

    2.  Özellikler penceresini açın ve aynı anda DSL Gezgini ve özellikleri görebilmek konumlandırın.

    3.  DSL Gezgini'nde **Düzenleyicisi**, **araç kutusu sekmeleri**,  *\<DSL'nizi >*, ardından **Araçları**.

    4.  Tıklayın **ExampleElement**. Öğeleri oluşturmak için kullanılan araç kutusu öğesi budur.

    5.  Özellikler penceresinde değişiklik **adı** özelliğini **kişi**.

         Dikkat **açıklamalı alt yazı** özelliği de değişir.

    6.  Aynı şekilde, adını değiştirmek **ExampleConnector** aracını **ParentLink**. ALTER **açıklamalı alt yazı** BT'nin Name özelliği bir kopyasını, yani özelliği. Örneğin, **üst bağlantı**.

3.  DSL yeniden oluşturun.

    1.  DSL tanım dosyasını kaydedin.

    2.  Tıklayın **tüm Şablonları Dönüştür** Çözüm Gezgini araç çubuğundaki

    3.  F5 tuşuna basın. Visual Studio'nun deneysel örneğinde görünene kadar bekleyin.

4.  Visual Studio'nun deneysel örneğinde hata ayıklama çözümde test model dosyasını açın. Öğeleri sürüklediğinizde araç kutusundan sürükleyin. Aracı açıklamalı alt yazılar ve DSL Gezgini içindeki tür adları değiştirildi dikkat edin.

5.  Model dosyasını kaydedin.

6.  .Tt dosyasını açın ve yeni adları ile eski türünü ve özellik adlarını değiştirme.

7.  .Tt dosyası içinde belirtilen dosya adı test modelinizi belirttiğinden emin olun.

8.  .Tt dosyayı kaydedin. .Tt dosyasında kod çalıştırmanın sonuçlarını görmek için oluşturulan dosyasını açın. Doğru olduğundan emin olun.

### <a name="add-domain-properties-to-classes"></a>Sınıflar için etki alanı özellikleri ekleyin
 Özellikler, örneğin doğum yılı ve bir kişinin ölüm temsil etmek bir alan sınıfına ekleyin.

 Diyagram üzerinde yeni özellikleri görünür yapmak için eklemelisiniz *dekoratörler* şekle model öğesi görüntüler. Dekoratörler için özellikler de eşlemeniz gerekir.

##### <a name="to-add-properties-and-display-them"></a>Özellikleri ekleyin ve bunları görüntülemek için

1. Özellikleri ekleyin.

   1.  DSL tanım diyagramı içinde sağ **kişi** etki alanı sınıfı, noktasına **Ekle**ve ardından **Domain özelliği**.

   2.  Yeni özellik adlarının bir listesini yazın **Doğum** ve **ölüm**. Tuşuna **Enter** sonra her biri.

2. Özellikleri şeklinde görüntüler dekoratörler ekleyin.

   1.  Kişinin etki alanı diyagramı diğer tarafında sınıftan gri çizgi izleyin. Diyagram öğesi eşlemesi budur. Bu etki alanı sınıfı bir şekil sınıfına bağlar.

   2.  Bu şeklin sınıf sağ tıklatın, **Ekle**ve ardından **metin Dekoratör**.

   3.  Adlara sahip iki dekoratörler gibi ekleme **BirthDecorator** ve **DeathDecorator**.

   4.  Her yeni dekoratör seçin ve Özellikler penceresinde ayarlayın **konumu** alan. Bu, etki alanı özellik değeri şeklin üzerinde nerede görüntüleneceğini belirler. Örneğin, **InnerBottomLeft** ve **InnerBottomRight**.

        ![Bölme şekli tanımı](../modeling/media/familyt_compartment.png)

3. Dekoratörler özelliklerine eşlenir.

   1.  DSL ayrıntıları penceresini açın. Genellikle bir sekmede çıkış penceresi yanındaki olur. Üzerinde göremiyorsanız, **görünümü** menüsünde **diğer Windows**ve ardından **DSL ayrıntıları**.

   2.  DSL tanım diyagramı üzerinde bağlanan çizgi **kişi** shape sınıfı için etki alanı sınıfı.

   3.  İçinde **DSL ayrıntıları**, **Dekoratör eşlemeleri** sekmesinde, eşlenmemiş bir dekoratör onay kutusuna tıklayın. İçinde **görüntüleme özelliği**, istediğiniz, eşlenmiş etki alanı özelliğini seçin. Örneğin, harita **BirthDecorator** için **Doğum**.

4. DSL kaydedin, tüm Şablonları Dönüştür'e tıklayın ve F5 tuşuna basın.

5. Örnek model diyagramda, seçtiğiniz konumları tıklayın artık ve bunları değerleri yazın doğrulayın. Ayrıca, seçtiğinizde bir **kişi** şeklini, Özellikler penceresinde Doğum ve ölüm yeni özellikleri gösterir.

6. .Tt dosyasında, her kişi özelliklerini alır kod ekleyebilirsiniz.

   ![Aile ağaç görünümünü, araç ve Gezgini](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Yeni sınıflar tanımlayın
 Bir model için etki alanı sınıfları ve ilişkileri ekleyebilirsiniz. Örneğin, şehir ve bir kişi bir piyasada orada yaşıyordum temsil etmek için yeni bir ilişki temsil etmek için yeni bir sınıf oluşturabilirsiniz.

 Farklı bir model diyagramda ayrı yapmak için etki alanı sınıfları farklı türden Şekil veya şekiller, renk ve farklı geometri eşleyebilirsiniz.

##### <a name="to-add-and-display-a-new-domain-class"></a>Ekleme ve yeni bir etki alanı sınıfını görüntüle

1.  Bir etki alanı sınıf ekleyin ve alt model kökünün yapın.

    1.  DSL tanım diyagramı içinde tıklayın **gömme ilişkisi** aracı, kök sınıfı tıklatın **FamilyTreeModel**ve ardından diyagramın boş bir bölümüne tıklayın.

         Yeni bir etki alanı sınıfı, FamilyTreeModel gömme ilişkisi ile bağlı görünür.

         Örneğin, adını ayarlayın **belediye**.

        > [!NOTE]
        >  Gömme hedefi bir sınıftan devralmalıdır veya en az bir gömme ilişkisi hedef modelin kökü dışındaki her etki alanı sınıfı olmalıdır. Bu nedenle, sık gömme ilişkisi aracını kullanarak bir etki alanı sınıfı oluşturmak uygun.

    2.  Yeni sınıfa, bir alan özelliği ekleyin, örneğin **adı**.

2.  Bir kişi ve şehir arasındaki başvuru ilişkisi ekleyin.

    1.  Tıklayın **başvuru ilişkisi** aracı, kişi ve ardından belediye tıklayın.

         ![DSL tanımının parçası: ailesi Ağaç kökü](../modeling/media/familyt_root.png)

        > [!NOTE]
        >  Başvuru ilişkilerini çapraz model ağacına bir bölümünden diğerine temsil eder.

3.  Model diyagramlarda kasabalarında şubeleri temsil etmek için bir şekil ekleyin.

    1.  Sürükleme bir **geometri şekli** araç kutusundan diyagrama ve örneğin, yeniden adlandırma **TownShape**.

    2.  Özellikler penceresinde dolgu rengi ve Geometry gibi yeni şekil görünüm alanlarını ayarlayın.

    3.  Belediye adını görüntülemek için bir Dekoratör ekleyin ve NameDecorator yeniden adlandırın. Kendi konum özelliğini ayarlayın.

4.  Belediye etki alanı sınıfı için TownShape eşleyin.

    1.  Tıklayın **diyagram öğesi eşlemesi** aracı ve şehir etki alanı sınıfı ve TownShape şekli sınıfı'ı tıklatın.

    2.  İçinde **Dekoratör eşlemeleri** sekmesinde **DSL ayrıntıları** map bağlayıcı penceresiyle seçili ve NameDecorator denetleyin **görüntüleme özelliği** adı.

5.  Kişi ve kasabalarında şubeleri arasındaki ilişkiyi görüntülemek için bir bağlayıcı oluşturun.

    1.  Bir bağlayıcı araç kutusundan diyagrama sürükleyin. Yeniden adlandırmak ve görünüm özelliklerini ayarlayın.

    2.  Kullanım **diyagram öğesi eşlemesi** yeni bağlayıcı kişi ve şehir arasındaki ilişkiyi bağlamak için aracı.

         ![Aile ağacı tanımıyla eklenmiş bir şekil Haritası](../modeling/media/familyt_shapemap.png)

6.  Yeni belediye yapmak için bir öğe aracı oluşturun.

    1.  İçinde **DSL Gezgini**, genişletme **Düzenleyicisi** ardından **araç kutusu sekmeleri**.

    2.  Sağ  *\<DSL'nizi >* ve ardından **yeni öğe aracı ekleme**.

    3.  Ayarlama **adı** özellik kümesi ve yeni aracı kendi **sınıfı** belediye özelliğini.

    4.  Ayarlama **araç kutusu simgesi** özelliği. Tıklayın **[...]**  ve **dosya adı** alanında, bir simge dosyası seçin.

7.  Kasabalarında şubeleri ve kişiler arasında bağlantı yapmak için bir bağlayıcı aracını oluşturun.

    1.  Sağ  *\<DSL'nizi >* ve ardından **ekleme yeni bağlayıcı aracını**.

    2.  Yeni aracı ad özelliğini ayarlayın.

    3.  İçinde **ConnectionBuilder** özelliği, kişi belediye ilişki adını içeren Oluşturucusu'nu seçin.

    4.  Ayarlama **araç kutusu simgesi**.

8.  DSL tanımını kaydedin, tıklayın **tüm Şablonları Dönüştür**ve tuşuna **F5**.

9. Visual Studio'nun deneysel örneğinde test model dosyasını açın. Yeni Araçları kasabalarında şubeleri ve kasabalarında şubeleri ve kişiler arasında bağlantı oluşturmak için kullanın. Yalnızca doğru türde öğe arasında bağlantılar oluşturabilirsiniz dikkat edin.

10. Listeler, her kişinin yaşadığı şehir kodu oluşturun. Metin şablonları gibi kod burada çalıştırabileceğiniz yerleri biridir. Örneğin, aşağıdaki kodu içeren hata ayıklama çözümü mevcut Sample.tt dosyasında değiştirebilirsiniz:

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

     *.Tt dosyasını kaydettiğinizde, kişiler ve bunların residences listesini içeren bir dosyası oluşturur. Daha fazla bilgi için [bir etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Doğrulama ve komutlar
 Doğrulama kısıtlamaları ekleyerek bu DSL daha fazla geliştirebilir. Bu kısıtlamaları, model doğru durumda olduğundan emin olun, tanımlayabilirsiniz, yöntemlerdir. Örneğin, doğum tarihi bir alt öğelerinden bundan sonraki olan emin olmak için bir kısıtlama tanımlayabilirsiniz. DSL kullanıcı kısıtlamaların hiçbirini keser bir model kaydetmeye çalıştığında doğrulama özelliği bir uyarı görüntüler. Daha fazla bilgi için [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 Ayrıca kullanıcının çağırabileceği menü komutları tanımlayabilirsiniz. Komutlar, model değiştirebilirsiniz. Ayrıca Visual Studio'da diğer modellerle ve dış kaynaklar ile etkileşebilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>DSL dağıtma
 Diğer kullanıcıların etki alanına özgü dil kullanmasına izin vermek için Visual Studio Uzantısı (VSIX) dosyasını dağıtın. DSL çözümü oluşturduğunuzda oluşturulur.

 Çözümünüzü bin klasöründe .vsix dosyasını bulun. Yüklemek istediğiniz bilgisayara kopyalayın. Bu bilgisayarda VSIX dosyasını çift tıklayın. DSL bu bilgisayarda Visual Studio'nun tüm örneklerini kullanılabilir.

 Visual Studio'nun deneysel örneğinde kullanmak zorunda değil, DSL kendi bilgisayarınıza yüklemek için aynı yordamı kullanabilirsiniz.

 Daha fazla bilgi için [etki alanına özgü dil çözümlerini dağıtma](../modeling/deploying-domain-specific-language-solutions.md).

##  <a name="Reset"></a> Eski Deneysel DSL'ler kaldırılıyor
 Artık istemediğiniz Deneysel DSL'ler oluşturduysanız, Visual Studio deneysel örneği sıfırlayarak bunları bilgisayarınızdan kaldırabilirsiniz.

 Tüm Deneysel DSL'ler ve diğer Deneysel Visual Studio uzantıları bu bilgisayardan kaldırır. Bu hata ayıklama modunda yürütülen uzantılarıdır.

 Bu yordam, DSL veya VSIX dosyasını yürüterek tam olarak yüklenmiş olan başka bir Visual Studio uzantısı kaldırmaz.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Visual Studio deneysel örneği sıfırlamak için

1.  Tıklayın **Başlat**, tıklayın **tüm programlar**, **Microsoft Visual Studio 2010 SDK**, **Araçları**, ardından **Microsoft sıfırlama Visual Studio 2010 deneysel örneği**.

2.  Deneysel hiçbir DSL'ler veya kullanmak istediğiniz diğer Deneysel Visual Studio uzantılarını yeniden oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)