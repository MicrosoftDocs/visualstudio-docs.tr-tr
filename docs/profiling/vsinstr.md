---
title: Vsınstr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2526938274299cc5a90319749531f80e8bd3a90d
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220553"
---
# <a name="vsinstr"></a>VSInstr
Vsınstr aracının çalıştırılması, ikili dosyaları araç haline getirmek için kullanılır. Aşağıdaki sözdizimini kullanarak çağrılır:  
  
```cmd  
VSInstr [/U] filename [/options]  
```  
  
 Vsınstr aracı seçenekleri aşağıdaki tabloda açıklanmaktadır:  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**Yardım** veya **?**|Yardımı görüntüler.|  
|**U**|Yeniden yönlendirilmiş konsol Çıkışı Unicode olarak yazar. Belirtilen ilk seçenek olmalıdır.|  
|`@filename`|Her satırda bir komut seçeneği içeren bir yanıt dosyası adını belirtir.  Tırnak işareti kullanmayın.|  
|**OutputPath** `:path`|Alet düzeni görüntüsü için bir hedef dizin belirtir. Bir çıkış yolu belirtilmezse, özgün ikili dosya adı ile aynı dizinde "Orig" ekleyerek yeniden adlandırılır ve bir kopyasını bir ikili dosya işaretlendi.|  
|**Hariç tutma** `:funcspec`|Araştırmalarla izlemeden hariç tutmak için işlev belirtimi belirtir. Sonda eklemesi bir işlevde profil oluşturma beklenmedik ve istenmeyen sonuçları neden olduğunda yararlı olur.<br /><br /> Kullanmayın **hariç** ve **INCLUDE** aynı ikili işlevlerde başvuran seçenekleri.<br /><br /> Birden çok işlev belirtimi ayrı belirtebilirsiniz **hariç** seçenekleri.<br /><br /> `funcspec` bir olarak tanımlanmıştır:<br /><br /> [ad alanı\<separator1 >] [sınıf\<separator2 >] işlevi<br /><br /> \<separator1 > olan `::` yerel kod ve `.` yönetilen kod için.<br /><br /> \<separator2 > her zaman `::`<br /><br /> **Dışlama** kod kapsamı ile desteklenir.<br /><br /> Joker karakter \* desteklenir. Örneğin, bir ad alanı kullanım uygulamasında tüm işlevleri hariç tutmak için şunu yazın:<br /><br /> MyNamespace::\*<br /><br /> Kullanabileceğiniz **Vsınstr /DumpFuncs** belirtilen ikili işlevlerin tam adlarını listelemek için.|  
|**İçerir** `:funcspec`|Bir işlev belirtimi araştırmalara sahip bir gereç ikili belirtir. İkili dosyaları diğer tüm işlevler işaretlendiğine değil.<br /><br /> Birden çok işlevine ilişkin belirtimlerden ayrı belirtebilirsiniz **INCLUDE** seçenekleri.<br /><br /> Kullanmayın **INCLUDE** ve **hariç** aynı ikili işlevlerde başvuran seçenekleri.<br /><br /> **Dahil** ile kod kapsamı desteklenmiyor.<br /><br /> `funcspec` bir olarak tanımlanmıştır:<br /><br /> [ad alanı\<separator1 >] [sınıf\<separator2 >] işlevi<br /><br /> \<separator1 > olan `::` yerel kod ve `.` yönetilen kod için.<br /><br /> \<separator2 > her zaman `::`<br /><br /> Joker karakter \* desteklenir. Örneğin, bir ad alanı kullanımda tüm işlevler eklemek için şunu yazın:<br /><br /> MyNamespace::\*<br /><br /> Kullanabileceğiniz **Vsınstr /DumpFuncs** belirtilen ikili işlevlerin tam adlarını listelemek için.|  
|**DumpFuncs**|Belirtilen görüntü içerisindeki fonksiyonları listeler. Hiçbir işaretleme gerçekleştirilmedi.|  
|**ExcludeSmallFuncs**|Küçük İşlevler, işlev çağrıları, izleme yapmayın kısa işlevleri dahil değildir. **ExcludeSmallFuncs** seçeneği, böylece geliştirilmiş izleme hızı için izleme yükü daha azdır sağlar.<br /><br /> Küçük işlevlerin dışlamayı da azaltır. *vsp* dosya boyutu ve analiz için gereken süre.|  
|**İşareti:**{**önce**`&#124;`**sonra**`&#124;`**üst**`&#124;`**alt**}`,funcname,markid`|Bir profili işareti (raporlardaki verileri sınırlandırmak üzere kullanılan tanımlayıcı) ekler başlangıç veya bitiş .vsp rapor dosyası içinde bir veri aralığı tanımlamak için kullanabilirsiniz.<br /><br /> **Önce** - hemen önce hedef işlev girişi.<br /><br /> **Sonra** - hedef işlev çıkmadan hemen sonra.<br /><br /> **Üst** - hemen sonra hedef işlev girişi.<br /><br /> **Alt** - hedef işlevindeki her iade işleminden hemen önce.<br /><br /> `funcname` -Hedef işlevin adı<br /><br /> `Markid` -Profil işaretinin tanımlayıcı olarak kullanılacak pozitif bir tamsayı (uzun).|  
|**Kapsamı**|İzleme kapsamayı gerçekleştirir. Yalnızca aşağıdaki seçenekler kullanılabilir: **ayrıntılı**, **OutputPath**, **hariç**, ve **Logfile**...|  
|**ayrıntılı**|**Ayrıntılı** seçeneği izleme işlemi hakkında ayrıntılı bilgi görüntülemek için kullanılır.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Tümünü Gizle veya belirli uyarıları.<br /><br /> `Message Number` -uyarı numarası. Varsa `Message Number` olan atlanırsa, tüm uyarıları görüntülenmez.<br /><br /> Daha fazla bilgi için [Vsınstr uyarıları](../profiling/vsinstr-warnings.md).|  
|**Denetim** `:{` **iş parçacığı** `&#124;` **işlem** `&#124;` **genel** `}`|Profil oluşturma şu Vsınstr veri koleksiyonu düzeyini belirtir seçeneklerini denetleme:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **İş parçacığı** -iş parçacığı düzeyinde veri koleksiyonu denetimi işlevleri belirtir. Profil oluşturma başlatıldı veya yalnızca geçerli iş parçacığı durduruldu. Diğer iş parçacıklarını profil oluşturma durumu etkilenmez. İş parçacığı varsayılandır.<br /><br /> **İşlem** -işlem düzeyinde profil oluşturma veri koleksiyonu denetimi işlevleri belirtir. Profil oluşturma başlatır veya geçerli işlemdeki tüm iş parçacıkları için durdurur. Diğer işlemlerin profil oluşturma durumu etkilenmez.<br /><br /> **Genel** -genel düzeyde (çapraz işlem) veri toplama denetimi işlevleri belirtir.<br /><br /> Profil oluşturma düzeyi belirtmezseniz, bir hata oluşur.|  
|**Başlangıç** `:{` **içinde** `&#124;` **dışında** `},funcname`|Veri toplama hedef işlevi ve bu işlev tarafından çağrılan alt işlevler için sınırlar.<br /><br /> **İçinde** -girişi hedef işlevi hemen sonra StartProfile işlevi ekler. Her iade işleminden hemen önce StopProfile işlevi hedef işlevi ekler.<br /><br /> **Dış** -hedef işlevi her çağrısının hemen önce StartProfile işlevi ekler. Her hedef işlevi çağrısı hemen sonra StopProfile işlevi ekler.<br /><br /> `funcname` -Hedef işlevin adı.|  
|**Askıya alma** `:{` **içinde** `&#124;` **dışında** `},funcname`|Hedef işlevi ve işlev tarafından çağrılan alt işlevleri için veri toplama dışlar.<br /><br /> **İçinde** -girişi hedef işlevi hemen sonra SuspendProfile işlevi ekler. Her iade işleminden hemen önce ResumeProfile işlevi hedef işlevi ekler.<br /><br /> **Dış** -girişi hedef işlevi hemen önce SuspendProfile işlevi ekler. Hedef işlevden çıkış hemen sonra ResumeProfile işlevi ekler.<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Hedef işlevi StartProfile işlevi içeriyorsa, daha önce SuspendProfile işlevi eklenir. Hedef işlevi StopProfile işlevi içeriyorsa, ResumeProfile işlevi sonra eklenir.|  
|**StartOnly:** `{` **önce** `&#124;` **sonra** `&#124;` **üst** `&#124;` **alt** `},funcname`|Profil oluşturma çalışması sırasında veri toplama başlar. Bunu, belirli bir konumda StartProfile API işlevi ekler.<br /><br /> **Önce** - hemen önce hedef işlev girişi.<br /><br /> **Sonra** - hedef işlev çıkmadan hemen sonra.<br /><br /> **Üst** - hemen sonra hedef işlev girişi.<br /><br /> **Alt** - hedef işlevindeki her iade işleminden hemen önce.<br /><br /> `funcname` -Hedef işlevin adı.|  
|**StopOnly:**{**önce**`&#124;`**sonra**`&#124;`**üst**`&#124;`**alt**}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. Bunu, belirli bir konumda StopProfile işlevi ekler.<br /><br /> **Önce** - hemen önce hedef işlev girişi.<br /><br /> **Sonra** - hedef işlev çıkmadan hemen sonra.<br /><br /> **Üst** - hemen sonra hedef işlev girişi.<br /><br /> **Alt** - hedef işlevindeki her iade işleminden hemen önce.<br /><br /> `funcname` -Hedef işlevin adı.|  
|**SuspendOnly:**{**önce**`&#124;`**sonra**`&#124;`**üst**`&#124;`**alt**}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. Bunu, belirli bir konumda SuspendProfile API ekler.<br /><br /> **Önce** - hemen önce hedef işlev girişi.<br /><br /> **Sonra** - hedef işlev çıkmadan hemen sonra.<br /><br /> **Üst** - hemen sonra hedef işlev girişi.<br /><br /> **Alt** - hedef işlevindeki her iade işleminden hemen önce.<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Hedef işlevi StartProfile işlevi içeriyorsa, daha önce SuspendProfile işlevi eklenir.|  
|**ResumeOnly:**{**önce**`&#124;`**sonra**`&#124;`**üst**`&#124;`**alt**}`,funcname`|Başlar veya veri toplama sırasında profil oluşturma yürütmesine sürdürür.<br /><br /> Sonra profil oluşturmayı başlatmak için genellikle kullanılan bir **SuspendOnly** seçeneği, profil oluşturma durduruldu. Bunu, belirli bir konumda ResumeProfile API ekler.<br /><br /> **Önce** - hemen önce hedef işlev girişi.<br /><br /> **Sonra** - hedef işlev çıkmadan hemen sonra.<br /><br /> **Üst** - hemen sonra hedef işlev girişi.<br /><br /> **Alt** - hedef işlevindeki her iade işleminden hemen önce.<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Hedef işlevi StopProfile işlevi içeriyorsa, ResumeProfile işlevi sonra eklenir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Vsınstr uyarıları](../profiling/vsinstr-warnings.md)   
 [Performans raporu görünümleri](../profiling/performance-report-views.md)