---
title: Sembol (.pdb) belirtin ve kaynak dosyaları hata ayıklayıcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f716bb50d04b7bb3e961325136c118d6dcc4a9db
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062754"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Visual Studio Hata Ayıklayıcısında Simge (.pdb) ve Kaynak Dosyaları Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sembol dosyası olarak da bilinen program veritabanı (.pdb) dosyası sınıflar, yöntemler ve başka bir kod için kaynak dosyalarında oluşturduğunuz tanımlayıcıları projenizin derlenen yürütülebilir dosyalarında kullanılan tanımlayıcılarla eşleştirir. .Pdb dosyası, kaynak kodundaki deyimleri yürütülebilir dosyalardaki yürütme yönergeleriyle de eşleştirir. Hata ayıklayıcı iki temel bilgi parçasını belirlemek için bu bilgileri kullanır: Visual Studio IDE'sinde görüntülenen kaynak dosya ve satır numarası ile bir kesme noktası ayarladığınızda durdurulacak yürütülebilir öğenin konumu. Sembol dosyası ayrıca orijinal kaynak dosyası konumunu ve isteğe bağlı olarak, kaynak dosyasının alındığı kaynak sunucusunun konumunu içerir.

 Visual Studio IDE içinde bir projede hata ayıklaması yaparken, hata ayıklayıcı kodunuz için .pdb ve kaynak dosyaları için varsayılan konum bilir. Proje çağrılarınızda Windows veya üçüncü taraf kodu olması gibi, proje kaynak kodunuz dışında kod hatası ayıklamak istiyorsanız, .pdb konumunu (ve isteğe bağlı olarak, harici kod kaynak dosyalarını) belirtmeniz gerekir ve bu dosyaların yürütülebilir yapıyla tam olarak eşleşmesi gerekir.

 Visual Studio 2012 önce uzak bir cihazda yönetilen kod hata ayıklaması yaparken sembol dosyalarını uzak makinede gerekli. Bu durum artık geçerli değildir. Tüm sembol dosyaları yerel makinede veya belirlenen bir konumda bulunan **Araçlar / Seçenekler / hata ayıklama / semboller** sayfası.

##  <a name="BKMK_Find_symbol___pdb__files"></a> Hata ayıklayıcı .pdb dosyalarını nerede arar

1.  DLL veya yürütülebilir dosyanın içinde belirtilen konum.

     (Varsayılan olarak, bilgisayarınızda bir DLL veya yürütülebilir dosya oluşturduysanız bağlayıcı, DLL veya yürütülebilir dosya içindeki ilgili .pdb dosyasının yolunu ve dosya adını tam olarak yerleştirir. Hata ayıklayıcı önce DLL'de veya yürütülebilir dosyada belirtilen konumda sembol dosyasının varolup olmadığını denetler. Her zaman bilgisayarınızda derlediğiniz kod için kullanılabilir semboller olduğundan bu yararlıdır.)

2.  DLL veya yürütülebilir dosyayla aynı klasörde bulunabilecek .pdb dosyaları.

3.  Yerel sembol önbellek klasörleri.

4.  Etkinleştirildiyse Microsoft sembol sunucusu gibi sunucu üzerinde belirtilen tüm ağ, internet veya yerel sembol sunucuları ve konumları.

###  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Neden sembol dosyalarının yürütülebilir dosyalarla tam olarak eşleşmesi gerekiyor mu?
 Hata ayıklayıcı, yalnızca yürütülebilir dosya oluşturulduğunda, oluşturulan .pdb dosyasıyla tam olarak eşleşen bir yürütülebilir dosya için bir .pdb dosyasını yükler (yani, .pdb özgün olmalı veya özgün .pdb'nin kopyasını olmalıdır). Doğru ve verimli kod oluşturma olan temel görevinin yanı sıra derleyici derleme hızı için de optimize edilmiş olduğundan, kodun kendisi değişmese bile yürütülebilir dosyanın gerçek düzeni değişebilir. Daha fazla bilgi için [neden Visual Studio gerektiriyor hata ayıklayıcı sembol birlikte oluşturuldukları ikili dosyalarla tam olarak eşleşen dosyaları?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

###  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Sembol konumları ve yükleme davranışı belirtin
 VS IDE içinde bir projede hata ayıklaması yaparken, hata ayıklayıcı proje dizininde yer alan sembol dosyalarını otomatik olarak yükler. Alternatif arama yolları belirtin ve Microsoft, Windows veya üçüncü taraf bileşenleri için Sembol sunucularını **Araçlar / Seçenekler / hata ayıklama / semboller**. Hata ayıklayıcının sembolleri otomatik olarak istediğiniz belirli modülleri belirtebilirsiniz. Ve daha sonra etkin bir şekilde hata ayıklama yaparken bu ayarları el ile değiştirebilirsiniz.

1. Visual Studio'da açın **Araçlar / Seçenekler / hata ayıklama / semboller** sayfası.

    ![Araçlar &#45; seçenekleri &#45; hata ayıklama &#45; semboller sayfasını](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")

2. Klasör Seç ![Araçları&#47; seçenekleri&#47; hata ayıklama&#47;sembolleri klasör simgesini](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") simgesi. Düzenlenebilir metin görünür **sembol dosyası (.pdb) konumlar** kutusu.

3. URL'yi ya da sembol sunucusunun veya sembol konumunun dizin yolunu yazın. Deyimi tamamlama doğru biçimi bulmanıza yardımcı olur.

4. Sembol geliştirmek için yükleme performansını yazın sembolleri kopyalanabildiği sembol sunucuları tarafından yerel bir dizin yolu **önbellek sembolleri bu dizinde** sembolleri kopyalanabilir yerel bir dizin kutusu.

   > [!NOTE]
   >  Sembol önbelleğinizi korunan klasöre (C:\Windows folder veya bunun alt klasörlerinden biri) koymayın. Bunun yerine okuma-yazma klasörü kullanın.

   **Sembol yükleme davranışı belirtin**

   Otomatik olarak yüklenmesini istediğiniz dosyaları belirtebilirsiniz **sembol dosyası (.pdb) konumlar** hata ayıklamaya başladığınızda kutusu konumlarından. Proje dizinindeki sembol dosyaları her zaman yüklenir.

5. Seçin **tüm modüllerin aktarılmadıysa** seçtiğinizde belirttiğiniz hariç tüm modüller için tüm sembolleri yüklemek üzere **dışlanan modülleri belirtin** bağlantı.

6. Seçin **yalnızca belirtilen modüller** seçeneğini ve ardından **modülleri belirtin** otomatik olarak yüklemek istediğiniz dosyaları sembol modülleri listelemek için. Diğer modüller için sembol dosyaları göz ardı edilir.

   **Ek sembol seçenekleri belirtin**

   Üzerinde şu seçenekler ayarlayabilirsiniz **Araçlar / Seçenekler / hata ayıklama / semboller** sayfası:

   **(Yalnızca yerel) sembol yoksa uyar**

   Seçilirse, hata ayıklayıcının kendisiyle ilgili sembole yönelik bilgi içermediği bir programdaki hataları ayıklamayı denediğinizde bir uyarı iletişim kutusu görüntüler.

   **DLL dışarı aktarmaları yükle**

   Seçildiğinde, DLL dışa aktarma tablolarını yükler. DLL dışa aktarma tablolarının sembole yönelik bilgileri, Windows iletileri, Windows yordamları (WindowProcs), COM nesneleri veya sıralama ile ya da sembolleri olmayan herhangi bir DLL ile çalışıyorsanız yararlı olabilir. DLL dışa aktarma bilgilerini okuma bazı ek okumalar içerir. Bu nedenle, bu özellik varsayılan olarak kapalıdır.

   Bir DLL'nin dışa aktarma tablosunda hangi sembollerin kullanılabilir görmek için `dumpbin /exports`. Semboller tüm 32-bit sistem DLL için kullanılabilir. Okuyarak `dumpbin /exports` çıkışı, alfasayısal olmayan karakterler de dahil tam işlev adını görebilirsiniz. Bu, bir işlev bir kesme noktası ayarlamak için yararlıdır. DLL dışarı aktarma tablolarındaki işlev adları, hata ayıklayıcının başka bir yerinde kesilmiş görünebilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir. Daha fazla bilgi için [dumpbin/EXPORTS](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).

###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Yerel makinenizde olmayan sembol dosyalarını bulmak için Sembol sunucularını kullanın
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklama sembol dosyalarını symsrv protokolünü uygulayan sembol sunucularından indirebilirsiniz. [Visual Studio Team Foundation Server](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) ve [Windows için hata ayıklama araçları](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) , sembol Hizmetleri uygulayan iki araçtır. VS kullanılacak sembol sunucularını belirtirsiniz **seçenekleri** iletişim kutusu.

 Kullanabileceğiniz sembol sunucuları şunlardır:

 **Microsoft Genel sembol sunucuları**

 Bir sistem DLL dosyasına veya bir üçüncü taraf kitaplığına yapılan bir çağrı sırasında oluşan bir çökme hatasını gidermek için, genellikle Windows DLL'leri, EXE'ler, ve cihaz sürücüleri için semboller içeren .pdb dosyalarına gereksinim duyarsınız. Bu sembolleri Microsoft ortak sembol sunucularından elde edebilirsiniz. Microsoft Genel sembol sunucuları, MDAC, IIS, ISA ek olarak Windows işletim sistemleri için semboller sağlar ve [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Microsoft sembol sunucuları kullanmayı tercih **seçenekler ve ayarlar** üzerinde **hata ayıklama** menüsünü seçip **sembolleri**. Seçin **Microsoft sembol sunucuları**.

 **Bir iç ağdaki veya yerel makinenizdeki sembol sunucuları**

 Ekibiniz veya şirketiniz, kendi ürünleriniz için ve dış kaynaklardan alınan sembollerin önbelleği olarak sembol sunucuları oluşturabilir. Kendi makineniz üzerinde bir sembol sunucusu olabilir. Bir URL veya yol olarak sembol sunucularının konumunu girin **hata ayıklama**/**sembolleri** VS sayfası **seçeneği iletişim**.

 **Üçüncü taraf sembol sunucuları**

 Üçüncü taraf Windows uygulamaları ve kitaplıkları sağlayıcılar internet üzerinden sembol sunucusuna erişim sağlayabilir. Bu sembol sunucularının URL'sini de girin **hata ayıklama**/**sembolleri** sayfası

> [!NOTE]
>  Microsoft ortak sembol sunucularından farklı bir sembol sunucusu kullanıyorsanız, sembol sunucusunun ve yolunun güvenilir olduğundan emin olun. Sembol dosyası rastgele yürütülebilir kod içerebileceğinden güvenlik tehditlerine maruz kalabilirsiniz.

###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a> Bulma ve hata ayıklama sırasında sembolleri yükle
 Hata ayıklayıcı kesme modundayken, hata ayıklayıcı seçenekleriyle daha önce hariç tutulan veya derleyicinin bulamadığı bir modül için semboller yükleyebilirsiniz. Çağrı Yığını, Modüller, Yereller, Otolar ve tüm Gözcü pencerelerinin kısayol menülerinden sembol yükleyebilirsiniz. Hata ayıklayıcısı sembol veya kaynak dosyalarına sahip olmayan kodu keserse, bir belge penceresi görüntülenir. Burada, eksik dosyaları ve bunları bulup yüklemek için yapılacak eylemler hakkında bilgi bulabilirsiniz.

 **Yüklü sembol yok belge sayfaları içeren sembolleri bulun**

 Hata ayıklayıcının kullanılabilir sembolleri bulunmayan kodlara girebilmesi için çeşitli yollar vardır:

1. Kodun içine adımlama.

2. Kodu kesme noktasından veya özel durumdan ayırma.

3. Farklı bir iş parçacığına geçiş.

4. Çağrı Yığını penceresinde bir çerçeveyi çift tıklayarak yığın çerçevesini değiştirme.

   Bu olaylardan biri oluştuğunda, hata ayıklayıcı görüntüler **yüklü sembol yok** gerekli sembolleri bilip yardımcı olması için sayfa.

   ![Yüklü sembol yok sayfası](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

- Arama yollarını değiştirmek için seçilmeyen bir yolu seçin veya **yeni** ve yeni bir yol girin. Seçin **yük** yolları tekrar aramak ve bulunursa sembol dosyasını yüklemek için.

- Seçin **Gözat ve Bul**_yürütülebilir dosya adı_**...**  herhangi bir sembol seçeneklerini geçersiz kılmak ve arama yollarını yeniden deneyin. Sembol dosyası bulunursa yüklenir veya sembol dosyasını el ile seçmeniz için bir Dosya Gezgini görüntülenir.

- Seçin **sembol ayarlarını değiştir...**  görüntülenecek **hata ayıklama** / **sembolleri** VS Seçenekleri iletişim kutusu sayfası.

- Seçin **ayrıştırılmış kodu görüntüle** yeni bir pencerede bir defa ayrıştırılmış kodu göstermek için.

- Kaynak veya sembol dosyaları bulunamadığında ayrıştırılmış kodu her zaman göstermek için seçin **Seçenekleri iletişim kutusu** bağlantısını ve her ikisini de seçin **adres seviyesinde hata ayıklamayı etkinleştir** ve **ayrıştırılmış Kodu Göster, Kaynak kullanılamıyor**.

   ![Seçenekleri &#47; hata ayıklama &#47; genel ayrıştırma seçenekleri](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")

  **Sembol seçeneklerini kısayol menüsünden değiştirme**

  Kesme modunda çalışırken, Çağrı Yığını, Modüller, Yerel Öğeler, Otomatik Öğeler ve tüm İzleme pencerelerinde görüntülenen öğelerin sembollerini bulabilir ve yükleyebilirsiniz. Pencerede bir öğe seçin, kısayol menüsünü açın ve aşağıdaki seçeneklerden birini seçin:

|Seçenek|Açıklama|
|------------|-----------------|
|**Sembolleri yükle**|Belirtilen konumlardan sembolleri yüklemeye çalışır **hata ayıklama** / **sembolleri** sayfasının **seçenekleri** iletişim kutusu. Sembol dosyası bulunamazsa, Dosya Gezgini başlatılır, bu sayede aranacak yeni bir konum belirtebilirsiniz.|
|**Sembol yükleme bilgisi**|Yüklenen sembol dosyasının konumunu veya hata ayıklayıcı dosyasını bulamazsanız, aranan konumları gösteren bilgiler sunar.|
|**Sembol ayarları...**|Açılır **hata ayıklama** / **sembolleri** VS sayfası **seçenekleri** iletişim kutusu.|
|**Her zaman otomatik olarak yükle**|Hata ayıklayıcı tarafından otomatik yüklenen dosya listesine sembol dosyası ekler.|

###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a> Sembol dosyaları için derleyici seçeneklerini ayarlama
 VS IDE'den projenizi ne zaman ve standart **hata ayıklama** yapı yapılandırması C++ ve yönetilen derleyiciler kodunuz için uygun semboller dosyalarını oluşturun. Sembol dosyaları oluşturmak için komut satırında derleyici seçeneklerini de ayarlayabilirsiniz.

 **C++ seçenekleri**

 Program veritabanı (.pdb) dosyası, hata ayıklamayı ve programınızın Hata ayıklama yapılandırmasının artımlı bağlamasına olanak tanıyan proje durum bilgilerini tutar. İle oluşturduğunuzda .pdb dosyası oluşur [/zı veya /Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) (C/C++ için).

 İçinde [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], [/Fd](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) seçeneği derleyici tarafından oluşturulan .pdb dosyasını adlandırır. Bir proje oluşturduğunuzda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sihirbazları kullanarak **/Fd** seçeneği adlı bir .pdb dosyası oluşturmak için ayarlanır *proje*.pdb.

 C/C++ uygulamanızı bir derleme görevleri dosyası derleme ve belirtirseniz **/zi** veya **/zi** olmadan **/Fd**, iki .pdb dosyası ile biter:

- VC*x*.pdb, burada *x* Visual C++ sürümlerinden birini, örneğin vc11.pdb öğesini temsil eder. Bu dosya, tek tek OBJ dosyaları için hata ayıklama bilgilerini depolar ve proje derleme görevleri dosyası ile aynı dizinde bulunur.

- Project.pdb bu dosya the.exe dosyası için tüm hata ayıklama bilgilerini depolar. C/C++'ta \debug alt dizininde bulunur.

  Her OBJ dosyası oluşturduğunda, C/C++ derleyicisi hata ayıklama bilgileri VC birleştirir.*x*.pdb. Eklenen bilgiler türü bilgilerini içerir, ancak işlev tanımları gibi sembol bilgilerini içermez. Her kaynak dosyası gibi ortak başlık dosyaları gibi içerse bile bunu \<windows.h >, bir başlıklardan her OBJ dosyasında olmak yerine yalnızca bir kez saklanır.

  Bağlayıcı, projenin EXE dosyasına ilişkin hata ayıklama bilgilerini içeren project.pdb'yi oluşturur. Project.pdb dosyası VC bulunan tür bilgilerini değil, işlev prototipleri dahil olmak üzere tam hata ayıklama bilgilerini içeren*x*.pdb. Her iki .pdb dosyası da artımlı güncelleştirmelere izin verir. Bağlayıcı ayrıca .pdb dosyasının yolunu, oluşturduğu .exe veya .dll dosyasına katıştırır.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hata ayıklayıcısı yolu EXE veya DLL dosyasında .pdb dosyasının project.pdb dosyasını bulmak için kullanır. Hata ayıklayıcısı .pdb dosyasını bu yerde bulunamıyor veya yol geçersizse (örneğin, proje başka bir bilgisayara taşınmışsa) hata ayıklayıcı EXE içeren yolu arar ve sembol yollarını arar **seçenekleri** iletişim kutusu (**hata ayıklama** klasöründe **sembolleri** düğümü). Hata ayıklayıcı, hata ayıklaması yapılan yürütülebilir öğeyle eşleşmeyen bir .pdb dosyası yüklemez. Hata ayıklayıcı bir .pdb dosyası bulamazsa, bir **sembol Bul** iletişim kutusu görüntülenir, burada sembol arayabilir veya arama yoluna ilave konum ekleyebilirsiniz.

  **.NET framework seçenekleri**

  Program veritabanı (.pdb) dosyası, hata ayıklamayı ve programınızın hata ayıklama yapılandırmasının artımlı bağlamasına olanak tanıyan proje durum bilgilerini tutar. İle oluşturduğunuzda .pdb dosyası oluşur **/debug**. İle uygulama oluşturabilirsiniz **/Debug: Full** veya **/debug:pdbonly**. İle oluşturma **/Debug: Full** hata ayıklaması yapılabilir kod oluşturur. İle oluşturma **/debug:pdbonly** .pdb dosyaları oluşturur ancak oluşturmaz `DebuggableAttribute` JIT derleyicisine hata ayıklama bilgilerinin kullanılabilir olduğunu bildirir. Kullanım **/debug:pdbonly** hata ayıklanabilir olmasını istemediğiniz yayın yapısı için .pdb dosyaları oluşturmak istiyorsanız. Daha fazla bilgi için [/Debug (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) veya [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hata ayıklayıcısı yolu EXE veya DLL dosyasında .pdb dosyasının project.pdb dosyasını bulmak için kullanır. Hata ayıklayıcısı .pdb dosyasını bu yerde bulunamıyor veya yol geçersizse, hata ayıklayıcı EXE içeren yolu arar ve sembol yollarını sonra belirtilen **seçenekleri** iletişim kutusu. Bu yol genellikle **hata ayıklama** klasöründe **sembolleri** düğümü. Hata ayıklayıcı, hata ayıklaması yapılan yürütülebilir dosyayla eşleşmeyen bir .pdb dosyası yüklemez. Hata ayıklayıcı bir .pdb dosyası bulamazsa, bir **sembol Bul** iletişim kutusu görüntülenir, burada sembol arayabilir veya arama yoluna ilave konum ekleyebilirsiniz.

  **Web uygulamaları**

  Uygulamanızın yapılandırma dosyası (Web.config) hata ayıklama moduna ayarlanmalıdır. Hata ayıklama modu ASP.NET'in dinamik olarak oluşturulan dosyalar için sembol oluşturmasına neden olur ve hata ayıklayıcının ASP.NET uygulamasına eklemesine olanak tanır. Web Proje şablonunu kullanarak projenizi oluşturduysanız, hata ayıklamayı başlattığınızda VS bunu otomatik olarak ayarlar.

##  <a name="BKMK_Find_source_files"></a> Kaynak dosyaları bulun

###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Hata ayıklayıcı kaynak dosyaları nerede arar
 Hata ayıklayıcı kaynak dosyaları aşağıdaki konumlarda arar:

1.  Hata ayıklayıcı tarafından başlatılan Visual Studio örneğinin IDE'si içinde açık olan dosyalar.

2.  Visual Studio örneğinde açık olan Çözümdeki dosyalar.

3.  Belirtilen dizinleri **ortak özellikler** / **kaynak dosyalarında Hata Ayıkla** çözüm özellikleri sayfasında. (İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve Seç'i seçin **özellikleri**. )

4.  Modülün .pdb dosyasının kaynak bilgisi. Bu, modül oluşturulduğunda kaynak dosyanın konumu olabileceği gibi, bir kaynak sunucuya ilişkin komut da olabilir.

###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Kaynak dosyalarını içeren kaynak bilip / yüklü sembol yok sayfaları
 Hata ayıklayıcı kaynak dosyasının olmadığı yerde yürütmeyi keserse, görüntüler **yüklü kaynak yok** veya **yüklü sembol yok** yardımcı olabilecek sayfaları kaynak dosyasını bulmaya. **Yüklü sembol yok** hata ayıklayıcı, arama işlemini tamamlamak üzere yürütülebilir dosya için bir simge (.pdb) dosyası bulamadığında görünür. Sembol Yok sayfası dosyayı aramak için seçenekler sağlar. Seçeneklerden birini çalıştırdıktan sonra .pdb bulunursa ve hata ayıklayıcı semboller dosyasındaki bilgileri kullanarak kaynak dosyayı alırsa, kaynak görüntülenir. Aksi takdirde, bir **yüklü kaynak yok** sorunu açıklayan sayfası görüntülenir. Sayfa, sorunu giderebilecek eylemleri gerçekleştirebilen seçenek bağlantıları görüntüler.

###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Kaynak dosyası arama yollarını çözüme ekleme
 Kaynak dosyalarını aramak için ağ veya yerel dizin belirtebilirsiniz.

1. Çözüm Gezgini içindeki çözümü seçin ve ardından **özellikleri** kısayol menüsünden.

2. Altında **ortak özellikler** düğümünü seçin **kaynak dosyalarında Hata Ayıkla**.

3. Klasörü tıklatın ![Araçları&#47; seçenekleri&#47; hata ayıklama&#47;sembolleri klasör simgesini](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") simgesi. Düzenlenebilir metin görünür **kaynak kodu içeren dizinler** listesi.

4. Aramak istediğiniz yolu ekleyin.

   Yalnızca belirtilen dizin arandığına dikkat edin. Arama yapmak istediğiniz alt dizinler için girdi eklemeniz gerekir.

###  <a name="BKMK_Use_source_servers"></a> Kaynak sunucuları kullanma
 Yerel makinede kaynak kod olmadığında veya .pdb dosyası kaynak kodla eşleşmediğinde, uygulamada hata ayıklamaya yardımcı olması için Kaynak Sunucuyu kullanabilirsiniz. Kaynak Sunucu, dosya isteklerini alır ve gerçek dosyaları döndürür. Kaynak Sunucu, srcsrv.dll adlı bir DLL dosyası ile çalışır. Kaynak Sunucu, kaynak kodu depodan almak için kullanılan komutların yanı sıra kaynak kodu deposuna işaretçiler içeren uygulamanın .pdb dosyasını okur. devenv.exe ve srcsrv.dll ile aynı dizine konması gereken srcsrv.ini adlı dosyadaki izin verilen komutları listeleyerek hangi komutlara uygulamanın .pdb dosyasından yürütülmesini izin verileceğini sınırlayabilirsiniz.

> [!IMPORTANT]
>  Rastgele komutlar uygulamanın .pdb dosyasına katıştırılabildiğinden yalnızca yürütmek istediğiniz komutları srcsrv.ini dosyasına koyduğunuzdan emin olun. srcsvr.ini dosyasında olmayan bir komutu yürütme girişimi, bir onay iletişim kutusunun görüntülenmesine neden olur. Daha fazla bilgi için [güvenlik uyarısı: hata ayıklayıcı gerekir yürütme güvenilmeyen komut](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlara dikkat edin. Örneğin, cmd.exe'ye güvendiyseniz, kötü niyetli bir kullanıcı, komutu tehlikeli duruma getirecek parametreler belirtebilir.

 **Bir kaynak sunucusunun kullanımını etkinleştirmek için**

1.  Önceki bölümde açıklanan güvenlik önlemleri ile derlediğinizden emin olun.

2.  Üzerinde **Araçları** menüsünde seçin **seçenekleri**.

     **Seçenekleri** iletişim kutusu görüntülenir.

3.  İçinde **hata ayıklama** düğümünü seçin **genel**.

4.  Seçin **kaynak sunucusu desteğini etkinleştir** onay kutusu.

     ![Kaynak sunucu seçenekleri etkinleştirme](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

5.  (İsteğe bağlı) İstediğiniz alt seçeneği belirleyin.

     Unutmayın hem **kısmi güven derlemeleri (sadece yönetilen) için kaynak sunucuya izin ver** ve **her zaman sormadan güvenilmeyen kaynak sunucu komutlarını Çalıştır** yukarıda açıklanan güvenlik risklerini artırabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 2012 ve 2013 değişiklikleri yükleme .NET uzaktan sembolü](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)
