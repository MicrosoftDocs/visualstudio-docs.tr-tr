---
title: Live Unit Testing SSS
ms.date: 2017-10-03
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 2c0c81bc8413b9d1698e2ad7c21d0d9f397834ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849079"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing sık sorulan sorular

## <a name="latest-features"></a>En son özellikleri
**Live Unit Testing geliştirildi ve düzenli olarak geliştirilmiştir. En yeni özellikler ve geliştirmeler hakkında bilgi nasıl bulabilirim?**

Live Unit Testing için Visual Studio 2017 sürüm 15.3 itibaren yapılan geliştirmeleri ve yeni özellikleri hakkında bilgi edinmek için bkz. [Live Unit Testing yenilikler](live-unit-testing-whats-new.md).

## <a name="supported-frameworks-and-versions"></a>Desteklenen çerçeveler ve sürümler
**Hangi test çerçevelerini mu Live Unit Testing Desteği ve en düşük desteklenen sürümlerle nelerdir?**

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim test çerçeveleri ile çalışır. Desteklenen en düşük sürüm bağdaştırıcılarının ve çerçeveleri de tabloda listelenir. Birim testi çerçevelerini NuGet.org adresinden tüm kullanılabilir.

<table>
<tr>
   <th>Test çerçevesi</th>
   <th>Visual Studio bağdaştırıcısı en düşük sürüm</th>
   <th>Framework en düşük sürüm</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.Runner.VisualStudio sürüm 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>3.5.1 NUnit3TestAdapter sürümü</td>
   <td>NUnit 3.5.0 sürümü</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Eski MSTest tabanlı test varsa, bu başvuruyu projeleri `Microsoft.VisualStudio.QualityTools.UnitTestFramework` ve yeni MSTest NuGet paketleri, Visual Studio 2017 sürüm 15.4 yükseltme için taşımak istediğiniz yok.

Bazı durumlarda, açıkça için Live Unit Testing çalışmaya sırayla çözümde proje tarafından başvurulan NuGet paketlerini geri yüklemek gerekebilir. Çözümün belirtik bir derleme yaparak ya da paketlerin geri yükleyebilirsiniz (seçin **derleme**, **çözümü yeniden derle** en üst düzey Visual Studio menüsünde), veya çözüme sağ tıklayarak ve seçme **NuGet paketlerini geri yükle** Living birim testi etkinleştirmeden önce.

## <a name="net-core-support"></a>.NET core desteği
**Live Unit Testing, .NET Core ile çalışır mı?**

Evet. Live Unit Testing, .NET Core ve .NET Framework ile çalışır. .NET Core desteği, en son Visual Studio 2017 sürüm 15.3 eklendi. .NET Core için Live Unit Testing Desteği istiyorsanız Visual Studio'nun bu sürümüne yükseltin.

## <a name="configuration"></a>Yapılandırma
**Live Unit Testing etkinleştirmeden olduğunda neden çalışmıyor?**

**Çıkış penceresine** (Live Unit Testing açılan seçildiğinde) neden Live Unit Testing çalışmıyor söyleyecektir. Live Unit Testing aşağıdaki nedenlerden biri için çalışmayabilir:

- Çözümde bir proje tarafından başvurulan NuGet paketlerini geri yüklenmedi, Live Unit Testing çalışmaz. Çözümün belirtik bir derleme işlemi gerçekleştirirken veya Live Unit Testing kapatmadan önce çözümdeki NuGet paketlerini geri yüklemek bu sorunu çözecektir.

- MSTest tabanlı testler projelerinizde kullanıyorsanız, başvuru kaldırmayı unutmayın `Microsoft.VisualStudio.QualityTools.UnitTestFramework`ve en son MSTest NuGet paket başvuruları ekleyin `MSTest.TestAdapter` (1.1.11 en eski bir sürümü gereklidir) ve `MSTest.TestFramework` (en düşük sürüm ' ın 1.1.11 gereklidir). Daha fazla bilgi için "Desteklenen test çerçevelerini" bölümüne bakın. [kullanım Live Unit Testing Visual Studio 2017 Enterprise sürümünde](live-unit-testing.md#supported-test-frameworks) makalesi.

- Çözümünüzdeki en az bir proje, NuGet başvurusu veya xUnit, NUnit, doğrudan başvuru olmalıdır veya MSTest test çerçevesi. Bu projeye karşılık gelen bir Visual Studio test bağdaştırıcısı NuGet paketini de başvurmalıdır. Visual Studio test bağdaştırıcısı aracılığıyla da başvurulabilen bir *.runsettings* dosya. *.Runsettings* dosya, aşağıdaki örneğe benzer bir giriş olmalıdır:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Yükseltmeden sonra yanlış kapsamı
**Neden Visual Studio projelerinizde desteklenen sürümüne başvurulan test bağdaştırıcısı yükselttikten sonra Live Unit Testing yanlış kapsamı gösteriyor mu?**

- Birden çok proje çözümü başvurusu NuGet bağdaştırıcı paketini test ettiğinizde, bunların her birini desteklenen sürüme yükseltilmelidir.

- MSBuild emin *.props* test bağdaştırıcısı paketten içe dosyası doğru şekilde güncelleştirilir de. NuGet Paket sürümü/yol genellikle aşağıdaki gibi proje dosyasının en üstüne yakın bulunabilir içeri aktarma denetleyin:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Derlemeleri özelleştirme
**Live Unit Testing derlemelerim özelleştirebilirim?**

Çözümünüzü "Normal" belgelenmiş derleme için gerekli olmayan alt yapısı (Live Unit Testing) oluşturmak için özel aşamanın sonra kod projenize ekleyin veya *.targets* denetleyen dosyaları`BuildingForLiveUnitTesting` özelliğini ve özel ön/son derleme adımları gerçekleştirir. Ayrıca, (yayımlama veya paketleri oluşturma gibi) belirli derleme adımları kaldırın veya bu proje özelliğini temel alarak bir Live Unit Testing derleme (Önkoşullar kopyalama gibi) derleme adımları eklemek için de seçebilirsiniz. Tuto vlastnost nelze upravovat temel yapı özelleştirme normal yapı hiçbir şekilde değiştirmez ve Live Unit Testing yapıları yalnızca etkiler.

Örneğin, normal bir yapı sırasında NuGet paketlerini üreten bir hedef olabilir. NuGet paketlerini yaptığınız her düzenlemeden sonra oluşturulacak büyük olasılıkla istemezsiniz. Bu nedenle, hedefleyen Live Unit Testing yapı aşağıdaki gibi yaparak devre dışı bırakabilirsiniz:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Hata iletileri ile &lt;OutputPath&gt; veya &lt;OutDir&gt;
**Neden alabilirim şu hatayı Live Unit Testing çözümüm oluşturmaya çalıştığında: ".. koşulsuz olarak ayarlanacak .appears `<OutputPath>` veya `<OutDir>`. Live Unit Testing testleri çıkış bütünleştirilmiş koddan yürütülmez"?**

Çözümünüz için yapı işlemini koşulsuz kılıyorsa, bu hatayı alabilirsiniz `<OutputPath>` veya `<OutDir>` dizininin bir alt olmaması `<BaseOutputPath>`. De derleme yapıtları altında bir klasöre bırakılan emin olmak için bu değerleri geçersiz kılar çünkü böyle durumlarda, Live Unit Testing çalışmaz `<BaseOutputPath>`. Derleme yapıtlarınızı normal bir yapı içinde bırakılacak, geçersiz kılmak istediğiniz yeri geçersiz kılmanız gerekir, `<OutputPath>` göre koşullu `<BaseOutputPath>`.

Örneğin, yapınızın kılıyorsa `<OutputPath>` aşağıda gösterildiği gibi:

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

sonra aşağıdaki XML olarak değiştirebilirsiniz:

```xml 
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Bu, sağlar `<OutputPath>` içinde kaynaklandığını `<BaseOutputPath>` klasör.

Geçersiz `<OutDir>` doğrudan yapı işleminizde; geçersiz kılma `<OutputPath>` bunun yerine belirli bir konuma derleme yapıtları bırakmak.

## <a name="set-the-location-of-build-artifacts"></a>Derleme yapıtları konumunu ayarlama
**Altında varsayılan konumu yerine belirli bir konuma gitmek için Live Unit Testing derleme yapıtları istiyorum *.vs* klasör. Bu sorunu nasıl değiştirebilirim?**

Ayarlama `LiveUnitTesting_BuildRoot` istediğiniz Live Unit Testing derleme yapıtlarını bırakılan yola kullanıcı düzeyinde ortam değişkeni. 

## <a name="test-explorer-vs-live-unit-testing-test-runs"></a>Explorer vs test edin. Live Unit Testing test çalıştırmaları 
**Nasıl testleri Test Gezgini penceresinden testleri Live Unit Testing içinde çalışan farklı mı çalışıyor?**

Bazı farklılıklar vardır:

- Çalıştırılırken veya hata ayıklama testlerden **Test Gezgini** penceresinde çalışır normal ikili dosyaları, izleme eklenmiş ikili dosyalar Live Unit Testing çalıştırılır. İzleme eklenmiş ikili dosyaların hatalarını ayıklamak isterseniz ekleyerek bir [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) test yönteminizde yöntem çağrısında yöntemi (ne zaman Live Unit Testing tarafından yürütülür dahil) yürütülür ve daha sonra herhangi bir zamanda başlatmak hata ayıklayıcı neden olur ekleme ve izleme eklenmiş ikili hatalarını ayıklayın. Ancak, çoğu kullanıcı senaryolarının saydam izleme ve hata ayıklama gerekmez izleme eklenmiş ikili dosyalar Hedefimiz olur.

- Live Unit Testing testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, ancak testleri çalıştırın **Test Gezgini** penceresi, yeni bir uygulama etki alanı oluşturun.

- Live Unit Testing çalışan testler her test derlemesindeki ardışık olarak ise birden çok testleri çalıştırırsanız **Test Gezgini** penceresi ve seçili **çalıştırmak testlerini paralel** düğmesi, bunların çalıştırılacağı Paralel.

- 2. sürümünü kullanır ve testleri Live Unit Testing yürütülmesi `TestPlatform`bilgileriyse **Test Gezgini** penceresi, sürüm 1 kullanır. Ancak çoğu durumda, bir fark dikkat olmaz.

- **Test Gezgini** Live Unit Testing testleri bir çok iş parçacıklı apartmanda (MTA) çalıştırılır testler varsayılan olarak, bir tek iş parçacıklı apartmanda (STA) şu anda çalışır. Live Unit Testing STA MSTest testleri çalıştırmak için test yöntemi veya kapsayan sınıfı ile donatmak `<STATestMethod>` veya `<STATestClass>` bulunabilir özniteliği `MSTest.STAExtensions 1.0.3-beta` NuGet paketi. NUnit için test yönteminin süslemek `<RequiresThread(ApartmentState.STA)>` özniteliği ve xUnit, ile `<STAFact>` özniteliği.

## <a name="exclude-tests"></a>Testleri Dışla
**Testleri Live Unit Testing içinde katılmalarını nasıl dışlansın mı?**

"Dahil etme ve dışlama projelerin test ve test yöntemleri" bölümüne bakın [kullanım Live Unit Testing Visual Studio 2017 Enterprise sürümünde](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) makale için kullanıcıya özgü ayarları. Testleri veya belirli düzenleme oturumu için testleri belirli bir kümesini çalıştırmak için veya kişisel tercihlerinize kalıcı hale getirmek için istediğiniz zaman yararlıdır.
 
Çözüme özel ayarlar için uyguladığınız <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> Live Unit Testing ile izleme eklenmiş gelen yöntemler, özellikler, sınıflar veya yapılar programlı olarak hariç tutmak için özniteliği. Buna ek olarak da ayarlayabilirsiniz `<ExcludeFromCodeCoverage>` özelliğini `true` proje dosyanızda izleme eklenmiş tüm proje dışlanacak. Live Unit Testing değil eklenmiş olan testleri çalışmaya devam edecektir, ancak kendi kapsamı olmayan görselleştirilir.

Ayrıca denetleyebilirsiniz olmadığını `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` geçerli uygulama etki alanına yüklenir ve testleri üzerinde neden temelinde devre dışı bırakın. Örneğin, xUnit ile aşağıdaki gibi bir şey yapabilirsiniz:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="win32-pe-headers"></a>Win32 PE üst bilgileri
**Neden Win32 PE üst bilgileri Canlı birim testi tarafından oluşturulan izleme eklenmiş derlemelerde farklı?**

Bu sorun düzeltilmiştir ve Visual Studio 2017 sürüm 15.3 yok. Visual Studio'nun bu sürümüne yükseltin.

Visual Studio 2017'in eski sürümleri için aşağıdaki Win32 PE üst bilgisi verileri eklemek için başarısız olan Live Unit Testing derlemelere neden, bilinen bir hata varsa:

- Sürüm dosyası (tarafından belirtilen @System.Reflection.AssemblyFileVersionAttribute kod).

- Win32 simgesi (tarafından belirtilen `/win32icon:` komut satırında).

- Win32 bildirimi (tarafından belirtilen `/win32manifest:` komut satırında).

Bu değerleri kullanan testler Canlı birim testi tarafından çalıştırıldığında başarısız olabilir.

## <a name="continuous-builds"></a>Sürekli derlemeler
**Neden miyim tüm düzenlemeleri hale getiriyorum değil olsa bile her zaman çözümüm oluşturmaya Canlı test birimi Canlı?**

Derleme hedef dosyalarınız uygun girdileri ve çıktıları belirtilen yoktur ve çözümünüzü oluşturma işlemi çözümün bir parçası olan kaynak kodu oluşturursa, düzenlemeleri değil olsa bile çözümünüzü oluşturabilirsiniz. MSBuild uygun güncel denetimleri gerçekleştirmek ve yeni bir derleme gerekip gerekmediğini hedefleri girişler ve çıkışlar listesini verilmelidir.

Live Unit Testing, kaynak dosyaların değiştiğini algıladığında, bir derleme başlar. Live Unit Testing, çözümünüzün derleme kaynak dosyaları oluşturduğundan, bir derleme sonsuz döngüye elde edersiniz. Live Unit Testing ikinci derleme (önceki yapı yeni oluşturulan kaynak dosyalarını sistemlerimiz) başlatıldığında, girdileri ve çıktıları hedefinin ancak işaretli değilse, girdileri ve çıktıları denetimleri olur çünkü bu derleme döngüden her şeyin güncel olduğunu gösterir.  

## <a name="lightweight-solution-load"></a>Basit çözüm yükü
**Nasıl iş basit çözüm yükü özelliği ile test birimi Canlı?**

Live Unit Testing ile de basit çözüm yükü özelliği şu anda çalışmıyor. En az bir test projeleri yalnızca yüklendikten sonra çalışır. Live Unit Testing en az bir test bağdaştırıcısı (MSTest, xUnit ve NUnit) başvuran test projeleri bağımlı olduğu için o tarihe kadar işe yaramaz yükleniyor.

> [!NOTE]
> Basit çözüm yükü, artık Visual Studio 2017 sürüm 15.5 kullanılabilir ve üzerinde desteklenir. Visual Studio 2017 sürüm 15.5 ve üzeri, içeren büyük çözümler kod yük önceden kıyasla çok daha hızlı, basit çözüm yükü olmadan bile yönetilen.

## <a name="new-process-coverage"></a>Yeni işlem kapsamı
**Neden Live Unit Testing, bir test tarafından oluşturulan yeni bir işlem kapsamı yakalamaz?**

Bu bilinen bir sorundur ve Visual Studio 2017'in sonraki bir güncelleştirmede düzeltilmelidir.

## <a name="including-or-excluding-tests-not-working"></a>Dahil veya hariç testleri çalışmıyor
**Neden dahil etmek veya testleri Canlı Test kümesi hariç sonra hiçbir şey?**

Bu sorun düzeltilmiştir ve Visual Studio 2017 sürüm 15.3 yok. Visual Studio'nun bu sürümüne yükseltin.

Visual Studio 2017'in eski sürümleri için bu bilinen bir sorundur. Bu sorunu çözmek için eklenen veya testleri hariç herhangi bir dosyaya bir düzenleme anlamak gerekir. 

## <a name="editor-icons"></a>Düzenleyici simgeleri
**Çıktı penceresinde iletileri göre testleri çalıştırması için Live Unit Testing görünüyor olsa da neden hiçbir simge Düzenleyicisi'nde göremiyorum?**

Live Unit Testing üzerinde çalışan derlemeler için herhangi bir nedenle izleme eklenmiş değildir, simge Düzenleyicisi'nde göremeyebilirsiniz. Örneğin, Live Unit Testing ayarlanan projeleri ile uyumlu olmayan `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. Bu durumda, yapı işleminizin ya da bu ayarını kaldırın veya değiştirilmesi güncelleştirilmesi gerekiyor `true` çalışmak Live Unit Testing için. 

## <a name="capture-logs"></a>Günlükleri yakalama
**Dosya hata raporları için nasıl daha ayrıntılı günlüklere topluyor?**

Daha ayrıntılı günlüklere toplamak için çeşitli şeyler yapabilirsiniz:

- Git **Araçları** > **seçenekleri** > **Live Unit Testing** ve günlüğe kaydetme seçeneğini değiştirme **ayrıntılı**. Ayrıntılı günlük kaydı neden gösterilecek daha ayrıntılı günlüklere **çıkış** penceresi.

- Ayarlama `LiveUnitTesting_BuildLog` MSBuild günlük yakalamak için kullanmak istediğiniz dosyanın adını kullanıcı ortam değişkeni. Live Unit Testing derlemelerden ayrıntılı MSBuild günlük iletilerini bu dosyadan sonra alınabilir.

- Ayarlama `LiveUnitTesting_TestPlatformLog` kullanıcı ortam değişkeni `1` Test platformu günlüğünü kaydetme amacıyla. Live Unit Testing çalıştırmalardan ayrıntılı Test platformu günlük iletilerini ardından alınabileceği `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Adlı bir kullanıcı düzeyinde ortam değişkenini oluşturmak `VS_UTE_DIAGNOSTICS` ve 1 olarak ayarlayın (veya herhangi bir değer) ve Visual Studio'yu yeniden başlatın. Günlüğe çok sayıda görürsünüz **çıkış - testleri** Visual Studio'da sekmesi.

## <a name="see-also"></a>Ayrıca bkz.

- [Canlı Birim Testi](live-unit-testing.md)
