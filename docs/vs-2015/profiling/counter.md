---
title: Sayaç | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d0d15c404284dfb40105f7a52cb23aef132f3a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764941"
---
# <a name="counter"></a>Sayaç
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Sayacı** seçeneği işlemci (Donanım) performans sayaçlarından veri toplar.  
  
- Örnekleme profili oluşturma yöntemi, kullanırken **sayacı** yonga üzerinde performans sayacı ve örnekleme aralığı kullanılacak sayacı olay sayısını belirtir. Örnekleme kullanırken, yalnızca bir sayaç belirtebilirsiniz.  
  
- Yöntemi profil oluşturma Araçları'nı kullanırken, geçerli ve önceki toplama olayları arasındaki aralık içinde oluşan sayacı olay sayısı profil oluşturucusu raporu ayrı alanlar olarak listelenir. Birden çok **sayacı** seçenekleri araçları kullanırken belirtilebilir.  
  
  Her işlemci türü kendi donanım performans sayaç kümesi vardır. Profil Oluşturucu, neredeyse tüm işlemciler için ortak olan genel performans sayaçları kümesini tanımlar. Genel ve işlemciye özgü sayaçları bilgisayarınızda listelemek için VSPerfCmd kullanın **QueryCounters** komutu.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Name`  
 Sayaç adı. VSPerfCmd.exe kullanın **/querycounters** bilgisayardaki kullanılabilir sayaçların adlarını listelemek için seçeneği.  
  
 `Reload`  
 Örnekleme aralığı içinde sayacı olay sayısı. Cihaz atama yöntemi ile kullanmayın.  
  
 `FriendlyName`  
 (İsteğe bağlı) Yerine kullanılacak dize `Name` profil oluşturucu raporları ve görünümleri sütun başlıklarına.  
  
## <a name="required-options"></a>Gerekli seçenekleri  
 Sayaç seçeneği, yalnızca aşağıdaki seçeneklerden biriyle kullanılabilir:  
  
 **Başlat:** `Trace`  
 Şüpheli işlem yöntemini kullanan profil oluşturucuyu başlatır.  
  
 **Başlat:** `AppName`  
 Belirtilen uygulama ve profil oluşturucuyu başlatır. Profil Oluşturucu örnekleme yöntemini kullanmak için başlatılması gerekir.  
  
 **Ekleme:** `PID`  
 Profil oluşturucuyu başlatır ve işlem kimliği tarafından belirtilen işlem ekler Profil Oluşturucu örnekleme yöntemini kullanmak için başlatılması gerekir.  
  
## <a name="example"></a>Örnek  
 Örnekleme yöntemi örneği her 1000 yineleme uygulama NonHaltedCycles genel profil oluşturucu sayacın örnek gösterilmektedir.  
  
 İzleme metodu örnek L2InstructionFetches sayacı olaylarını toplamak için profil oluşturucuyu başlatmak nasıl gösterir. İşlemci L2InstructionFetches sayaç adı özeldir.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)



