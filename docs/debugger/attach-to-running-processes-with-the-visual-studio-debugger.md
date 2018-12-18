---
title: Hata ayıklayıcısı ile çalıştırma işlemleri iliştirme | Microsoft Docs
ms.custom: seodec18
ms.date: 09/27/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07ed9670795e11b0d98b3703445450b468a93aa8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068467"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile çalıştırma işlemleri iliştirme
Visual Studio hata ayıklayıcı bir yerel veya uzak bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalışmaya başladıktan sonra seçin **hata ayıklama** > **iliştirme** veya basın **Ctrl**+**Alt** + **P** Visual Studio ve kullanım **iliştirme** işleme hata ayıklayıcı için iletişim kutusu.

Kullanabileceğiniz **iliştirme** yerel veya uzak bilgisayarlarda çalışan uygulamalarında hata ayıklamak için aynı anda birden çok işlemde hata ayıklamak, hata ayıklama Visual Studio'da oluşturulmamış uygulamaları veya Visual Studio'dan başlamadı herhangi bir uygulamayı hata ayıklama hata ayıklayıcısı ekli. Örneğin, hata ayıklayıcı olmadan bir uygulama çalıştırıyorsanız ve özel durumu ise, sonra uygulama çalışan işlemi için hata ayıklayıcının ve hata ayıklama başlayın.

Visual Studio temel hata ayıklama hakkında daha fazla bilgi için bkz: [hata ayıklayıcısını kullanmaya başlama](../debugger/getting-started-with-the-debugger.md).

> [!TIP]
> Emin değilim kullanıp kullanmayacağınızı **iliştirme** hata ayıklama senaryonuz için? Bkz: [yaygın hata ayıklama senaryoları](#BKMK_Scenarios). 

##  <a name="BKMK_Attach_to_a_running_process"></a> Yerel makinenizde çalışan bir işleme iliştirin  

Hızlı bir şekilde bağlı için daha önce bir İliştir için bkz: [bir İliştir](#BKMK_reattach). 

Uzak bilgisayarda bir işlemde hata ayıklamak için bkz: [uzak bilgisayardaki bir işleme iliştirin](#BKMK_Attach_to_a_process_on_a_remote_computer).

**Yerel bilgisayarınızda bir işleme iliştirmek için:**  

1. Visual Studio'da **hata ayıklama** > **iliştirme** (veya basın **Ctrl**+**Alt** + **P**) açmak için **iliştirme** iletişim kutusu.
  
   **Bağlantı türü** ayarlanmalıdır **varsayılan**. **Bağlantı hedefi** , yerel makine adı olmalıdır. 
  
   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
2. İçinde **kullanılabilir işlemler** listesinde, bulmak ve işlem ya da eklemek istediğiniz işlemleri seçin.  

   - Bir işlemi hızlı bir şekilde seçmek için adını veya ilk harfini yazın **filtreleme işlemleri** kutusu. 
  
   - İşlem adını bilmiyorsanız, listede göz atın veya bakın [yaygın hata ayıklama senaryoları](#BKMK_Scenarios) için bazı ortak işlem adları. 
  
   >[!TIP]
   >İşlemler başlatabilir ve durdurabilirsiniz arka planda **iliştirme** iletişim kutusu açıkken, böylece çalışan işlemlerin listesi her zaman geçerli olmayabilir. Seçebileceğiniz **Yenile** geçerli listesini görmek için herhangi bir zamanda. 
  
3. İçinde **ekleme** alan, hata ayıklama planladığınız kodun türünü listelendiğinden emin olun. Varsayılan **otomatik** works çoğu uygulama türleri için ayarlama. 
  
   Kod türleri el ile seçmek için:
   1. Tıklayın **seçin**. 
   1. İçinde **kod türünü seç** Seç iletişim kutusunda **bu tür kodlarda hata ayıklama**.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. Seçin **Tamam**.
  
4. Seçin **ekleme**.
  
>[!NOTE]
>Hata ayıklama için birden fazla uygulama için bağlı, ancak bir kerede yalnızca bir uygulama hata ayıklayıcıda etkin olur. Visual Studio'da etkin uygulaması ayarlayabilirsiniz **hata ayıklama konumu** araç veya **işlemleri** penceresi.  

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Uzak bilgisayardaki bir işleme ekleme  

Uzak bir bilgisayarda da seçebilirsiniz **iliştirme** iletişim kutusunda, bu bilgisayar üzerinde çalışan kullanılabilir süreçlerin listesini görüntüleyebilir ve bir veya daha fazla hata ayıklama için ekleyebilirsiniz. Uzaktan hata ayıklayıcı (*msvsmon.exe*) uzak bilgisayar üzerinde çalışıyor olması gerekir. Daha fazla bilgi için [uzaktan hata ayıklama](../debugger/remote-debugging.md). 

IIS'ye dağıtılan ASP.NET uygulamalarında hata ayıklama için daha eksiksiz yönergeler için bkz: [uzak bir IIS bilgisayarında ASP.NET hata ayıklama uzak](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Uzak bir bilgisayarda çalışan bir işleme iliştirmek için:**  

1. Visual Studio'da **hata ayıklama** > **iliştirme** (veya basın **Ctrl**+**Alt** + **P**) açmak için **iliştirme** iletişim kutusu.
  
2. **Bağlantı türü** olmalıdır **varsayılan** çoğu durum için. İçinde **bağlantı hedefi** kutusunda, aşağıdaki yöntemlerden birini kullanarak uzak bilgisayarı seçin:

   - Aşağı açılan oku seçin **bağlantı hedefi**, aşağı açılan listeden bilgisayar adını seçin.  
   - Bilgisayar adını yazın **bağlantı hedefi** kutusu.
      
     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsa, IP kullanmayı deneyin ve bağlantı noktası adresi (örneğin, `123.45.678.9:4022`). 4022 x64 Visual Studio 2017 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları konusuna bakın [uzaktan hata ayıklayıcı bağlantı noktası atamaları](remote-debugger-port-assignments.md).  
      
   - Seçin **Bul** düğmesinin yanındaki **bağlantı hedefi** açılacak kutusuna **uzak bağlantıları** iletişim kutusu. **Uzak bağlantıları** iletişim kutusu, yerel alt ağda veya bilgisayarınıza doğrudan bağlı tüm cihazları listeler. Gerekebilir [açın UDP bağlantı noktası 3702](../debugger/remote-debugger-port-assignments.md) uzak cihazları bulmak için sunucuda. Bilgisayarı veya cihazı ve ardından seçin **seçin**. 
  
   > [!NOTE]
   > **Bağlantı türü** ayarı, hata ayıklama oturumları arasında devam ettirir. **Bağlantı hedefi** ayarı, başarılı bir hata ayıklama bağlantı hedefleyen ile oluşursa hata ayıklama oturumları arasında devam ettirir.

3. Tıklayın **Yenile** doldurmak için **kullanılabilir işlemler** listesi.
     
    >[!TIP]
    >İşlemler başlatabilir ve durdurabilirsiniz arka planda **iliştirme** iletişim kutusu açıkken, böylece çalışan işlemlerin listesi her zaman geçerli olmayabilir. Seçebileceğiniz **Yenile** geçerli listesini görmek için herhangi bir zamanda. 
     
4. İçinde **kullanılabilir işlemler** listesinde, bulmak ve işlem ya da eklemek istediğiniz işlemleri seçin.  

   - Bir işlemi hızlı bir şekilde seçmek için adını veya ilk harfini yazın **filtreleme işlemleri** kutusu. 
  
   - İşlem adını bilmiyorsanız, listede göz atın veya bakın [yaygın hata ayıklama senaryoları](#BKMK_Scenarios) için bazı ortak işlem adları. 
  
   - Tüm kullanıcı hesapları altında çalışan işlemleri bulmak için seçin **tüm kullanıcıların işlemlerini göster** onay kutusu.
      
     >[!NOTE]
     >Güvenilmeyen bir kullanıcı tarafından sahip olunan bir işlem eklemeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görünecektir. Daha fazla bilgi için [güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
      
5. İçinde **ekleme** alan, hata ayıklama planladığınız kodun türünü listelendiğinden emin olun. Varsayılan **otomatik** works çoğu uygulama türleri için ayarlama. 
  
   Kod türleri el ile seçmek için:
   1. Tıklayın **seçin**. 
   1. İçinde **kod türünü seç** Seç iletişim kutusunda **bu tür kodlarda hata ayıklama**.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. Seçin **Tamam**.
  
6. Seçin **ekleme**.
  
>[!NOTE]
>Hata ayıklama için birden fazla uygulama için bağlı, ancak bir kerede yalnızca bir uygulama hata ayıklayıcıda etkin olur. Visual Studio'da etkin uygulaması ayarlayabilirsiniz **hata ayıklama konumu** araç veya **işlemleri** penceresi.  

Bazı durumlarda, bir Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıkladığınızda **kullanılabilir işlemler** listesi kullanılabilir tüm işlemleri olmaz. Visual Studio sınırlı bir kullanıcı hesabı olan bir kullanıcı çalıştırıyorsanız, **kullanılabilir işlemler** listelemek 0 oturumunda çalışan işlemler olmaz. 0 oturumu Hizmetleri ve dahil olmak üzere diğer sunucu işlemleri için kullanılan *w3wp.exe*. Çalıştırarak sorunu çözebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir yönetici hesabı altında ya da çalıştırarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Terminal Hizmetleri oturumu yerine sunucu konsolundan. 

Bu geçici çözümlerden biri Mümkünse, üçüncü seçenek olmasına çalıştırarak işleme iliştirmek `vsjitdebugger.exe -p <ProcessId>` Windows komut satırından. İşlem kimliğini kullanarak belirleyebilirsiniz *tlist.exe*. Edinme *tlist.exe*indir ve hata ayıklama araçları için Windows, kullanılabilir yükleme [WDK ve WinDbg yüklemeleri](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_reattach"></a> Bir İliştir

Hızlı, daha önce seçerek eklendiği işlemlere iliştirebilirsiniz **hata ayıklama** > **İliştir** (**Shift** + **Alt**+**P**). Bu komutu seçtiğinizde, son ilk önceki işlem kimliğini deneyerek bağlı işlemler iliştirmek hata ayıklayıcı hemen deneyecek ve bu, önceki eşleştirerek başarısız olursa adı işleyin. Herhangi bir eşleşme bulunursa veya çeşitli işlemlerin aynı ada sahipse **iliştirme** doğru işlemi seçebilmeniz için iletişim kutusu açılır.

> [!NOTE]
> **İliştir** komutu Visual Studio 2017'de yenidir.

## <a name="BKMK_Scenarios"></a> Hata ayıklama senaryoları

Kullanılıp kullanılmayacağını belirlemenize yardımcı olmak üzere **iliştirme** ve hangi işlemin, aşağıdaki tabloda, daha fazla bilgi için bağlantılarla birlikte bazı yaygın hata ayıklama senaryoları gösterilmektedir. mevcut olduğunda ekleme. (Bu liste kapsamlı değildir.) 

Evrensel Windows uygulamasında (UWP) uygulamaları gibi bazı uygulama türleri için doğrudan bir işlem adı iliştirme ancak kullanın **yüklenen uygulama paketinin hatalarını ayıklama** menü seçeneğini Visual Studio'da yerine (tabloya bakın).

C++ programında yazılan koda eklenmesi hata ayıklayıcı için kod yayması gerekir `DebuggableAttribute`. Bu, kodunuzu otomatik olarak ile bağlayarak ekleyebileceğiniz [assemblydebug](/cpp/build/reference/assemblydebug-add-debuggableattribute) bağlayıcı seçeneği.

İstemci tarafı betik hata ayıklama için betik hata ayıklamasını tarayıcıda etkinleştirilmelidir. Chrome üzerinde istemci tarafı betikte hata ayıklama için seçin **Webkit** kod türü ve uygulama türüne bağlı olarak, tüm Chrome örneklerini kapatın ve hata ayıklama modu tarayıcı başlatmak gerekebilir (tür `chrome.exe --remote-debugging-port=9222` komut satırından).

Hızlı bir şekilde çalışan bir işleme eklemek, Visual Studio'da seçmek için türü **Ctrl**+**Alt**+**P**, ilk harflerini yazın işlem adı.

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|Uzaktan hata ayıklama ASP.NET 4 veya 4.5 üzerinde bir IIS sunucusu|Uzak Araçlar'ı kullanın ve **iliştirme**|*W3wp.exe*|Bkz: [uzaktan uzak bir IIS bilgisayarında ASP.NET hata ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Uzaktan hata ayıklamayı ASP.NET Core IIS sunucusu|Uzak Araçlar'ı kullanın ve **iliştirme**|*dotnet.exe*|Uygulama dağıtımı için bkz: [IIS Yayımla](https://docs.asp.net/en/latest/publishing/iis.html). Hata ayıklama için bkz: [uzak bir IIS bilgisayarda uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Desteklenen uygulama türleri için yerel bir IIS sunucusunda istemci tarafı betikte hata ayıklama |Kullanım **işleme**|*Chrome.exe*, *MicrosoftEdgeCP.exe*, veya *iexplore.exe*|Komut dosyası hata ayıklaması etkinleştirilmelidir. Chrome için ayrıca Chrome seçin ve hata ayıklama modu çalıştırmalısınız **Webkit kod** içinde **ekleme** alan.|
|Yerel makinede bir C#, Visual Basic veya C++ uygulamasında hata ayıklama|Hangisini [standart hata ayıklama](../debugger/getting-started-with-the-debugger.md) veya **iliştirme**|*\<Appname > .exe*|Çoğu senaryoda, standart hata ayıklama kullanın ve **iliştirme**.|
|Uzaktan hata ayıklama bir Windows masaüstü uygulaması|Uzak Araçlar|Yok| Bkz: [uzaktan hata ayıklama, C# veya Visual Basic uygulama](../debugger/remote-debugging-csharp.md) veya [uzaktan hata ayıklama, C++ uygulama](../debugger/remote-debugging-cpp.md)|
|Hata Ayıklayıcı olmadan uygulamayı başlattıktan sonra yerel makine üzerinde bir ASP.NET uygulamasında hata ayıklama|Kullanım **işleme**|*iiexpress.exe*|Bu yük uygulamanızı hale getirmek yardımcı olabilecek daha hızlı gibi (örneğin) profili oluşturulurken. |
|Başka bir sunucu işlemi desteklenen uygulama türlerinde hata ayıklama|Sunucu uzak ise, uzak Araçlar kullanın ve **iliştirme**|*Chrome.exe*, *iexplore.exe*, veya diğer işlemler|Gerekirse, Kaynak İzleyicisi işlemi belirlemenize yardımcı olması için kullanın. Bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md).|
|Uzaktan hata ayıklama, bir evrensel Windows uygulamasında (UWP), OneCore, HoloLens ve IOT uygulaması|Yüklenen uygulama paketinin hatalarını ayıklama|Yok|Bkz: [yüklü uygulama paketinin hatalarını ayıklama](debug-installed-app-package.md) kullanmak yerine **iliştirme**|
|Visual Studio'dan başlatmamış bir evrensel Windows uygulamasında (UWP), OneCore, HoloLens ve IOT uygulamasında hata ayıklama|Yüklenen uygulama paketinin hatalarını ayıklama|Yok|Bkz: [yüklü uygulama paketinin hatalarını ayıklama](debug-installed-app-package.md) kullanmak yerine **iliştirme**|  
  
## <a name="use-debugger-features"></a>Debugger özelliklerini kullanma

Visual Studio hata ayıklayıcı (kesme noktalarının isabet etmesi gibi) tam özelliklerini kullanmak için bir işleme iliştirirken uygulama tam olarak yerel kaynak ve simgeleri eşleşmelidir. Diğer bir deyişle, hata ayıklayıcı doğru yüklemek gereken [sembol (.pdb) dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Varsayılan olarak, bu hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryoları için Visual Studio'da açık kaynak kodu (veya kaynak kodu bir kopyasını) sahip olmalıdır. Derlenmiş uygulama ikili dosyalarını uzak makinede gibi yerel makinede aynı derlemeden gelmelidir.

Uygulamayı doğru sembol dosyaları varsa bazı yerel hata ayıklama senaryolarında, Visual Studio'da kaynağına erişimi olmayan hata ayıklaması yapabilirsiniz. Varsayılan olarak, bu hata ayıklama derlemesi gerektirir. Daha fazla bilgi için [sembol ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> Sorun giderme hataları iliştirme  
 Çalışan bir işleme hata ayıklayıcı ekler, işlemi bir veya daha fazla kod türlerini içerebilir. Hata ayıklayıcının iliştirebileceği kod türleri görüntülenir ve seçili **kod türünü seç** iletişim kutusu.  
  
 Bazen, hata ayıklayıcı başarıyla bir kod türüne, ancak başka bir kod türüne ekleyebilirsiniz. Uzak bir bilgisayarda çalışan bir işlem eklemeye çalışıyorsanız, bu durum oluşabilir. Uzak bilgisayarda uzaktan hata ayıklama bileşenleri belirli kod türleri için kullanılabilir ancak diğerleri yüklü olabilir. Doğrudan veritabanı hata ayıklamaya iki veya daha fazla işlem eklemeye çalışırsanız da meydana gelebilir. SQL hata ayıklama için yalnızca tek bir işlem eklemeyi destekler.  
  
 Hata ayıklayıcı, ancak bazı değil tüm kod türlerine eklenebiliyorsa, hangi türlerin eklenemediğini tanımlayan bir ileti görürsünüz.  
  
 Hata ayıklayıcı en az bir kod türüne başarıyla ekleniyorsa işlemin hatalarını ayıklamaya devam edebilirsiniz. Sadece başarıyla eklenen kod türlerinde hata ayıklama mümkün olacaktır. İşlem eklenmemiş kodu hala çalışır, ancak kesme noktaları ayarlayın, veri görüntüleyemez veya kod hata ayıklama diğer işlemleri mümkün olmayacaktır.  
  
 Hata ayıklayıcının bir kod türünü başarısız olma nedenine ilişkin daha ayrıntılı bilgi isterseniz, yalnızca bu kod türüne yeniden deneyin.  
  
 **Neden bir kod türü eklemenin başarısız hakkında ayrıntılı bilgi edinmek için:**  
  
1.  İşlemden ayırın. Üzerinde **hata ayıklama** menüsünde **tümünü Ayır**.  
  
1.  Eklenemeye kod türü seçerek işleme yeniden bağlayın.  
  
    1.  İçinde **iliştirme** iletişim kutusunda, işlemi seçin **kullanılabilir işlemler** listesi.  
  
    2.  Seçin **seçin**.  
  
    3.  İçinde **kod türünü seç** Seç iletişim kutusunda **bu tür kodlarda hata ayıklama** ve eklenemeye kod türü. Diğer kod türleri seçimini kaldırın.  
  
    4.  Seçin **Tamam**.  
  
    5.  İçinde **iliştirme** iletişim kutusunda **iliştirme**.  
  
    Bu kez, iliştirme tümüyle başarısız olur ve belirli bir hata iletisi alırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)   
 [Just-In-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
 