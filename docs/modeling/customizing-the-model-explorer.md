---
title: Model Gezginini Özelleştirme
description: Etki alanına özgü dil tasarımcınız için gezgin görünümünü ve davranışını nasıl değiştiryebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c842988f3e5c9f1bbed5a859e73680cb109ecd43
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385909"
---
# <a name="customizing-the-model-explorer"></a>Model Gezginini Özelleştirme
Etki alanına özgü dil tasarımcınız için gezgin görünümünü ve davranışını aşağıdaki gibi değiştirebilirsiniz:

- Pencere başlığını değiştirme.

- Sekme simgesini değiştirme.

- Düğümlerin simgelerini değiştirme.

- Düğümleri gizle.

## <a name="changing-the-window-title"></a>Pencere Başlığını Değiştirme
 Oluşturulan gezginin pencere başlığını değiştirmek için  **DSL** Gezgini'nde Gezgin Davranışı'nın ardından Özellikler penceresinde **Başlık** özelliğini istediğiniz başlık olarak ayarlayın. 

## <a name="changing-the-tab-icon"></a>Sekme Simgesini Değiştirme
 Gezgin için sekme simgesini değiştirmek üzere bir dosyada 16x16 piksellik bir simge .bmp kullanın. Simge dosyasını \DslPackage\Resources\ klasörüne yerleştirin ve dosya adını **ModelExplorerToolWindowBitmaps.bmp.** Örneğin, setup.ico Visual Studio dosyasını farklı bir biçimde .bmp olarak değiştirebilir ve **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp.** Oluşturulan tasarımcı, bu simgeyi gezginle birlikte yerleştirildikleri zaman gezgininizin sekmesinde **Çözüm Gezgini.**

## <a name="setting-custom-icons-on-explorer-nodes"></a>Gezgin Düğümlerde Özel Simgeler Ayarlama
 Gezgin düğüm ayarlarını kullanarak gezgindeki düğümleri özelleştirebilirsiniz. Aşağıdaki yordamda bir düğüme simge ekleme işlemi gösterilir.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Gezgin düğümüne simge eklemek için

1. Görev [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Akışı çözüm şablonunu kullanarak bir çözüm oluşturun.

2. Çözümdeki **Dsl\Resources** .bmp 16x16 piksel simge içeren bir dosya oluşturun.

3. DSL **Gezgini'nde Gezgin** Davranışı'ne sağ **tıklayın ve** ardından Yeni Gezgin Düğümü **Ayarları Ekle'ye tıklayın.**

    Özel **Düğüm Ayarları düğümü altında ExplorerNodeSettings** **düğümü** görünür.

4. **ExplorerNodeSettings'i** seçin ve Özellikler **penceresinde Sınıf'ı** **Actor** olarak **ayarlayın.**

5. Simge **Dosyasını Görüntü olarak** simge dosyasının yoluna ayarlayın.

6. Tüm şablonları dönüştür ve ardından çözümü oluşturun ve çalıştırın.

7. Oluşturulan tasarımcıda Örnek diyagramı açın.

    Gezgin' de simgenizi **olan** üç Aktör düğümü gösterebilirsiniz.

> [!NOTE]
> Oluşturulan gezginde görüntülenen herhangi bir öğe için bir düğüm simgesi ayarladısanız, tüm gezgin düğümleri simgeyi görüntüler. Herhangi bir simge ayarlanmasa düğümler varsayılan simgeyi görüntüler.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Gezgin Düğümünde Görüntülenen Adı Değiştirme
 Model öğelerinin adlarının gezginde nasıl görüntülenmiyor olduğunu değiştirebilirsiniz. Aşağıdaki yordam, açıklama düğümünde bir **Açıklama tarafından** başvurulan Görevin adını **görüntülemeyi** gösterir.

#### <a name="to-display-a-property"></a>Bir özelliği görüntülemek için

1. Önceki yordamda oluşturduğunuz çözümü açın.

2. Özellik adı Subjects **olan** rolün çokluğu ayarını **Subjects** olarak 0..1 olarak ayarerek Açıklama'nın yalnızca tek bir etki alanı sınıfına başvur olduğundan emin olun. Özellik adı Konu, **ilişki** adı da **CommentReferencesSubject olur.**

3. DSL **Gezgini'nde Gezgin** Davranışı'ne sağ **tıklayın ve** ardından Yeni Gezgin Düğümü **Ayarları Ekle'ye tıklayın.**

     Özel **Düğüm Ayarları düğümü altında ExplorerNodeSettings** **düğümü** görünür.

4. **ExplorerNodeSettings'i** seçin ve Özellikler **penceresinde Sınıf'ı** **Açıklama olarak** **ayarlayın.**

5. Açıklama düğümüne **sağ tıklayın** ve ardından Yeni Özellik Yolu **Ekle'ye tıklayın.**

     Özellik Görüntülenen adlı yeni bir **düğüm görünür.**

6. Görüntülenen **Özellik'i** seçin ve **Özellikler** penceresinde, Özelliğin Yolu değer **alanına tıklayın.** **Açıklama'yi,** **ardından CommentReferencesSubject'i ve** ardından **FlowElement'i seçin.** Sonuçta elde edilen yol **CommentReferencesSubject.Subject/! Konu .**

7. Özellik değerinin alanında **Ad'ı** **seçin.**

8. Tüm şablonları dönüştürin ve ardından çözümlerinizi oluşturun ve çalıştırın.

9. Oluşturulan tasarımcıda Örnek diyagramı açın.

10. Diyagramda **açıklama öğesi** ile **Task1** öğesi arasında bir Açıklama Bağlayıcısı çizin.

     Gezgin düğümü açıklamayı **Task1 olarak görüntülemeli.**

## <a name="hiding-nodes"></a>Düğümleri Gizleme
 DSL Gezgini'nin Gizli Düğümler düğümüne yolunu ekleyerek **gezgindeki** bir düğümü **gizleyebilirsiniz.** Aşağıdaki yordam, Açıklama düğümlerini **gizlemeyi** gösterir.

#### <a name="to-hide-an-explorer-node"></a>Gezgin düğümünü gizlemek için

1. Önceki yordamda oluşturduğunuz çözümü açın.

2. DSL **Gezgini'nde Gezgin** Davranışı'ne sağ **tıklayın ve** ardından Yeni Etki Alanı **Yolu Ekle'ye tıklayın.**

     Gizli **Düğümler** altında bir Etki **Alanı Yolu düğümü görünür.**

3. Etki **Alanı Yolu'u** seçin ve **özellikler** penceresinde Yol Tanımı'nın değer **alanına tıklayın.** **FlowGraph'ı** ve **ardından FlowGraphHasComments'ı seçin.** Sonuçta elde edilen yol **FlowGraphHasComments.Comments'a benzer**

4. Tüm şablonları dönüştürin ve ardından çözümlerinizi oluşturun ve çalıştırın.

5. Oluşturulan tasarımcıda Örnek diyagramı açın.

     Gezgin yalnızca bir **Actors düğümünü** göstermeli ve Açıklamalar **düğümünü göstermeli.**

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))