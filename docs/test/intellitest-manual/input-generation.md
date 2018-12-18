---
title: Dinamik sembolik yürütme | Microsoft Intellitest Geliştirici Test aracı
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 33bd31c59de85f70d653d2de912b8c9bc5bb0e30
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295897"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Dinamik sembolik yürütme kullanarak giriş oluşturma

Intellitest oluşturur için girişler [parametreli birim testleri](test-generation.md#parameterized-unit-testing) programı dal koşulları analiz tarafından. Test girdileri olup programın yeni dal oluşturma davranışları tetikleyebilir göre seçilir. Analiz artımlı bir işlemdir. Bir koşul iyileştirir **s: ben -> {true, false}** giriş parametrelerini resmi test **miyim**. **q** Intellitest zaten gözlemlenen davranışların kümesini temsil eder. Başlangıçta **q: = false**, bu yana hiçbir şey henüz gözlenmiştir.

Döngünün adımlar şunlardır:

1. Intellitest belirler girişleri **miyim** şekilde **(i) q = false** kullanarak bir [kısıtlama Çözücü](#constraint-solver). 
   Yapı, giriş olarak **miyim** önce görülmeyen bir yürütme yolu götürür. Başlangıçta, yani **miyim** yürütme yol henüz saptanmamış olduğundan herhangi bir girişi olabilir.

1. Intellitest, seçilen giriş ile test yürütür **miyim**, test ve test edilen programın yürütülmesini izler.

1. Yürütme sırasında program, program tarafından koşullu dalları hakkında belirlenir belirli bir yol alır. Yürütme belirlemek tüm koşullar kümesini adlı *yol koşulu*koşul olarak yazılmış **ben -> {true, false} p:** biçimsel giriş parametrelerini üzerinden. Intellitest bir gösterimiyse, bu koşul hesaplar.

1. Intellitest kümeleri **q: (q ya da p) =**. Diğer bir deyişle, bu yolun gösterdiği yakaladı olgu kayıtları **p**.

1. 1. adıma gidin.

Intellitest'ın [kısıtlama Çözücü](#constraint-solver) .NET programlarında görünebilir tüm türlerin değerlerle giderebilirsiniz:

* [Tamsayıları](#integers-and-floats) ve [kaydırmalar](#integers-and-floats)
* [Nesneler](#objects)
* [Yapılar](#structs)
* [Diziler](#arrays-and-strings) ve [dizeleri](#arrays-and-strings)

Intellitest belirtilen varsayımlar ihlal girişleri filtreler.

Hemen girişleri yanı sıra (bağımsız değişkenleri [parametreli birim testleri](test-generation.md#parameterized-unit-testing)), bir test daha fazla giriş değerlerini çizebilirsiniz [PexChoose](static-helper-classes.md#pexchoose) statik sınıf. Seçenekler de davranışını belirlemek [mocks parametreli](#parameterized-mocks).

<a name="constraint-solver"></a>
## <a name="constraint-solver"></a>Kısıtlama Çözücü

Intellitest, test ve test altındaki program ilgili giriş değerlerini belirlemek için bir kısıtlama Çözücü kullanır.

Intellitest kullanan [Z3](https://github.com/Z3Prover/z3/wiki) kısıtlama Çözücü.

<a name="dynamic-code-coverage"></a>
## <a name="dynamic-code-coverage"></a>Dinamik kod kapsamı

Bir yan etkisi olarak izleme çalışma zamanının, Intellitest dinamik kod kapsamı verilerini toplar. Bu adlandırılır *dinamik* Intellitest yürütülen kod hakkında bildiğinden, başka bir kapsamı araç normalde yaptığınız gibi bu nedenle, mutlak değerler kapsam için aynı şekilde veremez. 

Intellitest 5/10 temel taşı olarak dinamik kapsam bildirdiğinde, örneğin, on dışında beş blokları, burada ele alındığını yani analiz tarafından şimdiye ulaştınız tüm yöntemleri bloklarında toplam sayısı (mevcut olan tüm yöntemleri aksine bir test edilen erleme) 10'dur.
Daha sonra analiz, daha fazla erişilebilir yöntemleri olarak bulunan, hem pay (Bu örnekte 5) ve (10) paydası artırabilir.

<a name="integers-and-floats"></a>
## <a name="integers-and-floats"></a>Tamsayıları ve float

Intellitest'ın [kısıtlama Çözücü](#constraint-solver) test giriş değerleri ilkel türleri gibi belirler **bayt**, **int**, **float**ve diğerleri test ve test altındaki program için farklı yürütme yollarını tetiklemek için sırası.

<a name="objects"></a>
## <a name="objects"></a>Nesneler

Intellitest olabilir ya da [mevcut .NET sınıfların örneklerini oluşturmak](#existing-classes), veya Intellitest'e otomatik olarak kullanabileceğiniz [sahte nesneler oluşturma](#parameterized-mocks) , belirli bir arabirim uygulamak ve farklı şekilde davranan kullanımınıza bağlı olarak.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Varolan bir sınıf örneği

**Sorun nedir?**

Intellitest, test ve test altındaki program çalıştığında yürütülen yönergeleri izler. Özellikle, tüm alanlarına erişim izler. Ardından kullanan bir [kısıtlama Çözücü](#constraint-solver) test ve program test altındaki diğer ilginç bir şekilde davranır, nesneleri ve alan değerlerini de dahil olmak üzere yeni test girdileri belirlemek için.

Bu alan değerlerine ayarlayın ve belirli bir türden nesneler oluşturmak için Intellitest gerektiğini anlamına gelir. Sınıf ise [görünür](#visibility) ve bir [görünür](#visibility) varsayılan oluşturucu, Intellitest sınıfının bir örneğini oluşturabilirsiniz.
Sınıfın tüm alanları [görünür](#visibility), Intellitest alanları otomatik olarak ayarlanır.

Tür görünür değil veya alanları olmayan [görünür](#visibility), Intellitest nesneleri oluşturmak ve bunları düzeyde kod kapsamını elde etmek için ilgi çekici durumlara getirmek için Yardım gerekiyor. Intellitest oluşturma ve isteğe bağlı şekillerde örnekleri başlatma için yansıma kullanabilirsiniz, ancak bu genellikle değil  
Nesne hiçbir zaman normal program yürütme sırasında oluşabilecek bir duruma getirin çünkü istenmez. Bunun yerine, Intellitest kullanıcıdan ipuçları kullanır.

<a name="visibility"></a>
## <a name="visibility"></a>Görünürlük

.NET Framework ayrıntılı görünürlük modeli vardır: türleri, yöntemleri, alanları ve diğer üyeleri olabilir **özel**, **genel**, **iç**ve daha fazlası.

Intellitest testleri oluşturduğunda, üretilen testler bağlamında .NET görünürlük kuralları ile ilgili yasal (örneğin, Oluşturucular, yöntemler, arama ve alanlarını ayarlama) yalnızca eylemleri gerçekleştirmek çalışacaktır.

Kurallar aşağıdaki gibidir:

* **İç üyelerin görünürlüğü**
  * Intellitest, üretilen testler kapsayan görünür iç üyelerine erişimi olduğunu varsayar [PexClass](attribute-glossary.md#pexclass).
  .NET sahip **Internalsvisibletoattribute** başka derlemeler iç üyelerin görünürlüğü genişletmek için.<p />

* **Özel görünürlüğünü ve ailesi (korumalı, C#) üyeleri [PexClass](attribute-glossary.md#pexclass)**
  * Intellitest her zaman yerleştirir testlerin doğrudan [PexClass](attribute-glossary.md#pexclass) veya bir alt sınıfı. Bu nedenle, tüm görünür aile üyelerine kullanabilir Intellitest varsayılır (**korumalı** C#).
  * Doğrudan testlerin yerleştirdiyseniz [PexClass](attribute-glossary.md#pexclass) (genellikle kısmi sınıflar kullanarak), Intellitest tüm özel üyeleri de kullanabilirsiniz. varsayar [PexClass](attribute-glossary.md#pexclass).<p />

* **Genel üye görünürlüğü**
  * Intellitest varsayar bağlamında görünen dışarı aktarılan tüm üyelere kullanabilir [PexClass](attribute-glossary.md#pexclass).

<a name="parameterized-mocks"></a>
## <a name="parameterized-mocks"></a>Parametreli mocks

Test bir arabirim türünün bir parametresi olan bir yöntemi nasıl? Korumalı olmayan bir sınıfın veya? Intellitest, bu yöntem çağrıldığında, daha sonra hangi uygulamaları kullanılacak bilmez. Ve belki de hiç bile gerçek bir uygulama kullanılabilir test zaman.

Geleneksel yanıt kullanmaktır *sahte nesneler* açık davranış. 

Sahte bir nesne bir arabirimi uygulayan (veya korumalı olmayan bir sınıfın uzantısı). Gerçek bir uygulama, ancak yalnızca sahte nesnesini kullanarak testlerin yürütmesini sağlayan kısayol temsil etmiyor. Uygulamanın davranışı, kullanıldığı her test çalışmasının bir parçası olarak el ile tanımlanır. Sahte nesneler ve beklenen davranışları tanımlamanızı kolaylaştıran birçok araç vardır, ancak bu davranış yine de el ile tanımlanmalıdır.

Sabit kodlanmış sahte nesnelerindeki değerler yerine Intellitest değerleri oluşturabilirsiniz. Bağlayabileceğinizi gibi [parametreli birim testi](test-generation.md#parameterized-unit-testing), Intellitest parametreli mocks de sağlar.

Parametreli mocks iki farklı yürütme modu vardır:

* **seçme**: Kodu Keşfetme, parametreli mocks ek test giriş kaynağı olan ve ilgi çekici değerleri seçmek Intellitest çalışır
* **yeniden yürütme**: daha önce oluşturulan bir test çalıştırırken, parametreli mocks saptamalar davranış (diğer bir deyişle, önceden tanımlı davranış) gibi davranır.

Kullanım [PexChoose](static-helper-classes.md#pexchoose) parametreli mocks değerlerini almak için.

<a name="structs"></a>
## <a name="structs"></a>Yapılar

Intellitest hakkında akıl **yapı** ilgilenen ile olduğu gibi değerler benzer [nesneleri](#objects).

<a name="arrays-and-strings"></a>
## <a name="arrays-and-strings"></a>Diziler ve dizeler

Intellitest, test ve test altındaki program çalışırken yürütülen yönergeleri izler. Özellikle, ne zaman program bir dize veya bir dizi (alt sınırı ve çok boyutlu bir dizi uzunluğu) uzunluğuna bağlıdır gözlemler. Program bir dize veya dizi listesinin farklı öğelerini nasıl kullanır uyan. Ardından kullanan bir [kısıtlama Çözücü](#constraint-solver) hangi uzunlukları ve öğe değerlerini test ve program test ilginç bir şekilde davranmasına yol açabileceğini saptayabilirsiniz.

Intellitest ilginç program davranışları tetiklemek için gereken dizeler ve dizi boyutu en aza indirmek çalışır.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Ek girişler alın

[PexChoose](static-helper-classes.md#pexchoose) statik sınıf testine ek girişler elde etmek için kullanılabilir ve uygulamak için kullanılan [mocks parametreli](#parameterized-mocks).

<a name="further-reading"></a>
## <a name="further-reading"></a>Daha fazla bilgi

* [Nasıl çalışır?](https://blogs.msdn.microsoft.com/devops/2014/12/11/smart-unit-tests-a-mental-model/)

## <a name="got-feedback"></a>Geri bildirim var mı?

Fikirlerinizi gönderin ve özellik istekleri [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).