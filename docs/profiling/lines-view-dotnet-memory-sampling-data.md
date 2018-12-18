---
title: Satırlar görünümü - .NET bellek örnekleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 67148180fab5c712ee15551cf60a8874f427dc0a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854851"
---
# <a name="lines-view---net-memory-sampling-data"></a>Satırlar görünümü - .NET bellek örnekleme verileri
Satırlar görünümü örnekleme yöntemini kullanan .NET bellek ayırma profil oluşturma verileri için ayrılan bellek profil oluşturma çalışması süresince deyimleri listeler. Sütunları ayırmaların sayısı ve boyutu de içerir.  
  
 Bir kaynak dosyasında bir deyimi kaynak dosyasında birden fazla satırı kapsayabilir ve tek bir satır birden fazla deyim içerebilir.  
  
 Bir deyimi aşağıdaki tarafından tanımlanır:  
  
- Function deyimi içeren kaynak dosyası.  
  
- Deyimi içeren işlev.  
  
- Deyim başladığı kaynak satırı.  
  
- Deyim başladığı kaynak satırı karakter.  
  
- Kaynak satırı başlangıçtan deyimini sonlandırır.  
  
- Deyim erdiği kaynak satırı karakter.  
  
  Satır adı sütunu tanımlayıcısı veri sıralanabilir bir birleşimini sağlar.  
  
  Tanımı gereği, diğer işlevler bir deyim çağırmaz. Bu nedenle, yalnızca özel değerler listelenmiştir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|Deyim içeren modül adı.|  
|**Modül yolu**|Deyim içeren modül yolu.|  
|**Kaynak dosyası**|Deyimi içeren kaynak dosya.|  
|**İşlev adı**|Deyim içeren işlevin adı.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**İşlev adresi**|İşlev başlangıç adresi.|  
|**Kaynak satır başlangıcı**|Ayırma oluşan kaynak dosyasındaki başlangıç satırı numarası.|  
|**Kaynak satır sonu**|Ayırma oluşan kaynak dosyasındaki bitiş satır sayısı.|  
|**Kaynak karakter başlangıcı**|Ayırma oluşan kaynak dosya satırında başlangıç karakteri uzaklığı.|  
|**Kaynak karakter sonu**|Öğesindeki taban karakterin bitiş ayırma oluşan kaynak dosya satır uzaklığı.|  
|**Satır adı**|Profil Oluşturucu tarafından oluşturulan bir satırın aşağıdaki sözdizimiyle tanıtıcısı:`Source File`**; [**  `Line Number Start` **,**`Character Start`**] ->; [** `Line Number Start,Character Start`**]**|  
|**Dışlamalı ayırmalar**|Bu satırı içinde oluşturulan nesnelerin toplam sayısı.|  
|**Dışlamalı ayırma yüzdesi**|Bu satırda ayrılan profil oluşturma çalışmasında oluşturulan tüm nesneleri yüzdesi.|  
|**Dışlamalı bayt**|Bu satırda ayrılan tüm profil oluşturma çalışmasında ayrılan belleği bayt yüzdesi.|  
|**Dışlamalı bayt yüzdesi**|Bu satırda ayrılan tüm profil oluşturma çalışmasında ayrılan belleği bayt yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)