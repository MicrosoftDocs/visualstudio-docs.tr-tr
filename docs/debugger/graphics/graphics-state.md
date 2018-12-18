---
title: Grafik durumu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b45e5d922a5f2ed5a2ba15086c708c734d25e95
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476386"
---
# <a name="graphics-state"></a>Grafik Durumu
Visual Studio grafik tanılama durumu penceresinde bir çizim çağrı gibi geçerli Olay sırasındaki etkin grafik durumunu anlamanıza yardımcı olur.  
  
## <a name="understanding-the-state-window"></a>Durum pencere anlama  
 Durum pencere birlikte işleme etkiler ve hiyerarşik olarak sunar durumu tek bir yerde toplar. Direct3D sürümüne bağlı olarak, uygulamanızın kullandığı, durumu penceresinde gösterilen bilgileri farklılıklar olabilir.  
  
### <a name="state-views"></a>Durum görünümleri  
 Durumu tablosunu birkaç farklı şekillerde görüntüleyebilirsiniz:  
  
|Görüntüle|Açıklama|  
|----------|-----------------|  
|API giriş durum görünümü|Bu görünüm durumu Durumu'nu oluşturan Direct3D nesnelerine benzer bir düzende gösterir.|  
|Mantıksal giriş durum görünümü|Bu görünüm mantıksal görünümünde Durumu'nu oluşturan Direct3D nesneleri düzenini yansıtan değil durumu sayısını gösterir.|  
|Durum görünümü sabitlenmiş|Bir hiyerarşi yerine tam adlarıyla düz bir liste sabitlenmiş durumu öğeleri Pinned durum görünümü gösterir. Bu Görünüm durumunun farklı paketleri birçok durumu öğelerinden küçük bir satır sayısı olarak görüntülemek yaptığı mümkündür.|  
  
##### <a name="to-change-the-state-view"></a>Durum görünümü değiştirmek için  
  
-   Durum penceresinde titlebar hemen sol üst kullanmak istediğiniz durumu görüntüle stil karşılık gelen düğmesini seçin.  
  
    -   **API giriş durum görünümü göster**  
  
    -   **Mantıksal durum görünümü göster**  
  
    -   **Pinned durum görünümü göster**  
  
> [!IMPORTANT]
>  Durumda PIN **Göster API giriş durumu** veya **Göster mantıksal durumu** görüntülenmesi için görünümleri **durum görünümü göster sabitlenmiş**.  
  
### <a name="state-table-format"></a>Durum tablo biçiminde  
 Durum pencere bilgi birkaç sütunlarını gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|Ad|Durum öğesinin adı. Bu öğe bir paket durumu temsil ediyorsa, öğeyi görüntülemek için genişletilebilir.<br /><br /> İçinde **API giriş durum görünümü** ve **mantıksal durum görünümü** durumları adları girintili durumları hiyerarşik ilişkiyi göstermek için.<br /><br /> İçinde **durum görünümü sabitlenmiş** durumunda, tam nitelenmiş adlar, düz bir liste görüntülenir.|  
|Değer|Durum öğesinin değeri.|  
|Tür|Durum öğesi türü.|  
  
### <a name="changed-state"></a>Değiştirilen durumu  
 Grafik durumu genellikle artımlı olarak sonraki çizim çağrıları arasında değiştirir ve durumu yanlış değiştirildiğinde çok çeşitli işleme sorunları nedeniyle oluşur. Önceki arama çizin bu yana hangi durumu değişti bulmanıza yardımcı olmak için değiştirilmiş durumu yıldızla işaretlenmiş ve kırmızı olarak görüntülenen — böylece değiştirilen durumunda kolayca belirleyebileceğiniz yalnızca durum ancak kendi üst durumu öğesi de bu geçerlidir en yüksek düzeye ve ardından detaya geçmek ayrıntıları.  
  
### <a name="pinning-state"></a>Sabitleme durumu  
 Birçok uygulama benzer nesneleri sırayla, durumu, bilinen bir dizi değiştirme işlemek için bazen çağrısı çizmek için çizim çağrısından taşıma nasıl değişiklikleri izleyebilmesi için yerinde değişen durumları sabitlemek yararlıdır.  
  
 Bu ayrıca belirli bir durum değişikliği nedeniyle olacak şekilde bir sorunun kaynağını ayırdığınız durumlarda yararlı olabilir.  
  
##### <a name="to-pin-state-in-place"></a>Yerinde durumu sabitlemek için  
  
1.  Durum penceresinde ilgilendiğiniz durumu bulun. İlgilendiğiniz ayrıntılarını bulmak için üst düzey durumu genişletmeniz gerekebilir.  
  
2.  İmleci, ilgilendiğiniz durumu üzerine getirin. Bir PIN simgesi durumu öğenin sol görünür.  
  
3.  Yerinde durumu öğesi sabitlemek için PIN simgesini seçin.