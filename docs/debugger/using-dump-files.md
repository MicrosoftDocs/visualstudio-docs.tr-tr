---
title: Hata ayıklayıcı döküm dosyalarını kullanma | Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e30f9d29ba3c922d70c8acdf7d4db5d8a1670fd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066960"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcı döküm dosyaları

<a name="BKMK_What_is_a_dump_file_"></a> A *döküm dosyasını* yürütülmekte olan işlem ve zaman içinde bir noktadaki bir uygulama için yüklenen modülleri gösterir bir anlık görüntüdür. Yığın bilgileri içeren bir döküm da bu noktada uygulamanın belleğinin anlık görüntüsünü içerir. 

Visual Studio'da bir yığın ile döküm dosyası açılırken bir hata ayıklama oturumunda kesme noktasında durdurulurken gibi bir şeydir. Yürütme devam edemiyor olsa da, döküm sırasında yığınlarını, iş parçacıklarını ve değişken değerlerini inceleyebilirsiniz.

Dökümleri, çoğunlukla geliştiricileri erişiminiz yoksa makinelerden hata ayıklamak için kullanılır. Bir kilitlenmesini yeniden oluşturamadığınızda veya kendi makinenizde askıda, bir müşterinin makinesinden döküm dosyasını kullanabilirsiniz. Test edicileri çökmeyi veya daha fazla test etmek için kullanılacak veri askıda dökümlerin oluşturabilir. 

Visual Studio hata ayıklayıcı, yönetilen veya yerel kod için döküm dosyaları kaydedebilir. Visual Studio veya dosyaları kaydetmek diğer uygulamalar tarafından oluşturulmuş döküm dosyalarının hatalarını ayıklayabilir *mini döküm* biçimi.

##  <a name="BKMK_Requirements_and_limitations"></a> Gereksinimler ve sınırlamalar

-   64 bit makinelerdeki döküm dosyalarının hatalarını için Visual Studio 64-bit makinede çalıştırılması gerekir.

-   Visual Studio, ARM cihazlarından yerel uygulamaların döküm dosyalarının hatalarını ayıklayabilir. Ayrıca, ARM cihazlarından, ancak yalnızca yerel hata ayıklayıcı, yönetilen uygulamaların dökümlerini de ayıklayabilirsiniz.

-   Hata ayıklamak için [çekirdek modu](/windows-hardware/drivers/debugger/kernel-mode-dump-files) düküm dosyalarında veya kullanın [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) hata ayıklama uzantısı Visual Studio'da hata ayıklama araçları indirme Windows için [Windows Sürücü Seti'nin (WDK)](/windows-hardware/drivers/download-the-wdk).

-   Visual Studio'nun eski içinde kaydedilen döküm dosyalarının hatalarını ayıklayamaz [tam kullanıcı modu dökümü](/windows/desktop/wer/collecting-user-mode-dumps) biçimi. Tam kullanıcı modu dökümü yığın ile döküm ile aynı değil.

-   En iyi duruma getirilmiş kodun döküm dosyalarının hatalarının ayıklanması kafa karıştırıcı olabilir. Örneğin, işlevlerin derleyici içerilmesi, beklenmeyen çağrı yığınlarıyla sonuçlanabilir ve diğer iyileştirmeler değişkenlerin ömrünü değiştirebilir.

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Yığınlar içeren veya içermeyen döküm dosyaları

Döküm dosyaları olabilir veya yığın bilgisi olmayabilir.

-   **Döküm dosyalarıyla yığınlar** döküm sırasında değişkenlerin değerleri de dahil olmak üzere, uygulamanın belleğinin anlık görüntüsünü içerir. Visual Studio ayrıca çok daha kolay hata ayıklama yapabilirsiniz bir yığın ile döküm dosyasında yüklenen yerel modüllerin ikili dosyaları kaydeder. Uygulama ikili bulunamıyor olsa bile bir yığın ile döküm dosyasından visual Studio sembolleri yükleyebilir. 

-   **Yığınlar içermeyen döküm dosyaları** yığınlar ile dökümleri daha küçük olur, ancak hata ayıklayıcı sembol bilgilerini bulmak için uygulama ikili dosyalarını yüklemeniz gerekir. Yüklenen ikili dosyaları, döküm oluşturma sırasında çalışan olanları tam olarak eşleşmelidir. Yığınlar içermeyen döküm dosyaları sadece yığın değişkenlerin değerleri kaydedin.

##  <a name="BKMK_Create_a_dump_file"></a> Bir döküm dosyası oluşturma

Visual Studio bir işlemde hata ayıklarken, hata ayıklayıcı bir kesme noktası veya özel durum durduğunda döküm kaydedebilirsiniz. 

İle [tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) etkin açabilir Visual Studio hata ayıklayıcısı Visual Studio dışında çöken bir işleme ve sonra hata ayıklayıcı'dan döküm dosyasını kaydedebilirsiniz. Bkz: [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Bir döküm dosyası kaydetmek için:**

1. Hata ayıklama sırasında bir hata veya kesme noktası durdurulduğu sırada, seçin **hata ayıklama** > **dökümü Farklı Kaydet**. 

1. İçinde **dökümü Farklı Kaydet** iletişim kutusunun **farklı kaydetme türü**seçin **mini döküm** veya **yığınlı** (varsayılan).

1. Bir yola göz atın ve bilgi döküm dosyası için bir ad seçin ve ardından **Kaydet**. 

>[!NOTE]
>Windows mini döküm biçimini destekleyen herhangi bir programla döküm dosyaları oluşturabilirsiniz. Örneğin, **Procdump** komut satırı yardımcı programı [Windows SysInternals](http://technet.microsoft.com/sysinternals/default) Tetikleyiciler veya isteğe bağlı işlem kilitlenme döküm dosyaları oluşturabilirsiniz. Bkz: [gereksinimleri ve sınırlamaları](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) döküm dosyalarını oluşturmak için diğer araçları kullanma hakkında bilgi.

##  <a name="BKMK_Open_a_dump_file"></a> Bir döküm dosyası Aç

1. Visual Studio'da **dosya** > **açık** > **dosya**.

1. İçinde **açık dosya** iletişim kutusunda, döküm dosyasını bulup seçin. Olması genellikle bir *.dmp* uzantısı. Seçin **Tamam**.

   **Mini döküm dosya özeti** penceresi gerçekleştirebileceğiniz özeti ve modül bilgi döküm dosyası ve eylemleri gösterir.

   ![Mini döküm Özet sayfası](../debugger/media/dbg_dump_summarypage.png "mini döküm Özet sayfası")

1. Altında **Eylemler**:
   - Sembol yükleme konumlarını belirlemek için seçin **sembol yollarını Ayarla**.
   - Hata ayıklamayı başlatmak için seçin **ile yalnızca yönetilen hata ayıklama**, **sadece Yerelle Hata Ayıkla**, **karışık olanla Hata Ayıkla**, veya **ile yönetilen bellek hata ayıklama**.

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> .Exe, .pdb ve kaynak dosyaları bulma

Kullanmak için Visual Studio'nun tam özelliklerini bir döküm dosyası hata ayıklama gerekir:

- *.Exe* döküm oluşturulduğu için dosya ve döküm işlemi kullanılan diğer ikili dosyalar (DLL'ler vb.).
- Sembol (*.pdb*) dosyaları *.exe* ve diğer ikili.
- *.Exe* ve *.pdb* sürüm ve derleme dosyaları, tam olarak eşleşen dosyaları döküm oluşturma.
- İlgili modüller için kaynak dosyaları. Kaynak dosyaları bulamazsanız modüllerin ayrıştırılmasını kullanabilirsiniz.

Döküm, yığın verileri varsa, Visual Studio bazı modüller için eksik ikili dosyalarla başa çıkabilir, ancak geçerli çağrı yığınları oluşturmak için yeterli modüller için ikili dosyalar olmalıdır. 

### <a name="search-paths-for-exe-files"></a>.Exe dosyaları için arama yolları

Visual Studio için bu konumları otomatik olarak arar *.exe* döküm dosyasında bulunmayan dosyaları:

1. Döküm dosyasını içeren klasör.
2. Modül yolu bilgi döküm dosyası, hangi döküm toplanan makinede modül yolu belirtir.
3. Belirtilen sembol yollarını **Araçları** (veya **hata ayıklama**) > **seçenekleri** > **hata ayıklama**  >  **Sembolleri**. Da açabilirsiniz **sembolleri** gelen sayfasında **eylemleri** bölmesinde **döküm dosyası özeti** penceresi. Bu sayfada arama yapmak için daha fazla konum ekleyebilirsiniz.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>İkili yok, sembol yok veya hiçbir kaynak bulunamadı sayfalarını kullanma

Visual Studio dosyaları bulamazsa dökümdeki bir modülün hatalarını ayıklamak gerekir, bu gösterir bir **hiçbir ikili bulunamadı**, **hiçbir sembol bulunamadı**, veya **hiçbir kaynak bulunamadı** sayfası. Bu sayfalar sorunun nedeni hakkında ayrıntılı bilgi sağlar ve yardımcı olabilecek eylem bağlantıları dosyaları bulun sağlayın. Bkz: [belirtin, sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Just-In-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)