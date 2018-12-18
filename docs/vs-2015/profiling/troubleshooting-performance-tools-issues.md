---
title: Sorunları araçları performans sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e9f75ad953ff9c6cd08e8eb78bcfbf01542223
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787932"
---
# <a name="troubleshooting-performance-tools-issues"></a>Performans sorunlarını giderme araçları sorunları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil oluşturma Araçları'nı kullandığınızda aşağıdaki sorunlardan biriyle karşılaşabilirsiniz:  
  
-   [Profil oluşturma araçları tarafından toplanan veri yok](#NoDataCollected)  
  
-   [Performans görünümleri ve raporlar için işlev adlarını sayıları görüntüleme](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Profil oluşturma araçları tarafından toplanan veri yok  
 Bir uygulamanın profilini sonra profil oluşturma veri (.vsp) dosyası oluşturulmaz ve çıktı penceresinde ya da komut penceresinde aşağıdaki uyarıyı alırsınız:  
  
 PRF0025: Hiçbir veri toplanamadı.  
  
 Bu sorunu çeşitli sorunları neden olabilir:  
  
-   Örnekleme veya .NET bellek yöntemi kullanarak profili oluşturulmuş bir işlem uygulama işi yapar işlem haline gelen bir alt işlemi başlatır. Örneğin, bazı uygulamalar, bir Windows uygulaması veya bir komut satırı uygulaması olarak başlatılmış olup olmadığını belirlemek için komut satırını okur. Bir Windows uygulaması istendi, özgün işlem bir Windows uygulaması olarak yapılandırılmış yeni bir işlem başlatır ve ardından özgün işlem çıkar. Profil oluşturma araçları otomatik olarak alt işlemleri için veri toplama için hiçbir veri toplanır.  
  
     Bu durumda profil oluşturma verilerini toplamak için profil oluşturucu uygulamaya Profil Oluşturucu ile başlatma yerine alt işlem ekleme. Daha fazla bilgi için [nasıl yapılır: Attach ve Detach, çalışan işlemler için performans araçları](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) ve [İliştir (VSPerfCmd)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> Performans görünümleri ve raporlar için işlev adlarını sayıları görüntüleme  
 Bir uygulamanın profilini sonra raporları ve görünümleri işlev adları yerine numaraları görürsünüz.  
  
 Bu sorun, kaynak kod bilgisi, bu işlev adları ve satır numaralarını derlenmiş dosyasına eşleşen sembol bilgilerini içeren .pdb dosyaları erişememe profil oluşturma araçları bir analiz motoru kaynaklanır. Uygulama dosyası oluşturulduğunda varsayılan olarak, derleyici .pdb dosyasını oluşturur. .Pdb dosyasının yerel dizin başvurusu derlenmiş uygulama depolanır. Analiz altyapısı, .pdb dosyasını başvurulan dizinini ve ardından şu anda uygulama dosyası içeren dosyayı arar. .Pdb dosyası bulunamazsa, bir analiz motoru işlevi uzaklıkları yerine işlev adlarını kullanır.  
  
 İki yoldan biriyle sorunu düzeltebilirsiniz:  
  
-   .Pdb dosyaları bulun ve uygulama dosyaları aynı dizine koyun.  
  
-   Sembol bilgilerini profil oluşturma veri (.vsp) dosyasına ekleyin. Daha fazla bilgi için [performans veri dosyalarıyla kaydetme sembol bilgilerini](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Analiz altyapısı, .pdb dosyasını derlenmiş uygulama dosyası aynı sürümde olmasını gerektirir. Önceki veya sonraki bir derleme uygulama dosyasının .pdb dosyasından çalışmaz.



