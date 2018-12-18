---
title: Yaygın MSBuild proje özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2018
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe2c39fc08528886e143bd51eb1f33219b386807
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921723"
---
# <a name="common-msbuild-project-properties"></a>Yaygın MSBuild proje özellikleri
Aşağıdaki tablo, Visual Studio proje dosyalarında tanımlı ya da dahil listeleri sık kullanılan özellikler *.targets* MSBuild'ın sağladığı dosyaları.  
  
 Proje dosyalarını Visual Studio (*.csproj*, *.vbproj*, *.vcxproj*ve diğerleri) bir projeyi IDE'yi kullanarak derlediğinizde çalışan MSBuild XML kodunu içerir. Projeleri genellikle bir veya daha fazla Al *.targets* yapı işlemlerini tanımlamak için dosyaları. Daha fazla bilgi için [MSBuild .targets dosyaları](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Ortak özellikler ve parametreler listesi  
  
| Özellik veya parametre adı | Açıklama |
|------------------------------------| - |
| AdditionalLibPaths | Derleyicilerin başvuru derlemeleri araması gereken ek klasörleri belirtir. |
| AddModules | Derleyicinin tüm tür bilgileri belirtilen derlemekte olduğunuz projeye kullandırmasına dosyaları. Bu özellik değerine eşdeğer olan `/addModules` derleyici anahtarı. |
| ALToolPath | Yolun burada *AL.exe* bulunabilir. Bu özellik geçerli sürümü geçersiz kılar *AL.exe* farklı bir sürüm kullanımını etkinleştirmek için. |
| ApplicationIcon | *.İco* Win32 simgesi olarak katıştırmak için derleyiciye geçirilecek simge dosyası. Özellik `/win32icon` derleyici anahtarı. |
| ApplicationManifest | Dış kullanıcı hesabı denetimi (UAC) bildirim bilgilerini oluşturmak için kullanılan dosyanın yolunu belirtir. Yalnızca hedefleyen Visual Studio projelerine yöneliktir [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> Çoğu durumda, bildirim katıştırılır. Ancak Registration Free COM kullanıyorsanız veya [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım ve bildirimi uygulama derlemeleriniz ile birlikte yüklenmiş harici bir dosyaya olabilir. Daha fazla bilgi için bu konuda NoWin32Manifest özelliğine bakın. |
| AssemblyOriginatorKeyFile | Derlemeyi imzalamak için kullanılan dosyayı belirtir (*.snk* veya *.pfx*) ve yapan [ResolveKeySource görevi](../msbuild/resolvekeysource-task.md) imzalamak için kullanılan gerçek anahtarı oluşturmak için derleme. |
| AssemblySearchPaths | Yapı zamanı başvurusu derleme çözümü sırasında aranacak konumların bir listesi. Daha sonraki girişlere göre öncelikli olduğundan daha önce listelenen yollar yollarını bu listede görünme sırasını anlam ifade eder. |
| AssemblyName | Proje derlendikten sonra son derlemenin adı. |
| BaseAddress | Ana çıkış derlemesinin temel adresini belirtir. Bu özellik değerine eşdeğer olan `/baseaddress` derleyici anahtarı. |
| BaseOutputPath | Çıktı dosyasının temel yolunu belirtir. Bu ayarlanırsa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kullanacağı `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Örnek sözdizimi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BaseIntermediateOutputPath | Tüm özel yapılandırma Ara çıktı klasörlerinin oluşturulduğu en üst düzey klasör. Varsayılan değer `obj\` şeklindedir. Aşağıdaki kod örneği verilmiştir: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| Buildınparallel | Proje başvuruları yerleşik veya paralel da temizlendiğini gösteren bir Boole değeri Multi-Proc [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kullanılır. Varsayılan değer `true`, birden çok çekirdek veya işlemci varsa, proje sistemi paralel oluşturulacak anlamına gelir. |
| BuildProjectReferences | Proje başvuruları tarafından oluşturulmuş olup olmadığını belirten bir Boole değeri [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Otomatik olarak ayarlanmış `false` projenizi oluşturma, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE) `true` , aksi takdirde. `-p:BuildProjectReferences=false` Başvurulan projeler güncel olduğunu kontrol önlemek için komut satırında belirtilebilir. |
| CleanFile | "Temiz önbellek." kullanılacak dosya adı Temiz önbellek, temizleme işlemi sırasında silinmek üzere oluşturulmuş dosyalar listesidir. Dosyanın, yapı işlemi tarafından ara çıkış yoluna konur.<br /><br /> Bu özellik yalnızca yol bilgisi olmayan dosya adlarını belirtir. |
| Kod sayfası | Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu özellik değerine eşdeğer olan `/codepage` derleyici anahtarı. |
| CompilerResponseFile | Derleyici görevlerine geçirilebilen isteğe bağlı bir yanıt dosyası. |
| Yapılandırma | Oluşturmakta olduğunuz yapılandırma "Debug" veya "Release." |
| CscToolPath | Yolu *csc.exe*, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] derleyici. |
| CustomBeforeMicrosoftCommonTargets | Proje dosyası veya ortak hedefler içe önce otomatik olarak içe aktarılacak hedefler dosyasının adı. |
| DebugSymbols | Semboller yapı tarafından oluşturulup oluşturulmadığını gösteren bir Boole değeri.<br /><br /> Ayarı **- p: DebugSymbols = false** komut satırında, program veritabanı oluşturulmasını devre dışı bırakır (*.pdb*) sembol dosyaları. |
| DefineConstants | Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgüllerle ayrılır ve aşağıdaki sözdizimi kullanılarak belirtilir:<br /><br /> *symbol1 = value1; symbol2 = value2*<br /><br /> Özellik `/define` derleyici anahtarı. |
| DefineDebug | DEBUG sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri. |
| DefineTrace | TRACE sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri. |
| DebugType | Üretilmesini istediğiniz hata ayıklama bilgi düzeyini tanımlar. Geçerli değerler: "full," "pdbonly" ve "none". |
| DelaySign | Tam imzalamak yerine Gecikmeli imzalayın derleme isteyip istemediğinizi belirten bir Boole değeri. |
| Belirleyici | Derleyici aynı girişler için aynı derlemeleri üretmesi gerektiğini belirten bir Boole değeri. Bu parametre için karşılık gelen `/deterministic` geçiş *vbc.exe* ve *csc.exe* derleyicileri. |
| DisabledWarnings | Belirtilen Uyarıları bastırır. Uyarı tanımlayıcısının yalnızca sayısal parçası belirtilmelidir. Çoklu uyarılar noktalı virgül ile ayrılır. Bu parametre için karşılık gelen `/nowarn` geçiş *vbc.exe* derleyici. |
| DisableFastUpToDateCheck | Geçerli bir Boole değeri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yalnızca. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Yöneticisi kullanan bir proje, güncel olması için yeniden oluşturulması olup olmadığını belirlemek için FastUpToDateCheck adlı bir işlem oluşturun. Bu işlem, kullanmaktan daha hızlıdır [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bunu belirlemek için. DisableFastUpToDateCheck özelliğini `true` atlamasına olanak tanır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yapı yöneticisini ve kullanmak için onu zorla [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projenin güncel olup olmadığını belirlemek için. |
| DocumentationFile | XML belgeleri dosyası olarak oluşturulacak dosyanın adı. Bu ad, yalnızca dosya adını içerir ve hiçbir yol bilgisi içermez. |
| ErrorReport | Derleyici görevinin iç derleyici hatalarını nasıl raporlayacağını belirtir. Geçerli değerler: "prompt," "send" ya da "none". Bu özellik değerine eşdeğer olan `/errorreport` derleyici anahtarı. |
| ExcludeDeploymentUrl | [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md) proje dosyası aşağıdaki öğeleri herhangi birini içeriyorsa, dağıtım bildirimine bir deploymentProvider etiketi ekler:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Excludedeploymenturl'yi kullanarak, Bununla birlikte, deploymentProvider etiketi yukarıdaki URL'lerden herhangi birini belirtilse bile dağıtım bildirimine eklenmesini engelleyebilirsiniz. Bunu yapmak için aşağıdaki özelliği proje dosyanıza ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Not:** Excludedeploymenturl'yi gösterilmese de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE ve yalnızca el ile proje dosyasını düzenleyerek ayarlanabilir. Bu özelliğin ayarlanması dahilinde yayımlamayı etkilemez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; yani deploymentProvider etiketi hala PublishUrl tarafından belirtilen URL'ye eklenir. |
| Filealignment değerini | , Çıktı dosyasının bölümlerinin hizalanacağı yeri bayt cinsinden belirtir. Geçerli değerler: 512, 1024, 2048, 4096, 8192. Bu özellik değerine eşdeğer olan `/filealignment` derleyici anahtarı. |
| FrameworkPathOverride | Konumunu belirtir *mscorlib.dll* ve *microsoft.visualbasic.dll*. Bu parametre değerine eşdeğer olan `/sdkpath` geçiş *vbc.exe* derleyici. |
| GenerateDocumentation | (Yalnızca Visual Basic) Belgeleri yapı tarafından oluşturulup oluşturulmadığını gösteren bir Boole parametresi. Varsa `true`, yapı, belgelendirme bilgilerini üretir ve bunu koyar bir *.xml* yürütülebilir dosya ya da yapı görevinin ürettiği kitaplık adı ile birlikte dosya. |
| IntermediateOutputPath | Ten türetildiği haliyle tam Ara çıktı yolu `BaseIntermediateOutputPath`, hiçbir yol belirtilmezse. Örneğin, *\obj\debug\\*. |
| AnahtarKapsayıcıAdı | Tanımlayıcı ad anahtar kapsayıcısı adı. |
| KeyOriginatorFile | Tanımlayıcı ad anahtar dosyası adı. |
| MSBuildProjectExtensionsPath | Proje uzantılarını bulunduğu yere yolunu belirtir. Varsayılan olarak, bu alan aynı değere `BaseIntermediateOutputPath`. |
| ModuleAssemblyName | Derlenmiş modülün içine alınacağı derlemenin adı. Özellik `/moduleassemblyname` derleyici anahtarı. |
| NoLogo | Derleyici logosunun devre dışı isteyip istemediğinizi belirten bir Boole değeri. Bu özellik değerine eşdeğer olan `/nologo` derleyici anahtarı. |
| NoStdLib | Standart kitaplık engellenmeyeceğini gösteren bir Boole değeri (*mscorlib.dll*). Varsayılan değer `false` şeklindedir. |
| NoVBRuntimeReference | Belirten boolean bir değer olup olmadığını [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] çalışma zamanı (*Microsoft.VisualBasic.dll*) projedeki bir başvuruyu olarak eklenmelidir. |
| NoWin32Manifest | Yürütülebilir uygulamanın kullanıcı hesabı denetimi (UAC) bildirim bilgisinin katıştırılmayacağını belirten bir Boole değeri. Yalnızca hedefleyen Visual Studio projelerine yöneliktir [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. Kullanılarak dağıtılan projelerde [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve Registration-Free COM, bu öğe yoksayılır. `False` (varsayılan değer), kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirtir. `True` UAC bildirim bilgileri katıştırılmayacağını belirtir.<br /><br /> Bu özellik yalnızca geçerlidir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hedefleyen projelerde [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. Kullanılarak dağıtılan projelerde [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve bu özelliği Registration-Free COM göz ardı edilir.<br /><br /> Yalnızca, istemiyorsanız NoWin32Manifest eklemelisiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için herhangi bir bildirim bilgisini uygulamanın yürütülebilir dosyasına katıştırılıp; bu işlem çağrılırken *sanallaştırma*. Sanallaştırma kullanmak üzere ayarlanmış `<ApplicationManifest>` birlikte `<NoWin32Manifest>` gibi:<br /><br /> -İçin [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeleri kaldırma `<ApplicationManifest>` düğümü. (İçinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeleri `<NoWin32Manifest>` zaman yok sayılır bir `<ApplicationManifest>` düğüm yok.)<br />-İçin [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projeleri kümesi `<ApplicationManifest>` için `False` ve `<NoWin32Manifest>` için `True`. (İçinde [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projeleri `<ApplicationManifest>` geçersiz kılmalar `<NoWin32Manifest>`.)<br /> Bu özellik değerine eşdeğer olan `/nowin32manifest` derleyici anahtarıyla *vbc.exe*. |
| En iyi duruma getirme | Bir Boole değeri ayarlandığında `true`, derleyici iyileştirmelerini sağlar. Bu özellik değerine eşdeğer olan `/optimize` derleyici anahtarı. |
| OptionCompare | Dize karşılaştırmaları nasıl yapılacağını belirtir. Geçerli değerler şunlardır: "binary" ya da "text." Bu özellik değerine eşdeğer olan `/optioncompare` derleyici anahtarıyla *vbc.exe*. |
| Option Explicit | Bir Boole değeri ayarlandığında `true`, kaynak kodundaki değişkenleri açık bildirimini gerektirir. Bu özellik değerine eşdeğer olan `/optionexplicit` derleyici anahtarı. |
| OptionInfer | Bir Boole değeri ayarlandığında `true`, etkinleştirir değişkenlerin tür girişimini. Bu özellik değerine eşdeğer olan `/optioninfer` derleyici anahtarı. |
| OptionStrict | Bir Boole değeri ayarlandığında `true`, yapı görevinin katı tür semantiği örtük tür dönüştürmelerini kısıtlamak için zorunlu neden olur. Bu özellik değerine eşdeğer olan `/optionstrict` geçiş *vbc.exe* derleyici. |
| OutputPath | Örneğin, proje dizinine göreli olarak çıktı dizini yolunu belirtir *bin\Debug*. |
| OutputType | Çıkış dosyasının dosya biçimini belirtir. Bu parametre aşağıdaki değerlerden biri olabilir:<br /><br /> -Kitaplığı. Bir kod kitaplığı oluşturur. (Varsayılan değer)<br />-Exe. Bir konsol uygulaması oluşturur.<br />-Module. Bir modül oluşturur.<br />-Winexe. Windows tabanlı bir program oluşturur.<br /><br /> Bu özellik değerine eşdeğer olan `/target` geçiş *vbc.exe* derleyici. |
| OverwriteReadOnlyFiles | Salt okunur dosyaların üzerine yaz veya bir hata tetiklemesini sağlayan isteyip istemediğinizi belirten bir Boole değeri. |
| PdbFile | Dosya adını *.pdb* oluşturmakta olduğunuz dosya. Bu özellik değerine eşdeğer olan `/pdb` geçiş *csc.exe* derleyici. |
| Platform | Derlemede hedeflediğiniz işletim sistemi. Geçerli değerler şunlardır: "Any CPU", "x 86" ve "x64". |
| ProduceReferenceAssembly | Bir Boole değeri ayarlandığında `true` üretimini etkinleştirir [başvuru derlemeleri](https://github.com/dotnet/roslyn/blob/master/docs/features/refout.md) geçerli derleme için. `Deterministic` olmalıdır `true` bu özelliği kullanırken. Bu özellik için karşılık gelen `/refout` geçiş *vbc.exe* ve *csc.exe* derleyicileri. |
| RemoveIntegerChecks | Tamsayı taşması hata denetimlerini devre dışı bırakılıp bırakılmayacağını belirten bir Boole değeri. Varsayılan değer `false` şeklindedir. Bu özellik değerine eşdeğer olan `/removeintchecks` geçiş *vbc.exe* derleyici. |
| SGenUseProxyTypes | Proxy türleri tarafından oluşturulması gerekip gerekmediğini gösteren bir Boole değeri *SGen.exe*.<br /><br /> SGen hedefi, bu özelliği UseProxyTypes bayrağını ayarlamak için kullanır. Bu özellik varsayılan olarak true'dur ve bunu değiştirmek için kullanıcı Arabirimi yoktur. Web hizmeti olmayan türleri serileştirme derlemesi oluşturmak için bu özelliği proje dosyasına ekleyin ve içeri aktarmadan önce false değerine ayarlıyken *Microsoft.Common.Targets* veya *c#/vb.targets'ı*. |
| SGenToolPath | Elde edilecek yeri belirten bir isteğe bağlı bir araç yolu *SGen.exe* zaman geçerli sürümü *SGen.exe* geçersiz kılınır. |
| StartupObject | Sınıf veya Main yöntemini veya Sub Main yordamını içeren Modülü belirtir. Bu özellik değerine eşdeğer olan `/main` derleyici anahtarı. |
| ProcessorArchitecture | Derleme başvuruları çözümlendiğinde kullanılan işlemci mimarisi. Geçerli değerler: "msil," "x86," "amd64" veya "ia64." |
| RootNamespace | Katıştırılmış bir kaynağı adlandırdığınızda kullanılacak kök ad alanı. Bu ad alanı, katıştırılmış kaynak bildirimi adının parçasıdır. |
| Satellite_AlgorithmId | Kimliği *AL.exe* karma algoritması uydu derlemeleri oluşturulduğunda kullanılacak. |
| Satellite_BaseAddress | Kullanarak kültüre özel uydu derlemeler derlenirken kullanılacak temel adres `CreateSatelliteAssemblies` hedef. |
| Satellite_CompanyName | Uygulamasına geçirmek için şirket adı *AL.exe* uydu derleme oluşturma sırasında. |
| Satellite_Configuration | Uygulamasına geçirmek için yapılandırma adı *AL.exe* uydu derleme oluşturma sırasında. |
| Satellite_Description | Uygulamasına geçirmek için açıklama metnini *AL.exe* uydu derleme oluşturma sırasında. |
| Satellite_EvidenceFile | Belirtilen dosya bir kaynak adı "Security.Evidence" olan uydu derlemeye katıştırır. |
| Satellite_FileVersion | Uydu derlemesindeki dosya sürümü alanı için bir dize belirtir. |
| Satellite_Flags | Uydu derlemesindeki Bayraklar alanı için bir değer belirtir. |
| Satellite_GenerateFullPaths | Bir hata iletisinde bildirilen dosyalar için mutlak yollar kullanmak derleme görevi neden olur. |
| Satellite_LinkResource | Belirtilen kaynak dosyalarını uydu bir derlemeye bağlar. |
| Satellite_MainEntryPoint | Bir modül, uydu derleme oluşturma sırasında yürütülebilir bir dosyaya dönüştürüldüğünde giriş noktası olarak kullanılacak yöntemin tam nitelikli adı (yani sınıf.yöntem biçimindeki) belirtir. |
| Satellite_ProductName | Uydu derlemesindeki ürün alanı için bir dize belirtir. |
| Satellite_ProductVersion | Uydu derlemesindeki ürün sürümü alanı için bir dize belirtir. |
| Satellite_TargetType | Uydu derleme çıktı dosyasının dosya biçimini "library," "exe" belirtir ya da "win" Varsayılan değer "library"'dir |
| Satellite_Title | Uydu derlemesindeki başlık alanı için bir dize belirtir. |
| Satellite_Trademark | Uydu derlemesindeki ticari marka alanı için bir dize belirtir. |
| Satellite_Version | Uydu derlemesinin sürüm bilgilerini belirtir. |
| Satellite_Win32Icon | Ekler bir *.ico* uydu derlemesindeki simge dosyası. |
| Satellite_Win32Resource | Bir Win32 kaynağı ekler (*.res* dosya) uydu derlemesini. |
| SubsystemVersion | Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir. Bu özellik değerine eşdeğer olan `/subsystemversion` derleyici anahtarı. Bu özellik varsayılan değeri hakkında daha fazla bilgi için bkz. [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) veya [/subsystemversion (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Derlemekte olduğunuz uygulamayı çalıştırmak için gereken .NET Compact Framework sürümü. Bunun belirtilmesi, başka türlü mümkün olmayabilir belirli çerçeve derlemelerine olanak tanır. |
| targetFrameworkVersion | Sürümü [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] derlemekte olduğunuz uygulamayı çalıştırmak için gereklidir. Bunun belirtilmesi, başka türlü mümkün olmayabilir belirli çerçeve derlemelerine olanak tanır. |
| TreatWarningsAsErrors | Bir Boole parametresi, varsa `true`, tüm uyarıları hata olarak kabul edilmesine neden olur. Bu parametre değerine eşdeğer olan `/nowarn` derleyici anahtarı. |
| UseHostCompilerIfAvailable | Bir Boole parametresi, varsa `true`, varsa yapı görevinin işlem içi derleyici nesnesini kullanmasına neden olur. Bu parametre yalnızca kullanılan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| Utf8Output | Bir Boole parametresi, varsa `true`, derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Bu parametre değerine eşdeğer olan `/utf8Output` derleyici anahtarı. |
| VbcToolPath | İçin başka bir konum belirten isteğe bağlı bir yol *vbc.exe* zaman geçerli sürümü *vbc.exe* geçersiz kılınır. |
| VbcVerbosity | Ayrıntı düzeyini belirtir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] derleyicisinin çıktısının. Geçerli değerler: "Quiet" "Normal" (varsayılan değer) veya "Verbose." |
| VisualStudioVersion | Bu proje altında çalıştırılması için düşünülmelidir Visual Studio sürümünü belirtir. Bu özellik belirtilmezse, MSBuild bunu makul bir varsayılan bir değere ayarlar.<br /><br /> Bu özellik, birkaç proje türünde derleme için kullanılan hedefleri kümesini belirtmek için kullanılır. Varsa `ToolsVersion` 4.0 veya üzeri bir proje için ayarlanmış `VisualStudioVersion` hangi sub-araç kümesini belirtmek için kullanılır. Daha fazla bilgi için [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Hata olarak değerlendirilecek uyarıların bir listesini belirtir. Bu parametre değerine eşdeğer olan `/warnaserror` derleyici anahtarı. |
| WarningsNotAsErrors | Hata olarak görülmeyen uyarıların bir listesini belirtir. Bu parametre değerine eşdeğer olan `/warnaserror` derleyici anahtarı. |
| Win32Manifest | Son derlemeye katıştırılması gereken bildirim dosyasının adı. Bu parametre değerine eşdeğer olan `/win32Manifest` derleyici anahtarı. |
| Win32Resource | Son derlemeye katıştırılacak Win32 kaynağının dosya adı. Bu parametre değerine eşdeğer olan `/win32resource` derleyici anahtarı. |
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
