---
title: Modelleri, Sınıfları ve İlişkileri Anlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 74172b6e7f03d7e3baef329f053fc4a83ee6ae28
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967395"
---
# <a name="understanding-models-classes-and-relationships"></a>Modelleri, Sınıfları ve İlişkileri Anlama
Bir etki alanına özgü dil (DSL) yazma herhangi bir özel program kodu ile birlikte, DSL tanımı dosyası tarafından tanımlanır. DSL çözüm program kodunda çoğu bu dosyadan oluşturulur.

 Bu konuda, DSL tanımını merkezi özellikleri açıklanmaktadır.

## <a name="the-dsl-definition"></a>DSL tanımı
 Açtığınızda `Dsl\DslDefinition.dsl`, Visual Studio penceresine aşağıdaki resme benzer.

 ![DSL Tasarımcısı](../modeling/media/dsl_designer.png)

 DSL tanım diyagramı DSL tanımındaki en önemli bilgileri görüntülenir. Ayrıca DslDefinition.dsl bir parçası olan ek bilgiler genellikle diyagram tarafında görünür DSL Gezgini görüntülenir. En sık kullanılan görevleri için diyagram ve daha gelişmiş özelleştirmeler DSL Gezgini ile çalışırsınız.

 DSL tanım diyagramı model öğelerini ve model öğeleri arasında bağlantılar tanımlayan ilişkileri tanımlayan etki alanı sınıflarını göstermektedir. Ayrıca, kullanıcıya model öğelerini göstermek için kullanılan bağlayıcılar ve şekiller de gösterir.

 ![DSL Tasarımcısı ile Kulvar](../modeling/media/dsl_desinger.png)

 DSL tanım diyagramı veya DSL Gezgini içinde bir öğe seçtiğinizde ilgili bilgileri Özellikler penceresinde görüntülenir. DSL Ayrıntıları penceresinde ek bilgiler görüntülenebilir.

### <a name="models-are-instances-of-dsls"></a>DSL örneklerini modelleridir
 A *modeli* DSL'nizi bir kullanıcı tarafından oluşturulan bir örneğidir. Bir modeli tanımladığınız etki alanı sınıfları ve örnekleri tanımladığınız etki alanı ilişkileri olan öğeler arasında bağlantılar örnekleri olan model öğelerini içerir. Bir model, şekiller ve bağlayıcıları, bir diyagram üzerinde model öğelerini ve bağlantılar görüntülemek de sahip olabilir. Şekil sınıfları, bağlayıcı sınıflar ve sınıf diyagramı DSL tanımını içerir.

 Bir DSL tanımı olarak da bilinir bir *etki alanı modeli*. Model etki alanına özgü dil çalışma zamanı örneğinin bilgileriyse bir DSL tanımını veya etki alanı modeli etki alanına özgü dil tasarım zamanı gösterimidir.

## <a name="domain-classes-define-model-elements"></a>Model öğelerini alan sınıfları tanımlama
 Etki alanı sınıfları etki alanında çeşitli öğeleri oluşturmak için kullanılır ve etki alanı ilişkileri olan öğeler arasında bağlantılardır. Öğeleri ve modellerini oluşturduklarında tasarım özgü dilin kullanıcılar tarafından oluşturulan bağlantıları tasarım zamanı gösterimi değildirler.

 Bu örnekte, Müzik Kitaplığı DSL kullanıcı tarafından oluşturulan bir model gösterilmiştir. Müzik albümleri şarkıya listesini içeren kutuları tarafından temsil edilir. Sanatçılar, yuvarlak köşeli kutuları tarafından temsil edilir ve katkıda buluna albümleri bağlanırsınız.

 ![Oluşturulan bir DSL örnek modeli](../modeling/media/music_instance.png)

 DSL tanımı iki boyutu ayırır. Görünüm modeli diyagramı üzerinde model öğelerinin şekli sınıfları ve bağlayıcı sınıfları kullanılarak tanımlanır. Etki alanı sınıflarını ve etki alanı ilişkileri kullanarak modele taşınan bilgiler tanımlanır.

 Aşağıdaki çizimde, Müzik Kitaplığı DSL tanımındaki alan sınıfları ve ilişkileri gösterir.

 ![Başvuru ekleme ve ilişkileri](../modeling/media/music_classes.png)

 Çizimde dört etki alanı sınıflarını göstermektedir: müzik, albüm, sanatçının ve şarkı. Etki alanı sınıf adı, başlık ve benzeri gibi etki alanı özellikleri tanımlayın. Örnek modelinde, bu özelliklerin bazıları değerlerini diyagramda görüntülenir.

 Etki alanı ilişkileri sınıflardır: MusicHasAlbums, MusicHasArtists AlbumbHasSongs ve ArtistAppearedOnAlbums. Çeşitlilikler 1..1 gibi ilişkilerine sahip 0.. *. Örneğin, her bir şarkıyı için tam olarak bir albüm AlbumHasSongs ilişkisi üzerinden ilişkili olmalıdır. Albümlerini şarkıya herhangi bir sayıda olabilir.

### <a name="rearranging-the-dsl-definition-diagram"></a>DSL tanım diyagramı yeniden düzenleme
 Albüm Bu resimde olduğu gibi bir alan sınıfına DSL tanım diyagramı üzerinde birkaç kez görünebilir dikkat edin. Her zaman bir ana görünüm yoktur ve olabilir bazı *başvuru* görünümleri.

 DSL tanım diyagramı yeniden düzenlemek için şunları yapabilirsiniz:

-   Ana takas ve görünümleri başvuru kullanarak **ağacı buraya getirin** ve **ağacı Böl** komutları. Bir tek etki alanı sınıfı, bu komutları görmek için sağ tıklayın.

-   Etki alanı sınıfları ve şekil sınıfları Ctrl + Yukarı Ok ve Ctrl + aşağı ok tuşlarına basarak yeniden sıralayabilir.

-   Daraltabilir veya her bir şeklin üst-sağ taraftaki simgesini kullanarak sınıfları genişletin.

-   Bir alan sınıfının altındaki eksi işareti (-) tıklayarak ağacı bölümlerini daraltın.

## <a name="inheritance"></a>Devralma
 Etki alanı sınıflar, devralma kullanılarak tanımlanabilir. Devralma türetme oluşturmak için devralma Aracı'nı tıklatın ve türetilen sınıfın temel sınıf'ye tıklayın. Bir model öğesini kendi etki alanı sınıfı, temel sınıftan devralınan tüm özelliklerle birlikte tanımlanan tüm özelliklerine sahiptir. Ayrıca, kendi ilişkileri rollerinde devralır.

 Devralma, ilişkiler, şekiller ve bağlayıcılar arasında kullanılabilir. Devralma, aynı Grup içerisinde tutmanız gerekir. Bir şekli alan sınıfından devralamaz.

## <a name="domain-relationships"></a>Etki alanı ilişkileri
 Model öğelerini ilişkileriyle bağlanabilir. Bağlantılar, her zaman ikili; Bunlar tam olarak iki öğe bağlayın. Ancak, herhangi bir öğe birçok bağlantı diğer nesnelere sahip olabilir ve ayrıca aynı bir öğe çiftinin arasında birden fazla bağlantı bile olabilir.

 Öğelerin farklı sınıflar yalnızca tanımlayabileceğiniz gibi farklı sınıflardaki bağlantıları tanımlayabilirsiniz. Bir bağlantının sınıfa bir *etki alanı ilişkisi*. Bir etki alanı ilişkisi öğesinin hangi sınıfların örneklerini belirtir. Her bir ilişki sonu olarak adlandırılan bir *rol*, etki alanı ilişkisi ilişki yanı sıra, iki rol için adları tanımlar.

 Etki alanı ilişkilerinin iki tür vardır: ilişkileri ve başvuru ilişkileri ekleme. DSL tanım diyagramı katıştırma ilişkileri düz çizgiler her rolün sahip ve başvuru ilişkileri satırları kesik çizgili.

### <a name="embedding-relationships"></a>İlişki ekleme
 Kendi kök dışında bir modeldeki her bir öğenin bir ekleme bağlantısı hedefidir. Bu nedenle, modelin tamamını bağlantılar ekleme, tek bir ağaç oluşturur. Gömme ilişkisi kapsama veya sahipliği temsil eder. Bu yolla ilişkili iki model olarak da bilinen üst ve alt öğeleridir. Alt, üst katıştırılmış bildirilir.

 Gömme bağlantılar genellikle açıkça bir diyagram üzerinde bağlayıcılar olarak gösterilmez. Bunun yerine, bunlar genellikle kapsama tarafından temsil edilir. Modelin köküne diyagram tarafından temsil edilir ve katıştırılmış öğeler diyagramdaki şekilleri olarak görüntülenir.

 Örnekte, müzik kök sınıfı için bir gömme AlbumHasSongs şarkı için olan albüm MusicHasAlbums gömme ilişkisi vardır. Şarkıya her albüm içinde bir listedeki öğeler olarak görüntülenir. Müzik örneklere da diyagramdaki şekilleri olarak görünür sanatçının sınıfına bir gömme MusicHasArtists de vardır.

 Ebeveynleri silindiğinde varsayılan olarak, katıştırılmış öğeleri otomatik olarak silinir.

 Bir model kaydedildiğinde serileştirme özelleştirmediyseniz XML biçiminde dosyasına katıştırılmış öğeleri ebeveynleri yerleştirilir.

> [!NOTE]
>  Gömme devralma ile aynı değil. Gömme ilişkisi, alt, üst öğenin özelliklerini devralmaz. Gömme model öğeleri arasında bağlantı türüdür. Devralma sınıfları arasındaki bir ilişkidir ve model öğeleri arasında bağlantılar oluşturmaz.

### <a name="embedding-rules"></a>Kuralları ekleme
 Her bir örnek modeli öğesinde modelin kökü dışında tam olarak bir gömme bağlantı hedefi olması gerekir.

 Bu nedenle, en az bir gömme ilişkisi hedef kök sınıfı hariç tüm soyut olmayan etki alanı sınıfı olmalıdır veya gömme bir taban sınıftan devralmalıdır. Bir sınıf iki veya daha fazla Gömmeleri hedefinin olabilir ancak kendi örnek model öğelerini bir kerede yalnızca bir üste sahip olabilir. Hedefin kaynağa çokluğu 0.. 1 veya 1..1 olmalıdır.

### <a name="the-explorer-displays-the-embedding-tree"></a>Gömme Ağaç Gezgini görüntüler
 DSL tanımınızı Ayrıca kendi modeli diyagramı yanı sıra kullanıcıların gördüğü bir Gezgin oluşturur.

 ![DSL, oluşturulan Gezgini](../modeling/media/music_explorer.png)

 Gezgini modeldeki olanlar şekilleri tanımlamadığınız tüm öğeleri gösterir. Öğeleri ve ilişkileri ekleme gösterir, ancak ilişkileri başvurusu değil.

 Bir öğenin etki alanı özelliklerinin değerlerini görmek için kullanıcı modeli diyagramı veya model Gezgini'nde bir öğe seçer ve Özellikler penceresi açılır. Diyagram üzerinde görüntülenmeyen olanlar gibi tüm etki alanı özellikleri gösterir. Örnekte, her şarkı hem bir başlık hem de bir türe sahiptir, ancak yalnızca başlık değeri diyagramda gösterilmiştir.

## <a name="reference-relationships"></a>Başvuru ilişkileri
 Başvuru ilişkisi herhangi bir türden değil gömme ilişkisi temsil eder.

 Başvuru ilişkilerini Bağlayıcılarla şekiller arasında bir diyagram üzerinde genellikle görüntülenir.

 Model XML gösterimini kullanarak bir referans bağlantı iki öğe arasındaki temsil edilen *takma adlar.* Diğer bir deyişle, bilinen adlar model içindeki her öğeyi benzersiz olarak tanımlayan adlarıdır. Her model öğe için XML düğümü ilişki adı ve diğer öğe bilinen adı belirten bir düğüm içeriyor.

## <a name="roles"></a>Rolleri
 Her etki alanı ilişkisi, iki rol, Kaynak rolü ve bir hedef rolü vardır.

 Aşağıdaki resimde, arasındaki çizgi **yayımcı** etki alanı sınıfı ve **PublisherCatalog** etki alanı ilişkisi kaynak roldür. Etki alanı ilişkisi arasındaki ve **albüm** etki alanı sınıfı, hedef rolü.

 ![Rolleri ve özellikleri.](../modeling/media/propertycode.png)

 Model trafiğiyle program kodu yazarken bir ilişki ile ilişkili adlarını özellikle önemlidir. Örneğin, DSL çözüm derlediğinizde, oluşturulan sınıfın yayımcı albümleri koleksiyonudur Kataloğu özellik vardır. ' % S'sınıfı albüm yayımcı sınıfın tek bir örneği yayımcı bir özelliğe sahiptir.

 Bir DSL tanımındaki bir ilişki oluşturduğunuzda, varsayılan değerleri özellik ve ilişki adlar verilir. Ancak, bunları değiştirebilirsiniz.

## <a name="multiplicities"></a>Çeşitlilikler
 Bir etki alanı ilişkisine kaç öğenin aynı role sahip olabilir Çeşitlilikler belirtin. Örnekte, sıfır çok (0..\*) çeşitlilik ayarı **Kataloğu** rol belirtir herhangi bir örneğine **yayımcı** etki alanı sınıfı kadar olabilir  **PublisherCatalog** ilişki vermek istediğiniz şekilde bağlar.

 Diyagram üzerine yazarak veya değiştirerek bir rolün çokluğu yapılandırma `Multiplicity` özelliğinde **özellikleri** penceresi. Aşağıdaki tabloda, bu özellik için ayarları açıklar.

|Çokluk türü|Açıklama|
|-|-|
|0.. * (sıfır-çok)|Etki alanı sınıfın her örneğini birden fazla ilişki veya ilişki örneği olabilir.|
|0..1 (bire sıfır)|Etki alanı sınıfın her örneğini birden fazla örneğini bir ilişki veya ilişki örneği olabilir.|
|1..1 (bir tane)|Her etki alanı sınıf örneği, bir ilişkinin örneğini olabilir. Rol sınıfın herhangi bir örneğinden Bu ilişkinin birden fazla örneğini oluşturamazsınız. Doğrulama etkinse, rol sınıfın örneklerini ilişki örneğine sahip olduğunda doğrulama hatası görünür.|
|1.. * (bire çok)|Bu çokluğuna sahip rolündeki sınıfın her örneğini birden fazla ilişkisi olabilir ve her örneğinin en az bir ilişkinin örneğini olmalıdır. Doğrulama etkinse, rol sınıfın örneklerini ilişki örneğine sahip olduğunda doğrulama hatası görünür.|

## <a name="domain-relationships-as-classes"></a>Sınıflar olarak etki alanı ilişkileri
 Bir bağlantı Store ModelElement türetilmiş bir sınıf olan LinkElement örneği olarak temsil edilir. Bu özellikler, etki alanı ilişkileri etki alanı modeli diyagramı tanımlayabilirsiniz.

 Bir ilişki, kaynak veya hedef diğer ilişki de yapabilirsiniz. Etki alanı modeli diyagramı alan ilişkisine sağ tıklayın ve ardından **sınıf olarak göster**. Ek sınıf kutusu görüntülenir. Ardından ona ilişkileri bağlanabilirsiniz.

 Alan sınıfları ile yapabildiğiniz gibi kısmen devralma yoluyla bir ilişki tanımlayabilirsiniz. Türetilmiş bir ilişki seçip ayarlayın **temel ilişkisinin** Özellikler penceresinde.

 Türetilmiş bir ilişki temel ilişkisini uzmanlaşmış. Bağlantılar nesnesinden türetilmesi BT'nin veya temel bir ilişkiyle bağlantılı sınıfları ile aynı etki alanı sınıfları. Bir modeldeki türetilen ilişkinin bir bağlantı oluşturulduğunda, türetilmiş ve temel ilişkilerden bir örneği var. Program kodunda temel veya türetilmiş sınıf tarafından oluşturulan özelliklerini kullanarak bağlantı sonuna ters gidebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
