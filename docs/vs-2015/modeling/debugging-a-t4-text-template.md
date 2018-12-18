---
title: Bir T4 metin şablonuna ilişkin hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
ms.assetid: 0877fdf2-20bf-42da-b3cc-4c5856b80821
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f299b89f7f59cbfc043bb77e6e56c3e5fac22d16
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298915"
---
# <a name="debugging-a-t4-text-template"></a>Bir T4 Metin Şablonuna İlişkin Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonlarında kesme noktaları ayarlayabilirsiniz. Tasarım zamanı metin şablonunda hata ayıklama için metin şablonu dosyasını kaydedin ve ardından **T4 şablonunda Hata Ayıkla** Çözüm Gezgini içinde dosyanın kısayol menüsünde. Bir çalışma zamanı metin şablonunda hata ayıklama için yalnızca ait olduğu uygulama hata ayıklama.  
  
 Bir metin şablonunda hata ayıklama için şablonu dönüştürme süreci adımları anlamanız gerekir. Her bir adımın çeşitli hatalar oluşabilir. Adımlar aşağıdaki gibidir.  
  
|Adım|Tasarım zamanı şablonu: ne olur?|Çalışma zamanı şablon: ne olur?|  
|----------|--------------------------------------------|-----------------------------------------|  
|Metin şablonundan kod oluşturulur.<br /><br /> Hataları yönergelerinde, eşleşmeyen veya disordered `<#…#>` etiketler.|Olduğunda şablonu kaydetmek veya metin dönüştürmeyi çağırma.|Olduğunda şablonu kaydetmek veya metin dönüştürmeyi çağırma.|  
|Oluşturulan kod derlenir.<br /><br /> Şablon kodunuzda derleme hataları.|Hemen önceki adımdan sonra.|Uygulama kodunuzun yanı sıra.|  
|Kodu çalıştırır.<br /><br /> Şablon kodunuzdaki çalışma zamanı hataları.|Hemen önceki adımdan sonra.|Ne zaman uygulamanızı çalışır ve şablon kodunu çağırır.|  
  
 Çoğu durumda, şablon kodunun satır numaralarını hata raporunda verilir. Hata raporu geçici bir dosya adına başvuran eşleşmeyen köşeli ayraç içindeki metin şablonunun kod olağan sebep olur.  
  
 Metin şablonlarında kesme noktaları ayarlayabilir ve her zamanki gibi hata ayıklama.  
  
## <a name="common-errors-and-fixes"></a>Yaygın hatalar ve düzeltmeler  
 Aşağıdaki tabloda, en sık karşılaşılan hataların ve bunların düzeltmeleri listelenmektedir.  
  
|Hata İletisi|Açıklama|Çözüm|  
|-------------------|-----------------|--------------|  
|Temel sınıfı yüklenemedi{0}' sınıf hangi dönüştürme devralır.|Belirtilen temel sınıf bulamazsanız gerçekleşir `inherits` parametresinde bir şablon yönergesi. İleti şablonu yönergenin satır numarası sağlar.|Belirtilen sınıfın var ve var. Bu derlemeyi bir derleme yönergesinde belirtildiğinden emin olun.|  
|Çözümlenemedi dosya için metni ekleyin:{0}|Dahil edilen bir şablon bulamazsanız oluşur. İleti istenen içerme dosyasının adını sağlar.|Özgün şablon yolu göreli dosya yolu olduğunu veya dosyanın konağı ile kayıtlı bir konumda olduğunu ya da dosyanın tam yolunu olduğundan emin olun.|  
|Dönüştürme nesnesi başlatılırken hatalar oluşturuldu. Dönüştürme çalışmaz.|Dönüştürme sınıfı 'Initialize()' başarısız oldu veya false döndürdü gerçekleşir.|Belirtilen temel dönüştürme sınıfına Initialize() işlevdeki kod geldiği \<#@template#> yönerge ve yönerge işlemcilerine. Başlatma, büyük olasılıkla başarısız olmasına neden olan hata hata listede bulunuyor. Neden başarısız olduğun araştırın. Bir şablonu hata ayıklama yordamları izleyerek Initialize() için gerçek üretilen koda bakabilirsiniz.|  
|Derleme '{0}'for 'yönerge işlemcisi{1}' FullTrust izin kümesi verilmedi. Sadece güvenilir bütünleştirilmiş kodların yönerge işlemcileri sağlamanıza izin verilir. Bu yönerge işlemcisi yüklenmeyecek.|Sistem bir yönerge işlemcisini içeren derleme için FullTrust izinlerini verin değil oluşur. İleti, derlemenin adı ve yönerge işlemcisinin adını sağlar.|Yalnızca yerel makinede güvenilir derlemeler, kullandığınızdan emin olun.|  
|Yol '{0}' Bu bilgisayarda yerel veya güvenilen bölgenizin bir parçası olmalıdır.|Yerel makinenizde olmayan veya ağınızın Güvenilir Bölge bir dosya yönergeniz veya derleme yönergesi başvuruda bulunduğunda oluşur.|Yönergeniz veya derleme yönergeleri bulunduğu dizin, güvenilen bir bölgede olduğundan emin olun. Internet Explorer aracılığıyla güvenilen bölgenizin bir ağ dizinine ekleyebilirsiniz.|  
|"Geçersiz belirteç ' catch'" veya "bir ad alanı doğrudan üyeleri içeremez" gibi birden çok sözdizimi hataları|Şablon kodunuz içinde çok fazla kapatma küme. Derleyici, standart nesil koduyla kafa karıştırıcı olduğu.|Küme parantezleri ve köşeli ayraçlar içinde kod sınırlayıcılar kapatma sayısını denetleyin.|  
|Döngüler veya derlenmiş değil veya düzgün şekilde yürütmesi koşullular. Örneğin: `<#if (i>10)#> Number is: <#= i #>`<br /><br /> Bu kod, her zaman değerini çıkarır ediyorum. Yalnızca "sayıdır:" koşullu değil.|C# içinde her zaman küme ayraçları denetim deyimlerinde katıştırılmış metin blokları kapsamak için kullanın.|Küme ayracı Ekle: `<#if (i>10) { #>    Number is: <#= i #><# } #>`.|  
|"İfade çok karmaşık", bir tasarım zamanı şablonu işleme veya bir çalışma zamanı (önceden işlenmiş) şablonu derleniyor.<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir çalışma zamanı şablon tarafından oluşturulan kodu incelemek çalışırken çalışmayı durdurur.|Metin bloğu çok uzun. T4 metin blokları her bir şablon satır için bir dize içeren bir dize birleştirme ifadesi dönüştürür. Çok uzun metin blokları, derleyicinin boyut sınırları çağırdığınızdan.|Uzun metin bloğu gibi bir ifade bloğu ile bölmeniz:<br /><br /> `<#= "" #>`|  
  
## <a name="warning-descriptions-and-fixes"></a>Uyarı açıklaması ve düzeltme  
 Aşağıdaki tabloda, varsa en yaygın uyarılar düzeltmeleri birlikte listeler.  
  
|Uyarı iletisi|Açıklama|Çözüm|  
|---------------------|-----------------|--------------|  
|İçerme dosyası yüklenirken '{0}' null veya boş dize döndürdü.|Eklenen metin şablonuna boşsa gerçekleşir. İleti eklenen dosyanın dosya adı sağlar.|INCLUDE yönergesi kaldırın ya da bazı içerik dosyası olduğundan emin olun.|  
|Dönüştürme derleniyor:|Tüm hata veya uyarı dönüşümü derlediğinde derleyicinin kaynaklanan bu dizesine ekler. Bu dize, derleyici bir hata veya uyarı oluşturdu anlamına gelir.|DLL bulunurken bir sorun varsa, DLL GAC'de ise tam yolunu ya da tam tanımlayıcı adı sağlamanız gerekebilir.|  
|Parametre '{0}' yönergesinde zaten mevcut. Yinelenen parametre yoksayılacak.|Parametre birden çok kez bir yönergesinde belirtilen oluşur. İleti parametre ve satır numarası yönergesi adı sağlar.|Yinelenen parametre belirtimini kaldırın.|  
|İçerme dosyası yüklenirken hata oluştu '{0}'. Dahil et yönerge yoksayılacak.|Belirtilen bir dosya bulamadığında gerçekleşir bir `include` yönergesi. İletinin dosya ve satır numarası yönergesi adı sağlar.|Orijinal metin şablonu dosyasını aynı dizine veya bir konak üzerinde kayıtlı dizinleri dahil etme dosyasının var olduğundan emin olun.|  
|Dönüştürme sınıfı için geçersiz bir temel sınıf belirtildi. Temel sınıf Microsoft.VisualStudio.texttemplating.texttransformation ile türetilmelidir.|Gerçekleşir, `inherits` öğesinden devralmayan bir sınıf bir şablon yönergesi belirtir `TextTransformation`. İleti şablonu yönergenin satır numarası sağlar.|Türetilen bir sınıf belirtmek `TextTransformation`.|  
|'Şablon' yönergesinde geçersiz bir kültür belirtildi. Kültür, "xx-XX" biçiminde olmalıdır. Sabit kültür kullanılacak.|Şablon yönergesinde kültür parametresi hatalı belirtildiğinde gerçekleşir. İleti şablonu yönergenin satır numarası sağlar.|Kültür parametresi "xx-XX" biçiminde geçerli bir kültür değiştirin.|  
|Geçersiz hata ayıklama değeri '{0}' şablon yönergesinde belirtildi. Hata ayıklama değeri "true" veya "false" olmalıdır. Varsayılan "false" kullanılır.|Gerçekleşir, `debug` şablon yönergesinde parametresi yanlış belirtildi. İleti şablonu yönergenin satır numarası sağlar.|Hata ayıklama parametresi "true" veya "false" olarak ayarlayın.|  
|Geçersiz bir HostSpecific değeri '{0}' şablon yönergesinde belirtildi. HostSpecific değeri "true" veya "false" olmalıdır. Varsayılan "false" kullanılır.|Gerçekleşir, konağa özgü parametreyi bir `template` yönergesi yanlış belirtildi. İleti şablonu yönergenin satır numarası sağlar.|Ana bilgisayara özgü parametresi "true" veya "false" olarak ayarlayın.|  
|Geçersiz bir dil '{0}' 'şablon' yönergesinde belirtildi. Dil, "C#" veya "VB" olmalıdır. Varsayılan değer olan "C#" kullanılacak.|Desteklenmeyen bir dil belirtilen oluşur `template` yönergesi. Yalnızca "C#" veya "VB" izin verilir (büyük küçük harfe duyarlı). İleti şablonu yönergenin satır numarası sağlar.|Ayarlama `language` şablon yönergesinde "C#" veya "VB" parametresi.|  
|Şablonda birden çok çıktı yönergesi bulundu. İlki dışındaki tüm alanlar yoksayılır.|Gerçekleşir, birden çok `output` yönergeleri, şablon dosyasında belirtilir. İleti yinelenen çıktı yönergesinde satır sayısını sağlar.|Yineleneni Kaldır `output` yönergeleri.|  
|Şablonda birden çok şablon yönergesi bulundu. İlki dışındaki tüm alanlar yoksayılır. Şablon yönergesi için birden çok parametre, bir şablon yönergesi içinde belirtilmelidir.|Birden çok belirtirseniz gerçekleşir `template` içindeki bir metin şablonu dosyasını (dahil edilen dosyalar da dahil). İleti yinelenen şablon yönergesi satır sayısını sağlar.|Farklı toplama `template` yönergeleri tek `template` yönergesi.|  
|Adlı yönerge için işlemci belirtilmedi '{0}'. Yönerge yoksayılacak.|Belirtirseniz gerçekleşir bir `custom` yönergesi, ancak sağlamadığı bir `processor` özniteliği. Message yönergesi ve satır numarası adını sağlar.|Sağlayan bir `processor` adını taşıyan öznitelik `directive` işlemci yönergesi.|  
|Adlı bir işlemci '{0}'adlı yönerge için bulunamadı'{1}'. Yönerge yoksayılacak.|Sistem bulamıyor oluşur `directive` içerisinde belirtilen işlemci bir `custom` yönergesi. Message yönergesi adı, işlemci adı ve satır numarası yönergesi sağlar.|Ayarlama `processor` yönergesi adına yönerge işlemcisinin özniteliği.|  
|Gerekli parametre '{0}'for 'yönergesine{1}' bulunamadı. Yönerge yoksayılacak.|Sistem, gerekli bir yönerge parametre sağlamaz oluşur. Eksik parametre adı, yönerge adı ve satır numarası ileti sağlar.|Eksik parametre belirtin.|  
|Adlı İşlemci '{0}'adlı yönergeyi desteklemiyor'{1}'. Yönerge yoksayılacak.|Bir yönerge işlemcisi bir yönergeyi desteklemiyor oluşur. İleti adı yönerge işlemcisinin yanı sıra sorunlu yönergesi adı ve satır sayısını sağlar.|Yönergenin adı düzeltin.|  
|Dosyasının içerme yönergesi '{0}' sonsuz bir döngüye neden olur.|Döngüsel yönergelerinde görüntülenir belirtilen (örneğin, dosya bir dosya içerir B, dosya içerir).|Döngüsel belirtmeyin yönergeleri içerir.|  
|Dönüştürme çalıştırılıyor:|Tüm hatalar veya dönüştürme çalıştırılırken üretilen uyarılar için bu dize ekler.|Yok.|  
|Bir blok içinde beklenmeyen başlangıç veya bitiş etiketi bulundu. Bir başlangıç veya bitiş etiketini yanlış yazmadınız ve şablonda iç içe geçmiş bir bloğu yok emin olun.|Beklenmeyen bir olduğunda görüntülenen \<# veya #>. Diğer bir deyişle, varsa bir \<# değil kapatılmış olan başka bir açık etiketinden sonra veya sahip bir #> önceki kapatılmamış bir açma etiketi yok olduğunda. İleti eşleşmeyen etiketi satır sayısını sağlar.|Eşleşmeyen başlangıç veya bitiş etiketi kaldırmak veya kaçış karakterini kullanın.|  
|Bir yönerge yanlış biçimde belirtildi. Yönerge yoksayılacak. Lütfen yönerge biçiminde belirtin `<#@ name [parametername="parametervalue"]*  #>`|Bir yönerge doğru biçimde belirtilmemiş ayrıştırıcı tarafından görüntülenir. İletinin hatalı yönergenin satır numarası sağlar.|Tüm yönergeleri biçiminde olduğundan emin olun `<#@ name [parametername="parametervalue"]*  #>`. Daha fazla bilgi için [T4 metin şablonu yönergeleri](../modeling/t4-text-template-directives.md).|  
|Bütünleştirilmiş kodu yüklenemedi '{0}'for 'kayıtlı yönerge işlemcisi{1}'<br /><br /> {2}|Bir yönerge işlemcisine ana bilgisayar tarafından yüklenemedi oluşur. Yönerge işlemcisini ve yönerge işlemcisinin adı için sağlanan derleme ileti tanımlar.|Yönerge işlemcisini doğru şekilde kaydedildiğini ve derleme var olduğundan emin olun.|  
|Türü bulunamadı '{0}'derlemesindeki'{1}'for 'kayıtlı yönerge işlemcisi{2}'<br /><br /> {3}|Bir yönerge işlemcisi türü olarak derlemesinden yüklenemedi oluşur. İleti türü, derleme ve yönerge işlemcisinin adını sağlar.|Vshost yönerge işlemcisi bilgileri (ad, derleme ve türü) kayıt defterinde bulur. Yönerge işlemcisini doğru şekilde kaydedildiğini ve türü derlemede var olduğundan emin olun.|  
|Derleme yüklenirken bir hata oluştu '{0}'|Bir derleme yüklenirken bir sorun olduğunda gerçekleşir. İleti, derlemenin adı sağlar.|İçinde yüklenen derlemeler belirlediğiniz \<@# assembly #> yönergeleri ve yönerge işlemcileri tarafından. Bu dize aşağıdaki hata iletisini derleme yük neden başarısız daha fazla veri sağlamanız gerekir.|  
|Bir sorun oluşturma ve başlatma adlı yönerge için işlemcinin oluştu '{1}'. İşlemci türü {0}. Yönerge yoksayılacak.|Sistem oluşturamadı veya bir yönerge işlemcisi başlatma gerçekleşir. Message yönergesi adı ve satır numarasını ve işlemci türü sağlar.|Doğru yönerge işlemcisi kullanmak ve yönerge işlemcisinin genel varsayılan oluşturucuya sahip olduğundan emin olun. Aksi takdirde, yönerge işlemcisi önce Initialize() yöntemini neden başarısız çıkış bulmak için hata ayıklama seçenekleri kullanın. Daha fazla bilgi için [sorun giderme metin şablonlarını](../modeling/debugging-a-t4-text-template.md).|  
|Adlı yönerge işlenirken bir özel durum '{0}'.|Bir yönerge işlemcisi, bir yönerge işlenirken bir özel durum oluşturduğunda gerçekleşir.|Yönerge işlemcisini parametrelerinin doğru olduğundan emin olun.|  
|Ana bilgisayar bütünleştirilmiş kod başvurusu çözümlenmeye çalışılırken hata özel durum oluşturdu '{0}'.|Ana bilgisayar bütünleştirilmiş kod başvurusu çözümlemeye çalışırken bir özel durum oluşturduğunda gerçekleşir. Derleme ileti sağlar başvuru dizesi.|Bütünleştirilmiş kod başvuruları geldiğini \<@# assembly #> yönergeleri ve yönerge işlemcilerine. Derleme parametresinde sağlanan 'name' parametresi doğru olduğundan emin olun.|  
|Belirtilmeye çalışıldı desteklenmeyen {1} değeri '{0}' yönergesi {2}|Gerçekleşir RequiresProvidesDirectiveProcessor (tümü bizim oluşturulan yönerge işlemcileri ondan türetilen), sağladığınız desteklenmeyen gerektirir veya bağımsız değişken sağlar.|Name = adlarında 'çiftleri sağlanan değer,' emin olmanız gerekir ve parametreleri doğru sağlar.|



