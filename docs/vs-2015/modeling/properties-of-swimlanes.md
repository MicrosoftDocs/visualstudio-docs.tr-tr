---
title: Kulvarların özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c914703d4cbe48e516d1d4e1aa48afb20c9e1cfe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189943"
---
# <a name="properties-of-swimlanes"></a>Kulvarların Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir diyagrama Kulvarlar ekleyebilirsiniz. Kulvarlar dikey veya yatay alana bir diyagram bölün. Diğer şekiller Kulvarlar içinde görüntülenecek tanımlayabilirsiniz. Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikler kullanma hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Kulvarlar aşağıdaki tabloda listelenen özelliklere sahiptir.  
  
|Özellik|Açıklama|Varsayılan|  
|--------------|-----------------|-------------|  
|Gövde dolgu rengi|Kulvar gövdesinin dolgu rengi.|Beyaz|  
|Başlık dolgu rengi|Kulvar üst bilgisinin dolgu rengi.|Koyu gri|  
|Ayırıcı rengi|Ayırıcı çizginin rengi.|LightGray|  
|Ayırıcı çizgi stili|Ayırıcı çizginin stili (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, veya `Custom`).|`Dash`|  
|Ayırıcı kalınlığı|İnç ayırıcı çizginin kalınlığı.|0.03125|  
|Metin rengi|Bu kulvarın ile ilişkili metin dekoratörleri için kullanılan renk.|Siyah|  
|Erişim değiştiricisi|Sınıf erişim düzeyini (`public` veya `internal`).|Ortak|  
|Özel Öznitelikler|Bu kulvarın oluşturulan kod sınıfı öznitelikler eklemek için kullanılır.|\<yok >|  
|Çift oluşturur türetilmiş|Varsa `True`, hem temel sınıf hem de (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) bir kısmi sınıf oluşturulur. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Özel oluşturucu vardır.|Varsa `True`, kaynak kodunda özel bir oluşturucu sağlanacaktır. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Devralma değiştiricisi|Kulvar oluşturulan kaynak kodu sınıf devralma türü açıklar (`none`, `abstract` veya `sealed`).|yok|  
|Temel Kulvar|Bu kulvarın temel sınıf.|(hiçbiri)|  
|Ad|Bu kulvarın adı.|Geçerli ad|  
|Ad Alanı|Bu kulvarın ile bağlantılı olan ad alanı.|Geçerli ad alanı|  
|Araç İpucu türü|Araç İpucu nasıl tanımlandığını (`fixed`, `variable`, veya `none`). Varsa `fixed`, ardından değerini `Fixed Tooltip Text` özelliği kullanılır; varsa `variable`, sonra araç ipucu özel kodda tanımlanır.|\<yok >|  
|Notlar|Bu kulvarın ile ilişkili resmi olmayan notlar.|\<yok >|  
|Hizalama|Yatay veya dikey hizalama.|Dikey|  
|İlk yükseklik|Bu kulvarın inç cinsinden başlangıç yüksekliği. Yalnızca yatay Kulvarlar için geçerlidir.|0|  
|Başlangıç genişliği|Bu kulvarın inç cinsinden başlangıç genişliği. Yalnızca dikey Kulvarlar için geçerlidir.|0|  
|Kullanıma sunan metin rengi|Varsa `True`, kullanıcı oluşturulan tasarımcıdaki bir Kulvar rengini ayarlayabilirsiniz. Bunu ayarlamak için Kulvar şekle sağ tıklayın ve **ekleme kullanıma sunulan**.|False|  
|Açıklama|Oluşturulan tasarımcının belge için kullanılır.|\<yok >|  
|Görünen ad|Bu kulvarın sınıfa başvurmak için oluşturulan tasarımcıda görüntülenecek ad.|\<yok >|  
|Sabit araç ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<yok >|  
|Yardım anahtar sözcüğü|Bu kulvarın için F1 Yardımı dizini oluşturmak için kullanılan anahtar sözcüğü.|\<yok >|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki alanına özgü dil araçları sözlüğü](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



