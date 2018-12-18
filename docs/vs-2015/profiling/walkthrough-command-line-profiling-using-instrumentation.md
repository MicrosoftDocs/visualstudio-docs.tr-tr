---
title: 'İzlenecek yol: İzleme metodunu kullanarak komut satırı profil | Microsoft Docs'
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
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b670ef29ca2edcc96ed8886b82dd5d7c6cb416b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741461"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>İzlenecek yol: İzleme Yöntemini Kullanarak Komut Satırı Profili Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, profil oluşturma ile alır. bir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ayrıntılı zamanlama toplayıp çağrı sayısı verileri profil oluşturma Araçları'nın izleme metodunu kullanarak tek başına uygulama. Bu kılavuzda, aşağıdaki görevleri yerine getirmiş olacaksınız:  
  
-   Kullanım [Vsınstr](../profiling/vsinstr.md) izleme eklenmiş ikili dosyaları oluşturmak için komut satırı aracı.  
  
-   Kullanım [VSPerfCLREnv](../profiling/vsperfclrenv.md) .NET profil oluşturma verilerini toplamak için ortam değişkenlerini ayarlamak için aracı.  
  
-   Kullanım [VSPerfCmd](../profiling/vsperfcmd.md) profil oluşturma verilerini toplamak için aracı.  
  
-   Kullanım [VSPerfReport](../profiling/vsperfreport.md) aracı profil oluşturma verilerinin dosya tabanlı raporlar oluşturmak için.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
-   C# Ara anlama  
  
-   Komut satırı araçları ile çalışma anlama Ara  
  
-   Bir kopyasını [PeopleTrax örneği](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Profil oluşturma tarafından sağlanan bilgiler ile çalışmak için hata ayıklama sembol bilgisi kullanılabilir olması en iyisidir. Daha fazla bilgi için [nasıl yapılır: başvuru Windows sembol bilgilerini](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Komut satırı izleme metodunu kullanarak profili oluşturma  
 İzleme profili oluşturulmuş ikili dosyalar özel olarak oluşturulmuş sürümleri işaretlenmiş modülde işlevlere giriş ve çıkış zamanlama bilgilerini toplamak araştırma işlevleri içerir bir profil oluşturma yöntemidir. Bu profil oluşturma yöntemi örnekleme değerinden daha bozucu olduğu için büyük miktarda bir ek yük doğurur. İzlenen ikili dosyaların hatalarını ayıklama veya ikili dosyaları sürüm ve dağıtım için hedeflenmemiş büyük.  
  
> [!NOTE]
>  İzleme eklenmiş ikili dosyalar, müşterilerinize göndermeyin. İzleme eklenmiş ikili dosyalar, çeşitli riskleri taşıyabilir. İkili dosyaları, uygulamanızı ters mühendislik, yanı sıra güvenlik risklerini daha kolay anlaşılır bilgileri içerir.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Araçlar yöntemini kullanarak PeopleTrax uygulama profiline  
  
1.  PeopleTrax örneği uygulamayı yüklemek ve yayın sürümünü oluşturun.  
  
2.  Bir komut istemi penceresi açın ve eklemek **profil oluşturma araçları** yerel yol ortam değişkenine dizin.  
  
3.  Çalışma dizini PeopleTrax ikili dosyaları içeren dizine geçin.  
  
4.  Dosya tabanlı raporlar içerecek bir dizin oluşturun. Şu komutu yazın:  
  
    ```  
    md Reports  
    ```  
  
5.  Uygulama içindeki ikili dosyaları araç haline getirmek için Vsınstr komut satırı aracını kullanın. Komut ayrı satırlarda aşağıdaki komutları yazın:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Not** varsayılan olarak, özgün dosya belgelenmiş bir yedeğini Vsınstr kaydeder. Yedekleme dosya adı uzantısına sahip. orig. Örneğin, "MyApp.exe" orijinal sürümünü "MyApp.exe.orig" kaydedilecektir  
  
6.  Uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  Profil oluşturucuyu başlatmak için aşağıdaki komutu yazın:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  Profil Oluşturucu izleme modunda başlattıktan sonra veri toplama PeopleTrax.exe işlemini belgelenmiş sürümünü çalıştırın.  
  
     **PeopleTrax** uygulama penceresi görünür.  
  
9. Tıklayın **kişileri Al**.  
  
     PeopleTrax veri kılavuzu verilerle doldurur.  
  
10. Tıklayın **verileri dışarı aktar**.  
  
     Not Defteri'ni başlar ve kişilerden listesini içeren yeni bir dosya görüntüler **PeopleTrax** uygulama.  
  
11. Not Defteri'ni kapatın ve ardından kapatın **PeopleTrax** uygulama.  
  
12. Profil oluşturucuyu kapatın. Şu komutu yazın:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Ortam değişkenleri sıfırlamak için aşağıdaki komutu yazın:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Oluşturmak için VSPerfReport aracı veya virgülle ayrılmış değer (.csv) rapor dosyalarını kullanın. Tür:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Bir elektronik tablo programında oluşturulan raporları çözümleyebilir veya kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Report.vsp dosyasında profil oluşturma verilerini analiz etmek için IDE. Daha fazla bilgi için [performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)   
 [Komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)   
 [Performans Raporu Görünümleri](../profiling/performance-report-views.md)



