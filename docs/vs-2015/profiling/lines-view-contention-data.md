---
title: Satırlar görünümü - çakışma verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d85173dcf2ab5632fdb18233f9f27f329ddd3769
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773203"
---
# <a name="lines-view---contention-data"></a>Satırlar Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çekişme verisi satırları görünümünü profil oluşturma çalıştırmasını örnek toplanmadı olduğunda yürüten deyimleri için performans verilerini listeler. Bir kaynak dosyasında bir deyimi kaynak dosyasında birden fazla satırı kapsayabilir ve tek bir satır birden fazla deyim içerebilir.  
  
 Bir ifade, aşağıdaki veriler tarafından tanımlanır:  
  
- Function deyimi içeren kaynak dosyası.  
  
- Deyimi içeren işlev.  
  
- Deyim başladığı kaynak satırı.  
  
- Deyim başladığı kaynak satırı karakter.  
  
- Kaynak satırı başlangıçtan deyimini sonlandırır.  
  
- Deyim erdiği kaynak satırı karakter.  
  
  Satır adı sütunu tanımlayıcısı veri sıralanabilir bir birleşimini sağlar.  
  
  Satırlar görünümü raporun sütunları aşağıdaki tabloda açıklanmaktadır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı engellenme süresi**|Bu sırada bu bildirimi nedeniyle bir çakışma olay deyiminde kodun yürütülmesini engellendi süre miktarı. Deyim çağıran işlevler engellenme süresi dahil değildir.|  
|**Dışlamalı engellenme süresi yüzdesi**|Dışlamalı engellenme süresi deyiminin olan işlemdeki tüm engellenme süresi yüzdesi.|  
|**Dışlamalı Çekişmeler**|Bu bildirimi nedeniyle bir çakışma olay deyiminde kodun yürütülmesini engellendi sayısı. Çekişme olayları deyim çağıran işlevler de dahil edilmez.|  
|**Dışlamalı Çekişme yüzdesi**|Bu deyim dışlamalı çekişmeler olan tüm Çekişme olayları işleminde yüzdesi.|  
|**İşlev adresi**|Bu deyim içeren işlevi adresi.|  
|**İşlev adı**|Bu deyim içeren işlev tam adı.|  
|**Kapsamlı engellenme süresi**|Bu ifade ve işlevleri engellenme süresi deyiminde çağrılır.|  
|**Kapsamlı engellenme süresi yüzdesi**|Kapsamlı engellenme süresi deyiminin olan işlemdeki tüm engellenme süresi yüzdesi.|  
|**Kapsamlı Çekişmeler**|Kaç kez bu deyim ve deyim içinde çağrılan işlevler çalıştırılması engellenen olduğunu.|  
|**Kapsamlı Çekişme yüzdesi**|Bu deyim kapsayıcı çekişmelerini olan tüm Çekişme olayları işleminde yüzdesi.|  
|**Satır adı**|Profil Oluşturucu tarafından oluşturulan bir tanımlayıcı satırı. Tanımlayıcı aşağıdaki sözdizimini kullanır:`SourceFile`**; [**  `LineNumberStart` **,**`CharacterStart`**] ->; [** `LineNumberEnd`**,**`CharacterEnd`**]**|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Modül adı**|Deyim içeren modül adı.|  
|**Modül yolu**|Deyim içeren modül yolu.|  
|**İşlem kimliği**|İşlem kimliği (PID) profilli işlemin.|  
|**İşlem adı**|İşlemin adı.|  
|**Kaynak karakter başlangıcı**|Bu bildirimi başladığı kaynak dosya satırında başlangıç karakteri uzaklığı.|  
|**Kaynak karakter sonu**|Bu bildirimi erdiği kaynak dosya satırında başlangıç karakteri uzaklığı.|  
|**Kaynak dosyası**|Function deyimi içeren kaynak dosyanın adı.|  
|**Kaynak satır başlangıcı**|Deyim başladığı kaynak dosyadaki satır numarası.|  
|**Kaynak satır sonu**|Deyim erdiği kaynak dosyadaki satır numarası.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Satırlar görünümü](../profiling/lines-view.md)   
 [Satırlar görünümü - örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)



