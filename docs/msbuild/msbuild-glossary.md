---
title: MSBuild sözlüğü | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf51cbc4cd20401f17f5e92def47713c6107f3d2
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078761"
---
# <a name="msbuild-glossary"></a>MSBuild sözlüğü
Bu terimler Microsoft Build Engine (MSBuild) ve bileşenlerini açıklamak için kullanılır.  
  
## <a name="glossary"></a>Sözlük  
 AssemblyFoldersEx  
 Bir kayıt defteri yolları her başvuru derlemelerini bulmak için tasarım zamanı çözünürlüğü burada bakabilirsiniz destekledikleri framework sürümü için üçüncü taraf satıcılarından depoladığınız konumu.  
  
 toplu işleme  
 Toplu işleme anlamına gelir öğeleri olarak bilinen farklı kategorilere ayırma *toplu*öğe meta verileri ve bir hedef veya görevi bir kez her batch kullanarak çalıştırarak göre. MSBuild denk olan toplu işleme için--yapısı döngü. Daha fazla bilgi için [toplu işleme](../msbuild/msbuild-batching.md).  
  
 derleme kapsamı  
 Derleme kapsamı MSBuild nesneyi, potansiyel olarak görünür, bir proje ve birden çok proje yapı içinde oluşturulan tüm alt projeler için örneğin, bir genel özellikse, açıklar.  
  
 alt proje  
 Bkz: *proje, alt*.  
  
 Koşul  
 Birçok MSBuild öğeleri koşullu olarak tanımlanabilir; diğer bir deyişle, `Condition` özniteliği öğesinde görünür. Koşullu öğelerin içeriği, koşul olarak değerlendirilmedikçe yoksayılır `true`. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).  
  
 tanımı, öğesi  
 Bkz: *öğe tanımı*.  
  
 öğe yayma  
 Bir derleme yürütme aşamasında öğeleri oluşturulabilir veya alt görevleri tarafından değiştirilen `Output` olan öğeler `ItemName` özniteliği. Görev "Yeni öğeleri göstermek için" kabul edilir.  
  
 özellik yayma  
 Bir derleme yürütme aşamasında özellikler oluşturulabilir veya alt görevleri tarafından değiştirilen `Output` olan öğeler `PropertyName` özniteliği. Görev "yeni özellik yaymak için" kabul edilir.  
  
 Değerlendirme Aşaması  
 Değerlendirme, bir proje derlemesi ilk aşamasıdır. Tüm özellikleri ve öğeleri projede göründükleri sırayla değerlendirilir. İçeri aktarılan projeleri, projede karşılaştığından değerlendirilir. Değerlendirme sırasında yürütme aşamasında ve özellikleri veya yayma bildirmek veya musunuz öğeleri göz ardı edilir kadar hedefler ve görevler çalıştırılmaz.  
  
 yürütme aşaması  
 Yürütme, Proje yapı ikinci aşamasıdır. Seçilen hedefler oluşturulur ve görevleri çalıştırma. Özellikleri ve öğeleri oluşturan veya değiştiren değerlendirme değerlerine kıyasla.  
  
 işlevi, özelliği  
 Bkz: *özelliği işlevi*.  
  
 öğesi, işlevi  
 Item işlevi bakın.  
  
 öğe  
 Öğeler Yapı sistemine girdi ve öğe adlarına dayalı öğe türlerine gruplanır. Öğeleri genelde dosyaları temsil ederler. Öğeleri öğe türüne göre adlandırılır çünkü koşulları, ait oldukları *öğesi* ve *öğe değeri* birbirlerinin yerine kullanılabilir. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  
  
 öğesi tanımı  
 Öğe tanımı gruplarındaki herhangi bir öğesi türü için varsayılan meta veri ekleme öğesi tanımları içerir. İyi bilinen meta verileri gibi varsayılan meta veri belirtilen öğe türündeki tüm öğeleri ile ilişkilidir. Varsayılan meta veri açıkça bir öğe tanımında geçersiz kılınabilir. Daha fazla bilgi için [öğesi tanımları](../msbuild/item-definitions.md).  
  
 Item işlevi  
 Öğe işlevleri, projede öğeleri hakkında bilgi alın. Bu işlevler, başlangıç Distinct() öğeleri basitleştirin ve öğeler arasında döngü daha hızlıdır. Öğe yolları ve dizeleri işlemek için işlevi vardır. Daha fazla bilgi için [öğe işlevleri](../msbuild/item-functions.md)  
  
 öğe meta verileri  
 Bkz: *meta öğesi*.  
  
 Öğe türü  
 Öğe türleri parametre olarak görevleri için kullanılabilir öğe listeleri içeren adlandırılır. Görevler, derleme işleminin adımları gerçekleştirmek için öğe değerlerini kullanın. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  
  
 Meta veriler, öğesi  
 Öğe meta verileri bir öğeyle ilişkili ad-değer çiftleri koleksiyonu ' dir. Meta veri öğesi için açıklayıcı bilgiler sağlar ve iyi bilinen meta verileri dışında isteğe bağlıdır. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  
  
 iyi bilinen meta  
 İyi bilinen meta veriler, önceden tanımlanmış bir değer kullanılarak başlatılır salt okunur öğesi meta verilerdir. İyi bilinen meta verileri bir dosyaya başvuran bir öğe için açıklayıcı bilgileri sağlar. Örneğin, adlı iyi bilinen meta veri değeri `FullPath` başvurulan dosyasının tam yoludur. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  
  
 çoklu sürüm desteği  
 Birçok farklı CLR'nin ve MSBuild ve Visual Studio'dan çerçeveleri hedeflemek bir derleme veya uygulama projesi için yeteneği.  
  
 Profili  
 Framework'ün tamamını bir alt kümesi. Bu, bir makineye indirilmesi gereken miktarı en aza indirmek için kullanılır.  
  
 Proje dosyası  
 Bir proje dosyası denetleyen yapı MSBuild komut dosyası içerir. Proje dosyaları, genellikle ile biten bir dosya uzantısına sahip *proj*, gibi *.csproj* veya *.vbproj*. Proje dosyaları, özellik dosyaları ve hedef dosyalarını içe.  
  
 özellik  
 Yapı işlemini denetlemek için kullanılan bir anahtar-değer çifti özelliğidir. Daha fazla bilgi için [MSBuild özellikleri](../msbuild/msbuild-properties.md).  
  
 özellik, ortam  
 Ortam özelliği aynı ada sahip bir sistem ortam değişkeninin değeri için otomatik olarak başlatılmış olan bir özelliktir. Daha fazla bilgi için [MSBuild özellikleri](../msbuild/msbuild-properties.md).  
  
 özellik dosyası  
 Çoğunlukla özelliği grupları ve yapıya rehberlik öğesi gruplarını içeren bir proje dosyası bir özellik dosyasıdır. İsteğe bağlı olarak kural olarak, dosya uzantısına sahip *.props*. Özellik dosyaları genellikle ilişkili proje dosyalarını başlangıcında alınır.  
  
 özelliği, işlev  
 Bir özellik işlevi bir sistem özelliği veya MSBuild komut değerlendirmek için kullanılan yöntemi kullanılabilir. Özellik yöntemleri, sistem saatini okuyabilir, dizeleri karşılaştırmak, normal ifadeleri eşleştirebilir ve diğer eylemleri gerçekleştirmek için kullanılabilir. Daha fazla bilgi için [özellik işlevleri](../msbuild/property-functions.md).  
  
 iç içe özellik işlevi  
 Özellik işlevleri forma birleştirilebilir daha karmaşık işlevleri. Örneğin,  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 Daha fazla bilgi için [özellik işlevleri](../msbuild/property-functions.md).  
  
 özelliği, genel  
 Bir genel özellikse derleme işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Genel özellikleri kullanarak veya bir komut isteminde ayarlama `Properties` özniteliği bir [MSBuild görevi](../msbuild/msbuild-task.md)ve bir yapının değerlendirme aşamasında değiştirilemez. Daha fazla bilgi için [MSBuild özellikleri](../msbuild/msbuild-properties.md).  
  
 özelliği yerel  
 Yerel bir özellik derleme işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Bu terim, yalnızca bir genel özellikse olmayan bir özelliğe ayırt etmek için kullanılır.  
  
 özelliği, kayıt defteri  
 Bir kayıt defteri özelliği sistem kayıt defteri alt anahtarının değeri okuyan özel bir sözdizimi kullanılarak ayarlanan bir değere sahip. Daha fazla bilgi için [MSBuild özellikleri](../msbuild/msbuild-properties.md).  
  
 ayrılmış özelliği  
 Ayrılmış bir özellik derleme işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Ayrılmış özellikler için önceden tanımlanmış değerler otomatik olarak başlatılır. Daha fazla bilgi için [MSBuild özellikleri](../msbuild/msbuild-properties.md).  
  
 proje kapsamı  
 Proje kapsamı yalnızca içeren proje dosyası ve bunu içe aktaran tüm projeleri için görünür olan gibi yerel bir özellik, bir MSBuild nesne açıklar.  
  
 Proje, alt  
 Bir alt proje, Proje yapı sırasında MSBuild görevi tarafından oluşturulur. Bu yeni proje, projenin içeren veya MSBuild görevi içeren hedef alır bir alt öğesidir. Tarafından değiştirilmediği sürece alt projenin ana proje genel özelliklerini devralır `Properties` özniteliği.  
  
 yeniden dağıtılabilir dosya listesi  
 Yeniden dağıtım listesi: belirli bir çerçeve için karşılık gelen derleme listesi.  
  
 başvuru bütünleştirilmiş kodu  
 Tasarım zamanında bir uygulama oluşturmak için kullanılan derleme. Başvuru bütünleştirilmiş kodu özel arabirimler kendisinden kaldırıldı ve gerçek kod, yalnızca meta veri ve ortak arabirimler bırakarak sahip olabilir.  
  
 kayıt defteri özelliği  
 Bkz: *özelliği, kayıt defteri*.  
  
 Hedef  
 Bir hedef, görevler, belirli bir sıraya göre gruplandıran ve proje dosyasının bölümlerini derleme işlemine giriş noktaları olarak kullanıma sunar. Daha fazla bilgi için [hedefleri](../msbuild/msbuild-targets.md).  
  
 Hedef, yapı  
 Hedef, çalışan bakın.  
  
 Hedef, değerlendirme  
 Özellikler ve öğeler için olası değişiklikler için artımlı derleme nedeniyle hedefleri çözümlenmesi gerekir. Hedef atlandı olsa bile, bu değişikliklerin yapılması gerekir. Bir hedef değerlendirirken bu analizini gerçekleştirme ve bu değişiklikler yapmayı anlamına gelir. Daha fazla bilgi için [artımlı derlemeleri](../msbuild/incremental-builds.md).  
  
 Hedef, yürütme  
 Bir hedef yürütme, değerlendirme ve hiç koşul sahip olan veya, koşul true olarak değerlendirilen tüm görevleri yürütme anlamına gelir. Artımlı derleme sırasında hedef atlandı veya yürütülen, ancak bunlar her zaman değerlendirilir. Daha fazla bilgi için hedef, değerlendirme.  
  
 çalışan hedefi  
 False değerlendiren bir koşul sahip bir hedef, yani çalıştırılmaz, derleme üzerinde hiçbir etkisi olmaz. Hedefleri çalıştırın ya da çalıştırılan atlandı veya. Her iki durumda da, hedef olarak değerlendirilir. Daha fazla bilgi için hedef, değerlendirme.  
  
 Hedef, atlanıyor  
 Artımlı derleme belirlerse tüm çıktı dosyalarının güncel olduğundan daha sonra hedef atlandı, diğer bir deyişle, hedef değerlendirilir, ancak hedef içindeki görevlerin yürütülmez. Daha fazla bilgi için hedef, değerlendirme.  
  
 Hedef Çerçeve adı  
 Framework (gibi. tanımlayan bir ad NETFramework, Silverlight, vb.), sürüm ve hedeflemek istediğiniz profil (örneğin, istemci, sunucu, vb.).  
  
 targeting Pack  
 Belirli bir çerçeve ve bu çerçeve için başvuru bütünleştirilmiş kodları kümesi ile dağıtılmış bir derleme listesi.  
  
 Hedef dosya  
 Çoğunlukla hedefler ve yapıya rehberlik görevleri içeren bir proje dosyası hedefleri dosyasıdır. İsteğe bağlı olarak kural olarak, dosya uzantısına sahip *.targets*. Hedef dosyalar genellikle ilişkili proje dosyalarını sonunda içeri aktarılır.  
  
 görev  
 Görevleridir yürütülebilir koddur, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projeleri derleme işlemlerini gerçekleştirmek için kullanın. Örneğin, bir görev giriş dosyalarını derleyebilir ya da bir harici araç çalıştırabilir. Daha fazla bilgi için [görevleri](../msbuild/msbuild-tasks.md).  
  
 transform  
 Dönüşüm, başka bir öğe koleksiyonuna bire bir dönüştürmedir. Öğe koleksiyonlarını dönüştürmek bir proje etkinleştirmeye ek olarak, bir dönüştürme giriş ve çıkışlarını arasında doğrudan bir eşleme tanımlamak bir hedef sağlar. Daha fazla bilgi için [dönüştüren](../msbuild/msbuild-transforms.md).  
  
 iyi bilinen meta verileri  
 Bkz: *iyi bilinen meta*.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild](../msbuild/msbuild.md)