---
title: 'Nasıl yapılır: izleme Profiler komut satırını kullanarak bir yerel hizmet ve ayrıntılı zamanlama verileri toplama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa230e858db8eea19e1f5b2ff7ad683e45a76fcb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757779"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Profil Oluşturucu Komut Satırını Kullanarak Yerel bir Hizmeti İzleme ve Ayrıntılı Zamanlama Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yerel (C/C++) araç haline getirmek için profil oluşturma araçları komut satırı araçları ve ayrıntılı zamanlama verileri toplamak.  

> [!NOTE]
>  Bilgisayar başlatıldıktan sonra hizmeti yeniden başlatılamıyor ise izleme yöntemi ile bir hizmetin profilini oluşturamazsınız, böyle bir hizmet, yalnızca işletim sistemi başlatıldığında başlatın.  
>   
>  Profil araçlarının komut satırı araçları tools\performance Tools alt dizininde içinde bulunan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yükleme dizini. 64 bit bilgisayarlarda araçların 64-bit hem 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Araçlar yöntemini kullanarak bir yerel hizmetten ayrıntılı zamanlama verileri toplamak için kullandığınız [VSInstr.exe](../profiling/vsinstr.md) aracını bileşenin belgelenmiş bir sürümünü oluşturmak için. Hizmet eklenmemiş sürümünü izleme eklenmiş sürümüyle hizmeti el ile başlatmak için yapılandırıldığından emin emin değiştirmeniz. Ardından profil oluşturucuyu başlatın.  

 Hizmet başlatıldığında, zamanlama verileri bir veri dosyasına otomatik olarak toplanır. Duraklatma ve profil oluşturma oturumu sırasında veri koleksiyonu devam ettirin.  

 Profil oluşturma oturumunu sona erdirmek için hizmeti kapatmak ve profil oluşturucuyu açıkça kapatın.  

## <a name="starting-the-application-with-the-profiler"></a>Profiler ile uygulama başlatılıyor  

#### <a name="to-start-profiling-a-native-service"></a>Bir yerel hizmete profil oluşturmayı başlatmak için  

1. Bir komut istemi penceresi açın.  

2. Kullanım **Vsınstr** aracını hizmet ikililerinin belgelenmiş bir sürümünü oluşturmak için.  

3. Özgün ikiliyi belgelenmiş sürüm ile değiştirin. Windows hizmeti Denetim Yöneticisi'nde hizmet başlangıç türü el ile olarak ayarlanmış olduğundan emin olun.  

4. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd** [/start](../profiling/start.md) **: izleme**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]    

   - **Çalıştığından** seçeneği profil oluşturucuyu başlatır.  

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **çalıştığından** seçeneği.  

   > [!NOTE]
   >  **/User** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                                   Açıklama                                                                                                                                                    |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |               ASP.NET çalışan işlemine sahip hesabın etki alanı ve kullanıcı adını belirtir. Bu seçenek, oturum açan kullanıcının farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir.               |
   |              [/ crosssession](../profiling/crosssession.md)              | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. ASP.NET uygulaması başka bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin İşlemler sekmesinde oturum kimliği sütununda listelenir. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   |        [/waitstart](../profiling/waitstart.md)[**:**`Interval`]         |                                                 Profil oluşturucunun hata vermeden önce başlatmak beklenecek saniye sayısını belirtir. Varsa `Interval` belirtilmezse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/start** hemen döndürür.                                                  |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                             Profil Oluşturucu veri toplamayı başlatmak için duraklatıldı, ekleme **/globaloff** seçeneğini **/start** komut satırı. Kullanım **/globalon** profil oluşturmayı devam ettirmek için.                                                                              |
   |           [/ Sayaç](../profiling/counter.md) **:** `Config`            |                                                                           Sayaç Config içerisinde belirtilen işlemci performans bilgileri toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir.                                                                           |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                    Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.                                                                                                                     |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                  İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır.                                                                                   |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                     Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.                                                                                     |


5. Servis kontrol yöneticisinden hizmeti başlatın.  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hizmet çalışırken kullanabileceğiniz **VSPerfCmd.exe** Profil Oluşturucu veri dosyasına verilerin yazılmasını başlatıp için Seçenekler. Veri toplama denetlenmesi size program yürütmenin, hizmeti kapatılıyor veya başlatma gibi özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki çiftleri **VSPerfCmd** seçenekleri başlatın ve veri toplamayı durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Başlar (**/threadon**) veya durdurur (**/threadoff**) veri toplama iş parçacığı kimliği tarafından belirtilen iş parçacığı için (`TID`).|  

## <a name="ending-the-profiling-session"></a>Profil Araçları oturumunu sonlandırma  
 Profil oluşturma oturumunu sona erdirmek için Araçlı bileşeni çalıştıran hizmetini durdurun ve sonra çağrı **VSPerfCmd**[/shutdown](../profiling/shutdown.md) profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatırsınız.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Servis kontrol yöneticisinden hizmeti durdurun.  

2.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd/Shutdown**  

3.  Belgelenmiş modülü özgün hali ile değiştirin. Gerekirse, hizmetin başlangıç türünü yeniden yapılandırın.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)   
 [İzleme Metodu Veri Görünümleri](../profiling/instrumentation-method-data-views.md)



