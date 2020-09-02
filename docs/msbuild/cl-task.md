---
title: CL görevi | Microsoft Docs
ms.date: 11/04/2016
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
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0e1feee1f7e1d271dd436a1879731354cbd8bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78865343"
---
# <a name="cl-task"></a>CL görevi

Microsoft C++ derleyici aracı 'nı sarmalayan *cl.exe*. Derleyici yürütülebilir (*. exe*) dosyalar, dinamik bağlantı kitaplığı (*. dll*) dosyaları veya kod modülü (*. netmodule*) dosyaları oluşturur. Daha fazla bilgi için bkz. [derleyici seçenekleri](/cpp/build/reference/compiler-options) ve [komut satırından MSBuild 'i kullanma](/cpp/build/msbuild-visual-cpp) ve [komut satırından Microsoft C++ araç takımını kullanma](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametreler

 Aşağıdaki listede **CL** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.

- **AdditionalIncludeDirectories**

   İsteğe bağlı dize [] parametresi.

   İçerme dosyaları için aranan dizinler listesine bir dizin ekler.

   Daha fazla bilgi için bkz. [/i (ek içerme dizinleri)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   İsteğe bağlı dize parametresi.

   Komut satırı seçeneklerinin listesi. Örneğin, "/ \<option1>  / \<option2>  / \<option#> ". Başka bir görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.

   Daha fazla bilgi için bkz. [derleyici seçenekleri](/cpp/build/reference/compiler-options).

- **Addiusingdizinleri**

   İsteğe bağlı dize [] parametresi.

   **#Using** yönergesine geçirilen dosya başvurularını çözümlemek için derleyicinin arayacaktır bir dizin belirtir.

   Daha fazla bilgi için bkz. [/AI (meta veri dizinlerini belirt)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   İsteğe bağlı dize parametresi.

   Her zaman komut satırına yayılan bir dize. Varsayılan değeri "**/c**" dir.

- **Lerlistinglocation 'ı birleştirin**

   Derleme kodu içeren bir listeleme dosyası oluşturur.

   Daha fazla bilgi için/fa [,/FA (listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file)içindeki **/FA** seçeneğine bakın.

- **Lerçıktıyı birleştirin**

   İsteğe bağlı dize parametresi.

   Derleme kodu içeren bir listeleme dosyası oluşturur.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NoList** - *\<none>*

  - **Assemblycode**  -  **/FA**

  - **Assemblyandmachinecode**  -  **/Fac**

  - **Assemblyandsourcecode**  -  **/Fas**

  - **Tümü**  -  **/FACS**

    Daha fazla bilgi için/fa **,** **/fac**, **/Fas**ve/FA,/FA [(listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file)içindeki **/FACS** seçeneklerine bakın.

- **Basicruntimedenetimleri**

   İsteğe bağlı dize parametresi.

   Çalışma zamanı hata denetimleri özelliğini, [runtime_checks](/cpp/preprocessor/runtime-checks) pragma ile birlikte etkinleştirilir ve devre dışı bırakır.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılanını** -                          *\<none>*

  - **StackFrameRuntimeCheck**  -  **/RTCs**

  - **Unınitializedlocalusagecheck**  -  **/RTCu**

  - **Enablefastdenetimleri**  -                           **/RTC1**

    Daha fazla bilgi için bkz. [/RTC (çalışma zamanı hata denetimleri)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   İsteğe bağlı Boolean parametresi.

   İse `true` , bir tarama bilgi dosyası oluşturur.

   Daha fazla bilgi için/fr [,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file)içindeki **/fr** seçeneğine bakın.

- **BrowseInformationFile**

   İsteğe bağlı dize parametresi.

   Tarama bilgisi dosyası için bir dosya adı belirtir.

   Daha fazla bilgi için bu tablodaki **BrowseInformation** parametresine bakın ve ayrıca bkz. [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   İsteğe bağlı Boolean parametresi.

   `true`, Dönüş adresinin üzerine yazılacak bazı arabellek taşmalarını algılar, bu da arabellek boyutu kısıtlamalarını zorlayamayan kodun yararlanmak için ortak bir tekniktir.

   Daha fazla bilgi için bkz. [/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check).

- **Buildingınıde**

   İsteğe bağlı Boolean parametresi.

   İse `true` , **MSBUILD** 'in IDE tarafından çağrıldığını gösterir. Aksi takdirde, **MSBuild** komut satırında çağrılır.

- **CallingConvention**

   İsteğe bağlı dize parametresi.

   İşlev bağımsız değişkenlerinin yığına gönderilme sırasını belirleyen çağırma kuralını belirtir, çağıran işlevin veya çağrılan işlevin, çağrının sonundaki bağımsız değişkenleri yığından kaldırmasının yanı sıra derleyicinin bağımsız işlevleri tanımlamak için kullandığı ad dekorasyon kuralı.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Cdecl**  -  **/GD**

  - **Fastcall**  -                           **/Gr**

  - **Stdcall**  -                           **/Gz**

    Daha fazla bilgi için bkz. [/GD,/gr,/GV,/GZ (çağırma kuralı)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   İsteğe bağlı dize parametresi.

   Giriş dosyasının C veya C++ kaynak dosyası olarak derlenmesi gerekip gerekmediğini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılanını** - *\<none>*

  - **Compileasc**  -  **/TC**

  - **Compileascpp**  -  **/TP**

    Daha fazla bilgi için bkz. [/TC,/TP,/TC,/TP (kaynak dosya türünü belirtin)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   İsteğe bağlı dize parametresi.

   Uygulamaların ve bileşenlerin ortak dil çalışma zamanı (CLR) özelliklerini kullanmasına olanak sağlar.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **yanlýþ** - *\<none>*

  - **doğru**  -  **/clr**

  - **Saf**  -  **/clr: Pure**

  - **Güvenli**  -  **/clr: Safe**

  - **OldSyntax**  -  **/clr: oldSyntax**

    Daha fazla bilgi için bkz. [/clr (ortak dil çalışma zamanı derlemesi)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **Createhotpatchableımage**

   İsteğe bağlı Boolean parametresi.

   İse `true` derleyiciye, *sık*yama için bir görüntü hazırlamasını söyler. Bu parametre, her işlevin ilk yönergesinin, sık yama için gerekli olan iki bayt olmasını sağlar.

   Daha fazla bilgi için bkz. [/hotpatch (düzeltme eki eklenebilir görüntü oluşturma)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   İsteğe bağlı dize parametresi.

   Programınız için oluşturulan hata ayıklama bilgileri türünü ve bu bilgilerin nesne (*. obj*) dosyalarında mi yoksa bir program VERITABANı (pdb) içinde tutulup tutulmadığını seçer.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Eskistil**  -  **/Z7**

  - **Programdatabase**  -  **/Zi**

  - **Editandcontinue**  -  **/Zi**

    Daha fazla bilgi için bkz. [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   İsteğe bağlı Boolean parametresi.

   **True**ise, derleyiciye ANSI C veya ANSI C++ ile uyumlu olmayan dil yapıları için bir hata yaymasını söyler.

   Daha fazla bilgi için [/za,/Ze (dil uzantılarını devre dışı bırak)](/cpp/build/reference/za-ze-disable-language-extensions)içindeki **/za** seçeneğine bakın.

- **Disablespecificuyarılar**

   İsteğe bağlı dize [] parametresi.

   Noktalı virgülle ayrılmış bir listede belirtilen uyarı numaralarını devre dışı bırakır.

   Daha fazla bilgi için `/wd` [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/duvar,/WD,/we,/Wo,/WV,/WX (uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level)içindeki seçeneğe bakın.

- **EnableEnhancedInstructionSet**

   İsteğe bağlı dize parametresi.

   Streaming SIMD Extensions (SSE) ve Streaming SIMD Extensions 2 (SSE2) yönergelerini kullanan kod oluşturma mimarisini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **StreamingSIMDExtensions**  -  **/Arch: SSE**

  - **StreamingSIMDExtensions2**  -  **/Arch: SSE2**

    Daha fazla bilgi için bkz. [/Arch (x86)](/cpp/build/reference/arch-x86).

- **Enablefibersafeiyileştirmeleri**

   İsteğe bağlı Boolean parametresi.

   `true`, Statik iş parçacığı yerel depolama (kullanılarak ayrılan veriler) kullanılarak ayrılan veriler için fiber güvenliği destekler `__declspec(thread)` .

   Daha fazla bilgi için bkz. [/gt (Fiber güvenli iş parçacığı-yerel depolamayı destekle)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   İsteğe bağlı Boolean parametresi.

   İse `true` , Kod analizini etkinleştirin.

   Daha fazla bilgi için bkz. [/analyze (kod analizi)](/cpp/build/reference/analyze-code-analysis).

- **ErrorReporting**

   İsteğe bağlı dize parametresi.

   İç derleyici hatası (ıCE) bilgilerini doğrudan Microsoft 'a sağlamanıza olanak tanır. Varsayılan olarak IDE derlemeleri ayarı **Prompt** olur ve komut satırı Derlemeleriyle ayarı **Queue**olur.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Hiçbiri**  -  **/errorreport: yok**

  - **Komut istemi**  -  **/errorreport: Prompt**

  - **Kuyruk**  -  **/errorreport: kuyruk**

  - **Gönder**  -  **/errorreport: gönder**

    Daha fazla bilgi için bkz. [/errorreport (iç derleyici hatalarını raporla)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   İsteğe bağlı dize parametresi.

   Derleyici tarafından kullanılacak özel durum işleme modelini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **yanlýþ** - *\<none>*

  - **Zaman uyumsuz**  -  **/EHa** dili

  - **Eşitleme**  -  **/EHsc**

  - **Synccthrow**  -  **/EHS**

    Daha fazla bilgi için bkz. [/Eh (özel durum işleme modeli)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   İsteğe bağlı Boolean parametresi.

   İse `true` , kaynak dosyaya eklenen genişletilmiş öznitelikleri olan bir listeleme dosyası oluşturur.

   Daha fazla bilgi için bkz. [/FX (eklenen kodu Birleştir)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   İsteğe bağlı dize parametresi.

   Kod boyutunun veya kod hızının tercih edilip edilmeyeceğini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Tanımlanmadığından** - *\<none>*

  - **Boyut**  -  **/OS**

  - **Hız**  -  **/Ot**

    Daha fazla bilgi için bkz. [/OS,/ot (küçük koda öncelik ver, hızlı kodu tercih et)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   İsteğe bağlı Boolean parametresi.

   `true`, Güvenilir kayan nokta özel durum modelini etkinleştirmesine izin vermez. Özel durumlar, tetiklendikten hemen sonra oluşturulur.

   Daha fazla bilgi için bkz./fp içindeki/**FP: except** seçeneği [(kayan nokta davranışını belirt)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **FloatingPointModel**

   İsteğe bağlı dize parametresi.

   Kayan nokta modelini ayarlar.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Kesin**  -  **/FP: kesin**

  - **Katı**  -  **/FP: Strict**

  - **Hızlı**  -  **/FP: Fast**

    Daha fazla bilgi için bkz. [/FP (kayan nokta davranışını belirt)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope**

   İsteğe bağlı Boolean parametresi.

   İse `true` , Microsoft uzantıları kullanan döngüler [için](/cpp/cpp/for-statement-cpp) ' de standart C++ davranışını uygular ([/ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Daha fazla bilgi için bkz. [/Zc: forScope (döngü kapsamında uygunluğu zorla)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   İsteğe bağlı `String[]` parametre.

   Önişlemci 'nin belirtilen bir veya daha fazla üst bilgi dosyasını işlemesini sağlar.

   Daha fazla bilgi için bkz. [/Fi (zorunlu içerme dosyasını Adlandır)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   İsteğe bağlı **dize []** parametresi.

   Önişlemci 'nin belirtilen bir veya daha fazla **#using** dosyayı işlemesini sağlar.

   Daha fazla bilgi için bkz. [/Fu (zorlanan #using dosyayı adlandır)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **Functionlevellink**

   İsteğe bağlı `Boolean` parametre.

   `true`, Derleyicinin paketlenmiş işlevler (Compts) biçiminde tek tek işlevleri paketleyip dağıtmalarını sağlar.

   Daha fazla bilgi için bkz. [/GY (işlev düzeyi bağlamayı etkinleştir)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , derleyicinin kaynak kodu dosyalarındaki belge açıklamalarını işlemesini ve belge açıklamalarını içeren her kaynak kodu dosyası için bir *. xdc* dosyası oluşturmasını sağlar.

   Daha fazla bilgi için bkz. [/doc (işlem belgeleri açıklamaları) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Ayrıca bkz. bu tablodaki **Xmlbelgeadı** parametresi.

- **Ignorestandardincludepath**

   İsteğe bağlı `Boolean` parametre.

   `true`, DERLEYICININ yolda belirtilen dizinlerde ekleme ve ortam DEĞIŞKENLERINI içerme gibi dosyaları aramasını engeller.

   Daha fazla bilgi için bkz. [/x (Standart içerme yollarını yoksay)](/cpp/build/reference/x-ignore-standard-include-paths).

- **Inlinefunctiongenişleme**

   İsteğe bağlı **dize** parametresi.

   Derleme için satır içi işlev genişletmesinin düzeyini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılanını** - *\<none>*

  - **Devre dışı**  -  **/Ob0**

  - **Yalnızca açıkça satır içi**  -  **/OB1**

  - **Anyuygun**  -  **/Ob2**

    Daha fazla bilgi için bkz. [/ob (satır içi işlev genişletmesi)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , uygulamanızın daha hızlı çalışmasına yardımcı olan işlevin iç veya diğer özel formlarıyla birlikte bazı işlev çağrılarını değiştirir.

   Daha fazla bilgi için bkz. [/Oi (iç Işlevler üret)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **En az yeniden derleme**

   İsteğe bağlı `Boolean` parametre.

   `true`, Değiştirilen c++ sınıf tanımlarını Içeren c++ kaynak dosyalarının (üst bilgi (. h) dosyalarına) yeniden derlenmesi gerekip gerekmediğini belirleyen, en az yeniden derlemeyi sunar.

   Daha fazla bilgi için bkz. [/GD (en az yeniden derlemeyi etkinleştir)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , derlemek için birden çok işlemci kullanın. Bu parametre, bilgisayarınızdaki her bir etkin işlemci için bir işlem oluşturur.

   Daha fazla bilgi için bkz. [/MP (birden çok Işlemle derleme)](/cpp/build/reference/mp-build-with-multiple-processes). Ayrıca bkz. bu tablodaki **ProcessorNumber** parametresi.

- **ObjectFileName**

   İsteğe bağlı **dize** parametresi.

   Varsayılan yerine kullanılacak bir nesne (. obj) dosya adı veya dizin belirtir.

   Daha fazla bilgi için bkz. [/fo (nesne dosyası adı)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   İsteğe bağlı **dize []** parametresi.

   Nesne dosyalarının listesi.

- **OmitDefaultLibName**

   İsteğe bağlı `Boolean` parametre.

   `true`, Nesne (*. obj*) dosyasındaki varsayılan C çalışma zamanı kitaplık adını atlar. Varsayılan olarak, derleyici, bağlayıcıyı doğru kitaplığa yönlendirmek için kitaplığın adını *. obj* dosyasına koyar.

   Daha fazla bilgi için bkz. [/zl (varsayılan kitaplık adını atla)](/cpp/build/reference/zl-omit-default-library-name).

- **Omitframeişaretçiler**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.

   Daha fazla bilgi için bkz. [/oy (çerçeve işaretçisi atlama)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , derleyicinin OpenMP yan tümceleri ve yönergeleri işlemesini sağlar.

   Daha fazla bilgi için bkz. [/OpenMP (openmp 2,0 desteğini etkinleştir)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **İyileştirme**

   İsteğe bağlı **dize** parametresi.

   Hız ve boyut için çeşitli kod iyileştirmeleri belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Devre dışı**  -  **/Od**

  - **Minspace**  -  **/O1**

  - **Maxspeed**  -  **/O2**

  - **Tam**  -  **/Ox**

    Daha fazla bilgi için bkz. [/O Seçenekler (kodu iyileştirme)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   İsteğe bağlı **dize** parametresi.

   Derleme sırasında önceden derlenmiş üst bilgi (*. pch*) dosyası oluşturun veya kullanın.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotUsing** - *\<none>*

  - **Oluştur**  -  **/Rivc**

  - **Kullanım**  -  **/Yu**

    Daha fazla bilgi için bkz. [/Yıc (ön derlenmiş üstbilgi dosyası oluştur)](/cpp/build/reference/yc-create-precompiled-header-file) ve [/yu (önceden derlenmiş üst bilgi dosyası kullan)](/cpp/build/reference/yu-use-precompiled-header-file). Ayrıca, bu tablodaki **PrecompiledHeaderFile** ve **Precompiledheaderçıkışdosyası** parametrelerine bakın.

- **PrecompiledHeaderFile**

   İsteğe bağlı **dize** parametresi.

   Oluşturulacak veya kullanılacak ön derlenmiş üstbilgi dosyası adını belirtir.

   Daha fazla bilgi için bkz. [/Yıc (ön derlenmiş üstbilgi dosyası oluştur)](/cpp/build/reference/yc-create-precompiled-header-file) ve [/yu (önceden derlenmiş üst bilgi dosyası kullan)](/cpp/build/reference/yu-use-precompiled-header-file).

- **Precompiledheaderçıktıdosyası**

   İsteğe bağlı **dize** parametresi.

   Varsayılan yol adını kullanmak yerine önceden derlenmiş üst bilgi için bir yol adı belirtir.

   Daha fazla bilgi için bkz. [/FP (ad. pch dosyası)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , ön işleme sırasında açıklamaları korur.

   Daha fazla bilgi için bkz. [/c (ön işleme sırasında açıklamaları koru)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   İsteğe bağlı `String[]` parametre.

   Kaynak dosyanız için ön işleme sembolünü tanımlar.

   Daha fazla bilgi için bkz. [/d (Önişlemci tanımları)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   İsteğe bağlı `ITaskItem[]` parametre.

   Görevler tarafından tüketilen ve yayılan bir Önişlemci çıkış öğeleri dizisi tanımlar.

- **PreprocessOutputPath**

   İsteğe bağlı `String` parametre.

   **PreprocessToFile** parametresinin önceden işlenmiş çıktıyı yazdığı çıkış dosyasının adını belirtir.

   Daha fazla bilgi için bkz. [/Fi (çıktı dosyası adını Önişle)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , C ve C++ kaynak dosyalarını önceden işler ve önceden işlenen dosyaları standart çıkış cihazına kopyalar.

   Daha fazla bilgi için bkz. [/EP (#line yönergeler olmadan stdout Için önceden işleme)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   İsteğe bağlı `Boolean` parametre.

   Eğer `true` , C ve C++ kaynak dosyalarını önişler ve önceden işlenmiş çıktıyı bir dosyaya yazar.

   Daha fazla bilgi için bkz. [/p (bir dosyaya ön işlem)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   İsteğe bağlı `Integer` parametre.

   Çok işlemcili bir derlemede kullanılacak en fazla işlemci sayısını belirtir. **MultiProcessorCompilation** parametresiyle birlikte bu parametreyi kullanın.

- **ProgramDataBaseFileName**

   İsteğe bağlı `String` parametre.

   Program veritabanı (PDB) dosyası için bir dosya adı belirtir.

   Daha fazla bilgi için bkz. [/FD (program veritabanı dosya adı)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   İsteğe bağlı `String` parametre.

   Çok iş parçacıklı bir modülün bir DLL olup olmadığını belirtir ve çalışma zamanı kitaplığının perakende veya hata ayıklama sürümlerini seçer.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - Çok **Iş parçacıklı**  -  **/MT**

  - **Multithreadeddebug**  -  **/MTD**

  - **Multithreadeddll**  -  **/Md**

  - **Multithreadeddebugdll**  -  **/MDD**

    Daha fazla bilgi için bkz. [/MD,/MT,/LD (çalışma zamanı kitaplığını kullan)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , çalışma zamanında C++ nesne türlerini denetlemek için kod ekler (çalışma zamanı tür bilgisi).

   Daha fazla bilgi için bkz. [/gr (çalışma zamanı türü bilgilerini etkinleştir)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , derleyicinin içerme dosyalarının bir listesini çıktılarına neden olur.

   Daha fazla bilgi için bkz. [/showIncludes (liste içerme dosyaları)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   İsteğe bağlı `Boolean` parametre.

   `true`, Bir değer daha küçük bir veri türüne atanmışsa ve veri kaybına neden olursa bir çalışma zamanı hatası bildiriyor.

   Daha fazla bilgi için [/RTC (çalışma zamanı hata denetimleri)](/cpp/build/reference/rtc-run-time-error-checks)içindeki **/RTCC** seçeneğine bakın.

- **Kaynaklar**

   Gerekli `ITaskItem[]` parametre.

   Boşluklarla ayrılmış kaynak dosyalarının bir listesini belirtir.

- **StringPooling**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , derleyicinin program görüntüsünde özdeş dizelerin bir kopyasını oluşturmasını sağlar.

   Daha fazla bilgi için bkz. [/GF (Yinelenen dizeleri ortadan kaldırma)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **Structmemberhizalaması**

   İsteğe bağlı `String` parametre.

   Bir yapıdaki tüm üyelerin bayt hizalamasını belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan**  -  **/ZP1**

  - **1Bayt**  -  **/ZP1**

  - **2 bayt**  -  **/ZP2**

  - **4 bayt**  -  **/ZP4**

  - **8 bayt**  -  **/ZP8**

  - **16 bayt**  -  **/Zp16**

    Daha fazla bilgi için bkz. [/Zp (struct üye hizalaması)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.

   Daha fazla bilgi için bkz. [/nologo (başlangıç başlığını gösterme) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   İsteğe bağlı `String` parametre.

   Bu görev için İzleme günlüklerinin depolandığı ara dizini belirtir.

   Daha fazla bilgi için bu tablodaki **TLogReadFiles** ve **TLogWriteFiles** parametrelerine bakın.

- **TreatSpecificWarningsAsErrors**

   İsteğe bağlı **dize []** parametresi.

   Belirtilen derleyici uyarıları listesini hata olarak değerlendirir.

   Daha fazla bilgi için **/we** `n` [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/duvar,/WD,/we,/Wo,/WV,/WX (uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level)içindeki/we seçeneğine bakın.

- **TreatWarningAsError**

   İsteğe bağlı `Boolean` parametre.

   Varsa `true` , tüm derleyici uyarılarını hata olarak değerlendirin.

   Daha fazla bilgi için [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/duvar,/WD,/we,/Wo,/WV,/WX (uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level)içindeki **/WX** seçeneğine bakın.

- **TreatWChar_tAsBuiltInType**

   İsteğe bağlı `Boolean` parametre.

   `true`, `wchar_t` Türü yerel bir tür olarak değerlendirin.

   Daha fazla bilgi için bkz. [/Zc: wchar_t (wchar_t yerel tür)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   İsteğe bağlı `Boolean` parametre.

   `true`, Derleyicinin tanımladığı Microsoft 'a özgü sembolleri kaldırır.

   Daha fazla bilgi için/u [,/u (simgeleri tanımla)](/cpp/build/reference/u-u-undefine-symbols)içindeki **/u** seçeneğine bakın.

- **UndefinePreprocessorDefinitions**

   İsteğe bağlı `String[]` parametre.

   Tanımlanacak bir veya daha fazla önişlemci sembol listesini belirtir.

   Daha fazla bilgi için/u [,/u,/u (sembolleri tanımlama)](/cpp/build/reference/u-u-undefine-symbols) **bölümüne bakın** .

- **UseFullPaths**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , tanılamada derleyiciye geçirilen kaynak kodu dosyalarının tam yolunu görüntüler.

   Daha fazla bilgi için bkz. [/FC (kaynak kodu dosyasının Tanılamadaki Tam yolu)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **Useunicodefor, Lerlist**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , çıkış dosyasının UTF-8 biçiminde oluşturulmasına neden olur.

   Daha fazla bilgi için [/FA,/FA (listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file)içindeki **/FAU** seçeneğine bakın.

- **Uyarı düzeyi**

   İsteğe bağlı `String` parametre.

   Derleyici tarafından oluşturulacak en yüksek uyarı düzeyini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - Birlikte **kapatma uyarıları**  -  **/W0**

  - **Level1**  -  **/W1**

  - **Level2**  -  **/W2**

  - **Level3**  -  **/W3**

  - **Level4**  -  **/W4**

  - **Enablealluyarıları**  -  **/Duvar**

    Daha fazla bilgi için [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/duvar,/WD,/we,/Wo,/WV,/WX (uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level)içindeki **/w**_n_ seçeneğine bakın.

- **WholeProgramOptimization**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , tüm program iyileştirmesini sunar.

   Daha fazla bilgi için bkz. [/GL (tüm program iyileştirmesi)](/cpp/build/reference/gl-whole-program-optimization).

- **Xmlbelgeadı**

   İsteğe bağlı `String` parametre.

   Oluşturulan XML belgesi dosyalarının adını belirtir. Bu parametre bir dosya veya dizin adı olabilir.

   Daha fazla bilgi için bkz `name` . [/doc (işlem belgeleri açıklamaları) içindeki bağımsız değişken (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Ayrıca bkz. bu tablodaki **GenerateXMLDocumentationFiles** parametresi.

- **MinimalRebuildFromTracking**

   İsteğe bağlı `Boolean` parametre.

   `true`, İzlenen bir artımlı derleme gerçekleştirilir; varsa `false` , yeniden oluşturma gerçekleştirilir.

- **TLogReadFiles**

   İsteğe bağlı `ITaskItem[]` parametre.

   *Okuma dosyası izleme günlüklerini*temsil eden bir öğe dizisi belirtir.

   Okuma dosyası izleme günlüğü (*. TLog*), bir görev tarafından okunan giriş dosyalarının adlarını içerir ve proje yapı sistemi tarafından artımlı derlemeleri desteklemek için kullanılır. Daha fazla bilgi için bu tablodaki **TrackerLogDirectory** ve **TrackFileAccess** parametrelerine bakın.

- **TLogWriteFiles**

   İsteğe bağlı `ITaskItem[]` parametre.

   *Yazma dosyası izleme günlüklerini*temsil eden bir öğe dizisi belirtir.

   Yazma dosyası izleme günlüğü (*. TLog*), bir görev tarafından yazılan çıkış dosyalarının adlarını içerir ve proje yapı sistemi tarafından artımlı derlemeleri desteklemek için kullanılır. Daha fazla bilgi için bu tablodaki **TrackerLogDirectory** ve **TrackFileAccess** parametrelerine bakın.

- **TrackFileAccess**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , dosya erişim desenlerini izler.

   Daha fazla bilgi için bu tablodaki **TLogReadFiles** ve **TLogWriteFiles** parametrelerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
