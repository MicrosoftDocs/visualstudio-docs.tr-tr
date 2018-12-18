---
title: Keşif sınırları | Microsoft Intellitest Geliştirici Test aracı
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9d1ac08a2314119c924417191ca509a4bcd18021
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000662"
---
# <a name="exploration-bounds"></a>Keşif sınırları

**PexSettingsAttributeBase** ayarları sınırları öznitelikleri için soyut temel sınıf. Bkz: [ayarlar Şelalesi](settings-waterfall.md) Intellitest ayarlarında genel bakış.

Bu ve türetilmiş özniteliklerini özelliklerini adlandırılmış kullanarak ayarları değiştirebilirsiniz:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Kısıtlama sınırları çözme**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) -saniye sayısını [kısıtlama Çözücü](input-generation.md#constraint-solver) izlenmesi yeni ve farklı yürütme yol açacak girişleri bulmak vardır.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) -boyutunu megabayt cinsinden, [kısıtlama Çözücü](input-generation.md#constraint-solver) girişleri bulmak için kullanabilirsiniz.<p />
* **Araştırma yolu sınırları**
  * [MaxBranches](#maxbranches) -tek bir yürütme yol boyunca gerçekleştirilen dalları sayısı.
  * [MaxCalls](#maxcalls) -tek bir yürütme yolu sırasında yapılan çağrı sayısı.
  * [MaxStack](#maxstack) -bir tek bir yürütme yolu sırasında herhangi bir zamanda yığının en büyük boyutunu etkin çağrı çerçeve sayısı ölçülür.
  * [MaxConditions](#maxconditions) -koşullar sırasında tek bir yürütme yolu denetlenebilir girişleri üzerinden sayısı.<p />
* **Keşif sınırları**
  * [MaxRuns](#maxruns) -İnceleme sırasında denenecek çalıştırmalarının sayısı.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) -yayılan yeni bir test olmadan ardışık çalıştırma sayısı üst sınırı.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) -İnceleme sırasında denenecek benzersiz yürütme yolları ile çalıştırma sayısı üst sınırı.
  * [Maxexceptions yapılandırma](#maxexceptions) -tüm bulunan yürütme yolları bileşimini bulunabilir özel durum sayısı.<p />
* **Test paketi kodu oluşturma ayarları**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) -true olduğunda herhangi bir yol sınırları aşan yürütme yolları ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [ MaxConditions](#maxconditions)) göz ardı edilir.
  * [TestEmissionFilter](#testemissionfilter) -hangi koşullar altında testleri Intellitest yayma gösterir.
  * [TestEmissionBranchHits](#testemissionbranchhits) -kaç testin Intellitest yayan denetler.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Saniye sayısını [kısıtlama Çözücü](input-generation.md#constraint-solver) gerçekleştirilecek bir yeni ve farklı yürütme yol açacak girişleri hesaplamak vardır. Bu bir seçenektir, **PexSettingsAttributeBase** ve onun türetilmiş türlerine.

Daha ayrıntılı bir program yürütme yollarını, Intellitest keşfediyor, denetim akışı ve veri akışı programının Intellitest yapılar kısıtlaması sistemleri daha karmaşık hale gelir. Zaman sınırlama bağlı olarak, daha fazla veya daha az zaman bulan yeni yürütme yolları yararlanmak Intellitest izin vermek için bu değeri ayarlayabilirsiniz.

Genellikle, bir zaman aşımı nedeni, Intellitest bir çözüme sahip olmayan bir kısıtlama sistemi için bir çözüm bulmaya çalışıyor, ancak bu duruma dikkat edin değil olmasıdır. Bu zaman aşımı için en yaygın durumda olduğundan, bu sınırı artırmak için anlamlı olmayabilir.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Megabayt sayısı bu [kısıtlama Çözücü](input-generation.md#constraint-solver) gerçekleştirilecek bir yeni ve farklı yürütme yol açacak girişleri hesaplamak vardır. Bu bir seçenektir, *PexSettingsAttributeBase** ve onun türetilmiş türlerine.

Daha ayrıntılı Intellitest denetim akışı ve veri akışı programının Intellitest yapılar kısıtlaması sistemleri haline daha karmaşık bir program yürütme yollarını açıklar. Bilgisayarınıza bağlı olarak kullanılabilir bellek, daha karmaşık kısıtlaması sistemleri çıkmanın Intellitest izin vermek için bu değeri ayarlayabilirsiniz.

Genellikle, bir zaman aşımı nedeni, Intellitest bir çözüme sahip olmayan bir kısıtlama sistemi için bir çözüm bulmaya çalışıyor, ancak bu duruma dikkat edin değil olmasıdır. Bu en yaygın nedeni bellek yetersiz durumuna olduğundan, bu sınırı artırmak için anlamlı olmayabilir.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Tek Yürütme yol boyunca gerçekleştirilen dalları maksimum sayısı.

Bağlı Bu araştırma arkasında motivasyon sırasında Intellitest keşfediyor herhangi bir yürütme yolu uzunluğu sınırlandırmaktır [giriş oluşturma](input-generation.md). Özellikle, Intellitest program sonsuz bir döngüye giriyor, yanıt vermeyen hale gelmesini engeller.

Yürütülen ve izlenen kodun her koşullu ve koşulsuz dal, parametreli bir test girişleri üzerinde bağlı olmayan dallar dahil olmak üzere, bu sınır doğrultusunda sayılır.

Örneğin, aşağıdaki kod dalları 100 siparişinin kullanır:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Tek bir yürütme yolu sırasında yapılan çağrı sayısı.

Bağlı Bu araştırma arkasında motivasyon sırasında Intellitest keşfediyor herhangi bir yürütme yolu uzunluğu sınırlandırmaktır [giriş oluşturma](input-generation.md). Özellikle, Intellitest program Intellitest kurtaramazsınız bir yığın taşmasına neden olduğu zaman, sonsuz sayıda yöntemi tekrar tekrar çağırırsa yanıt vermeyen hale gelmesini engeller.

Her ' % s'çağrı (doğrudan, dolaylı, sanal, atlama) yürütülen ve izlenen kodun bu sınırında sayılır.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Etkin arama çerçeve sayısı ölçülen bir tek bir yürütme yolu sırasında herhangi bir zamanda yığının maksimum boyutu.

Intellitest sırasında keşfediyor herhangi bir yürütme yolu yığın boyutunu sınırlamak için motivasyon bağlı Bu araştırma arkasında olan [giriş oluşturma](input-generation.md). Özellikle, Intellitest kurtaramazsınız bir yığın taşmasına neden olduğu tüm kullanılabilir yığın alanı kullanarak Intellitest engeller.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Koşullar sırasında tek bir yürütme yolu denetlenebilir girişleri üzerinden emaximum sayısı.

Bağlı Bu araştırma arkasında motivasyon sırasında Intellitest keşfediyor herhangi bir yürütme yolu karmaşıklığını sınırlandırmaktır [giriş oluşturma](input-generation.md). Parametreli bir test girdilerine bağımlı her koşullu dalda bu sınırında sayılır.

Örneğin, aşağıdaki kod her yolda n + 1 koşullar kullanır:

```csharp
[PexMethod]
void ParameterizedTest(int n) 
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

Intellitest, test araştırma sırasında deneyecek çalıştırma TH emaximum sayısı.

Döngüler veya özyineleme içeren herhangi bir kod yürütme yolları sonsuz sayıda olabilir ve bu nedenle Intellitest sırasında sınırlı olması gereken motivasyon bağlı Bu araştırma arkasında olan [giriş oluşturma](input-generation.md).

İki ayar **MaxRuns** ve **MaxRunsWithUniquePaths** gibi ilgili:

* Intellitest çağıracaktır parametreli bir test yönteminin en fazla **MaxRuns** zamanlarla farklı test girdileri.
* Intellitest, yürütülen kodun belirleyici ise, farklı yürütme yolu her zaman alabilir. Ancak, bazı koşullar altında yürütülen kodun izleyin ve bu da, daha önce farklı girişlerle denetlendiği bir yürütme yolu.
* Intellitest bulduğu kaç tane benzersiz yürütme yolları sayar; Bu sayı sınırlıdır **MaxRunsWithUniquePaths** seçeneği.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Art arda çalışmaları olmadan yayılan yeni bir test sayısı.

Intellitest genellikle kısa süre içinde birçok ilgi çekici test giriş bulabilirsiniz, ancak bir süre sonra dosyayı daha yeni girişler test ve daha fazla birim testleri yayar bulamaz. Bu yapılandırma seçeneği bağımlı Intellitest yeni bir test yayma olmadan gerçekleştirebilir ardışık girişimlerinin sayısını getirir. Erişildiğinde, onu araştırma durdurulur.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Intellitest, inceleme sırasında dikkate alacaktır benzersiz yollara maksimum sayısı.

Bu araştırma bağlı arkasında motivasyon döngüler veya bir özyinelemede içeren herhangi bir kod yürütme yolları sonsuz sayıda olabilir ve bu nedenle Intellitest olmalıdır sırasında sınırlı olduğu [giriş oluşturma](input-generation.md).

İki ayar **MaxRuns** ve **MaxRunsWithUniquePaths** gibi ilgili: 

* Intellitest çağıracaktır parametreli bir test yönteminin en fazla **MaxRuns** zamanlarla farklı test girdileri.
* Intellitest, yürütülen kodun belirleyici ise, farklı yürütme yolu her zaman alabilir. Ancak, bazı koşullar altında yürütülen kodun izleyin ve bu da, daha önce farklı girişlerle denetlendiği bir yürütme yolu. 
* Intellitest bulduğu kaç tane benzersiz yürütme yolları sayar; Bu sayı sınırlıdır **MaxRunsWithUniquePaths** seçeneği.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>Maxexceptions yapılandırma

Araştırma işlemi durduruldu önce karşılaşılabilir özel durumları maksimum sayısı.

Bu araştırma bağlı arkasında motivasyon birçok hata içeren kod İnceleme önlemektir. Intellitest kod içinde çok fazla hata bulursa, araştırma durduruldu.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Yapılandırılmış yolu sınırları aşma yürütme yolları [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), ve [MaxConditions](#maxconditions) göz ardı edilir.

Bu araştırma bağlı arkasında motivasyon (büyük olasılıkla) Sonlandırıcı olmayan testlerle başa sağlamaktır. Intellitest gibi bağlı İnceleme ulaştığında [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), veya [MaxConditions](#maxconditions), bunu kabul eder. test Sonlandırıcı olmayan bir işlem olur ve bir yığın taşması daha sonra neden olmaz. Bu test çalışmalarını diğer test çerçeveleri ile ilgili sorunlara neden olabilir ve bu özniteliği, büyük olasılıkla Sonlandırıcı olmayan işlemler için test çalışmaları veya test çalışmaları, yığın taşmasına neden olacak yayma gelen Intellitest önlemek için bir yol sağlar.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Intellitest yayma testleri türlerini gösterir. Olası değerler şunlardır:

* **Tüm** -testleri dahil her şeyi için ihlal varsayımı yayma.
* **FailuresAndIncreasedBranchHits** (varsayılan) - tüm benzersiz hataları için testleri yayma ve her bir test çalışması artırır kapsamı tarafından denetlenen [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths** - Intellitest bulduğu tüm hataları için testleri yayma ve aynı zamanda benzersiz yürütme yolunu neden için her bir test girişi.
* **Hataları** -yalnızca hataları için testleri gösterin.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

Geçerli bağlı olarak [TestEmissionFilter](#testemissionfilter) bunlar programın önce ele alınmayan bir dalda kapsar, ayarlama, Intellitest yeni test çalışmaları yayar.

**TestEmissionBranchHits** ayarı belirler Intellitest yalnızca bir dal hiç kapsamında dikkate almanız gereken varsa (**TestEmissionBranchHits = 1**), bir test, ya da iki kez (kapsamında **TestEmissionBranchHits = 2**) ve benzeri.

**TestEmissionBranchHits = 1** Intellitest ulaşmak tüm dalları kapsar bir küçük test paketi oluşturur. Özellikle, bu test paketi aynı zamanda tüm temel bloklar ve bu sınıra deyimleri ele alınacaktır.

Bu seçenek için varsayılan değer **TestEmissionBranchHits = 2**, ayrıca daha iyidir daha ifadesel bir test paketi oluşturduğu uygun gelecekteki regresyon hataları algılama için.

## <a name="got-feedback"></a>Geri bildirim var mı?

Fikirlerinizi gönderin ve özellik istekleri [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
