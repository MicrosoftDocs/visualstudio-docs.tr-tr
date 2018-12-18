---
title: Dosya Aç komutunu kullanarak dosyaları görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 425433c3d67e654398fde1609b3f9c4d54e63648
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498731"
---
# <a name="display-files-by-using-the-open-file-command"></a>Dosya Aç komutunu kullanarak dosyaları görüntüleme
Aşağıdaki adımlar, IDE nasıl işlediğini açıklar **açık dosya** kullanılabilir olan komutunu **dosya** menüde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Adımları ayrıca nasıl projeleri bu komutu kaynaklanan çağrıları yanıt açıklar.  
  
 Kullanıcı tıkladığında **açık dosya** komutunu **dosya** menüsünde, bir dosyadan seçer **açık dosya** iletişim kutusunda aşağıdaki süreç gerçekleşir:  
  
1.  Çalıştırılan Belge tablosu kullanarak IDE dosyanın zaten projede açık olup olmadığını belirler.  
  
    -   Dosya açık değilse, IDE penceresi resurfaces.  
  
    -   Dosya açık değilse, IDE çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> her proje, proje dosyasını açabilirsiniz belirlemek için sorgulanamıyor.  
  
        > [!NOTE]
        >  Proje uygulamanızda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, projenizi, dosyayı açar düzeyini gösteren bir öncelik değeri sağlayın. Öncelik değerleri sağlanan <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> sabit listesi.  
  
2.  Her proje önemini gösteren bir öncelik düzeyi ile yanıt dosyasını açmak için bir proje olan üzerinde yerleştirir.  
  
3.  IDE, proje dosyası açılır belirlemek için aşağıdaki ölçütleri kullanır:  
  
    -   En yüksek öncelikli yanıt proje (`DP_Intrinsic`) dosyasını açar. Bu önceliğine sahip birden fazla proje yanıt verirse, yanıt için ilk proje dosyasını açar.  
  
    -   En yüksek önceliğe hiçbir proje yanıt verirse (`DP_Intrinsic`), ancak tüm projeleri yanıt aynı, daha düşük önceliğe etkin proje dosyasını açar. Hiçbir proje etkin olursa, yanıt için ilk proje dosyasını açar.  
  
    -   Proje dosyasının sahipliğini talep varsa (`DP_Unsupported`), çeşitli dosyalar projeleri dosyasını açar.  
  
         Çeşitli dosyalar projeleri örneği oluşturduysanız, proje her zaman değeri ile yanıt `DP_CanAddAsExternal`. Bu değer, proje dosyayı açabilmesini gösterir. Bu proje, başka bir projede olmayan açık dosyaları barındırmak için kullanılır. Bu projede öğelerin listesini kalıcı değil; Bu proje görülebilir **Çözüm Gezgini** yalnızca bir dosyayı açmaya kullanıldığında.  
  
         Çeşitli dosyalar projeleri dosyayı açabilmesini denenemeyeceğini belirtmiyorsa, proje örneği oluşturulmamış. Bu durumda, IDE çeşitli dosyalar projeleri örneği oluşturur ve dosyayı proje söyler.  
  
4.  Proje dosyası açılır IDE belirler hemen sonra çağrılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> proje yöntemi.  
  
5.  Proje, projeye özgü Düzenleyici ya da bir standart düzenleyici kullanarak dosyayı açma seçeneğini ardından sahiptir. Daha fazla bilgi için [nasıl yapılır: projeye özgü düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md) ve [nasıl yapılır: standart düzenleyicileri açma](../../extensibility/how-to-open-standard-editors.md)sırasıyla.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Birlikte Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Açın ve proje öğeleri Kaydet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Nasıl yapılır: projeye özgü düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md)   
 [Nasıl yapılır: standart düzenleyicileri açma](../../extensibility/how-to-open-standard-editors.md)