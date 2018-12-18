---
title: Birden çok işlemde hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b306bcca4ac8cc0568fc609ec25c8b335d18010
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305656"
---
# <a name="debug-multiple-processes"></a>Birden çok işlemde hata ayıklama

Visual Studio, birçok işlem sahip bir çözüm ayıklayabilirsiniz. Başlatabilir ve işlemler arasında geçiş yapmak, kesme, devam etmek için ve kaynak, hata ayıklamayı Durdur ve son adımla veya bireysel işlemlerden ayırın.  

##  <a name="start-debugging-with-multiple-processes"></a>Birden çok işlem ile hata ayıklamayı Başlat 

Visual Studio çözümünde birden fazla proje bağımsız olarak çalıştırabilirsiniz, hata ayıklayıcıyı başlatır hangi proje seçebilirsiniz. Geçerli başlangıç projesini görünür kalın **Çözüm Gezgini**. 

Başlangıç projesi değiştirmek için **Çözüm Gezgini**, farklı bir projeye sağ tıklayıp **başlangıç projesi olarak ayarla**.

Bir projeden hata ayıklamayı başlatmak için **Çözüm Gezgini** yapmadan bunu başlangıç projesi, projeye sağ tıklayıp seçin **hata ayıklama** > **yeni örnek Başlat** veya **yeni örneği içine Adımlama**. 

**Başlangıç projesi veya birden çok proje çözümü özellikleri ayarlamak için:**

1. Çözümde seçin **Çözüm Gezgini** seçip **özellikleri** simgesine araç veya çözüme sağ tıklatın ve seçin **özellikleri**.  
   
1. Üzerinde **özellikleri** sayfasında **ortak özellikler** > **başlangıç projesi**.
   
   ![Bir proje başlangıç türünün değiştirilmesi](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
   
1. Seçin **geçerli seçimi**, **tek başlangıç projesi** ve bir proje dosyası veya **birden fazla başlangıç projesi**. 

   Seçerseniz **birden fazla başlangıç projesi**, eylem ve başlatma sırası her proje için gerçekleştirilecek değiştirebilirsiniz: **Başlat**, **ayıklamadan Başlat**, veya **Hiçbiri**.  
   
1. Seçin **Uygula**, veya **Tamam** uygulamak ve iletişim kutusunu kapatın. 

###  <a name="BKMK_Attach_to_a_process"></a> Bir işleme  

Hata ayıklayıcı ayrıca *ekleme* uzak cihazlarda da dahil olmak üzere Visual Studio dışındaki işlemlerde çalışan uygulamalar için. Bir uygulamayı ekledikten sonra Visual Studio hata ayıklayıcısını kullanabilirsiniz. Hata ayıklama özelliklerinin sınırlı olabilir. Bu uygulamayı hata ayıklama bilgileri ile mi oluşturulmuş, uygulamanın kaynak koduna erişim iznine sahip olup ve JIT derleyicisine hata ayıklama bilgilerini mi takip bağlıdır.  
  
Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
**Çalışan bir işleme iliştirmek için:**  
  
1. Çalışan uygulamayla seçin **hata ayıklama** > **iliştirme**. 

   ![Ekleme işlemi iletişim kutusuna](../debugger/media/dbg_attachtoprocessdlg.png "eklemek için işlem iletişim kutusu")  
  
1. İçinde **iliştirme** iletişim kutusunda, işlemden seçin **kullanılabilir işlemler** listeleyin ve ardından **iliştirme**.  
  
>[!NOTE]
>Alt projenin aynı çözüm içinde olsa bile hata ayıklayıcı hata ayıklaması yapılmış bir işlem tarafından başlatılan bir alt işleme otomatik olarak eklemez. Bir alt işlemde hata ayıklamak için başladıktan sonra alt işleme ekleyin veya alt işlem yeni bir hata ayıklayıcı örneği başlatmak için Windows Kayıt Defteri Düzenleyicisi'ni yapılandırabilirsiniz.  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Bir işlemin hata ayıklayıcıda otomatik olarak başlatmak için Kayıt Defteri Düzenleyicisi'ni kullanın  

Bazen, başka bir işlem tarafından başlatılan bir uygulama için başlatma kodunun hatalarını ayıklamak gerekebilir. Hizmetleri ve özel kurulum eylemleri verilebilir. Hata ayıklayıcıyı başlatın ve otomatik olarak uygulamaya iliştirmek olabilir. 

1. Windows Kayıt Defteri Düzenleyicisi'ni çalıştırarak başlayın *regedit.exe*.  
   
1. Kayıt Defteri Düzenleyicisi'nde gidin **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows nt\currentversion\ımage File Execution Options**.  
  
1. Hata ayıklayıcıda başlatmak istediğiniz uygulamanın klasörünü seçin.  
   
   Uygulamayı bir alt klasör olarak listelenmiyorsa, sağ **Image File Execution Options**seçin **yeni** > **anahtar**, uygulama adı yazın. Ya da seçim ağacında, yeni anahtar sağ **Yeniden Adlandır**ve ardından uygulama adı girin. 
   
1. Yeni anahtar ağaç seçip sağ **yeni** > **dize değeri**.  
   
1. Yeni değer adını değiştirmek **yeni değer #1** için `debugger`.  
   
1. Sağ **hata ayıklayıcı** seçip **Değiştir**.  
   
   ![Düzenle iletişim kutusu dize](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "dize Düzenle iletişim kutusu")  
   
1. İçinde **dize Düzenle** iletişim kutusuna `vsjitdebugger.exe` içinde **değer verisi** kutusuna ve ardından **Tamam**.  
   
   ![Otomatik hata ayıklayıcıyı başlatmak giriş regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "otomatik hata ayıklayıcı regedit.exe giriş Başlat")  
   
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> İle birden çok işlemde hata ayıklama 
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> 

Birden çok süreçle bir uygulamanın hataları ayıklanırken, yeni, adımlama ve devam eden hata ayıklayıcı komutları varsayılan olarak tüm işlemleri etkiler. Örneğin, bir işlem bir kesme noktasında askıya alındığında, diğer tüm işlemlerin yürütmesi de askıya alınır. Yürütme komutlarının hedefleri üzerinde daha fazla denetim kazanmak için bu varsayılan davranışı değiştirebilirsiniz.  

**Bir işlem kesildiğinde tüm işlemleri askıya alınmış durumda olup olmadığını değiştirmek için:**

- Altında **Araçları** (veya **hata ayıklama**) > **seçenekleri** > **hata ayıklama** > **genel**seçin veya temizleyin **bir işlem kesildiğinde tüm işlemleri Kes** onay kutusu.  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Kesme, adım ve devam etme komutları  
  
Aşağıdaki tabloda, hata ayıklama davranışları açıklanmaktadır ne zaman komutları **bir işlem kesildiğinde tüm işlemleri Kes** onay kutusunun seçili veya seçimi:

|**komutu**|Seçili|Seçimi|  
|-|-|-|  
|**Hata ayıklama**  > **tümünü Kes**|Tüm işlemler kesilir.|Tüm işlemler kesilir.|  
|**Hata ayıklama** > **devam edin**|Tüm işlemler sürdürülür.|Tüm askıya alınan işlemler sürdürülür.|  
|**Hata ayıklama** > **adımla**, **üzerinden adımla**, veya **dışına adımla**|Geçerli işlem ilerlerken tüm işlemler çalıştırılır. <br />Ardından, tüm işlemler kesilir.|Geçerli işlem adımları. <br />Aksıda işlemler sürdürülüyor. <br />Çalışan işlemler devam ediyor.|  
|**Hata ayıklama** > **geçerli işlem içine adımla**, **geçerli işlem üzerinden adımla**, veya **geçerli işlem dışına adımla**|Yok|Geçerli işlem adımları.<br />Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|Kaynak penceresinde **kesme noktası**|Tüm işlemler kesilir.|Yalnızca kaynak pencere işlemi kesilir.|  
|Kaynak penceresinde **imlece kadar Çalıştır**<br />Kaynak pencerenin geçerli işlemde olması gerekir.|Kaynak pencere işlemleri imlece çalıştırıldığında ve sonra kesildiğinde tüm işlemler çalıştırılır.<br />Daha sonra diğer tüm işlemler kesilir.|Kaynak pencere işlemi imleç olarak çalışır.<br />Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|**İşlemler** penceresi > **kesme işlemi**|Yok|Seçili işlem kesilir.<br />Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|**İşlemler** penceresi > **devam işlemi**|Yok|Seçili işlem devam eder.<br />Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  

###  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Kaynak ve sembol (.pdb) dosyalarını bulun  
Bir işlemin kaynak koduna gitmek için hata ayıklayıcı, kaynak dosyalarına ve simge dosyalarına erişmesi. Daha fazla bilgi için [belirtin, sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
Bir işlem için dosyalara erişemiyorsanız, kullanarak gidebilirsiniz **ayrıştırılmış kodu** penceresi. Daha fazla bilgi için [nasıl yapılır: Ayrıştırılmış kod penceresini kullanma](../debugger/how-to-use-the-disassembly-window.md).  

###  <a name="BKMK_Switch_between_processes"></a> İşlemler arasında geçiş yap  

Hata ayıklama, ancak yalnızca bir işlemi belirli bir zamanda hata ayıklayıcıda etkin değilse, birden çok işleme iliştirebilirsiniz. Etkin ayarlayabilirsiniz veya *geçerli* işlemini **hata ayıklama konumu** araç veya **işlemleri** penceresi. İşlemler arasında geçiş yapmak için her iki işlem kesme modunda olması gerekir.  
  
**Hata ayıklama konumu araç çubuğundan geçerli işlemi ayarlamak için:**  
  
1. Açmak için **hata ayıklama konumu** araç, select **görünümü** > **araç çubukları** > **hata ayıklama konumu**.  
   
1. Hata ayıklama, üzerinde sırasında **hata ayıklama konumu** araç, geçerli işlemden olarak ayarlamak istediğiniz işlemi seçin **işlem** açılır.  
  
   ![İşlemler arasında geçiş](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
**İşlemler penceresinden geçerli işlemi ayarlamak için:**  
  
1. Açmak için **işlemleri** hata ayıklarken, penceresinde **hata ayıklama** > **Windows** > **işlemleri**. 

1. İçinde **işlemleri** penceresi, geçerli işlem sarı bir ok ile işaretlenir. Geçerli işlem olarak ayarlamak istediğiniz işlemi çift tıklayın.  
  
   ![İşlemler penceresi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")  

Bir işleme geçiş hata ayıklama amacıyla geçerli işlem olarak ayarlar. Hata ayıklayıcı pencerelerinde geçerli işlemin durumunu gösterir ve Adımlama komutları yalnızca geçerli işlemi etkiler.  
  
## <a name="stop-debugging-with-multiple-processes"></a>Birden çok işlem ile hata ayıklamayı Durdur  
  
Seçtiğinizde varsayılan olarak **hata ayıklama** > **hata ayıklamayı Durdur**, hata ayıklayıcı sona erer veya tüm işlemlerden ayırır. 
  
- Hata ayıklayıcıda geçerli işlem başlatıldıysa, işlem sonlandırılır.  
  
- Geçerli işleme hata ayıklayıcıyı eklediyseniz, hata ayıklayıcı işlemden ayırır ve çalışan işlemi bırakır.  
  
Visual Studio çözümünden bir işlemin hatalarını ayıklamaya başlatırsanız, sonra zaten çalışan başka bir işleme iliştirin ve ardından **hata ayıklamayı Durdur**, hata ayıklama oturumu sona erer. Visual Studio'da başlatılan işlem için bağlı işlem çalışmaya devam eder ancak sonlandırır. 

Denetlenmesine, **hata ayıklamayı Durdur** içinde tek bir işlemi etkiler **işlemleri** penceresinde, bir işlemin sağ tıklayın ve ardından seçin veya temizleyin **hata ayıklamadurdurulduğundaayırma** onay kutusu.  
  
>[!NOTE]
>**Bir işlem kesildiğinde tüm işlemleri Kes** hata ayıklayıcı seçeneği, durdurma, sonlandırma veya işlemlerden ayırma etkilemez.  
  
###  <a name="stop-terminate-and-detach-commands"></a>Durdurun, sonlandırın ve komutları Ayır  
  
Aşağıdaki tablo hata ayıklayıcıyı Durdur davranışlarını tanımlar, sonlandırın ve komutları birden çok süreçle ayırma: 

|**komutu**|**Açıklama**|  
|-|-| 
|**Hata ayıklama** > **hata ayıklamayı Durdur**|Davranış olarak değiştirilmediği sürece **işlemleri** penceresinde, hata ayıklayıcı tarafından başlatılan işlemler tarihinde sona erdi ve ekli işlemleri ayrılmasının.|  
|**Hata ayıklama** > **tümünü Sonlandır**|Tüm işlemler sonlandırılır.|  
|**Hata ayıklama** > **tümünü Ayır**|Hata ayıklayıcı tüm işlemden ayrılır.|  
|**İşlemler** penceresi > **ayırma işlemi**|Hata ayıklayıcı seçilen işlemden ayrılır.<br />Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|**İşlemler** penceresi > **sonlandırma işlemi**|Seçilen işlem sonlandırıldı.<br />Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|**İşlemler** penceresi > **hata ayıklama durdurulduğunda ayırma**|Seçili değilse **hata ayıklama** > **hata ayıklamayı Durdur** seçilen işlemden ayrılır. <br />Seçilmezse, **hata ayıklama** > **hata ayıklamayı Durdur** seçili işlemi sonlandırır. |  
## <a name="see-also"></a>Ayrıca bkz.  
 [Sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Çalıştırma işlemleri iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Hata ayıklayıcısı ile kodda gezinme](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just-In-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Çok iş parçacıklı uygulamaların hatalarını ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)