---
title: Özellikleri özniteliklerin UML sınıf diyagramları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0129242593596ea7e3875db2a748045c50863c4c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817366"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>UML sınıf diyagramlarındaki özniteliklerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir UML sınıf diyagramı üzerinde eklediğiniz *öznitelikleri* sınıfları ve arabirimleri. Özniteliği, sınıf veya arabirim örneklerine eklenebilecek değerleri tanımlar.  

 Bir öznitelik eklemek için sınıf veya arabirim sağ tıklatın, **Ekle**ve ardından **özniteliği**.  

 Bir sınıf diyagramında özniteliklerini görünür değilse, üst sınıfı veya arabirimi genişletmek için köşeli çift Ayraca tıklayın. Eğer görebiliyorsanız **öznitelikleri** başlık tıklayın **[+]** öznitelikleri bölümü genişletin.  

## <a name="signature-of-an-attribute"></a>Bir özniteliğin imzası  
 Bir öznitelik, bir sınıfta veya arabirimde bir UML sınıf diyagramı temsil eden satırı imzadır. Bu, bu biçime sahiptir:  

```  
+ AttributeName : TypeName [*]  
```  

 \+ Genel görünürlük gösterir. Bir izin verilen değerler: - (özel), (korumalı), # ~ (paket).  

 `AttributeName` öznitelik statik ise çizilir.  

 `: TypeName` öznitelik türü yok kaldırılır.  

 `[*]` çeşitlilik gösterir. Çokluk 1 ise atlanmıştır.  

## <a name="properties"></a>Özellikler  
 Aşağıdaki tabloda bir UML sınıf diyagramında sınıf veya arabirim öznitelik özelliklerini açıklar.  

 Bir öznitelik özelliklerini görmek için öznitelik sınıfı veya arabirimi diyagram üzerinde sağ tıklayın ve ardından **özellikleri**. Özellikler, Özellikler penceresinde görünür.  

 Bir öznitelik özelliklerini görüntülemek için sağ tıklayın ve ardından **özellikleri**.  


|   **Özelliği**    | **Default**  |                                                                                                                                                                                                         Açıklama                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Varsayılan değer** |   (boş)    |                                                                                                                                                                               Sınıflandırıcı örneği oluşturulduğunda özniteliğinin değeri.                                                                                                                                                                                |
| **Salt okunur**  |    False     |                                                                                                                                                                                    TRUE ise, öznitelik değeri değiştirilemez.                                                                                                                                                                                    |
|   **Statik**   |    False     |                                                                                                                    TRUE ise, bu öznitelik için tek bir değer bu türün tüm örnekleri arasında paylaşılır.<br /><br /> TRUE ise, öznitelik adı diyagram üzerinde göründüğü çizilir.                                                                                                                    |
|     **Ad**      | (yeni ad) |                                                                                                                                                                                        Sahip olan bir sınıflandırıcı içinde benzersiz olmalıdır.                                                                                                                                                                                        |
|     **Türü**      |    (hiçbiri)    |                                                Basit bir tür gibi **tamsayı**, veya modelde tanımlı bir tür. İlkel olmayan türleri gibi kullanamazsınız **ondalık** değeri meta verilerde kodlanması için. Bu özelliği yeni bir tür için bir ad girin, bir tür eklenecek **belirtilmemiş türler** UML Model Gezgini bölümü.                                                 |
|  **Görünürlük**   |    Ortak    |                                     İmzada görünen karakterler ve izin verilen değerler aşağıdaki gibidir:<br /><br /> **+ Genel** - görünür genel<br /><br /> **-Özel** - türü dışında görünür değil<br /><br /> **# Korumalı** - sahibinden türetilen türler görünür<br /><br /> **~ Paketini** - aynı paket içindeki diğer türlere görünür.                                      |
|  **İş öğeleri**   | ilişkili 0 |                                                                                                                          İlişkili iş öğelerinin sayısı. Salt okunur.<br /><br /> Daha fazla bilgi için [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Yaprak**    |    False     |                                                                                                                                                                    TRUE ise, bu öznitelik şemadaki türetilmiş türlerine izin vermek üzere tasarlanmamıştır.                                                                                                                                                                     |
|  **Türetilmiş**   |    False     |                                                                                                              TRUE ise, bu öznitelik diğer öznitelikleri hesaplanır. Örneğin, çapraz, genişlik ve yükseklik hesaplanır. Ayrıntılar yazılmalıdır **açıklama** veya bağlı bir açıklama.                                                                                                              |
|  **Açıklama**  |   (boş)    |                                                                                                                                                                        Genel notları veya öznitelik değerleri kısıtlamaları tanımlamak için.                                                                                                                                                                        |
| **Çokluk**  |      1.       | **1** -bu öznitelik belirtilen türe ait tek bir değere sahip.<br /><br /> **0..1** -bu öznitelik değeri olabilir `null`.<br /><br /> **\\**\* -Bu özniteliğin değeri, değerlerin bir koleksiyonudur.<br /><br /> **1..\\**  \* -bu özniteliğin değeri en az bir değer içeren bir koleksiyondur.<br /><br /> *n* **...** *m* -bu özniteliğin değeri arasında içeren bir koleksiyondur *n* ve *m* değerleri. |
|  **Sıralı**   |    False     |                                                                                                                                                                    TRUE ise koleksiyon sıralı bir liste oluşturur. İçin **Çoğulluk** 1'den fazla.                                                                                                                                                                     |
|   **Benzersiz**   |    False     |                                                                                                                                                                TRUE ise, koleksiyonda yinelenen değerler yoktur. İçin **Çoğulluk** 1'den fazla.                                                                                                                                                                |

## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML sınıf diyagramlarındaki türlerin özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)   
 [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)



