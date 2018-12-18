---
title: VSPerfCLREnv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5623cfc9d6f72805e4ced489ef7a786aaad155e6
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34446237"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

VSPerfCLREnv aracı, .NET Framework uygulama profili için gerekli ortam değişkenlerini ayarlamak için kullanılır. Aşağıdaki sözdizimini kullanır:

```cmd
VsPerfCLREnv [/option]
```

Seçtiğiniz seçeneği hangi, profil oluşturma üç tür kullanmasına bağlı olarak değişir: örnekleme, izleme, veya genel. Profil oluşturma verileri katman etkileşim verileri eklemek için ayrı bir seçenek gerekir. Aşağıdaki tablolarda her seçeneği söz dizimi açıklanmıştır.

> [!NOTE]
> İşiniz bittiğinde profil çalıştırmak **VSPerfCLREnv** ile **/ kapalı** veya **/globaloff** profil için gerekli ortam değişkenleri silmeye seçeneği. VSPerfCLREnv seçenekleri ortam burada gösterilen ayarları silmek için daha fazla bilgi için bkz.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Katman etkileşim verileri dahil etmek için VSPerfCLREnv seçenekleri

> [!WARNING]
> Katman etkileşim profil, herhangi bir sürümünü Visual Studio kullanarak toplanabilir. Ancak, katman etkileşimli profil oluşturma verilerini, yalnızca Visual Studio kuruluş içinde görüntülenebilir.

Katman etkileşim profil çok katmanlı uygulamalarda ADO.NET sorguları hakkında ek bilgi sağlar. Verileri yalnızca zaman uyumlu işlev çağrıları için toplanır. Etkileşim verileri herhangi bir profil oluşturma yöntemini kullanarak profil Çalıştır olarak eklenebilir.

**InteractionOn** ve **GlobalInteractionOn** seçeneklerini etkinleştirme katman etkileşim verileri koleksiyonu. Bir uygulama profili için gerekli olan VSPerfCLREnv ortam değişkeni ayarı sonra etkileşim seçeneği ayarlamanız gerekir.

Aşağıdaki örnek, katman etkileşim verileri örnekleme yöntemini kullanan bir profil çalıştırmada içerir:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Aşağıdaki örnek, bir Windows hizmeti için profil oluşturma çalıştırmada katman etkileşim verileri içerir:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp 
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>İşlem profil oluşturma araçları için VSPerfCLREnv seçenekleri

Aşağıdaki tabloda, profil oluşturma araçları için VSPerfCLREnv seçenekleri açıklanmaktadır:

|Seçenek|Açıklama|
|------------|-----------------|
|**TraceOn**|İzleme metodunu kullanarak profil oluşturmayı etkinleştirir. Profil oluşturma veya nesne yaşam verisi toplama bellek ayırma etkinleştirmez.|
|**TraceGC**|Bellek ayırma izleme metodunu kullanarak profil sağlar. Nesne ömrü veri toplama etkinleştirmez.|
|**TraceGCLife**|Profil oluşturma ve izleme metodunu kullanarak nesne yaşam verisi toplama bellek ayırma sağlar.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Örnekleme profili oluşturma işlemi için VSPerfCLREnv seçenekleri

Örnekleme profili oluşturma için VSPerfCLREnv seçenekleri aşağıdaki tabloda açıklanmaktadır:

|Seçenek|Açıklama|
|------------|-----------------|
|**SampleOn**|Örnekleme yöntemini kullanarak profil oluşturmayı etkinleştirir. Profil oluşturma veya nesne yaşam verisi toplama bellek ayırma etkinleştirmez.|
|**SampleGC**|Bellek ayırma örnekleme yöntemini kullanarak profil sağlar. Nesne ömrü veri toplama etkinleştirmez.|
|**SampleGCLife**|Bellek ayırma örnekleme yöntemini kullanarak profil sağlar. Ayrıca toplama nesne yaşam verisi sağlar.|
|**SampleLineOff**|.NET profil oluşturma verilerini satır düzeyi koleksiyonunu devre dışı bırakır.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Genel profil oluşturma için VSPerfCLREnv seçenekleri

Yönetilen hizmet gibi ve kullanıcı tarafından başlatılmakta yerine işletim sistemi tarafından başlatılan ASP.NET web uygulaması profili için VSPerfCLREnv seçenekleri genel profil oluşturma için seçenekleri kullanın. Aşağıdaki tabloda VSPerfCLREnv seçenekleri genel sürümlerini açıklar. Bu seçenekler, kayıt defterinde uygun ortam değişkenlerini ayarlayın.

|Seçenek|Açıklama|
|------------|-----------------|
|**GlobalTraceOn**|İzleme metodunu kullanarak genel profil oluşturmayı etkinleştirir. Bellek ayırma olayları veya nesne yaşam verisi toplamaz.|
|**GlobalTraceGC**|Genel bellek ayırma izleme metodunu kullanarak profil sağlar. Nesne ömrü veri toplama etkinleştirmez.|
|**GlobalTraceGCLife**|Genel bellek ayırma izleme metodunu kullanarak profil sağlar. Ayrıca nesne yaşam verisi koleksiyonunu sağlar.|
|**GlobalSampleOn**|Örnekleme yöntemini kullanarak genel profil oluşturmayı etkinleştirir. Toplama bellek ayırma olayları veya nesne yaşam verisi etkinleştirmez.|
|**GlobalSampleGC**|Örnekleme yöntemini kullanarak genel bellek ayırma profil oluşturmayı etkinleştirir. Nesne ömrü veri toplama etkinleştirmez.|
|**GlobalSampleGCLife**|Örnekleme yöntemini kullanarak genel bellek ayırma profil oluşturmayı etkinleştirir. Ayrıca toplama nesne yaşam verisi sağlar.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Ortam ayarları silmek için VSPerfCLREnv seçenekleri

 Yönetilen uygulama profili oluşturma işiniz bittiğinde, VSPerfCLREnv tarafından eklenen ortam değişkenleri silmek için aşağıdaki seçeneklerden birini kullanın. Aşağıdaki tabloda, hem standart hem de genel ortam değişkenlerini silme açıklar:

|Seçenek|Açıklama|
|------------|-----------------|
|**Kapalı**|Standart .NET profil oluşturma için ortam değişkenleri siler. Profil Oluşturucu ortam değişkenlerini ayarlamak için kullanılan genel olmayan VSPerfClrEnv seçenekleri olduğunda bu seçeneği kullanın.|
|**GlobalOff**|Genel .NET profil oluşturma için ortam değişkenleri siler. Uygulama işletim sistemi ve değil Profil Oluşturucu tarafından başlatıldığında bu seçeneği kullanın.|

## <a name="remarks"></a>Açıklamalar

Bu seçenekler IDE içinde performans Gezgini'ni kullanarak uygulama başlattıysanız, yönetilen bir uygulamaya profil oluşturma için gerekli değildir. Performans Gezgini, tüm gerekli ortam ayarlarını belirler.

Profil oluşturma sırasında doğru ortam ayarlı değil, bir uyarı çözümleme ve yönetilen işlev adları değil düzgün çözümlenir sırasında bildirilir.

## <a name="see-also"></a>Ayrıca bkz.

[Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)