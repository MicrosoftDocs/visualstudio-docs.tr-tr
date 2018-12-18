---
title: Çalıştırılacak C++ Kurallarını Belirtmek için Kural Kümeleri Kullanma
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: a2bd14e4d052179df8a61dfa4b418f07b0f31e3c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893604"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Çalıştırılacak C++ kurallarını belirtmek için kural kümeleri kullanma

Visual Studio'da oluşturma ve değiştirme özel *kural kümesi* Kod Analizi ile ilgili belirli proje gereksinimlerini karşılamak için. Varsayılan kural kümesi içinde depolanan `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 sürüm 15.7** özel kural kümeleri kullanarak herhangi bir metin düzenleyicisi oluşturun ve bunları ne yapı sistemi kullandığınızdan bağımsız olarak komut satırı derlemeleri de uygulayabilirsiniz. Daha fazla bilgi için [/ analyze: ruleset](/cpp/build/reference/analyze-code-analysis).

Visual Studio'da bir özel C++ kural oluşturmak için C/C++ proje Visual Studio IDE'de açık olması gerekir. Ardından bir standart bir kural kümesi kural kümesi Düzenleyicisi'nde açın ve ardından ekleyin veya belirli kuralları kaldırın ve isteğe bağlı olarak Kod Analizi kural ihlal belirlediğinde, gerçekleşen eylemi değiştirebilirsiniz.

Yeni bir özel kural oluşturmak için yeni bir dosya adını kullanarak kaydedin. Özel kural kümesi, projeye otomatik olarak atanır.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Var olan tek kural kümesinden özel bir kural oluşturmak için

1. Çözüm Gezgini'nde, proje için kısayol menüsünü açın ve ardından **özellikleri**.

2. Üzerinde **özellikleri** sekmesini, **Kod Analizi**.

3. İçinde **kural kümesi** aşağı açılan listesinde, aşağıdakilerden birini yapın:

   - Özelleştirmek istediğiniz kural kümesi seçin.

     \- veya -

   - Seçin  **\<Gözat … >** mevcut bir kuralı kümesini belirlemek için listesinde değil.

4. Seçin **açık** kuralları kural kümesi Düzenleyicisi'nde görüntülemek için.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Bir kuralı değiştirmek için kural kümesi Düzenleyicisi'nde ayarlayın.

- Kural kümesi görünen adını değiştirmek için **görünümü** menüsünde seçin **Özellikler penceresi**. Görünen ad girin **adı** kutusu. Görünen ad dosya adından farklı olabilir dikkat edin.

- Özel kural kümesi için tüm Grup kurallarını eklemek için grubunun onay kutusunu seçin. Grubun tüm kuralları kaldırmak için onay kutusunu temizleyin.

- Özel kural kümesi için belirli bir kural eklemek için kuralın onay kutusunu seçin. Kural kural kümesinden kaldırmak için onay kutusunu temizleyin.

- Bir kod analizi kural ihlal edildiğinde gerçekleştirilecek eylemi değiştirmek için seçin **eylem** kural için alan ve sonra aşağıdaki değerlerden birini seçin:

     **Uyar** -bir uyarı oluşturur.

     **Hata** -bir hata oluşturur.

     **Hiçbiri** -kural devre dışı bırakır. Bu eylem kural kümesi kuralı kaldırma aynıdır.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Gruplandırmak için filtre veya kural kümesi Düzenleyici'sini alanları, kural kümesi Düzenleyici araç kullanarak

- Tüm grupları kurallarında genişletmek için seçin **Tümünü Genişlet**.

- Tüm grupları kurallarında daraltmak için seçin **Daralt tüm**.

- Kurallar tarafından gruplandırılır alanını değiştirmek için alanı seçin **Group By** listesi. Gruplandırılmamış kuralları görüntülemeyi tercih  **\<yok >**.

- Alan kuralı sütunlar ekleyip için seçin **sütun seçenekleri**.

- Geçerli çözüme geçerli olmayan kuralları gizlemek için seçin **Gizle geçerli çözüme geçerli olmayan kuralları**.

- Hata eylemi atanmış olan kuralları gizleme ve gösterme arasında geçiş yapmak için seçin **kod analiz hataları verebilen kuralları göster**.

- Uyarı eylemi atanmış olan kuralları gizleme ve gösterme arasında geçiş yapmak için seçin **kod analiz uyarıları üretebilen kuralları göster**.

- Atanan kuralları gizleme ve gösterme arasında geçiş yapmak için **hiçbiri** eylemi seçin **etkin olmayan kuralları göster**.

- Varsayılan kural kümeleri geçerli kural kümesine Microsoft ekleyip için seçin **alt kural kümelerini Ekle veya Kaldır**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Bir metin düzenleyicisinde bir kural oluşturmak için

Özel kural kümesi düzenleyici metin oluşturmak, herhangi bir konumda depolayın bir `.ruleset` uzantısı ve ile uygulama [/ analyze: ruleset](/cpp/build/reference/analyze-code-analysis) derleyici seçeneği.

Aşağıdaki örnek, bir başlangıç noktası olarak kullanabileceğiniz dosyası temel bir kural kümesi gösterilmektedir:

```xml

<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```
