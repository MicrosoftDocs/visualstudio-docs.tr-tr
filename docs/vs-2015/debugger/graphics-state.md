---
title: Grafik durumu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5100f32a7a706f0d61e3b0ac006c8168e1ee553
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750366"
---
# <a name="graphics-state"></a>Grafik Durumu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio grafik tanılama durumu penceresinde bir çizim çağrısı gibi geçerli bir Olay sırasındaki etkin olan grafik durumu anlamanıza yardımcı olur.  
  
## <a name="understanding-the-state-window"></a>Durum Penceresi'ni anlama  
 Durum Penceresi'ni birlikte işleme etkiler ve hiyerarşik olarak sunduğu durumu tek bir yerde toplar. Direct3D sürümüne bağlı olarak uygulamanızı kullanır, durumu penceresinde görüntülenen bilgileri farklar olabilir.  
  
### <a name="state-views"></a>Durum görünümleri  
 Durum tablosu birkaç farklı yolla görüntüleyebilirsiniz:  
  
|Görüntüle|Açıklama|  
|----------|-----------------|  
|API giriş durumu görünümünü|Bu görünüm durumunda Durumu'nu oluşturan Direct3D nesneleri için benzer bir düzen gösterir.|  
|Mantıksal giriş durumu görünümünü|Bu görünüm mantıksal görünümündeki Durumu'nu oluşturan Direct3D nesneleri düzenini yansıtan değil durumu sayısını gösterir.|  
|Sabitlenmiş durum görünümü|Bir hiyerarşi yerine Pinned durum görünümü sabitlenmiş durum öğeleri düz bir liste ile tam olarak nitelenmiş adlar sunar. Bu Görünüm durumunun farklı paketleri birçok durum öğeleri az sayıda satır içinde görüntülemek yaptığı mümkündür.|  
  
##### <a name="to-change-the-state-view"></a>Durum görünümü değiştirmek için  
  
-   Titlebar hemen sol üst kısımdaki durum Penceresi'ni kullanmak istediğiniz durum görünümü stiline karşılık gelen düğmeyi seçin.  
  
    -   **API giriş durumu görünümünü göster**  
  
    -   **Mantıksal durumu görünümünü göster**  
  
    -   **Pinned durumu görünümünü göster**  
  
> [!IMPORTANT]
>  Durumda sabitleme gerekir **Göster API giriş durumu** veya **Göster mantıksal durumlarına** görüntülenmesi için görünümleri **durum görünümü göster sabitlenmiş**.  
  
### <a name="state-table-format"></a>Durum tablo biçimi  
 Durum Penceresi'ni çeşitli sütunlar sunar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|Ad|Durum öğesi adı. Bu öğe bir paket durumu temsil ediyorsa, öğeyi görüntülemek için genişletilebilir.<br /><br /> İçinde **API giriş durumu görünümünü** ve **mantıksal durum görünümünü** durumlarını adları girintili durumları hiyerarşik ilişkiyi göstermek için.<br /><br /> İçinde **durum görünümü sabitlenmiş** durumunda, tam olarak nitelenmiş adlar, düz bir listede görüntülenir.|  
|Değer|Durum öğesinin değeri.|  
|Tür|Durum öğenin türü.|  
  
### <a name="changed-state"></a>Durum değiştirme  
 Grafik durumu genellikle artımlı olarak sonraki çizim çağrıları arasında değiştirir ve çok çeşitli işleme sorunlarını durumu yanlış değiştirildiğinde kaynaklanır. Önceki çizim çağrısı çıktılarının sonra hangi durumu değişti bulmanıza yardımcı olmak için değiştirilip değiştirilmediğini durumu yıldız ile işaretlenmiş ve kırmızı renkte gösterilir; böylece değişen durumunu kolayca belirleyebileceğiniz durumu yalnızca sağlar, ancak kendi üst durum öğesi de bu geçerlidir en yüksek düzeyde ve ardından detaya gitme ayrıntıları.  
  
### <a name="pinning-state"></a>Sabitleme durumu  
 Birçok uygulama durumu, bilinen bir dizi değiştirme benzer nesnelerini ardışık olarak işleyin. çünkü bazen çizim çağrısından çizim çağrısı çıktılarının taşıma nasıl değişiklikleri izleyebilmesi için yerinde değişen durumları sabitlemek yararlıdır.  
  
 Bu da bir özel durum nedeniyle olacak şekilde bir sorunun kaynağını ayırdığınız durumlarda yararlı olabilir.  
  
##### <a name="to-pin-state-in-place"></a>Yerinde durumu sabitlemek için  
  
1.  İlginizi çeken durumu durum penceresinde bulun. İlgilendiğiniz ayrıntılarını bulmak için üst düzey durum genişletmeniz gerekebilir.  
  
2.  İlginizi çeken durumu üzerine imleci yerleştirin. Raptiye simgesini, durum öğesi solunda görünür.  
  
3.  Yerinde durumu öğesi sabitlemek için Raptiye simgesini seçin.



