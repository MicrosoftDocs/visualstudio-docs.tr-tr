---
title: Sembol (.pdb) ve kaynak dosyaları hata ayıklayıcısı'nda ayarlayın
ms.custom: seodec18
ms.date: 10/08/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ba2f7794b052712d35bbdadb02a0ea8551dc78b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060452"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio hata ayıklayıcısında simge (.pdb) ve kaynak dosyaları belirtin (C#, C++, Visual Basic F#)

Program veritabanı (*.pdb*) dosyaları, simge dosyaları olarak da bilinir tanımlayıcılarını eşleme ve karşılık gelen tanımlayıcıları projenizin kaynak kodundaki deyimleri ve yönergeleri derlenmiş uygulamalar. 

Visual Studio IDE'den hata ayıklama derleme yapılandırması standart bir proje oluşturduğunuzda, derleyicinin uygun sembol dosyaları oluşturur. Ayrıca [kodda sembol seçeneklerini ayarlama](#compiler-symbol-options). 

*.Pdb* dosyası uygulamanızın hata ayıklama yapılandırmasının artımlı bağlamasına olanak tanıyan hata ayıklama ve proje durum bilgilerini tutar. Visual Studio hata ayıklayıcısını kullanan *.pdb* iki temel hata ayıklama sırasında bilgi parçasını belirlemek için dosyaları:

* Visual Studio IDE içinde görüntülemek için kaynak dosya adı ve satır numarası.
* Bir kesme noktası için durdurmak için uygulamayı nerede.

Sembol dosyaları da kaynak dosyaları ve isteğe bağlı olarak bunları almak için sunucu konumunu gösterir.
  
Hata ayıklayıcı yalnızca yükler *.pdb* tam olarak eşleşen dosyaları *.pdb* bir uygulama oluşturulduğunda oluşturulan dosyalar (diğer bir deyişle, özgün *.pdb* dosyaları veya kopya). Bu tam çoğaltma gerekli olduğundan kodun kendisi değişmese bile uygulama düzenini değiştirebilirsiniz. Daha fazla bilgi için [neden Visual Studio gerektiriyor hata ayıklayıcı sembol birlikte oluşturuldukları ikili dosyalarla tam olarak eşleşen dosyaları?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

> [!TIP]
> Proje çağrılarınızda Windows kod veya üçüncü taraf kodu gibi proje kaynak kodunuz dışında kod hatası ayıklamak için dış kodun konumunu belirtin *.pdb* dosyaları (ve isteğe bağlı olarak kaynak dosyaları), tam olarak eşleşmelidir uygulamanızda derlemeler. 

## <a name="symbol-file-locations-and-loading-behavior"></a>Sembol dosyası konumlarını ve yükleme davranışı

> [!NOTE]
> Uzak bir cihazda yönetilen kod hata ayıklaması yaparken tüm sembol dosyaları yerel makinede veya bir konumda bulunmalıdır [hata ayıklayıcı ayarlarında belirtilen](#BKMK_Specify_symbol_locations_and_loading_behavior).  
  
Visual Studio IDE içinde bir projede hata ayıklaması yaparken, hata ayıklayıcı proje klasöründe yer alan sembol dosyalarını otomatik olarak yükler. 

Hata ayıklayıcı ayrıca sembol dosyaları aşağıdaki konumlarda arar:

1. DLL veya yürütülebilir dosyanın içinde belirtilen konumdan (*.exe*) dosyası.  
   
   Varsayılan olarak, bir DLL oluşturduysanız veya bir *.exe* bağlayıcı bilgisayarınızda dosyanın bulunduğu yerleştirir tam yolunu ve dosya ilişkili *.pdb* DLL dosyasında veya *.exe* dosya. Hata ayıklayıcı sembol dosyası bu konumda olup olmadığını denetler.  
   
2. Dll dosyasını aynı klasöre veya *.exe* dosya.
   
3. Hata ayıklayıcı seçeneklerindeki sembol dosyaları için belirtilen konumlara. Ekleme ve simge konumları etkinleştirmek için bkz: [sembol konumlarını yapılandırma ve yükleme seçenekleri](#BKMK_Specify_symbol_locations_and_loading_behavior). 
   
   - Tüm yerel sembol Önbellek klasörü.  
  
   - Belirtilen ağ, internet veya yerel sembol sunucuları ve konumları, seçtiyseniz, Microsoft sembol sunucuları gibi. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hata ayıklama sembol dosyalarını uygulayan sembol sunucularından indirebilirsiniz `symsrv` protokolü. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) ve [Windows için hata ayıklama araçları](/windows-hardware/drivers/debugger/index) sembol sunucuları kullanabileceğiniz iki araçtır.
      
     Kullanabileceğinize sembol sunucuları şunlardır:  
      
     **Genel Microsoft sembol sunucuları**: bir sistem DLL Dosyasına veya bir üçüncü taraf kitaplığı için bir çağrı sırasında oluşan bir çökme hatasını gidermek için genellikle sistem gerekir *.pdb* dosyaları. Sistem *.pdb* dosyaları Windows DLL'leri için semboller içeren *.exe* dosyaları ve cihaz sürücüleri. Windows işletim sistemlerinde, MDAC, IIS, ISA sembolleri alabilirsiniz ve [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] genel Microsoft sembol sunucularından. 
      
     **Sembol sunucularını bir iç ağdaki veya yerel makinenizde**: ekibiniz veya şirketiniz, kendi ürünleriniz için ve sembollerin önbelleği olarak sembol sunucuları dış kaynaklardan oluşturabilirsiniz. Kendi makineniz üzerinde bir sembol sunucusu olabilir. 
      
     **Üçüncü taraf sembol sunucuları**: Windows uygulamaları ve kitaplıkları, üçüncü taraf sağlayıcılar, Internet üzerinden sembol sunucusuna erişim sağlayabilir. 
    
     > [!WARNING]
     > Genel Microsoft sembol sunucuları farklı bir sembol sunucusu kullanıyorsanız, sembol sunucusunun ve yolunun güvenilir olduğundan emin olun. Sembol dosyası rastgele yürütülebilir kod içerebileceğinden güvenlik tehditlerine karşı sunulabilir.  

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Sembol konumları ve yükleme seçeneklerini yapılandırın

Üzerinde **Araçları** > **seçenekleri** > **hata ayıklama** > **sembolleri** sayfasında, şunları yapabilirsiniz:

- Belirtin ve Microsoft, Windows veya üçüncü taraf bileşenleri için arama yolları ve sembol sunucularını seçin.
- Bunu yapabilir veya hata ayıklayıcının sembolleri otomatik olarak istediğiniz modülleri belirtin.
- Etkin bir şekilde ayıklarken bu ayarları değiştirin. Bkz: [hata ayıklama sırasında sembolleri yönetme](#manage-symbols-while-debugging). 
  
**Sembol konumları ve yükleme seçenekleri belirtmek için:**

1. Visual Studio'da açın **Araçları** > **seçenekleri** > **hata ayıklama** > **sembolleri** (veya **Hata ayıklama** > **seçenekleri** > **sembolleri**).  
   
   ![Araçlar &#45; seçenekleri &#45; hata ayıklama &#45; semboller sayfasını](media/dbg-options-symbols.png "Araçları &#45; seçenekleri &#45; hata ayıklama &#45; semboller sayfasını")  
   
2. Altında **sembol dosyası (.pdb) konumlar**,
   - Kullanılacak **Microsoft sembol sunucuları**, onay kutusunu işaretleyin.  
   
   - Yeni bir sembol sunucusu konumu eklemek için
     1. Seçin **+** araç çubuğunda simge. 
     1. Metin alanına da sembol sunucusunun veya sembol konumunun URL veya klasör yolunu yazın. Deyimi tamamlama doğru biçimi bulmanıza yardımcı olur.
     
     >[!NOTE]
     >Yalnızca belirtilen klasör aranır. Arama yapmak istediğiniz tüm alt klasörlerde girişlerinde eklemeniz gerekir.  
   
   - Yeni bir VSTS sembol sunucusu konumu eklemek için 
     1. Seçin ![Araçları&#47; seçenekleri&#47; hata ayıklama&#47;sembolleri yeni sunucu simgesi](media/dbg_tools_options_foldersicon.png "Araçları &#45; seçenekleri &#45; hata ayıklama &#45; sembolleri yeni sunucu simgesi") araç çubuğunda simge. 
     1. İçinde **VSTS sembol Sunucusu'na Bağlan** iletişim kutusunda kullanılabilir sembol sunucularından birini seçip **Connect**.  
   
   - Simge konumları yüklenme sırasını değiştirmek için kullanın **Ctrl**+**yukarı** ve **Ctrl**+**aşağı**, veya **yukarı** ve **aşağı** ok simgeler. 
   - URL veya yol düzenlemek için girişi çift tıklatın veya seçin ve basın **F2**.  
   - Girişi kaldırmak için onu seçin ve ardından **-** simgesi.
  
3. (İsteğe bağlı) Altında sembol yükleme performansını iyileştirmek için **önbellek sembolleri bu dizinde**, sembol sunucuları kopyalayabilirsiniz bir yerel klasör yolunun semboller için türü.  
  
   > [!NOTE]
   > Yerel sembol önbellek C:\Windows veya bir alt klasör gibi korumalı bir klasördeki yerleştirmeyin. Bunun yerine okuma-yazma klasörü kullanın.  
  
   > [!NOTE]
   > Varsa C++ projeleri için `_NT_SYMBOL_PATH` ortam değişken ayarlandığında, altında ayarlanan değer kılar **önbellek sembolleri bu dizinde**.
  
4. Hata ayıklayıcıyı yüklemek istediğiniz modülleri belirtin **sembol dosyası (.pdb) konumlar** başladığı zaman.  
  
   -  Seçin **aktarılmadıysa tüm modülleri Yükle** (sembol dosyası konumu, özellikle hariç modüller hariç tüm modüller için tüm sembolleri yüklemek için varsayılan). Bazı modüller hariç tutmak için işaretleyin **dışlanan modülleri belirtin**seçin **+** simge modülleri hariç tutmak ve adlarını yazın **Tamam**.  
  
   -  Sembol dosyası konumlardan belirttiğiniz modülleri yüklemek için işaretleyin **yük yalnızca belirtilen modüller**. Seçin **modülleri belirt dahil**seçin **+** simgesi ekleyin ve ardından modülleri adlarını yazın **Tamam**. Diğer modüller için Sembol dosyaları yüklü değil.  
  
5. Seçin **Tamam**.

## <a name="other-symbol-options-for-debugging"></a>Hata ayıklama için diğer sembol seçenekleri
  
Ek sembol seçenekleri, seçtiğiniz **Araçları** > **seçenekleri** > **hata ayıklama** > **genel** (veya **hata ayıklama** > **seçenekleri** > **genel**):  

- **DLL dışarı aktarmaları (yalnızca yerel) yükle**  
  
  C/C++ için dışa aktarma tablolarını yükler DLL. Ayrıntılar için bkz [DLL dışarı aktarma tabloları](#use-dumpbin-exports). Dışa aktarma tablolarının yüklenirken varsayılan olarak kapalıdır için bazı ek yükler okuma DLL dışa aktarma bilgilerini içerir. Ayrıca `dumpbin /exports` C/C++ derleme komut satırında.  
  
- **Adres seviyesinde hata ayıklamayı etkinleştir** ve **Show Ayrıştırılmış kod kaynak kullanılamıyorsa**  
  
  Dosyaları kaynak veya sembol bulunamadığında ayrıştırılmış kodu her zaman gösterir.  
  
  ![Seçenekleri &#47; hata ayıklama &#47; genel ayrıştırma seçenekleri](../debugger/media/dbg_options_general_disassembly_checkbox.png "seçenekleri &#47; hata ayıklama &#47; genel ayrıştırma seçenekleri")  
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Kaynak sunucusu desteğini etkinleştir**  
  
  Yerel makinede kaynak kod olduğunda, bir uygulamanın hatalarını ayıklamak için kaynak sunucu kullanır veya *.pdb* dosya kaynak kodu eşleşmiyor. Kaynak sunucu, dosya isteklerini alır ve kaynak denetiminden gerçek dosyaları döndürür. Kaynak sunucuda çalışan adlı bir DLL kullanarak *srcsrv.dll* uygulamanın okunacak *.pdb* dosya. *.Pdb* dosya kaynak kodu depodan almak için kullanılan komutların yanı sıra kaynak kod deposu işaretçileri içerir. 
  
  Komutlar sınırlandırabilir, *srcsrv.dll* uygulamanın yürütebilir *.pdb* adlı dosyadaki izin verilen komutları listesi dosyasını *srcsrv.ini*. Bir yerde *srcsrv.ini* dosya aynı klasörde *srcsrv.dll* ve *devenv.exe*.  
  
  >[!IMPORTANT]
  >Rastgele komutlar uygulamanın içinde gömülebilir *.pdb* dosya, bu nedenle yalnızca içine yürütmek istediğiniz komutları yerleştirdiğinizden emin olun bir *srcsrv.ini* dosya. İçinde olmayan bir komutu yürütmek yapmaya *srcsvr.ini* dosya bir onay iletişim kutusunda görünmesine neden olur. Daha fazla bilgi için [güvenlik uyarısı: hata ayıklayıcı gerekir yürütme güvenilmeyen komut](../debugger/security-warning-debugger-must-execute-untrusted-command.md). 
  >
  >Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlara dikkat edin. Örneğin, listelenen *cmd.exe* içinde *srcsrv.ini*, kötü niyetli bir kullanıcı şirket parametreler belirtebilir *cmd.exe* olun, tehlikeli.  
  
  Bu öğeyi ve alt öğeleri seçin. **Kısmi güven derlemeleri (sadece yönetilen) için kaynak sunucuya izin** ve **her zaman sormadan güvenilmeyen kaynak sunucu komutlarını Çalıştır** güvenlik risklerini artırabilir.  
  
  ![Kaynak sunucu seçenekleri etkinleştirme](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  

## <a name="compiler-symbol-options"></a>Derleyici sembol seçenekleri  

Visual Studio IDE'den standart bir proje oluşturduğunuzda **hata ayıklama** yapı yapılandırması C++ ve yönetilen derleyiciler kodunuz için uygun sembol dosyalarını oluşturun. Kodda derleyici seçeneklerini de ayarlayabilirsiniz. 

### <a name="cc-options"></a>C/C++ seçenekleri 

- *VC\<x > .pdb* ve  *\<Proje > .pdb* dosyaları
  
  A *.pdb* C/C++ ile oluşturduğunuzda oluşturulan için dosya [/zı veya /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format). İçinde [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], [/Fd](/cpp/build/reference/fd-program-database-file-name) seçenek adları *.pdb* dosya derleyici oluşturur. Bir proje oluşturduğunuzda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE'yi kullanarak **/Fd** seçeneği oluşturmak için ayarlanmış bir *.pdb* adlı dosya  *\<Proje > .pdb*.  
  
  C/C++ uygulamanızı bir derleme görevleri dosyası derleme ve belirtirseniz **/zi** veya **/zi** kullanmadan **/Fd**, derleyici iki oluşturur *.pdb*dosyaları:  
  
  - *VC\<x > .pdb*burada  *\<x >* Visual C++ sürümlerinden birini, örneğin temsil *vc11.pdb öğesini* 
    
    *VC\<x > .pdb* dosya tek bir nesne dosyaları için tüm hata ayıklama bilgilerini depolar ve proje derleme görevleri dosyası ile aynı dizinde bulunur. Her bir nesne dosyası oluşturduğunda, C/C++ derleyicisi hata ayıklama bilgileri birleştirir *VC\<x > .pdb*. Her kaynak dosyası gibi ortak başlık dosyaları gibi içerse bile bunu  *\<windows.h >*, başlıklardan yalnızca bir kez yerine her nesne dosyasında depolanır. Eklenen bilgiler türü bilgilerini içerir, ancak işlev tanımları gibi sembol bilgilerini içermez.  
  
  - *\<Proje > .pdb* 
    
     *\<Proje > .pdb* dosya projenin tüm hata ayıklama bilgilerini depolar *.exe* dosya ve bulunan *\debug* alt.  *\<Proje > .pdb* bulunan tür bilgilerini değil dosya içeren işlev prototipleri dahil olmak üzere tam hata ayıklama bilgilerini *VC\<x > .pdb*. 
  
  Her iki *VC\<x > .pdb* ve  *\<Proje > .pdb* dosyaları artımlı güncelleştirmelere izin. Bağlayıcı ayrıca yolunu katıştırır *.pdb* dosyalar *.exe* veya *.dll* dosyası oluşturur.  
  
- <a name="use-dumpbin-exports"></a>DLL dışarı aktarma tabloları
  
  Kullanım `dumpbin /exports` bir DLL'nin dışa aktarma tablosunda kullanılabilir sembolleri görmek için. DLL dışa aktarma tablolarının simgesel bilgiler Windows iletileri, Windows yordamları (WindowProcs), COM nesneleri, hazırlama veya sembolleri olmayan herhangi bir DLL ile çalışmak için yararlı olabilir. Semboller tüm 32-bit sistem DLL için kullanılabilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir. 
  
  Okuyarak `dumpbin /exports` çıkışı, alfasayısal olmayan karakterler de dahil tam işlev adlarını görebilirsiniz. İşlev adları hata ayıklayıcıda başka bir yerde kesilebiliyorsa tam işlev adlarını görme bir işlev üzerinde bir kesme noktası ayarlamak için kullanışlıdır. Daha fazla bilgi için [dumpbin/EXPORTS](/cpp/build/reference/dash-exports).  
  
### <a name="net-framework-options"></a>.NET Framework seçenekleri 
  
İle derleme **/debug** oluşturmak için bir *.pdb* dosya. İle uygulama oluşturabilirsiniz **/Debug: Full** veya **/debug:pdbonly**. İle oluşturma **/Debug: Full** hata ayıklaması yapılabilir kod oluşturur. İle oluşturma **/debug:pdbonly** oluşturur *.pdb* dosyaları, ancak oluşturmaz `DebuggableAttribute` JIT derleyicisine hata ayıklama bilgilerinin kullanılabilir olduğunu bildirir. Kullanım **/debug:pdbonly** oluşturmak istiyorsanız *.pdb* dosyaları bir yayın için derleme, hata ayıklanabilir olmasını istemediğinizi. Daha fazla bilgi için [/Debug (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) veya [/Debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).  
  
### <a name="web-applications"></a>Web uygulamaları  
  
Ayarlama *web.config* dosya, ASP.NET uygulamanızın hata ayıklama modu. Hata ayıklama modu ASP.NET'in dinamik olarak oluşturulan dosyalar için sembol oluşturmasına neden olur ve hata ayıklayıcının ASP.NET uygulamasına eklemesine olanak tanır. Visual Studio hata ayıklamak başlattığınızda web proje şablonunu projenizi oluşturduysanız bu otomatik olarak ayarlar.  

##  <a name="manage-symbols-while-debugging"></a>Hata ayıklama sırasında sembolleri yönetme 

Kullanabileceğiniz **modülleri**, **çağrı yığını**, **Yereller**, **Otolar**, veya herhangi **izleyin** penceresi yüklemek için simgeleri veya hata ayıklama sırasında sembol seçeneklerini değiştirin. Daha fazla bilgi için [Hata Ayıklayıcı'nın uygulamanıza nasıl ekleyen daha iyi tanımak](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="use-the-modules-window"></a>Modüller penceresini kullanma

Hata ayıklama sırasında **modülleri** penceresi kullanıcı kodu veya My Code ve durumu yüklenirken, sembol hata ayıklayıcı değerlendirmesini kod modülleri gösterir. Sembol yükleme durumu izleyin, yük sembolleri da sembol seçenekleri değiştirin **modülleri** penceresi.

**İzleme veya hata ayıklama sırasında simge konumları veya seçeneklerini değiştirmek için:**

1. Açmak için **modülleri** hata ayıklarken, penceresinde **hata ayıklama** > **Windows** > **modülleri**. 
1. İçinde **modülleri** penceresinde sağ **sembol durumu** veya **sembol dosyası** üstbilgilerinde veya herhangi bir modül. 
1. Bağlam menüsünde aşağıdaki seçeneklerden birini seçin:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Sembolleri yükle**|Atlanan, bulunamadı veya yüklenmedi simgelerle modüller için görünür. Belirtilen konumlardan sembolleri yüklemeye çalışır **seçenekleri** > **hata ayıklama** > **sembolleri** sayfası. Sembol dosyası bulunamadı veya yüklenmedi, başlatan **dosya Gezgini** aranacak yeni bir konum belirtebilirsiniz.|  
|**Sembol yükleme bilgisi**|Yüklenen sembol dosyasının konumunu veya hata ayıklayıcı dosyasını bulamazsanız, aranan konumları gösterilir.|  
|**Sembol ayarları**|Açılır **seçenekleri** > **hata ayıklama** > **sembolleri** sayfasında, düzenlemek ve simge konumları ekleyebileceğiniz yerdir.|  
|**Her zaman otomatik olarak yükle**|Seçili sembol dosyası hata ayıklayıcı tarafından otomatik olarak yüklenecek dosya listesi ekler.|  

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Yüklü sembol yok Loaded/No kaynak sayfalarını kullanma

Hata ayıklayıcısı sembol veya kaynak dosyalarına sahip olmayan kod içine kesmeyle girmenin birkaç yolu vardır:  

-  Kodda ilerleyebilmeniz.  
-  Bir kesme noktası veya özel durum koda bölün.  
-  Farklı bir iş parçacığına geçiş.  
-  Bir çerçevede çift tıklayarak yığın çerçevesini değiştirme **çağrı yığını** penceresi.  
   
Bu durumda, hata ayıklayıcı görüntüler **yüklü sembol yok** veya **yüklü kaynak yok** kaynak ve gerekli sembolleri bilip yardım sayfalarına.  
  
 ![Yüklü sembol yok sayfası](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
**Eksik sembolleri bilip yardımcı olmak için yüklü sembol yok belge sayfası kullanmak için:**  
  
-   Arama yolunu değiştirmek için seçilmeyen bir yolu seçin veya seçin **yeni yol** veya **yeni VSTS yolu** girin veya yeni bir yol seçin. Seçin **yük** yolları tekrar aramak ve bulunursa sembol dosyasını yüklemek için.  
-   Arama yollarını yeniden deneyin ve herhangi bir sembol seçeneklerini geçersiz kılmak için **Gözat ve Bul \<yürütülebilir dosya adı >**. Sembol dosyası bulunursa, yüklendikten veya **dosya Gezgini** sembol dosyasını el ile seçebilmeniz için açar.  
-   Açmak için **seçenekleri** > **hata ayıklama** > **sembolleri** sayfasında **sembol ayarlarını değiştir**.  
-   Yeni bir pencerede bir defa ayrıştırılmış kodu göstermek için seçin **ayrıştırılmış kodu görüntüle**, ya da seçin **Seçenekleri iletişim kutusu** dosyaları kaynak veya sembol bulunamadığında ayrıştırılmış kodu her zaman göstermek için seçeneği ayarlamak için. 
-   Aranan konumları ve sonucu göstermek için genişletin **sembol yükleme bilgisi**. 

Hata ayıklayıcı bulursa *.pdb* seçeneklerden birini yürütme ve kaynak dosya bilgileri kullanarak alabilir sonra dosya *.pdb* dosya, kaynak görüntülenir. Aksi halde görüntüler bir **yüklü kaynak yok** sorunu giderebilecek eylemleri için bağlantılarla birlikte sorunu açıklayan bir sayfa.

**Kaynak dosyası arama yollarını çözüme eklemek için:**
  
Hata ayıklayıcı kaynak dosyaları arar konumlarını belirtin ve arama belirli dosyaları dışlayın.

1. Çözümde seçin **Çözüm Gezgini**ve ardından **özellikleri** simgesi, tuşuna **Alt**+**Enter**, veya sağ tıklayıp **özellikleri**.
   
1. Seçin **hata ayıklama kaynak dosyalarının**.
   
1. Altında **kaynak kodu içeren dizinler**aramak için kaynak kodu konumları seçin veya yazın. Kullanım **yeni satır** simgesini, daha fazla konum ekleyebilirsiniz **yukarı** ve **aşağı** , yeniden sıralamak için ok simgeleri veya **X** silmeyi simgesi.
   
   >[!NOTE]
   >Hata ayıklayıcısının yalnızca belirtilen dizin arar. Arama yapmak istediğiniz alt dizinler için girdi eklemeniz gerekir.
   
1. Altında **bu kaynak dosyaları arama**, kaynak dosyaları arama dışında tutulacak adlarını yazın. 
   
1. Seçin **Tamam** veya **uygulamak**.


## <a name="see-also"></a>Ayrıca bkz.  
[Sembol dosyalarını ve Visual Studio sembol Ayarları'nı anlama](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)

[Visual Studio 2012 ve 2013 değişiklikleri yükleme .NET uzaktan sembolü](https://blogs.msdn.microsoft.com/devops/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
