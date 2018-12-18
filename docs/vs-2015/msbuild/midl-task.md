---
title: MIDL görevi | Microsoft Docs
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 345cd480cd5e34a6fe4650c9321d3ad9f90db01e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215793"
---
# <a name="midl-task"></a>MIDL Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sarmalar Microsoft arabirim tanımı dili (MIDL) derleyici aracı midl.exe'yi. Daha fazla bilgi için "MIDL komut satırı başvurusu" bakın [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır **MIDL** görev. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
-   **AdditionalIncludeDirectories**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bir dizin, içeri aktarılan IDL dosyaları, dahil edilen üst bilgi dosyaları ve uygulama yapılandırma dosyaları (ACF) için Aranan dizinleri listesine ekler.  
  
     Daha fazla bilgi için **/I** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **AdditionalOptions**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Komut satırı seçeneklerinin listesi. Örneğin, **"**_/option1 /option2 /option#_". Herhangi diğer MIDL görev parametresi tarafından temsil edilmez komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.  
  
     Daha fazla bilgi için "MIDL komut satırı başvurusu" bakın [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **ApplicationConfigurationMode**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bazı ACF anahtar sözcükleri IDL dosyasında kullanmanıza olanak sağlar.  
  
     Daha fazla bilgi için **/app_config** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **ClientStubFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     RPC arabirimi için istemci saplama dosyası adını belirtir.  
  
     Daha fazla bilgi için **/cstub** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca bkz: **ServerStubFile** bu tablodaki parametresi.  
  
-   **CPreprocessOptions**  
  
     İsteğe bağlı **dize** parametresi.  
  
     C/C++ önişlemci geçirilecek seçeneklerini belirtir. Önişlemci seçenekleri boşlukla ayrılmış bir listesini belirtin.  
  
     Daha fazla bilgi için **/cpp_opt** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **DefaultCharType**  
  
     İsteğe bağlı **dize** parametresi.  
  
     C derleyicisinin oluşturulmuş kodu derlemek için kullanacağı varsayılan karakter türünü belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**İmzalı**|**/char imzalı**|  
    |**İşaretsiz**|**/char işaretsiz**|  
    |**Ascii**|**/char ascii7**|  
  
     Daha fazla bilgi için **/char** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **DllDataFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Oluşturulan dosya adını belirtir *dlldata* bir ara sunucu DLL dosyası.  
  
     Daha fazla bilgi için **/dlldata** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **EnableErrorChecks**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Çalışma zamanında oluşturulan saptamalar gerçekleştireceğini denetlemede hata türünü belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**Yok**|**/ Error none**|  
    |**EnableCustom**|**/ Error**|  
    |**Tüm**|**/ Error tüm**|  
  
     Daha fazla bilgi için **/Error** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **ErrorCheckAllocations**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bellek yetersiz hataları kontrol edin.  
  
     Daha fazla bilgi için **/Error ayırma** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **ErrorCheckBounds**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`uyumluluğunu değişen boyutunu denetler ve iletim uzunluğu belirtimlerinin karşı diziler Çeşitleme uygulanıyor.  
  
     Daha fazla bilgi için **/Error bounds_check** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **ErrorCheckEnumRange**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, sabit listesi değerlerinin bir izin verilen aralıkta olup olmadığını kontrol eder.  
  
     Daha fazla bilgi için **/Error enum** komut satırı Yardımı seçeneğinde (**/?**) midl.exe'yi için.  
  
-   **ErrorCheckRefPointers**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, hiçbir null başvuru işaretçilerini istemci saptamalar için geçirilen olup olmadığını kontrol edin.  
  
     Daha fazla bilgi için **/Error ref** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **ErrorCheckStubData**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, sunucu tarafında unmarshaling özel durumlarını yakalayan ve bunları istemciye yayan bir saplama oluşturur.  
  
     Daha fazla bilgi için **/Error stub_data** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **GenerateClientFiles**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Derleyici bir RPC arabirimi için istemci tarafı C kaynak dosyaları oluşturup oluşturmayacağını belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**Yok**|**/ Client yok**|  
    |**Stub**|**/ Client saptama**|  
  
     Daha fazla bilgi için **/Client** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **GenerateServerFiles**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Derleyici bir RPC arabirimi için sunucu tarafı C kaynak dosyaları oluşturup oluşturmayacağını belirtir.  
  
     Her biri bir komut satırı seçeneğine karşılık gelir aşağıdaki değerlerden birini belirtin.  
  
    |Değer|Komut satırı seçeneği|  
    |-----------|--------------------------|  
    |**Yok**|**/ Server yok**|  
    |**Stub**|**/ Server saptama**|  
  
     Daha fazla bilgi için **/Server** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **GenerateStublessProxies**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, tam olarak yorumlanan saplamalar birlikte nesne arabirimleri için saplamasız proxy'ler oluşturur.  
  
     Daha fazla bilgi için **/oicf** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **GenerateTypeLibrary**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, bir tür kitaplığı (.tlb) dosyası oluşturulmuyor.  
  
     Daha fazla bilgi için **/notlb** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **HeaderFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Oluşturulan üst bilgi dosyasının adını belirtir.  
  
     Daha fazla bilgi için **/h** veya **/header** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **IgnoreStandardIncludePath**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, MIDL görevi kullanılarak belirtilen dizinleri arar **Additionalıncludedirectories** geçin ve geçerli dizinde ve INCLUDE ortam değişkeni tarafından belirtilen dizinlerini yoksayar.  
  
     Daha fazla bilgi için **/no_def_idir** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **InterfaceIdentifierFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Adını belirtir *arabirim tanımlayıcı dosyasının* bir COM arabirimi. Bu işlem için IDL dosyası adı "_i.c" ekleyerek alınan varsayılan adını geçersiz kılar.  
  
     Daha fazla bilgi için **/iid** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **LocaleID**  
  
     İsteğe bağlı **int** parametresi.  
  
     Belirtir *yerel ayar tanımlayıcısı* , giriş dosyaları, dosya adları ve dizin yolları uluslararası karakterlerin kullanılmasına olanak tanır. Bir ondalık yerel ayar kimliği belirtin.  
  
     Daha fazla bilgi için **/lcid** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca, "Yerel ayar kimlikleri atanan tarafından Microsoft'ta" MSDN bakın.  
  
-   **MkTypLibCompatible**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, mktyplib.exe 2.03 sürümüyle uyumlu olması için giriş dosyasının biçimi gerektirir.  
  
     Daha fazla bilgi için **/mktyplib203** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca MSDN Web sitesindeki "ODL FILE söz Dizimiyle" bakın.  
  
-   **OutputDirectory**  
  
     İsteğe bağlı **dize** parametresi.  
  
     MIDL görevi Çıkış dosyalarını nereye yazdığını varsayılan dizini belirtir.  
  
     Daha fazla bilgi için **/out** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **PreprocessorDefinitions**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Bir veya daha fazla belirtir *tanımlar*; diğer bir deyişle, bir ad ve isteğe bağlı bir değer C önişlemcisi geçirilecek IF bir `#define` yönergesi. Her tanımla biçimindedir, *[= değer] adı*.  
  
     Daha fazla bilgi için **/D** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca bkz **UndefinePreprocessorDefinitions** bu tablodaki parametresi.  
  
-   **ProxyFileName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Bir COM arabirimi arabirimi proxy dosyasının adını belirtir.  
  
     Daha fazla bilgi için **/proxy** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **RedirectOutputAndErrors**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Çıkış, hata iletileri ve uyarılar, belirtilen dosyaya standart çıktısından gibi yeniden yönlendirir.  
  
     Daha fazla bilgi için **/o** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **ServerStubFile**  
  
     İsteğe bağlı **dize** parametresi.  
  
     RPC arabirimi için sunucu saplama dosyası adını belirtir.  
  
     Daha fazla bilgi için **/sstub** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca bkz **ClientStubFile** bu tablodaki parametresi.  
  
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
  
     Daha fazla bilgi için **/ZP** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. **/ZP** seçenektir eşdeğer **/paketi** seçeneği ve eski **/ hizalama** seçeneği.  
  
-   **SuppressCompilerWarnings**  
  
     İsteğe bağlı **Boole** parametresi.  
  
     Varsa `true`, MIDL görevi uyarı ilerileri bastırır.  
  
     Daha fazla bilgi için **/no_warn** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **SuppressStartupBanner**  
  
     İsteğe bağlı `Boolean` parametresi.  
  
     Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.  
  
     Daha fazla bilgi için **/nologo** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
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
  
     Daha fazla bilgi için **/env** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
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
  
     Daha fazla bilgi için **/newtlb** ve **/oldtlb** Seçenekleri "İçinde MIDL komut satırı başvurusu" [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **TypeLibraryName**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Tür kitaplığı dosyasının adını belirtir.  
  
     Daha fazla bilgi için **/TLB** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **UndefinePreprocessorDefinitions**  
  
     İsteğe bağlı **String []** parametresi.  
  
     Önceki herhangi bir ad tanımı adı C önişlemcisi iletilmesiyle kaldırır. Eğer tarafından bir `#undefine` yönergesi. Bir veya daha fazla önceden tanımlanmış adlarını belirtin.  
  
     Daha fazla bilgi için **/U** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca bkz **PreprocessorDefinitions** bu tablodaki parametresi.  
  
-   **ValidateAllParameters**  
  
     İsteğe bağlı `Boolean` parametresi.  
  
     Varsa `true`, çalışma zamanında bütünlük denetimi gerçekleştirmek için kullanılan ek hata denetimi bilgileri oluşturur. Varsa `false`, hata denetimi bilgilerin oluşturulmuyor.  
  
     Daha fazla bilgi için **/ robust** ve **/no_robust** Seçenekleri "İçinde MIDL komut satırı başvurusu" [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
-   **WarnAsError**  
  
     İsteğe bağlı `Boolean` parametresi.  
  
     Varsa `true`, tüm uyarıları hata olarak değerlendirir.  
  
     Varsa **WarningLevel** MIDL görev parametresi belirtilmezse, varsayılan düzeyinde düzey 1 uyarı hata olarak kabul edilir.  
  
     Daha fazla bilgi için **wx** Seçenekleri "İçinde MIDL komut satırı başvurusu" [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca bkz **WarningLevel** bu tablodaki parametresi.  
  
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
  
     Daha fazla bilgi için **/W** "İçinde MIDL komut satırı başvuru" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca bkz **WarnAsError** bu tablodaki parametresi.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



