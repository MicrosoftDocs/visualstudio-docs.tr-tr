---
title: Performans oturumu özellikleri | Microsoft Docs
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
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
ms.assetid: c3a86913-172b-488f-a31a-cea01a71b2ea
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed020d09bc3c7b85a395625f410f0062bf4bfac9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739283"
---
# <a name="performance-session-properties"></a>Performans Oturum Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A **performans oturumu** nasıl uygulama profili oluşturulmuş belirleyen ayarları yapılandırmanızı sağlar. Ayrıca, profil oluşturma oturumu için oluşturulan raporlar depolar.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Oluşturduğunuz bir **performans oturumu** çalıştırarak **performans Sihirbazı** veya el ile bir oturumu oluşturma. **Performans oturumu** görüntülenen **performans Gezgini** sonra **performans oturumu** oluşturuldu.  
  
  Görüntülemek için **performans oturumu** özellikler, oturumun adı **performans Gezgini**, sağ tıklayın ve ardından **özellikleri**.  
  
  Performans oturumu aşağıdaki özellik sayfaları sahiptir:  
  
## <a name="general"></a>Genel  
 Yöntemi, .NET nesne koleksiyonu ve yaşam süresi verisi eklemek ve varsayılan rapor konumu belirtmek için profil oluşturma ve adlandırma seçmek bu ayarları etkinleştirmeniz kuralları.  
  
 Daha fazla bilgi için bkz.:  
  
 [Nasıl Yapılır: Toplama Metotlarını Seçme](../profiling/how-to-choose-collection-methods.md)  
  
 [.NET Bellek Ayırma ve Yaşam Süresi Verilerini Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Nasıl Yapılır: Performans Veri Dosyası Adlandırma Seçeneklerini Ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)  
  
## <a name="launch"></a>Başlat  
 Bu ayarlar, ikili dosyalar listesinden seçin ve ikili dosyalarının başlatma sırasını belirtmek etkinleştirin.  
  
 Daha fazla bilgi için [nasıl yapılır: başlatma için ikili dosya belirtme](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="sampling"></a>Örnekleme  
 Bu ayarlar, örnekleme profil oluşturma yöntemi olarak kullanıldığında, örnek olay ve örnekleme aralığı seçmenize olanak sağlar. Örnek olay, belirtilen zaman aralığı profil oluşturma verilerini toplamak için kullanılır. Örneğin, saat döngüleri örnek olayı olduğu ve örnekleme aralığı için profil oluşturma verilerini 10,000,000 ayarlanırsa sonra her 10 milyon toplanır saat döngüleri. Örnek olay aşağıdaki dört türleri kullanılabilir:  
  
- Saat döngüsü - CPU sorunlarını bağlı.  
  
- Sayfa hataları - bellek ile ilgili sorunlar  
  
- Sistem çağrıları - g/ç için ilgili sorunlar  
  
- -Alt düzey performans sorunları, performans sayaçları  
  
- Ek örnek olaylar ulaşılabilir performans sayaçları tabanlı belirtilebilir.  
  
  Daha fazla bilgi için [nasıl yapılır: örnekleme olayları seçin](../profiling/how-to-choose-sampling-events.md)  
  
## <a name="binary"></a>İkili  
 Bu ayarlar, başka bir konuma işaretlenmiş ikilileri yeniden Yerleştir isteyip istemediğinizi belirtmek etkinleştirin. Örneğin, My.DLL profil ve işaretlenmiş ikilileri yeniden Yerleştir değil tercih My.Orig.DLL adlı My.DLL yedek bir kopyası oluşturulur. My.DLL verileri toplamak için araştırmalar ekleyerek daha sonra değiştirildi. İşaretlenmiş ikilileri yeniden Yerleştir karar verirseniz, özgün ikiliyi yeniden adlandırılmaz ve izleme eklenmiş ikili izleme sırasında kullanım için belirtilen konuma kopyalanır.  
  
 Daha fazla bilgi için [nasıl yapılır: başlatma için ikili dosya belirtme](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="tier-interactions"></a>Katman etkileşimleri  
 Daha fazla bilgi için [katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)  
  
## <a name="instrumentation"></a>İzleme  
 Bu ayarlar, JScript kod için performans verilerini toplamak etkinleştirdiğiniz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] belirtmek ve Web sayfaları **işaretleme öncesi** ve **son izleme** önce veya sonra gerçekleşmesini istediğiniz olayları izleme işlemi.  
  
 Daha fazla bilgi için bkz.:  
  
 [Nasıl Yapılır: Web Sayfalarında JavaScript Kodunun Profilini Oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)  
  
 [Nasıl Yapılır: Ön ve Son İzleme Komutları Belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)  
  
## <a name="cpu-counters"></a>CPU sayaçları  
 Bu ayarlar yönteminin profil oluşturma Araçları'nı kullanırken CPU performans sayaçları hakkında veri toplamak etkinleştirin. Taşınabilir performans sayaçları, CPU tasarım veya üretici bağımsız olarak kullanılabilir. Platform olayı CPU tasarım ve üretici özgüdür. Yonga üzerinde performans sayaçları hakkında daha fazla bilgi için belirli bir işlemci belgelerine bakın.  
  
 Daha fazla bilgi için [nasıl yapılır: CPU sayaç verileri toplama](../profiling/how-to-collect-cpu-counter-data.md)  
  
## <a name="windows-events"></a>Windows Olayları  
 Profil oluşturma sırasında olay izleme sağlayıcılarını veri toplayabilir. VSPerfReport.exe komut satırı aracını kullanarak verileri görüntüleyebilirsiniz `/calltrace` seçeneği. İlgili olay izleme için Windows (ETW) daha fazla bilgi için [hakkında olay izleme](http://go.microsoft.com/fwlink/?linkid=90752).  
  
 Daha fazla bilgi için bkz.:  
  
 [Nasıl Yapılır: Windows İçin Olay İzleme (ETW) Verileri Toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)  
  
 [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="windows-counters"></a>Windows sayaçları  
 Bu seçenek Windows Performans İzleyicisi sayaçları veri toplamanızı sağlar. Bu verileri toplamak için etiketli onay kutusunu seçin. **Windows performans sayaçlarını Topla**. Koleksiyon aralığı ayarlanabilir **koleksiyon aralığı** kutusu. **Sayaç kategorisi** ve **örneği** kullanılabilir olabilir. Bazı varsayılan Windows Performans İzleyicisi sayaçları kullanılabilir.  
  
 Daha fazla bilgi için [nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md).  
  
## <a name="advanced"></a>Gelişmiş  
 Bu ayarlar bir veya daha fazla seçeneklerini belirterek izleme işleme seçenekleri eklemenize olanak tanıyan [Vsınstr](../profiling/vsinstr.md) komut satırı aracı profil oluşturma. Uygulama birden fazla sürümünü kullandığında, profil için ortak çalışma zamanı sürümünü belirtebilirsiniz.  
  
 Daha fazla bilgi için bkz.:  
  
 [Nasıl Yapılır: .NET Framework Çalışma Zamanını Belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)  
  
 [Nasıl Yapılır: Ek İzleme Seçeneklerini Belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel bakış](../profiling/overviews-performance-tools.md)   
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Veri Koleksiyonunu Denetleme](../profiling/controlling-data-collection.md)



