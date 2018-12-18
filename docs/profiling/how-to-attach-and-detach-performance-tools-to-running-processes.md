---
title: Performans araçları çalıştırma işlemleri iliştirme
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb245b6930d1a633d5d5befa3266c3c7540c0915
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048534"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Nasıl yapılır: ekleme ve ayırma işlemleri çalıştırmak için performans araçları
Profil Oluşturucu ekleme veya örnekleme ve toplar performans verilerini daha kolay hale getirmek için çalışan bir işlemden ayırmak için kullanılabilir. Uygulama yükleme süresi hakkında veri toplama kaçınmak istiyorsanız ya da sonraki bir işlemin performansını izlemek için belirli bir duruma ulaştığında bir işlem profili için bu yöntemi kullanabilirsiniz.  
  
> [!NOTE]
>  Ekleme ve ayırma işlemleri içinden aşağıdaki adımları uygulamak [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] tümleşik geliştirme environmnent (IDE). Komut satırı araçlarının nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md). Profil hizmetler hakkında daha fazla bilgi için bkz. [profil Hizmetleri](../profiling/command-line-profiling-of-services.md).  
  
 Profili için kullanılabilir olan işlemleri, bilgisayarın yönetici tarafından ayarlanan kullanıcı erişimi izinleri bağlıdır. Örneğin, bir kullanıcı hesabı izni aşağıdakilerden herhangi biri olabilir:  
  
- Gelişmiş Özellikler, sürücü ve hizmeti başlatmak için yöneticiniz tarafından belirlenen zaman profil oluşturma.  
  
- Yalnızca (etki alanı kullanıcı) profil oluşturma örneği.  
  
- Herkes için profil oluşturma için erişimi engeller.  
  
  Daha fazla bilgi için [profil oluşturma ve Windows Vista Güvenliği](../profiling/profiling-and-windows-vista-security.md) ve yönetim seçeneklerini [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Çalışan bir işleme iliştirmek için  
  
1.  Üzerinde **hata ayıklama** menüsünde **Profiler**, ardından **performans Gezgini**ve ardından **iliştirme**.    
  
     **İşleme iliştirmek Profiler** iletişim kutusu görüntülenir.  
  
2.  Eklemek istediğiniz işlemin adını tıklayın.  
  
3.  Tıklayın **ekleme**.  
  
### <a name="to-detach-from-a-running-process"></a>Çalışan bir işlemden ayırmak için  
  
1.  n **hata ayıklama** menüsünde **Profiler**, ardından **performans Gezgini**ve ardından **ayırma**. 
  
     **İşleme iliştirmek Profiler** iletişim kutusu görüntülenir.  
  
2.  Ayırmak istediğiniz görüntü adına tıklayın.  
  
3.  Tıklayın **ayırma**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)   
 [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)   
 [Nasıl yapılır: Başlangıç ve bitiş performans verilerini toplama](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)