---
title: 'Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama'
description: Bir şablondan, etki alanına özgü dil (DSL) tanımlamak için bir Visual Studio çözümü oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51717e4bdbf12478e22bb825a9c84cfc82815f98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387365"
---
# <a name="how-to-define-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama
Bir etki alanına özgü dil (DSL) tanımlamak için, bir şablondan bir Visual Studio çözümü oluşturursunuz. Çözümün anahtar bölümü DslDefinition. dsl ' de depolanan DSL tanımı diyagramıdır. DSL tanımı, DSL 'nin sınıflarını ve şekillerini tanımlar. Bu öğelere değiştirdikten ve ekledikten sonra, DSL 'yi daha ayrıntılı şekilde özelleştirmek için program kodu ekleyebilirsiniz.

DSLs 'yi yeni Deneyiyorsanız, bu sitede bulabileceğiniz **dsl araçları Laboratuvarı** aracılığıyla çalışmanızı öneririz: [görselleştirme ve modelleme SDK 'sı](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="selecting-a-template-solution"></a><a name="templates"></a> Şablon çözümü seçme

Bir DSL tanımlamak için aşağıdaki bileşenleri yüklemiş olmanız gerekir:

- Visual Studio
- Visual Studio uzantısı geliştirme iş yükü (Visual Studio SDK 'Sı dahil)
- Modelleme SDK 'Sı (Visual Studio 'da tek bir bileşen olarak yükler)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Yeni bir etki alanına özgü dil oluşturmak için Domain-Specific Language proje şablonunu kullanarak yeni bir Visual Studio çözümü oluşturun.

### <a name="to-create-a-dsl-solution"></a>DSL çözümü oluşturmak için

1. Yeni bir **etki alanına özgü dil** projesi oluşturun.

   ::: moniker range="vs-2017"

    ![DSL oluştur iletişim kutusu](../modeling/media/create_dsldialog.png)

   ::: moniker-end

    **Etki alanına özgü dil Sihirbazı** açılır ve şablon DSL çözümlerinin listesini görüntüler.

2. Açıklamaları görmek için her şablona tıklayın. Oluşturmak istediklerinizi en yakından benzeyen çözümü seçin.

    Her DSL şablonu, temel bir çalışan DSL tanımlar. Bu DSL 'yi kendi gereksinimlerinize uyacak şekilde düzenleyecaksınız.

    Daha fazla bilgi için her örneğe tıklayın.

   - Kulvarlar içeren bir DSL oluşturmak için **Görev akışı** ' nı seçin. Kulvarlar, diyagramın dikey veya yatay bölümlerdir.

   - Bağlantı noktaları olan bir DSL oluşturmak için **bileşen modellerini** seçin. Bağlantı noktaları, daha büyük bir şeklin kenarındaki küçük şekillerdir.

   - Bölme şekillerine sahip bir DSL tanımlamak için **sınıf diyagramları** ' nı seçin. Bölme şekilleri öğe listelerini içerir.

   - Diğer durumlarda veya emin değilseniz, **küçük bir dil** seçin.

   - Windows Forms veya WPF yüzeyinde görüntülenen bir DSL oluşturmak için **en az WinForm Designer** veya **Minimum WPF Tasarımcısı** ' nı seçin. Düzenleyiciyi tanımlamak için kod yazmanız gerekir. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

        [Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [WPF Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Uygun sihirbaz sayfasında DSL 'niz için bir dosya adı uzantısı girin. Bu, DSL 'nin örneklerini içeren dosyaların kullanacağı uzantıdır.

   - Bilgisayarınızdaki herhangi bir uygulamayla veya DSL 'yi yüklemek istediğiniz herhangi bir bilgisayarda ilişkilendirilmemiş bir dosya adı uzantısı seçin. Örneğin, **docx** ve **htm** kabul edilemez dosya adı uzantıları olacaktır.

   - Girdiğiniz uzantı DSL olarak kullanılıyorsa, sihirbaz sizi uyarır. Farklı bir dosya adı uzantısı kullanmayı düşünün. Ayrıca, eski deneysel tasarımcıları temizlemek için Visual Studio SDK Deneysel örneğini de sıfırlayabilirsiniz. **Başlat**' a tıklayın, **tüm programlar**, **Microsoft Visual Studio 2010 SDK** ve **araçlar**' a tıklayın ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın**.

4. Diğer sayfalardaki ayarları ayarlayabilir ya da varsayılan değerleri bırakabilirsiniz.

5. **Finish (Son)** düğmesine tıklayın.

    Sihirbaz iki veya üç proje içeren bir çözüm oluşturur ve DSL tanımından kod üretir.

   Kullanıcı arabirimi artık aşağıdaki resme benzer.

   ![DSL Tasarımcısı](../modeling/media/dsl_designer.png)

   Bu çözüm, etki alanına özgü bir dili tanımlar. Daha fazla bilgi için bkz. [Domain-Specific dil Araçları Kullanıcı arabirimine genel bakış](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Çözümü test etme
 Şablon çözümü, farklı şekilde değiştirebileceğiniz veya kullanabileceğiniz bir çalışan DSL sağlar.

 Çözümü test etmek için F5 veya CTRL + F5 tuşlarına basın. Visual Studio 'nun yeni bir örneği deneysel modda açılır.

 Visual Studio 'nun yeni örneğinde, Çözüm Gezgini, örnek dosyayı açın. Bir araç kutusu ile diyagram olarak açılır.

 **En az dil** şablonundan oluşturduğunuz bir çözümü çalıştırırsanız, deneysel Visual Studio, aşağıdaki örneğe benzer olacaktır:

 ![Visual Studio 'da etki alanına özgü dil örnek ağacı](../modeling/media/dsl_min.png)

 Araçlarla denemeler yapın. Öğeler oluşturun ve bunları bağlayın.

 Visual Studio 'nun Deneysel örneğini kapatın.

> [!NOTE]
> DSL 'yi değiştirdiğinizde, örnek test dosyasında artık şekilleri göremezsiniz. Bununla birlikte, yeni öğeler de oluşturabilirsiniz.

### <a name="modifying-the-template-dsl"></a>Şablon DSL 'yi değiştirme
 Şablon DSL tanımında, tüm etki alanı sınıflarını ve şekil sınıflarını yeniden adlandırın ve saklayın. Yeni sınıf adlarınız, boşluk veya noktalama işareti olmadan geçerli CLR adları olmalıdır.

 Bu sınıfların tutulması özellikle yararlıdır:

- Kök sınıf, **sınıflar ve ilişkiler** altında DSL tanımı diyagramının sol üst kısmında görünür. Bunu DSL 'den farklı bir adla yeniden adlandırın. Örneğin, **MusicLibrary** ADLı bir DSL **müzik** adlı bir kök sınıfa sahip olabilir.

- Diyagram sınıfı, DSL tanımı diyagramının sağ alt kısmında, **diyagram öğeleri** sütununda görünür. Görmek için sağa kaydırmanız gerekebilir. Genellikle _DSL_**Diyagramı** olarak adlandırılır.

- **Görev akışı** şablonunu kullandıysanız ve kulvarlar ile diyagramlar oluşturmak istiyorsanız aktör etki alanı sınıfını ve Actorkulvar şeklini tutun ve yeniden adlandırın.

  Diğer sınıfları gereksinimlerinize uyacak şekilde silin veya yeniden adlandırın.

## <a name="patterns-for-defining-a-dsl"></a><a name="patterns"></a> DSL tanımlamaya yönelik desenler
 Bir veya iki özelliği tek seferde ekleyerek veya ayarlayarak bir DSL geliştirmenizi öneririz. Bir özellik ekleyin, DSL 'yi çalıştırın ve test edin ve ardından bir veya daha fazla özellik ekleyin. DSL 'nizin tipik bir özelliği şu olabilir:

- Bir etki alanı sınıfı, öğeyi modele bağlayan katıştırma ilişkisi, diyagramda bu sınıfın öğelerini göstermek için gereken şekil ve kullanıcıların öğe oluşturmalarına izin veren öğe aracı.

- Bir etki alanı sınıfının etki alanı özellikleri ve bunları bir şekil üzerinde görüntüleyen dekoratörler.

- Diyagramda ve kullanıcıların bağlantı oluşturmalarına izin veren bağlayıcı aracında görüntüleyen bir başvuru ilişkisi ve bağlayıcı.

- Bir doğrulama kısıtlaması veya bir menü komutu gibi program kodu gerektiren bir özelleştirme.

  Aşağıdaki bölümlerde, en kullanışlı DSL özelliği türlerinin nasıl oluşturulacağı açıklanır. Bir DSL 'nin oluşturulabileceği birçok farklı düzen vardır, ancak bunlar en sık kullanılan bu modellerdir.

> [!NOTE]
> Bir Özellik eklendikten sonra, DSL 'yi derleyip çalıştırmadan önce Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür** ' e tıklamayın.

 Aşağıdaki şekilde, bu konuda bir örnek olarak kullanılan DSL 'nin sınıfları ve ilişkiler bölümü gösterilmektedir.

 ![Ekleme ve başvuru ilişkileri](../modeling/media/music_classes.png)

 Sonraki şekil, bu DSL 'nin örnek bir modelidir:

 ![Oluşturulan DSL örnek modeli](../modeling/media/music_instance.png)

> [!NOTE]
> "Model", kullanıcıların oluşturduðu bir DSL örneğine başvurur ve genellikle diyagram olarak görüntülenir. Bu konuda hem DSL tanımı diyagramı hem de DSL kullanıldığında görüntülenen model diyagramları ele alınmaktadır.

## <a name="defining-domain-classes"></a><a name="classes"></a> Etki alanı sınıfları tanımlama
 Etki alanı sınıfları DSL kavramlarını temsil eder. Örnekler *model öğeleridir*. Örneğin, bir **MusicLibrary** DSL 'de, **Albüm** ve **şarkı** adında etki alanı sınıfları olabilir.

 Bir etki alanı sınıfı oluşturmak için, **adlandırılmış alan sınıfı** aracından diyagrama sürükleyebilir ve sonra sınıfı yeniden adlandırabilirsiniz.

 Daha fazla bilgi için bkz. [etki alanı sınıflarının özellikleri](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Her etki alanı sınıfı için bir katıştırma Ilişkisi oluştur
 Kök sınıf hariç her etki alanı sınıfı, en az bir katıştırma ilişkisinin hedefi olmalıdır veya bir katıştırma ilişkisinin hedefi olan bir sınıftan devralması gerekir.

 Bir modelde, her model öğesi, katıştırma ilişkilerinin tek bir ağacındaki bir düğümdür. Gömme ilişkisinin kaynağı ve hedefi sıklıkla üst ve alt olarak adlandırılır.

 Bir etki alanı sınıfı için bir üst öğe seçimi, kendi öğelerinin yaşam sürelerinin diğer öğelere nasıl bağlı olduğunu nasıl istediğinize bağlıdır. Bir ağacın bir düğümü silinirse, alt ağacı da genellikle silinir. Bağımsız varlığına sahip öğe sınıfları, bu nedenle doğrudan kök sınıfının altına katıştırılır.

 Genellikle, başka bir öğenin içindeki bir öğeyi görüntülediğinizde, bir sahip ilişkisini göstermek istersiniz. Bu durumda, en uygun üst sınıf kapsayıcının sınıfındır. Özel durum, bir kapsayıcı içinde gördüğünüz öğe gerçekte bağımsız bir öğeye yalnızca bir başvuru bağlantısıdır. Bu durumda, kapsayıcıyı silmek başvuruyu siler, ancak hedefini silmez.

 Bu konuda açıklanan DSL tanımı desenlerinde, kapsayıcı silindiğinde bir kapsayıcı içinde görüntülenen öğelerin silineceğini varsayacağız. Daha karmaşık şemalar mümkündür ve kurallar tanımlayarak elde edilebilir.

|Öğe nasıl görüntülenir|Parent (katıştırma) sınıfı|DSL çözüm şablonunda örnek|
|-|-|-|
|Diyagramda şekil.<br /><br /> Kulvar.|DSL kök sınıfı.|En az dil.<br /><br /> Görev akışı: aktör sınıfı.|
|Kulvardaki şekil.|Kulvarlar olarak görüntülenen öğelerin alan sınıfı.|Görev akışı: görev sınıfı.|
|Şekildeki öğe, kapsayıcı silinirse öğenin silindiği öğe.<br /><br /> Şeklin kenarındaki bağlantı noktası.|Kapsayıcı şekline eşlenen alan sınıfı.|Sınıf diyagramı: öznitelik sınıfı.<br /><br /> Bileşen diyagramı: bağlantı noktası sınıfı.|
|Kapsayıcı silinirse, listedeki öğe silinmez.|DSL kök sınıfı.<br /><br /> Listede başvuru bağlantıları görüntülenir.||
|Doğrudan gösterilmiyor.|Bölüm oluşturan sınıf.||

 Müzik kitaplığı örneğinde, albümler, şarkıların başlıklarının listelendiği dikdörtgenler olarak görüntülenir. Bu nedenle, albümün üst öğesi kök sınıf Music, şarkının üst öğesi ise albümdür.

 Aynı anda bir etki alanı sınıfı ve ekleme oluşturmak için, **katıştırma ilişkisi** aracına tıklayın, ardından üst sınıfa tıklayın ve ardından diyagramın boş bir kısmına tıklayın.

 Genellikle, sınıf adlarını otomatik olarak izleyecağından, ekleme ilişkisinin ve rollerinin adının ayarlanması genellikle gerekli değildir.

 Daha fazla bilgi için bkz. etki alanı rollerinin [özellikleri](../modeling/properties-of-domain-relationships.md) ve [etki alanı rollerinin özellikleri](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> Ekleme, devralma ile aynı değildir. Bir katıştırma ilişkisindeki alt öğeler, üst öğelerinden Özellikler devralınmaz.

### <a name="add-domain-properties-to-each-domain-class"></a>Her etki alanı sınıfına etki alanı özellikleri ekleyin
 Etki alanı özellikleri mağaza değerleri. Örnekler: ad, başlık, Yayın tarihi.

 Sınıfında **etki alanı özellikleri** ' ne tıklayın, ENTER tuşuna basın ve ardından bir özelliğin adını yazın. Bir etki alanı özelliğinin varsayılan türü dizedir. Türü değiştirmek istiyorsanız, etki alanı özelliğini seçin ve **Özellikler** penceresinde **türü** ayarlayın. İstediğiniz tür açılan listede değilse, bkz. [özellik türleri ekleme](#addTypes).

 **Öğe adı özelliği ayarlayın.** Dil Gezgini 'nde öğeleri tanımlamak için kullanılabilecek bir etki alanı özelliği seçin. Örneğin, Song etki alanı sınıfında başlık alanı özelliğini seçebilirsiniz. **Özellikler** penceresinde, **öğe adı** ' nı olarak ayarlayın `true` .

### <a name="create-derived-domain-classes"></a>Türetilmiş etki alanı sınıfları oluşturma
 Bir etki alanı sınıfının özelliklerini ve ilişkilerini devralan çeşitleri olmasını istiyorsanız, bundan türetilmiş sınıflar oluşturun. Örneğin, albüm, WMA ve MP3 türetilmiş sınıflarına sahip olabilir.

 **Alan sınıfı** aracını kullanarak türetilmiş sınıfı oluşturun.

 **Devralma** aracına tıklayın, türetilmiş sınıfa tıklayın ve ardından temel sınıfa tıklayın.

 Taban sınıfın **Devralma değiştiricisini** **soyut** olarak ayarlamayı düşünün. Temel sınıfın örneklerine ihtiyacınız olabileceğini düşünüyorsanız, bunun yerine ayrı bir türetilmiş sınıf oluşturmayı düşünün.

 Türetilmiş sınıflar, temel sınıflarının özelliklerini ve rollerini devralınır.

### <a name="tidy-the-dsl-definition-diagram"></a>Kady DSL tanımı diyagramı
 İlişki eklediğinizde bazı sınıflarınız birden fazla yerde görünür. Görünüm sayısını azaltmak ve diyagramı daha geniş hale getirmek için bir ilişkinin hedef sınıfına sağ tıklayın ve ardından **ağacı buraya getir**' e tıklayın. Ters efekt için bir ilişkinin hedef sınıfına sağ tıklayın ve **ağacı Böl**' e tıklayın. Bu menü komutlarını görmüyorsanız, yalnızca etki alanı sınıfının seçildiğinden emin olun.

 Etki alanı sınıflarını ve şekil sınıflarını taşımak için CTRL + yukarı ve CTRL + aşağı tuşlarını kullanın.

### <a name="test-the-domain-classes"></a>Etki alanı sınıflarını test etme

##### <a name="to-test-the-new-domain-classes"></a>Yeni etki alanı sınıflarını test etmek için

1. DSL Tasarımcısı kodu oluşturmak için Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür ' e tıklayın** . Bu adımı otomatik hale getirebilirsiniz. Daha fazla bilgi için bkz. [tüm şablonları dönüştürmeyi otomatikleştirme](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. **DSL derleyin ve çalıştırın.** Visual Studio 'nun yeni bir örneğini deneysel modda çalıştırmak için F5 veya CTRL + F5 tuşlarına basın. Visual Studio 'nun deneysel örneğinde, DSL 'niz dosya adı uzantısına sahip bir dosya açın veya oluşturun.

3. **Gezginini açın.** Diyagramın yanında, genellikle *dil* Gezgini olarak adlandırılan dil Gezgini penceresi bulunur. Bu pencereyi görmüyorsanız, Çözüm Gezgini altındaki bir sekmede olabilir. Bunu bulamıyorsanız, **Görünüm** menüsünde **diğer pencereler**' in üzerine gelin ve ardından *dil* **Gezgini**' ne tıklayın.

     Gezgin, modelin ağaç görünümünü sunar.

4. **Yeni öğeler oluşturun.** Üstteki kök düğüme sağ tıklayın ve ardından **Yeni**_YourClass_ Ekle ' ye tıklayın.

     Dil Gezgininde sınıfınızın yeni bir örneği görüntülenir.

5. Yeni örnekler oluştururken her örneğin farklı bir ada sahip olduğunu doğrulayın. Bu, yalnızca bir etki alanı özelliğinde **, öğe adı** bayrağını ayarladıysanız oluşur.

6. **Etki alanı özelliklerini inceleyin. Sınıfınızın bir örneği seçiliyken** Özellikler penceresi inceleyin. Bu etki alanı sınıfında tanımladığınız etki alanı özelliklerini göstermelidir.

7. **Dosyayı kaydedin, kapatın ve yeniden açın**. Düğümleri genişlettikten sonra oluşturduğunuz tüm örneklerin gezgin 'de görünür olması gerekir.

## <a name="defining-shapes-on-the-diagram"></a><a name="shapes"></a> Diyagramdaki şekilleri tanımlama
 Diyagramda dikdörtgen, üç nokta veya simge olarak görünen öğelerin sınıflarını tanımlayabilirsiniz.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Diyagramda şekil olarak görünen öğelerin bir sınıfını tanımlamak için

1. Etki alanı [sınıflarını tanımlama](#classes) **bölümünde açıklandığı gibi bir etki alanı sınıfını tanımlayın ve test** edin **.**  

   - Sınıfın üst öğesi kök sınıf olmalıdır. Diğer bir deyişle, kök sınıf ve yeni etki alanı sınıfı arasında bir katıştırma ilişkisi olmalıdır.

   - Diyagramınızın kulvarları varsa, üst öğe bir kulvara eşlenmiş etki alanı sınıfı olabilir. Bu yordama devam etmeden önce, [kulvarlar içeren BIR DSL tanımlama](#swimlanes)bölümüne bakın.

2. Model diyagramındaki öğeleri temsil eden **bir şekil sınıfı ekleyin** . Aşağıdaki araçlardan birinden DSL tanımı diyagramına sürükleyin:

   - **Geometri şekli** bir dikdörtgen veya elips sağlar.

   - **Resim şekli** , sağladığınız bir görüntüyü görüntüler.

   - **Bölme şekli** bir veya daha fazla öğe listesi içeren bir dikdörtgendir.

     Şekil ve bağlayıcılar altında, DSL tanımı diyagramının sağ tarafında görünecek olan Shape sınıfını yeniden adlandırın.

3. **Bir resim şekli oluşturduysanız bir görüntü tanımlayın**.

   1. Herhangi bir boyutta bir görüntü dosyası oluşturun. BMP, JPEG, GIF ve EMF biçimleri desteklenir.

   2. Çözüm Gezgini, dosyayı Dsl\resourcesaltında çözüme ekleyin.

   3. DSL tanımı diyagramına dönün ve yeni görüntü şekli sınıfını seçin.

   4. Özellikler penceresi **resim** özelliğine tıklayın.

   5. **Görüntü Seç** Iletişim kutusunda **dosya adı**' nın altındaki açılan menüye tıklayın ve görüntüyü seçin.

4. **Etki alanı özelliklerini göstermek için şekle metin Dekoratörleri ekleyin.**

    Model öğesinin adını veya başlığını göstermek için muhtemelen en az bir metin dekoratörü gerekir.

    Şekil sınıfının üstbilgisine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **metin dekoratörü**' ne tıklayın. Dekoratörün adını ayarlayın ve Özellikler penceresi **konumunu** ayarlayın.

5. **Her şekli bir diyagram öğesi eşlemesi görüntülenecek olan etki alanı sınıfına bağlayın**.

    **Diyagram öğesi eşleme** aracına tıklayın, ardından etki alanı sınıfına ve ardından şekil sınıfına tıklayın.

6. **Özellikleri metin Dekoratörleri ile eşleyin.**

   1. Alan sınıfı ve diyagram öğe eşlemesini temsil eden şekil sınıfı arasındaki gri çizgiyi seçin.

   2. **DSL ayrıntıları** penceresinde **dekoratör haritaları** sekmesine tıklayın. **DSL ayrıntıları** penceresini görmüyorsanız, **Görünüm** menüsünde **diğer pencereler** ' in üzerine gelin ve **DSL ayrıntıları**' na tıklayın. Tüm içeriğini görmek için bu pencerenin en üstünü yükseltmek sık sık gereklidir.

   3. Bir dekoratörün adını seçin. **Display özelliği** altında, Domain sınıfının bir özelliğinin adını seçin. Her dekoratör için bunu tekrarlayın.

       İlişkili bir öğenin bir özelliğini göstermek istiyorsanız, **özelliği görüntüle**' nin altındaki açılır ağaç Gezgininde tıklayın.

   4. Her dekoratör adının yanında bir onay işaretinin göründüğünden emin olun.

      ![Şekil eşlemeleri ve DSL ayrıntıları penceresi](../modeling/media/dsldetailswindow.png)

7. **Alan sınıfının öğelerini oluşturmak için bir araç kutusu öğesi oluşturun.**

   1. **DSL Gezgini**' nde, **Düzenleyici** düğümünü ve tüm alt düğümlerini genişletin.

   2. DSL ile aynı ada sahip **araç kutusu sekmeleri** altındaki düğüme sağ tıklayın, örneğin, MusicLibrary. **Öğe Ekle aracı**' na tıklayın.

       > [!NOTE]
       > **Araçlar** düğümüne sağ tıklarsanız, **öğe Ekle aracını** görmezsiniz. Bunun yerine, yukarıdaki düğüme tıklayın.

   3. Yeni öğe aracı seçiliyken Özellikler penceresi, **sınıfı** en son eklediğiniz etki alanı sınıfına ayarlayın.

   4. **Açıklamalı altyazı** ve **araç ipucu** ayarlayın.

   5. **Araç kutusu simgesini** araç kutusunda görünecek bir simgeye ayarlayın. Bunu yeni bir simge veya başka bir araç için zaten kullanılan bir simge olarak ayarlayabilirsiniz.

        Yeni bir simge oluşturmak için, **Çözüm Gezgini**'de Dsl\Resources dosyasını açın. Varolan öğe aracı BMP dosyalarından birini kopyalayıp yapıştırın. Yapıştırılan kopyayı yeniden adlandırın ve ardından düzenlemek için çift tıklayın.

        DSL tanımı diyagramına dönün, aracı seçin ve Özellikler penceresi **araç kutusu simgesinde** **[...]** simgesine tıklayın. **Bit eşlem Seç** iletişim kutusunda, açılır menüden .BMP dosyanızı seçin.

   Daha fazla bilgi için bkz. [görüntü şekillerinin](../modeling/properties-of-image-shapes.md) [geometri şekillerinin](../modeling/properties-of-geometry-shapes.md) ve özelliklerinin özellikleri.

#### <a name="to-test-shapes"></a>Şekilleri test etmek için

1. DSL Tasarımcısı kodu oluşturmak için Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür ' e tıklayın** .

2. **DSL derleyin ve çalıştırın.** Visual Studio 'nun yeni bir örneğini deneysel modda çalıştırmak için F5 veya CTRL + F5 tuşlarına basın. Visual Studio 'nun deneysel örneğinde, DSL 'niz dosya adı uzantısına sahip bir dosya açın veya oluşturun.

3. **Araç kutusunda öğe araçlarının göründüğünü doğrulayın.**

4. Bir araçtan model diyagramına sürükleyerek **şekiller oluşturun** .

5. **Her metin dekoratın göründüğünü** ve şunları doğrulayın:

   1. Etki alanı özelliğinde **Kullanıcı arabirimi salt okuma** bayrağını ayarlamadığınız takdirde düzenleyebilirsiniz.

   2. Özelliği Özellikler penceresi veya dekoratör içinde düzenlediğinizde, diğer görünüm güncellenir.

   Bir şekli ilk kez test ettikten sonra bazı özelliklerini ayarlamak ve daha gelişmiş özellikler eklemek isteyebilirsiniz. Daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-reference-relationships"></a><a name="references"></a> Başvuru Ilişkileri tanımlama
 Herhangi bir kaynak etki alanı sınıfı ve herhangi bir hedef etki alanı sınıfı arasında bir başvuru ilişkisi tanımlayabilirsiniz. Başvuru ilişkileri genellikle diyagramda, şekiller arasında çizgiler olan bağlayıcılar olarak görüntülenir.

 Örneğin, müzik albümleri ve sanatçılar diyagramınızda şekil olarak görüntüleniyorsa, sanatçıları üzerinde çalıştıkları Albümler 'e bağlayan Artistsappearedonalbümler adlı bir ilişki tanımlayabilirsiniz. Şekildeki örneğe bakın.

 ![Oluşturulan DSL örnek modeli](../modeling/media/music_instance.png)

 Başvuru ilişkileri aynı türdeki öğeleri de bağlanabilir. Örneğin, bir aile ağacını temsil eden bir DSL 'de, üst ve alt öğeleri arasındaki ilişki kişiden kişiye bir başvuru ilişkisidir.

### <a name="define-a-reference-relationship"></a>Başvuru Ilişkisi tanımlama
 Başvuru Ilişkisi aracına tıklayın, sonra ilişkinin kaynak etki alanı sınıfına ve ardından hedef etki alanı sınıfına tıklayın. Hedef sınıf, kaynak sınıfla aynı olabilir.

 Her ilişkide, ilişki kutusunun her tarafındaki satırla temsil edilen iki rol bulunur. Her bir rolü seçebilir ve Özellikler penceresi özelliklerini ayarlayabilirsiniz.

 **Rolleri yeniden adlandırmayı düşünün**. Örneğin, kişi ve kişi arasındaki bir ilişkide, varsayılan adları üst ve alt öğeler, müdür ve astları, öğretmen ve öğrenci, vb. olarak değiştirmek isteyebilirsiniz.

 Gerekirse **Her rolün çeşitlilimlerini ayarlayın**. Her kişinin en fazla bir yöneticiye sahip olmasını istiyorsanız, diyagramdaki yönetici etiketinin altında görüntülenen çoğulluğu 0.. 1 olarak ayarlayın.

 **İlişkiye etki alanı özellikleri ekleyin.** Şekilde, Artist-Album ilişkisinde rolün bir özelliği vardır.

 Aynı sınıfa ait birden fazla bağlantı, aynı model öğesi çifti arasında mevcutsa **Ilişkinin yinelemelerini Izin verir özelliğini ayarlayın** . Örneğin, öğretmende aynı öğrenciye birden fazla konu öğretin.

 ![Bağlayıcılar için şekil haritaları](../modeling/media/music_connector.png)

 Daha fazla bilgi için bkz. etki alanı rollerinin [özellikleri](../modeling/properties-of-domain-relationships.md) ve [etki alanı rollerinin özellikleri](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Ilişkiyi göstermek için bir bağlayıcı tanımlayın
 Bir bağlayıcı, model diyagramındaki iki şekil arasında bir çizgi görüntüler.

 **Bağlayıcı** aracını DSL tanımı diyagramına sürükleyin.

 Bağlayıcıdaki etiketleri göstermek istiyorsanız metin Dekoratörleri ekleyin. Konumlarını ayarlayın. Kullanıcının bir metin dekoratörü taşımasına izin vermek için, **taşınamayacak** özelliğini ayarlayın.

 Bağlayıcıyı başvuru ilişkisine bağlamak için **Diyagram öğe eşleme** aracını kullanın.

 Diyagram öğesi eşlemesi seçiliyken, **DSL ayrıntıları** penceresini açın ve **dekoratör haritaları** sekmesini açın.

 Her bir **dekoratörü** seçin ve **Display özelliğini** doğru etki alanı özelliğine ayarlayın.

 **Dekoratörler** listesindeki her bir öğenin yanında bir onay işaretinin göründüğünden emin olun.

### <a name="define-a-connection-builder-tool"></a>Bağlantı Oluşturucu aracı tanımlama
 **DSL Gezgini** penceresinde, **Düzenleyici** düğümünü ve tüm alt düğümlerini genişletin.

 DSL ile aynı ada sahip düğüme sağ tıklayın ve ardından **Yeni bağlantı aracı ekle**' ye tıklayın.

 Yeni araç seçiliyken Özellikler penceresi:

- **Resim yazısını** ve **araç ipucunu** ayarlayın.

- **Bağlantı Oluşturucu** ' ya tıklayın ve yeni ilişki için uygun oluşturucuyu seçin.

- Araç **kutusu simgesini** araç kutusunda görünmesini istediğiniz simgeye ayarlayın. Bunu yeni bir simge veya başka bir araç için zaten kullanılan bir simge olarak ayarlayabilirsiniz.

     Yeni bir simge oluşturmak için, **Çözüm Gezgini**'de Dsl\Resources dosyasını açın. Varolan öğe aracı BMP dosyalarından birini kopyalayıp yapıştırın. Yapıştırılan kopyayı yeniden adlandırın ve ardından düzenlemek için çift tıklayın.

     DSL tanımı diyagramına dönün, aracı seçin ve Özellikler penceresi **araç kutusu simgesinde** **[...]** simgesine tıklayın. **Bit eşlem Seç** iletişim kutusunda, açılır menüden .BMP dosyanızı seçin.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Başvuru Ilişkisini ve bağlayıcıyı test etmek için

1. DSL Tasarımcısı kodu oluşturmak için Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür ' e tıklayın** .

2. **DSL derleyin ve çalıştırın.** Deneysel modda yeni bir örnek çalıştırmak için F5 veya CTRL+F5 Visual Studio tuşlarına basın. Visual Studio örneğinde DSL'nizin dosya adı uzantısına sahip bir dosya açın veya oluşturun.

3. **Bağlantı aracının araç kutusunda görüntülendiğinden emin olun.**

4. **Bir araçtan** model diyagramına sürükleyerek şekiller oluşturun.

5. **Şekiller arasında** bağlantılar oluşturun. Bağlayıcı aracına tıklayın, bir şekle tıklayın ve ardından başka bir şekle tıklayın.

6. **Uygunsuz sınıflar arasında bağlantı oluşturamayışınızı doğrulayın.** Örneğin, İkizler ve Ressamlar arasındaki ilişkiniz varsa, Artists'ı Artists'a bağlayamayabilirsiniz.

7. **Çoklulıkların doğru olduğunu doğrulayın. Örneğin, bir Kişiyi birden fazla yöneticiye bağlayamayamazken doğrulayın.**

8. **Her metin dekoratörün görüntülendiğinden ve şunları** doğrulayın:

   1. Etki alanı özelliğinde Kullanıcı Arabirimi Salt Okunur **bayrağını ayarlamadıysanız** düzenleyebilirsiniz.

   2. Özelliği Özellikler penceresi veya dekoratörde düzenlerken diğer görünüm güncelleştirilir.

   Bir bağlayıcıyı ilk kez test ettikten sonra, bazı özelliklerini ayarlamak ve daha gelişmiş özellikler eklemek iyi olabilir. Daha fazla bilgi için, [bkz. Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-shapes-that-contain-lists-compartment-shapes"></a><a name="compartments"></a> Listeleri Içeren Şekilleri Tanımlama: Bölme Şekilleri
 Bölme şekli bir veya daha fazla öğe listesi içerir. Örneğin, bir Müzik Kitaplığı DSL'sinde müzikLenas'ı temsil etmek için bölme şekillerini kullanabilirsiniz. Her Bir Müzikte Bir Şarkı Listesi Yer Alıyor.

 ![Bölme Şekli](../modeling/media/compartmentshape.png)

 DSL tanımında bu etkiyi elde etmek için en basit yöntemde, kapsayıcı için bir etki alanı sınıfı ve her liste için bir etki alanı sınıfı tanımlarsiniz. Kapsayıcı sınıfı bölme şekliyle eşlenmiş.

 ![Şekil haritası](../modeling/media/music_mapcomp.png)

 Daha fazla bilgi için [bkz. Bölme Şekillerinin Özellikleri.](../modeling/properties-of-compartment-shapes.md)

#### <a name="to-define-a-compartment-shape"></a>Bölme Şekli tanımlamak için

1. **Kapsayıcı etki alanı sınıfını oluşturun.** Ekleme **İlişkisi aracına** tıklayın, modelin kök sınıfına tıklayın ve ardından DSL tanım diyagramının boş bir parçasına tıklayın. Bu, örnek şekilde Yer Alan adlı etki alanı sınıfını oluşturur.

     Alternatif olarak, kapsayıcıyı kök sınıfa eklemek yerine kullana eşlenmiş bir etki alanı sınıfına katıştırabilirsiniz.

     Sınıfa Name gibi bir etki alanı özelliği ekleyin ve sınıfa **Is Element Name** bayrağını Özellikler penceresi.

2. **Liste öğesi etki alanı sınıfını oluşturun.** Ekleme **İlişkisi aracına tıklayın,** kapsayıcı sınıfına (Katıştırma) tıklayın ve ardından diyagramın boş bir parçasına tıklayın. Bu, örnek şekilde Song adlı etki alanı sınıfını oluşturur.

     Sınıfına Title gibi bir etki alanı özelliği ekleyin ve Is **Element Name bayrağını** ayarlayın.

     Diğer etki alanı özelliklerini ekleyin.

     Görüntülemek istediğiniz her liste için başka bir liste öğesi etki alanı sınıfı ekleyin.

3. **listesinde çeşitli öğe türlerini karıştırmak için,** liste sınıfından devralınan sınıflar oluşturun. Devralma Değiştiricisini ayarerek liste **sınıfını soyut hale ekleyin.**

     Örneğin klasik müziklerin ressam yerine müzik oluşturucuya göre sıralandırılmalarını tercih ediyorsanız, KlasikSong ve NonClassicalSong adlı iki alt sınıf oluşturabilirsiniz.

4. **Bölme şeklini oluşturun.** Bölme Şekli **aracından** DSL tanım diyagramına sürükleyin.

     Bir metin dekoratörü ekleyin ve adını ayarlayın.

     Bölme ekleyin ve adını ayarlayın.

5. Kullanıcının liste bölmelerini gizlemesine izin için bölme şekil sınıfına sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından **Genişlet/Dekoratör'e tıklayın.** Bu Özellikler penceresi dekoratörün konumunu ayarlayın.

6. Diyagram Öğesi **Eşleme aracına** tıklayın, kapsayıcı etki alanı sınıfına tıklayın ve bölme şekline tıklayın.

7. Etki alanı sınıfı ile şekil arasındaki diyagram öğesi eşleme bağlantısını seçin. DSL **Ayrıntıları penceresinde:**

    1. **Dekoratörler sekmesine** tıklayın. Dekoratör adına tıklayın ve ardından Özelliği Görüntüle altında uygun **öğeyi seçin.** Dekoratör adının yanında bir onay işareti göründüğünden emin olun.

    2. Bölme Haritaları **sekmesine** tıklayın.

         Bölmenin adına tıklayın.

         Görüntülenen **öğeler koleksiyon yolu altında** liste öğesi sınıfına (Song) gidin. Gezgin aracını kullanmak için açılan oka tıklayın.

         Özelliği **Görüntüle** altında, listede görüntülenecek özelliği seçin. Örnekte bu Başlık'dır.

> [!NOTE]
> Dekoratör Eşlemesi ve Bölme eşleme alanlarındaki Yol alanlarını kullanarak, etki alanı sınıfları ve bölme şekli arasında daha karmaşık ilişkiler kurulur.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Şekli oluşturmak için bir araç tanımlamak için

1. **Etki alanı sınıfının öğelerini oluşturmak için bir araç kutusu öğesi oluşturma.**

2. **DSL Gezgini'nde** Düzenleyici **düğümünü** ve tüm alt düğümlerini genişletin.

3. DSL'niz ile **aynı adı (örneğin** MusicLibrary) sahip Araç Kutusu Sekmeleri'nin altındaki düğüme sağ tıklayın. Öğe **Aracı Ekle'ye tıklayın.**

    > [!NOTE]
    > Araçlar düğümüne sağ **tıklarsanız** Öğe Aracı **Ekle'yi görmezsiniz.** Bunun yerine, üzerindeki düğüme tıklayın.

4. Yeni Özellikler penceresi aracı seçiliyken, Sınıf'a **yakın** zamanda eklemiş olduğunu etki alanı sınıfı olarak ayarlayın.

5. Resim **Yazısı ve** Araç **İpucu'nı ayarlayın.**

6. Araç **Kutusu Simgesi'ne** araç kutusunda görünecek bir simge ayarlayın. Bunu yeni bir simgeye veya başka bir araç için zaten kullanılan bir simgeye ayarlayın.

     Yeni bir simge oluşturmak için Dsl\Resources'i **Çözüm Gezgini.** Dosyalarda mevcut öğe araçlarından birini kopyalayıp .BMP yapıştırın. Yapıştıran kopyayı yeniden adlandırın ve düzenlemek için çift tıklayın.

     DSL Tanımı diyagramına geri dönüp aracı seçin ve araç çubuğunda araç Özellikler penceresi **simgesine tıklayın .** Bit **Eşlem** Seç iletişim kutusunda, açılan menüden BMP dosyanızı seçin.

#### <a name="to-test-a-compartment-shape"></a>Bölme şeklini test etmek için

1. **DSL tasarımcısı kodunu oluşturmak için** Çözüm Gezgini araç çubuğunda Tüm Şablonları Dönüştür'e tıklayın.

2. **DSL'i derleme ve çalıştırma.** Deneysel modda yeni bir örnek çalıştırmak için F5 veya CTRL+F5 Visual Studio tuşlarına basın. Visual Studio örneğinde DSL'nizin dosya adı uzantısına sahip bir dosya açın veya oluşturun.

3. **Aracın araç kutusunda görüntülendiğinden emin olmak.**

4. Aracı model diyagramına sürükleyin. Bir şekil oluşturulur.

    Öğenin adının görüntülendiğinden ve otomatik olarak varsayılan değere ayarlendiğinden emin olur.

5. Yeni şeklin üst bilgisine sağ tıklayın ve ardından Liste Öğenizi *Ekle'ye tıklayın.* Örnekte, komutu Şarkı Ekle'dir.

    Bir öğenin listede görüntülendiğinden ve yeni bir ada sahip olduğunu doğrulayın.

6. Liste öğelerine tıklayın ve ardından Özellikler penceresi. Liste öğelerinin özelliklerini görüyor gerekir.

7. Dil Gezgini'ni açın. İçinde liste öğesi düğümleri bulunan kapsayıcı düğümlerini gördüğünüzden emin olmak.

   ![DSL'nin oluşturulan gezgini](../modeling/media/music_explorer.png)

   Bölme şeklini ilk kez test ettikten sonra, bazı özelliklerini ayarlamak ve daha gelişmiş özellikler eklemek iyi olabilir. Daha fazla bilgi için, [bkz. Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Bir Bölmede Başvuru Bağlantısını Görüntüleme
 Genellikle bölmede görüntülene bir öğe, bölme şekliyle temsil edilen öğenin alt öğesidir. Ancak bazen buna bir başvuru ilişkisiyle bağlı olan bir öğeyi görüntülemek de istebilirsiniz.

 Örneğin, YerŞekser'e bağlı Olan Ressamların listesini görüntüleyen ikinci bir bölme ekleyebilirsiniz.

 Bu durumda bölme, başvurulan öğe yerine bağlantıyı görüntülemeli. Bunun nedeni, kullanıcı bölmedeki öğeyi seçer ve DELETE tuşuna bassa, bağlantının başvurulan öğeyi değil, silinmesini istemenizdir.

 Bununla birlikte, başvurulan öğenin adının bölmede görünmesini sebilirsiniz.

 Aşağıdaki yordamda, bu bölümün önceki kısımlarında açıklandığı gibi etki alanı sınıfını, başvuru ilişkisini, bölme şeklini ve diyagram öğesi haritasını önceden oluşturduğunuz varsayıldı.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Bir bölmede başvuru bağlantısını görüntülemek için

1. **Bölme şekline bir bölme ekleyin**. DSL tanımı diyagramında bölme şekli sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve **bölme**' ya tıklayın.

2. **Görüntülenecek Öğeler koleksiyon yolunu** , hedef öğesi yerine bağlantısına gitmek için ayarlayın. Açılan menüye tıklayın ve ağaç görünümünü kullanarak, hedefi yerine başvuru ilişkisini seçin. Örnekte, ilişki **Artistappearedonalbümler**' dir.

3. Hedef öğeye olan bağlantıdan gezinmek için **görüntülenecek özelliğin yolunu** ayarlayın. Örnekte, bu **sanatçı**' dır.

4. **Display özelliğini** , örneğin **Name** gibi Target öğesinin uygun özelliğine ayarlayın.

5. **Tüm şablonları dönüştürün**, DSL oluşturup çalıştırın ve bir test modeli açın.

6. Model diyagramında uygun şekil sınıflarını oluşturun, adlarını ayarlayın ve aralarında bir bağlantı oluşturun. Bölme şeklinin içinde, bağlantılı öğelerin adları görünmelidir.

7. Bağlantı ya da bölme şeklindeki öğeyi seçin. Hem bağlantı hem de öğe kaybolmalıdır.

## <a name="defining-ports-on-the-boundary-of-another-shape"></a><a name="ports"></a> Başka bir şeklin sınırında bağlantı noktalarını tanımlama
 Bağlantı noktası, başka bir şeklin sınırında bulunan bir şekildir.

 Bağlantı noktaları, başka bir şekle, kullanıcının bağlayıcılar çizebileceği bir sabit bağlantı noktası sağlamak için de kullanılabilir. Bu durumda, bağlantı noktası şeklini saydam hale getirebilirsiniz.

 Bağlantı noktalarını kullanan bir örneği görmek için yeni bir DSL çözümü oluştururken **bileşen diyagramı** şablonunu seçin. Bu örnek, bağlantı noktalarını tanımlarken göz önünde bulundurmanız gereken ana noktaları gösterir:

- Bağlantı noktalarının kapsayıcısını temsil eden bir etki alanı sınıfı vardır `Component` .

- Bağlantı noktalarını temsil eden bir etki alanı sınıfı vardır. Örnekte, bu `ComponentPort` .

- Kapsayıcı etki alanı sınıfından bağlantı noktası etki alanı sınıfına bir katıştırma ilişkisi vardır. Daha fazla bilgi için bkz. [etki alanı sınıfları tanımlama](#classes).

- Farklı bağlantı noktası türlerinin aynı kapsayıcıda karışık olmasını istiyorsanız, bağlantı noktası etki alanı sınıfının alt sınıflarını oluşturabilirsiniz. Örnekte, ve ' `InPort` `OutPort` den devralma `ComponentPort` .

- Kapsayıcı etki alanı sınıfı herhangi bir şekil türüne eşlenebilir. Örnekte, `ComponentShape` . Daha fazla bilgi için bkz. [şekilleri tanımlama](#shapes).

- Bağlantı noktası etki alanı sınıfları bağlantı noktası şekillerine eşlenir. Türetilmiş sınıfları, bağlantı noktası şekil sınıflarını ayrı ayrı eşleyebilirsiniz veya temel sınıfı bir bağlantı noktası şekil sınıfına eşleyebilirsiniz.

  Diğer bir durumda, bağlantı noktası şekilleri [şekilleri tanımlama](#shapes)bölümünde açıklandığı gibi davranır.

  Daha fazla bilgi için bkz. [bağlantı noktası şekillerinin özellikleri](../modeling/properties-of-port-shapes.md).

## <a name="defining-a-dsl-that-has-swimlanes"></a><a name="swimlanes"></a> Kulvarları olan bir DSL tanımlama
 Kulvarlar bir diyagramın yatay veya dikey bölümüdür. Her kulvar bir model öğesine karşılık gelir. DSL tanımınız, kulvar öğeleri için bir etki alanı sınıfı gerektirir.

 Kulvarlar ile DSL oluşturmanın en iyi yolu, yeni bir DSL çözümü oluşturmak ve görev akışı çözüm şablonunu kullanmaktır. DSL tanımında aktör sınıfı, kulvara eşlenen etki alanı sınıfıdır. Bu ve diğer sınıfları projenize uyacak şekilde yeniden adlandırın.

 Kulvar içinde şekil olarak görüntülenecek bir sınıf eklemek için, kulvar sınıfı ve yeni sınıfınız arasında bir katıştırma Ilişkisi oluşturun. Kullanıcılar öğeleri bir kulvardan diğerine sürükleyebilir, ancak her öğe her zaman belirli bir Kulvar içinde yer alacak. Görev akışı çözüm şablonunda, FlowElement, kulvar sınıfının bir alt öğesidir.

 Kulvarlardan bağımsız olarak bir şekil olarak görüntülenecek bir sınıf eklemek için, kök sınıf ve yeni sınıfınız arasında bir katıştırma Ilişkisi oluşturun. Kullanıcılar bu şekilleri diyagram üzerinde herhangi bir yere yerleştirebilir, kulvarların sınırları ve kulvarların dışında yer alır. Görev akışı çözüm şablonunda, açıklama kök sınıfının bir alt öğesidir.

 Daha fazla bilgi için bkz. [kulvarların özellikleri](../modeling/properties-of-swimlanes.md).

## <a name="adding-property-types"></a><a name="addTypes"></a> Özellik türleri ekleme

### <a name="domain-enumerations-and-literals"></a>Etki alanı numaralandırmaları ve sabit değerleri
 Etki alanı numaralandırması, birden çok değişmez değer içeren bir türdür.

 Bir etki alanı numaralandırması eklemek için, **DSL Gezgininde** modelin köküne sağ tıklayın ve ardından **yeni etki alanı numaralandırması Ekle**' ye tıklayın. Öğesi, **etki alanı türleri** düğümünün altında **DSL Gezgini** 'nde görünür. Bu öğe diyagramda görünmüyor.

 Etki alanı numaralandırmasında sabit listesi sabit değerleri eklemek için **DSL Gezgininde** etki alanı numaralandırması ' ne sağ tıklayın ve ardından **Yeni sabit listesi sabit değeri Ekle**' ye tıklayın.

 Varsayılan olarak, bir numaralandırma türüne sahip bir özellik, bir kerede numaralandırmanın yalnızca bir değerine ayarlanabilir. Kullanıcıların ve programcıların herhangi bir değer birleşimini ayarlayabilmesini istiyorsanız-bir "bit alanı"-numaralandırmanın **IsFlags** özelliğini ayarlayın.

### <a name="external-types"></a>Dış türler
 Bir etki alanı özelliğinin türünü ayarladığınızda, **tür** açılır listesinde istediğiniz türü bulamazsanız, bir dış tür ekleyebilirsiniz. Örneğin, **System. Drawing. Color** türünü listeye ekleyebilirsiniz.

 Bir tür eklemek için, DSL Gezgini ' nde modelin köküne sağ tıklayın ve sonra **yeni dış tür Ekle**' ye tıklayın. Özellikler penceresi, adı **Color** ve ad alanı olarak **System. Drawing** olarak ayarlayın. Bu tür artık DSL Gezgini 'nde **etki alanı türleri** altında görüntülenir. Bir etki alanı özelliğinin türünü her ayarladığınızda bunu seçebilirsiniz.

## <a name="customizing-the-dsl"></a><a name="custom"></a> DSL 'yi özelleştirme
 Bu konuda açıklanan teknikleri kullanarak, bir diagrammatik gösterimi, okunabilir bir XML formu ve kod ve diğer yapıtları oluşturmak için gereken temel araçları kullanarak hızlı bir şekilde DSL oluşturabilirsiniz.

 DSL tanımını genişletmenin iki yöntemi vardır:

1. DSL tanımının daha fazla özelliğini kullanarak DSL 'yi hassas olarak ayarlayın. Örneğin, birden çok bağlayıcı türü oluşturabileceğiniz tek bir bağlayıcı aracı oluşturabilirsiniz ve bir öğenin silinmesi ile ilgili öğeleri de sildiği kuralları kontrol edebilirsiniz. Bu teknikler, genellikle DSL tanımındaki değerler ayarlanarak elde edilir ve bazıları bazı program kodu satırları gerektirir.

     Daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Daha gelişmiş etkiler elde etmek için program kodunu kullanarak modelleme araçlarınızı genişletin. Örneğin, modeli değiştirecek menü komutları oluşturabilir ve iki veya daha fazla DSLs 'yi tümleştiren araçlar oluşturabilirsiniz. VMSDK, uzantılarınızı DSL tanımından oluşturulan kodla tümleştirmeyi kolaylaştırmak için özel olarak tasarlanmıştır.  Daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirmek Için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>DSL tanımını değiştirme
 Bir DSL tanımında herhangi bir öğe oluşturduğunuzda, çoğu varsayılan değer otomatik olarak ayarlanır. Ayarlandıklarında, bunları değiştirebilirsiniz. Bu, bir DSL geliştirmeyi basitleştirir, ancak yine de güçlü özelleştirmeler sağlar.

 Örneğin, bir şekli bir öğesiyle eşleştirdiğinizde, eşlemenin üst öğe yolu, etki alanı sınıfının katıştırma ilişkisine göre otomatik olarak ayarlanır. Ancak, daha sonra ekleme ilişkisini değiştirirseniz, üst öğe yolu otomatik olarak değiştirilmez.

 Bu nedenle, DSL tanımınızdaki bazı ilişkileri değiştirdiğiniz zaman, tanımı kaydettiğinizde ya da tüm şablonları dönüştürdüğünüzde hatalar için olağandışı değildir. Bu hataların çoğunun düzeltilmesi kolay bir işlemdir. Hatanın konumunu görmek için hata raporuna çift tıklayın.

 Ayrıca bkz. [nasıl yapılır: Domain-Specific dilin ad alanını değiştirme](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="troubleshooting"></a><a name="trouble"></a> Sorunu
 Aşağıdaki tabloda, bir DSL tasarlarken karşılaşılan en yaygın sorunların bazıları, çözümüne yönelik önerilerle birlikte listelenmiştir. [Görselleştirme araçları genişletilebilirlik forumundan](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx)daha fazla öneri bulabilirsiniz.

| Sorun | Öneri |
|-|-|
| DSL tanımı dosyasında yaptığım değişikliklerin etkisi yoktur. | Çözüm Gezgini yukarıdaki araç çubuğundan **Tüm Şablonları Dönüştür** ' e tıklayın ve ardından çözümü yeniden derleyin. |
| Şekiller, özellik değeri yerine bir dekoratörün adını gösterir. | Dekoratör eşlemesini ayarlayın. DSL tanımı diyagramında, alan sınıfı ve şekil sınıfı arasındaki gri çizgi olan diyagram öğe haritasına tıklayın.<br /><br /> **DSL ayrıntıları** penceresini açın. Bunu göremiyorsanız, Görünüm menüsünde **diğer pencereler**' in üzerine gelin ve **DSL ayrıntıları**' na tıklayın.<br /><br /> **Dekoratör haritaları** sekmesine tıklayın. Dekoratör adını seçin. Yanındaki kutunun işaretli olduğundan emin olun. **Görüntü özelliği** altında, bir etki alanı özelliğinin adını seçin.<br /><br /> Daha fazla bilgi için bkz. [diyagramdaki şekiller](#shapes). |
| DSL Gezgini 'nde bir koleksiyona ekleyemiyorum. Örneğin, araçlara sağ tıkladığınızda menüdeki "araç ekle" komutu yoktur.<br /><br /> DSL için Gezgininde bir listeye öğe ekleyemiyorum. | Denediğiniz düğümün üstündeki öğeye sağ tıklayın. Bir listeye eklemek istediğinizde, Add komutu liste düğümünde değil, kendi sahibidir. |
| Bir etki alanı sınıfı oluşturdum, ancak dil Gezgini 'nde örnek oluşturamıyorum. | Kök hariç her etki alanı sınıfı, bir katıştırma ilişkisinin hedefi olmalıdır. |
| DSL için Gezgininde öğeler yalnızca tür adlarıyla gösterilir. | DSL tanımında, sınıfının bir etki alanı özelliğini seçin ve Özellikler penceresi, **öğe adı** ' nı true ' olarak ayarlayın. |
| DSL her zaman XML düzenleyicisinde açılır. | Dosya okunurken bir hata nedeniyle bu durum oluşabilir. Ancak, bu hatayı düzelttikten sonra bile düzenleyiciyi DSL tasarımcısı olarak açıkça sıfırlamanız gerekir.<br /><br /> Proje öğesine sağ tıklayın, **birlikte Aç** ' a tıklayın ve * YourLanguage ***Tasarımcı (varsayılan)** seçeneğini belirleyin. |
| Derleme adlarını değiştirdikten sonra DSL 'nin araç kutusu görünmüyor. | İnceleme ve güncelleştirme **DslPackage\GeneratedCode\Package.tt** daha fazla bilgi için bkz. [nasıl yapılır: Domain-Specific dilin ad alanını değiştirme](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md). |
| DSL araç kutusu görünmüyor, ancak derleme adını değiştirdim.<br /><br /> Ya da bir uzantı yükleme başarısızlığını bildiren bir ileti kutusu görüntülenir. | Deneysel örneği sıfırlayın ve çözümünüzü yeniden derleyin.<br /><br /> 1. Windows Başlat menüsünde, **tüm programlar**' ın altında, Araçlar ' ı genişletin [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] ve ardından **Microsoft Visual Studio deneysel örneği Sıfırla**' ya tıklayın. <br />2. **Yapı** menüsünde **çözümü yeniden derle**' ye tıklayın. |

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dillerle Çalışmaya Başlama](../modeling/getting-started-with-domain-specific-languages.md)
- [Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [WPF Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md)
