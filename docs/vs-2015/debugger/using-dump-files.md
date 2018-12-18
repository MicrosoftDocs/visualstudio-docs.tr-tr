---
title: Döküm dosyalarını kullanma | Microsoft Docs
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
- vs.debug.crashdump
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c117e0aa7922c70f919a7b16fa6d40a447f2ce2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761127"
---
# <a name="using-dump-files"></a>Döküm dosyalarını kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yığınlar içeren veya içermeyen döküm dosyaları; bir döküm dosyası oluşturun; bir döküm dosyasını açın; döküm dosyası için kaynak dosyasını, pdb'leri ve ikili dosyaları bulun. 
  
##  <a name="BKMK_Contents"></a> İçeriği  
 [Bir döküm dosyası nedir?](#BKMK_What_is_a_dump_file_)  
  
 [Yığınlar içeren veya içermeyen döküm dosyaları](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Gereksinimler ve sınırlamalar](#BKMK_Requirements_and_limitations)  
  
 [Bir döküm dosyası oluşturma](#BKMK_Create_a_dump_file)  
  
 [Bir döküm dosyası Aç](#BKMK_Open_a_dump_file)  
  
 [İkili dosyalar, sembol (.pdb) dosyalarını ve kaynak dosyaları bulma](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
##  <a name="BKMK_What_is_a_dump_file_"></a> Bir döküm dosyası nedir?  
 A *döküm dosyasını* dökümün alındığı andaki bir uygulamanın anlık görüntüsüdür. Hangi işlemin yürütülmüş, hangi modüllerin de yüklenmiş olduğunu gösterir. Döküm, yığın bilgileriyle kaydedildiyse, döküm dosyası, zaman içinde o anda uygulamanın belleğinde olanların bir anlık görüntüsünü içerir. Döküm dosyasını Visual Studio'da bir yığın ile açmak, bir hata ayıklama oturumunda kesme noktasında durdurmak gibidir. Yürütme devam edemiyor olsanız da, döküm oluştuğu anda uygulamanın yığınlarını, iş parçacıklarını ve değişken değerlerini inceleyebilirsiniz.  
  
 Dökümler öncelikle geliştiricinin erişiminin olmadığı makinelerde oluşan sorunların hatalarını ayıklamak için kullanılır. Örneğin, müşterinin kilitlenmesini yeniden oluşturamadığınızda veya makineniz kesintiye uğradığında bir müşterinin makinesinden döküm dosyası kullanabilirsiniz. Daha fazla test için test makinesinin kullanılabilmesi amacıyla çökmeyi veya takılma verilerini kaydetmek üzere testçiler tarafından da dökümler oluşturulur. Visual Studio hata ayıklayıcı, yönetilen veya yerel kod için döküm dosyaları kaydedebilir. Hata ayıklayıcı, Visual Studio veya dosyaları kaydeden başka programlar tarafından oluşturulmuş döküm dosyalarını yükleyebilir *mini döküm* biçimi.  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Yığınlar içeren veya içermeyen döküm dosyaları  
 Yığın bilgileri içeren veya içermeyen döküm dosyaları oluşturabilirsiniz.  
  
- **Yığınlar içeren döküm dosyaları** uygulamanın bellek anlık görüntüsünü içerir. Bu döküm oluşturulduğundaki değişkenlerin değerlerini içerir. Yığınla kaydedilmiş bir döküm dosyası yüklerseniz, uygulama ikili dosyası bulunamasa bile Visual Studio sembolleri yükleyebilir. Visual Studio ayrıca döküm dosyasında yüklenen yerel modüllerin ikili dosyalarını kaydederek hata ayıklamayı daha da kolaylaştırır.  
  
- **Yığınlar içermeyen döküm dosyaları** yığın bilgileri içeren daha küçük olur. Ancak hata ayıklayıcısının sembol bilgilerini bulmak için uygulama ikili dosyalarını yüklemesi gerekir. İkili dosyalar, döküm oluşturulduğunda kullanılan ikili dosyalarla tam olarak eşleşen ikili dosyalar olmalıdır. Sadece yığın değişkenlerin değerleri öbek veri olmadan döküm dosyalarına kaydedilir.  
  
  ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Requirements_and_limitations"></a> Gereksinimler ve sınırlamalar  
  
- En iyi duruma getirilmiş kodun döküm dosyalarının hatalarının ayıklanması kafa karıştırıcı olabilir. Örneğin, işlevlerin derleyici içerilmesi, beklenmeyen çağrı yığınlarıyla sonuçlanabilir ve diğer iyileştirmeler, değişkenlerin ömrünü değiştirebilir.  
  
- 64 bit bilgisayarda çalışan bir Visual Studio örneğinde 64 bit makinelerdeki döküm dosyalarının hataları ayıklanmalıdır.  
  
- Visual Studio'nun VS 2013 öncesi sürümlerinde, 64 bit makinelerde çalıştırılan 32 bit uygulamaların bazı araçlar tarafından toplanan (Görev Yöneticisi ve 64-bit WinDbg) dökümleri Visual Studio'da açılamadı. Bu sınırlama, VS 2013 sürümünde kaldırılmıştır.  
  
- Visual Studio, ARM cihazlarından yerel uygulamaların döküm dosyalarının hatalarını ayıklayabilir. Visual Studio, ARM cihazlarındaki yönetilen uygulamaların uygulama döküm dosyalarının da hatalarını ayıklayabilir, ancak bunu yalnızca yerel hata ayıklayıcıda yapabilir.  
  
- Hata ayıklamak için [çekirdek modu](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) döküm dosyalarını Visual Studio 2013'te, yükleme [Windows 8.1 sürümünü, hata ayıklama araçları için Windows](http://msdn.microsoft.com/windows/hardware/gg463009). Bkz: [Visual Studio'da çekirdek hata ayıklama](http://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Visual Studio olarak bilinen eski döküm biçiminde kaydedilen döküm dosyalarının hatalarını ayıklayamaz bir [tam kullanıcı modu dökümü](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx). Tam kullanıcı modu dökümünün yığını olan bir dökümle aynı olmadığına dikkat edin.  
  
- İle hata ayıklamak için [SOS.dll (SOS Debugging Extension)](http://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) Visual Studio'da hata ayıklama araçları için Windows Sürücü Seti'nin (WDK) parçası olan Windows yüklemeniz gerekir. Bkz: [Windows 8.1 önizleme: setler, bits ve Araçlar indirin](http://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Create_a_dump_file"></a> Bir döküm dosyası oluşturma  
 Visual Studio ile bir döküm dosyası oluşturmak için:  
  
- Visual Studio'daki bir işlemde hata ayıklarken, hata ayıklayıcı kesme noktası veya bir özel durumda durduğunda döküm dosyasını kaydedebilirsiniz. Seçin **dökümü Farklı Kaydet**, **hata ayıklama**. İçinde **dökümü Farklı Kaydet** iletişim kutusundaki **farklı kaydetme türü** seçebileceğiniz listesinde **mini döküm** veya **yığınlı** (varsayılan).  
  
- İle [tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) etkinleştirildiğinde, hata ayıklayıcının hata ayıklayıcısı dışında çalışan çöken bir işleme ve sonra döküm dosyasını kaydedebilirsiniz. Bkz: [çalıştırma işlemleri iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  Windows mini döküm biçimini destekleyen herhangi bir programla da döküm dosyaları oluşturabilirsiniz. Örneğin, **Procdump** komut satırı yardımcı programı [Windows SysInternals](http://technet.microsoft.com/sysinternals/default) Tetikleyiciler veya isteğe bağlı göre işlem kilitlenme döküm dosyaları oluşturabilirsiniz. Bkz: [gereksinimleri ve sınırlamaları](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) döküm dosyalarını oluşturmak için diğer araçları kullanma hakkında ek bilgi için bu konuda.  
  
  ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Open_a_dump_file"></a> Bir döküm dosyası Aç  
  
1.  Visual Studio'da **dosya**, **açık**, **dosya**.  
  
2.  İçinde **açık dosya** iletişim kutusunda, döküm dosyasını bulup seçin. Çoğunlukla .dmp uzantısına sahip olacaktır. Ardından **Tamam**.  
  
3.  **Döküm dosyası özeti** penceresi görüntülenir. Bu pencerede, döküm dosyasının hata ayıklama özet bilgilerini görüntüleyebilir, sembol yolunu ayarlayabilir, hata ayıklamayı başlatabilir ve özet bilgilerini panoya kopyalayabilirsiniz.  
  
     ![Mini döküm Özet sayfası](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4.  Hata ayıklamayı başlatmak için Git **eylemleri** bölüm ve seçmeniz **sadece Yerelle Hata Ayıkla** veya **karışık olanla Hata Ayıkla**.  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> İkili dosyalar, sembol (.pdb) dosyalarını ve kaynak dosyaları bulma  
 Bir döküm dosyasında hata ayıklamak üzere Visual Studio'nun tam özelliklerini kullanmak aşağıdakilere erişim gerekir:  
  
- Dökümün alındığı .Exe dosyası ve döküm işleminde kullanılan diğer ikili dosyalar (DLL'ler vb.).  
  
   Yığın veriler ile bir dökümün hatalarını ayıklıyorsanız, Visual Studio bazı modüller için eksik ikili dosyalarla başa çıkabilir, ancak geçerli çağrı yığınları oluşturmak için yeterli modüller için ikili dosyalara sahip olmalıdır. Visual Studio, yığın ile döküm dosyasında yerel modüller içerir.  
  
- .exe ve diğer ikili dosyalar için sembol (.pdb) dosyaları.  
  
- İlgilendiğiniz modüller için kaynak dosyaları.  
  
   Yürütülebilir ve .pdb dosyaları, döküm oluşturulduğunda kullanılan dosyaların sürüm ve yapısıyla tam olarak eşleşmelidir.  
  
   Kaynak dosyaları bulamazsanız, modüllerin ayrıştırılmasını kullanarak hata ayıklayabilirsiniz,  
  
  **Yürütülebilir dosyalar için varsayılan arama yolları**  
  
  Visual Studio, döküm dosyasında bulunmayan yürütülebilir dosyalar için bu konumları otomatik olarak arar:  
  
1. Döküm dosyasını içeren dizin.  
  
2. Döküm dosyasında belirtilen modül yolu. Bu, makinede dökümün toplandığı modül yoludur.  
  
3. Belirtilen sembol yollarını **hata ayıklama**, **seçenekleri**, **sembolleri** sayfa Visual Studio'nun **Araçları**, **seçenekleri**  iletişim kutusu. Bu sayfada arama yapmak için daha fazla konum ekleyebilirsiniz.  
  
   **Kullanarak ikili yok / sembol / kaynak sayfalarını**  
  
   Visual Studio dökümdeki bir modülün hatalarını ayıklamak için gerekli dosyaları bulamazsa, uygun bir sayfayı gösterir (**hiçbir ikili bulunamadı**, **hiçbir sembol bulunamadı**, veya **hiçbir kaynak bulunamadı**). Bu sayfalar, sorunun nedeni hakkında ayrıntılı bilgi sağlar ve dosyaların doğru konumunu belirlememenize yardımcı olabilecek eylem bağlantıları sağlar. Bkz: [sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Just-ın-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)

