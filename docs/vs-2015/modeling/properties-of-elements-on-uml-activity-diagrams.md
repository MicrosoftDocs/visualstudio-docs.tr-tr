---
title: Etkinlik diyagramlarındaki öğelerin özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
- activity diagrams, properties
ms.assetid: 9849d45e-65d5-46bd-a319-757e90b7c748
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5a3233d073a4b54c7c52b4b725f0d15833f5a51f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803064"
---
# <a name="properties-of-elements-on-uml-activity-diagrams"></a>Etkinlik diyagramlarındaki öğelerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML etkinlik diyagramı üzerinde her öğe diyagram üzerindeki özellikleri vardır. Öğenin özelliklerini görmek için diyagram üzerinde veya öğeye sağ tıklayın **UML Model Gezgini** ve ardından **özellikleri**. Özellikleri görünür **özellikleri** penceresi.  
  
> [!NOTE]
>  Bu konuda, etkinlik diyagramlarındaki öğelerin özellikleri hakkındadır. UML etkinlik diyagramları okuma hakkında daha fazla bilgi için bkz: [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md). UML etkinlik diyagramları çizmek hakkında daha fazla bilgi için bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Öğelerin özellikleri  
  
|         Özellik         |        Varsayılan         |                               Öğe                               |                                                                                                                                                                Açıklama                                                                                                                                                                 |
|--------------------------|------------------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         **Ad**         |     Varsayılan bir ad     |                                 Tümü                                 |                                                                                                                                                          Öğeyi tanımlar.                                                                                                                                                           |
|    **Tam adı**    |    Paket:: adı     |                                 Tümü                                 |                                                                                                                     Öğeyi benzersiz şekilde tanımlar. İle içerdiği paket tam adı öneki.                                                                                                                     |
|      **İş öğeleri**      |      ilişkili 0      |                                 Tümü                                 |                                                                                Bu öğeyle ilişkili çalışma öğelerinin sayısı. İş öğelerini ilişkilendirmek için bkz: [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).                                                                                |
|     **Açıklama**      |         (hiçbiri)         |                                 Tümü                                 |                                                                                                                                             Burada bir öğeyle ilgili genel bir not alabilirsiniz.                                                                                                                                             |
|        **Renk**         | (varsayılan türü için) |                                 Tümü                                 |                                                                                                                                                          Şeklin rengi.                                                                                                                                                           |
|         **Gövde**         |         (hiçbiri)         |                               Eylem                                |                                                                                                                                                      Eylemi ayrıntılı olarak belirtir.                                                                                                                                                       |
|       **Dil**       |         (hiçbiri)         |                               Eylem                                |                                                                                                                                                  İfade gövdesi içinde dili.                                                                                                                                                   |
| **Yerel koşul Sonralarına** |         (hiçbiri)         |         Eylem, gönderme, kabul, çağrı davranışı, arama işlemi         |                                                                                                                          Yürütme sona erdiğinde, karşılanması gereken kısıtlamaları. Eylem tarafından elde edilen hedefi.                                                                                                                          |
| **Yerel önkoşulları**  |         (hiçbiri)         |         Eylem, gönderme, kabul, çağrı davranışı, arama işlemi         |                                                                                                                                        Yürütme başlamadan önce karşılanması gereken kısıtlamaları.                                                                                                                                         |
|    **Uyumludur**    |          Doğru          |                    Çağrı davranışı, işlem çağırma                    |                                                                                                                                        -Etkinlik sonlanana kadar doğruysa eylem bekler.                                                                                                                                        |
|       **Davranışı**       |         (hiçbiri)         |                            Çağrı davranışı                            |                                                                                                                                                         -Etkinlik çağrıldı.                                                                                                                                                          |
|      **İşlemi**       |         (hiçbiri)         |                           İşlem çağırma                            |                                                                                                                                                         -İşlem çağrılır.                                                                                                                                                         |
|    **Sıradan çıkarılmaya olduğu**     |         False          |                            Olay kabul edin                             |                                                                                                       -Doğruysa, birden çok çıktı pini olabilir ve veri açtığına döndürülür. False ise, tüm verilerini tek bir PIN'in görünür.                                                                                                        |
|     **Üst sınır**      |        **\\**\*        |                   Nesne düğümü, Etkinlik parametresi                   |                                                                                                      **0** veri akış boyunca doğrudan geçmesi gerektiğini gösterir.<br /><br /> **\\**\* veri akışı depolanabileceğini belirtir.                                                                                                      |
|      **Seçimi**       |         (hiçbiri)         | Düğüm, Etkinlik parametresi, giriş PIN, PIN çıkış, akış nesne nesnesi |                                                                                                                          Verilere filtre işlemi çağırır. Bu işlem, başka bir diyagrama tanımlanabilir.                                                                                                                          |
|       **Sıralama**       |         (hiçbiri)         |       Nesne düğümü, Etkinlik parametresi giriş PIN, PIN çıkış        |                                                                                                                                                    -Birden çok belirteç nasıl depolanır.                                                                                                                                                     |
|      **Denetimi**      |         False          |                        Giriş PIN, PIN çıkış                        |                                                                                                                            -True Bu PIN akış denetim akışı olur. Bu, yanlışsa, bir nesne akışıdır.                                                                                                                            |
|         **Türü**         |         (hiçbiri)         |       Giriş PIN, PIN çıkış, nesne düğümü, Etkinlik parametresi        |                              -Aktarılan nesnelerin türü.<br />-Türü tamsayı gibi basit bir tür olabilir veya bir sınıflandırıcı başka bir yerde modelde tanımlı. Tanımlanmamış bir türün adını girerseniz, görüneceği **belirtilmemiş türler** UML Model Gezgini bölümü.                               |
|     **Çokluk**     |           1.            |                        Giriş PIN, PIN çıkış                        | -Tek bir değer veya bir aralık olabilir `[n..m]`.<br />-Alt sınır `n` -eylem olamaz (için Giriş bir PIN) Başlat veya Durdur (çıkış PIN için) kadar `n` PIN'i bekleyen nesneler.<br />-Üst sınır `m` -eylem kullanma veya üretemez birden fazla `m` tek bir yürütme nesneleri. \* sınır olmadığını anlamına gelir. |
|    **Dönüştürme**    |         (hiçbiri)         |                             Nesne akışı                             |                                                                                                                      -Verileri dönüştüren bir işlem başlatır. Bu işlem, başka bir diyagrama tanımlanabilir.                                                                                                                       |
|     **Çok noktaya yayın olduğu**     |         False          |                             Nesne akışı                             |                                                                                                                                 -Birden çok alıcı nesneleri veya bileşenleri olabileceğini gösterir.                                                                                                                                 |
|   **ÇokluAlıcı mı**    |         False          |                             Nesne akışı                             |                                                                                                                                 -Birden çok alıcı nesneleri veya bileşenleri olabileceğini gösterir.                                                                                                                                 |
| **Tek Yürütme**  |         False          |                          Etkinlik diyagramı                           |                                                                                                                                   -Eğer ayarlanmış, bu diyagramda, tek bir yürütme aynı anda en fazla yoktur.                                                                                                                                    |
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md)   
 [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)



