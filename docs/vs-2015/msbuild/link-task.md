---
title: Bağlantı görevi | Microsoft Docs
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2ca9c721567d89bddad4a9ee61639bd3a82f10d
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143456"
---
# <a name="link-task"></a>Bağlantı Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ bağlayıcı aracı sarmalar link.exe. Bağlayıcı aracı ortak nesne dosyası biçimi (COFF) nesne dosyaları ve kitaplıkları bir yürütülebilir (.exe) dosyası oluşturmak için veya bir dinamik bağlantı kitaplığı (DLL) bağlar. Daha fazla bilgi için [bağlayıcı seçenekleri](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır **bağlantı** görev. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
- **AdditionalDependencies**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Giriş dosyaları için bir komut eklemek için bir listesini belirtir.  
  
   Daha fazla bilgi için [LINK giriş dosyaları](http://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **AdditionalLibraryDirectories**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Kullanıcının ortam kitaplık yolunu geçersiz kılar. Bir dizin adı belirtin.  
  
   Daha fazla bilgi için [/Libpath (ek Libpath)](http://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Yerleştirilecek öznitelikleri belirtir `dependency` bildirim dosyasının.  
  
   Daha fazla bilgi için [/MANIFESTDEPENDENCY (bildirim bağımlılıklarını belirtin)](http://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Ayrıca, üzerinde "Yayımcı yapılandırma dosyaları" bkz [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
- **AdditionalOptions**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Belirtilen komut satırında bağlayıcı seçenekleri listesi. Örneğin, **"**_/option1 /option2 /option#_". Diğer tarafından temsil edilmez bağlayıcı seçenekleri belirtmek için bu parametreyi kullanın **bağlantı** görev parametresi.  
  
   Daha fazla bilgi için [bağlayıcı seçenekleri](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Bir derlemeye bir modül başvurusu ekler.  
  
   Daha fazla bilgi için [assemblymodule (derlemeye MSIL Modülü Ekle)](http://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **Allowısolatıon**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, işletim sisteminin aramaları bildirim neden olur ve yükler. Varsa `false`, DLL'leri, hiçbir bildirim olduysa gibi yüklendiğini gösterir.  
  
   Daha fazla bilgi için [/ALLOWISOLATION (bildirim arama)](http://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, yayan **DebuggableAttribute** hata ayıklama bilgisi izleme ve devre dışı bırakır JIT iyileştirmelerini birlikte öznitelik. Varsa `false`, yayan **DebuggableAttribute** özniteliği ancak hata ayıklama bilgisi izlemeyi devre dışı bırakır ve JIT iyileştirmelerini sağlar.  
  
   Daha fazla bilgi için [assemblydebug (DebuggableAttribute ekleme)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **Assemblylınkresource**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Çıkış dosyasında .NET Framework kaynağına bağlantı oluşturur. kaynak dosyası çıkış dosyasına yerleştirilmez. Kaynağın adını belirtin.  
  
   Daha fazla bilgi için [/assemblylınkresource (.NET Framework kaynağına bağlantı)](http://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Örtük **Boole** parametresi.  
  
   Daha ayrıntılı dosya bağlantı artımlı bir kullanıcının davranışını yakalamak için izleme sağlar. Her zaman döndürür `true`.  
  
- **BaseAddress**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Program veya oluşturulmakta DLL temel adres ayarlar. Belirtin `{address[,size] | @filename,key}`.  
  
   Daha fazla bilgi için [/Base (Temel adres)](http://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **BuildingInIDE**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   TRUE ise, MSBuild IDE'den çağrılan gösterir. Aksi takdirde, MSBuild komut satırından çağrılır gösterir.  
  
   Bu parametre, denk bağlayıcı seçeneği vardır.  
  
- **CLRImageType**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir ortak dil çalışma zamanı (CLR) görüntü türünü ayarlar.  
  
   Her biri için bir bağlayıcı seçeneği karşılık gelen şu değerlerden birini belirtin.  
  
  - **Varsayılan** - *\<yok >*  
  
  - **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
  - **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
  - **ForceSafeILImage** - **kullanılır**  
  
    Daha fazla bilgi için [/CLRIMAGETYPE (CLR, türü görüntü belirtin)](http://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **Clrsupportlasterror'ü**  
  
   İsteğe bağlı **dize** parametresi.  
  
   P/Invoke mekanizmasıyla çağrılan işlevlerin son hata kodunu korur.  
  
   Her biri için bir bağlayıcı seçeneği karşılık gelen şu değerlerden birini belirtin.  
  
  - **Etkin** - **/CLRSupportLastError**  
  
  - **Devre dışı bırakılmış** - **/CLRSupportLastError:NO**  
  
  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    Daha fazla bilgi için [/CLRSUPPORTLASTERROR (korumak için son hata kodunu PInvoke çağrıları)](http://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **Clrthreadattrıbute**  
  
   İsteğe bağlı **dize** parametresi.  
  
   CLR programınızın giriş noktası için iş parçacığı oluşturma özniteliğini açıkça belirtir.  
  
   Her biri için bir bağlayıcı seçeneği karşılık gelen şu değerlerden birini belirtin.  
  
  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE: yok**  
  
  - **MTAThreadingAttribute** - **MTA**  
  
  - **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    Daha fazla bilgi için [/CLRTHREADATTRIBUTE (CLR iş parçacığı özniteliğini Ayarla)](http://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Bağlayıcı uygulayıp uygulamayacağını belirtir **SuppressUnmanagedCodeSecurityAttribute** bağlayıcı tarafından oluşturulan P/Invoke çağırıyor yönetilen koddan yerel DLL'lere için.  
  
   Daha fazla bilgi için [/clrunmanagedcodecheck (SuppressUnmanagedCodeSecurityAttribute Ekle)](http://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **CreateHotPatchableImage**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Görüntüyü Yeniden başlatmasız düzeltme için hazırlar.  
  
   Bir bağlayıcı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Etkin** - **/FUNCTIONPADMIN**  
  
  - **X86Image** - **/FUNCTIONPADMIN:5**  
  
  - **X64Image** - **/FUNCTIONPADMIN:6**  
  
  - **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    Daha fazla bilgi için [/FUNCTIONPADMIN (düzeltme eki eklenebilen görüntü oluşturma)](http://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **DataExecutionPrevention**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, yürütülebilir bir dosya Windows Veri Yürütme Engellemesi özelliği ile uyumlu olduğunun saptandığını gösterir.  
  
   Daha fazla bilgi için [/NXCOMPAT (veri yürütme önlemesi ile uyumlu)](http://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Bu parametre neden *Gecikmeli yükleme* dll. Bir DLL gecikme yükü adını belirtin.  
  
   Daha fazla bilgi için [/delayload (gecikme yükü içe)](http://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, bir derlemeyi kısmen imzalar. Varsayılan değer olan `false`.  
  
   Daha fazla bilgi için [/delaysign (bir derlemeyi kısmen imzalayın)](http://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Sürücü**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir Windows NT Çekirdek modu sürücüsü oluşturmak için bu parametreyi belirtin.  
  
   Her biri için bir bağlayıcı seçeneği karşılık gelen şu değerlerden birini belirtin.  
  
  - **NotSet** - *\<yok >*  
  
  - **Sürücü** - **Driver/Driver**  
  
  - **UpOnly** - **/DRIVER:UPONLY**  
  
  - **WDM** -   **/DRIVER: WDM**  
  
    Daha fazla bilgi için [(Windows NT Çekirdek modu sürücüsü) Driver/Driver](http://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Bir derlemeye kaynak dosyası gömer. Gerekli kaynak dosya adı belirtin. İsteğe bağlı olarak kaynak yüklemek için kullanılan mantıksal adı belirtin ve **özel** seçeneği, bütünleştirilmiş kod bildirimi kaynak dosyası özel olduğunu belirtir.  
  
   Daha fazla bilgi için [koduna konmaz (yönetilen kaynağı katıştır)](http://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **EnableCOMDATFolding**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, eşdeğer COMDAT katlaması sağlar.  
  
   Daha fazla bilgi için `ICF[= iterations]` bağımsız değişkeni [OPT (iyileştirmeler)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **EnableUAC**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, kullanıcı hesabı denetimi (UAC) bilgisinin program bildiriminde gömülü olup olmadığını belirtir.  
  
   Daha fazla bilgi için [/MANIFESTUAC (bildirimdeki UAC bilgilerini katıştırır)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir .exe dosyası veya DLL için başlangıç adresi olarak giriş noktası işlevini belirtir. Bir işlev adı parametre değeri olarak belirtin.  
  
   Daha fazla bilgi için [/Entry (giriş noktası simgesi)](http://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, yalnızca tercih edilen temel adresini bir program veya yüklenmesi gereken DLL oluşturur.  
  
   Daha fazla bilgi için [/FIXED (sabit temel adres)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Geçerli bir .exe dosyası oluşturmak için söyler veya DLL sembole başvurulduğunda ancak bile tanımlanan, veya tanımlı çarpın.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Etkin** -   **/FORCE**  
  
  - **MultiplyDefinedSymbolOnly** -   **/Force: multıple**  
  
  - **UndefinedSymbolOnly** -   **/FORCE: KARARSIZ**  
  
    Daha fazla bilgi için [/Force (dosya çıktısını zorla)](http://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **ForceSymbolReferences**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Bu parametre, belirtilen sembolü sembol tablosuna eklemek için söyler.  
  
   Daha fazla bilgi için [/Include (simge başvurularını zorla)](http://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bu parametre imajın içine önceden belirlenmiş bir sırada belirtilen paketlenmiş işlevler (Comdat'lar) koyarak programınızı iyileştirir.  
  
   Daha fazla bilgi için [/order (Put işlevleri Sırala)](http://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, .exe dosyası veya DLL için hata ayıklama bilgileri oluşturur.  
  
   Daha fazla bilgi için [/Debug (hata ayıklama bilgisi Oluştur)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, yan yana bildirim dosyası oluşturur.  
  
   Daha fazla bilgi için [/MANIFEST (oluşturma yan yana derleme bildirimi)](http://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, oluşturur bir *Haritası*. Dosya adı uzantısı, eşleme dosyası .map ' dir.  
  
   Daha fazla bilgi için [Map (eşlem dosyası oluştur)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Aynı anda ayrılacak yığında fiziksel bellek miktarını belirtir.  
  
   Daha fazla bilgi için `commit` değişkeninde [/HEAP (öbek boyutunu Ayarla)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Ayrıca bkz **HeapReserveSize** parametresi.  
  
- **HeapReserveSize**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Sanal bellekte toplam yığın ayırma belirtir.  
  
   Daha fazla bilgi için `reserve` değişkeninde [/HEAP (öbek boyutunu Ayarla)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Ayrıca bkz **HeapCommitSize** bu tablodaki parametresi.  
  
- **IgnoreAllDefaultLibraries**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, söyler kaldırın ya da daha fazla varsayılan kitaplık kitaplıkları listesinden bunu ne zaman arar dış başvuruları çözümleniyor.  
  
   Daha fazla bilgi için [/nodefaultlıb (kitaplıkları yoksay)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, IDL öznitelikleri kaynak kodundaki .idl dosyasına işlenmemesi gerektiğini belirtir.  
  
   Daha fazla bilgi için [/ıgnoreıdl (yoksa işlem öznitelikler MIDL)](http://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, bu yapılandırmanın oluşturduğu içeri aktarma kitaplığının bağımlı projelere aktarılmaması gerektiğini belirtir.  
  
   Bu parametre için bir bağlayıcı seçeneği karşılık gelmiyor.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   İsteğe bağlı **String []** parametresi.  
  
   Bir veya daha fazla varsayılan kitaplık adlarını belirtir. Birden çok kitaplık noktalı virgül kullanarak ayırın.  
  
   Daha fazla bilgi için [/nodefaultlıb (kitaplıkları yoksay)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **ImageHasSafeExceptionHandlers**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, yalnızca görüntünün güvenli özel durum işleyicileri tablosu da üretebileceği, bağlayıcı bir görüntü üretiyor.  
  
   Daha fazla bilgi için [SAFESEH (görüntüde güvenli özel durum işleyicileri var)](http://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Varsayılan kitaplık adını değiştirir bir kullanıcı tarafından belirtilen içeri aktarma kitaplığı adı.  
  
   Daha fazla bilgi için [/IMPLIB (içeri aktarma kitaplığını Adlandır)](http://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   İsteğe bağlı **dize** parametresi.  
  
   İmzalı bir derleme için anahtarı içeren kapsayıcı.  
  
   Daha fazla bilgi için [/keycontainer (derlemeyi imzalamak için bir anahtar kapsayıcısı belirtin)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Ayrıca bkz **KeyFile** bu tablodaki parametresi.  
  
- **KeyFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   İmzalı bir derleme için anahtarı içeren dosyayı belirtir.  
  
   Daha fazla bilgi için [/keyfile (derlemeyi imzalamak için anahtar belirtin veya anahtar çiftini)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Ayrıca bkz **KeyContainer** parametresi.  
  
- **LargeAddressAware**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, uygulama 2 gigabayt'tan daha büyük adresleri işleyebilir.  
  
   Daha fazla bilgi için [/largeaddressaware (büyük adresleri işlemek)](http://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, DLL olarak ana çıkış dosyası oluşturur.  
  
   Daha fazla bilgi için [/dll (DLL derleme)](http://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Derleyici iç hatası (ICE) bilgilerini doğrudan Microsoft'a sağlamanıza olanak tanır.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **NoErrorReport** -   **/errorreport: yok**  
  
  - **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** - **okunmalı**  
  
    Daha fazla bilgi için [/errorreport (dahili bağlayıcı hatalarını raporla)](http://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **LinkIncremental**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, artımlı bağlamayı etkinleştirir.  
  
   Daha fazla bilgi için [/Incremental (artımlı bağlantı)](http://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, proje bağımlılıklarının kitaplık çıkışları içinde otomatik olarak bağlandığını belirtir.  
  
   Bu parametre için bir bağlayıcı seçeneği karşılık gelmiyor.  
  
- **LinkStatus**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, bağlayıcı bağlantıyı yüzde tamamlandıktan gösteren bir İlerleme göstergesi görüntülemesi gerektiğini belirtir.  
  
   Daha fazla bilgi için `STATUS` bağımsız değişkeni [/LTCG (bağlama zamanı kodu oluşturma)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **LinkTimeCodeGeneration**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Profil temelli İyileştirme seçeneklerini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan** - *\<yok >*  
  
  - **UseLinkTimeCodeGeneration** - **/LTCG**  
  
  - **PGInstrument** - **/LTCG:PGInstrument**  
  
  - **PGOptimization** - **/LTCG:PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG:PGUpdate**  
  
    Daha fazla bilgi için [/LTCG (bağlama zamanı kodu oluşturma)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **Manıfestfıle**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Varsayılan bildirim dosyası adı için belirtilen dosya adını değiştirir.  
  
   Daha fazla bilgi için [/MANIFESTFILE (bildirim dosyasını Adlandır)](http://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **MapExports**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, eşleme dosyasında dışarı aktarılan işlevleri dahil etmesini bağlayıcıya bildirir.  
  
   Daha fazla bilgi için `EXPORTS` bağımsız değişkeni [mapınfo (eşlem dosyası bilgileri dahil)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Belirtilen dosya adı için varsayılan eşleme dosyası adını değiştirir.  
  
- **MergedIDLBaseFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   .İdl dosyasının dosya adı uzantısı ve dosya adını belirtir.  
  
   Daha fazla bilgi için [/ıdlout (MIDL çıktı dosyalarının adını)](http://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir görüntü olarak bölümlerde birleştirir. Belirtin `from-section=to-section`.  
  
   Daha fazla bilgi için [/Merge (bölümleri Birleştir)](http://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **MidlCommandFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   MIDL komut satırı seçeneklerini içeren dosyanın adını belirtin.  
  
   Daha fazla bilgi için [/MIDL (MIDL komut satırı seçeneklerini belirtin)](http://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Alt sistemin gerekli en düşük sürümü belirtir. Bağımsız değişkenler, 0 ila 65.535 aralığındaki ondalık sayılardır.  
  
- **ModuleDefinitionFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Adını belirten bir [modül tanım dosyası](http://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
   Daha fazla bilgi için [/def (modül tanım dosyası belirtin)](http://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Belirtilen MS-DOS saplama programını Win32 programına iliştirir.  
  
   Daha fazla bilgi için [/stub (MS-DOS saplama dosyası adı)](http://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, yalnızca kaynak DLL yüklemesini belirtir.  
  
   Daha fazla bilgi için [/NOENTRY (giriş noktası yok)](http://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Örtük **String []** parametresi.  
  
   Bağlantılı nesne dosyaları belirtir.  
  
- **OptimizeReferences**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, işlevleri ve/veya hiçbir zaman başvurulmayan verileri ortadan kaldırır.  
  
   Daha fazla bilgi için `REF` değişkeninde [OPT (iyileştirmeler)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **OutputFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Varsayılan adı ve bağlayıcının oluşturduğu program konumunu geçersiz kılar.  
  
   Daha fazla bilgi için [/OUT (çıktı dosyası adı)](http://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true` ve çıkışı kayda etkin zorlar kayıt için Yazar **HKEY_CLASSES_ROOT** için yönlendirilmesi **HKEY_CURRENT_USER**.  
  
- **PreprocessOutput**  
  
   İsteğe bağlı `ITaskItem[]` parametresi.  
  
   Tüketilen ve görevler tarafından yayılan önişlemci çıktısını öğeleri bir dizisi tanımlanmaktadır.  
  
- **PreventDllBinding**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, Bind.exe'yi bağlantılı görüntü bağlı gösterir.  
  
   Daha fazla bilgi için [/ALLOWBIND (DLL bağlamayı önleme)](http://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Profili**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, kullanılabilir bir çıktı dosyası üretir **performans araçları** profil oluşturucu.  
  
   Daha fazla bilgi için [PROFILE (performans araçları Profiler)](http://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **ProfileGuidedDatabase**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Çalışan programa hakkındaki bilgileri tutmak için kullanılan bir .pgd dosyası adını belirtir  
  
   Daha fazla bilgi için [/PGD (permutasyonları iyileştirmeler için veritabanını belirtin)](http://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
- **ProgramDatabaseFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bağlayıcının oluşturduğu program veritabanı (PDB) için bir ad belirtir.  
  
   Daha fazla bilgi için [/pdb (Program veritabanını kullan)](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, rastgele yükleme zamanında temellendirilebilen bir yürütülebilir görüntü oluşturur *adres boşluğu düzeni rastgele seçimini* Windows (ASLR) özelliği.  
  
   Daha fazla bilgi için [dynamıcbase (adres boşluğu düzeni rastgele'seçimini kullan)](http://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, bu derlemenin birincil çıkışının kaydeder.  
  
- **SectionAlignment**  
  
   İsteğe bağlı **tamsayı** parametresi.  
  
   Programın doğrusal adres alanındaki her bölümün hizalamasını belirtir. Parametre değeri bayt birim sayısı ve ikinin üssü.  
  
   Daha fazla bilgi için [/ALIGN (bölüm hizalama)](http://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **SetChecksum**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, bir .exe dosyası üst bilgisinde sağlama toplamını ayarlar.  
  
   Daha fazla bilgi için [/Release (sağlama toplamını Ayarla)](http://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **ShowProgress**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bağlama işlemi için ilerleme raporları, ayrıntı düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **NotSet** - *\<yok >*  
  
  - **LinkVerbose** - **/VERBOSE**  
  
  - **LinkVerboseLib** - **/VERBOSE:Lib**  
  
  - **LinkVerboseICF** - **/VERBOSE:ICF**  
  
  - **LinkVerboseREF** - **/VERBOSE:REF**  
  
  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
  - **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    Daha fazla bilgi için [/verbose (ilerleme iletilerini Yazdır)](http://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Kaynakları**  
  
   Gerekli `ITaskItem[]` parametresi.  
  
   Tüketilen ve görevler tarafından yayılan MSBuild kaynak dosya öğeleri bir dizisi tanımlanmaktadır.  
  
- **SpecifySectionAttributes**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir bölümün özniteliklerini belirtir. Bu bölüm için .obj dosyası derlendiğinde ayarlanan öznitelikleri geçersiz kılar.  
  
   Daha fazla bilgi için [/SECTION (bölüm özniteliklerini belirtin)](http://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Ek bellek tahsis edildiğinde her ayırma fiziksel bellek miktarını belirtir.  
  
   Daha fazla bilgi için `commit` bağımsız değişkeni [/STACK (yığın ayırmaları)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StackReserveSize**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Sanal bellekte toplam yığın ayırma boyutunu belirtir.  
  
   Daha fazla bilgi için `reserve` bağımsız değişkeni [/STACK (yığın ayırmaları)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StripPrivateSymbols**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Dağıtmak için müşterilerinize istemediğiniz sembolleri atar ikinci bir program veritabanı (PDB) dosyası oluşturur. İkinci PDB dosyasının adını belirtin.  
  
   Daha fazla bilgi için [/pdbstrıpped (özel simgeleri)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **Alt sistem**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Yürütülebilir dosya için ortamı belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **NotSet** - *\<yok >*  
  
  - **Konsol** -   **/Subsystem: Console**  
  
  - **Windows** - **/SUBSYSTEM:WINDOWS**  
  
  - **Yerel** - **natıve**  
  
  - **EFI uygulaması** - **/SUBSYSTEM:EFI_APPLICATION**  
  
  - **EFI Önyükleme servisi sürücüsü** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
  - **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
  - **EFI çalışma zamanı** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **Wındowsce** - **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Daha fazla bilgi için [/Subsystem (alt sistemi belirtin)](http://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, bağlanabilir bir içeri aktarma adres tablosu (IAT) son görüntüde eklememesini söyler.  
  
   Daha fazla bilgi için `NOBIND` bağımsız değişkeni [/delay (gecikme yükü içe aktarma ayarları)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, açık DLL'i kaldırma desteklemek için gecikme yük yardımcı işlevinizi söyler.  
  
   Daha fazla bilgi için `UNLOAD` bağımsız değişkeni [/delay (gecikme yükü içe aktarma ayarları)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SuppressStartupBanner**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.  
  
   Daha fazla bilgi için [/nologo (Başlangıç başlığını gösterme) (Bağlayıcı)](http://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, işletim sisteminin önce bağlayıcı çıktısını takas dosyasına kopyalama bildirir ve ardından görüntüyü oradan çalıştırın.  
  
   Daha fazla bilgi için `CD` bağımsız değişkeni [swaprun (Bağlayıcı çıktısını takas dosyası yükle)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Ayrıca bkz **SwapRunFromNET** parametresi.  
  
- **SwapRunFromNET**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, işletim sisteminin önce bağlayıcı çıktısını takas dosyasına kopyalama bildirir ve ardından görüntüyü oradan çalıştırın.  
  
   Daha fazla bilgi için `NET` bağımsız değişkeni [swaprun (Bağlayıcı çıktısını takas dosyası yükle)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Ayrıca bkz **SwapRunFromCD** bu tablodaki parametresi.  
  
- **TargetMachine**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Program veya DLL için hedef platformu belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **NotSet** - *\<yok >*  
  
  - **MachineARM** - **/MACHINE:ARM**  
  
  - **MachineEBC** - **/MACHINE:EBC**  
  
  - **MachineIA64** - **/MACHINE:IA64**  
  
  - **MachineMIPS** - **/MACHINE:MIPS**  
  
  - **MachineMIPS16** - **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
  - **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
  - **MachineSH4** - **/MACHINE:SH4**  
  
  - **MachineTHUMB** - **/MACHINE:THUMB**  
  
  - **MachineX64** - **/MACHINE:X 64**  
  
  - **MachineX86** - **/MACHINE:X 86**  
  
    Daha fazla bilgi için [/Machine (hedef Platform belirtin)](http://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, program görüntüsünün isteğe bağlı üst bilgisindeki ımage_optıonal_header DllCharacteristics alanında bir bayrak ayarlar. Bu bayrak ayarlandığında Terminal sunucusu uygulamada bazı değişiklikler yapmaz.  
  
   Daha fazla bilgi için [/TSAWARE (Terminal sunucusu kullanan uygulama oluştur)](http://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **TrackerLogDirectory**  
  
   İsteğe bağlı **dize** parametresi.  
  
   İzleyici günlüğü dizini belirtir.  
  
- **TreatLinkerWarningAsErrors**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, bağlayıcı bir uyarı oluşturduğunda çıkış dosyası oluşturulmamasını sağlar.  
  
   Daha fazla bilgi için [/WX (Bağlayıcı uyarıları hata olarak değerlendir)](http://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, bir .NET Framework derlemesinin olmadan geçerli çıkış dosyası için bir görüntü oluşturur.  
  
   Daha fazla bilgi için [noassembly (MSIL modülü Oluştur)](http://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   .Tlb dosyasının dosya adı uzantısı ve dosya adını belirtir. Bir dosya adı veya yolu ve dosya adı belirtin.  
  
   Daha fazla bilgi için  [ /tlbout (adı. TLB dosyası)](http://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   İsteğe bağlı **tamsayı** parametresi.  
  
   Bağlayıcı tarafından oluşturulan tür kitaplığı için bir kullanıcı tarafından belirtilen değeri atar. 1 ile 65535 arasında bir değer belirtin.  
  
   Daha fazla bilgi için [/TLBID (kaynak kimliği belirt TypeLib için)](http://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **UACExecutionLevel**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Altında kullanıcı hesabı denetimi ile çalışırken, uygulama için istenen yürütme düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator'a** - `level='requireAdministrator'`  
  
    Daha fazla bilgi için `level` bağımsız değişkeni [/MANIFESTUAC (bildirimdeki UAC bilgilerini katıştırır)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UACUIAccess**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`, uygulama kullanıcı arabirimi koruma düzeylerinin atlar ve sürücüleri giriş izni yüksek windows masaüstü için; Aksi takdirde `false`.  
  
   Daha fazla bilgi için `uiAccess` bağımsız değişkeni [/MANIFESTUAC (bildirimdeki UAC bilgilerini katıştırır)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UseLibraryDependencyInputs**  
  
   İsteğe bağlı **Boole** parametresi.  
  
   Varsa `true`kitaplıkçı aracının kullanılan yerine, kitaplık dosyasının kendisi proje bağımlılıklarının kitaplık çıkışları olduğunda bağlanır.  
  
- **Sürüm**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir sürüm numarası, .exe veya .dll dosyasının başlığına yerleştirin. Belirtin "`major[.minor]`". `major` Ve `minor` bağımsız değişkenler 0 ile 65535 arasında ondalık sayı.  
  
   Daha fazla bilgi için [/VERSION (sürüm bilgileri)](http://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



