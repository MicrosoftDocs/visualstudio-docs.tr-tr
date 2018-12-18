---
title: Performans oturum özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ce4fb6b9a57db78e3dbb7f3082a87df9ffb7360
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254699"
---
# <a name="performance-session-properties"></a>Performans oturumu özellikleri

A **Performans oturumunu** nasıl uygulama profili belirleyen ayarları yapılandırmanıza olanak sağlar. Ayrıca, profil oluşturma oturumu için oluşturulan raporlar depolar.

Oluşturduğunuz bir **Performans oturumunu** çalıştırarak **performans Sihirbazı** veya el ile bir oturum oluşturarak. **Performans oturumunu** görüntülenen **performans Gezgini** sonra **Performans oturumunu** oluşturuldu.

Görüntülemek için **Performans oturumunu** özellikler, oturum adı **performans Gezgini**, sağ tıklatın ve ardından **özellikleri**.

Performans oturumunu aşağıdaki özellik sayfaları vardır:

## <a name="general"></a>Genel

Bu ayarları profili oluşturma yöntemi, .NET nesne koleksiyonu ve yaşam verisi eklemek ve varsayılan rapor konumu belirtmek için ve adlandırma seçmenizi sağlar kuralları.

Daha fazla bilgi için bkz.:

[Nasıl yapılır: Toplama metotlarını seçme](../profiling/how-to-choose-collection-methods.md)

[.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

 [Nasıl yapılır: Performans veri dosyası adlandırma seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Başlat

Bu ayarlar, ikili dosyalar listesinden seçin ve ikili dosyaları başlangıç sırasını belirtmenize olanak sağlar.

Daha fazla bilgi için bkz: [nasıl yapılır: başlatmak için ikili belirtin](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="sampling"></a>Örnekleme

Bu ayarlar örnekleme profili oluşturma yöntemi olarak kullanıldığında, örnek olay ve örnekleme aralığı seçmenize olanak sağlar. Örnek olayı, belirli aralıklarla profil oluşturma verileri toplamak için kullanılır. Örneğin, saat döngüleri örnek olayı olduğunda ve örnekleme aralığı veri profil oluşturma 10,000,000 sonra her 10 milyon toplanan ise saat döngüleri. Örnek olaylar aşağıdaki dört türleri kullanılabilir:

- Saat döngüleri - CPU sorunlarını bağlı.
- Sayfa hataları - belleği ilgili sorunları
- Sistem çağrıları - g/ç için ilgili sorunlar
- -Alt düzey performans sorunları için performans sayaçları
- Kullanılabilir performans sayaçlarına göre ek örnek olaylar belirtilebilir.

Daha fazla bilgi için bkz: [nasıl yapılır: örnekleme olayları seçme](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>İkili
Bu ayarlar, izleme eklenmiş ikili başka bir konuma taşıyabilir isteyip istemediğinizi belirtmenizi sağlar. Örneğin, profil, *My.DLL* ve izleme eklenmiş ikili, yedek bir kopyasını taşıyabilir değil seçin *My.DLL* adlı *My.Orig.DLL* oluşturulur. Sonuç olarak, *My.DLL* verileri toplamak için araştırmalar ekleyerek değiştirilir. İzleme eklenmiş ikili taşıyabilir karar verirseniz, özgün ikili yeniden adlandırılmaz ve izleme eklenmiş ikili sırasında araçları kullanmak için belirtilen konuma kopyalanır.

Daha fazla bilgi için bkz: [nasıl yapılır: başlatmak için ikili belirtin](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Katman etkileşimleri

Daha fazla bilgi için bkz: [katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>İzleme

JScript kodda için performans verilerini toplamak bu ayarları etkinleştirmeniz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web sayfaları ve herhangi belirtmek **ön izleme** ve **sonrası Gereci** önce veya sonra gerçekleştirilmesini istediğiniz olayları izleme işlemi.

Daha fazla bilgi için bkz.:

[Nasıl yapılır: web sayfalarında profili JavaScript kodu](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Nasıl yapılır: Ön ve son izleme komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>CPU sayaçları

Bu ayarlar, izleme profili oluşturma yöntemi kullanırken CPU performans sayaçları hakkında veri toplamak etkinleştirin. Taşınabilir performans sayaçları, CPU tasarım veya üretici bağımsız olarak kullanılabilir. Platform olayları CPU tasarım ve üretici özgüdür. Yongadaki performans sayaçları hakkında daha fazla bilgi için belirli işlemci belgelerine bakın.

Daha fazla bilgi için bkz: [nasıl yapılır: toplamak CPU sayaç verileri](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Windows olayları

Profil oluşturma sırasında olay izleme sağlayıcılarından verileri toplayabilir. Kullanarak verileri görüntüleyebilirsiniz *VSPerfReport.exe* komut satırı aracı `/calltrace` seçeneği. İlgili olay Windows için izleme (ETW) daha fazla bilgi için bkz: [hakkında olay izleme](http://go.microsoft.com/fwlink/?linkid=90752).

Daha fazla bilgi için bkz.:

[Nasıl yapılır: Windows için olay izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Windows sayaçları

Bu seçenek, Windows Performans İzleyicisi sayaçları veri toplamanıza olanak sağlar. Bu verileri toplamak için etiketli onay kutusunu seçin. **Windows performans sayaçlarını Topla**. Toplama aralığı ayarlanabilir **toplama aralığı** kutusu. **Kategori sayacı** ve **örneği** de kullanılabilir. Bazı varsayılan Windows Performans İzleyicisi sayaçları kullanılabilir.

 Daha fazla bilgi için bkz: [nasıl yapılır: toplamak Windows sayaç verileri](../profiling/how-to-collect-windows-counter-data.md).

## <a name="advanced"></a>Gelişmiş

Bu ayarlar, bir veya daha fazla seçenekleri belirterek araçları işleme seçenekleri eklemenizi sağlayan [Vsınstr](../profiling/vsinstr.md) komut satırı aracı profili oluşturma. Uygulama birden fazla sürümünü kullanırken profiline ortak çalışma zamanı sürümü de belirtebilirsiniz.

Daha fazla bilgi için bkz.:

[Nasıl yapılır: .NET Framework çalışma zamanını belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Nasıl yapılır: Ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Ayrıca bkz.

[Genel Bakışlar](../profiling/overviews-performance-tools.md)  
[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)  
[Veri toplamayı denetleme](../profiling/controlling-data-collection.md)