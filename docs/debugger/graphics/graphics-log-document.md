---
title: Grafik günlük belgesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eab888fa800e8be695b6dca4cf38f2a0ed478ebb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931109"
---
# <a name="graphics-log-document"></a>Grafik Günlük Belgesi
Grafik günlük belgesi uygulamanızı grafik Tanılama oturumu altında çalışırken oluşan bir grafik olaylarını kaydıdır. Kaydedilen sonra Visual Studio grafik Çözümleyicisi aygıtını işleme ve performans sorunlarını tanılama günlüğüne inceleyebilirsiniz.  

 Bu grafik Çözümleyicisi'nde göründüğünü hangi bir grafik günlük belgesi.  

 ![İki yakalanan kareleri içeren bir grafik günlüğü. ](media/gfx_diag_demo_graphics_log_orientation.png "gfx_diag_demo_graphics_log_orientation")  

## <a name="understanding-graphics-log-documents"></a>Belgeler anlama grafik oturumu  
 Grafik günlük belgesi incelemek için grafik Çözümleyicisi'ni kullanarak, yakalama sırasında oluşan işleme hedefi Direct3D olayları etkilerini görselleştirebilirsiniz. İşleme hedefinin beklenmeyen çıkış içeren bölgeler saptayabilirler. Etkilenen bölgede bir piksel seçtiğinizde, kendi gölgelendiricileri, etkilenen Direct3D olayları, bu olayları için yönetilen uygulama çağrı yığını ve bu olayları destekleyen DirectX nesneleri incelemek için grafik tanılama kullanabilirsiniz. Oyunlarda veya uygulamalarda işleme sorunları tanılamak için bu bilgileri kullanabilirsiniz.  

 Pencerenin üst kısmında (**grafik Experiment.vsglog**) geçerli işleme hedefi çıktısı Seçilen çerçevenin alt bölümü görüntüler ve görüntüler bir **çerçeve listesi** küçük resim görüntülerini içerir yakalanan çerçeve.  

#### <a name="to-inspect-a-frame"></a>Bir çerçeveyi incelemek için  

-   İçinde **çerçeve listesi**, incelemek istediğiniz çerçeveyi seçin. İşleme hedefi çıktısı grafik günlük belgesi üst kısmında seçilen çerçevenin görüntülemek için güncelleştirilir.  

#### <a name="to-inspect-a-pixel"></a>Bir pikselin incelemek için  

-   Grafik günlük belgesi üst kısmında, işleme hedefi çıktısı istediğiniz piksel seçin. Bir pikselin seçildiğinde, kullanabileceğiniz **grafik piksel geçmişi** seçilen piksel hakkında ayrıntılı bilgi görüntülemek için pencere. Daha fazla bilgi için [piksel geçmişi](graphics-pixel-history.md).  

## <a name="playback-machine"></a>Kayıttan yürütme makinesi  
 Ayrıca sağ üst köşesinde görüntülenen **çerçeve listesi** olduğu **kayıttan yürütme makinesi**. Kayıttan yürütme makinesi, bir makine ya da grafik olaylarını bir grafik günlüğü dosyasından daha yeni bir grafik Tanılama oturumu sırasında kayıttan yürütmek için kullanılan cihaz ' dir. Yakalanan olaylar kayıttan yürütmek için geliştirme makinenizi yerine farklı bir cihaz kullanarak tarafından sorun oluştuğu yürütme ortamı daha doğru bir şekilde üretebileceği — Örneğin, farklı grafik donanımının veya sürücüleri olan bir makine kullanabilirsiniz. Geliştirme makinenizde kullanan olanları veya diğer tür cihazlar, bir tablet ARM tabanlı Windows RT veya Windows Phone cihazı gibi.  

 Kayıttan yürütme makinesi belirtme hakkında daha fazla bilgi için bkz: [nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme](how-to-change-the-graphics-diagnostics-playback-machine.md).  

## <a name="graphics-log-summary-information"></a>Grafik günlük özet bilgileri  
 Grafik günlük dosyası etkin belgede olduğunda **özellikleri** penceresi, grafik tanılama yakalama oturumu barındırılan ortamıyla ilgili bilgileri görüntüler. Bilgi çeşitli kategorilerde görüntülenir.  

 **Direct3D bilgileri**  
 Yakalama oturumu sırasında kullanılan görüntü bağdaştırıcısı donanım ve sürücü özellikleri hakkında bilgileri listeler.  

|Özellik|Açıklama|  
|--------------|-----------------|  
|**10-bit XR yüksek renk biçimi**|**Doğru** 10-bit XR yüksek renk biçimi desteklenen; Aksi takdirde ise **False**.|  
|**DirectCompute CS 4.x**|**Doğru** Compute gölgelendirici 4.0 ise, desteklenen; Aksi takdirde **False**.|  
|**Çift duyarlık gölgelendiricileri**|**Doğru** çift duyarlıklı kayan nokta değerleri (64-bit); görüntü bağdaştırıcısı destekliyorsa, aksi takdirde, **False**.|  
|**Sürücü komut listeleri**|**Doğru** sürücü komut listeleri; destekliyorsa, aksi takdirde, **False**.|  
|**Sürücü eşzamanlı oluşturmaları**|**Doğru** sürücü eşzamanlı (uyumsuz) oluşturma; destekliyorsa, aksi takdirde, **False**.|  
|**Genişletilmiş biçimler (BGRA, vs.)**|**Doğru** BGRA gibi genişletilmiş biçimler, desteklenen; Aksi takdirde **False**.|  
|**Maksimum donanım özelliği düzeyi**|Görüntü bağdaştırıcısı tarafından desteklenen en yüksek özellik düzeyini görüntüler.|  

 **Bilgi görüntüleme**  
 Yakalama oturumu sırasında kullanılan görüntü bağdaştırıcısı hakkında bilgileri listeler.  

|Özellik|Açıklama|  
|--------------|-----------------|  
|**Açıklama**|Görüntü bağdaştırıcısı açıklama dizesi.|  
|**Görüntüleme belleği**|Grafik bağdaştırıcıda yüklü bellek miktarı.|  
|**Sürücü adı**|Grafik bağdaştırıcısı sürücü adı.|  
|**Sürücü sürümü**|Grafik Bağdaştırıcısı Sürücüsü sürümü.|  
|**Ad**|Grafik bağdaştırıcısının adı.|  

 **Deneme dosyası**  
 Yakalama oturumu ile ilişkili deneme dosya hakkındaki bilgileri listeler.  

|Özellik|Açıklama|  
|--------------|-----------------|  
|**Yolu**|.Vsglog dosyasının yolu. **Not:** eski yakalama altında bu özellik kullanılmıyor.|  

 **Modül bilgilerini**  
 Yakalama oturumu sırasında uygulama tarafından yüklenmiş dinamik bağlantı kitaplıklarını (DLL'ler) sürümünü ve adını listeler.  

 **Sistem bilgileri**  
 Donanım ve işletim sistemi, uygulama yakalama oturumu sırasında barındırılan listeler.  

|Özellik|Açıklama|  
|--------------|-----------------|  
|**Bellek**|Bilgisayarda yüklü bellek miktarı.|  
|**İşletim sistemi mimarisi**|Hedef işletim sisteminin CPU mimarisi.|  
|**İşletim sistemi sürümü**|İşletim sistemi sürümü.|  
|**İşlemci**|Bilgisayarda yüklü olan işlemci.|  
|**Hedef uygulama yapısı**|Hedef CPU mimarisi uygulama. Bu farklı olabilir **işletim sistemi mimarisi**.|  

 **Hedef uygulama**  
 Yakalama oturumu konusu bu uygulama hakkında bilgileri listeler.  

|Özellik|Açıklama|  
|--------------|-----------------|  
|**Son değiştirilme tarihi/saati**|Uygulamanın oluşturulduğu saat ve tarihi.|  
|**Yolu**|Uygulama yolu.|  
|**İşlem kimliği**|Uygulamaya verilen işlem kimliği.|  
|**Sürüm**|Uygulama sürümü.|  

 **VSG günlük dosyası**  
 Grafik günlük belgesi hakkında bilgileri listeler.  


| Özellik | Açıklama |
|------------------------| - |
| **Tarafından oluşturulan** | Grafik oluşturulan bir uygulama adı, belge oturum açın. Örneğin, yakalama oturumu başlatıldığına [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (el ile yakalama) Bu özellik değeri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| **Oturum başlangıç saati** | Yakalama oturumunu başladığı saat ve tarihi. |
| **Boyutu** | Grafik günlük belgesi boyutu. |

## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Köşe gölgeleme nedeniyle nesnelerin eksikliği](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [İzlenecek Yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)