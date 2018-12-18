---
title: Kod kapsamı test etme
ms.date: 09/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc8b08b68bb6c48fa22abaa90ba8b0b9daa25e89
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370945"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından test edilen belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Etkin hatalara karşı koruma sağlamak için testleriniz çalışmalı veya kodunuzun büyük bir kısmını 'kapsamalıdır'.

Kod Kapsamı Çözümleme (CLI) yönetilen ve yönetilmeyen (yerel) kod için uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png)

## <a name="requirements"></a>Gereksinimler

Kod kapsamı özelliği, yalnızca Visual Studio Enterprise Edition'da kullanılabilir.

## <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Test Gezgini'ndeki birim testlerinde kod kapsamını analiz etmek için

1. Üzerinde **Test** menüsünde seçin **kod kapsamı analizi**.

2. Çalışan satırları görmek için ![kod kapsamı renklerini simgesini göster](../test/media/codecoverage-showcoloringicon.png) **kod kapsamı renklerini Göster**.

   Renkleri değiştirmek veya kalın yüz kullanmak için seçin **Araçları** > **seçenekleri** > **ortam** > **yazı tipleri ve Renkleri** > **ayarlarını göster: Metin Düzenleyicisi**. Altında **görünen öğeler**, kapsama öğelerini ayarlayın.

3. Sonuçlar düşük kapsamı gösterirse, hangi kod parçalarının uygulanmadığını araştırın ve bunları kapsamak için daha fazla test yazın. Geliştirme ekipleri için tipik olarak yaklaşık %80 kod kapsamı hedeflenir. Bazı durumlarda, düşük kapsam kabul edilebilir. Örneğin, düşük kapsamı bazı kodlar standart şablonundan oluşturulduğu kabul edilebilir.

> [!TIP]
> - Bu derleyici optimizasyonunun kapalı olduğundan emin olun
> - Yönetilmeyen (yerel) kod ile çalışıyorsanız, hata ayıklama derlemesini kullanma
> - Her derleme için .pdb (simge) dosyaları oluşturduğunuzdan emin olun.

Beklediğiniz sonuçları alamazsanız, bkz. [kod kapsamı sorunlarını giderme](../test/troubleshooting-code-coverage.md). Kod kapsamını kod güncelleştirdikten sonra çalıştırmayı unutmayın. Kodunuzu değiştirdikten sonra veya testleri çalıştırdığınızda kapsam sonuçları ve kod renklendirme otomatik olarak güncelleştirilmez.

## <a name="report-in-blocks-or-lines"></a>Bloklarda veya satırlarda raporu

Kod kapsamı sayılır *blokları*. Bir blok, tek bir giriş ve çıkış noktası kodu parçasıdır.  Programın denetim akışı bir test çalıştırması sırasında bir blok geçerse, o blok anlatıldığı gibi sayılır. Blok kullanılma sayısının sonuç üzerinde etkisi yoktur.

Seçerek satırlarda gösterilen sonuçlarınız da olabilir **sütunları Ekle/Kaldır** tablo üstbilgisinde. Test, kodun herhangi bir satırında tüm kod bloklarına uygulanırsa, tek satır olarak sayılır. Uygulanan ve uygulanmayan bazı kod blokları bir satır içerdiğinde bu kısmi bir satır olarak sayılır.

Yüzdeler kaynak kodunda gördüğünüz parçaların boyutuyla daha yakından ilişkili olduğundan bazı kullanıcılar satırları saymayı tercih eder. Birçok satır kaplayan olsa bile uzun bir blok hesaplama tek bir blok olarak sayılacaktır.

## <a name="manage-code-coverage-results"></a>Kod kapsamı sonuçlarını yönetme

**Kod kapsamı sonuçlarını** penceresi genellikle en son çalıştırma sonucunu gösterir. Sonuçlar test verilerini değiştirirseniz veya testlerinizin her defasında yalnızca bir kısmını çalıştırırsanız değişir.

Kod kapsamı penceresini önceki sonuçları veya diğer bilgisayarlarda elde edilen sonuçları görüntülemek için de kullanılabilir.

Birçok çalıştırmanın sonucunu örneğin farklı test verileri kullanan çalışmalardan birleştirebilirsiniz.

- **Bir önceki sonuç kümesini görüntülemek için**, aşağı açılan menüden seçim yapın. Menü, yeni bir çözüm açtığınızda temizlenen geçici bir liste gösterir.

- **Bir önceki oturumdan sonuçları görüntülemek için**, seçin **kod kapsamı sonuçlarını Al**, gitmek **TestResults** çözümünüzü ve alma klasöründe bir *.coverage* dosya.

   Karşılama renklendirme beri kaynak kodu değişirse yanlış olabilir *.coverage* dosyası oluşturuldu.

- **Sonuçları metin olarak okunabilir hale getirmek için**, seçin **kod kapsamı sonuçlarını ver**. Bu bir okunabilir oluşturur *.coveragexml* diğer araçlarla işlemek veya kolayca posta ile göndermek, dosya.

- **Sonuçları başka bir kişiye göndermek için**, göndermek ya da bir *.coverage* dosya ya da dışarı aktarılan bir *.coveragexml* dosya. Sonra dosyayı içe aktarabilirsiniz. Kaynak kodun aynı sürümü varsa, kapsam renklendirmeyi görebilirsiniz.

## <a name="merge-results-from-different-runs"></a>Farklı çalışmalardan sonuçları birleştirme

Bazı durumlarda, test verilerine bağlı olarak kodunuzda farklı bloklar kullanılacaktır. Bu nedenle, farklı bir test çalışmasının sonuçlarını birleştirmek isteyebilirsiniz.

Örneğin, giriş "2" ile bir test çalıştırdığınızda, belirli bir işlevin %50'sinin kapsandığını bulun. Giriş "-2" ile ikinci kez test çalıştırdığınızda diğer % 50'si işlev kapsamında görünüm renklendirme kapsamına bakın. Şimdi iki test çalışması sonuçlarını birleştirin ve işlevin %100 kapsamında rapor ve görünümü renklendirme kapsamını gösterin.

Kullanım ![kod kapsamı penceresinde birleştirme düğmesi için simge](../test/media/codecoverage-mergeicon.png) **kod kapsamı sonuçlarını Birleştir** Bunu yapmak için. Son çalışmaların veya alınan sonuçların herhangi bir bileşimini seçebilirsiniz. Dışa aktarılan sonuçları birleştirmek istiyorsanız, bunları önce almanız gerekir.

Kullanım **kod kapsamı sonuçlarını ver** birleştirme işleminin sonuçlarını kaydetmek için.

### <a name="limitations-in-merging"></a>Birleştirmede sınırlamalar

- Kodun farklı sürümlerinden kapsama verilerini birleştirirseniz, sonuçlar ayrı ayrı gösterilir, ancak birleştirilmez. Tam olarak birleştirilmiş sonuçlar almak için test verilerini değiştirerek kodun aynı yapısını kullanın.

- Dışa ve sonra içe alınmış sonuç dosyasını birleştirirseniz, sonuçları bloklarla değil yalnızca çizgilerle görüntüleyebilirsiniz. Kullanım **sütunları Ekle/Kaldır** satır verilerini göstermek için komutu.

- ASP.NET projesinin testlerinden sonuçları birleştirirseniz, birleştirilmiş değil ayrı testlerin sonuçları görüntülenir. Bu yalnızca ASP.NET yapılarına uygulanır: başka bir derleme için sonuçlar birleştirilecektir.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Kod kapsamı sonuçlarından öğeleri hariç tut

Örneğin kodu bir metin şablonundan oluşturulan tedarik puanlarını kodunuzda belirli öğeler dışında isteyebilirsiniz. Ekleme <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> özniteliği aşağıdaki kod öğelerinden birine: sınıf, yapı, yöntem, özellik, özellik ayarlayıcısı veya alıcı, olay.

> [!TIP]
> Hariç tutulan bir sınıfın türetilmiş sınıfları dışarıda tuttuğunu.

Örneğin:

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Yerel C++ kod öğeleri hariç tut

C++ koddaki yönetilmeyen (yerel) öğeleri dışlamak için:

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Aşağıdaki makroları kullanın:

`ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

`ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

- *ExclusionName* herhangi bir benzersiz ad.

- *FunctionName* tam olarak nitelenmiş işlev adıdır. Joker karakterler içerebilir. Örneğin, bir sınıfın tüm işlevlerini hariç tutmak için yazma `MyNamespace::MyClass::*`

- *SourceFilePath* yerel veya .cpp dosyasının UNC yoludur. Joker karakterler içerebilir. Aşağıdaki örnek, belirli bir dizindeki tüm dosyaları hariç tutar: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Herhangi bir ad alanı veya sınıf içindeki değil genel ad alanındaki dışlama makroları için çağrılar yerleşir.

- Dışlamaları birim test kod dosyasına veya uygulama kod dosyasına yerleştirebilirsiniz.

- Derleyici seçeneğini ayarlayarak ya da kullanarak yönetilmeyen (yerel) kod Dışlamalar derlenmelidir `#pragma managed(off)`.

> [!NOTE]
> C + işlevleri hariç tutmak için +/ CLI kod, öznitelik Uygula `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` işlevi. Bu C# ile aynıdır.

### <a name="include-or-exclude-additional-elements"></a>Dahil edilecek veya hariç ek öğeler

Kod kapsamı analizi yüklenen derlemeler ve kendisi için gerçekleştirilen bir *.pdb* aynı dizinde dosya kullanılabilir *.dll* veya *.exe* dosya. Bu nedenle bazı durumlarda, uygun kopyalarını alarak eklenen derleme kümesini genişletebilirsiniz *.pdb* dosyaları.

Üzerinde derlemeleri ve öğeleri seçili kod kapsamı çözümleme yazarak daha fazla denetimle alıştırma yapabilirsiniz bir *.runsettings* dosya. Örneğin, kendi sınıfları için öznitelikler eklemek zorunda kalmadan belirli tür derlemeleri hariç tutabilirsiniz. Daha fazla bilgi için [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Azure işlem hatları, kod kapsamını analiz etme

Kodunuzda denetlediğinizde, testlerinizi testleri birlikte yapı sunucusunda diğer ekip üyelerinden çalıştırın. Tüm projeye en güncel ve en kapsamlı resmi almak için Azure işlem hatları kod kapsamını analiz etmek kullanışlıdır. Ayrıca, Otomatik Sistem testleri ve geliştirme makinelerinde genellikle çalıştırma kodlanmış diğer testleri de içerir. Daha fazla bilgi için [derlemelerinizi ile birim testleri çalıştırma](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Komut satırından kod kapsamını analiz etme

Komut satırından testleri çalıştırmak için kullanın *vstest.console.exe*. Kod kapsamı olan bir seçeneği *vstest.console.exe* yardımcı programı.

1. Visual Studio için geliştirici komut istemi başlatın:

   Windows içinde **Başlat** menüsünde seçin **Visual Studio 2017** > **VS 2017 için geliştirici komut istemi**.

2. Komut isteminde aşağıdaki komutu çalıştırın:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Daha fazla bilgi için [VSTest.Console.exe komut satırı seçenekleri](vstest-console-options.md).

## <a name="troubleshoot"></a>Sorun giderme

Kod kapsamı sonuçlarını görmüyorsanız [kod kapsamı sorunlarını giderme](../test/troubleshooting-code-coverage.md) makalesi size yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
- [Kod kapsamı sorunlarını giderme](../test/troubleshooting-code-coverage.md)
- [Birim testi kod](../test/unit-test-your-code.md)
