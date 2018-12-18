---
title: Uyarıları ve hataları | Microsoft Intellitest Geliştirici Test aracı
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: efb82a7419ba58c27ccab864d2360538075a1089
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000620"
---
# <a name="warnings-and-errors"></a>Uyarıları ve hatalar

## <a name="warnings-and-errors-by-category"></a>Uyarı ve hata kategorisine göre

* **Sınırlar
  * [MaxBranches aşıldı](#maxbranches-exceeded)
  * [MaxConstraintSolverTime aşıldı](#maxconstraintsolvertime-exceeded)
  * [MaxConditions aşıldı](#maxconditions-exceeded)
  * [MaxCalls aşıldı](#maxcalls-exceeded)
  * [MaxStack aşıldı](#maxstack-exceeded)
  * [MaxRuns aşıldı](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests aşıldı](#maxrunswithoutnewtests-exceeded)<p />

* **Kısıtlama çözme**
  * [Çözüm Somutlaştırılamıyor](#cannot-concretize-solution)<p />

* **etki alanları**
  * [Nesnesi oluşturmak için Yardım gerekiyor](#help-construct)
  * [Türleri bulmak için Yardım gerekiyor](#help-types)
  * [Tahmin kullanılabilir türü](#usable-type-guessed)<p />

* **Yürütme**
  * [Araştırma sırasında beklenmeyen hata](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)<p />

* **İzleme**
  * [İzlemesiz yöntemi çağrılır](#uninstrumented-method-called)
  * [Adlı dış yöntemi](#external-method-called)
  * [Adlı izlenemeyen yöntemi](#uninstrumentable-method-called)
  * [Test Edilebilirlik sorununu](#testability-issue)
  * [Sınırlama](#limitation)<p />

* **Yorumlayıcı**
  * [Çağrı uyuşmazlığı gözlemlendi](#observed-call-mismatch)
  * [Statik alanda depolanan değer](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches aşıldı

Intellitest sınırlar sırasında keşfediyor herhangi bir yürütme yolu uzunluğu [giriş oluşturma](input-generation.md). Bu özellik Intellitest program sonsuz bir döngüye giriyor, yanıt vermeyen hale gelmesini engeller.

Yürütülen ve izlenen kodun her koşullu ve koşulsuz dal girişleri üzerinde bağlı olmayan dallar dahil olmak üzere bu sınır doğru sayılır [parametreli birim testine](test-generation.md#parameterized-unit-testing).

Örneğin, aşağıdaki kodu 100 sırasına göre dallar kullanır:

```csharp
for (int i=0; i<100; i++) { }
```

Düzenleyebileceğiniz **MaxBranches** seçeneği bir özniteliğin sınıfından türetilen **PexSettingsAttributeBase**, gibi [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod) . Aşağıdaki örnek bu bağlı etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Ayrıca **TestExcludePathBoundsExceeded** Intellitest nasıl genellikle bu sorunlarla başa çıkmak için bildirmek için seçeneği.

Test kodu içindedir, kullandığınız [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) kısıtlamaları döngü koşul tarafından oluşturulan yok saymak için:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime aşıldı

Intellitest kullanan bir [kısıtlama Çözücü](input-generation.md#constraint-solver) yeni test girdileri hesaplamak için. Kısıtlama çözme olabilir çok zaman alan bir işlem Intellitest sınırları - özellikle yapılandırmanıza olanak tanır şekilde **MaxConstraintSolverTime**.

Birçok uygulama için daha iyi kapsamı içinde önemli ölçüde zaman aşımını artırmayı oluşturmayacaktır. Bunun nedeni, çoğu zaman aşımları çözüm olan kısıtlaması sistemleri tarafından neden olduğunu ' dir. Ancak, Intellitest, zaman aşımı neden olacak tüm olası çözümleri çalışmadan tutarsız olduğunu belirlemek mümkün olmayabilir.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions aşıldı

Intellitest sınırlar sırasında keşfediyor herhangi bir yürütme yolu uzunluğu [giriş oluşturma](input-generation.md). Bu özellik Intellitest program sonsuz bir döngüye girer, yanıt vermeyen hale gelmesini engeller.

' In girdilerine bağımlı her koşullu dalda [parametreli birim testine](test-generation.md#parameterized-unit-testing) bu sınırında sayılır.

Örneğin, aşağıdaki kod her yolda tüketir **n + 1** koşullar:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

Düzenleyebileceğiniz **MaxConditions** seçeneği bir özniteliğin sınıfından türetilen **PexSettingsAttributeBase**, gibi [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod). Örneğin:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Ayrıca **TestExcludePathBoundsExceeded** Intellitest genellikle bu sorunlarla başa çıkmak nasıl kaydolacaklarını için seçeneği.

Kullanabileceğiniz [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) kısıtlamaları döngü koşul tarafından oluşturulan yok saymak için:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>MaxCalls aşıldı

Intellitest sınırlar sırasında keşfediyor herhangi bir yürütme yolu uzunluğu [giriş oluşturma](input-generation.md). Bu özellik, programın sonsuz bir döngüye girer gittiğinde yanıt vermeyen olmaktan Intellitest önler.

Her çağrının (doğrudan, dolaylı, sanal veya atlayın) yürütülen ve izlenen kodunu bu sınırında sayılır.

Düzenleyebileceğiniz **MaxCalls** seçeneği bir özniteliğin sınıfından türetilen **PexSettingsAttributeBase**, gibi [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod). Aşağıdaki örnek bu bağlı etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Ayrıca **TestExcludePathBoundsExceeded** Intellitest genellikle bu sorunlarla başa çıkmak nasıl kaydolacaklarını için seçeneği.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack aşıldı

Intellitest sırasında keşfediyor herhangi bir yürütme yolu çağrı yığınının boyutunu sınırlar [giriş oluşturma](input-generation.md). Bu özellik, bir yığın taşması oluştuğunda sonlandırma gelen Intellitest engeller.

Düzenleyebileceğiniz **MaxStack** seçeneği bir özniteliğin sınıfından türetilen **PexSettingsAttributeBase**, gibi [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod). Aşağıdaki örnek, bu sınır (önerilmez) etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Ayrıca **TestExcludePathBoundsExceeded** Intellitest genellikle bu sorunlarla başa çıkmak nasıl kaydolacaklarını için seçeneği.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns aşıldı

Intellitest sırasında keşfediyor yürütme yolları sayısını sınırlar [giriş oluşturma](input-generation.md). Bu özellik, program döngüler veya bir özyinelemede olduğunda Intellitest sonlandırır sağlar.

Intellitest parametreli bir test ile belirli girişleri her çalıştırıldığında yeni bir test çalışması yayar, durumda olmayabilir. Bkz: [TestEmissionFilter](exploration-bounds.md#testemissionfilter) daha fazla bilgi için.

Düzenleyebileceğiniz **MaxRuns** seçeneği bir özniteliğin sınıfından türetilen **PexSettingsAttributeBase**, gibi [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod). Aşağıdaki örnek, bu sınır (önerilmez) etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests aşıldı

Intellitest sırasında keşfediyor yürütme yolları sayısını sınırlar [giriş oluşturma](input-generation.md). Bu özellik, program döngüler veya bir özyinelemede olduğunda Intellitest sonlandırır sağlar.

Intellitest parametreli bir test ile belirli girişleri her çalıştırıldığında yeni bir test çalışması yayar, durumda olmayabilir. Bkz: [TestEmissionFilter](exploration-bounds.md#testemissionfilter) daha fazla bilgi için.

Intellitest genellikle birçok ilgi çekici test girdileri başlangıçta bulur, ancak bu bir süre sonra - herhangi bir daha fazla test yayabilir değil -. Bu seçenek, ne kadar süreyle Intellitest başka bir ilgili test girişi bulmak denemeye devam yönetir.

Düzenleyebileceğiniz **MaxRunsWithoutNewTests** seçeneği bir özniteliğin sınıfından türetilen **PexSettingsAttributeBase**, gibi [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod). Aşağıdaki örnek, bu sınır (önerilmez) etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Çözüm somutlaştırılamıyor

Bu hata genellikle önceki bir hata sonucu var. Intellitest kullanan bir [kısıtlama Çözücü](input-generation.md#constraint-solver) yeni test girdileri belirlemek için. Bazı durumlarda, girişler tarafından önerilen test [kısıtlama Çözücü](input-generation.md#constraint-solver) geçersizdir. Bu durum ortaya çıkabilir olduğunda:

* bazı kısıtlamalar bilinmiyor
* Kullanıcı kodunda hata neden olan bir kullanıcı tanımlı yol değerleri oluşturulursa
* Bazı ilgili türleri (örneğin, COM sınıfları) Intellitest tarafından denetlenmeyen başlatma mantığına sahip

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Nesnesi oluşturmak için Yardım gerekiyor

Intellitest [test girdileri oluşturur](input-generation.md), ve bazı girişleri nesneleri alanlara sahip olabilir.
Burada, özel bir alan olan bir sınıf örneği oluşturmak Intellitest çalışır ve ilgi çekici bir program davranışı, bu özel alan belirli bir değere sahip olduğunda meydana gelir varsayar.

Ancak, bu yansıma ile mümkün olmakla birlikte, Intellitest rastgele alan değerlerine sahip nesneleri üretmez.
Bunun yerine, bu gibi durumlarda kullanıcının bir nesne oluşturur ve kendi özel alan istenen değere sahip olduğu bir duruma getirmek için ortak bir sınıftaki yöntemleri kullanma hakkında ipuçları sağlayın kullanır.

Okuma [varolan sınıf oluşturma](input-generation.md#existing-classes) ilginç nesneleri oluşturmak için Intellitest nasıl yardımcı olabileceğini öğrenin.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Türleri bulmak için Yardım gerekiyor

Intellitest [test girdileri oluşturur](input-generation.md) için herhangi bir .NET türü. Burada, soyut bir sınıftan türetilen veya soyut bir arabirimi uygulayan bir örneğini oluşturmak Intellitest çalışır ve Intellitest kısıtlamalar karşılayan herhangi bir türde bilmez.

Intellitest kısıtlamalarla eşleşen bir veya daha fazla türlerine işaret ederek yardımcı olabilir. Genellikle, aşağıdaki özniteliklerden birini yardımcı olur:

* **PexUseTypeAttribute**, işaret ettiği için belirli bir tür.

  Intellitest BT'nin bildirirse, örneğin "öğesine atanamaz türler, bilmez **System.Collections.IDictionary**", aşağıdakileri ekleyerek yardımcı olabilecek **PexUseTypeAttribute** test (veya düzeni sınıfı için):

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Bir derleme düzeyi özniteliği**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Tahmin kullanılabilir türü

Intellitest [test girdileri oluşturur](input-generation.md) için herhangi bir .NET türü. Bir türü soyut veya arabirim olduğunda, Intellitest türü belirli bir uygulama seçmeniz gerekir. Bu seçim yapmak için hangi türlerin mevcut bilmesi gerekir.

Bu uyarı gösterildiğinde, BT Intellitest başvurulan derlemeleri bazıları baktığı ve bir uygulama türü, ancak bulunan indiicates yazın veya varsa daha uygun kullanılabilir türleri başka bir yerde kullanması gereken olup olmadığından emin değil. Intellitest yalnızca taahhüdü aranan bir türü seçtiniz.

Bu uyarıyı önlemek için Intellitest'ın türü seçimi kabul veya diğer türleri kullanarak karşılık gelen ekleyerek Intellitest yardımcı [PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Araştırma sırasında beklenmeyen hata

Bir test araştırma sırasında beklenmeyen bir özel durum yakalandı.

Lütfen [bu hata bildirin](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Kullanıcı kodunda bir özel durum oluştu. Yığın izlemesi inceleyin ve kodunuzda hata kaldırın.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>İzlemesiz yöntemi çağrılır

Intellitest [test girdileri oluşturur](input-generation.md) programın yürütülmesini izleyerek. Intellitest davranışını izleyebilmeniz ilgili kodu düzgün şekilde işaretlenmiş gereklidir.

İşaretlenmiş kod başka bir, izlemesiz derlemede yöntemleri çağırdığında, bu uyarı görüntülenir.
Her ikisi de etkileşimi keşfetmek için Intellitest isterseniz diğer derleme (veya bazı bölümleri) işaretlemelidir.

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Adlı dış yöntemi

Intellitest [test girdileri oluşturur](input-generation.md) .NET uygulamalarını yürütülmesini izleyerek.
Intellitest, bir .NET dilinde olmayan kod için anlamlı test girdileri oluşturulamıyor.

İşaretlenmiş kod Intellitest analiz edemiyoruz bir yönetilmeyen, yerel bir yöntemi çağırdığında, bu uyarı görüntülenir. Her ikisi de etkileşimi keşfetmek için Intellitest istiyorsanız, yönetilmeyen yöntemi sahte gerekir.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Adlı izlenemeyen yöntemi

Intellitest [test girdileri oluşturur](input-generation.md) .NET uygulamalarını yürütülmesini izleyerek. Ancak, teknik nedenlerle Intellitest izleyemez, bazı yöntemler vardır. Örneğin, Intellitest statik Oluşturucu izleyemez.

İşaretlenmiş kod Intellitest izleyemez bir yöntemi çağırdığında, bu uyarı görüntülenir.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Test Edilebilirlik sorununu

Intellitest [test girdileri oluşturur](input-generation.md) programın yürütülmesi izleyerek. Program belirleyici olduğunda ve ilgili davranışı test girdileri tarafından denetlenir ilgili test girdileri yalnızca oluşturabilirsiniz.

Test çalışması yürütülmesi sırasında bir yöntem çağrıldığından, ya da belirleyici olmayan şekilde davranan veya ortam ile etkileşime giren bu uyarı görüntülenir. Örnekler yöntemlerinin **System.Random** ve **System.IO.File**. Anlamlı test girdileri oluşturmak için Intellitest istiyorsanız, Intellitest Test Edilebilirlik sorunları işaretler yöntemleri sahte gerekir.

<a name="limitation"></a>
## <a name="limitation"></a>Sınırlama

Intellitest [test girdileri oluşturur](input-generation.md) kullanarak bir [kısıtlama Çözücü](input-generation.md#constraint-solver).
Ancak, kapsamı dışındadır bazı işlemler vardır [kısıtlama Çözücü](input-generation.md#constraint-solver).
Şu anda bu içerir:

* en kayan nokta işlemleri (doğrusal bazı aritmetik kayan noktalı sayının desteklenir)
* kayan noktalı sayıları ve tam sayılar arasında dönüştürmeler
* tüm işlemler **System.Decimal** türü

Intellitest yorumlanamıyor bir yöntemi çağırır veya bir işlem gerçekleştirir yürütülen kod bu uyarı görüntülenir.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Çağrı uyuşmazlığı gözlemlendi

Intellitest [test girdileri oluşturur](input-generation.md) programın yürütülmesini izleyerek. Ancak, Intellitest tüm yönergeleri izlemeniz mümkün olmayabilir. Örneğin, yerel kod izleyemez ve izlenmiyor kod izleyemez.

Intellitest kod izleyemez olduğunda, bu kod için uygun olan test girdileri oluşturulamıyor.
Genellikle, Intellitest bu yönteme bir çağrı dönene kadar bir yöntem izleyemez duruma dikkat edin değil. Ancak, bu uyarı nedeni:

* Intellitest izlenen bir yönteme bir çağrı başlatılan bazı kod
* İşaretlenmiş bir yöntemi çağıran yönteme
* Intellitest çağrıldı Araçlı yöntemi izler

İç içe geçmiş izleme eklenmiş çağrısını ilgili olan test girdileri oluşturmak mümkün olmayabilir şekilde ne Ara yönteme yaptığını, Intellitest bilmez.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Statik alanda depolanan değer

Intellitest sistematik olarak belirleyebilir [ilgili test girdileri](input-generation.md) yalnızca belirleyici, birim testi; başka bir deyişle, her zaman aynı test girdileri ile aynı şekilde davranır. Özellikle, bu test sistemi yeniden test çalışmasına izin veren bir durumda bırakmanız gerekir anlamına gelir.
İdeal olarak, birim testi tüm genel durumunu değiştirmemesi gerekir, ancak genel öğeleri ile tüm etkileşimler örnek.

Bu uyarı, bir statik alan değiştirildiğini belirtir; Bu belirleyici olmayan şekilde davranan test çalışmasına neden olabilir.

Bazı durumlarda, statik bir alanı değiştirme kabul edilebilir:

* Kurulum veya temizleme kod değişikliği geri almak test girdilerine sebep olduğunda
* zaman alan yalnızca bir kez başlatılır ve değer daha sonra değişmez

<a name="report-bug"></a>

## <a name="got-feedback"></a>Geri bildirim var mı?

Fikirlerinizi gönderin ve özellik istekleri [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).