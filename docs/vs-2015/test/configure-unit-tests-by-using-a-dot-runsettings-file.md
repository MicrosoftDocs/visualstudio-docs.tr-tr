---
title: .Runsettings dosyasını kullanarak birim testlerini yapılandırma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7e9e4a2-5d01-4f78-b408-5be3892bd162
caps.latest.revision: 28
ms.author: gewarren
manager: douge
ms.openlocfilehash: 806c19b7132a4541ff97c253700a5e5e980ef556
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817983"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>.runsettings dosyasını kullanarak birim testlerini yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da birim testlerini *.runsettings dosyası kullanılarak yapılandırılabilir. ('.Runsettings.' uzantısı kullandığınız sağlanan dosya adı, önemli değildir) Örneğin, üzerinde testler çalıştırılacak, .NET Framework burada test sonuçlarının teslim edildiği ve test sırasında toplanan verileri çalıştırma dizini değiştirebilirsiniz.  
  
 Özel bir yapılandırma gerçekleştirmek istiyorsanız, bir *.runsettings dosyası gerekmez. Özelleştirme için sıkça kullanılır [kod kapsamı](../test/customizing-code-coverage-analysis.md).  
  
> [!NOTE]
>  **.runsettings ve .testsettings**  
>   
>  Testleri yapılandırma dosyasının iki türü vardır. *.runsettings birim testleri için kullanılır. Ve \*için .testsettings [laboratuvar ortamında test](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901), web performansı ve yük testleri ve IntelliTrace ve olay günlüğünü bağdaştırıcıları gibi tanılama veri bağdaştırıcılarının bazı türlerini özelleştirme.  
>   
>  Visual Studio 2010'da, en fazla birim testleri de *.testsettings dosyalarını kullanarak özelleştirilmiş önceki sürümleri. Yine de bunu yapabilirsiniz, ancak testleri eşdeğer yapılandırmalarında kullanıyorsanız daha yavaş çalışır bir \*.runsettings dosyası.  
  
## <a name="customizing-tests-with-a-runsettings-file"></a>Bir .runsettings dosyası ile testleri özelleştirme  
  
1. Visual Studio çözümünüze bir XML dosyası ekleyin ve test.runsettings için yeniden adlandırın. (Dosya adı önemli değildir, ancak .runsettings uzantısı olması gerekir.)  
  
2. Dosya içeriğini ile değiştirin [örnek](#example).  
  
    Kendi gereksinimlerine göre düzenleyin.  
  
3. Üzerinde **Test** menüsünde seçin **Test ayarları**, **Test ayarları dosyasını Seç**.  
  
   Birden fazla oluşturabilirsiniz \*.runsettings dosyası çözümünüze etkinleştirin veya onları farklı zamanlarda devre dışı bırakmak için **Test ayarları** menüsü.  
  
   ![Çalıştırma ayarları dosyasını etkinleştirmeden](../test/media/runsettings-1.png "RunSettings-1")  
  
##  <a name="example"></a> Bu örnek .runsettings dosyasını kopyalayın  
 Tipik *.runsettings dosyası aşağıda verilmiştir. Her değerin bir varsayılanı olduğundan, dosyanın her bir öğesi isteğe bağlıdır.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<RunSettings>  
  <!-- Configurations that affect the Test Framework -->  
  <RunConfiguration>  
    <MaxCpuCount>1</MaxCpuCount>  
    <!-- Path relative to solution directory -->  
    <ResultsDirectory>.\TestResults</ResultsDirectory>  
  
    <!-- [x86] | x64    
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->  
    <TargetPlatform>x86</TargetPlatform>  
  
    <!-- Framework35 | [Framework40] | Framework45 -->  
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>  
  
    <!-- Path to Test Adapters -->  
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>  
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
  
 .Runsettings dosyası da yapılandırmak için kullanılan [kod kapsamı](../test/customizing-code-coverage-analysis.md).  
  
 Bu konunun geri kalanı dosya içeriğini açıklamaktadır.  
  
## <a name="edit-your-runsettings-file"></a>.runsettings dosyanızı düzenleme  
 .Runsettings dosyası aşağıdaki öğelere sahiptir.  
  
### <a name="test-run-configuration"></a>Test çalıştırma yapılandırması  
  
|Düğüm|Varsayılan|Değerler|  
|----------|-------------|------------|  
|`ResultsDirectory`||Test sonuçlarının yerleştirileceği dizin.|  
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Bu birim test çerçevesinin hangi sürümünün testlerini bulmak ve yürütmek için kullanıldığını belirtir. Birim test projesinin yapı özelliklerinde belirttiğiniz .NET platformu sürümünden farklı olabilir.|  
|`TargetPlatform`|x86|x86, x64|  
|`TreatTestAdapterErrorsAsWarnings`|false|yanlış, doğru|  
|`TestAdaptersPaths`||Bir veya birden çok yol TestAdapters bulunduğu dizine|  
|`MaxCpuCount`|1.|Bu denetimleri birim çalıştırırken paralel test yürütme derecesini, makinede kullanılabilir çekirdek kullanarak test eder.  Test yürütme altyapısının kullanılabilir her Çekirdekte ayrı bir işlem olarak başlar ve her çekirdek ile bir derleme, DLL veya ilgili yapıt gibi çalışması için testleri bir kapsayıcı sağlar.  Zamanlama birimi test kapsayıcısıdır.  Her bir kapsayıcıda test çerçevesi göre testler çalıştırılır.  Çok sayıda kapsayıcı varsa, ardından bir kapsayıcı içinde testleri çalıştırma bitiş işlerken kendisine sonraki kullanılabilir kapsayıcı verilir.<br /><br /> MaxCpuCount olabilir:<br /><br /> 1 burada n < = n < = çekirdek sayısı: n işlemlerinin tasarrufundadır başlatılır<br /><br /> n, burada n herhangi bir değer =: işlem sayısı, makinede kadar kullanılabilir adede kadar çekirdek olacaktır|  
  
### <a name="diagnostic-data-adapters-data-collectors"></a>Tanılama Veri Bağdaştırıcıları (Veri Toplayıcıları)  
 `DataCollectors` Öğesi tanılama veri bağdaştırıcılarının ayarlarını belirtir. Tanılama veri bağdaştırıcıları, test uygulanmakta olan uygulama ve ortam hakkında ek bilgi toplamak için kullanılır. Her bağdaştırıcı varsayılan ayarlara sahiptir ve yalnızca varsayılan değerleri kullanmak istemiyorsanız ayarları sağlamanız gerekir.  
  
#### <a name="code-coverage-adapter"></a>Kod kapsamı bağdaştırıcısı  
 Kod kapsamı veri toplayıcısı uygulama kodu bölümlerinin testte uygulandığı bir günlük oluşturur. Kod kapsamının ayarlarını özelleştirme hakkında daha fazla bilgi için bkz. [kod kapsamı çözümlemeyi özelleştirme](../test/customizing-code-coverage-analysis.md).  
  
#### <a name="other-diagnostic-data-adapters"></a>Diğer tanılama veri bağdaştırıcıları  
 Kod kapsamı bağdaştırıcısı şu anda çalışma ayarları dosyası kullanılarak özelleştirilebilen tek bağdaştırıcıdır.  
  
 Başka herhangi bir tür tanılama verisi bağdaştırıcısını özelleştirmek için test ayarları dosyası kullanmanız gerekir. Daha fazla bilgi için [Visual Studio testleri için Test ayarlarını belirtme](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901).  
  
#### <a name="testrunparameters"></a>TestRunParameters  
 TestRunParameters değişkenleri ve testlere çalışma zamanında kullanılabilir olan değerler tanımlamak için bir yol sağlar.  
  
### <a name="mstest-run-settings"></a>MSTest Çalıştırma Ayarları  
 Bu ayarlar sahip test yöntemlerini çalıştıran test bağdaştırıcısına özgüdür `[TestMethod]` özniteliği.  
  
|Yapılandırma|Varsayılan|Değerler|  
|-------------------|-------------|------------|  
|ForcedLegacyMode|false|Visual Studio 2012'de, MSTest bağdaştırıcısı daha hızlı ve daha ölçeklenebilir olması için iyileştirilmiştir. Testlerin çalışma sırası gibi bazı davranışlar Visual Studio'nun önceki sürümlerindekiyle aynı olmayabilir. Bu değer `true` eski test bağdaştırıcısı kullanmak için.<br /><br /> Örneğin, birim testi için belirtilen bir app.config dosyanız varsa bunu kullanabilirsiniz.<br /><br /> Daha yeni bağdaştırıcı kullanmanıza olanak vermek için testlerinizi yeniden düzenlemenizi öneririz.|  
|IgnoreTestImpact|false|MSTest veya Microsoft Test Yöneticisi'nde çalıştırıldığında test etkisi özelliği son değişikliklerden etkilenen testleri önceliklendirir. Bu ayar özelliği devre dışı bırakır. Daha fazla bilgi için [nasıl yapılır: kod değişikliklerinden sonra çalıştırmak, testleri gerektiğini denetlemek için veri toplamaya olması](http://msdn.microsoft.com/library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|  
|SettingsFile||Burada MS Test bağdaştırıcısı ile kullanmak için test ayarları dosyası belirtebilirsiniz. Menüsünü kullanarak bir test ayarları dosyası da belirtebilirsiniz **Test**, **Test ayarlarını**, **Test ayarları dosyasını Seç**.<br /><br /> Bu değeri belirtirseniz, aynı zamanda ayarlamalısınız **ForcedlegacyMode** için **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|  
|KeepExecutorAliveAfterLegacyRun|false|Test çalıştırması tamamlandıktan sonra MSTest kapatılır. Testin bir parçası olarak başlatılan tüm işlemler de şu anda bitirilecek. Test yürütücüsünü canlı tutmak istiyorsanız bu yapılandırmayı doğru olarak etkinleştirin.<br /><br /> Örneğin, tarayıcının kodlanmış UI testleri arasında çalışmasını sürdürmek için bunu kullanabilirsiniz.|  
|DeploymentEnabled|true|Bunu yanlış olarak ayarlarsanız, test yönteminizde belirttiğiniz dağıtım öğeleri dağıtım dizinine kopyalanmaz.|  
|CaptureTraceOutput|true|Trace.WriteLine kullanarak Test yönteminizden hata ayıklama izine yazabilirsiniz. Bu yapılandırmayı kullanarak bu hata ayıklama izlemelerini kapatabilirsiniz.|  
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Dağıtım Dizini'ni, bu değeri yanlış olarak ayarlayarak bir test çalıştırdıktan sonra koruyabilirsiniz.|  
|MapInconclusiveToFailed|false|Bir test, yetersiz durum getirirse genellikle Test Gezgini'nde Atlandı durumuna eşlenir. Yetersiz testlerin Başarısız olarak gösterilmesini istiyorsanız bu yapılandırmayı kullanın.|  
|InProcMode|false|MS Test bağdaştırıcısı olarak testlerinizin aynı işlemde çalıştırılmasını isterseniz bu değeri doğru olarak ayarlayın. Bu ayar, küçük bir performans kazancı sağlar. Ancak özel durum içeren bir test varsa, diğer testler devam etmez.|  
|AssemblyResolution|false|Bulma ve birim testlerini çalıştırırken ek derlemeler için yol belirtebilirsiniz.  Örneğin, test derlemesi ile aynı dizinde bulunan yoksa bağımlılık derlemeler için bu yolları kullanın.  Bir yol belirtmek için "Dizin yolu" öğesini kullanın.  Yolları, ortam değişkenleri içerebilir.<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod kapsamı çözümlemeyi özelleştirme](../test/customizing-code-coverage-analysis.md)   
 [Visual Studio testleri için test ayarlarını belirtme](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)



