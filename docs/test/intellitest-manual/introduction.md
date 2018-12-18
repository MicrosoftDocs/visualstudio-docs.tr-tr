---
title: Genel bakış | Microsoft Intellitest Geliştirici Test aracı
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c2a8e6df93d3af64bd114e0e9994aadce58e7f8d
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296027"
---
# <a name="overview-of-microsoft-intellitest"></a>Microsoft Intellitest genel bakış

Intellitest, erken hataları bulmanıza olanak sağlar ve test bakım maliyetlerini azaltır. Intellitest, otomatik ve şeffaf bir sınama yaklaşımı kullanarak testleri için .NET kodunuzu aday paketi oluşturabilirsiniz. Test paketi oluşturma daha destekli tarafından *doğruluk özelliklerini* belirtirsiniz. Test edilen kod geliştikçe Intellitest bile test paketi otomatik olarak evrilir.

**Nitelemesi testleri** Intellitest açısından geleneksel birim testleri paketi kod davranışını belirlemek etkinleştirir.
Bu tür bir test paketi, eski veya tanımadığınız kodu yeniden düzenleme ile ilişkili karmaşıklığı bağlayabileceğiniz temelini oluşturan bir regresyon paketi olarak kullanılabilir.

**Kılavuzlu test üretimi giriş** kesin test giriş değerleri; otomatik olarak oluşturmak için Intellitest kullanan bir açık Kod Analizi ve yaklaşım çözme kısıtlaması herhangi bir kullanıcı müdahalesi gerektirmeden genellikle. Karmaşık nesne türleri için fabrikaları otomatik olarak oluşturur. Genişletme ve gereksinimlerinize uyacak şekilde fabrikaları yapılandırarak test giriş üretim yönlendirebilir. Koddaki onaylar olarak belirtilen doğruluk özelliklerini de otomatik olarak daha fazla test giriş oluşturma kılavuzu için kullanılır.

**IDE tümleştirme** Intellitest Visual Studio IDE içinde tamamen tümleşiktir. (Otomatik olarak oluşturulan giriş, çıkış kodunuzu, oluşturulan test çalışmalarını ve bunların geçiş veya başarısız durumu gibi) test paketi oluşturma sırasında toplanan tüm bilgiler Visual Studio IDE içinde görünür. Kod çözme ve Visual Studio IDE'den çıkmadan Intellitest, artırarak algoritmanın yeniden çalıştırılması arasında kolayca yineleyebilirsiniz.
Testleri çözümünde birim testi projesi olarak kaydedilebilir ve otomatik olarak daha sonra Visual Studio Test Gezgini tarafından algılanır.

**Var olan uygulamaları test etme için tamamlayıcı** var olan bir sınama tamamlamak için kullanım Intellitest yöntemler, zaten izleyin.

Test etmek isterseniz:

* Temel veri ya da temel veri dizileri üzerinden algoritmaları:
  * Yazma [parametreli birim testleri](test-generation.md#parameterized-unit-testing)
* Algoritmalar derleyici gibi karmaşık veri üzerinde:
  * Intellitest ilk soyut bir veri temsilini oluşturur ve ardından algoritmaya akışı sağlar
  * Intellitest kullanarak örneği oluşturmak istiyorum [özel nesne oluşturma](input-generation.md#objects) ve veri okuduğunuzda ve ardından algoritma çağırma
* Veri kapsayıcıları:
  * Yazma [parametreli birim testleri](test-generation.md#parameterized-unit-testing)
  * Intellitest kullanarak örneği oluşturmak istiyorum [özel nesne oluşturma](input-generation.md#objects) ve veri okuduğunuzda ve kapsayıcının bir yöntemi çağırmak ve okuduğunuzda daha sonra yeniden denetle
  * Yazma [parametreli birim testleri](test-generation.md#parameterized-unit-testing) farklı yöntemleri parametrelere bağlı olarak bir uygulama arayın
* Varolan bir kod tabanına:
  * bir dizi oluşturarak çalışmaya başlamak için Visual Studio'nun Intellitest Sihirbazı'nı kullanın [parametreli birim testleri (PUTs)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Intellitest, Merhaba Dünya

Intellitest girişleri, ünlü oluşturmak için kullanabileceğiniz anlamına gelir test edilmiş program ilgili bulur **Merhaba Dünya!** dize. Bu, oluşturduğunuz varsayılır bir C# MSTest tabanlı test projesi ve bir başvuru eklenir **Microsoft.Pex.Framework**. Farklı test çerçevesi kullanıyorsanız, oluşturun bir C# sınıf kitaplığı ve projeyi kurmak nasıl test framework belgelerine bakın.

Aşağıdaki örnek, iki kısıtlamalar adlı parametre oluşturur **değer** böylece Intellitest gereken dizeyi oluşturur:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

Intellitest, derlemenizi ve yürütmenizi sonra aşağıdaki gibi test kümesi oluşturur:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

Okuma [Intellitest ile birim testleri oluşturmak](../../test/generate-unit-tests-for-your-code-with-intellitest.md) testlerin kaydedildiği anlamak için. Oluşturulan test kodu aşağıdaki kod gibi bir test içermelidir:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

Bu kadar kolay!

## <a name="limitations"></a>Sınırlamalar

Bu bölümde, Intellitest sınırlamaları açıklanmaktadır:

* [Nondeterminism](#nondeterminism)
* [Eşzamanlılık](#concurrency)
* [.NET yerel kodu](#native-code)
* [Platform](#platform)
* [Dil](#language)
* [Sembolik akıl yürütme](#symbolic-reasoning)
* [Yığın izlemeleri](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Nondeterminism

Intellitest çözümlenen program kararlı olduğunu varsayar. Yüklü değilse, bağlı bir araştırma ulaşana kadar Intellitest döngüsü.

Intellitest Intellitest kontrol girişleri üzerinde dayanıyorsa determistic olmayan olacak şekilde bir program göz önünde bulundurur.

Intellitest denetimleri için sağlanan girişler [parametreli birim testleri](test-generation.md#parameterized-unit-testing) ve öğesinden alınan [PexChoose](static-helper-classes.md#pexchoose).
Bu algılama yönetilmeyen veya izlemesiz koddaki çağrıları sonuçlarını "Giriş" olarak işaretlenmiş program ayrıca değerlendirilir, ancak Intellitest kontrol edemezsiniz. Programın denetim akışı, bu dış kaynaklardan gelen belirli değerlere bağlıysa, Intellitest "program önceden yazdığı ortaya çıkarıldı alanları faaliyetidir olamaz".

Ayrıca, programın dış kaynaklardan gelen değerleri, programın yeniden çalıştırma değiştirirseniz determistic olmayan olarak kabul edilir. Böyle durumlarda, programın yürütülmesini denetime Intellitest kaybeder ve arama verimli hale gelir.

Böyle bir durumda bazen belirgin değildir.
Aşağıdaki örnekleri dikkate alın:

* Sonucu **GetHashCode()** yöntemi yönetilmeyen kod tarafından sağlanır ve tahmin edilebilir değil.
* **System.Random** sınıfı geçerli sistem saatinin gerçekten rastgele değerler sunmak için kullanır.
* **System.DateTime** sınıfı Intellitest denetimi altında değil geçerli saati sağlar.

### <a name="concurrency"></a>Eşzamanlılık

Intellitest, çok iş parçacıklı programlar işlemez.

### <a name="native-code"></a>Yerel kod

Intellitest anlamak x86 gibi yerel kod yönergeleri adlı aracılığıyla **P/Invoke**. Böyle çağrılar için geçirilen kısıtlamalar çevirmek nasıl bilmez [kısıtlama Çözücü](input-generation.md#constraint-solver).
.NET kodu için bile, yalnızca bu Instruments kod çözümleyebilirsiniz. Intellitest bazı kısımlarını işaretleme yapılamıyor **mscorlib**, reflection kitaplığını dahil. **DynamicMethod** izlenemez.

Önerilen geçici çözüm, bu tür yöntemler dinamik bütünleştirilmiş kodundaki türler nerede bulunur test modu sağlamaktır. Ancak, bazı yöntemler izlemesiz olsa bile Intellitest olarak işaretlenmiş bir kod mümkün olduğunca çoğunu kaplayacak şekilde çalışacaktır.

### <a name="platform"></a>Platform

Intellitest yalnızca X86 üzerinde 32-bit desteklenir. NETframework.

### <a name="language"></a>Dil

İlkesi, Intellitest herhangi bir .NET dilinde yazılmış rastgele .NET programlarının çözümleyebilirsiniz. Ancak, Visual Studio'da yalnızca desteklediği C#.

### <a name="symbolic-reasoning"></a>Sembolik akıl yürütme

Intellitest kullanan otomatik [kısıtlama Çözücü](input-generation.md#constraint-solver) hangi değerlerin test ve test programı için uygun olduğunu belirlemek için. Ancak, kısıtlama Çözücü yeteneklerini de her zaman olacaktır, sınırlı.

### <a name="incorrect-stack-traces"></a>Yanlış Yığın izlemeleri

Intellitest yakalar ve "özel durumları izleme eklenmiş her yöntemi beklerseniz" çünkü yığın izlemelerini satır numaralarını doğru olmayacaktır. Tasarıma göre "rethrow" yönerge sınırlama budur.

## <a name="further-reading"></a>Daha fazla bilgi

* [Tanıtım blog gönderisi](https://blogs.msdn.microsoft.com/devops/2014/11/19/introducing-smart-unit-tests/).
* [Intellitest ile kodunuz için birim testleri oluşturma](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
