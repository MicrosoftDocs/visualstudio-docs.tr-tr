---
title: VSPerfCLREnv | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff359904b2b4d8b10dbc180f076606651028e80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741499"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCLREnv aracı, .NET Framework uygulamasına profil için gereken ortam değişkenlerini ayarlamak için kullanılır. Aşağıdaki sözdizimini kullanır:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 Seçtiğiniz seçenek olan, profil oluşturma üç tür kullandığınıza bağlıdır: örnekleme, izleme, ya da genel. Katman etkileşim verileri profil oluşturma verileri dahil etmek için ayrı bir seçenek gereklidir. Her seçeneği söz dizimi aşağıdaki tablolarda açıklanmıştır.  
  
> [!NOTE]
>  İşiniz bittiğinde profil oluşturma, çalıştırma **VSPerfCLREnv** ile **/ off** veya **/globaloff** profil oluşturmak için gereken ortam değişkenlerini silmeniz için seçeneği. Daha fazla bilgi için VSPerfCLREnv seçenekleri ortam burada gösterilen ayarları silmek için bkz.  
  
 **Katman etkileşim verileri ekleme VSPerfCLREnv seçenekleri**  
  
> [!WARNING]
>  Katman etkileşim profili oluşturma toplanacak kullanarak [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], veya [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Ancak, katman etkileşimli profil oluşturma veri yalnızca görüntülenebilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] ve [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 Katman etkileşim profili oluşturma, çok katmanlı uygulamalarda ADO.NET sorgularının hakkında ek bilgi sağlar. Verileri yalnızca zaman uyumlu işlev çağrıları için toplanır. Herhangi bir profil oluşturma yöntemini kullanarak tüm profil oluşturma yürütmesine etkileşim verileri eklenebilir.  
  
 **InteractionOn** ve **GlobalInteractionOn** seçenekleri katman etkileşim verilerinin toplanmasını sağlar. Sonra VSPerfCLREnv ortam değişkenini ayarlayarak bir uygulama profili için gerekli olan etkileşimi seçeneği ayarlanmalıdır.  
  
 Aşağıdaki örnek örnekleme yöntemini kullanan profil oluşturma yürütmesine katman etkileşim verileri içerir:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Aşağıdaki örnek bir Windows hizmeti için profil oluşturma yürütmesine katman etkileşim verileri içerir:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **VSPerfCLREnv seçeneklerini işlem izleme profil**  
  
 Aşağıdaki tabloda, profil oluşturma araçları için VSPerfCLREnv seçenekleri tanımlar:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**TraceOn**|Araçlar yöntemini kullanarak profil oluşturmayı etkinleştirir. Bellek ayırma profil oluşturma veya nesne yaşam süresi verilerini toplama etkinleştirmez.|  
|**TraceGC**|Bellek ayırma izleme metodunu kullanarak profili oluşturmayı etkinleştirir. Nesne yaşam verisi toplamayı etkinleştirmez.|  
|**TraceGCLife**|Bellek ayırma profil oluşturma ve izleme metodunu kullanarak nesne yaşam verisi toplamayı etkinleştirir.|  
  
 **İşlem örnekleme profil VSPerfCLREnv seçenekleri**  
  
 Örnekleme profil VSPerfCLREnv seçenekleri aşağıdaki tabloda açıklanmaktadır:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**SampleOn**|Örnekleme metodu kullanılarak profili oluşturma etkinleştirir. Bellek ayırma profil oluşturma veya nesne yaşam süresi verilerini toplama etkinleştirmez.|  
|**SampleGC**|Bellek ayırma örnekleme metodu kullanılarak profili oluşturmayı etkinleştirir. Nesne yaşam verisi toplamayı etkinleştirmez.|  
|**SampleGCLife**|Bellek ayırma örnekleme metodu kullanılarak profili oluşturmayı etkinleştirir. Ayrıca nesne yaşam verisi toplamayı sağlar.|  
|**SampleLineOff**|.NET profil oluşturma verilerini satır düzeyi koleksiyonunu devre dışı bırakır.|  
  
 **Genel profil oluşturma için VSPerfCLREnv seçenekleri**  
  
 Gibi yönetilen hizmet ve işletim sistemi yerine kullanıcı tarafından başlatıldı başlatan, ASP.NET web uygulamasının profilini çıkarmak için seçenekleri VSPerfCLREnv seçenekleri genel profil oluşturma için kullanın. Aşağıdaki tabloda, genel sürümlerini VSPerfCLREnv seçenekleri açıklar. Bu seçenekler, kayıt defterinde uygun ortam değişkenlerini ayarlayın.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**GlobalTraceOn**|Araçlar yöntemini kullanarak genel profil oluşturma sağlar. Bellek ayırma olayları veya nesne yaşam süresi verilerini toplamaz.|  
|**GlobalTraceGC**|Araçlar yöntemini kullanarak genel bellek ayırma profil oluşturma sağlar. Nesne yaşam verisi toplamayı etkinleştirmez.|  
|**GlobalTraceGCLife**|Araçlar yöntemini kullanarak genel bellek ayırma profil oluşturma sağlar. Ayrıca nesne yaşam süresi verilerinin toplanmasını sağlar.|  
|**GlobalSampleOn**|Örnekleme metodu kullanılarak genel profil oluşturma sağlar. Bellek ayırma olayları toplamak veya nesne yaşam verisi etkinleştirmez.|  
|**GlobalSampleGC**|Örnekleme metodu kullanılarak genel bellek ayırma profil oluşturma sağlar. Nesne yaşam verisi toplamayı etkinleştirmez.|  
|**GlobalSampleGCLife**|Örnekleme metodu kullanılarak genel bellek ayırma profil oluşturma sağlar. Ayrıca nesne yaşam verisi toplamayı sağlar.|  
  
 **Ortam ayarları silmek için VSPerfCLREnv seçenekleri**  
  
 Yönetilen uygulama profil oluşturmayı tamamladığınızda, VSPerfCLREnv tarafından eklenen ortam değişkenlerini silmek için aşağıdaki seçeneklerden birini kullanın. Aşağıdaki tabloda, her iki standart ve genel ortam değişkenlerini silmeniz açıklar:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Kapalı**|Standart .NET profil oluşturma ortam değişkenlerini siler. Profil Oluşturucu ortam değişkenlerini ayarlamak için kullanılan genel olmayan VSPerfClrEnv seçenekleri olduğunda bu seçeneği kullanın.|  
|**GlobalOff**|Genel .NET profil oluşturma ortam değişkenlerini siler. İşletim sistemi olmayan Profil Oluşturucu ile uygulama başlatıldığında, bu seçeneği kullanın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenekler, IDE içinde performans Gezgini kullanarak uygulama başlatıldığında, yönetilen bir uygulamaya profil oluşturma için gerekli değildir. Performans Gezgini, tüm gerekli ortam ayarlarını belirler.  
  
 Profil oluşturma sırasında doğru ortamı ayarlı değil, bir uyarı çözümleme ve yönetilen işlev adları değil düzgün çözümlenir sırasında bildirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)



