---
title: Hata ayıklayıcısı ile çalıştırma işlemleri iliştirme | Microsoft Docs
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
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d439f0b13c0284d203c917c748b178c6d443220a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056648"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio Hata Ayıklayıcısı ile Çalıştırma İşlemleri İliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı bir yerel veya uzak bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalışmaya başladıktan sonra tıklayın **hata ayıklama / iliştirme** (veya basın **CTRL + ALT + P**) açmak için **iliştirme** iletişim kutusu.

Bu özellik, bir yerel veya uzak bilgisayarda çalışan uygulamaların hata ayıklama, aynı anda birden çok işlemde hata ayıklama veya Visual Studio'da oluşturulmamış bir uygulamada hata ayıklamak için kullanabilirsiniz. Bir uygulamanın hatalarını ayıklamak istediğiniz zaman çoğunlukla yararlı olur ancak (herhangi bir nedenle), başlamadı uygulamayı Visual Studio'dan hata ayıklayıcısı ekli. Örneğin, hata ayıklayıcı olmadan uygulamayı çalıştırdığınız ve bir özel durum oluştu, hata ayıklamayı başlatmak için uygulama çalışan işlemi için daha sonra iliştirin.

> [!TIP]
> Emin değil mi ihtiyacınız kullanılacak **iliştirme** hata ayıklama senaryonuz için? Bkz: [yaygın hata ayıklama senaryoları](#BKMK_Scenarios). IIS'ye dağıtılan, bkz: ASP.NET uygulamalarında hata ayıklamak istiyorsanız [uzak bir IIS bilgisayarda uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a> Yerel makinede çalışan bir işleme iliştirin
 Bir işleme iliştirmek için işlemin adını bilmeniz gerekir (bkz [yaygın hata ayıklama senaryoları](#BKMK_Scenarios) birkaç ortak işlem adları için).

1.  Visual Studio'da **hata ayıklama / iliştirme** (veya basın **CTRL + ALT + P**).

2.  İçinde **iliştirme** iletişim kutusunda, iliştirmek istediğiniz programı bulun **kullanılabilir işlemler** listesi.

     İstediğiniz işlemi hızla seçmek için işlem adı ilk harflerini yazın. İşlem adını bilmiyorsanız, bkz. [yaygın hata ayıklama senaryoları](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     İşlemi farklı bir kullanıcı hesabı altında çalışıyorsa, seçin **tüm kullanıcıların işlemlerini göster** onay kutusu.

3.  İçinde **ekleme** kutusunda, hata ayıklama kodun türünü listelendiğinden emin olun. Varsayılan **otomatik** ayarı, hata ayıklamak istediğiniz kod türünü belirlemeye çalışır. Kod türünü el ile ayarlamak için aşağıdakileri yapın

    1.  İçinde **ekleme** kutusunun **seçin**.

    2.  İçinde **kod türünü seç** iletişim kutusu, tıklayın **bu tür kodlarda hata ayıklama** ve ayıklanacak türleri seçin.

    3.  **Tamam**'ı tıklatın.

4.  Tıklayın **ekleme**.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Uzak bilgisayardaki bir işleme ekleme
 Bir işleme iliştirmek için işlemin adını bilmeniz gerekir (bkz [yaygın hata ayıklama senaryoları](#BKMK_Scenarios) birkaç ortak işlem adları için). IIS'ye dağıtılan ASP.NET uygulamaları için daha eksiksiz yönergeler için bkz. [uzak bir IIS bilgisayarda uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Diğer uygulamalar için Görev Yöneticisi'nde işleminin adını bulma mümkün olabilir.

 Kullanırken **iliştirme** iletişim kutusunda, uzaktan hata ayıklama için ayarlanmış başka bir bilgisayara seçebilirsiniz. Daha fazla bilgi için [uzaktan hata ayıklama](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Bir uzak bilgisayar seçtiğinizde, bu bilgisayar üzerinde çalışan kullanılabilir süreçlerin listesini görüntüleyebilir ve bir veya daha fazla hata ayıklama için iliştirin.

 **Bir uzak bilgisayar seçmek için:**

1. Visual Studio'da **hata ayıklama / iliştirme** (veya basın **CTRL + ALT + P**).

2. İçinde **iliştirme** uygun bağlantı türünü iletişim kutusunda **aktarım** listesi. **Varsayılan** çoğu durum için doğru ayardır.

   **Aktarım** ayarı, hata ayıklama oturumları arasında devam ettirir.

3. Kullanım **niteleyicisi** liste kutusunda, aşağıdaki yöntemlerden birini kullanarak uzak bilgisayar adını seçmek için:

   1. Adı yazın **niteleyicisi** liste kutusu.

      >**Not** sonraki adımlarda, uzak bilgisayar adını kullanarak bağlanamazsa, IP adresini kullanın. (Bağlantı noktası numarasını otomatik olarak işlem seçtikten sonra görünebilir. Da onu el ile girebilirsiniz. Aşağıdaki çizimde, 4020 uzaktan hata ayıklayıcı için varsayılan bağlantı noktası var.)

   2. Eklenmiş açılan oku tıklatın **niteleyicisi** liste kutusu ve aşağı açılan listeden bilgisayar adını seçin.

   3. Tıklayın **Bul** düğmesinin yanındaki **niteleyicisi** listesini açmak için **uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu. **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu, yerel alt ağınız tüm cihazları ve Ethernet kablosu ile bilgisayarınıza doğrudan bağlı herhangi bir CİHAZDAN listeler. ' A tıklayın ve ardından cihaz ve bilgisayar **seçin**.

      **Niteleyicisi** ayarını, yalnızca bu niteleyici ile başarılı bir hata ayıklama bağlantısı oluşursa hata ayıklama oturumları arasında devam ettirir.

4. Tıklayın **Yenile**.

     **Kullanılabilir işlemler** listesi açıldığında otomatik olarak görüntüleniyor **işlemleri** iletişim kutusu. İşlemler başlatabilir ve iletişim kutusu açıkken arka planda durdurabilirsiniz. Ancak, içeriği her zaman geçerli değildir. Listeden tıklayarak işlemlerin geçerli listesini görmek için herhangi bir zamanda yenileyebilirsiniz **Yenile**.

5. İçinde **iliştirme** iletişim kutusunda, iliştirmek istediğiniz programı bulun **kullanılabilir işlemler** listesi.

    İşlemi farklı bir kullanıcı hesabı altında çalışıyorsa, seçin **tüm kullanıcıların işlemlerini göster** onay kutusu.

6. Tıklayın **ekleme**.

## <a name="additional-info"></a>Ek bilgi

Birden çok programları için hata ayıklama, ancak herhangi bir anda yalnızca bir programı hata ayıklayıcıda etkin eklenebilir. Etkin programı ayarlayabilirsiniz **hata ayıklama konumu** araç veya **işlemleri** penceresi. Daha fazla bilgi için [nasıl yapılır: geçerli programı ayarlama](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Güvenilmeyen bir kullanıcı tarafından sahip olunan bir işlem eklemeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görünecektir. Daha fazla bilgi için [güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).

Bazı durumlarda, bir Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıkladığınızda **kullanılabilir işlemler** listesi kullanılabilir tüm işlemleri görüntülemez. Visual Studio sınırlı bir kullanıcı hesabı olan bir kullanıcı çalıştırıyorsanız, **kullanılabilir işlemler** Hizmetleri ve w3wp.exe dahil olmak üzere diğer sunucu işlemleri için kullanılan oturum 0'da çalışan işlemler listesi gösterilmez. Çalıştırarak sorunu çözebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir yönetici hesabı altında ya da çalıştırarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Terminal Hizmetleri oturumu yerine sunucu konsolundan. Bu geçici çözümlerden biri Mümkünse, üçüncü seçenek olmasına çalıştırarak işleme iliştirmek `vsjitdebugger.exe -p` *ProcessId* Windows komut satırından. Tlist.exe kullanarak işlem kimliğini belirleyebilirsiniz. Tlist.exe'yi edinmek için indirme ve hata ayıklama araçları için Windows, kullanılabilir yükleme [WDK ve WinDbg yüklemeleri](http://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a> Hata ayıklama senaryoları

Kullanılacak gerekip gerekmediğini belirlemenize yardımcı olması için **iliştirme** ve hangi işlemin eklemek, burada gösterilen bazı yaygın hata ayıklama senaryoları (Bu liste kapsamlı değildir). Daha fazla yönerge kullanılabiliyorsa, bağlantılar sağlıyoruz.

Bazı uygulama türlerini (örneğin, Windows Store apps) için doğrudan bir işlem adı iliştirme ancak kullanın **yüklenen uygulama paketinin hatalarını ayıklama** menü seçeneği yerine (tabloya bakın).

> [!NOTE]
> Visual Studio temel hata ayıklama hakkında daha fazla bilgi için bkz: [hata ayıklayıcısını kullanmaya başlama](../debugger/getting-started-with-the-debugger.md).

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|Yerel makinede bir yönetilen veya yerel uygulamasında hata ayıklama|Kullanım iliştirme veya [standart hata ayıklama](../debugger/getting-started-with-the-debugger.md)|*Appname*.exe|Hızlı bir şekilde iletişim kutusuna erişmek için **CTRL + ALT + P** işlem adının ilk harfi yazın.|
|Hata Ayıklayıcı olmadan uygulamayı başlattıktan sonra yerel makinede uygulamaları ASP.NET hata ayıklama|Kullanım iliştirme|iiexpress.exe|Bu yük uygulamanızı hale getirmek yardımcı olabilecek daha hızlı gibi (örneğin) profili oluşturulurken. |
|Uzaktan hata ayıklama ASP.NET 4 veya 4.5 üzerinde bir IIS sunucusu|Uzak Araçlar'ı kullanın ve işleme|W3wp.exe|Bkz: [uzak bir IIS bilgisayarda uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Uzaktan hata ayıklamayı ASP.NET Core IIS sunucusu|Uzak Araçlar'ı kullanın ve işleme|dnx.exe|Uygulama dağıtımı için bkz: [IIS Yayımla](https://docs.asp.net/en/latest/publishing/iis.html). Hata ayıklama için bkz: [uzak bir IIS bilgisayarda uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Başka bir sunucu işlemi desteklenen uygulama türlerinde hata ayıklama|Uzak Araçlar (sunucu uzaktaysa) kullanın ve işleme|iexplore.exe veya diğer işlemler|Gerekirse, işlem belirlemenize yardımcı olması için Görev Yöneticisi'ni kullanın. Bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md) ve bu konunun sonraki bölümlerinde|
|Uzaktan hata ayıklama bir Windows masaüstü uygulaması|Uzak Araçlar ve F5|Yok| Bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Uzaktan hata ayıklama, bir Windows Evrensel (UWP), OneCore, HoloLens ve IOT uygulaması|Yüklenen uygulama paketinin hatalarını ayıklama|Yok|Kullanım **hata ayıklama / diğer hata ayıklama hedefleri / yüklenen uygulama paketinin hatalarını ayıklama** yerine **iliştirme**|
|Visual Studio'dan başlatmamış bir Windows Evrensel (UWP), OneCore, HoloLens ve IOT uygulamasında hata ayıklama|Yüklenen uygulama paketinin hatalarını ayıklama|Yok|Kullanım **hata ayıklama / diğer hata ayıklama hedefleri / yüklenen uygulama paketinin hatalarını ayıklama** yerine **iliştirme**|

> [!WARNING]
>  JavaScript'te yazılmış bir Windows Evrensel uygulaması iliştirmek için önce uygulama için hata ayıklamayı etkinleştirmeniz gerekir. Bkz: [hata ayıklayıcının](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) Windows geliştirme Merkezi'nde.

> [!NOTE]
>  C++ programında yazılan koda eklenmesi hata ayıklayıcı için kod yayması gerekir `DebuggableAttribute`. Bu, kodunuzu otomatik olarak ile bağlayarak ekleyebileceğiniz [assemblydebug](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) bağlayıcı seçeneği.

## <a name="what-debugger-features-can-i-use"></a>Hangi hata ayıklayıcısı özellikleri kullanabilir miyim?

Visual Studio hata ayıklayıcı (kesme noktalarının isabet etmesi gibi) tam özelliklerini kullanmak için bir işleme iliştirirken yürütülebilir dosyanın tam olarak yerel kaynak ve simgeleri eşleşmelidir (diğer bir deyişle, hata ayıklayıcı doğru yüklemek gereken [sembol (.pbd) dosyaları ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Varsayılan olarak, bu hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryoları için Visual Studio'da açık kaynak kodu (veya kaynak kodu bir kopyasını) sahip olmalıdır. Derlenmiş uygulama ikili dosyalarını uzak makinede gibi yerel makinede aynı derlemeden gelmelidir.

Uygulamayı doğru sembol dosyaları varsa bazı yerel hata ayıklama senaryolarında, Visual Studio'da kaynağına erişimi olmayan hata ayıklaması yapabilirsiniz (varsayılan olarak, bu, hata ayıklama derlemesi'gerektirir). Daha fazla bilgi için bkz. [belirtin, sembol ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

##  <a name="BKMK_Troubleshoot_attach_errors"></a> Sorun giderme hataları iliştirme
 Çalışan bir işleme hata ayıklayıcı ekler, işlemi bir veya daha fazla kod türlerini içerebilir. Hata ayıklayıcının iliştirebileceği kod türleri görüntülenir ve seçili **kod türünü seç** iletişim kutusu.

 Bazen, hata ayıklayıcı başarıyla bir kod türüne, ancak başka bir kod türüne ekleyebilirsiniz. Uzak bir bilgisayarda çalışan bir işlem eklemeye çalışıyorsanız, bu durum oluşabilir. Uzak bilgisayarda uzaktan hata ayıklama bileşenleri belirli kod türleri için kullanılabilir ancak diğerleri yüklü olabilir. Doğrudan veritabanı hata ayıklamaya iki veya daha fazla işlem eklemeye çalışırsanız da meydana gelebilir. SQL hata ayıklama için yalnızca tek bir işlem eklemeyi destekler.

 Hata ayıklayıcı, ancak bazı değil tüm kod türlerine eklenebiliyorsa, hangi türlerin eklenemediğini tanımlayan bir ileti görürsünüz.

 Hata ayıklayıcı en az bir kod türüne başarıyla ekleniyorsa işlemin hatalarını ayıklamaya devam edebilirsiniz. Sadece başarıyla eklenen kod türlerinde hata ayıklama mümkün olacaktır. Yukarıdaki örnek ileti, komut dosyası kodu türü eklemenin başarısız olduğunu gösterir. Bu nedenle, işlem içinde komut satırı kodunda hata ayıklamanız mümkün olmaz. İşlemdeki komut dosyası kodu hala çalışır, ancak kesme noktaları ayarlayın, veri görüntüleyemez veya komut dosyasında başka hata ayıklama işlemleri gerçekleştirmek mümkün olmaz.

 Hata ayıklayıcının bir kod türünü başarısız olma nedenine ilişkin daha ayrıntılı bilgi isterseniz, yalnızca bu kod türüne yeniden deneyebilirsiniz.

 **Neden bir kod türü eklemenin başarısız hakkında ayrıntılı bilgi edinmek için**

1. İşlemden ayırın. Üzerinde **hata ayıklama** menüsünü tıklatın **tümünü Ayır**.

2. Yalnızca tek bir kod türü seçerek işleme yeniden bağlayın.

   1. İçinde **iliştirme** iletişim kutusunda, işlemi seçin **kullanılabilir işlemler** listesi.

   2. Tıklayın **seçin**.

   3. İçinde **kod türünü seç** Seç iletişim kutusunda **bu tür kodlarda hata ayıklama** ve eklenemeye kod türü. Diğer kodları temizleyin.

   4. **Tamam**'ı tıklatın. **Kod türünü seç** iletişim kutusu kapanır.

   5. İçinde **iliştirme** iletişim kutusu, tıklayın **iliştirme**.

      Bu kez, iliştirme tümüyle başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca Bkz.
 [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md) [Just-ın-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) [uzaktan hata ayıklama](../debugger/remote-debugging.md)
