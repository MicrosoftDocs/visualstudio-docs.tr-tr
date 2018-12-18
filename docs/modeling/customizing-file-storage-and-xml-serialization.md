---
title: Dosya Depolamayı ve XML Serileştirmeyi Özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8a21067eab6e55f3fb031e57fa2257b0d40a7eb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886467"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Dosya Depolama ve XML Serileştirmeyi Özelleştirme

Kullanıcı bir örneği kaydettiğinde veya *modeli*, bir etki alanına özgü dili (DSL) Visual Studio, bir XML dosyası oluşturulduğunda veya güncelleştirildiğinde. Store modelde yeniden oluşturmak için dosya yeniden yüklenebilir.

Ayarlar altında ayarlayarak, serileştirme düzenini özelleştirebilirsiniz **Xml serileştirme davranışı** DSL Gezgini içinde. Bir düğüm altında **Xml serileştirme davranışı** her etki alanı sınıfı, özellik ve ilişki. İlişkiler, kendi kaynak sınıfları altında yer alır. Düğüm şekli, bağlayıcı ve diyagram sınıfları karşılık gelen vardır.

Ayrıca, daha gelişmiş özelleştirme için program kodu yazabilirsiniz.

> [!NOTE]
> Modelin belirli bir biçimde kaydetmek istediğiniz, ancak bu formdan yeniden gerekmez modelinden özel serileştirme düzeni yerine çıktı üretmek için metin şablonlarını kullanmayı düşünün. Daha fazla bilgi için [bir etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Model ve diyagram dosyaları

Her model, genellikle iki dosyalarında kaydedilir:

-   Model dosyası gibi bir ada sahip **Model1.mydsl**. Bu model öğeleri ve ilişkileri ve özellikleri depolar. Dosya uzantısı gibi **.mydsl** tarafından belirlenen **FileExtension** özelliği **Düzenleyicisi** DSL tanımındaki düğümü.

-   Diyagram dosyası gibi bir ada sahip **Model1.mydsl.diagram**. Bunu, şekiller, bağlayıcılar ve konumlarını, renkleri, kalınlıklarda çizgi ve diğer diyagram görünümünü ayrıntılarını depolar. Kullanıcı silerse bir **.diagram** dosyası, ilişkin temel bilgileri modelinde değil kayıp. Diyagramın düzenini kaybolur. Model dosya açıldığında, şekiller bir varsayılan değer ve bağlayıcılar oluşturulur.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Bir DSL dosya uzantısını değiştirmek için

1.  DSL tanımını açın. DSL Gezgini içinde Düzenleyici düğüme tıklayın.

2.  Özellikler penceresinde Düzenle **FileExtension** özelliği. İlk içermez "." dosya adı uzantısı.

3.  Çözüm Gezgini içinde iki öğe şablonu dosyaları adını değiştirmek **DslPackage\ProjectItemTemplates**. Bu dosyalar, şu biçimi takip adlara sahiptir:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Varsayılan serileştirme düzeni

Bu konu için örnek oluşturmak için aşağıdaki DSL tanımı kullanıldı.

![DSL tanım diyagramı &#45; ailesi ağaç modeli](../modeling/media/familyt_person.png)

Bu DSL aşağıdaki görünüm ekranında sahip bir model oluşturmak için kullanıldı.

![Aile ağaç görünümünü, araç ve Gezgini](../modeling/media/familyt_instance.png)

Bu model başarıyla kaydedildi ve daha sonra yeniden XML metin Düzenleyicisi'nde açılır:

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

Serileştirilmiş modeli hakkında aşağıdaki noktalara dikkat edin:

-   İlk harfi küçük harf olması dışında her XML düğümü bir etki alanı sınıfı adıyla aynı olan bir adı vardır. Örneğin, `familyTreeModel` ve `person`.

-   Etki alanı özellikleri adı ve BirthYear gibi XML düğümüyle öznitelikler olarak serileştirilir. Yeniden özellik adının ilk karakteri küçük harfe dönüştürülür.

-   Her ilişki için ilişkinin kaynak sonu içinde iç içe geçmiş bir XML düğümü olarak serileştirilir. Düğüm, Kaynak rolü özelliği, ancak bir küçük harf ilk karakter ile aynı ada sahip.

     Örneğin, DSL tanımındaki, adında bir rolü **kişiler** adresindeki kaynaklanan **FamilyTree** sınıfı.  XML'de, bu adlı bir düğüm tarafından temsil edilen `people` içinde iç içe geçmiş `familyTreeModel` düğümü.

-   Her bir gömme ilişkisi hedef sonuna ilişki altında iç içe geçmiş bir düğüm olarak seri hale getirilir. Örneğin, `people` düğümü içeren birkaç `person` düğümleri.

-   Her başvuru ilişkisi hedef sonu olarak serileştirilmiş bir *ad*, hedef öğeye başvuru kodlar.

     Örneğin, altında bir `person` düğümünü olabilir bir `children` ilişki. Bu düğüm, bilinen adlar gibi içerir:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Takma ad anlama

Adlar, model ve şema dosyalarını farklı kısımlarını arasında çapraz temsil etmek için kullanılır. Ayrıca kullanıldığına `.diagram` model dosyası düğümler başvurmak için dosya. Bilinen ad iki tür vardır:

-   *Kimliği adlar* teklif hedef öğenin GUİD'si. Örneğin:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

-   *Nitelikli adlar anahtar* hedef öğenin bilinen ad anahtarı adlı bir atanan etki alanı özellik değeri tarafından tanımlayın. Bilinen ad hedef öğenin bilinen ad öğesi ilişkileri ekleme ağacında üst öğesi tarafından önekidir.

     Aşağıdaki örnekler adlandırılmış şarkı sınıfı gömme ilişkisi bir etki alanına sahip albümü, adlandırılmış alan sınıfı DSL, var olan alınmıştır:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Tam anahtar adlar, hedef sınıfın kendisi için bir alan özelliği varsa kullanılacak seçeneği **olduğu bilinen ad anahtarı** ayarlanır `true` içinde **Xml serileştirme davranışı**. Örnekte, "Title", "Albümü" ve "Şarkı" etki alanı sınıfları adlı etki alanı özellikleri için bu seçeneği ayarlayın.

Tam anahtar takma ad kimliği adlar daha kolay okunuyor. Kişiler tarafından okunacak XML modeli dosyalarınızın düşündüğünüz anahtar nitelenmiş adlar kullanmayı düşünün. Ancak, aynı ad anahtarı için birden fazla öğe ayarlanacak kullanıcı için mümkündür. Yinelenen anahtarlar dosyasının doğru şekilde yeniden değil neden olabilir. Bu nedenle, anahtar nitelenmiş adlar kullanarak başvurulan bir alan sınıfına tanımlarsanız, kullanıcı yinelenen adlar sahip bir dosyayı kaydetmelerini engelleyerek yolları göz önünde bulundurmalısınız.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Bir etki alanı sınıfı kimliği takma adlarıyla başvurulmak üzere ayarlamak için

1.  Emin olun **olduğu bilinen ad anahtarı** olduğu `false` sınıfı ve temel sınıfları, her etki alanı özelliği.

    1.  DSL Gezgini'nde **Xml serileştirme Behavior\Class verileri\\\<etki alanı sınıfı > \Element veri**.

    2.  Doğrulayın **olduğu bilinen ad anahtarı** olduğu `false` her etki alanı özelliği.

    3.  Etki alanı sınıfı, temel sınıf varsa, o sınıfta yordamı yineleyin.

2.  Ayarlama **serileştirmek kimliği**  =  `true` için etki alanı sınıfı.

     Bu özellik, altında bulunabilir **Xml serileştirme davranışı**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Bir etki alanı sınıfı, tam bir anahtar takma adlarıyla başvurulmak üzere ayarlamak için

-   Ayarlama **olduğu bilinen ad anahtarı** var olan bir etki alanı sınıfı, bir etki alanı özelliği. Özelliğin türü olmalıdır `string`.

    1.  DSL Gezgini'nde **Xml serileştirme Behavior\Class verileri\\\<etki alanı sınıfı > \Element veri**ve ardından etki alanı özelliği seçin.

    2.  Özellikler penceresinde ayarlayın **olduğu bilinen ad anahtarı** için `true`.

-   \- veya -

     Yeni bir etki alanı sınıfını kullanarak oluşturmak **adlı etki alanı sınıfı** aracı.

     Bu aracı adı bir etki alanı özelliğine sahip yeni bir sınıf oluşturur. **Öğe adı** ve **olduğu bilinen ad anahtarı** özellikleri bu etki alanı özelliğinin başlatıldığı `true`.

-   \- veya -

     Devralma ilişkisi etki alanı sınıfı, bir bilinen ad anahtarı özelliği olan başka bir sınıf oluşturun.

### <a name="avoid-duplicate-monikers"></a>Yinelenen adlar kaçının

Tam anahtar adlar kullanırsanız, bir kullanıcının modelinde iki öğe anahtar özelliği aynı değere sahip mümkündür. Örneğin, bir sınıf bir özellik adı olan bir kişi DSL'nizi varsa kullanıcı iki öğe adları aynı olacak şekilde ayarlayabilirsiniz. Model olabilmesine rağmen dosyasına kaydedildi, doğru bir şekilde yeniden değil.

Bu durumdan kaçınmak yardımcı çeşitli yöntemleri vardır:

-   Ayarlama **öğe adı**  =  `true` anahtar alan özelliğine yönelik. Etki alanı özelliği DSL tanım diyagramı seçin ve ardından Özellikler penceresinde ayarlarsınız.

     Kullanıcı sınıfının yeni bir örneğini oluşturduğunda, bu değeri alan özelliği, farklı bir değer otomatik olarak atanacak neden olur. Varsayılan davranış, sınıf adının sonuna bir sayı ekler. Bu kullanıcı için yinelenen bir adın değiştirmesini engellemez, ancak kullanıcı modeli kaydetmeden önce değer ayarlamaz olduğunda durumda yardımcı olur.

-   DSL doğrulamasını etkinleştirin. DSL Gezgini Editor\Validation seçin ve ayarlayın **kullanır...**  özelliklerine `true`.

     Belirsizlikler için denetleyen bir otomatik olarak oluşturulan bir doğrulama yöntemi yoktur. Yöntem `Load` doğrulama kategorisi. Bu, kullanıcı bu dosyayı tekrar açmanın mümkün olmayabileceğini uyarılır emin olur.

     Daha fazla bilgi için [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Bilinen ad yolları ve niteleyicileri

Tam bir anahtar adı, bilinen ad anahtarı ile sona erer ve katıştırma ağacında, üst öğesinin ad önüne. Örneğin, bilinen adı albümü, ise:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Ardından, albüm şarkıları biri olabilir:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Albümleri yerine kimliği tarafından başvurulan, ancak ardından adlar şu şekilde olacaktır:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Bir GUID benzersiz olduğundan, hiçbir zaman üst bilinen ad tarafından öneki, dikkat edin.

Belirli bir etki alanı özelliği her zaman bir model içinde benzersiz bir değere sahip olduğunu biliyorsanız, ayarlayabileceğiniz **bilinen ad niteleyicisi olduğundan** için `true` bu özellik için. Bu, üst öğenin bilinen adını kullanarak olmadan bir niteleyici kullanılacak neden olur. Örneğin, her ikisi de ayarlarsanız **bilinen ad niteleyicisi olduğundan** ve **olduğu bilinen ad anahtarı** için başlık domain özelliği albüm sınıfının modelin adına veya tanımlayıcısına bilinen Adlardaki niteleyiciyi albüm ve kendi katıştırılmış için kullanılmaz alt öğeleri:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>XML yapısını özelleştirme

Şu özelleştirmeleri yapmak için genişletin **Xml serileştirme davranışı** DSL Gezgininde. Altında bir etki alanı sınıfı, özellikler ve bu sınıfa kaynaklanan ilişkiler listesini görmek için öğe veri düğümünü genişletin. Bir ilişkiyi seçin ve Özellikler penceresinde seçeneklerini ayarlayın.

-   Ayarlama **atlamak öğesi** yalnızca hedef öğeleri listesi bırakarak Kaynak rolü düğümü atlamak için doğru şekilde. Kaynak ve hedef sınıflarını arasında birden fazla ilişki varsa bu seçeneği ayarlanmamalıdır.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

-   Ayarlama **kullanımı tam Form** hedef düğümleri ilişki örneklerini temsil eden düğümler eklemek için. Bir etki alanı ilişkisine etki alanı özellikleri eklediğinizde, bu seçenek otomatik olarak ayarlanır.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

-   Ayarlama **gösterimi** = **öğesi** yerine bir öğe olarak bir öznitelik değeri olarak kaydedilmiş bir etki alanı özelliğine sahip.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

-   , Öznitelikleri ve ilişkiler seri sırasını değiştirmek için öğe verileri altında bir öğeye sağ tıklayın ve kullanmak **Yukarı Taşı** veya **Aşağı Taşı** menü komutları.

## <a name="major-customization-using-program-code"></a>Program kodunu kullanarak temel özelleştirme

Bölümleri veya tümü serileştirme algoritmaları değiştirebilirsiniz.

Kod üzerinde çalışmanız önerilir **Dsl\Generated Code\Serializer.cs** ve **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Belirli bir sınıfın seri hale getirme özelleştirmek için

1.  Ayarlama **olan özel** düğümünde altında o sınıf için **Xml serileştirme davranışı**.

2.  Tüm Şablonları dönüştürme, çözümü derleyin ve sonuçta elde edilen derleme hataları araştırın. Neredeyse her hata açıklamaları, sağlamanız gereken hangi kod açıklanmaktadır.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Modelin tamamını için kendi serileştirme sağlamak için

1.  Dsl\GeneratedCode\SerializationHelper.cs yöntemleri geçersiz kıl

## <a name="options-in-xml-serialization-behavior"></a>Xml serileştirme davranışı seçenekleri

DSL Gezgini içinde bir alt düğüm her etki alanı sınıfı, ilişki, şekil, bağlayıcı ve diyagram sınıfı için Xml serileştirme davranışı düğüm içerir. Her düğümleri altında özellikler ve ilişkiler bu öğede kaynaklanan listesidir. İlişkiler, kendi sağ hem kendi kaynak sınıfları altında gösterilir.

Bu bölümde DSL tanımının ayarlayabilirsiniz seçenekler aşağıdaki tabloda özetlenmiştir. Her durumda, DSL Gezgini içinde bir öğe seçin ve Özellikler penceresinde seçeneklerini ayarlayın.

### <a name="xml-class-data"></a>XML sınıfı verileri

Bu öğeleri DSL Gezgini altında bulunan **Xml serileştirme Behavior\Class verileri**.

|||
|-|-|
|Özellik|Açıklama|
|Özel bir öğe şeması olup|TRUE ise alan sınıfında özel bir öğe şeması olup gösterir.|
|Özel|Bu ayar **True** , bu etki alanı sınıfı için serileştirme ve seri durumundan çıkarma kendi kodunuzu yazma istiyorsanız.<br /><br /> Çözümü derleyin ve ayrıntılı yönergeler bulmak için hataları inceleyin.|
|Etki alanı sınıfı|Bu sınıf veri düğümü geçerli olduğu etki alanı sınıfı. Salt okunur.|
|Öğe adı|Bu sınıfına ait öğelerin XML düğümü adı. Varsayılan değer, etki alanı sınıfı adı küçük harflerden sürümüdür.|
|Bilinen ad özniteliği adı|Başvuruyu içerecek bilinen ad öğelerinde kullanılan özniteliğin adı. Boş ise anahtar özelliğinin ve kimliğin adı kullanılır.<br /><br /> Bu örnekte, "name" verilmiştir:  `<personMoniker name="/Mike Nash"/>`|
|Bilinen ad öğesi adı|Başvurmak için bu sınıfın öğelerine ait bilinen adlar için kullanılan xml öğesinin adı.<br /><br /> Varsayılan değer "Moniker" ile ve sonra sınıf adı küçük bir sürümüdür. Örneğin: `personMoniker`|
|Bilinen ad tür adı|Bu sınıfın öğelerine ait bilinen adlar için oluşturulan xsd türünün adı. XSD bulunduğu **Dsl\Generated kod\\\*Schema.xsd**|
|Kimliği seri hale getirme|TRUE ise, ' % s'öğesi GUID'si dosyasına dahil edilir. Bu işaretlenmiş özelliği yok ise true **olduğu bilinen ad anahtarı** DSL bu sınıfa başvuru ilişkileri tanımlar.|
|Tür adı|Xsd belirtilen alan sınıfından oluşturulan xml türünün adı.|
|Notlar|Bu öğeyle ilişkili resmi olmayan Notlar|

### <a name="xml-property-data"></a>XML özellik verileri

XML özellik düğümleri sınıfı düğümleri altında bulunur.

|||
|-|-|
|Özellik|Açıklama|
|Etki alanı özelliği|Xml serileştirme yapılandırması verilerinin geçerli olduğu özellik. Salt okunur.|
|Bilinen ad anahtarı|TRUE ise özellik bu etki alanı sınıf örneklerini başvuru bilinen adlar oluşturmaya yönelik anahtar olarak kullanılır.|
|Bilinen ad niteleyicisi olduğundan|TRUE ise özellik bilinen Adlardaki niteleyiciyi niteleyici oluşturmak için kullanılır. False ise ve Serializeıd bu etki alanı sınıfı için doğru değilse, bilinen adlar katıştırma ağacında üst öğe bilinen adı tarafından yetkili olan.|
|Temsili|Attribute ise özellik bir xml özniteliği olarak serileştirilir Öğesi, eğer ise bir öğesi olarak; seri Ignore ise serileştirilmiş.|
|XML adı|Xml özniteliği veya özelliği temsil eden öğe için kullanılan ad. Varsayılan olarak, etki alanı özellik adı küçük bir sürümünü budur.|
|Notlar|Bu öğeyle ilişkili resmi olmayan Notlar|

### <a name="xml-role-data"></a>XML rol verileri

Rol veri düğümü, kaynak sınıfı düğümleri altında bulunur.

|Özellik|Açıklama|
|-|-|
|Özel bilinen adı var|Oluşturma ve bu ilişkinin çapraz takma ad çözümleme için kendi kodunuzu sağlamak istiyorsanız true olarak ayarlayın.<br /><br /> Ayrıntılı yönergeler için çözümü derleyin ve ardından hata iletileri çift tıklayın.|
|Etki alanı ilişkisi|Bu seçenekler uygulandığı ilişkiyi belirtir. Salt okunur.|
|Öğe atla|TRUE ise kaynak rolüne karşılık gelen XML düğümü şemadan çıkarılır.<br /><br /> Kaynak ve hedef sınıflarını arasında birden fazla ilişki varsa, bu rolü düğüm iki ilişkilerini ait bağlantılar ayırt eder. Bu nedenle, bu seçenek bu durumda ayarlamayın öneririz.|
|Rol öğe adı|Kaynak rolünden türetilen XML öğesinin adını belirtir. Rol özellik adı varsayılan değerdir.|
|Tam biçimini kullanın|TRUE ise, her bir hedef öğe veya bilinen ad, ilişkiyi temsil eden bir XML düğümünde içine alınır. Bu ilişki, kendi etki alanı özellikleri varsa true olarak ayarlanmalıdır.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)