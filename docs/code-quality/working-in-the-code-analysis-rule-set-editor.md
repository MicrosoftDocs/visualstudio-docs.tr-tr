---
title: Kod Analizi kural kümesi düzenleyicisini kullanma
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdd80031530049b204c0befc445c1416aa08b43e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000822"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Kod Analizi kural kümesi düzenleyicisini kullanma

Kod çözümleme kural önem derecesi kural ihlalleri ayarlayabilir ve bir özel kuralın içerdiği kuralları belirtmenizi Düzenleyicisi sağlar ayarlayın.

Aşağıdaki tablo önem derecesi seçenekleri gösterir:

|Eylem (önem derecesi)|Açıklama|
|-|-|
|Uyarı|Bir uyarı üretir **hata listesi** ve aynı zamanda derleme zamanında.|
|Hata|Bir hata oluşturur **hata listesi** ve aynı zamanda derleme zamanında.|
|Bilgi|Bir ileti oluşturur **hata listesi**.|
|Hidden|İhlalin kullanıcı için görünür değil. IDE ihlalini ancak bildirilir.|
|Yok.|Kural bastırılır. Kuralın kural kümesi kaldırıldıysa gibi davranış aynıdır.|

Düzenleyici kuralları, belirttiğiniz alan grupları kuralları bir kural tarafından ayarlanan bir ağaç yapısında görüntüler. Ekleme veya kuralları kural kümesinden kaldırmak için bir veya daha fazla aşağıdaki adımları gerçekleştirin:

- Seçin veya eklemek veya gruptaki tüm kurallar kaldırmak için Grup düğümü onay kutusunu temizleyin. Bir grubu seçtiğinizde, tüm kuralları ayarlandığından **uyarı** eylem.

   > [!TIP]
   > Kurallar nasıl gruplandırılır değiştirebilirsiniz **gruplandırma ölçütü** açılır.

- Tıklayın **eylem** bir grubun alan ve sonra gruptaki tüm kuralları uygulamak için eylem belirtin.

- Seçin veya tek bir kural için onay kutusunu temizleyin. Bir kural için onay kutusunu seçtiğinizde, kural bir uyarı eylemi için ayarlanır.

## <a name="toolbar"></a>Araç Çubuğu

Kural kümesi Düzenleyici araç çubuğunda, gruplandırma, filtreleme ve kural kümesi kılavuzunda görüntülenen verileri aramak için kullanabilirsiniz.

Aşağıdaki tabloda, kural kümesi Düzenleyicisi araç çubuğundaki denetimleri açıklanmaktadır.

|ToolBar denetimi|Açıklama|
|---------------------|-----------------|
|**Tümünü Genişlet**|İçindeki tüm gruplar kuralları gösterir.|
|**Tümünü Daralt**|Tüm grupları kurallarında gizler.|
|**Gruplandırma ölçütü**|Kurallar tarafından gruplandırılır alanını belirtir. Tıklayın  **\<yok >** grupları olmadan kuralları göstermek için.|
|**Sütun seçenekleri**|Görüntülenecek kural alanları belirtir.|
|**Geçerli çözüme uygulamayın gizleme kuralları**|Çözümü olarak aynı hedef türünün olmayan kuralları gizler veya gösterir.|
|**Kod analiz hataları verebilen kuralları göster**|Hata eylemi atanmış olan kuralları gizler veya gösterir.|
|**Kod analiz uyarıları üretebilen kuralları göster**|Uyarı eylemi atanmış olan kuralları gizler veya gösterir.|
|**Etkin olmayan kuralları göster**|Gösterir veya gizler hiçbiri atanmış olan kural eylemi.|
|**Alt kural kümelerini Ekle Kaldır**|Ekler veya seçili kural kümelerini kuralları kaldırır.|
|**Arama kuralları**|Tüm alan değerleri belirttiğiniz dizeyi arar.|

## <a name="rule-set-fields"></a>Kural kümesi alanları

Kural kümesi alanlar, bir kural kümesi hakkındaki bilgileri görüntülemek ve sıralama ve Gruplama kural listesi için kullanılabilir. Görüntülemek veya alanları gizlemek için seçin **sütun seçenekleri** kuralında Düzenleyici araç çubuğunda ayarlayın ve ardından olup olmadığını denetleyin veya göstermek veya gizlemek için alanların onay kutularını temizleyin.

Aşağıdaki tablo, bir kural kümesi alanlarını açıklar:

|Alan|Açıklama|
|-----------|-----------------|
|**ID**|Kural tanımlayıcısı.|
|**Kategori**|Kural kümeleri üyeliklerine ek olarak, Kod Analizi kuralları da kategoriye göre gruplandırılır. Daha fazla bilgi için [Kod Analizi uyarıları](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Ad**|Kural başlığı.|
|**Namespace**|Kural ad alanı.|
|**Hedef türü**|Kural için yerel, yönetilen veya kod veritabanı gösterir.|
|**Eylem**|Bir kod çözümlemeyi Çalıştır kuralını ihlal edildiğinde gerçekleştirilecek eylem. Düzenleyebileceğiniz **eylem** alan.|
|**Kaynak kural kümeleri**|Kural içeren kural kümesi.|

## <a name="sort-and-filter-rule-sets"></a>Sırala ve Filtrele kural kümeleri

Kural kümesi kılavuz sütun üstbilgileri kaldırın, sıralama ve alan değerleriyle kurallarını Filtrele.

- Kural kümesi listeleri sıralamak için sıralamak istediğiniz alanın sütun başlığına tıklayın. Kural kümeleri gruplanması durumunda her grubu ayrı ayrı sıralanır.

- Kural kümeleri bir alanın değerini göre filtrelemek için filtre düğmesini filtrelemek istediğiniz alanın sütun başlığına tıklayın. Göstermek istediğiniz değerler onay kutularını işaretleyin ve gizlemek istediğiniz değerleri onay kutularını temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir özel kural kümesi oluşturma](../code-quality/how-to-create-a-custom-rule-set.md)