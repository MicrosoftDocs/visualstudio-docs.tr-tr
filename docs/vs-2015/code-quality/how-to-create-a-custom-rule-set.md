---
title: 'Nasıl yapılır: bir özel kural kümesi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a5d8a5cb7e29cfd900ce81fa5f4b6253f0c49014
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812471"
---
# <a name="how-to-create-a-custom-rule-set"></a>Nasıl yapılır: Özel Kural Kümesi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)], ve [!INCLUDE[vsPro](../includes/vspro-md.md)], özel bir oluşturup *kural kümesi* Kod Analizi ile ilgili belirli proje gereksinimlerini karşılamak için. Özel bir kural oluşturmak için bir açın veya kural kümesi Düzenleyicisi'nde daha fazla standart bir kural koyar. Ekleyebilir veya belirli kuralları kaldırın ve Kod Analizi kural ihlal belirlediğinde, gerçekleşen eylemi değiştirebilirsiniz.  
  
 Yeni bir özel kural oluşturmak için yeni bir dosya adını kullanarak kaydedin. Özel kural kümesi, projeye otomatik olarak atanır.  
  
## <a name="opening-the-rule-set-editor"></a>Açma kural kümesi Düzenleyici  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Kural boş açmak için kural kümesi Düzenleyicisi'nde dosya kümesi  
  
1.  Üzerinde **dosya** menüsü [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], işaret **yeni** ve ardından **dosya**.  
  
2.  İçinde **yeni dosya** iletişim kutusu, tıklayın **genel** içinde **yüklü şablonlar** listeleyin ve ardından **Kod Analizi kural kümesi**.  
  
3.  Kural kümesi Düzenleyicisi görünür. Düzenleyici listesinde hiçbir kural seçilmedi.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Var olan tek kural kümesinden özel bir kural oluşturmak için  
  
1. Çözüm Gezgini'nde projeye sağ tıklayın ve ardından **özellikleri**.  
  
2. Üzerinde **özellikleri** sekmesinde **Kod Analizi**.  
  
3. İçinde **kural kümesi** aşağı açılan listesinde, aşağıdakilerden birini yapın:  
  
   - Özelleştirmek istediğiniz kural kümesi seçin.  
  
     \- veya -  
  
   - Seçin  **\<Gözat … >** mevcut bir kuralı kümesini belirlemek için listesinde değil.  
  
4. Tıklayın **açık** kuralları kural kümesi Düzenleyicisi'nde görüntülemek için.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Özel bir kural oluşturmak için var olan birden çok kural kümelerinden ayarlayın.  
  
1.  Çözüm Gezgini'nde projeye sağ tıklayın ve ardından **özellikleri**.  
  
2.  Üzerinde **özellikleri** sekmesinde **Kod Analizi**.  
  
3.  Seçin  **\<birden çok kural kümeleri... seçin >** gelen **bu kural kümesini Çalıştır**.  
  
4.  İçinde **Ekle veya Kaldır kural kümeleri** kural kümeleri üzerinde iletişim kutusunda, yeni bir kural kümesi temel ve ardından istediğiniz **Tamam**.  
  
5.  Yeni kural kümesi kaydedin.  
  
     Yeni Kural kümesinin adını seçili **bu kural kümesini Çalıştır** listesi. Kural kümesi sonraki adımda görünen adını değiştirebilirsiniz.  
  
6.  (İsteğe bağlı) Kural kümesi görünen adını değiştirmek için **görünümü** menüsünde tıklatın **Özellikler penceresi**. Görünen ad yazın **adı** kutusu.  
  
7.  Eklemek, kaldırmak veya yeni bir kural kümesi içinde belirli bir kod analizi kuralları Değiştir, tıklayın **açık**.  
  
## <a name="modifying-a-rule-set"></a>Bir kural kümesini değiştirme  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Bir kuralı değiştirmek için kural kümesi Düzenleyicisi'nde ayarlayın.  
  
-   Kural kümesi görünen adını değiştirmek için **görünümü** menüsünde tıklatın **Özellikler penceresi**. Görünen ad girin **adı** kutusu. Görünen ad dosya adından farklı olabilir dikkat edin.  
  
-   Özel kural kümesi için tüm Grup kurallarını eklemek için grubunun onay kutusunu seçin. Grubun tüm kuralları kaldırmak için onay kutusunu temizleyin.  
  
-   Özel kural kümesi için belirli bir kural eklemek için kuralın onay kutusunu seçin. Kural kural kümesinden kaldırmak için onay kutusunu temizleyin.  
  
-   Bir kod analizi kural ihlal edildiğinde gerçekleştirilecek eylemi değiştirmek için tıklayın **eylem** kural için alan ve sonra aşağıdaki değerlerden birini seçin:  
  
     **Uyar** -bir uyarı oluşturur.  
  
     **Hata** -bir hata oluşturur.  
  
     **Hiçbiri** -kural devre dışı bırakır. Bu eylem kural kümesi kuralı kaldırma aynıdır.  
  
## <a name="changing-the-rule-set-editor-display"></a>Düzenleyici görünümünü kuralını değiştirmek ayarlama  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Gruplandırmak için filtre veya kural kümesi Düzenleyici'sini alanları, kural kümesi Düzenleyici araç kullanarak  
  
-   Tüm grupları kurallarında genişletmek için **Tümünü Genişlet**.  
  
-   Tüm grupları kurallarında daraltmak için tıklatın **Daralt tüm**.  
  
-   Kurallar tarafından gruplandırılır alanını değiştirmek için alanı seçin **Group By** listesi. Gruplandırılmamış kurallarını görüntülemek için seçin  **\<yok >**.  
  
-   Alan kuralı sütunlar ekleyip için tıklatın **sütun seçenekleri**.  
  
-   Geçerli çözüme, geçerli olmayan kuralları gizlemek için **Gizle geçerli çözüme geçerli olmayan kuralları**.  
  
-   Hata eylemi atanmış olan kuralları gizleme ve gösterme arasında geçiş yapmak için tıklatın **kod analiz hataları verebilen kuralları göster**.  
  
-   Uyarı eylemi atanmış olan kuralları gizleme ve gösterme arasında geçiş yapmak için tıklatın **kod analiz uyarıları üretebilen kuralları göster**.  
  
-   Atanan kuralları gizleme ve gösterme arasında geçiş yapmak için **hiçbiri** eylem tıklayın **etkin olmayan kuralları göster**.  
  
-   Varsayılan kural kümeleri geçerli kural kümesine Microsoft ekleyip için tıklatın **alt kural kümelerini Ekle veya Kaldır**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yönetilen kod projesi için kod çözümlemesini yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Kod çözümleme kural kümesi başvurusu](../code-quality/code-analysis-rule-set-reference.md)



