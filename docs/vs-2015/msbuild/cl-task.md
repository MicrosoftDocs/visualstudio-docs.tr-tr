---
title: CL görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb9b6924f5d11e3d857308e3a1bcf1e1644f78bc
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220254"
---
# <a name="cl-task"></a>CL Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ Derleyici aracı sarmalar cl.exe. Derleyici, yürütülebilir (.exe) dosyaları, dinamik bağlantı kitaplığı (.dll) dosyaları ya da kod modülüdür (.netmodule) dosyaları oluşturur. Daha fazla bilgi için [derleyici seçenekleri](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır **CL** görev. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
- **AdditionalIncludeDirectories**  
  
   İsteğe bağlı dize [] parametresi.  
  
   Bir dizin dahil etme dosyaları için Aranan dizinleri listesine ekler.  
  
   Daha fazla bilgi için [/ı (ek içeren dizinler)](http://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   İsteğe bağlı dize parametresi.  
  
   Komut satırı seçeneklerinin listesi. Örneğin, "/*Seçenek1* /*Seçenek2* /*seçeneği #*". Herhangi bir görev parametresi tarafından temsil edilmez komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.  
  
   Daha fazla bilgi için [derleyici seçenekleri](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **AdditionalUsingDirectories** isteğe bağlı dize [] parametresi.  
  
   Geçirilen dosya başvurularını çözümlemek için derleyicinin arama yapacağı dizini belirtir **#using** yönergesi.  
  
   Daha fazla bilgi için [/AI (meta veri dizinlerini belirtin)](http://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   İsteğe bağlı dize parametresi.  
  
   Bir dize, komut satırında yayılan her zaman. Varsayılan değeri "**/c**".  
  
- **AssemblerListingLocation**  
  
   Derleme kodu içeren bir listeleme dosyası oluşturur.  
  
   Daha fazla bilgi için **/Fa** seçeneğini [/FA, /Fa (listeleme dosyası)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **AssemblerOutput**  
  
   İsteğe bağlı dize parametresi.  
  
   Derleme kodu içeren bir listeleme dosyası oluşturur.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **NoListing** - *\<yok >*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** - **/FAc**  
  
  - **AssemblyAndSourceCode** - **/FAs**  
  
  - **Tüm** -   **/facs**  
  
    Daha fazla bilgi için **/FA**, **/Fac**, **/Fas**, ve **/facs** seçeneklerini [/FA, /Fa (listeleme dosyası)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **BasicRuntimeChecks**  
  
   İsteğe bağlı dize parametresi.  
  
   Sağlar ve birlikte çalışma zamanı hata denetimleri özelliğini devre dışı bırakır [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) pragması.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan** -                          *\<yok >*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **/RTCu**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Daha fazla bilgi için [/RTC (çalışma zamanı hata denetimleri)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, gözatma bilgisi dosyası oluşturur.  
  
   Daha fazla bilgi için **/FR** seçeneğini [/FR, /Fr (oluşturun. SBR dosyası)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   İsteğe bağlı dize parametresi.  
  
   Gözatma bilgisi dosyası için bir dosya adı belirtir.  
  
   Daha fazla bilgi için **BrowseInformation** Bu tablo, ayrıca bkz: parametresinde [/FR, /Fr (oluşturun. SBR dosyası)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, dönüş adresi, arabellek boyutu kısıtlamaları zorunlu kılmaz kod kötüye için genel bir tekniktir üzerine bazı arabellek taşmalarına algılar.  
  
   Daha fazla bilgi için [/GS (arabellek güvenlik denetimi)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
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
  
    Daha fazla bilgi için [/Gd, / Gr, GV, /Gz (çağırma kuralı)](http://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   İsteğe bağlı dize parametresi.  
  
   Giriş dosyası olarak bir C veya C++ kaynak dosyasını derlemek belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan** - *\<yok >*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Daha fazla bilgi için [/Tc, /Tp, /TC, /TP (kaynak dosya türünü belirtin)](http://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   İsteğe bağlı dize parametresi.  
  
   Ortak dil çalışma zamanı (CLR) özellikleri kullanmak, uygulamaları ve bileşenleri sağlar.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **false** - *\<yok >*  
  
  - **doğru** -   **/CLR**  
  
  - **Saf** -   **/CLR: pure**  
  
  - **Safe** - **/clr:safe**  
  
  - **OldSyntax** - **/clr:oldSyntax**  
  
    Daha fazla bilgi için [/CLR (ortak dil çalışma zamanı derlemesi)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **CreateHotpatchableImage**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, derleyiciye bir görüntü için hazırlama *Yeniden başlatmasız düzeltme*. Bu parametre, Yeniden başlatmasız düzeltme için gerekli olan her işlevin ilk yönergesinin iki bayt olmasını sağlar.  
  
   Daha fazla bilgi için [/hotpatch (düzeltme eki eklenebilen görüntü oluşturma)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   İsteğe bağlı dize parametresi.  
  
   Programınız ve bu bilgileri nesne (.obj) dosyalarında veya bir program veritabanı (PDB) tutulur için oluşturulan hata ayıklama bilgisini türünü seçer.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **OldStyle** - **/Z7**  
  
  - **ProgramDatabase** -   **/zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Daha fazla bilgi için [/z7, / zi, /zı (hata ayıklama bilgileri biçimi)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa **true**, ANSI C veya C++ ANSI ile uyumlu olmayan dil yapıları için hata yayma derleyiciye.  
  
   Daha fazla bilgi için **/Za** seçeneğini [/Za, /Ze (dil uzantılarını devre dışı bırak)](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
- **DisableSpecificWarnings**  
  
   İsteğe bağlı dize [] parametresi.  
  
   Noktalı virgülle ayrılmış bir listede belirtilen uyarı numaralarını devre dışı bırakır.  
  
   Daha fazla bilgi için `/wd` seçeneğini [/w, /W0, / W1, / w2, / W3, / W4, / W1, / w2, / W3, / W4, /Wall, WD, / we Wo, wv, /WX (uyarı düzeyi)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **EnableEnhancedInstructionSet**  
  
   İsteğe bağlı dize parametresi.  
  
   Streaming SIMD Extensions 2 (SSE2) yönergeleri ve Akış SIMD Uzantıları'nı (SSE) kullanan kod oluşturma mimarisini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** -   **/arch: SSE2**  
  
    Daha fazla bilgi için [/arch (x86)](http://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **EnableFiberSafeOptimizations**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, statik iş parçacığı yerel depolama, diğer bir deyişle, veriler kullanılarak kullanılarak yer ayrılan veri için fiber güvenliğini destekler `__declspec(thread)`.  
  
   Daha fazla bilgi için [/GT (Fiber-güvenli iş parçacığı-yerel depolamayı destekle)](http://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, kod analizini etkinleştirir.  
  
   Daha fazla bilgi için [/ analyze (kod çözümleme)](http://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   İsteğe bağlı dize parametresi.  
  
   Derleyici iç hatası (ICE) bilgilerini doğrudan Microsoft'a sağlamanıza olanak tanır. Varsayılan olarak, IDE yapılarında ayardır **istemi** ve komut satırı derlemeleri ayarda **kuyruk**.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **None** - **/errorReport:none**  
  
  - **Prompt** - **/errorReport:prompt**  
  
  - **Queue** - **/errorReport:queue**  
  
  - **Send** - **/errorReport:send**  
  
    Daha fazla bilgi için [/errorreport (dahili derleme hatalarını raporla)](http://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   İsteğe bağlı dize parametresi.  
  
   Derleyici tarafından kullanılması için özel durum işleme modelini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **false** - *\<yok >*  
  
  - **Async** - **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Daha fazla bilgi için [/EH (özel durum işleme modeli)](http://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, genişletilmiş öznitelikleri kaynak dosyasına eklenen bir listeleme dosyası oluşturur.  
  
   Daha fazla bilgi için [/Fx (eklenen kodu Birleştir)](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   İsteğe bağlı dize parametresi.  
  
   Kod boyutu veya kod hızına ayrıcalık tanı belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Ne** - *\<yok >*  
  
  - **Boyutu** - **/Os**  
  
  - **Hızı** - **/Ot**  
  
    Daha fazla bilgi için [/Os, /Ot (küçük koda, ayrıcalık hızlı koda ayrıcalık tanı)](http://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, güvenilir kayan nokta özel durum modeli sağlar. Özel durumlar, tetiklendikten hemen sonra gerçekleştirilecektir.  
  
   Daha fazla bilgi için bkz. /**fp: except** seçeneğini [FP (Floating-Point davranışını belirtin)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **FloatingPointModel**  
  
   İsteğe bağlı dize parametresi.  
  
   Ayarlar kayan nokta modeli.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Precise** - **/fp:precise**  
  
  - **Katı** -   **/FP: strict**  
  
  - **Fast** - **/fp:fast**  
  
    Daha fazla bilgi için [FP (Floating-Point davranışını belirtin)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **ForceConformanceInForLoopScope**  
  
   İsteğe bağlı Boole parametresi.  
  
   Varsa `true`, standart C++ davranışını uygulayan [için](http://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) Microsoft uzantıları kullanma döngüler ([/Ze](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
   Daha fazla bilgi için [/ZC: forscope (zorla döngü kapsamında uyumluluğu)](http://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   İsteğe bağlı `String[]` parametresi.  
  
   Bir veya daha fazla belirtilen üstbilgi dosyalarını işlemek önişlemci neden olur.  
  
   Daha fazla bilgi için [/FI (zorla dahil dosyasını Adlandır)](http://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Önişlemci işlemine bir veya daha fazla belirtilen neden **#using** dosyaları.  
  
   Daha fazla bilgi için [/FU (zorlanan adı #using)](http://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **FunctionLevelLinking**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, bireysel işlevleri paketlenmiş işlevler (Comdat'lar) biçiminde derleyiciyi etkinleştirir.  
  
   Daha fazla bilgi için [/Gy (işlev düzeyi bağlamayı etkinleştir)](http://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, belgeleri işlemek için derleyicinin açıklamaları, kaynak kodu dosyaları ve her bir kaynak için bir .xdc dosyasını oluşturmak için kod dosyasını nedeni belge açıklamaları vardır.  
  
   Daha fazla bilgi için [/doc (işlem belgeleri açıklamaları) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Ayrıca bkz: **XMLDocumentationFileName** bu tablodaki parametresi.  
  
- **IgnoreStandardIncludePath**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, derleyici PATH ve INCLUDE Ortam değişkenlerinde belirtilen dizinlerde ekleme dosyalarını aramasını önler.  
  
   Daha fazla bilgi için [/X (Ignore Standard INCLUDE Paths)](http://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **InlineFunctionExpansion**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Derleme için satır içi işlev genişletmesi düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan** - *\<yok >*  
  
  - **Devre dışı bırakılmış** - **/Ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** -   **/ob2**  
  
    Daha fazla bilgi için [/Ob (satır içi işlev genişletmesi)](http://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **IntrinsicFunctions**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, değiştirir bazı işlev çağrıları ile iç veya aksi halde uygulamanızı yardımcı işlevinin özel formlar daha hızlı çalışır.  
  
   Daha fazla bilgi için [(iç işlevler Oluştur) /Oi](http://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **MinimalRebuild**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, değiştirilmiş C++ içeren C++ kaynak dosyaları (Üstbilgi (.h) dosyalarında depolanan) tanımları sınıf olup olmadığını belirler. en az yeniden derlemeyi yeniden sağlar.  
  
   Daha fazla bilgi için [/GM derlemeyi (etkinleştirme en az yeniden derlemeyi)](http://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
- **MultiProcessorCompilation**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, birden çok işlemci derlemek için kullanın. Bu parametre, bilgisayarınızda etkili her işlemci için bir işlem oluşturur.  
  
   Daha fazla bilgi için [/MP (birden çok süreçle derleme)](http://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Ayrıca bkz **ProcessorNumber** bu tablodaki parametresi.  
  
- **ObjectFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir nesne (.obj) dosya adı veya varsayılan yerine kullanılacak dizini belirtir.  
  
   Daha fazla bilgi için [/Fo (nesne dosya adı)](http://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Nesne dosyaların listesi.  
  
- **OmitDefaultLibName**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, nesne (.obj) dosyası varsayılan C çalışma zamanı kitaplığı adından atlar. Varsayılan olarak, derleyici doğru kitaplık bağlayıcıya yönlendirmek için .obj dosyasına kitaplığının adı geçirir.  
  
   Daha fazla bilgi için [/Zl (varsayılan kitaplık adını atla)](http://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **OmitFramePointers**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.  
  
   Daha fazla bilgi için [/Oy (Çerçeve işaretçisini atlama)](http://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, derleyicinin OpenMP yan tümceleri ve yönergeleri işlemek.  
  
   Daha fazla bilgi için [/OpenMP (OpenMP 2.0 desteğini etkinleştir)](http://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **En iyi duruma getirme**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Çeşitli kod iyileştirmeleri hız ve boyutunu belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Devre dışı bırakılmış** - **/Od**  
  
  - **MinSpace** -   **/O1**  
  
  - **MaxSpeed** -   **/O2**  
  
  - **Tam** - **/Ox**  
  
    Daha fazla bilgi için [/O seçenekler (kodu İyileştir)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Oluşturun veya derleme sırasında önceden derlenmiş üst bilgi (.pch) dosyasını kullanın.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **NotUsing** - *\<yok >*  
  
  - **Oluşturma** - **/Yc**  
  
  - **Kullanım** - **/Yu**  
  
    Daha fazla bilgi için [/Yc (önceden derlenmiş üst bilgi dosyası oluştur)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) ve [/Yu (önceden derlenmiş üst bilgi dosyasını kullanma)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Ayrıca bkz **PrecompiledHeaderFile** ve **PrecompiledHeaderOutputFile** bu tabloda parametreler.  
  
- **PrecompiledHeaderFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Oluşturmayı veya kullanmayı önceden derlenmiş üst bilgi dosyası adını belirtir.  
  
   Daha fazla bilgi için [/Yc (önceden derlenmiş üst bilgi dosyası oluştur)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) ve [/Yu (önceden derlenmiş üst bilgi dosyasını kullanma)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **PrecompiledHeaderOutputFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Varsayılan yol adı yerine önceden derlenmiş üst bilgi için bir yol adı belirtir.  
  
   Daha fazla bilgi için [FP (adı. PCH dosyası)](http://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, ön işleme sırasında yorumları korur.  
  
   Daha fazla bilgi için [/C (korumak açıklamaları sırasındaki)](http://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   İsteğe bağlı `String[]` parametresi.  
  
   Kaynak dosyanız için önceden işleme simgesini tanımlar.  
  
   Daha fazla bilgi için [/D (önişlemci tanımları)](http://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   İsteğe bağlı `ITaskItem[]` parametresi.  
  
   Tüketilen ve görevler tarafından yayılan önişlemci çıktısını öğeleri bir dizisi tanımlanmaktadır.  
  
- **PreprocessOutputPath**  
  
   İsteğe bağlı `String` parametresi.  
  
   Hangi çıkış dosyasının adını belirtir **PreprocessToFile** parametresi önceden işlenmiş çıktı yazar.  
  
   Daha fazla bilgi için [/Fi (çıktı dosyası adı Önişle)](http://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, C ve C++ kaynak dosyalarını önceden işler ve standart çıktı cihazına önceden işlenmiş dosya kopyalar.  
  
   Daha fazla bilgi için [/EP (#line yönergeleri olmadan stdout'ta önişle ön işleme)](http://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, C ve C++ kaynak dosyalarını önceden işler ve önceden işlenen çıkışı bir dosyaya yazar.  
  
   Daha fazla bilgi için [/P (dosyaya ön işleme)](http://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   İsteğe bağlı `Integer` parametresi.  
  
   Çok işlemcili bir derleme içinde kullanılacak işlemcileri maksimum sayısını belirtir. Bu parametre ile birlikte kullanma **MultiProcessorCompilation** parametresi.  
  
- **ProgramDataBaseFileName**  
  
   İsteğe bağlı `String` parametresi.  
  
   Program veritabanı (PDB) dosyası için bir dosya adı belirtir.  
  
   Daha fazla bilgi için [/Fd (Program veritabanı dosya adı)](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   İsteğe bağlı `String` parametresi.  
  
   Çok iş parçacıklı bir modülün bir DLL ve çalışma zamanı kitaplığının perakende veya hata ayıklama sürümlerini seçer olup olmadığını gösterir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Çok iş parçacıklı** -   **/MT**  
  
  - **MultiThreadedDebug** -   **/mtd**  
  
  - **MultiThreadedDLL** -   **/MD**  
  
  - **MultiThreadedDebugDLL** - **/MDd**  
  
    Daha fazla bilgi için [/MD, / MT, /LD (çalışma zamanı kitaplığını kullan)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, çalışma zamanında (çalışma zamanı tür bilgisi) C++ nesne türlerini denetlemek için kod ekler.  
  
   Daha fazla bilgi için [/GR (çalışma zamanı türü bilgileri etkinleştir)](http://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **Showıncludes**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, ekleme kodu dosyalarının bir listesini çıkarmak derleyicinin neden olur.  
  
   Daha fazla bilgi için [/showıncludes (liste dosyaları içerir)](http://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, bir değer daha küçük bir veri türüne atandı ve veri kaybına neden olan bir çalışma zamanı hatası bildirir.  
  
   Daha fazla bilgi için **/RTCc** seçeneğini [/RTC (çalışma zamanı hata denetimleri)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **Kaynakları**  
  
   Gerekli `ITaskItem[]` parametresi.  
  
   Kaynak dosyaları boşluklarla ayrılmış bir listesini belirtir.  
  
- **StringPooling**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, program görüntüde aynı dizelerin bir kopyasını oluşturmak derleyiciyi etkinleştirir.  
  
   Daha fazla bilgi için [/GF (yinelenen dizeleri ortadan)](http://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
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
  
    Daha fazla bilgi için [/Zp (yapı üyesi hizalama)](http://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.  
  
   Daha fazla bilgi için [/nologo (Başlangıç başlığını gösterme) (C/C++)](http://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **TrackerLogDirectory**  
  
   İsteğe bağlı `String` parametresi.  
  
   Bu görev için izleme günlüklerinin depolandığı Ara dizini belirtir.  
  
   Daha fazla bilgi için **TLogReadFiles** ve **TLogWriteFiles** bu tabloda parametreler.  
  
- **TreatSpecificWarningsAsErrors**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Belirtilen Derleyici uyarılarını hata olarak değerlendirir.  
  
   Daha fazla bilgi için **/we** `n` seçeneğini [/w, /W0, / W1, / w2, / W3, / W4, / W1, / w2, / W3, / W4, /Wall, WD, / we Wo, wv, /WX (uyarı düzeyi)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWarningAsError**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, tüm Derleyici uyarılarını hata olarak değerlendir.  
  
   Daha fazla bilgi için **wx** seçeneğini [/w, /W0, / W1, / w2, / W3, / W4, / W1, / w2, / W3, / W4, /Wall, WD, / we Wo, wv, /WX (uyarı düzeyi)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWChar_tAsBuiltInType**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, işle `wchar_t` türü olarak yerel bir tür.  
  
   Daha fazla bilgi için [/ZC: wchar_t (wchar_t yerel türü olduğu)](http://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, derleyici tanımlayan Microsoft'a özgü simgeleri tanımsızı.  
  
   Daha fazla bilgi için **/u** seçeneğini [/U, /u (simge tanımlarını Kaldır)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UndefinePreprocessorDefinitions**  
  
   İsteğe bağlı `String[]` parametresi.  
  
   Tanımsız için bir veya daha çok önişlemci sembolleri listesini belirtir.  
  
   Daha fazla bilgi için **/U** seçeneğini [/U, /u (simge tanımlarını Kaldır)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UseFullPaths**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, derleyici tanılama geçirilen kaynak kodu dosyalarının tam yolunu görüntüler.  
  
   Daha fazla bilgi için [/FC (tam yol, kaynak kodu dosyasında tanılama)](http://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **UseUnicodeForAssemblerListing**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, çıkış dosyasının UTF-8 biçiminde oluşturulmasını sağlar.  
  
   Daha fazla bilgi için **/fau** seçeneğini [/FA, /Fa (listeleme dosyası)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
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
  
    Daha fazla bilgi için **/W**_n_ seçeneğini [/w, /W0, / W1, / w2, / W3, / W4, / W1, / w2, / W3, / W4, /Wall, WD, / we Wo, wv, /WX (uyarı düzeyi)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **WholeProgramOptimization**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, tüm programın iyileştirilmesini etkinleştirir.  
  
   Daha fazla bilgi için [/GL (bütün Program iyileştirmesi)](http://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **XMLDocumentationFileName**  
  
   İsteğe bağlı `String` parametresi.  
  
   Oluşturulmuş XML belgesi dosyalarının adını belirtir. Bu parametre bir dosya veya dizin adı olabilir.  
  
   Daha fazla bilgi için `name` değişkeninde [/doc (işlem belgeleri açıklamaları) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Ayrıca bkz: **GenerateXMLDocumentationFiles** bu tablodaki parametresi.  
  
- **MinimalRebuildFromTracking**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, izlenen bir artımlı derleme; yapılmaz `false`, yeniden gerçekleştirilir.  
  
- **TLogReadFiles**  
  
   İsteğe bağlı `ITaskItem[]` parametresi.  
  
   Temsil eden öğelerin bir dizisi belirtir *günlükleri izleme dosyası okuma*.  
  
   Bir dosyayı oku izleme günlüğü (.tlog), bir görev tarafından okunur ve artımlı derlemeleri desteklemek için proje sistemi tarafından kullanılan giriş dosyalarının adlarını içerir. Daha fazla bilgi için **TrackerLogDirectory** ve **trackfileaccess değeri** bu tabloda parametreler.  
  
- **TLogWriteFiles**  
  
   İsteğe bağlı `ITaskItem[]` parametresi.  
  
   Temsil eden öğelerin bir dizisi belirtir *günlükleri izleme dosyası yazma*.  
  
   Yazma dosya izleme günlük (.tlog), bir görev tarafından yazılmış ve artımlı derlemeleri desteklemek için proje sistemi tarafından kullanılan çıkış dosyalarının adlarını içerir. Daha fazla bilgi için **TrackerLogDirectory** ve **trackfileaccess değeri** bu tabloda parametreler.  
  
- **TrackFileAccess**  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, dosya erişim düzenlerini izler.  
  
   Daha fazla bilgi için **TLogReadFiles** ve **TLogWriteFiles** bu tabloda parametreler.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



