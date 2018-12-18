---
title: VSPerfCmd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23abc362b3c91579585272e4ebf1b190cab55dde
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320988"
---
# <a name="vsperfcmd"></a>VSPerfCmd
*VSPerfCmd.exe* aracı, performans veri toplamayı başlatır ve durdurur için kullanılır. Aşağıdaki sözdizimini kullanır:  
  
```cmd  
VSPerfCmd [/U] [/options]  
```  
  
 Aşağıdaki tabloların açıkladığı *VSPerfCmd.exe* araç seçenekleri.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**U**|Yeniden yönlendirilmiş konsol Çıkışı Unicode olarak yazılır. İlk seçenek belirtilmelidir.|  
|[Başlangıç](../profiling/start.md) **:** `mode`|Profil oluşturma hizmetinin belirtilen modunda başlatır.|  
|[Çıkış](../profiling/output.md) **:** `filename`|Çıkış dosyası adını belirtir. Yalnızca kullanmak **Başlat**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Profil oluşturma Windows oturumlarda etkinleştirir. Yalnızca kullanmak **Başlat**, **ekleme**, **veya başlatma**.|  
|[Kullanıcı](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Profil Oluşturucu hizmeti için belirtilen hesap erişim sağlar. Yalnızca kullanmak **Başlat**.|  
|[Waıtstart](../profiling/waitstart.md)[**:**`n`]|Başlatmak veri koleksiyonu Günlükçüsünü bekler. Varsa `n` belirtilen **VSPerfCmd** en fazla bekleme `n` saniye. Varsa `n` belirtilmezse, **VSPerfCmd** süresiz olarak bekler. Bu kolaylaştırır **VSPerfCmd** toplu iş işleminin bir parçası olarak.|  
|[Sayaç](../profiling/counter.md) **:** `cfg`|Örnek profili oluşturma yöntemi kullanıldığında, CPU sayaç ve örnekleme aralığı kullanılacak olay sayısını belirtir. Sayaç değeri yalnızca bir örnek oluşturabilirsiniz.<br /><br /> İzleme profili oluşturma metodu kullanıldığında, her bir izleme noktasına toplanacak CPU sayaç belirtir. Yalnızca kullanmak **Başlat:**`Trace`, **ekleme**, veya **başlatma**.|  
|[QueryCounters](../profiling/querycounters.md)|Geçerli makine için geçerli CPU sayaçları listesini görüntüler.|  
|[WinCounter](../profiling/wincounter.md) **:** *yolu*|Profil işareti verilerle dahil etmek için bir Windows performans sayacı olay belirtir. Yalnızca kullanmak **Başlat**.|  
|[Otomatik işaret zamanının](../profiling/automark.md) **:** *n*|Windows performans sayacı verilerini toplama olayları zaman aralığını (milisaniye cinsinden) belirtir. İle kullanma **WinCounter**.|  
|[Olayları](../profiling/events-vsperfcmd.md) **:** `option`|Belirtilen olay izleme için Windows (ETW) olayları toplamayı denetler. ETW verilerini toplanır bir. *ITL* değil profil oluşturma veri dosyası (. *Vsp*) dosyası.|  
|[Status](../profiling/status.md)|Şu anda profillenen işlemleri ve profil oluşturucu denetlemek için yetkiye sahip hesaplar hakkında bilgi, profil oluşturucu durumunu görüntüler.|  
|[Kapatma](../profiling/shutdown.md)[**:**`n`]|Profil oluşturma veri dosyasını kapatır ve profil oluşturucuyu devre dışı bırakır.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Veri toplama çağrısı yapıldıktan sonra sürdürür **VSPerfCmdGlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Tüm veri toplamayı durdurur ancak profil oluşturma oturumu sona ermez.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Belirtilen işlem için veri toplama için bir çağrı tarafından profil oluşturma duraklatıldı sonra sürdürür **VSPerfCmdProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Belirtilen işlem için veri toplamayı durdurur.|  
|[ThreadOn ve ThreadOff](../profiling/threadon-and-threadoff.md) **:** *TID*|Belirtilen işlem için bir çağrı tarafından profil oluşturma duraklatıldı sonra profil oluşturmayı devam ettirir **VSPerfCmdThreadOff**. Kullanım **ThreadOn** yalnızca cihaz atama yöntemi ile profili oluşturulurken.|  
|[ThreadOn ve ThreadOff](../profiling/threadon-and-threadoff.md) **:** *TID*|Belirtilen iş parçacığı profil oluşturma duraklatır. Kullanım **ThreadOff** yalnızca cihaz atama yöntemi ile profili oluşturulurken.|  
|[İşareti](../profiling/mark.md) **:** _MarkNum_[**,**_MarkText_**]**|Profil oluşturma veri dosyasını, isteğe bağlı metinle bir işaret ekler.|  
  
## <a name="sample-method-options"></a>Örnek yöntem seçenekleri  
 Aşağıdaki seçenekler, yalnızca örnekleme profili oluşturma yöntemi kullanırken kullanılabilir.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|[Başlatma](../profiling/launch.md) **:** *yürütülebilir dosya*|Belirtilen uygulamayı başlatır ve profil oluşturma başlar.|  
|[Args](../profiling/args.md) **:** *bağımsız değişkenleri*|Başlatılan uygulamaya geçirilecek komut satırı bağımsız değişkenleri belirtir.|  
|[Console](../profiling/console.md)|Belirtilen komut yeni bir komut istemi penceresinde başlatır.|  
|[Ekleme](../profiling/attach.md) **:** *PID*[**,**_PID_]|Belirtilen işlemler için profil oluşturma başlar. İşlemler işlem kimliği veya işlem adına göre tanımlanabilir.|  
|[Ayırma](../profiling/detach.md)[**:**_PID_[,_PID_]]|Belirtilen işlemler profil oluşturmayı durdurur. İşlemler işlem kimliği veya işlem adına göre tanımlanabilir. Hiçbir işlem belirtilmezse, profil oluşturma için tüm işlemler durdurulur.|  
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**ayırma**`&#124;`**ömrü**}]|.NET bellek ayırma ve nesne yaşam süresi verisi toplar. Yalnızca kullanmak **VSPerfCmdLaunch** seçeneği.|  
  
### <a name="sample-interval-options"></a>Örnek aralık seçenekleri  
 Aşağıdaki seçenekler, örnekleme aralıklar ın süresi ve türünü belirtin. Varsayılan değer **Zamanlayıcı**. Kullanarak CPU sayaç ve aralık olarak da belirtebilirsiniz **sayacı** seçeneği. Bu seçenekler yalnızca ile belirtilebilir **başlatma** veya ilk **iliştirme** profil oluşturma oturumunun.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|[PF](../profiling/pf.md)[**:**_n_]|Her n. sayfa hatası örnekleri (varsayılan = 10).|  
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Her n. Sistem çağrısında örnek (varsayılan = 10).|  
|[Zamanlayıcı](../profiling/timer.md)[**:**_n_]|Her n. işlemci örnekleri döngüsü (varsayılan = 10000000).|  
  
## <a name="service-component-and-kernel-mode-device-options"></a>Hizmet bileşeni ve çekirdek modu cihaz seçenekleri  
 Aşağıdaki yönetim seçenekleri, profil oluşturma hizmet bileşenleri veya kernel modlu cihaz sürücüleri destekler. Yönetim seçenekleri, profil oluşturma izinlerini ayarlama ve profili oluşturulan hizmeti veya aygıt sürücüsü denetimi.  
  
 Yönetim seçenekleri, bir komut isteminde yönetici kimlik bilgileriyle çalışıyor yürütülmelidir.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Admin:security**, \< **izin&#124;REDDET**>, *sağ*[ *sağ*], \< *kullanıcı* &#124; *Grubu*>|Erişim izni verdiği veya belirtilen kullanıcı veya profil oluşturma hizmetleri için Grup erişimi engeller.<br /><br /> `Right` aşağıdakilerden biri olabilir:<br /><br /> CrossSession - hizmete profil oluşturma oturumunu kesecek şekilde kullanıcı erişimi sağlar.<br /><br /> SampleProfiling - kullanıcı erişim örnekleme profil oluşturmayı etkinleştirmek için bir sürücü için sağlar. İzleme profil oluşturma sırasında çekirdek geçiş bilgilere erişmek için de kullanılır.<br /><br /> FullAccess - kullanıcı verir CrossSession hem SampleProfiling erişim.|  
|**Admin:Security, listesi**|Profil oluşturma hizmetleri geçerli durumunu listeler ve kullanıcı izinleri listeler.|  
|**Yönetici:** \< *hizmet*&#124;*sürücü*>\<**Başlat**&#124;**Durdur**  &#124; **Yükleme**&#124;**Kaldır**>|Başlatır, durdurur, yükler veya profil oluşturma hizmet bileşenini (hizmet) veya çekirdek modu cihaz sürücüsünü (sürücü) kaldırır.|  
|**Yönetici:** \< *hizmet*&#124;*sürücü*>**AutoStart**\<**üzerinde** &#124; **Kapalı**>|Etkinleştirir veya yeniden başlatmadan sonra profil oluşturma hizmetinin (hizmet) veya çekirdek modu cihaz sürücüsünü (sürücü) otomatik olarak başlatılmasını devre dışı bırakır.|  
  
## <a name="vsperfcmd-driver"></a>VSPerfCmd Driver/Driver  
 **VSPerfCmd Driver/Driver** seçeneği kullanılmıyor şimdi. Kullanım **VsPerfCmdAdmin** bu işlevselliği için Seçenekler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Vsınstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)