---
title: Kod ölçümleri IDE veya komut satırından oluşturun
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3f8d6f2df0b0d9ec6e3f9d8ead7fd1e08929f8e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966537"
---
# <a name="how-to-generate-code-metrics-data"></a>Nasıl yapılır: kod ölçümleri verileri üretme

Kod ölçümleri sonuçları bir veya daha fazla proje veya bütün bir çözüm için oluşturabilirsiniz. Kod ölçümleri kullanılabilir Visual Studio etkileşimli geliştirme ortamında (IDE) ve için C# ve Visual Basic projeleri, komut satırına.

Ayrıca, yükleyebileceğiniz bir [NuGet paketini](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) dört kod ölçümlerini içeren [Çözümleyicisi](roslyn-analyzers-overview.md) kuralları: CA1501, CA1502 CA1505 ve CA1506. Bu kurallar varsayılan olarak devre dışıdır, ancak bunları etkinleştirebilirsiniz **Çözüm Gezgini** veya bir [kural kümesi](using-rule-sets-to-group-code-analysis-rules.md) dosya.

## <a name="visual-studio-ide-code-metrics"></a>Visual Studio IDE kod ölçümleri

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Bütün bir çözüm için kod ölçümleri sonuçları oluşturma

Bütün bir çözüm için kod ölçümleri sonuçları aşağıdaki yollardan biriyle oluşturabilirsiniz:

- Menü çubuğundan seçin **Çözümle** > **kod ölçümlerini Hesapla** > **çözüm**.

- İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve ardından **kod ölçümlerini Hesapla**.

- İçinde **kod ölçümleri sonuçları** penceresinde seçin **çözüm için kod ölçümlerini Hesapla** düğmesi.

Sonuçları oluşturulur ve **kod ölçümleri sonuçları** penceresi görüntülenir. Sonuçları ayrıntılarını görüntülemek için ağaç genişletin **hiyerarşi** sütun.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Bir veya daha fazla proje için kod ölçümleri sonuçları oluşturma

1. İçinde **Çözüm Gezgini**, bir veya daha fazla proje seçin.

1. Menü çubuğundan seçin **Çözümle** > **kod ölçümlerini Hesapla** > **seçili projeleri için**.

Sonuçları oluşturulur ve **kod ölçümleri sonuçları** penceresi görüntülenir. Sonuçları ayrıntılarını görüntülemek için ağaç genişletin **hiyerarşi**.

## <a name="command-line-code-metrics"></a>Komut satırı kod ölçümleri

Komut satırı için kod ölçümleri verileri üretme C# ve Visual Basic projeleri .NET Framework, .NET Core ve .NET Standard uygulamaları için. Kod ölçümleri komut satırı araçlarını çağrılır *Metrics.exe*.

Edinme *Metrics.exe* yürütülebilir, gerekir [kendiniz oluşturmak](#generate-the-executable). Yakın gelecekte bir [yayımlanmış sürümü *Metrics.exe* kullanılabilir](https://github.com/dotnet/roslyn-analyzers/issues/1756) bunu kendiniz yapılandırmak zorunda değilsiniz.

### <a name="generate-the-executable"></a>Yürütülebilir dosya oluşturur

Yürütülebilir dosyayı oluşturmak için *Metrics.exe*, şu adımları izleyin:

1. Kopya [roslyn/dotnet-Çözümleyicileri](https://github.com/dotnet/roslyn-analyzers) depo.
2. Geliştirici komut istemi için Visual Studio'yu yönetici olarak açın.
3. Kök klasöründen **roslyn Çözümleyicileri** depo, aşağıdaki komutu yürütün: `Restore.cmd`
4. Dizini *src\Tools*.
5. Oluşturmak için aşağıdaki komutu yürütün **Metrics.csproj** proje:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Adlı bir yürütülebilir dosya *Metrics.exe* içinde oluşturulan *ikili dosyaları* depo kökü altındaki dizin.

   > [!TIP]
   > Oluşturulacak *Metrics.exe* içinde [eski modu](#legacy-mode), aşağıdaki komutu yürütün:
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>Kullanım

Çalıştırılacak *Metrics.exe*, kaynağı bir proje veya çözüm ve bir çıkış XML dosyası bağımsız değişken olarak. Örneğin:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>Çıkış

Oluşturulan XML çıktısı, aşağıdaki biçimi alır:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="tool-differences"></a>Aracı farkları

Visual Studio 2015 dahil olmak üzere Visual Studio'nun önceki sürümleri dahil adında bir komut satırı kod ölçümleri araç *Metrics.exe*. Bu Aracı'nın önceki sürümünü ikili bir analiz, diğer bir deyişle, derleme tabanlı analiz vermedi. Yeni aracı, bunun yerine kaynak kodunu analiz eder. Çünkü yeni *Metrics.exe* sonuçları önceki sürümleri tarafından oluşturulan için farklı kod tabanlı, kaynağıdır *Metrics.exe* ve Visual Studio 2017 IDE içinde.

Yeni *Metrics.exe* çözüm ve proje yüklü olduğu sürece, aracı ölçümleri kaynak kod hataları varsa bile işlem.

#### <a name="metric-value-differences"></a>Ölçüm değeri farkları

`LinesOfCode` Daha doğru ve güvenilir yeni ölçüm *Metrics.exe*. Bu codegen farkları bağımsız ve çalışma zamanı ve araç takımı değiştiğinde değiştirmez. Yeni *Metrics.exe* boş satırlar ve yorumlarla birlikte kod, gerçek satırları sayar.

Gibi diğer ölçümler `CyclomaticComplexity` ve `MaintainabilityIndex` formüller önceki sürümlerini kullanan *Metrics.exe*, ancak yeni *Metrics.exe* sayar `IOperations` (mantıksal Kaynak yönergeleri) yerine Ara dil (IL) yönergeleri. Sayılar önceki sürümlerden biraz farklı olacaktır *Metrics.exe* ve Visual Studio 2017 IDE kod ölçümleri sonuçları.

### <a name="legacy-mode"></a>Eski mod

Ayrıca yapı seçebilirsiniz *Metrics.exe* içinde *eski modu*. Aracı'nın eski modu sürümü oluşturulan aracın eski hangi sürümlerine yakın olan ölçüm değerleri oluşturur. Buna ek olarak, eski modda, *Metrics.exe* aracıyla oluşturulmuş kod ölçümleri için söz konusu önceki sürümlerini yöntemi aynı dizi türleri için kod ölçümleri oluşturur. Örneğin, kod ölçümleri verileri alan ve özellik başlatıcıları için oluşturmaz. Geriye dönük uyumluluk veya kodu iade kapılar varsa sayı kod ölçümlere göre eski modu kullanışlıdır. Derleme için komutu *Metrics.exe* eski modda:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Daha fazla bilgi için [eski modda kod ölçümleri oluşturma etkinleştir](https://github.com/dotnet/roslyn-analyzers/pull/1841).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod ölçümleri sonuçları penceresini kullanma](../code-quality/working-with-code-metrics-data.md)
- [Kod ölçüm değerleri](../code-quality/code-metrics-values.md)