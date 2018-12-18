---
title: Sorunları araçları performans sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 531080945413bbc0959d2cdf91e2096c1e51f61d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677139"
---
# <a name="troubleshoot-performance-tools-issues"></a>Performans sorunlarını giderme
Profil oluşturma Araçları'nı kullandığınızda aşağıdaki sorunlardan biriyle karşılaşabilirsiniz:  
  
-   [Profil oluşturma araçları tarafından toplanan veri yok](#no-data-is-collected-by-the-profiling-tools)  
  
-   [Performans görünümlerinde ve raporlarında sayılar için işlev adlarını görüntüle](#performance-views-and-reports-display-numbers-for-function-names)  
  
## <a name="no-data-is-collected-by-the-profiling-tools"></a>Profil oluşturma araçları tarafından toplanan veri yok  
 Profil oluşturma verilerinin bir uygulama profili sonra (. *Vsp*) dosyası oluşturulmaz ve aşağıdaki uyarıyı alırsınız **çıkış** penceresi ya da komut penceresinde:  
  
 PRF0025: Hiçbir veri toplanamadı.  
  
 Bu sorunu çeşitli sorunları neden olabilir:  
  
-   Örnekleme veya .NET bellek yöntemi kullanarak profili oluşturulmuş bir işlem uygulama işi yapar işlem haline gelen bir alt işlemi başlatır. Örneğin, bazı uygulamalar, bir Windows uygulaması veya bir komut satırı uygulaması olarak başlatılmış olup olmadığını belirlemek için komut satırını okur. Bir Windows uygulaması istendi, özgün işlem bir Windows uygulaması olarak yapılandırılmış yeni bir işlem başlatır ve ardından özgün işlem çıkar. Profil oluşturma araçları otomatik olarak alt işlemleri için veri toplama için hiçbir veri toplanır.  
  
     Bu durumda profil oluşturma verilerini toplamak için profil oluşturucu uygulamaya Profil Oluşturucu ile başlatma yerine alt işlem ekleme. Daha fazla bilgi için [nasıl yapılır: iliştirme ve performans araçlarını çalışan işlemlere ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) ve [İliştir (VSPerfCmd)](../profiling/attach.md)  
  
## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Performans görünümlerinde ve raporlarında sayılar için işlev adlarını görüntüle  
 Bir uygulamanın profilini sonra raporları ve görünümleri işlev adları yerine numaraları görürsünüz.  
  
 Bu sorunu bulmak çözememesi profil oluşturma araçları analiz altyapısı tarafından neden olur. *pdb* haritalar kod bilgileri gibi işlev adları ve satır numaralarını derlenmiş dosyasına kaynak sembol bilgilerini içeren dosyaları. Varsayılan olarak, derleyici oluşturur. *pdb* uygulama dosyası yapılandırıldığında dosyası. Yerel dizinden bir başvuru. *pdb* derlenmiş uygulamada saklanır. Analiz altyapısı için başvurulan bir dizini arar. *pdb* dosya ve ardından dosyasında şu anda uygulama dosyasını içeren. Varsa. *pdb* dosya bulunamadı, analiz altyapısı işlevi uzaklıkları yerine işlev adlarını kullanır.  
  
 İki yoldan biriyle sorunu düzeltebilirsiniz:  
  
-   Bulun. *pdb* dosyaları ve uygulama dosyaları aynı dizine koyun.  
  
-   Sembol bilgilerini profil oluşturma verileri ekleme (. *Vsp*) dosyası. Daha fazla bilgi için [sembol bilgilerini performans veri dosyalarını Kaydet](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Analiz altyapısı gerektirir. *pdb* derlenmiş uygulama dosyası aynı sürüme dosyasıdır. A. *pdb* uygulama dosyasının bir önceki veya sonraki derleme dosyasından çalışmaz.