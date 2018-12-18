---
title: Birim testleri bir .runsettings dosyası ile yapılandırma
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 935c1ebfb2efd888de5b336eafab4059fa6cd443
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903562"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Kullanarak birim testlerini yapılandırma bir *.runsettings* dosyası

Kullanarak birim testlerini Visual Studio'da yapılandırılabilir bir *.runsettings* dosya. Örneğin, üzerinde yapılan testler, test sonuçlarını ya da bir test çalıştırması sırasında toplanan verileri için dizin .NET Framework sürümünü değiştirebilirsiniz.

Çalışma ayarları dosyası isteğe bağlıdır. Özel bir yapılandırma gerektirmeyen, ihtiyacınız olmayan bir *.runsettings* dosya. En yaygın kullanımı bir *.runsettings* dosyasıdır özelleştirmek için [kod kapsamı analizi](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Çalıştırma ayarları dosyasını belirtin

Çalıştırma ayarları dosyaları, gelen çalıştırmak testlerini yapılandırma için kullanılabilir [komut satırı](vstest-console-options.md), IDE veya içinde bir [iş akışınızı oluşturma](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) Azure Test planları veya Team Foundation Server (TFS) kullanarak.

### <a name="specify-a-run-settings-file-in-the-ide"></a>IDE içinde çalıştırma ayarları dosyasını belirtin

Seçin **Test** > **Test ayarları** > **Test ayarları dosyasını Seç** seçip *.runsettings*dosya. Dosya çubuğunda görünür **Test ayarları** menü ve seçebilir veya seçimi. Seçili durumdayken, seçtiğiniz her çalışma ayarları dosyası geçerli **kod kapsamı analizi**.

![Visual Studio'da Test ayarları dosyası menüsü seçin](media/select-test-settings-file.png)

### <a name="specify-a-run-settings-file-at-the-command-line"></a>Komut satırına bir çalıştırma ayarları dosyasını belirtin

Komut satırından testleri çalıştırmak için kullanın *vstest.console.exe* kullanarak ayarları dosyasını belirtin **/Settings** parametresi.

1. Visual Studio Geliştirici Komut Satırını başlatın:

   Windows üzerinde **Başlat** menüsünde seçin **Visual Studio 2017** > **VS 2017 için geliştirici komut istemi**.

2. Benzer şekilde bir komut girin:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

Daha fazla bilgi için [VSTest.Console.exe komut satırı seçenekleri](vstest-console-options.md).

## <a name="customize-tests"></a>Testleri özelleştirme

Kullanarak testlerinizi özelleştirmek için bir *.runsettings* dosya, aşağıdaki adımları izleyin:

1. Visual Studio çözümünüze bir XML dosyası ekleyin ve kaydedileceği *test.runsettings*.

   > [!TIP]
   > Uzantı kullandığınız sürece dosya adı önemli değildir *.runsettings*.

1. Aşağıdaki örnek XML'den dosya içeriğini değiştirin ve gerektiği gibi özelleştirin.

1. Üzerinde **Test** menüsünde seçin **Test ayarları** > **Test ayarları dosyasını Seç**. Gözat *.runsettings* dosyası oluşturulur ve ardından **Tamam**.

   > [!TIP]
   > Birden fazla oluşturabilirsiniz *.runsettings* dosya çözümünüzde ve gerektiğinde etkin test ayarları dosyası seçin.

## <a name="example-runsettings-file"></a>Örnek *.runsettings* dosyası

Aşağıdaki XML içeriği tipik bir gösterilir *.runsettings* dosya. Varsayılan değeri olduğundan, dosyanın her öğe isteğe bağlıdır.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from menu Test > Test Settings > Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector is only available with Visual Studio 2017 version 15.5 and higher -->
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="elements-of-a-runsettings-file"></a>Öğeleri bir *.runsettings* dosyası

Aşağıdaki bölümlerde ayrıntılı öğelerini bir *.runsettings* dosya.

### <a name="run-configuration"></a>Çalıştırma yapılandırma

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

**RunConfiguration** öğesi, aşağıdaki öğeleri içerebilir:

|Düğüm|Varsayılan|Değerler|
|-|-|-|
|**ResultsDirectory**||Test sonuçlarını yerleştirildiği dizin.|
|**targetFrameworkVersion**|Framework40|Framework35, Framework40, Framework45<br /><br />Bu ayar, bulmak ve testleri yürütmek için kullanılan birim test çerçevesi sürümünü belirtir. Birim test projesinin yapı özelliklerinde belirttiğiniz .NET platformu sürümünden farklı olabilir.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|yanlış, doğru|
|**TestAdaptersPaths**||Bir veya daha fazla yol TestAdapters bulunduğu dizine|
|**MaxCpuCount**|1.|Bu, birim testleri çalıştırma ayarı paralel test yürütme düzeyini denetler, makinede kullanılabilir çekirdek kullanarak. Test yürütme altyapısının kullanılabilir her Çekirdekte ayrı bir işlem olarak başlar ve her çekirdek ile testleri çalıştırmak için bir kapsayıcı sağlar. Bir kapsayıcı, bir derleme, DLL veya ilgili yapıt olabilir. Zamanlama birimi test kapsayıcısıdır. Her bir kapsayıcıda test çerçevesi göre testler çalıştırılır. Çok sayıda kapsayıcı varsa, ardından bir kapsayıcı içinde testleri çalıştırma bitiş işlediği gibi bunlar sonraki kullanılabilir kapsayıcı verilir.<br /><br />MaxCpuCount olabilir:<br /><br />1 burada n < = n < = çekirdek sayısı: n işlemlerinin tasarrufundadır başlattı<br /><br />n, burada n herhangi bir değer =: işlem sayısı, kullanılabilir çekirdek sayısı kadar olabilir|
|**TestSessionTimeout**||Kullanıcıların belirli bir zaman aşımı aştığında bir sınama oturumu sonlandırmak olanak tanır. Bir süre için ayar kaynakları da tüketilir bir zaman aşımı sağlar ve test oturumları kısıtlanmıştır. Ayar kullanılabilir **Visual Studio 2017 sürüm 15.5** ve daha sonra.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Tanılama veri bağdaştırıcıları (veri toplayıcıları)

**DataCollectors** öğesi tanılama veri bağdaştırıcılarının ayarlarını belirtir. Tanılama veri bağdaştırıcılarını ve ortam test altındaki uygulama hakkında ek bilgi toplayın. Her bağdaştırıcı varsayılan ayarlara sahiptir ve yalnızca varsayılan değerleri kullanmak istemiyorsanız ayarları sağlamanız gerekir.

#### <a name="code-coverage-adapter"></a>Kod kapsamı bağdaştırıcısı

```xml
<CodeCoverage>
    <ModulePaths>
        <Exclude>
            <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
    </ModulePaths>

    <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
    <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
    <CollectFromChildProcesses>True</CollectFromChildProcesses>
    <CollectAspDotNet>False</CollectAspDotNet>
</CodeCoverage>
```

Kod kapsamı veri toplayıcısı uygulama kodu bölümlerinin testte uygulandığı bir günlük oluşturur. Kod kapsamının ayarlarını özelleştirme hakkında daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Video veri toplayıcı

Testler varken ekran kaydı video veri toplayıcı yakalar. Bu kayıt, UI testlerine ilişkin sorun giderme için kullanışlıdır. Video veri toplayıcı kullanılabilir **Visual Studio 2017 sürüm 15.5** ve daha sonra.

Başka türde bir tanılama veri bağdaştırıcıları özelleştirmek için bir [test ayarları dosyası](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
</TestRunParameters>
```

Test çalıştırması parametreleri, değişkenler ve testlere çalışma zamanında kullanılabilir olan değerler tanımlamak için bir yol sağlar. Kullanarak parametreleri erişim <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> özelliği:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Test çalıştırması parametrelerini kullanmak için özel bir ekleme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> alan ve ortak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> test sınıfınıza özelliği.

### <a name="mstest-run-settings"></a>MSTest çalıştırma ayarları

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Bu ayarlar sahip test yöntemlerini çalıştıran test bağdaştırıcısına özgüdür <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliği.

|Yapılandırma|Varsayılan|Değerler|
|-|-|-|
|**ForcedLegacyMode**|false|Visual Studio 2012'de, MSTest bağdaştırıcısı daha hızlı ve daha ölçeklenebilir hale getirilmiş. Testlerin çalışma sırası gibi bazı davranışlar Visual Studio'nun önceki sürümlerindekiyle aynı olmayabilir. Bu değer kümesine **true** eski test bağdaştırıcısı kullanmak için.<br /><br />Örneğin, varsa bu ayarı kullanabilirsiniz bir *app.config* birim testi için belirtilen dosya.<br /><br />Daha yeni bağdaştırıcı kullanmanıza olanak vermek için testlerinizi yeniden düzenlemenizi öneririz.|
|**IgnoreTestImpact**|false|MSTest veya Microsoft Test Yöneticisi'nde çalıştırıldığında test etkisi özelliği son değişikliklerden etkilenen testleri önceliklendirir. Bu ayar özelliği devre dışı bırakır. Daha fazla bilgi için [önceki derlemeden sonra hangi testlerin çalıştırılmalıdır](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Burada MSTest bağdaştırıcısı ile kullanmak için test ayarları dosyası belirtebilirsiniz. Test ayarları dosyasını seçerek belirtebilirsiniz **Test** > **Test ayarlarını** > **Test ayarları dosyasını Seç**.<br /><br />Bu değeri belirtirseniz, aynı zamanda ayarlamalısınız **ForcedlegacyMode** için **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Test çalıştırması tamamlandıktan sonra MSTest kapatılır. Testin bir parçası da sonlandırılan olarak başlatılan bir işlem. Test yürütücüsünü Canlı tutmak istiyorsanız, değer kümesine **true**. Örneğin, tarayıcının kodlanmış UI testleri arasında çalışmasını tutmak için bu ayarı kullanabilirsiniz.|
|**DeploymentEnabled**|true|Değeri ayarlamanız **false**, test yönteminizde belirttiğiniz dağıtım öğeleri dağıtım dizinine kopyalanır değil.|
|**CaptureTraceOutput**|true|Hata ayıklama, test yöntemi kullanmanızı yazabileceğiniz <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Bu değer bir test çalıştırması tamamlandıktan sonra dağıtım Dizini'ni için kümesine **false**.|
|**MapInconclusiveToFailed**|false|Bir test yetersiz durum tamamlanırsa atlandı durumuna eşlenir **Test Gezgini**. Yetersiz testlerin başarısız olarak gösterilmesini istiyorsanız değerine **true**.|
|**InProcMode**|false|Testlerinizin aynı işlemde MSTest bağdaştırıcısı olarak çalıştırmak istiyorsanız, bu değeri ayarlamak **true**. Bu ayar, küçük bir performans kazancı sağlar. Ancak bir özel durum ile bir test varsa, kalan testleri çalıştırma.|
|**AssemblyResolution**|false|Bulma ve birim testlerini çalıştırırken ek derlemeler için yol belirtebilirsiniz. Örneğin, test derlemesi ile aynı dizinde değil bağımlılık derlemeler için bu yolları kullanın. Bir yol belirtmek için kullanın. bir **dizin yolu** öğesi. Yolları, ortam değişkenleri içerebilir.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
- [Visual Studio test görevi (Azure Test planları)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
