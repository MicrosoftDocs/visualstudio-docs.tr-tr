---
title: Kural kümeleri kullanma çalıştırılacak C++ kurallarını belirtmek için | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 42c8926403825032f295c31e2ce113bef4ff1bbd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810299"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Çalıştırılacak C++ Kurallarını Belirtmek için Kural Kümeleri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] ve [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], özel bir oluşturup *kural kümesi* Kod Analizi ile ilgili belirli proje gereksinimlerini karşılamak için. C++ özel bir kural oluşturmak için C/C++ proje Visual Studio IDE'de açık olması gerekir. Ardından bir standart bir kural kümesi kural kümesi Düzenleyicisi'nde açın ve ardından ekleyin veya belirli kuralları kaldırın ve isteğe bağlı olarak Kod Analizi kural ihlal belirlediğinde, gerçekleşen eylemi değiştirebilirsiniz.  
  
 Yeni bir özel kural oluşturmak için yeni bir dosya adını kullanarak kaydedin. Özel kural kümesi, projeye otomatik olarak atanır.  
  
## <a name="opening-the-rule-set-editor"></a>Açma kural kümesi Düzenleyici  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Var olan tek kural kümesinden özel bir kural oluşturmak için  
  
1. Çözüm Gezgini'nde, proje için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2. Üzerinde **özellikleri** sekmesini, **Kod Analizi**.  
  
3. İçinde **kural kümesi** aşağı açılan listesinde, aşağıdakilerden birini yapın:  
  
   - Özelleştirmek istediğiniz kural kümesi seçin.  
  
     \- veya -  
  
   - Seçin  **\<Gözat … >** mevcut bir kuralı kümesini belirlemek için listesinde değil.  
  
4. Seçin **açık** kuralları kural kümesi Düzenleyicisi'nde görüntülemek için.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Bir kuralı değiştirmek için kural kümesi Düzenleyicisi'nde ayarlayın.  
  
-   Kural kümesi görünen adını değiştirmek için **görünümü** menüsünde seçin **Özellikler penceresi**. Görünen ad girin **adı** kutusu. Görünen ad dosya adından farklı olabilir dikkat edin.  
  
-   Özel kural kümesi için tüm Grup kurallarını eklemek için grubunun onay kutusunu seçin. Grubun tüm kuralları kaldırmak için onay kutusunu temizleyin.  
  
-   Özel kural kümesi için belirli bir kural eklemek için kuralın onay kutusunu seçin. Kural kural kümesinden kaldırmak için onay kutusunu temizleyin.  
  
-   Bir kod analizi kural ihlal edildiğinde gerçekleştirilecek eylemi değiştirmek için seçin **eylem** kural için alan ve sonra aşağıdaki değerlerden birini seçin:  
  
     **Uyar** -bir uyarı oluşturur.  
  
     **Hata** -bir hata oluşturur.  
  
     **Hiçbiri** -kural devre dışı bırakır. Bu eylem kural kümesi kuralı kaldırma aynıdır.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Gruplandırmak için filtre veya kural kümesi Düzenleyici'sini alanları, kural kümesi Düzenleyici araç kullanarak  
  
-   Tüm grupları kurallarında genişletmek için seçin **Tümünü Genişlet**.  
  
-   Tüm grupları kurallarında daraltmak için seçin **Daralt tüm**.  
  
-   Kurallar tarafından gruplandırılır alanını değiştirmek için alanı seçin **Group By** listesi. Gruplandırılmamış kuralları görüntülemeyi tercih  **\<yok >**.  
  
-   Alan kuralı sütunlar ekleyip için seçin **sütun seçenekleri**.  
  
-   Geçerli çözüme geçerli olmayan kuralları gizlemek için seçin **Gizle geçerli çözüme geçerli olmayan kuralları**.  
  
-   Hata eylemi atanmış olan kuralları gizleme ve gösterme arasında geçiş yapmak için seçin **kod analiz hataları verebilen kuralları göster**.  
  
-   Uyarı eylemi atanmış olan kuralları gizleme ve gösterme arasında geçiş yapmak için seçin **kod analiz uyarıları üretebilen kuralları göster**.  
  
-   Atanan kuralları gizleme ve gösterme arasında geçiş yapmak için **hiçbiri** eylemi seçin **etkin olmayan kuralları göster**.  
  
-   Varsayılan kural kümeleri geçerli kural kümesine Microsoft ekleyip için seçin **alt kural kümelerini Ekle veya Kaldır**.



