---
title: Birden çok işlemde hata ayıklama | Microsoft Docs
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
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56982a3b5c0a0d8a5cb0b682ab67b6f5eb133dd1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793054"
---
# <a name="debug-multiple-processes"></a>Birden çok işlemde hata ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şöyle işlemleri hata ayıklamayı Başlat, işlemler arasında geçiş yapmak, Kes ve yürütmeye devam et, kaynak boyunca, hata ayıklamayı Durdur ve sonlandırma işlemlerden ayırın.  
  
##  <a name="BKMK_Contents"></a> İçeriği  
 [Birden çok işlem yürütme davranışını Yapılandır](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Kaynak ve sembol (.pdb) dosyalarını bulun](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Bir VS çözümde birden çok işlem Başlat, bir işleme, bir işlemin hata ayıklayıcıda otomatik olarak Başlat](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Geçiş işlemleri, kesme ve yürütme, kaynak boyunca devam edin](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Hata ayıklamayı durdurun, sonlandırın işlemlerden ayırın](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Birden çok işlem yürütme davranışını Yapılandır  
 Birden çok işlem hata ayıklayıcısı içinde çalışırken varsayılan olarak, kesme, atlama ve durdurma hata ayıklayıcı komutları genellikle tüm işlemleri etkiler. Örneğin, bir işlem bir kesme noktasında askıya alındığında, diğer tüm işlemlerin yürütmesi de askıya alınır. Yürütme komutlarının hedefleri üzerinde daha fazla denetim kazanmak için bu varsayılan davranışı değiştirebilirsiniz.  
  
1. Üzerinde **hata ayıklama** menüsünde seçin **seçenekler ve ayarlar**.  
  
2. Üzerinde **hata ayıklama**, **genel** sayfasında, NET **bir işlem kesildiğinde tüm işlemleri Kes** onay kutusu.  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Kaynak ve sembol (.pdb) dosyalarını bulun  
 Bir işlemin kaynak koduna gitmek için hata ayıklayıcı kaynak dosyaları ve sembol dosyalarını işleminin erişim gerekir. Bkz: [sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Bir işlem için dosyalara erişemiyorsanız, ayrıştırma penceresini kullanarak gidebilirsiniz. Bkz: [nasıl yapılır: Ayrıştırılmış kod penceresini kullanma](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Bir VS çözümde birden çok işlem Başlat, bir işleme, bir işlemin hata ayıklayıcıda otomatik olarak Başlat  
  
-   [Visual Studio çözümünde birden çok işlem hata ayıklamayı Başlat](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [başlangıç projesini değiştirme](#BKMK_Change_the_startup_project) • [bir çözümde belirli bir proje başlatın](#BKMK_Start_a_specific_project_in_a_solution) • [birden çok proje başlatın bir Çözüm](#BKMK_Start_multiple_projects_in_a_solution) • [bir işleme iliştirin](#BKMK_Attach_to_a_process) • [otomatik olarak hata ayıklayıcıda bir işlem başlatma](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Alt projenin aynı çözüm içinde olsa bile hata ayıklayıcı hata ayıklaması yapılmış bir işlem tarafından başlatılan bir alt işleme otomatik olarak eklemez. Bir alt işlemde hata ayıklamak için:  
> 
> - Başlatıldıktan sonra alt işleme ekleyin.  
> 
>   veya  
>   -   Windows alt işlem hata ayıklayıcının yeni bir örneğinde otomatik olarak başlayacak şekilde yapılandırın.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Visual Studio çözümünde birden çok işlem hata ayıklamayı Başlat  
 Bağımsız olarak çalışabilen bir Visual Studio çözümünde birden fazla proje olduğunda (seçebilirsiniz, hata ayıklayıcı başladığında projeleri ayrı süreçlerde çalışan projeler).  
  
 ![Bir proje başlangıç türünün değiştirilmesi](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Başlangıç projesini değiştirme  
 Çözüm başlangıç projesi değiştirmek için Çözüm Gezgini'nde projeyi seçin ve ardından **başlangıç projesi olarak ayarla** bağlam menüsünden.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Bir çözümde belirli bir proje başlatın  
 Varsayılan başlangıç projesini değiştirmeden bir çözüm için bir proje başlatmak için Çözüm Gezgini'nde projeyi seçin ve ardından **hata ayıklama** bağlam menüsünden. Daha sonra seçebilirsiniz **yeni örnek Başlat** veya **yeni örneğe geç**.  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [bir VS çözümde birden çok işlem Başlat, bir işleme, bir işlemin hata ayıklayıcıda otomatik olarak Başlat](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Bir çözümde birden çok proje başlatın  
  
1. Çözüm Gezgini içindeki çözümü seçin ve ardından **özellikleri** bağlam menüsünde.  
  
2. Seçin **ortak özellikler**, **başlangıç projesi** üzerinde **özellikleri** iletişim kutusu.  
  
3. Değiştirmek istediğiniz her proje ya da seçin **Başlat**, **ayıklamadan Başlat**, veya **hiçbiri**.  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [bir VS çözümde birden çok işlem Başlat, bir işleme, bir işlemin hata ayıklayıcıda otomatik olarak Başlat](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Bir işleme  
 Hata ayıklayıcı ayrıca olabilir *ekleme* Visual Studio dışındaki işlemlerde çalışan programlara, uzak bir cihazta çalışan programlar da dahil olmak üzere. Bir programa ekledikten sonra hata ayıklayıcı yürütme komutlarını kullanabilir, program durumunu inceleyebilir ve benzeri. Programı İnceleme olanağınız, programın hata ayıklama bilgileri ile mi oluşturulmuş ve programın kaynak koduna erişim iznine sahip olup ve ortak dil çalışma zamanı JIT derleyicisine hata ayıklama bilgilerini mi takip bağlı olarak sınırlı olabilir.  
  
 Bkz: [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) daha fazla bilgi için.  
  
 **Yerel makinenizde çalışan bir işleme ekleme**  
  
 Seçin **hata ayıklama**, **işleme**. Üzerinde **iliştirme** iletişim kutusunda, işlemden seçin **kullanılabilir işlemler** listeleyin ve ardından **iliştirme**.  
  
 ![Ekle iletişim kutusu işlem](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Bir işlemin hata ayıklayıcıda otomatik olarak Başlat  
 Bazen, başka bir işlem tarafından başlatılan bir program için başlatma kodunun hatalarını ayıklamak gerekebilir. Hizmetleri ve özel kurulum eylemleri verilebilir. Bu senaryolarda ayıklayıcısının başlatılmasını ve uygulamanız başlatıldığında otomatik olarak ekleyin.  
  
1. Kayıt defteri düzenleyicisini başlatın (**regedit.exe**).  
  
2. Gidin **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows nt\currentversion\ımage File Execution Options** klasör.  
  
3. Hata ayıklayıcıda başlatmak istediğiniz uygulamanın klasörünü seçin.  
  
    Bir uygulama adı bir alt klasör olarak listelenmiyorsa seçin **Image File Execution Options** seçip **yeni**, **anahtar** bağlam menüsünde. Yeni anahtarı seçin, **Yeniden Adlandır** kısayol menüsünde ve ardından uygulama adı girin.  
  
4. Uygulama klasör bağlam menüsünde **yeni**, **dize değeri**.  
  
5. Yeni değer adını değiştirmek **yeni değer** için `debugger`.  
  
6. Hata ayıklayıcı girişinin bağlam menüsünde **Değiştir**.  
  
7. Dize Düzenle iletişim kutusunda, yazın `vsjitdebugger.exe` içinde **değer verisi** kutusu.  
  
    ![Düzenle iletişim kutusu dize](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Otomatik hata ayıklayıcıyı başlatmak giriş regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Geçiş işlemleri, kesme ve yürütme, kaynak boyunca devam edin  
  
-   [İşlemler arasında geçiş](#BKMK_Switch_between_processes) • [kesme, adım ve devam etme komutları](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> İşlemler arasında geçiş yap  
 Hata ayıklama, ancak yalnızca bir işlemi belirli bir zamanda hata ayıklayıcıda etkin değilse, birden çok işleme iliştirebilirsiniz. Etkin ayarlayabilirsiniz veya *geçerli* hata ayıklama konumu araç çubuğu ya da işlem **işlemleri** penceresi. İşlemler arasında geçiş yapmak için her iki işlem kesme modunda olması gerekir.  
  
 **Geçerli işlemi ayarlamak için**  
  
- Hata ayıklama konumu araç çubuğunda **işlem** görüntülemek için **işlem** liste kutusu. Geçerli işlem olarak belirtmek istediğiniz işlemi seçin.  
  
   ![İşlemler arasında geçiş](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Varsa **hata ayıklama konumu** araç çubuğu görünür değilse, seçin **Araçları**, **Özelleştir**. Üzerinde **araç çubukları** sekmesini, **hata ayıklama konumu**.  
  
- Açık **işlemleri** penceresi (kısayol **Ctrl + Alt + Z**), geçerli işlem olarak ayarlamak istediğiniz işlemi bulun ve çift tıklayın.  
  
   ![İşlemler penceresi](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Geçerli işlem sarı bir ok ile işaretlenir.  
  
  Bir projeye geçiş yapmak onu hata ayıklama amaçları için geçerli işlem ayarlar. Görüntülediğiniz herhangi bir hata ayıklayıcı penceresi geçerli işlemin durumunu gösterir ve tüm adım komutları yalnızca geçerli işlemi etkiler.  
  
  ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [geçiş işlemleri, kesme ve yürütme, kaynak boyunca devam edin](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Kesme, adım ve devam etme komutları  
  
> [!NOTE]
>  Varsayılan olarak, kesme, devam etmek ve atlama hata ayıklayıcı komutları, hatası ayıklanan tüm işlemleri etkiler. Bu davranışı değiştirmek için bkz: [birden çok işlem yürütme davranışını Yapılandır](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Komutu**|**Bir işlem kesildiğinde tüm işlemleri Kes**<br /><br /> İşaretlenmiş (varsayılan)|**Bir işlem kesildiğinde tüm işlemleri Kes**<br /><br /> Temizlenmiş|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümünü Kes**|Tüm işlemler kesilir.|Tüm işlemler kesilir.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Devam et**|Tüm işlemler sürdürülür.|Tüm askıya alınan işlemler sürdürülür.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Adımla**<br />-   **Üzerinden adımla**<br />-   **Dışına adımla**|Geçerli işlem ilerlerken tüm işlemler çalıştırılır.<br /><br /> Ardından, tüm işlemler kesilir.|Geçerli işlem adımları.<br /><br /> Aksıda işlemler sürdürülüyor.<br /><br /> Çalışan işlemler devam ediyor.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Geçerli işlem içine adımla**<br />-   **Geçerli işlem üzerinden adımla**<br />-   **Geçerli işlem dışına adımla**|Yok|Geçerli işlem adımları.<br /><br /> Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|Kaynak penceresi<br /><br /> -   **Kesme noktası**|Tüm işlemler kesilir.|Yalnızca kaynak pencere işlemi kesilir.|  
|Kaynak penceresi bağlam menüsü:<br /><br /> -   **İmlece kadar Çalıştır**<br /><br /> Kaynak pencerenin geçerli işlemde olması gerekir.|Kaynak pencere işlemleri imlece çalıştırıldığında ve sonra kesildiğinde tüm işlemler çalıştırılır.<br /><br /> Daha sonra diğer tüm işlemler kesilir.|Kaynak pencere işlemi imleç olarak çalışır.<br /><br /> Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **İşlemi kesme**|Yok|Seçili işlem kesilir.<br /><br /> Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **İşleme devam edin**|Yok|Seçili işlem devam eder.<br /><br /> Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [geçiş işlemleri, kesme ve yürütme, kaynak boyunca devam edin](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Hata ayıklamayı durdurun, sonlandırın işlemlerden ayırın  
  
- [Durdurun, sonlandırın ve komutları Ayır](#BKMK_Stop__terminate__and_detach_commands)  
  
  Varsayılan olarak, seçtiğinizde **hata ayıklama**, **hata ayıklamayı Durdur** hata ayıklayıcıda birden çok işlem açıkken, hata ayıklayıcı sonlandırılır veya işlemin nasıl açılmış bağlı olarak, tüm işlemlerden ayırır Hata Ayıklayıcı:  
  
- Hata ayıklayıcıda geçerli işlem başlatıldıysa, bu işlem sonlandırılır.  
  
- Geçerli işleme hata ayıklayıcıyı eklediyseniz, hata ayıklayıcı işlemden ayırır ve çalışan işlemi bırakır.  
  
  Örneğin, bir Visual Studio çözümünden bir işlemin hatalarını ayıklamaya başlatırsanız, zaten çalışan başka bir işleme iliştirin ve ardından **hata ayıklamayı Durdur**, hata ayıklama oturumu sona erer, Visual Studio'da başlatılan işlem eklediğiniz işlem çalışır durumda kalır ancak, sonlandırılır. Hata ayıklamayı durdurma biçiminizi denetlemek için aşağıdaki yordamları kullanabilirsiniz.  
  
> [!NOTE]
>  **Bir işlem kesildiğinde tüm işlemleri Kes** seçeneği hata ayıklama veya sonlandırma ve ayırma işlemleri durduruluyor etkilemez.  
  
 **Hata ayıklamayı Durdur tek bir işlemi nasıl etkilediğini değiştirmek için**  
  
-   Açık **işlemleri** penceresi (kısayol **Ctrl + Alt + Z**). Bir işlem seçin ve ardından seçin veya temizleyin **hata ayıklama durdurulduğunda ayırma** onay kutusu.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Durdurun, sonlandırın ve komutları Ayır  
  
|||  
|-|-|  
|**Komutu**|**Açıklama**|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Hata ayıklamayı Durdur**|Davranış tarafından değiştirilmedikçe **işlemleri** penceresi **hata ayıklama durdurulduğunda ayırma** seçeneği:<br /><br /> 1.  Hata ayıklayıcı tarafından başlatılan işlemler sonlandırılır.<br />2.  Eklenen işlemler, hata ayıklayıcıdan ayrılır.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümünü Sonlandır**|Tüm işlemler sonlandırılır.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümünü Ayır**|Hata ayıklayıcı tüm işlemden ayrılır.|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **İşlem ayırma**|Hata ayıklayıcı seçilen işlemden ayrılır.<br /><br /> Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **İşlemi Sonlandır**|Seçilen işlem sonlandırıldı.<br /><br /> Diğer işlemler varolan durum (askıya alınmış veya çalışıyor) korur.|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **Hata ayıklama durdurulduğunda ayırma**|Davranışını değiştirir **hata ayıklama**, **hata ayıklamayı Durdur** seçilen işlem için:<br /><br /> -Checked: Hata ayıklayıcı işlemden ayırır.<br />-Temizlenmiş: İşlem sonlandırıldı.|  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [hata ayıklamayı durdurun, sonlandırın işlemlerden ayırın](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Çalıştırma işlemleri iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just-ın-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Çok İş Parçacıklı Uygulamaların Hatalarını Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)



