---
title: UML işlemlerin özellikleri sınıf diyagramları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7a5a2e18c41f99462231da2a11dc80a0ae01e99e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804485"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>UML sınıf diyagramlarındaki işlemlerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir UML sınıf diyagramı üzerinde eklediğiniz *işlemleri* sınıfları ve arabirimleri. Bir yöntem veya bir sınıf veya arabirim örneği tarafından gerçekleştirilebilen işlevi bir işlemdir.  

 Bir işlem eklemek için sınıf veya arabirim sağ tıklatın, **Ekle**ve ardından **işlemi**.  

 Bir sınıfın işlemleri diyagramda görünür değilse, sınıf veya arabirim üst kısmındaki Genişlet Köşeli Çift Ayraca tıklayın. Gördüğünüz varsa **işlemi** başlık tıklayın **[+]** operations bölümü genişletin.  

## <a name="signature-of-an-operation"></a>Bir işlemin imzası  
 Bir işlemin imza, bir sınıfta veya arabirimde bir UML sınıf diyagramı temsil eden metin satırının değil. Bunu, aşağıdaki biçime sahiptir:  

 \+ OperationName (parametre1: Type1 [*],...): ReturnType [\*]  

 \+ Genel görünürlük gösterir. Bir izin verilen değerler: - (özel), (korumalı), # ~ (paket).  

 `OperationName` altı çizili olup **Is Static** özelliği true ise ve italic varsa **soyut** özelliği true ise.  

 `: ReturnType` dönüş türü tanımladıysanız atlanır.  

 `[*]` bir parametre veya dönüş türünün çokluğu gösterir. Çokluk 1 ise atlanmıştır.  

 Bu özelliklerin tam bir açıklaması için sonraki bölüme bakın.  

## <a name="properties"></a>Özellikler  
 Bu sınıfta veya arabirimde bir işlemde bir UML sınıf diyagramında özellikleridir.  

 Bir işlem özelliklerini görmek için diyagramda sınıfı veya arabirimi işlemi sağ tıklayın ve ardından **özellikleri**. Özellikleri görünür **özellikleri** penceresi.  


|      Özellik       |   Varsayılan    |                                                                                                                                                                                 Açıklama                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Ad**       | (yeni ad) |                                                                                                                                                                Kapsayan türü içinde benzersiz olmalıdır.                                                                                                                                                                 |
|   **Parametreler**    |    (hiçbiri)    |      Forma sahip bir listeyi <em>adı</em>**:**<em>türü</em>**,** <em>adı</em>**:**  <em>Tür</em>**,...** Tıklayın **[...]**  listesini düzenlemek için.<br /><br /> Türler, ilkel türler veya modelde tanımlı türleri olabilir. Bu özelliği yeni bir tür için bir ad girin, bir tür eklenecek **belirtilmemiş türler** UML Model Gezgini bölümü.      |
|   **Dönüş Türü**   |    (hiçbiri)    |                                                                               **(hiçbiri)** , veya basit türü veya modelde tanımlı bir tür. Bu özelliği yeni bir tür için bir ad girin, bir tür eklenecek **belirtilmemiş türler** UML Model Gezgini bölümü.                                                                                |
| **Koşul sonralarına**  |    (hiçbiri)    |                                                                                                                         Önce ve sonra işlemin yürütülmesinin sistem durumunu arasında bir ilişki belirten isteğe bağlı koşul.                                                                                                                         |
|  **Önkoşulları**  |    (hiçbiri)    |                                                                                                                            Yürütme işleminden önce sistem durumu hakkındaki varsayımların belirten isteğe bağlı koşul başlar.                                                                                                                            |
| **Gövde koşulları** |    (hiçbiri)    |                                                                                                                                                       İsteğe bağlı bir işlem tarafından döndürülen değer kısıtlaması.                                                                                                                                                       |
|   **Görünürlük**    |    Ortak    |                  İmzada görünen karakterler ve izin verilen değerler şunlardır:<br /><br /> **+ Genel** - görünür genel<br /><br /> **-Özel** - türü dışında görünür değil<br /><br /> **# Korumalı** - sahibinden türetilen türler görünür<br /><br /> **~ Paketini** - aynı paket içindeki diğer türlere görünür.                   |
|    **İmza**    |  +*Ad*)   |                                                                                      Görünürlük, adı, parametreleri ve dönüş türü bu işlem özetler. Bu özellikler, diyagram imza düzenleyerek veya bireysel özelliklerini düzenleyerek değiştirebilirsiniz.                                                                                      |
|   **İş öğeleri**    | ilişkili 0 |                                                                                                  İlişkili iş öğelerinin sayısı. Salt okunur.<br /><br /> Daha fazla bilgi için [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Eşzamanlılık**   |  Sıralı  | **Sıralı** -işlemi olduğundan veya eşzamanlılık denetimi olmadan tasarlanır. Bu işlem aynı anda çağırma hatalara neden olabilir.<br /><br /> **Korumalı** -işlemi otomatik olarak diğer örneklerini tamamlanıncaya kadar engeller.<br /><br /> **Eş zamanlı** -işlemi birden çok çağrı eşzamanlı olarak çalıştırabilmeniz için tasarlanmıştır. |
|    **Statik**    |    False     |                                                                                                  TRUE ise, bu işlem bu türün tüm örnekleri arasında paylaşılır.<br /><br /> TRUE ise işlemi adı diyagram üzerinde göründüğü altı çizili olacaktır.                                                                                                   |
|   **Özet**   |    False     |                                                                                                                                        TRUE ise, hiçbir kod bu işlem ile ilişkilidir. Bu nedenle, sahip olan sınıf soyuttur.                                                                                                                                         |
|     **Yaprak**     |    False     |                                                                                                                                              Tasarımcı, türetilen sınıflarda bu işlemi geçersiz kılınamaz amaçlamaktadır.                                                                                                                                              |
|    **Sorgu**     |    False     |                                                                                                 TRUE ise, sistem durumunu önemli bir değişiklik bu işlem tarafından yapılır. Bu nedenle, bu, örneğin, sistemin durumunu denetlemek için bir test çalıştırmasında kullanılabilir.                                                                                                  |
|  **Çokluk**   |      1.       |                                 **1** -tek bir değeri belirtilen türe ait.<br /><br /> **0..1** -olabilir `null`.<br /><br /> \* -belirtilen türde değerler koleksiyonu.<br /><br /> **1..\\**  \* - en az bir değer içeren bir koleksiyon.<br /><br /> *n* `..` *m* -arasında içeren bir koleksiyon `n` ve `m` değerleri.                                  |
|   **Sıralı**    |    False     |                                                                                                                                             TRUE ise koleksiyon sıralı bir liste oluşturur. İçin **Çoğulluk** 1'den fazla.                                                                                                                                              |
|    **Benzersiz**    |    False     |                                                                                                                                         TRUE ise, koleksiyonda yinelenen değerler yoktur. İçin **Çoğulluk** 1'den fazla.                                                                                                                                         |

## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML sınıf diyagramlarındaki türlerin özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki İlişkilendirmelerin Özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)



