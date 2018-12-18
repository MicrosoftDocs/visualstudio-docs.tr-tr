---
title: Kod Analizi kural kümesi de çalışma Düzenleyicisi | Microsoft Docs
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
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cd107f2ac0c377765fda2f62f175d7285eb01bb6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269652"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Kod Çözümleme Kural Kümesi Düzenleyici'de Çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi kural kümesi Düzenleyici'sini, bir özel kural kümesinde bulunan kuralları belirtmek ve eylem belirtmenize olanak sağlar. Kod Analizi kural ihlalini karşılaştığında gerçekleştirilecek eylemi de belirtebilirsiniz.  
  
|Eylem|Açıklama|  
|------------|-----------------|  
|**Uyarı**|Bir uyarı üretir **hata listesi** penceresi.|  
|**Hata:**|Bir hata oluşturur **hata listesi** penceresi.|  
|**Yok**|Kuralı devre dışı bırakır.|  
  
 Düzenleyici kuralları, belirttiğiniz alan grupları kuralları bir kural tarafından ayarlanan bir ağaç yapısında görüntüler. Ekleme veya kuralları kural kümesinden kaldırmak için bir veya daha fazla aşağıdaki adımları gerçekleştirin:  
  
-   Seçin veya eklemek veya gruptaki tüm kurallar kaldırmak için Grup düğümü onay kutusunu temizleyin. Bir grubu seçtiğinizde, tüm kuralları ayarlandığından **uyarı** eylem.  
  
-   Tıklayın **eylem** bir grubun alan ve sonra gruptaki tüm kuralları uygulamak için eylem belirtin.  
  
-   Seçin veya tek bir kural için onay kutusunu temizleyin. Bir kural için onay kutusunu seçtiğinizde, kural bir uyarı eylemi için ayarlanır.  
  
## <a name="rule-set-editor-toolbar"></a>Kural kümesi Düzenleyici araç çubuğu  
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
 Kural bir kural görüntü bilgilerini ayarlamak ve sıralama ve Gruplama kural listesi için kullanılabilir alanları ayarlayın. Alanları gizleme ya da görüntülemek için tıklayın **sütun seçenekleri** kuralında Düzenleyici araç çubuğunda ayarlayın ve ardından olup olmadığını denetleyin veya göstermek veya gizlemek için alanların onay kutularını temizleyin.  
  
 Aşağıdaki tabloda, bir kural kümesi alanlarını açıklar.  
  
|Alan|Açıklama|  
|-----------|-----------------|  
|**ID**|Kural tanımlayıcısı.|  
|**Kategori**|Kural kümeleri üyeliklerine ek olarak, Kod Analizi kuralları da kategoriye göre gruplandırılır. Daha fazla bilgi için [yönetilen kod uyarıları için Kod Analizi](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Ad**|Kural başlığı.|  
|**Namespace**|Kural ad alanı.|  
|**Hedef türü**|Kural için yerel, yönetilen veya kod veritabanı gösterir.|  
|**Eylem**|Bir kod çözümlemeyi Çalıştır kuralını ihlal edildiğinde gerçekleştirilecek eylem.<br /><br /> **Uyarı** -bir uyarı oluşturur.<br /><br /> **Hata** -bir hata oluşturur.<br /><br /> **Hiçbiri** -kural devre dışı bırakır.<br /><br /> Eylem alanı düzenleyebilirsiniz. Değer None olarak ayarlamadan kuralı için onay kutusunun işaretini kaldırarak aynıdır.|  
|**Kaynak kural kümeleri**|Kural içeren kural kümesi.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Sıralama ve filtreleme kural kümeleri  
 Kural kümesi kılavuz sütun üstbilgileri kaldırın, sıralama ve alan değerleriyle kurallarını Filtrele.  
  
-   Kural kümesi listeleri sıralamak için sıralamak istediğiniz alanın sütun başlığına tıklayın. Kural kümeleri gruplanması durumunda her grubu ayrı ayrı sıralanır.  
  
-   Kural kümeleri bir alanın değerini göre filtrelemek için filtre düğmesini filtrelemek istediğiniz alanın sütun başlığına tıklayın. Göstermek istediğiniz değerler onay kutularını işaretleyin ve gizlemek istediğiniz değerleri onay kutularını temizleyin.



