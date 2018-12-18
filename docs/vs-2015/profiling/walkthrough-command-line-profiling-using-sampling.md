---
title: 'İzlenecek yol: Örnekleme metodunu kullanarak komut satırı profil | Microsoft Docs'
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
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b46af3a5485f896e1a5014c094646f364876d0d0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752483"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>İzlenecek yol: Örnekleme Yöntemini Kullanarak Komut Satırı Profili Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu yönerge, nasıl bir uygulama komut satırı araçlarını kullanarak ve performans sorunlarını belirlemek için örnekleme profili gösterir.  
  
 Bu kılavuzda komut satırı araçlarını kullanarak yönetilen bir uygulama profili oluşturma işlemi adım adım ve uygulamada performans sorunlarını belirlemek ve ayırmak için örnekleme kullanın.  
  
 Bu kılavuzda, aşağıdaki adımları izler:  
  
-   Bir uygulamayı, komut satırı araçlarını kullanarak ve örnekleme profil.  
  
-   Performans sorunlarını bulun ve örneklenen profil oluşturma sonuçları analiz edin.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], veya [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Ara anlayış [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]  
  
-   Komut satırı araçları ile çalışma anlama Ara  
  
-   Bir kopyasını [PeopleTrax örneği](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Profil oluşturma tarafından sağlanan bilgiler ile çalışmak için hata ayıklama sembol bilgisi kullanılabilir olması en iyisidir.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Komut satırı örnekleme metodu kullanılarak profili oluşturma  
 Örnekleme tarafından belirli bir işlem düzenli aralıklarla etkin işlev belirlemek için yoklanabileceği bir profil oluşturma yöntemidir. Sonuçta elde edilen veriler işlem örneklendiğinde ne sıklıkta işlev çağrı yığının en üstünde olan sayısına sağlar.  
  
> [!NOTE]
>  Profil Oluşturma Araçlarının komut satırı araçları, Visual Studio yükleme dizini altındaki \Team Tools\Performance Tools alt dizininde yer alır. 64 bit bilgisayarlarda araçların 64-bit hem 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax 32-bit uygulamadır.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak PeopleTrax uygulama profiline  
  
1.  PeopleTrax örneği uygulamayı yüklemek ve uygulamanın yayın sürümünü oluşturun.  
  
2.  Bir komut istemi penceresi açın ve profil oluşturma araçları dizini için yerel yol ortam değişkenine ekleyin.  
  
3.  Çalışma dizini PeopleTrax ikili dosyaları içeren dizine geçin.  
  
4.  Uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5.  Profil Oluşturucu denetleyen komut satırı aracı olan VSPerfCmd.exe çalıştırarak profil oluşturmayı başlatın. Aşağıdaki komut, uygulama ve profil oluşturucu örnekleme modunda başlatır:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Profil Oluşturucu işlemiyle başlar ve PeopleTrax.exe işlemine ekler. Rapor dosyasına toplanan profil oluşturma verilerini yazmak profil oluşturucu işlemi başlatır.  
  
6.  Tıklayın **kişileri Al**.  
  
7.  Tıklayın **ExportData**.  
  
     Notepad açılır ve dışarı aktarılan verileri içeren yeni bir dosya görüntüler **PeopleTrax**.  
  
8.  Not Defteri'ni kapatın ve ardından kapatın **PeopleTrax** uygulama.  
  
9. Profil oluşturucuyu kapatın. Şu komutu yazın:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Ortam değişkenleri sıfırlamak için aşağıdaki komutu kullanın:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. Profil oluşturma verilerini the.vsp dosyasında depolanan sonuçları, aşağıdaki yöntemlerden birini kullanarak analiz edin:  
  
    -   Visual Studio IDE'de the.Vsp dosyasını açın.  
  
         — veya —  
  
    -   VSPerfReport.exe komut satırı aracını kullanarak bir virgülle ayrılmış değer (.csv) dosyası oluşturun. Dışında kullanım için raporlar üretmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, aşağıdaki komutu kullanın:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)   
 [Komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)   
 [Performans Raporu Görünümleri](../profiling/performance-report-views.md)



