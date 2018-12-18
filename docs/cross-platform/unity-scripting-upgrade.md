---
title: .NET kullanarak 4.x Unity
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: conceptual
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 294f3efe5e541a316a8bb90da07d75e9319e7983
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027380"
---
# <a name="using-net-4x-in-unity"></a>.NET kullanarak 4.x Unity

C# ve .NET, Unity betik, temel alınan teknoloji 2002'de, bunları başlangıçta Microsoft yayımlanan bu yana güncelleştirmeleri almaya devam etti. Ancak, Unity geliştiricilerinin .NET Framework ve C# dili için eklenen yeni özellikler gitmenize haberdar olmayabilir. Unity 2017.1 önce bir .NET yıl güncelleştirmelerin eksik 3.5 scripting çalışma zamanı, eşdeğer Unity kullanıyor olmasıdır.

Unity 2017.1 sürümünden, Unity, Deneysel bir C# 6 uyumlu sürümü, bir .NET 4.6 yükseltme komut dosyası, çalışma zamanı sürümü kullanıma sunuldu. Unity 2018.1 .NET 4.x eşdeğer çalışma zamanı artık eşdeğer çalışma zamanı artık eski bir sürüm olarak kabul edilir daha eski .NET 3.5 sırasında Deneysel olarak kabul edilir. Ve Unity 2018.3'ın yayınlanmasıyla birlikte, Unity yükseltilmiş bir komut dosyası çalışma zamanı varsayılan seçimi yapın ve hatta C# 7 daha fazla sınırlandıramazsınız güncelleştirmek için edeceğini öngörüyor. Daha fazla bilgi ve bu yol haritasında ilgili son güncelleştirmeleri için Unity'nın okuma [blog gönderisi](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) veya ziyaret kendi [Deneysel betik önizlemeler Forumu](https://forum.unity.com/forums/experimental-scripting-previews.107/). Bu sırada, aşağıdaki bölümlere .NET 4.x komut dosyası çalışma zamanıyla artık kullanılabilir yeni özellikler hakkında daha fazla bilgi için göz atın.

## <a name="prerequisites"></a>Önkoşullar

* [Unity 2017.1 veya yukarıdaki](https://unity3d.com/) (2018.2 önerilir)
* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>.NET 4.x komut dosyası çalışma zamanı Unity etkinleştirme

.NET 4.x komut dosyası çalışma zamanı'nı etkinleştirmek için aşağıdaki adımları uygulayın:

1. Açık PlayerSettings Unity denetçi'deki seçerek **Düzenle > Proje Ayarları > oyuncu**.

1. Altında **yapılandırma** başlığını tıklatın **Scripting çalışma zamanı sürümü** açılan seçip **.NET 4.x eşdeğer**. Unity yeniden başlatmanız istenir.

![.NET 4.x eşdeğer seçin](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Seçme arasında .NET 4.x ve .NET Standard 2.0 profilleri

.NET 4.x eşdeğer komut dosyası çalışma zamanı için değiştirdikten sonra belirtebileceğiniz **API uyumluluk düzeyi** PlayerSettings içinde açılır menüsünü kullanarak (**Düzenle > Proje Ayarları > oyuncu**). İki seçenek vardır:

* **.NET standard 2.0**. Bu profili eşleşen [.NET Standard 2.0 profil](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) .NET Foundation tarafından yayımlanmış. Unity için yeni projeler .NET Standard 2.0 önerir. .NET küçük olan 4.x, boyutu kısıtlı platformlar için avantajlıdır. Ayrıca, bu profili destek Unity destekleyen tüm platformlarda Unity kaydoldu.

* **.NET 4.x**. Bu profil en son .NET 4 API'sine erişim sağlar. .NET Framework sınıf kitaplıkları tüm mevcut kodlar içerir ve .NET Standard 2.0 profillerini destekler. .NET Standard 2.0 profile dahil edilmemiş API parçası, projenizin gerektirdiği .NET 4.x profili kullanın. Ancak, bu API bazı bölümlerini tüm platformlarda Unity'nın desteklenmiyor olabilir.

Unity kişinin seçenekleri bunlar hakkında daha fazla bilgi edinebilirsiniz [blog gönderisi](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/).

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>.NET kullanarak derleme başvurularını eklemeyi 4.x API uyumluluk düzeyi

.NET Standard 2.0 ayarı kullanırken **API uyumluluk düzeyi** açılır listesinde, tüm derlemelerin API profilinde başvurulan ve kullanılabilir. Ancak, daha büyük bir .NET 4.x profil kullanılırken, Unity ile birlikte gelen derlemelerden bazıları varsayılan olarak başvurulan değildir. Bu API'leri kullanmak için elle bir bütünleştirilmiş kod başvurusu eklemeniz gerekir. Unity ile birlikte gelir, derlemeleri görüntüleyebilir **MonoBleedingEdge/lib/mono** Unity editor yüklemenizin dizin:

![MonoBleedingEdge dizini](media/vstu_monobleedingedge.png)

Örneğin, .NET 4.x profili kullanıyorsanız ve kullanmak istediğiniz `HttpClient`, System.Net.Http.dll için bir bütünleştirilmiş kod başvurusu eklemeniz gerekir. Bu olmadan, derleyici bir bütünleştirilmiş kod başvurusu eksik Şikayet:

![Eksik derleme başvurusu](media/vstu_missing-reference.png)

Visual Studio Unity projeleri için .csproj ve .sln dosyaları, açtığınız her durumda yeniden oluşturur. Sonuç olarak, projeyi yeniden açmayı üzerine kayıp çünkü, doğrudan Visual Studio'da derleme başvurularını ekleyemezsiniz. Bunun yerine, bir özel metin dosyası adlı **mcs.rsp** kullanılmalıdır:

1. Adlı yeni bir metin dosyası oluşturun **mcs.rsp** Unity proje kökündeki **varlıklar** dizin.

1. Boş metin dosyası birinci satırda girin: `-r:System.Net.Http.dll` ve ardından dosyayı kaydedin. Dahil edilen derlemeler ile bir başvuru eksik olabilir, "System.Net.Http.dll" değiştirebilirsiniz.

1. Unity Düzenleyicisi'ni yeniden başlatın.

## <a name="taking-advantage-of-net-compatibility"></a>.NET uyumluluğu yararlanma

Yeni C# sözdizimi ve dil özelliklerin yanı sıra .NET 4.x komut dosyası çalışma zamanı Unity kullanıcılar eski .NET 3.5 komut dosyası çalışma zamanı ile uyumsuz .NET paket çok büyük bir kitaplık erişmenizi sağlar.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Paketleri Nuget'ten Unity projeye ekleyin.

[NuGet](https://www.nuget.org/) .NET için paket yöneticisidir. NuGet, Visual Studio'da tümleşiktir. Ancak, Unity projeleri NuGet paketleri eklemek için özel bir işlem gerektirir. Unity içinde bir proje açtığınızda Visual Studio Proje dosyalarının yeniden oluşturulur, gerekli yapılandırmaları geri alma olmasıdır. Bir paket, Unity projesi için aşağıdakileri yapın Nuget'ten eklemek için:

1. NuGet, eklemek istediğiniz uyumlu bir paketi bulmak için Gözat (.NET Standard 2.0 ya da .NET 4.x). Bu örnekte ekleme gösterilecektir [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), .NET Standard 2.0 projeye JSON ile çalışmak için popüler bir paket.

1. Tıklayın **indirme** düğmesi:

    ![indir düğmesi](media/vstu_nuget-download.png)

1. İndirilen dosyayı bulun ve uzantısını değiştirme **.nupkg** için **.zip**.

1. Zip dosyası içinde gidin **lib/netstandard2.0** dizin ve kopyalama **Microsoft.Developer.accountmanagement** dosya.

1. Unity proje kökündeki **varlıklar** klasör adında yeni bir klasör oluşturun **eklentileri**. Eklentiler bir Unity özel klasör addır. Bkz: [Unity belgeleri](https://docs.unity3d.com/Manual/Plugins.html) daha fazla bilgi için.

1. Yapıştırma **Microsoft.Developer.accountmanagement** Unity proje dosyasına **eklentileri** dizin.

1. Adlı bir dosya oluşturun **link.xml** Unity projenizin **varlıklar** dizin ve aşağıdaki XML'i ekleyin.  Bu, Unity'nın bayt şeridi oluşturma işlemi bir ıl2cpp platformu verirken gerekli verileri kaldırmaz garanti eder.  Bu adım bu kitaplığın belirli olsa da, yansıma benzer şekillerde kullandığınız diğer kitaplıklarla sorunlar çalıştırabilirsiniz.  Daha fazla bilgi için lütfen bkz [Unity'nın docs](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) bu konuda.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Olan her şeyi yerinde, artık Json.NET paketini kullanabilirsiniz.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Bu, bağımlılıkları olan bir kitaplık kullanılarak, basit bir örnektir. NuGet paketleri kullanan diğer NuGet paketleri, bu bağımlılıkları el ile indirin ve aynı şekilde projeye eklemek gerekir.

## <a name="new-syntax-and-language-features"></a>Yeni söz dizimi ve dil özellikleri

Güncelleştirilmiş komut dosyası çalışma zamanı'nı kullanarak C# 6 ve çok sayıda yeni dil özellikleri ve söz dizimi için Unity geliştiricileri erişmenizi sağlar.

### <a name="auto-property-initializers"></a>Otomatik-özellik başlatıcıları

Unity'nın .NET 3.5 komut dosyası çalışma zamanı, otomatik özelliği söz dizimi başlatılmamış özelliklere hızlıca tanımlamak kolaylaştırır, ancak başlatma betiğinizde başka bir yerde olması gerekir. Artık .NET 4.x çalışma zamanı ile aynı satırda otomatik özelliklerde başlatmak mümkündür:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Dize ilişkilendirme

Eski .NET 3.5 çalışma zamanı ile dize birleştirme garip sözdizimi gereklidir. Artık .NET 4.x çalışma zamanı ile [ `$` dize ilişkilendirme](https://docs.microsoft.com/dotnet/csharp/language-reference/tokens/interpolated) ifadeleri dizelere daha doğrudan ve okunabilir sözdiziminde eklenecek özellik sağlar:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>İfade gövdeli üyeler

Yeni C# sözdizimi ile .NET 4.x çalışma zamanında kullanılabilir [lambda ifadeleri](https://docs.microsoft.com/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) daha Sözün okunmaları işlevleri gövdesini değiştirebilirsiniz:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

İfade gövdeli üyeler salt okunur özellikler de kullanabilirsiniz:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Görev Tabanlı Zaman Uyumsuz Desen (TAP)

[Zaman uyumsuz programlama](https://docs.microsoft.com/dotnet/csharp/async) uygulamanızın yanıt veremez duruma gelmesine neden olmadan gerçekleşmesi uzun süren işlemlere izin verir. Bu işlev, bu işlemlerin sonuçlarına bağlı olan kod devam etmeden önce tamamlanması uzun süren işlemleri için beklenecek kodunuzu de sağlar. Örneğin, bir dosyaya yük ya da bir ağ işlemin tamamlanmasını bekleyebilir.

Unity içinde zaman uyumsuz programlamaya genel ile gerçekleştirilir [eş yordamlar](https://docs.unity3d.com/Manual/Coroutines.html). Ancak, C# 5 bu yana, .NET geliştirme zaman uyumsuz programlamada, tercih edilen yöntem olmuştur [görev tabanlı zaman uyumsuz desen (TAP)](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) kullanarak `async` ve `await` anahtar sözcüklerle [ System.Threading.Task](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task). Özet olarak, içinde bir `async` yapabilecekleriniz işlevi `await` güncelleştirme uygulamanızın geri kalanını engelleme olmadan bir görevin tamamlanma:

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

DOKUNUN karmaşık bir konu, geliştiricilerin düşünmelisiniz Unity özgü farklılıklarına sahip olur. Sonuç olarak, DOKUNUN Unity oluşturucuda Evrensel bir ardılı değildir; Ancak, yararlanarak başka bir araçtır. Bu özelliğin kapsamı dışında bu makalede, ancak bazı genel en iyi uygulamalar ve ipuçları aşağıda verilmiştir.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Unity DOKUNARAK için başlatılan bir başvuru alma

Bu ipuçlarını Unity TAP kullanmaya başlamanıza yardımcı olabilir:

* Zaman uyumsuz işlevleri beklenmesini hedeflenen, dönüş türü olmalıdır [ `Task` ](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task) veya [ `Task<TResult>` ](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task-1).
* Bir görev döndüren zaman uyumsuz işlevleri soneki olmalıdır **"Async"** adlarını eklenir. "Async" soneki yardımcı olan bir işlev her zaman beklenmesini gösterir.
* Yalnızca `async void` dönüş türü için zaman uyumsuz işlevleri geleneksel zaman uyumlu koddan devre dışı etkinleştiren işlevler. Bu tür işlevleri kendilerini beklenemez ve "Async" soneki adlarında olmamalıdır.
* Unity UnitySynchronizationContext zaman uyumsuz işlevleri, varsayılan olarak ana iş parçacığında çalışır emin olmak için kullanır. Unity API ana iş parçacığı dışında erişilebilir değildir.
* Görevleri arka plan iş parçacıklarında gibi yöntemleri çalıştırmak mümkündür [ `Task.Run` ](https://msdn.microsoft.com/library/hh195051.aspx) ve [ `Task.ConfigureAwait(false)` ](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx). Bu ana iş parçacığından performansı artırmak için pahalı işlemler boşaltılması için kullanışlı bir tekniktir. Ancak, arka plan iş parçacığı kullanarak hata ayıklama, gibi zor olan sorunlara yol açabilir [yarış koşulları](https://wikipedia.org/wiki/Race_condition).
* Unity API ana iş parçacığı dışında erişilebilir değildir.
* Kullanım iş parçacıkları üzerinde Unity WebGL desteklenmeyen görevleri oluşturur.

#### <a name="differences-between-coroutines-and-tap"></a>Eş yordamlar DOKUNUN arasındaki farklar

Eş yordamlar ve DOKUNUN arasında bazı önemli farklar vardır / async-await:

* Eş yordamlar değerleri döndüremiyor ancak `Task<TResult>` olabilir.
* Konulamıyor bir `yield` bir try-catch deyiminde hata işleme eş yordamlar zorlaşır. Ancak, try-catch DOKUNARAK çalışır.
* MonoBehaviour türetilen olmayan sınıflarda Unity'nın eş yordam özelliği kullanılamaz. DOKUNUN, zaman uyumsuz programlama bu tür sınıflar için mükemmeldir.
* Bu noktada, Unity DOKUNUN önermek ve bu da bir eş yordamlar toptan yerine değil. Profil oluşturma ve diğer herhangi bir proje için bir yaklaşım belirli sonuçları bilmek tek yoludur.

> [!NOTE]
> Unity 2018.2 itibariyle, zaman uyumsuz yöntemlerle kesme noktaları hata ayıklama tam olarak desteklenmiyor; Ancak, [bu işlevsellik Unity 2018.3 beklenen](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof işleci

`nameof` İşleci bir değişken, tür veya üye dize adını alır. Bazı durumlarda nerede `nameof` el altında hatalarını günlüğe kaydetme ve bir sabit dize adını alma:

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Arayan bilgileri öznitelikleri

[Arayan bilgisi özniteliklerini](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/caller-information) bir yöntemin arayanı hakkında bilgi sağlar. Çağıran bilgisi özniteliği ile kullanmak istediğiniz her parametre için varsayılan bir değer sağlamanız gerekir:

```csharp
private void Start ()
    {
        ShowCallerInfo("Something happened.");
    }
    public void ShowCallerInfo(string message,
            [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
            [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
            [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
    {
        Debug.Log($"message: {message}");
        Debug.Log($"member name: {memberName}");
        Debug.Log($"source file path: {sourceFilePath}");
        Debug.Log($"source line number: {sourceLineNumber}");
    }
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>' Using static

[' Using static](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/using-static) statik İşlevler, sınıf adını yazmadan kullanmanıza olanak tanır. Aynı sınıftaki statik çeşitli işlevler kullanmanız gerekirse statik kullanarak, alan ve zaman kaydedebilirsiniz:

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Il2cpp konuları

Oyununuzu iOS gibi platformlarda verirken, Unity kendi ıl2cpp altyapısına "derleyin" IL ardından hedef platformu yerel derleyiciyi kullanarak derlenmiş C++ kodu için kullanır. Bu senaryoda, yansıma bölümlerini ve kullanımı gibi desteklenmeyen birden fazla .NET özellikleri vardır `dynamic` anahtar sözcüğü. Kendi kodunuzda bu özellikleri kullanmaya kontrol edebilirsiniz, ancak sorunlar ıl2cpp ve Unity ile göz önünde 3. parti DLL'ler ve değil yazılan SDK'ları kullanarak çalıştırabilirsiniz. Bu konu hakkında daha fazla bilgi için lütfen bkz [betik kısıtlamaları](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) Unity'nın site açıktır.

Ayrıca, yukarıdaki Json.NET örnekte belirtildiği gibi Unity kullanılmayan kodu ıl2cpp dışarı aktarma işlemi sırasında Şerit dener.  Bu genellikle, yansıma kullanan kitaplıkları ile ilgili bir sorun değildir; ancak, yanlışlıkla özellikleri veya dışarı aktarma anda belirlenemiyor zamanında çağrılacak yöntem çıkarmanız.  Bu sorunları düzeltmek için ekleme bir **link.xml** projenize derlemeler ve ad alanları stripping işlemine yönelik çalıştırmayı listesini içeren dosya.  Tüm Ayrıntılar için lütfen bkz [bytecode çıkarma üzerinde Unity'nın docs](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>.NET 4.x örnek Unity projesi

Örnek, çeşitli .NET 4.x özellikleri örnekleri içerir. Projeyi indirmek ya da kaynak kodunu görüntülemek [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Ek kaynaklar

* [Unity Blog - Unity 2018.2 çalışma zamanı iyileştirmeleri betik oluşturma](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [C# geçmişi](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-version-history)
* [C# 6 yenilikleri](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-6)
* [Unity, eş yordam kullanılarak ve DOKUNUN zaman uyumsuz programlama](https://blogs.msdn.microsoft.com/appconsult/2017/09/01/unity-coroutine-tap)
* [Unity 2017 oluşturucuda yerine zaman uyumsuz-bekleme](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Unity Forumu - Deneysel betik önizlemeleri](https://forum.unity.com/forums/experimental-scripting-previews.107/)