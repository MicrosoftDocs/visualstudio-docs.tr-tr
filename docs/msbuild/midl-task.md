---
title: MIDL görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), MIDL task
- MIDL task (MSBuild (Visual C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1affc4d84b8ea44cbaed51f656c8a3e97e04f97a
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219815"
---
# <a name="midl-task"></a>MIDL görevi
Microsoft arabirim tanımı dili (MIDL) derleyici aracı sarmalar *midl.exe'yi*. Daha fazla bilgi için [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki parametreleri açıklar **MIDL** görev. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
-   **AdditionalIncludeDirectories**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bir dizin, içeri aktarılan IDL dosyaları, dahil edilen üst bilgi dosyaları ve uygulama yapılandırma dosyaları (ACF) için Aranan dizinleri listesine ekler.  
  
     Daha fazla bilgi için **/I** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **AdditionalOptions**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Komut satırı seçeneklerinin listesi. Örneğin, /\<Seçenek1 > /\<Seçenek2 > /\<seçeneği #>. Herhangi diğer MIDL görev parametresi tarafından temsil edilmez komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.  
  
     Daha fazla bilgi için [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ApplicationConfigurationMode**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bazı ACF anahtar sözcükleri IDL dosyasında kullanmanıza olanak sağlar.  
  
     Daha fazla bilgi için **/app_config** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ClientStubFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     RPC arabirimi için istemci saplama dosyası adını belirtir.  
  
     Daha fazla bilgi için **/cstub** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Ayrıca bkz: **ServerStubFile** bu tablodaki parametresi.  
  
-   **CPreprocessOptions**  
  
     İsteğe bağlı **dize** parametresi.  
  
     C/C++ önişlemci geçirilecek seçeneklerini belirtir. Önişlemci seçenekleri boşlukla ayrılmış bir listesini belirtin.  
  
     Daha fazla bilgi için **/cpp_opt** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **DefaultCharType**  
  
     İsteğe bağlı **dize** parametresi.  
  
     C derleyicisinin oluşturulmuş kodu derlemek için kullanacağı varsayılan karakter türünü belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**İmzalı**|**/char imzalı**|  
    |**İşaretsiz**|**/char işaretsiz**|  
    |**Ascii**|**/char ascii7**|  
  
     Daha fazla bilgi için **/char** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **DllDataFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Oluşturulan dosya adını belirtir *dlldata* bir ara sunucu DLL dosyası.  
  
     Daha fazla bilgi için **/dlldata** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **EnableErrorChecks**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Çalışma zamanında oluşturulan saptamalar gerçekleştireceğini denetlemede hata türünü belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**Yok**|**/ Error none**|  
    |**EnableCustom**|**/ Error**|  
    |**Tüm**|**/ Error tüm**|  
  
     Daha fazla bilgi için **/Error** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ErrorCheckAllocations**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bellek yetersiz hataları kontrol edin.  
  
     Daha fazla bilgi için **/Error ayırma** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ErrorCheckBounds**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`uyumluluğunu değişen boyutunu denetler ve iletim uzunluğu belirtimlerinin karşı diziler Çeşitleme uygulanıyor.  
  
     Daha fazla bilgi için **/Error bounds_check** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ErrorCheckEnumRange**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, sabit listesi değerlerinin bir izin verilen aralıkta olup olmadığını kontrol eder.  
  
     Daha fazla bilgi için **/Error enum** komut satırı Yardımı seçeneğinde (**/?**) için *midl.exe'yi*.  
  
-   **ErrorCheckRefPointers**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, hiçbir null başvuru işaretçilerini istemci saptamalar için geçirilen olup olmadığını kontrol edin.  
  
     Daha fazla bilgi için **/Error ref** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ErrorCheckStubData**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, sunucu tarafında unmarshaling özel durumlarını yakalayan ve bunları istemciye yayan bir saplama oluşturur.  
  
     Daha fazla bilgi için **/Error stub_data** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **GenerateClientFiles**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Derleyici bir RPC arabirimi için istemci tarafı C kaynak dosyaları oluşturup oluşturmayacağını belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**Yok**|**/ Client yok**|  
    |**Stub**|**/ Client saptama**|  
  
     Daha fazla bilgi için **/Client** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **GenerateServerFiles**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Derleyici bir RPC arabirimi için sunucu tarafı C kaynak dosyaları oluşturup oluşturmayacağını belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**Yok**|**/ Server yok**|  
    |**Stub**|**/ Server saptama**|  
  
     Daha fazla bilgi için **/Server** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **GenerateStublessProxies**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, tam olarak yorumlanan saplamalar birlikte nesne arabirimleri için saplamasız proxy'ler oluşturur.  
  
     Daha fazla bilgi için **/oicf** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **GenerateTypeLibrary**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bir tür kitaplığı (*.tlb*) dosyası oluşturulmuyor.  
  
     Daha fazla bilgi için **/notlb** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **HeaderFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Oluşturulan üst bilgi dosyasının adını belirtir.  
  
     Daha fazla bilgi için **/h** veya **/header** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **IgnoreStandardIncludePath**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, MIDL görevi kullanılarak belirtilen dizinleri arar **Additionalıncludedirectories** geçin ve geçerli dizinde ve INCLUDE ortam değişkeni tarafından belirtilen dizinlerini yoksayar.  
  
     Daha fazla bilgi için **/no_def_idir** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **InterfaceIdentifierFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Adını belirtir *arabirim tanımlayıcı dosyasının* bir COM arabirimi. Bu işlem için IDL dosyası adı "_i.c" ekleyerek alınan varsayılan adını geçersiz kılar.  
  
     Daha fazla bilgi için **/iid** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **LocaleID**  
  
     İsteğe bağlı **int** parametresi.  
  
     Belirtir *yerel ayar tanımlayıcısı* , giriş dosyaları, dosya adları ve dizin yolları uluslararası karakterlerin kullanılmasına olanak tanır. Bir ondalık yerel ayar kimliği belirtin.  
  
     Daha fazla bilgi için **/lcid** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Ayrıca bkz: [yerel ayar tanımlayıcılarını](https://docs.microsoft.com/windows/desktop/intl/locale-identifiers).  
  
-   **MkTypLibCompatible**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, uyumlu olması için giriş dosyasının biçimi gerektirir *mktyplib.exe* 2.03 sürümü.  
  
     Daha fazla bilgi için **/mktyplib203** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Ayrıca bkz [ODL FILE söz dizimiyle](/previous-versions/windows/desktop/automat/odl-file-syntax) MSDN Web sitesinde.  
  
-   **OutputDirectory**  
  
     İsteğe bağlı **dize** parametresi.  
  
     MIDL görevi Çıkış dosyalarını nereye yazdığını varsayılan dizini belirtir.  
  
     Daha fazla bilgi için **/out** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **PreprocessorDefinitions**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bir veya daha fazla belirtir *tanımlar*; diğer bir deyişle, bir ad ve isteğe bağlı bir değer C önişlemcisi geçirilecek IF bir `#define` yönergesi. Her tanımla biçimindedir, *[= değer] adı*.  
  
     Daha fazla bilgi için **/D** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Ayrıca bkz **UndefinePreprocessorDefinitions** bu tablodaki parametresi.  
  
-   **ProxyFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bir COM arabirimi arabirimi proxy dosyasının adını belirtir.  
  
     Daha fazla bilgi için **/proxy** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **RedirectOutputAndErrors**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Çıkış, hata iletileri ve uyarılar, belirtilen dosyaya standart çıktısından gibi yeniden yönlendirir.  
  
     Daha fazla bilgi için **/o** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ServerStubFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     RPC arabirimi için sunucu saplama dosyası adını belirtir.  
  
     Daha fazla bilgi için **/sstub** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Ayrıca bkz **ClientStubFile** bu tablodaki parametresi.  
  
-   **Kaynak**  
  
     Gerekli `ITaskItem[]` parametresi.  
  
     Kaynak dosyaları boşluklarla ayrılmış bir listesini belirtir.  
  
-   **StructMemberAlignment**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Hizalamayı belirtir (*düzeyi paketleme*) yapılarının hedef sistemde.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**NotSet**|*\<yok >*|  
    |**1**|**/Zp1**|  
    |**2**|**/Zp2**|  
    |**4**|**/Zp4**|  
    |**8**|**/Zp8**|  
  
     Daha fazla bilgi için **/ZP** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). **/ZP** seçenektir eşdeğer **/paketi** seçeneği ve eski **/ hizalama** seçeneği.  
  
-   **SuppressCompilerWarnings**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, MIDL görevi uyarı ilerileri bastırır.  
  
     Daha fazla bilgi için **/no_warn** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **SuppressStartupBanner**  
  
     İsteğe bağlı `Boolean` parametresi.  
  
     Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.  
  
     Daha fazla bilgi için **/nologo** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **TargetEnvironment**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Uygulamanın çalıştığı ortamı belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**NotSet**|*\<yok >*|  
    |**Win32**|**/ env win32**|  
    |**Itanium**|**/ env ia64**|  
    |**X64**|**/env x64**|  
  
     Daha fazla bilgi için **/env** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **TrackerLogDirectory**  
  
     İsteğe bağlı `String` parametresi.  
  
     Bu görev için izleme günlüklerinin depolandığı Ara dizini belirtir.  
  
-   **TypeLibFormat**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Tür kitaplığı dosyası biçimini belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Daha fazla bilgi için **/newtlb** ve **/oldtlb** seçeneklerini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **TypeLibraryName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Tür kitaplığı dosyasının adını belirtir.  
  
     Daha fazla bilgi için **/TLB** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **UndefinePreprocessorDefinitions**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Önceki herhangi bir ad tanımı adı C önişlemcisi iletilmesiyle kaldırır. Eğer tarafından bir `#undefine` yönergesi. Bir veya daha fazla önceden tanımlanmış adlarını belirtin.  
  
     Daha fazla bilgi için **/U** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Ayrıca bkz **PreprocessorDefinitions** bu tablodaki parametresi.  
  
-   **ValidateAllParameters**  
  
     İsteğe bağlı `Boolean` parametresi.  
  
     Varsa `true`, çalışma zamanında bütünlük denetimi gerçekleştirmek için kullanılan ek hata denetimi bilgileri oluşturur. Varsa `false`, hata denetimi bilgilerin oluşturulmuyor.  
  
     Daha fazla bilgi için **/ robust** ve **/no_robust** seçeneklerini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **WarnAsError**  
  
     İsteğe bağlı `Boolean` parametresi.  
  
     Varsa `true`, tüm uyarıları hata olarak değerlendirir.  
  
     Varsa **WarningLevel** MIDL görev parametresi belirtilmezse, varsayılan düzeyinde düzey 1 uyarı hata olarak kabul edilir.  
  
     Daha fazla bilgi için **wx** seçeneklerini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Ayrıca bkz **WarningLevel** bu tablodaki parametresi.  
  
-   **WarningLevel**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Önem derecesini belirtir (*uyarı düzeyi*) yaymak için uyarıları. Herhangi bir uyarı için 0 değerini yayılır. Uyarı düzeyiyle sayısal ise bir uyarı Aksi takdirde, yayılan belirtilen değere eşit veya ondan daha az.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**0**|**/ W0**|  
    |**1**|**/ W1**|  
    |**2**|**/ W2**|  
    |**3**|**/ W3**|  
    |**4**|**/ W4**|  
  
     Daha fazla bilgi için **/W** seçeneğini [MIDL komut satırı başvurusu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Ayrıca bkz **WarnAsError** bu tablodaki parametresi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)