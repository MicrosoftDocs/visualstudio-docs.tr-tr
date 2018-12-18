---
title: Bağlantı görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cd79db9b5bfc2e68dea2ff711b2da6ce55c9bc0
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220127"
---
# <a name="link-task"></a>Bağlantı görevi
Visual C++ bağlayıcı aracı sarmalar *link.exe*. Ortak nesne dosyası biçimi (COFF) nesne dosyaları ve yürütülebilir bir dosya oluşturmak için kitaplıklar bağlayıcı aracı bağlantılar (*.exe*) dosya veya dinamik bağlantı kitaplığı (DLL). Daha fazla bilgi için [bağlayıcı seçenekleri](/cpp/build/reference/linker-options).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki parametreleri açıklar **bağlantı** görev. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
-   **AdditionalDependencies**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Giriş dosyaları için bir komut eklemek için bir listesini belirtir.  
  
     Daha fazla bilgi için [bağlantı giriş dosyalarını](/cpp/build/reference/link-input-files).  
  
-   **AdditionalLibraryDirectories**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Kullanıcının ortam kitaplık yolunu geçersiz kılar. Bir dizin adı belirtin.  
  
     Daha fazla bilgi için [/Libpath (ek Libpath)](/cpp/build/reference/libpath-additional-libpath).  
  
-   **AdditionalManifestDependencies**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Yerleştirilecek öznitelikleri belirtir `dependency` bildirim dosyasının.  
  
     Daha fazla bilgi için [/MANIFESTDEPENDENCY (bildirim bağımlılıklarını belirt)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Ayrıca bkz: [yayımcı yapılandırma dosyaları](https://docs.microsoft.com/windows/desktop/SbsCs/publisher-configuration-files).  
  
-   **AdditionalOptions**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Belirtilen komut satırında bağlayıcı seçenekleri listesi. Örneğin, /\<Seçenek1 > /\<Seçenek2 > /\<seçeneği #>. Diğer tarafından temsil edilmez bağlayıcı seçenekleri belirtmek için bu parametreyi kullanın **bağlantı** görev parametresi.  
  
     Daha fazla bilgi için [bağlayıcı seçenekleri](/cpp/build/reference/linker-options).  
  
-   **AddModuleNamesToAssembly**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bir derlemeye bir modül başvurusu ekler.  
  
     Daha fazla bilgi için [assemblymodule (derlemeye MSIL Modülü Ekle)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).  
  
-   **Allowısolatıon**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, işletim sisteminin aramaları bildirim neden olur ve yükler. Varsa `false`, DLL'leri, hiçbir bildirim olduysa gibi yüklendiğini gösterir.  
  
     Daha fazla bilgi için [/ALLOWISOLATION (bildirim arama)](/cpp/build/reference/allowisolation-manifest-lookup).  
  
-   **AssemblyDebug**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, yayan **DebuggableAttribute** hata ayıklama bilgisi izleme ve devre dışı bırakır JIT iyileştirmelerini birlikte öznitelik. Varsa `false`, yayan **DebuggableAttribute** özniteliği ancak hata ayıklama bilgisi izlemeyi devre dışı bırakır ve JIT iyileştirmelerini sağlar.  
  
     Daha fazla bilgi için [assemblydebug (DebuggableAttribute ekleme)](/cpp/build/reference/assemblydebug-add-debuggableattribute).  
  
-   **Assemblylınkresource**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Çıkış dosyasında .NET Framework kaynağına bağlantı oluşturur. kaynak dosyası çıkış dosyasına yerleştirilmez. Kaynağın adını belirtin.  
  
     Daha fazla bilgi için [/assemblylınkresource (.NET Framework kaynağına bağlantı)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).  
  
-   **AttributeFileTracking**  
  
     Örtük **Boole** parametresi.  
  
     Daha ayrıntılı dosya bağlantı artımlı bir kullanıcının davranışını yakalamak için izleme sağlar. Her zaman döndürür `true`.  
  
-   **BaseAddress**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Program veya oluşturulmakta DLL temel adres ayarlar. Belirtin `{address[,size] | @filename,key}`.  
  
     Daha fazla bilgi için [/Base (Temel adres)](/cpp/build/reference/base-base-address).  
  
-   **BuildingInIDE**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     TRUE ise, MSBuild IDE'den çağrılan gösterir. Aksi takdirde, MSBuild komut satırından çağrılır gösterir.  
  
     Bu parametre, denk bağlayıcı seçeneği vardır.  
  
-   **CLRImageType**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bir ortak dil çalışma zamanı (CLR) görüntü türünü ayarlar.  
  
     Her biri için bir bağlayıcı seçeneği karşılık gelen şu değerlerden birini belirtin.  
  
    -   **Varsayılan** - *\<yok >*  
  
    -   **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
    -   **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
    -   **ForceSafeILImage** - **kullanılır**  
  
    Daha fazla bilgi için [/CLRIMAGETYPE (CLR görüntü türünü belirt)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).  
  
-   **Clrsupportlasterror'ü**  
  
     İsteğe bağlı **dize** parametresi.  
  
     P/Invoke mekanizmasıyla çağrılan işlevlerin son hata kodunu korur.  
  
     Her biri için bir bağlayıcı seçeneği karşılık gelen şu değerlerden birini belirtin.  
  
    -   **Etkin** - **/CLRSupportLastError**  
  
    -   **Devre dışı bırakılmış** - **/CLRSupportLastError:NO**  
  
    -   **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    Daha fazla bilgi için [/CLRSUPPORTLASTERROR (son hata kodunu Koru PInvoke çağrıları için)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).  
  
-   **Clrthreadattrıbute**  
  
     İsteğe bağlı **dize** parametresi.  
  
     CLR programınızın giriş noktası için iş parçacığı oluşturma özniteliğini açıkça belirtir.  
  
     Her biri için bir bağlayıcı seçeneği karşılık gelen şu değerlerden birini belirtin.  
  
    -   **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE: yok**  
  
    -   **MTAThreadingAttribute** - **MTA**  
  
    -   **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    Daha fazla bilgi için [/CLRTHREADATTRIBUTE (iş parçacığı özniteliğini Ayarla CLR)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).  
  
-   **CLRUnmanagedCodeCheck**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Bağlayıcı uygulayıp uygulamayacağını belirtir **SuppressUnmanagedCodeSecurityAttribute** bağlayıcı tarafından oluşturulan P/Invoke çağırıyor yönetilen koddan yerel DLL'lere için.  
  
    Daha fazla bilgi için [/clrunmanagedcodecheck (SuppressUnmanagedCodeSecurityAttribute Ekle)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).  
  
-   **CreateHotPatchableImage**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Görüntüyü Yeniden başlatmasız düzeltme için hazırlar.  
  
     Bir bağlayıcı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    -   **Etkin** - **/FUNCTIONPADMIN**  
  
    -   **X86Image** - **/FUNCTIONPADMIN:5**  
  
    -   **X64Image** - **/FUNCTIONPADMIN:6**  
  
    -   **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    Daha fazla bilgi için [/FUNCTIONPADMIN (düzeltme eki eklenebilen görüntü oluşturma)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).  
  
-   **DataExecutionPrevention**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, yürütülebilir bir dosya Windows Veri Yürütme Engellemesi özelliği ile uyumlu olduğunun saptandığını gösterir.  
  
     Daha fazla bilgi için [/NXCOMPAT (veri yürütme önlemesi ile uyumlu)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).  
  
-   **DelayLoadDLLs**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bu parametre neden *Gecikmeli yükleme* dll. Bir DLL gecikme yükü adını belirtin.  
  
     Daha fazla bilgi için [/delayload (gecikme yükü içe)](/cpp/build/reference/delayload-delay-load-import).  
  
-   **DelaySign**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bir derlemeyi kısmen imzalar. Varsayılan değer olan `false`.  
  
     Daha fazla bilgi için [/delaysign (bir derlemeyi kısmen imzalayın)](/cpp/build/reference/delaysign-partially-sign-an-assembly).  
  
-   **Sürücü**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bir Windows NT Çekirdek modu sürücüsü oluşturmak için bu parametreyi belirtin.  
  
     Her biri için bir bağlayıcı seçeneği karşılık gelen şu değerlerden birini belirtin.  
  
    -   **NotSet** - *\<yok >*  
  
    -   **Sürücü** - **Driver/Driver**  
  
    -   **UpOnly** - **/DRIVER:UPONLY**  
  
    -   **WDM** -   **/DRIVER: WDM**  
  
    Daha fazla bilgi için [(Windows NT Çekirdek modu sürücüsü) Driver/Driver](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).  
  
-   **EmbedManagedResourceFile**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bir derlemeye kaynak dosyası gömer. Gerekli kaynak dosya adı belirtin. İsteğe bağlı olarak kaynak yüklemek için kullanılan mantıksal adı belirtin ve **özel** seçeneği, bütünleştirilmiş kod bildirimi kaynak dosyası özel olduğunu belirtir.  
  
     Daha fazla bilgi için [koduna konmaz (yönetilen kaynağı katıştır)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).  
  
-   **EnableCOMDATFolding**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, eşdeğer COMDAT katlaması sağlar.  
  
     Daha fazla bilgi için `ICF[= iterations]` bağımsız değişkeni [OPT (iyileştirmeler)](/cpp/build/reference/opt-optimizations).  
  
-   **EnableUAC**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, kullanıcı hesabı denetimi (UAC) bilgisinin program bildiriminde gömülü olup olmadığını belirtir.  
  
     Daha fazla bilgi için [/MANIFESTUAC (bildirimdeki UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **EntryPointSymbol**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Başlangıç adresi olarak giriş noktası işlevini belirtir bir *.exe* dosyası veya DLL. Bir işlev adı parametre değeri olarak belirtin.  
  
     Daha fazla bilgi için [/Entry (giriş noktası simgesi)](/cpp/build/reference/entry-entry-point-symbol).  
  
-   **FixedBaseAddress**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, yalnızca tercih edilen temel adresini bir program veya yüklenmesi gereken DLL oluşturur.  
  
     Daha fazla bilgi için [/FIXED (sabit temel adres)](/cpp/build/reference/fixed-fixed-base-address).  
  
-   **ForceFileOutput**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Geçerli bir oluşturma söyler *.exe* dosyası veya DLL bile sembole başvurulduğunda ancak tanımlanmamış veya birden çok kez tanımlanmış.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    -   **Etkin** -   **/FORCE**  
  
    -   **MultiplyDefinedSymbolOnly** -   **/Force: multıple**  
  
    -   **UndefinedSymbolOnly** -   **/FORCE: KARARSIZ**  
  
    Daha fazla bilgi için [/Force (dosya çıktısını zorla)](/cpp/build/reference/force-force-file-output).  
  
-   **ForceSymbolReferences**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bu parametre, belirtilen sembolü sembol tablosuna eklemek için söyler.  
  
     Daha fazla bilgi için [/Include (simge başvurularını zorla)](/cpp/build/reference/include-force-symbol-references).  
  
-   **FunctionOrder**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bu parametre imajın içine önceden belirlenmiş bir sırada belirtilen paketlenmiş işlevler (Comdat'lar) koyarak programınızı iyileştirir.  
  
     Daha fazla bilgi için [/order (işlevleri Sırala Put)](/cpp/build/reference/order-put-functions-in-order).  
  
-   **GenerateDebugInformation**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, hata ayıklama bilgileri oluşturur *.exe* dosyası veya DLL.  
  
     Daha fazla bilgi için [/Debug (hata ayıklama bilgileri üret)](/cpp/build/reference/debug-generate-debug-info).  
  
-   **GenerateManifest**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, yan yana bildirim dosyası oluşturur.  
  
     Daha fazla bilgi için [/MANIFEST (yan yana derleme bildirimi oluşturma)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).  
  
-   **GenerateMapFile**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, oluşturur bir *Haritası*. Eşleme dosyasının dosya adı uzantısı *.map*.  
  
     Daha fazla bilgi için [Map (eşlem Oluştur)](/cpp/build/reference/map-generate-mapfile).  
  
-   **HeapCommitSize**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Aynı anda ayrılacak yığında fiziksel bellek miktarını belirtir.  
  
     Daha fazla bilgi için `commit` değişkeninde [/HEAP (yığın boyutunu Ayarla)](/cpp/build/reference/heap-set-heap-size). Ayrıca bkz **HeapReserveSize** parametresi.  
  
-   **HeapReserveSize**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Sanal bellekte toplam yığın ayırma belirtir.  
  
     Daha fazla bilgi için `reserve` değişkeninde [/HEAP (yığın boyutunu Ayarla)](/cpp/build/reference/heap-set-heap-size). Ayrıca bkz **HeapCommitSize** bu tablodaki parametresi.  
  
-   **IgnoreAllDefaultLibraries**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, söyler kaldırın ya da daha fazla varsayılan kitaplık kitaplıkları listesinden bunu ne zaman arar dış başvuruları çözümleniyor.  
  
     Daha fazla bilgi için [/nodefaultlıb (kitaplıkları yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **IgnoreEmbeddedIDL**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, kaynak kodundaki IDL öznitelikleri içine işlenmemesi gerektiğini belirten bir *.idl* dosya.  
  
     Daha fazla bilgi için [/ıgnoreıdl (öznitelikleri Mıdl'ye işleme)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).  
  
-   **IgnoreImportLibrary**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bu yapılandırmanın oluşturduğu içeri aktarma kitaplığının bağımlı projelere aktarılmaması gerektiğini belirtir.  
  
     Bu parametre için bir bağlayıcı seçeneği karşılık gelmiyor.  
  
-   **IgnoreSpecificDefaultLibraries**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bir veya daha fazla varsayılan kitaplık adlarını belirtir. Birden çok kitaplık noktalı virgül kullanarak ayırın.  
  
     Daha fazla bilgi için [/nodefaultlıb (kitaplıkları yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **ImageHasSafeExceptionHandlers**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, yalnızca görüntünün güvenli özel durum işleyicileri tablosu da üretebileceği, bağlayıcı bir görüntü üretiyor.  
  
     Daha fazla bilgi için [SAFESEH (görüntüde güvenli özel durum işleyicileri var)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).  
  
-   **ImportLibrary**  
  
     Varsayılan kitaplık adını değiştirir bir kullanıcı tarafından belirtilen içeri aktarma kitaplığı adı.  
  
     Daha fazla bilgi için [/IMPLIB (içeri aktarma kitaplığını Adlandır)](/cpp/build/reference/implib-name-import-library).  
  
-   **KeyContainer**  
  
     İsteğe bağlı **dize** parametresi.  
  
     İmzalı bir derleme için anahtarı içeren kapsayıcı.  
  
     Daha fazla bilgi için [/keycontainer (derlemeyi imzalamak için belirtin bir anahtar kapsayıcısı)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Ayrıca bkz **KeyFile** bu tablodaki parametresi.  
  
-   **KeyFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     İmzalı bir derleme için anahtarı içeren dosyayı belirtir.  
  
     Daha fazla bilgi için [/keyfile (belirtin anahtar veya bir derlemeyi imzalamak için anahtar çifti)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Ayrıca bkz **KeyContainer** parametresi.  
  
-   **LargeAddressAware**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, uygulama 2 gigabayt'tan daha büyük adresleri işleyebilir.  
  
     Daha fazla bilgi için [/largeaddressaware (büyük adresleri işle)](/cpp/build/reference/largeaddressaware-handle-large-addresses).  
  
-   **LinkDLL**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, DLL olarak ana çıkış dosyası oluşturur.  
  
     Daha fazla bilgi için [/dll (DLL derleme)](/cpp/build/reference/dll-build-a-dll).  
  
-   **LinkErrorReporting**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Derleyici iç hatası (ICE) bilgilerini doğrudan Microsoft'a sağlamanıza olanak tanır.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    -   **NoErrorReport** -   **/errorreport: yok**  
  
    -   **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
    -   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
    -   **SendErrorReport** - **okunmalı**  
  
    Daha fazla bilgi için [/errorreport (dahili bağlayıcı hatalarını raporla)](/cpp/build/reference/errorreport-report-internal-linker-errors).  
  
-   **LinkIncremental**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, artımlı bağlamayı etkinleştirir.  
  
     Daha fazla bilgi için [/INCREMENTAL (artımlı Bağla)](/cpp/build/reference/incremental-link-incrementally).  
  
-   **LinkLibraryDependencies**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, proje bağımlılıklarının kitaplık çıkışları içinde otomatik olarak bağlandığını belirtir.  
  
     Bu parametre için bir bağlayıcı seçeneği karşılık gelmiyor.  
  
-   **LinkStatus**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bağlayıcı bağlantıyı yüzde tamamlandıktan gösteren bir İlerleme göstergesi görüntülemesi gerektiğini belirtir.  
  
     Daha fazla bilgi için `STATUS` bağımsız değişkeni [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **LinkTimeCodeGeneration**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Profil temelli İyileştirme seçeneklerini belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    -   **Varsayılan** - *\<yok >*  
  
    -   **UseLinkTimeCodeGeneration** - **/LTCG**  
  
    -   **PGInstrument** - **/LTCG:PGInstrument**  
  
    -   **PGOptimization** - **/LTCG:PGOptimize**  
  
    -   **PGUpdate**  
  
         \- **/LTCG:PGUpdate**  
  
    Daha fazla bilgi için [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **Manıfestfıle**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Varsayılan bildirim dosyası adı için belirtilen dosya adını değiştirir.  
  
     Daha fazla bilgi için [/MANIFESTFILE (bildirim dosyasını Adlandır)](/cpp/build/reference/manifestfile-name-manifest-file).  
  
-   **MapExports**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, eşleme dosyasında dışarı aktarılan işlevleri dahil etmesini bağlayıcıya bildirir.  
  
     Daha fazla bilgi için `EXPORTS` bağımsız değişkeni [mapınfo (bilgileri eşlem dosyası Ekle)](/cpp/build/reference/mapinfo-include-information-in-mapfile).  
  
-   **MapFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Belirtilen dosya adı için varsayılan eşleme dosyası adını değiştirir.  
  
-   **MergedIDLBaseFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Dosya adı uzantısı ve dosya adını belirtir *.idl* dosya.  
  
     Daha fazla bilgi için [/ıdlout (MIDL adı Çıkış dosyalarını)](/cpp/build/reference/idlout-name-midl-output-files).  
  
-   **MergeSections**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bir görüntü olarak bölümlerde birleştirir. Belirtin `from-section=to-section`.  
  
     Daha fazla bilgi için [/Merge (bölümleri Birleştir)](/cpp/build/reference/merge-combine-sections).  
  
-   **MidlCommandFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     MIDL komut satırı seçeneklerini içeren dosyanın adını belirtin.  
  
     Daha fazla bilgi için [/MIDL (belirtin MIDL komut satırı seçenekleri)](/cpp/build/reference/midl-specify-midl-command-line-options).  
  
-   **MinimumRequiredVersion**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Alt sistemin gerekli en düşük sürümü belirtir. Bağımsız değişkenler, 0 ila 65.535 aralığındaki ondalık sayılardır.  
  
-   **ModuleDefinitionFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Adını belirten bir [modül tanım dosyası](/cpp/build/reference/module-definition-dot-def-files).  
  
     Daha fazla bilgi için [/def (modül tanım dosyasını belirt)](/cpp/build/reference/def-specify-module-definition-file).  
  
-   **MSDOSStubFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Belirtilen MS-DOS saplama programını Win32 programına iliştirir.  
  
     Daha fazla bilgi için [/stub (MS-DOS saplama dosyası adı)](/cpp/build/reference/stub-ms-dos-stub-file-name).  
  
-   **NoEntryPoint**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, yalnızca kaynak DLL yüklemesini belirtir.  
  
     Daha fazla bilgi için [/NOENTRY (giriş noktası yok)](/cpp/build/reference/noentry-no-entry-point).  
  
-   **ObjectFiles**  
  
     Örtük **String []** parametresi.  
  
     Bağlantılı nesne dosyaları belirtir.  
  
-   **OptimizeReferences**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, işlevleri ve/veya hiçbir zaman başvurulmayan verileri ortadan kaldırır.  
  
     Daha fazla bilgi için `REF` değişkeninde [OPT (iyileştirmeler)](/cpp/build/reference/opt-optimizations).  
  
-   **OutputFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Varsayılan adı ve bağlayıcının oluşturduğu program konumunu geçersiz kılar.  
  
     Daha fazla bilgi için [/OUT (çıktı dosyası adı)](/cpp/build/reference/out-output-file-name).  
  
-   **PerUserRedirection**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true` ve çıkışı kayda etkin zorlar kayıt için Yazar **HKEY_CLASSES_ROOT** için yönlendirilmesi **HKEY_CURRENT_USER**.  
  
-   **PreprocessOutput**  
  
     İsteğe bağlı `ITaskItem[]` parametresi.  
  
     Tüketilen ve görevler tarafından yayılan önişlemci çıktısını öğeleri bir dizisi tanımlanmaktadır.  
  
-   **PreventDllBinding**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, gösterir *Bind.exe'yi* bağlantılı görüntü bağlı.  
  
     Daha fazla bilgi için [/ALLOWBIND (önlemek DLL bağlamayı)](/cpp/build/reference/allowbind-prevent-dll-binding).  
  
-   **Profili**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, kullanılabilir bir çıktı dosyası üretir **performans araçları** profil oluşturucu.  
  
     Daha fazla bilgi için [PROFILE (performans araçları Profil Oluşturucusu)](/cpp/build/reference/profile-performance-tools-profiler).  
  
-   **ProfileGuidedDatabase**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Adını belirtir *.pgd* çalışan programa hakkındaki bilgileri tutmak için kullanılan dosya  
  
     Daha fazla bilgi için [/PGD (Profil temelli iyileştirmeler için veritabanını belirt)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).  
  
-   **ProgramDatabaseFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bağlayıcının oluşturduğu program veritabanı (PDB) için bir ad belirtir.  
  
     Daha fazla bilgi için [/pdb (program veritabanını kullan)](/cpp/build/reference/pdb-use-program-database).  
  
-   **RandomizedBaseAddress**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, rastgele yükleme zamanında temellendirilebilen bir yürütülebilir görüntü oluşturur *adres boşluğu düzeni rastgele seçimini* Windows (ASLR) özelliği.  
  
     Daha fazla bilgi için [dynamıcbase (adres boşluğu düzeni rastgele'seçimini kullan)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).  
  
-   **RegisterOutput**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bu derlemenin birincil çıkışının kaydeder.  
  
-   **SectionAlignment**  
  
     İsteğe bağlı **tamsayı** parametresi.  
  
     Programın doğrusal adres alanındaki her bölümün hizalamasını belirtir. Parametre değeri bayt birim sayısı ve ikinin üssü.  
  
     Daha fazla bilgi için [/ALIGN (bölüm hizalama)](/cpp/build/reference/align-section-alignment).  
  
-   **SetChecksum**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, üst bilgisinde sağlama toplamını ayarlar bir *.exe* dosya.  
  
     Daha fazla bilgi için [/Release (sağlama toplamını Ayarla)](/cpp/build/reference/release-set-the-checksum).  
  
-   **ShowProgress**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bağlama işlemi için ilerleme raporları, ayrıntı düzeyini belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    -   **NotSet** - *\<yok >*  
  
    -   **LinkVerbose** - **/VERBOSE**  
  
    -   **LinkVerboseLib** - **/VERBOSE:Lib**  
  
    -   **LinkVerboseICF** - **/VERBOSE:ICF**  
  
    -   **LinkVerboseREF** - **/VERBOSE:REF**  
  
    -   **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
    -   **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    Daha fazla bilgi için [/verbose (ilerleme iletilerini Yazdır)](/cpp/build/reference/verbose-print-progress-messages).  
  
-   **Kaynakları**  
  
     Gerekli `ITaskItem[]` parametresi.  
  
     Tüketilen ve görevler tarafından yayılan MSBuild kaynak dosya öğeleri bir dizisi tanımlanmaktadır.  
  
-   **SpecifySectionAttributes**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bir bölümün özniteliklerini belirtir. Bu ne zaman ayarlanan özniteliklerini geçersiz kılar *.obj* bölümü derlenen için dosya.  
  
     Daha fazla bilgi için [/SECTION (bölüm özniteliklerini belirt)](/cpp/build/reference/section-specify-section-attributes).  
  
-   **StackCommitSize**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Ek bellek tahsis edildiğinde her ayırma fiziksel bellek miktarını belirtir.  
  
     Daha fazla bilgi için `commit` bağımsız değişkeni [/STACK (yığın ayırmaları)](/cpp/build/reference/stack-stack-allocations).  
  
-   **StackReserveSize**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Sanal bellekte toplam yığın ayırma boyutunu belirtir.  
  
     Daha fazla bilgi için `reserve` bağımsız değişkeni [/STACK (yığın ayırmaları)](/cpp/build/reference/stack-stack-allocations).  
  
-   **StripPrivateSymbols**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Dağıtmak için müşterilerinize istemediğiniz sembolleri atar ikinci bir program veritabanı (PDB) dosyası oluşturur. İkinci PDB dosyasının adını belirtin.  
  
     Daha fazla bilgi için [/pdbstrıpped (özel simgeleri Şerit)](/cpp/build/reference/pdbstripped-strip-private-symbols).  
  
-   **Alt sistem**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Yürütülebilir dosya için ortamı belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    -   **NotSet** - *\<yok >*  
  
    -   **Konsol** -   **/Subsystem: Console**  
  
    -   **Windows** - **/SUBSYSTEM:WINDOWS**  
  
    -   **Yerel** - **natıve**  
  
    -   **EFI uygulaması** - **/SUBSYSTEM:EFI_APPLICATION**  
  
    -   **EFI Önyükleme servisi sürücüsü** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
    -   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
    -   **EFI çalışma zamanı** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
    -   **Wındowsce** - **/SUBSYSTEM:WINDOWSCE**  
  
    -   **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Daha fazla bilgi için [/Subsystem (alt belirtin)](/cpp/build/reference/subsystem-specify-subsystem).  
  
-   **SupportNobindOfDelayLoadedDLL**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bağlanabilir bir içeri aktarma adres tablosu (IAT) son görüntüde eklememesini söyler.  
  
     Daha fazla bilgi için `NOBIND` bağımsız değişkeni [/delay (gecikme yükü içe aktarma ayarları)](/cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SupportUnloadOfDelayLoadedDLL**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, açık DLL'i kaldırma desteklemek için gecikme yük yardımcı işlevinizi söyler.  
  
     Daha fazla bilgi için `UNLOAD` bağımsız değişkeni [/delay (gecikme yükü içe aktarma ayarları)](/cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SuppressStartupBanner**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.  
  
     Daha fazla bilgi için [/nologo (Başlangıç başlığını gösterme) (Bağlayıcı)](/cpp/build/reference/nologo-suppress-startup-banner-linker).  
  
-   **SwapRunFromCD**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, işletim sisteminin önce bağlayıcı çıktısını takas dosyasına kopyalama bildirir ve ardından görüntüyü oradan çalıştırın.  
  
     Daha fazla bilgi için `CD` bağımsız değişkeni [swaprun (dosya çıktısını takas dosyasına yükle bağlayıcı)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Ayrıca bkz **SwapRunFromNET** parametresi.  
  
-   **SwapRunFromNET**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, işletim sisteminin önce bağlayıcı çıktısını takas dosyasına kopyalama bildirir ve ardından görüntüyü oradan çalıştırın.  
  
     Daha fazla bilgi için `NET` bağımsız değişkeni [swaprun (dosya çıktısını takas dosyasına yükle bağlayıcı)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Ayrıca bkz **SwapRunFromCD** bu tablodaki parametresi.  
  
-   **TargetMachine**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Program veya DLL için hedef platformu belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    -   **NotSet** - *\<yok >*  
  
    -   **MachineARM** - **/MACHINE:ARM**  
  
    -   **MachineEBC** - **/MACHINE:EBC**  
  
    -   **MachineIA64** - **/MACHINE:IA64**  
  
    -   **MachineMIPS** - **/MACHINE:MIPS**  
  
    -   **MachineMIPS16** - **/MACHINE:MIPS16**  
  
    -   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
    -   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
    -   **MachineSH4** - **/MACHINE:SH4**  
  
    -   **MachineTHUMB** - **/MACHINE:THUMB**  
  
    -   **MachineX64** - **/MACHINE:X 64**  
  
    -   **MachineX86** - **/MACHINE:X 86**  
  
    Daha fazla bilgi için [/Machine (hedef platformu belirt)](/cpp/build/reference/machine-specify-target-platform).  
  
-   **TerminalServerAware**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, program görüntüsünün isteğe bağlı üst bilgisindeki ımage_optıonal_header DllCharacteristics alanında bir bayrak ayarlar. Bu bayrak ayarlandığında Terminal sunucusu uygulamada bazı değişiklikler yapmaz.  
  
     Daha fazla bilgi için [/TSAWARE (Terminal sunucusu oluşturma algılayan uygulama)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).  
  
-   **TrackerLogDirectory**  
  
     İsteğe bağlı **dize** parametresi.  
  
     İzleyici günlüğü dizini belirtir.  
  
-   **TreatLinkerWarningAsErrors**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bağlayıcı bir uyarı oluşturduğunda çıkış dosyası oluşturulmamasını sağlar.  
  
     Daha fazla bilgi için [/WX (Bağlayıcı uyarılarını hata olarak)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).  
  
-   **TurnOffAssemblyGeneration**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bir .NET Framework derlemesinin olmadan geçerli çıkış dosyası için bir görüntü oluşturur.  
  
     Daha fazla bilgi için [noassembly (MSIL modülü Oluştur)](/cpp/build/reference/noassembly-create-a-msil-module).  
  
-   **TypeLibraryFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Dosya adı uzantısı ve dosya adını belirtir *.tlb* dosya. Bir dosya adı veya yolu ve dosya adı belirtin.  
  
     Daha fazla bilgi için [/tlbout (.tlb dosyası Adlandır)](/cpp/build/reference/tlbout-name-dot-tlb-file).  
  
-   **TypeLibraryResourceID**  
  
     İsteğe bağlı **tamsayı** parametresi.  
  
     Bağlayıcı tarafından oluşturulan tür kitaplığı için bir kullanıcı tarafından belirtilen değeri atar. 1 ile 65535 arasında bir değer belirtin.  
  
     Daha fazla bilgi için [/TLBID (TypeLib için kaynak kimliği belirtin)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).  
  
-   **UACExecutionLevel**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Altında kullanıcı hesabı denetimi ile çalışırken, uygulama için istenen yürütme düzeyini belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    -   **AsInvoker** - `level='asInvoker'`  
  
    -   **HighestAvailable** - `level='highestAvailable'`  
  
    -   **RequireAdministrator'a** - `level='requireAdministrator'`  
  
    Daha fazla bilgi için `level` bağımsız değişkeni [/MANIFESTUAC (bildirimdeki UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UACUIAccess**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, uygulama kullanıcı arabirimi koruma düzeylerinin atlar ve sürücüleri giriş izni yüksek windows masaüstü için; Aksi takdirde `false`.  
  
     Daha fazla bilgi için `uiAccess` bağımsız değişkeni [/MANIFESTUAC (bildirimdeki UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UseLibraryDependencyInputs**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`kitaplıkçı aracının kullanılan yerine, kitaplık dosyasının kendisi proje bağımlılıklarının kitaplık çıkışları olduğunda bağlanır.  
  
-   **Sürüm**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Üst bilgisinde sürüm numarası put *.exe* veya *.dll* dosya. Belirtin "`major[.minor]`". `major` Ve `minor` bağımsız değişkenler 0 ile 65535 arasında ondalık sayı.  
  
     Daha fazla bilgi için [/VERSION (sürüm bilgileri)](/cpp/build/reference/version-version-information).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
