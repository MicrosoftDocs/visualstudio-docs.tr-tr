---
title: CL görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c239dc78d152e9060d176ebe1d4abd3b981a57d
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220371"
---
# <a name="cl-task"></a>CL görevi
Visual C++ Derleyici aracı sarmalar *cl.exe*. Derleyici çalıştırılabilir dosyası oluşturur (*.exe*) dosyaları, dinamik bağlantı kitaplığı (*.dll*) dosyaları ya da kod modülünü (*.netmodule*) dosyaları. Daha fazla bilgi için [derleyici seçenekleri](/cpp/build/reference/compiler-options).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki listede parametrelerini açıklar **CL** görev. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
- **AdditionalIncludeDirectories**  
  
   İsteğe bağlı dize [] parametresi.  
  
   Bir dizin dahil etme dosyaları için Aranan dizinleri listesine ekler.  
  
   Daha fazla bilgi için [/ı (ek içeren dizinler)](/cpp/build/reference/i-additional-include-directories).  
  
- **AdditionalOptions**  
  
   İsteğe bağlı dize parametresi.  
  
   Komut satırı seçeneklerinin listesi. Örneğin, "/\<Seçenek1 > /\<Seçenek2 > /\<seçeneği #>". Herhangi bir görev parametresi tarafından temsil edilmez komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.  
  
   Daha fazla bilgi için [derleyici seçenekleri](/cpp/build/reference/compiler-options).  
  
- **AdditionalUsingDirectories**

   İsteğe bağlı dize [] parametresi.  
  
   Geçirilen dosya başvurularını çözümlemek için derleyicinin arama yapacağı dizini belirtir **#using** yönergesi.  
  
   Daha fazla bilgi için [/AI (meta veri dizinlerini belirt)](/cpp/build/reference/ai-specify-metadata-directories).  
  
- **AlwaysAppend**  
  
   İsteğe bağlı dize parametresi.  
  
   Bir dize, komut satırında yayılan her zaman. Varsayılan değeri "**/c**".  
  
- **AssemblerListingLocation**  
  
   Derleme kodu içeren bir listeleme dosyası oluşturur.  
  
   Daha fazla bilgi için **/Fa** seçeneğini [/FA, /Fa (listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file).  
  
- **AssemblerOutput**  
  
   İsteğe bağlı dize parametresi.  
  
   Derleme kodu içeren bir listeleme dosyası oluşturur.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **NoListing** - *\<yok >*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** - **/FAc**  
  
  - **AssemblyAndSourceCode** - **/FAs**  
  
  - **Tüm** -   **/facs**  
  
    Daha fazla bilgi için **/FA**, **/Fac**, **/Fas**, ve **/facs** seçeneklerini [/FA, /Fa (listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file).  
  
- **BasicRuntimeChecks**  
  
   İsteğe bağlı dize parametresi.  
  
   Sağlar ve birlikte çalışma zamanı hata denetimleri özelliğini devre dışı bırakır [runtime_checks](/cpp/preprocessor/runtime-checks) pragması.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan** -                          *\<yok >*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **/RTCu**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Daha fazla bilgi için [/RTC (çalışma zamanı hata denetimleri)](/cpp/build/reference/rtc-run-time-error-checks).  
  
- **BrowseInformation**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, gözatma bilgisi dosyası oluşturur.  
  
   Daha fazla bilgi için **/FR** seçeneğini [/FR, /Fr (.sbr dosyası oluştur)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
- **BrowseInformationFile**  
  
   İsteğe bağlı dize parametresi.  
  
   Gözatma bilgisi dosyası için bir dosya adı belirtir.  
  
   Daha fazla bilgi için **BrowseInformation** Bu tablo, ayrıca bkz: parametresinde [/FR, /Fr (.sbr dosyası oluştur)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
- **BufferSecurityCheck**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, dönüş adresi, arabellek boyutu kısıtlamaları zorunlu kılmaz kod kötüye için genel bir tekniktir üzerine bazı arabellek taşmalarına algılar.  
  
   Daha fazla bilgi için [/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check).  
  
- **BuildingInIDE**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, belirten **MSBuild** IDE tarafından çağrılır. Aksi takdirde, **MSBuild** komut satırında çağrılır.  
  
- **CallingConvention**  
  
   İsteğe bağlı dize parametresi.  
  
   Çağıran işlevin veya çağrılan işlevin çağrının sonunda yığından bağımsız değişkenler kaldırır olup olmadığını, işlev bağımsız değişkenleri yığın itilir sırasını belirler, çağırma kuralı ve bir ad dekorasyon kuralı belirtir, Derleyici, tek tek işlevleri tanımlamak için kullanır.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Cdecl** - **/Gd**  
  
  - **FastCall** -                          **Gr**  
  
  - **StdCall** -                          **/Gz**  
  
    Daha fazla bilgi için [/Gd, / Gr, GV, /Gz (çağırma kuralı)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).  
  
- **CompileAs**  
  
   İsteğe bağlı dize parametresi.  
  
   Giriş dosyası olarak bir C veya C++ kaynak dosyasını derlemek belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan** - *\<yok >*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Daha fazla bilgi için [/Tc, /Tp, /TC, /TP (kaynak dosya türünü belirtin)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).  
  
- **CompileAsManaged**  
  
   İsteğe bağlı dize parametresi.  
  
   Ortak dil çalışma zamanı (CLR) özellikleri kullanmak, uygulamaları ve bileşenleri sağlar.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **false** - *\<yok >*  
  
  - **doğru** -   **/CLR**  
  
  - **Saf** -   **/CLR: pure**  
  
  - **Safe** - **/clr:safe**  
  
  - **OldSyntax** - **/clr:oldSyntax**  
  
    Daha fazla bilgi için [/CLR (ortak dil çalışma zamanı derlemesi)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
- **CreateHotpatchableImage**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, derleyiciye bir görüntü için hazırlama *Yeniden başlatmasız düzeltme*. Bu parametre, Yeniden başlatmasız düzeltme için gerekli olan her işlevin ilk yönergesinin iki bayt olmasını sağlar.  
  
   Daha fazla bilgi için [/hotpatch (düzeltme eki eklenebilen görüntü oluşturma)](/cpp/build/reference/hotpatch-create-hotpatchable-image).  
  
- **DebugInformationFormat**  
  
   İsteğe bağlı dize parametresi.  
  
   Programınız ve bu bilgileri nesnesinde olup tutulur için oluşturulan hata ayıklama bilgisini türünü seçer (*.obj*) dosyaları veya içinde bir program veritabanı (PDB).  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **OldStyle** - **/Z7**  
  
  - **ProgramDatabase** -   **/zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Daha fazla bilgi için [/z7, / zi, /zı (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format).  
  
- **DisableLanguageExtensions**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa **true**, ANSI C veya C++ ANSI ile uyumlu olmayan dil yapıları için hata yayma derleyiciye.  
  
   Daha fazla bilgi için **/Za** seçeneğini [/Za, /Ze (dil uzantılarını devre dışı bırak)](/cpp/build/reference/za-ze-disable-language-extensions).  
  
- **DisableSpecificWarnings**  
  
   İsteğe bağlı dize [] parametresi.  
  
   Noktalı virgülle ayrılmış bir listede belirtilen uyarı numaralarını devre dışı bırakır.  
  
   Daha fazla bilgi için `/wd` seçeneğini [/w, /W0, / W1, / w2, / W3, / W4, / W1, / w2, / W3, / W4, /Wall, WD, / we Wo, wv, /WX (uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level).  
  
- **EnableEnhancedInstructionSet**  
  
   İsteğe bağlı dize parametresi.  
  
   Streaming SIMD Extensions 2 (SSE2) yönergeleri ve Akış SIMD Uzantıları'nı (SSE) kullanan kod oluşturma mimarisini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** -   **/arch: SSE2**  
  
    Daha fazla bilgi için [/arch (x86)](/cpp/build/reference/arch-x86).  
  
- **EnableFiberSafeOptimizations**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, statik iş parçacığı yerel depolama, diğer bir deyişle, veriler kullanılarak kullanılarak yer ayrılan veri için fiber güvenliğini destekler `__declspec(thread)`.  
  
   Daha fazla bilgi için [/GT (fiber-güvenli iş parçacığı-yerel depolamayı destekle)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).  
  
- **EnablePREfast**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, kod analizini etkinleştirir.  
  
   Daha fazla bilgi için [/ analyze (kod çözümleme)](/cpp/build/reference/analyze-code-analysis).  
  
- **ErrorReporting**  
  
   İsteğe bağlı dize parametresi.  
  
   Derleyici iç hatası (ICE) bilgilerini doğrudan Microsoft'a sağlamanıza olanak tanır. Varsayılan olarak, IDE yapılarında ayardır **istemi** ve komut satırı derlemeleri ayarda **kuyruk**.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **None** - **/errorReport:none**  
  
  - **Prompt** - **/errorReport:prompt**  
  
  - **Queue** - **/errorReport:queue**  
  
  - **Send** - **/errorReport:send**  
  
    Daha fazla bilgi için [/errorreport (dahili derleme hatalarını raporla)](/cpp/build/reference/errorreport-report-internal-compiler-errors).  
  
- **ExceptionHandling**  
  
   İsteğe bağlı dize parametresi.  
  
   Derleyici tarafından kullanılması için özel durum işleme modelini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **false** - *\<yok >*  
  
  - **Async** - **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Daha fazla bilgi için [/EH (özel durum işleme modeli)](/cpp/build/reference/eh-exception-handling-model).  
  
- **ExpandAttributedSource**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, genişletilmiş öznitelikleri kaynak dosyasına eklenen bir listeleme dosyası oluşturur.  
  
   Daha fazla bilgi için [/Fx (eklenen birleştirme kodu)](/cpp/build/reference/fx-merge-injected-code).  
  
- **FavorSizeOrSpeed**  
  
   İsteğe bağlı dize parametresi.  
  
   Kod boyutu veya kod hızına ayrıcalık tanı belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Ne** - *\<yok >*  
  
  - **Boyutu** - **/Os**  
  
  - **Hızı** - **/Ot**  
  
    Daha fazla bilgi için [/Os, /Ot (küçük koda, hızlı koda ayrıcalık)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).  
  
- **FloatingPointExceptions**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, güvenilir kayan nokta özel durum modeli sağlar. Özel durumlar, tetiklendikten hemen sonra gerçekleştirilecektir.  
  
   Daha fazla bilgi için /**fp: except** seçeneğini [/fp (kayan nokta davranışını belirt)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
- **FloatingPointModel**  
  
   İsteğe bağlı dize parametresi.  
  
   Ayarlar kayan nokta modeli.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Precise** - **/fp:precise**  
  
  - **Katı** -   **/FP: strict**  
  
  - **Fast** - **/fp:fast**  
  
    Daha fazla bilgi için [/fp (kayan nokta davranışını belirt)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
- **ForceConformanceInForLoopScope**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, standart C++ davranışını uygulayan [için](/cpp/cpp/for-statement-cpp) Microsoft uzantıları kullanma döngüler ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).  
  
   Daha fazla bilgi için [/ZC: forscope (zorla döngü kapsamında uyumluluğu)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).  
  
- **ForcedIncludeFiles**  
  
   İsteğe bağlı `String[]` parametresi.  
  
   Bir veya daha fazla belirtilen üstbilgi dosyalarını işlemek önişlemci neden olur.  
  
   Daha fazla bilgi için [/FI (zorla dahil dosya)](/cpp/build/reference/fi-name-forced-include-file).  
  
- **ForcedUsingFiles**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Önişlemci işlemine bir veya daha fazla belirtilen neden **#using** dosyaları.  
  
   Daha fazla bilgi için [/FU (zorlanan adı #using)](/cpp/build/reference/fu-name-forced-hash-using-file).  
  
- **FunctionLevelLinking**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, bireysel işlevleri paketlenmiş işlevler (Comdat'lar) biçiminde derleyiciyi etkinleştirir.  
  
   Daha fazla bilgi için [/Gy (işlev düzeyi bağlamayı etkinleştir)](/cpp/build/reference/gy-enable-function-level-linking).  
  
- **GenerateXMLDocumentationFiles**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, kaynak kodu dosyalarında belge açıklamalarını işle ve oluşturmak için derleyicinin bir *.xdc* belge açıklamaları olan her kaynak kodu dosyası için dosya.  
  
   Daha fazla bilgi için [/doc (işlem belgeleri açıklamaları) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Ayrıca bkz: **XMLDocumentationFileName** bu tablodaki parametresi.  
  
- **IgnoreStandardIncludePath**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, derleyici PATH ve INCLUDE Ortam değişkenlerinde belirtilen dizinlerde ekleme dosyalarını aramasını önler.  
  
   Daha fazla bilgi için [/X (Ignore standard yolları dahil)](/cpp/build/reference/x-ignore-standard-include-paths).  
  
- **InlineFunctionExpansion**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Derleme için satır içi işlev genişletmesi düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan** - *\<yok >*  
  
  - **Devre dışı bırakılmış** - **/Ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** -   **/ob2**  
  
    Daha fazla bilgi için [/Ob (satır içi işlev genişletmesi)](/cpp/build/reference/ob-inline-function-expansion).  
  
- **IntrinsicFunctions**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, değiştirir bazı işlev çağrıları ile iç veya aksi halde uygulamanızı yardımcı işlevinin özel formlar daha hızlı çalışır.  
  
   Daha fazla bilgi için [/Oi (iç işlevler üret)](/cpp/build/reference/oi-generate-intrinsic-functions).  
  
- **MinimalRebuild**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, değiştirilmiş C++ içeren C++ kaynak dosyaları (Üstbilgi (.h) dosyalarında depolanan) tanımları sınıf olup olmadığını belirler. en az yeniden derlemeyi yeniden sağlar.  
  
   Daha fazla bilgi için [(en az /GM yeniden derlemeyi etkinleştir)](/cpp/build/reference/gm-enable-minimal-rebuild).  
  
- **MultiProcessorCompilation**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, birden çok işlemci derlemek için kullanın. Bu parametre, bilgisayarınızda etkili her işlemci için bir işlem oluşturur.  
  
   Daha fazla bilgi için [/MP (birden çok süreçle derleme)](/cpp/build/reference/mp-build-with-multiple-processes). Ayrıca bkz **ProcessorNumber** bu tablodaki parametresi.  
  
- **ObjectFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir nesne (.obj) dosya adı veya varsayılan yerine kullanılacak dizini belirtir.  
  
   Daha fazla bilgi için [/Fo (nesne dosya adı)](/cpp/build/reference/fo-object-file-name).  
  
- **ObjectFiles**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Nesne dosyaların listesi.  
  
- **OmitDefaultLibName**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, varsayılan C çalışma zamanı kitaplığı adı nesnesinden atlar (*.obj*) dosyası. Varsayılan olarak, derleyici kitaplığa adını geçirir *.obj* doğru kitaplık bağlayıcıya yönlendirmek için dosya.  
  
   Daha fazla bilgi için [/Zl (varsayılan kitaplık adını çıkarın)](/cpp/build/reference/zl-omit-default-library-name).  
  
- **OmitFramePointers**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.  
  
   Daha fazla bilgi için [/Oy (Çerçeve işaretçisini atlama)](/cpp/build/reference/oy-frame-pointer-omission).  
  
- **OpenMPSupport**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, derleyicinin OpenMP yan tümceleri ve yönergeleri işlemek.  
  
   Daha fazla bilgi için [/OpenMP (OpenMP 2.0 etkinleştirme desteği)](/cpp/build/reference/openmp-enable-openmp-2-0-support).  
  
- **En iyi duruma getirme**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Çeşitli kod iyileştirmeleri hız ve boyutunu belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Devre dışı bırakılmış** - **/Od**  
  
  - **MinSpace** -   **/O1**  
  
  - **MaxSpeed** -   **/O2**  
  
  - **Tam** - **/Ox**  
  
    Daha fazla bilgi için [/O seçenekler (kodu İyileştir)](/cpp/build/reference/o-options-optimize-code).  
  
- **PrecompiledHeader**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Oluşturabilir veya önceden derlenmiş üstbilgi kullanabilirsiniz (*.pch*) derleme sırasında dosya.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **NotUsing** - *\<yok >*  
  
  - **Oluşturma** - **/Yc**  
  
  - **Kullanım** - **/Yu**  
  
    Daha fazla bilgi için [/Yc (önceden derlenmiş üst bilgi dosyası oluştur)](/cpp/build/reference/yc-create-precompiled-header-file) ve [/Yu (önceden derlenmiş üst bilgi dosyasını kullanma)](/cpp/build/reference/yu-use-precompiled-header-file). Ayrıca bkz **PrecompiledHeaderFile** ve **PrecompiledHeaderOutputFile** bu tabloda parametreler.  
  
- **PrecompiledHeaderFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Oluşturmayı veya kullanmayı önceden derlenmiş üst bilgi dosyası adını belirtir.  
  
   Daha fazla bilgi için [/Yc (önceden derlenmiş üst bilgi dosyası oluştur)](/cpp/build/reference/yc-create-precompiled-header-file) ve [/Yu (önceden derlenmiş üst bilgi dosyasını kullanma)](/cpp/build/reference/yu-use-precompiled-header-file).  
  
- **PrecompiledHeaderOutputFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Varsayılan yol adı yerine önceden derlenmiş üst bilgi için bir yol adı belirtir.  
  
   Daha fazla bilgi için [/Fp (.pch dosyası Adlandır)](/cpp/build/reference/fp-name-dot-pch-file).  
  
- **PreprocessKeepComments**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, ön işleme sırasında yorumları korur.  
  
   Daha fazla bilgi için [/C (önişleme sırasında açıklamaları Koru)](/cpp/build/reference/c-preserve-comments-during-preprocessing).  
  
- **PreprocessorDefinitions**  
  
   İsteğe bağlı `String[]` parametresi.  
  
   Kaynak dosyanız için önceden işleme simgesini tanımlar.  
  
   Daha fazla bilgi için [/D (önişlemci tanımları)](/cpp/build/reference/d-preprocessor-definitions).  
  
- **PreprocessOutput**  
  
   İsteğe bağlı `ITaskItem[]` parametresi.  
  
   Tüketilen ve görevler tarafından yayılan önişlemci çıktısını öğeleri bir dizisi tanımlanmaktadır.  
  
- **PreprocessOutputPath**  
  
   İsteğe bağlı `String` parametresi.  
  
   Hangi çıkış dosyasının adını belirtir **PreprocessToFile** parametresi önceden işlenmiş çıktı yazar.  
  
   Daha fazla bilgi için [/Fi (çıktı dosyası adı ön işleme)](/cpp/build/reference/fi-preprocess-output-file-name).  
  
- **PreprocessSuppressLineNumbers**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, C ve C++ kaynak dosyalarını önceden işler ve standart çıktı cihazına önceden işlenmiş dosya kopyalar.  
  
   Daha fazla bilgi için [/EP (#line yönergeleri olmadan stdout'ta önişle ön işleme)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).  
  
- **PreprocessToFile**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, C ve C++ kaynak dosyalarını önceden işler ve önceden işlenen çıkışı bir dosyaya yazar.  
  
   Daha fazla bilgi için [/P (dosyaya ön işleme)](/cpp/build/reference/p-preprocess-to-a-file).  
  
- **ProcessorNumber**  
  
   İsteğe bağlı `Integer` parametresi.  
  
   Çok işlemcili bir derleme içinde kullanılacak işlemcileri maksimum sayısını belirtir. Bu parametre ile birlikte kullanma **MultiProcessorCompilation** parametresi.  
  
- **ProgramDataBaseFileName**  
  
   İsteğe bağlı `String` parametresi.  
  
   Program veritabanı (PDB) dosyası için bir dosya adı belirtir.  
  
   Daha fazla bilgi için [/Fd (Program veritabanı dosya adı)](/cpp/build/reference/fd-program-database-file-name).  
  
- **RuntimeLibrary**  
  
   İsteğe bağlı `String` parametresi.  
  
   Çok iş parçacıklı bir modülün bir DLL ve çalışma zamanı kitaplığının perakende veya hata ayıklama sürümlerini seçer olup olmadığını gösterir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Çok iş parçacıklı** -   **/MT**  
  
  - **MultiThreadedDebug** -   **/mtd**  
  
  - **MultiThreadedDLL** -   **/MD**  
  
  - **MultiThreadedDebugDLL** - **/MDd**  
  
    Daha fazla bilgi için [/MD, / MT, /LD (çalışma zamanı kitaplığını kullan)](/cpp/build/reference/md-mt-ld-use-run-time-library).  
  
- **RuntimeTypeInfo**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, çalışma zamanında (çalışma zamanı tür bilgisi) C++ nesne türlerini denetlemek için kod ekler.  
  
   Daha fazla bilgi için [/GR (çalışma zamanı türü bilgileri etkinleştir)](/cpp/build/reference/gr-enable-run-time-type-information).  
  
- **Showıncludes**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, ekleme kodu dosyalarının bir listesini çıkarmak derleyicinin neden olur.  
  
   Daha fazla bilgi için [/showıncludes (liste dosyaları içerir)](/cpp/build/reference/showincludes-list-include-files).  
  
- **SmallerTypeCheck**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, bir değer daha küçük bir veri türüne atandı ve veri kaybına neden olan bir çalışma zamanı hatası bildirir.  
  
   Daha fazla bilgi için **/RTCc** seçeneğini [/RTC (çalışma zamanı hata denetimleri)](/cpp/build/reference/rtc-run-time-error-checks).  
  
- **Kaynakları**  
  
   Gerekli `ITaskItem[]` parametresi.  
  
   Kaynak dosyaları boşluklarla ayrılmış bir listesini belirtir.  
  
- **StringPooling**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, program görüntüde aynı dizelerin bir kopyasını oluşturmak derleyiciyi etkinleştirir.  
  
   Daha fazla bilgi için [/GF (yinelenen dizeleri ortadan kaldırın)](/cpp/build/reference/gf-eliminate-duplicate-strings).  
  
- **StructMemberAlignment**  
  
   İsteğe bağlı `String` parametresi.  
  
   Tüm üyeleri için bayt hizalama bir yapıda belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan** - **/Zp1**  
  
  - **1Byte** - **/Zp1**  
  
  - **2Bytes** - **/Zp2**  
  
  - **4Bytes** - **/Zp4**  
  
  - **8Bytes** - **/Zp8**  
  
  - **16Bytes** - **/Zp16**  
  
    Daha fazla bilgi için [/Zp (yapı üyesi hizalama)](/cpp/build/reference/zp-struct-member-alignment).  
  
- **SuppressStartupBanner**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.  
  
   Daha fazla bilgi için [/nologo (Başlangıç başlığını gösterme) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).  
  
- **TrackerLogDirectory**  
  
   İsteğe bağlı `String` parametresi.  
  
   Bu görev için izleme günlüklerinin depolandığı Ara dizini belirtir.  
  
   Daha fazla bilgi için **TLogReadFiles** ve **TLogWriteFiles** bu tabloda parametreler.  
  
- **TreatSpecificWarningsAsErrors**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Belirtilen Derleyici uyarılarını hata olarak değerlendirir.  
  
   Daha fazla bilgi için **/we** `n` seçeneğini [/w, /W0, / W1, / w2, / W3, / W4, / W1, / w2, / W3, / W4, /Wall, WD, / we Wo, wv, /WX (uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level).  
  
- **TreatWarningAsError**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, tüm Derleyici uyarılarını hata olarak değerlendir.  
  
   Daha fazla bilgi için **wx** seçeneğini [/w, /W0, / W1, / w2, / W3, / W4, / W1, / w2, / W3, / W4, /Wall, WD, / we Wo, wv, /WX (uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level).  
  
- **TreatWChar_tAsBuiltInType**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, işle `wchar_t` türü olarak yerel bir tür.  
  
   Daha fazla bilgi için [/ZC: wchar_t (wchar_t yerel türü olduğu)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, derleyici tanımlayan Microsoft'a özgü simgeleri tanımsızı.  
  
   Daha fazla bilgi için **/u** seçeneğini [/U, /u (tanımlanmamış sembol)](/cpp/build/reference/u-u-undefine-symbols).  
  
- **UndefinePreprocessorDefinitions**  
  
   İsteğe bağlı `String[]` parametresi.  
  
   Tanımsız için bir veya daha çok önişlemci sembolleri listesini belirtir.  
  
   Daha fazla bilgi için **/U** seçeneğini [/U, /u (tanımlanmamış sembol)](/cpp/build/reference/u-u-undefine-symbols).  
  
- **UseFullPaths**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, derleyici tanılama geçirilen kaynak kodu dosyalarının tam yolunu görüntüler.  
  
   Daha fazla bilgi için [/FC (kaynak kodu dosyasının tanılamadaki tam yolu)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).  
  
- **UseUnicodeForAssemblerListing**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, çıkış dosyasının UTF-8 biçiminde oluşturulmasını sağlar.  
  
   Daha fazla bilgi için **/fau** seçeneğini [/FA, /Fa (listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file).  
  
- **WarningLevel**  
  
   İsteğe bağlı `String` parametresi.  
  
   En yüksek derleyici tarafından oluşturulup uyarı düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **TurnOffAllWarnings** - **/W0**  
  
  - **Level1** -   **/W1**  
  
  - **Level2** -   **/w2**  
  
  - **Level3** -   **/w3**  
  
  - **Level4** -   **/W4**  
  
  - **EnableAllWarnings** -   **/Wall**  
  
    Daha fazla bilgi için **/W**_n_ seçeneğini [/w, /W0, / W1, / w2, / W3, / W4, / W1, / w2, / W3, / W4, /Wall, WD, / we Wo, wv, /WX (uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level).  
  
- **WholeProgramOptimization**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, tüm programın iyileştirilmesini etkinleştirir.  
  
   Daha fazla bilgi için [/GL (bütün program iyileştirmesi)](/cpp/build/reference/gl-whole-program-optimization).  
  
- **XMLDocumentationFileName**  
  
   İsteğe bağlı `String` parametresi.  
  
   Oluşturulmuş XML belgesi dosyalarının adını belirtir. Bu parametre bir dosya veya dizin adı olabilir.  
  
   Daha fazla bilgi için `name` değişkeninde [/doc (işlem belgeleri açıklamaları) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Ayrıca bkz: **GenerateXMLDocumentationFiles** bu tablodaki parametresi.  
  
- **MinimalRebuildFromTracking**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, izlenen bir artımlı derleme; yapılmaz `false`, yeniden gerçekleştirilir.  
  
- **TLogReadFiles**  
  
   İsteğe bağlı `ITaskItem[]` parametresi.  
  
   Temsil eden öğelerin bir dizisi belirtir *günlükleri izleme dosyası okuma*.  
  
   Bir dosyayı oku izleme günlüğü (*.tlog*), bir görev tarafından okunur ve artımlı derlemeleri desteklemek için proje sistemi tarafından kullanılan giriş dosyalarının adlarını içerir. Daha fazla bilgi için **TrackerLogDirectory** ve **trackfileaccess değeri** bu tabloda parametreler.  
  
- **TLogWriteFiles**  
  
   İsteğe bağlı `ITaskItem[]` parametresi.  
  
   Temsil eden öğelerin bir dizisi belirtir *günlükleri izleme dosyası yazma*.  
  
   Yazma dosya izleme günlük (*.tlog*), bir görev tarafından yazılmış ve artımlı derlemeleri desteklemek için proje sistemi tarafından kullanılır ve çıkış dosyalarının adlarını içerir. Daha fazla bilgi için **TrackerLogDirectory** ve **trackfileaccess değeri** bu tabloda parametreler.  
  
- **TrackFileAccess**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, dosya erişim düzenlerini izler.  
  
   Daha fazla bilgi için **TLogReadFiles** ve **TLogWriteFiles** bu tabloda parametreler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)