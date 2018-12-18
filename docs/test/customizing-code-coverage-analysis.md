---
title: Kod Kapsamı Çözümlemeyi Özelleştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 09af57ca64524dafa506d57d486e9385a4c35a93
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054952"
---
# <a name="customize-code-coverage-analysis"></a>Kod kapsamı analizini özelleştirme

Varsayılan olarak, birim testleri sırasında yüklenen tüm çözüm derlemelerine kod kapsamı analiz eder. Çoğu zaman iyi çalıştığı için bu varsayılan davranışı kullanmanızı öneririz. Daha fazla bilgi için [ne kadar kod test belirlemek için kod kapsamı kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Kod kapsamı sonuçları test kodu hariç ve yalnızca uygulama kodu eklemek için aşağıdakileri ekleyin <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> test sınıfı özniteliği.

Dahil etmek, çözümünüzün bir parçası olmayan derlemeler için elde *.pdb* bu derlemeler için dosyaları ve derleme olarak aynı klasöre kopyalayın *.dll* dosyaları.

## <a name="run-settings-file"></a>Çalışma ayarları dosyası

[Çalışma ayarları dosyası](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) birim testi araçları tarafından kullanılan yapılandırma dosyasıdır. Gelişmiş kod kapsamı ayarları içinde belirtilmiş bir *.runsettings* dosya.

Kod kapsamını özelleştirmek için aşağıdaki adımları izleyin:

1. Çalıştırma ayarları dosyasını çözümünüze ekleyin. İçinde **Çözüm Gezgini**, çözümünüzün kısayol menüsünde **Ekle** > **yeni öğe**seçip **XML dosyası**. Dosyayı gibi bir adla kaydetme *CodeCoverage.runsettings*.

1. İçerik bu makalenin sonunda örnek dosyası ekleyin ve sonra gereksinimleriniz için aşağıdaki bölümlerde açıklandığı şekilde özelleştirin.

1. Çalışma ayarları dosyası seçilecek **Test** menüsünde seçin **Test ayarları** > **Test ayarları dosyasını Seç**. Testleri komut satırından veya derleme iş akışında çalıştırmak için çalıştırma ayarları dosyasını belirtmek için bkz: [kullanarak birim testlerini yapılandırma bir *.runsettings* dosya](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file).

   Seçtiğinizde, **kod kapsamı analizi**, yapılandırma bilgilerini çalışma ayarları dosyasından okunur.

   > [!TIP]
   > Testleri çalıştırmak veya kodunuzu güncelleştirdiğinizde önceki kod kapsamı sonuçlarını ve kod renklendirme otomatik olarak gizli değildir.

Özel ayarlar kapatın ve açın, seçimini kaldırın veya dosyayı seçin **Test** > **Test ayarları** menüsü.

![Özel ayarlar dosya ile test ayarları menüsü](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Sembol arama yollarını belirtin

Kod kapsamı sembol dosyalarını gerektirir (*.pdb* dosyaları) derlemeler için. Çözümünüz tarafından oluşturulmuş derlemeler için simge dosyaları genellikle ikili dosyaların yanı sıra varsa ve kod kapsamı otomatik olarak çalışır. Ancak bazı durumlarda, kod kapsamı çözümlemenizde başvurulmuş derlemeleri eklemek isteyebilirsiniz. Bu gibi durumlarda *.pdb* dosyaları ikili bitişik olmayabilir ve sembol arama yolu belirtebilirsiniz *.runsettings* dosya.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Sembol çözümleme zaman alabilir özellikle birçok derlemeleri ile bir uzak dosya konumu kullanırken. Bu nedenle, kopyalamayı düşünün *.pdb* aynı yerel konuma ikili dosyaları (*.dll* ve *.exe*) dosyaları.

### <a name="exclude-and-include"></a>Dahil ve hariç tut

Belirtilen derleme kod kapsamını çözümleme dışı bırakabilirsiniz. Örneğin:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Alternatif olarak, hangi derlemelerin dahil edileceğini belirtebilirsiniz. Bu yaklaşımın daha fazla derlemeleri çözümü eklediğinizde dezavantajı vardır, listeye eklemeyi unutmamalısınız:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Varsa **INCLUDE** kod kapsamı işleme yüklenen ve tüm derlemeleri içerir sonra boştur *.pdb* dosyaları bulunabilir. Kod kapsamı yan tümcesinde eşleşen öğeleri içermez bir **hariç** listesi.

**Dahil** önce işlenen **hariç**.

### <a name="regular-expressions"></a>Normal ifadeler

Dahil ve hariç düğümler normal ifadeler kullanır. Daha fazla bilgi için [Visual Studio'da normal ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md). Normal ifadeler joker karakterler ile aynı değildir. Özellikle:

- **. \\** * herhangi bir karakter dizesi ile eşleşir

- **\\.** eşleşen bir nokta ".")

- **\\( \\)** eşleşen parantez "(")

- **\\\\** eşleşen bir dosya yolu sınırlayıcı "\\"

- **^** dizenin başlangıcıyla eşleşir

- **$** Dize sonu ile eşleşir

Tüm eşlemeler büyük/küçük harf duyarsızdır.

Örneğin:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> Atlanmayan veya eşleşmeyen parantezler gibi normal bir ifadede bir hata varsa kod kapsamı çözümleme çalışmaz.

### <a name="other-ways-to-include-or-exclude-elements"></a>Öğeleri içerecek veya dışlayacak diğer yollar

- **ModulePath** -derleme dosyası yolu tarafından belirtilen derlemeler eşleşir.

- **CompanyName** -tarafından derlemeler eşleşir **şirket** özniteliği.

- **PublicKeyToken** -imzalı derlemeler ortak anahtar belirteci tarafından eşleşir.

- **Kaynak** -bunlar tanımlandığı kaynak dosyasının yolu adıyla eşleşen öğeler.

- **Öznitelik** -belirli bir özniteliği bağlı öğeleri ile eşleşir. Özniteliğin tam adını belirtin ve adın sonunda "öznitelik" dahil.

- **İşlev** -yordamları, işlevleri veya yöntemleri tam adıyla eşleştirir. Normal ifade bir işlev adı ile eşleşmesi için ad alanı, sınıf adı, yöntem adı ve parametre listesine dahil olmak üzere, işlevinin tam adı eşleşmelidir. Örneğin:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

   ```xml
   <Functions>
     <Include>
       <!-- Include methods in the Fabrikam namespace: -->
       <Function>^Fabrikam\..*</Function>
       <!-- Include all methods named EqualTo: -->
       <Function>.*\.EqualTo\(.*</Function>
     </Include>
     <Exclude>
       <!-- Exclude methods in a class or namespace named UnitTest: -->
       <Function>.*\.UnitTest\..*</Function>
     </Exclude>
   </Functions>
   ```

## <a name="sample-runsettings-file"></a>Örnek .runsettings dosyası

Bu kodu kopyalayın ve ihtiyaçlarınıza uyacak şekilde düzenleyin.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalıştırma ayarları dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Ne kadar kod test belirlemek için kod kapsamını kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Birim testi kod](../test/unit-test-your-code.md)